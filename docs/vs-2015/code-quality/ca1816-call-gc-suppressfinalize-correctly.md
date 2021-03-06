---
title: 'CA1816: GC를 호출 합니다. SuppressFinalize 올바르게 | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1816
- DisposeMethodsShouldCallSuppressFinalize
helpviewer_keywords:
- DisposeMethodsShouldCallSuppressFinalize
- CA1816
ms.assetid: 47915fbb-103f-4333-b157-1da16bf49660
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d859f8fe38d4b6efecb83b117f35cbf483467b6f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913880"
---
# <a name="ca1816-call-gcsuppressfinalize-correctly"></a>CA1816: GC.SuppressFinalize를 올바르게 호출하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGCSuppressFinalizeCorrectly|
|CheckId|CA1816|
|범주|Microsoft입니다. 사용법|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인

-   구현 하는 메서드 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 호출 하지 않습니다 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>합니다.

-   구현의 없는 메서드에 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 호출 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>합니다.

-   메서드 호출 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 이 (Visual Basic의 Me) 이외의 값을 전달 하 고 있습니다.

## <a name="rule-description"></a>규칙 설명
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 메서드를 사용 하면 사용자 개체를 가비지 수집 되기 전에 언제 든 지 리소스를 해제 합니다. 경우는 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 메서드를 호출할 개체의 리소스를 해제 합니다. 이렇게 하면 종료는 불필요 합니다. <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> 호출 해야 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 하므로 가비지 수집기는 개체의 종료자를 호출 하지 않습니다.

 [변수]를 다시 구현 하지 않아도 파생된 형식과 종료자를 방지 하기 위해 (<!-- TODO: review code entity reference <xref:assetId:///System.IDisposable?qualifyHint=True&amp;autoUpgrade=False>  -->) 계속 호출 해야 종료자 없이 unsealed 형식의 호출 하 고 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 에이 규칙 위반 문제를 해결 합니다.

 메서드 구현의 경우 <xref:System.IDisposable.Dispose%2A>, 호출을 추가 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>합니다.

 메서드 구현의 없으면 <xref:System.IDisposable.Dispose%2A>에 대 한 호출을 제거 하거나 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 형식으로 이동 하거나 <xref:System.IDisposable.Dispose%2A> 구현 합니다.

 변경에 대 한 모든 호출 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 이 Me (Visual basic에서)를 전달 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 사용 하 여 의도적는 경우에이 규칙에서 경고를 표시 하지 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> 다른 개체의 수명을 제어 합니다. 구현의 경우이 규칙에서 경고를 표시 하지 마십시오 <xref:System.IDisposable.Dispose%2A> 호출 하지 않습니다 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>합니다. 이런 경우 종료 되지 않도록 하는 데 실패 하 고 성능이 저하 됩니다 및 이점도 없습니다.

## <a name="example"></a>예제
 다음 예제에서는 메서드는 잘못 표시 호출 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>합니다.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly.vb#1)]

## <a name="example"></a>예제
 다음 예제에서는 메서드를 보여 줍니다는 올바르게 호출 <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName>합니다.

 [!code-csharp[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/CS/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.cs#1)]
 [!code-vb[FxCop.Usage.CallGCSuppressFinalizeCorrectly2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CallGCSuppressFinalizeCorrectly2/VB/FxCop.Usage.CallGCSuppressFinalizeCorrectly2.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA2215: Dispose 메서드는 기본 클래스 Dispose를 호출해야 합니다.](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)

 [CA2216: 삭제 가능한 형식은 종료자를 선언해야 합니다.](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)

## <a name="see-also"></a>참고 항목
 [삭제 패턴](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)




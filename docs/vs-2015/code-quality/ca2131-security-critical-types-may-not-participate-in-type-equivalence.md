---
title: 'CA2131: 보안에 중요 한 형식은 형식 동등에 참여 하지 않을 수 있습니다 | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7ae6adb868f30485137bc59a09f5521c42dcab32
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591987"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: 보안에 중요한 형식은 형식 등가에 참여할 수 없습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [CA2131: 보안에 중요 한 형식은 형식 등가에 참여할 수 없습니다](https://docs.microsoft.com/visualstudio/code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence)합니다.

|||
|-|-|
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|
|CheckId|CA2131|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 형식 자체에 형식 동등에 참여 하는 형식 또는 멤버 또는 형식의 필드를 사용 하 여 표시 됩니다는 <xref:System.Security.SecurityCriticalAttribute> 특성입니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙은 중요한 형식 또는 중요한 메서드나 필드를 포함하는 형식이 형식 동등에 참여하는 경우에 적용됩니다. CLR에서 이러한 형식이 검색을 사용 하 여 로드 실패를 <xref:System.TypeLoadException> 런타임 시. 일반적으로 이 규칙은 사용자가 tlbimp와 컴파일러를 이용하여 형식 동등을 수행하지 않고 수동으로 형식 동등을 구현하는 경우에만 적용됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 SecurityCritical 특성을 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 인터페이스, 메서드 및이 규칙을 실행 하면 필드를 보여 줍니다.

 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2131.criticaltypesmustnotparticipateintypeequivalence/cs/ca2131 - criticaltypesmustnotparticipateintypeequivalence.cs#1)]

## <a name="see-also"></a>참고 항목
 [보안 투명 코드, 수준 2](http://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)



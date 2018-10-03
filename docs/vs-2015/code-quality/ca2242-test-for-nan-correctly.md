---
title: 'CA2242: NaN에 대해 테스트 올바르게 | Microsoft Docs'
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
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: dcbfd5e5bd52be2919835cbe5bdfb06119f2a688
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591665"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: NaN에 대해 정확하게 테스트하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [CA2242: NaN에 대해 올바르게 테스트](https://docs.microsoft.com/visualstudio/code-quality/ca2242-test-for-nan-correctly)합니다.

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|범주|Microsoft.Usage|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 식에 대 한 값을 테스트 <xref:System.Single.NaN?displayProperty=fullName> 또는 <xref:System.Double.NaN?displayProperty=fullName>합니다.

## <a name="rule-description"></a>규칙 설명
 <xref:System.Double.NaN?displayProperty=fullName>를 나타내는 숫자가 not 기본값인 산술 연산을 정의 되지 않습니다. 경우에 발생 합니다. 값이 같은지를 테스트 하는 모든 식 및 <xref:System.Double.NaN?displayProperty=fullName> 항상 반환 `false`합니다. 값 사이의 같지 않음 테스트 하는 모든 식 및 <xref:System.Double.NaN?displayProperty=fullName> 항상 반환 `true`합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하 고 정확 하 게 값을 나타내는지 여부를 확인 하려면 <xref:System.Double.NaN?displayProperty=fullName>를 사용 하 여 <xref:System.Single.IsNaN%2A?displayProperty=fullName> 또는 <xref:System.Double.IsNaN%2A?displayProperty=fullName> 값을 테스트 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 두 식에 대 한 값을 잘못 테스트 보여 줍니다 <xref:System.Double.NaN?displayProperty=fullName> 올바르게 사용 하는 식 및 <xref:System.Double.IsNaN%2A?displayProperty=fullName> 값을 테스트 합니다.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]



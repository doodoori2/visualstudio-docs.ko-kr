---
title: 'CA2234: 문자열 대신 System.Uri 개체를 전달하세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PassSystemUriObjectsInsteadOfStrings
- CA2234
helpviewer_keywords:
- CA2234
- PassSystemUriObjectsInsteadOfStrings
ms.assetid: 14616b37-74c4-4286-b051-115d00aceb5f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1f15cda7c95946cd0b7c01a9d11dbe0728e41ef9
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953778"
---
# <a name="ca2234-pass-systemuri-objects-instead-of-strings"></a>CA2234: 문자열 대신 System.Uri 개체를 전달하세요.

|||
|-|-|
|TypeName|PassSystemUriObjectsInsteadOfStrings|
|CheckId|CA2234|
|범주|Microsoft.Usage|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 이름에 "uri", "Uri", "urn", "Urn", "url" 또는 "Url"; 포함 된 문자열 매개 변수가 있는 메서드 호출 메서드의 선언 형식에는 해당 메서드 오버 로드를 포함 한 <xref:System.Uri?displayProperty=fullName> 매개 변수입니다.

## <a name="rule-description"></a>규칙 설명
 매개 변수 이름에 카멜식 대/소문자 규칙에 따라 토큰으로 분할 됩니다 및 각 토큰 다음 "uri", "Uri", "urn", "Urn", "url" 또는 "Url" 같은지 확인 확인 합니다. 일치 하는 경우 매개 변수는 uniform resource identifier (URI)를 나타내는로 간주 됩니다. URI의 문자열 표현은 구문 분석 및 인코딩 오류를 발생시키기 쉬우며 보안 문제를 일으킬 수 있습니다. <xref:System.Uri> 클래스는 안전 하 고 안전한 방식으로 이러한 서비스를 제공 합니다. URI의 표현에 대 한만 다른 두 오버 로드를 선택한 경우 사용자는 오버 로드를 선택 해야는 <xref:System.Uri> 인수입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하는 오버 로드를 호출 하 여 <xref:System.Uri> 인수입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하는 경우
 문자열 매개 변수는 URI를 나타내지 않는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 메서드를 보여 줍니다 `ErrorProne`, 규칙을 위반 하는 메서드는 `SaferWay`를 올바르게 호출을 <xref:System.Uri> 오버 로드 합니다.

 [!code-vb[FxCop.Usage.PassUri#1](../code-quality/codesnippet/VisualBasic/ca2234-pass-system-uri-objects-instead-of-strings_1.vb)]
 [!code-cpp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CPP/ca2234-pass-system-uri-objects-instead-of-strings_1.cpp)]
 [!code-csharp[FxCop.Usage.PassUri#1](../code-quality/codesnippet/CSharp/ca2234-pass-system-uri-objects-instead-of-strings_1.cs)]

## <a name="related-rules"></a>관련된 규칙
 [CA1057: 문자열 URI 오버 로드는 System.Uri 오버 로드를 호출](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)

 [CA1056: URI 속성은 문자열이 면 안 됩니다.](../code-quality/ca1056-uri-properties-should-not-be-strings.md)

 [CA1054: URI 매개 변수는 문자열이 면 안 됩니다.](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)

 [CA1055: URI 반환 값은 문자열이 면 안 됩니다.](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)
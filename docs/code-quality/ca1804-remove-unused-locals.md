---
title: 'CA1804: 사용되지 않는 로컬 항목을 제거하세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1804
- RemoveUnusedLocals
helpviewer_keywords:
- RemoveUnusedLocals
- CA1804
ms.assetid: cc332e67-6543-4813-bd8a-6f6fc75bf22a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: f567fa1d1f793395532efac5991b01c5087b638a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55908532"
---
# <a name="ca1804-remove-unused-locals"></a>CA1804: 사용되지 않는 로컬 항목을 제거하세요.

|||
|-|-|
|TypeName|RemoveUnusedLocals|
|CheckId|CA1804|
|범주|Microsoft.Performance|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 메서드 지역 변수를 선언 하지만 사용 하지 않습니다 제외 하 고 변수의 가능한 대입문의 받는 사람으로 합니다. 이 규칙에 따라 분석에 대 한 디버깅 정보로 테스트 되는 어셈블리를 빌드해야 하 고 연결된 프로그램 데이터베이스 (.pdb) 파일을 사용할 수 있어야 합니다.

## <a name="rule-description"></a>규칙 설명
 사용되지 않는 지역 변수와 불필요한 할당으로 어셈블리의 크기가 증가하고 성능이 저하될 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 제거 하거나 지역 변수를 사용 합니다. C# 컴파일러 되는 포함 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] 사용 되지 않는 로컬 변수를 제거 때는 `optimize` 옵션을 사용 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하는 경우
 컴파일러는 변수를 내보낸 경우이 규칙에서 경고를 표시 합니다. 또한 성능 및 코드 유지 관리 주요 관심사 없는 경우에이 규칙에서 경고를 표시 하거나 규칙을 사용 하지 않으려면 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 몇 가지 사용 되지 않는 로컬 변수를 보여 줍니다.

 [!code-vb[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/VisualBasic/ca1804-remove-unused-locals_1.vb)]
 [!code-csharp[FxCop.Performance.UnusedLocals#1](../code-quality/codesnippet/CSharp/ca1804-remove-unused-locals_1.cs)]

## <a name="related-rules"></a>관련된 규칙
 [CA1809: 과도 한 지역 변수를 방지 합니다.](../code-quality/ca1809-avoid-excessive-locals.md)

 [CA1811: 호출 되지 않는 전용 코드를 방지 합니다.](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: 인스턴스화되지 않은 내부 클래스를 방지 합니다.](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1801: 사용 되지 않는 매개 변수를 검토](../code-quality/ca1801-review-unused-parameters.md)
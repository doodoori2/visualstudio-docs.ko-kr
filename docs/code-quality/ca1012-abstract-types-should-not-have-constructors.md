---
title: 'CA1012: 추상 형식에는 생성자를 사용하면 안 됩니다.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AbstractTypesShouldNotHaveConstructors
- CA1012
helpviewer_keywords:
- CA1012
ms.assetid: 09f458ac-dd88-4cd7-a47f-4106c1e80ece
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 182a0fc2b0d8947e6e77d557679d5ad92e5bb443
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55929130"
---
# <a name="ca1012-abstract-types-should-not-have-constructors"></a>CA1012: 추상 형식에는 생성자를 사용하면 안 됩니다.

|||
|-|-|
|TypeName|AbstractTypesShouldNotHaveConstructors|
|CheckId|CA1012|
|범주|Microsoft.Design|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 Public 형식이 추상 이며 public 생성자가 있습니다.

## <a name="rule-description"></a>규칙 설명
 추상 형식에 대한 생성자는 파생된 형식에서만 호출할 수 있습니다. public 생성자에서 형식의 인스턴스를 만들고 사용자는 추상 형식의 인스턴스를 만들 수 없기 때문에 public 생성자가 있는 추상 형식은 잘못 디자인된 것입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 생성자를 보호 하거나 형식을 추상으로 선언 하지 마십시오.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하는 경우
 이 규칙에서는 경고를 표시해야 합니다. 추상 형식에 public 생성자를 있습니다.

## <a name="example"></a>예제
 다음 예제에서는이 규칙을 위반 하는 추상 형식을 포함 합니다.

 [!code-vb[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_1.vb)]
 [!code-csharp[FxCop.Design.AbstractTypeBad#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_1.cs)]

## <a name="example"></a>예제
 다음 예제에서 생성자의 내게 필요한 옵션을 변경 하 여 위반을 해결 `public` 에 `protected`입니다.

 [!code-csharp[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/CSharp/ca1012-abstract-types-should-not-have-constructors_2.cs)]
 [!code-vb[FxCop.Design.AbstractTypeGood#1](../code-quality/codesnippet/VisualBasic/ca1012-abstract-types-should-not-have-constructors_2.vb)]
---
title: 'CA1707: 식별자가 밑줄을 포함 하지 않아야 | Microsoft Docs'
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
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0aeea5c113ebebe33d4c371fed1a5c46da4e735e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211070"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: 식별자에는 밑줄을 사용할 수 없습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017에서 최신 설명서를 참조 하세요 [CA1707: 식별자에는 밑줄 없어야 합니다.](https://docs.microsoft.com/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores) docs.microsoft.com에서 제공 합니다.  
  
|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainUnderscores|  
|CheckId|CA1707|  
|범주|Microsoft.Naming|  
|변경 수준|주요-어셈블리에서 발생 한 경우<br /><br /> 아님-형식 매개 변수에서 발생 한 경우|  
  
## <a name="cause"></a>원인  
 밑줄 (_) 문자를 포함 하는 식별자의 이름입니다.  
  
## <a name="rule-description"></a>규칙 설명  
 규칙에 따라 식별자 이름에는 밑줄 문자(_)가 포함될 수 없습니다. 규칙 네임 스페이스, 형식, 멤버 및 매개 변수를 확인합니다.  
  
 명명 규칙은 공통 된 모양을 라이브러리에 대 한 해당 공용 언어 런타임을 대상으로 합니다. 이렇게 하면 새 소프트웨어 라이브러리에 대 한 필수 항목이 며 관리 코드 개발의 전문 지식을 가진 사람이 라이브러리를 개발 하는 고객 신뢰도 증가 하는 학습 곡선을 줄어듭니다.  
  
## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법  
 이름에서 밑줄 문자를 모두 제거 합니다.  
  
## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우  
 이 규칙에서는 경고를 표시해야 합니다.  
  
## <a name="related-rules"></a>관련된 규칙  
 [CA1709: 식별자는 정확한 대/소문자를 사용해야 합니다.](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: 식별자에는 대/소문자만 다른 이름을 사용할 수 없습니다.](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)


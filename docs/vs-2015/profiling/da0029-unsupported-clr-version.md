---
title: 'DA0029: 지원되지 않는 CLR 버전 | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df5deda533c21033d26af4b8dc08d98a5dafc583
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47541382"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: 지원되지 않는 CLR 버전
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [DA0029: 지원 되지 않는 CLR 버전](https://docs.microsoft.com/visualstudio/profiling/da0029-unsupported-clr-version)합니다.  
  
규칙 Id | DA0029 |  
| 범주 | 프로 파일링 도구 사용 |  
| 프로 파일링 방법을 | 명령줄에서 프로 파일링 |  
| 메시지 | 지원 되지 않는 CLR 버전이 수집 하는 동안 발견 되었습니다. 관리 되는 기호가 제대로 확인 되지 않을 수 있습니다. |  
| 규칙 유형 | 정보. |  
  
## <a name="cause"></a>원인  
 프로파일링 도구에서 지원되지 않는 [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)]을(를) 사용하는 응용 프로그램 프로파일링하려고 합니다.  
  
## <a name="rule-description"></a>규칙 설명  
 이 경고는 프로파일링 도구가 응용 프로그램에서 실행되는 관리되는 코드에 대한 기호를 확인할 수 없기 때문에 발생합니다. 프로파일링 도구는 [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)]을(를) 실행하는 응용 프로그램에 대한 관리되는 코드 기호를 확인할 수 없습니다.  
  
## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법  
 없음



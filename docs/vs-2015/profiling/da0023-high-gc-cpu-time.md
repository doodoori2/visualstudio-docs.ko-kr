---
title: 'DA0023: 높은 GC CPU 시간 | Microsoft 문서'
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
- vs.performance.DA0023
- vs.performance.23
- vs.performance.rules.DA0023
ms.assetid: aba875fe-9cbc-418d-a2c4-6eb47519a5bb
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5cdb5e3ea9e01e6444cf05709138984091c36a6d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47550440"
---
# <a name="da0023-high-gc-cpu-time"></a>DA0023: 높은 GC CPU 시간
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [DA0023: 높은 GC CPU 시간](https://docs.microsoft.com/visualstudio/profiling/da0023-high-gc-cpu-time)합니다.  
  
규칙 Id | DA0023 |  
| 범주. NET Framework 사용 |  
| 프로 파일링 방법을 | 모든 |  
| 메시지 | % Time in GC가 상당히 높습니다. 이는 과다한 가비지 수집 오버헤드가 응용 프로그램의 반응성에 영향을 줄 수 있음을 나타냅니다. .NET 메모리 할당 데이터 및 개체 수명 정보를 응용 프로그램에 더 잘 사용 하는 메모리 할당 패턴을 파악을 수집할 수 있습니다. |  
| 규칙 유형 | 정보 제공 용 이므로 |  
  
 샘플링, .NET 메모리 또는 리소스 경합 방법을 사용하여 프로파일링할 경우 이 규칙을 트리거하려면 10개 이상의 샘플을 수집해야 합니다.  
  
## <a name="cause"></a>원인  
 프로파일링 중에 수집되는 시스템 성능 데이터가 가비지 수집에 걸린 시간이 총 응용 프로그램 처리 시간에 비해 크다는 것을 나타냅니다.  
  
## <a name="rule-description"></a>규칙 설명  
 Microsoft .NET CLR(공용 언어 런타임)는 가비지 수집을 사용하여 응용 프로그램에 더 이상 사용되지 않는 개체에서 메모리를 회수하는 자동 메모리 관리 메커니즘을 제공합니다. 가비지 수집기는 많은 할당이 단기 유지된다는 가정 하에 세대를 기준으로 합니다. 예를 들어 로컬 변수는 단기 유지되어야 합니다. 새로 만들어진 개체는 0세대(gen 0)에서 시작되고, 가비지 수집 실행에서 생존하면 1세대로 이동하고, 응용 프로그램에 계속 사용될 경우 마지막으로 2세대로 전환됩니다.  
  
 0세대의 개체는 빈번하게, 보통 매우 효율적으로 수집됩니다. 1세대의 개체는 덜 빈번하게, 덜 효율적으로 수집됩니다. 마지막으로 2세대의 장기 유지 개체는 훨씬 덜 빈번하게 수집되어야 합니다. 전체 가비지 수집 실행을 나타내는 2세대 수집은 가장 부담이 큰 작업이기도 합니다.  
  
 프로파일링 중에 수집되는 시스템 성능 데이터가 가비지 수집에 걸린 시간이 총 응용 프로그램 처리 시간에 비해 클 경우 이 규칙이 실행됩니다.  
  
> [!NOTE]
>  가비지 수집에 걸린 시간이 총 응용 프로그램 처리 시간에 비해 과도할 경우 [DA0024: 과도한 GC CPU 시간](../profiling/da0024-excessive-gc-cpu-time.md) 경고가 이 규칙 대신 실행됩니다.  
  
## <a name="how-to-investigate-a-warning"></a>경고를 조사하는 방법  
 [오류 목록] 창에서 메시지를 두 번 클릭하여 프로파일링 데이터의 [표시 뷰](../profiling/marks-view.md)로 이동합니다. **.NET CLR Memory\\% Time in GC** 열을 찾습니다. 다른 단계보다 관리되는 메모리 가비지 수집의 오버헤드가 더 큰 특정 프로그램 실행 단계가 있는지 확인합니다. % Time in GC 값을 **# of Gen 0 Collections**, **# of Gen 1 Collections**, **# of Gen 2 Collections** 값에서 보고된 가비지 수집 비율에 비교합니다.  
  
 % Time in GC 값은 총 처리량에 비례하여 응용 프로그램이 가비지 수집을 수행하는 데 걸리는 시간을 보고하려고 합니다. % Time in GC 값이 매우 높은 값을 보고하지만 과도한 가비지 수집이 원인이 아닌 상황이 있을 수 있습니다. % Time in GC 값이 계산되는 방법에 대한 자세한 내용은 MSDN에서 **Maoni’s Weblog**의 [Difference Between Perf Data Reported by Different Tools – 4](http://go.microsoft.com/fwlink/?LinkId=177863)(여러 가지 도구에서 보고하는 성능 데이터 간의 차이점 – 4) 항목을 참조하세요. 가비 수집 중에 컴퓨터에서 우선순위가 더 높은 다른 작업이 응용 프로그램을 선점하거나 페이지 오류가 발생할 경우 % Time in GC 카운터가 추가적인 지연을 반영합니다.



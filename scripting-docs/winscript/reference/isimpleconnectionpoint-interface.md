---
title: ISimpleConnectionPoint 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a756fa3f933f4adff56c41a86aee19a0a2a93aa
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346412"
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint 인터페이스
설명 하 고 특정 연결 지점에서 발생 한 이벤트를 열거 하기 위한 간단한 방법을 제공 합니다. 이 인터페이스 또한 쉽게 연결 하는 `IDispatch` 이벤트만 개체입니다. 이 인터페이스에서 프로세스 디버그 관리자 (PDM), 구현 이며 스크립트 엔진에서 사용 됩니다.  
  
 이 인터페이스는에서 사용할 수 있는 `IDebugHelper::CreateSimpleConnectionPoint`합니다.  
  
 상속 된 메서드 외에도 `IUnknown`, `ISimpleConnectionPoint` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|간단한 연결 지점 개체와 클라이언트의 싱크 간에 연결을 설정 합니다.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|이벤트의 지정된 된 범위에서 각 이벤트에 대 한 이름과 DISPID를 반환합니다.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|이 인터페이스에서 노출 하는 이벤트의 수를 반환 합니다.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|`ISimpleConnectionPoint::Advise`를 통해 이전에 설치된 권장된 연결을 종료합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProperty 인터페이스](../../winscript/reference/idebugproperty-interface.md)
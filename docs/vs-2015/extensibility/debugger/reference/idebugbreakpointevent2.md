---
title: IDebugBreakpointEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBreakpointEvent2
helpviewer_keywords:
- IDebugBreakpointEvent2 interface
ms.assetid: 50b3a7a7-331b-42c8-922c-ff3522ebe1da
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5e1f583bca6127aaf9e8b1eb81d9226301b1db60
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47542292"
---
# <a name="idebugbreakpointevent2"></a>IDebugBreakpointEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [IDebugBreakpointEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbreakpointevent2)합니다.  
  
디버그 엔진 (DE) 프로그램이 중단점에서 중지 되 면 (SDM) 세션 디버그 관리자에 게이 인터페이스를 보냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
IDebugBreakpointEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>구현자 참고 사항  
 DE 중단점에 대 한 지원의 일부로이 인터페이스를 구현합니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 이 인터페이스와 동일한 개체에서 인터페이스를 구현 해야 (SDM 사용 [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 액세스 하는 `IDebugEvent2` 인터페이스).  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 DE 만들고 프로그램에서은 하나 이상의 중단점에 도달할 때이 이벤트 개체를 전송 합니다. 이벤트를 사용 하 여 전송 되는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) SDM를 디버깅 중인 프로그램에 연결할 때 제공한 콜백 함수.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDebugBreakpointEvent2`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)|현재 코드 위치에서 발생 하는 모든 중단점에 대 한 열거자를 만듭니다.|  
  
## <a name="requirements"></a>요구 사항  
 헤더: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

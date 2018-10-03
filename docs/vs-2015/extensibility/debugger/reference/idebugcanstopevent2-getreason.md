---
title: IDebugCanStopEvent2::GetReason | Microsoft Docs
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
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fcc130a2b6dc1874c1ac536ae2e7d13aa3db4952
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47553386"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [IDebugCanStopEvent2::GetReason](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcanstopevent2-getreason)합니다.  
  
디버그 엔진 (DE)를 중지 하려고 하는 이유는 이유를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pcr`  
 [out] 값을 반환 합니다 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) 이 이벤트에 대 한 이유를 설명 하는 열거형입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 하기 전에이 메서드는 일반적으로 호출 합니다 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) 메서드 호출자에 게는 0이 아닌 값을 전달할지 여부를 확인할 수 있습니다 (`TRUE`)에 `IDebugCanStopEvent2::CanStop` 메서드.  
  
 중지 이유 일 수 있습니다 `CANSTOP_ENTRYPOINT`는 DE 즉 진입점에 도달 했습니다 또는 `CANSTOP_STEPIN`, 함수 한 단계씩에 DE 의미 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)

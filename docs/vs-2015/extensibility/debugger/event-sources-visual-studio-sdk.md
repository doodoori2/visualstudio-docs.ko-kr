---
title: 이벤트 소스 (Visual Studio SDK) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], event sources
ms.assetid: b9ba0908-ae4c-4a64-aab1-bee453dd7a22
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ee6186714682e381e2ee3d404eaaaed68580f931
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51760781"
---
# <a name="event-sources-visual-studio-sdk"></a>이벤트 소스(Visual Studio SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이벤트의 두 원본이: 디버그 엔진 (DE) 및 세션 디버그 관리자 (SDM). SDM에서 전송 되는 이벤트를 NULL 엔진을 설치 하는 동안에 NULL이 아닌 엔진을가 하는 독일에서 전송 되는 이벤트입니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 보내는 방법을 보여 줍니다 합니다 **IDebugProgramCreateEvent2** SDM DE에서.  
  
```  
CDebugProgramCreateEvent* pProgramCreateEvent = new CDebugProgramCreateEvent();  
if (FAILED(pCallback->Event(m_pEngine, NULL, m_pProgram, NULL, pProgramCreateEvent, IID_IDebugProgramCreateEvent2, EVENT_ASYNCHRONOUS)))  
{  
   // Handle failure here.  
}  
]  
  
CEvent * pProgCreate = new CEvent(IID_IDebugProgramCreateEvent2, EVENT_ASYNCHRONOUS);    
pProgCreate->SendEvent(pCallback, m_pEngine, (IDebugProgram2 *)this, NULL);  
  
HRESULT CEvent::SendEvent(IDebugEventCallback2 *pCallback, IDebugEngine2 *pEngine, IDebugProgram2 *pProgram, IDebugThread2 *pThread) {    
   HRESULT hr;    
  
   if (m_dwAttrib & EVENT_STOPPING)    
   {    
      hr = SendStoppingEvent(pCallback, pEngine, pProgram, pThread);    
   }    
   else if (m_dwAttrib & EVENT_SYNCHRONOUS)    
   {    
      hr = SendSynchronousEvent(pCallback, pEngine, pProgram, pThread);    
   }    
   else    
   {    
      assert(m_dwAttrib == 0);    
      hr = SendAsynchronousEvent(pCallback, pEngine, pProgram, pThread);    
   }    
  
   return hr;    
}    
  
HRESULT CEvent::SendAsynchronousEvent(IDebugEventCallback2 *pCallback, IDebugEngine2 *pEngine, IDebugProgram2 *pProgram, IDebugThread2 *pThread) {    
  
    HRESULT hr;    
  
   // Make sure the CEvent object running this code is not deleted until the code completes.    
   AddRef();    
  
   pCallback->Event(pEngine, NULL, pProgram, pThread, (IDebugEvent2 *)this, m_riid, m_dwAttrib);    
  
   // No error recovery here.    
   hr = S_OK;     
  
   Release();    
   return hr;    
}  
  
```  
  
## <a name="see-also"></a>참고 항목  
 [이벤트 보내기](../../extensibility/debugger/sending-events.md)


---
title: 'Iremotedebugapplication:: Getrootnode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.GetRootNode
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::GetRootNode
ms.assetid: 6c043aba-1dc5-41de-9711-96cde5e040f6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75b398ddac53f2633cbc090f5d49574bd4d94d36
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097775"
---
# <a name="iremotedebugapplicationgetrootnode"></a>IRemoteDebugApplication::GetRootNode
응용 프로그램을 사용 하 여 연결 하는 모든 노드가 추가 되는 응용 프로그램 노드를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetRootNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppdanRoot`  
 [out] 응용 프로그램을 사용 하 여 연결 하는 모든 노드가 추가 되는 디버그 응용 프로그램 노드.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 이 메서드는 응용 프로그램과 연결 하는 모든 노드가 추가 되는 응용 프로그램 노드를 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IRemoteDebugApplication 인터페이스](../../winscript/reference/iremotedebugapplication-interface.md)
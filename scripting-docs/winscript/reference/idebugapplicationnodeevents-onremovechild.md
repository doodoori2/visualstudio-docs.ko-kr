---
title: IDebugApplicationNodeEvents::onRemoveChild | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplicationNodeEvents.onRemoveChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugApplicationNodeEvents::onRemoveChild
ms.assetid: 2e025d29-b8c0-4793-a2d3-c20d548d6386
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fab0d9e70a3c3536043b4050b2f34bf2ae7ab32c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092207"
---
# <a name="idebugapplicationnodeeventsonremovechild"></a>IDebugApplicationNodeEvents::onRemoveChild
디버그 응용 프로그램 노드 개체의 자식 노드를 제거할 때 이벤트를 처리 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT onRemoveChild(  
   IDebugApplicationNode*  prddpChild  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `prddpChild`  
 [in] 제거 된 자식 응용 프로그램 노드입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 이 메서드는 디버그 응용 프로그램 노드 개체의 자식 노드를 제거할 때 이벤트를 처리 합니다.  
  
 구현자는 `IDebugApplicationNode` 인터페이스에는이 이벤트가 발생 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugApplicationNodeEvents 인터페이스](../../winscript/reference/idebugapplicationnodeevents-interface.md)   
 [IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)   
 [IDebugApplicationNode 인터페이스](../../winscript/reference/idebugapplicationnode-interface.md)
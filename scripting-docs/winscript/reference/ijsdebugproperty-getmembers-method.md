---
title: 'Ijsdebugproperty:: Getmembers 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProperty.GetMembers
apilocation:
- jscript9diag.dll
ms.assetid: a32b5372-d9cb-4b9a-9bc2-81b5e1df365c
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 351862f488aceb5fd3e9176cc4676e70b197d803
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087029"
---
# <a name="ijsdebugpropertygetmembers-method"></a>IJsDebugProperty::GetMembers 메서드
이 개체의 멤버를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetMembers(  
   JS_PROPERTY_MEMBERS members,  
   IJsEnumDebugProperty **ppEnum  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `members`  
 [in] 멤버 정보에 포함 된 항목을 지정 하는 플래그입니다.  
  
 `ppEnum`  
 [out] 개체의 멤버입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참고 항목  
 [IJsDebugProperty 인터페이스](../../winscript/reference/ijsdebugproperty-interface.md)
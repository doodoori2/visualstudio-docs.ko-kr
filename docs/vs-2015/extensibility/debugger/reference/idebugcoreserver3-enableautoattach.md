---
title: IDebugCoreServer3::EnableAutoAttach | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0823c64e150d306d4613a8df797f11c0785ba762
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774499"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

지정 된 디버그 엔진에 대 한 자동 연결을 사용 하도록 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `rgguidSpecificEngines`  
 [in] 자동 연결로 표시할 각 디버그 엔진에 대 한 Guid의 배열입니다.  
  
 `celtSpecificEngines`  
 [in] 에 지정 된 엔진 수가 `rgguidSpecificEngines`합니다.  
  
 `pszStartPageUrl`  
 [in] 자동 연결 하는 경우 사용할 시작 URL입니다.  
  
 `pbstrSessionID`  
 [out] 자동 연결 된 세션 ID입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`; 그렇지 않으면 오류 코드를 반환 합니다. 하나의 오류 코드는 `E_AUTO_ATTACH_NOT_REGISTERED`, auto-attach 클래스 팩터리를 등록 되지 않은 나타냅니다.  
  
## <a name="remarks"></a>설명  
 지정 된 URL에 연결 된 프로그램이 시작 되 면 지정 된 디버그 엔진을 자동으로 시작 및 연결 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)


---
title: IDebugProperty2::GetExtendedInfo | Microsoft Docs
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
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9f6fd711a70c050a6f490a27a56eb860c84de867
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726961"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

확장 속성에 대 한 정보를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```csharp  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `guidExtendedInfo`  
 [in] 검색할 확장 정보의 형식을 결정 하는 GUID입니다. 세부 정보에 대 한 설명을 참조 하세요.  
  
 `pExtendedInfo`  
 [out] 반환 된 `VARIANT` (c + +) 또는 개체 (C#) 확장된 속성 정보를 검색 하려면 사용할 수 있는 합니다. 예를 들어이 매개 변수를 반환할 수 있습니다는 `IUnknown` 에 대해 쿼리할 수 있는 인터페이스를 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) 인터페이스입니다. 세부 정보에 대 한 설명을 참조 하세요.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`; 그렇지 않으면 오류 코드를 반환 합니다. 반환 `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` 검색할 확장된 정보가 없는 경우.  
  
## <a name="remarks"></a>설명  
 이 메서드는 그다지 유용 하지 호출 하 여 검색 되는 정보를 검색 하기 위해 존재 합니다 [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 메서드.  
  
 다음 Guid (GUID 값 이름을 어셈블리에서 사용할 수 없으므로 C#에 대해 지정 된)이 메서드에서 일반적으로 인식 됩니다. 내부 사용에 대 한 추가 Guid는 만들 수 있습니다.  
  
|이름|GUID|설명|  
|----------|----------|-----------------|  
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|반환 된 `IUnknown` 문서에 대 한 인터페이스입니다. 일반적으로 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) 에서이 인터페이스를 가져올 수 있습니다 `IUnknown` 인터페이스입니다.|  
|guidCodeContext|{e2fc65e-56ce-11 d 1-b528-00aax004a8797}|반환 된 `IUnknown` 인터페이스 문서 컨텍스트를 합니다. 일반적으로 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 에서이 인터페이스를 가져올 수 있습니다 `IUnknown` 인터페이스입니다.|  
|guidCustomViewerSupported|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|식 계산기에서 주로 구현 되는 사용자 지정 뷰어를의 CLSID를 포함 하는 문자열을 반환 합니다.|  
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|이 속성을 관리 되는 코드 로컬 주소를 나타내는 경우 원하는 슬롯 번호를 나타내는 32 비트 숫자를 반환 합니다.|  
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|속성 개체에 연결 된 변수 시그니처를 포함 하는 문자열을 반환 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)


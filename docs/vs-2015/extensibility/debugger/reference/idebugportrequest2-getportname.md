---
title: IDebugPortRequest2::GetPortName | Microsoft Docs
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
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4d7beb95a91f1b72a44046160359d171f3fcc4b3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51754130"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

포트의 이름을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pbstrPortName`  
 [out] 포트의 이름을 반환합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 합니다 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) 인터페이스는 일반적으로 전달할 디버그 패키지 (클라이언트)에서 포트 공급자 (서버) 연결 포트입니다. 디버그 패키지와 포트 공급자가 포트에 대 한 가능한 선택 항목을 인식 합니다. 간단한 문자열을 해당 포트를 설명할 수 있습니다 하는 경우 해당 `IDebugPortRequest2::GetPortName` 메서드가 연결을 만드는 데 충분 한 정보입니다. 서버를 사용 하 여 가져올 수 있는 클라이언트에서 추가 인터페이스를 지정할 수이 고, 그렇지 `IDebugPortRequest2::QueryInterface`합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)


---
title: IDebugProcessSecurity::GetUserName | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c0dee5cd71cc41c8377914ade5800976d9e7ff57
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557313"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [IDebugProcessSecurity::GetUserName](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocesssecurity-getusername)합니다.  
  
포트 공급자에서 사용자 이름을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```csharp  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pbstrUserName`  
 [out] 사용자 이름을 포함 하는 문자열입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드가 성공 하는 경우 반환 `S_OK`합니다. 그렇지 않으면 오류 코드를 반환합니다.  
  
## <a name="remarks"></a>설명  
 `GetUserName` 에 표시 되는 사용자 이름을 반환 합니다 **사용자 이름** 열의 합니다 **프로세스에 연결** 대화 상자. 보려는 합니다 **프로세스에 연결** 대화 상자에서 클릭 **프로세스에 연결** 에 **도구** 메뉴에서를 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 통합된 개발 환경 (IDE).  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)

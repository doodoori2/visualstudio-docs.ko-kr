---
title: IActiveScriptSite::GetDocVersionString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a451f4883373978772643e11fe22feb9122be30e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349753"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
현재 문서 버전을 고유 하 게 식별 하는 호스트 정의 문자열을 검색 합니다. 관련된 문서 (예: 메모장을 사용 하 여 편집 중인 HTML 페이지의 경우) Windows 스크립트 범위 밖에 서 변경 된 경우 스크립팅 엔진 지속 된 상태로, 다음 스크립트를 로드할 때 다시 컴파일을 적용 함께 저장 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pstrVersionString`  
 [out] 문서 호스트 정의 버전 문자열의 주소입니다.  
  
## <a name="return-value"></a>반환 값  
 반환 `S_OK` 성공 하면 또는 `E_NOTIMPL` 경우이 메서드가 지원 되지 않습니다.  
  
## <a name="remarks"></a>설명  
 경우 `E_NOTIMPL` 반환 되 면 스크립트 문서를 사용 하 여 동기화는 스크립팅 엔진 가정해 야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)
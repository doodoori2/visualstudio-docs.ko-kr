---
title: 'Idiaimagedata:: Get_imagebase | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaImageData::get_imageBase method
ms.assetid: 4ba3d9e4-b205-4ee6-a41d-6996972f1f85
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 278ea226c9531cdf16cc7660bb4eba67860430a4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557182"
---
# <a name="idiaimagedatagetimagebase"></a>IDiaImageData::get_imageBase
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [idiaimagedata:: Get_imagebase](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiaimagedata-get-imagebase)합니다.  
  
여기서 이미지를 기반으로 하는 메모리 위치를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT get_imageBase (   
   ULONGLONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pRetVal`  
 [out] 이미지 제안 된 기본 값을 반환합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이미지 기본 충돌로 인해 이미지 수 기준 주소를 지정할 자동으로 사용 되지 않는 메모리 위치에 로드 되는 경우. 이 메서드는 컴파일 시 모듈에 저장 된 기본 힌트 (제안 된 메모리 위치)를 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)



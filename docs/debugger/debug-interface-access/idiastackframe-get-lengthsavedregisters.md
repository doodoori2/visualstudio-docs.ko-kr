---
title: 'Idiastackframe:: Get_lengthsavedregisters | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_lengthSavedRegisters method
ms.assetid: b75fad6e-1ef4-44e6-89e3-c31c6fba10b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 936cd1f057258bdeda455c67e69e3cd7a9272cc7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56615340"
---
# <a name="idiastackframegetlengthsavedregisters"></a>IDiaStackFrame::get_lengthSavedRegisters
스택에 저장 된 레지스터의 바이트 수를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_lengthSavedRegisters ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

[out] 저장 된 레지스터의 바이트 수를 반환합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 반환 `S_FALSE` 속성이 지원 되지 않는 경우. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="see-also"></a>참고 항목
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
---
title: IEnumDebugObjects::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Next
helpviewer_keywords:
- IEnumDebugObjects::Next method
ms.assetid: e54c3055-6030-4dc9-9f7a-5e3ce75f252f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33d9bf44d8d586c5e9206ff23ec69970b5a00449
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704269"
---
# <a name="ienumdebugobjectsnext"></a>IEnumDebugObjects::Next
이 메서드는 열거형에서 다음 요소 집합을 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Next(
   ULONG          celt,
   IDebugObject** rgelt,
   ULONG*         pceltFetched
);
```

```csharp
int Next(
   uint           celt,
   IDebugObject[] rgelt,
   ref uint       pceltFetched
);
```

#### <a name="parameters"></a>매개 변수
 `celt`

 [in] 검색할 요소의 수입니다. 또한 최대 크기를 지정 된 `rgelt` 배열입니다.

 `rgelt`

 [out에서] 배열을 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) 채울 요소입니다.

 `pceltFetched`

 [out] 에 실제로 반환 된 요소의 수를 반환 합니다. `rgelt`합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 반환 `S_FALSE` 요소의 요청 된 수보다 적은; 반환 될 수 있으면이 고, 그렇지 오류 코드를 반환 합니다.

## <a name="see-also"></a>참고 항목
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
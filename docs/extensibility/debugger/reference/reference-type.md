---
title: REFERENCE_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- REFERENCE_TYPE
helpviewer_keywords:
- REFERENCE_TYPE enumeration
ms.assetid: b1ffba10-eb9d-48ba-bf48-6d8b71d6f270
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcfc3745676ba1309327dc84143b0706ba02b5a2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694441"
---
# <a name="referencetype"></a>REFERENCE_TYPE
참조 형식을 지정합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_REFERENCE_TYPE { 
   REF_TYPE_WEAK   = 0x0001,
   REF_TYPE_STRONG = 0x0002
};
typedef DWORD REFERENCE_TYPE;
```

```csharp
public enum enum_REFERENCE_TYPE { 
   REF_TYPE_WEAK   = 0x0001,
   REF_TYPE_STRONG = 0x0002
};
```

## <a name="members"></a>멤버
 REF_TYPE_WEAK 약한 참조를 지정합니다. 함께 사용할 수 없습니다 `REF_TYPE_STRONG`합니다.

 REF_TYPE_STRONG 강력한 참조를 지정합니다. 함께 사용할 수 없습니다 `REF_TYPE_WEAK`합니다.

## <a name="remarks"></a>설명
 로 사용 합니다 `dwRefType` 의 멤버는 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) 구조입니다.

 매개 변수로 전달 된 [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md) 메서드.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)
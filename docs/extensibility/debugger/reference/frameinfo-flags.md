---
title: FRAMEINFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FRAMEINFO_FLAGS
helpviewer_keywords:
- FRAMEINFO_FLAGS enumeration
ms.assetid: 41578062-8455-412a-9d8b-1e1e9dc8d52e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 54bb93fa6f88c02731691728bceacdd4a5fe2036
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56694350"
---
# <a name="frameinfoflags"></a>FRAMEINFO_FLAGS
스택 프레임 개체에 대 한 검색 정보를 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
typedef DWORD FRAMEINFO_FLAGS;
```

```csharp
public enum enum_FRAMEINFO_FLAGS {
    FIF_FUNCNAME              = 0x00000001,
    FIF_RETURNTYPE            = 0x00000002,
    FIF_ARGS                  = 0x00000004,
    FIF_LANGUAGE              = 0x00000008,
    FIF_MODULE                = 0x00000010,
    FIF_STACKRANGE            = 0x00000020,
    FIF_FRAME                 = 0x00000040,
    FIF_DEBUGINFO             = 0x00000080,
    FIF_STALECODE             = 0x00000100,
    FIF_ANNOTATEDFRAME        = 0x00000200,
    FIF_DEBUG_MODULEP         = 0x00000400,
    FIF_FUNCNAME_FORMAT       = 0x00001000,
    FIF_FUNCNAME_RETURNTYPE   = 0x00002000,
    FIF_FUNCNAME_ARGS         = 0x00004000,
    FIF_FUNCNAME_LANGUAGE     = 0x00008000,
    FIF_FUNCNAME_MODULE       = 0x00010000,
    FIF_FUNCNAME_LINES        = 0x00020000,
    FIF_FUNCNAME_OFFSET       = 0x00040000,
    FIF_FUNCNAME_ARGS_TYPES   = 0x00100000,
    FIF_FUNCNAME_ARGS_NAMES   = 0x00200000,
    FIF_FUNCNAME_ARGS_VALUES  = 0x00400000,
    FIF_FUNCNAME_ARGS_ALL     = 0x00700000,
    FIF_ARGS_TYPES            = 0x01000000,
    FIF_ARGS_NAMES            = 0x02000000,
    FIF_ARGS_VALUES           = 0x04000000,
    FIF_ARGS_ALL              = 0x07000000,
    FIF_ARGS_NOFORMAT         = 0x08000000,
    FIF_ARGS_NO_FUNC_EVAL     = 0x10000000,
    FIF_FILTER_NON_USER_CODE  = 0x20000000,
    FIF_ARGS_NO_TOSTRING      = 0x40000000,
    FIF_DESIGN_TIME_EXPR_EVAL = 0x80000000
};
```

## <a name="members"></a>멤버
FIF_FUNCNAME 초기화/사용 된 `m_bstrFuncName` 필드입니다.

FIF_RETURNTYPE 초기화/사용 된 `m_bstrReturnType` 필드입니다.

FIF_ARGS 초기화/사용 된 `m_bstrArgs` 필드입니다.

FIF_LANGUAGE 초기화/사용 된 `m_bstrLanguage` 필드입니다.

FIF_MODULE 초기화/사용 된 `m_bstrModule` 필드입니다.

FIF_STACKRANGE 초기화/사용 된 `m_addrMin` 및 `m_addrMax` (스택 범위) 필드입니다.

FIF_FRAME 초기화/사용 된 `m_pFrame` 필드입니다.

FIF_DEBUGINFO 초기화/사용 된 `m_fHasDebugInfo` 필드입니다.

FIF_STALECODE 초기화/사용 된 `m_fStaleCode` 필드입니다.

FIF_ANNOTATEDFRAME 초기화/사용 된 `m_fAnnotatedFrame` 필드입니다.

FIF_DEBUG_MODULEP 초기화/사용 된 `m_pModule` 필드입니다.

FIF_FUNCNAME_FORMAT 함수 이름의 표시 형식을 지정 합니다. 결과에 반환 됩니다는 `m_bstrFunName` 필드 및 기타 필드가 채워집니다.

FIF_FUNCNAME_RETURNTYPE 반환 형식이 추가 된 `m_bstrFuncName` 필드입니다.

FIF_FUNCNAME_ARGS 추가 대 한 인수는 `m_bstrFuncName` 필드입니다.

FIF_FUNCNAME_LANGUAGE 추가 언어는 `m_bstrFuncName` 필드입니다.

모듈 이름을 추가 하는 FIF_FUNCNAME_MODULE는 `m_bstrFuncName` 필드입니다.

줄 번호를 추가 하는 FIF_FUNCNAME_LINES는 `m_bstrFuncName` 필드입니다.

FIF_FUNCNAME_OFFSET에 추가 합니다 `m_bstrFuncName` 줄의 시작 부분에서 바이트 오프셋 필드 `FIF_FUNCNAME_LINES` 지정 됩니다. 경우 `FIF_FUNCNAME_LINES` 지정 하지 않으면 줄 번호를 사용할 수 없는 경우 추가 오프셋 (바이트)를 함수 시작 지점에서 또는 합니다.

각 함수 인수의 유형을 추가 하는 FIF_FUNCNAME_ARGS_TYPES는 `m_bstrFuncName` 필드입니다.

각 함수 인수의 이름을 추가 하는 FIF_FUNCNAME_ARGS_NAMES는 `m_bstrFuncName` 필드입니다.

각 함수 인수의 값을 추가 하는 FIF_FUNCNAME_ARGS_VALUES는 `m_bstrFuncName` 필드입니다.

FIF_FUNCNAME_ARGS_ALL 추가 유형, 이름 및 값에 대 한 모든 인수는 `m_bstrFuncName` 필드입니다.

FIF_ARGS_TYPES 인수 형식이 검색 되 고 형식이 지정 됩니다.

FIF_ARGS_NAMES 인수 이름이 검색 되 고 형식이 지정 됩니다.

인수 값 FIF_ARGS_VALUES 검색 되 고 형식이 지정 됩니다.

FIF_ARGS_ALL 검색 및 형식 유형, 이름 및 모든 인수의 값입니다.

서식을 지정할 인수는 FIF_ARGS_NOFORMAT 지정 (예를 들어 하지 열기 및 닫기 괄호로 인수 목록에 추가 하지 수 없는 인수 사이의 구분 기호를 추가).

함수 (속성) 계산 FIF_ARGS_NO_FUNC_EVAL 지정 해서는 안 인수 값을 검색 하는 경우.

디버그 엔진 FIF_FILTER_NON_USER_CODE 포함 되지 않으므로 사용자 코드가 아닌 프레임을 필터링 하는 것입니다.

허용 안 함 FIF_ARGS_NO_TOSTRING `ToString()` 함수 평가 또는 함수 인수를 반환할 때 서식 지정 합니다.

호스팅 프로세스를 사용 하지 않고 호스팅된 응용 프로그램 도메인에서 FIF_DESIGN_TIME_EXPR_EVAL 프레임 정보를 얻을 수 해야 합니다.

## <a name="remarks"></a>설명
이러한 플래그에 전달 되는 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) 및 [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md) 에 초기화할 필드를 나타내려면 메서드를 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 구조체 또는 구조체입니다.

이러한 플래그는의 필드를 나타내는 데 또한 합니다 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) 구조는 유효 하 고 사용 되는 반환 하는 경우. 이러한 값을 비트 결합할 수 있습니다 `OR`합니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)

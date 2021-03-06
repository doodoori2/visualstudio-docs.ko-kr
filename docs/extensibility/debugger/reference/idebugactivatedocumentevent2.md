---
title: IDebugActivateDocumentEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugActivateDocumentEvent2
helpviewer_keywords:
- IDebugActivateDocumentEvent2 interface
ms.assetid: 6f37edd7-a48c-4b41-b160-dff9be63a284
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd113dec63d98e54e72cc68c333d009db4e35a04
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56677841"
---
# <a name="idebugactivatedocumentevent2"></a>IDebugActivateDocumentEvent2
로드할 문서를 요청 하려면이 인터페이스를 사용 하는 디버그 엔진 (DE) 합니다.

## <a name="syntax"></a>구문

```
IDebugActivateDocumentEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 DE 소스 파일을 열 수 해야 하는 경우이 인터페이스를 구현 합니다. 이 인터페이스를 사용 하거나 스크립트 인터프리터의 일부인 디버그 엔진에 의해서만 구현 됩니다. [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 이 인터페이스와 동일한 개체에서 인터페이스를 구현 해야 (SDM 사용 [QueryInterface](/cpp/atl/queryinterface) 액세스 하는 `IDebugEvent2` 인터페이스).

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 DE 만들고 소스 파일을 연 해야 할 경우이 이벤트 개체를 전송 합니다. 이벤트를 사용 하 여 전송 되는 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) SDM를 디버깅 중인 프로그램에 연결할 때 제공한 콜백 함수.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugActivateDocumentEvent2`합니다.

|메서드|설명|
|-------------|-----------------|
|[GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)|활성화 하려면 문서를 가져옵니다.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)|문서 내의 위치를 설명 하는 문서 컨텍스트를 가져옵니다.|

## <a name="remarks"></a>설명
 이 인터페이스 사용 되는 일반적인 시나리오는은 구문 분석 오류를 사용 하 여 문서를 표시할 수 있도록 DE 스크립트의 SDM을이 인터페이스 보내는 HTML 페이지의 스크립트 코드에서 구문 분석 오류가 발생 하는 경우입니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고 항목
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
---
title: IDiaStackWalkFrame | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
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
- IDiaStackWalkFrame interface
ms.assetid: 42d82845-d6f6-4846-9ecd-9dd169216077
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a047b1a75cb511332bf9382d19fe274eb731069
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790372"
---
# <a name="idiastackwalkframe"></a>IDiaStackWalkFrame
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

호출 사이의 스택 컨텍스트를 유지 관리 합니다 [idiaframedata:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) 메서드.  
  
## <a name="syntax"></a>구문  
  
```  
IDiaStackWalkFrame : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
 다음 표에서의 메서드를 보여 줍니다. `IDiaStackWalkFrame`합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[IDiaStackWalkFrame::get_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-get-registervalue.md)|레지스터의 값을 검색 합니다.|  
|[IDiaStackWalkFrame::put_registerValue](../../debugger/debug-interface-access/idiastackwalkframe-put-registervalue.md)|레지스터의 값을 설정 합니다.|  
|[IDiaStackWalkFrame::readMemory](../../debugger/debug-interface-access/idiastackwalkframe-readmemory.md)|이미지에서 메모리를 읽습니다.|  
|[IDiaStackWalkFrame::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddress.md)|가장 가까운 함수 반환 주소를 지정한 스택 프레임을 검색합니다.|  
|[IDiaStackWalkFrame::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkframe-searchforreturnaddressstart.md)|지정한 스택 프레임이 나 지정된 된 주소 반환 주소를 검색합니다.|  
  
## <a name="remarks"></a>설명  
 이 인터페이스는 읽기 및 등록 뿐만 아니라 메모리에 액세스 쓰고 반환 주소를 확인 프로그램 실행 중 사용 됩니다.  
  
## <a name="notes-for-callers"></a>호출자에 대 한 정보  
 이 인터페이스를 구현 하 고 인터페이스의 인스턴스를 전달 하는 클라이언트 응용 프로그램을 [idiaframedata:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) 메서드. 이 인터페이스의 동일한 인스턴스에 나중에 다시 호출 될 때마다 레지스터의 상태를 유지 관리 되는 `execute` 메서드. `execute` 또한 메서드 반환 주소를 확인 하려면이 인터페이스를 사용 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: Dia2.h  
  
 라이브러리: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>참고 항목  
 [인터페이스 (디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md)




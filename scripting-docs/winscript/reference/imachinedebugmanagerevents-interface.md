---
title: IMachineDebugManagerEvents 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerEvents interface
ms.assetid: 468de2f4-49e0-4f6f-ba0c-0f5f6832c092
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9aab3d7abeecd22e830c68f174896df0e7df2da
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344036"
---
# <a name="imachinedebugmanagerevents-interface"></a>IMachineDebugManagerEvents 인터페이스
컴퓨터 디버그 관리자에서 관리하는 실행 중인 애플리케이션 목록의 변경을 알립니다. 이 인터페이스 응용 프로그램의 동적 목록을 표시 하려면 디버거 IDE 통해 사용할 수 있습니다.  
  
 상속 된 메서드 외에도 `IUnknown`, `IMachineDebugManagerEvents` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IMachineDebugManagerEvents::onAddApplication](../../winscript/reference/imachinedebugmanagerevents-onaddapplication.md)|응용 프로그램 실행에 추가 되 면 이벤트를 처리 응용 프로그램 목록입니다.|  
|[IMachineDebugManagerEvents::onRemoveApplication](../../winscript/reference/imachinedebugmanagerevents-onremoveapplication.md)|응용 프로그램 실행에서 제거 되 면 이벤트를 처리 응용 프로그램 목록입니다.|
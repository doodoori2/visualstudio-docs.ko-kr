---
title: IActiveScriptWinRTErrorDebug 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug Interface
ms.assetid: 58b45096-633f-479f-95c4-8eae7376d3a1
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2355b9aa38abbed2ca66964a07bb47082eb76c32
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346503"
---
# <a name="iactivescriptwinrterrordebug-interface"></a>IActiveScriptWinRTErrorDebug 인터페이스
확장 된 Windows 런타임 오류 정보를 제공 하기 위해 JavaScript 엔진에 의해 구현 된 [BREAKREASON 열거형](../../winscript/reference/breakreason-enumeration.md) 이벤트입니다. 가져오려는 QueryInterface를 수행할 수 있습니다는 [IActiveScriptError](../../winscript/reference/iactivescripterror.md) 개체입니다.  
  
> [!IMPORTANT]
>  이 인터페이스는 PDM v11.0 이상에 의해 구현됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="methods"></a>메서드  
 `IActiveScriptWinRTErrorDebug` 인터페이스는 다음 메서드를 노출합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptWinRTErrorDebug::GetCapabilitySid](../../winscript/reference/iactivescriptwinrterrordebug-getcapabilitysid.md)|사용 가능한 경우 Windows 런타임 오류에 대 한 기능 SID를 반환 합니다.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorReference](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorreference.md)|사용 가능한 경우 오류 참조 문자열을 제한 하는 Windows 런타임에서 반환 합니다.|  
|[IActiveScriptWinRTErrorDebug::GetRestrictedErrorString](../../winscript/reference/iactivescriptwinrterrordebug-getrestrictederrorstring.md)|사용 가능한 경우 오류 문자열을 제한 하는 Windows 런타임에서 반환 합니다.|
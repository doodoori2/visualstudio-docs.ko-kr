---
title: AddMessage | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 28f9150c55c7475a9412ee440cd8ae5215ca25cb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788955"
---
# <a name="addmessage"></a>AddMessage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

그래픽 진단에 사용자 지정 메시지를 추가 *HUD* (Head-up Display).  
  
## <a name="syntax"></a>구문  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `szMessage`  
 HUD에 추가할 메시지입니다.  
  
## <a name="remarks"></a>설명  
 그래픽 진단 HUD가 그래픽 진단에서 실행 중인 앱의 왼쪽 위에 표시됩니다. 여기에는 앱 및 그래픽 정보 캡처에 대한 정보, 이 함수를 호출하여 추가되는 메시지가 표시됩니다.  
  
 HUD에 메시지를 추가 하려면 그래픽 정보를 캡처하지 않아도 필요가-즉, 인스턴스를 통해 메시지를 추가할 수 있습니다는 `VsgDbg` 클래스 이지만 [Init](../debugger/init.md) 멤버 함수가 먼저 호출 되지는지 않습니다. 메시지는 HUD에만 표시되고 그래픽 로그 파일에는 기록되지 않습니다.




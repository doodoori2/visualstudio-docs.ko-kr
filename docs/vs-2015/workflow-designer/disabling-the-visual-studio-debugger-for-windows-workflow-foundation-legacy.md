---
title: Visual Studio Debugger for Windows Workflow Foundation (레거시)를 사용 하지 않도록 설정 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 9fd51e47ff92e231507e56bb3eacad212a47c90d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47554864"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Visual Studio Debugger for Windows Workflow Foundation을 사용하지 않도록 설정(레거시)
이 항목에서는 레거시 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 [!INCLUDE[wf](../includes/wf-md.md)] 응용 프로그램을 빌드할 때 구성 파일을 사용하여 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 디버거를 비활성화하는 방법에 대해 설명합니다. 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.  
  
 기본적으로는 호스트 프로세스에 [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)]용 [!INCLUDE[wf](../includes/wf-md.md)] 디버거를 사용할 수 있습니다. 워크플로 디버깅을 사용 하지 않으려면 명시적으로 해제 해야 하는 "DisableWorkflowDebugging" 항목을 추가 하 여  **\<스위치 >** 요소에는  **\<system.diagnostics >** 호스트 구성 파일의 섹션입니다.  
  
 다음 예제에서는 워크플로 디버깅을 사용하지 않도록 호스트 구성 파일을 수정하는 방법을 보여 줍니다.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="DisableWorkflowDebugging" value="true"/>  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio Debugger for Windows Workflow Foundation (레거시)를 호출합니다.](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [레거시 워크플로 디버깅](../workflow-designer/debugging-legacy-workflows.md)
---
title: '방법: 편집기에서 포커스를 잃을 때 이벤트를 발생 시키는 | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2875ff13302b1f54d87f1f69a68757b10fb98dca
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749231"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>방법: 편집기에서 포커스를 잃을 때 이벤트 발생
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

경우에 따라 편집기 창 프레임에 포커스를 잃을 때 알아야 합니다. 예를 들어, 편집기에서 포커스를 잃을 후 코드 창에서 코드를 추출 해야 합니다. 다음 절차는 포커스를 잃는 편집기에 대 한 알림을 수신 하는 단계를 제공 합니다.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>포커스를 잃는 편집기에 대 한 응답에서 이벤트를 발생 시키는  
  
1.  확보 하 여 선택 이벤트를 모니터링 합니다.는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> 에서 개체 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>합니다.  
  
2.  호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> 제공 하면 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> 개체입니다.  
  
3.  호출에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A>를 검색할 `elementid==SEID_WindowFrame`합니다.  
  
4.  테스트는 `varValueNew` 두 가지에 대 한 매개 변수:  
  
    1.  찾고자 하는 창 프레임입니다.  
  
    2.  프로그램의 선택 영역 창 프레임을 손실는 점입니다.


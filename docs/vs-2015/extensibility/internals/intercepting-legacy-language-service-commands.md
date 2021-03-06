---
title: 레거시 언어 서비스 명령 가로채기 | Microsoft Docs
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
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41d89e2947cbd7bf1087f8dfa0ecffdd75033171
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752991"
---
# <a name="intercepting-legacy-language-service-commands"></a>레거시 언어 서비스 명령 가로채기
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

사용 하 여 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], 텍스트 뷰 처리할 수 있는 언어 서비스 절편 명령 할 수 있습니다. 텍스트 뷰를 관리 하지 않는 언어 관련 동작에 유용 합니다. 언어 서비스에서 하나 이상의 명령 필터 텍스트 보기에 추가 하 여 이러한 명령을 가로챌 수 있습니다.  
  
## <a name="getting-and-routing-the-command"></a>가져오기 및 명령 라우팅  
 명령 필터는는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 특정 문자 시퀀스 또는 키 명령을 모니터링 하는 개체입니다. 단일 텍스트 뷰를 사용 하 여 명령 필터가 여러 개 연결할 수 있습니다. 각 텍스트 보기의 명령 체인 필터를 유지 관리합니다. 새 명령 필터를 만든 후 적절 한 텍스트 보기에 대 한 체인에 필터를 추가 합니다.  
  
 호출을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 메서드는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 명령 필터 체인에 추가할. 호출 하는 경우 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 명령 필터 처리 하지 않는 명령을 전달할 수 있습니다 하는 다른 명령 필터를 반환 합니다.  
  
 명령 처리에 대 한 다음과 같은 옵션이 있습니다.  
  
- 명령을 처리 하 고 체인의 다음 명령 필터에 명령을 전달 합니다.  
  
- 명령을 처리 하 고 명령 필터에 명령을 전달 하지 마십시오.  
  
- 명령을 처리 하지 않습니다 하지만 다음 명령은 필터에는 명령을 전달 합니다.  
  
- 이 명령은 무시 됩니다. 현재 필터에서 처리 하지 않습니다 하 고 필터에 전달 하지 마세요.  
  
  언어 서비스는 명령에 대 한 처리 하는 정보를 참조 하세요 [언어 서비스 필터에 대 한 중요 명령](../../extensibility/internals/important-commands-for-language-service-filters.md)입니다.


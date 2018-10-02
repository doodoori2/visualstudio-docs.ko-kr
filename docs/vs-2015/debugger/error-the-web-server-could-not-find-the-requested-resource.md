---
title: '오류: 웹 서버를 찾을 수 없습니다 요청된 된 리소스 | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 1ceeaf30-918c-42bb-ace1-96944530fef3
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc41673da6157306cd0e4e66070717d5745d6218
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47542771"
---
# <a name="error-the-web-server-could-not-find-the-requested-resource"></a>오류: 요청한 리소스를 웹 서버에서 찾지 못했습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [오류: 웹 서버에 요청 된 리소스를 찾을 수 없습니다.](https://docs.microsoft.com/visualstudio/debugger/error-the-web-server-could-not-find-the-requested-resource)합니다.  
  
보안 고려 사항 때문에 IIS에서 일반 오류를 반환했습니다.  
  
 한 가지 가능한 원인은 서버의 보안 구성입니다. IIS 6.0 및 이전 버전에서는 URLScan이라는 추가 기능 프로그램을 사용하여 형식이 잘못된 의심스러운 요청을 필터링합니다. IIS 7.0에서는 동일한 목적을 위해 요청 필터링이 기본적으로 제공됩니다. 두 경우 모두 요청 필터링이 지나치게 제한적이면 Visual Studio에서 서버를 디버깅하지 못할 수 있습니다.  
  
 이 오류의 가능한 원인은 매우 다양합니다. 가장 일반적인 원인 중 몇 가지는 IIS 설치 또는 구성 문제, 웹 사이트 구성 문제 또는 파일 시스템의 사용 권한 문제입니다. 브라우저를 사용하여 리소스에 액세스할 수 있습니다. IIS가 구성된 방식에 따라 자세한 오류 메시지를 얻으려면 서버에서 로컬 브라우저를 사용하거나 IIS 오류 로그를 검사해야 할 수 있습니다.  
  
 IIS 문제 해결에 대 한 자세한 내용은 참조 하세요. [IIS Management and Administration](http://go.microsoft.com/fwlink/?LinkId=255872)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [UrlScan 보안 도구](http://www.microsoft.com/technet/security/tools/urlscan.mspx)   
 [오류: 웹 서버가 잠겨 있기 때문에 디버깅을 사용하기 위해 필요한 DEBUG 동사를 사용할 수 없습니다.](../debugger/error-the-web-server-has-been-locked-down-and-is-blocking-the-debug-verb.md)



---
title: 코드 조각 문제 해결 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a6cc8cde833d9580e3fae03df2df11e87eed8cf2
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47555655"
---
# <a name="troubleshooting-snippets"></a>코드 조각 문제 해결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [코드 조각 문제 해결](https://docs.microsoft.com/visualstudio/ide/troubleshooting-snippets)합니다.  
  
IntelliSense 코드 조각 문제는 코드 조각 파일이 손상되었거나 코드 조각 파일에 잘못된 내용이 있는 등 일반적으로 두 가지 문제로 인해 발생합니다.  
  
## <a name="common-problems"></a>일반적인 문제  
  
### <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>코드 조각은 파일 탐색기에서 Visual Studio 원본 파일로 끌어올 수 없습니다.  
  
-   코드 조각 파일의 XML은 손상되었을 수 있습니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 **XML 편집기**는 XML 구조에서 문제를 찾을 수 있습니다.  
  
-   코드 조각 파일은 코드 조각 스키마를 준수하지 않을 수 있습니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 **XML 편집기**는 XML 구조에서 문제를 찾을 수 있습니다.  
  
### <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>코드에는 강조 표시되지 않는 컴파일러 오류가 있습니다.  
  
-   프로젝트 참조를 누락했을 수 있습니다. 코드 조각에 대한 설명서를 검토합니다. 참조가 컴퓨터에 없는 경우 설치해야 합니다. 코드 조각을 삽입하려면 필요한 참조를 프로젝트에 추가해야 합니다. 코드 조각이 참조 정보를 누락한 경우 코드 조각 생성자에 오류로 보고될 수 있습니다.  
  
-   변수는 정의되지 않을 수 있습니다. 코드 조각에서 정의되지 않은 변수는 강조 표시해야 합니다. 그렇지 않으면 코드 조각 작성자에 오류로 보고될 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [코드 조각](../ide/code-snippets.md)



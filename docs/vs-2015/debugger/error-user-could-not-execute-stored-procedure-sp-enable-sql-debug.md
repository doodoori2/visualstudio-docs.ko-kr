---
title: '오류: 사용자 수 있습니다 하지 실행할 저장 프로시저 sp_enable_sql_debug | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.sqlde_accessdenied
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 11957495-c238-4cc5-8937-e4026f5e10e1
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9f7d30a64b96d88df9ac25c97276880a5839804
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789813"
---
# <a name="error-user-could-not-execute-stored-procedure-spenablesqldebug"></a>오류: 사용자는 sp_enable_sql_debug 저장 프로시저를 실행할 수 없습니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

저장 프로시저 sp_enable_sql_debug를 서버에서 실행할 수 없는 경우입니다. 이 오류의 원인은 다음과 같습니다.  
  
- 연결에 문제가 있는 경우입니다. 서버에 안정적으로 연결되어 있어야 합니다.  
  
- 서버에 대해 필요한 권한이 없는 경우입니다. SQL Server 2005에서 디버깅하려면 Visual Studio를 실행하는 데 사용되는 계정과 SQL Server에 연결하는 데 사용되는 계정이 모두 sysadmin 역할의 멤버여야 합니다. SQL Server에 연결하는 데 사용한 계정이 Windows 사용자 계정(Windows 인증을 사용하는 경우)이거나 사용자 ID와 암호로 지정된 계정(SQL 인증을 사용하는 경우)입니다.  
  
  자세한 내용은 [방법: 디버깅에 대 한 SQL Server 권한 설정](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [방법: 디버깅을 위해 SQL Server 사용 권한 설정](http://msdn.microsoft.com/en-us/84e088d0-0409-41d4-841b-f5d4b0fda414)   
 [SQL 디버깅 설정](http://msdn.microsoft.com/en-us/3db09e68-edcc-42de-9c22-4e97cfd55ab3)




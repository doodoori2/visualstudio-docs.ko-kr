---
title: ClickOnce 응용 프로그램 보안 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce security
- ClickOnce deployment, security
- deploying applications, ClickOnce security
ms.assetid: a05b5f2f-d1f2-471a-8096-8b11f7554265
caps.latest.revision: 47
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 247ebd5a68f4bb3936d9b67779f7d67d0a1ccf85
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47564832"
---
# <a name="securing-clickonce-applications"></a>ClickOnce 응용 프로그램 보안
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [ClickOnce 응용 프로그램 보안](https://docs.microsoft.com/visualstudio/deployment/securing-clickonce-applications)합니다.  
  
[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램에서는 .NET Framework의 코드 액세스 보안 제한에 따라 보호된 리소스 및 작업에 대한 코드의 액세스를 제한합니다. 따라서 코드 액세스 보안의 의미를 이해하여 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램을 적절하게 작성해야 합니다. 응용 프로그램에서는 완전 신뢰 영역이나 부분 신뢰 영역(예: 인터넷 및 인트라넷 영역)을 사용하여 액세스를 제한할 수 있습니다.  
  
 또한 ClickOnce에서는 인증서를 사용하여 응용 프로그램 게시자의 신뢰성을 확인하고 응용 프로그램 및 배포 매니페스트에 서명하여 파일이 훼손되지 않았음을 증명합니다. 서명은 매니페스트를 생성한 후 응용 프로그램 파일을 쉽게 변경할 수 있게 해주는 선택적인 단계입니다. 하지만 서명된 매니페스트가 없으면 응용 프로그램 설치 관리자가 중간자 개입 보안 공격에 의해 손상되지 않았는지 보증하기 어렵습니다. 따라서 응용 프로그램 보안을 위해서는 응용 프로그램 및 개발 매니페스트를 서명하는 것이 좋습니다.  
  
## <a name="zones"></a>영역  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 기술을 사용하여 배포되는 응용 프로그램은 보안 영역에 정의된 권한과 작업 집합으로 제한됩니다. 보안 영역은 Internet Explorer에서 정의하며 응용 프로그램 위치를 기준으로 합니다. 다음 표는 배포 위치에 따른 기본 사용 권한을 보여 줍니다.  
  
|배포 위치|보안 영역|  
|-------------------------|-------------------|  
|웹에서 실행|인터넷 영역|  
|웹에서 설치|인터넷 영역|  
|네트워크 파일 공유에서 설치|로컬 인트라넷 영역|  
|CD-ROM에서 설치|Full Trust|  
  
 기본 사용 권한은 응용 프로그램의 원래 버전이 배포된 위치를 기반으로 하며, 응용 프로그램 업데이트 시 해당 사용 권한이 상속됩니다. 응용 프로그램이 웹 또는 네트워크 위치에서 업데이트를 확인하도록 구성되어 있고 최신 버전이 사용 가능하면 원래 설치된 버전에서 완전 신뢰 권한 대신 인터넷 또는 인트라넷 영역에 대한 사용 권한을 받을 수 있습니다. 시스템 관리자가 특정 응용 프로그램 게시자를 신뢰할 수 있는 소스로 정의하는 ClickOnce 배포 정책을 지정하여 해당 메시지가 표시되지 않게 할 수도 있습니다. 이 정책이 배포되는 컴퓨터의 경우 사용 권한이 자동으로 부여되므로 사용자에게 관련 메시지가 표시되지 않습니다. 자세한 내용은 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)을 참조하십시오. 신뢰할 수 있는 응용 프로그램 배포를 구성하기 위해 인증서를 컴퓨터 또는 엔터프라이즈 수준에 설치할 수 있습니다. 자세한 내용은 [방법: ClickOnce 응용 프로그램의 클라이언트 컴퓨터에 트러스트된 게시자 추가](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)을 참조하십시오.  
  
## <a name="code-access-security-policies"></a>코드 액세스 보안 정책  
 응용 프로그램에 대 한 사용 권한이 설정에 따라 결정 됩니다 합니다 [ \<trustInfo > 요소](../deployment/trustinfo-element-clickonce-application.md) 응용 프로그램 매니페스트 요소입니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로젝트의 설정에 따라이 정보를 자동 생성 **보안** 속성 페이지. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램에 요청 하는 특정 권한만 부여 됩니다. 예를 들어, 파일에 액세스하는 데 완전 신뢰 권한이 필요할 때 응용 프로그램에서 파일 액세스 권한을 요청하면 완전 신뢰 권한이 아니라 파일 액세스 권한만 부여됩니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램을 개발할 때, 응용 프로그램에서 필요한 특정 권한만 요청해야 합니다. 대부분의 경우, 인터넷 또는 로컬 인트라넷 영역을 사용하여 응용 프로그램을 부분 신뢰로 제한할 수 있습니다. 자세한 내용은 [방법: ClickOnce 응용 프로그램의 보안 영역 설정](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)을 참조하십시오. 응용 프로그램에 사용자 지정 권한이 필요한 경우 사용자 지정 영역을 만들 수 있습니다. 자세한 내용은 [방법: ClickOnce 응용 프로그램에 대한 사용자 지정 권한 설정](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)을 참조하세요.  
  
 응용 프로그램이 배포되는 영역의 기본 권한 집합에 속하지 않는 권한을 포함하면 설치 또는 업데이트 시 권한을 부여하라는 메시지가 나타납니다. 시스템 관리자가 특정 응용 프로그램 게시자를 신뢰할 수 있는 소스로 정의하는 ClickOnce 배포 정책을 지정하여 해당 메시지가 표시되지 않게 할 수도 있습니다. 이 정책이 배포되는 컴퓨터에서는 사용 권한이 자동으로 부여되므로 사용자에게 관련 메시지가 표시되지 않습니다.  
  
 개발자는 적절한 사용 권한으로 응용 프로그램이 실행되도록 해야 합니다. 응용 프로그램이 런타임에 영역 외부에서 권한을 요청하는 경우 보안 예외가 발생할 수 있습니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 대상 보안 영역에서 응용 프로그램을 디버깅할 수 있습니다. 또한, 보안 응용 프로그램 개발에 대한 도움말을 제공 합니다. 자세한 내용은 [방법: 제한된 권한으로 ClickOnce 응용 프로그램 디버그](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)을 참조하세요.  
  
 코드 액세스 보안 및 ClickOnce에 대한 자세한 내용은 [Code Access Security for ClickOnce Applications](../deployment/code-access-security-for-clickonce-applications.md)을(를) 참조하세요.  
  
## <a name="code-signing-certificates"></a>코드 서명 인증서  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포를 사용하여 응용 프로그램을 게시하려면 공개/전용 키 쌍을 사용하여 응용 프로그램과 해당 응용 프로그램의 배포 매니페스트에 서명합니다. 매니페스트에 서명하는 도구는 **프로젝트 디자이너** 의 **서명**페이지에서 사용할 수 있습니다. 자세한 내용은 [Signing Page, Project Designer](../ide/reference/signing-page-project-designer.md)을 참조하십시오. 또는 게시 마법사를 사용하여 게시 프로세스 동안 키 파일로 매니페스트를 서명할 수 있습니다.  
  
 매니페스트에 서명한 후에는 설치 시 Authenticode 서명 기반의 게시자 정보가 권한 대화 상자에 표시되어 응용 프로그램의 출처를 신뢰할 수 있음을 보여 줍니다.  
  
 ClickOnce 및 인증서에 대한 자세한 내용은 [ClickOnce and Authenticode](../deployment/clickonce-and-authenticode.md)을(를) 참조하세요.  
  
## <a name="aspnet-form-based-authentication"></a>ASP.NET 폼 기반 인증  
 각 사용자가 액세스할 수 있는 배포를 제어하려면 웹 서버에 배포된 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램에 익명 액세스를 허용하지 마십시오. 대신 Windows 인증을 사용하여 사용자 ID를 기반으로 사용자가 설치한 배포에 대한 사용자 액세스를 허용합니다.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]에서는 영구 쿠키를 사용하므로 ASP.NET 폼 기반 인증을 지원하지 않습니다. 영구 쿠키는 Internet Explorer 캐시에 위치하여 해킹 가능하므로 보안 위험이 존재합니다. 따라서 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램을 배포할 경우 Windows 인증 이외의 인증 시나리오는 지원되지 않습니다.  
  
## <a name="passing-arguments"></a>인수 전달  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램에 인수를 전달해야 하는 경우 보안과 관련하여 몇 가지 사항을 더 고려해야 합니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 개발자가 웹을 통해 배포 된 응용 프로그램 쿼리 문자열을 제공할 수 있습니다. 쿼리 문자열은 일련의 이름/값 쌍 형식으로서, 다음과 같이 응용 프로그램을 시작하는 데 사용되는 URL의 끝에 붙습니다.  
  
 `http://servername.adatum.com/WindowsApp1.application?username=joeuser`  
  
 기본적으로 쿼리 문자열 인수는 사용할 수 없습니다. 쿼리 문자열을 사용하려면 응용 프로그램 배포 매니페스트에서 `trustUrlParameters` 특성을 설정해야 합니다. 이 값은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 및 MageUI.exe에서 설정할 수 있습니다. 전달을 사용 하도록 설정 하는 방법에 대 한 자세한 내용은 쿼리 문자열 [방법: 온라인 ClickOnce 응용 프로그램에서 쿼리 문자열 정보 검색](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)합니다.  
  
 쿼리 문자열을 통해 검색된 인수를 안전성을 확인하지 않고 데이터베이스나 명령줄에 직접 전달하면 안 됩니다. 안전하지 않은 인수는 데이터베이스 또는 명령줄 이스케이프 문자가 들어 있는 인수입니다. 이러한 문자가 있으면 악의적인 사용자가 응용 프로그램을 조작하여 임의의 명령을 실행할 수 있게 됩니다.  
  
> [!NOTE]
>  쿼리 문자열 인수는 시작할 때 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램에 인수를 전달할 수 있는 유일한 방법입니다. 인수를 전달할 수 없습니다는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 명령줄에서 응용 프로그램입니다.  
  
## <a name="deploying-obfuscated-assemblies"></a>난독 처리된 어셈블리 배포  
 Dotfuscator를 통해 응용 프로그램을 난독 처리하여 다른 사용자가 코드를 리버스 엔지니어링하지 못하도록 할 수 있습니다. 그러나 어셈블리 난독 처리는 Visual Studio IDE 또는 ClickOnce 배포 프로세스에 통합되지 않습니다. 따라서 빌드 후 단계 등을 통해 배포 프로세스 외부에서 난독 처리를 수행해야 합니다. 프로젝트를 빌드한 후 Visual Studio 외부에서 다음 단계를 직접 수행합니다.  
  
1.  Dotfuscator를 사용하여 난독 처리를 수행합니다.  
  
2.  Mage.exe나 MageUI.exe를 사용하여 ClickOnce 매니페스트를 생성하고 서명합니다. 자세한 내용은 [Mage.exe (매니페스트 생성 및 편집 도구)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1) 하 고 [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](http://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)합니다.  
  
3.  배포 소스 위치(웹 서버, UNC 공유 또는 CD-ROM)에 파일을 직접 복사하여 게시합니다.  
  
## <a name="see-also"></a>참고 항목  
 [ClickOnce 보안 및 배포](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce 배포 전략 선택](../deployment/choosing-a-clickonce-deployment-strategy.md)



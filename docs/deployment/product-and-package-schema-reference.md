---
title: 제품 및 패키지 스키마 참조 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.CircularIncludes
- MSBuild.ResolveManifestFiles.PublishFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce, product and package files
- Windows Installer, product and package files
- product files [ClickOnce]
- ClickOnce, bootstrapper elements
- package files [Windows Installer]
- product files [Windows Installer]
- package files [ClickOnce]
- Windows Installer, bootstrapper elements
ms.assetid: 5a74878f-b896-4cca-b968-98d00fe78fb0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 489415eba929a73c25b8aea7262c3e930a5d90cd
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598988"
---
# <a name="product-and-package-schema-reference"></a>제품 및 패키지 스키마 참조
A *제품 파일* 에 필요한 외부 종속성의 모든 설명 하는 XML 매니페스트는는 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램입니다. 외부 종속성의 예로 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 및 Microsoft Data Access Components (MDAC). 패키지 파일을 제품 파일과 유사 하지만 지역화 된 어셈블리, 사용권 계약 및 설명서 등의 종속성을의 문화권 종속 구성 요소를 설치 하는 데 사용 됩니다.

 제품 및 패키지 파일 구성 중 최상위 `Product` 또는 `Package` 요소에는 다음 요소가 포함 된 각 합니다.

|요소|설명|특성|
|-------------|-----------------|----------------|
|[\<제품 > 요소](../deployment/product-element-bootstrapper.md)|제품 파일의 최상위 요소가 필요 합니다.|없음|
|[\<패키지 > 요소](../deployment/package-element-bootstrapper.md)|패키지 파일의 최상위 요소가 필요 합니다.|`Culture`<br /><br /> `Name`<br /><br /> `EULA`|
|[\<RelatedProducts > 요소](../deployment/relatedproducts-element-bootstrapper.md)|제품 파일에 대 한 선택적 요소입니다. 다른 제품을이 제품을 설치 또는 변경에 따라 달라 집니다.|없음|
|[\<InstallChecks > 요소](../deployment/installchecks-element-bootstrapper.md)|필수적 요소입니다. 목록 종속성을 설치 하는 동안 로컬 컴퓨터에서 수행 하려면 확인 합니다.|없음|
|[\<명령 > 요소](../deployment/commands-element-bootstrapper.md)|필수적 요소입니다.  에 설명 된 대로 하나 이상의 설치 검사를 실행 `InstallChecks`, 설치할 패키지를 확인 해야은 실패 합니다.|없음|
|[\<PackageFiles > 요소](../deployment/packagefiles-element-bootstrapper.md)|필수적 요소입니다. 이 설치 프로세스에서 설치할 수 있는 패키지를 나열 합니다.|없음|
|[\<문자열 > 요소](../deployment/strings-element-bootstrapper.md)|필수적 요소입니다. 저장소 버전의 제품 이름 및 오류 문자열을 지역화 합니다.|없음|

## <a name="remarks"></a>주의
 패키지 스키마에서 사용 됩니다 *Setup.exe*, 자체의 작은 하드 코드 된 논리를 포함 하는 태스크를 부트스트래핑 MS 빌드에서 생성 되는 스텁 프로그램입니다. 스키마는 설치 프로세스의 모든 측면을 구동합니다.

 `InstallChecks` 테스트는 setup.exe 특정된 패키지의 존재 여부에 대해 수행 해야 합니다. `PackageFiles` 설치 프로세스를 설치 해야 할 수를 지정 된 테스트를 실패 하는 패키지의 모든를 나열 합니다. 명령에서 각 명령은 항목에서 설명 하는 테스트 중 하나를 실행 `InstallChecks`를 지정 하 고 `PackageFile` 실행할 테스트 실패 합니다. 사용할 수는 `Strings` 이진 단일 설치를 사용 하 여 다양 한 언어 응용 프로그램을 설치할 수 있도록 제품 이름 및 오류 메시지를 지역화 하는 요소입니다.

## <a name="example"></a>예제
 다음 코드 예제에는 설치에 대 한 완전 한 제품 파일을 보여 줍니다는 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]합니다.

```xml
<?xml version="1.0" encoding="utf-8" ?>

<Product
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"
  ProductCode="Microsoft.Net.Framework.2.0"
>

    <RelatedProducts>
        <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
    </RelatedProducts>

    <!-- Defines list of files to be copied on build -->
    <PackageFiles>
        <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>
        <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>
        <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>
        <PackageFile Name="dotnetchk.exe"/>
    </PackageFiles>

    <InstallChecks>
        <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />
        <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />
    </InstallChecks>

    <!-- Defines how to invoke the setup for the .NET Framework redist -->
    <!-- TODO: Needs EstrimatedTempSpace, LogFile, and an update of EstimatedDiskSpace -->
    <Commands Reboot="Defer">
        <Command PackageFile="instmsia.exe"
                 Arguments= ' /q /c:"msiinst /delayrebootq"'
                 EstimatedInstallSeconds="20" >
            <InstallConditions>
                <BypassIf Property="VersionNT" Compare="ValueExists"/>
                <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>
            </InstallConditions>
            <ExitCodes>
                <ExitCode Value="0" Result="SuccessReboot"/>
                <ExitCode Value="1641" Result="SuccessReboot"/>
                <ExitCode Value="3010" Result="SuccessReboot"/>
                <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />
            </ExitCodes>
        </Command>
        <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"
                 Arguments= '/quiet /norestart'
                 EstimatedInstallSeconds="20" >
          <InstallConditions>
              <BypassIf Property="Version9x" Compare="ValueExists"/>
              <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>
              <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>
              <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>
          </InstallConditions>
          <ExitCodes>
              <ExitCode Value="0" Result="Success"/>
              <ExitCode Value="1641" Result="SuccessReboot"/>
              <ExitCode Value="3010" Result="SuccessReboot"/>
              <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />
          </ExitCodes>
        </Command>
        <Command PackageFile="dotnetfx.exe"
             Arguments=' /q:a /c:"install /q /l"'
             EstimatedInstalledBytes="21000000"
             EstimatedInstallSeconds="300">

            <!-- These checks determine whether the package is to be installed -->
            <InstallConditions>
                <!-- Either of these properties indicates the .NET Framework is already installed -->
                <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>

                <!-- Block install if user does not have admin privileges -->
                <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>

                <!-- Block install on Windows 95 -->
                <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>

                <!-- Block install on Windows 2000 SP 2 or less -->
                <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>

                <!-- Block install if Internet Explorer 5.01 or greater is not present -->
                <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />
                <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />

                <!-- Block install if the platform is not x86 -->
                <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />
            </InstallConditions>

            <ExitCodes>
                <ExitCode Value="0" Result="Success"/>
                <ExitCode Value="3010" Result="SuccessReboot"/>
                <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>
                <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>
                <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>
                <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>
                <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>
                <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>
                <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />
            </ExitCodes>

        </Command>
    </Commands>
</Product>
```

## <a name="see-also"></a>참고 항목
- [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)
- [ClickOnce 애플리케이션 매니페스트](../deployment/clickonce-application-manifest.md)
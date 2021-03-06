---
title: Start | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df1e76c895102d5a33d66628a7c6436ab604b1ba
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639767"
---
# <a name="start"></a>시작
**Start** 옵션은 지정된 프로파일링 방법으로 프로파일러를 초기화하는 *VSPerfCmd.exe* 옵션입니다.

## <a name="syntax"></a>구문

```cmd
VSPerfCmd.exe /Start:Method /Output:FileName [Options]
```

#### <a name="parameters"></a>매개 변수
 `Method` 다음 키워드 중 하나여야 합니다.

-   **TRACE** - 계측 방법을 지정합니다.

-   **SAMPLE** - 샘플링 방법을 지정합니다.

-   **COVERAGE** - 코드 검사를 지정합니다.

-   **CONCURRENCY** - 리소스 경합 방법을 지정합니다.

## <a name="required-options"></a>필수 옵션
 명령줄에서 **Start**를 지정할 때는 **Output** 옵션을 지정해야 합니다.

 **출력:** `filename` 출력 파일 이름을 지정합니다.

## <a name="exclusive-options"></a>전용 옵션
 다음 옵션은 명령줄에서 **Start** 옵션과 함께 사용해야 합니다.

 **CrossSession**&#124;**CS** 프로세스 간 프로파일링을 활성화합니다. 옵션 이름 **CrossSession** 및 **CS**가 둘 다 지원됩니다.

 **User:**[`domain\`]`username` 클라이언트가 지정한 계정에서 모니터에 액세스할 수 있습니다.

 **WinCounter:** `Path` [**Automark**:`n`] **WinCounter**는 프로파일링 데이터 파일의 표시로 포함할 Windows 성능 카운터를 지정합니다. **AutoMark**는 데이터 파일의 수집 간 간격(밀리초)을 지정합니다.

## <a name="invalid-options"></a>잘못된 옵션
 다음 옵션은 명령줄에서 **Start** 옵션과 함께 사용할 수 없습니다.

 **Status** - **Status**는 프로파일링되는 프로세스에 적용됩니다. 프로세스 및 스레드와 해당 현재 프로필 상태(On/Off) 목록을 표시합니다. 예를 들어 프로세스가 중지되더라도 보고서에서 **Status**에는 해당 상태가 나타나지 않습니다. 즉, **Status**는 프로세스가 프로파일링되었는지 여부를 표시합니다.

 **Shutdown**[**:**`Timeout`] 프로파일러를 해제합니다.

## <a name="example"></a>예제
 다음 예제에서는 *VSPerfCmd.exe* **Start** 옵션을 사용하여 프로파일러를 초기화하는 방법을 보여 줍니다.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp
VSPerfCmd.exe /Launch:TestApp.exe
```

## <a name="see-also"></a>참고 항목
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [독립 실행형 애플리케이션 프로파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [ASP.NET 웹 애플리케이션 프로파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
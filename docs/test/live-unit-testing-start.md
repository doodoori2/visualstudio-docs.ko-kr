---
title: Live Unit Test로 코드를 테스트하는 방법 알아보기
ms.date: 08/31/2017
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio ALM
- Live Unit Testing
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
ms.openlocfilehash: 4676727f70b8065aee34578f563f286bc85bcb25
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55950307"
---
# <a name="get-started-with-live-unit-testing-in-visual-studio"></a>Visual Studio에서 Live Unit Testing 시작

Visual Studio 솔루션에서 Live Unit Testing을 사용하도록 설정하면 Live Unit Testing이 테스트 검사와 테스트 상태를 시각적으로 보여 줍니다. 코드를 수정할 때마다 동적으로 테스트를 실행하고, 변경 내용으로 인해 테스트가 실패하는 경우 즉시 알림을 표시합니다.

.NET Framework 또는 .NET Core를 대상으로 하는 솔루션을 테스트하는 데 Live Unit Testing을 사용할 수 있습니다. 이 자습서에서는 .NET Standard를 대상으로 하는 간단한 클래스 라이브러리를 생성하여 Live Unit Testing을 사용하는 방법을 알아보고 .NET Core를 대상으로 테스트하는 MSTest 프로젝트를 생성합니다.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

전체 C# 솔루션은 GitHub의 [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/csharp/UtilityLibraries/) 리포지토리에서 다운로드할 수 있습니다.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

전체 Visual Basic 솔루션은 GitHub의 [MicrosoftDocs/visualstudio-docs](https://github.com/MicrosoftDocs/visualstudio-docs/tree/master/docs/test/samples/visual-basic/UtilityLibraries/) 리포지토리에서 다운로드할 수 있습니다.

---

## <a name="prerequisites"></a>전제 조건

이 자습서를 사용하려면 .NET Core 2.0 워크로드가 있는 Visual Studio 2017 Enterprise Edition 버전 15.3을 설치해야 합니다.

## <a name="create-the-solution-and-the-class-library-project"></a>솔루션 및 클래스 라이브러리 프로젝트 생성

단일 .NET Standard 클래스 라이브러리 프로젝트 `StringLibrary`로 구성된 `UtilityLibraries`라는 Visual Studio 솔루션을 만들어 시작합니다. C# 또는 Visual Basic으로 `StringLibrary`를 작성할 수 있습니다.

솔루션은 하나 이상의 프로젝트에 대한 컨테이너일 뿐입니다. 솔루션을 만들려면 Visual Studio 2017을 열고 다음을 수행합니다.

1. 최상위 Visual Studio 메뉴에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

1. **새 프로젝트** 대화 상자에서 **기타 프로젝트 형식** 노드를 확장하고 **Visual Studio 솔루션**을 선택합니다. 오른쪽 창의 **빈 솔루션** 템플릿을 선택하고 다음 그림과 같이 **이름** 텍스트 상자에 `UtilityLibraries`를 입력합니다.

   ![**새 프로젝트** 대화 상자](./media/lut-start/new-solution.png)

1. **확인**을 선택하여 솔루션을 만듭니다.

이제 솔루션을 만들었으므로 문자열 작업을 위한 여러 가지 확장 메서드가 포함된 `StringLibrary`라는 클래스 라이브러리를 만듭니다.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. **솔루션 탐색기**에서 `UtilityLibraries` 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 선택합니다.

1. **새 프로젝트 추가** 대화 상자에서 C# 노드를 선택한 후 **.NET Standard**를 선택합니다.

   > [!NOTE]
   > 라이브러리는 특정 .NET 구현보다는 .NET Standard를 대상으로 하므로 해당 버전의 .NET Standard를 지원하는 모든 .NET 구현에서 호출할 수 있습니다. 자세한 내용은 [.NET 표준](/dotnet/standard/net-standard)을 참조하세요.

1. 오른쪽 창의 **클래스 라이브러리(.NET Standard)** 템플릿을 선택하고 다음 그림과 같이 **이름** 텍스트 상자에 `StringLibrary`를 입력합니다.

   ![**새 프로젝트 추가** 대화 상자](./media/lut-start/add-project-cs.png)

1. **확인**을 선택하여 프로젝트를 만듭니다.

1. 코드 창에서 모든 기존 코드를 다음 코드로 바꿉니다.

   [!code-csharp[StringLibrary source code](samples/csharp/utilitylibraries/stringlibrary/class1.cs)]

   `StringLibrary`에는 세 가지 정적 메서드가 있습니다.

      - `StartsWithUpper`는 문자열이 대문자로 시작하는 경우 `true`를 반환하고 그렇지 않은 경우 `false`를 반환합니다.

      - `StartsWithLower`는 문자열이 소문자로 시작하는 경우 `true`를 반환하고 그렇지 않은 경우 `false`를 반환합니다.

      - `HasEmbeddedSpaces`는 문자열에 포함된 공백 문자가 있는 경우 `true`를 반환하고 그렇지 않은 경우 `false`를 반환합니다.

1. 최상위 Visual Studio 메뉴에서 **빌드** > **솔루션 빌드**를 선택합니다. Visual Studio에서 라이브러리가 성공적으로 빌드됩니다.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. **솔루션 탐색기**에서 `UtilityLibraries` 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 선택합니다.

1. **새 프로젝트 추가** 대화 상자에서 Visual Basic 노드를 선택한 후 **.NET Standard**를 선택합니다.

   > [!NOTE]
   > 라이브러리는 특정 .NET 구현보다는 .NET Standard를 대상으로 하므로 해당 버전의 .NET Standard를 지원하는 모든 .NET 구현에서 호출할 수 있습니다. 자세한 내용은 [.NET 표준](/dotnet/standard/net-standard)을 참조하세요.

1. 오른쪽 창의 **클래스 라이브러리(.NET Standard)** 템플릿을 선택하고 다음 그림과 같이 **이름** 텍스트 상자에 `StringLibrary`를 입력합니다.

   ![**새 프로젝트 추가** 대화 상자](./media/lut-start/add-project-vb.png)

1. **확인**을 선택하여 프로젝트를 만듭니다.

1. 코드 창에서 모든 기존 코드를 다음 코드로 바꿉니다.

   [!code-vb[StringLibrary source code](samples/visual-basic/utilitylibraries/stringlibrary/class1.vb)]

   `StringLibrary`에는 세 가지 정적 메서드가 있습니다.

      - `StartsWithUpper`는 문자열이 대문자로 시작하는 경우 `true`를 반환하고 그렇지 않은 경우 `false`를 반환합니다.

      - `StartsWithLower`는 문자열이 소문자로 시작하는 경우 `true`를 반환하고 그렇지 않은 경우 `false`를 반환합니다.

      - `HasEmbeddedSpaces`는 문자열에 포함된 공백 문자가 있는 경우 `true`를 반환하고 그렇지 않은 경우 `false`를 반환합니다.

1. **솔루션 탐색기**에서 StringLibrary 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다. **애플리케이션** 탭에서 다음 그림과 같이 **루트 네임 스페이스** 텍스트 상자에 있는 텍스트를 삭제합니다. 루트 네임 스페이스는 소스 코드의 [Namespace 문](/dotnet/visual-basic/language-reference/statements/namespace-statement)으로 정의됩니다.

   ![Visual Basic 프로젝트에 대한 [프로젝트 속성] 대화 상자](./media/lut-start/vb-properties.png)

1. 최상위 Visual Studio 메뉴에서 **빌드** > **솔루션 빌드**를 선택합니다. Visual Studio에서 라이브러리가 성공적으로 빌드됩니다.

---

## <a name="create-the-test-project"></a>테스트 프로젝트 만들기

다음 단계는 `StringLibrary` 라이브러리를 테스트하기 위한 단위 테스트 프로젝트를 만드는 것입니다. 다음 단계를 수행하여 단위 테스트를 만듭니다.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. **솔루션 탐색기**에서 `UtilityLibraries` 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 선택합니다.

1. **새 프로젝트 추가** 대화 상자에서 C# 노드를 선택한 후 **.NET Core**를 선택합니다.

   > [!NOTE]
   > 클래스 라이브러리와 동일한 언어로 단위 테스트를 작성할 필요가 없습니다.

1. 오른쪽 창의 **단위 테스트 프로젝트(.NET Core)** 템플릿을 선택하고 다음 그림과 같이 **이름** 텍스트 상자에 `StringLibraryTests`를 입력합니다.

   ![단위 테스트 프로젝트에 대한 **새 프로젝트 추가** 대화 상자](./media/lut-start/add-unit-test-cs.png)

1. **확인**을 선택하여 프로젝트를 만듭니다.

   > [!NOTE]
   > 이 시작 자습서는 MSTest 테스트 프레임워크와 함께 Live Unit Testing을 사용합니다. 또한 xUnit 및 NUnit 테스트 프레임워크도 사용할 수 있습니다.

1. 단위 테스트 프로젝트는 테스트 중인 클래스 라이브러리에 자동으로 액세스할 수 없습니다. 클래스 라이브러리 프로젝트에 대한 참조를 추가하여 테스트 라이브러리 액세스를 제공합니다. 이렇게 하려면 `StringLibraryTests` 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** > **참조**를 선택합니다. **참조 관리자** 대화 상자에서 **솔루션** 탭이 선택되어 있는지 확인하고 다음 그림에 표시된 것처럼 `StringLibrary` 프로젝트를 선택합니다.

   ![**참조 관리자** 대화 상자](./media/lut-start/add-reference.png)

1. 템플릿에서 제공하는 상용구 단위 테스트 코드를 다음 코드로 바꿉니다.

   [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest1.cs)]

1. 도구 모음에서 **저장** 아이콘을 선택하여 프로젝트를 저장합니다.

1. 단위 테스트 코드는 비ASCII 문자를 포함하므로 Visual Studio는 기본 ASCII 형식으로 파일을 저장한 경우 일부 문자가 손실될 수 있다는 경고를 제공합니다. **다른 인코딩으로 저장** 단추를 선택합니다.

   ![파일 인코딩 선택](media/lut-start/ascii-encoding.png)

1. **고급 저장 옵션** 대화 상자의 **인코딩** 드롭다운 목록에서 다음 그림과 같이 **유니코드(서명 없는 UTF-8) - 코드 페이지 65001**을 선택합니다.

   ![UTF-8 인코딩 선택](media/lut-start/utf8-encoding.png)

1. 최상위 Visual Studio 메뉴에서 **빌드** > **솔루션 다시 빌드**를 선택하여 단위 테스트 프로젝트를 컴파일합니다.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. **솔루션 탐색기**에서 `UtilityLibraries` 솔루션을 마우스 오른쪽 단추로 클릭하고 **추가** > **새 프로젝트**를 선택합니다.

1. **새 프로젝트 추가** 대화 상자에서 Visual Basic 노드를 선택한 후 **.NET Core**를 선택합니다.

   > [!NOTE]
   > 클래스 라이브러리와 동일한 언어로 단위 테스트를 작성할 필요가 없습니다.

1. 오른쪽 창의 **단위 테스트 프로젝트(.NET Core)** 템플릿을 선택하고 다음 그림과 같이 **이름** 텍스트 상자에 `StringLibraryTests`를 입력합니다.

   ![단위 테스트를 위한 **새 프로젝트 추가** 대화 상자](./media/lut-start/add-unit-test-vb.png)

1. **확인**을 선택하여 프로젝트를 만듭니다.

   > [!NOTE]
   > 이 시작 자습서는 MSTest 테스트 프레임워크와 함께 Live Unit Testing을 사용합니다. 또한 xUnit 및 NUnit 테스트 프레임워크도 사용할 수 있습니다.

1. 단위 테스트 프로젝트는 테스트 중인 클래스 라이브러리에 자동으로 액세스할 수 없습니다. 클래스 라이브러리 프로젝트에 대한 참조를 추가하여 테스트 라이브러리 액세스를 제공합니다. 이렇게 하려면 `StringLibraryTests` 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가** > **참조**를 선택합니다. **참조 관리자** 대화 상자에서 **솔루션** 탭이 선택되어 있는지 확인하고 다음 그림에 표시된 것처럼 `StringLibrary` 프로젝트를 선택합니다.

   ![**참조 관리자** 대화 상자](./media/lut-start/add-reference.png)

1. 템플릿에서 제공하는 상용구 단위 테스트 코드를 다음 코드로 바꿉니다.

   [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest1.vb)]

1. 도구 모음에서 **저장** 아이콘을 선택하여 프로젝트를 저장합니다.

1. 단위 테스트 코드는 비ASCII 문자를 포함하므로 Visual Studio는 기본 ASCII 형식으로 파일을 저장한 경우 일부 문자가 손실될 수 있다는 경고를 제공합니다. **다른 인코딩으로 저장** 단추를 선택합니다.

   ![파일 인코딩 선택](media/lut-start/ascii-encoding.png)

1. **고급 저장 옵션** 대화 상자의 **인코딩** 드롭다운 목록에서 다음 그림과 같이 **유니코드(서명 없는 UTF-8) - 코드 페이지 65001**을 선택합니다.

   ![UTF-8 인코딩 선택](media/lut-start/utf8-encoding.png)

1. 최상위 Visual Studio 메뉴에서 **빌드** > **솔루션 다시 빌드**별로 단위 테스트 프로젝트를 컴파일합니다.

---

클래스 라이브러리와 이에 대한 단위 테스트를 만들었습니다. 이제 Live Unit Testing을 사용하는 데 필요한 준비 작업을 완료했습니다.

## <a name="enable-live-unit-testing"></a>Live Unit Testing을 사용하도록 설정

지금까지 `StringLibrary` 클래스 라이브러리에 대한 테스트를 작성했지만 실행하지는 않았습니다. Live Unit Testing을 사용하도록 설정했으면 자동으로 실행됩니다. 이렇게 하려면 다음을 수행할 수 있습니다.

1. 필요에 따라 `StringLibrary`에 대한 코드가 포함된 코드 창을 선택합니다. C# 프로젝트의 경우 *Class1.cs*이고, Visual Basic 프로젝트의 경우 *Class1.vb*입니다. (이 단계를 통해 Live Unit Testing을 사용하도록 설정한 후 테스트 결과와 코드 검사를 시각적으로 검사할 수 있습니다.)

1. 최상위 Visual Studio 메뉴에서 **테스트** > **Live Unit Testing** > **시작**을 선택합니다.

1. Visual Studio에서 Live Unit Test를 시작하며 이에 따라 모든 테스트가 자동으로 실행됩니다.

테스트 실행이 완료되면 **테스트 탐색기**에 전반적인 결과와 개별 테스트 결과가 모두 표시됩니다. 또한 코드 창에는 테스트 코드 검사와 테스트 결과가 그래픽 방식으로 모두 표시됩니다. 다음 그림에서 볼 수 있듯이 세 테스트가 모두 성공적으로 실행됩니다. 또한 테스트가 `StartsWithUpper` 메서드의 모든 코드 경로를 포함하고 해당 테스트가 모두 성공적으로 실행되었음을 보여 줍니다(녹색 확인 표시 "✓"로 표시됨). 마지막으로 `StringLibrary`의 다른 메서드 중 어느 것도 코드 검사를 포함하지 않음을 보여 줍니다(파란색 선 “➖”로 표시됨).

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

![Live Unit testing을 시작한 후 테스트 탐색기 및 코드 창](media/lut-start/lut-results-cs.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

![Live Unit testing을 시작한 후 테스트 탐색기 및 코드 창](media/lut-start/lut-results-vb.png)

---

코드 창에서 특정 코드 검사 아이콘을 선택하여 테스트 검사 및 테스트 결과에 대한 자세한 정보를 얻을 수도 있습니다. 이 세부 정보를 검사하려면 다음을 수행합니다.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. `StartsWithUpper` 메서드에서 `if (String.IsNullOrWhiteSpace(s))`라는 줄에서 녹색 확인 표시를 클릭합니다. 다음 그림처럼 Live Unit Testing은 코드 줄을 포함하는 세 가지 테스트를 나타내며 모두 성공적으로 실행되었습니다.

   !['If' 조건 문에 대한 코드 검사](media/lut-start/code-coverage-cs1.png)

1. `StartsWithUpper` 메서드에서 `return Char.IsUpper(s[0])`라는 줄에서 녹색 확인 표시를 클릭합니다. 다음 그림처럼 Live Unit Testing은 코드 줄을 포함하는 두 가지 테스트만 나타내며 모두 성공적으로 실행되었습니다.

   ![return 문에 대한 코드 검사](media/lut-start/code-coverage-cs2.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. `StartsWithUpper` 메서드에서 `If (String.IsNullOrWhiteSpace(s)) Then`라는 줄에서 녹색 확인 표시를 클릭합니다. 다음 그림처럼 Live Unit Testing은 코드 줄을 포함하는 세 가지 테스트를 나타내며 모두 성공적으로 실행되었습니다.

   !['If' 조건 문에 대한 코드 검사](media/lut-start/code-coverage-vb1.png)

1. `StartsWithUpper` 메서드에서 `Return Char.IsUpper(s(0))`라는 줄에서 녹색 확인 표시를 클릭합니다. 다음 그림처럼 Live Unit Testing은 코드 줄을 포함하는 두 가지 테스트만 나타내며 모두 성공적으로 실행되었습니다.

   ![return 문에 대한 코드 검사](media/lut-start/code-coverage-vb2.png)

---

Live Unit Testing에서 확인해야 할 주요 문제점은 불완전한 코드 검사입니다. 다음 섹션에서 이를 해결합니다.

## <a name="expand-test-coverage"></a>테스트 검사 확장

이 섹션에서는 단위 테스트를 `StartsWithLower` 메서드로 확장합니다. 이렇게 하는 동안 Live Unit Testing은 계속해서 동적으로 코드를 테스트합니다.

코드 검사를 `StartsWithLower` 메서드로 확장하려면 다음을 수행합니다.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. 다음 `TestStartsWithLower` 및 `TestDoesNotStartWithLower` 메서드를 프로젝트의 테스트 소스 코드 파일로 추가합니다.

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#1)]

1. [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) 메서드 호출 바로 다음에 아래 코드를 추가하여 `DirectCallWithNullOrEmpty` 메서드를 수정합니다.

    [!code-csharp[StringLibraryTest source code](samples/snippets/csharp/lut-start/unittest2.cs#2)]

1. 소스 코드를 수정하면 Live Unit Testing이 새 테스트와 수정된 테스트를 자동으로 실행합니다. 다음 **테스트 탐색기** 그림처럼 추가한 두 테스트와 수정한 한 테스트 모두 성공했습니다.

   ![테스트 검사를 확장한 후 테스트 탐색기입니다.](media/lut-start/test-dynamic.png)

1. `StringLibrary` 클래스에 대한 소스 코드가 포함된 창으로 전환합니다. 이제 Live Unit Testing은 코드 검사가 `StartsWithLower` 메서드로 확장되었음을 보여 줍니다.

    ![StartsWithLower 메서드에 대한 코드 검사](media/lut-start/lut-extended-cs.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. 다음 `TestStartsWithLower` 및 `TestDoesNotStartWithLower` 메서드를 프로젝트의 테스트 소스 코드 파일로 추가합니다.

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#1)]

1. [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.isfalse) 메서드 호출 바로 다음에 아래 코드를 추가하여 `DirectCallWithNullOrEmpty` 메서드를 수정합니다.

    [!code-vb[StringLibraryTest source code](samples/snippets/visual-basic/lut-start/unittest2.vb#2)]

1. 소스 코드를 수정하면 Live Unit Testing이 새 테스트와 수정된 테스트를 자동으로 실행합니다. 다음 **테스트 탐색기** 그림처럼 추가한 두 테스트와 수정한 한 테스트 모두 성공했습니다.

   ![테스트 검사를 확장한 후 테스트 탐색기입니다.](media/lut-start/test-dynamic.png)

1. `StringLibrary` 클래스에 대한 소스 코드가 포함된 창으로 전환합니다. 이제 Live Unit Testing은 코드 검사가 `StartsWithLower` 메서드로 확장되었음을 보여 줍니다.

    ![StartsWithLower 메서드에 대한 코드 검사](media/lut-start/lut-extended-vb.png)

---

경우에 따라 **테스트 탐색기**의 성공적인 테스트가 흐리게 표시될 수 있습니다. 이것은 테스트가 현재 실행 중이거나, 마지막으로 실행된 이후 테스트에 영향을 줄 수 있는 코드 변경이 없으므로 테스트가 다시 실행되지 않음을 나타냅니다.

지금까지 테스트는 모두 성공했습니다. 다음 섹션에서는 테스트 실패를 처리하는 방법을 살펴봅니다.

## <a name="handle-a-test-failure"></a>테스트 실패 처리

이 섹션에서는 Live Unit Testing을 사용하여 테스트 실패를 식별, 문제 해결 및 처리하는 방법을 알아봅니다. 테스트 검사를 `HasEmbeddedSpaces` 메서드로 확장하여 이 작업을 수행합니다.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. 다음 메서드를 테스트 파일에 추가합니다.

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/unittest2.cs#3)]

1. 테스트를 실행하면 다음 그림과 같이 Live Unit Testing이 `TestHasEmbeddedSpaces` 메서드가 실패했음을 보여 줍니다.

   ![테스트 탐색기에서 실패한 테스트 보고.](media/lut-start/test-failure.png)

1. 라이브러리 코드를 표시하는 창을 선택합니다. Live Unit Testing에서 코드 검사를 `HasEmbeddedSpaces` 메서드로 확장했습니다. 또한 빨간색 "🞩"를 실패한 테스트 범위 줄에 추가하여 테스트 실패를 보고합니다.

1. `HasEmbeddedSpaces` 메서드 서명이 있는 줄 위로 마우스를 가리킵니다. Live Unit Testing은 메서드가 하나의 테스트에서 검사됨을 보고하는 도구 설명을 표시합니다.

   ![실패한 테스트에서 Live Unit Testing 정보.](media/lut-start/test-failure-info-cs.png)

1. 실패한 **TestHasEmbeddedSpaces** 테스트를 선택합니다. Live Unit Testing은 다음 그림과 같이 모든 테스트 실행, 선택 테스트 실행, 모든 테스트 디버깅 및 선택한 테스트 디버깅과 같은 여러 가지 옵션을 제공합니다.

   ![실패한 테스트에 대한 Live Unit Testing 옵션.](media/lut-start/test-failure-options.png)

1. **Debug Selected(디버그 선택됨)** 를 선택하여 실패한 테스트를 디버깅합니다.

1. Visual Studio는 디버그 모드에서 테스트를 실행합니다. 테스트에서는 배열의 각 문자열을 `phrase`라는 변수에 할당하고 이를 `HasEmbeddedSpaces` 메서드에 전달합니다. 어설션 문이 처음으로 `false`일 때 프로그램 실행이 일시 중지되고 디버거를 호출합니다. [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) 메서드 호출의 예기치 않은 값으로 생성되는 예외 대화 상자가 다음 그림에 표시됩니다.

   ![Live Unit Testing 예외 대화 상자.](media/lut-start/exception-dialog-cs.png)

   또한 다음 그림처럼 Visual Studio에서 제공하는 모든 디버깅 도구를 실패한 테스트를 문제 해결하는 데 사용할 수 있습니다.

   ![Visual Studio 디버깅 도구.](media/lut-start/debugging-tools-cs.png)

   **Autos** 창에서 `phrase` 변수 값이 배열의 두 번째 요소인 "Name\tDescription"임을 확인합니다. 테스트 메서드는 `HasEmbeddedSpaces`가 이 문자열을 전달할 때 `true`를 반환할 것으로 예상하지만 `false`를 반환합니다. 분명히, 탭 문자 "\t"를 포함된 공백으로 인식하지 않습니다.

1. **디버그** > **계속**을 선택하거나, **F5** 키를 누르거나 도구 모음에서 **계속** 단추를 클릭하여 테스트 프로그램 실행을 계속합니다. 처리되지 않은 예외가 발생했으므로 테스트를 종료합니다.

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. 다음 메서드를 테스트 파일에 추가합니다.

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/unittest2.vb#3)]

1. 테스트를 실행하면 다음 그림과 같이 Live Unit Testing이 `TestHasEmbeddedSpaces` 메서드가 실패했음을 보여 줍니다.

   ![테스트 탐색기에서 실패한 테스트 보고.](media/lut-start/test-failure.png)

1. 라이브러리 코드를 표시하는 창을 선택합니다. Live Unit Testing에서 코드 검사를 `HasEmbeddedSpaces` 메서드로 확장했습니다. 또한 빨간색 "🞩"를 실패한 테스트 범위 줄에 추가하여 테스트 실패를 보고합니다.

1. `HasEmbeddedSpaces` 메서드 서명이 있는 줄 위로 마우스를 가리킵니다. Live Unit Testing은 메서드가 하나의 테스트에서 검사됨을 보고하는 도구 설명을 표시합니다.

   ![실패한 테스트에서 Live Unit Testing 정보.](media/lut-start/test-failure-info-vb.png)

1. 실패한 **TestHasEmbeddedSpaces** 테스트를 선택합니다. Live Unit Testing은 다음 그림과 같이 모든 테스트 실행, 선택한 테스트 실행, 모든 테스트 디버깅 및 선택한 테스트 디버깅과 같은 다양한 옵션을 제공합니다.

   ![실패한 테스트에 대한 Live Unit Testing 옵션.](media/lut-start/test-failure-options.png)

1. **Debug Selected(디버그 선택됨)** 를 선택하여 실패한 테스트를 디버깅합니다.

1. Visual Studio는 디버그 모드에서 테스트를 실행합니다. 테스트에서는 배열의 각 문자열을 `phrase`라는 변수에 할당하고 이를 `HasEmbeddedSpaces` 메서드에 전달합니다. 어설션 문이 처음으로 `false`일 때 프로그램 실행이 일시 중지되고 디버거를 호출합니다. [`Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue`](/dotnet/api/microsoft.visualstudio.testtools.unittesting.assert.istrue) 메서드 호출의 예기치 않은 값으로 생성되는 예외 대화 상자가 다음 그림에 표시됩니다.

   ![Live Unit Testing 예외 대화 상자.](media/lut-start/exception-dialog-vb.png)

   또한 다음 그림처럼 Visual Studio에서 제공하는 모든 디버깅 도구를 실패한 테스트를 문제 해결하는 데 사용할 수 있습니다.

   ![Visual Studio 디버깅 도구.](media/lut-start/debugging-tools-vb.png)

   **Autos** 창에서 `phrase` 변수 값이 배열의 두 번째 요소인 "Name" + vbTab + "Description"임을 확인합니다. 테스트 메서드는 `HasEmbeddedSpaces`가 이 문자열을 전달할 때 `true`를 반환할 것으로 예상하지만 `false`를 반환합니다. 분명히, 탭 문자를 포함된 공백으로 인식하지 않습니다.

1. **디버그** > **계속**을 선택하거나, **F5** 키를 누르거나 도구 모음에서 **계속** 단추를 클릭하여 테스트 프로그램 실행을 계속합니다. 처리되지 않은 예외가 발생했으므로 테스트를 종료합니다.

---

여기서는 버그의 예비 조사를 위한 충분한 정보를 제공합니다. 테스트 루틴 `TestHasEmbeddedSpaces`가 잘못된 가정을 했거나 `HasEmbeddedSpaces`가 포함된 모든 공백을 제대로 인식하지 못합니다. 문제를 진단하고 해결하려면 `StringLibrary.HasEmbeddedSpaces` 메서드를 시작합니다.

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

1. `HasEmbeddedSpaces` 메서드에서 비교를 확인합니다. 포함된 공백을 U+0020으로 간주합니다. 그러나 유니코드 표준은 다른 공백 문자 수를 포함합니다. 이것은 라이브러리 코드가 공백 문자를 잘못 테스트했음을 나타냅니다.

1. 같음 비교를 <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> 메서드에 대한 호출로 바꿉니다.

    [!code-csharp[The TestHasEmbeddedSpaces test method](samples/snippets/csharp/lut-start/program2.cs#1)]

1. Live Unit Testing은 실패한 테스트 메서드를 자동으로 다시 실행하고 다음 그림과 같이 코드 창과 **테스트 탐색기**에서 결과를 업데이트합니다.

    ![성공적인 HasEmbeddedSpaces 테스트.](media/lut-start/test-success-cs.png)

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

1. `HasEmbeddedSpaces` 메서드에서 비교를 확인합니다. 포함된 공백을 U+0020으로 간주합니다. 그러나 유니코드 표준은 다른 공백 문자 수를 포함합니다. 이것은 라이브러리 코드가 공백 문자를 잘못 테스트했음을 나타냅니다.

1. 같음 비교를 <xref:System.Char.IsWhiteSpace%2A?displayProperty=fullName> 메서드에 대한 호출로 바꿉니다.

    [!code-vb[The TestHasEmbeddedSpaces test method](samples/snippets/visual-basic/lut-start/class2.vb#1)]

1. Live Unit Testing은 실패한 테스트 메서드를 자동으로 다시 실행하고 다음 그림과 같이 코드 창과 **테스트 탐색기**에서 결과를 업데이트합니다.

    ![성공적인 HasEmbeddedSpaces 테스트.](media/lut-start/test-success-vb.png)

---

## <a name="see-also"></a>참고 항목

- [Visual Studio의 Live Unit Testing](live-unit-testing.md)
- [Live Unit Testing 질문과 대답](live-unit-testing-faq.md)
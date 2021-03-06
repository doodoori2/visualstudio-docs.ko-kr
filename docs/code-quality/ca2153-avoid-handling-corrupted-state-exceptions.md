---
title: 손상 된 상태 예외에 대 한 코드 분석 규칙 CA2153
ms.date: 02/19/2019
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b75e45b8a199265eaefe3a2b3c37ed62039e0eb
ms.sourcegitcommit: 845442e2b515c3ca1e4e47b46cc1cef4df4f08d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56450271"
---
# <a name="ca2153-avoid-handling-corrupted-state-exceptions"></a>CA2153: 손상 된 상태 예외 처리 방지

|||
|-|-|
|TypeName|AvoidHandlingCorruptedStateExceptions|
|CheckId|CA2153|
|범주|Microsoft.Security|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인

[손상 된 상태 예외 (Cse)](https://msdn.microsoft.com/magazine/dd419661.aspx) 해당 메모리를 나타낼 손상 프로세스에 존재 합니다. 프로세스 충돌을 허용하는 대신 catch하면 공격자가 손상된 메모리 영역에 익스플로잇을 배치할 수 있는 경우 보안 취약점이 발생할 수 있습니다.

## <a name="rule-description"></a>규칙 설명

CSE는 프로세스의 상태가 손상되었으며 시스템에 의해 catch되지 않았음을 나타냅니다. 손상 된 상태 시나리오에서 일반 처리기만 예외를 catch 메서드를 사용 하 여 표시 하는 경우는 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName> 특성입니다. 기본적으로 [공용 언어 런타임 (CLR)](/dotnet/standard/clr) Cse에 대 한 catch 처리기를 호출 하지 않습니다.

이러한 종류의 예외를 catch 하지 않고도 프로세스 충돌을 허용 하도록 가장 안전한 옵션이입니다. 로깅 코드 조차 공격자가 메모리 손상 버그를 악용할 수 있습니다.

예를 들어, 모든 예외를 catch 하는 일반 처리기로 Cse를 catch 하는 경우이 경고를 트리거합니다 `catch (System.Exception e)` 또는 `catch` 매개 변수가 없는 예외입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 경고를 해결 하려면 다음 중 하나를 수행 합니다.

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> 특성을 제거합니다. 이렇게 하면 CSE가 catch 처리기로 전달되지 않는 기본 런타임 동작으로 돌아갑니다.

- 특정 예외 유형을 catch하는 처리기 기본 설정에서 일반 catch 처리기를 제거합니다. 이 Cse를 가정 하 고 처리기 코드를 안전 하 게 처리할 수 있습니다 (드 묾)을 포함할 수 있습니다.

- 호출자에 게 예외를 전달 하 고 실행 중인 프로세스를 종료 개가 수신 되어야 하는 catch 처리기에서 CSE를 다시 throw 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하는 경우

이 규칙에서는 경고를 표시해야 합니다.

## <a name="pseudo-code-example"></a>의사 (pseudo) 코드 예제

### <a name="violation"></a>위반

다음 의사 코드에서는 이 규칙에 의해 검색되는 패턴을 보여 줍니다.

```csharp
[HandleProcessCorruptedStateExceptions]
// Method that handles CSE exceptions.
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-1---remove-the-attribute"></a>해결 방법 1-특성 제거

제거 된 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> 특성 확인 방법을에서 손상 된 상태 예외 처리 하지 않습니다.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Handle exception.
    }
}
```

### <a name="solution-2---catch-specific-exceptions"></a>해결 방법 2-특정 예외를 catch 합니다.

일반 catch 처리기를 제거하고 특정 예외 형식만 catch합니다.

```csharp
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (IOException e)
    {
        // Handle IOException.
    }
    catch (UnauthorizedAccessException e)
    {
        // Handle UnauthorizedAccessException.
    }
}
```

### <a name="solution-3---rethrow"></a>해결 방법 3-다시 throw

예외를 다시 throw 합니다.

```csharp
[HandleProcessCorruptedStateExceptions]
void TestMethod1()
{
    try
    {
        FileStream fileStream = new FileStream("name", FileMode.Create);
    }
    catch (Exception e)
    {
        // Rethrow the exception.
        throw;
    }
}
```
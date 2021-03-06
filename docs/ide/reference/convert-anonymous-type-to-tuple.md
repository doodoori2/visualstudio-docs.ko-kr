---
title: 익명 형식을 튜플로 변환
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: b7a53aa8f329c1cdedc0cedff7e56b3f6dfa2f2a
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335876"
---
# <a name="convert-anonymous-type-to-tuple"></a>익명 형식을 튜플로 변환

이 리팩터링은 다음에 적용됩니다.

- C#

**내용:** 익명 형식을 튜플로 변환합니다.

**시기:** 튜플로 한정된 익명 형식이 있습니다.

**이유:** [튜플](/dotnet/csharp/tuples)은 간단한 구문을 유지하는 데 도움이 됩니다. 이 빠른 작업을 통해 C# 기능을 더 쉽게 이용할 수 있습니다.

## <a name="how-to"></a>방법

1. 익명 형식으로 커서를 놓습니다.
2. 줄의 임의 위치에서 **Ctrl**+**.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

   ![익명 형식을 튜플로 변환](media/convert-anon-to-tuple.png)

2. **Enter**를 눌러 리팩터링을 수락합니다.

   ![익명 형식을 튜플로 변환](media/convert-anon-to-tuple-complete.png)

## <a name="see-also"></a>참고 항목

- [리팩터링](../refactoring-in-visual-studio.md)

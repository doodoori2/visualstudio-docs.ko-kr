---
title: 코드 변경 내용 미리 보기
ms.date: 12/16/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.codefix.previewchanges
ms.workload:
- multiple
ms.openlocfilehash: 07d722848725753b0b2abf25c8497327cdb53835
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55952166"
---
# <a name="preview-changes-window"></a>변경 내용 미리 보기 창

Visual Studio에서 다양한 *빠른 작업* 또는 *리팩터링* 도구를 사용하는 경우 프로젝트에 대한 변경 내용을 허용하기 전에 미리 볼 수 있습니다. 이 작업은 **변경 내용 미리 보기** 창에서 수행합니다.  예를 들어 다음은 C# 프로젝트에서 이름 바꾸기 리팩터링 중에 변경되는 내용을 보여 주는 **변경 내용 미리 보기** 창입니다.

![변경 내용 미리 보기](media/previewchanges.png)

창의 위쪽에는 변경되는 특정 줄이 표시되고 각 줄에 해당하는 확인란이 있습니다. 특정 줄에만 선택적으로 리팩터링을 적용하려는 경우 각 확인란을 선택하거나 선택을 취소할 수 있습니다.

창의 아래쪽에는 프로젝트에서 변경되는 서식이 지정된 코드가 표시되며 영향을 받는 영역이 강조 표시됩니다. 창 위쪽에서 특정 줄을 선택하면 아래쪽의 해당 줄이 강조 표시됩니다. 따라서 해당 줄로 빠르게 건너뛰어 주변 코드를 확인할 수 있습니다.

변경 내용을 검토한 후 **적용** 단추를 클릭하여 변경 내용을 커밋하거나, **취소** 단추를 클릭하여 현재 상태를 유지합니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio에서 리팩터링](../ide/refactoring-in-visual-studio.md)
- [빠른 작업](../ide/quick-actions.md)

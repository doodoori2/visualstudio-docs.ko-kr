---
title: 서식 지정, XML, 텍스트 편집기, 옵션 대화 상자
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: bb539b3a-027c-4b2f-906e-403e0e22ba8d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 79b34c30e3d00e4f145a32acbaf769d13888298d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55923203"
---
# <a name="formatting-xml-text-editor-options-dialog-box"></a>서식 지정, XML, 텍스트 편집기, 옵션 대화 상자

이 대화 상자에서는 XML 편집기에 대한 서식 설정을 지정할 수 있습니다. 액세스할 수 있습니다 합니다 **옵션** 대화 상자를 **도구** 메뉴.

> [!NOTE]
> 선택 하면 이러한 설정을 사용할 수 있습니다는 **텍스트 편집기** 폴더를 **XML** 폴더를 차례로 **서식** 에서 옵션을 **옵션** 대화 상자.

## <a name="attributes"></a>특성
 **수동으로 지정한 특성 서식 유지**

 특성의 서식은 다시 지정되지 않습니다. 이 값이 기본값입니다.

> [!NOTE]
> 특성이 여러 줄에 있을 경우 편집기는 부모 요소의 들여쓰기와 일치하도록 각 특성 줄을 들여씁니다.

 **자체 줄에 특성 맞춤**

 첫 번째 특성의 들여쓰기와 일치하도록 두 번째 특성 및 그 이후 특성이 세로로 정렬됩니다. 다음 XML 텍스트는 특성 정렬 방식의 예제입니다.

```xml
<item id = "123-A"
      name = "hammer"
      price = "9.95">
</item>
```

## <a name="auto-reformat"></a>자동 서식 다시 지정
 **클립보드에서 붙여넣기 시**

 클립보드에서 붙여넣은 XML 텍스트의 서식을 다시 지정합니다.

 **끝 태그 완료 시**

 끝 태그가 완료될 때 요소의 서식을 다시 지정합니다.

## <a name="mixed-content"></a>혼합 된 콘텐츠
 **혼합된 내용을 기본값으로 유지**

 편집기에서 혼합 내용 서식을 다시 지정하는지 여부를 결정합니다. 혼합 내용이 `xml:space="preserve"` 범위에 있는 경우를 제외하고 기본적으로 편집기에서는 혼합 내용의 서식을 다시 지정하려고 시도합니다.

 요소에 텍스트와 태그가 혼합되어 있는 경우 이 내용은 혼합 내용으로 간주됩니다. 다음은 혼합 내용이 포함된 요소의 예제입니다.

```xml
<dir>c:\data\AlphaProject\
  <file readOnly="false">test1.txt</file>
  <file readOnly="false">test2.txt</file>
</dir>
```

## <a name="see-also"></a>참고자료

- [XML 문서 속성, 속성 창](../xml-tools/xml-document-properties-properties-window.md)
- [XML 편집기 구성 요소](../xml-tools/xml-editor-components.md)
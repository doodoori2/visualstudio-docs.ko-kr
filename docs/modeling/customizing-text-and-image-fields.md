---
title: 텍스트 및 이미지 필드 사용자 지정
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d63354d552b04d07f0b2d0ede41d28fc33cda3a3
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970727"
---
# <a name="customizing-text-and-image-fields"></a>텍스트 및 이미지 필드 사용자 지정
셰이프의 텍스트 decorator를 정의한 경우에 텍스트 필드에서 표시 됩니다. TextFields와 다른 ShapeFields 초기화의 예제를 DSL 솔루션에서 Dsl\GeneratedCode\Shapes.cs를 검사 합니다.

 텍스트 필드는 레이블에 할당 된 공간 등의 셰이프 내에서 영역을 관리 하는 개체입니다. TextField 인스턴스는 동일한 클래스의 여러 도형 간에 공유 됩니다. TextField 인스턴스는 각 인스턴스에 대해 개별적으로 레이블의 텍스트를 저장 하지 않습니다: 대신는 `GetDisplayText(ShapeElement)` 메서드 매개 변수로 셰이프를 사용 하 고 해당 모델 요소에 현재 상태에 따라 텍스트를 조회할 수 있습니다.

## <a name="how-the-appearance-of-a-text-field-is-determined"></a>텍스트 필드의 모양이 결정 하는
 `DoPaint()` 메서드가 호출 되어 표시 필드를 화면에 있습니다. 기본값을 재정의 하거나 수 `DoPaint(),` 호출 하는 방법 중 일부를 재정의할 수 있습니다. 기본 메서드의 다음 단순화 된 버전은 기본 동작을 재정의 하는 방법을 이해할 수 있습니다.

```csharp
// Simplified version:
public override void DoPaint(DiagramPaintEventArgs e, ShapeElement parentShape)
{
  string text = GetDisplayText(shape);
  StringFormat format = GetStringFormat(parentShape);
  Brush brush = GetTextBrush(e.View, shape);
  using (Font font = GetFont(shape))
  {
    e.Graphics.DrawString(text, font, brush, format);
  }
}
// StringFormat determines whether the string is centered etc.
// To customize statically for all instances of this shape field,
// assign to DefaultStringFormat.
// To customize dynamically or per shape, override this:
public virtual StringFormat GetStringFormat(ShapeElement shape)
{ return DefaultStringFormat; }

// Override to customize the displayed string:
public virtual string GetDisplayText(ShapeElement shape)
{ return this.GetValue(shape).ToString(); }

// Brush determines the text color.
// To change the brush for every field, change the shape's styleset.
// To customize to a brush in the style set, override GetTextBrushId.
// To change the brush to non-standard color, override this.
// Should take account of whether selected.
public virtual Brush GetTextBrush(DiagramClientView view, ShapeElement shape)
{ return shape.StyleSet.GetBrush(this.GetTextBrushId(view, shape)); }

// Brush ID selects a brush from a StyleSet.
// Either return a member of DiagramBrushes
// or add your own brush to the shape or application's styleset.
// Override this to change dynamically or per instance.
// To change statically, just assign to default values.
public virtual StyleSetResourceId GetTextBrushId(DiagramClientView view, ShapeElement shape)
{ return IsSelected(view, shape) ? (view.Focused ? DefaultSelectedTextBrushId
: DefaultInactiveSelectedTextBrushId ) : DefaultTextBrushId ;
}

// Font determines the shape and size of the text.
// To change the font for every field, change the shape's styleset.
// To customize to a font in the style set, override GetFontId.
// To change the font to a non-standard font, override this.
public virtual Font GetFont(ShapeElement shape)
{ return shape.StyleSet.GetFont(GetFontId(shape)); }

// Selects a font from a styleset.
// Either return a member of DiagramFonts or
// add your own font to the shape or application's styleset.
// To change statically for all instances of this field,
// assign to DefaultFontId.
// To change per shape or dynamically, override this.
public virtual StyleSetResourceId GetFontId(ShapeElement parentShape)
{ return DefaultFontId; }
```

 다른 쌍의 여러 가지 `Get` 메서드 및 `Default` 속성을 같은 `DefaultMultipleLine/GetMultipleLine()`합니다. 셰이프 필드의 모든 인스턴스에 대 한 값을 변경 하려면 기본 속성 값을 할당할 수 있습니다. 에 다른 셰이프 또는 모델 요소의 상태에 따라 다를 모양 인스턴스에서 값을 설정, 재정의 `Get` 메서드.

## <a name="static-customizations"></a>정적 사용자 지정
 이 셰이프 필드의 모든 인스턴스를 변경 하려는 경우 먼저 확인 여부 DSL 정의에서 속성을 설정할 수 있습니다. 예를 들어, 속성 창에서 글꼴 크기 및 스타일을 설정할 수 있습니다.

 그렇지 않은 경우 다음 재정의 하는 `InitializeShapeFields` 할당을 적절 한 값을 확인 하 고 모양 클래스의 메서드 `Default...` 텍스트 필드의 속성입니다.

> [!WARNING]
>  재정의할 `InitializeShapeFields()`를 설정 해야 합니다는 **Generates Double Derived** 모양 클래스의 속성 `true` DSL 정의에서 합니다.

 이 예제에서는 도형에는 사용자 의견에 대 한 사용 될 텍스트 필드입니다. 표준 주석 글꼴을 사용 하려고 합니다. 스타일 집합에서 표준 글꼴 이기 때문에 기본 글꼴 id를 설정할 수 있습니다.

```csharp

 partial class ExampleShape
{   protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Find and update comment field:
      TextField commentField = ShapeElement.FindShapeField(shapeFields, "CommentDecorator") as TextField;
      // Use the standard font for comments:
      commentField.DefaultFontId = DiagramFonts.CommentText;
```

## <a name="dynamic-customizations"></a>동적 사용자 지정
 셰이프나 모델 요소의 상태에 따라 달라 집니다 모양의 하려면의 고유한 하위 클래스를 파생 `TextField` 하나 이상의 재정의 및 `Get...` 메서드. 또한 프로그램 도형의 InitializeShapeFields 메서드를 재정의 하 고 사용자 지정 클래스의 인스턴스를 사용 하 여 텍스트 필드의 인스턴스를 대체 해야 합니다.

 다음 예제에서는 도형의 모델 요소의 부울 도메인 속성의 상태에 따라 텍스트 필드의 글꼴을 만듭니다.

 이 예제 코드를 실행 하려면 최소 언어 템플릿을 사용 하 여 새 DSL 솔루션을 만듭니다. 부울 도메인 속성 추가 `AlternateState` ExampleElement 도메인 클래스에 있습니다. ExampleShape 클래스에 아이콘 decorator를 추가 하 고 비트맵 파일에 해당 이미지를 설정 합니다. 클릭 **모든 템플릿 변환**합니다. DSL 프로젝트에서 새 코드 파일을 추가 하 고 다음 코드를 삽입 합니다.

 코드를 테스트 하려면 F5 키를 눌러 하 고 디버깅 솔루션에서 샘플 다이어그램을 엽니다. 아이콘의 기본 상태로 표시 됩니다. 셰이프를 선택 하 고 속성 창에서 값을 변경 합니다 **AlternateState** 속성입니다. 요소 이름의 글꼴을 변경 해야 합니다.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...

  partial class ExampleShape
  {
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);
      // Replace the text field for NameDecorator:
      TextField oldField = ShapeElement.FindShapeField(shapeFields, "NameDecorator") as TextField;
      shapeFields.Remove(oldField);
      // Replace with my text field based on DSL Definition values:
      MyTextField newField = new MyTextField(oldField);
      shapeFields.Add(newField);
    }
  }
  /// <summary>
  /// Dynamic font depends on state of model element.
  /// </summary>
  public class MyTextField : TextField
  {
    public MyTextField(TextField prototype)
      : base(prototype.Name)
    {
      DefaultText = prototype.DefaultText;
      DefaultFocusable = prototype.DefaultFocusable;
      DefaultAutoSize = prototype.DefaultAutoSize;
      AnchoringBehavior.MinimumHeightInLines = prototype.AnchoringBehavior.MinimumHeightInLines;
      AnchoringBehavior.MinimumWidthInCharacters = prototype.AnchoringBehavior.MinimumWidthInCharacters;
      DefaultAccessibleState = prototype.DefaultAccessibleState;
    }

    public override System.Drawing.Font GetFont(ShapeElement parentShape)
    {
      // Access the Boolean domain property of the model element:
      if ((parentShape.ModelElement as ExampleElement).AlternateState)
        return new System.Drawing.Font("Callisto", 14.0f,
               System.Drawing.FontStyle.Italic |
               System.Drawing.FontStyle.Bold);
      else
        return base.GetFont(parentShape);
    }

  }
```

## <a name="style-sets"></a>스타일 설정
 앞의 예제를 사용할 수 있는 글꼴 텍스트 필드를 변경 하는 방법을 보여 줍니다. 그러나 것이 좋습니다 메서드는 응용 프로그램 또는 셰이프를 사용 하 여 연결 된 스타일 집합 중 하나를 변경 하려면. 이 위해 재정의 <xref:Microsoft.VisualStudio.Modeling.Diagrams.TextField.GetFontId%2A> 또는 GetTextBrushId() 합니다.

 또는 스타일 집합을 변경 하면 셰이프를 재정의 하 여는 것이 좋습니다 <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.InitializeResources%2A>합니다. 이 글꼴 및 셰이프 필드의 모든 브러시를 변경 하는 효과가 있습니다.

## <a name="customizing-image-fields"></a>이미지 필드 사용자 지정
 도형에 이미지 데코레이터를 정의 하는 경우 및 이미지 모양을 정의 하는 경우 영역 셰이프를 표시 하는 이미지 필드에서 관리 됩니다. ImageFields와 다른 ShapeFields 초기화의 예제를 DSL 솔루션에서 Dsl\GeneratedCode\Shapes.cs를 검사 합니다.

 이미지 필드는 데코레이터에 할당 된 공간 등의 셰이프 내에서 영역을 관리 하는 개체입니다. 이미지 필드 인스턴스는 동일한 모양 클래스의 여러 도형 간에 공유 됩니다. 이미지 필드 인스턴스 각 셰이프에 대 한 별도 이미지를 저장 하지 않습니다: 대신는 `GetDisplayImage(ShapeElement)` 메서드 매개 변수로 셰이프를 사용 하 고 해당 모델 요소에 현재 상태에 따라 이미지를 조회할 수 있습니다.

 변수 이미지와 같은 특수 한 동작이 하려는 경우에 이미지 필드에서 파생 된 고유한 클래스를 만들 수 있습니다.

#### <a name="to-create-a-subclass-of-imagefield"></a>이미지 필드의 하위 클래스를 만들려면

1.  설정 된 **Generates Double Derived** DSL 정의에서 부모 모양 클래스의 속성입니다.

2.  재정의 `InitializeShapeFields` 모양 클래스의 메서드.

    -   DSL 프로젝트에서 새 코드 파일을 만들고 모양 클래스에 대 한 partial 클래스 정의 작성 합니다. 있습니다 메서드 정의 재정의 합니다.

3.  코드 검사 `InitializeShapeFields` DSL\GeneratedCode\Shapes.cs에서.

     재정의 메서드에서 기본 메서드를 호출 하 고 사용자 고유의 이미지 필드 클래스의 인스턴스를 만듭니다. 일반 이미지 필드를 대체 하는 데 사용 된 `shapeFields` 목록입니다.

## <a name="dynamic-icons"></a>동적 아이콘
 이 예제에서는 변경 아이콘 도형의 모델 요소의 상태에 따라 달라 집니다.

> [!WARNING]
>  이 예제에서는 동적 이미지 데코레이터를 확인 하는 방법에 설명 합니다. 이지만 모델 변수의 상태에 따라 하나 또는 두 개의 이미지를 전환 하려는 경우 간단 하 게 여러 이미지 데코레이터를 만들고 셰이프를에서 같은 위치에 배치할 표시 유형 필터는 모델의 특정 값에 따라 달라 지도록 설정 변수입니다. 이 필터를 설정 하려면 DSL 정의에서 도형 맵에서 선택 하 고 DSL 세부 정보 창 열고 데코레이터 탭을 클릭 합니다.

 이 예제 코드를 실행 하려면 최소 언어 템플릿을 사용 하 여 새 DSL 솔루션을 만듭니다. 부울 도메인 속성 추가 `AlternateState` ExampleElement 도메인 클래스에 있습니다. ExampleShape 클래스에 아이콘 decorator를 추가 하 고 비트맵 파일에 해당 이미지를 설정 합니다. 클릭 **모든 템플릿 변환**합니다. DSL 프로젝트에서 새 코드 파일을 추가 하 고 다음 코드를 삽입 합니다.

 코드를 테스트 하려면 F5 키를 눌러 하 고 디버깅 솔루션에서 샘플 다이어그램을 엽니다. 아이콘의 기본 상태로 표시 됩니다. 셰이프를 선택 하 고 속성 창에서 값을 변경 합니다 **AlternateState** 속성입니다. 다음 아이콘을 통해 해당 셰이프에 90도 회전 표시 됩니다.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
...
partial class ExampleShape
{
    /// <summary>
    /// Compose a list of the fields in this shape.
    /// Called once for each shape class.
    /// </summary>
    /// <param name="shapeFields"></param>
    protected override void InitializeShapeFields(IList<ShapeField> shapeFields)
    {
      // Fields set up according to DSL Definition:
      base.InitializeShapeFields(shapeFields);

      // Replace the image field:
      ShapeField oldField = ShapeElement.FindShapeField(shapeFields, "IconDecorator");
      shapeFields.Remove(oldField);
      // Must keep the same name:
      MyImageField newField = new MyImageField(oldField.Name);
      shapeFields.Add(newField);
      newField.DefaultImage = (oldField as ImageField).DefaultImage.Clone() as System.Drawing.Image;
    }
  }

  public class MyImageField : ImageField
  {
    public MyImageField(string tag) : base(tag) { }

    /// <summary>
    /// Get the image for this field in the given shape.
    /// </summary>
    public override System.Drawing.Image GetDisplayImage(ShapeElement parentShape)
    {
      ExampleElement element = parentShape.ModelElement as ExampleElement;
      if (element.AlternateState == true)
        return AlternateImage;
      else
        return base.GetDisplayImage(parentShape);
    }

    private System.Drawing.Image alternateImage;
    public System.Drawing.Image AlternateImage
    {
      get
      {
        if (alternateImage == null)
        {
          // Alternate image is a copy of the default, rotated by 90 degrees:
          alternateImage = this.DefaultImage.Clone() as System.Drawing.Image;
          alternateImage.RotateFlip(System.Drawing.RotateFlipType.Rotate90FlipNone);
        }
        return alternateImage;
      }
    }
  }
}
```

## <a name="see-also"></a>참고 항목

- [모양 및 연결선 정의](../modeling/defining-shapes-and-connectors.md)
- [다이어그램에 배경 이미지 설정](../modeling/setting-a-background-image-on-a-diagram.md)
- [프로그램 코드에서 모델 탐색 및 업데이트](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [도메인별 언어를 사용자 지정하는 코드 작성](../modeling/writing-code-to-customise-a-domain-specific-language.md)
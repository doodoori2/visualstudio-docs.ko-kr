---
title: 옵션, 텍스트 편집기, JavaScript, 서식 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Formatting.New_Lines
ms.assetid: 28a0aef1-9353-4d94-95a5-54b42e15c0dc
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b4a5a69d556beb8ebf3d3f75720614f7258b1780
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47550178"
---
# <a name="options-text-editor-javascript-formatting"></a>옵션, 텍스트 편집기, JavaScript, 서식
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [옵션, 텍스트 편집기, JavaScript, 서식](https://docs.microsoft.com/visualstudio/ide/reference/options-text-editor-javascript-formatting)합니다.  
  
  
**옵션** 대화 상자의 **서식** 페이지를 사용하여 코드 편집기의 서식 코드에 대한 옵션을 설정합니다. 메뉴 모음에서 이 페이지에 액세스하려면 **도구**, **옵션**을 선택한 다음 **텍스트 편집기**, **JavaScript** 및 **서식**을 확장합니다.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
## <a name="automatic-formatting"></a>자동 형식 지정  
 이러한 옵션은 **소스** 보기에서 서식 지정이 발생하는 시기를 결정합니다.  
  
## <a name="uielement-list"></a>UI 요소 목록  
  
|옵션|설명|  
|------------|-----------------|  
|**Enter 키 입력 시 완성 문에 서식 자동 지정**|이 옵션을 선택하면 Enter 키를 선택하는 경우 코드 편집기가 자동으로 줄의 서식을 지정합니다.|  
|**; 입력 시 완성 문에 서식 자동 지정**|이 옵션을 선택하면 세미콜론(;) 키를 선택하는 경우 코드 편집기가 자동으로 줄의 서식을 지정합니다.|  
|**} 입력 시 완성 블록에 서식 자동 지정**|이 옵션을 선택하면 닫는 중괄호(}) 키를 선택하는 경우 코드 편집기가 자동으로 줄의 서식을 지정합니다.|  
|**붙여넣을 때 서식 지정**|이 옵션을 선택하면 편집기에 붙여 넣을 경우 코드 편집기가 코드의 서식을 다시 지정합니다. 편집기는 현재 정의된 서식 지정 규칙을 사용합니다. 이 옵션을 선택하지 않으면 편집기는 붙여넣은 코드의 원래 서식을 사용합니다.|  
  
## <a name="new-lines"></a>새로운 줄  
 이 옵션은 코드 편집기가 새 줄에 함수 및 컨트롤 블록용 여는 중괄호를 배치할지 결정합니다.  
  
## <a name="uielement-list"></a>UI 요소 목록  
  
|옵션|설명|  
|------------|-----------------|  
|**함수의 여는 중괄호를 새 줄에 배치**|이 옵션을 선택하면 코드 편집기는 함수와 연결된 여는 중괄호를 새 줄로 이동합니다.|  
|**컨트롤 블록의 여는 중괄호를 새 줄에 배치**|이 옵션을 선택하면 코드 편집기는 컨트롤 블록(예:`if` 및 `while` 컨트롤 블록) 과 연결된 여는 중괄호를 새 줄로 이동합니다.|  
  
## <a name="spacing"></a>간격  
 이 옵션은 **소스** 보기에서 공백이 삽입되는 방식을 결정합니다.  
  
## <a name="uielement-list"></a>UI 요소 목록  
  
|옵션|설명|  
|------------|-----------------|  
|**쉼표 구분 기호 뒤에 공백 삽입**|이 옵션을 선택하면 코드 편집기는 쉼표 구분 기호 뒤에 공백을 추가합니다.|  
|**'for' 문의 세미콜론 뒤에 공백 삽입**|이 옵션을 추가하면 코드 편집기는 `for` 루프의 첫 번째 줄에서 각 세미콜론 뒤에 공백을 추가합니다.|  
|**이항 연산자의 앞뒤에 공백 삽입**|이 옵션을 선택하면 코드 편집기는 이항 연산자 앞뒤에 공백을 추가합니다(예: +, -, &&, &#124;&#124;).|  
|**제어 흐름 문의 키워드 뒤에 공백 삽입**|이 옵션을 선택하면 코드 편집기는 제어 흐름 문의 JavaScript 키워드 뒤에 공백을 추가합니다.|  
|**익명 함수의 function 키워드 뒤에 공백 삽입**|이 옵션을 선택하면 코드 편집기는 익명 함수에 대한 `function` 키워드 뒤에 공백을 추가합니다.|  
|**여는 괄호 뒤와 비어 있지 않은 닫는 괄호 앞에 공백 삽입**|이 옵션을 선택하면 코드 편집기는 비어 있지 않는 문자가 있는 경우 여는 괄호 뒤와 닫는 괄호 앞에 공백을 추가합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [옵션 대화 상자, 환경, 일반](../../ide/reference/general-environment-options-dialog-box.md)



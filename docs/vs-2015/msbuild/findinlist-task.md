---
title: FindInList 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindInList task [MSBuild]
- MSBuild, FindInList task
ms.assetid: d49b9f84-52a2-4242-9269-b741a7a7e9f7
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f5011d1b9e83b379be8eb4b23ec6a7aac649ef9a
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54774559"
---
# <a name="findinlist-task"></a>FindInList 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
지정된 목록에서 일치하는 itemspec이 있는 항목을 찾습니다.  
  
## <a name="parameters"></a>매개 변수  
 다음 표에서는 [FindInList 작업](../msbuild/findinlist-task.md)의 매개 변수에 대해 설명합니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`CaseSensitive`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 검색은 대/소문자를 구분하고, 그렇지 않으면 구분하지 않습니다. 기본값은 `true`여야 합니다.|  
|`FindLastMatch`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 마지막 일치 항목을 반환하고, 그렇지 않으면 첫 번째 일치 항목을 반환합니다. 기본값은 `false`여야 합니다.|  
|`ItemFound`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 읽기 전용 출력 매개 변수입니다.<br /><br /> 있는 경우 목록에서 처음으로 일치하는 항목입니다.|  
|`ItemSpecToFind`|필수 `String` 매개 변수입니다.<br /><br /> 검색할 itemspec입니다.|  
|`List`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> itemspec을 검색할 목록입니다.|  
|`MatchFileNameOnly`|선택적 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 itemspec의 파일 이름 부분에 대해 일치하고, 그렇지 않으면 전체 itemspec에 대해 일치합니다. 기본값은 `true`여야 합니다.|  
  
## <a name="remarks"></a>주의  
 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [작업](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)

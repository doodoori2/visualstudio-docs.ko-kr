---
title: AssignTargetPath 작업 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: efae349037d6a826c4d267e12d901306eed7629b
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54758699"
---
# <a name="assigntargetpath-task"></a>AssignTargetPath 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
이 작업은 파일 목록을 수락하고 `<TargetPath>` 특성을 아직 지정하지 않은 경우 추가합니다.  
  
## <a name="task-parameters"></a>작업 매개 변수  
 다음 표에서는 `AssignTargetPath` 작업의 매개 변수에 대해 설명합니다.  
  
|매개 변수|설명|  
|---------------|-----------------|  
|`RootFolder`|선택적 `string` 입력 매개 변수입니다.<br /><br /> 대상 링크를 포함하는 폴더에 대한 경로가 포함됩니다.|  
|`Files`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 입력 매개 변수입니다.<br /><br /> 들어오는 파일 목록을 포함합니다.|  
|`AssignedFiles`|Optional<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem> `[]` 출력 매개 변수입니다.<br /><br /> 결과 파일 목록을 포함합니다.|  
  
## <a name="remarks"></a>주의  
 이 작업은 위에 나와 있는 매개 변수 외에 <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension Base Class](../msbuild/taskextension-base-class.md)를 참조하세요.  
  
## <a name="example"></a>예  
 다음 예제에서는 `AssignTargetPath` 작업을 실행하여 프로젝트를 구성합니다.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyProject">  
        <AssignTargetPath  
RootFolder="Resources"  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
        </AssignTargetPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>참고 항목  
 [작업](../msbuild/msbuild-tasks.md)   
 [작업 참조](../msbuild/msbuild-task-reference.md)

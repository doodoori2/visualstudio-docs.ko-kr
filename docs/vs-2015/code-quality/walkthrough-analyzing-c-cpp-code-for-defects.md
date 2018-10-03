---
title: '연습: C / c + + 코드의 오류 분석 | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: 37
author: corob-msft
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1c944a50330f458240b3da2fea8952abb5b8f02b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47543004"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>연습: C/C++ 코드의 오류 분석
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [연습: C/c + + 코드 오류에 대 한 분석](https://docs.microsoft.com/visualstudio/code-quality/walkthrough-analyzing-c-cpp-code-for-defects)합니다.  
  
이 연습에서는 C/c + + 코드에 대 한 코드 분석 도구를 사용 하 여 잠재적인 코드 오류에 대 한 C/c + + 코드를 분석 하는 방법에 설명 합니다.  
  
 이 연습에서는 잠재적인 코드 오류에 대 한 C/c + + 코드를 분석 하려면 코드 분석을 사용 하는 프로세스를 통해 단계입니다.  
  
 다음 단계를 완료 합니다.  
  
-   네이티브 코드에서 코드 분석을 실행 합니다.  
  
-   코드 오류 경고를 분석 합니다.  
  
-   경고를 오류로 처리 합니다.  
  
-   코드 오류 분석을 개선 하기 위해 소스 코드에 주석을 추가 합니다.  
  
## <a name="prerequisites"></a>전제 조건  
  
-   [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] 또는 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]  
  
-   복사본을 [데모 샘플](../code-quality/demo-sample.md)합니다.  
  
-   C/c + +의 기본적인 이해입니다.  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>네이티브 코드에 코드 결함 분석을 실행 하려면  
  
1.  데모 솔루션을 엽니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.  
  
     Demo 솔루션이 열립니다 **솔루션 탐색기**합니다.  
  
2.  에 **빌드할** 메뉴에서 클릭 **솔루션 다시 빌드**합니다.  
  
     솔루션이 오류 또는 경고 없이 빌드됩니다.  
  
3.  **솔루션 탐색기**, CodeDefects 프로젝트를 선택 합니다.  
  
4.  **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
     합니다 **CodeDefects 속성 페이지** 대화 상자가 표시 됩니다.  
  
5.  클릭 **코드 분석**합니다.  
  
6.  클릭 합니다 **C/c + + 빌드에 대 한 코드 분석 사용** 확인란 합니다.  
  
7.  CodeDefects 프로젝트를 다시 작성 합니다.  
  
     코드 분석 경고에 표시 되는 **오류 목록**합니다.  
  
### <a name="to-analyze-code-defect-warnings"></a>코드 오류 경고를 분석 하려면  
  
1.  에 **뷰** 메뉴에서 클릭 **오류 목록**합니다.  
  
     개발자 프로필의 선택에 따라 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 가리키도록 해야 **다른 Windows** 에 **보기** 메뉴를 클릭 한 다음 **오류 목록**합니다.  
  
2.  에 **오류 목록**, 다음 경고를 두 번 클릭 합니다.  
  
     경고 C6230: 의미 체계가 다른 형식 간의 암시적 캐스트: 부울 컨텍스트에서 HRESULT를 사용 합니다.  
  
     함수에서 경고를 발생 시킨 줄을 표시 하는 코드 편집기 `bool``ProcessDomain()`합니다. 이 경고는 HRESULT를 되는 'if' 문에서 부울 결과가 필요한 경우를 나타냅니다.  
  
3.  SUCCEEDED 매크로 사용 하 여이 경고를 해결 합니다. 코드에는 다음 코드와 유사 해야 합니다.  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4.  에 **오류 목록**, 다음 경고를 두 번 클릭 합니다.  
  
     경고 C6282: 잘못 된 연산자: 테스트 컨텍스트에서 상수를 할당 합니다. 가 의도 한 = =?  
  
5.  같음 테스트 하 여이 경고를 해결 합니다. 코드를 다음 코드로 유사 합니다.  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>경고를 오류로 처리 하려면  
  
1.  Bug.cpp 파일에 다음 추가 `#pragma` C6001 경고를 오류로 처리 하는 파일의 시작 부분에 문의 합니다.  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2.  CodeDefects 프로젝트를 다시 작성 합니다.  
  
     에 **오류 목록**, C6001 오류로 나타납니다.  
  
3.  나머지 두 C6001 오류를 해결 합니다 **오류 목록** 초기화 하 여 `i` 및 `j` 0으로.  
  
4.  CodeDefects 프로젝트를 다시 작성 합니다.  
  
     프로젝트 경고 또는 오류 없이 빌드됩니다.  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Annotation.c에서 소스 코드 주석 경고를 해결 하려면  
  
1.  솔루션 탐색기에서 주석 프로젝트를 선택 합니다.  
  
2.  **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
     합니다 **주석 속성 페이지** 대화 상자가 표시 됩니다.  
  
3.  클릭 **코드 분석**합니다.  
  
4.  선택 된 **C/c + + 빌드에 대 한 코드 분석 사용** 확인란 합니다.  
  
5.  주석 프로젝트를 다시 작성 합니다.  
  
6.  에 **오류 목록**, 다음 경고를 두 번 클릭 합니다.  
  
     경고 C6011: NULL 포인터 'newNode'를 역참조 합니다.  
  
     이 경고는 반환 값을 확인 하려면 호출자가 오류를 나타냅니다. 이 경우 호출에서 **AllocateNode** NULL 값을 반환할 수 있습니다 (AllocateNode에 대 한 함수 선언에 대 한 annotations.h 헤더 파일 참조).  
  
7.  Annotations.cpp 파일을 엽니다.  
  
8.  이 경고를 해결 하려면 'if' 문을 사용 하 여 반환 값을 테스트 합니다. 코드에는 다음 코드와 유사 해야 합니다.  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. 주석 프로젝트를 다시 작성 합니다.  
  
     프로젝트 경고 또는 오류 없이 빌드됩니다.  
  
### <a name="to-use-source-code-annotation"></a>소스 코드 주석을 사용 하려면  
  
1.  정식 매개 변수를 주석 달기 및 함수의 값 반환 `AddTail` 이 예와 같이 사전 및 사후 조건을 사용 하 여:  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2.  주석 프로젝트를 다시 작성 합니다.  
  
3.  에 **오류 목록**, 다음 경고를 두 번 클릭 합니다.  
  
     경고 C6011: NULL 포인터 역참조 'node'.  
  
     이 경고는 함수에 전달 하는 노드는 null 일 수를 나타냅니다와 경고를 발생 하는 줄 번호를 나타냅니다.  
  
4.  이 경고를 해결 하려면 'if' 문을 사용 하 여 반환 값을 테스트 합니다. 코드에는 다음 코드와 유사 해야 합니다.  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5.  주석 프로젝트를 다시 작성 합니다.  
  
     프로젝트 경고 또는 오류 없이 빌드됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [연습: 관리 코드의 코드 오류 분석](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)



---
title: TableAdapter 사용 하 여 데이터베이스에 직접 액세스 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- databases [Visual Basic], accessing with a TableAdapter
- DBDirect methods
- datasets [Visual Basic], adding to projects
- data [Visual Studio], saving
- TableAdapter.Delete method
- GenerateDbDirectMethods property
- TableAdapter.Insert method
- TableAdapter.GenerateDBDirectMethods property
- TableAdapter.Update method
- saving data
- TableAdapters
ms.assetid: 012c5924-91f7-4790-b2a6-f51402b7014b
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a592a185ad3dd01f881526e0b9471e3f5e969a94
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49178453"
---
# <a name="directly-access-the-database-with-a-tableadapter"></a>TableAdapter를 사용하여 데이터베이스에 직접 액세스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
외에 `InsertCommand`, `UpdateCommand`, 및 `DeleteCommand`, Tableadapter는 데이터베이스에 대해 직접 실행할 수 있는 메서드를 사용 하 여 만들어집니다. 이러한 메서드 (`TableAdapter.Insert`, `TableAdapter.Update`, 및 `TableAdapter.Delete`) 데이터베이스에서 직접 데이터를 조작 하기 위해 호출할 수 있습니다.  
  
 이러한 직접 메서드를 만드는 않으려면 TableAdapter의 설정 `GenerateDbDirectMethods` 속성을 `false` 에 **속성** 창입니다. TableAdapter의 기본 쿼리 외에도 TableAdapter에 쿼리를 추가 하는 경우 이러한 DbDirect 메서드를 생성 하지 않는 독립 실행형 쿼리 됩니다.  
  
## <a name="sendcommandsdirectly-to-a-database"></a>데이터베이스에 Sendcommandsdirectly  
 수행 하려는 작업을 수행 하는 TableAdapter DbDirect 메서드를 호출 합니다.  
  
#### <a name="to-insert-new-records-directly-into-a-database"></a>데이터베이스에 직접 새 레코드를 삽입 하려면  
  
-   TableAdapter의 호출 `Insert` 메서드를 매개 변수로 각 열에 대 한 값을 전달 합니다. 다음 절차에서는 `Region` 테이블 Northwind databaseas의 예입니다.  
  
    > [!NOTE]
    >  인스턴스에 사용할 수 없는 경우 사용 하려는 TableAdapter를 인스턴스화하십시오.  
  
     [!code-csharp[VbRaddataSaving#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#15)]
     [!code-vb[VbRaddataSaving#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#15)]  
  
#### <a name="to-update-records-directly-in-a-database"></a>데이터베이스에서 직접 레코드를 업데이트 하려면  
  
-   TableAdapter의 호출 `Update` 메서드를 매개 변수로 각 열에 대 한 새 및 원래 값을 전달 합니다.  
  
    > [!NOTE]
    >  인스턴스에 사용할 수 없는 경우 사용 하려는 TableAdapter를 인스턴스화하십시오.  
  
     [!code-csharp[VbRaddataSaving#18](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#18)]
     [!code-vb[VbRaddataSaving#18](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#18)]  
  
#### <a name="to-delete-records-directly-from-a-database"></a>데이터베이스에서 직접 레코드를 삭제 하려면  
  
-   TableAdapter의 호출 `Delete` 의 매개 변수로 각 열에 대 한 값을 전달 하는 메서드를 `Delete` 메서드. 다음 절차에서는 `Region` 테이블 Northwind databaseas의 예입니다.  
  
    > [!NOTE]
    >  인스턴스에 사용할 수 없는 경우 사용 하려는 TableAdapter를 인스턴스화하십시오.  
  
     [!code-csharp[VbRaddataSaving#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Class1.cs#21)]
     [!code-vb[VbRaddataSaving#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>참고 항목  
 [TableAdapter를 사용하여 데이터 집합 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)


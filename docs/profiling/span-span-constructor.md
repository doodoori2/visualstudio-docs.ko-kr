---
title: span::span 생성자 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::span::span
helpviewer_keywords:
- Concurrency::diagnostic::span constructor
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b04f9edc946b83f8785c6a6fb3e9720db4840f0
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596200"
---
# <a name="spanspan-constructor"></a>span::span 생성자
`span` 클래스의 새 인스턴스를 초기화합니다.

## <a name="syntax"></a>구문

```cpp
span(
   const marker_series& _Series,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
span(
   const marker_series& _Series,
   marker_importance _Importance,
   int _Category,
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>매개 변수
 `_Series` 유효한 표식 계열 컨텍스트입니다.

 `_Format` 인수 목록의 개체에 해당하는 0개 이상의 서식 항목과 결합된 텍스트를 포함하는 합성 서식 문자열입니다.

 `_Importance` 중요도 수준.

 `_Category` 범주.

## <a name="requirements"></a>요구 사항
 **헤더:** *cvmarkersobj.h*

 **네임스페이스:** Concurrency::diagnostic

 ## <a name="see-also"></a>참고 항목
- [span 클래스](../profiling/span-class.md)
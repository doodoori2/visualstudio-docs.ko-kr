---
title: 'CA2004: GC.KeepAlive에 대한 호출을 제거하세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
helpviewer_keywords:
- RemoveCallsToGCKeepAlive
- CA2004
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4520649050e6e4004b2c8864d5c081897852826c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55910105"
---
# <a name="ca2004-remove-calls-to-gckeepalive"></a>CA2004: GC.KeepAlive에 대한 호출을 제거하세요.

|||
|-|-|
|TypeName|RemoveCallsToGCKeepAlive|
|CheckId|CA2004|
|범주|Microsoft.Reliability|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 클래스를 사용 하 여 `SafeHandle` 여전히에 대 한 호출을 포함 하지만 `GC.KeepAlive`합니다.

## <a name="rule-description"></a>규칙 설명
 변환 하는 경우 `SafeHandle` 사용에 대 한 모든 호출을 제거 `GC.KeepAlive` (개체). 이 경우 클래스 해야 호출할 필요가 없습니다 `GC.KeepAlive`, 종료 자가 없는 있지만 의존 가정 `SafeHandle` 에 OS 핸들을 완료 합니다.  하지만 비용에 대 한 호출을 두면 `GC.KeepAlive` 인식 성능을 기준으로 무시할 수 없습니다는에 대 한 호출 `GC.KeepAlive` 필요 하거나 더 이상 존재 하는 문제는 코드를 하기 어렵게 만듭니다 수명을 해결 하는 데 충분 유지 관리 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 에 대 한 호출을 제거 `GC.KeepAlive`합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하는 경우
 변환할 기술적으로 올바르지 않은 경우에이 경고를 표시 하지 않을 수 `SafeHandle` 클래스에서 사용 합니다.
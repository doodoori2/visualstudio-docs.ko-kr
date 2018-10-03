---
title: 1x1 뷰포트 크기 변형 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dbc3247-00f5-4644-8ff9-72e9febcf09a
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c0052a2d59dbcef1d7ea32eab789ab955750f3f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47565249"
---
# <a name="1x1-viewport-size-variant"></a>1x1 뷰포트 크기 변형
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목의 최신 버전에서 찾을 수 있습니다 [1x1 뷰포트 크기 변형](https://docs.microsoft.com/visualstudio/debugger/graphics/1x1-viewport-size-variant)합니다.  
  
모든 렌더링 대상의 뷰포트 크기를 1x1 픽셀로 줄입니다.  
  
## <a name="interpretation"></a>해석  
 뷰포트가 더 작으면 음영 처리해야 하는 픽셀 수가 줄어들지만 처리해야 하는 꼭짓점 수가 줄지는 않습니다. 뷰포트 크기를 1x1픽셀로 설정하면 앱에서 픽셀 음영이 효과적으로 제거됩니다.  
  
 이러한 변형으로 성능이 크게 향상되면 앱에서 채우기 속도를 너무 많이 사용함을 나타낼 수 있습니다. 이는 선택한 해상도가 대상 플랫폼에 비해 너무 높거나 앱에서 나중에 덮어쓰기(overdraw)한 픽셀을 음영 처리하는 데 상당한 시간이 소요됨을 나타낼 수 있습니다. 이 결과는 프레임 버퍼의 크기를 줄이거나 overdraw 양을 줄이면 앱의 성능이 향상된다는 것을 알려줍니다.  
  
## <a name="remarks"></a>설명  
 `ID3D11DeviceContext::OMSetRenderTargets` 또는 `ID3D11DeviceContext::RSSetViewports`를 호출한 후에는 항상 뷰포트 크기가 1x1로 다시 설정됩니다.  
  
## <a name="example"></a>예제  
 이 변형은 다음과 같은 코드를 사용하여 재현할 수 있습니다.  
  
```  
D3D11_VIEWPORT viewport;  
viewport.TopLeftX = 0;  
viewport.TopLeftY = 0;  
viewport.Width = 1;  
viewport.Height = 1;  
d3d_context->RSSetViewports(1, &viewport);  
```



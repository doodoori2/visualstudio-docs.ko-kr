---
title: 'Idiasession:: Findsymbolbyrvaex | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::findSymbolByRVAEx method
ms.assetid: 61344966-fed4-4c02-9e27-20356ec2ef7c
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f507258a0c4eec9ee550d781029b7dbf0ced7b28
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51776072"
---
# <a name="idiasessionfindsymbolbyrvaex"></a>IDiaSession::findSymbolByRVAEx
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

포함 된 단어나 가장 가까운 지정 된 가상 RVA (상대 주소) 및 오프셋에 지정 된 기호 형식을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT findSymbolByRVAEx (   
   DWORD        rva,  
   SymTagEnum   symtag,  
   IDiaSymbol** ppSymbol,  
   LONG*        displacement  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `rva`  
 [in] RVA를 지정합니다.  
  
 `symtag`  
 [in] 찾을 기호 형식입니다. 값에서 수행 되는 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md) 열거형입니다.  
  
 `ppSymbol`  
 [out] 반환 된 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) 기호를 나타내는 개체를 검색 합니다.  
  
 `displacement`  
 [out] 에 지정 된 상대 가상 주소 오프셋을 지정 하는 값을 반환 합니다 `rva`합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="example"></a>예제  
  
```cpp#  
IDiaSymbol* pFunc;  
LONG disp = 0;  
pSession->findSymbolByRVAEx( rva, SymTagFunction, &pFunc, &disp );  
```  
  
## <a name="see-also"></a>참고 항목  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 열거형](../../debugger/debug-interface-access/symtagenum.md)




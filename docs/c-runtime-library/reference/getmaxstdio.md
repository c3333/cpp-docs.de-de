---
title: _getmaxstdio | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getmaxstdio
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getmaxstdio
- getmaxstdio
dev_langs:
- C++
helpviewer_keywords:
- files [C++], number open
- _getmaxstdio function
- getmaxstdio function
- open files, getting number
ms.assetid: 700ca8ce-4a8c-4e00-9467-dfa9d6b831a0
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: db700e385fe59d5ff6cc7448c17444cb2b0e8796
ms.contentlocale: de-de
ms.lasthandoff: 10/09/2017

---
# <a name="getmaxstdio"></a>_getmaxstdio
Gibt die Anzahl der Dateien an, die auf der E/A-Ebene des Streams gleichzeitig geöffnet sein können.  
  
## <a name="syntax"></a>Syntax  
  
```  
int _getmaxstdio( void );  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt eine Zahl zurück, die die Anzahl der Dateien darstellt, die derzeit gleichzeitig auf der Ebene des `stdio` geöffnet sein können.  
  
## <a name="remarks"></a>Hinweise  
 Verwenden Sie [_setmaxstdio](../../c-runtime-library/reference/setmaxstdio.md), um die Anzahl der Dateien zu konfigurieren, die auf der Ebene von `stdio` gleichzeitig geöffnet sein können.  
  
## <a name="requirements"></a>Anforderungen  
  
|Routine|Erforderlicher Header|  
|-------------|---------------------|  
|`_getmaxstdio`|\<stdio.h>|  
  
 Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md) in der Einführung.  
  
## <a name="example"></a>Beispiel  
  
```  
// crt_setmaxstdio.c  
// The program retrieves the maximum number  
// of open files and prints the results  
// to the console.  
  
#include <stdio.h>  
  
int main()  
{  
   printf( "%d\n", _getmaxstdio());  
  
   _setmaxstdio(2048);  
  
   printf( "%d\n", _getmaxstdio());  
}  
```  
  
```Output  
512  
2048  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Stream-E/A](../../c-runtime-library/stream-i-o.md)
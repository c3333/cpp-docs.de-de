---
title: clog10, clog10f, clog10l | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- clog10
- clog10f
- clog10l
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- clog10
- clog10f
- clog10l
- complex/clog10
- complex/clog10f
- complex/clog10l
dev_langs: C++
helpviewer_keywords:
- clog10 function
- clog10f function
- clog10l function
ms.assetid: 2ddae00d-ef93-4441-add3-f4d58358401b
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: bab5be9a8c686c2c6cd207232ddc6f98d11aa519
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="clog10-clog10f-clog10l"></a>clog10, clog10f, clog10l
Ruft den Logarithmus zur Basis 10 einer komplexen Zahl ab.  
  
## <a name="syntax"></a>Syntax  
  
```  
_Dcomplex clog10(   
   _Dcomplex z   
);  
_Fcomplex clog10(   
  _Fcomplex z   
);  // C++ only  
_Lcomplex clog10(   
   _Lcomplex z   
);  // C++ only  
_Fcomplex clog10f(   
   _Fcomplex z   
);  
_Lcomplex clog10l(   
   _Lcomplex z   
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `z`  
 Die Basis des Logarithmus.  
  
## <a name="return-value"></a>Rückgabewert  
 Die möglichen Rückgabewerte sind:  
  
|z Parameter|Rückgabewert|  
|-----------------|------------------|  
|Positiv|Der Logarithmus zur Basis 10 von z|  
|Zero|- ∞|  
|Negativ|NaN|  
|NaN|NaN|  
|+ ∞|+ ∞|  
  
## <a name="remarks"></a>Hinweise  
 Da C++ das Überladen zulässt, können Sie Überladungen von `clog10` aufrufen, die `_Fcomplex`- und `_Lcomplex`-Werte verwenden und zurückgeben. In einem C-Programm nimmt `clog10` immer einen `_Dcomplex` -Wert an, und gibt auch einen solchen zurück.  
  
## <a name="requirements"></a>Anforderungen  
  
|Routine|C-Header|C++-Header|  
|-------------|--------------|------------------|  
|`clog10`,               `clog10f`, `clogl`|\<complex.h>|\<ccomplex>|  
  
 Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md) in der Einführung.  
  
## <a name="see-also"></a>Siehe auch  
 [CRT-Funktionsreferenz (alphabetisch)](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [cexp, cexpf, cexpl](../../c-runtime-library/reference/cexp-cexpf-cexpl.md)   
 [cpow, cpowf, cpowl](../../c-runtime-library/reference/cpow-cpowf-cpowl.md)   
 [clog, clogf, clogl](../../c-runtime-library/reference/clog-clogf-clogl.md)
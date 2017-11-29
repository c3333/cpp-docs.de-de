---
title: modf, modff, modfl | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- modff
- modf
- modfl
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
- modff
- _modfl
- modf
- modfl
- math/modf
- math/modff
- math/modfl
dev_langs: C++
helpviewer_keywords:
- modf function
- modff function
- modfl function
ms.assetid: b1c7abf5-d476-43ca-a03c-02072a86e32d
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 72568970159c1b334232bb81f0295d829a5221af
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="modf-modff-modfl"></a>modf, modff, modfl
Teilt einen Gleitkommawert in Nachkommastellen und ganze Zahlen.  
  
## <a name="syntax"></a>Syntax  
  
```  
double modf(  
   double x,  
   double * intptr   
);  
float modf(  
   float x,  
   float * intptr  
);  // C++ only  
long double modf(  
   long double x,  
   long double * intptr  
);  // C++ only  
float modff(  
   float x,  
   float * intptr   
);  
long double modfl(  
   long double x,  
   long double * intptr  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 *x*  
 Gleitkommawert.  
  
 `intptr`  
 Zeiger auf gespeicherten Ganzzahlbereich.  
  
## <a name="return-value"></a>Rückgabewert  
 Diese Funktion gibt den Bruchteil von *x* mit Vorzeichen zurück. Es gibt keine Fehlerrückgabe.  
  
## <a name="remarks"></a>Hinweise  
 Die Funktionen `modf` teilen den Gleitkommawert `x` in Nachkommastellen und ganze Zahlen, die alle die gleichen Vorzeichen wie `x` haben. Der Bruchteil von `x` mit Vorzeichen wird zurückgegeben. Der Ganzzahlbereich wird als Gleitkommawert unter `intptr.` gespeichert.  
  
 `modf` ist eine Implementierung, die SIMD-Streamingerweiterungen 2 (SSE2) verwendet. Informationen und Einschränkungen zur Verwendung der SSE2-Implementierung finden Sie unter [_set_SSE2_enable](../../c-runtime-library/reference/set-sse2-enable.md).  
  
 Da C++ das Überladen zulässt, können Sie Überladungen von `modf` aufrufen, die Parameter für `float` oder `long double` verwenden und zurückgeben. In einem C-Programm verwendet `modf` immer zwei double-Werte und gibt einen double-Wert zurück.  
  
## <a name="requirements"></a>Anforderungen  
  
|Routine|Erforderlicher Header|  
|-------------|---------------------|  
|`modf`, `modff`, `modfl`|C: \<math.h><br /><br /> C++: , \<cmath> oder \<math.h>|  
  
 Zusätzliche Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md) in der Einführung.  
  
## <a name="libraries"></a>Bibliotheken  
 Alle Versionen der [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Beispiel  
  
```  
// crt_modf.c  
  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   double x, y, n;  
  
   x = -14.87654321;      /* Divide x into its fractional */  
   y = modf( x, &n );     /* and integer parts            */  
  
   printf( "For %f, the fraction is %f and the integer is %.f\n",   
           x, y, n );  
}  
```  
  
## <a name="output"></a>Ausgabe  
  
```  
For -14.876543, the fraction is -0.876543 and the integer is -14  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)   
 [frexp](../../c-runtime-library/reference/frexp.md)   
 [ldexp](../../c-runtime-library/reference/ldexp.md)
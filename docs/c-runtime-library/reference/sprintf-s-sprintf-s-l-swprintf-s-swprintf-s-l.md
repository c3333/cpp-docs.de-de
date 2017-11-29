---
title: sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _swprintf_s_l
- _sprintf_s_l
- swprintf_s
- sprintf_s
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
apitype: DLLExport
f1_keywords:
- swprintf_s
- sprintf_s
- stdio/sprintf_s
- stdio/swprintf_s
- stdio/_sprintf_s_l
- stdio/_swprintf_s_l
- _sprintf_s_l
- _swprintf_s_l
dev_langs: C++
helpviewer_keywords:
- stprintf_s function
- stprintf_s_l function
- swprintf_s_l function
- sprintf_s function
- swprintf_s function
- _swprintf_s_l function
- sprintf_s_l function
- _stprintf_s_l function
- _stprintf_s function
- _sprintf_s_l function
- formatted text [C++]
ms.assetid: 424f0a29-22ef-40e8-b565-969f5f57782f
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 12b5799c9471ffaf8328d4f8aa6a994319e4f30f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/24/2017
---
# <a name="sprintfs-sprintfsl-swprintfs-swprintfsl"></a>sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l
Schreiben Sie formatierte Daten in eine Zeichenfolge. Dies sind Versionen von [sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md) mit Sicherheitsverbesserungen, wie in [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.  
  
## <a name="syntax"></a>Syntax  
  
```  
int sprintf_s(  
   char *buffer,  
   size_t sizeOfBuffer,  
   const char *format,  
   ...   
);  
int _sprintf_s_l(  
   char *buffer,  
   size_t sizeOfBuffer,  
   const char *format,  
   locale_t locale,  
   ...   
);  
int swprintf_s(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   const wchar_t *format,  
   ...  
);  
int _swprintf_s_l(  
   wchar_t *buffer,  
   size_t sizeOfBuffer,  
   const wchar_t *format,  
   locale_t locale,  
   ...  
);  
template <size_t size>  
int sprintf_s(  
   char (&buffer)[size],  
   const char *format,  
   ...   
); // C++ only  
template <size_t size>  
int swprintf_s(  
   wchar_t (&buffer)[size],  
   const wchar_t *format,  
   ...  
); // C++ only  
```  
  
#### <a name="parameters"></a>Parameter  
 `buffer`  
 Speicherort für die Ausgabe  
  
 `sizeOfBuffer`  
 Die maximale Anzahl der zu speichernden Zeichen.  
  
 `format`  
 Formatsteuerzeichenfolge  
  
 `...`  
 Optionale Argumente, die formatiert werden müssen  
  
 `locale`  
 Das zu verwendende Gebietsschema.  
  
 Weitere Informationen finden Sie unter [Formatangaben](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## <a name="return-value"></a>Rückgabewert  
 Die Anzahl geschriebener Zeichen oder -1, wenn ein Fehler aufgetreten. Wenn `buffer` oder `format` ein NULL-Zeiger ist, geben `sprintf_s` und `swprintf_s` -1 zurück und stellen `errno` auf `EINVAL`ein.  
  
 `sprintf_s` gibt die in `buffer`gespeicherte Byteanzahl zurück. Das beendende NULL-Zeichen wird dabei nicht mitgezählt. `swprintf_s` gibt die Anzahl der in `buffer` gespeicherten Breitzeichen zurück. Das beendende NULL-Breitzeichen wird dabei nicht mitgezählt.  
  
## <a name="remarks"></a>Hinweise  
 Die `sprintf_s`-Funktion formatiert und speichert eine Reihe von Zeichen und Werte in `buffer`. Jedes `argument` (falls vorhanden) wird entsprechend der jeweiligen Formatangabe in `format`konvertiert und ausgegeben. Das Format besteht aus normalen Zeichen und hat die gleiche Form und Funktion wie das `format` -Argument für [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md). Ein NULL-Zeichen wird nach dem letzten geschriebenen Zeichen angefügt. Wenn der Kopiervorgang zwischen Zeichenfolgen ausgeführt wird, die sich überschneiden, ist das Verhalten nicht definiert.  
  
 Ein Hauptunterschied zwischen `sprintf_s` und `sprintf` besteht darin, dass `sprintf_s` die Formatzeichenfolge auf gültige Formatierungszeichen überprüft. Dagegen überprüft `sprintf` nur, ob es sich bei der Formatzeichenfolge oder beim Puffer um einen `NULL` -Zeiger handelt. Wenn bei einer der beiden Überprüfungen ein Fehler auftritt, wird der Handler für ungültige Parameter aufgerufen, wie in [Parameter Validation](../../c-runtime-library/parameter-validation.md)beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt die Funktion -1 zurück und stellt `errno` auf `EINVAL`ein.  
  
 Der andere Hauptunterschied zwischen `sprintf_s` und `sprintf` besteht darin, dass `sprintf_s` einen Längenparameter akzeptiert, der die Größe des Ausgabepuffers in den Zeichen angibt. Wenn der Puffer für den formatierten Text einschließlich abschließendem NULL-Zeichen zu klein ist, wird er auf eine leere Zeichenfolge festgelegt, indem ein NULL-Zeichen in `buffer[0]`gespeichert wird, und der Handler für ungültige Parameter wird aufgerufen. Im Gegensatz zu `_snprintf`garantiert `sprintf_s` , dass der Puffer mit NULL endet (es sei denn, die Puffergröße ist gleich null).  
  
 `swprintf_s` ist eine Breitzeichen-Version von `sprintf_s`. Die Zeigerargumente zu `swprintf_s` sind Breitzeichen-Zeichenfolgen. Die Erkennung von Codierungsfehlern in `swprintf_s` unterscheidet sich möglicherweise von der in `sprintf_s`. Die Versionen dieser Funktionen mit dem `_l` -Suffix sind beinahe identisch, verwenden jedoch den ihnen übergebenen Gebietsschemaparameter anstelle des aktuellen Threadgebietsschemas.  
  
 In C++ wird die Verwendung dieser Funktionen durch Vorlagenüberladungen vereinfacht. Die Überladungen können automatisch Rückschlüsse auf die Pufferlänge ziehen (wodurch kein Größenargument mehr angegeben werden muss), und sie können automatisch die älteren, nicht sicheren Funktionen durch ihre neueren, sicheren Entsprechungen ersetzen. Weitere Informationen finden Sie unter [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md).  
  
 Es gibt Versionen von `sprintf_s` , die eine zusätzliche Kontrolle darüber bieten, was geschieht, wenn der Puffer zu klein ist. Weitere Informationen finden Sie unter [_snprintf_s, _snprintf_s_l, _snwprintf_s, _snwprintf_s_l](../../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md).  
  
### <a name="generic-text-routine-mappings"></a>Zuordnung generischer Textroutinen  
  
|TCHAR.H-Routine|_UNICODE und _MBCS nicht definiert.|_MBCS definiert|_UNICODE definiert|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_stprintf_s`|`sprintf_s`|`sprintf_s`|`swprintf_s`|  
|`_stprintf_s_l`|`_sprintf_s_l`|`_sprintf_s_l`|`_swprintf_s_l`|  
  
## <a name="requirements"></a>Anforderungen  
  
|Routine|Erforderlicher Header|  
|-------------|---------------------|  
|`sprintf_s`, `_sprintf_s_l`|C: \<stdio.h><br /><br /> C++: \<cstdio> oder \<stdio.h>|  
|`swprintf_s`, `_swprintf_s_l`|C: \<stdio.h> oder \<wchar.h><br /><br /> C++: \<cstdio>, \<cwchar>, \<stdio.h> oder \<wchar.h>|  
  
 Weitere Informationen zur Kompatibilität finden Sie unter [Kompatibilität](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Beispiel  
  
```  
// crt_sprintf_s.c  
// This program uses sprintf_s to format various  
// data and place them in the string named buffer.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   char  buffer[200], s[] = "computer", c = 'l';  
   int   i = 35, j;  
   float fp = 1.7320534f;  
  
   // Format and print various data:   
   j  = sprintf_s( buffer, 200,     "   String:    %s\n", s );  
   j += sprintf_s( buffer + j, 200 - j, "   Character: %c\n", c );  
   j += sprintf_s( buffer + j, 200 - j, "   Integer:   %d\n", i );  
   j += sprintf_s( buffer + j, 200 - j, "   Real:      %f\n", fp );  
  
   printf_s( "Output:\n%s\ncharacter count = %d\n", buffer, j );  
}  
```  
  
```Output  
Output:  
   String:    computer  
   Character: l  
   Integer:   35  
   Real:      1.732053  
  
character count = 79  
```  
  
## <a name="example"></a>Beispiel  
  
```  
// crt_swprintf_s.c  
// wide character example  
// also demonstrates swprintf_s returning error code  
#include <stdio.h>  
  
int main( void )  
{  
   wchar_t buf[100];  
   int len = swprintf_s( buf, 100, L"%s", L"Hello world" );  
   printf( "wrote %d characters\n", len );  
   len = swprintf_s( buf, 100, L"%s", L"Hello\xffff world" );  
   // swprintf_s fails because string contains WEOF (\xffff)  
   printf( "wrote %d characters\n", len );  
}  
```  
  
```Output  
wrote 11 characters  
wrote -1 characters  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Stream-E/A](../../c-runtime-library/stream-i-o.md)   
 [fprintf, _fprintf_l, fwprintf, _fwprintf_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf, _printf_l, wprintf, _wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf, _scanf_l, wscanf, _wscanf_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf, _sscanf_l, swscanf, _swscanf_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vprintf-Funktionen](../../c-runtime-library/vprintf-functions.md)
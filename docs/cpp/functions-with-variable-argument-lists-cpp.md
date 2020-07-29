---
title: Funktionen mit Variablenargumentlisten (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], variable number of
- variable argument lists
- declarators, functions
- argument lists [C++], variable number of
- declaring functions [C++], variables
- function calls, variable number of arguments
ms.assetid: 27c2f83a-21dd-44c6-913c-2834cb944703
ms.openlocfilehash: 99f1f5cec2350f99bf2993947870f25e357ffc23
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213423"
---
# <a name="functions-with-variable-argument-lists--c"></a>Funktionen mit Variablenargumentlisten (C++)

Funktionsdeklarationen, in denen der letzte Member von  das Auslassungszeichen (...) ist, können eine variable Anzahl von Argumenten akzeptieren. In diesen Fällen stellt C++ die Typüberprüfung nur für die explizit deklarierten Argumente bereit. Sie können Variablenargumentlisten verwenden, wenn Sie eine Funktion so allgemein gestalten müssen, dass sogar die Anzahl und Typen von Argumenten variieren können. Die-Funktions Familie ist ein Beispiel für Funktionen, die Variablen Argumentlisten verwenden. `printf` *Argument-declaration-list*

## <a name="functions-with-variable-arguments"></a>Funktionen mit Variablenargumenten

Um auf Argumente nach den deklarierten Argumenten zuzugreifen, verwenden Sie die in der standardmäßigen Includedatei enthaltenen Makros, \<stdarg.h> wie unten beschrieben.

**Microsoft-spezifisch**

Mit Microsoft C++ kann das Auslassungszeichen als Argument angegeben werden, wenn das Auslassungszeichen das letzte Argument ist und ein Komma als Präfix hat. Daher ist die Deklaration `int Func( int i, ... );` gültig, `int Func( int i ... );` jedoch nicht.

**Ende Microsoft-spezifisch**

Die Deklaration einer Funktion, die eine variable Anzahl von Argumenten akzeptiert, erfordert selbst dann mindestens ein Platzhalterargument, wenn sie nicht verwendet wird. Wenn dieses Platzhalterargument nicht angegeben ist, gibt es keine Möglichkeit, auf die übrigen Argumente zugreifen.

Wenn Argumente des Typs **`char`** als Variablen Argumente übermittelt werden, werden Sie in den Typ konvertiert **`int`** . Wenn Argumente des Typs **`float`** als Variablen Argumente übermittelt werden, werden Sie ebenso in den Typ konvertiert **`double`** . Argumente anderer Typen unterliegen den üblichen Ganzzahl- und Gleitkomma-Erweiterungen. Weitere Informationen finden Sie unter [Standard Konvertierungen](standard-conversions.md) .

Funktionen, für die Variablenlisten erforderlich sind, werden mithilfe von Auslassungspunkten (...) in der Argumentliste deklariert. Verwenden Sie die Typen und Makros, die in der \<stdarg.h> include-Datei beschrieben werden, um auf Argumente zuzugreifen, die von einer Variablen Liste weitergegeben werden. Weitere Informationen zu diesen Makros finden Sie unter [va_arg, va_copy va_end, va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md). in der Dokumentation für die C-Laufzeitbibliothek.

Im folgenden Beispiel wird gezeigt, wie die Makros zusammen mit dem-Typ (deklariert in \<stdarg.h> ) funktionieren:

```cpp
// variable_argument_lists.cpp
#include <stdio.h>
#include <stdarg.h>

//  Declaration, but not definition, of ShowVar.
void ShowVar( char *szTypes, ... );
int main() {
   ShowVar( "fcsi", 32.4f, 'a', "Test string", 4 );
}

//  ShowVar takes a format string of the form
//   "ifcs", where each character specifies the
//   type of the argument in that position.
//
//  i = int
//  f = float
//  c = char
//  s = string (char *)
//
//  Following the format specification is a variable
//  list of arguments. Each argument corresponds to
//  a format character in the format string to which
// the szTypes parameter points
void ShowVar( char *szTypes, ... ) {
   va_list vl;
   int i;

   //  szTypes is the last argument specified; you must access
   //  all others using the variable-argument macros.
   va_start( vl, szTypes );

   // Step through the list.
   for( i = 0; szTypes[i] != '\0'; ++i ) {
      union Printable_t {
         int     i;
         float   f;
         char    c;
         char   *s;
      } Printable;

      switch( szTypes[i] ) {   // Type to expect.
         case 'i':
            Printable.i = va_arg( vl, int );
            printf_s( "%i\n", Printable.i );
         break;

         case 'f':
             Printable.f = va_arg( vl, double );
             printf_s( "%f\n", Printable.f );
         break;

         case 'c':
             Printable.c = va_arg( vl, char );
             printf_s( "%c\n", Printable.c );
         break;

         case 's':
             Printable.s = va_arg( vl, char * );
             printf_s( "%s\n", Printable.s );
         break;

         default:
         break;
      }
   }
   va_end( vl );
}
//Output:
// 32.400002
// a
// Test string
```

Das vorherige Beispiel verdeutlicht diese wichtigen Konzepte:

1. Sie müssen eine Listenmarkierung als Variable vom Typ `va_list` erstellen, bevor auf beliebige Variablenargumente zugegriffen wird. Im vorherigen Beispiel wird die Markierung als `vl` bezeichnet.

1. Auf die einzelnen Argumente wird unter Verwendung des Makros `va_arg` zugegriffen. Sie müssen dem `va_arg`-Makro den Typ des abzurufenden Arguments mitteilen, sodass es die richtige Anzahl von Bytes aus dem Stapel übertragen kann. Wenn Sie einen falschen Typ Größe festlegen, die sich von der unterscheidet, die vom aufrufenden Programm für `va_arg` angegeben wurde, sind die Ergebnisse unvorhersehbar.

1. Sie sollten das erhaltene Ergebnis explizit in den gewünschten Typ umwandeln, indem Sie das `va_arg`-Makro verwenden.

Sie müssen das `va_end`-Makro aufrufen, um die Variablenargumentverarbeitung zu beenden.

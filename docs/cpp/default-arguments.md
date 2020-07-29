---
title: Standardargumente
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function declarators
- functions [C++], default arguments
- declaring functions [C++], declarators
- default arguments
- arguments [C++], default
- defaults [C++], arguments
ms.assetid: d32cf516-05cb-4d4d-b169-92f5649fdfa2
ms.openlocfilehash: ef0c81501fe37bd27a23daf2dd1c58b3e6a4f6c0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221730"
---
# <a name="default-arguments"></a>Standardargumente

In vielen Fällen haben Funktionen Argumente, die so selten verwendet werden, dass ein Standardwert genügt. Für dieses Szenario ermöglicht die Standardargumentfunktion, nur die Argumente für eine Funktion anzugeben, die für einen bestimmten Aufruf von Bedeutung sind. Um dieses Konzept zu veranschaulichen, sehen Sie sich das Beispiel unter [Funktions Überladung](../cpp/function-overloading.md)an.

```cpp
// Prototype three print functions.
int print( char *s );                  // Print a string.
int print( double dvalue );            // Print a double.
int print( double dvalue, int prec );  // Print a double with a
//  given precision.
```

Bei vielen Anwendungen kann ein angemessener Standardwert für `prec` angegeben werden, und die Anforderung für zwei Funktionen entfällt:

```cpp
// Prototype two print functions.
int print( char *s );                    // Print a string.
int print( double dvalue, int prec=2 );  // Print a double with a
//  given precision.
```

Die Implementierung der `print` Funktion wird leicht geändert, um die Tatsache widerzuspiegeln, dass nur eine solche Funktion für den Typ vorhanden ist **`double`** :

```cpp
// default_arguments.cpp
// compile with: /EHsc /c

// Print a double in specified precision.
//  Positive numbers for precision indicate how many digits
//  precision after the decimal point to show. Negative
//  numbers for precision indicate where to round the number
//  to the left of the decimal point.

#include <iostream>
#include <math.h>
using namespace std;

int print( double dvalue, int prec ) {
   // Use table-lookup for rounding/truncation.
   static const double rgPow10[] = {
      10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1, 10E0,
         10E1,  10E2,  10E3,  10E4, 10E5,  10E6
   };
   const int iPowZero = 6;
   // If precision out of range, just print the number.
   if( prec >= -6 && prec <= 7 )
      // Scale, truncate, then rescale.
      dvalue = floor( dvalue / rgPow10[iPowZero - prec] ) *
      rgPow10[iPowZero - prec];
   cout << dvalue << endl;
   return cout.good();
}
```

Um die neue `print`-Funktion aufrufen, verwenden Sie Code wie den folgenden:

```cpp
print( d );    // Precision of 2 supplied by default argument.
print( d, 0 ); // Override default argument to achieve other
//  results.
```

Beachten Sie diese Punkte, wenn Standardargumente verwendet werden:

- Standardargumente werden nur in Funktionsaufrufen verwendet, in denen nachfolgende Argumente ausgelassen werden – sie müssen die letzten Argumente sein. Daher ist der folgende Code ungültig:

    ```cpp
    int print( double dvalue = 0.0, int prec );
    ```

- Ein Standardargument kann nicht in späteren Deklarationen neu definiert werden, auch wenn die Neudefinition mit dem Original identisch ist. Daher generiert der folgende Code einen Fehler:

    ```cpp
    // Prototype for print function.
    int print( double dvalue, int prec = 2 );

    ...

    // Definition for print function.
    int print( double dvalue, int prec = 2 )
    {
    ...
    }
    ```

   Das Problem des Codes besteht darin, dass die Funktionsdeklaration in der Definition das Standardargument für `prec` neu definiert.

- Zusätzliche Standardargumente können durch neuere Deklarationen hinzugefügt werden.

- Standardargumente können für Zeiger auf Funktionen bereitgestellt werden. Beispiel:

    ```cpp
    int (*pShowIntVal)( int i = 0 );
    ```

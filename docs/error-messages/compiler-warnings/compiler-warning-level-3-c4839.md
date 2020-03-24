---
title: Compilerwarnung (Stufe 3) C4839
ms.date: 09/13/2018
f1_keywords:
- C4839
helpviewer_keywords:
- C4839
ms.assetid: f4f99066-9258-4330-81a8-f4a75a1d95ee
ms.openlocfilehash: 2c238dc16359583bf55f7590d2ce7c0363d66df7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198574"
---
# <a name="compiler-warning-level-3-c4839"></a>Compilerwarnung (Stufe 3) C4839

> nicht standardmäßige Verwendung der '*Type*'-Klasse als Argument für eine Variadic-Funktion

Klassen oder Strukturen, die an eine Variadic-Funktion wie z. b. `printf` übermittelt werden, müssen trivial kopiert werden können. Wenn solche Objekte übergeben werden, macht der Compiler einfach eine bitweise Kopie und ruft keinen Konstruktor oder Destruktor auf.

Diese Warnung ist ab Visual Studio 2017 verfügbar.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C4839 generiert:

```cpp
// C4839.cpp
// compile by using: cl /EHsc /W3 C4839.cpp
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function
                        // note: the constructor and destructor will not be called;
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function
}
```

Sie können eine Memberfunktion aufrufen, die einen einfachen kopierbaren Typ zurückgibt, um den Fehler zu beheben,

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

Für Zeichen folgen, die mit `CStringW`erstellt und verwaltet werden, sollte die angegebene `operator LPCWSTR()` verwendet werden, um ein `CStringW` Objekt in den von der Format Zeichenfolge erwarteten C-Zeiger umzuwandeln.

```cpp
    CStringW str1;
    CStringW str2;
    // ...
    str1.Format("%s", static_cast<LPCWSTR>(str2));
```

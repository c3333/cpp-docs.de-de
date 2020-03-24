---
title: Compilerwarnung (Stufe 1) C4067
ms.date: 11/04/2016
f1_keywords:
- C4067
helpviewer_keywords:
- C4067
ms.assetid: 1d10353e-8cd5-4b01-9184-a06189b965a4
ms.openlocfilehash: 8bdd16f5c3182e4217e195475bdb4a9a0f60fa6f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164117"
---
# <a name="compiler-warning-level-1-c4067"></a>Compilerwarnung (Stufe 1) C4067

> unerwartete Token nach Präprozessordirektive-erwartet wurde ein Zeilen Vorstrich.

## <a name="remarks"></a>Bemerkungen

Der Compiler hat nach einer Präprozessordirektive zusätzliche Zeichen gefunden und ignoriert. Dies kann durch unerwartete Zeichen verursacht werden. eine häufige Ursache ist jedoch ein unzulässiges Semikolon nach der-Direktive. Diese Warnung wird nicht durch Kommentare verursacht. Die **/Za** -Compileroption aktiviert diese Warnung für mehr Präprozessordirektiven als die Standardeinstellung.

## <a name="example"></a>Beispiel

```cpp
// C4067a.cpp
// compile with: cl /EHsc /DX /W1 /Za C4067a.cpp
#include <iostream>
#include <string> s     // C4067
#if defined(X);         // C4067
std::string s{"X is defined"};
#else
std::string s{"X is not defined"};
#endif;                 // C4067 only under /Za
int main()
{
    std::cout << s << std::endl;
}
```

Um diese Warnung zu beheben, löschen Sie die unverstreuten Zeichen, oder verschieben Sie Sie in einen Kommentar Block. Bestimmte C4067-Warnungen können deaktiviert werden, indem die **/Za** -Compileroption entfernt wird.

```cpp
// C4067b.cpp
// compile with: cl /EHsc /DX /W1 C4067b.cpp
#include <iostream>
#include <string>
#if defined(X)
std::string s{"X is defined"};
#else
std::string s{"X is not defined"};
#endif
int main()
{
    std::cout << s << std::endl;
}
```

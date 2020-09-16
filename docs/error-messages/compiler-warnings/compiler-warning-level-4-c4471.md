---
title: Compilerwarnung (Stufe 4) C4471
ms.date: 04/24/2017
f1_keywords:
- C4471
helpviewer_keywords:
- C4471
ms.assetid: ccfd8bd5-bc1b-4be7-a6ea-0e3a7add6607
ms.openlocfilehash: 5b8c3ef419a4c6eaf9a674827cd5545a1f1b2bfe
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685501"
---
# <a name="compiler-warning-level-4-c4471"></a>Compilerwarnung (Stufe 4) C4471

'*Enumeration*': für eine vorwärts Deklaration einer Enumeration ohne Bereichs Einschränkung ist ein zugrunde liegender Typ erforderlich (int wird angenommen).

Eine vorwärts Deklaration einer Enumeration ohne Bereichs Einschränkung wurde ohne einen Spezifizierer für den zugrunde liegenden Typ gefunden. Standardmäßig geht Visual C++ davon aus, **`int`** dass der zugrunde liegende Typ für eine Enumeration ist. Dies kann zu Problemen führen, wenn ein anderer Typ in der Enumerationsdefinition verwendet wird, z. b. Wenn ein anderer expliziter Typ angegeben ist oder wenn ein anderer Typ implizit durch einen Initialisierer festgelegt wird. Möglicherweise haben Sie auch Portabilitäts Probleme. andere Compiler gehen nicht davon aus, dass **`int`** es sich um den zugrunde liegenden Typ einer Enumeration handelt.

Diese Warnung ist standardmäßig deaktiviert. Sie können/Wall oder/w*N*4471 verwenden, um es in der Befehlszeile zu aktivieren, oder Sie verwenden #Pragma [Warnung](../../preprocessor/warning.md) in der Quelldatei.

## <a name="examples"></a>Beispiele

In einigen Fällen ist diese Warnung falsch. Wenn eine vorwärts Deklaration für eine Enumeration nach der Definition angezeigt wird, kann diese Warnung ausgelöst werden. Beispielsweise ist dieser Code gültig, obwohl er C4471 verursachen kann:

```cpp
// C4471a.cpp
// Compile with: cl /c /w14471 C4471a.cpp
enum Example { item = 0x80000000UL };
enum Example;    // Spurious C4471
// ...
```

Im Allgemeinen ist es sicher, die vollständige Definition für eine Enumeration ohne Bereichs Einschränkung anstelle einer vorwärts Deklaration zu verwenden. Sie können die Definition in eine Header Datei einfügen und in Quelldateien einschließen, die darauf verweisen. Dies funktioniert in Code, der für c++ 98 und höher geschrieben wurde. Wir empfehlen diese Lösung für die Portabilität und einfache Wartung.

```cpp
// C4471b.cpp
// Compile with: cl /c /w14471 C4471b.cpp
enum Example;    // C4471
// To fix, replace the line above with the enumeration definition:
// enum Example { item = 0x80000000UL };
// ...
```

In c++ 11 können Sie einer Enumeration ohne Bereichs Einschränkung und ihrer vorwärts Deklaration einen expliziten Typ hinzufügen. Diese Lösung wird nur dann empfohlen, wenn eine komplexe Header-Inklusions Logik die Verwendung der Definition anstelle einer vorwärts Deklaration verhindert. Diese Lösung kann zu einem Wartungsproblem führen: Wenn Sie den zugrunde liegenden Typ ändern, der für die Enumerationsdefinition verwendet wird, müssen Sie auch alle vorwärts Deklarationen entsprechend ändern, oder Sie können in Ihrem Code zu stillen Fehlern führen. Sie können die vorwärts Deklaration in eine Header Datei einfügen, um dieses Problem zu minimieren.

```cpp
// C4471c.cpp
// Client code for enumeration defined in C4471d.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example;    // C4471, int assumed
// To fix, replace the lines above with the forward declarations:
// enum Example : unsigned;
// ...
```

```cpp
// C4471d.cpp
// Definition for enumeration used in C4471c.cpp
// Compile with: cl /c /w14471 C4471c.cpp C4471d.cpp
enum Example : unsigned { item = 0x80000000 }; // explicit type
// ...
```

Wenn Sie einen expliziten Typ für eine Enumeration angeben, empfiehlt es sich, auch die Warnung [C4369](compiler-warning-level-1-C4369.md)zu aktivieren, die standardmäßig aktiviert ist. Dies identifiziert Fälle, in denen ein Enumerationselement einen anderen Typ als den explizit angegebenen Typ erfordert.

Sie können den Code so ändern, dass er eine Bereichs bezogene Enum verwendet, eine neue Funktion in c++ 11. Sowohl die Definition als auch jeder Client Code, der den Enumerationstyp verwendet, muss so geändert werden, dass eine Bereichs bezogene Enumeration verwendet wird. Es wird empfohlen, eine Bereichs bezogene Enumeration zu verwenden, wenn Probleme mit der Namespace-Verunreinigung auftreten, da die Namen definierter Enumerationselemente auf den Gültigkeitsbereich der Enumeration beschränkt sind. Ein weiteres Feature einer Bereichs bezogenen Enumeration ist, dass seine Member nicht implizit in einen anderen integralen oder Enumerationstyp konvertiert werden können. Dies kann eine Quelle von geringfügigen Fehlern sein.

```cpp
// C4471e.cpp
// Client code for scoped enumeration defined in C4471f.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum Example;    // C4471
// To fix, replace the line above with the forward declaration:
// enum class Example;
// ...
```

```cpp
// C4471f.cpp
// Definition for scoped enumeration used in C4471e.cpp
// Compile with: cl /c /w14471 C4471e.cpp C4471f.cpp
enum class Example { item = 0 };
// ...
```

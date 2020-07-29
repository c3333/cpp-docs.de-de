---
title: Compilerfehler C2513
ms.date: 11/04/2016
f1_keywords:
- C2513
helpviewer_keywords:
- C2513
ms.assetid: ab5b21d3-61e2-4df7-8eea-6f14d6ba8620
ms.openlocfilehash: 96f2ccc29eed5c1fa4e29f69d18ae6503417f211
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212721"
---
# <a name="compiler-error-c2513"></a>Compilerfehler C2513

"Typ": keine Variable vor "=" deklariert

Der Typspezifizierer wird in der Deklaration ohne Variablen Bezeichner angezeigt.

Im folgenden Beispiel wird C2513 generiert:

```cpp
// C2513.cpp
int main() {
   int = 9;   // C2513
   int i = 9;   // OK
}
```

Dieser Fehler kann auch infolge einer für Visual Studio .NET 2003 abgeschlossenen compilerübereinstimmungs-Arbeit generiert werden: die Initialisierung einer TypeDef ist nicht mehr zulässig. Die Initialisierung einer TypeDef ist vom Standard nicht zulässig und generiert nun einen Compilerfehler.

```cpp
// C2513b.cpp
// compile with: /c
typedef struct S {
   int m_i;
} S = { 1 };   // C2513
// try the following line instead
// } S;
```

Eine Alternative wäre **`typedef`** das Löschen von, um eine Variable mit Aggregat Initialisiererliste zu definieren. Dies wird jedoch nicht empfohlen, da dadurch eine Variable mit dem gleichen Namen wie der Typ erstellt und der Typname ausgeblendet wird.

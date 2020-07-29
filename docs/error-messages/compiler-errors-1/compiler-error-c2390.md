---
title: Compilerfehler C2390
ms.date: 11/04/2016
f1_keywords:
- C2390
helpviewer_keywords:
- C2390
ms.assetid: 06b749ee-d072-4db1-b229-715f2c0728b5
ms.openlocfilehash: 48012c0fe31b2017cad29cc98992c9b1121efa7c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221184"
---
# <a name="compiler-error-c2390"></a>Compilerfehler C2390

"Bezeichner": falsche Speicher Klasse "Spezifizierer"

Die Speicher Klasse ist für den Bezeichner des globalen Bereichs nicht gültig. Die Standard Speicher Klasse wird anstelle der ungültigen-Klasse verwendet.

Mögliche Lösungen:

- Wenn der Bezeichner eine Funktion ist, deklarieren Sie ihn mit **`extern`** Storage.

- Wenn der Bezeichner ein formaler Parameter oder eine lokale Variable ist, deklarieren Sie ihn mit dem automatischen Speicher.

- Wenn der Bezeichner eine globale Variable ist, deklarieren Sie ihn ohne Speicher Klasse (automatischer Speicher).

## <a name="example"></a>Beispiel

- Im folgenden Beispiel wird C2390 generiert:

```cpp
// C2390.cpp
register int i;   // C2390

int main() {
   register int j;   // OK
}
```

---
title: Compilerwarnung (Stufe 3) C4191
ms.date: 11/04/2016
f1_keywords:
- C4191
helpviewer_keywords:
- C4191
ms.assetid: 576d3bc6-95b7-448a-af31-5d798452df09
ms.openlocfilehash: 9914818520fafb707b6821ba827e867b8aea9928
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220027"
---
# <a name="compiler-warning-level-3-c4191"></a>Compilerwarnung (Stufe 3) C4191

'operator/operation': unsichere Konvertierung von 'type of expression' zu 'type required'

Verschiedene Operationen, die Funktionszeiger verwenden, werden als unsicher angesehen:

- Funktionstypen mit unterschiedlichen Aufrufkonventionen.

- Funktionstypen mit unterschiedlichen Rückgabekonventionen.

- Argument- oder Rückgabetypen mit verschiedenen Größen, Typkategorien oder Klassifikationen.

- Unterschiedliche Argumentlisten Längen (on **`__cdecl`** , nur bei der Umwandlung von einer längeren Liste in eine kürzere Liste, auch wenn der kürzerer Wert varargs ist).

- Zeiger auf Daten (mit Ausnahme von **`void`** <strong>\*</strong> ), die für einen Zeiger auf eine Funktion als Alias dienen.

- Jeder andere typunterschied, der einen Fehler oder eine Warnung für einen ergeben würde **`reinterpret_cast`** .

Das Aufrufen dieser Funktion über den Ergebniszeiger kann zum Absturz des Programms führen.

Diese Warnung ist standardmäßig deaktiviert. Weitere Informationen finden Sie unter [Standardmäßig deaktivierte Compilerwarnungen](../../preprocessor/compiler-warnings-that-are-off-by-default.md) .

Im folgenden Beispiel wird C4191 generiert:

```cpp
// C4191.cpp
// compile with: /W3 /clr
#pragma warning(default: 4191)

void __clrcall f1() { }
void __cdecl   f2() { }

typedef void (__clrcall * fnptr1)();
typedef void (__cdecl   * fnptr2)();

int main() {
   fnptr1 fp1 = static_cast<fnptr1>(&f1);
   fnptr2 fp2 = (fnptr2) &f2;

   fnptr1 fp3 = (fnptr1) &f2;   // C4191
   fnptr2 fp4 = (fnptr2) &f1;   // C4191
};
```

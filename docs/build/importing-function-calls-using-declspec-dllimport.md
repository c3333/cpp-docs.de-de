---
title: Importieren von Funktionsaufrufen mithilfe von __declspec(dllimport)
description: Hier erfahren Sie mehr über die Verwendung von „__declspec(dllimport)“ beim Aufrufen von DLL-Daten und -Funktionen (Dynamic Link Library).
ms.date: 05/03/2020
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 515fbdb2824c1eaf41e822adeae1a16d3072eec4
ms.sourcegitcommit: 8a01ae145bc65f5bc90d6e47b4a1bdf47b073ee7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765720"
---
# <a name="importing-function-calls-using-__declspecdllimport"></a>Importieren von Funktionsaufrufen mithilfe von `__declspec(dllimport)`

Das Kommentieren von Aufrufen mithilfe von **`__declspec(dllimport)`** kann den Vorgang beschleunigen. **`__declspec(dllimport)`** ist immer erforderlich, um auf exportierte DLL-Daten zuzugreifen.

## <a name="import-a-function-from-a-dll"></a>Importieren einer Funktion aus einer DLL

Im folgenden Codebeispiel wird gezeigt, wie **`__declspec(dllimport)`** zum Importieren von Funktionsaufrufen aus einer DLL in eine Anwendung verwendet wird. Angenommen, `func1` ist eine Funktion, die sich in einer DLL getrennt von der ausführbaren Datei befindet, die die **main**-Funktion enthält.

Ohne **`__declspec(dllimport)`** liegt folgender Code vor:

```C
int main(void)
{
   func1();
}
```

Der Compiler generiert den folgenden Code:

```asm
call func1
```

Der Linker übersetzt den Aufruf in etwa wie folgt:

```asm
call 0x4000000         ; The address of 'func1'.
```

Wenn `func1` in einer anderen DLL vorhanden ist, kann der Linker diese Adresse nicht direkt auflösen, da er nicht weiß, wie die Adresse von `func1` lautet. In 32-Bit- und 64-Bit-Umgebungen generiert der Linker einen Thunk an einer bekannten Adresse. In einer 32-Bit-Umgebung sieht der Thunk wie folgt aus:

```asm
0x40000000:    jmp DWORD PTR __imp_func1
```

Hier ist `__imp_func1` die Adresse für den `func1`-Slot in der Importadresstabelle der ausführbaren Datei. All diese Adressen sind dem Linker bekannt. Das Ladeprogramm muss nur die Importadresstabelle der ausführbaren Datei zur Ladezeit aktualisieren, damit alles ordnungsgemäß funktioniert.

Die Verwendung von **`__declspec(dllimport)`** ist besser geeignet, da der Linker hier keinen Thunk generiert, wenn dieser nicht erforderlich ist. Thunks machen den Code größer (auf RISC-Systemen kann er mehrere Anweisungen umfassen) und können die Cacheleistung beeinträchtigen. Wenn Sie den Compiler anweisen, dass sich die Funktion in einer DLL befindet, kann er einen indirekten Aufruf generieren.

Nun lautet der Code wie folgt:

```C
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

Die folgende Anweisung wird generiert:

```asm
call DWORD PTR __imp_func1
```

Es gibt keinen Thunk und keine `jmp`-Anweisung, sodass der Code kompakter und schneller ist. Sie können die gleiche Wirkung auch ohne **`__declspec(dllimport)`** erzielen, indem Sie das gesamte Programm optimieren. Weitere Informationen finden Sie unter [/GL (Optimierung des ganzen Programms)](reference/gl-whole-program-optimization.md).

Bei Funktionsaufrufen innerhalb einer DLL sollen keine indirekten Aufrufe verwendet werden. Der Linker kennt bereits die Adresse der Funktion. Es wird mehr Zeit benötigt, und es ist zusätzlicher Speicher erforderlich, um die Adresse der Funktion vor einem indirekten Aufruf zu laden und zu speichern. Ein direkter Aufruf ist immer schneller und kompakter. Sie sollten **`__declspec(dllimport)`** nur beim Aufrufen von DLL-Funktionen von außerhalb der DLL selbst verwenden. Verwenden Sie **`__declspec(dllimport)`** nicht für Funktionen innerhalb einer DLL, wenn Sie diese erstellen.

## <a name="see-also"></a>Siehe auch

[Importieren in eine Anwendung](importing-into-an-application.md)

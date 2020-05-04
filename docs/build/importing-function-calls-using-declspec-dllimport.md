---
title: Importieren von Funktionsaufrufen mithilfe von __declspec(dllimport)
description: Wie und warum __declspec (dllimport) beim Aufrufen von DLL-Daten und-Funktionen verwendet werden.
ms.date: 05/03/2020
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 515fbdb2824c1eaf41e822adeae1a16d3072eec4
ms.sourcegitcommit: 8a01ae145bc65f5bc90d6e47b4a1bdf47b073ee7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/04/2020
ms.locfileid: "82765720"
---
# <a name="importing-function-calls-using-__declspecdllimport"></a>Importieren von Funktionsaufrufen mithilfe von`__declspec(dllimport)`

Durch das **`__declspec(dllimport)`** kommentieren von Aufrufen mithilfe von können Sie diese schneller machen. **`__declspec(dllimport)`** ist immer erforderlich, um auf exportierte dll-Daten zuzugreifen.

## <a name="import-a-function-from-a-dll"></a>Importieren einer Funktion aus einer dll

Im folgenden Codebeispiel wird gezeigt, wie **`__declspec(dllimport)`** verwendet wird, um Funktionsaufrufe aus einer DLL in eine Anwendung zu importieren. Angenommen, `func1` es handelt sich um eine Funktion, die sich in einer DLL getrennt von der ausführbaren Datei befindet, die die **Main** -Funktion enthält.

Ohne **`__declspec(dllimport)`**, angesichts dieses Codes:

```C
int main(void)
{
   func1();
}
```

der Compiler generiert Code, der wie folgt aussieht:

```asm
call func1
```

und der Linker übersetzt den-Befehl in etwa wie folgt:

```asm
call 0x4000000         ; The address of 'func1'.
```

Wenn `func1` in einer anderen dll vorhanden ist, kann der Linker diese Adresse nicht direkt auflösen, da Sie nicht wissen kann, wie `func1` die Adresse von ist. In 32-Bit-und 64-Bit-Umgebungen generiert der Linker einen Thunk an einer bekannten Adresse. In einer 32-Bit-Umgebung sieht der Thunk wie folgt aus:

```asm
0x40000000:    jmp DWORD PTR __imp_func1
```

Hier `__imp_func1` ist die Adresse für den `func1` Slot in der Import Adress Tabelle der ausführbaren Datei. Alle diese Adressen sind dem Linker bekannt. Das Lade Programm muss nur die Import Adress Tabelle der ausführbaren Datei zur Ladezeit aktualisieren, damit alles ordnungsgemäß funktioniert.

Daher ist die Verwendung **`__declspec(dllimport)`** von besser: da der Linker keinen Thunk generiert, wenn er nicht erforderlich ist. Thunjs machen den Code größer (in RISC-Systemen, es kann mehrere Anweisungen geben) und können Ihre Cache Leistung beeinträchtigen. Wenn Sie dem Compiler mitteilen, dass sich die Funktion in einer DLL befindet, kann Sie einen indirekten-Rückruf generieren.

Nun lautet der folgende Code:

```C
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

generiert diese Anweisung:

```asm
call DWORD PTR __imp_func1
```

Es gibt keinen Thunk und keine `jmp` Anweisungen, sodass der Code kleiner und schneller ist. Sie können auch ohne **`__declspec(dllimport)`** die Optimierung des gesamten Programms denselben Effekt erzielen. Weitere Informationen finden Sie unter [/GL (Optimierung des ganzen Programms)](reference/gl-whole-program-optimization.md).

Bei Funktionsaufrufen innerhalb einer DLL möchten Sie keinen indirekten Aufruf verwenden. Der Linker kennt bereits die Adresse der Funktion. Es benötigt zusätzliche Zeit und Speicherplatz, um die Adresse der Funktion vor einem indirekten Aufruf zu laden und zu speichern. Ein direkter-Rückruf ist immer schneller und kleiner. Sie möchten nur verwenden **`__declspec(dllimport)`** , wenn Sie DLL-Funktionen von außerhalb der DLL selbst aufrufen. Verwenden **`__declspec(dllimport)`** Sie bei der Erstellung dieser DLL nicht für Funktionen innerhalb einer DLL.

## <a name="see-also"></a>Weitere Informationen:

[Importieren in eine Anwendung](importing-into-an-application.md)

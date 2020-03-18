---
title: Importieren von Funktionsaufrufen mithilfe von „__declspec(dllimport)“
ms.date: 11/04/2016
helpviewer_keywords:
- importing function calls [C++]
- dllimport attribute [C++], function call imports
- __declspec(dllimport) keyword [C++]
- function calls [C++], importing
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
ms.openlocfilehash: 1743cbba8c3046ef844f16be8e78d43c61f62606
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442517"
---
# <a name="importing-function-calls-using-__declspecdllimport"></a>Importieren von Funktionsaufrufen mithilfe von „__declspec(dllimport)“

Im folgenden Codebeispiel wird gezeigt, wie **_declspec (dllimport)** verwendet wird, um Funktionsaufrufe aus einer DLL in eine Anwendung zu importieren. Nehmen Sie an, dass `func1` eine Funktion ist, die sich in einer DLL getrennt von der exe-Datei befindet, die die **Main** -Funktion enthält.

Ohne **__declspec (dllimport)** , wenn der folgende Code angezeigt wird:

```
int main(void)
{
   func1();
}
```

der Compiler generiert Code, der wie folgt aussieht:

```
call func1
```

und der Linker übersetzt den-Befehl in etwa wie folgt:

```
call 0x4000000         ; The address of 'func1'.
```

Wenn `func1` in einer anderen dll vorhanden ist, kann der Linker diese nicht direkt auflösen, da er nicht weiß, wie die Adresse von `func1` ist. In 16-Bit-Umgebungen fügt der Linker diese Code Adresse einer Liste in der exe-Datei hinzu, die das Lade Tool zur Laufzeit mit der richtigen Adresse Patchen würde. In 32-Bit-und 64-Bit-Umgebungen generiert der Linker einen Thunk, der die Adresse kennt. In einer 32-Bit-Umgebung sieht der Thunk wie folgt aus:

```
0x40000000:    jmp DWORD PTR __imp_func1
```

Hier ist `imp_func1` die Adresse für den `func1` Slot in der Import Adress Tabelle der exe-Datei. Alle Adressen sind dem Linker bekannt. Das Lade Modul muss die Import Adress Tabelle der exe-Datei zur Ladezeit nur aktualisieren, damit alles ordnungsgemäß funktioniert.

Daher ist die Verwendung von **__declspec (dllimport)** besser, da der Linker keinen Thunk generiert, wenn er nicht erforderlich ist. Thunjs machen den Code größer (in RISC-Systemen, es kann mehrere Anweisungen geben) und können Ihre Cache Leistung beeinträchtigen. Wenn Sie dem Compiler mitteilen, dass sich die Funktion in einer DLL befindet, kann Sie einen indirekten-Rückruf generieren.

Nun lautet der folgende Code:

```
__declspec(dllimport) void func1(void);
int main(void)
{
   func1();
}
```

generiert diese Anweisung:

```
call DWORD PTR __imp_func1
```

Es gibt keinen Thunk und keine `jmp`-Anweisung, sodass der Code kleiner und schneller ist.

Andererseits sollten Sie für Funktionsaufrufe innerhalb einer DLL nicht einen indirekten Aufruf verwenden müssen. Sie kennen bereits die Adresse einer Funktion. Da Zeit und Speicherplatz erforderlich sind, um die Adresse der Funktion vor einem indirekten Aufruf zu laden und zu speichern, ist ein direkter Aufruf immer schneller und kleiner. Sie möchten nur **__declspec (dllimport)** verwenden, wenn Sie DLL-Funktionen von außerhalb der DLL selbst aufrufen. Verwenden Sie für Funktionen innerhalb einer DLL nicht **__declspec (dllimport)** , wenn Sie diese DLL-Datei aufbauen.

## <a name="see-also"></a>Weitere Informationen

[Importieren in eine Anwendung](importing-into-an-application.md)

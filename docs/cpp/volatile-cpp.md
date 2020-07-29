---
title: volatile (C++)
ms.date: 05/07/2019
f1_keywords:
- volatile_cpp
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
ms.openlocfilehash: bbdd7d03d820b9fc0d541dbb31d55b641226f14e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213098"
---
# <a name="volatile-c"></a>volatile (C++)

Ein Typqualifizierer, den Sie verwenden können, um zu deklarieren, dass ein Objekt im Programm von der Hardware geändert werden kann.

## <a name="syntax"></a>Syntax

```
volatile declarator ;
```

## <a name="remarks"></a>Bemerkungen

Sie können den [/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) -Compilerschalter verwenden, um zu ändern, wie der Compiler dieses Schlüsselwort interpretiert.

Visual Studio interpretiert das **`volatile`** Schlüsselwort abhängig von der Zielarchitektur unterschiedlich. Wenn die Compileroption " **/volatile** " nicht angegeben wird, führt der Compiler aus, als ob " **/volatile: ISO** " angegeben wurde. Wenn für andere Architekturen als Arm keine **/volatile** -Compileroption angegeben ist, führt der Compiler aus, als ob **/volatile: ms** angegeben wurde. Daher wird für andere Architekturen als Arm dringend empfohlen, **/volatile: ISO**anzugeben und explizite Synchronisierungs primitiven und systeminterne Compiler-Funktionen zu verwenden, wenn Sie mit Arbeitsspeicher arbeiten, der über mehrere Threads gemeinsam genutzt wird.

Sie können den- **`volatile`** Qualifizierer verwenden, um den Zugriff auf Speicherorte zu ermöglichen, die von asynchronen Prozessen wie interrupthandlern verwendet werden.

Wenn **`volatile`** für eine Variable verwendet wird, die auch das [__restrict](../cpp/extension-restrict.md) -Schlüsselwort aufweist, hat **`volatile`** Vorrang.

Wenn ein **`struct`** Member als gekennzeichnet ist **`volatile`** , **`volatile`** wird an die gesamte-Struktur weitergegeben. Wenn eine Struktur nicht über eine Länge verfügt, die in der aktuellen Architektur mithilfe einer Anweisung kopiert werden kann, ist **`volatile`** in dieser Struktur möglicherweise vollständig verloren.

Das **`volatile`** Schlüsselwort hat möglicherweise keine Auswirkung auf ein Feld, wenn eine der folgenden Bedingungen zutrifft:

- Die Länge des flüchtigen Felds überschreitet die maximale Größe, die in der aktuellen Architektur mithilfe einer Anweisung kopiert werden kann.

- Die Länge der äußersten enthaltenden **`struct`** – oder, wenn es sich um einen Member eines möglicherweise eingefügten Elements handelt **`struct`** – überschreitet die maximale Größe, die in der aktuellen Architektur mithilfe einer Anweisung kopiert werden kann.

Obwohl der Prozessor nicht zwischen speicherbare Speicherzugriffe nicht neu anordnet, müssen nicht zwischen speicherbare Variablen als gekennzeichnet werden, **`volatile`** um sicherzustellen, dass der Compiler die Speicherzugriffe nicht neu anordnet.

Objekte, die als deklariert werden, **`volatile`** werden in bestimmten Optimierungen nicht verwendet, da sich ihre Werte jederzeit ändern können.  Das System liest bei jeder Anforderung den aktuellen Wert eines flüchtigen Objekts, selbst wenn eine vorherige Anweisung bereits den Wert des gleichen Objekts abgefragt hatte.  Außerdem wird der Wert des Objekts sofort durch Zuweisung geschrieben.

## <a name="iso-compliant"></a>ISO-Kompatibilität

Wenn Sie mit dem c#-Schlüsselwort Volatile vertraut sind oder mit dem Verhalten von **`volatile`** in früheren Versionen des Microsoft C++-Compilers (MSVC) vertraut sind, beachten Sie, dass das ISO Standard **`volatile`** -Schlüsselwort C++ 11 anders ist und in MSVC unterstützt wird, wenn die [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) -Compileroption angegeben wird. (In ARM ist es standardmäßig festgelegt). Das **`volatile`** Schlüsselwort im ISO-Standard Code c++ 11 soll nur für den Hardware Zugriff verwendet werden. verwenden Sie es nicht für die Kommunikation zwischen Threads. Verwenden Sie für die Kommunikation zwischen Threads Mechanismen wie " [Std:: Atomic \<T> ](../standard-library/atomic.md) " aus der [C++-Standard Bibliothek](../standard-library/cpp-standard-library-reference.md).

## <a name="end-of-iso-compliant"></a>Ende ISO-Kompatibilität

**Microsoft-spezifisch**

Wenn die **/volatile: ms** -Compileroption – standardmäßig verwendet wird, wenn andere Architekturen als Arm als Ziel verwendet werden – der Compiler zusätzlichen Code generiert, um die Reihenfolge der Verweise auf flüchtige Objekte zu verwalten, zusätzlich zur Beibehaltung der Reihenfolge an Verweise auf andere globale Objekte. Dies gilt insbesondere für:

- Das Schreiben in ein flüchtiges Objekt (auch als flüchtiger Schreibvorgang bezeichnet) weist Release-Semantik auf. Das heißt, dass ein Verweis auf ein globales oder statisches Objekt, das vor einem Schreibvorgang in ein flüchtiges Objekt in der Anweisungsabfolge auftritt, vor diesem flüchtigen Schreibvorgang in der kompilierten Binärdatei auftritt.

- Das Lesen eines flüchtigen Objekts (auch als flüchtiger Lesevorgang bezeichnet) weist Acquire-Semantik auf. Das heißt, dass ein Verweis auf ein globales oder statisches Objekt, das nach dem Lesevorgang eines flüchtigen Arbeitsspeichers in der Anweisungsabfolge auftritt, nach dem flüchtigen Lesevorgang in der kompilierten Binärdatei auftritt.

Dadurch können flüchtige Objekte für Arbeitsspeichersperren und -freigaben in Multithreadanwendungen verwendet werden.

> [!NOTE]
> Wenn die erweiterte Garantie verwendet wird, die bei Verwendung der **/volatile: ms** -Compileroption bereitgestellt wird, ist der Code nicht portabel.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[const](../cpp/const-cpp.md)<br/>
[Konstante und flüchtige Zeiger](../cpp/const-and-volatile-pointers.md)

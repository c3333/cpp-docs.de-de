---
title: Temporäre Objekte
ms.date: 11/04/2016
helpviewer_keywords:
- temporary objects
- objects [C++], temporary
ms.assetid: 4c8cec02-391e-4225-9bc6-06d150201412
ms.openlocfilehash: 0f4cca7100ff8046123f7b2950c1d557797c70f4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223550"
---
# <a name="temporary-objects"></a>Temporäre Objekte

In einigen Fällen muss der Compiler temporäre Objekte erstellen. Diese temporären Objekte können aus folgenden Gründen erstellt werden:

- Die Initialisierung eines **`const`** Verweises mit einem Initialisierer eines Typs unterscheidet sich von dem des zugrunde liegenden Typs des Verweises, der initialisiert wird.

- Um den Rückgabewert einer Funktion zu speichern, die einen benutzerdefinierten Typ zurückgibt. Diese temporären Objekte werden nur erstellt, wenn das Programm den Rückgabewert nicht in ein Objekt kopiert. Beispiel:

    ```cpp
    UDT Func1();    //  Declare a function that returns a user-defined
                    //   type.

    ...

    Func1();        //  Call Func1, but discard return value.
                    //  A temporary object is created to store the return
                    //   value.
    ```

   Da der Rückgabewert nicht in ein anderes Objekt kopiert wird, wird ein temporäres Objekt erstellt. Ein allgemeinerer Fall, in dem temporäre Dateien erstellt werden, ist während der Auswertung eines Ausdrucks, wobei überladene Operator-Funktionen aufgerufen werden müssen. Diese überladenen Operatorfunktionen geben einen benutzerdefinierten Typ zurück, der häufig nicht in ein anderes Objekt kopiert wird.

   Betrachten Sie den Ausdruck `ComplexResult = Complex1 + Complex2 + Complex3`. Der Ausdruck `Complex1 + Complex2` wird ausgewertet und das Ergebnis wird in einem temporären Objekt gespeichert. Anschließend wird der Ausdruck *temporär* `+ Complex3` ausgewertet, und das Ergebnis wird in kopiert `ComplexResult` (vorausgesetzt, der Zuweisungs Operator ist nicht überladen).

- Um das Ergebnis einer Typumwandlung in einem benutzerdefinierten Typ zu speichern. Wenn ein Objekt eines angegebenen Typs explizit in einen benutzerdefinierten Typ konvertiert wird, wird das neue Objekt als temporäres Objekt erstellt.

Temporäre Objekte haben eine Lebensdauer, die sich nach dem Zeitpunkt der Erstellung und Zerstörung richtet. Jeder Ausdruck, der mehr als einer temporäres Objekt erstellt, zerstört sie letztendlich in umgekehrter Reihenfolge, in der sie erstellt wurden. In der folgenden Tabelle sind die Punkte dargestellt, an denen Zerstörung auftritt.

### <a name="destruction-points-for-temporary-objects"></a>Zerstörungspunkte für temporäre Objekte

|Grund "temporär" erstellt|Zerstörungspunkt|
|------------------------------|-----------------------|
|Ergebnis der Ausdrucksauswertung|Alle temporare, die als Ergebnis der Ausdrucks Auswertung erstellt werden, werden am Ende der Ausdrucks Anweisung (d. h. am Semikolon) oder am Ende der Steuerungs Ausdrücke für die **`for`** Anweisungen, **`if`** , **`while`** , **`do`** und zerstört **`switch`** .|
|Initialisieren von **`const`** verweisen|Wenn ein Initialisierer kein l-Wert desselben Typs wie der initialisierte Verweis ist, wird ein temporäres Objekt des zugrunde liegenden Objekttyps erstellt und mit dem Initialisierungsausdruck initialisiert. Dieses temporäre Objekt wird zerstört, sobald das Verweisobjekt, an das es gebunden ist, zerstört wurde.|

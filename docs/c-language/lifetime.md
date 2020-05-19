---
title: Lebensdauer
ms.date: 11/04/2016
helpviewer_keywords:
- local variables, lifetime
- variables, automatic
- storage classes, lifetime
- variables, lifetime
- automatic storage class
- automatic storage class, duration
- storage class specifiers, storage duration
- memory allocation, dynamic allocation
- functions [C++], lifetime
- storage duration
- dynamic memory allocation
- memory allocation, dynamic
- lifetime
- global variables, lifetime
ms.assetid: ff0b42cb-3f0f-49a3-a94f-d1d825d8ddfe
ms.openlocfilehash: 962e5ef4cae1be142091d2a209b4c60c0b789e74
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232773"
---
# <a name="lifetime"></a>Lebensdauer

"Lebensdauer" ist der Zeitraum der Ausführung eines Programms, in dem eine Variable oder eine Funktion vorhanden ist. Die Speicherdauer des Bezeichners bestimmt dessen Lebensdauer.

Ein Bezeichner, der mit dem *Speicherklassenspezifizierer* **static** deklariert wird, weist eine statische Speicherdauer auf. Bezeichner mit statischer Speicherdauer (auch "global" genannt) weisen Speicher und einen definierten Wert für die Dauer eines Programms auf. Speicher wird reserviert, und der gespeicherte Wert des Bezeichners wird nur einmal, und zwar vor dem Programmstart, initialisiert. Ein Bezeichner, der mit externer oder interner Verknüpfung deklariert wird, hat auch eine statische Speicherdauer (Informationen finden Sie unter [Verknüpfung](../c-language/linkage.md)).

Ein Bezeichner, der ohne den Speicherklassenspezifizierer **static** deklariert wird, hat eine automatische Speicherdauer, wenn er innerhalb einer Funktion deklariert wird. Ein Bezeichner mit automatischer Speicherdauer (ein "lokaler Bezeichner") weist Speicher und einen definierten Wert nur innerhalb des Blocks auf, in dem der Bezeichner definiert oder deklariert ist. Bei jedem Wechsel des Programms in diesen Block wird einem automatischen Bezeichner neuer Speicher zugeordnet. Wenn das Programm diesen Block beendet, verliert er seinen Speicher (und den Wert). Bezeichner, die in einer Funktion ohne Bindung deklariert werden, haben auch eine automatische Speicherdauer.

In den folgenden Regeln ist festgelegt, ob ein Bezeichner über eine globale (statische) oder lokale (automatische) Lebensdauer verfügt:

- Alle Funktionen haben statische Lebensdauer. Daher sind sie während der Programmausführung jederzeit vorhanden. Bezeichner, die auf externer Ebene deklariert werden (also außerhalb aller Blöcke im Programm auf der gleichen Ebene der Funktionsdefinitionen), haben immer eine globale (statische) Lebensdauer.

- Wenn eine lokale Variable einen Initialisierer hat, wird die Variable jedes Mal bei Erstellung initialisiert (es sei denn, sie ist als **static** deklariert). Funktionsparameter haben auch eine lokale Lebensdauer. Sie können die globale Lebensdauer für einen Bezeichner innerhalb eines Blocks angeben, indem Sie den Speicherklassenspezifizierer **static** in der Deklaration einschließen. Sobald die Variable als **static** deklariert wurde, behält sie ihren Wert von einem Eintrag des Blocks zum nächsten.

Obwohl ein Bezeichner mit einer globalen Lebensdauer während der gesamten Ausführung des Quellprogramms vorhanden ist (z.B. eine extern deklarierte Variable oder eine mit dem **static**-Schlüsselwort deklarierte lokale Variable), ist er möglicherweise nicht in allen Teilen des Programms sichtbar. Weitere Informationen über Sichtbarkeit finden Sie unter [Bereich und Sichtbarkeit](../c-language/scope-and-visibility.md). Unter [Speicherklassen](../c-language/c-storage-classes.md) finden Sie eine Erläuterung zum *storage-class-specifier*-Nichtterminal.

Arbeitsspeicher kann nach Bedarf zugeordnet werden (dynamisch), wenn er durch die Verwendung von speziellen Bibliotheksroutinen wie `malloc` erstellt wird. Da die dynamische Speicherbelegung Bibliotheksroutinen verwendet, gilt sie nicht als Teil der Sprache. Weitere Informationen zur [malloc](../c-runtime-library/reference/malloc.md)-Funktion finden Sie in der *Laufzeitbibliotheksreferenz*.

## <a name="see-also"></a>Siehe auch

[Lebensdauer, Bereich, Sichtbarkeit und Verknüpfung](../c-language/lifetime-scope-visibility-and-linkage.md)

---
title: E. Durch die Implementierung definiertes Verhalten in OpenMP (C/C++)
ms.date: 01/22/2019
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
ms.openlocfilehash: e866eee9c6d85e93388f9f1d086badf948e2600e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215045"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. Durch die Implementierung definiertes Verhalten in OpenMP (C/C++)

In diesem Anhang werden die Verhaltensweisen zusammengefasst, die in dieser API als "Implementierungs definiert" beschrieben werden.  Jedes Verhalten wird in der Hauptspezifikation auf einen Querverweis zurück zur Beschreibung zurückverwiesen.

## <a name="remarks"></a>Bemerkungen

Eine-Implementierung ist erforderlich, um das Verhalten in diesen Fällen zu definieren und zu dokumentieren, aber diese Liste ist möglicherweise unvollständig.

- **Anzahl von Threads:** Wenn ein paralleler Bereich festgestellt wird, während die dynamische Anpassung der Anzahl der Threads deaktiviert ist, und die Anzahl der für den parallelen Bereich angeforderten Threads größer ist als die vom Laufzeitsystem bereitgestellte Anzahl von Threads, ist das Verhalten des Programms Implementierungs definiert (siehe Seite 9).

   In Visual C++wird für einen nicht genetzten parallelen Bereich 64 Threads (der Höchstwert) bereitgestellt.

- **Anzahl der Prozessoren:** Die Anzahl der physischen Prozessoren, die die Threads tatsächlich zu einem beliebigen Zeitpunkt gehostet haben, ist Implementierungs definiert (siehe Seite 10).

   In Visual C++ist diese Zahl nicht konstant und wird vom Betriebssystem gesteuert.

- **Erstellen von Thread Teams:** Die Anzahl der Threads in einem Team, die einen genetzten parallelen Bereich ausführen, wird durch die Implementierung definiert (siehe Seite 10).

   In Visual C++wird diese Zahl vom Betriebssystem bestimmt.

- **Zeitplan (Laufzeit):** Die Entscheidung über die Zeitplanung wird bis zur Laufzeit verzögert. Der Zeit Plantyp und die Segmentgröße können zur Laufzeit durch Festlegen der Umgebungsvariablen `OMP_SCHEDULE` ausgewählt werden. Wenn diese Umgebungsvariable nicht festgelegt ist, wird der resultierende Zeitplan von der Implementierung definiert (siehe Seite 13).

   In Visual C++wird der Zeit Plantyp ohne Blockgröße `static`.

- **Standardzeit Planung:** Wenn keine Schedule-Klausel vorhanden ist, wird der Standard Zeitplan von der Implementierung definiert (siehe Seite 13).

   In Visual C++wird der Standardzeit Plantyp ohne Blockgröße `static`.

- **Atomarisch:** Es ist Implementierungs definiert, ob eine Implementierung alle `atomic` Direktiven durch `critical` Direktiven ersetzt, die denselben eindeutigen Namen haben (siehe Seite 20).

   In Visualisierungen C++verwenden alle atomaren Operationen, die diese Eigenschaft erfüllen, einen kritischen Abschnitt, wenn die von [Atomic](reference/openmp-directives.md#atomic) geänderten Daten nicht in einer natürlichen Ausrichtung liegen oder wenn Sie ein oder zwei Bytes lang sind. Andernfalls werden kritische Abschnitte nicht verwendet.

- **[omp_get_num_threads](3-run-time-library-functions.md#312-omp_get_num_threads-function):** Wenn die Anzahl der Threads nicht explizit vom Benutzer festgelegt wurde, wird der Standardwert von der Implementierung definiert (siehe Seite 9).

   In Visual C++ist die Standard Anzahl von Threads gleich der Anzahl der Prozessoren.

- **[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function):** Der Standardwert für die dynamische Thread Anpassung ist von der Implementierung definiert.

   In Visual C++wird der Standardwert `FALSE`.

- **[omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function):** Wenn die gestreamte Parallelität aktiviert ist, wird die Anzahl der Threads, die für die Ausführung von gemusteten parallelen Bereichen verwendet werden, von der Implementierung definiert

   In Visual C++wird die Anzahl der Threads vom Betriebssystem bestimmt.

- Umgebungsvariable [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule) : der Standardwert für diese Umgebungsvariable ist von der Implementierung definiert.

   In Visual C++wird der Zeit Plantyp ohne Blockgröße `static`.

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) -Umgebungsvariable: Wenn für die `OMP_NUM_THREADS`-Umgebungsvariable kein Wert angegeben wird, oder wenn der angegebene Wert keine positive Ganzzahl ist oder wenn der Wert größer als die maximale Anzahl von Threads ist, die das System unterstützen kann, wird die Anzahl der zu verwendenden Threads von der Implementierung definiert.

   Wenn der C++angegebene Wert in Visual NULL oder kleiner ist, ist die Anzahl der Threads gleich der Anzahl der Prozessoren.  Wenn der Wert größer als 64 ist, ist die Anzahl der Threads 64.

- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) -Umgebungsvariable: der Standardwert ist von der Implementierung definiert.

   In Visual C++wird der Standardwert `FALSE`.

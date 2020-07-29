---
title: Synchronisierungsdatenstrukturen
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
ms.openlocfilehash: 244aaac9bd40c83d0bbec3c360bdf7351da54baf
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231662"
---
# <a name="synchronization-data-structures"></a>Synchronisierungsdatenstrukturen

Der Concurrency Runtime stellt mehrere Datenstrukturen bereit, mit denen Sie den Zugriff auf freigegebene Daten aus mehreren Threads synchronisieren können. Diese Datenstrukturen sind nützlich, wenn Sie über freigegebene Daten verfügen, die Sie nur selten ändern. Ein Synchronisierungs Objekt, z. b. ein kritischer Abschnitt, bewirkt, dass andere Threads warten, bis die freigegebene Ressource verfügbar ist. Wenn Sie daher ein solches Objekt zum Synchronisieren des Zugriffs auf häufig verwendete Daten verwenden, können Sie die Skalierbarkeit in der Anwendung verlieren. Die [Parallel Patterns Library (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) stellt die [parallelcurrency:: combinable](../../parallel/concrt/reference/combinable-class.md) -Klasse bereit, mit der Sie eine Ressource für mehrere Threads oder Tasks freigeben können, ohne dass eine Synchronisierung erforderlich ist. Weitere Informationen zur `combinable` -Klasse finden Sie unter [parallele Container und Objekte](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="sections"></a><a name="top"></a>Strecken

In diesem Thema werden die folgenden asynchronen Nachrichtenblock Typen ausführlich beschrieben:

- [critical_section](#critical_section)

- [reader_writer_lock](#reader_writer_lock)

- [scoped_lock und scoped_lock_read](#scoped_lock)

- [event](#event)

## <a name="critical_section"></a><a name="critical_section"></a>critical_section

Die " [parallelcurrency:: CRITICAL_SECTION](../../parallel/concrt/reference/critical-section-class.md) "-Klasse stellt ein paralleles gegenseitiges Ausschluss Objekt dar, das andere Tasks liefert, anstatt diese vorab zu verwenden. Kritische Abschnitte sind nützlich, wenn mehrere Threads exklusiven Lese-und Schreibzugriff auf freigegebene Daten benötigen.

Die `critical_section` Klasse ist nicht Wiedereintritts fähig. Die Methode " [parallelcurrency:: critical_section:: Lock](reference/critical-section-class.md#lock) " löst eine Ausnahme vom Typ " [parallelcurrency:: Improper_lock](../../parallel/concrt/reference/improper-lock-class.md) " aus, wenn Sie von dem Thread aufgerufen wird, der die Sperre bereits besitzt.

### <a name="methods-and-features"></a>Methoden und Features

In der folgenden Tabelle sind die wichtigen Methoden aufgeführt, die von der-Klasse definiert werden `critical_section` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[lock](reference/critical-section-class.md#lock)|Ruft den kritischen Abschnitt ab. Der aufrufende Kontext blockiert, bis er die Sperre erhält.|
|[try_lock](reference/critical-section-class.md#try_lock)|Versucht, den kritischen Abschnitt abzurufen, aber blockiert nicht.|
|[Entsperren](reference/critical-section-class.md#unlock)|Gibt den kritischen Abschnitt frei.|

[Nach[oben](#top)]

## <a name="reader_writer_lock"></a><a name="reader_writer_lock"></a>reader_writer_lock

Die Klasse " [parallelcurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) " stellt Thread sichere Lese-/Schreibvorgänge für freigegebene Daten bereit. Verwenden Sie Lese-/Schreibsperren, wenn mehrere Threads gleichzeitigen Lesezugriff auf eine freigegebene Ressource benötigen, aber nur selten in diese freigegebene Ressource schreiben. Diese Klasse gewährt zu einem beliebigen Zeitpunkt nur einen Thread Schreibzugriff auf ein Objekt.

Die- `reader_writer_lock` Klasse kann eine bessere Leistung als die- `critical_section` Klasse erzielen, da ein- `critical_section` Objekt exklusiven Zugriff auf eine freigegebene Ressource erhält, die gleichzeitigen Lesezugriff verhindert.

Wie die- `critical_section` Klasse stellt die- `reader_writer_lock` Klasse ein kooperatives gegenseitiges Ausschluss Objekt dar, das an andere Aufgaben übergibt, anstatt diese vorab zu verwenden.

Wenn ein Thread, der in eine freigegebene Ressource schreiben muss, eine Lese-/Schreibsperre erhält, werden andere Threads, die ebenfalls auf die Ressource zugreifen müssen, blockiert, bis der Writer die Sperre freigibt. Die `reader_writer_lock` -Klasse ist ein Beispiel für eine Sperre mit *Schreibvorgängen* , bei der es sich um eine Sperre handelt, die die Blockierung der wartenden Writer blockiert, bevor die Blockierung von Lesern

Wie die- `critical_section` Klasse `reader_writer_lock` ist die-Klasse nicht Wiedereintritts fähig. Die [parallelcurrency:: reader_writer_lock:: Lock](reference/reader-writer-lock-class.md#lock) -Methode und die [parallelcurrency:: reader_writer_lock:: lock_read](reference/reader-writer-lock-class.md#lock_read) -Methode lösen eine Ausnahme vom Typ aus `improper_lock` , wenn Sie von einem Thread aufgerufen werden, der bereits die Sperre besitzt.

> [!NOTE]
> Da die `reader_writer_lock` -Klasse nicht wieder einentrant ist, können Sie eine schreibgeschützte Sperre nicht auf eine Lese-/Schreibsperre aktualisieren oder eine Lese-/Schreibsperre auf eine schreibgeschützte Sperre herabstufen. Durch das Ausführen eines dieser Vorgänge wird ein nicht bestimmtes Verhalten erzeugt.

### <a name="methods-and-features"></a>Methoden und Features

In der folgenden Tabelle sind die wichtigen Methoden aufgeführt, die von der-Klasse definiert werden `reader_writer_lock` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[lock](reference/reader-writer-lock-class.md#lock)|Erhält Lese-/Schreibzugriff auf die Sperre.|
|[try_lock](reference/reader-writer-lock-class.md#try_lock)|Versucht, Lese-/Schreibzugriff auf die Sperre zu erhalten, blockiert jedoch nicht.|
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|Erhält schreibgeschützten Zugriff auf die Sperre.|
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|Versucht, schreibgeschützten Zugriff auf die Sperre zu erhalten, blockiert jedoch nicht.|
|[Entsperren](reference/reader-writer-lock-class.md#unlock)|Hebt die Sperre auf.|

[Nach[oben](#top)]

## <a name="scoped_lock-and-scoped_lock_read"></a><a name="scoped_lock"></a>scoped_lock und scoped_lock_read

Die `critical_section` -Klasse und die- `reader_writer_lock` Klasse stellen die für die Arbeit mit gegenseitigen Ausschluss Objekten notwendigen Klassen zur Verfügung. Diese Hilfsklassen werden als Bereichs bezogene *Sperren*bezeichnet.

Die `critical_section` Klasse enthält die Klasse " [parallelcurrency:: critical_section:: scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) ". Der Konstruktor erhält Zugriff auf das bereitgestellte `critical_section` Objekt. der Dekonstruktor gibt den Zugriff auf dieses Objekt frei. Die `reader_writer_lock` Klasse enthält die Klasse " [parallelcurrency:: reader_writer_lock:: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) ", die ähnelt `critical_section::scoped_lock` , mit der Ausnahme, dass Sie Schreibzugriff auf das bereitgestellte `reader_writer_lock` Objekt verwaltet. Die `reader_writer_lock` Klasse enthält auch die Klasse " [parallelcurrency:: reader_writer_lock:: scoped_lock_read](reference/reader-writer-lock-class.md#scoped_lock_read_class) ". Diese Klasse verwaltet den Lesezugriff auf das bereitgestellte- `reader_writer_lock` Objekt.

Bereichs bezogene Sperren bieten mehrere Vorteile, wenn Sie mit `critical_section` -Objekten und- `reader_writer_lock` Objekten manuell arbeiten. In der Regel weisen Sie dem Stapel eine Bereichs bezogene Sperre zu. Eine Bereichs bezogene Sperre gibt den Zugriff auf das gegenseitige Ausschluss Objekt automatisch frei, wenn es zerstört wird. Daher wird das zugrunde liegende Objekt nicht manuell entsperrt. Dies ist nützlich, wenn eine Funktion mehrere- **`return`** Anweisungen enthält. Bereichs bezogene Sperren können Ihnen auch helfen, Ausnahme sicheren Code zu schreiben. Wenn eine- **`throw`** Anweisung bewirkt, dass der Stapel entladen wird, wird der Dekonstruktor für jede aktive Bereichs bezogene Sperre aufgerufen. Daher wird das gegenseitige Ausschluss Objekt immer ordnungsgemäß freigegeben.

> [!NOTE]
> Wenn Sie die `critical_section::scoped_lock` Klassen, `reader_writer_lock::scoped_lock` und verwenden `reader_writer_lock::scoped_lock_read` , sollten Sie den Zugriff auf das zugrunde liegende gegenseitige Ausschluss Objekt nicht manuell freigeben. Dadurch kann die Laufzeit in einen ungültigen Zustand versetzt werden.

## <a name="event"></a><a name="event"></a> -Ereignis

Die " [parallelcurrency:: Event](../../parallel/concrt/reference/event-class.md) "-Klasse stellt ein Synchronisierungs Objekt dar, dessen Zustand signalisiert oder nicht signalisiert werden kann. Im Gegensatz zu Synchronisierungs Objekten, wie z. b. kritischen Abschnitten, deren Zweck der Schutz des Zugriffs auf freigegebene Daten ist, wird die Ausführung von Ereignissen synchronisiert.

Die- `event` Klasse ist nützlich, wenn eine Aufgabe die Arbeit für eine andere Aufgabe abgeschlossen hat. Beispielsweise könnte eine Aufgabe einer anderen Aufgabe signalisieren, dass Sie Daten aus einer Netzwerkverbindung oder aus einer Datei gelesen hat.

### <a name="methods-and-features"></a>Methoden und Features

In der folgenden Tabelle werden einige der wichtigen Methoden angezeigt, die von der-Klasse definiert werden `event` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Warte](reference/event-class.md#wait)|Wartet, bis das Ereignis signalisiert wird.|
|[set](reference/event-class.md#set)|Legt das-Ereignis auf den signalisierten Zustand fest.|
|[reset](reference/event-class.md#reset)|Legt das Ereignis auf den nicht signalisierten Zustand fest.|
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|Wartet, bis mehrere Ereignisse signalisiert werden.|

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung der- `event` Klasse finden Sie unter [Vergleich der Synchronisierungs Datenstrukturen mit der Windows-API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).

[Nach[oben](#top)]

## <a name="related-sections"></a>Verwandte Abschnitte

[Vergleichen der Synchronisierungs Datenstrukturen mit der Windows-API](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
Vergleicht das Verhalten der Synchronisierungs Datenstrukturen mit den von der Windows-API bereitgestellten.

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)<br/>
Beschreibt die Concurrency Runtime, die die parallele Programmierung vereinfacht, und stellt Links zu verwandten Themen bereit.

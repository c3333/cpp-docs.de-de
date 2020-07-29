---
title: '&lt;future&gt;'
ms.date: 11/04/2016
f1_keywords:
- <future>
ms.assetid: 2f5830fc-455d-44f9-9e3d-94ea051596a2
ms.openlocfilehash: b5f18de772ea2221ecbd4098b94e0b4f14c0484c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220924"
---
# <a name="ltfuturegt"></a>&lt;future&gt;

Schließen Sie den Standard Header ein \<future> , um Klassen Vorlagen und unterstützende Vorlagen zu definieren, die das Ausführen einer Funktion – möglicherweise in einem separaten Thread – und das Abrufen des Ergebnisses vereinfachen. Das Ergebnis zeigt entweder den Wert, der von der Funktion zurückgegeben wird oder eine Ausnahme, die von der Funktion ausgegeben, aber nicht in der Funktion abgefangen wird.

Für diesen Header wird "Concurrency Runtime (ConcRT)" verwendet, sodass er zusammen mit anderen ConcRT-Mechanismen verwendet werden kann. Weitere Informationen finden Sie unter [Concurrency Runtime](../parallel/concrt/concurrency-runtime.md).

## <a name="syntax"></a>Syntax

```cpp
#include <future>
```

## <a name="remarks"></a>Bemerkungen

> [!NOTE]
> In Code, der mit **/CLR**kompiliert wird, wird dieser Header blockiert.

In einem *asynchronen Anbieter* wird das Ergebnis eines Funktionsaufrufs gespeichert. Ein a*synchrones Rückgabeobjekt* wird zum Abrufen des Ergebnisses eines Funktionsaufrufs verwendet. Ein *asynchroner zugeordneter Zustand* ermöglicht die Kommunikation zwischen einem asynchronen Anbieter und mindestens einem asynchronen Rückgabeobjekt.

Mit einem Programm werden nicht direkt zugeordnete asynchrone Zustandsobjekte erstellt. Mit dem Programm wird ein asynchroner Anbieter erstellt, wenn einer benötigt wird. Davon wird ein asynchrones Rückgabeobjekt erstellt, das dem Anbieter den asynchronen zugeordneten Zustand freigibt. Von asynchronen Anbietern und asynchronen Rückgabeobjekten werden Objekte zurückgegeben, die den freigegebenen zugeordneten asynchronen Zustand enthalten. Wenn das letzte Objekt, das den asynchronen zugeordneten Zustand verweist, diesen freigibt, wird das Objekt, das den asynchronen zugeordneten Zustand enthält, zerstört.

Ein asynchroner Anbieter oder ein asynchrones Rückgabeobjekt, das keinen verknüpften asynchronen Zustand aufweist, ist *leer*.

Ein zugeordneter asynchroner Zustand ist nur dann *bereit* , wenn sein asynchroner Anbieter einen Rückgabewert gespeichert oder eine Ausnahme gespeichert hat.

Die Vorlagen Funktion `async` und die Klassen Vorlagen `promise` und `packaged_task` sind asynchrone Anbieter. Die Klassen Vorlagen `future` und `shared_future` beschreiben asynchrone Rückgabe Objekte.

Jede der Klassen Vorlagen `promise` , `future` , und `shared_future` verfügt über eine Spezialisierung für den Typ **`void`** und eine partielle Spezialisierung zum Speichern und Abrufen eines Werts als Verweis. Diese Spezialisierungen unterscheiden sich von der primären Vorlage nur durch die Signaturen und die Semantik der Funktionen, die den zurückgegebenen Wert speichern und abrufen.

Die Klassen Vorlagen `future` und `shared_future` nie in ihren Dekonstruktoren blockieren, außer in einem Fall, der aus Gründen der Abwärtskompatibilität beibehalten wird: anders als bei allen anderen Futures, bei einem `future` – oder dem letzten `shared_future` –, das an eine Aufgabe angefügt ist, die mit gestartet wurde `std::async` , blockiert der Dekonstruktor, wenn die Aufgabe `.get()` noch nicht ausgeführt wurde `.wait()` Der folgende Hinweis zur Nutzbarkeit wurde der Beschreibung von `std::async` im Normenentwurf hinzugefügt: "[Hinweis: Wenn eine von "std::async" erhaltene Zukunft außerhalb des lokalen Bereichs verschoben wird, muss beim Schreiben von anderem Code, bei dem die Zukunft verwendet wird, beachtet werden, dass der Destruktor de Zukunft möglicherweise blockiert, sodass der Freigabezustand in den Bereitschaftszustand wechseln kann – Ende des Hinweises]". In allen anderen Fällen sind `future` und `shared_future`-Destruktoren erforderlich und blockieren garantiert nie.

## <a name="members"></a>Member

### <a name="classes"></a>Klassen

|name|BESCHREIBUNG|
|----------|-----------------|
|[zukünftige Klasse](../standard-library/future-class.md)|Beschreibt ein asynchrones Rückgabeobjekt.|
|[future_error-Klasse](../standard-library/future-error-class.md)|Beschreibt ein Ausnahmeobjekt, das von Methoden des `future`-Objekte verwaltenden Typs ausgelöst werden.|
|[packaged_task-Klasse](../standard-library/packaged-task-class.md)|Beschreibt einen asynchronen Anbieter, der ein Aufrufwrapper ist und dessen Aufrufsignatur `Ty(ArgTypes...)` ist. Der zugehörige asynchrone Zustand enthält zusätzlich zum potentiellen Ergebnisses eine Kopie des aufrufbaren Objekts .|
|[Promise-Klasse](../standard-library/promise-class.md)|Beschreibt einen asynchronen Anbieter.|
|[shared_future-Klasse](../standard-library/shared-future-class.md)|Beschreibt ein asynchrones Rückgabeobjekt. Im Gegensatz zu einem `future`-Objekt, kann ein asynchroner Anbieter beliebig vielen `shared_future`-Objekten zugeordnet werden.|

### <a name="structures"></a>Strukturen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[is_error_code_enum-Struktur](../standard-library/is-error-code-enum-structure.md)|Spezialisierungen, die angeben, dass `future_errc` für das Speichern von `error_code` geeignet ist.|
|[uses_allocator-Struktur](../standard-library/uses-allocator-structure.md)|Spezialisierung, die immer "True" ist.|

### <a name="functions"></a>Functions

|Name|BESCHREIBUNG|
|----------|-----------------|
|[async](../standard-library/future-functions.md#async)|Stellt einen asynchronen Anbieter dar.|
|[future_category](../standard-library/future-functions.md#future_category)|Gibt einen Verweis auf das `error_category`-Objekt zurück, das Fehler bestimmt, die `future`-Objekten zugeordnet werden.|
|[make_error_code](../standard-library/future-functions.md#make_error_code)|Erstellt ein `error_code`-Element, das das `error_category`-Objekt aufweist, das `future` Fehler bestimmt.|
|[make_error_condition](../standard-library/future-functions.md#make_error_condition)|Erstellt ein `error_condition`-Element, das das `error_category`-Objekt aufweist, das `future` Fehler bestimmt.|
|[swap](../standard-library/future-functions.md#swap)|Tauscht den zugeordneten Zustand eines asynchronen `promise`-Objekts mit dem des anderen aus.|

### <a name="enumerations"></a>Enumerationen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[future_errc](../standard-library/future-enums.md#future_errc)|Liefert symbolische Namen für die von der `future_error`-Klasse ausgegeben Fehler.|
|[future_status](../standard-library/future-enums.md#future_status)|Liefert symbolische Namen für die Gründe, aus denen eine zeitgesteuerte Wartefunktion eine Rückgabe ausführen kann.|
|[gestartet](../standard-library/future-enums.md#launch)|Stellt einen Bitmaskentyp dar, mit dem die möglichen Modi für die Vorlagenfunktion `async` beschrieben werden.|

## <a name="see-also"></a>Weitere Informationen

[Headerdateienreferenz](../standard-library/cpp-standard-library-header-files.md)

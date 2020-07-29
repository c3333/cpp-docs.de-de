---
title: CMemoryState-Struktur
ms.date: 11/04/2016
f1_keywords:
- CMemoryState
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
ms.openlocfilehash: 823d424620e205d14f247a147bbf7dcb40a626b9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222913"
---
# <a name="cmemorystate-structure"></a>CMemoryState-Struktur

Stellt eine bequeme Methode zum Erkennen von Speicher Verlusten in Ihrem Programm bereit.

## <a name="syntax"></a>Syntax

```
struct CMemoryState
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CMemoryState:: CMemoryState](#cmemorystate)|Erstellt eine Klassen ähnliche Struktur zum Steuern von Speicher Prüfpunkten.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CMemoryState:: Checkpoint](#checkpoint)|Ruft eine Momentaufnahme (Prüfpunkt) des aktuellen Speicher Zustands ab.|
|[CMemoryState::D ifference](#difference)|Berechnet den Unterschied zwischen zwei Objekten des Typs `CMemoryState` .|
|[CMemoryState::D-Umschlag](#dumpallobjectssince)|Sichert eine Zusammenfassung aller aktuell zugeordneten Objekte seit einem vorherigen Prüfpunkt.|
|[CMemoryState::D umpstatistics](#dumpstatistics)|Druckt Speicher Belegungs Statistiken für ein- `CMemoryState` Objekt.|

## <a name="remarks"></a>Bemerkungen

`CMemoryState`ist eine-Struktur und weist keine Basisklasse auf.

Ein "Speicherfehler" tritt auf, wenn der Speicher für ein Objekt auf dem Heap zugeordnet, aber nicht aufgehoben wird, wenn er nicht mehr benötigt wird. Solche Speicher Verluste können letztendlich zu Fehlern aufgrund von nicht genügend Arbeitsspeicher führen. Es gibt mehrere Möglichkeiten, Arbeitsspeicher in Ihrem Programm zuzuordnen und deren Speicherplatz zuzuweisen:

- Verwenden der- `malloc` /  `free` Funktions Familie aus der Lauf Zeit Bibliothek.

- Mithilfe der Windows-API-Speicherverwaltungsfunktionen `LocalAlloc` /  `LocalFree` und `GlobalAlloc` /  `GlobalFree` .

- Verwenden der C++ **`new`** -und- **`delete`** Operatoren.

Die `CMemoryState` Diagnose dient nur zum Erkennen von Speicher Verlusten, die verursacht werden, wenn der mit dem Operator zugewiesene Arbeitsspeicher **`new`** nicht mit der Zuordnung der Zuordnung **`delete`** Die anderen beiden Gruppen von Speicherverwaltungsfunktionen sind für nicht-C + +-Programme, und das kombinieren mit **`new`** und **`delete`** in demselben Programm wird nicht empfohlen. Ein zusätzliches Makro, DEBUG_NEW, wird bereitgestellt, um den Operator zu ersetzen, **`new`** Wenn Sie die Nachverfolgung von Datei-und Zeilennummern von Speicher Belegungen benötigen. DEBUG_NEW wird immer verwendet, wenn Sie normalerweise den- **`new`** Operator verwenden.

Wie bei anderen Diagnosefunktionen `CMemoryState` sind die Diagnose nur in Debugversionen des Programms verfügbar. Für eine Debugversion muss die _DEBUG Konstante definiert sein.

Wenn Sie vermuten, dass Ihr Programm einen Speicherfehler aufweist, können Sie `Checkpoint` die `Difference` Funktionen, und verwenden, `DumpStatistics` um den Unterschied zwischen dem Speicherstatus (zugeordnete Objekte) an zwei verschiedenen Punkten der Programmausführung zu ermitteln. Diese Informationen können hilfreich sein, um zu bestimmen, ob eine Funktion alle Objekte bereinigt, die Sie zuordnet.

Wenn Sie einfach wissen, an welcher Stelle das Ungleichgewicht bei der Zuordnung und der Aufhebung der Zuordnung nicht ausreicht, können Sie die- `DumpAllObjectsSince` Funktion verwenden, um alle-Objekte zu sichern, die seit dem vorherigen-Vorgang zugeordnet wurden `Checkpoint` . Diese Sicherung zeigt die Reihenfolge der Zuordnung, die Quelldatei und die Zeile an, in der das Objekt zugeordnet wurde (wenn Sie DEBUG_NEW für die Zuordnung verwenden) und die Ableitung des Objekts, seiner Adresse und seiner Größe. `DumpAllObjectsSince`Ruft auch die-Funktion jedes Objekts `Dump` auf, um Informationen über den aktuellen Zustand bereitzustellen.

Weitere Informationen zur Verwendung von `CMemoryState` und anderen Diagnosen finden Sie unter [Debuggen von MFC-Anwendungen](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
> Deklarationen von Objekten des Typs `CMemoryState` und Aufrufe an Member-Funktionen sollten durch-Anweisungen in Klammern gesetzt werden `#if defined(_DEBUG)/#endif` . Dies bewirkt, dass die Speicher Diagnose nur in Debugbuilds des Programms eingeschlossen wird.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CMemoryState`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFX. h

## <a name="cmemorystatecheckpoint"></a><a name="checkpoint"></a>CMemoryState:: Checkpoint

Erstellt eine Momentaufnahme-Zusammenfassung des Arbeitsspeichers und speichert Sie in diesem- `CMemoryState` Objekt.

```cpp
void Checkpoint();
```

### <a name="remarks"></a>Bemerkungen

Die `CMemoryState` [Unterschiede](#difference) von Element Funktionen und [dumpzuweisung](#dumpallobjectssince) verwenden diese Moment aufnahmendaten.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für den [CMemoryState](#cmemorystate) -Konstruktor.

## <a name="cmemorystatecmemorystate"></a><a name="cmemorystate"></a>CMemoryState:: CMemoryState

Erstellt ein leeres- `CMemoryState` Objekt, das von der Prüfpunkt [Checkpoint](#checkpoint) -oder [Differenz](#difference) Element Funktion ausgefüllt werden muss.

```
CMemoryState();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

## <a name="cmemorystatedifference"></a><a name="difference"></a>CMemoryState::D ifference

Vergleicht zwei- `CMemoryState` Objekte und speichert dann den Unterschied in diesem- `CMemoryState` Objekt.

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>Parameter

*oldState*<br/>
Der anfängliche Speicher Zustand, wie durch einen Prüfpunkt definiert `CMemoryState` .

*newState*<br/>
Der neue Speicher Zustand, wie durch einen Prüfpunkt definiert `CMemoryState` .

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn sich die beiden Speicher Zustände unterscheiden. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Der Prüfpunkt [muss für](#checkpoint) jeden der beiden Speicher Zustandsparameter aufgerufen werden.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für den [CMemoryState](#cmemorystate) -Konstruktor.

## <a name="cmemorystatedumpallobjectssince"></a><a name="dumpallobjectssince"></a>CMemoryState::D-Umschlag

Ruft die- `Dump` Funktion für alle Objekte eines Typs auf, der von `CObject` der-Klasse abgeleitet wurde, die seit dem letzten Prüf [Checkpoint](#checkpoint) Punkt Aufruf für dieses-Objekt zugeordnet wurden (und noch zugeordnet sind) `CMemoryState` .

```cpp
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>Bemerkungen

`DumpAllObjectsSince`Durch den Aufruf von mit einem nicht initialisierten `CMemoryState` Objekt werden alle Objekte, die sich derzeit im Speicher befinden, abgeblendet

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für den [CMemoryState](#cmemorystate) -Konstruktor.

## <a name="cmemorystatedumpstatistics"></a><a name="dumpstatistics"></a>CMemoryState::D umpstatistics

Druckt einen präzisen Speicher Statistikbericht von einem- `CMemoryState` Objekt, das von der [Difference](#difference) -Member-Funktion ausgefüllt wird.

```cpp
void DumpStatistics() const;
```

### <a name="remarks"></a>Bemerkungen

Der Bericht, der auf dem [afxDump](diagnostic-services.md#afxdump) -Gerät gedruckt wird, zeigt Folgendes:

Ein Beispiel Bericht enthält Informationen über die Anzahl (oder den Betrag) von:

- freie Blöcke

- normale Blöcke

- CRT-Blöcke

- Blöcke ignorieren

- Clientblöcke

- Maximaler Arbeitsspeicher, der vom Programm gleichzeitig verwendet wird (in Bytes)

- aktuell vom Programm verwendeter Arbeitsspeicher (in Byte)

Freie Blöcke sind die Anzahl der Blöcke, deren Aufhebung der Zuordnung verzögert wurde `afxMemDF` , wenn auf festgelegt wurde `delayFreeMemDF` . Weitere Informationen finden Sie im Abschnitt " [afxMemDF](diagnostic-services.md#afxmemdf)" im Abschnitt "MFC-Makros und Globals".

### <a name="example"></a>Beispiel

  Der folgende Code sollte in *Projektname*app. cpp abgelegt werden. Definieren Sie die folgenden globalen Variablen:

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

Fügen Sie in der- `InitInstance` Funktion die folgende Zeile hinzu:

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

Fügen Sie einen Handler für die Funktion hinzu, `ExitInstance` und verwenden Sie den folgenden Code:

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

Sie können das Programm jetzt im Debugmodus ausführen, um die Ausgabe der `DumpStatistics` Funktion anzuzeigen.

## <a name="see-also"></a>Siehe auch

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)

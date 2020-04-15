---
title: CMemoryState Structure
ms.date: 11/04/2016
f1_keywords:
- CMemoryState
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
ms.openlocfilehash: 8f49a9faf70673c62167deeaa1bef33e4882378f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369985"
---
# <a name="cmemorystate-structure"></a>CMemoryState Structure

Bietet eine bequeme Möglichkeit, Speicherverluste in Ihrem Programm zu erkennen.

## <a name="syntax"></a>Syntax

```
struct CMemoryState
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMemoryState::CMemoryState](#cmemorystate)|Erstellt eine klassenähnliche Struktur, die Speicherprüfpunkte steuert.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMemoryState::Checkpoint](#checkpoint)|Ruft einen Snapshot (Checkpoint) des aktuellen Speicherstatus ab.|
|[CMemoryState::DReferenz](#difference)|Berechnet die Differenz zwischen zwei `CMemoryState`Objekten vom Typ .|
|[CMemoryState::DumpAllObjectsSince](#dumpallobjectssince)|Dumpt eine Zusammenfassung aller aktuell zugewiesenen Objekte seit einem vorherigen Prüfpunkt.|
|[CMemoryState::DumpStatistiken](#dumpstatistics)|Druckt Speicherzuordnungsstatistiken für ein `CMemoryState` Objekt.|

## <a name="remarks"></a>Bemerkungen

`CMemoryState`ist eine Struktur und hat keine Basisklasse.

Ein "Speicherverlust" tritt auf, wenn Speicher für ein Objekt auf dem Heap zugewiesen wird, aber nicht zugewiesen wird, wenn es nicht mehr benötigt wird. Solche Speicherverluste können schließlich zu Fehlern aneben führen. Es gibt mehrere Möglichkeiten, Speicher in Ihrem Programm zuzuweisen und zu verteilen:

- Verwenden `malloc` /  `free` der Funktionsfamilie aus der Laufzeitbibliothek.

- Verwenden `LocalAlloc` /  `LocalFree` der Windows-API-Speicherverwaltungsfunktionen und `GlobalAlloc` /  `GlobalFree`.

- Verwenden der C++-Operatoren **"Neu"** und **"Löschen".**

Die `CMemoryState` Diagnose hilft nur dabei, Speicherverluste zu erkennen, die verursacht werden, wenn der mit dem **neuen** Operator zugewiesene Speicher nicht mit **delete**zugeordnet wird. Die anderen beiden Gruppen von Speicherverwaltungsfunktionen sind für Nicht-C++-Programme, und das Mischen mit **Neu** und **Löschen** im selben Programm wird nicht empfohlen. Ein zusätzliches Makro, DEBUG_NEW, wird bereitgestellt, um den **neuen** Operator zu ersetzen, wenn Sie die Datei- und Zeilennummernverfolgung von Speicherzuweisungen benötigen. DEBUG_NEW wird immer dann verwendet, wenn Sie normalerweise den **neuen** Operator verwenden würden.

Wie bei anderen Diagnosen ist die `CMemoryState` Diagnose nur in Debugversionen Ihres Programms verfügbar. Für eine Debugversion muss die _DEBUG-Konstante definiert sein.

Wenn Sie vermuten, dass Ihr Programm einen `Checkpoint` `Difference`Speicherverlust `DumpStatistics` hat, können Sie die , und Funktionen verwenden, um den Unterschied zwischen dem Speicherzustand (den zugeordneten Objekten) an zwei verschiedenen Punkten in der Programmausführung zu ermitteln. Diese Informationen können nützlich sein, um zu bestimmen, ob eine Funktion alle Objekte bereinigen, die sie zuweist.

Wenn das bloße Wissen, wo das Ungleichgewicht bei der Zuweisung und `DumpAllObjectsSince` Zuweisung auftritt, nicht genügend Informationen `Checkpoint`liefert, können Sie die Funktion verwenden, um alle Objekte zu dumpen, die seit dem vorherigen Aufruf von zugeordnet wurden. Dieses Dump zeigt die Reihenfolge der Zuordnung, die Quelldatei und Zeile, in der das Objekt zugeordnet wurde (wenn Sie DEBUG_NEW für die Zuordnung verwenden), sowie die Ableitung des Objekts, seine Adresse und seine Größe. `DumpAllObjectsSince`ruft auch die `Dump` Funktion jedes Objekts auf, um Informationen über seinen aktuellen Status bereitzustellen.

Weitere Informationen zur Verwendung `CMemoryState` und anderen Diagnosen finden Sie unter [Debuggen von MFC-Anwendungen](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
> Deklarationen von `CMemoryState` Objekten des Typs und `#if defined(_DEBUG)/#endif` Aufrufen von Memberfunktionen sollten durch Direktiven in Klammern gesetzt werden. Dies bewirkt, dass die Speicherdiagnose nur in Debugbuilds Ihres Programms enthalten ist.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CMemoryState`

## <a name="requirements"></a>Anforderungen

**Kopf:** afx.h

## <a name="cmemorystatecheckpoint"></a><a name="checkpoint"></a>CMemoryState::Checkpoint

Erstellt eine Momentaufnahme des Arbeitsspeichers und speichert ihn in diesem `CMemoryState` Objekt.

```
void Checkpoint();
```

### <a name="remarks"></a>Bemerkungen

Die `CMemoryState` Memberfunktionen [Difference](#difference) und [DumpAllObjectsSince](#dumpallobjectssince) verwenden diese Snapshot-Daten.

### <a name="example"></a>Beispiel

  Siehe beispielfür den [CMemoryState-Konstruktor.](#cmemorystate)

## <a name="cmemorystatecmemorystate"></a><a name="cmemorystate"></a>CMemoryState::CMemoryState

Erstellt ein `CMemoryState` leeres Objekt, das von der [Elementfunktion Checkpoint](#checkpoint) oder [Differenz](#difference) ausgefüllt werden muss.

```
CMemoryState();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

## <a name="cmemorystatedifference"></a><a name="difference"></a>CMemoryState::DReferenz

Vergleicht `CMemoryState` zwei Objekte und speichert `CMemoryState` dann den Unterschied in diesem Objekt.

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>Parameter

*oldState*<br/>
Der anfängliche Speicherstatus, `CMemoryState` der durch einen Prüfpunkt definiert wird.

*newState*<br/>
Der neue Speicherstatus, `CMemoryState` der durch einen Prüfpunkt definiert wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die beiden Speicherzustände unterschiedlich sind; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

[Der Prüfpunkt](#checkpoint) muss für jeden der beiden Speicherzustandsparameter aufgerufen worden sein.

### <a name="example"></a>Beispiel

  Siehe beispielfür den [CMemoryState-Konstruktor.](#cmemorystate)

## <a name="cmemorystatedumpallobjectssince"></a><a name="dumpallobjectssince"></a>CMemoryState::DumpAllObjectsSince

Ruft `Dump` die Funktion für alle Objekte `CObject` eines Typs auf, die seit dem letzten `CMemoryState` [Checkpoint-Aufruf](#checkpoint) für dieses Objekt von der Klasse abgeleitet wurden (und immer noch zugewiesen sind).

```
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>Bemerkungen

Wenn `DumpAllObjectsSince` Sie mit `CMemoryState` einem nicht initialisierten Objekt aufrufen, werden alle Objekte, die sich derzeit im Arbeitsspeicher befinden, ausgelagert.

### <a name="example"></a>Beispiel

  Siehe beispielfür den [CMemoryState-Konstruktor.](#cmemorystate)

## <a name="cmemorystatedumpstatistics"></a><a name="dumpstatistics"></a>CMemoryState::DumpStatistiken

Druckt einen präzisen `CMemoryState` Speicherstatistikbericht aus einem Objekt, das mit der [Memberfunktion Differenz](#difference) gefüllt wird.

```
void DumpStatistics() const;
```

### <a name="remarks"></a>Bemerkungen

Der Bericht, der auf dem [afxDump-Gerät](diagnostic-services.md#afxdump) gedruckt wird, zeigt Folgendes an:

Ein Beispielbericht gibt Auskunft über die Anzahl (oder den Betrag) von:

- freie Blöcke

- normale Blöcke

- CRT-Blöcke

- Ignorieren von Blöcken

- Clientblöcke

- Maximaler Speicher, der vom Programm zu jeder Zeit verwendet wird (in Bytes)

- Gesamtspeicher, der derzeit vom Programm verwendet wird (in Bytes)

Freie Blöcke sind die Anzahl der Blöcke, deren Dezuweisung verzögert wurde, wenn `afxMemDF` auf `delayFreeMemDF`festgelegt wurde. Weitere Informationen finden Sie unter [afxMemDF](diagnostic-services.md#afxmemdf), im Abschnitt "MFC-Makros und Globals".

### <a name="example"></a>Beispiel

  Der folgende Code sollte in *projname*App.cpp platziert werden. Definieren Sie die folgenden globalen Variablen:

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

Fügen `InitInstance` Sie in der Funktion die Zeile hinzu:

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

Fügen Sie einen `ExitInstance` Handler für die Funktion hinzu, und verwenden Sie den folgenden Code:

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

Sie können das Programm nun im Debug-Modus `DumpStatistics` ausführen, um die Ausgabe der Funktion anzuzeigen.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)

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
ms.openlocfilehash: a110e1345cb970c117de125bd8105e1bc86eaf94
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855298"
---
# <a name="cmemorystate-structure"></a>CMemoryState-Struktur

Stellt eine bequeme Methode zum Erkennen von Speicher Verlusten in Ihrem Programm bereit.

## <a name="syntax"></a>Syntax

```
struct CMemoryState
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMemoryState:: CMemoryState](#cmemorystate)|Erstellt eine Klassen ähnliche Struktur zum Steuern von Speicher Prüfpunkten.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CMemoryState:: Checkpoint](#checkpoint)|Ruft eine Momentaufnahme (Prüfpunkt) des aktuellen Speicher Zustands ab.|
|[CMemoryState::D ifference](#difference)|Berechnet den Unterschied zwischen zwei Objekten vom Typ `CMemoryState`.|
|[CMemoryState::D-Umschlag](#dumpallobjectssince)|Sichert eine Zusammenfassung aller aktuell zugeordneten Objekte seit einem vorherigen Prüfpunkt.|
|[CMemoryState::D umpstatistics](#dumpstatistics)|Druckt Speicher Belegungs Statistiken für ein `CMemoryState` Objekt.|

## <a name="remarks"></a>Bemerkungen

`CMemoryState` ist eine Struktur, die keine Basisklasse hat.

Ein "Speicherfehler" tritt auf, wenn der Speicher für ein Objekt auf dem Heap zugeordnet, aber nicht aufgehoben wird, wenn er nicht mehr benötigt wird. Solche Speicher Verluste können letztendlich zu Fehlern aufgrund von nicht genügend Arbeitsspeicher führen. Es gibt mehrere Möglichkeiten, Arbeitsspeicher in Ihrem Programm zuzuordnen und deren Speicherplatz zuzuweisen:

- Mithilfe der `malloc`/ `free`-Funktions Familie aus der Lauf Zeit Bibliothek.

- Mit den Funktionen der Windows-API-Speicherverwaltung `LocalAlloc`/ `LocalFree` und `GlobalAlloc`/ `GlobalFree`.

- Mithilfe der C++ **New** -und **Delete** -Operatoren.

Die `CMemoryState` Diagnose unterstützt nur das Erkennen von Speicher Verlusten, die verursacht werden, wenn der mit dem **New** -Operator zugewiesene Arbeitsspeicher nicht mit **Delete**aufgehoben wird Die anderen beiden Gruppen von Speicherverwaltungsfunktionen sind für nicht--C++ Programme, und das kombinieren mit **neuen** und **Lösch** Vorgängen in demselben Programm wird nicht empfohlen. Ein zusätzliches Makro, DEBUG_NEW, wird bereitgestellt, um den **neuen** Operator zu ersetzen, wenn Sie die Nachverfolgung von Datei-und Zeilennummern von Speicher Belegungen benötigen. DEBUG_NEW wird immer verwendet, wenn Sie normalerweise den **New** -Operator verwenden.

Wie bei anderen Diagnosefunktionen sind die `CMemoryState` Diagnose nur in Debugversionen Ihres Programms verfügbar. Für eine Debugversion muss die _DEBUG Konstante definiert sein.

Wenn Sie vermuten, dass Ihr Programm einen Speicherfehler aufweist, können Sie die Funktionen `Checkpoint`, `Difference`und `DumpStatistics` verwenden, um den Unterschied zwischen dem Speicherstatus (zugeordnete Objekte) an zwei verschiedenen Punkten der Programmausführung zu ermitteln. Diese Informationen können hilfreich sein, um zu bestimmen, ob eine Funktion alle Objekte bereinigt, die Sie zuordnet.

Wenn Sie einfach wissen, an welcher Stelle das Ungleichgewicht bei der Zuordnung und der Aufhebung der Zuordnung keine ausreichenden Informationen bereitstellt, können Sie die `DumpAllObjectsSince`-Funktion verwenden, um alle Objekte zu sichern, die seit dem vorherigen `Checkpoint`aufgerufen wurden. Diese Sicherung zeigt die Reihenfolge der Zuordnung, die Quelldatei und die Zeile an, in der das Objekt zugeordnet wurde (wenn Sie DEBUG_NEW für die Zuordnung verwenden) und die Ableitung des Objekts, seiner Adresse und seiner Größe. `DumpAllObjectsSince` ruft auch die `Dump`-Funktion jedes Objekts auf, um Informationen über den aktuellen Zustand bereitzustellen.

Weitere Informationen zur Verwendung von `CMemoryState` und anderen Diagnosen finden Sie unter [Debuggen von MFC-Anwendungen](/visualstudio/debugger/mfc-debugging-techniques).

> [!NOTE]
>  Deklarationen von Objekten vom Typ `CMemoryState` und Aufrufe an Member-Funktionen sollten von `#if defined(_DEBUG)/#endif` Direktiven in Klammern gesetzt werden. Dies bewirkt, dass die Speicher Diagnose nur in Debugbuilds des Programms eingeschlossen wird.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CMemoryState`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afx.h

##  <a name="checkpoint"></a>CMemoryState:: Checkpoint

Erstellt eine Momentaufnahme-Zusammenfassung des Arbeitsspeichers und speichert Sie in diesem `CMemoryState` Objekt.

```
void Checkpoint();
```

### <a name="remarks"></a>Bemerkungen

Die [Unterschiede](#difference) von `CMemoryState` Member-Funktionen und [Dump-enumerjectssince](#dumpallobjectssince) verwenden diese Momentaufnahme Daten.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für den [CMemoryState](#cmemorystate) -Konstruktor.

##  <a name="cmemorystate"></a>CMemoryState:: CMemoryState

Erstellt ein leeres `CMemoryState` Objekt [, das von der](#checkpoint) Prüfpunkt-oder [Differenz](#difference) Element Funktion ausgefüllt werden muss.

```
CMemoryState();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]

##  <a name="difference"></a>CMemoryState::D ifference

Vergleicht zwei `CMemoryState`-Objekte und speichert dann den Unterschied in diesem `CMemoryState`-Objekt.

```
BOOL Difference(
    const CMemoryState& oldState,
    const CMemoryState& newState);
```

### <a name="parameters"></a>Parameter

*oldState*<br/>
Der anfängliche Speicher Zustand, wie durch einen `CMemoryState` Prüfpunkt definiert.

*newState*<br/>
Der neue Speicher Zustand, wie durch einen `CMemoryState` Prüfpunkt definiert.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn sich die beiden Speicher Zustände unterscheiden. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Der Prüfpunkt [muss für](#checkpoint) jeden der beiden Speicher Zustandsparameter aufgerufen werden.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für den [CMemoryState](#cmemorystate) -Konstruktor.

##  <a name="dumpallobjectssince"></a>CMemoryState::D-Umschlag

Ruft die `Dump`-Funktion für alle Objekte eines Typs auf, der von Class `CObject` abgeleitet wurde, die seit [dem letzten Prüf](#checkpoint) Punkt Aufruf für dieses `CMemoryState`-Objekt zugeordnet wurden (und noch zugeordnet sind).

```
void DumpAllObjectsSince() const;
```

### <a name="remarks"></a>Bemerkungen

Durch das Aufrufen von `DumpAllObjectsSince` mit einem nicht initialisierten `CMemoryState` Objekt werden alle derzeit im Arbeitsspeicher ausgewerteten Objekte abgeblendet.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für den [CMemoryState](#cmemorystate) -Konstruktor.

##  <a name="dumpstatistics"></a>CMemoryState::D umpstatistics

Druckt einen präzisen Speicher Statistikbericht aus einem `CMemoryState` Objekt, das von der [Differenz](#difference) Element Funktion ausgefüllt wird.

```
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

Freie Blöcke sind die Anzahl der Blöcke, deren Aufhebung der Zuordnung verzögert wurde, wenn `afxMemDF` auf `delayFreeMemDF`festgelegt wurde. Weitere Informationen finden Sie im Abschnitt " [afxMemDF](diagnostic-services.md#afxmemdf)" im Abschnitt "MFC-Makros und Globals".

### <a name="example"></a>Beispiel

  Der folgende Code sollte in *Projektname*app. cpp abgelegt werden. Definieren Sie die folgenden globalen Variablen:

[!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]

Fügen Sie in der `InitInstance`-Funktion die folgende Zeile hinzu:

[!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]

Fügen Sie einen Handler für die `ExitInstance`-Funktion hinzu, und verwenden Sie den folgenden Code:

[!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]

Sie können das Programm jetzt im Debugmodus ausführen, um die Ausgabe der `DumpStatistics` Funktion anzuzeigen.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)

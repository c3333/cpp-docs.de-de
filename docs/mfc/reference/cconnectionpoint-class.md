---
title: CConnectionPoint-Klasse
ms.date: 11/04/2016
f1_keywords:
- CConnectionPoint
- AFXDISP/CConnectionPoint
- AFXDISP/CConnectionPoint::CConnectionPoint
- AFXDISP/CConnectionPoint::GetConnections
- AFXDISP/CConnectionPoint::GetContainer
- AFXDISP/CConnectionPoint::GetIID
- AFXDISP/CConnectionPoint::GetMaxConnections
- AFXDISP/CConnectionPoint::GetNextConnection
- AFXDISP/CConnectionPoint::GetStartPosition
- AFXDISP/CConnectionPoint::OnAdvise
- AFXDISP/CConnectionPoint::QuerySinkInterface
helpviewer_keywords:
- CConnectionPoint [MFC], CConnectionPoint
- CConnectionPoint [MFC], GetConnections
- CConnectionPoint [MFC], GetContainer
- CConnectionPoint [MFC], GetIID
- CConnectionPoint [MFC], GetMaxConnections
- CConnectionPoint [MFC], GetNextConnection
- CConnectionPoint [MFC], GetStartPosition
- CConnectionPoint [MFC], OnAdvise
- CConnectionPoint [MFC], QuerySinkInterface
ms.assetid: f0f23a1e-5e8c-41a9-aa6c-1a4793b28e8f
ms.openlocfilehash: f428ec597e0e4a56788fae2455eff80b286fda39
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87183083"
---
# <a name="cconnectionpoint-class"></a>CConnectionPoint-Klasse

Definiert einen besonderen Schnittstellentyp, "Verbindungspunkt" genannt, der verwendet wird, um mit anderen OLE-Objekten zu kommunizieren.

## <a name="syntax"></a>Syntax

```
class CConnectionPoint : public CCmdTarget
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CConnectionPoint:: CConnectionPoint](#cconnectionpoint)|Erstellt ein `CConnectionPoint`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CConnectionPoint:: GetConnections](#getconnections)|Ruft alle Verbindungspunkte in einer Verbindungs Zuordnung ab.|
|[CConnectionPoint:: getContainer](#getcontainer)|Ruft den Container des Steuer Elements ab, das die Verbindungs Zuordnung besitzt.|
|[CConnectionPoint:: getiid](#getiid)|Ruft die Schnittstellen-ID eines Verbindungs Punkts ab.|
|[CConnectionPoint:: getmaxconnections](#getmaxconnections)|Ruft die maximale Anzahl von Verbindungs Punkten ab, die von einem-Steuerelement unterstützt werden.|
|[CConnectionPoint:: GetNextConnection](#getnextconnection)|Ruft einen Zeiger auf das Verbindungselement bei *POS*ab.|
|[CConnectionPoint:: GetStartPosition](#getstartposition)|Startet eine Karten iterierung durch Zurückgeben eines Positions Werts, der an einen-Befehl übermittelt werden kann `GetNextConnection` .|
|[CConnectionPoint:: on-Empfehlung](#onadvise)|Wird vom Framework aufgerufen, wenn Verbindungen hergestellt oder unterbrochen werden.|
|[CConnectionPoint:: querysink Interface](#querysinkinterface)|Ruft einen Zeiger auf die angeforderte Senke Schnittstelle ab.|

## <a name="remarks"></a>Bemerkungen

Im Gegensatz zu normalen OLE-Schnittstellen, die verwendet werden, um die Funktionalität eines OLE-Steuer Elements zu implementieren und verfügbar zu machen, implementiert ein Verbindungspunkt eine ausgehende Schnittstelle, die Aktionen für andere Objekte initiieren kann, wie das Auslösen von Ereignissen und das Ändern von Benachrichtigungen.

Eine Verbindung besteht aus zwei Teilen: dem Objekt, das die-Schnittstelle aufruft, als "Quelle" bezeichnet, und dem Objekt, das die-Schnittstelle implementiert, so genannte "Sink". Durch die Bereitstellung eines Verbindungs Punkts ermöglicht eine Quelle senken, Verbindungen mit sich selbst herzustellen. Durch den Verbindungspunkt Mechanismus erhält ein Quell Objekt einen Zeiger auf die Implementierung der Senke eines Satzes von Element Funktionen. Um z. b. ein von der Senke implementiertes Ereignis auszulösen, kann die Quelle die entsprechende Methode der Senke-Implementierung aufzurufen.

Standardmäßig implementiert eine von `COleControl` abgeleitete Klasse zwei Verbindungspunkte: einen für Ereignisse und einen für Benachrichtigungen über Eigenschafts Änderungen. Diese Verbindungen werden verwendet, um Ereignisse auszulösen und eine Senke (z. b. den Container des Steuer Elements) zu benachrichtigen, wenn sich ein Eigenschafts Wert geändert hat. Die Unterstützung wird auch für OLE-Steuerelemente zur Implementierung zusätzlicher Verbindungspunkte bereitgestellt. Für jeden zusätzlichen Verbindungspunkt, der in der Steuerelement Klasse implementiert ist, müssen Sie einen "Verbindungsteil" deklarieren, der den Verbindungspunkt implementiert. Wenn Sie einen oder mehrere Verbindungspunkte implementieren, müssen Sie auch eine einzelne "Verbindungs Zuordnung" in der Steuerelement Klasse deklarieren.

Das folgende Beispiel veranschaulicht eine einfache Verbindungs Zuordnung und einen Verbindungspunkt für das `Sample` OLE-Steuerelement, bestehend aus zwei Code Fragmenten: der erste Teil deklariert die Verbindungs Zuordnung und den Punkt. die zweite implementiert diese Karte und diesen Punkt. Das erste Fragment wird in die Deklaration der Steuerelement Klasse im Abschnitt eingefügt **`protected`** :

[!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]

Die Makros BEGIN_CONNECTION_PART und END_CONNECTION_PART deklarieren eine eingebettete Klasse `XSampleConnPt` (abgeleitet von `CConnectionPoint` ), die diesen speziellen Verbindungspunkt implementiert. Wenn Sie Element `CConnectionPoint` Funktionen überschreiben oder eigene Element Funktionen hinzufügen möchten, deklarieren Sie Sie zwischen diesen beiden Makros. Das CONNECTION_IID-Makro überschreibt z. b. die-Element `CConnectionPoint::GetIID` Funktion, wenn diese zwischen diesen beiden Makros platziert wird.

Das zweite Code Fragment wird in die Implementierungs Datei () eingefügt. Cpp) Ihrer Steuerelement Klasse. Dieser Code implementiert die Verbindungs Zuordnung, die den zusätzlichen Verbindungspunkt umfasst `SampleConnPt` :

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]

Nachdem diese Code Fragmente eingefügt wurden, macht das OLE-Beispiel Steuerelement einen Verbindungspunkt für die- `ISampleSink` Schnittstelle verfügbar.

Verbindungspunkte unterstützen in der Regel "Multicasting", was die Möglichkeit zum Übertragen an mehrere senken mit derselben Schnittstelle ist. Im folgenden Code Fragment wird veranschaulicht, wie Multicasting durchlaufen der einzelnen senken an einem Verbindungspunkt erreicht wird:

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

In diesem Beispiel wird der aktuelle Satz von Verbindungen auf dem `SampleConnPt` Verbindungspunkt mit einem-Befehl abgerufen `CConnectionPoint::GetConnections` . Anschließend durchläuft Sie die Verbindungen und ruft `ISampleSink::SinkFunc` für jede aktive Verbindung auf.

Weitere Informationen zur Verwendung von `CConnectionPoint` finden Sie im Artikel [Verbindungspunkte](../../mfc/connection-points.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CConnectionPoint`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdisp.h

## <a name="cconnectionpointcconnectionpoint"></a><a name="cconnectionpoint"></a>CConnectionPoint:: CConnectionPoint

Erstellt ein `CConnectionPoint`-Objekt.

```
CConnectionPoint();
```

## <a name="cconnectionpointgetconnections"></a><a name="getconnections"></a>CConnectionPoint:: GetConnections

Rufen Sie diese Funktion auf, um alle aktiven Verbindungen für einen Verbindungspunkt abzurufen.

```
const CPtrArray* GetConnections();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Array von aktiven Verbindungen (senken). Einige der Zeiger im Array können NULL sein. Jeder nicht-NULL-Zeiger in diesem Array kann mithilfe eines Umwandlungs Operators sicher in einen Zeiger auf die Senkenschnittstelle konvertiert werden.

## <a name="cconnectionpointgetcontainer"></a><a name="getcontainer"></a>CConnectionPoint:: getContainer

Wird von Framework aufgerufen, um den `IConnectionPointContainer` für den Verbindungspunkt abzurufen.

```
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ein Zeiger auf den Container. andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird in der Regel durch das BEGIN_CONNECTION_PART-Makro implementiert.

## <a name="cconnectionpointgetiid"></a><a name="getiid"></a>CConnectionPoint:: getiid

Wird von Framework aufgerufen, um die Schnittstellen-ID eines Verbindungs Punkts abzurufen.

```
virtual REFIID GetIID() = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf die Schnittstellen-ID des Verbindungs Punkts.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um die Schnittstellen-ID für diesen Verbindungspunkt zurückzugeben.

## <a name="cconnectionpointgetmaxconnections"></a><a name="getmaxconnections"></a>CConnectionPoint:: getmaxconnections

Wird von Framework aufgerufen, um die maximale Anzahl von Verbindungen abzurufen, die vom Verbindungspunkt unterstützt werden.

```
virtual int GetMaxConnections();
```

### <a name="return-value"></a>Rückgabewert

Die maximale Anzahl von Verbindungen, die vom Steuerelement unterstützt werden, oder-1, wenn keine Begrenzung erreicht ist.

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung gibt "-1" zurück, was bedeutet, dass keine Begrenzung

Überschreiben Sie diese Funktion, wenn Sie die Anzahl der senken begrenzen möchten, die eine Verbindung mit dem Steuerelement herstellen können.

## <a name="cconnectionpointgetnextconnection"></a><a name="getnextconnection"></a>CConnectionPoint:: GetNextConnection

Ruft einen Zeiger auf das Verbindungselement bei *POS*ab.

```
LPUNKNOWN GetNextConnection(POSITION& pos) const;
```

### <a name="parameters"></a>Parameter

*POS*<br/>
Gibt einen Verweis auf einen Positionswert an, der von einem vorherigen `GetNextConnection` oder [GetStartPosition](#getstartposition) -Befehl zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das von *POS*angegebene Verbindungselement oder NULL.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist besonders nützlich für das Durchlaufen aller Elemente in der Verbindungs Zuordnung. Überspringen Sie beim durchlaufen alle Nullen, die von dieser Funktion zurückgegeben werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

## <a name="cconnectionpointgetstartposition"></a><a name="getstartposition"></a>CConnectionPoint:: GetStartPosition

Startet eine Karten iterierung durch Zurückgeben eines Positions Werts, der an einen [GetNextConnection](#getnextconnection) -Befehl übermittelt werden kann.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Positionswert, der eine Anfangs Position zum Durchlaufen der Zuordnung angibt. oder NULL, wenn die Zuordnung leer ist.

### <a name="remarks"></a>Bemerkungen

Die Iterations Sequenz ist nicht vorhersagbar. Daher hat das "erste Element in der Zuordnung" keine besondere Bedeutung.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CConnectionPoint:: GetNextConnection](#getnextconnection).

## <a name="cconnectionpointonadvise"></a><a name="onadvise"></a>CConnectionPoint:: on-Empfehlung

Wird von Framework aufgerufen, wenn eine Verbindung hergestellt oder getrennt wird.

```
virtual void OnAdvise(BOOL bAdvise);
```

### <a name="parameters"></a>Parameter

*bEmpfehlung*<br/>
TRUE, wenn eine Verbindung hergestellt wird. andernfalls false.

### <a name="remarks"></a>Bemerkungen

Bei der Standardimplementierung wird keine Aktion ausgeführt.

Überschreiben Sie diese Funktion, wenn Sie benachrichtigt werden möchten, wenn senken eine Verbindung mit Ihrem Verbindungspunkt herstellen oder diese trennen.

## <a name="cconnectionpointquerysinkinterface"></a><a name="querysinkinterface"></a>CConnectionPoint:: querysink Interface

Ruft einen Zeiger auf die angeforderte Senke Schnittstelle ab.

```
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,
    void** ppInterface);
```

### <a name="parameters"></a>Parameter

*punksink*<br/>
Der Bezeichner der angeforderten Senkenschnittstelle.

*ppinterface*<br/>
Ein Zeiger auf den Schnittstellen Zeiger, der von " *punksink*" identifiziert wird. Wenn das Objekt diese Schnittstelle nicht unterstützt, \* wird *ppinterface* auf NULL festgelegt.

### <a name="return-value"></a>Rückgabewert

Ein HRESULT-Standardwert.

## <a name="see-also"></a>Weitere Informationen

[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)

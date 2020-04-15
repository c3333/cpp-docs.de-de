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
ms.openlocfilehash: ce72c156ab31b742a42d2960923fc56afff656c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369432"
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
|[CConnectionPoint::CConnectionPoint](#cconnectionpoint)|Erstellt ein `CConnectionPoint`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CConnectionPoint::GetConnections](#getconnections)|Ruft alle Verbindungspunkte in einer Verbindungszuordnung ab.|
|[CConnectionPoint::GetContainer](#getcontainer)|Ruft den Container des Steuerelements ab, das eigentümer der Verbindungszuordnung ist.|
|[CConnectionPoint::GetIID](#getiid)|Ruft die Schnittstellen-ID eines Verbindungspunkts ab.|
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|Ruft die maximale Anzahl von Verbindungspunkten ab, die von einem Steuerelement unterstützt werden.|
|[CConnectionPoint::GetNextConnection](#getnextconnection)|Ruft einen Zeiger auf das Verbindungselement bei *pos*ab.|
|[CConnectionPoint::GetStartPosition](#getstartposition)|Startet eine Karteniteration, indem ein POSITION-Wert `GetNextConnection` zurückgegeben wird, der an einen Aufruf übergeben werden kann.|
|[CConnectionPoint::OnAdvise](#onadvise)|Wird vom Framework beim Herstellen oder Aufbrechen von Verbindungen aufgerufen.|
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|Ruft einen Zeiger auf die angeforderte Senkenschnittstelle ab.|

## <a name="remarks"></a>Bemerkungen

Im Gegensatz zu normalen OLE-Schnittstellen, die zum Implementieren und Verfügbarmachen der Funktionalität eines OLE-Steuerelements verwendet werden, implementiert ein Verbindungspunkt eine ausgehende Schnittstelle, die Aktionen für andere Objekte initiieren kann, z. B. das Auslösen von Ereignissen und Änderungsbenachrichtigungen.

Eine Verbindung besteht aus zwei Teilen: dem Objekt, das die Schnittstelle aufruft, die als "Quelle" bezeichnet wird, und dem Objekt, das die Schnittstelle implementiert, das als "Sink" bezeichnet wird. Durch das Aussetzen eines Verbindungspunkts ermöglicht eine Quelle Senken, Verbindungen zu sich selbst herzustellen. Über den Verbindungspunktmechanismus erhält ein Quellobjekt einen Zeiger auf die Implementierung einer Gruppe von Memberfunktionen in der Senke. Um beispielsweise ein von der Senke implementiertes Ereignis zu ausgelöst, kann die Quelle die entsprechende Methode der Implementierung der Senke aufrufen.

Standardmäßig implementiert `COleControl`eine -derived-Klasse zwei Verbindungspunkte: einen für Ereignisse und einen für Eigenschaftenänderungsbenachrichtigungen. Diese Verbindungen werden bzw. zum Auslösen von Ereignissen und zum Notifizieren einer Senke (z. B. des Containers des Steuerelements) verwendet, wenn sich ein Eigenschaftswert geändert hat. Unterstützung für OLE-Steuerelemente zum Implementieren zusätzlicher Verbindungspunkte wird ebenfalls bereitgestellt. Für jeden zusätzlichen Verbindungspunkt, der in Ihrer Steuerelementklasse implementiert ist, müssen Sie einen "Verbindungsteil" deklarieren, der den Verbindungspunkt implementiert. Wenn Sie einen oder mehrere Verbindungspunkte implementieren, müssen Sie auch eine einzelne "Verbindungszuordnung" in Ihrer Steuerelementklasse deklarieren.

Das folgende Beispiel veranschaulicht eine einfache Verbindungszuordnung `Sample` und einen Verbindungspunkt für das OLE-Steuerelement, das aus zwei Codefragmenten besteht: Der erste Teil deklariert die Verbindungszuordnung und den Punkt; die zweite implementiert diese Karte und Punkt. Das erste Fragment wird in die Deklaration der Steuerelementklasse unter dem **geschützten** Abschnitt eingefügt:

[!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]

Die BEGIN_CONNECTION_PART und END_CONNECTION_PART-Makros `XSampleConnPt` eine eingebettete Klasse (abgeleitet von ) deklarieren, die `CConnectionPoint`diesen bestimmten Verbindungspunkt implementiert. Wenn Sie `CConnectionPoint` Memberfunktionen überschreiben oder eigene Memberfunktionen hinzufügen möchten, deklarieren Sie diese zwischen diesen beiden Makros. Beispielsweise überschreibt das CONNECTION_IID `CConnectionPoint::GetIID` Makro die Memberfunktion, wenn sie zwischen diesen beiden Makros platziert wird.

Das zweite Codefragment wird in die Implementierungsdatei (. CPP) Ihrer Kontrollklasse. Dieser Code implementiert die Verbindungszuordnung, die den `SampleConnPt`zusätzlichen Verbindungspunkt enthält:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]

Nachdem diese Codefragmente eingefügt wurden, macht das OLE-Beispielsteuerelement `ISampleSink` einen Verbindungspunkt für die Schnittstelle verfügbar.

In der Regel unterstützen Verbindungspunkte "Multicasting", d. h. die Möglichkeit, an mehrere Senken zu senden, die mit derselben Schnittstelle verbunden sind. Das folgende Codefragment veranschaulicht, wie Multicastings durch Durchlaufen jeder Senke auf einem Verbindungspunkt erreicht werden:

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

In diesem Beispiel wird der aktuelle `SampleConnPt` Satz von Verbindungen `CConnectionPoint::GetConnections`auf dem Verbindungspunkt mit einem Aufruf von abgerufen. Es iteriert dann durch `ISampleSink::SinkFunc` die Verbindungen und ruft jede aktive Verbindung auf.

Weitere Informationen zur `CConnectionPoint`Verwendung finden Sie im Artikel [Verbindungspunkte](../../mfc/connection-points.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CConnectionPoint`

## <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="cconnectionpointcconnectionpoint"></a><a name="cconnectionpoint"></a>CConnectionPoint::CConnectionPoint

Erstellt ein `CConnectionPoint`-Objekt.

```
CConnectionPoint();
```

## <a name="cconnectionpointgetconnections"></a><a name="getconnections"></a>CConnectionPoint::GetConnections

Rufen Sie diese Funktion auf, um alle aktiven Verbindungen für einen Verbindungspunkt abzurufen.

```
const CPtrArray* GetConnections();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Array aktiver Verbindungen (Senken). Einige zeigers im Array sind möglicherweise NULL. Jeder Nicht-NULL-Zeiger in diesem Array kann mithilfe eines Umwandlungsoperators sicher in einen Zeiger auf die Senkenschnittstelle konvertiert werden.

## <a name="cconnectionpointgetcontainer"></a><a name="getcontainer"></a>CConnectionPoint::GetContainer

Wird vom Framework aufgerufen, um den `IConnectionPointContainer` für den Verbindungspunkt abzurufen.

```
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, ein Zeiger auf den Container; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird in der Regel vom BEGIN_CONNECTION_PART Makro implementiert.

## <a name="cconnectionpointgetiid"></a><a name="getiid"></a>CConnectionPoint::GetIID

Wird vom Framework aufgerufen, um die Schnittstellen-ID eines Verbindungspunkts abzurufen.

```
virtual REFIID GetIID() = 0;
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf die Schnittstellen-ID des Verbindungspunkts.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um die Schnittstellen-ID für diesen Verbindungspunkt zurückzugeben.

## <a name="cconnectionpointgetmaxconnections"></a><a name="getmaxconnections"></a>CConnectionPoint::GetMaxConnections

Wird vom Framework aufgerufen, um die maximale Anzahl von Verbindungen abzurufen, die vom Verbindungspunkt unterstützt werden.

```
virtual int GetMaxConnections();
```

### <a name="return-value"></a>Rückgabewert

Die maximale Anzahl von Verbindungen, die vom Steuerelement unterstützt werden, oder -1, wenn keine Begrenzung vorhanden ist.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung gibt -1 zurück, was auf keine Begrenzung hinweist.

Überschreiben Sie diese Funktion, wenn Sie die Anzahl der Senken begrenzen möchten, die eine Verbindung mit dem Steuerelement herstellen können.

## <a name="cconnectionpointgetnextconnection"></a><a name="getnextconnection"></a>CConnectionPoint::GetNextConnection

Ruft einen Zeiger auf das Verbindungselement bei *pos*ab.

```
LPUNKNOWN GetNextConnection(POSITION& pos) const;
```

### <a name="parameters"></a>Parameter

*Pos*<br/>
Gibt einen Verweis auf einen POSITION-Wert an, der von einem vorherigen `GetNextConnection` oder [GetStartPosition-Aufruf](#getstartposition) zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Verbindungselement, das durch *pos*oder NULL angegeben wird.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist besonders nützlich, um alle Elemente in der Verbindungszuordnung zu durchlaufen. Überspringen Sie beim Iterieren alle NULLs, die von dieser Funktion zurückgegeben werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

## <a name="cconnectionpointgetstartposition"></a><a name="getstartposition"></a>CConnectionPoint::GetStartPosition

Startet eine Karteniteration, indem ein POSITION-Wert zurückgegeben wird, der an einen [GetNextConnection-Aufruf](#getnextconnection) übergeben werden kann.

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>Rückgabewert

Ein POSITION-Wert, der eine Startposition für die Iterierung der Karte angibt; oder NULL, wenn die Karte leer ist.

### <a name="remarks"></a>Bemerkungen

Die Iterationssequenz ist nicht vorhersagbar. Daher hat das "erste Element in der Karte" keine besondere Bedeutung.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CConnectionPoint::GetNextConnection](#getnextconnection).

## <a name="cconnectionpointonadvise"></a><a name="onadvise"></a>CConnectionPoint::OnAdvise

Wird vom Framework aufgerufen, wenn eine Verbindung hergestellt oder unterbrochen wird.

```
virtual void OnAdvise(BOOL bAdvise);
```

### <a name="parameters"></a>Parameter

*bAdvise*<br/>
TRUE, wenn eine Verbindung hergestellt wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Bei der Standardimplementierung wird keine Aktion ausgeführt.

Überschreiben Sie diese Funktion, wenn Sie eine Benachrichtigung wünschen, wenn Senken eine Verbindung zum Verbindungspunkt herstellen oder die Verbindung zum Verbindungspunkt trennen sollen.

## <a name="cconnectionpointquerysinkinterface"></a><a name="querysinkinterface"></a>CConnectionPoint::QuerySinkInterface

Ruft einen Zeiger auf die angeforderte Senkenschnittstelle ab.

```
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,
    void** ppInterface);
```

### <a name="parameters"></a>Parameter

*pUnkSink*<br/>
Der Bezeichner der angeforderten Senkenschnittstelle.

*ppSchnittstelle*<br/>
Ein Zeiger auf den Schnittstellenzeiger, der von *pUnkSink*identifiziert wird. Wenn das Objekt diese Schnittstelle \* nicht unterstützt, wird *ppInterface* auf NULL gesetzt.

### <a name="return-value"></a>Rückgabewert

Ein Standard-HRESULT-Wert.

## <a name="see-also"></a>Siehe auch

[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)

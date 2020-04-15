---
title: CDocObjectServer-Klasse
ms.date: 09/12/2018
f1_keywords:
- CDocObjectServer
- AFXDOCOB/CDocObjectServer
- AFXDOCOB/CDocObjectServer::CDocObjectServer
- AFXDOCOB/CDocObjectServer::ActivateDocObject
- AFXDOCOB/CDocObjectServer::OnActivateView
- AFXDOCOB/CDocObjectServer::OnApplyViewState
- AFXDOCOB/CDocObjectServer::OnSaveViewState
helpviewer_keywords:
- CDocObjectServer [MFC], CDocObjectServer
- CDocObjectServer [MFC], ActivateDocObject
- CDocObjectServer [MFC], OnActivateView
- CDocObjectServer [MFC], OnApplyViewState
- CDocObjectServer [MFC], OnSaveViewState
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
ms.openlocfilehash: ccd8ddc9f4981b3d9f7f4e1decdf6790cd05b98b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375491"
---
# <a name="cdocobjectserver-class"></a>CDocObjectServer-Klasse

Implementiert die zusätzlichen OLE-Schnittstellen, die erforderlich sind, um aus einem normalen `COleDocument` -Server einen vollständigen DocObject-Server zu machen: `IOleDocument`, `IOleDocumentView`, `IOleCommandTarget`und `IPrint`.

## <a name="syntax"></a>Syntax

```
class CDocObjectServer : public CCmdTarget
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDocObjectServer::CDocObjectServer](#cdocobjectserver)|Erstellt ein `CDocObjectServer`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDocObjectServer::ActivateDocObject](#activatedocobject)|Aktiviert den Dokumentobjektserver, zeigt ihn jedoch nicht an.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDocObjectServer::OnActivateView](#onactivateview)|Zeigt die DocObject-Ansicht an.|
|[CDocObjectServer::OnApplyViewState](#onapplyviewstate)|Stellt den Status der DocObject-Ansicht wieder her.|
|[CDocObjectServer::OnSaveViewState](#onsaveviewstate)|Speichert den Status der DocObject-Ansicht.|

## <a name="remarks"></a>Bemerkungen

`CDocObjectServer`abgeleitet `CCmdTarget` ist und eng `COleServerDoc` mit den Schnittstellen zusammenarbeitet.

Ein DocObject-Serverdokument kann [CDocObjectServerItem-Objekte](../../mfc/reference/cdocobjectserveritem-class.md) enthalten, die die Serverschnittstelle zu DocObject-Elementen darstellen.

Um Ihren DocObject-Server anzupassen, leiten `CDocObjectServer` Sie Ihre eigene Klasse von den Ansichtseinrichtungsfunktionen [OnActivateView](#onactivateview), [OnApplyViewState](#onapplyviewstate)und [OnSaveViewState](#onsaveviewstate)ab und überschreiben diese. Sie müssen eine neue Instanz Ihrer Klasse als Reaktion auf Frameworkaufrufe bereitstellen.

Weitere Informationen zu DocObjects finden Sie unter [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) und [COleCmdUI](../../mfc/reference/colecmdui-class.md) in der *MFC-Referenz*.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocObjectServer`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxdocob.h

## <a name="cdocobjectserveractivatedocobject"></a><a name="activatedocobject"></a>CDocObjectServer::ActivateDocObject

Rufen Sie diese Funktion auf, um den Dokumentobjektserver zu aktivieren (aber nicht anzuzeigen).

```
void ActivateDocObject();
```

### <a name="remarks"></a>Bemerkungen

`ActivateDocObject`ruft `IOleDocumentSite`die `ActivateMe` Methode auf, zeigt die Ansicht jedoch nicht an, da sie auf bestimmte Anweisungen zum Einrichten und Anzeigen der Ansicht wartet, die im Aufruf von [CDocObjectServer::OnActivateView](#onactivateview)angegeben sind.

Aktivieren `ActivateDocObject` und `OnActivateView` zeigen Sie gemeinsam die DocObject-Ansicht an. Die DocObject-Aktivierung unterscheidet sich von anderen Arten der ortsbasierten OLE-Aktivierung. Die DocObject-Aktivierung umgeht die Anzeige von ortseigenen Schraffurrahmen und Objektverzierungen (z. B. Größengriffen), ignoriert Objektausdehnungsfunktionen und zeichnet Bildlaufleisten innerhalb des Ansichtsrechtecks, anstatt sie außerhalb dieses Rechtecks zu zeichnen (wie bei der normalen direkt erfolgten Aktivierung).

## <a name="cdocobjectservercdocobjectserver"></a><a name="cdocobjectserver"></a>CDocObjectServer::CDocObjectServer

Erstellt und initialisiert ein `CDocObjectServer`-Objekt.

```
explicit CDocObjectServer(
    COleServerDoc* pOwner,
    LPOLEDOCUMENTSITE pDocSite = NULL);
```

### <a name="parameters"></a>Parameter

*pOwner*<br/>
Ein Zeiger auf das Clientwebsitedokument, das der Client für den DocObject-Server ist.

*pDocSite*<br/>
Ein Zeiger auf `IOleDocumentSite` die vom Container implementierte Schnittstelle.

### <a name="remarks"></a>Bemerkungen

Wenn ein DocObject aktiv ist, ermöglicht `IOleDocumentSite`die OLE-Schnittstelle der Clientsite ( ) dem DocObject-Server die Kommunikation mit seinem Client (dem Container). Wenn ein DocObject-Server aktiviert ist, überprüft er `IOleDocumentSite` zunächst, ob der Container die Schnittstelle implementiert. Wenn dies der Zuspruch hat, wird [COleServerDoc::GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver) aufgerufen, um zu sehen, ob der Container DocObjects unterstützt. Gibt standardmäßig `GetDocObjectServer` NULL zurück. Sie müssen `COleServerDoc::GetDocObjectServer` überschreiben, `CDocObjectServer` um ein neues Oder ein eigenes abgeleitetes `COleServerDoc` Objekt mit `IOleDocumentSite` Zeigern auf den Container und dessen Schnittstelle als Argumente für den Konstruktor zu erstellen.

## <a name="cdocobjectserveronactivateview"></a><a name="onactivateview"></a>CDocObjectServer::OnActivateView

Rufen Sie diese Funktion auf, um die DocObject-Ansicht anzuzeigen.

```
virtual HRESULT OnActivateView();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Fehler- oder Warnwert zurück. Gibt standardmäßig NOERROR zurück, wenn es erfolgreich ist. andernfalls E_FAIL.

### <a name="remarks"></a>Bemerkungen

Diese Funktion erstellt ein ortsspezifisches Rahmenfenster, zeichnet Bildlaufleisten innerhalb der Ansicht, richtet die Menüs ein, die der Server mit seinem Container teilt, fügt Framesteuerelemente hinzu, legt das aktive Objekt fest, zeigt dann schließlich das eingefügte Rahmenfenster an und legt den Fokus fest.

## <a name="cdocobjectserveronapplyviewstate"></a><a name="onapplyviewstate"></a>CDocObjectServer::OnApplyViewState

Überschreiben Sie diese Funktion, um den Status der DocObject-Ansicht wiederherzustellen.

```
virtual void OnApplyViewState(CArchive& ar);
```

### <a name="parameters"></a>Parameter

*ar*<br/>
Ein `CArchive` Objekt, von dem aus der Ansichtszustand serialisiert werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird aufgerufen, wenn die Ansicht nach ihrer Instanziierung zum ersten Mal angezeigt wird. `OnApplyViewState`weist eine Ansicht an, sich entsprechend den Daten `CArchive` in dem zuvor mit [OnSaveViewState](#onsaveviewstate)gespeicherten Objekt erneut zu initialisieren. Die Ansicht muss die `CArchive` Daten im Objekt überprüfen, da der Container nicht versucht, die Ansichtszustandsdaten in irgendeiner Weise zu interpretieren.

Sie können `OnSaveViewState` persistente Informationen speichern, die für den Status Ihrer Ansicht spezifisch sind. Wenn Sie `OnSaveViewState` zum Speichern von Informationen überschreiben, sollten Sie diese Informationen überschreiben, `OnApplyViewState` um diese Informationen zu lesen und sie auf Ihre Ansicht anzuwenden, wenn sie neu aktiviert wird.

## <a name="cdocobjectserveronsaveviewstate"></a><a name="onsaveviewstate"></a>CDocObjectServer::OnSaveViewState

Überschreiben Sie diese Funktion, um zusätzliche Statusinformationen zu Ihrer DocObject-Ansicht zu speichern.

```
virtual void OnSaveViewState(CArchive& ar);
```

### <a name="parameters"></a>Parameter

*ar*<br/>
Ein `CArchive` Objekt, für das der Ansichtszustand serialisiert wird.

### <a name="remarks"></a>Bemerkungen

Ihr Status kann Eigenschaften wie Ansichtstyp, Zoomfaktor, Einfüge- und Auswahlpunkt usw. enthalten. Der Container ruft diese Funktion in der Regel auf, bevor die Ansicht deaktiviert wird. Der gespeicherte Status kann später über [OnApplyViewState](#onapplyviewstate)wiederhergestellt werden.

Sie können `OnSaveViewState` persistente Informationen speichern, die für den Status Ihrer Ansicht spezifisch sind. Wenn Sie `OnSaveViewState` zum Speichern von Informationen überschreiben, sollten Sie diese Informationen überschreiben, `OnApplyViewState` um diese Informationen zu lesen und sie auf Ihre Ansicht anzuwenden, wenn sie neu aktiviert wird.

## <a name="see-also"></a>Siehe auch

[CCmdTarget-Klasse](../../mfc/reference/ccmdtarget-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServerItem-Klasse](../../mfc/reference/cdocobjectserveritem-class.md)

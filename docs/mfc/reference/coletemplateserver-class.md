---
title: COleTemplateServer-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleTemplateServer
- AFXDISP/COleTemplateServer
- AFXDISP/COleTemplateServer::COleTemplateServer
- AFXDISP/COleTemplateServer::ConnectTemplate
- AFXDISP/COleTemplateServer::Unregister
- AFXDISP/COleTemplateServer::UpdateRegistry
helpviewer_keywords:
- COleTemplateServer [MFC], COleTemplateServer
- COleTemplateServer [MFC], ConnectTemplate
- COleTemplateServer [MFC], Unregister
- COleTemplateServer [MFC], UpdateRegistry
ms.assetid: 47a2887d-8162-4993-a842-a784177c7f5c
ms.openlocfilehash: 561da5060aae3c938dc3e55d0310718a881c1a3b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753730"
---
# <a name="coletemplateserver-class"></a>COleTemplateServer-Klasse

Wird für OLE-Server mit direkter Aktivierung, Automatisierungsserver und Linkcontainer verwendet (also in Anwendungen, die Links zu Einbettungen unterstützen).

## <a name="syntax"></a>Syntax

```
class COleTemplateServer : public COleObjectFactory
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleTemplateServer::COleTemplateServer](#coletemplateserver)|Erstellt ein `COleTemplateServer`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleTemplateServer::ConnectTemplate](#connecttemplate)|Verbindet eine Dokumentvorlage `COleObjectFactory` mit dem zugrunde liegenden Objekt.|
|[COleTemplateServer::Registrieren](#unregister)|Heben Sie die Registrierung der zugeordneten Dokumentvorlage auf.|
|[COleTemplateServer::UpdateRegistry](#updateregistry)|Registriert den Dokumenttyp bei der OLE-Systemregistrierung.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse wird von der Klasse [COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)abgeleitet. in der Regel `COleTemplateServer` können Sie direkt verwenden, anstatt Ihre eigene Klasse abzuleiten. `COleTemplateServer`verwendet ein [CDocTemplate-Objekt,](../../mfc/reference/cdoctemplate-class.md) um die Serverdokumente zu verwalten. Verwenden `COleTemplateServer` Sie diese Version beim Implementieren eines vollständigen Servers, d. h. eines Servers, der als eigenständige Anwendung ausgeführt werden kann. Vollständige Server sind in der Regel MDI-Anwendungen (Multiple Document Interface), obwohl SDI-Anwendungen (Single Document Interface) unterstützt werden. Für `COleTemplateServer` jeden Servertyp, den eine Anwendung unterstützt, wird ein Objekt benötigt. Wenn Ihre Serveranwendung sowohl Arbeitsblätter als auch Diagramme `COleTemplateServer` unterstützt, müssen Sie über zwei Objekte verfügen.

`COleTemplateServer`überschreibt `OnCreateInstance` die Memberfunktion, die durch `COleObjectFactory`definiert ist. Diese Memberfunktion wird vom Framework aufgerufen, um ein C++-Objekt des richtigen Typs zu erstellen.

Weitere Informationen zu Servern finden Sie im Artikel [Server: Implementieren eines Servers](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleObjectFactory](../../mfc/reference/coleobjectfactory-class.md)

`COleTemplateServer`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdisp.h

## <a name="coletemplateservercoletemplateserver"></a><a name="coletemplateserver"></a>COleTemplateServer::COleTemplateServer

Erstellt ein `COleTemplateServer`-Objekt.

```
COleTemplateServer();
```

### <a name="remarks"></a>Bemerkungen

Eine kurze Beschreibung der Verwendung `COleTemplateServer` der Klasse finden Sie in der [COleLinkingDoc-Klassenübersicht.](../../mfc/reference/colelinkingdoc-class.md)

## <a name="coletemplateserverconnecttemplate"></a><a name="connecttemplate"></a>COleTemplateServer::ConnectTemplate

Verbindet die Dokumentvorlage, auf die *pDocTemplate* zeigt, mit dem zugrunde liegenden [COleObjectFactory-Objekt.](../../mfc/reference/coleobjectfactory-class.md)

```cpp
void ConnectTemplate(
    REFCLSID clsid,
    CDocTemplate* pDocTemplate,
    BOOL bMultiInstance);
```

### <a name="parameters"></a>Parameter

*clsid*<br/>
Verweis auf die OLE-Klassen-ID, die die Vorlage anfordert.

*pDocTemplate*<br/>
Zeiger auf die Dokumentvorlage.

*bMultiInstance*<br/>
Gibt an, ob eine einzelne Instanz der Anwendung mehrere Instanziierungen unterstützen kann. Wenn TRUE, werden mehrere Instanzen der Anwendung für jede Anforderung zum Erstellen eines Objekts gestartet.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [CLSID-Schlüssel](/windows/win32/com/clsid-key-hklm) im Windows SDK.

## <a name="coletemplateserverunregister"></a><a name="unregister"></a>COleTemplateServer::Registrieren

Heben Sie die Registrierung der zugeordneten Dokumentvorlage auf.

```
BOOL Unregister();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn erfolgreich, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

EnterRemarks

## <a name="coletemplateserverupdateregistry"></a><a name="updateregistry"></a>COleTemplateServer::UpdateRegistry

Lädt Dateitypinformationen aus der Dokumentvorlagenzeichenfolge und platziert diese Informationen in der OLE-Systemregistrierung.

```cpp
void UpdateRegistry(
    OLE_APPTYPE nAppType = OAT_INPLACE_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL,
    BOOL bRegister = TRUE);
```

### <a name="parameters"></a>Parameter

*nAppType*<br/>
Ein Wert aus der OLE_APPTYPE-Enumeration, die in AFXDISP definiert ist. H. Es kann einen der folgenden Werte haben:

- OAT_INPLACE_SERVER Server verfügt über eine vollständige Server-Benutzeroberfläche.

- OAT_SERVER Server unterstützt nur das Einbetten.

- OAT_CONTAINER Container unterstützt Links zu eingebetteten Objekten.

- OAT_DISPATCH_OBJECT-Objekt `IDispatch`ist -fähig.

- OAT_DOC_OBJECT_SERVER Server unterstützt sowohl das Einbetten als auch das Dokumentobjektkomponentenmodell.

*rglpszRegister*<br/>
Eine Liste von Einträgen, die nur dann in die Registrierung geschrieben werden, wenn keine Einträge vorhanden sind.

*rglpszOverwrite*<br/>
Eine Liste von Einträgen, die in die Registrierung geschrieben werden, unabhängig davon, ob vorhergehende Einträge vorhanden sind.

*bRegister*<br/>
Bestimmt, ob die Klasse registriert werden soll. Wenn *bRegister* TRUE ist, wird die Klasse bei der Systemregistrierung registriert. Andernfalls wird die Registrierung der Klasse aufheben.

### <a name="remarks"></a>Bemerkungen

Die Registrierungsinformationen werden über einen Aufruf von [CDocTemplate::GetDocString](../../mfc/reference/cdoctemplate-class.md#getdocstring)geladen. Bei den abgerufenen Teilzeichenfolgen `regFileTypeId`handelt `regFileTypeName`es `fileNewName`sich um `GetDocString` die, die durch die Indizes , und , wie in den Referenzseiten beschrieben, identifiziert werden.

Wenn `regFileTypeId` die Teilzeichenfolge leer ist `GetDocString` oder der Aufruf aus einem anderen Grund fehlschlägt, schlägt diese Funktion fehl, und die Dateiinformationen werden nicht in die Registrierung eingegeben.

Die Informationen in den Argumenten *rglpszRegister* und *rglpszOverwrite* werden über einen Aufruf von [AfxOleRegisterServerClass](application-control.md#afxoleregisterserverclass)in die Registrierung geschrieben. Die Standardinformationen, die registriert werden, wenn die beiden Argumente NULL sind, sind für die meisten Anwendungen geeignet. Informationen zur Struktur der Informationen in diesen `AfxOleRegisterServerClass`Argumenten finden Sie unter .

Weitere Informationen finden Sie unter [Implementing the IDispatch Interface](/previous-versions/windows/desktop/automat/implementing-the-idispatch-interface).

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleObjectFactory-Klasse](../../mfc/reference/coleobjectfactory-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc-Klasse](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleServerItem-Klasse](../../mfc/reference/coleserveritem-class.md)

---
title: CCachedDataPathProperty-Klasse
ms.date: 11/04/2016
f1_keywords:
- CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::CCachedDataPathProperty
- AFXCTL/CCachedDataPathProperty::m_Cache
helpviewer_keywords:
- CCachedDataPathProperty [MFC], CCachedDataPathProperty
- CCachedDataPathProperty [MFC], m_Cache
ms.assetid: 0d81356b-4fe5-43f6-aed2-2eb5a5485706
ms.openlocfilehash: ebab34433f23b119e3444b3eaa8b0ad6313555af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352370"
---
# <a name="ccacheddatapathproperty-class"></a>CCachedDataPathProperty-Klasse

Implementiert eine asynchron übertragene und in einer Arbeitsspeicherdatei zwischengespeicherte OLE-Steuerelementeigenschaft.

## <a name="syntax"></a>Syntax

```
class CCachedDataPathProperty : public CDataPathProperty
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCachedDataPathProperty::CCachedDataPathProperty](#ccacheddatapathproperty)|Erstellt ein `CCachedDataPathProperty`-Objekt.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCachedDataPathProperty::m_Cache](#m_cache)|`CMemFile`Objekt, in dem Daten zwischengespeichert werden sollen.|

## <a name="remarks"></a>Bemerkungen

Eine Speicherdatei wird im RAM und nicht auf der Festplatte gespeichert und ist für schnelle temporäre Übertragungen nützlich.

Zusammen `CAysncMonikerFile` mit `CDataPathProperty` `CCachedDataPathProperty` und bietet Funktionalität für die Verwendung von asynchronen Monikern in OLE-Steuerelementen. Bei `CCachedDataPathProperty` Objekten können Sie Daten asynchron von einer URL oder Dateiquelle übertragen und `m_Cache` über die öffentliche Variable in einer Speicherdatei speichern. Alle Daten werden in der Speicherdatei gespeichert, und Es ist nicht erforderlich, [OnDataAvailable](../../mfc/reference/casyncmonikerfile-class.md#ondataavailable) zu überschreiben, es sei denn, Sie möchten auf Benachrichtigungen achten und antworten. Wenn Sie z. B. eine große übertragen. GIF-Datei und möchten Ihr Steuerelement benachrichtigen, dass mehr Daten `OnDataAvailable` angekommen sind und es sollte sich neu zeichnen, überschreiben, um die Benachrichtigung zu machen.

Die `CCachedDataPathProperty` Klasse wird `CDataPathProperty`von abgeleitet.

Weitere Informationen zur Verwendung asynchroner Moniker und ActiveX-Steuerelemente in Internetanwendungen finden Sie in den folgenden Themen:

- [Erste Schritte im Internet: ActiveX-Steuerelemente](../../mfc/activex-controls-on-the-internet.md)

- [Erste Schritte im Internet: Asynchrone Moniker](../../mfc/asynchronous-monikers-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

[CAsyncMonikerFile](../../mfc/reference/casyncmonikerfile-class.md)

[CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)

`CCachedDataPathProperty`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxctl.h

## <a name="ccacheddatapathpropertyccacheddatapathproperty"></a><a name="ccacheddatapathproperty"></a>CCachedDataPathProperty::CCachedDataPathProperty

Erstellt ein `CCachedDataPathProperty`-Objekt.

```
CCachedDataPathProperty(COleControl* pControl = NULL);

CCachedDataPathProperty(
    LPCTSTR lpszPath,
    COleControl* pControl = NULL);
```

### <a name="parameters"></a>Parameter

*pControl*<br/>
Ein Zeiger auf das ActiveX-Steuerelementobjekt, `CCachedDataPathProperty` das diesem Objekt zugeordnet werden soll.

*lpszPath*<br/>
Der Pfad, der absolut oder relativ sein kann, wird verwendet, um einen asynchronen Moniker zu erstellen, der auf die tatsächliche absolute Position der Eigenschaft verweist. `CCachedDataPathProperty`verwendet URLs, nicht Dateinamen. Wenn Sie `CCachedDataPathProperty` ein Objekt für eine Datei benötigen, stellen Sie file:// dem Pfad vor.

### <a name="remarks"></a>Bemerkungen

Das `COleControl` Objekt, auf das *pControl* zeigt, wird von [Open](../../mfc/reference/cdatapathproperty-class.md#open) verwendet und von abgeleiteten Klassen abgerufen. Wenn *pControl* NULL ist, `Open` sollte das verwendete Steuerelement mit [SetControl](../../mfc/reference/cdatapathproperty-class.md#setcontrol)festgelegt werden. Wenn *lpszPath* NULL ist, können Sie `Open` den Pfad durchgehen oder mit [SetPath](../../mfc/reference/cdatapathproperty-class.md#setpath)festlegen.

## <a name="ccacheddatapathpropertym_cache"></a><a name="m_cache"></a>CCachedDataPathProperty::m_Cache

Enthält den Klassennamen der Speicherdatei, in der Daten zwischengespeichert werden.

```
CMemFile m_Cache;
```

### <a name="remarks"></a>Bemerkungen

Eine Speicherdatei wird im RAM und nicht auf dem Datenträger gespeichert.

## <a name="see-also"></a>Siehe auch

[CDataPathProperty-Klasse](../../mfc/reference/cdatapathproperty-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDataPathProperty-Klasse](../../mfc/reference/cdatapathproperty-class.md)

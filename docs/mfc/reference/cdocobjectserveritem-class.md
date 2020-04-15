---
title: CDocObjectServerItem-Klasse
ms.date: 03/27/2019
f1_keywords:
- CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::CDocObjectServerItem
- AFXDOCOB/CDocObjectServerItem::GetDocument
- AFXDOCOB/CDocObjectServerItem::OnDoVerb
- AFXDOCOB/CDocObjectServerItem::OnHide
- AFXDOCOB/CDocObjectServerItem::OnShow
helpviewer_keywords:
- CDocObjectServerItem [MFC], CDocObjectServerItem
- CDocObjectServerItem [MFC], GetDocument
- CDocObjectServerItem [MFC], OnDoVerb
- CDocObjectServerItem [MFC], OnHide
- CDocObjectServerItem [MFC], OnShow
ms.assetid: 530f7156-50c8-4806-9328-602c9133f622
ms.openlocfilehash: 1f0f5cf93aab35a17f7174b2beee0d1398564a3d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375527"
---
# <a name="cdocobjectserveritem-class"></a>CDocObjectServerItem-Klasse

Implementiert OLE-Serververben speziell für DocObject-Server.

## <a name="syntax"></a>Syntax

```
class CDocObjectServerItem : public COleServerItem
```

## <a name="members"></a>Member

### <a name="protected-constructors"></a>Geschützte Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDocObjectServerItem::CDocObjectServerItem](#cdocobjectserveritem)|Erstellt ein `CDocObjectServerItem`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDocObjectServerItem::GetDocument](#getdocument)|Ruft einen Zeiger auf das Dokument ab, das das Element enthält.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CdocObjectServerItem::OnDoverb](#ondoverb)|Wird aufgerufen, um ein Verb auszuführen.|
|[CDocObjectServerItem::OnHide](#onhide)|Löst eine Ausnahme aus, wenn das Framework versucht, ein DocObject-Element auszublenden.|
|[CDocObjectServerItem::OnShow](#onshow)|Wird vom Framework aufgerufen, um das DocObject-Element an Ort und Stelle aktiv zu machen. Wenn es sich bei dem Element nicht um ein DocObject handelt, ruft [cOleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onshow)auf.|

## <a name="remarks"></a>Bemerkungen

`CDocObjectServerItem`definiert überschreibbare Memberfunktionen: [OnHide](#onhide), [OnDoVerb](#ondoverb)und [OnShow](#onshow).

Um `CDocObjectServerItem`zu verwenden, stellen Sie sicher, `COleServerDoc`dass die [OnGetEmbeddedItem-Überschreibung](../../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) in Ihrer -derived-Klasse ein neues `CDocObjectServerItem` Objekt zurückgibt. Wenn Sie Funktionen in Ihrem Element ändern müssen, können Sie `CDocObjectServerItem`eine neue Instanz Ihrer eigenen -abgeleiteten Klasse erstellen.

Weitere Informationen zu DocObjects finden Sie unter [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md) und [COleCmdUI](../../mfc/reference/colecmdui-class.md) in der *MFC-Referenz*.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleServerItem](../../mfc/reference/coleserveritem-class.md)

`CDocObjectServerItem`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxdocob.h

## <a name="cdocobjectserveritemcdocobjectserveritem"></a><a name="cdocobjectserveritem"></a>CDocObjectServerItem::CDocObjectServerItem

Erstellt ein `CDocObjectServerItem`-Objekt.

```
CDocObjectServerItem(COleServerDoc* pServerDoc, BOOL bAutoDelete);
```

### <a name="parameters"></a>Parameter

*pServerDoc*<br/>
Ein Zeiger auf das Dokument, das das neue DocObject-Element enthält.

*bAutoDelete*<br/>
Gibt an, ob das Objekt gelöscht werden kann, wenn ein Link zu ihm freigegeben wird. Legen Sie das Argument `CDocObjectServerItem` auf FALSE fest, wenn das Objekt ein integraler Bestandteil der Dokumentdaten ist. Legen Sie es auf TRUE fest, wenn es sich bei dem Objekt um eine sekundäre Struktur handelt, die zum Identifizieren eines Bereichs in den Dokumentdaten verwendet wird, der vom Framework gelöscht werden kann.

## <a name="cdocobjectserveritemgetdocument"></a><a name="getdocument"></a>CDocObjectServerItem::GetDocument

Ruft einen Zeiger auf das Dokument ab, das das Element enthält.

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Dokument, das das Element enthält; NULL, wenn das Element nicht Teil eines Dokuments ist.

### <a name="remarks"></a>Bemerkungen

Dadurch ist der Zugriff auf das Serverdokument möglich, das Sie als Argument an den [CDocObjectServerItem-Konstruktor](#cdocobjectserveritem) übergeben haben.

## <a name="cdocobjectserveritemondoverb"></a><a name="ondoverb"></a>CdocObjectServerItem::OnDoverb

Wird vom Framework aufgerufen, um das angegebene Verb auszuführen.

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>Parameter

*iVerb*<br/>
Gibt das auszuführende Verb an. Mögliche Werte finden Sie unter [IOleObject::DoVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) im Windows SDK.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung ruft die [OnShow-Memberfunktion](#onshow) auf, wenn es sich bei dem Element um ein DocObject handelt und die OLEIVERB_INPLACEACTIVATE oder OLEIVERB_SHOW angegeben ist. Wenn es sich bei dem Element nicht um ein DocObject handelt oder ein anderes Verb angegeben ist, ruft die Standardimplementierung [COleServerItem::OnDoVerb](../../mfc/reference/coleserveritem-class.md#ondoverb)auf.

## <a name="cdocobjectserveritemonhide"></a><a name="onhide"></a>CDocObjectServerItem::OnHide

Wird vom Framework aufgerufen, um das Element auszublenden.

```
virtual void OnHide();
```

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung löst eine Ausnahme aus, wenn es sich bei dem Element um ein DocObject handelt. Sie können ein aktives DocObject-Element nicht ausblenden, da es die gesamte Ansicht übernimmt. Sie müssen das DocObject-Element deaktivieren, damit es ausgeblendet wird. Wenn es sich bei dem Element nicht um ein DocObject handelt, ruft die Standardimplementierung [COleServerItem::OnHide](../../mfc/reference/coleserveritem-class.md#onhide)auf.

## <a name="cdocobjectserveritemonshow"></a><a name="onshow"></a>CDocObjectServerItem::OnShow

Wird vom Framework aufgerufen, um die Serveranwendung anzuweisen, das DocObject-Element an Ort und Stelle aktiv zu machen.

```
virtual void OnShow();
```

### <a name="remarks"></a>Bemerkungen

Wenn es sich bei dem Element nicht um ein DocObject handelt, ruft die Standardimplementierung [COleServerItem::OnShow](../../mfc/reference/coleserveritem-class.md#onopen)auf. Überschreiben Sie diese Funktion, wenn Sie beim Öffnen eines DocObject-Elements eine spezielle Verarbeitung durchführen möchten.

## <a name="see-also"></a>Siehe auch

[COleServerItem-Klasse](../../mfc/reference/coleserveritem-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServer-Klasse](../../mfc/reference/cdocobjectserver-class.md)<br/>
[COleDocObjectItem-Klasse](../../mfc/reference/coledocobjectitem-class.md)

---
title: CRichEditCntrItem-Klasse
ms.date: 11/04/2016
f1_keywords:
- CRichEditCntrItem
- AFXRICH/CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::CRichEditCntrItem
- AFXRICH/CRichEditCntrItem::SyncToRichEditObject
helpviewer_keywords:
- CRichEditCntrItem [MFC], CRichEditCntrItem
- CRichEditCntrItem [MFC], SyncToRichEditObject
ms.assetid: 6c0b4efe-0fb8-4621-b5e1-fdcb8ec48c3b
ms.openlocfilehash: b8158105d09d5cfc7c25512567a98121b194a82a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368290"
---
# <a name="cricheditcntritem-class"></a>CRichEditCntrItem-Klasse

Mit [CRichEditView](../../mfc/reference/cricheditview-class.md) und [CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)bietet die Funktionalität des Rich-Edit-Steuerelements im Kontext der Dokumentansichtsarchitektur von MFC.

## <a name="syntax"></a>Syntax

```
class CRichEditCntrItem : public COleClientItem
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRichEditCntrItem::CRichEditCntrItem](#cricheditcntritem)|Erstellt ein `CRichEditCntrItem`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRichEditCntrItem::SyncToRichEditObject](#synctoricheditobject)|Aktiviert das Element als einen anderen Typ.|

## <a name="remarks"></a>Bemerkungen

Ein "Rich-Edit-Steuerelement" ist ein Fenster, in dem der Benutzer Text eingeben und bearbeiten kann. Dem Text können Zeichen- und Absatzformatierungen zugewiesen werden und eingebettete OLE-Objekte enthalten sein. Rich-Edit-Steuerelemente bieten eine Programmierschnittstelle zum Formatieren von Text. Eine Anwendung muss jedoch alle Benutzeroberflächenkomponenten implementieren, die erforderlich sind, um formatierungsvorgänge für den Benutzer verfügbar zu machen.

`CRichEditView`behält das Text- und Formatierungsmerkmal des Textes bei. `CRichEditDoc`verwaltet die Liste der OLE-Clientelemente, die sich in der Ansicht befinden. `CRichEditCntrItem`bietet containerseitigen Zugriff auf das OLE-Clientelement.

Dieses Windows Common-Steuerelement (und damit das [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) und verwandte Klassen) ist nur für Programme verfügbar, die unter Windows 95/98 und Windows NT-Versionen 3.51 und höher ausgeführt werden.

Ein Beispiel für die Verwendung von Rich-Edit-Containerelementen in einer MFC-Anwendung finden Sie in der [WORDPAD-Beispielanwendung.](../../overview/visual-cpp-samples.md)

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`CRichEditCntrItem`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxrich.h

## <a name="cricheditcntritemcricheditcntritem"></a><a name="cricheditcntritem"></a>CRichEditCntrItem::CRichEditCntrItem

Rufen Sie diese `CRichEditCntrItem` Funktion auf, um ein Objekt zu erstellen und es dem Containerdokument hinzuzufügen.

```
CRichEditCntrItem(
    REOBJECT* preo = NULL,
    CRichEditDoc* pContainer = NULL);
```

### <a name="parameters"></a>Parameter

*preo*<br/>
Zeiger auf eine [REOBJECT-Struktur,](/windows/win32/api/richole/ns-richole-reobject) die ein OLE-Element beschreibt. Das `CRichEditCntrItem` neue Objekt wird um dieses OLE-Element herum erstellt. Wenn *preo* NULL ist, ist das Clientelement leer.

*pContainer*<br/>
Zeigen Sie mit dem Zeiger auf das Containerdokument, das dieses Element enthält. Wenn *pContainer* NULL ist, müssen Sie [COleDocument::AddItem](../../mfc/reference/coledocument-class.md#additem) explizit aufrufen, um dieses Clientelement zu einem Dokument hinzuzufügen.

### <a name="remarks"></a>Bemerkungen

Diese Funktion führt keine OLE-Initialisierung aus.

Weitere Informationen finden Sie in der [REOBJECT-Struktur](/windows/win32/api/richole/ns-richole-reobject) im Windows SDK.

## <a name="cricheditcntritemsynctoricheditobject"></a><a name="synctoricheditobject"></a>CRichEditCntrItem::SyncToRichEditObject

Rufen Sie diese Funktion auf, um den `CRichEditCntrltem` Geräteaspekt [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), davon mit dem von *reo*angegebenen zu synchronisieren.

```
void SyncToRichEditObject(REOBJECT& reo);
```

### <a name="parameters"></a>Parameter

*Reo*<br/>
Verweis auf eine [REOBJECT-Struktur,](/windows/win32/api/richole/ns-richole-reobject) die ein OLE-Element beschreibt.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) im Windows SDK.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem-Klasse](../../mfc/reference/coleclientitem-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc-Klasse](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditView-Klasse](../../mfc/reference/cricheditview-class.md)

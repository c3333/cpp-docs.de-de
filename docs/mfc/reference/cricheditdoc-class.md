---
title: CRichEditDoc-Klasse
ms.date: 11/04/2016
f1_keywords:
- CRichEditDoc
- AFXRICH/CRichEditDoc
- AFXRICH/CRichEditDoc::CreateClientItem
- AFXRICH/CRichEditDoc::GetStreamFormat
- AFXRICH/CRichEditDoc::GetView
- AFXRICH/CRichEditDoc::m_bRTF
helpviewer_keywords:
- CRichEditDoc [MFC], CreateClientItem
- CRichEditDoc [MFC], GetStreamFormat
- CRichEditDoc [MFC], GetView
- CRichEditDoc [MFC], m_bRTF
ms.assetid: c936ec18-d516-49d4-b7fb-c9aa0229eddc
ms.openlocfilehash: 587cf65543e24e586fb8b2336481d6e841473134
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368265"
---
# <a name="cricheditdoc-class"></a>CRichEditDoc-Klasse

Mit [CRichEditView](../../mfc/reference/cricheditview-class.md) und [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)bietet die Funktionalität des Rich Edit-Steuerelements im Kontext der MFC-Dokumentansichtsarchitektur.

## <a name="syntax"></a>Syntax

```
class CRichEditDoc : public COleServerDoc
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRichEditDoc::CreateClientItem](#createclientitem)|Wird aufgerufen, um die Bereinigung des Dokuments durchzuführen.|
|[CRichEditDoc::GetStreamFormat](#getstreamformat)|Gibt an, ob Streameingabe und -ausgabe Formatierungsinformationen enthalten sollen.|
|[CRichEditDoc::GetView](#getview)|Ruft das asssoziierte [CRichEditView-Objekt](../../mfc/reference/cricheditview-class.md) ab.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRichEditDoc::m_bRTF](#m_brtf)|Gibt an, ob Stream-E/A-Formatierungen enthalten sollen.|

## <a name="remarks"></a>Bemerkungen

Ein "Rich-Edit-Steuerelement" ist ein Fenster, in dem der Benutzer Text eingeben und bearbeiten kann. Dem Text können Zeichen- und Absatzformatierungen zugewiesen werden und eingebettete OLE-Objekte enthalten sein. Rich-Edit-Steuerelemente bieten eine Programmierschnittstelle zum Formatieren von Text. Eine Anwendung muss jedoch alle Benutzeroberflächenkomponenten implementieren, die erforderlich sind, um formatierungsvorgänge für den Benutzer verfügbar zu machen.

`CRichEditView`behält das Text- und Formatierungsmerkmal des Textes bei. `CRichEditDoc`verwaltet die Liste der Clientelemente, die sich in der Ansicht befinden. `CRichEditCntrItem`bietet containerseitigen Zugriff auf die OLE-Clientelemente.

Dieses Windows Common-Steuerelement (und damit das [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) und verwandte Klassen) ist nur für Programme verfügbar, die unter Windows 95/98 und Windows NT-Versionen 3.51 und höher ausgeführt werden.

Ein Beispiel für die Verwendung eines umfangreichen Bearbeitungsdokuments [WORDPAD](../../overview/visual-cpp-samples.md) in einer MFC-Anwendung finden Sie in der WORDPAD-Beispielanwendung.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

[COleServerDoc](../../mfc/reference/coleserverdoc-class.md)

`CRichEditDoc`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxrich.h

## <a name="cricheditdoccreateclientitem"></a><a name="createclientitem"></a>CRichEditDoc::CreateClientItem

Rufen Sie diese `CRichEditCntrItem` Funktion auf, um ein Objekt zu erstellen und es diesem Dokument hinzuzufügen.

```
virtual CRichEditCntrItem* CreateClientItem(REOBJECT* preo = NULL) const = 0;
```

### <a name="parameters"></a>Parameter

*preo*<br/>
Zeiger auf eine [REOBJECT-Struktur,](/windows/win32/api/richole/ns-richole-reobject) die ein OLE-Element beschreibt. Das `CRichEditCntrItem` neue Objekt wird um dieses OLE-Element herum erstellt. Wenn *preo* NULL ist, ist das neue Clientelement leer.

### <a name="return-value"></a>Rückgabewert

Zeiger auf ein neues [CRichEditCntrItem-Objekt,](../../mfc/reference/cricheditcntritem-class.md) das diesem Dokument hinzugefügt wurde.

### <a name="remarks"></a>Bemerkungen

Diese Funktion führt keine OLE-Initialisierung aus.

Weitere Informationen finden Sie in der [REOBJECT-Struktur](/windows/win32/api/richole/ns-richole-reobject) im Windows SDK.

## <a name="cricheditdocgetstreamformat"></a><a name="getstreamformat"></a>CRichEditDoc::GetStreamFormat

Rufen Sie diese Funktion auf, um das Textformat für das Streaming des Inhalts der Rich-Bearbeitung zu bestimmen.

```
int GetStreamFormat() const;
```

### <a name="return-value"></a>Rückgabewert

Eines der folgenden Flags:

- SF_TEXT Gibt an, dass das Rich-Edit-Steuerelement keine Formatierungsinformationen verwaltet.

- SF_RTF Gibt an, dass das Rich-Edit-Steuerelement Formatierungsinformationen verwaltet.

### <a name="remarks"></a>Bemerkungen

Der Rückgabewert basiert auf dem [m_bRTF](#m_brtf) Datenmember. Diese Funktion gibt `m_bRTF` SF_RTF zurück, wenn TRUE ist. andernfalls SF_TEXT.

## <a name="cricheditdocgetview"></a><a name="getview"></a>CRichEditDoc::GetView

Rufen Sie diese Funktion auf, um auf `CRichEditDoc` das [CRichEditView-Objekt](../../mfc/reference/cricheditview-class.md) zuzugreifen, das diesem Objekt zugeordnet ist.

```
virtual CRichEditView* GetView() const;
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf `CRichEditView` das dem Dokument zugeordnete Objekt.

### <a name="remarks"></a>Bemerkungen

Die Text- und Formatierungsinformationen sind im `CRichEditView` Objekt enthalten. Das `CRichEditDoc` Objekt verwaltet die OLE-Elemente für die Serialisierung. Es sollte nur `CRichEditView` eine `CRichEditDoc`für jeden geben.

## <a name="cricheditdocm_brtf"></a><a name="m_brtf"></a>CRichEditDoc::m_bRTF

Wenn TRUE, gibt an, dass [CRichEditCtrl::StreamIn](../../mfc/reference/cricheditctrl-class.md#streamin) und [CRichEditCtrl::StreamOut](../../mfc/reference/cricheditctrl-class.md#streamout) Absatz- und Zeichenformatierungsmerkmale speichern sollen.

```
BOOL m_bRTF;
```

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel WORDPAD](../../overview/visual-cpp-samples.md)<br/>
[COleServerDoc-Klasse](../../mfc/reference/coleserverdoc-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CRichEditView-Klasse](../../mfc/reference/cricheditview-class.md)<br/>
[CRichEditCntrItem-Klasse](../../mfc/reference/cricheditcntritem-class.md)<br/>
[COleDocument-Klasse](../../mfc/reference/coledocument-class.md)<br/>
[CRichEditCtrl-Klasse](../../mfc/reference/cricheditctrl-class.md)

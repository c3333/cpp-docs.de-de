---
title: COleResizeBar-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleResizeBar
- AFXOLE/COleResizeBar
- AFXOLE/COleResizeBar::COleResizeBar
- AFXOLE/COleResizeBar::Create
helpviewer_keywords:
- COleResizeBar [MFC], COleResizeBar
- COleResizeBar [MFC], Create
ms.assetid: 56a708d9-28c5-4eb0-9404-77b688d91c63
ms.openlocfilehash: beb0c37b6ac23310b7d5c8506fbdaf677dd74d8d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376153"
---
# <a name="coleresizebar-class"></a>COleResizeBar-Klasse

Ein Steuerleistentyp, die Größenanpassung von direkten OLE-Elementen unterstützt.

## <a name="syntax"></a>Syntax

```
class COleResizeBar : public CControlBar
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleResizeBar::COleResizeBar](#coleresizebar)|Erstellt ein `COleResizeBar`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleResizeBar::Erstellen](#create)|Erstellt und initialisiert ein untergeordnetes Windows-Fenster und ordnet es dem `COleResizeBar` Objekt zu.|

## <a name="remarks"></a>Bemerkungen

`COleResizeBar`Objekte werden als [CRectTracker](../../mfc/reference/crecttracker-class.md) mit einem geschlüpften Rahmen und äußeren Größenumziehblättern angezeigt.

`COleResizeBar`Objekte sind in der Regel eingebettete Member von Frame-Window-Objekten, die von der [COleIPFrameWnd-Klasse](../../mfc/reference/coleipframewnd-class.md) abgeleitet sind.

Weitere Informationen finden Sie im Artikel [Aktivierung](../../mfc/activation-cpp.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CControlBar](../../mfc/reference/ccontrolbar-class.md)

`COleResizeBar`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxole.h

## <a name="coleresizebarcoleresizebar"></a><a name="coleresizebar"></a>COleResizeBar::COleResizeBar

Erstellt ein `COleResizeBar`-Objekt.

```
COleResizeBar();
```

### <a name="remarks"></a>Bemerkungen

Rufen `Create` Sie auf, um das Größenänderungsbalkenobjekt zu erstellen.

## <a name="coleresizebarcreate"></a><a name="create"></a>COleResizeBar::Erstellen

Erstellt ein untergeordnetes Fenster `COleResizeBar` und ordnet es dem Objekt zu.

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_RESIZE_BAR);
```

### <a name="parameters"></a>Parameter

*pParentWnd*<br/>
Zeigen Sie mit dem Zeiger auf das übergeordnete Fenster der Größenleiste.

*dwStyle*<br/>
Gibt die [Fensterstilattribute](../../mfc/reference/styles-used-by-mfc.md#window-styles) an.

*nID*<br/>
Die untergeordnete Fenster-ID der Größenleiste.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Größenblock erstellt wurde; andernfalls 0.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel SUPERPAD](../../overview/visual-cpp-samples.md)<br/>
[CControlBar-Klasse](../../mfc/reference/ccontrolbar-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleServerDoc-Klasse](../../mfc/reference/coleserverdoc-class.md)

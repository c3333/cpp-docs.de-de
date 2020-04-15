---
title: CStatic-Klasse
ms.date: 11/04/2016
f1_keywords:
- CStatic
- AFXWIN/CStatic
- AFXWIN/CStatic::CStatic
- AFXWIN/CStatic::Create
- AFXWIN/CStatic::DrawItem
- AFXWIN/CStatic::GetBitmap
- AFXWIN/CStatic::GetCursor
- AFXWIN/CStatic::GetEnhMetaFile
- AFXWIN/CStatic::GetIcon
- AFXWIN/CStatic::SetBitmap
- AFXWIN/CStatic::SetCursor
- AFXWIN/CStatic::SetEnhMetaFile
- AFXWIN/CStatic::SetIcon
helpviewer_keywords:
- CStatic [MFC], CStatic
- CStatic [MFC], Create
- CStatic [MFC], DrawItem
- CStatic [MFC], GetBitmap
- CStatic [MFC], GetCursor
- CStatic [MFC], GetEnhMetaFile
- CStatic [MFC], GetIcon
- CStatic [MFC], SetBitmap
- CStatic [MFC], SetCursor
- CStatic [MFC], SetEnhMetaFile
- CStatic [MFC], SetIcon
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
ms.openlocfilehash: e5c3705c0aa2fd90e73cb54ba5a97c252ed2cf83
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371644"
---
# <a name="cstatic-class"></a>CStatic-Klasse

Stellt die Funktionalität eines statischen Windows-Steuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CStatic : public CWnd
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStatic::CStatisch](#cstatic)|Erstellt ein `CStatic`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CStatic::Erstellen](#create)|Erstellt das statische Windows-Steuerelement und `CStatic` fügt es an das Objekt an.|
|[CStatic::DrawItem](#drawitem)|Überschreiben, um ein vom Besitzer gezeichnetes statisches Steuerelement zu zeichnen.|
|[CStatic::GetBitmap](#getbitmap)|Ruft das Handle der Bitmap ab, die zuvor mit [SetBitmap](#setbitmap)festgelegt wurde.|
|[CStatic::GetCursor](#getcursor)|Ruft das Handle des Cursorbilds ab, das zuvor mit [SetCursor](#setcursor)festgelegt wurde.|
|[CStatic::GetEnhMetaFile](#getenhmetafile)|Ruft das Handle der erweiterten Metadatei ab, die zuvor mit [SetEnhMetaFile](#setenhmetafile)festgelegt wurde.|
|[CStatic::GetIcon](#geticon)|Ruft das Handle des zuvor mit [SetIcon](#seticon)festgelegten Symbols ab.|
|[CStatic::SetBitmap](#setbitmap)|Gibt eine Bitmap an, die im statischen Steuerelement angezeigt werden soll.|
|[CStatic::SetCursor](#setcursor)|Gibt ein Cursorbild an, das im statischen Steuerelement angezeigt werden soll.|
|[CStatic::SetEnhMetaFile](#setenhmetafile)|Gibt eine erweiterte Metadatei an, die im statischen Steuerelement angezeigt werden soll.|
|[CStatic::SetIcon](#seticon)|Gibt ein Symbol an, das im statischen Steuerelement angezeigt werden soll.|

## <a name="remarks"></a>Bemerkungen

Ein statisches Steuerelement zeigt eine Textzeichenfolge, ein Feld, ein Rechteck, ein Symbol, einen Cursor, eine Bitmap oder eine erweiterte Metadatei an. Es kann verwendet werden, um andere Steuerelemente zu beschriften, zu verschachteln oder zu trennen. Ein statisches Steuerelement benötigt normalerweise keine Eingabe und liefert keine Ausgabe. Es kann jedoch sein übergeordnetes Element über Mausklicks benachrichtigen, wenn es mit SS_NOTIFY Stil erstellt wurde.

Erstellen Sie ein statisches Steuerelement in zwei Schritten. Rufen Sie zunächst den Konstruktor auf, um das `CStatic` Objekt zu konstruieren, und rufen Sie dann die [Memberfunktion Erstellen](#create) auf, um das statische Steuerelement zu erstellen und es an das `CStatic` Objekt anzufügen.

Wenn Sie `CStatic` ein Objekt in einem Dialogfeld (über eine Dialogfeldressource) erstellen, wird das `CStatic` Objekt automatisch zerstört, wenn der Benutzer das Dialogfeld schließt.

Wenn Sie `CStatic` ein Objekt in einem Fenster erstellen, müssen Sie es möglicherweise auch zerstören. Ein `CStatic` Objekt, das auf dem Stapel in einem Fenster erstellt wird, wird automatisch zerstört. Wenn Sie `CStatic` das Objekt auf dem Heap mithilfe der **neuen** Funktion erstellen, müssen Sie **das Objekt** löschen aufrufen, um es zu zerstören, wenn Sie damit fertig sind.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cstaticcreate"></a><a name="create"></a>CStatic::Erstellen

Erstellt das statische Windows-Steuerelement und `CStatic` fügt es an das Objekt an.

```
virtual BOOL Create(
    LPCTSTR lpszText,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID = 0xffff);
```

### <a name="parameters"></a>Parameter

*lpszText*<br/>
Gibt den Text an, der im Steuerelement platziert werden soll. Wenn NULL, ist kein Text sichtbar.

*dwStyle*<br/>
Gibt den Fensterstil des statischen Steuerelements an. Wenden Sie eine beliebige Kombination [statischer Steuerelementstile](../../mfc/reference/styles-used-by-mfc.md#static-styles) auf das Steuerelement an.

*Rect*<br/>
Gibt die Position und Größe des statischen Steuerelements an. Es kann entweder `RECT` eine `CRect` Struktur oder ein Objekt sein.

*pParentWnd*<br/>
Gibt das `CStatic` übergeordnete Fenster `CDialog` an, in der Regel ein Objekt. Es darf nicht NULL sein.

*nID*<br/>
Gibt die Steuerelement-ID des statischen Steuerelements an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Erstellen `CStatic` Sie ein Objekt in zwei Schritten. Rufen Sie zunächst `CStatic`den Konstruktor `Create`auf, und rufen Sie dann auf, das das statische Windows-Steuerelement erstellt und an das `CStatic` Objekt anfügt.

Wenden Sie die folgenden [Fensterstile](../../mfc/reference/styles-used-by-mfc.md#window-styles) auf ein statisches Steuerelement an:

- WS_CHILD Immer

- WS_VISIBLE In der Regel

- WS_DISABLED Selten

Wenn Sie eine Bitmap, einen Cursor, ein Symbol oder eine Metadatei im statischen Steuerelement anzeigen möchten, müssen Sie einen der folgenden [statischen Stile](../../mfc/reference/styles-used-by-mfc.md#static-styles)anwenden:

- SS_BITMAP Verwenden Sie diesen Stil für Bitmaps.

- SS_ICON Verwenden Sie diesen Stil für Cursor und Symbole.

- SS_ENHMETAFILE Verwenden Sie diesen Stil für erweiterte Metadateien.

Bei Cursorn, Bitmaps oder Symbolen können Sie auch den folgenden Stil verwenden:

- SS_CENTERIMAGE Verwenden Sie diese Verwendung, um das Bild im statischen Steuerelement zu zentrieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

## <a name="cstaticcstatic"></a><a name="cstatic"></a>CStatic::CStatisch

Erstellt ein `CStatic`-Objekt.

```
CStatic();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

## <a name="cstaticdrawitem"></a><a name="drawitem"></a>CStatic::DrawItem

Wird vom Framework aufgerufen, um ein vom Besitzer gezeichnetes statisches Steuerelement zu zeichnen.

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>Parameter

*lpDrawItemStruct*<br/>
Ein Zeiger auf eine [DRAWITEMSTRUCT-Struktur.](/windows/win32/api/winuser/ns-winuser-drawitemstruct) Die Struktur enthält Informationen über das zu zeichnende Element und den erforderlichen Zeichnungstyp.

### <a name="remarks"></a>Bemerkungen

Überschreiben Sie diese Funktion, um `CStatic` die Zeichnung für ein vom Besitzer gezeichnetes Objekt zu implementieren (das Steuerelement verfügt über den Stil SS_OWNERDRAW).

## <a name="cstaticgetbitmap"></a><a name="getbitmap"></a>CStatic::GetBitmap

Ruft das Handle der Bitmap ab, die zuvor mit `CStatic` [SetBitmap](#setbitmap)festgelegt wurde, das mit zugeordnet ist.

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für die aktuelle Bitmap oder NULL, wenn keine Bitmap festgelegt wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

## <a name="cstaticgetcursor"></a><a name="getcursor"></a>CStatic::GetCursor

Ruft das Handle des Cursors ab, der zuvor `CStatic`mit [SetCursor](#setcursor)festgelegt wurde, der mit zugeordnet ist.

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für den aktuellen Cursor oder NULL, wenn kein Cursor festgelegt wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

## <a name="cstaticgetenhmetafile"></a><a name="getenhmetafile"></a>CStatic::GetEnhMetaFile

Ruft das Handle der erweiterten Metadatei ab, die zuvor mit [SetEnhMetafile](#setenhmetafile)festgelegt wurde, das `CStatic`mit zugeordnet ist.

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für die aktuelle erweiterte Metadatei oder NULL, wenn keine erweiterte Metadatei festgelegt wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

## <a name="cstaticgeticon"></a><a name="geticon"></a>CStatic::GetIcon

Ruft das Handle des Symbols ab, das zuvor `CStatic`mit [SetIcon](#seticon)festgelegt wurde und mit zugeordnet ist.

```
HICON GetIcon() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für das aktuelle Symbol oder NULL, wenn kein Symbol festgelegt wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="cstaticsetbitmap"></a><a name="setbitmap"></a>CStatic::SetBitmap

Ordnet dem statischen Steuerelement eine neue Bitmap zu.

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parameter

*hBitmap*<br/>
Handle der Bitmap, die im statischen Steuerelement gezeichnet werden soll.

### <a name="return-value"></a>Rückgabewert

Das Handle der Bitmap, das zuvor dem statischen Steuerelement zugeordnet war, oder NULL, wenn dem statischen Steuerelement keine Bitmap zugeordnet war.

### <a name="remarks"></a>Bemerkungen

Die Bitmap wird automatisch im statischen Steuerelement gezeichnet. Standardmäßig wird sie in der oberen linken Ecke gezeichnet, und die Größe des statischen Steuerelements wird auf die Größe der Bitmap geändert.

Sie können verschiedene Fenster- und statische Steuerelementstile verwenden, einschließlich der folgenden:

- SS_BITMAP Verwenden Sie diesen Stil immer für Bitmaps.

- SS_CENTERIMAGE Verwenden Sie diese Verwendung, um das Bild im statischen Steuerelement zu zentrieren. Wenn das Bild größer als das statische Steuerelement ist, wird es abgeschnitten. Wenn es kleiner als das statische Steuerelement ist, wird der leere Raum um das Bild durch die Farbe des Pixels in der oberen linken Ecke der Bitmap gefüllt.

- MFC stellt `CBitmap`die Klasse bereit, die Sie verwenden können, wenn Sie mehr mit `LoadBitmap`einem Bitmap-Bild zu tun haben, als nur die Win32-Funktion aufzurufen. `CBitmap`, das eine Art GDI-Objekt enthält, `CStatic`wird häufig `CWnd` in Zusammenarbeit mit verwendet, einer Klasse, die zum Anzeigen eines Grafikobjekts als statisches Steuerelement verwendet wird.

`CImage`ist eine ATL/MFC-Klasse, mit der Sie einfacher mit geräteunabhängigen Bitmaps (DIB) arbeiten können. Weitere Informationen finden Sie unter [CImage Class](../../atl-mfc-shared/reference/cimage-class.md).

- Typische Verwendung besteht `CStatic::SetBitmap` darin, ein GDI-Objekt zu geben, `CBitmap` `CImage` das vom HBITMAP-Operator eines oder-Objekts zurückgegeben wird. Der Code, der dies tut, ähnelt der folgenden Zeile.

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```

Im folgenden Beispiel `CStatic` werden zwei Objekte auf dem Heap erstellt. Anschließend wird eine mit einer `CBitmap::LoadOEMBitmap` Systembitmap mit und `CImage::Load`die andere aus einer Datei mit geladen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

## <a name="cstaticsetcursor"></a><a name="setcursor"></a>CStatic::SetCursor

Ordnet dem statischen Steuerelement ein neues Cursorbild zu.

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>Parameter

*hCursor*<br/>
Handle des Cursors, der im statischen Steuerelement gezeichnet werden soll.

### <a name="return-value"></a>Rückgabewert

Das Handle des Cursors, der zuvor dem statischen Steuerelement zugeordnet war, oder NULL, wenn dem statischen Steuerelement kein Cursor zugeordnet war.

### <a name="remarks"></a>Bemerkungen

Der Cursor wird automatisch im statischen Steuerelement gezeichnet. Standardmäßig wird es in der oberen linken Ecke gezeichnet, und die Größe des statischen Steuerelements wird auf die Größe des Cursors geändert.

Sie können verschiedene Fenster- und statische Steuerelementstile verwenden, einschließlich der folgenden:

- SS_ICON Verwenden Sie diesen Stil immer für Cursor und Symbole.

- SS_CENTERIMAGE Verwenden Sie diese Verwendung, um im statischen Steuerelement zu zentrieren. Wenn das Bild größer als das statische Steuerelement ist, wird es abgeschnitten. Wenn es kleiner als das statische Steuerelement ist, wird der leere Raum um das Bild mit der Hintergrundfarbe des statischen Steuerelements gefüllt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

## <a name="cstaticsetenhmetafile"></a><a name="setenhmetafile"></a>CStatic::SetEnhMetaFile

Ordnet dem statischen Steuerelement ein neues erweitertes Metadateibild zu.

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>Parameter

*hMetaFile*<br/>
Handle der erweiterten Metadatei, die im statischen Steuerelement gezeichnet werden soll.

### <a name="return-value"></a>Rückgabewert

Das Handle der erweiterten Metadatei, die zuvor dem statischen Steuerelement zugeordnet war, oder NULL, wenn dem statischen Steuerelement keine erweiterte Metadatei zugeordnet war.

### <a name="remarks"></a>Bemerkungen

Die erweiterte Metadatei wird automatisch im statischen Steuerelement gezeichnet. Die erweiterte Metadatei wird an die Größe des statischen Steuerelements geskaliert.

Sie können verschiedene Fenster- und statische Steuerelementstile verwenden, einschließlich der folgenden:

- SS_ENHMETAFILE Verwenden Sie diesen Stil immer für erweiterte Metadateien.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

## <a name="cstaticseticon"></a><a name="seticon"></a>CStatic::SetIcon

Ordnet dem statischen Steuerelement ein neues Symbolbild zu.

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>Parameter

*hIcon*<br/>
Handle des Symbols, das im statischen Steuerelement gezeichnet werden soll.

### <a name="return-value"></a>Rückgabewert

Das Handle des Symbols, das zuvor dem statischen Steuerelement zugeordnet war, oder NULL, wenn dem statischen Steuerelement kein Symbol zugeordnet war.

### <a name="remarks"></a>Bemerkungen

Das Symbol wird automatisch im statischen Steuerelement gezeichnet. Standardmäßig wird es in der oberen linken Ecke gezeichnet und die Größe des statischen Steuerelements auf die Größe des Symbols geändert.

Sie können verschiedene Fenster- und statische Steuerelementstile verwenden, einschließlich der folgenden:

- SS_ICON Verwenden Sie diesen Stil immer für Cursor und Symbole.

- SS_CENTERIMAGE Verwenden Sie diese Verwendung, um im statischen Steuerelement zu zentrieren. Wenn das Bild größer als das statische Steuerelement ist, wird es abgeschnitten. Wenn es kleiner als das statische Steuerelement ist, wird der leere Raum um das Bild mit der Hintergrundfarbe des statischen Steuerelements gefüllt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="see-also"></a>Siehe auch

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[CButton-Klasse](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox-Klasse](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox-Klasse](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar-Klasse](../../mfc/reference/cscrollbar-class.md)<br/>
[CDialog-Klasse](../../mfc/reference/cdialog-class.md)

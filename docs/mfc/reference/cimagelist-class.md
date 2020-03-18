---
title: CImageList-Klasse
ms.date: 11/04/2016
f1_keywords:
- CImageList
- AFXCMN/CImageList
- AFXCMN/CImageList::CImageList
- AFXCMN/CImageList::Add
- AFXCMN/CImageList::Attach
- AFXCMN/CImageList::BeginDrag
- AFXCMN/CImageList::Copy
- AFXCMN/CImageList::Create
- AFXCMN/CImageList::DeleteImageList
- AFXCMN/CImageList::DeleteTempMap
- AFXCMN/CImageList::Detach
- AFXCMN/CImageList::DragEnter
- AFXCMN/CImageList::DragLeave
- AFXCMN/CImageList::DragMove
- AFXCMN/CImageList::DragShowNolock
- AFXCMN/CImageList::Draw
- AFXCMN/CImageList::DrawEx
- AFXCMN/CImageList::DrawIndirect
- AFXCMN/CImageList::EndDrag
- AFXCMN/CImageList::ExtractIcon
- AFXCMN/CImageList::FromHandle
- AFXCMN/CImageList::FromHandlePermanent
- AFXCMN/CImageList::GetBkColor
- AFXCMN/CImageList::GetDragImage
- AFXCMN/CImageList::GetImageCount
- AFXCMN/CImageList::GetImageInfo
- AFXCMN/CImageList::GetSafeHandle
- AFXCMN/CImageList::Read
- AFXCMN/CImageList::Remove
- AFXCMN/CImageList::Replace
- AFXCMN/CImageList::SetBkColor
- AFXCMN/CImageList::SetDragCursorImage
- AFXCMN/CImageList::SetImageCount
- AFXCMN/CImageList::SetOverlayImage
- AFXCMN/CImageList::Write
- AFXCMN/CImageList::m_hImageList
helpviewer_keywords:
- CImageList [MFC], CImageList
- CImageList [MFC], Add
- CImageList [MFC], Attach
- CImageList [MFC], BeginDrag
- CImageList [MFC], Copy
- CImageList [MFC], Create
- CImageList [MFC], DeleteImageList
- CImageList [MFC], DeleteTempMap
- CImageList [MFC], Detach
- CImageList [MFC], DragEnter
- CImageList [MFC], DragLeave
- CImageList [MFC], DragMove
- CImageList [MFC], DragShowNolock
- CImageList [MFC], Draw
- CImageList [MFC], DrawEx
- CImageList [MFC], DrawIndirect
- CImageList [MFC], EndDrag
- CImageList [MFC], ExtractIcon
- CImageList [MFC], FromHandle
- CImageList [MFC], FromHandlePermanent
- CImageList [MFC], GetBkColor
- CImageList [MFC], GetDragImage
- CImageList [MFC], GetImageCount
- CImageList [MFC], GetImageInfo
- CImageList [MFC], GetSafeHandle
- CImageList [MFC], Read
- CImageList [MFC], Remove
- CImageList [MFC], Replace
- CImageList [MFC], SetBkColor
- CImageList [MFC], SetDragCursorImage
- CImageList [MFC], SetImageCount
- CImageList [MFC], SetOverlayImage
- CImageList [MFC], Write
- CImageList [MFC], m_hImageList
ms.assetid: b6d1a704-1c82-4548-8a8f-77972adc98a5
ms.openlocfilehash: 1555209ce0f1c2caacbfb4b01107775db948d230
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425856"
---
# <a name="cimagelist-class"></a>CImageList-Klasse

Stellt die Funktionalität des allgemeinen Windows-Bildlisten-Steuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CImageList : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CImageList:: CImageList](#cimagelist)|Erstellt ein `CImageList`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CImageList:: Add](#add)|Fügt einer Bildliste ein Bild oder Bilder hinzu.|
|[CImageList:: Attach](#attach)|Fügt eine Bildliste an ein `CImageList` Objekt an.|
|[CImageList:: BeginDrag](#begindrag)|Startet das Ziehen eines Bilds.|
|[CImageList:: Copy](#copy)|Kopiert ein Bild in einem `CImageList`-Objekt.|
|[CImageList:: Create](#create)|Initialisiert eine Bildliste und fügt Sie an ein `CImageList` Objekt an.|
|[CImageList::D eleteimagelist](#deleteimagelist)|Löscht eine Bildliste.|
|[CImageList::D eletetempmap](#deletetempmap)|Wird vom [CWinApp](../../mfc/reference/cwinapp-class.md) -Leerlaufzeit Handler aufgerufen, um alle temporären `CImageList` von `FromHandle`erstellten Objekte zu löschen.|
|[CImageList::D Etach](#detach)|Trennt ein Bildlisten Objekt von einem `CImageList` Objekt und gibt ein Handle für eine Bildliste zurück.|
|[CImageList::D ragenter](#dragenter)|Sperrt Updates während eines Zieh Vorgangs und zeigt das Zieh Bild an einer angegebenen Position an.|
|[CImageList::D ragleave](#dragleave)|Entsperrt das Fenster und blendet das Zieh Bild aus, sodass das Fenster aktualisiert werden kann.|
|[CImageList::D ragmove](#dragmove)|Verschiebt das Bild, das gezogen wird, während eines Drag & Drop-Vorgangs.|
|[CImageList::D ragshownolock](#dragshownolock)|Zeigt das Zieh Bild während eines Zieh Vorgangs an oder blendet es aus, ohne das Fenster zu sperren.|
|[CImageList::D RAW](#draw)|Zeichnet das Bild, das während eines Drag & Drop-Vorgangs gezogen wird.|
|[CImageList::D rawex](#drawex)|Zeichnet ein Bildlisten Element im angegebenen Gerätekontext. Die-Funktion verwendet die angegebene Zeichnungs Art und kombiniert das Bild mit der angegebenen Farbe.|
|[CImageList::D rawindirect](#drawindirect)|Zeichnet ein Bild aus einer Bildliste.|
|[CImageList:: EndDrag](#enddrag)|Beendet einen Zieh Vorgang.|
|[CImageList:: ExtractIcon](#extracticon)|Erstellt ein Symbol auf der Grundlage eines Bilds und einer Maske in einer Bildliste.|
|[CImageList:: FromHandle](#fromhandle)|Gibt einen Zeiger auf ein `CImageList` Objekt zurück, wenn ein Handle für eine Bildliste angegeben ist. Wenn ein `CImageList`-Objekt nicht an das Handle angefügt ist, wird ein temporäres `CImageList`-Objekt erstellt und angefügt.|
|[CImageList:: fromlenker permanent](#fromhandlepermanent)|Gibt einen Zeiger auf ein `CImageList` Objekt zurück, wenn ein Handle für eine Bildliste angegeben ist. Wenn ein `CImageList` Objekt nicht an das Handle angefügt ist, wird NULL zurückgegeben.|
|[CImageList:: GetBkColor](#getbkcolor)|Ruft die aktuelle Hintergrundfarbe für eine Bildliste ab.|
|[CImageList:: GetDragImage](#getdragimage)|Ruft die temporäre Bildliste ab, die für das Ziehen verwendet wird.|
|[CImageList:: GetImageCount](#getimagecount)|Ruft die Anzahl der Bilder in einer Bildliste ab.|
|[CImageList:: getimagan FO](#getimageinfo)|Ruft Informationen zu einem Bild ab.|
|[CImageList:: geout afehandle](#getsafehandle)|Ruft `m_hImageList`ab.|
|[CImageList:: Read](#read)|Liest eine Bildliste aus einem Archiv.|
|[CImageList:: Remove](#remove)|Entfernt ein Bild aus einer Bildliste.|
|[CImageList:: Replace](#replace)|Ersetzt ein Bild in einer Bildliste durch ein neues Bild.|
|[CImageList:: SetBkColor](#setbkcolor)|Legt die Hintergrundfarbe für eine Bildliste fest.|
|[CImageList:: setdragcurrsorimage](#setdragcursorimage)|Erstellt ein neues Zieh Bild.|
|[CImageList:: Abbild magecount](#setimagecount)|Setzt die Anzahl der Bilder in einer Bildliste zurück.|
|[CImageList:: Server-layimage](#setoverlayimage)|Fügt der Liste der Bilder, die als Überlagerungs Masken verwendet werden sollen, den NULL basierten Index eines Bilds hinzu.|
|[CImageList:: Write](#write)|Schreibt eine Bildliste in ein Archiv.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[CImageList:: Operator HIMAGELIST](#operator_himagelist)|Gibt die an den `CImageList`angefügte HIMAGELIST zurück.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|Beschreibung|
|----------|-----------------|
|[CImageList:: m_hImageList](#m_himagelist)|Ein Handle, das die an dieses-Objekt angefügte Bildliste enthält.|

## <a name="remarks"></a>Hinweise

Eine "Bildliste" ist eine Sammlung von Bildern gleicher Größe, auf die jeweils durch den NULL basierten Index verwiesen werden kann. Bildlisten werden verwendet, um große Mengen von Symbolen oder Bitmaps effizient zu verwalten. Alle Bilder in einer Bildliste sind in einer einzelnen, breiten Bitmap im Bildschirmformat enthalten. Eine Bildliste kann auch eine monochrome Bitmap enthalten, die Masken enthält, mit denen Bilder transparent gezeichnet werden (Symbol Stil). Die Microsoft Win32-API (Application Programming Interface) stellt Bildlisten Funktionen bereit, mit denen Sie Bilder zeichnen, Bildlisten erstellen und zerstören, Bilder hinzufügen und entfernen, Bilder ersetzen, Bilder zusammenführen und Bilder ziehen können.

Dieses Steuerelement (und damit auch die `CImageList`-Klasse) ist nur für Programme verfügbar, die unter Windows 95/98 und Windows NT, Version 3,51 und höher, ausgeführt werden.

Weitere Informationen zur Verwendung von `CImageList`finden Sie unter Steuer [Elemente](../../mfc/controls-mfc.md) und [Verwenden von CImageList](../../mfc/using-cimagelist.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxcmn.h

##  <a name="add"></a>CImageList:: Add

Mit dieser Funktion können Sie einer Bildliste ein oder mehrere Bilder oder ein Symbol hinzufügen.

```
int Add(
    CBitmap* pbmImage,
    CBitmap* pbmMask);

int Add(
    CBitmap* pbmImage,
    COLORREF crMask);

int Add(HICON hIcon);
```

### <a name="parameters"></a>Parameter

*pbmimage*<br/>
Ein Zeiger auf die Bitmap, die das Bild oder die Bilder enthält. Die Anzahl der Bilder wird von der Breite der Bitmap abgeleitet.

*pbmmask*<br/>
Ein Zeiger auf die Bitmap, die die Maske enthält. Wenn keine Maske mit der Bildliste verwendet wird, wird dieser Parameter ignoriert.

*crmask*<br/>
Die zum Generieren der Maske verwendete Farbe. Jedes Pixel dieser Farbe in der angegebenen Bitmap wird in Schwarz geändert, und das entsprechende Bit in der Maske wird auf 1 festgelegt.

*hIcon*<br/>
Handle des Symbols, das die Bitmap und Maske für das neue Bild enthält.

### <a name="return-value"></a>Rückgabewert

NULL basierter Index des ersten neuen Bilds, wenn erfolgreich. andernfalls-1.

### <a name="remarks"></a>Hinweise

Sie sind verantwortlich für das Freigeben des Symbol Handles, wenn Sie damit abgeschlossen sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

##  <a name="attach"></a>CImageList:: Attach

Diese Funktion wird aufgerufen, um eine Bildliste an ein `CImageList` Objekt anzufügen.

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parameter

*hImageList*<br/>
Ein Handle für ein Bildlisten Objekt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Anlage erfolgreich war. andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

##  <a name="begindrag"></a>CImageList:: BeginDrag

Mit dieser Funktion können Sie mit dem Ziehen eines Bilds beginnen.

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parameter

*nbild*<br/>
Der null basierte Index des zu ziehenden Bilds.

*pthotspot*<br/>
Koordinaten der Anfangs Zieh Position (in der Regel die Cursorposition). Die Koordinaten sind relativ zur linken oberen Ecke des Bilds.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Diese Funktion erstellt eine temporäre Bildliste, die für das Ziehen verwendet wird. Das Bild kombiniert das angegebene Bild und seine Maske mit dem aktuellen Cursor. Als Reaktion auf nachfolgende WM_MOUSEMOVE-Nachrichten können Sie das Zieh Bild mithilfe der `DragMove` Member-Funktion verschieben. Um den Zieh Vorgang zu beenden, können Sie die `EndDrag` Member-Funktion verwenden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

##  <a name="cimagelist"></a>CImageList:: CImageList

Erstellt ein `CImageList`-Objekt.

```
CImageList();
```

##  <a name="copy"></a>CImageList:: Copy

Diese Member-Funktion implementiert das Verhalten der Win32-Funktion [ImageList_Copy](/windows/win32/api/commctrl/nf-commctrl-imagelist_copy), wie in der Windows SDK beschrieben.

```
BOOL Copy(
    int iDst,
    int iSrc,
    UINT uFlags = ILCF_MOVE);

BOOL Copy(
    int iDst,
    CImageList* pSrc,
    int iSrc,
    UINT uFlags = ILCF_MOVE);
```

### <a name="parameters"></a>Parameter

*idst*<br/>
Der null basierte Index des Bilds, das als Ziel des Kopiervorgangs verwendet werden soll.

*ISRC*<br/>
Der null basierte Index des Bilds, das als Quelle für den Kopiervorgang verwendet werden soll.

*uFlags*<br/>
Der bitflagwert, der den Typ des Kopiervorgangs angibt, der erstellt werden soll. Dieser Parameter kann einen der folgenden Werte aufweisen:

|Wert|Bedeutung|
|-----------|-------------|
|ILCF_MOVE|Das Quellbild wird in den Index des Ziel Images kopiert. Dieser Vorgang führt zu mehreren Instanzen eines bestimmten Bilds. ILCF_MOVE ist die Standardeinstellung.|
|ILCF_SWAP|Die Quell-und Ziel Images tauschen Positionen in der Bildliste aus.|

*pSrc*<br/>
Ein Zeiger auf ein `CImageList` Objekt, das das Ziel des Kopiervorgangs ist.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

##  <a name="create"></a>CImageList:: Create

Initialisiert eine Bildliste und fügt Sie an ein [CImageList](../../mfc/reference/cimagelist-class.md) -Objekt an.

```
BOOL Create(
    int cx,
    int cy,
    UINT nFlags,
    int nInitial,
    int nGrow);

BOOL Create(
    UINT nBitmapID,
    int cx,
    int nGrow,
    COLORREF crMask);

BOOL Create(
    LPCTSTR lpszBitmapID,
    int cx,
    int nGrow,
    COLORREF crMask);

BOOL Create(
    CImageList& imagelist1,
    int nImage1,
    CImageList& imagelist2,
    int nImage2,
    int dx,
    int dy);

BOOL Create(CImageList* pImageList);
```

### <a name="parameters"></a>Parameter

*verschoben*<br/>
Dimensionen jedes Bilds in Pixel.

*CY*<br/>
Dimensionen jedes Bilds in Pixel.

*nFlags*<br/>
Gibt den Typ der zu erstellenden Bildliste an. Dieser Parameter kann eine Kombination der folgenden Werte sein, kann jedoch nur einen der `ILC_COLOR` Werte enthalten.

|Wert|Bedeutung|
|-----------|-------------|
|ILC_COLOR|Verwenden Sie das Standardverhalten, wenn keines der anderen ILC_COLOR *-Flags angegeben wird. In der Regel ist der Standardwert ILC_COLOR4. für ältere Anzeigetreiber ist der Standardwert ILC_COLORDDB.|
|ILC_COLOR4|Verwenden Sie einen (16) geräteunabhängigen Bitmap-Abschnitt (DIB), der als Bitmap für die Bildliste verwendet wird.|
|ILC_COLOR8|Verwenden Sie einen 8-Bit-DIB-Abschnitt. Die Farben, die für die Farbtabelle verwendet werden, entsprechen den Farben der halbftone-Palette.|
|ILC_COLOR16|Verwenden Sie einen 16-Bit-DIB-Abschnitt (32/64K-Farbe).|
|ILC_COLOR24|Verwenden Sie einen 24-Bit-DIB-Abschnitt.|
|ILC_COLOR32|Verwenden Sie einen 32-Bit-DIB-Abschnitt.|
|ILC_COLORDDB|Verwenden Sie eine Geräte abhängige Bitmap.|
|ILC_MASK|Verwendet eine Maske. Die Bildliste enthält zwei Bitmaps, von denen eine eine monochrome Bitmap ist, die als Maske verwendet wird. Wenn dieser Wert nicht eingeschlossen ist, enthält die Bildliste nur eine Bitmap. Weitere Informationen zu maskierten Bildern finden Sie [unterzeichnen von Bildern aus einer Bildliste](../../mfc/drawing-images-from-an-image-list.md) .|

*ninitial*<br/>
Anzahl der Images, die in der Bildliste anfänglich enthalten sind.

*nvergrößerung*<br/>
Anzahl der Images, mit denen die Bildliste vergrößert werden kann, wenn das System die Größe der Liste ändern muss, um Platz für neue Images zu schaffen. Dieser Parameter stellt die Anzahl der neuen Bilder dar, die in der Bildliste mit Größenänderung enthalten sein können.

*nbitmapid*<br/>
Ressourcen-IDs der Bitmap, die der Bildliste zugeordnet werden soll.

*crmask*<br/>
Die zum Generieren einer Maske verwendete Farbe. Jedes Pixel dieser Farbe in der angegebenen Bitmap wird in Schwarz geändert, und das entsprechende Bit in der Maske wird auf 1 festgelegt.

*lpszbitmapid*<br/>
Eine Zeichenfolge, die die Ressourcen-IDs der Bilder enthält.

*imagelist1*<br/>
Ein Verweis auf ein `CImageList`-Objekt.

*nImage1*<br/>
Der Index des ersten vorhandenen Bilds.

*imagelist2*<br/>
Ein Verweis auf ein `CImageList`-Objekt.

*nImage2*<br/>
Index des zweiten vorhandenen Bilds.

*Market*<br/>
Offset der x-Achse des zweiten Bilds in Beziehung zum ersten Bild in Pixel.

*reiche*<br/>
Offset der y-Achse des zweiten Bilds in Beziehung zum ersten Bild in Pixel.

*pimagelist*<br/>
Ein Zeiger auf ein `CImageList` -Objekt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Sie erstellen eine `CImageList` in zwei Schritten. Zuerst wird der-Konstruktor aufgerufen und dann `Create`aufgerufen, der die Bildliste erstellt und an das `CImageList`-Objekt anfügt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

##  <a name="deleteimagelist"></a>CImageList::D eleteimagelist

Mit dieser Funktion können Sie eine Bildliste löschen.

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

##  <a name="deletetempmap"></a>CImageList::D eletetempmap

Wird automatisch vom `CWinApp` Leerlaufzeit Handler aufgerufen `DeleteTempMap` löscht alle temporären `CImageList` Objekte, die von [FromHandle](#fromhandle)erstellt wurden, aber keine Handles (`hImageList`) zerstört, die vorübergehend den `ImageList` Objekten zugeordnet sind.

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

##  <a name="detach"></a>CImageList::D Etach

Mit dieser Funktion können Sie ein bildlist-Objekt von einem `CImageList` Objekt trennen.

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für ein Bildlisten Objekt.

### <a name="remarks"></a>Hinweise

Diese Funktion gibt ein Handle für das Image List-Objekt zurück.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CImageList:: Attach](#attach).

##  <a name="dragenter"></a>CImageList::D ragenter

Während eines Zieh Vorgangs sperrt Updates für das von *pwndlock* angegebene Fenster und zeigt das Zieh Bild an der durch *Punkt*angegebenen Position an.

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>Parameter

*pwndlock*<br/>
Zeiger auf das Fenster, das das Zieh Bild besitzt.

*Punkt*<br/>
Die Position, an der das Zieh Bild angezeigt werden soll. Die Koordinaten sind relativ zur linken oberen Ecke des Fensters (nicht zum Client Bereich).

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Die Koordinaten sind relativ zur oberen linken Ecke des Fensters, sodass Sie die Breite der Fensterelemente, wie z. b. den Rahmen, die Titelleiste und die Menüleiste, beim Angeben der Koordinaten ausgleichen müssen.

Wenn *pwndlock* den Wert NULL hat, zeichnet diese Funktion das Bild im dem Desktop Fenster zugeordneten Anzeige Kontext, und die Koordinaten sind relativ zur oberen linken Ecke des Bildschirms.

Diese Funktion sperrt alle anderen Updates für das angegebene Fenster während des Zieh Vorgangs. Wenn Sie während eines Zieh Vorgangs eine Zeichnung durchführen müssen, z. b. das Ziel eines Drag & Drop-Vorgangs, können Sie das gezogene Bild temporär ausblenden, indem Sie die [CImageList::D ragleave](#dragleave) -Funktion verwenden.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CImageList:: BeginDrag](#begindrag).

##  <a name="dragleave"></a>CImageList::D ragleave

Entsperrt das von *pwndlock* angegebene Fenster und blendet das Zieh Bild aus, sodass das Fenster aktualisiert werden kann.

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>Parameter

*pwndlock*<br/>
Zeiger auf das Fenster, das das Zieh Bild besitzt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CImageList:: EndDrag](#enddrag).

##  <a name="dragmove"></a>CImageList::D ragmove

Diese Funktion wird aufgerufen, um das Bild zu verschieben, das während eines Drag & Drop-Vorgangs gezogen wird.

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>Parameter

*pt*<br/>
Neue Zieh Position.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Diese Funktion wird in der Regel als Reaktion auf eine WM_MOUSEMOVE Nachricht aufgerufen. Um einen Zieh Vorgang zu starten, verwenden Sie die `BeginDrag` Member-Funktion.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

##  <a name="dragshownolock"></a>CImageList::D ragshownolock

Zeigt das Zieh Bild während eines Zieh Vorgangs an oder blendet es aus, ohne das Fenster zu sperren.

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>Parameter

*bShow*<br/>
Gibt an, ob das Zieh Bild angezeigt werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Die Funktion [CImageList::D ragenter](#dragenter) sperrt alle Updates für das Fenster während eines Zieh Vorgangs. Diese Funktion sperrt das Fenster jedoch nicht.

##  <a name="draw"></a>CImageList::D RAW

Mit dieser Funktion wird das Bild gezeichnet, das während eines Drag & Drop-Vorgangs gezogen wird.

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Zeiger auf den Zielgeräte Kontext.

*nbild*<br/>
Der null basierte Index des zu zeichnenden Bilds.

*pt*<br/>
Der Speicherort, an dem im angegebenen Gerätekontext gezeichnet werden soll.

*nstyle*<br/>
Flag zum Angeben der Zeichnungs Art. Es kann sich um einen oder mehrere der folgenden Werte handeln:

|Wert|Bedeutung|
|-----------|-------------|
|ILD_BLEND25, ILD_FOCUS|Zeichnet das Bild, wobei 25 Prozent mit der Hervorhebungs Farbe des Systems kombiniert werden. Dieser Wert hat keine Auswirkung, wenn die Bildliste keine Maske enthält.|
|ILD_BLEND50, ILD_SELECTED, ILD_BLEND|Zeichnet das Bild, wobei 50 Prozent mit der Hervorhebungs Farbe des Systems kombiniert werden. Dieser Wert hat keine Auswirkung, wenn die Bildliste keine Maske enthält.|
|ILD_MASK|Zeichnet die Maske.|
|ILD_NORMAL|Zeichnet das Bild mithilfe der Hintergrundfarbe für die Bildliste. Wenn die Hintergrundfarbe der CLR_NONE Wert ist, wird das Bild transparent mithilfe der Maske gezeichnet.|
|ILD_TRANSPARENT|Zeichnet das Bild unabhängig von der Hintergrundfarbe transparent mithilfe der Maske.|

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CImageList:: Server Image](#setoverlayimage).

##  <a name="drawex"></a>CImageList::D rawex

Zeichnet ein Bildlisten Element im angegebenen Gerätekontext.

```
BOOL DrawEx(
    CDC* pDC,
    int nImage,
    POINT pt,
    SIZE sz,
    COLORREF clrBk,
    COLORREF clrFg,
    UINT nStyle);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Zeiger auf den Zielgeräte Kontext.

*nbild*<br/>
Der null basierte Index des zu zeichnenden Bilds.

*pt*<br/>
Der Speicherort, an dem im angegebenen Gerätekontext gezeichnet werden soll.

*RT*<br/>
Die Größe des Bilds, das in Relation zur oberen linken Ecke des Bilds gezeichnet werden soll. Weitere Informationen finden Sie unter *DX* und *dy* in [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) im Windows SDK.

*clrbk*<br/>
Hintergrundfarbe des Bilds. Weitere Informationen finden Sie unter *rgbbk* in [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) im Windows SDK.

*clrfg*<br/>
Vordergrundfarbe des Bilds. Weitere Informationen finden Sie unter *rgbfg* in [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) im Windows SDK.

*nstyle*<br/>
Flag zum Angeben der Zeichnungs Art. Weitere *Informationen finden Sie unter* [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) in der Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Die-Funktion verwendet die angegebene Zeichnungs Art und kombiniert das Bild mit der angegebenen Farbe.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

##  <a name="drawindirect"></a>CImageList::D rawindirect

Diese Member-Funktion aufrufen, um ein Bild aus einer Bildliste zu zeichnen.

```
BOOL DrawIndirect(IMAGELISTDRAWPARAMS* pimldp);

BOOL DrawIndirect(
    CDC* pDC,
    int nImage,
    POINT pt,
    SIZE sz,
    POINT ptOrigin,
    UINT fStyle = ILD_NORMAL,
    DWORD dwRop = SRCCOPY,
    COLORREF rgbBack = CLR_DEFAULT,
    COLORREF rgbFore = CLR_DEFAULT,
    DWORD fState = ILS_NORMAL,
    DWORD Frame = 0,
    COLORREF crEffect = CLR_DEFAULT);
```

### <a name="parameters"></a>Parameter

*pimldp*<br/>
Ein Zeiger auf eine [imagelistdrawparameams](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) -Struktur, die Informationen über den Zeichnungs Vorgang enthält.

*pDC*<br/>
Ein Zeiger auf den Zielgeräte Kontext. Sie müssen dieses [CDC](../../mfc/reference/cdc-class.md) -Objekt löschen, wenn Sie damit abgeschlossen sind.

*nbild*<br/>
Der null basierte Index des Bilds, das gezeichnet werden soll.

*pt*<br/>
Eine [Punkt](/previous-versions/dd162805\(v=vs.85\)) Struktur, die die x-und y-Koordinaten enthält, in denen das Bild gezeichnet wird.

*RT*<br/>
Eine [Größen](/windows/win32/api/windef/ns-windef-size) Struktur, die die Größe des Bilds angibt, das gezeichnet werden soll.

*ptorigin*<br/>
Eine [Punkt](/previous-versions/dd162805\(v=vs.85\)) Struktur, die die x-und y-Koordinaten enthält, die die linke obere Ecke des Zeichnungs Vorgangs in Bezug auf das Bild selbst angeben. Pixel des Bilds, die sich Links von der x-Koordinate und oberhalb der y-Koordinate befinden, werden nicht gezeichnet.

*Stil*<br/>
Flag, das die Zeichnungsart und optional das Überlagerungs Bild angibt. Weitere Informationen zum Überlagerungs Bild finden Sie im Abschnitt "Hinweise". Die MFC-Standard Implementierung, ILD_NORMAL, zeichnet das Bild mithilfe der Hintergrundfarbe für die Bildliste. Wenn die Hintergrundfarbe der CLR_NONE Wert ist, wird das Bild transparent mithilfe einer Maske gezeichnet.

Andere mögliche Stile werden unter dem *fstyle* -Member der [imagelistdrawparameams](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) -Struktur beschrieben.

*dwrop*<br/>
Ein-Wert, der einen Raster Vorgangs Code angibt. Diese Codes definieren, wie die Farbdaten für das Quell Rechteck mit den Farbdaten für das Ziel Rechteck kombiniert werden, um die endgültige Farbe zu erzielen. Die MFC-Standard Implementierung (srccopy) kopiert das Quell Rechteck direkt in das Ziel Rechteck. Dieser Parameter wird ignoriert, wenn der Parameter " *sstyle* " das ILD_ROP-Flag nicht enthält.

Andere mögliche Werte werden unter dem *dwrop* -Member der [imagelistdrawparameams](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) -Struktur beschrieben.

*rgbback*<br/>
Die Hintergrundfarbe des Bilds standardmäßig CLR_DEFAULT. Dieser Parameter kann ein von der Anwendung definierter RGB-Wert oder einer der folgenden Werte sein:

|Wert|Bedeutung|
|-----------|-------------|
|CLR_DEFAULT|Standard Hintergrundfarbe. Das Bild wird mithilfe der Hintergrundfarbe der Bildliste gezeichnet.|
|CLR_NONE|Keine Hintergrundfarbe. Das Bild wird transparent gezeichnet.|

*rgbfore*<br/>
Bild Vordergrundfarbe, standardmäßig CLR_DEFAULT. Dieser Parameter kann ein von der Anwendung definierter RGB-Wert oder einer der folgenden Werte sein:

|Wert|Bedeutung|
|-----------|-------------|
|CLR_DEFAULT|Standard Vordergrundfarbe. Das Bild wird mit der Hervorhebungs Farbe des Systems als Vordergrundfarbe gezeichnet.|
|CLR_NONE|Keine Blend-Farbe. Das Bild wird mit der Farbe des Zielgeräte Kontexts kombiniert.|

Dieser Parameter wird nur verwendet, *Wenn der* Wert für die ILD_BLEND25 oder ILD_BLEND50-Flag enthält.

*Status*<br/>
Flag, das den Zeichnungs Zustand angibt. Dieser Member kann eine oder mehrere Bildlisten-Statusflags enthalten.

*Frame*<br/>
Wirkt sich auf das Verhalten von Effekten und Alpha Mischungs Effekten aus.

Bei Verwendung mit ILS_SATURATE enthält dieser Member den Wert, der jeder Farbkomponente des RGB-Dreiecks für jedes Pixel im Symbol hinzugefügt wird.

Bei Verwendung mit ILS_APLHA enthält dieser Member den Wert für den Alphakanal. Dieser Wert kann zwischen 0 und 255 liegen, wobei 0 vollständig transparent ist und 255 vollständig deckend ist.

*"feffect"*<br/>
Ein [COLORREF](/windows/win32/gdi/colorref) -Wert, der für Glanz-und Schatteneffekte verwendet wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Bild erfolgreich gezeichnet wird. andernfalls false.

### <a name="remarks"></a>Hinweise

Verwenden Sie die erste Version, wenn Sie die Win32-Struktur selbst auffüllen möchten. Verwenden Sie die zweite Version, wenn Sie mindestens ein MFC-Standardargument nutzen oder die Struktur nicht verwalten möchten.

Ein Überlagerungs Bild ist ein Bild, das über dem primär Bild gezeichnet wird, das in dieser Member-Funktion durch den *nImage* -Parameter angegeben wird. Zeichnen Sie eine Überlagerungs Maske mithilfe der [Draw](#draw) -Member-Funktion mit dem 1-basierten Index der Überlagerungs Maske, die mithilfe des [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) -Makros angegeben wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

##  <a name="enddrag"></a>CImageList:: EndDrag

Mit dieser Funktion können Sie einen Zieh Vorgang beenden.

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>Hinweise

Um einen Zieh Vorgang zu starten, verwenden Sie die `BeginDrag` Member-Funktion.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

##  <a name="extracticon"></a>CImageList:: ExtractIcon

Rufen Sie diese Funktion auf, um ein Symbol auf der Grundlage eines Bilds und der zugehörigen Maske in einer Bildliste zu erstellen.

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>Parameter

*nbild*<br/>
NULL basierter Index des Bilds.

### <a name="return-value"></a>Rückgabewert

Handle des Symbols, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Hinweise

Diese Methode basiert auf dem Verhalten des [ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) -Makros, um das Symbol zu erstellen. Weitere Informationen zum Erstellen und Bereinigen von Symbolen finden Sie im [ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) -Makro.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

##  <a name="fromhandle"></a>CImageList:: FromHandle

Gibt einen Zeiger auf ein `CImageList` Objekt zurück, wenn ein Handle für eine Bildliste angegeben ist.

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parameter

*hImageList*<br/>
Gibt die Bildliste an.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `CImageList` Objekt, wenn erfolgreich. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Wenn eine `CImageList` nicht bereits an das Handle angefügt ist, wird ein temporäres `CImageList` Objekt erstellt und angefügt. Dieses temporäre `CImageList` Objekt ist nur gültig, bis das nächste Mal die Leerlaufzeit der Anwendung in der Ereignisschleife liegt. zu diesem Zeitpunkt werden alle temporären Objekte gelöscht.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

##  <a name="fromhandlepermanent"></a>CImageList:: fromlenker permanent

Gibt einen Zeiger auf ein `CImageList` Objekt zurück, wenn ein Handle für eine Bildliste angegeben ist.

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parameter

*hImageList*<br/>
Gibt die Bildliste an.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `CImageList` Objekt, wenn erfolgreich. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Wenn ein `CImageList` Objekt nicht an das Handle angefügt ist, wird NULL zurückgegeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

##  <a name="getbkcolor"></a>CImageList:: GetBkColor

Rufen Sie diese Funktion auf, um die aktuelle Hintergrundfarbe für eine Bildliste abzurufen.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Rückgabewert

Der RGB-Farbwert der Hintergrundfarbe des `CImageList` Objekts.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CImageList:: SetBkColor](#setbkcolor).

##  <a name="getdragimage"></a>CImageList:: GetDragImage

Ruft die temporäre Bildliste ab, die für das Ziehen verwendet wird.

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>Parameter

*lpPoint*<br/>
Adresse einer [Punkt](/previous-versions/dd162805\(v=vs.85\)) Struktur, die die aktuelle Zieh Position empfängt.

*lppointhotspot*<br/>
Adresse einer `POINT`-Struktur, die den Offset des Zieh Bilds in Relation zur Zieh Position empfängt.

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ein Zeiger auf die temporäre Bildliste, die für das Ziehen verwendet wird. andernfalls NULL.

##  <a name="getimagecount"></a>CImageList:: GetImageCount

Mit dieser Funktion wird die Anzahl von Bildern in einer Bildliste abgerufen.

```
int GetImageCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Bilder.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CImageList:: ExtractIcon](#extracticon).

##  <a name="getimageinfo"></a>CImageList:: getimagan FO

Rufen Sie diese Funktion auf, um Informationen zu einem Bild abzurufen.

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>Parameter

*nbild*<br/>
NULL basierter Index des Bilds.

*pimagumfo*<br/>
Ein Zeiger auf eine [imageinfo](/windows/win32/api/commctrl/ns-commctrl-imageinfo) -Struktur, die Informationen über das Bild empfängt. Die Informationen in dieser Struktur können verwendet werden, um die Bitmaps für das Bild direkt zu bearbeiten.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Die `IMAGEINFO`-Struktur enthält Informationen zu einem Bild in einer Bildliste.

##  <a name="getsafehandle"></a>CImageList:: geout afehandle

Rufen Sie diese Funktion auf, um den `m_hImageList` Datenmember abzurufen.

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für die angefügte Bildliste. andernfalls NULL, wenn kein Objekt angefügt ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

##  <a name="m_himagelist"></a>CImageList:: m_hImageList

Ein Handle der Bildliste, die an dieses-Objekt angefügt ist.

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>Hinweise

Der `m_hImageList` Datenmember ist eine öffentliche Variable des Typs HIMAGELIST.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

##  <a name="operator_himagelist"></a>CImageList:: Operator HIMAGELIST

Verwenden Sie diesen Operator, um das angefügte Handle des `CImageList` Objekts zu erhalten.

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ein Handle für die Bildliste, die durch das `CImageList`-Objekt dargestellt wird. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Dieser Operator ist ein Typumwandlungs Operator, der die direkte Verwendung eines HIMAGELIST-Objekts unterstützt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

##  <a name="read"></a>CImageList:: Read

Mit dieser Funktion können Sie eine Bildliste aus einem Archiv lesen.

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>Parameter

*wird verarbeitet*<br/>
Ein Zeiger auf ein `CArchive` Objekt, aus dem die Bildliste gelesen werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

##  <a name="remove"></a>CImageList:: Remove

Mit dieser Funktion können Sie ein Bild aus einem Bildlisten Objekt entfernen.

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>Parameter

*nbild*<br/>
Der null basierte Index des zu entfernenden Bilds.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Alle Elemente nach *nImage* werden nun um eine Position nach unten verschoben. Wenn eine Bildliste beispielsweise zwei Elemente enthält, führt das Löschen des ersten Elements dazu, dass das restliche Element jetzt an der ersten Position liegt. *nImage*= 0 für das Element an der ersten Position.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

##  <a name="replace"></a>CImageList:: Replace

Mit dieser Funktion können Sie ein Bild in einer Bildliste durch ein neues Bild ersetzen.

```
BOOL Replace(
    int nImage,
    CBitmap* pbmImage,
    CBitmap* pbmMask);

int Replace(
    int nImage,
    HICON hIcon);
```

### <a name="parameters"></a>Parameter

*nbild*<br/>
Der null basierte Index des zu ersetzenden Bilds.

*pbmimage*<br/>
Ein Zeiger auf die Bitmap, die das Bild enthält.

*pbmmask*<br/>
Ein Zeiger auf die Bitmap, die die Maske enthält. Wenn keine Maske mit der Bildliste verwendet wird, wird dieser Parameter ignoriert.

*hIcon*<br/>
Ein Handle für das Symbol, das die Bitmap und Maske für das neue Bild enthält.

### <a name="return-value"></a>Rückgabewert

Die Version, die bool zurückgibt, gibt bei erfolgreicher Ausführung ungleich NULL zurück andernfalls 0.

Die Version **int** gibt den NULL basierten Index des Bilds zurück, wenn erfolgreich. andernfalls-1.

### <a name="remarks"></a>Hinweise

Rufen Sie diese Member-Funktion nach dem Aufruf von "" " [", um](#setimagecount) die neuen, gültigen Bilder den Platzhalter Bild Indexnummern zuzuweisen.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CImageList::-Abbild magecount](#setimagecount).

##  <a name="setbkcolor"></a>CImageList:: SetBkColor

Mit dieser Funktion wird die Hintergrundfarbe für eine Bildliste festgelegt.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parameter

*programmiert*<br/>
Die festzulegende Hintergrundfarbe. Sie kann CLR_NONE werden. In diesem Fall werden Bilder mithilfe der Maske transparent gezeichnet.

### <a name="return-value"></a>Rückgabewert

Die vorherige Hintergrundfarbe, wenn erfolgreich. Andernfalls CLR_NONE.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

##  <a name="setdragcursorimage"></a>CImageList:: setdragcurrsorimage

Erstellt ein neues Zieh Bild, indem das angegebene Bild (in der Regel ein Mauszeiger Bild) mit dem aktuellen Drag-Bild kombiniert wird.

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parameter

*ndrag*<br/>
Der Index des neuen Bilds, das mit dem Zieh Bild kombiniert werden soll.

*pthotspot*<br/>
Die Position des Hotspots innerhalb des neuen Bilds.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Da die Zieh Funktionen das neue Bild während eines Zieh Vorgangs verwenden, sollten Sie die Windows [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor) -Funktion verwenden, um den eigentlichen Mauszeiger nach dem Aufrufen von `CImageList::SetDragCursorImage`auszublenden. Andernfalls weist das System möglicherweise zwei Mauszeiger auf die Dauer des Zieh Vorgangs auf.

##  <a name="setimagecount"></a>CImageList:: Abbild magecount

Mit dieser Member-Funktion können Sie die Anzahl der Bilder in einem `CImageList` Objekt zurücksetzen.

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>Parameter

*unewcount*<br/>
Der-Wert, der die neue Gesamtzahl der Bilder in der Bildliste angibt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Hinweise

Wenn Sie diese Member-Funktion zum Erhöhen der Anzahl der Bilder in der Bildliste aufgerufen haben, können Sie für jedes weitere Bild [ersetzen](#replace) , um die neuen Indizes gültigen Bildern zuzuweisen. Wenn Sie die Indizes nicht gültigen Bildern zuweisen, sind Zeichnungsvorgänge, die die neuen Images erstellen, unvorhersehbar.

Wenn Sie die Größe einer Bildliste mit dieser Funktion verringern, werden die abgeschnittene Bilder freigegeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

##  <a name="setoverlayimage"></a>CImageList:: Server-layimage

Mit dieser Funktion können Sie den NULL basierten Index eines Bilds der Liste der Bilder hinzufügen, die als Überlagerungs Masken verwendet werden sollen.

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>Parameter

*nbild*<br/>
NULL basierter Index des Bilds, das als Überlagerungs Maske verwendet werden soll.

*noverlay*<br/>
Ein einbasierter Index der Überlagerungs Maske.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Der Liste können bis zu vier Indizes hinzugefügt werden.

Eine Überlagerungs Maske ist ein Bild, das transparent über ein anderes Bild gezeichnet wird. Zeichnen Sie eine Überlagerungs Maske über ein Bild, indem Sie die Funktion [CImageList::D RAW](#draw) Member mit dem 1-basierten Index der über Lagerungs Maske verwenden, die mit dem INDEXTOOVERLAYMASK-Makro angegeben wurde.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

##  <a name="write"></a>CImageList:: Write

Mit dieser Funktion können Sie ein bildlist-Objekt in ein Archiv schreiben.

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>Parameter

*wird verarbeitet*<br/>
Ein Zeiger auf ein `CArchive` Objekt, in dem die Bildliste gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CListCtrl-Klasse](../../mfc/reference/clistctrl-class.md)<br/>
[CTabCtrl-Klasse](../../mfc/reference/ctabctrl-class.md)

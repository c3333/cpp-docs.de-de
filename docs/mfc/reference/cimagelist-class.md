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
ms.openlocfilehash: 17cd2a94cb397e59e4622aea8ed7bb6fbe1eee43
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752687"
---
# <a name="cimagelist-class"></a>CImageList-Klasse

Stellt die Funktionalität des allgemeinen Windows-Bildlisten-Steuerelements bereit.

## <a name="syntax"></a>Syntax

```
class CImageList : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CImageList::CImageList](#cimagelist)|Erstellt ein `CImageList`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CImageList::Hinzufügen](#add)|Fügt ein Bild oder Bilder zu einer Bildliste hinzu.|
|[CImageList::Anfügen](#attach)|Fügt eine Bildliste `CImageList` an ein Objekt an.|
|[CImageList::BeginDrag](#begindrag)|Beginnt mit dem Ziehen eines Bildes.|
|[CImageList::Kopieren](#copy)|Kopiert ein Bild `CImageList` innerhalb eines Objekts.|
|[CImageList::Erstellen](#create)|Initialisiert eine Bildliste und fügt `CImageList` sie an ein Objekt an.|
|[CImageList::DeleteImageList](#deleteimagelist)|Löscht eine Bildliste.|
|[CImageList::DeleteTempMap](#deletetempmap)|Wird vom [CWinApp-Leerlaufzeithandler](../../mfc/reference/cwinapp-class.md) aufgerufen, um alle temporären `CImageList` Objekte zu löschen, die von `FromHandle`erstellt wurden.|
|[CImageList::Detach](#detach)|Trennt ein Bildlistenobjekt von `CImageList` einem Objekt und gibt ein Handle in eine Bildliste zurück.|
|[CImageList::DragEnter](#dragenter)|Sperrt Aktualisierungen während eines Ziehvorgangs und zeigt das Ziehbild an einer angegebenen Position an.|
|[CImageList::DragLeave](#dragleave)|Entsperrt das Fenster und blendet das Ziehbild aus, sodass das Fenster aktualisiert werden kann.|
|[CImageList::DragMove](#dragmove)|Verschiebt das Bild, das während eines Drag-and-Drop-Vorgangs gezogen wird.|
|[CImageList::DragShowNolock](#dragshownolock)|Zeigt das Ziehbild während eines Ziehvorgangs an oder blendet es aus, ohne das Fenster zu sperren.|
|[CImageList::Draw](#draw)|Zeichnet das Bild, das während eines Drag-and-Drop-Vorgangs gezogen wird.|
|[CImageList::DrawEx](#drawex)|Zeichnet ein Bildlistenelement im angegebenen Gerätekontext. Die Funktion verwendet den angegebenen Zeichnungsstil und fügt das Bild mit der angegebenen Farbe überein.|
|[CImageList::DrawIndirect](#drawindirect)|Zeichnet ein Bild aus einer Bildliste.|
|[CImageList::EndDrag](#enddrag)|Beendet einen Ziehvorgang.|
|[CImageList::ExtractIcon](#extracticon)|Erstellt ein Symbol basierend auf einem Bild und einer Maske in einer Bildliste.|
|[CImageList::FromHandle](#fromhandle)|Gibt einen Zeiger `CImageList` auf ein Objekt zurück, wenn einer Bildliste ein Handle gegeben wird. Wenn ein `CImageList`-Objekt nicht an das Handle angefügt ist, wird ein temporäres `CImageList`-Objekt erstellt und angefügt.|
|[CImageList::FromHandlePermanent](#fromhandlepermanent)|Gibt einen Zeiger `CImageList` auf ein Objekt zurück, wenn einer Bildliste ein Handle gegeben wird. Wenn `CImageList` ein Objekt nicht an das Handle angefügt ist, wird NULL zurückgegeben.|
|[CImageList::GetBkColor](#getbkcolor)|Ruft die aktuelle Hintergrundfarbe für eine Bildliste ab.|
|[CImageList::GetDragImage](#getdragimage)|Ruft die temporäre Bildliste ab, die zum Ziehen verwendet wird.|
|[CImageList::GetImageCount](#getimagecount)|Ruft die Anzahl der Bilder in einer Bildliste ab.|
|[CImageList::GetImageInfo](#getimageinfo)|Ruft Informationen zu einem Bild ab.|
|[CImageList::GetSafeHandle](#getsafehandle)|Ruft `m_hImageList`ab .|
|[CImageList::Lesen](#read)|Liest eine Bildliste aus einem Archiv.|
|[CImageList::Entfernen](#remove)|Entfernt ein Bild aus einer Bildliste.|
|[CImageList::Ersetzen](#replace)|Ersetzt ein Bild in einer Bildliste durch ein neues Bild.|
|[CImageList::SetBkColor](#setbkcolor)|Legt die Hintergrundfarbe für eine Bildliste fest.|
|[CImageList::SetDragCursorImage](#setdragcursorimage)|Erstellt ein neues Ziehbild.|
|[CImageList::SetImageCount](#setimagecount)|Setzt die Anzahl der Bilder in einer Bildliste zurück.|
|[CImageList::SetOverlayImage](#setoverlayimage)|Fügt den nullbasierten Index eines Bildes zur Liste der Bilder hinzu, die als Überlagerungsmasken verwendet werden sollen.|
|[CImageList::Schreiben](#write)|Schreibt eine Bildliste in ein Archiv.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CImageList::operator HIMAGELIST](#operator_himagelist)|Gibt die HIMAGELIST `CImageList`zurück, die an die angehängt ist.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CImageList::m_hImageList](#m_himagelist)|Ein Handle, der die Bildliste enthält, die diesem Objekt zugeordnet ist.|

## <a name="remarks"></a>Bemerkungen

Eine "Bildliste" ist eine Sammlung gleichgroßer Bilder, auf die jeder durch den nullbasierten Index verweisen kann. Bildlisten werden verwendet, um große Sätze von Symbolen oder Bitmaps effizient zu verwalten. Alle Bilder in einer Bildliste sind in einer einzigen, breiten Bitmap im Bildschirmgeräteformat enthalten. Eine Bildliste kann auch eine monochrome Bitmap enthalten, die Masken enthält, die zum transparenten Zeichnen von Bildern verwendet werden (Symbolstil). Die Microsoft Win32 Application Programming Interface (API) bietet Bildlistenfunktionen, mit denen Sie Bilder zeichnen, Bildlisten erstellen und zerstören, Bilder hinzufügen und entfernen, Bilder ersetzen, Bilder zusammenführen und Bilder ziehen können.

Dieses Steuerelement (und `CImageList` damit die Klasse) ist nur für Programme verfügbar, die unter Windows 95/98 und Windows NT Version 3.51 und höher ausgeführt werden.

Weitere Informationen zur `CImageList`Verwendung von finden Sie unter [Steuerelemente](../../mfc/controls-mfc.md) und [Verwenden von CImageList](../../mfc/using-cimagelist.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcmn.h

## <a name="cimagelistadd"></a><a name="add"></a>CImageList::Hinzufügen

Rufen Sie diese Funktion auf, um eine oder mehrere Bilder oder ein Symbol zu einer Bildliste hinzuzufügen.

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

*pbmImage*<br/>
Zeigen Sie mit dem Zeiger auf die Bitmap, die das Bild oder die Bilder enthält. Die Anzahl der Bilder wird aus der Breite der Bitmap abgeleitet.

*pbmMaske*<br/>
Zeiger auf die Bitmap, die die Maske enthält. Wenn keine Maske mit der Bildliste verwendet wird, wird dieser Parameter ignoriert.

*crMask*<br/>
Farbe, die zum Generieren der Maske verwendet wird. Jedes Pixel dieser Farbe in der angegebenen Bitmap wird in Schwarz geändert und das entsprechende Bit in der Maske auf eins gesetzt.

*hIcon*<br/>
Handle des Symbols, das die Bitmap und Maske für das neue Bild enthält.

### <a name="return-value"></a>Rückgabewert

Nullbasierter Index des ersten neuen Bildes, wenn erfolgreich; ansonsten - 1.

### <a name="remarks"></a>Bemerkungen

Sie sind dafür verantwortlich, das Icon-Handle freizugeben, wenn Sie damit fertig sind.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

## <a name="cimagelistattach"></a><a name="attach"></a>CImageList::Anfügen

Rufen Sie diese Funktion auf, `CImageList` um eine Bildliste an ein Objekt anzufügen.

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parameter

*hImageList*<br/>
Ein Handle für ein Bildlistenobjekt.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Anlage erfolgreich war; andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

## <a name="cimagelistbegindrag"></a><a name="begindrag"></a>CImageList::BeginDrag

Rufen Sie diese Funktion auf, um mit dem Ziehen eines Bildes zu beginnen.

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parameter

*nImage*<br/>
Nullbasierter Index des zu ziehenden Bildes.

*ptHotSpot*<br/>
Koordinaten der Start-Ziehposition (in der Regel die Cursorposition). Die Koordinaten sind relativ zur oberen linken Ecke des Bildes.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Funktion erstellt eine temporäre Bildliste, die zum Ziehen verwendet wird. Das Bild kombiniert das angegebene Bild und seine Maske mit dem aktuellen Cursor. Als Reaktion auf nachfolgende WM_MOUSEMOVE-Nachrichten können Sie `DragMove` das Ziehbild mithilfe der Memberfunktion verschieben. Um den Ziehvorgang zu beenden, können Sie die `EndDrag` Memberfunktion verwenden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

## <a name="cimagelistcimagelist"></a><a name="cimagelist"></a>CImageList::CImageList

Erstellt ein `CImageList`-Objekt.

```
CImageList();
```

## <a name="cimagelistcopy"></a><a name="copy"></a>CImageList::Kopieren

Diese Memberfunktion implementiert das Verhalten der Win32-Funktion [ImageList_Copy](/windows/win32/api/commctrl/nf-commctrl-imagelist_copy), wie im Windows SDK beschrieben.

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

*iDst*<br/>
Der nullbasierte Index des Bildes, das als Ziel des Kopiervorgangs verwendet werden soll.

*Isrc*<br/>
Der nullbasierte Index des Bildes, das als Quelle des Kopiervorgangs verwendet werden soll.

*uFlags*<br/>
Der Bit-Flag-Wert, der den Typ des zu machenden Kopiervorgangs angibt. Dieser Parameter kann einer der folgenden Werte sein:

|Wert|Bedeutung|
|-----------|-------------|
|ILCF_MOVE|Das Quellbild wird in den Index des Zielbilds kopiert. Dieser Vorgang führt zu mehreren Instanzen eines bestimmten Abbilds. ILCF_MOVE ist die Standardeinstellung.|
|ILCF_SWAP|Die Quell- und Zielbilder tauschen Positionen in der Bildliste aus.|

*pSrc*<br/>
Ein Zeiger auf `CImageList` ein Objekt, das das Ziel des Kopiervorgangs ist.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

## <a name="cimagelistcreate"></a><a name="create"></a>CImageList::Erstellen

Initialisiert eine Bildliste und fügt sie an ein [CImageList-Objekt](../../mfc/reference/cimagelist-class.md) an.

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

*Cx*<br/>
Abmessungen jedes Bildes in Pixel.

*Cy*<br/>
Abmessungen jedes Bildes in Pixel.

*nFlags*<br/>
Gibt den Typ der zu erstellenden Bildliste an. Dieser Parameter kann eine Kombination der folgenden Werte sein, `ILC_COLOR` aber er kann nur einen der Werte enthalten.

|Wert|Bedeutung|
|-----------|-------------|
|ILC_COLOR|Verwenden Sie das Standardverhalten, wenn keines der anderen ILC_COLOR*-Flags angegeben ist. In der Regel ist der Standardwert ILC_COLOR4. bei älteren Anzeigetreibern ist die Standardeinstellung jedoch ILC_COLORDDB.|
|ILC_COLOR4|Verwenden Sie einen 4-Bit (16 Farbe) geräteunabhängigen Bitmap (DIB) Abschnitt als Bitmap für die Bildliste.|
|ILC_COLOR8|Verwenden Sie einen 8-Bit-DIB-Abschnitt. Die für die Farbtabelle verwendeten Farben sind die gleichen Farben wie die Halbtonpalette.|
|ILC_COLOR16|Verwenden Sie einen 16-Bit-DIB-Abschnitt (32/64k Farbe).|
|ILC_COLOR24|Verwenden Sie einen 24-Bit-DIB-Abschnitt.|
|ILC_COLOR32|Verwenden Sie einen 32-Bit-DIB-Abschnitt.|
|ILC_COLORDDB|Verwenden Sie eine geräteabhängige Bitmap.|
|ILC_MASK|Verwendet eine Maske. Die Bildliste enthält zwei Bitmaps, von denen eine eine monochrome Bitmap ist, die als Maske verwendet wird. Wenn dieser Wert nicht enthalten ist, enthält die Bildliste nur eine Bitmap. Weitere Informationen zu maskierten Bildern finden Sie unter [Zeichnen von Bildern aus einer Bildliste.](../../mfc/drawing-images-from-an-image-list.md)|

*nInitial*<br/>
Anzahl der Bilder, die die Bildliste ursprünglich enthält.

*nWachsen*<br/>
Anzahl der Bilder, um die die Bildliste wachsen kann, wenn das System die Größe der Liste ändern muss, um Platz für neue Bilder zu schaffen. Dieser Parameter stellt die Anzahl der neuen Bilder dar, die die geänderte Bildliste enthalten kann.

*nBitmapID*<br/>
Ressourcen-IDs der Bitmap, die der Bildliste zugeordnet werden sollen.

*crMask*<br/>
Farbe, die zum Generieren einer Maske verwendet wird. Jedes Pixel dieser Farbe in der angegebenen Bitmap wird in Schwarz geändert, und das entsprechende Bit in der Maske wird auf eins festgelegt.

*lpszBitmapID*<br/>
Eine Zeichenfolge, die die Ressourcen-IDs der Bilder enthält.

*Imageliste1*<br/>
Ein Verweis auf ein `CImageList`-Objekt.

*nImage1*<br/>
Index des ersten vorhandenen Bildes.

*imagelist2*<br/>
Ein Verweis auf ein `CImageList`-Objekt.

*nImage2*<br/>
Index des zweiten vorhandenen Bildes.

*Dx*<br/>
Offset der x-Achse des zweiten Bildes in Beziehung zum ersten Bild in Pixel.

*Dy*<br/>
Offset der y-Achse des zweiten Bildes in Beziehung zum ersten Bild in Pixel.

*pImageList*<br/>
Ein Zeiger auf ein `CImageList`-Objekt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Sie erstellen `CImageList` eine in zwei Schritten. Rufen Sie zunächst den Konstruktor auf, und rufen Sie dann auf, `Create`der die Bildliste erstellt und an das `CImageList` Objekt anfügt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

## <a name="cimagelistdeleteimagelist"></a><a name="deleteimagelist"></a>CImageList::DeleteImageList

Rufen Sie diese Funktion auf, um eine Bildliste zu löschen.

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

## <a name="cimagelistdeletetempmap"></a><a name="deletetempmap"></a>CImageList::DeleteTempMap

Wird automatisch `CWinApp` vom Leerlaufzeithandler aufgerufen, `CImageList` löscht alle temporären Objekte, `DeleteTempMap` die von [FromHandle](#fromhandle)erstellt wurden, zerstört jedoch keine Handles ( `hImageList`), die den `ImageList` Objekten vorübergehend zugeordnet sind.

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

## <a name="cimagelistdetach"></a><a name="detach"></a>CImageList::Detach

Rufen Sie diese Funktion auf, um `CImageList` ein Bildlistenobjekt von einem Objekt zu trennen.

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>Rückgabewert

Ein Handle für ein Bildlistenobjekt.

### <a name="remarks"></a>Bemerkungen

Diese Funktion gibt ein Handle an das Bildlistenobjekt zurück.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CImageList::Attach](#attach).

## <a name="cimagelistdragenter"></a><a name="dragenter"></a>CImageList::DragEnter

Während eines Ziehvorgangs werden Aktualisierungen des von *pWndLock* angegebenen Fensters gesperrt und das Ziehbild an der durch *Punkt*angegebenen Position angezeigt.

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>Parameter

*pWndLock*<br/>
Zeigen Sie mit dem Zeiger auf das Fenster, das das Ziehbild besitzt.

*Punkt*<br/>
Position, an der das Ziehbild angezeigt werden soll. Koordinaten sind relativ zur oberen linken Ecke des Fensters (nicht der Clientbereich).

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die Koordinaten sind relativ zur oberen linken Ecke des Fensters, daher müssen Sie die Breiten von Fensterelementen, wie den Rahmen, die Titelleiste und die Menüleiste, beim Angeben der Koordinaten kompensieren.

Wenn *pWndLock* NULL ist, zeichnet diese Funktion das Bild im Anzeigekontext, der dem Desktopfenster zugeordnet ist, und die Koordinaten sind relativ zur oberen linken Ecke des Bildschirms.

Diese Funktion sperrt alle anderen Aktualisierungen des angegebenen Fensters während des Ziehvorgangs. Wenn Sie während eines Ziehvorgangs eine Zeichnung erstellen müssen, z. B. das Ziel eines Drag-and-Drop-Vorgangs hervorheben, können Sie das gezogene Bild mithilfe der Funktion [CImageList::DragLeave](#dragleave) vorübergehend ausblenden.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CImageList::BeginDrag](#begindrag).

## <a name="cimagelistdragleave"></a><a name="dragleave"></a>CImageList::DragLeave

Entsperrt das von *pWndLock* angegebene Fenster und blendet das Ziehbild aus, sodass das Fenster aktualisiert werden kann.

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>Parameter

*pWndLock*<br/>
Zeigen Sie mit dem Zeiger auf das Fenster, das das Ziehbild besitzt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CImageList::EndDrag](#enddrag).

## <a name="cimagelistdragmove"></a><a name="dragmove"></a>CImageList::DragMove

Rufen Sie diese Funktion auf, um das Bild zu verschieben, das während eines Drag-and-Drop-Vorgangs gezogen wird.

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>Parameter

*Pt*<br/>
Neue Ziehposition.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird in der Regel als Reaktion auf eine WM_MOUSEMOVE Nachricht aufgerufen. Um einen Ziehvorgang zu `BeginDrag` starten, verwenden Sie die Memberfunktion.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

## <a name="cimagelistdragshownolock"></a><a name="dragshownolock"></a>CImageList::DragShowNolock

Zeigt das Ziehbild während eines Ziehvorgangs an oder blendet es aus, ohne das Fenster zu sperren.

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>Parameter

*bShow*<br/>
Gibt an, ob das Ziehbild angezeigt werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die Funktion [CImageList::DragEnter](#dragenter) sperrt alle Aktualisierungen des Fensters während eines Ziehvorgangs. Diese Funktion verriegelt das Fenster jedoch nicht.

## <a name="cimagelistdraw"></a><a name="draw"></a>CImageList::Draw

Rufen Sie diese Funktion auf, um das Bild zu zeichnen, das während eines Drag-and-Drop-Vorgangs gezogen wird.

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Zeiger auf den Zielgerätekontext.

*nImage*<br/>
Nullbasierter Index des zu zeichnenden Bildes.

*Pt*<br/>
Speicherort, an dem innerhalb des angegebenen Gerätekontexts gezeichnet werden soll.

*nStyle*<br/>
Flag, das den Zeichnungsstil angibt. Es kann einer oder mehrere dieser Werte sein:

|Wert|Bedeutung|
|-----------|-------------|
|ILD_BLEND25, ILD_FOCUS|Zeichnet das Bild und fügt 25 Prozent mit der System-Hervorhebungsfarbe zusammen. Dieser Wert hat keine Auswirkung, wenn die Bildliste keine Maske enthält.|
|ILD_BLEND50, ILD_SELECTED ILD_BLEND|Zeichnet das Bild und fügt 50 Prozent mit der System-Hervorhebungsfarbe zusammen. Dieser Wert hat keine Auswirkung, wenn die Bildliste keine Maske enthält.|
|ILD_MASK|Zeichnet die Maske.|
|ILD_NORMAL|Zeichnet das Bild mit der Hintergrundfarbe für die Bildliste. Wenn die Hintergrundfarbe der CLR_NONE Wert ist, wird das Bild transparent mit der Maske gezeichnet.|
|ILD_TRANSPARENT|Zeichnet das Bild transparent mit der Maske, unabhängig von der Hintergrundfarbe.|

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CImageList::SetOverlayImage](#setoverlayimage).

## <a name="cimagelistdrawex"></a><a name="drawex"></a>CImageList::DrawEx

Zeichnet ein Bildlistenelement im angegebenen Gerätekontext.

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
Zeiger auf den Zielgerätekontext.

*nImage*<br/>
Nullbasierter Index des zu zeichnenden Bildes.

*Pt*<br/>
Speicherort, an dem innerhalb des angegebenen Gerätekontexts gezeichnet werden soll.

*Sz*<br/>
Größe des Teils des Bildes, der relativ zur oberen linken Ecke des Bildes gezeichnet werden soll. Siehe *dx* und *dy* in [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) im Windows SDK.

*clrBk*<br/>
Hintergrundfarbe des Bildes. Siehe *rgbBk* in [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) im Windows SDK.

*clrFg*<br/>
Vordergrundfarbe des Bildes. Siehe *rgbFg* in [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) im Windows SDK.

*nStyle*<br/>
Flag, das den Zeichnungsstil angibt. Siehe *fStyle* in [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die Funktion verwendet den angegebenen Zeichnungsstil und fügt das Bild mit der angegebenen Farbe überein.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

## <a name="cimagelistdrawindirect"></a><a name="drawindirect"></a>CImageList::DrawIndirect

Rufen Sie diese Memberfunktion auf, um ein Bild aus einer Bildliste zu zeichnen.

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
Ein Zeiger auf eine [IMAGELISTDRAWPARAMS-Struktur,](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) die Informationen zum Zeichnungsvorgang enthält.

*pDC*<br/>
Ein Zeiger auf den Zielgerätekontext. Sie müssen dieses [CDC-Objekt](../../mfc/reference/cdc-class.md) löschen, wenn Sie damit fertig sind.

*nImage*<br/>
Der nullbasierte Index des zu zeichnenden Bildes.

*Pt*<br/>
Eine [POINT](/windows/win32/api/windef/ns-windef-point) POINT-Struktur, die die x- und y-Koordinaten enthält, in denen das Bild gezeichnet wird.

*Sz*<br/>
Eine [SIZE](/windows/win32/api/windef/ns-windef-size) SIZE-Struktur, die die Größe des zu zeichnenden Bildes angibt.

*ptOrigin*<br/>
Eine [POINT](/windows/win32/api/windef/ns-windef-point) POINT-Struktur, die die x- und y-Koordinaten enthält, die die obere linke Ecke des Zeichnungsvorgangs in Bezug auf das Bild selbst angibt. Pixel des Bildes, die sich links von der x-Koordinate und oberhalb der y-Koordinate befinden, werden nicht gezeichnet.

*fStyle*<br/>
Flag, das den Zeichnungsstil und optional das Überlagerungsbild angibt. Weitere Informationen zum Überlagerungsbild finden Sie im Abschnitt "Bemerkungen". Die MFC-Standardimplementierung ILD_NORMAL zeichnet das Bild mit der Hintergrundfarbe für die Bildliste. Wenn die Hintergrundfarbe der CLR_NONE Wert ist, wird das Bild transparent mit einer Maske gezeichnet.

Andere mögliche Stile werden unter dem *fStyle-Member* der [IMAGELISTDRAWPARAMS-Struktur](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) beschrieben.

*dwRop*<br/>
Wert, der einen Raster-Vorgangscode angibt. Diese Codes definieren, wie die Farbdaten für das Quellrechteck mit den Farbdaten für das Zielrechteck kombiniert werden, um die endgültige Farbe zu erreichen. Die Standardimplementierung von MFC, SRCCOPY, kopiert das Quellrechteck direkt in das Zielrechteck. Dieser Parameter wird ignoriert, wenn der *fStyle-Parameter* das ILD_ROP-Flag nicht enthält.

Andere mögliche Werte werden unter dem *dwRop-Member* der [IMAGELISTDRAWPARAMS-Struktur](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) beschrieben.

*rgbBack*<br/>
Die Hintergrundfarbe des Bildes CLR_DEFAULT standardmäßig. Dieser Parameter kann ein anwendungsdefinierter RGB-Wert oder einer der folgenden Werte sein:

|Wert|Bedeutung|
|-----------|-------------|
|CLR_DEFAULT|Standard-Hintergrundfarbe. Das Bild wird mit der Hintergrundfarbe der Bildliste gezeichnet.|
|CLR_NONE|Keine Hintergrundfarbe. Das Bild wird transparent gezeichnet.|

*rgbFore*<br/>
Bild Vordergrundfarbe, standardmäßig CLR_DEFAULT. Dieser Parameter kann ein anwendungsdefinierter RGB-Wert oder einer der folgenden Werte sein:

|Wert|Bedeutung|
|-----------|-------------|
|CLR_DEFAULT|Standard-Vordergrundfarbe. Das Bild wird mit der System-Hervorhebungsfarbe als Vordergrundfarbe gezeichnet.|
|CLR_NONE|Keine Mischfarbe. Das Bild wird mit der Farbe des Zielgerätekontexts vermischt.|

Dieser Parameter wird nur verwendet, wenn *fStyle* das ILD_BLEND25- oder ILD_BLEND50-Flag enthält.

*fState*<br/>
Flag, das den Zeichnungszustand angibt. Dieses Element kann eine oder mehrere Bildlistenstatusflags enthalten.

*Frame*<br/>
Beeinflusst das Verhalten von gesättigten und Alpha-Blending-Effekten.

Bei Verwendung mit ILS_SATURATE enthält dieses Element den Wert, der jeder Farbkomponente des RGB-Triplets für jedes Pixel im Symbol hinzugefügt wird.

Bei Verwendung mit ILS_APLHA enthält dieses Element den Wert für den Alphakanal. Dieser Wert kann von 0 bis 255 sein, wobei 0 vollständig transparent und 255 vollständig undurchsichtig ist.

*crEffect*<br/>
Ein [COLORREF-Wert,](/windows/win32/gdi/colorref) der für Glüh- und Schatteneffekte verwendet wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn das Bild erfolgreich gezeichnet wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie die erste Version, wenn Sie die Win32-Struktur selbst ausfüllen möchten. Verwenden Sie die zweite Version, wenn Sie eines oder mehrere der Standardargumente von MFC nutzen oder die Verwaltung der Struktur vermeiden möchten.

Ein Überlagerungsbild ist ein Bild, das über dem primären Bild gezeichnet wird und in dieser Memberfunktion durch den Parameter *nImage* angegeben wird. Zeichnen Sie eine Überlagerungsmaske, indem Sie die [Memberfunktion Zeichnen](#draw) mit dem einbasierten Index der Überlagerungsmaske verwenden, die mit dem Makro [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) angegeben wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

## <a name="cimagelistenddrag"></a><a name="enddrag"></a>CImageList::EndDrag

Rufen Sie diese Funktion auf, um einen Ziehvorgang zu beenden.

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>Bemerkungen

Um einen Ziehvorgang zu `BeginDrag` starten, verwenden Sie die Memberfunktion.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

## <a name="cimagelistextracticon"></a><a name="extracticon"></a>CImageList::ExtractIcon

Rufen Sie diese Funktion auf, um ein Symbol basierend auf einem Bild und der zugehörigen Maske in einer Bildliste zu erstellen.

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>Parameter

*nImage*<br/>
Nullbasierter Index des Bildes.

### <a name="return-value"></a>Rückgabewert

Handle des Symbols, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Diese Methode basiert auf dem Verhalten des [ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) Makros, um das Symbol zu erstellen. Weitere Informationen [ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon) zur Symbolerstellung und -bereinigung finden Sie im ImageList_ExtractIcon-Makro.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

## <a name="cimagelistfromhandle"></a><a name="fromhandle"></a>CImageList::FromHandle

Gibt einen Zeiger `CImageList` auf ein Objekt zurück, wenn einer Bildliste ein Handle gegeben wird.

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parameter

*hImageList*<br/>
Gibt die Bildliste an.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CImageList` ein Objekt, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Wenn `CImageList` a nicht bereits mit dem `CImageList` Handle verbunden ist, wird ein temporäres Objekt erstellt und angefügt. Dieses `CImageList` temporäre Objekt ist nur gültig, bis die Anwendung das nächste Mal Leerlaufzeit in ihrer Ereignisschleife hat, zu diesem Zeitpunkt alle temporären Objekte gelöscht werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

## <a name="cimagelistfromhandlepermanent"></a><a name="fromhandlepermanent"></a>CImageList::FromHandlePermanent

Gibt einen Zeiger `CImageList` auf ein Objekt zurück, wenn einer Bildliste ein Handle gegeben wird.

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>Parameter

*hImageList*<br/>
Gibt die Bildliste an.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CImageList` ein Objekt, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Wenn `CImageList` ein Objekt nicht an das Handle angefügt ist, wird NULL zurückgegeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

## <a name="cimagelistgetbkcolor"></a><a name="getbkcolor"></a>CImageList::GetBkColor

Rufen Sie diese Funktion auf, um die aktuelle Hintergrundfarbe für eine Bildliste abzurufen.

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>Rückgabewert

Der RGB-Farbwert `CImageList` der Objekthintergrundfarbe.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CImageList::SetBkColor](#setbkcolor).

## <a name="cimagelistgetdragimage"></a><a name="getdragimage"></a>CImageList::GetDragImage

Ruft die temporäre Bildliste ab, die zum Ziehen verwendet wird.

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>Parameter

*lpPoint*<br/>
Adresse einer [POINT](/windows/win32/api/windef/ns-windef-point) POINT-Struktur, die die aktuelle Ziehposition empfängt.

*lpPointHotSpot*<br/>
Adresse einer `POINT` Struktur, die den Versatz des Ziehbildes relativ zur Ziehposition empfängt.

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, ein Zeiger auf die temporäre Bildliste, die zum Ziehen verwendet wird; andernfalls NULL.

## <a name="cimagelistgetimagecount"></a><a name="getimagecount"></a>CImageList::GetImageCount

Rufen Sie diese Funktion auf, um die Anzahl der Bilder in einer Bildliste abzurufen.

```
int GetImageCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Bilder.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CImageList::ExtractIcon](#extracticon).

## <a name="cimagelistgetimageinfo"></a><a name="getimageinfo"></a>CImageList::GetImageInfo

Rufen Sie diese Funktion auf, um Informationen zu einem Bild abzurufen.

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>Parameter

*nImage*<br/>
Nullbasierter Index des Bildes.

*pImageInfo*<br/>
Zeiger auf eine [IMAGEINFO-Struktur,](/windows/win32/api/commctrl/ns-commctrl-imageinfo) die Informationen über das Bild empfängt. Die Informationen in dieser Struktur können verwendet werden, um die Bitmaps für das Bild direkt zu bearbeiten.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die `IMAGEINFO` Struktur enthält Informationen zu einem Bild in einer Bildliste.

## <a name="cimagelistgetsafehandle"></a><a name="getsafehandle"></a>CImageList::GetSafeHandle

Rufen Sie diese `m_hImageList` Funktion auf, um das Datenelement abzurufen.

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Handle zur angehängten Bildliste; ANDERNFALLS NULL, wenn kein Objekt angefügt ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

## <a name="cimagelistm_himagelist"></a><a name="m_himagelist"></a>CImageList::m_hImageList

Ein Handle der Bildliste, das an dieses Objekt angefügt ist.

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>Bemerkungen

Das `m_hImageList` Datenelement ist eine öffentliche Variable vom Typ HIMAGELIST.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

## <a name="cimagelistoperator-himagelist"></a><a name="operator_himagelist"></a>CImageList::operator HIMAGELIST

Verwenden Sie diesen Operator, um `CImageList` das angefügte Handle des Objekts abzubekommen.

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, ein Handle für die `CImageList` Bildliste, die durch das Objekt dargestellt wird; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Dieser Operator ist ein Gießoperator, der die direkte Verwendung eines HIMAGELIST-Objekts unterstützt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

## <a name="cimagelistread"></a><a name="read"></a>CImageList::Lesen

Rufen Sie diese Funktion auf, um eine Bildliste aus einem Archiv zu lesen.

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>Parameter

*Parchive*<br/>
Ein Zeiger auf `CArchive` ein Objekt, von dem die Bildliste gelesen werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

## <a name="cimagelistremove"></a><a name="remove"></a>CImageList::Entfernen

Rufen Sie diese Funktion auf, um ein Bild aus einem Bildlistenobjekt zu entfernen.

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>Parameter

*nImage*<br/>
Nullbasierter Index des zu entfernenden Bildes.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Alle Elemente, die *nImage folgen,* bewegen sich nun um eine Position nach unten. Wenn z. B. eine Bildliste zwei Elemente enthält, führt das Löschen des ersten Elements dazu, dass sich das verbleibende Element jetzt an der ersten Position befindet. *nImage*=0 für das Element an der ersten Position.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

## <a name="cimagelistreplace"></a><a name="replace"></a>CImageList::Ersetzen

Rufen Sie diese Funktion auf, um ein Bild in einer Bildliste durch ein neues Bild zu ersetzen.

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

*nImage*<br/>
Nullbasierter Index des zu ersetzenden Bildes.

*pbmImage*<br/>
Ein Zeiger auf die Bitmap, die das Bild enthält.

*pbmMaske*<br/>
Ein Zeiger auf die Bitmap, die die Maske enthält. Wenn keine Maske mit der Bildliste verwendet wird, wird dieser Parameter ignoriert.

*hIcon*<br/>
Ein Handle für das Symbol, das die Bitmap und Maske für das neue Bild enthält.

### <a name="return-value"></a>Rückgabewert

Die Version, die BOOL zurückgibt, gibt bei Erfolg einen Wert ungleich Null zurück. andernfalls 0.

Die Version, **die int** zurückgibt, gibt den nullbasierten Index des Bildes zurück, wenn dies erfolgreich ist. ansonsten - 1.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Memberfunktion auf, nachdem Sie [SetImageCount](#setimagecount) aufgerufen haben, um den Platzhalterbildindexnummern die neuen, gültigen Bilder zuzuweisen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CImageList::SetImageCount](#setimagecount).

## <a name="cimagelistsetbkcolor"></a><a name="setbkcolor"></a>CImageList::SetBkColor

Rufen Sie diese Funktion auf, um die Hintergrundfarbe für eine Bildliste festzulegen.

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>Parameter

*Cr*<br/>
Hintergrundfarbe, die festgelegt werden soll. Es kann CLR_NONE sein. In diesem Fall werden Bilder transparent mit der Maske gezeichnet.

### <a name="return-value"></a>Rückgabewert

Die vorherige Hintergrundfarbe, wenn erfolgreich; ansonsten CLR_NONE.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

## <a name="cimagelistsetdragcursorimage"></a><a name="setdragcursorimage"></a>CImageList::SetDragCursorImage

Erstellt ein neues Ziehbild, indem das angegebene Bild (in der Regel ein Mauscursorbild) mit dem aktuellen Ziehbild kombiniert wird.

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>Parameter

*nDrag*<br/>
Index des neuen Bildes, das mit dem Ziehbild kombiniert werden soll.

*ptHotSpot*<br/>
Position des Hotspots innerhalb des neuen Bildes.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Da die Ziehfunktionen das neue Bild während eines Ziehvorgangs verwenden, sollten Sie die `CImageList::SetDragCursorImage`Windows [ShowCursor-Funktion](/windows/win32/api/winuser/nf-winuser-showcursor) verwenden, um den tatsächlichen Mauszeiger nach dem Aufruf auszublenden. Andernfalls scheint das System zwei Mauszeiger für die Dauer des Ziehvorgangs zu haben.

## <a name="cimagelistsetimagecount"></a><a name="setimagecount"></a>CImageList::SetImageCount

Rufen Sie diese Memberfunktion auf, `CImageList` um die Anzahl der Bilder in einem Objekt zurückzusetzen.

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>Parameter

*uNewCount*<br/>
Der Wert, der die neue Gesamtzahl der Bilder in der Bildliste angibt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0, wenn erfolgreich, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Memberfunktion aufrufen, um die Anzahl der Bilder in der Bildliste zu erhöhen, rufen Sie für jedes zusätzliche Bild [Ersetzen](#replace) auf, um die neuen Indizes gültigen Bildern zuzuweisen. Wenn Sie die Indizes nicht gültigen Bildern zuweisen, sind Zeichnungsvorgänge, die die neuen Bilder erstellen, unvorhersehbar.

Wenn Sie die Größe einer Bildliste mit dieser Funktion verringern, werden die abgeschnittenen Bilder freigegeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

## <a name="cimagelistsetoverlayimage"></a><a name="setoverlayimage"></a>CImageList::SetOverlayImage

Rufen Sie diese Funktion auf, um den nullbasierten Index eines Bildes zur Liste der Bilder hinzuzufügen, die als Überlagerungsmasken verwendet werden sollen.

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>Parameter

*nImage*<br/>
Nullbasierter Index des Bildes, der als Überlagerungsmaske verwendet werden soll.

*nOverlay*<br/>
Ein basierter Index der Überlagerungsmaske.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Der Liste können bis zu vier Indizes hinzugefügt werden.

Eine Überlagerungsmaske ist ein Bild, das transparent über ein anderes Bild gezeichnet wird. Zeichnen Sie eine Überlagerungsmaske über einem Bild, indem Sie die [Memberfunktion CImageList::Draw](#draw) mit dem einbasierten Index der Overlay-Maske verwenden, die mit dem Makro INDEXTOOVERLAYMASK angegeben wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

## <a name="cimagelistwrite"></a><a name="write"></a>CImageList::Schreiben

Rufen Sie diese Funktion auf, um ein Bildlistenobjekt in ein Archiv zu schreiben.

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>Parameter

*Parchive*<br/>
Ein Zeiger auf `CArchive` ein Objekt, in dem die Bildliste gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CListCtrl-Klasse](../../mfc/reference/clistctrl-class.md)<br/>
[CTabCtrl-Klasse](../../mfc/reference/ctabctrl-class.md)

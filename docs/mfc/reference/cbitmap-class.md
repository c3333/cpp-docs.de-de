---
title: CBitmap-Klasse
ms.date: 11/04/2016
f1_keywords:
- CBitmap
- AFXWIN/CBitmap
- AFXWIN/CBitmap::CBitmap
- AFXWIN/CBitmap::CreateBitmap
- AFXWIN/CBitmap::CreateBitmapIndirect
- AFXWIN/CBitmap::CreateCompatibleBitmap
- AFXWIN/CBitmap::CreateDiscardableBitmap
- AFXWIN/CBitmap::FromHandle
- AFXWIN/CBitmap::GetBitmap
- AFXWIN/CBitmap::GetBitmapBits
- AFXWIN/CBitmap::GetBitmapDimension
- AFXWIN/CBitmap::LoadBitmap
- AFXWIN/CBitmap::LoadMappedBitmap
- AFXWIN/CBitmap::LoadOEMBitmap
- AFXWIN/CBitmap::SetBitmapBits
- AFXWIN/CBitmap::SetBitmapDimension
helpviewer_keywords:
- CBitmap [MFC], CBitmap
- CBitmap [MFC], CreateBitmap
- CBitmap [MFC], CreateBitmapIndirect
- CBitmap [MFC], CreateCompatibleBitmap
- CBitmap [MFC], CreateDiscardableBitmap
- CBitmap [MFC], FromHandle
- CBitmap [MFC], GetBitmap
- CBitmap [MFC], GetBitmapBits
- CBitmap [MFC], GetBitmapDimension
- CBitmap [MFC], LoadBitmap
- CBitmap [MFC], LoadMappedBitmap
- CBitmap [MFC], LoadOEMBitmap
- CBitmap [MFC], SetBitmapBits
- CBitmap [MFC], SetBitmapDimension
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
ms.openlocfilehash: 9a33a6e1bea601422e043d7f2a80029c72d97e50
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352743"
---
# <a name="cbitmap-class"></a>CBitmap-Klasse

Kapselt eine Bitmap der Windows GDI (Graphics Device Interface) und stellt Memberfunktionen zur Bearbeitung der Bitmap bereit.

## <a name="syntax"></a>Syntax

```
class CBitmap : public CGdiObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBitmap::CBitmap](#cbitmap)|Erstellt ein `CBitmap`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBitmap::CreateBitmap](#createbitmap)|Initialisiert das Objekt mit einer geräteabhängigen Speicherbitmap mit einer angegebenen Breite, Höhe und Bitmuster.|
|[CBitmap::CreateBitmapIndirect](#createbitmapindirect)|Initialisiert das Objekt mit einer Bitmap mit der In-Struktur angegebenen Breite, `BITMAP` Höhe und Bitmuster (falls angegeben).|
|[CBitmap::CreateCompatibleBitmap](#createcompatiblebitmap)|Initialisiert das Objekt mit einer Bitmap, sodass es mit einem angegebenen Gerät kompatibel ist.|
|[CBitmap::CreateDiscardableBitmap](#creatediscardablebitmap)|Initialisiert das Objekt mit einer verwerfbaren Bitmap, die mit einem angegebenen Gerät kompatibel ist.|
|[CBitmap::FromHandle](#fromhandle)|Gibt einen Zeiger `CBitmap` auf ein Objekt zurück, `HBITMAP` wenn einer Windows-Bitmap ein Handle gegeben wird.|
|[CBitmap::GetBitmap](#getbitmap)|Füllt eine `BITMAP` Struktur mit Informationen zur Bitmap.|
|[CBitmap::GetBitmapBits](#getbitmapbits)|Kopiert die Bits der angegebenen Bitmap in den angegebenen Puffer.|
|[CBitmap::GetBitmapDimension](#getbitmapdimension)|Gibt die Breite und Höhe der Bitmap zurück. Es wird davon ausgegangen, dass die Höhe und Breite zuvor von der [SetBitmapDimension-Memberfunktion](#setbitmapdimension) festgelegt wurden.|
|[CBitmap::LoadBitmap](#loadbitmap)|Initialisiert das Objekt, indem eine benannte Bitmapressource aus der ausführbaren Datei der Anwendung geladen und die Bitmap an das Objekt angefügt wird.|
|[CBitmap::LoadMappedBitmap](#loadmappedbitmap)|Lädt eine Bitmap und ordnet den aktuellen Systemfarben Farben zu.|
|[CBitmap::LoadOEMBitmap](#loadoembitmap)|Initialisiert das Objekt, indem eine vordefinierte Windows-Bitmap geladen und die Bitmap an das Objekt angefügt wird.|
|[CBitmap::SetBitmapBits](#setbitmapbits)|Legt die Bits einer Bitmap auf die angegebenen Bitwerte fest.|
|[CBitmap::SetBitmapDimension](#setbitmapdimension)|Weist einer Bitmap in 0,1-Millimeter-Einheiten eine Breite und Höhe zu.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBitmap::operator HBITMAP](#operator_hbitmap)|Gibt das Windows-Handle `CBitmap` zurück, das an das Objekt angefügt ist.|

## <a name="remarks"></a>Bemerkungen

Um ein `CBitmap` Objekt zu verwenden, erstellen Sie das Objekt, fügen Sie ihm mit einer der Initialisierungsmemberfunktionen ein Bitmap-Handle an, und rufen Sie dann die Memberfunktionen des Objekts auf.

Weitere Informationen zur Verwendung `CBitmap`von Grafikobjekten wie finden Sie unter [Grafikobjekte](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cbitmapcbitmap"></a><a name="cbitmap"></a>CBitmap::CBitmap

Erstellt ein `CBitmap`-Objekt.

```
CBitmap();
```

### <a name="remarks"></a>Bemerkungen

Das resultierende Objekt muss mit einer der Initialisierungsmemberfunktionen initialisiert werden.

## <a name="cbitmapcreatebitmap"></a><a name="createbitmap"></a>CBitmap::CreateBitmap

Initialisiert eine geräteabhängige Speicherbitmap, die die angegebene Breite, Höhe und das angegebene Bitmuster aufweist.

```
BOOL CreateBitmap(
    int nWidth,
    int nHeight,
    UINT nPlanes,
    UINT nBitcount,
    const void* lpBits);
```

### <a name="parameters"></a>Parameter

*nWidth*<br/>
Gibt die Breite der Bitmap (in Pixeln) an.

*nHeight*<br/>
Gibt die Höhe der Bitmap (in Pixeln) an.

*nPlanes*<br/>
Gibt die Anzahl von Farbebenen in der Bitmap an.

*nBitcount*<br/>
Gibt die Anzahl der Farbbits pro Anzeigepixel an.

*lpBits*<br/>
Zeigt auf ein Array von Bytes, das die ursprünglichen Bitwerte der Bitmap enthält. Ist dieser Wert NULL, bleibt die neue Bitmap nicht initialisiert.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Für eine Farbbitmap sollte entweder der Parameter *nPlanes* oder *nBitcount* auf 1 gesetzt werden. Wenn beide Parameter auf 1 festgelegt sind, erstellt `CreateBitmap` eine monochrome Bitmap.

Obwohl eine Bitmap nicht direkt für ein Anzeigegerät ausgewählt werden kann, kann sie als aktuelle Bitmap für einen „Speichergerätekontext“ mithilfe von [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) ausgewählt und mithilfe der [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) -Funktion auf einen beliebigen kompatiblen Gerätekontext kopiert werden.

Wenn Sie mit dem `CBitmap` -Objekt fertig sind, das von der `CreateBitmap` -Funktion erstellt wurde, wählen Sie zunächst die Bitmap im Gerätekontext aus, und löschen Sie dann das `CBitmap` -Objekt.

Weitere Informationen finden Sie in `bmBits` der `BITMAP` Beschreibung des Felds in der Struktur. Die [BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap) -Struktur wird unter der [CBitmap::CreateBitmapIndirect](#createbitmapindirect) -Memberfunktion beschrieben.

## <a name="cbitmapcreatebitmapindirect"></a><a name="createbitmapindirect"></a>CBitmap::CreateBitmapIndirect

Initialisiert eine Bitmap mit der Breite, Höhe und dem Bitmuster (falls angegeben) in der Struktur, auf die von *lpBitmap*verwiesen wird.

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>Parameter

*lpBitmap*<br/>
Verweist auf eine [BITMAP-Struktur,](/windows/win32/api/wingdi/ns-wingdi-bitmap) die Informationen zur Bitmap enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Obwohl eine Bitmap nicht direkt für ein Anzeigegerät ausgewählt werden kann, kann sie mithilfe von [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) als aktuelle Bitmap für einen Speichergerätekontext ausgewählt und mithilfe der [Funktion CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) oder [CDC::StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) in einen kompatiblen Gerätekontext kopiert werden. (Die [CDC::PatBlt-Funktion](../../mfc/reference/cdc-class.md#patblt) kann die Bitmap für den aktuellen Pinsel direkt in den Displaygerätekontext kopieren.)

Wenn `BITMAP` die Struktur, auf die der Parameter *lpBitmap* zeigt, mithilfe der `GetObject` Funktion ausgefüllt wurde, werden die Bits der Bitmap nicht angegeben, und die Bitmap wird nicht initialisiert. Zum Initialisieren der Bitmap kann eine Anwendung eine Funktion wie [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) oder [SetDIBits](/windows/win32/api/wingdi/nf-wingdi-setdibits) verwenden, um `CGdiObject::GetObject` die Bits aus `CreateBitmapIndirect`der Bitmap zu kopieren, die durch den ersten Parameter der Bitmap identifiziert wurde, die von erstellt wurde.

Wenn Sie mit `CBitmap` dem `CreateBitmapIndirect` mit der Funktion erstellten Objekt fertig sind, `CBitmap` wählen Sie zuerst die Bitmap aus dem Gerätekontext aus, und löschen Sie dann das Objekt.

## <a name="cbitmapcreatecompatiblebitmap"></a><a name="createcompatiblebitmap"></a>CBitmap::CreateCompatibleBitmap

Initialisiert eine Bitmap, die mit dem von *pDC*angegebenen Gerät kompatibel ist.

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Gibt den Gerätekontext an.

*nWidth*<br/>
Gibt die Breite der Bitmap (in Pixeln) an.

*nHeight*<br/>
Gibt die Höhe der Bitmap (in Pixeln) an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die Bitmap hat die gleiche Anzahl von Farbebenen oder das gleiche Bits-pro-Pixel-Format wie der angegebene Gerätekontext. Sie kann als aktuelle Bitmap für jedes Speichergerät ausgewählt werden, das mit dem von *pDC*angegebenen kompatibel ist.

Wenn *pDC* ein Speichergerätekontext ist, hat die zurückgegebene Bitmap das gleiche Format wie die aktuell ausgewählte Bitmap in diesem Gerätekontext. Ein "Speichergerätekontext" ist ein Speicherblock, der eine Anzeigefläche darstellt. Es kann verwendet werden, um Bilder im Speicher vorzubereiten, bevor sie auf die tatsächliche Anzeigefläche des kompatiblen Geräts kopiert werden.

Wenn ein Speichergerätekontext erstellt wird, wählt GDI automatisch eine monochrome Stockbitmap dafür aus.

Da für einen Farbspeichergerätekontext entweder Farb- oder monochrome Bitmaps ausgewählt `CreateCompatibleBitmap` sein können, ist das Format der von der Funktion zurückgegebenen Bitmap nicht immer identisch. Das Format einer kompatiblen Bitmap für einen Nichtspeichergerätekontext ist jedoch immer im Format des Geräts.

Wenn Sie mit `CBitmap` dem mit `CreateCompatibleBitmap` der Funktion erstellten Objekt fertig sind, wählen `CBitmap` Sie zuerst die Bitmap aus dem Gerätekontext aus, und löschen Sie dann das Objekt.

## <a name="cbitmapcreatediscardablebitmap"></a><a name="creatediscardablebitmap"></a>CBitmap::CreateDiscardableBitmap

Initialisiert eine verwerfbare Bitmap, die mit dem von *pDC*identifizierten Gerätekontext kompatibel ist.

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Gibt einen Gerätekontext an.

*nWidth*<br/>
Gibt die Breite (in Bits) der Bitmap an.

*nHeight*<br/>
Gibt die Höhe (in Bits) der Bitmap an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die Bitmap hat die gleiche Anzahl von Farbebenen oder das gleiche Bits-pro-Pixel-Format wie der angegebene Gerätekontext. Eine Anwendung kann diese Bitmap als aktuelle Bitmap für ein Speichergerät auswählen, das mit der von *pDC*angegebenen kompatibel ist.

Windows kann eine von dieser Funktion erstellte Bitmap nur verwerfen, wenn eine Anwendung sie nicht in einem Anzeigekontext ausgewählt hat. Wenn Windows die Bitmap verwirft, wenn sie nicht ausgewählt ist, und die Anwendung später versucht, sie auszuwählen, gibt die [CDC::SelectObject-Funktion](../../mfc/reference/cdc-class.md#selectobject) NULL zurück.

Wenn Sie mit `CBitmap` dem mit `CreateDiscardableBitmap` der Funktion erstellten Objekt fertig sind, wählen `CBitmap` Sie zuerst die Bitmap aus dem Gerätekontext aus, und löschen Sie dann das Objekt.

## <a name="cbitmapfromhandle"></a><a name="fromhandle"></a>CBitmap::FromHandle

Gibt einen Zeiger `CBitmap` auf ein Objekt zurück, wenn einer Windows GDI-Bitmap ein Handle gegeben wird.

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parameter

*hBitmap*<br/>
Gibt eine Windows GDI-Bitmap an.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CBitmap` ein Objekt, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Wenn `CBitmap` ein Objekt noch nicht an das `CBitmap` Handle angefügt ist, wird ein temporäres Objekt erstellt und angefügt. Dieses `CBitmap` temporäre Objekt ist nur gültig, bis die Anwendung das nächste Mal Leerlaufzeit in ihrer Ereignisschleife hat, zu diesem Zeitpunkt alle temporären Grafikobjekte gelöscht werden. Eine andere Möglichkeit, dies zu sagen, ist, dass das temporäre Objekt nur während der Verarbeitung einer Fensternachricht gültig ist.

## <a name="cbitmapgetbitmap"></a><a name="getbitmap"></a>CBitmap::GetBitmap

Ruft Bildeigenschaften für die angefügte Bitmap ab.

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>Parameter

*pBitMap*<br/>
Zeiger auf eine [BITMAP-Struktur,](/windows/win32/api/wingdi/ns-wingdi-bitmap) die die Bildeigenschaften empfängt. Dieser Parameter darf nicht NULL sein.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Methode erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

## <a name="cbitmapgetbitmapbits"></a><a name="getbitmapbits"></a>CBitmap::GetBitmapBits

Kopiert das Bitmuster der angehängten Bitmap in den angegebenen Puffer.

```
DWORD GetBitmapBits(
    DWORD dwCount,
    LPVOID lpBits) const;
```

### <a name="parameters"></a>Parameter

*dwCount*<br/>
Die Anzahl von Bytes, die in den Puffer kopiert werden sollen.

*lpBits*<br/>
Zeiger auf den Puffer, der die Bitmap empfängt.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Bytes, die in den Puffer kopiert wurden, wenn die Methode erfolgreich war. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie [CBitmap::GetBitmap,](#getbitmap) um die erforderliche Puffergröße zu bestimmen.

## <a name="cbitmapgetbitmapdimension"></a><a name="getbitmapdimension"></a>CBitmap::GetBitmapDimension

Gibt die Breite und Höhe der Bitmap zurück.

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>Rückgabewert

Die Breite und Höhe der Bitmap, gemessen in 0,1-Millimeter-Einheiten. Die Höhe befindet `cy` sich `CSize` im Element des Objekts, und die Breite befindet sich im `cx` Element. Wenn die Bitmapbreite und -höhe `SetBitmapDimension`nicht mithilfe von festgelegt wurden, ist der Rückgabewert 0.

### <a name="remarks"></a>Bemerkungen

Es wird davon ausgegangen, dass die Höhe und Breite zuvor mithilfe der [Elementfunktion SetBitmapDimension](#setbitmapdimension) festgelegt wurden.

## <a name="cbitmaploadbitmap"></a><a name="loadbitmap"></a>CBitmap::LoadBitmap

Lädt die Bitmapressource, die von *lpszResourceName* benannt oder durch die ID-Nummer in *nIDResource* identifiziert wird, aus der ausführbaren Datei der Anwendung.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parameter

*lpszResourceName*<br/>
Verweist auf eine null-terminierte Zeichenfolge, die den Namen der Bitmapressource enthält.

*nIDResource*<br/>
Gibt die Ressourcen-ID-Nummer der Bitmapressource an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Die geladene Bitmap `CBitmap` wird an das Objekt angefügt.

Wenn die von *lpszResourceName* identifizierte Bitmap nicht vorhanden ist oder nicht genügend Arbeitsspeicher zum Laden der Bitmap vorhanden ist, gibt die Funktion 0 zurück.

Sie können die Funktion [CGdiObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) verwenden, `LoadBitmap` um die `CBitmap` von der Funktion geladene Bitmap zu löschen, oder der Destruktor löscht das Objekt für Sie.

> [!CAUTION]
> Stellen Sie vor dem Löschen des Objekts sicher, dass es nicht in einem Gerätekontext ausgewählt ist.

Die folgenden Bitmaps wurden zu Windows-Versionen 3.1 und höher hinzugefügt:

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

Diese Bitmaps werden in Gerätetreibern für Windows-Versionen 3.0 und früher nicht gefunden. Eine vollständige Liste der Bitmaps und eine Anzeige ihrer Darstellung finden Sie im Windows SDK.

## <a name="cbitmaploadmappedbitmap"></a><a name="loadmappedbitmap"></a>CBitmap::LoadMappedBitmap

Rufen Sie diese Memberfunktion auf, um eine Bitmap zu laden und die Farben den aktuellen Systemfarben zuzuordnen.

```
BOOL LoadMappedBitmap(
    UINT nIDBitmap,
    UINT nFlags = 0,
    LPCOLORMAP lpColorMap = NULL,
    int nMapSize = 0);
```

### <a name="parameters"></a>Parameter

*nIDBitmap*<br/>
Die ID der Bitmapressource.

*nFlags*<br/>
Ein Flag für eine Bitmap. Kann Null oder CMB_MASKED sein.

*lpColorMap*<br/>
Ein Zeiger auf `COLORMAP` eine Struktur, die die Farbinformationen enthält, die zum Zuordnen der Bitmaps erforderlich sind. Wenn dieser Parameter NULL ist, verwendet die Funktion die Standardfarbzuordnung.

*nMapSize*<br/>
Die Anzahl der Farbkarten, auf die *lpColorMap*zeigt.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Standardmäßig werden `LoadMappedBitmap` Farben zugeordnet, die häufig in Schaltflächenglyphen verwendet werden.

Informationen zum Erstellen einer zugeordneten Bitmap finden Sie in der Windows-Funktion [CreateMappedBitmap](https://go.microsoft.com/fwlink/p/?linkid=230562) und in der [COLORMAP-Struktur](/windows/win32/api/commctrl/ns-commctrl-colormap) im Windows SDK.

## <a name="cbitmaploadoembitmap"></a><a name="loadoembitmap"></a>CBitmap::LoadOEMBitmap

Lädt eine vordefinierte Bitmap, die von Windows verwendet wird.

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>Parameter

*nIDBitmap*<br/>
ID-Nummer der vordefinierten Windows-Bitmap. Die möglichen Werte sind unten in WINDOWS aufgeführt. H:

|||
|-|-|
|OBM_BTNCORNERS|OBM_OLD_RESTORE|
|OBM_BTSIZE|OBM_OLD_RGARROW|
|OBM_CHECK|OBM_OLD_UPARROW|
|OBM_CHECKBOXES|OBM_OLD_ZOOM|
|OBM_CLOSE|OBM_REDUCE|
|OBM_COMBO|OBM_REDUCED|
|OBM_DNARROW|OBM_RESTORE|
|OBM_DNARROWD|OBM_RESTORED|
|OBM_DNARROWI|OBM_RGARROW|
|OBM_LFARROW|OBM_RGARROWD|
|OBM_LFARROWD|OBM_RGARROWI|
|OBM_LFARROWI|OBM_SIZE|
|OBM_MNARROW|OBM_UPARROW|
|OBM_OLD_CLOSE|OBM_UPARROWD|
|OBM_OLD_DNARROW|OBM_UPARROW|
|OBM_OLD_LFARROW|OBM_ZOOM|
|OBM_OLD_REDUCE|OBM_ZOOMD|

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Bitmapnamen, die mit OBM_OLD beginnen, stellen Bitmaps dar, die von Windows-Versionen vor 3.0 verwendet werden.

Beachten Sie, dass die konstante OEMRESOURCE vor dem Einschließen von WINDOWS definiert werden muss. H, um eine der **OBM_** Konstanten zu verwenden.

## <a name="cbitmapoperator-hbitmap"></a><a name="operator_hbitmap"></a>CBitmap::operator HBITMAP

Verwenden Sie diesen Operator, um das `CBitmap` angefügte Windows GDI-Handle des Objekts abzubekommen.

```
operator HBITMAP() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, ein Handle für das Windows `CBitmap` GDI-Objekt, das durch das Objekt dargestellt wird; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Dieser Operator ist ein Gießoperator, der `HBITMAP` die direkte Verwendung eines Objekts unterstützt.

Weitere Informationen zur Verwendung von Grafikobjekten finden Sie unter [Grafikobjekte](/windows/win32/gdi/graphic-objects) im Windows SDK.

## <a name="cbitmapsetbitmapbits"></a><a name="setbitmapbits"></a>CBitmap::SetBitmapBits

Legt die Bits einer Bitmap auf die Bitwerte fest, die von *lpBits*angegeben werden.

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>Parameter

*dwCount*<br/>
Gibt die Anzahl der Bytes an, auf die von *lpBits*verwiesen wird.

*lpBits*<br/>
Zeigt auf das BYTE-Array, das die `CBitmap` Pixelwerte enthält, die in das Objekt kopiert werden sollen. Damit die Bitmap ihr Bild korrekt rendern kann, sollten die Werte so formatiert werden, dass sie den Höhen-, Breiten- und Farbtiefenwerten entsprechen, die beim Erstellen der CBitmap-Instanz angegeben wurden. Weitere Informationen finden Sie unter [CBitmap::CreateBitmap](#createbitmap).

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Bytes, die beim Festlegen der Bitmapbits verwendet werden. 0, wenn die Funktion fehlschlägt.

## <a name="cbitmapsetbitmapdimension"></a><a name="setbitmapdimension"></a>CBitmap::SetBitmapDimension

Weist einer Bitmap in 0,1-Millimeter-Einheiten eine Breite und Höhe zu.

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parameter

*nWidth*<br/>
Gibt die Breite der Bitmap (in 0,1-Millimeter-Einheiten) an.

*nHeight*<br/>
Gibt die Höhe der Bitmap (in 0,1-Millimeter-Einheiten) an.

### <a name="return-value"></a>Rückgabewert

Die vorherigen Bitmap-Dimensionen. Height befindet `cy` sich in `CSize` der Membervariablen des `cx` Objekts, und die Breite befindet sich in der Membervariablen.

### <a name="remarks"></a>Bemerkungen

Die GDI verwendet diese Werte nur, um sie zurückzugeben, wenn eine Anwendung die [GetBitmapDimension-Memberfunktion](#getbitmapdimension) aufruft.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel MDI](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject-Klasse](../../mfc/reference/cgdiobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)

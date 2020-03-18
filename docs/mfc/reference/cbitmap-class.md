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
ms.openlocfilehash: 7161a4cf4484b6cc9e76e6955de558ca6e9121ca
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424680"
---
# <a name="cbitmap-class"></a>CBitmap-Klasse

Kapselt eine Bitmap der Windows GDI (Graphics Device Interface) und stellt Memberfunktionen zur Bearbeitung der Bitmap bereit.

## <a name="syntax"></a>Syntax

```
class CBitmap : public CGdiObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|Beschreibung|
|----------|-----------------|
|[CBitmap:: CBitmap](#cbitmap)|Erstellt ein `CBitmap`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|Beschreibung|
|----------|-----------------|
|[CBitmap:: kreatebitmap](#createbitmap)|Initialisiert das-Objekt mit einer geräteabhängigen Speicher Bitmap, die über eine angegebene Breite, Höhe und ein angegebenes Bitmuster verfügt.|
|[CBitmap:: kreatebitmapindirekte](#createbitmapindirect)|Initialisiert das-Objekt mit einer Bitmap mit der Breite, Höhe und dem Bitmuster (sofern angegeben), die in einer `BITMAP` Struktur angegeben sind.|
|[CBitmap:: kreatecompatiblebitmap](#createcompatiblebitmap)|Initialisiert das-Objekt mit einer Bitmap, sodass es mit einem angegebenen Gerät kompatibel ist.|
|[CBitmap:: kreateverwerdablebitmap](#creatediscardablebitmap)|Initialisiert das-Objekt mit einer verwerfbaren Bitmap, die mit einem angegebenen Gerät kompatibel ist.|
|[CBitmap:: FromHandle](#fromhandle)|Gibt einen Zeiger auf ein `CBitmap` Objekt zurück, wenn ein Handle für eine Windows `HBITMAP` Bitmap angegeben wurde.|
|[CBitmap:: getbitmap](#getbitmap)|Füllt eine `BITMAP`-Struktur mit Informationen über die Bitmap.|
|[CBitmap:: getbitmapbits](#getbitmapbits)|Kopiert die Bits der angegebenen Bitmap in den angegebenen Puffer.|
|[CBitmap:: getbitmapdimension](#getbitmapdimension)|Gibt die Breite und Höhe der Bitmap zurück. Es wird davon ausgegangen, dass die Höhe und Breite zuvor durch die Member-Funktion von [setbitmapdimension](#setbitmapdimension) festgelegt wurde.|
|[CBitmap:: LoadBitmap](#loadbitmap)|Initialisiert das-Objekt, indem eine benannte Bitmap-Ressource aus der ausführbaren Datei der Anwendung geladen und die Bitmap an das-Objekt angefügt wird.|
|[CBitmap:: loadmappedbitmap](#loadmappedbitmap)|Lädt eine Bitmap und ordnet Farben den aktuellen Systemfarben zu.|
|[CBitmap:: loadoembitmap](#loadoembitmap)|Initialisiert das-Objekt, indem eine vordefinierte Windows-Bitmap geladen und die Bitmap an das-Objekt angefügt wird.|
|[CBitmap:: setbitmapbits](#setbitmapbits)|Legt die Bits einer Bitmap auf die angegebenen Bitwerte fest.|
|[CBitmap:: setbitmapdimension](#setbitmapdimension)|Weist eine Breite und Höhe einer Bitmap in 0,1-Millimeter-Einheiten zu.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[CBitmap:: Operator HBITMAP](#operator_hbitmap)|Gibt das an das `CBitmap` Objekt angefügte Windows-Handle zurück.|

## <a name="remarks"></a>Hinweise

Wenn Sie ein `CBitmap` Objekt verwenden möchten, erstellen Sie das-Objekt, fügen Sie ein Bitmap-Handle mit einer der initialisierungsmember-Funktionen an, und nennen Sie dann die-Element Funktionen des-Objekts.

Weitere Informationen zur Verwendung von Grafikobjekten wie `CBitmap`finden Sie unter [Graphic Objects](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBitmap`

## <a name="requirements"></a>Voraussetzungen

**Header:** afxwin.h

##  <a name="cbitmap"></a>CBitmap:: CBitmap

Erstellt ein `CBitmap`-Objekt.

```
CBitmap();
```

### <a name="remarks"></a>Hinweise

Das resultierende-Objekt muss mit einer der initialisierungsmember-Funktionen initialisiert werden.

##  <a name="createbitmap"></a>CBitmap:: kreatebitmap

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

*nwidth*<br/>
Gibt die Breite der Bitmap (in Pixeln) an.

*nheight*<br/>
Gibt die Höhe der Bitmap (in Pixeln) an.

*nplane*<br/>
Gibt die Anzahl von Farbebenen in der Bitmap an.

*nbitcount*<br/>
Gibt die Anzahl der Farbbits pro Anzeigepixel an.

*lpbits*<br/>
Zeigt auf ein Array von Bytes, das die ursprünglichen Bitwerte der Bitmap enthält. Ist dieser Wert NULL, bleibt die neue Bitmap nicht initialisiert.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Für eine Farb Bitmap sollte entweder der *nplane* -Parameter oder der *nbitcount* -Parameter auf 1 festgelegt werden. Wenn beide Parameter auf 1 festgelegt sind, erstellt `CreateBitmap` eine monochrome Bitmap.

Obwohl eine Bitmap nicht direkt für ein Anzeigegerät ausgewählt werden kann, kann sie als aktuelle Bitmap für einen „Speichergerätekontext“ mithilfe von [CDC::SelectObject](../../mfc/reference/cdc-class.md#selectobject) ausgewählt und mithilfe der [CDC::BitBlt](../../mfc/reference/cdc-class.md#bitblt) -Funktion auf einen beliebigen kompatiblen Gerätekontext kopiert werden.

Wenn Sie mit dem `CBitmap` -Objekt fertig sind, das von der `CreateBitmap` -Funktion erstellt wurde, wählen Sie zunächst die Bitmap im Gerätekontext aus, und löschen Sie dann das `CBitmap` -Objekt.

Weitere Informationen finden Sie in der Beschreibung des `bmBits`-Felds in der `BITMAP`-Struktur. Die [BITMAP](/windows/win32/api/wingdi/ns-wingdi-bitmap) -Struktur wird unter der [CBitmap::CreateBitmapIndirect](#createbitmapindirect) -Memberfunktion beschrieben.

##  <a name="createbitmapindirect"></a>CBitmap:: kreatebitmapindirekte

Initialisiert eine Bitmap, die über die Breite, Höhe und das Bitmuster verfügt (sofern angegeben), die in der Struktur angegeben sind, auf die von *lpbitmap*verwiesen wird.

```
BOOL CreateBitmapIndirect(LPBITMAP lpBitmap);
```

### <a name="parameters"></a>Parameter

*lpbitmap*<br/>
Verweist auf eine [Bitmap](/windows/win32/api/wingdi/ns-wingdi-bitmap) -Struktur, die Informationen über die Bitmap enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Obwohl eine Bitmap nicht direkt für ein Anzeigegerät ausgewählt werden kann, kann Sie als aktuelle Bitmap für einen Speichergeräte Kontext mithilfe von [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) ausgewählt und mithilfe der [CDC:: BitBLT](../../mfc/reference/cdc-class.md#bitblt) -oder [CDC:: StretchBlt](../../mfc/reference/cdc-class.md#stretchblt) -Funktion in einen beliebigen kompatiblen Gerätekontext kopiert werden. (Die [CDC::P atblt](../../mfc/reference/cdc-class.md#patblt) -Funktion kann die Bitmap für den aktuellen Pinsel direkt in den Anzeigegeräte Kontext kopieren.)

Wenn die `BITMAP` Struktur, auf die durch den *lpbitmap* -Parameter verwiesen wird, mithilfe der `GetObject`-Funktion ausgefüllt wurde, werden die Bits der Bitmap nicht angegeben, und die Bitmap ist nicht initialisiert. Zum Initialisieren der Bitmap kann eine Anwendung eine Funktion wie [CDC:: BitBLT](../../mfc/reference/cdc-class.md#bitblt) oder [SetDIBits](/windows/win32/api/wingdi/nf-wingdi-setdibits) verwenden, um die Bits aus der Bitmap zu kopieren, die durch den ersten Parameter von `CGdiObject::GetObject` identifiziert wird, in die von `CreateBitmapIndirect`erstellte Bitmap.

Wenn Sie mit dem `CBitmap` Objekt fertig sind, das mit `CreateBitmapIndirect`-Funktion erstellt wurde, wählen Sie zunächst die Bitmap aus dem Gerätekontext aus, und löschen Sie dann das `CBitmap`-Objekt.

##  <a name="createcompatiblebitmap"></a>CBitmap:: kreatecompatiblebitmap

Initialisiert eine Bitmap, die mit dem durch *PDC*angegebenen Gerät kompatibel ist.

```
BOOL CreateCompatibleBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Gibt den Gerätekontext an.

*nwidth*<br/>
Gibt die Breite der Bitmap (in Pixeln) an.

*nheight*<br/>
Gibt die Höhe der Bitmap (in Pixeln) an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Die Bitmap verfügt über die gleiche Anzahl von Farbebenen oder das gleiche Bits-pro-Pixel-Format wie der angegebene Gerätekontext. Sie kann als aktuelle Bitmap für ein beliebiges Speichergerät ausgewählt werden, das mit dem durch *PDC*angegebenen Speichergerät kompatibel ist.

Handelt es sich bei *PDC* um einen Speichergeräte Kontext, hat die zurückgegebene Bitmap dasselbe Format wie das aktuell ausgewählte Bitmap in diesem Gerätekontext. Ein "Speichergeräte Kontext" ist ein Speicherblock, der eine Anzeige Oberfläche darstellt. Sie kann verwendet werden, um Bilder im Speicher vorzubereiten, bevor Sie auf die tatsächliche Anzeige Oberfläche des kompatiblen Geräts kopiert werden.

Wenn ein Speichergeräte Kontext erstellt wird, wählt GDI automatisch eine monochrome Aktien Bitmap aus.

Da für einen Farb Speicher-Gerätekontext entweder Color-oder Chrome-Bitmaps ausgewählt werden können, ist das von der `CreateCompatibleBitmap`-Funktion zurückgegebene Bitmap-Format nicht immer identisch. das Format einer kompatiblen Bitmap für einen nicht-Speichergeräte Kontext weist jedoch immer das Format des Geräts auf.

Wenn Sie mit dem `CBitmap` Objekt fertig sind, das mit der `CreateCompatibleBitmap`-Funktion erstellt wurde, wählen Sie zunächst die Bitmap aus dem Gerätekontext aus, und löschen Sie dann das `CBitmap`-Objekt.

##  <a name="creatediscardablebitmap"></a>CBitmap:: kreateverwerdablebitmap

Initialisiert eine verwerfbare Bitmap, die mit dem durch *PDC*identifizierten Gerätekontext kompatibel ist.

```
BOOL CreateDiscardableBitmap(
    CDC* pDC,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Gibt einen Gerätekontext an.

*nwidth*<br/>
Gibt die Breite (in Bits) der Bitmap an.

*nheight*<br/>
Gibt die Höhe (in Bits) der Bitmap an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Die Bitmap verfügt über die gleiche Anzahl von Farbebenen oder das gleiche Bits-pro-Pixel-Format wie der angegebene Gerätekontext. Eine Anwendung kann diese Bitmap als aktuelle Bitmap für ein Speichergerät auswählen, das mit der von *PDC*angegebenen kompatibel ist.

Windows kann eine Bitmap, die von dieser Funktion erstellt wurde, nur verwerfen, wenn Sie von einer Anwendung nicht in einem Anzeige Kontext ausgewählt wurde. Wenn die Bitmap von Windows verworfen wird, wenn Sie nicht ausgewählt ist, und die Anwendung später versucht, die Bitmap auszuwählen, gibt die [CDC:: SelectObject](../../mfc/reference/cdc-class.md#selectobject) -Funktion NULL zurück.

Wenn Sie mit dem `CBitmap` Objekt fertig sind, das mit der `CreateDiscardableBitmap`-Funktion erstellt wurde, wählen Sie zunächst die Bitmap aus dem Gerätekontext aus, und löschen Sie dann das `CBitmap`-Objekt.

##  <a name="fromhandle"></a>CBitmap:: FromHandle

Gibt einen Zeiger auf ein `CBitmap` Objekt zurück, wenn ein Handle für eine Windows GDI-Bitmap angegeben wurde.

```
static CBitmap* PASCAL FromHandle(HBITMAP hBitmap);
```

### <a name="parameters"></a>Parameter

*HBITMAP*<br/>
Gibt eine Windows-GDI-Bitmap an.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `CBitmap` Objekt, wenn erfolgreich. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Wenn ein `CBitmap` Objekt noch nicht an das Handle angefügt ist, wird ein temporäres `CBitmap` Objekt erstellt und angefügt. Dieses temporäre `CBitmap` Objekt ist nur gültig, bis das nächste Mal die Leerlaufzeit der Anwendung in der Ereignisschleife liegt. zu diesem Zeitpunkt werden alle temporären Grafik Objekte gelöscht. Eine andere Möglichkeit, dies zu sagen, besteht darin, dass das temporäre Objekt nur während der Verarbeitung einer Fenster Nachricht gültig ist.

##  <a name="getbitmap"></a>CBitmap:: getbitmap

Ruft Bildeigenschaften für die angefügte Bitmap ab.

```
int GetBitmap(BITMAP* pBitMap);
```

### <a name="parameters"></a>Parameter

*pbitmap*<br/>
Zeiger auf eine [Bitmap](/windows/win32/api/wingdi/ns-wingdi-bitmap) -Struktur, die die Bildeigenschaften empfängt. Dieser Parameter darf nicht NULL sein.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Methode erfolgreich war. andernfalls 0.

### <a name="remarks"></a>Hinweise

##  <a name="getbitmapbits"></a>CBitmap:: getbitmapbits

Kopiert das Bitmuster der angefügten Bitmap in den angegebenen Puffer.

```
DWORD GetBitmapBits(
    DWORD dwCount,
    LPVOID lpBits) const;
```

### <a name="parameters"></a>Parameter

*dwCount*<br/>
Die Anzahl von Bytes, die in den Puffer kopiert werden sollen.

*lpbits*<br/>
Zeiger auf den Puffer, der die Bitmap empfängt.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Bytes, die in den Puffer kopiert werden, wenn die Methode erfolgreich war. andernfalls 0.

### <a name="remarks"></a>Hinweise

Verwenden Sie [CBitmap:: getbitmap](#getbitmap) , um die erforderliche Puffergröße zu bestimmen.

##  <a name="getbitmapdimension"></a>CBitmap:: getbitmapdimension

Gibt die Breite und Höhe der Bitmap zurück.

```
CSize GetBitmapDimension() const;
```

### <a name="return-value"></a>Rückgabewert

Die Breite und Höhe der Bitmap, gemessen in Einheiten von 0,1 Millimeter. Die Höhe befindet sich im `cy`-Member des `CSize`-Objekts, und die Breite ist im `cx` Member. Wenn die Breite und Höhe der Bitmap nicht mithilfe von `SetBitmapDimension`festgelegt wurde, ist der Rückgabewert 0.

### <a name="remarks"></a>Hinweise

Es wird davon ausgegangen, dass die Höhe und die Breite zuvor mithilfe der [setbitmapdimension](#setbitmapdimension) -Element Funktion festgelegt wurden.

##  <a name="loadbitmap"></a>CBitmap:: LoadBitmap

Lädt die Bitmap-Ressource mit dem Namen *lpszresourcename* oder identifiziert durch die ID-Nummer in *nidresource* aus der ausführbaren Datei der Anwendung.

```
BOOL LoadBitmap(LPCTSTR lpszResourceName);
BOOL LoadBitmap(UINT nIDResource);
```

### <a name="parameters"></a>Parameter

*lpszresourcename*<br/>
Verweist auf eine mit NULL endenden Zeichenfolge, die den Namen der Bitmap-Ressource enthält.

*nidresource*<br/>
Gibt die Ressourcen-ID-Nummer der Bitmap-Ressource an.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Die geladene Bitmap wird an das `CBitmap` Objekt angefügt.

Wenn die von *lpszresourcename* identifizierte Bitmap nicht vorhanden ist oder nicht genügend Arbeitsspeicher zum Laden der Bitmap vorhanden ist, gibt die Funktion 0 zurück.

Sie können die [CGdiObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject) -Funktion verwenden, um die von der `LoadBitmap`-Funktion geladene Bitmap zu löschen, oder der `CBitmap`-debugtor löscht das-Objekt für Sie.

> [!CAUTION]
>  Bevor Sie das Objekt löschen, stellen Sie sicher, dass es nicht in einem Gerätekontext ausgewählt ist.

Die folgenden Bitmaps wurden den Windows-Versionen 3,1 und höher hinzugefügt:

OBM_UPARRROWIOBM_DNARROWIOBM_RGARROWIOBM_LFARROWI

Diese Bitmaps wurden in Gerätetreibern für Windows-Versionen 3,0 und früher nicht gefunden. Eine umfassende Liste der Bitmaps und eine Anzeige Ihrer Darstellung finden Sie in der Windows SDK.

##  <a name="loadmappedbitmap"></a>CBitmap:: loadmappedbitmap

Mit dieser Member-Funktion können Sie eine Bitmap laden und die Farben den aktuellen Systemfarben zuordnen.

```
BOOL LoadMappedBitmap(
    UINT nIDBitmap,
    UINT nFlags = 0,
    LPCOLORMAP lpColorMap = NULL,
    int nMapSize = 0);
```

### <a name="parameters"></a>Parameter

*nidbitmap*<br/>
Die ID der Bitmap-Ressource.

*nFlags*<br/>
Ein Flag für eine Bitmap. Kann NULL oder CMB_MASKED sein.

*lpcolormap*<br/>
Ein Zeiger auf eine `COLORMAP`-Struktur, die die zum Zuordnen der Bitmaps benötigten Farbinformationen enthält. Wenn dieser Parameter NULL ist, verwendet die Funktion die Standard Farbzuordnung.

*nmapsize*<br/>
Die Anzahl der Farb Zuordnungen, auf die von *lpcolormap*verwiesen wird.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Standardmäßig werden in `LoadMappedBitmap` Farben zugeordnet, die häufig in Schaltflächen Symbolen verwendet werden.

Weitere Informationen zum Erstellen einer zugeordneten Bitmap finden Sie unter der Windows-Funktion " [kreatemappedbitmap](https://go.microsoft.com/fwlink/p/?linkid=230562) " und der [ColorMap](/windows/win32/api/commctrl/ns-commctrl-colormap) -Struktur in der Windows SDK.

##  <a name="loadoembitmap"></a>CBitmap:: loadoembitmap

Lädt eine vordefinierte Bitmap, die von Windows verwendet wird.

```
BOOL LoadOEMBitmap(UINT nIDBitmap);
```

### <a name="parameters"></a>Parameter

*nidbitmap*<br/>
ID-Nummer der vordefinierten Windows-Bitmap. Die möglichen Werte sind unten unter Windows aufgeführt. Micha

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

### <a name="remarks"></a>Hinweise

Bitmapnamen, die mit OBM_OLD beginnen, stellen Bitmaps dar, die von Windows-Versionen vor 3,0 verwendet werden.

Beachten Sie, dass die Konstante oemresource vor dem einschließen von Windows definiert werden muss. H, um eine der **OBM_** Konstanten zu verwenden.

##  <a name="operator_hbitmap"></a>CBitmap:: Operator HBITMAP

Verwenden Sie diesen Operator, um das angefügte Windows-GDI-Handle des `CBitmap` Objekts zu erhalten.

```
operator HBITMAP() const;
```

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ein Handle für das Windows-GDI-Objekt, das durch das `CBitmap`-Objekt dargestellt wird. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Dieser Operator ist ein Typumwandlungs Operator, der die direkte Verwendung eines `HBITMAP` Objekts unterstützt.

Weitere Informationen zum Verwenden von Grafikobjekten finden Sie unter [Graphic Objects](/windows/win32/gdi/graphic-objects) in the Windows SDK.

##  <a name="setbitmapbits"></a>CBitmap:: setbitmapbits

Legt die Bits einer Bitmap auf die Bitwerte fest, die von *lpbits*angegeben werden.

```
DWORD SetBitmapBits(
    DWORD dwCount,
    const void* lpBits);
```

### <a name="parameters"></a>Parameter

*dwCount*<br/>
Gibt die Anzahl der Bytes an, auf die von *lpbits*verwiesen wird.

*lpbits*<br/>
Verweist auf das Bytearray, das die Pixelwerte enthält, die in das `CBitmap` Objekt kopiert werden sollen. Damit die Bitmap das Bild ordnungsgemäß renderfähig ist, sollten die Werte so formatiert werden, dass Sie den Werten für Höhe, Breite und Farbtiefe entsprechen, die beim Erstellen der CBitmap-Instanz angegeben wurden. Weitere Informationen finden Sie unter [CBitmap:: erkreatebitmap](#createbitmap).

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Bytes, die beim Festlegen der Bitmapbits verwendet werden. 0, wenn die Funktion fehlschlägt.

##  <a name="setbitmapdimension"></a>CBitmap:: setbitmapdimension

Weist eine Breite und Höhe einer Bitmap in 0,1-Millimeter-Einheiten zu.

```
CSize SetBitmapDimension(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>Parameter

*nwidth*<br/>
Gibt die Breite der Bitmap an (in Einheiten von 0,1 Millimeter).

*nheight*<br/>
Gibt die Höhe der Bitmap an (in Einheiten von 0,1 Millimeter).

### <a name="return-value"></a>Rückgabewert

Die vorherigen bitmapdimensionen. Die Höhe befindet sich in der `cy` Member-Variable des `CSize`-Objekts, und die Breite ist in der `cx` Member-Variable.

### <a name="remarks"></a>Hinweise

Der GDI verwendet diese Werte nicht, es sei denn, Sie werden zurückgegeben, wenn eine Anwendung die [getbitmapdimension](#getbitmapdimension) -Member-Funktion aufruft.

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel-MDI](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject-Klasse](../../mfc/reference/cgdiobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)

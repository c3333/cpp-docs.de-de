---
title: CBrush-Klasse
ms.date: 11/04/2016
f1_keywords:
- CBrush
- AFXWIN/CBrush
- AFXWIN/CBrush::CBrush
- AFXWIN/CBrush::CreateBrushIndirect
- AFXWIN/CBrush::CreateDIBPatternBrush
- AFXWIN/CBrush::CreateHatchBrush
- AFXWIN/CBrush::CreatePatternBrush
- AFXWIN/CBrush::CreateSolidBrush
- AFXWIN/CBrush::CreateSysColorBrush
- AFXWIN/CBrush::FromHandle
- AFXWIN/CBrush::GetLogBrush
helpviewer_keywords:
- CBrush [MFC], CBrush
- CBrush [MFC], CreateBrushIndirect
- CBrush [MFC], CreateDIBPatternBrush
- CBrush [MFC], CreateHatchBrush
- CBrush [MFC], CreatePatternBrush
- CBrush [MFC], CreateSolidBrush
- CBrush [MFC], CreateSysColorBrush
- CBrush [MFC], FromHandle
- CBrush [MFC], GetLogBrush
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
ms.openlocfilehash: a99d8c8022d23f627320b66c3f376be803c9c839
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79426012"
---
# <a name="cbrush-class"></a>CBrush-Klasse

Kapselt einen Pinsel der Windows GDI (Graphics Device Interface).

## <a name="syntax"></a>Syntax

```
class CBrush : public CGdiObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|-Name|Beschreibung|
|----------|-----------------|
|[CBrush::CBrush](#cbrush)|Erstellt ein `CBrush`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|-Name|Beschreibung|
|----------|-----------------|
|[CBrush::CreateBrushIndirect](#createbrushindirect)|Initialisiert einen Pinsel mit dem Stil, der Farbe und dem Muster, der in einer [logbrush](/windows/win32/api/wingdi/ns-wingdi-logbrush) -Struktur angegeben ist.|
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|Initialisiert einen Pinsel mit einem Muster, das durch eine geräteunabhängige Bitmap (DIB) angegeben wird.|
|[CBrush::CreateHatchBrush](#createhatchbrush)|Initialisiert einen Pinsel mit dem angegebenen Schraffurmuster und der angegebenen Farbe.|
|[CBrush::CreatePatternBrush](#createpatternbrush)|Initialisiert einen Pinsel mit einem Muster, das durch eine Bitmap angegeben wird.|
|[CBrush::CreateSolidBrush](#createsolidbrush)|Initialisiert einen Pinsel mit der angegebenen voll Tonfarbe.|
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|Erstellt einen Pinsel, bei dem es sich um die Standardsystem Farbe handelt.|
|[CBrush::FromHandle](#fromhandle)|Gibt einen Zeiger auf ein `CBrush` Objekt zurück, wenn ein Handle für ein Windows `HBRUSH`-Objekt angegeben ist.|
|[CBrush::GetLogBrush](#getlogbrush)|Ruft eine [logbrush](/windows/win32/api/wingdi/ns-wingdi-logbrush) -Struktur ab.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[CBrush:: Operator hBrush](#operator_hbrush)|Gibt das an das `CBrush` Objekt angefügte Windows-Handle zurück.|

## <a name="remarks"></a>Hinweise

Um ein `CBrush` Objekt zu verwenden, erstellen Sie ein `CBrush` Objekt und übergeben es an eine beliebige `CDC` Member-Funktion, die einen Pinsel erfordert.

Pinsel können durchgezogen, angezeigt oder gemustert werden.

Weitere Informationen zu `CBrush`finden Sie unter [Graphic Objects](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

##  <a name="cbrushcbrush"></a><a name="cbrush"></a>CBrush:: CBrush

Erstellt ein `CBrush`-Objekt.

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parameter

*crColor*<br/>
Gibt die Vordergrundfarbe des Pinsels als RGB-Farbe an. Wenn der Pinsel angezeigt wird, gibt dieser Parameter die Farbe der Schraffur an.

*nIndex*<br/>
Gibt die Schraffurart des Pinsels an. Es kann sich um einen der folgenden Werte handeln:

- HS_BDIAGONAL abwärts Schraffur (von links nach rechts) um 45 Grad

- Horizontale und vertikale Kreuz HS_CROSS

- HS_DIAGCROSS crosshatch um 45 Grad

- HS_FDIAGONAL nach oben (von links nach rechts) um 45 Grad

- Horizontale Schraffur HS_HORIZONTAL

- HS_VERTICAL vertikale Schraffur

*pBitmap*<br/>
Verweist auf ein `CBitmap` Objekt, das eine Bitmap angibt, mit der der Pinsel zeichnet.

### <a name="remarks"></a>Hinweise

`CBrush` über vier überladene Konstruktoren verfügt. Der Konstruktor ohne Argumente erstellt ein nicht initialisiertes `CBrush` Objekt, das initialisiert werden muss, bevor es verwendet werden kann.

Wenn Sie den Konstruktor ohne Argumente verwenden, müssen Sie das resultierende `CBrush` Objekt mit demBefehl [CreateSolidBrush](#createsolidbrush), [CreateHatchBrush](#createhatchbrush), [CreateBrushIndirect](#createbrushindirect), [CreatePatternBrush](#createpatternbrush)oder " [kreatedibpatternbrush](#createdibpatternbrush)" initialisieren. Wenn Sie einen der Konstruktoren verwenden, der Argumente annimmt, ist keine weitere Initialisierung erforderlich. Die Konstruktoren mit Argumenten können eine Ausnahme auslösen, wenn Fehler auftreten, während der Konstruktor ohne Argumente immer erfolgreich ist.

Der Konstruktor mit einem einzelnen [COLORREF](/windows/win32/gdi/colorref) -Parameter erstellt einen Pinsel mit der angegebenen Farbe. Die Farbe gibt einen RGB-Wert an und kann mit dem RGB-Makro in Windows erstellt werden. Micha.

Der Konstruktor mit zwei Parametern erstellt einen Schraffurpinsel. Der *nIndex* -Parameter gibt den Index eines Schraffurmusters an. Der *crcolor* -Parameter gibt die Farbe an.

Der Konstruktor mit einem `CBitmap`-Parameter erstellt einen gemusterten Pinsel. Der-Parameter identifiziert eine Bitmap. Es wird davon ausgegangen, dass die Bitmap mithilfe von [CBitmap:: deatebitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap:: deatebitmapindirekte](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap:: LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)oder [CBitmap:: anatecompatiblebitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)erstellt wurde. Die minimale Größe für eine Bitmap, die in einem Füllmuster verwendet werden soll, beträgt 8 Pixel x 8 Pixel.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

##  <a name="cbrushcreatebrushindirect"></a><a name="createbrushindirect"></a>CBrush:: kreatebrushindirekte

Initialisiert einen Pinsel mit einem Stil, einer Farbe und einem Muster, das in einer [logbrush](/windows/win32/api/wingdi/ns-wingdi-logbrush) -Struktur angegeben ist.

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>Parameter

*lpLogBrush*<br/>
Verweist auf eine [logbrush](/windows/win32/api/wingdi/ns-wingdi-logbrush) -Struktur, die Informationen über den Pinsel enthält.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Hinweise

Der Pinsel kann anschließend als aktueller Pinsel für beliebige Geräte Kontexte ausgewählt werden.

Ein Pinsel, der mithilfe einer Monochrom (1 Ebene, 1 Bit pro Pixel) erstellt wurde, wird mithilfe der aktuellen Text-und Hintergrundfarben gezeichnet. Pixel, die durch ein Bit dargestellt werden, das auf 0 festgelegt ist, werden mit der aktuellen Textfarbe gezeichnet. Pixel, die durch ein Bit dargestellt werden, das auf 1 festgelegt ist, werden mit der aktuellen Hintergrundfarbe gezeichnet.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

##  <a name="cbrushcreatedibpatternbrush"></a><a name="createdibpatternbrush"></a>CBrush:: kreatedibpatternbrush

Initialisiert einen Pinsel mit dem Muster, das durch eine geräteunabhängige Bitmap (DIB) angegeben wird.

```
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,
    UINT nUsage);

BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,
    UINT nUsage);
```

### <a name="parameters"></a>Parameter

*hPackedDIB*<br/>
Identifiziert ein Objekt mit globalem Speicher, das eine gepackte geräteunabhängige Bitmap (DIB) enthält.

*nUsage*<br/>
Gibt an, ob die `bmiColors[]` Felder der [BitmapInfo](/windows/win32/api/wingdi/ns-wingdi-bitmapinfo) -Datenstruktur (ein Teil des "gepackten DIB") explizite RGB-Werte oder Indizes in die derzeit erkannte logische Palette enthalten. Der Parameter muss einen der folgenden Werte aufweisen:

- DIB_PAL_COLORS die Farbtabelle besteht aus einem Array von 16-Bit-Indizes.

- DIB_RGB_COLORS die Farbtabelle Literale RGB-Werte enthält.

*lpPackedDIB*<br/>
Verweist auf ein gepacktes DIB, das aus einer `BITMAPINFO`-Struktur besteht, auf die direkt ein Bytearray folgt, das die Pixel der Bitmap definiert.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Der Pinsel kann anschließend für jeden Gerätekontext ausgewählt werden, der Raster Vorgänge unterstützt.

Die beiden Versionen unterscheiden sich in der Art und Weise, wie Sie die DIB behandeln:

- In der ersten Version rufen Sie zum Abrufen eines Handles zum DIB die Windows `GlobalAlloc`-Funktion auf, um einen Block des globalen Speichers zuzuordnen, und füllen Sie dann den Arbeitsspeicher mit dem gepackten DIB.

- In der zweiten Version ist es nicht notwendig, `GlobalAlloc` aufzurufen, um Speicher für das gepackte DIB zuzuweisen.

Ein gepacktes DIB besteht aus einer `BITMAPINFO` Datenstruktur, der unmittelbar das Bytearray folgt, das die Pixel der Bitmap definiert. Bitmaps, die als Füllmuster verwendet werden, sollten 8 Pixel x 8 Pixel betragen. Wenn die Bitmap größer ist, erstellt Windows ein Füllmuster mit nur den Bits, die den ersten 8 Zeilen und 8 Spalten der Pixel in der oberen linken Ecke der Bitmap entsprechen.

Wenn eine Anwendung einen zweifarbigen DIB-Muster Pinsel in einem monochrome-Gerätekontext auswählt, ignoriert Windows die im DIB angegebenen Farben und zeigt stattdessen den Muster Pinsel mithilfe der aktuellen Text-und Hintergrundfarben des Geräte Kontexts an. Pixel, die der ersten Farbe (bei Offset 0 in der DIB-Farbtabelle) des DIB zugeordnet sind, werden mit der Textfarbe angezeigt. Pixel, die der zweiten Farbe (bei Offset 1 in der Farbtabelle) zugeordnet sind, werden unter Verwendung der Hintergrundfarbe angezeigt.

Informationen zur Verwendung der folgenden Windows-Funktionen finden Sie unter Windows SDK:

- " [Kreatedibpatternbrush](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrush) " (diese Funktion wird nur für die Kompatibilität mit Anwendungen bereitgestellt, die für ältere Windows-Versionen als 3,0 geschrieben wurden. verwenden Sie die `CreateDIBPatternBrushPt`-Funktion.)

- " [Kreatedibpatternbrushpt](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrushpt) " (diese Funktion sollte für Win32-basierte Anwendungen verwendet werden.)

- [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

##  <a name="cbrushcreatehatchbrush"></a><a name="createhatchbrush"></a>CBrush:: kreatehatchbrush

Initialisiert einen Pinsel mit dem angegebenen Schraffurmuster und der angegebenen Farbe.

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt die Schraffurart des Pinsels an. Es kann sich um einen der folgenden Werte handeln:

- HS_BDIAGONAL abwärts Schraffur (von links nach rechts) um 45 Grad

- Horizontale und vertikale Kreuz HS_CROSS

- HS_DIAGCROSS crosshatch um 45 Grad

- HS_FDIAGONAL nach oben (von links nach rechts) um 45 Grad

- Horizontale Schraffur HS_HORIZONTAL

- HS_VERTICAL vertikale Schraffur

*crColor*<br/>
Gibt die Vordergrundfarbe des Pinsels als RGB-Farbe an (die Farbe der Schraffuren). Weitere Informationen finden Sie unter [COLORREF](/windows/win32/gdi/colorref) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Der Pinsel kann anschließend als aktueller Pinsel für beliebige Geräte Kontexte ausgewählt werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

##  <a name="cbrushcreatepatternbrush"></a><a name="createpatternbrush"></a>CBrush:: kreatepatternbrush

Initialisiert einen Pinsel mit einem Muster, das durch eine Bitmap angegeben wird.

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parameter

*pBitmap*<br/>
Bezeichnet eine Bitmap.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Der Pinsel kann anschließend für jeden Gerätekontext ausgewählt werden, der Raster Vorgänge unterstützt. Die durch *pbitmap* identifizierte Bitmap wird in der Regel mithilfe der [CBitmap:: deatebitmap](../../mfc/reference/cbitmap-class.md#createbitmap)-, [CBitmap:: up-bitmapindirekte](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap:: LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)-Funktion oder der [CBitmap:: deatecompatiblebitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap) -Funktion initialisiert.

Bitmaps, die als Füllmuster verwendet werden, sollten 8 Pixel x 8 Pixel betragen. Wenn die Bitmap größer ist, verwendet Windows nur die Bits, die den ersten 8 Zeilen und Spalten der Pixel in der oberen linken Ecke der Bitmap entsprechen.

Ein Muster Pinsel kann gelöscht werden, ohne dass sich dies auf die zugeordnete Bitmap auswirkt. Dies bedeutet, dass die Bitmap zum Erstellen einer beliebigen Anzahl von Muster Pinseln verwendet werden kann.

Ein Pinsel, der mit einer monochrome Bitmap (1 Farb Ebene, 1 Bit pro Pixel) erstellt wurde, wird mithilfe der aktuellen Text-und Hintergrundfarben gezeichnet. Pixel, die durch ein Bit dargestellt werden, das auf 0 gesetzt ist, werden mit der aktuellen Textfarbe gezeichnet. Pixel, die durch ein Bit, das auf 1 festgelegt ist, werden mit der aktuellen Hintergrundfarbe gezeichnet.

Informationen zur Verwendung von " [kreatepatternbrush](/windows/win32/api/wingdi/nf-wingdi-createpatternbrush)", eine Windows-Funktion, finden Sie unter Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

##  <a name="cbrushcreatesolidbrush"></a><a name="createsolidbrush"></a>CBrush:: kreatesolidbrush

Initialisiert einen Pinsel mit einer angegebenen voll Tonfarbe.

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>Parameter

*crColor*<br/>
Eine [COLORREF](/windows/win32/gdi/colorref) -Struktur, die die Farbe des Pinsels angibt. Die Farbe gibt einen RGB-Wert an und kann mit dem RGB-Makro in Windows erstellt werden. Micha.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Der Pinsel kann anschließend als aktueller Pinsel für beliebige Geräte Kontexte ausgewählt werden.

Wenn eine Anwendung die Verwendung des durch `CreateSolidBrush`erstellten Pinsels beendet hat, sollte der Pinsel aus dem Gerätekontext ausgewählt werden.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CBrush:: CBrush](#cbrush).

##  <a name="cbrushcreatesyscolorbrush"></a><a name="createsyscolorbrush"></a>CBrush:: kreatesyscolorbrush

Initialisiert eine Pinsel Farbe.

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt einen Farbindex an. Dieser Wert entspricht der Farbe, die zum Zeichnen eines der 21 Fensterelemente verwendet wird. Eine Liste der Werte finden Sie unter [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Hinweise

Der Pinsel kann anschließend als aktueller Pinsel für beliebige Geräte Kontexte ausgewählt werden.

Wenn eine Anwendung die Verwendung des durch `CreateSysColorBrush`erstellten Pinsels beendet hat, sollte der Pinsel aus dem Gerätekontext ausgewählt werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

##  <a name="cbrushfromhandle"></a><a name="fromhandle"></a>CBrush:: FromHandle

Gibt einen Zeiger auf ein `CBrush` Objekt zurück, wenn ein Handle für ein Windows [hBrush](#operator_hbrush) -Objekt angegeben ist.

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>Parameter

*hBrush*<br/>
Handle für einen Windows-GDI-Pinsel.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `CBrush` Objekt, wenn erfolgreich. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Wenn ein `CBrush` Objekt noch nicht an das Handle angefügt ist, wird ein temporäres `CBrush` Objekt erstellt und angefügt. Dieses temporäre `CBrush` Objekt ist nur gültig, bis die Anwendung das nächste Mal in der Ereignisschleife eine Leerlaufzeit aufweist. Zu diesem Zeitpunkt werden alle temporären Grafik Objekte gelöscht. Das heißt, dass das temporäre Objekt nur während der Verarbeitung einer Fenster Nachricht gültig ist.

Weitere Informationen zum Verwenden von Grafikobjekten finden Sie unter [Graphic Objects](/windows/win32/gdi/graphic-objects) in the Windows SDK.

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CBrush:: CBrush](#cbrush).

##  <a name="cbrushgetlogbrush"></a><a name="getlogbrush"></a>CBrush:: getlogbrush

Rufen Sie diese Member-Funktion auf, um die `LOGBRUSH`-Struktur abzurufen.

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>Parameter

*pLogBrush*<br/>
Verweist auf eine [logbrush](/windows/win32/api/wingdi/ns-wingdi-logbrush) -Struktur, die Informationen über den Pinsel enthält.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist und *plogbrush* ein gültiger Zeiger ist, ist der Rückgabewert die Anzahl von Bytes, die im Puffer gespeichert werden.

Wenn die Funktion erfolgreich ist und *plogbrush* den Wert NULL hat, ist der Rückgabewert die Anzahl von Bytes, die zum Speichern der Informationen erforderlich sind, die von der Funktion im Puffer gespeichert werden.

Wenn die Funktion fehlschlägt, ist der Rückgabewert 0.

### <a name="remarks"></a>Hinweise

Die `LOGBRUSH` Struktur definiert den Stil, die Farbe und das Muster eines Pinsels.

Beispielsweise wird `GetLogBrush` aufgerufen, um die jeweilige Farbe oder das Muster einer Bitmap abzugleichen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

##  <a name="cbrushoperator-hbrush"></a><a name="operator_hbrush"></a>CBrush:: Operator hBrush

Verwenden Sie diesen Operator, um das angefügte Windows-GDI-Handle des `CBrush` Objekts zu erhalten.

```
operator HBRUSH() const;
```

### <a name="return-value"></a>Rückgabewert

Bei Erfolg ein Handle für das Windows-GDI-Objekt, das durch das `CBrush`-Objekt dargestellt wird. andernfalls NULL.

### <a name="remarks"></a>Hinweise

Dieser Operator ist ein Typumwandlungs Operator, der die direkte Verwendung eines hBrush-Objekts unterstützt.

Weitere Informationen zum Verwenden von Grafikobjekten finden Sie unter [Graphic Objects](/windows/win32/gdi/graphic-objects) in the Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject-Klasse](../../mfc/reference/cgdiobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CBitmap-Klasse](../../mfc/reference/cbitmap-class.md)<br/>
[CDC-Klasse](../../mfc/reference/cdc-class.md)

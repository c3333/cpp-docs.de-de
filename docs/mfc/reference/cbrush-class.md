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
ms.openlocfilehash: 15132bb5497886638edfe431ae769dd446785df8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352480"
---
# <a name="cbrush-class"></a>CBrush-Klasse

Kapselt einen Pinsel der Windows GDI (Graphics Device Interface).

## <a name="syntax"></a>Syntax

```
class CBrush : public CGdiObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBrush::CBrush](#cbrush)|Erstellt ein `CBrush`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBrush::CreateBrushIndirect](#createbrushindirect)|Initialisiert einen Pinsel mit dem Stil, der Farbe und dem Muster, die in einer [LOGBRUSH-Struktur](/windows/win32/api/wingdi/ns-wingdi-logbrush) angegeben sind.|
|[CBrush::CreateDIBPatternBrush](#createdibpatternbrush)|Initialisiert einen Pinsel mit einem Muster, das von einer geräteunabhängigen Bitmap (DIB) angegeben wird.|
|[CBrush::CreateHatchBrush](#createhatchbrush)|Initialisiert einen Pinsel mit dem angegebenen Schraffurmuster und der angegebenen Farbe.|
|[CBrush::CreatePatternBrush](#createpatternbrush)|Initialisiert einen Pinsel mit einem Muster, das durch eine Bitmap angegeben wird.|
|[CBrush::CreateSolidBrush](#createsolidbrush)|Initialisiert einen Pinsel mit der angegebenen Volltonfarbe.|
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|Erstellt einen Pinsel, der die Standardsystemfarbe ist.|
|[CBrush::FromHandle](#fromhandle)|Gibt einen Zeiger `CBrush` auf ein Objekt zurück, `HBRUSH` wenn einem Windows-Objekt ein Handle gegeben wird.|
|[CBrush::GetLogBrush](#getlogbrush)|Ruft eine [LOGBRUSH-Struktur ab.](/windows/win32/api/wingdi/ns-wingdi-logbrush)|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBrush::operator HBRUSH](#operator_hbrush)|Gibt das Windows-Handle `CBrush` zurück, das an das Objekt angefügt ist.|

## <a name="remarks"></a>Bemerkungen

Um ein `CBrush` Objekt zu `CBrush` verwenden, erstellen `CDC` Sie ein Objekt und übergeben Sie es an jede Memberfunktion, die einen Pinsel erfordert.

Bürsten können fest, geschlüpft oder gemustert sein.

Weitere Informationen `CBrush`zu finden Sie unter [Grafikobjekte](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="cbrushcbrush"></a><a name="cbrush"></a>CBrush::CBrush

Erstellt ein `CBrush`-Objekt.

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parameter

*crColor*<br/>
Gibt die Vordergrundfarbe des Pinsels als RGB-Farbe an. Wenn der Pinsel geschlüpft ist, gibt dieser Parameter die Farbe des Schraffurens an.

*nIndex*<br/>
Gibt den Schraffurstil des Pinsels an. Es kann einer der folgenden Werte sein:

- HS_BDIAGONAL Abschrägklappe (von links nach rechts) bei 45 Grad

- HS_CROSS Horizontale und vertikale Schraffur

- HS_DIAGCROSS Crosshatch bei 45 Grad

- HS_FDIAGONAL Aufwärtsluke (von links nach rechts) bei 45 Grad

- HS_HORIZONTAL Horizontale Luke

- HS_VERTICAL Vertikale Luke

*pBitmap*<br/>
Zeigt auf `CBitmap` ein Objekt, das eine Bitmap angibt, mit der der Pinsel malt.

### <a name="remarks"></a>Bemerkungen

`CBrush`hat vier überladene Konstruktoren. Der Konstruktor ohne Argumente erstellt ein `CBrush` nicht initialisiertes Objekt, das initialisiert werden muss, bevor es verwendet werden kann.

Wenn Sie den Konstruktor ohne Argumente verwenden, `CBrush` müssen Sie das resultierende Objekt mit [CreateSolidBrush](#createsolidbrush), [CreateHatchBrush](#createhatchbrush), [CreateBrushIndirect](#createbrushindirect), [CreatePatternBrush](#createpatternbrush)oder [CreateDIBPatternBrush](#createdibpatternbrush)initialisieren. Wenn Sie einen der Konstruktoren verwenden, die Argumente verwenden, ist keine weitere Initialisierung erforderlich. Die Konstruktoren mit Argumenten können eine Ausnahme auslösen, wenn Fehler auftreten, während der Konstruktor ohne Argumente immer erfolgreich ist.

Der Konstruktor mit einem einzelnen [COLORREF-Parameter](/windows/win32/gdi/colorref) erstellt einen Volumenkörperpinsel mit der angegebenen Farbe. Die Farbe gibt einen RGB-Wert an und kann mit dem RGB-Makro in WINDOWS erstellt werden. H.

Der Konstruktor mit zwei Parametern erstellt einen Schraffurpinsel. Der *Parameter nIndex* gibt den Index eines Schraffurmusters an. Der Parameter *crColor* gibt die Farbe an.

Der Konstruktor `CBitmap` mit einem Parameter erstellt einen gemusterten Pinsel. Der Parameter identifiziert eine Bitmap. Es wird angenommen, dass die Bitmap mit [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)oder [CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)erstellt wurde. Die Mindestgröße für eine Bitmap, die in einem Füllmuster verwendet werden soll, beträgt 8 X x 8 Pixel.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

## <a name="cbrushcreatebrushindirect"></a><a name="createbrushindirect"></a>CBrush::CreateBrushIndirect

Initialisiert einen Pinsel mit einem Stil, einer Farbe und einem Muster, der in einer [LOGBRUSH-Struktur](/windows/win32/api/wingdi/ns-wingdi-logbrush) angegeben ist.

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>Parameter

*lpLogBrush*<br/>
Zeigt auf eine [LOGBRUSH-Struktur,](/windows/win32/api/wingdi/ns-wingdi-logbrush) die Informationen über den Pinsel enthält.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Bemerkungen

Der Pinsel kann anschließend als aktueller Pinsel für jeden Gerätekontext ausgewählt werden.

Ein Pinsel, der mit einer monochromen Bitmap (1 Ebene, 1 Bit pro Pixel) erstellt wurde, wird mit den aktuellen Text- und Hintergrundfarben gezeichnet. Pixel, die durch ein Bit dargestellt werden, das auf 0 gesetzt ist, werden mit der aktuellen Textfarbe gezeichnet. Pixel, die durch ein Bit dargestellt werden, das auf 1 gesetzt ist, werden mit der aktuellen Hintergrundfarbe gezeichnet.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

## <a name="cbrushcreatedibpatternbrush"></a><a name="createdibpatternbrush"></a>CBrush::CreateDIBPatternBrush

Initialisiert einen Pinsel mit dem Muster, das von einer geräteunabhängigen Bitmap (DIB) angegeben wird.

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
Identifiziert ein Global-Memory-Objekt, das eine gepackte geräteunabhängige Bitmap (DIB) enthält.

*nVerwendung*<br/>
Gibt an, `bmiColors[]` ob die Felder der [BITMAPINFO-Datenstruktur](/windows/win32/api/wingdi/ns-wingdi-bitmapinfo) (ein Teil des "verpackten DIB") explizite RGB-Werte oder Indizes in der aktuell realisierten logischen Palette enthalten. Der Parameter muss einer der folgenden Werte sein:

- DIB_PAL_COLORS Die Farbtabelle besteht aus einem Array von 16-Bit-Indizes.

- DIB_RGB_COLORS Die Farbtabelle enthält literale RGB-Werte.

*lpPackedDIB*<br/>
Verweist auf einen gepackten `BITMAPINFO` DIB, der aus einer Struktur besteht, gefolgt von einem Array von Bytes, die die Pixel der Bitmap definieren.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Der Pinsel kann anschließend für jeden Gerätekontext ausgewählt werden, der Raster-Operationen unterstützt.

Die beiden Versionen unterscheiden sich in der Art und Weise, wie Sie mit dem DIB umgehen:

- Um in der ersten Version ein Handle für den `GlobalAlloc` DIB zu erhalten, rufen Sie die Windows-Funktion auf, um einen Block globalen Speichers zuzuweisen und dann den Speicher mit dem gepackten DIB zu füllen.

- In der zweiten Version ist es `GlobalAlloc` nicht notwendig, den Speicher für das gepackte DIB aufzurufen.

Ein gepacktes DIB `BITMAPINFO` besteht aus einer Datenstruktur, gefolgt vom Array von Bytes, das die Pixel der Bitmap definiert. Bitmaps, die als Füllmuster verwendet werden, sollten 8 Pixel x 8 Pixel betragen. Wenn die Bitmap größer ist, erstellt Windows ein Füllmuster, das nur die Bits verwendet, die den ersten 8 Zeilen und 8 Pixelspalten in der oberen linken Ecke der Bitmap entsprechen.

Wenn eine Anwendung einen zweifarbigen DIB-Musterpinsel in einen monochromen Gerätekontext auswählt, ignoriert Windows die im DIB angegebenen Farben und zeigt stattdessen den Musterpinsel mit dem aktuellen Text und den Hintergrundfarben des Gerätekontexts an. Pixel, die der ersten Farbe (bei Offset 0 in der DIB-Farbtabelle) des DIB zugeordnet sind, werden mit der Textfarbe angezeigt. Pixel, die der zweiten Farbe zugeordnet sind (bei Offset 1 in der Farbtabelle), werden mit der Hintergrundfarbe angezeigt.

Informationen zur Verwendung der folgenden Windows-Funktionen finden Sie im Windows SDK:

- [CreateDIBPatternBrush](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrush) (Diese Funktion wird nur für die Kompatibilität mit Anwendungen bereitgestellt, die `CreateDIBPatternBrushPt` für Windows-Versionen vor 3.0 geschrieben wurden; verwenden Sie die Funktion.)

- [CreateDIBPatternBrushPt](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrushpt) (Diese Funktion sollte für Win32-basierte Anwendungen verwendet werden.)

- [Globalalloc](/windows/win32/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

## <a name="cbrushcreatehatchbrush"></a><a name="createhatchbrush"></a>CBrush::CreateHatchBrush

Initialisiert einen Pinsel mit dem angegebenen Schraffurmuster und der angegebenen Farbe.

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt den Schraffurstil des Pinsels an. Es kann einer der folgenden Werte sein:

- HS_BDIAGONAL Abschrägklappe (von links nach rechts) bei 45 Grad

- HS_CROSS Horizontale und vertikale Schraffur

- HS_DIAGCROSS Crosshatch bei 45 Grad

- HS_FDIAGONAL Aufwärtsluke (von links nach rechts) bei 45 Grad

- HS_HORIZONTAL Horizontale Luke

- HS_VERTICAL Vertikale Luke

*crColor*<br/>
Gibt die Vordergrundfarbe des Pinsels als RGB-Farbe (die Farbe der Schraffuren) an. Weitere Informationen finden Sie unter [COLORREF](/windows/win32/gdi/colorref) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Der Pinsel kann anschließend als aktueller Pinsel für jeden Gerätekontext ausgewählt werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

## <a name="cbrushcreatepatternbrush"></a><a name="createpatternbrush"></a>CBrush::CreatePatternBrush

Initialisiert einen Pinsel mit einem Muster, das durch eine Bitmap angegeben wird.

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>Parameter

*pBitmap*<br/>
Identifiziert eine Bitmap.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Der Pinsel kann anschließend für jeden Gerätekontext ausgewählt werden, der Raster-Operationen unterstützt. Die von *pBitmap* identifizierte Bitmap wird in der Regel mithilfe der Funktion [CBitmap::CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap), [CBitmap::CreateBitmapIndirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect), [CBitmap::LoadBitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)oder [CBitmap::CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap) initialisiert.

Bitmaps, die als Füllmuster verwendet werden, sollten 8 Pixel x 8 Pixel betragen. Wenn die Bitmap größer ist, verwendet Windows nur die Bits, die den ersten 8 Zeilen und Pixelspalten in der oberen linken Ecke der Bitmap entsprechen.

Ein Musterpinsel kann gelöscht werden, ohne die zugehörige Bitmap zu beeinflussen. Dies bedeutet, dass die Bitmap verwendet werden kann, um eine beliebige Anzahl von Musterpinsel zu erstellen.

Ein Pinsel, der mit einer monochromen Bitmap (1 Farbebene, 1 Bit pro Pixel) erstellt wurde, wird mit den aktuellen Text- und Hintergrundfarben gezeichnet. Pixel, die durch ein Bit dargestellt werden, das auf 0 gesetzt ist, werden mit der aktuellen Textfarbe gezeichnet. Pixel, die durch ein Bit dargestellt werden, das auf 1 gesetzt ist, werden mit der aktuellen Hintergrundfarbe gezeichnet.

Informationen zur Verwendung von [CreatePatternBrush](/windows/win32/api/wingdi/nf-wingdi-createpatternbrush), einer Windows-Funktion, finden Sie im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

## <a name="cbrushcreatesolidbrush"></a><a name="createsolidbrush"></a>CBrush::CreateSolidBrush

Initialisiert einen Pinsel mit einer angegebenen Volltonfarbe.

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>Parameter

*crColor*<br/>
Eine [COLORREF-Struktur,](/windows/win32/gdi/colorref) die die Farbe des Pinsels angibt. Die Farbe gibt einen RGB-Wert an und kann mit dem RGB-Makro in WINDOWS erstellt werden. H.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Der Pinsel kann anschließend als aktueller Pinsel für jeden Gerätekontext ausgewählt werden.

Wenn eine Anwendung den von `CreateSolidBrush`erstellten Pinsel verwendet hat, sollte sie den Pinsel aus dem Gerätekontext auswählen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CBrush::CBrush](#cbrush).

## <a name="cbrushcreatesyscolorbrush"></a><a name="createsyscolorbrush"></a>CBrush::CreateSysColorBrush

Initialisiert eine Pinselfarbe.

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Gibt einen Farbindex an. Dieser Wert entspricht der Farbe, die zum Malen eines der 21 Fensterelemente verwendet wird. Eine Liste von Werten finden Sie unter [GetSysColor](/windows/win32/api/winuser/nf-winuser-getsyscolor) im Windows SDK.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich, andernfalls 0 (Null).

### <a name="remarks"></a>Bemerkungen

Der Pinsel kann anschließend als aktueller Pinsel für jeden Gerätekontext ausgewählt werden.

Wenn eine Anwendung den von `CreateSysColorBrush`erstellten Pinsel verwendet hat, sollte sie den Pinsel aus dem Gerätekontext auswählen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

## <a name="cbrushfromhandle"></a><a name="fromhandle"></a>CBrush::FromHandle

Gibt einen Zeiger `CBrush` auf ein Objekt zurück, wenn einem Windows [HBRUSH-Objekt](#operator_hbrush) ein Handle übergeben wird.

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>Parameter

*hBrush*<br/>
HANDLE zu einem Windows GDI-Pinsel.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `CBrush` ein Objekt, wenn erfolgreich; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Wenn `CBrush` ein Objekt noch nicht an das `CBrush` Handle angefügt ist, wird ein temporäres Objekt erstellt und angefügt. Dieses `CBrush` temporäre Objekt ist nur bis zum nächsten Zeitpunkt gültig, wenn die Anwendung Leerlaufzeit in ihrer Ereignisschleife hat. Zu diesem Zeitpunkt werden alle temporären Grafikobjekte gelöscht. Mit anderen Worten, das temporäre Objekt ist nur während der Verarbeitung einer Fensternachricht gültig.

Weitere Informationen zur Verwendung von Grafikobjekten finden Sie unter [Grafikobjekte](/windows/win32/gdi/graphic-objects) im Windows SDK.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CBrush::CBrush](#cbrush).

## <a name="cbrushgetlogbrush"></a><a name="getlogbrush"></a>CBrush::GetLogBrush

Rufen Sie diese Memberfunktion auf, um die `LOGBRUSH` Struktur abzurufen.

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>Parameter

*pLogBrush*<br/>
Zeigt auf eine [LOGBRUSH-Struktur,](/windows/win32/api/wingdi/ns-wingdi-logbrush) die Informationen über den Pinsel enthält.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist und *pLogBrush* ein gültiger Zeiger ist, ist der Rückgabewert die Anzahl der im Puffer gespeicherten Bytes.

Wenn die Funktion erfolgreich ist und *pLogBrush* NULL ist, ist der Rückgabewert die Anzahl der Bytes, die erforderlich sind, um die Informationen zu speichern, die die Funktion im Puffer speichern würde.

Wenn die Funktion fehlschlägt, ist der Rückgabewert 0.

### <a name="remarks"></a>Bemerkungen

Die `LOGBRUSH` Struktur definiert den Stil, die Farbe und das Muster eines Pinsels.

Rufen Sie `GetLogBrush` z. B. auf, um der bestimmten Farbe oder dem Muster einer Bitmap zu entsprechen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

## <a name="cbrushoperator-hbrush"></a><a name="operator_hbrush"></a>CBrush::operator HBRUSH

Verwenden Sie diesen Operator, um das `CBrush` angefügte Windows GDI-Handle des Objekts abzubekommen.

```
operator HBRUSH() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, ein Handle für das Windows `CBrush` GDI-Objekt, das durch das Objekt dargestellt wird; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Dieser Operator ist ein Gießoperator, der die direkte Verwendung eines HBRUSH-Objekts unterstützt.

Weitere Informationen zur Verwendung von Grafikobjekten finden Sie unter [Grafikobjekte](/windows/win32/gdi/graphic-objects) im Windows SDK.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject-Klasse](../../mfc/reference/cgdiobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CBitmap-Klasse](../../mfc/reference/cbitmap-class.md)<br/>
[CDC-Klasse](../../mfc/reference/cdc-class.md)

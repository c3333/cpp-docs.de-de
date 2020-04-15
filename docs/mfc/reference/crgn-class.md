---
title: CRgn-Klasse
ms.date: 11/04/2016
f1_keywords:
- CRgn
- AFXWIN/CRgn
- AFXWIN/CRgn::CRgn
- AFXWIN/CRgn::CombineRgn
- AFXWIN/CRgn::CopyRgn
- AFXWIN/CRgn::CreateEllipticRgn
- AFXWIN/CRgn::CreateEllipticRgnIndirect
- AFXWIN/CRgn::CreateFromData
- AFXWIN/CRgn::CreateFromPath
- AFXWIN/CRgn::CreatePolygonRgn
- AFXWIN/CRgn::CreatePolyPolygonRgn
- AFXWIN/CRgn::CreateRectRgn
- AFXWIN/CRgn::CreateRectRgnIndirect
- AFXWIN/CRgn::CreateRoundRectRgn
- AFXWIN/CRgn::EqualRgn
- AFXWIN/CRgn::FromHandle
- AFXWIN/CRgn::GetRegionData
- AFXWIN/CRgn::GetRgnBox
- AFXWIN/CRgn::OffsetRgn
- AFXWIN/CRgn::PtInRegion
- AFXWIN/CRgn::RectInRegion
- AFXWIN/CRgn::SetRectRgn
helpviewer_keywords:
- CRgn [MFC], CRgn
- CRgn [MFC], CombineRgn
- CRgn [MFC], CopyRgn
- CRgn [MFC], CreateEllipticRgn
- CRgn [MFC], CreateEllipticRgnIndirect
- CRgn [MFC], CreateFromData
- CRgn [MFC], CreateFromPath
- CRgn [MFC], CreatePolygonRgn
- CRgn [MFC], CreatePolyPolygonRgn
- CRgn [MFC], CreateRectRgn
- CRgn [MFC], CreateRectRgnIndirect
- CRgn [MFC], CreateRoundRectRgn
- CRgn [MFC], EqualRgn
- CRgn [MFC], FromHandle
- CRgn [MFC], GetRegionData
- CRgn [MFC], GetRgnBox
- CRgn [MFC], OffsetRgn
- CRgn [MFC], PtInRegion
- CRgn [MFC], RectInRegion
- CRgn [MFC], SetRectRgn
ms.assetid: d904da84-76aa-481e-8780-b09485f49e64
ms.openlocfilehash: 72ab4027880285a3c4cd24d586e163e1e01b98f2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368306"
---
# <a name="crgn-class"></a>CRgn-Klasse

Kapselt einen Bereich der Windows GDI (Graphics Device Interface).

## <a name="syntax"></a>Syntax

```
class CRgn : public CGdiObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRgn::CRgn](#crgn)|Erstellt ein `CRgn`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRgn::CombineRgn](#combinergn)|Legt `CRgn` ein Objekt so fest, dass es `CRgn` der Vereinigung zweier angegebener Objekte entspricht.|
|[CRgn::CopyRgn](#copyrgn)|Legt `CRgn` ein Objekt so fest, dass `CRgn` es sich um eine Kopie eines angegebenen Objekts handelt.|
|[CRgn::CreateEllipticRgn](#createellipticrgn)|Initialisiert ein `CRgn` Objekt mit einem elliptischen Bereich.|
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|Initialisiert ein `CRgn` Objekt mit einem elliptischen Bereich, der durch eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) definiert ist.|
|[CRgn::CreateFromData](#createfromdata)|Erstellt eine Region aus der angegebenen Region und Transformationsdaten.|
|[CRgn::CreateFromPath](#createfrompath)|Erstellt einen Bereich aus dem Pfad, der im angegebenen Gerätekontext ausgewählt ist.|
|[CRgn::PolygonRgn erstellen](#createpolygonrgn)|Initialisiert ein `CRgn` Objekt mit einem polygonalen Bereich. Das System schließt das Polygon bei Bedarf automatisch, indem es eine Linie vom letzten Scheitelpunkt zum ersten Zeichen zeichnet.|
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|Initialisiert ein `CRgn` Objekt mit einem Bereich, der aus einer Reihe geschlossener Polygone besteht. Die Polygone können getrennt sein oder sich überlappen.|
|[CRgn::CreateRectRgn](#createrectrgn)|Initialisiert ein `CRgn` Objekt mit einem rechteckigen Bereich.|
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|Initialisiert ein `CRgn` Objekt mit einem rechteckigen Bereich, der durch eine [RECT-Truktur](/windows/win32/api/windef/ns-windef-rect)definiert ist.|
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|Initialisiert ein `CRgn` Objekt mit einem rechteckigen Bereich mit abgerundeten Ecken.|
|[CRgn::EqualRgn](#equalrgn)|Überprüft `CRgn` zwei Objekte, um festzustellen, ob sie äquivalent sind.|
|[CRgn::FromHandle](#fromhandle)|Gibt einen Zeiger `CRgn` auf ein Objekt zurück, wenn einem Windows-Bereich ein Handle übergeben wird.|
|[CRgn::GetRegionData](#getregiondata)|Füllt den angegebenen Puffer mit Daten, die den angegebenen Bereich beschreiben.|
|[CRgn::GetRgnBox](#getrgnbox)|Ruft die Koordinaten des umgrenzenden `CRgn` Rechtecks eines Objekts ab.|
|[CRgn::OffsetRgn](#offsetrgn)|Verschiebt `CRgn` ein Objekt um die angegebenen Offsets.|
|[CRgn::PtInRegion](#ptinregion)|Bestimmt, ob sich ein angegebener Punkt in der Region befindet.|
|[CRgn::RectInRegion](#rectinregion)|Bestimmt, ob sich ein Teil eines angegebenen Rechtecks innerhalb der Grenzen des Bereichs befindet.|
|[CRgn::SetRectRgn](#setrectrgn)|Legt `CRgn` das Objekt auf den angegebenen rechteckigen Bereich fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRgn::operator HRGN](#operator_hrgn)|Gibt das im `CRgn` Objekt enthaltene Windows-Handle zurück.|

## <a name="remarks"></a>Bemerkungen

Ein Bereich ist ein elliptischer oder polygonaler Bereich innerhalb eines Fensters. Um Regionen zu verwenden, verwenden `CRgn` Sie die Memberfunktionen der Klasse `CDC`mit den Clipping-Funktionen, die als Member der Klasse definiert sind.

Die Memberfunktionen `CRgn` zum Erstellen, Ändern und Abrufen von Informationen über das Regionsobjekt, für das sie aufgerufen werden.

Weitere Informationen zur `CRgn`Verwendung finden Sie unter [Grafikobjekte](../../mfc/graphic-objects.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>Anforderungen

**Header:** afxwin.h

## <a name="crgncombinergn"></a><a name="combinergn"></a>CRgn::CombineRgn

Erstellt eine neue GDI-Region, indem zwei vorhandene Regionen kombiniert werden.

```
int CombineRgn(
    CRgn* pRgn1,
    CRgn* pRgn2,
    int nCombineMode);
```

### <a name="parameters"></a>Parameter

*pRgn1*<br/>
Identifiziert eine vorhandene Region.

*pRgn2*<br/>
Identifiziert eine vorhandene Region.

*nCombineMode*<br/>
Gibt den Vorgang an, der beim Kombinieren der beiden Quellbereiche ausgeführt werden soll. Es kann einer der folgenden Werte sein:

- RGN_AND Verwendet überlappende Bereiche beider Regionen (Schnittpunkt).

- RGN_COPY Erstellt eine Kopie von Region 1 (identifiziert durch *pRgn1*).

- RGN_DIFF Erstellt eine Region, die aus den Gebieten der Region 1 (identifiziert durch *pRgn1*) besteht, die nicht Teil von Region 2 sind (identifiziert durch *pRgn2*).

- RGN_OR Kombiniert beide Regionen in ihrer Gesamtheit (Union).

- RGN_XOR Kombiniert beide Bereiche, entfernt jedoch überlappende Bereiche.

### <a name="return-value"></a>Rückgabewert

Gibt den Typ der resultierenden Region an. Es kann sich um einen der folgenden Werte handeln:

- COMPLEXREGION Neue Region hat sich überlappende Grenzen.

- FEHLER Keine neue Region erstellt.

- NULLREGION Neue Region ist leer.

- SIMPLEREGION Neue Region hat keine überlappenden Grenzen.

### <a name="remarks"></a>Bemerkungen

Die Regionen werden wie angegeben durch *nCombineMode*kombiniert.

Die beiden angegebenen Bereiche werden kombiniert, und das `CRgn` resultierende Bereichshandle wird im Objekt gespeichert. Daher wird jeder Bereich, `CRgn` der im Objekt gespeichert ist, durch den kombinierten Bereich ersetzt.

Die Größe einer Region ist auf 32.767 durch 32.767 logische Einheiten oder 64K Speicher begrenzt, je nach Größe kleiner.

Verwenden Sie [CopyRgn,](#copyrgn) um einfach eine Region in eine andere Region zu kopieren.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

## <a name="crgncopyrgn"></a><a name="copyrgn"></a>CRgn::CopyRgn

Kopiert den von *pRgnSrc* `CRgn` definierten Bereich in das Objekt.

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>Parameter

*pRgnSrc*<br/>
Identifiziert eine vorhandene Region.

### <a name="return-value"></a>Rückgabewert

Gibt den Typ der resultierenden Region an. Es kann sich um einen der folgenden Werte handeln:

- COMPLEXREGION Neue Region hat sich überlappende Grenzen.

- FEHLER Keine neue Region erstellt.

- NULLREGION Neue Region ist leer.

- SIMPLEREGION Neue Region hat keine überlappenden Grenzen.

### <a name="remarks"></a>Bemerkungen

Der neue Bereich ersetzt den Bereich, der `CRgn` zuvor im Objekt gespeichert war. Diese Funktion ist ein Sonderfall der [CombineRgn-Memberfunktion.](#combinergn)

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CRgn::CreateEllipticRgn](#createellipticrgn).

## <a name="crgncreateellipticrgn"></a><a name="createellipticrgn"></a>CRgn::CreateEllipticRgn

Erstellt einen elliptischen Bereich.

```
BOOL CreateEllipticRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>Parameter

*x1*<br/>
Gibt die logische x-Koordinate der oberen linken Ecke des umgrenzenden Rechtecks der Ellipse an.

*y1*<br/>
Gibt die logische y-Koordinate der oberen linken Ecke des umgrenzenden Rechtecks der Ellipse an.

*x2*<br/>
Gibt die logische x-Koordinate der unteren rechten Ecke des umgrenzenden Rechtecks der Ellipse an.

*y2*<br/>
Gibt die logische y-Koordinate der unteren rechten Ecke des umgrenzenden Rechtecks der Ellipse an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Vorgang erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Der Bereich wird durch das umgebende Rechteck definiert, das durch *x1*, *y1*, *x2*und *y2*angegeben wird. Der Bereich wird `CRgn` im Objekt gespeichert.

Die Größe einer Region ist auf 32.767 durch 32.767 logische Einheiten oder 64K Speicher begrenzt, je nach Größe kleiner.

Wenn sie die Verwendung eines `CreateEllipticRgn` mit der Funktion erstellten Bereichs abgeschlossen hat, `DeleteObject` sollte eine Anwendung den Bereich aus dem Gerätekontext auswählen und die Funktion verwenden, um ihn zu entfernen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

## <a name="crgncreateellipticrgnindirect"></a><a name="createellipticrgnindirect"></a>CRgn::CreateEllipticRgnIndirect

Erstellt einen elliptischen Bereich.

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parameter

*lpRect*<br/>
Zeigt auf `RECT` eine `CRect` Struktur oder ein Objekt, das die logischen Koordinaten der oberen linken und unteren rechten Ecke des umgrenzenden Rechtecks der Ellipse enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Vorgang erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Der Bereich wird durch die Struktur oder das Objekt definiert, `CRgn` auf das *lpRect* zeigt, und wird im Objekt gespeichert.

Die Größe einer Region ist auf 32.767 durch 32.767 logische Einheiten oder 64K Speicher begrenzt, je nach Größe kleiner.

Wenn sie die Verwendung eines `CreateEllipticRgnIndirect` mit der Funktion erstellten Bereichs abgeschlossen hat, `DeleteObject` sollte eine Anwendung den Bereich aus dem Gerätekontext auswählen und die Funktion verwenden, um ihn zu entfernen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CRgn::CreateRectRgnIndirect](#createrectrgnindirect).

## <a name="crgncreatefromdata"></a><a name="createfromdata"></a>CRgn::CreateFromData

Erstellt eine Region aus der angegebenen Region und Transformationsdaten.

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>Parameter

*lpXForm*<br/>
Zeigt auf eine [XFORM](/windows/win32/api/wingdi/ns-wingdi-xform)ata-Struktur, die die Transformation definiert, die für die Region ausgeführt werden soll. Wenn dieser Zeiger NULL ist, wird die Identitätstransformation verwendet.

*nCount*<br/>
Gibt die Anzahl der Bytes an, auf die *pRgnData*zeigt.

*pRgnData*<br/>
Verweist auf eine [RGNDATA-Datenstruktur,](/windows/win32/api/wingdi/ns-wingdi-rgndata) die die Regionsdaten enthält.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Bemerkungen

Eine Anwendung kann Daten für eine `CRgn::GetRegionData` Region abrufen, indem sie die Funktion aufruft.

## <a name="crgncreatefrompath"></a><a name="createfrompath"></a>CRgn::CreateFromPath

Erstellt einen Bereich aus dem Pfad, der im angegebenen Gerätekontext ausgewählt ist.

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>Parameter

*pDC*<br/>
Identifiziert einen Gerätekontext, der einen geschlossenen Pfad enthält.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Bemerkungen

Der vom *pDC-Parameter* identifizierte Gerätekontext muss einen geschlossenen Pfad enthalten. Nachdem `CreateFromPath` ein Pfad in einen Bereich konvertiert wurde, verwirft Windows den geschlossenen Pfad aus dem Gerätekontext.

## <a name="crgncreatepolygonrgn"></a><a name="createpolygonrgn"></a>CRgn::PolygonRgn erstellen

Erstellt einen polygonalen Bereich.

```
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,
    int nCount,
    int nMode);
```

### <a name="parameters"></a>Parameter

*lpPoints*<br/>
Verweist auf ein `POINT` Array von `CPoint` Strukturen oder ein Array von Objekten. Jede Struktur gibt die x-Koordinate und y-Koordinate eines Scheitelpunkts des Polygons an. Die `POINT` Struktur hat die folgende Form:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*nCount*<br/>
Gibt die Anzahl `POINT` der `CPoint` Strukturen oder Objekte im Array an, auf die *lpPoints*verweist.

*nMode*<br/>
Gibt den Füllmodus für die Region an. Dieser Parameter kann entweder ALTERNATE oder WINDING sein.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Vorgang erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Das System schließt das Polygon bei Bedarf automatisch, indem es eine Linie vom letzten Scheitelpunkt zum ersten Zeichen zeichnet. Der resultierende Bereich wird `CRgn` im Objekt gespeichert.

Die Größe einer Region ist auf 32.767 durch 32.767 logische Einheiten oder 64K Speicher begrenzt, je nach Größe kleiner.

Wenn der Polygonfüllmodus ALTERNATE ist, füllt das System den Bereich zwischen ungeraden und geraden Polygonseiten auf jeder Scanlinie. Das heißt, das System füllt den Bereich zwischen der ersten und zweiten Seite, zwischen der dritten und vierten Seite usw.

Wenn der Polygonfüllmodus WINDING ist, verwendet das System die Richtung, in der eine Figur gezeichnet wurde, um zu bestimmen, ob ein Bereich gefüllt werden soll. Jedes Liniensegment in einem Polygon wird entweder im Uhrzeigersinn oder gegen den Uhrzeigersinn gezeichnet. Wenn eine imaginäre Linie, die von einem geschlossenen Bereich nach außen nach einer Figur gezogen wird, durch ein Liniensegment im Uhrzeigersinn verläuft, wird eine Anzahl erhöht. Wenn die Linie ein Gegen-Uhrzeigerz-Liniensegment durchläuft, wird die Anzahl verringert. Der Bereich wird gefüllt, wenn die Anzahl ungleich Null ist, wenn die Linie die Außenseite der Abbildung erreicht.

Wenn eine Anwendung mit einer Region `CreatePolygonRgn` fertig ist, die mit der Funktion erstellt `DeleteObject` wurde, sollte sie den Bereich aus dem Gerätekontext auswählen und die Funktion verwenden, um sie zu entfernen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

## <a name="crgncreatepolypolygonrgn"></a><a name="createpolypolygonrgn"></a>CRgn::CreatePolyPolygonRgn

Erstellt einen Bereich, der aus einer Reihe geschlossener Polygone besteht.

```
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,
    LPINT lpPolyCounts,
    int nCount,
    int nPolyFillMode);
```

### <a name="parameters"></a>Parameter

*lpPoints*<br/>
Zeigt auf ein `POINT` Array von `CPoint` Strukturen oder ein Array von Objekten, das die Scheitelpunkte der Polygone definiert. Jedes Polygon muss explizit geschlossen werden, da das System sie nicht automatisch schließt. Die Polygone werden fortlaufend angegeben. Die `POINT` Struktur hat die folgende Form:

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyCounts*<br/>
Zeigt auf ein Array von ganzzahlenden Dateien. Die erste ganze Zahl gibt die Anzahl der Scheitelpunkte im ersten Polygon im *lpPoints-Array* an, die zweite ganze Zahl gibt die Anzahl der Scheitelpunkte im zweiten Polygon usw. an.

*nCount*<br/>
Gibt die Gesamtzahl der ganzzahlrigen im *lpPolyCounts-Array* an.

*nPolyFillMode*<br/>
Gibt den Polygonfüllmodus an. Dieser Wert kann entweder ALTERNATE oder WINDING sein.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Vorgang erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Der resultierende Bereich wird `CRgn` im Objekt gespeichert.

Die Polygone können getrennt sein oder sich überlappen.

Die Größe einer Region ist auf 32.767 durch 32.767 logische Einheiten oder 64K Speicher begrenzt, je nach Größe kleiner.

Wenn der Polygonfüllmodus ALTERNATE ist, füllt das System den Bereich zwischen ungeraden und geraden Polygonseiten auf jeder Scanlinie. Das heißt, das System füllt den Bereich zwischen der ersten und zweiten Seite, zwischen der dritten und vierten Seite usw.

Wenn der Polygonfüllmodus WINDING ist, verwendet das System die Richtung, in der eine Figur gezeichnet wurde, um zu bestimmen, ob ein Bereich gefüllt werden soll. Jedes Liniensegment in einem Polygon wird entweder im Uhrzeigersinn oder gegen den Uhrzeigersinn gezeichnet. Wenn eine imaginäre Linie, die von einem geschlossenen Bereich nach außen nach einer Figur gezogen wird, durch ein Liniensegment im Uhrzeigersinn verläuft, wird eine Anzahl erhöht. Wenn die Linie ein Gegen-Uhrzeigerz-Liniensegment durchläuft, wird die Anzahl verringert. Der Bereich wird gefüllt, wenn die Anzahl ungleich Null ist, wenn die Linie die Außenseite der Abbildung erreicht.

Wenn eine Anwendung mit einer Region `CreatePolyPolygonRgn` fertig ist, die mit der Funktion erstellt wurde, sollte sie den Bereich aus dem Gerätekontext auswählen und die [Memberfunktion CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) verwenden, um sie zu entfernen.

## <a name="crgncreaterectrgn"></a><a name="createrectrgn"></a>CRgn::CreateRectRgn

Erstellt einen rechteckigen Bereich, `CRgn` der im Objekt gespeichert ist.

```
BOOL CreateRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>Parameter

*x1*<br/>
Gibt die logische x-Koordinate der oberen linken Ecke des Bereichs an.

*y1*<br/>
Gibt die logische y-Koordinate der oberen linken Ecke des Bereichs an.

*x2*<br/>
Gibt die logische x-Koordinate der unteren rechten Ecke des Bereichs an.

*y2*<br/>
Gibt die logische y-Koordinate der unteren rechten Ecke des Bereichs an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Vorgang erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Größe einer Region ist auf 32.767 durch 32.767 logische Einheiten oder 64K Speicher begrenzt, je nach Größe kleiner.

Wenn die Verwendung einer von `CreateRectRgn`erstellten Region abgeschlossen ist, sollte eine Anwendung die [Memberfunktion CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) verwenden, um den Bereich zu entfernen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

Ein weiteres Beispiel finden Sie unter [CRgn::CombineRgn](#combinergn).

## <a name="crgncreaterectrgnindirect"></a><a name="createrectrgnindirect"></a>CRgn::CreateRectRgnIndirect

Erstellt einen rechteckigen Bereich, `CRgn` der im Objekt gespeichert ist.

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>Parameter

*lpRect*<br/>
Zeigt auf `RECT` eine `CRect` Struktur oder ein Objekt, das die logischen Koordinaten der oberen linken und unteren rechten Ecke des Bereichs enthält. Die `RECT` Struktur hat die folgende Form:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Vorgang erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Größe einer Region ist auf 32.767 durch 32.767 logische Einheiten oder 64K Speicher begrenzt, je nach Größe kleiner.

Wenn die Verwendung einer von `CreateRectRgnIndirect`erstellten Region abgeschlossen ist, sollte eine Anwendung die [Memberfunktion CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) verwenden, um den Bereich zu entfernen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

## <a name="crgncreateroundrectrgn"></a><a name="createroundrectrgn"></a>CRgn::CreateRoundRectRgn

Erstellt einen rechteckigen Bereich mit abgerundeten Ecken, der `CRgn` im Objekt gespeichert ist.

```
BOOL CreateRoundRectRgn(
    int x1,
    int y1,
    int x2,
    int y2,
    int x3,
    int y3);
```

### <a name="parameters"></a>Parameter

*x1*<br/>
Gibt die logische x-Koordinate der oberen linken Ecke des Bereichs an.

*y1*<br/>
Gibt die logische y-Koordinate der oberen linken Ecke des Bereichs an.

*x2*<br/>
Gibt die logische x-Koordinate der unteren rechten Ecke des Bereichs an.

*y2*<br/>
Gibt die logische y-Koordinate der unteren rechten Ecke des Bereichs an.

*x3*<br/>
Gibt die Breite der Ellipse an, die zum Erstellen der abgerundeten Ecken verwendet wird.

*y3*<br/>
Gibt die Höhe der Ellipse an, die zum Erstellen der abgerundeten Ecken verwendet wird.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Vorgang erfolgreich war; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die Größe einer Region ist auf 32.767 durch 32.767 logische Einheiten oder 64K Speicher begrenzt, je nach Größe kleiner.

Wenn eine Anwendung mit einer Region `CreateRoundRectRgn` fertig ist, die mit der Funktion erstellt wurde, sollte sie den Bereich aus dem Gerätekontext auswählen und die [Memberfunktion CGDIObject::DeleteObject](../../mfc/reference/cgdiobject-class.md#deleteobject) verwenden, um sie zu entfernen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

## <a name="crgncrgn"></a><a name="crgn"></a>CRgn::CRgn

Erstellt ein `CRgn`-Objekt.

```
CRgn();
```

### <a name="remarks"></a>Bemerkungen

Der `m_hObject` Datenmember enthält erst dann einen gültigen Windows-GDI-Bereich, wenn `CRgn` das Objekt mit einer oder mehreren anderen Memberfunktionen initialisiert wurde.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CRgn::CreateRoundRectRgn](#createroundrectrgn).

## <a name="crgnequalrgn"></a><a name="equalrgn"></a>CRgn::EqualRgn

Bestimmt, ob der angegebene Bereich dem `CRgn` im Objekt gespeicherten Bereich entspricht.

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>Parameter

*pRgn*<br/>
Identifiziert eine Region.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn die beiden Regionen äquivalent sind; andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

## <a name="crgnfromhandle"></a><a name="fromhandle"></a>CRgn::FromHandle

Gibt einen Zeiger `CRgn` auf ein Objekt zurück, wenn einem Windows-Bereich ein Handle übergeben wird.

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>Parameter

*hRgn*<br/>
Gibt ein Handle für eine Windows-Region an.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein `CRgn`-Objekt. Wenn die Funktion nicht erfolgreich war, lautet der Rückgabewert NULL.

### <a name="remarks"></a>Bemerkungen

Wenn `CRgn` ein Objekt noch nicht an das `CRgn` Handle angefügt ist, wird ein temporäres Objekt erstellt und angefügt. Dieses `CRgn` temporäre Objekt ist nur gültig, bis die Anwendung das nächste Mal Leerlaufzeit in ihrer Ereignisschleife hat, zu diesem Zeitpunkt alle temporären Grafikobjekte gelöscht werden. Eine andere Möglichkeit, dies zu sagen, ist, dass das temporäre Objekt nur während der Verarbeitung einer Fensternachricht gültig ist.

## <a name="crgngetregiondata"></a><a name="getregiondata"></a>CRgn::GetRegionData

Füllt den angegebenen Puffer mit Daten, die die Region beschreiben.

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>Parameter

*lpRgnData*<br/>
Verweist auf eine [RGNDATA-Datenstruktur,](/windows/win32/api/wingdi/ns-wingdi-rgndata) die die Informationen empfängt. Wenn dieser Parameter NULL ist, enthält der Rückgabewert die Anzahl der Bytes, die für die Regionsdaten benötigt werden.

*nCount*<br/>
Gibt die Größe des *lpRgnData-Puffers* in Bytes an.

### <a name="return-value"></a>Rückgabewert

Wenn die Funktion erfolgreich ist und *nCount* eine ausreichende Anzahl von Bytes angibt, lautet der Rückgabewert immer *nCount*. Wenn die Funktion fehlschlägt oder *nCount* weniger als die ausreichende Anzahl von Bytes angibt, ist der Rückgabewert 0 (Fehler).

### <a name="remarks"></a>Bemerkungen

Diese Daten enthalten die Dimensionen der Rechtecke, aus denen sich der Bereich zusammensetzt. Diese Funktion wird in `CRgn::CreateFromData` Verbindung mit der Funktion verwendet.

## <a name="crgngetrgnbox"></a><a name="getrgnbox"></a>CRgn::GetRgnBox

Ruft die Koordinaten des umgrenzenden `CRgn` Rechtecks des Objekts ab.

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

*lpRect*<br/>
Zeigt auf `RECT` eine `CRect` Struktur oder ein Objekt, um die Koordinaten des umgrenzenden Rechtecks zu empfangen. Die `RECT` Struktur hat die folgende Form:

`typedef struct tagRECT {`

`int left;`

`int top;`

`int right;`

`int bottom;`

`} RECT;`

### <a name="return-value"></a>Rückgabewert

Gibt den Typ der Region an. Dabei kann es sich um einen der folgenden Werte handeln:

- COMPLEXREGION hat überlappende Grenzen.

- NULLREGION Region ist leer.

- Das `CRgn` ERROR-Objekt gibt keinen gültigen Bereich an.

- DIE Region SIMPLEREGION hat keine überlappenden Grenzen.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CRgn::CreatePolygonRgn](#createpolygonrgn).

## <a name="crgnoffsetrgn"></a><a name="offsetrgn"></a>CRgn::OffsetRgn

Verschiebt den im `CRgn` Objekt gespeicherten Bereich um die angegebenen Offsets.

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>Parameter

*X*<br/>
Gibt die Anzahl der Einheiten an, die nach links oder rechts verschoben werden sollen.

*y*<br/>
Gibt die Anzahl der Einheiten an, die nach oben oder unten verschoben werden sollen.

*Punkt*<br/>
Die x-Koordinate des *Punkts* gibt die Anzahl der Einheiten an, die nach links oder rechts verschoben werden sollen. Die y-Koordinate des *Punkts* gibt die Anzahl der Einheiten an, die nach oben oder unten verschoben werden sollen. Der *Punktparameter* kann `POINT` entweder eine `CPoint` Struktur oder ein Objekt sein.

### <a name="return-value"></a>Rückgabewert

Der Typ der neuen Region. Es kann einer der folgenden Werte sein:

- COMPLEXREGION hat überlappende Grenzen.

- Das FEHLERbereichshandle ist ungültig.

- NULLREGION Region ist leer.

- DIE Region SIMPLEREGION hat keine überlappenden Grenzen.

### <a name="remarks"></a>Bemerkungen

Die Funktion verschiebt die *Bereichs-x-Einheiten* entlang der x-Achse und *y-Einheiten* entlang der y-Achse.

Die Koordinatenwerte einer Region müssen kleiner oder gleich 32.767 und größer oder gleich -32.768 sein. Die *parameter x* und *y* müssen sorgfältig ausgewählt werden, um ungültige Regionskoordinaten zu verhindern.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CRgn::CreateEllipticRgn](#createellipticrgn).

## <a name="crgnoperator-hrgn"></a><a name="operator_hrgn"></a>CRgn::operator HRGN

Verwenden Sie diesen Operator, um das `CRgn` angefügte Windows GDI-Handle des Objekts abzubekommen.

```
operator HRGN() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn erfolgreich, ein Handle für das Windows `CRgn` GDI-Objekt, das durch das Objekt dargestellt wird; andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Dieser Operator ist ein Gießoperator, der die direkte Verwendung eines HRGN-Objekts unterstützt.

Weitere Informationen zur Verwendung von Grafikobjekten finden Sie im Artikel [Grafikobjekte](/windows/win32/gdi/graphic-objects) im Windows SDK.

## <a name="crgnptinregion"></a><a name="ptinregion"></a>CRgn::PtInRegion

Überprüft, ob sich der von *x* und *y* angegebene Punkt in dem im `CRgn` Objekt gespeicherten Bereich befindet.

```
BOOL PtInRegion(
    int x,
    int y) const;

BOOL PtInRegion(POINT point) const;
```

### <a name="parameters"></a>Parameter

*X*<br/>
Gibt die logische x-Koordinate des zu testenden Punktes an.

*y*<br/>
Gibt die logische y-Koordinate des zu testenden Punkts an.

*Punkt*<br/>
Die x- und y-Koordinaten des *Punkts* geben die x- und y-Koordinaten des Punkts an, um den Wert von zu testen. Der *Punktparameter* kann `POINT` entweder eine `CPoint` Struktur oder ein Objekt sein.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn sich der Punkt in der Region befindet; andernfalls 0.

## <a name="crgnrectinregion"></a><a name="rectinregion"></a>CRgn::RectInRegion

Bestimmt, ob sich ein Teil des von *lpRect* angegebenen Rechtecks `CRgn` innerhalb der Grenzen des im Objekt gespeicherten Bereichs befindet.

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>Parameter

*lpRect*<br/>
Zeigt auf `RECT` eine `CRect` Struktur oder ein Objekt. Die `RECT` Struktur hat die folgende Form:

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn ein Teil des angegebenen Rechtecks innerhalb der Grenzen des Bereichs liegt; andernfalls 0.

## <a name="crgnsetrectrgn"></a><a name="setrectrgn"></a>CRgn::SetRectRgn

Erstellt einen rechteckigen Bereich.

```
void SetRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);

void SetRectRgn(LPCRECT lpRect);
```

### <a name="parameters"></a>Parameter

*x1*<br/>
Gibt die x-Koordinate der oberen linken Ecke des rechteckigen Bereichs an.

*y1*<br/>
Gibt die y-Koordinate der oberen linken Ecke des rechteckigen Bereichs an.

*x2*<br/>
Gibt die x-Koordinate der unteren rechten Ecke des rechteckigen Bereichs an.

*y2*<br/>
Gibt die y-Koordinate der unteren rechten Ecke des rechteckigen Bereichs an.

*lpRect*<br/>
Gibt den rechteckigen Bereich an. Kann entweder ein Zeiger `RECT` auf eine `CRect` Struktur oder ein Objekt sein.

### <a name="remarks"></a>Bemerkungen

Im Gegensatz zu [CreateRectRgn](#createrectrgn)weist es jedoch keinen zusätzlichen Speicher aus dem lokalen Windows-Anwendungsheap zu. Stattdessen wird der Fürden zugewiesene Speicherplatz `CRgn` für den im Objekt gespeicherten Bereich verwendet. Dies bedeutet, dass das `CRgn` Objekt bereits vor dem `SetRectRgn`Aufruf mit einer gültigen Windows-Region initialisiert wurde. Die von *x1*, *y1*, *x2*und *y2* angegebenen Punkte geben die Mindestgröße des zugewiesenen Speicherplatzes an.

Verwenden Sie diese `CreateRectRgn` Funktion anstelle der Memberfunktion, um Aufrufe an den lokalen Speicher-Manager zu vermeiden.

## <a name="see-also"></a>Siehe auch

[CWnd-Klasse](../../mfc/reference/cwnd-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)

---
title: CRect-Klasse
ms.date: 11/06/2018
f1_keywords:
- CRect
- ATLTYPES/ATL::CRect
- ATLTYPES/ATL::CRect::CRect
- ATLTYPES/ATL::CRect::BottomRight
- ATLTYPES/ATL::CRect::CenterPoint
- ATLTYPES/ATL::CRect::CopyRect
- ATLTYPES/ATL::CRect::DeflateRect
- ATLTYPES/ATL::CRect::EqualRect
- ATLTYPES/ATL::CRect::Height
- ATLTYPES/ATL::CRect::InflateRect
- ATLTYPES/ATL::CRect::IntersectRect
- ATLTYPES/ATL::CRect::IsRectEmpty
- ATLTYPES/ATL::CRect::IsRectNull
- ATLTYPES/ATL::CRect::MoveToX
- ATLTYPES/ATL::CRect::MoveToXY
- ATLTYPES/ATL::CRect::MoveToY
- ATLTYPES/ATL::CRect::NormalizeRect
- ATLTYPES/ATL::CRect::OffsetRect
- ATLTYPES/ATL::CRect::PtInRect
- ATLTYPES/ATL::CRect::SetRect
- ATLTYPES/ATL::CRect::SetRectEmpty
- ATLTYPES/ATL::CRect::Size
- ATLTYPES/ATL::CRect::SubtractRect
- ATLTYPES/ATL::CRect::TopLeft
- ATLTYPES/ATL::CRect::UnionRect
- ATLTYPES/ATL::CRect::Width
helpviewer_keywords:
- LPCRECT data type
- CRect class
- LPRECT operator
- RECT structure
ms.assetid: dee4e752-15d6-4db4-b68f-1ad65b2ed6ca
ms.openlocfilehash: c59ed587e2c8e51f5c08a026a7ee0b9d0af25168
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317708"
---
# <a name="crect-class"></a>CRect-Klasse

Ähnlich wie bei einer Windows [RECT-Struktur.](/windows/win32/api/windef/ns-windef-rect)

## <a name="syntax"></a>Syntax

```
class CRect : public tagRECT
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRect::CRect](#crect)|Erstellt ein `CRect`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRect::BottomRight](#bottomright)|Gibt den unteren rechten `CRect`Punkt von zurück.|
|[CRect::CenterPoint](#centerpoint)|Gibt den Mittelpunkt `CRect`von zurück.|
|[CRect::CopyRect](#copyrect)|Kopiert die Dimensionen eines `CRect`Quellrechtecks in .|
|[CRect::DeflateRect](#deflaterect)|Verringert die Breite und `CRect`Höhe von .|
|[CRect::EqualRect](#equalrect)|Bestimmt, `CRect` ob es dem angegebenen Rechteck entspricht.|
|[CRect::Höhe](#height)|Berechnet die Höhe `CRect`von .|
|[CRect::InflateRect](#inflaterect)|Erhöht die Breite `CRect`und Höhe von .|
|[CRect::IntersectRect](#intersectrect)|Legt `CRect` fest, dass der Schnittpunkt zweier Rechtecke ausgeglichen ist.|
|[CRect::IsRectEmpty](#isrectempty)|Bestimmt, `CRect` ob leer ist. `CRect`ist leer, wenn die Breite und/oder Höhe 0 ist.|
|[CRect::IsRectNull](#isrectnull)|Bestimmt, `top`ob `bottom` `left`die `right` Variablen , , und Member alle gleich 0 sind.|
|[CRect::MoveToX](#movetox)|Wechselt `CRect` zur angegebenen x-Koordinate.|
|[CRect::MoveToXY](#movetoxy)|Wechselt `CRect` zu den angegebenen x- und y-Koordinaten.|
|[CRect::MoveToY](#movetoy)|Wechselt `CRect` zur angegebenen y-Koordinate.|
|[CRect::NormalizeRect](#normalizerect)|Standardisiert die Höhe und `CRect`Breite von .|
|[CRect::OffsetRect](#offsetrect)|Wird `CRect` um die angegebenen Offsets verschoben.|
|[CRect::PtInRect](#ptinrect)|Bestimmt, ob der `CRect`angegebene Punkt innerhalb von liegt.|
|[CRect::SetRect](#setrect)|Legt die `CRect`Abmessungen von fest.|
|[CRect::SetRectEmpty](#setrectempty)|Legt `CRect` ein leeres Rechteck fest (alle Koordinaten gleich 0).|
|[CRect::Größe](#size)|Berechnet die Größe `CRect`von .|
|[CRect::SubtractRect](#subtractrect)|Subtrahiert ein Rechteck von einem anderen.|
|[CRect::TopLeft](#topleft)|Gibt den linken oberen `CRect`Punkt von zurück.|
|[CRect::UnionRect](#unionrect)|Legt `CRect` fest, dass die Vereinigung von zwei Rechtecken gleich ist.|
|[CRect::Breite](#width)|Berechnet die Breite `CRect`von .|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRect::Operator -](#operator_-)|Subtrahiert die angegebenen `CRect` Offsets `CRect` von oder `CRect`deflationiert und gibt die resultierende zurück.|
|[CRect::operator LPCRECT](#operator_lpcrect)|Konvertiert ein `CRect`-Element in ein `LPCRECT`-Element.|
|[CRect::operator LPRECT](#operator_lprect)|Konvertiert ein `CRect`-Element in ein `LPRECT`-Element.|
|[CRect::operator !=](#operator_neq)|Bestimmt, `CRect` ob es nicht gleich einem Rechteck ist.|
|[CRect::Operator&amp;](#operator_amp)|Erstellt den `CRect` Schnittpunkt und ein `CRect`Rechteck und gibt die resultierende zurück.|
|[CRect::Operator&amp;=](#operator_amp_eq)|Legt `CRect` fest, dass `CRect` der Schnittpunkt von und ein Rechteck gleich ist.|
|[CRect::Operator &#124;](#operator_or)|Erstellt die `CRect` Vereinigung von und ein `CRect`Rechteck und gibt die resultierende zurück.|
|[CRect::operator &#124;=](#operator_or_eq)|Legt `CRect` fest, dass `CRect` die Union von und ein Rechteck gleich ist.|
|[CRect::Operator +](#operator_add)|Fügt die angegebenen `CRect` Offsets zu `CRect` oder aufundwerden und gibt die resultierende `CRect`zurück.|
|[CRect::Operator +=](#operator_add_eq)|Fügt die angegebenen `CRect` Offsets zu `CRect`oder aufbläht .|
|[CRect::operator =](#operator_eq)|Kopiert die Abmessungen eines `CRect`Rechtecks in .|
|[CRect::operator -=](#operator_-_eq)|Subtrahiert die angegebenen `CRect` Offsets `CRect`von oder deflationiert .|
|[CRect::operator ==](#operator_eq_eq)|Bestimmt, `CRect` ob es sich um ein Rechteck handelt.|

## <a name="remarks"></a>Bemerkungen

`CRect`enthält auch Memberfunktionen `CRect` zum `RECT` Bearbeiten von Objekten und Windows-Strukturen.

Ein `CRect` Objekt kann als Funktionsparameter `RECT` übergeben `LPCRECT`werden, `LPRECT` wo immer eine Struktur, , oder übergeben werden kann.

> [!NOTE]
> Diese Klasse wird `tagRECT` von der Struktur abgeleitet. (Der `tagRECT` Name ist ein weniger gebräuchgroßer Name für die `RECT` Struktur.) Dies bedeutet, dass`left` `top`die `right`Datenmember ( , , und `bottom`) der `RECT` Struktur auf Datenmember von `CRect`zugreifen können.

A `CRect` enthält Elementvariablen, die die oberen linken und unteren rechten Punkte eines Rechtecks definieren.

Wenn Sie `CRect`eine angeben, müssen Sie darauf achten, sie so zu konstruieren, dass sie normalisiert wird, d. h., der Wert der linken Koordinate ist kleiner als die rechte und die oberseite kleiner als die untere. Beispielsweise definiert ein oberes linkes von (10,10) und unten rechts von (20,20) ein normalisiertes Rechteck, aber eine obere linke Von (20,20) und unten rechts von (10,10) definiert ein nicht normalisiertes Rechteck. Wenn das Rechteck nicht normalisiert wird, geben viele `CRect` Memberfunktionen möglicherweise falsche Ergebnisse zurück. (Eine Liste dieser Funktionen finden Sie unter [CRect::NormalizeRect.)](#normalizerect) Bevor Sie eine Funktion aufrufen, die normalisierte Rechtecke erfordert, können Sie `NormalizeRect` nicht normalisierte Rechtecke normalisieren, indem Sie die Funktion aufrufen.

Seien Sie vorsichtig, `CRect` wenn Sie a mit den [Memberfunktionen CDC::DPtoLP](../../mfc/reference/cdc-class.md#dptolp) und [CDC::LPtoDP](../../mfc/reference/cdc-class.md#lptodp) bearbeiten. Wenn der Zuordnungsmodus eines Anzeigekontexts so ist, dass `MM_LOENGLISH`die `CDC::DPtoLP` y-Ausdehnung negativ ist, wie in , transformiert die, `CRect` sodass ihr Oberteil größer als der Boden ist. Funktionen wie `Height` `Size` und geben dann negative Werte für `CRect`die Höhe des transformierten zurück, und das Rechteck wird nicht normalisiert.

Bei der `CRect` Verwendung überladener Operatoren `CRect`muss der erste Operand ein ; die zweite kann entweder eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) oder ein `CRect` Objekt sein.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`tagRECT`

`CRect`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atltypes.h

## <a name="crectbottomright"></a><a name="bottomright"></a>CRect::BottomRight

Die Koordinaten werden als Verweis auf ein [CPoint-Objekt](cpoint-class.md) zurückgegeben, das in `CRect`enthalten ist.

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Koordinaten der rechten unteren Ecke des Rechtecks.

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion können Sie die rechte untere Ecke des Rechtecks abrufen oder festlegen. Legen Sie die Ecke fest, indem Sie diese Funktion auf der linken Seite des Zuweisungsoperators verwenden.

### <a name="example"></a>Beispiel

```cpp
// use BottomRight() to retrieve the bottom
// right POINT
CRect rect(210, 150, 350, 900);
CPoint ptDown;

ptDown = rect.BottomRight();

// ptDown is now set to (350, 900)
ASSERT(ptDown == CPoint(350, 900));

// or, use BottomRight() to set the bottom
// right POINT
CRect rect2(10, 10, 350, 350);
CPoint ptLow(180, 180);

CRect rect2(10, 10, 350, 350);
CPoint ptLow(180, 180);
rect2.BottomRight() = ptLow;

// rect2 is now (10, 10, 180, 180)
ASSERT(rect2 == CRect(10, 10, 180, 180));
```

## <a name="crectcenterpoint"></a><a name="centerpoint"></a>CRect::CenterPoint

Berechnet den Mittelpunkt `CRect` von, indem der linke und rechte Wert hinzugefügt und durch zwei geteilt, die oberen und unteren Werte hinzugefügt und durch zwei geteilt werden.

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein `CPoint` Objekt, das den `CRect`Mittelpunkt von .

### <a name="example"></a>Beispiel

```cpp
// Code from this OnPaint() implementation can be pasted into your own application
// to draw lines that would look like a letter "Y" within your dialog.
void CMyDlg::OnPaint()
{
    CPaintDC dc(this);

    // device context for painting

    // get the size and position of the client area of
    // your window

    CRect rect;
    GetClientRect(&rect);

    // Move the current pen to the top left of the window. We call the
    // TopLeft() member of CRect here and it returns a CPoint object we
    // pass to the override of CDC::MoveTo() that accepts a CPoint.

    dc.MoveTo(rect.TopLeft());

    // Draw a line from the top left to the center of the window.
    // CenterPoint() gives us the middle point of the window as a
    // CPoint, and since CDC::LineTo() has an override that accepts a
    // CPoint, we can just pass it along.

    dc.LineTo(rect.CenterPoint());

    // Now, draw a line to the top right of the window. There's no
    // CRect member which returns a CPoint for the top right of the
    // window, so we'll reference the CPoint members directly and call
    // the CDC::LineTo() override which takes two integers.

    dc.LineTo(rect.right, rect.top);

    // The top part of the "Y" is drawn. Now, we'll draw the stem. We
    // start from the center point.

    dc.MoveTo(rect.CenterPoint());

    // and then draw to the middle of the bottom edge of the window.
    // We'll get the x-coordinate from the x member of the CPOINT
    // returned by CenterPoint(), and the y value comes directly from
    // the rect.

    dc.LineTo(rect.CenterPoint().x, rect.bottom);
}
```

## <a name="crectcopyrect"></a><a name="copyrect"></a>CRect::CopyRect

Kopiert `lpSrcRect` das `CRect`Rechteck in .

```
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>Parameter

*lpSrcRect*<br/>
Zeigt auf die [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) oder `CRect` das zu kopierende Objekt.

### <a name="example"></a>Beispiel

```cpp
CRect rectSource(35, 10, 125, 10);
CRect rectDest;

rectDest.CopyRect(&rectSource);

// rectDest is now set to (35, 10, 125, 10)

RECT rectSource2;
rectSource2.left = 0;
rectSource2.top = 0;
rectSource2.bottom = 480;
rectSource2.right = 640;

rectDest.CopyRect(&rectSource2);

// works against RECT structures, too!
// rectDest is now set to (0, 0, 640, 480)
```

## <a name="crectcrect"></a><a name="crect"></a>CRect::CRect

Erstellt ein `CRect`-Objekt.

```
CRect() throw();
CRect(int l, int t, int r, int b) throw();
CRect(const RECT& srcRect) throw();
CRect(LPCRECT lpSrcRect) throw();
CRect(POINT point, SIZE size) throw();
CRect(POINT topLeft, POINT bottomRight) throw();
```

### <a name="parameters"></a>Parameter

*L*<br/>
Gibt die linke `CRect`Position von an.

*T*<br/>
Gibt den oberen `CRect`Rand von an.

*R*<br/>
Gibt die richtige `CRect`Position von an.

*B*<br/>
Gibt den unteren `CRect`Rand von an.

*Srcrect*<br/>
Bezieht sich auf die [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) mit den Koordinaten für `CRect`.

*lpSrcRect*<br/>
Zeigt auf `RECT` die Struktur `CRect`mit den Koordinaten für .

*Punkt*<br/>
Gibt den Ursprungspunkt für das zu errichtende Rechteck an. Entspricht der linken oberen Ecke.

*Größe*<br/>
Gibt die Verschiebung von der linken oberen Ecke in die untere rechte Ecke des zu errichtenden Rechtecks an.

*topLeft*<br/>
Gibt die position oben `CRect`links von an.

*bottomRight*<br/>
Gibt die rechte Position `CRect`von unten rechts an.

### <a name="remarks"></a>Bemerkungen

Wenn keine Argumente `left`angegeben `top` `right`werden, `bottom` werden , , und Member nicht initialisiert.

Die `CRect``const RECT&`Konstruktoren ( ) und `CRect`(`LPCRECT`) führen eine [CopyRect](#copyrect)aus. Die anderen Konstruktoren initialisieren die Membervariablen des Objekts direkt.

### <a name="example"></a>Beispiel

```cpp
// default constructor doesn't initialize!
CRect rectUnknown;

// four-integers are left, top, right, and bottom
CRect rect(0, 0, 100, 50);
ASSERT(rect.Width() == 100);
ASSERT(rect.Height() == 50);

// Initialize from RECT structure
RECT sdkRect;
sdkRect.left = 0;
sdkRect.top = 0;
sdkRect.right = 100;
sdkRect.bottom = 50;

CRect rect2(sdkRect);
// by reference
CRect rect3(&sdkRect);

// by address
ASSERT(rect2 == rect);
ASSERT(rect3 == rect);

// from a point and a size
CPoint pt(0, 0);
CSize sz(100, 50);
CRect rect4(pt, sz);
ASSERT(rect4 == rect2);

// from two points
CPoint ptBottomRight(100, 50);
CRect rect5(pt, ptBottomRight);
ASSERT(rect5 == rect4);
```

## <a name="crectdeflaterect"></a><a name="deflaterect"></a>CRect::DeflateRect

`DeflateRect`entleert `CRect` sich, indem er seine Seiten in Richtung seines Zentrums bewegt.

```
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>Parameter

*X*<br/>
Gibt die Anzahl der Einheiten an, die `CRect`die linke und rechte Seite von entleeren sollen.

*y*<br/>
Gibt die Anzahl der Einheiten an, die `CRect`am oberen und unteren Rand von entleert werden sollen.

*Größe*<br/>
Eine [GRÖSSE](/windows/win32/api/windef/ns-windef-size) oder [CSize,](csize-class.md) die die `CRect`Anzahl der zu entleerenden Einheiten angibt. Der `cx` Wert gibt die Anzahl der Einheiten an, die `cy` die linke und rechte Seite deflationieren sollen, und der Wert gibt die Anzahl der Einheiten an, die oben und unten entleert werden sollen.

*lpRect*<br/>
Zeigt auf eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) oder `CRect` gibt die Anzahl der Einheiten an, die auf jeder Seite entschärft werden sollen.

*L*<br/>
Gibt die Anzahl der Einheiten an, `CRect`die die linke Seite von entleeren sollen.

*T*<br/>
Gibt die Anzahl der Einheiten an, `CRect`die am oberen Rand von entleert werden sollen.

*R*<br/>
Gibt die Anzahl der Einheiten an, `CRect`die die rechte Seite von entleeren sollen.

*B*<br/>
Gibt die Anzahl der Einheiten an, `CRect`die am unteren Rand von entleert werden sollen.

### <a name="remarks"></a>Bemerkungen

`DeflateRect` Fügt dazu Einheiten links und oben hinzu und subtrahiert Einheiten von rechts und unten. Die Parameter `DeflateRect` von sind signierte Werte; positive Werte `CRect` deflationieren und negative Werte blasen sie auf.

Die ersten beiden Überladungen entleeren `CRect` beide Paare von gegenüberliegenden Seiten von, `cx`so dass seine Gesamtbreite um das `cy`Zweifache *x* (oder ) verringert wird und seine Gesamthöhe um das Zweifache *y* (oder ) verringert wird. Die anderen beiden Überladungen `CRect` entleeren jede Seite unabhängig von den anderen.

### <a name="example"></a>Beispiel

```cpp
CRect rect(10, 10, 50, 50);
rect.DeflateRect(1, 2);
ASSERT(rect.left == 11 && rect.right == 49);
ASSERT(rect.top == 12 && rect.bottom == 48);

CRect rect2(10, 10, 50, 50);
CRect rectDeflate(1, 2, 3, 4);
rect2.DeflateRect(&rectDeflate);
ASSERT(rect2.left == 11 && rect2.right == 47);
ASSERT(rect2.top == 12 && rect2.bottom == 46);
```

## <a name="crectequalrect"></a><a name="equalrect"></a>CRect::EqualRect

Bestimmt, `CRect` ob es dem angegebenen Rechteck entspricht.

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parameter

*lpRect*<br/>
Zeigt auf eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) oder `CRect` ein Objekt, das die oberen linken und unteren rechten Eckkoordinaten eines Rechtecks enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die beiden Rechtecke die gleichen oberen, linken, unteren und rechten Werte aufweisen. andernfalls 0.

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, sonst schlägt diese Funktion fehl. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999, 6, 3);
ASSERT(rect1.EqualRect(rect2));
ASSERT(!rect1.EqualRect(rect3));
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect1.EqualRect(&test));
```

## <a name="crectheight"></a><a name="height"></a>CRect::Höhe

Berechnet die Höhe `CRect` von, indem der obere Wert vom unteren Wert subtrahiert wird.

```
int Height() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Höhe `CRect`von .

### <a name="remarks"></a>Bemerkungen

Der resultierende Wert kann negativ sein.

> [!NOTE]
> Das Rechteck muss normalisiert werden, sonst schlägt diese Funktion fehl. Sie können [NormalizeRect](#normalizerect) aufrufen, um das Rechteck zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

## <a name="crectinflaterect"></a><a name="inflaterect"></a>CRect::InflateRect

`InflateRect`aufbläht, `CRect` indem man seine Seiten von seinem Zentrum wegbewegt.

```
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>Parameter

*X*<br/>
Gibt die Anzahl der Einheiten an, die die `CRect`linke und rechte Seite von aufblasen sollen.

*y*<br/>
Gibt die Anzahl der Einheiten an, die `CRect`oben und unten von aufgeblasen werden sollen.

*Größe*<br/>
Eine [GRÖßE](/windows/win32/api/windef/ns-windef-size) oder [CSize,](csize-class.md) die die Anzahl `CRect`der Einheiten angibt, die aufgeblasen werden sollen. Der `cx` Wert gibt die Anzahl der Einheiten an, die `cy` die linke und rechte Seite aufblasen sollen, und der Wert gibt die Anzahl der Einheiten an, die oben und unten aufgeblasen werden sollen.

*lpRect*<br/>
Zeigt auf eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) oder `CRect` gibt die Anzahl der Einheiten an, die auf jeder Seite aufgeblasen werden sollen.

*L*<br/>
Gibt die Anzahl der Einheiten an, die `CRect`auf der linken Seite von aufgeblasen werden sollen.

*T*<br/>
Gibt die Anzahl der Einheiten an, `CRect`die am oberen Rand von aufgeblasen werden sollen.

*R*<br/>
Gibt die Anzahl der Einheiten an, die `CRect`die rechte Seite von aufblasen sollen.

*B*<br/>
Gibt die Anzahl der Einheiten an, `CRect`die am unteren Rand von aufgeblasen werden sollen.

### <a name="remarks"></a>Bemerkungen

Subtrahiert `InflateRect` dazu Einheiten von links und oben und fügt Einheiten nach rechts und unten hinzu. Die Parameter `InflateRect` von sind signierte Werte; positive Werte aufblasen `CRect` und negative Werte deflationieren sie.

Die ersten beiden Überladungen blasen beide `CRect` Paare von gegenüberliegenden Seiten auf, so `cx`dass ihre Gesamtbreite um das Zweifache `cy` *x* (oder ) und ihre Gesamthöhe um das Zweifache *y* (oder) erhöht wird. Die anderen beiden Überladungen blasen `CRect` jede Seite unabhängig von den anderen auf.

### <a name="example"></a>Beispiel

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

## <a name="crectintersectrect"></a><a name="intersectrect"></a>CRect::IntersectRect

Macht `CRect` einen Punktschnitt aus zwei vorhandenen Rechtecken.

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parameter

*lpRect1*<br/>
Zeigt auf eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) oder `CRect` ein Objekt, das ein Quellrechteck enthält.

*lpRect2*<br/>
Zeigt auf `RECT` eine `CRect` Struktur oder ein Objekt, das ein Quellrechteck enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Schnittpunkt nicht leer ist; 0, wenn der Schnittpunkt leer ist.

### <a name="remarks"></a>Bemerkungen

Der Schnittpunkt ist das größte Rechteck, das in beiden vorhandenen Rechtecken enthalten ist.

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, sonst schlägt diese Funktion fehl. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect rectOne(125,  0, 150, 200);
CRect rectTwo(0, 75, 350, 95);
CRect rectInter;

rectInter.IntersectRect(rectOne, rectTwo);
ASSERT(rectInter == CRect(125, 75, 150, 95));
// operator &= can do the same task:

CRect rectInter2 = rectOne;
rectInter2 &= rectTwo;
ASSERT(rectInter2 == CRect(125, 75, 150, 95));
```

## <a name="crectisrectempty"></a><a name="isrectempty"></a>CRect::IsRectEmpty

Bestimmt, `CRect` ob leer ist.

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert `CRect` ungleich Null, wenn leer ist; 0, `CRect` wenn nicht leer ist.

### <a name="remarks"></a>Bemerkungen

Ein Rechteck ist leer, wenn die Breite und/oder Höhe 0 oder negativ ist. Unterscheidet sich `IsRectNull`von , die bestimmt, ob alle Koordinaten des Rechtecks Null sind.

> [!NOTE]
> Das Rechteck muss normalisiert werden, sonst schlägt diese Funktion fehl. Sie können [NormalizeRect](#normalizerect) aufrufen, um das Rechteck zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
ASSERT(rectEmpty.IsRectEmpty());
```

## <a name="crectisrectnull"></a><a name="isrectnull"></a>CRect::IsRectNull

Bestimmt, ob die oberen, linken, `CRect` unteren und rechten Werte von alle gleich 0 sind.

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert `CRect`ungleich Null, wenn die oberen, linken, unteren und rechten Werte von 's gleich 0 sind. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Unterscheidet sich `IsRectEmpty`von , wodurch bestimmt wird, ob das Rechteck leer ist.

### <a name="example"></a>Beispiel

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectNull());
ASSERT(!rectSome.IsRectNull());
// note that null means _all_ zeros

CRect rectNotNull(0, 0, 35, 50);
ASSERT(!rectNotNull.IsRectNull());
```

## <a name="crectmovetox"></a><a name="movetox"></a>CRect::MoveToX

Rufen Sie diese Funktion auf, um das Rechteck in die absolute x-Koordinate zu verschieben, die durch *x*angegeben wird.

```
void MoveToX(int x) throw();
```

### <a name="parameters"></a>Parameter

*X*<br/>
Die absolute x-Koordinate für die obere linke Ecke des Rechtecks.

### <a name="example"></a>Beispiel

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

// rect is now (10, 0, 110, 100);
ASSERT(rect == CRect(10, 0, 110, 100));
```

## <a name="crectmovetoxy"></a><a name="movetoxy"></a>CRect::MoveToXY

Rufen Sie diese Funktion auf, um das Rechteck in die angegebenen absoluten x- und y-Koordinaten zu verschieben.

```
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>Parameter

*X*<br/>
Die absolute x-Koordinate für die obere linke Ecke des Rechtecks.

*y*<br/>
Die absolute y-Koordinate für die obere linke Ecke des Rechtecks.

*Punkt*<br/>
Eine `POINT` Struktur, die die absolute obere linke Ecke des Rechtecks angibt.

### <a name="example"></a>Beispiel

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
ASSERT(rect == CRect(10, 10, 110, 110));
```

## <a name="crectmovetoy"></a><a name="movetoy"></a>CRect::MoveToY

Rufen Sie diese Funktion auf, um das Rechteck in die von *y*angegebene absolute y-Koordinate zu verschieben.

```
void MoveToY(int y) throw();
```

### <a name="parameters"></a>Parameter

*y*<br/>
Die absolute y-Koordinate für die obere linke Ecke des Rechtecks.

### <a name="example"></a>Beispiel

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
ASSERT(rect == CRect(0, 10, 100, 110));
```

## <a name="crectnormalizerect"></a><a name="normalizerect"></a>CRect::NormalizeRect

Normalisiert, `CRect` so dass sowohl die Höhe als auch die Breite positiv sind.

```
void NormalizeRect() throw();
```

### <a name="remarks"></a>Bemerkungen

Das Rechteck wird für die Positionierung mit vier Quadranten normalisiert, die Windows normalerweise für Koordinaten verwendet. `NormalizeRect`vergleicht die oberen und unteren Werte und tauscht sie aus, wenn die Oberseite größer als die Unterseite ist. In ähnlicher Weise werden die linken und rechten Werte ausgetauscht, wenn die linke Werte größer als die rechte sind. Diese Funktion ist nützlich, wenn Sie mit verschiedenen Zuordnungsmodi und invertierten Rechtecken umgehen.

> [!NOTE]
> Die `CRect` folgenden Memberfunktionen erfordern normalisierte Rechtecke, um richtig zu funktionieren: [Höhe](#height), [Breite](#width), [Größe](#size), [IsRectEmpty](#isrectempty), [PtInRect](#ptinrect), [EqualRect](#equalrect), [UnionRect](#unionrect), [IntersectRect](#intersectrect), [SubtractRect](#subtractrect), [Operator ==](#operator_eq_eq), [Operator !=](#operator_neq), [Operator &#124;](#operator_or), Operator [&#124;=](#operator_or_eq), Operator [&](#operator_amp)und Operator [&=](#operator_amp_eq).

### <a name="example"></a>Beispiel

```cpp
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
rect2.NormalizeRect();
ASSERT(rect1 == rect2);
```

## <a name="crectoffsetrect"></a><a name="offsetrect"></a>CRect::OffsetRect

Wird `CRect` um die angegebenen Offsets verschoben.

```
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();
```

### <a name="parameters"></a>Parameter

*X*<br/>
Gibt den Betrag an, der nach links oder rechts verschoben werden soll. Es muss negativ sein, sich nach links zu bewegen.

*y*<br/>
Gibt den Betrag an, der nach oben oder unten verschoben werden soll. Es muss negativ sein, nach oben zu kommen.

*Punkt*<br/>
Enthält eine [POINT-Struktur](/windows/win32/api/windef/ns-windef-point) oder ein [CPoint-Objekt,](cpoint-class.md) das beide Dimensionen angibt, um die verschoben werden soll.

*Größe*<br/>
Enthält eine [SIZE-Struktur](/windows/win32/api/windef/ns-windef-size) oder ein [CSize-Objekt,](csize-class.md) das beide Dimensionen angibt, um die verschoben werden soll.

### <a name="remarks"></a>Bemerkungen

Verschiebt `CRect` *x-Einheiten* entlang der x-Achse und *y-Einheiten* entlang der y-Achse. Die *x-* und *y-Parameter* sind signierte Werte, sodass `CRect` sie nach links oder rechts und nach oben oder unten verschoben werden können.

### <a name="example"></a>Beispiel

```cpp
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

// rect is now (230, 230, 265, 265)
ASSERT(rect == CRect(230, 230, 265, 265));
```

## <a name="crectoperator-lpcrect-converts-a-crect-to-an-lpcrect"></a><a name="operator_lpcrect"></a>CRect::operator LPCRECT Konvertiert `CRect` a in ein [LPCRECT](../../mfc/reference/data-types-mfc.md).

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Funktion verwenden, benötigen Sie den**&** Operator Address-of ( ) nicht. Dieser Operator wird automatisch verwendet, `CRect` wenn Sie ein `LPCRECT`Objekt an eine Funktion übergeben, die eine erwartet.

## <a name="crectoperator-lprect"></a><a name="operator_lprect"></a>CRect::operator LPRECT

Konvertiert a `CRect` in ein [LPRECT](../../mfc/reference/data-types-mfc.md).

```
operator LPRECT() throw();
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Funktion verwenden, benötigen Sie den**&** Operator Address-of ( ) nicht. Dieser Operator wird automatisch verwendet, `CRect` wenn Sie ein `LPRECT`Objekt an eine Funktion übergeben, die eine erwartet.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CRect::operator LPCRECT](#operator_lpcrect).

## <a name="crectoperator-"></a><a name="operator_eq"></a>CRect::operator =

Weist *srcRect* `CRect`zu .

```
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>Parameter

*Srcrect*<br/>
Bezieht sich auf ein Quellrechteck. Kann ein [RECT](/windows/win32/api/windef/ns-windef-rect) oder `CRect`sein.

### <a name="example"></a>Beispiel

```cpp
CRect rect(0, 0, 127, 168);
CRect rect2;

rect2 = rect;
ASSERT(rect2 == CRect(0, 0, 127, 168));
```

## <a name="crectoperator-"></a><a name="operator_eq_eq"></a>CRect::operator ==

Bestimmt, `rect` ob `CRect` gleich ist, indem die Koordinaten der oberen linken und unteren rechten Ecke verglichen werden.

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Bezieht sich auf ein Quellrechteck. Kann ein [RECT](/windows/win32/api/windef/ns-windef-rect) oder `CRect`sein.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn gleich; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, sonst schlägt diese Funktion fehl. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999, 6, 3);
ASSERT(rect1 == rect2);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect1 == test);
```

## <a name="crectoperator-"></a><a name="operator_neq"></a>CRect::operator !=

Bestimmt, ob *Die* Korrektur `CRect` nicht gleich ist, indem die Koordinaten der oberen linken und unteren rechten Ecke verglichen werden.

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Bezieht sich auf ein Quellrechteck. Kann ein [RECT](/windows/win32/api/windef/ns-windef-rect) oder `CRect`sein.

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn nicht gleich; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, sonst schlägt diese Funktion fehl. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999,  6,  3);
ASSERT(rect1 != rect3);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect3 != test);
```

## <a name="crectoperator-"></a><a name="operator_add_eq"></a>CRect::Operator +=

Die ersten beiden `CRect` Überladungen werden um die angegebenen Offsets verschoben.

```
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Eine [POINT-Struktur](/windows/win32/api/windef/ns-windef-point) oder ein [CPoint-Objekt,](cpoint-class.md) das die Anzahl der Einheiten angibt, die das Rechteck verschieben sollen.

*Größe*<br/>
Eine [SIZE-Struktur](/windows/win32/api/windef/ns-windef-size) oder ein [CSize-Objekt,](csize-class.md) das die Anzahl der Einheiten angibt, die das Rechteck verschieben sollen.

*lpRect*<br/>
Zeigt auf eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) oder `CRect` ein OBJEKT, das die `CRect`Anzahl der Einheiten enthält, die auf jeder Seite von aufgeblasen werden sollen.

### <a name="remarks"></a>Bemerkungen

Die *x-* und *y-Werte* `cx` (oder und `CRect` `cy`) des Parameters werden zu hinzugefügt.

Die dritte Überladung `CRect` wird um die Anzahl der Einheiten aufgebläht, die in jedem Element des Parameters angegeben sind.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint  pt(35, 65);
CRect   rect2(135, 300, 235, 400);

rect1 += pt;
ASSERT(rect1 == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-_eq"></a>CRect::operator -=

Die ersten beiden `CRect` Überladungen werden um die angegebenen Offsets verschoben.

```
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Eine [POINT-Struktur](/windows/win32/api/windef/ns-windef-point) oder ein [CPoint-Objekt,](cpoint-class.md) das die Anzahl der Einheiten angibt, die das Rechteck verschieben sollen.

*Größe*<br/>
Eine [SIZE-Struktur](/windows/win32/api/windef/ns-windef-size) oder ein [CSize-Objekt,](csize-class.md) das die Anzahl der Einheiten angibt, die das Rechteck verschieben sollen.

*lpRect*<br/>
Zeigt auf eine RECT-Struktur oder `CRect` ein `CRect` [RECT-Objekt,](/windows/win32/api/windef/ns-windef-rect) das die Anzahl der Einheiten enthält, die jede Seite von entleeren sollen.

### <a name="remarks"></a>Bemerkungen

Die *x-* und *y-Werte* `cx` (oder und `cy`) `CRect`des Parameters werden von subtrahiert.

Die dritte Überladung `CRect` deflationiert um die Anzahl der Einheiten, die in jedem Element des Parameters angegeben sind. Beachten Sie, dass diese Überladung funktionen wie [DeflateRect](#deflaterect).

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);

rect1 -= pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect1 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp_eq"></a>CRect::Operator&amp;=

Legt `CRect` fest, dass `CRect` `rect`der Schnittpunkt von und .

```
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Enthält eine [RECT](/windows/win32/api/windef/ns-windef-rect) oder `CRect`.

### <a name="remarks"></a>Bemerkungen

Der Schnittpunkt ist das größte Rechteck, das in beiden Rechtecken enthalten ist.

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, sonst schlägt diese Funktion fehl. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CRect::IntersectRect](#intersectrect).

## <a name="crectoperator-124"></a><a name="operator_or_eq"></a>CRect::operator &#124;=

Legt `CRect` fest, dass `CRect` `rect`die Union von und .

```
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Enthält `CRect` eine oder [RECT](/windows/win32/api/windef/ns-windef-rect).

### <a name="remarks"></a>Bemerkungen

Die Union ist das kleinste Rechteck, das beide Quellrechtecke enthält.

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, sonst schlägt diese Funktion fehl. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);

rect1 |= rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect1);
```

## <a name="crectoperator-"></a><a name="operator_add"></a>CRect::Operator +

Die ersten beiden Überladungen geben `CRect` `CRect` ein Objekt zurück, das gleich dem Durchstellen durch die angegebenen Offsets ist.

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Eine [POINT-Struktur](/windows/win32/api/windef/ns-windef-point) oder ein [CPoint-Objekt,](cpoint-class.md) das die Anzahl der Einheiten angibt, die den Rückgabewert verschieben sollen.

*Größe*<br/>
Eine [SIZE-Struktur](/windows/win32/api/windef/ns-windef-size) oder ein [CSize-Objekt,](csize-class.md) das die Anzahl der Einheiten angibt, die den Rückgabewert verschieben sollen.

*lpRect*<br/>
Zeigt auf eine RECT-Struktur oder `CRect` ein [RECT-Objekt,](/windows/win32/api/windef/ns-windef-rect) das die Anzahl der Einheiten enthält, die auf jeder Seite des Rückgabewerts aufgeblasen werden sollen.

### <a name="return-value"></a>Rückgabewert

Das `CRect` Ergebnis des Verschiebens `CRect` oder Aufblasens durch die Anzahl der im Parameter angegebenen Einheiten.

### <a name="remarks"></a>Bemerkungen

Die Parameter *x* *y* und y `cx` `cy`(oder und `CRect`) des Parameters werden der Position von 's hinzugefügt.

Die dritte Überladung `CRect` gibt eine `CRect` neue zurück, die gleich aufgeblasen ist durch die Anzahl der Einheiten, die in jedem Element des Parameters angegeben sind.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 + pt;
CRect   rectResult(135, 300, 235, 400);
ASSERT(rectResult == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-"></a>CRect::Operator -

Die ersten beiden Überladungen geben `CRect` `CRect` ein Objekt zurück, das gleich dem Durchstellen durch die angegebenen Offsets ist.

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Eine POINT-Struktur oder `CPoint` ein [PUNKTobjekt,](/windows/win32/api/windef/ns-windef-point) das die Anzahl der Einheiten angibt, die den Rückgabewert verschieben sollen.

*Größe*<br/>
Eine SIZE-Struktur oder `CSize` ein [Objekt,](/windows/win32/api/windef/ns-windef-size) das die Anzahl der Einheiten angibt, die den Rückgabewert verschieben sollen.

*lpRect*<br/>
Zeigt auf eine RECT-Struktur oder `CRect` ein [RECT-Objekt,](/windows/win32/api/windef/ns-windef-rect) das die Anzahl der Einheiten enthält, die jede Seite des Rückgabewerts entleeren sollen.

### <a name="return-value"></a>Rückgabewert

Das `CRect` Ergebnis der Verschiebung `CRect` oder Entleerung durch die Anzahl der im Parameter angegebenen Einheiten.

### <a name="remarks"></a>Bemerkungen

Die Parameter *x* *y* und y `cx` `cy`(oder und ) `CRect`des Parameters werden von der Position von 's subtrahiert.

Die dritte Überladung `CRect` gibt eine `CRect` neue zurück, die gleich deflationiert ist durch die Anzahl der Einheiten, die in jedem Element des Parameters angegeben sind. Beachten Sie, dass diese Überladung speziert wie [DeflateRect](#deflaterect), nicht [SubtractRect](#subtractrect).

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 - pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect2 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp"></a>CRect::Operator&amp;

Gibt `CRect` eine zurück, `CRect` die der Schnittpunkt von und *rect2*ist.

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>Parameter

*rect2*<br/>
Enthält eine [RECT](/windows/win32/api/windef/ns-windef-rect) oder `CRect`.

### <a name="return-value"></a>Rückgabewert

Eine, `CRect` die der `CRect` Schnittpunkt von und *rect2*ist.

### <a name="remarks"></a>Bemerkungen

Der Schnittpunkt ist das größte Rechteck, das in beiden Rechtecken enthalten ist.

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, sonst schlägt diese Funktion fehl. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 & rect2;
CRect   rectResult(100, 100, 200, 200);
ASSERT(rectResult == rect3);
```

## <a name="crectoperator-124"></a><a name="operator_or"></a>CRect::Operator &#124;

Gibt `CRect` eine zurück, `CRect` die die Vereinigung von und *rect2*ist.

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>Parameter

*rect2*<br/>
Enthält eine [RECT](/windows/win32/api/windef/ns-windef-rect) oder `CRect`.

### <a name="return-value"></a>Rückgabewert

A, `CRect` die die `CRect` Vereinigung von und *rekt2*ist.

### <a name="remarks"></a>Bemerkungen

Die Union ist das kleinste Rechteck, das beide Rechtecke enthält.

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, sonst schlägt diese Funktion fehl. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 | rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

## <a name="crectptinrect"></a><a name="ptinrect"></a>CRect::PtInRect

Bestimmt, ob der `CRect`angegebene Punkt innerhalb von liegt.

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Enthält eine [POINT-Struktur](/windows/win32/api/windef/ns-windef-point) oder ein [CPoint-Objekt.](cpoint-class.md)

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich `CRect`Null, wenn der Punkt darin liegt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ein Punkt `CRect` ist drin, wenn er auf der linken oder oberen Seite liegt oder sich innerhalb aller vier Seiten befindet. Ein Punkt auf der rechten `CRect`oder unteren Seite befindet sich außerhalb .

> [!NOTE]
> Das Rechteck muss normalisiert werden, sonst schlägt diese Funktion fehl. Sie können [NormalizeRect](#normalizerect) aufrufen, um das Rechteck zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect rect(5, 5, 100, 100);
CPoint pt1(35, 50);
CPoint pt2(125, 298);

// this is true, because pt1 is inside the rectangle
ASSERT(rect.PtInRect(pt1));

// this is NOT true, because pt2 is outside the rectangle
ASSERT(!rect.PtInRect(pt2));

// note that the right and the bottom aren't inside
ASSERT(!rect.PtInRect(CPoint(35, 100)));
ASSERT(!rect.PtInRect(CPoint(100, 98)));

// but the top and the left are inside
ASSERT(rect.PtInRect(CPoint(5, 65)));
ASSERT(rect.PtInRect(CPoint(88, 5)));

// and that PtInRect() works against a POINT, too
POINT pt;
pt.x = 35;
pt.y = 50;
ASSERT(rect.PtInRect(pt));
```

## <a name="crectsetrect"></a><a name="setrect"></a>CRect::SetRect

Legt die `CRect` Bemaßungen von auf die angegebenen Koordinaten fest.

```
void SetRect(int x1, int y1, int x2, int y2) throw();
```

### <a name="parameters"></a>Parameter

*x1*<br/>
Gibt die x-Koordinate der oberen linken Ecke an.

*y1*<br/>
Gibt die y-Koordinate der oberen linken Ecke an.

*x2*<br/>
Gibt die x-Koordinate der unteren rechten Ecke an.

*y2*<br/>
Gibt die y-Koordinate der unteren rechten Ecke an.

### <a name="example"></a>Beispiel

```cpp
CRect rect;
rect.SetRect(256, 256, 512, 512);
ASSERT(rect == CRect(256, 256, 512, 512));
```

## <a name="crectsetrectempty"></a><a name="setrectempty"></a>CRect::SetRectEmpty

Macht `CRect` ein Nullrechteck, indem alle Koordinaten auf Null gesetzt werden.

```
void SetRectEmpty() throw();
```

### <a name="example"></a>Beispiel

```cpp
CRect rect;
rect.SetRectEmpty();

// rect is now (0, 0, 0, 0)
ASSERT(rect.IsRectEmpty());
```

## <a name="crectsize"></a><a name="size"></a>CRect::SIZE

Die `cx` `cy` und die Elemente des Rückgabewerts `CRect`enthalten die Höhe und Breite von .

```
CSize Size() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein [CSize-Objekt,](csize-class.md) das `CRect`die Größe von enthält.

### <a name="remarks"></a>Bemerkungen

Die Höhe oder Breite kann negativ sein.

> [!NOTE]
> Das Rechteck muss normalisiert werden, sonst schlägt diese Funktion fehl. Sie können [NormalizeRect](#normalizerect) aufrufen, um das Rechteck zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

## <a name="crectsubtractrect"></a><a name="subtractrect"></a>CRect::SubtractRect

Macht die Abmessungen `CRect` des gleich der `lpRectSrc2` `lpRectSrc1`Subtraktion von .

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>Parameter

*lpRectSrc1*<br/>
Zeigt auf die [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) oder `CRect` das Objekt, von dem ein Rechteck subtrahiert werden soll.

*lpRectSrc2*<br/>
Zeigt auf `RECT` die `CRect` Struktur oder das Objekt, auf das das Rechteck subtrahiert werden soll, auf das der Parameter *lpRectSrc1* zeigt.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Bemerkungen

Die Subtraktion ist das kleinste Rechteck, das alle Punkte in *lpRectScr1* enthält, die sich nicht im Schnittpunkt von *lpRectScr1* und *lpRectScr2*befinden.

Das von *lpRectSrc1* angegebene Rechteck bleibt unverändert, wenn das von *lpRectSrc2* angegebene Rechteck das von *lpRectSrc1* angegebene Rechteck in mindestens einer x- oder y-Richtung nicht vollständig überlappt.

Wenn beispielsweise *lpRectSrc1* (10,10, 100,100) und *lpRectSrc2* (50,50, 150,150) wären, blieb das Rechteck, auf das *lpRectSrc1* zeigt, unverändert, wenn die Funktion zurückgegeben wird. Wenn *lpRectSrc1* (10,10, 100,100) und *lpRectSrc2* (50,10, 150,150) wären, würde das Rechteck, auf das *lpRectSrc1* zeigt, die Koordinaten (10,10, 50,100) enthalten, wenn die Funktion zurückgegeben wird.

`SubtractRect`ist nicht identisch mit [Operator -](#operator_-) noch [Operator -=](#operator_-_eq). Keiner dieser Betreiber `SubtractRect`ruft jemals an.

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, sonst schlägt diese Funktion fehl. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
RECT   rectOne;
RECT   rectTwo;

rectOne.left = 10;
rectOne.top = 10;
rectOne.bottom = 100;
rectOne.right = 100;

rectTwo.left = 50;
rectTwo.top = 10;
rectTwo.bottom = 150;
rectTwo.right = 150;

CRect   rectDiff;

rectDiff.SubtractRect(&rectOne, &rectTwo);
CRect   rectResult(10, 10, 50, 100);

ASSERT(rectDiff == rectResult);

// works for CRect, too, since there is
// implicit CRect -> LPCRECT conversion

CRect rect1(10, 10, 100, 100);
CRect rect2(50, 10, 150, 150);
CRect rectOut;

rectOut.SubtractRect(rect1, rect2);
ASSERT(rectResult == rectOut);
```

## <a name="crecttopleft"></a><a name="topleft"></a>CRect::TopLeft

Die Koordinaten werden als Verweis auf ein [CPoint-Objekt](cpoint-class.md) zurückgegeben, das in `CRect`enthalten ist.

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Koordinaten der linken oberen Ecke des Rechtecks.

### <a name="remarks"></a>Bemerkungen

Mit dieser Funktion können Sie die obere linke Ecke des Rechtecks abrufen oder festlegen. Legen Sie die Ecke fest, indem Sie diese Funktion auf der linken Seite des Zuweisungsoperators verwenden.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CRect::CenterPoint](#centerpoint).

## <a name="crectunionrect"></a><a name="unionrect"></a>CRect::UnionRect

Macht die `CRect` Dimensionen gleich der Vereinigung der beiden Quellrechtecke.

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parameter

*lpRect1*<br/>
Zeigt auf ein `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) oder enthält ein Quellrechteck.

*lpRect2*<br/>
Zeigt auf `RECT` `CRect` ein oder, das ein Quellrechteck enthält.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Union nicht leer ist; 0, wenn die Union leer ist.

### <a name="remarks"></a>Bemerkungen

Die Union ist das kleinste Rechteck, das beide Quellrechtecke enthält.

Windows ignoriert die Abmessungen eines leeren Rechtecks. Das heißt, ein Rechteck, das keine Höhe oder keine Breite hat.

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, sonst schlägt diese Funktion fehl. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3.UnionRect(&rect1, &rect2);
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

## <a name="crectwidth"></a><a name="width"></a>CRect::Breite

Berechnet die Breite `CRect` von, indem der linke Wert vom rechten Wert subtrahiert wird.

```
int Width() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Breite `CRect`von .

### <a name="remarks"></a>Bemerkungen

Die Breite kann negativ sein.

> [!NOTE]
> Das Rechteck muss normalisiert werden, sonst schlägt diese Funktion fehl. Sie können [NormalizeRect](#normalizerect) aufrufen, um das Rechteck zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect rect(20, 30, 80, 70);
int nWid = rect.Width();
// nWid is now 60
ASSERT(nWid == 60);
```

## <a name="see-also"></a>Siehe auch

[CPoint-Klasse](cpoint-class.md)<br/>
[CSize-Klasse](csize-class.md)<br/>
[Rect](/windows/win32/api/windef/ns-windef-rect)

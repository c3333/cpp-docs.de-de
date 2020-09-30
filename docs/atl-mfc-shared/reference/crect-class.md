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
ms.openlocfilehash: f45090971e8dbb89ae281b408cc3a14e102ffe17
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502874"
---
# <a name="crect-class"></a>CRect-Klasse

Ähnelt einer Windows- [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur.

## <a name="syntax"></a>Syntax

```
class CRect : public tagRECT
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|name|Beschreibung|
|----------|-----------------|
|[CRect:: CRect](#crect)|Erstellt ein `CRect`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|Beschreibung|
|----------|-----------------|
|[CRect:: BottomRight](#bottomright)|Gibt den unteren rechten Punkt von zurück `CRect` .|
|[CRect:: Centerpoint](#centerpoint)|Gibt den Mittelpunkt von zurück `CRect` .|
|[CRect:: copyrect](#copyrect)|Kopiert die Dimensionen eines Quell Rechtecks in `CRect` .|
|[CRect::D eflaterect](#deflaterect)|Verringert die Breite und Höhe von `CRect` .|
|[CRect:: equalrect](#equalrect)|Bestimmt `CRect` , ob gleich dem angegebenen Rechteck ist.|
|[CRect:: height](#height)|Berechnet die Höhe von `CRect` .|
|[CRect:: inflaterect](#inflaterect)|Erhöht die Breite und Höhe von `CRect` .|
|[CRect:: intersectRect](#intersectrect)|Legt `CRect` den Wert für die Schnittmenge von zwei Rechtecke fest.|
|[CRect:: isrectempty](#isrectempty)|Bestimmt, ob `CRect` leer ist. `CRect` ist leer, wenn Breite und/oder Höhe 0 (null) ist.|
|[CRect:: isrectnull](#isrectnull)|Bestimmt, ob `top` die `bottom` `left` -,-,-und-Element `right` Variablen gleich 0 sind.|
|[CRect:: muvetox](#movetox)|Wechselt `CRect` zur angegebenen x-Koordinate.|
|[CRect:: muvedexy](#movetoxy)|Wechselt `CRect` zu den angegebenen x-und y-Koordinaten.|
|[CRect:: muvetoy](#movetoy)|Wechselt `CRect` zur angegebenen y-Koordinate.|
|[CRect:: NormalizeRect](#normalizerect)|Standardisiert die Höhe und die Breite von `CRect` .|
|[CRect:: offsetrect](#offsetrect)|Verschiebt `CRect` um die angegebenen Offsets.|
|[CRect::P tinrect](#ptinrect)|Bestimmt, ob der angegebene Punkt innerhalb von liegt `CRect` .|
|[CRect:: SetRect](#setrect)|Legt die Dimensionen von fest `CRect` .|
|[CRect:: setrectempty](#setrectempty)|Legt `CRect` auf ein leeres Rechteck (alle Koordinaten gleich 0) fest.|
|[CRect:: size](#size)|Berechnet die Größe von `CRect` .|
|[CRect:: subtractrect](#subtractrect)|Subtrahiert ein Rechteck von einem anderen.|
|[CRect:: TopLeft](#topleft)|Gibt den oberen linken Punkt von zurück `CRect` .|
|[CRect:: unionrect](#unionrect)|`CRect`Entspricht der Vereinigung von zwei Rechtecke.|
|[CRect:: width](#width)|Berechnet die Breite von `CRect` .|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|Beschreibung|
|----------|-----------------|
|[CRect:: Operator-](#operator_-)|Subtrahiert die angegebenen Offsets von `CRect` oder entleert `CRect` und gibt das resultierende zurück `CRect` .|
|[CRect:: Operator lpcrect](#operator_lpcrect)|Konvertiert ein `CRect`-Element in ein `LPCRECT`-Element.|
|[CRect:: Operator lprect](#operator_lprect)|Konvertiert ein `CRect`-Element in ein `LPRECT`-Element.|
|[CRect:: Operator! =](#operator_neq)|Bestimmt `CRect` , ob nicht gleich einem Rechteck ist.|
|[CRect::-Operator &amp;](#operator_amp)|Erstellt die Schnittmenge von `CRect` und einem Rechteck und gibt das resultierende zurück `CRect` .|
|[CRect::-Operator &amp;=](#operator_amp_eq)|Legt `CRect` den Wert für die Schnittmenge von `CRect` und einem Rechteck fest.|
|[CRect:: Operator &#124;](#operator_or)|Erstellt die Vereinigung von `CRect` und einem Rechteck und gibt das resultierende zurück `CRect` .|
|[CRect:: Operator &#124;=](#operator_or_eq)|Legt `CRect` gleich der Union von `CRect` und einem Rechteck fest.|
|[CRect:: Operator +](#operator_add)|Fügt die angegebenen Offsets hinzu `CRect` oder vergrößert Sie `CRect` und gibt das resultierende zurück `CRect` .|
|[CRect:: Operator + =](#operator_add_eq)|Fügt die angegebenen Offsets hinzu `CRect` oder vergrößert Sie `CRect` .|
|[CRect:: Operator =](#operator_eq)|Kopiert die Dimensionen eines Rechtecks in `CRect` .|
|[CRect:: Operator-=](#operator_-_eq)|Subtrahiert die angegebenen Offsets von `CRect` oder entleert `CRect` .|
|[CRect:: Operator = =](#operator_eq_eq)|Bestimmt `CRect` , ob gleich einem Rechteck ist.|

## <a name="remarks"></a>Bemerkungen

`CRect` umfasst auch Element Funktionen zum Bearbeiten von `CRect` Objekten und Windows- `RECT` Strukturen.

Ein- `CRect` Objekt kann immer dann als Funktionsparameter übergeben werden, wenn eine- `RECT` Struktur, `LPCRECT` oder `LPRECT` übergeben werden kann.

> [!NOTE]
> Diese Klasse wird von der- `tagRECT` Struktur abgeleitet. (Der Name `tagRECT` ist ein Name für die Struktur, der weniger häufig verwendet wird `RECT` .) Dies bedeutet, dass auf die Datenmember ( `left` ,, `top` `right` und `bottom` ) der- `RECT` Struktur zugegriffen werden kann `CRect` .

Ein `CRect` enthält Element Variablen, die die oberen linken und unteren rechten Punkte eines Rechtecks definieren.

Beim angeben `CRect` von müssen Sie darauf achten, dass Sie Sie so erstellen, dass Sie normalisiert werden, d. –., dass der Wert der linken Koordinate kleiner als der Rechte und der obere kleiner als der untere Wert ist. Beispielsweise wird in einer oberen linken Ecke von (10, 10) und unten rechts von (20, 20) ein normalisiertes Rechteck definiert, aber von oben links (20, 20) und von unten rechts von (10, 10) wird ein nicht normalisiertes Rechteck definiert. Wenn das Rechteck nicht normalisiert ist, geben viele Element `CRect` Funktionen möglicherweise falsche Ergebnisse zurück. (Eine Liste dieser Funktionen finden Sie unter [CRect:: NormalizeRect](#normalizerect) .) Bevor Sie eine Funktion aufrufen, die normalisierte Rechtecke erfordert, können Sie nicht normalisierte Rechtecke normalisieren, indem Sie die- `NormalizeRect` Funktion aufrufen.

Gehen Sie vorsichtig vor, wenn Sie eine `CRect` mit den Member-Funktionen [CDC::D ptolp](../../mfc/reference/cdc-class.md#dptolp) und [CDC:: lptodp](../../mfc/reference/cdc-class.md#lptodp) bearbeiten. Wenn der Kartenmodus eines Anzeige Kontexts so ist, dass der y-Block negativ ist, wie in `MM_LOENGLISH` , `CDC::DPtoLP` wird der von transformiert, `CRect` sodass der obere Wert größer als der untere Wert ist. Funktionen wie `Height` und `Size` geben dann negative Werte für die Höhe des transformierten zurück `CRect` , und das Rechteck wird nicht normalisiert.

Wenn überladene `CRect` Operatoren verwendet werden, muss der erste Operand eine sein `CRect` . der zweite Operand kann entweder eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder ein- `CRect` Objekt sein.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`tagRECT`

`CRect`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atltypes. h

## <a name="crectbottomright"></a><a name="bottomright"></a> CRect:: BottomRight

Die Koordinaten werden als Verweis auf ein [CPoint](cpoint-class.md) -Objekt zurückgegeben, das in enthalten ist `CRect` .

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Koordinaten der rechten unteren Ecke des Rechtecks.

### <a name="remarks"></a>Bemerkungen

Sie können diese Funktion verwenden, um die rechte untere Ecke des Rechtecks zu erhalten oder festzulegen. Legen Sie die Ecke fest, indem Sie diese Funktion auf der linken Seite des Zuweisungs Operators verwenden.

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

## <a name="crectcenterpoint"></a><a name="centerpoint"></a> CRect:: Centerpoint

Berechnet den Mittelpunkt von `CRect` durch Hinzufügen der linken und rechten Werte, dividiert durch zwei, durch Hinzufügen der obersten und untersten Werte und durch zwei dividieren.

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein- `CPoint` Objekt, das der Mittelpunkt von ist `CRect` .

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

## <a name="crectcopyrect"></a><a name="copyrect"></a> CRect:: copyrect

Kopiert das `lpSrcRect` Rechteck in `CRect` .

```cpp
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>Parameter

*lpsrcrect*<br/>
Verweist auf die [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder `CRect` das Objekt, das kopiert werden soll.

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

## <a name="crectcrect"></a><a name="crect"></a> CRect:: CRect

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

*l*<br/>
Gibt die linke Position von an `CRect` .

*t*<br/>
Gibt den oberen Rand von an `CRect` .

*r*<br/>
Gibt die richtige Position von an `CRect` .

*b*<br/>
Gibt den unteren Rand von an `CRect` .

*srcRect*<br/>
Verweist auf die [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur mit den Koordinaten für `CRect` .

*lpsrcrect*<br/>
Verweist auf die- `RECT` Struktur mit den Koordinaten für `CRect` .

*Punkt*<br/>
Gibt den Ursprungs Punkt für das Rechteck an, das erstellt werden soll. Entspricht der linken oberen Ecke.

*size*<br/>
Gibt die Verschiebung von der linken oberen Ecke zur rechten unteren Ecke des zu erstellenden Rechtecks an.

*topLeft*<br/>
Gibt die linke obere Position von an `CRect` .

*bottomRight*<br/>
Gibt die untere rechte Position von an `CRect` .

### <a name="remarks"></a>Bemerkungen

Wenn keine Argumente angegeben werden, `left` werden die Member,, `top` `right` und `bottom` auf 0 festgelegt.

Die `CRect` `const RECT&` Konstruktoren () und `CRect` ( `LPCRECT` ) führen ein [copyrect](#copyrect)aus. Die anderen Konstruktoren initialisieren die Element Variablen des-Objekts direkt.

### <a name="example"></a>Beispiel

```cpp
// default constructor is equivalent to CRect(0, 0, 0, 0)
CRect emptyRect;

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

## <a name="crectdeflaterect"></a><a name="deflaterect"></a> CRect::D eflaterect

`DeflateRect` defliert `CRect` durch Verschieben der Seiten in den Mittelpunkt.

```cpp
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>Parameter

*x*<br/>
Gibt die Anzahl von Einheiten an, die die linke und die Rechte Seite von isolieren soll `CRect` .

*y*<br/>
Gibt die Anzahl der Einheiten an, um den oberen und unteren Rand von zu isolieren `CRect` .

*size*<br/>
Eine [Größe](/windows/win32/api/windef/ns-windef-size) oder [CSize](csize-class.md) , die die Anzahl der zu deflieren Einheiten angibt `CRect` . Der `cx` -Wert gibt die Anzahl der Einheiten an, um die linke und die Rechte Seite zu isolieren, und der- `cy` Wert gibt die Anzahl der Einheiten an, um den oberen und unteren Rand zu isolieren.

*lprect*<br/>
Verweist auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder eine `CRect` , die die Anzahl von Einheiten angibt, mit denen die einzelnen Seiten deflatieren werden.

*l*<br/>
Gibt die Anzahl der Einheiten an, die die linke Seite von isolieren soll `CRect` .

*t*<br/>
Gibt die Anzahl der Einheiten an, die den Anfang von isolieren `CRect` .

*r*<br/>
Gibt die Anzahl der Einheiten an, die die Rechte Seite von isolieren soll `CRect` .

*b*<br/>
Gibt die Anzahl der Einheiten an, die das Ende von isolieren soll `CRect` .

### <a name="remarks"></a>Bemerkungen

Fügen Sie zu diesem Zweck `DeflateRect` die Einheiten Links und oben hinzu, und subtrahiert Einheiten von der rechten und unteren Ebene. Die Parameter von `DeflateRect` sind signierte Werte; positive Werte deflate `CRect` und negative Werte erhöhen diese Werte.

Die ersten beiden über Ladungen deflieren beide Paare von gegenüberliegenden Seiten von `CRect` , sodass die Gesamtbreite um das zweifache *x* (oder) verringert wird `cx` und die Gesamthöhe um das zwei fache *y* (oder) verringert wird `cy` . Die anderen beiden über Ladungen deflieren jede Seite von `CRect` unabhängig von den anderen.

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

## <a name="crectequalrect"></a><a name="equalrect"></a> CRect:: equalrect

Bestimmt `CRect` , ob gleich dem angegebenen Rechteck ist.

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parameter

*lprect*<br/>
Verweist auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder ein- `CRect` Objekt, das die oberen linken und rechten unteren Ecke eines Rechtecks enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die beiden Rechtecke dieselben Werte für Top, Left, Bottom und Right aufweisen; andernfalls 0.

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

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

## <a name="crectheight"></a><a name="height"></a> CRect:: height

Berechnet die Höhe von, `CRect` indem der obere Wert von dem unteren Wert subtrahieren wird.

```
int Height() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Höhe von `CRect` .

### <a name="remarks"></a>Bemerkungen

Der resultierende Wert kann negativ sein.

> [!NOTE]
> Das Rechteck muss normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um das Rechteck zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

## <a name="crectinflaterect"></a><a name="inflaterect"></a> CRect:: inflaterect

`InflateRect` wird vergrößert, `CRect` indem die Seiten von der Mitte weg verschoben werden.

```cpp
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>Parameter

*x*<br/>
Gibt die Anzahl der Einheiten an, um die linke und Rechte Seite von vergrößert werden soll `CRect` .

*y*<br/>
Gibt die Anzahl der Einheiten an, um den oberen und unteren Rand von zu erhöhen `CRect` .

*size*<br/>
Eine [Größe](/windows/win32/api/windef/ns-windef-size) oder [CSize](csize-class.md) , die die Anzahl der aufzuhefenden Einheiten angibt `CRect` . Der `cx` -Wert gibt die Anzahl der Einheiten an, um die linke und die Rechte Seite aufzufüllen, und der- `cy` Wert gibt die Anzahl der Einheiten an, um den oberen und unteren Rand aufzufüllen.

*lprect*<br/>
Verweist auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder eine `CRect` , die die Anzahl von Einheiten angibt, mit denen die einzelnen Seiten vergrößert werden.

*l*<br/>
Gibt die Anzahl der Einheiten an, um die die linke Seite vergrößert werden soll `CRect` .

*t*<br/>
Gibt die Anzahl der Einheiten an, um die der obere Rand von vergrößert werden soll `CRect` .

*r*<br/>
Gibt die Anzahl der Einheiten an, um die die Rechte Seite vergrößert werden soll `CRect` .

*b*<br/>
Gibt die Anzahl der Einheiten an, um die der untere Rand vergrößert werden soll `CRect` .

### <a name="remarks"></a>Bemerkungen

Zu diesem Zweck `InflateRect` subtrahiert Einheiten von links nach oben und fügt Einheiten rechts und unten hinzu. Die Parameter von `InflateRect` sind signierte Werte; positive Werte werden vergrößert, `CRect` und negative Werte werden dadurch deflatieren.

Die ersten beiden über Ladungen erhöhen beide Paare von gegenüberliegenden Seiten von `CRect` , sodass die Gesamtbreite um das zwei fache *x* (oder) erhöht wird `cx` und die Gesamthöhe um das zwei fache *y* (oder) erhöht wird `cy` . Die anderen beiden über Ladungen erhöhen jede Seite von `CRect` unabhängig von den anderen.

### <a name="example"></a>Beispiel

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

## <a name="crectintersectrect"></a><a name="intersectrect"></a> CRect:: intersectRect

Macht einen `CRect` gleich dem Schnittpunkt zweier bestehender Rechtecke.

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parameter

*lpRect1*<br/>
Verweist auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder `CRect` ein Objekt, das ein Quell Rechteck enthält.

*lpRect2*<br/>
Verweist auf eine `RECT` Struktur oder ein `CRect` Objekt, das ein Quell Rechteck enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Schnittmenge nicht leer ist. 0, wenn die Schnittmenge leer ist.

### <a name="remarks"></a>Bemerkungen

Die Schnittmenge ist das größte Rechteck, das in beiden vorhandenen Rechtecke enthalten ist.

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

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

## <a name="crectisrectempty"></a><a name="isrectempty"></a> CRect:: isrectempty

Bestimmt, ob `CRect` leer ist.

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null) `CRect` , wenn leer ist; 0, wenn `CRect` nicht leer ist.

### <a name="remarks"></a>Bemerkungen

Ein Rechteck ist leer, wenn Breite und/oder Höhe 0 oder negativ sind. Unterscheidet `IsRectNull` sich von, das bestimmt, ob alle Koordinaten des Rechtecks NULL sind.

> [!NOTE]
> Das Rechteck muss normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um das Rechteck zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
ASSERT(rectEmpty.IsRectEmpty());
```

## <a name="crectisrectnull"></a><a name="isrectnull"></a> CRect:: isrectnull

Bestimmt, ob die Werte für oben, Links, unten und rechts von `CRect` gleich 0 sind.

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null) `CRect` , wenn die Werte Top, Left, Bottom und right gleich 0 sind, andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Unterscheidet `IsRectEmpty` sich von, das bestimmt, ob das Rechteck leer ist.

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

## <a name="crectmovetox"></a><a name="movetox"></a> CRect:: muvetox

Mit dieser Funktion können Sie das Rechteck in die absolute x-Koordinate verschieben, die von *x*angegeben wird.

```cpp
void MoveToX(int x) throw();
```

### <a name="parameters"></a>Parameter

*x*<br/>
Die absolute x-Koordinate für die linke obere Ecke des Rechtecks.

### <a name="example"></a>Beispiel

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

// rect is now (10, 0, 110, 100);
ASSERT(rect == CRect(10, 0, 110, 100));
```

## <a name="crectmovetoxy"></a><a name="movetoxy"></a> CRect:: muvedexy

Mit dieser Funktion können Sie das Rechteck in die absolute x-und y-Koordinaten verschieben.

```cpp
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>Parameter

*x*<br/>
Die absolute x-Koordinate für die linke obere Ecke des Rechtecks.

*y*<br/>
Die absolute y-Koordinate für die linke obere Ecke des Rechtecks.

*Punkt*<br/>
Eine- `POINT` Struktur, die die absolute linke obere Ecke des Rechtecks angibt.

### <a name="example"></a>Beispiel

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
ASSERT(rect == CRect(10, 10, 110, 110));
```

## <a name="crectmovetoy"></a><a name="movetoy"></a> CRect:: muvetoy

Mit dieser Funktion können Sie das Rechteck in die absolute, von *y*angegebene y-Koordinate verschieben.

```cpp
void MoveToY(int y) throw();
```

### <a name="parameters"></a>Parameter

*y*<br/>
Die absolute y-Koordinate für die linke obere Ecke des Rechtecks.

### <a name="example"></a>Beispiel

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
ASSERT(rect == CRect(0, 10, 100, 110));
```

## <a name="crectnormalizerect"></a><a name="normalizerect"></a> CRect:: NormalizeRect

Normalisiert `CRect` , sodass sowohl die Höhe als auch die Breite positiv sind.

```cpp
void NormalizeRect() throw();
```

### <a name="remarks"></a>Bemerkungen

Das Rechteck wird zur Positionierung des vierten Quadranten normalisiert, das Windows in der Regel für Koordinaten verwendet. `NormalizeRect` Vergleicht die oberen und unteren Werte und tauscht Sie aus, wenn der obere Wert größer als der untere Wert ist. Entsprechend werden die linken und rechten Werte ausgetauscht, wenn die linke Seite größer als die Rechte ist. Diese Funktion ist nützlich, wenn Sie mit unterschiedlichen Karten Modi und umgekehrten Rechtecke umzugehen.

> [!NOTE]
> Die folgenden `CRect` Member-Funktionen erfordern normalisierte Rechtecke, damit Sie ordnungsgemäß funktionieren: [height](#height), [Width](#width), [size](#size), [isrectempty](#isrectempty), [PtInRect](#ptinrect), [equalrect](#equalrect), [unionrect](#unionrect), [intersectRect](#intersectrect), [subtractrect](#subtractrect), [Operator = =](#operator_eq_eq), [Operator! =](#operator_neq), [Operator &#124;](#operator_or), [Operator &#124;=](#operator_or_eq), [Operator &](#operator_amp)und [Operator &=](#operator_amp_eq).

### <a name="example"></a>Beispiel

```cpp
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
rect2.NormalizeRect();
ASSERT(rect1 == rect2);
```

## <a name="crectoffsetrect"></a><a name="offsetrect"></a> CRect:: offsetrect

Verschiebt `CRect` um die angegebenen Offsets.

```cpp
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();
```

### <a name="parameters"></a>Parameter

*x*<br/>
Gibt den Betrag an, nach links oder rechts verschoben werden soll. Er muss negativ sein, um nach Links zu verschieben.

*y*<br/>
Gibt den Betrag an, der nach oben oder unten verschoben werden soll. Es muss negativ sein, um nach oben zu wechseln.

*Punkt*<br/>
Enthält eine [Punkt](/windows/win32/api/windef/ns-windef-point) Struktur oder ein [CPoint](cpoint-class.md) -Objekt, das beide Dimensionen angibt, nach denen verschoben werden soll.

*size*<br/>
Enthält eine [Größen](/windows/win32/api/windef/ns-windef-size) Struktur oder ein [CSize](csize-class.md) -Objekt, das beide Dimensionen angibt, nach denen verschoben werden soll.

### <a name="remarks"></a>Bemerkungen

Verschiebt `CRect` *x* -Einheiten entlang der x-Achse und *y* -Einheiten entlang der y-Achse. Der *x* -und der *y* -Parameter sind signierte Werte `CRect` und können daher nach links oder rechts und nach oben oder unten verschoben werden.

### <a name="example"></a>Beispiel

```cpp
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

// rect is now (230, 230, 265, 265)
ASSERT(rect == CRect(230, 230, 265, 265));
```

## <a name="crectoperator-lpcrect-converts-a-crect-to-an-lpcrect"></a><a name="operator_lpcrect"></a> CRect:: Operator lpcrect konvertiert einen `CRect` in ein [lpcrect](../../mfc/reference/data-types-mfc.md).

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Funktion verwenden, benötigen Sie nicht den Address-of ( **&** )-Operator. Dieser Operator wird automatisch verwendet, wenn Sie ein- `CRect` Objekt an eine Funktion übergeben, die eine erwartet `LPCRECT` .

## <a name="crectoperator-lprect"></a><a name="operator_lprect"></a> CRect:: Operator lprect

Konvertiert einen `CRect` in einen [lprect](../../mfc/reference/data-types-mfc.md).

```
operator LPRECT() throw();
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Funktion verwenden, benötigen Sie nicht den Address-of ( **&** )-Operator. Dieser Operator wird automatisch verwendet, wenn Sie ein- `CRect` Objekt an eine Funktion übergeben, die eine erwartet `LPRECT` .

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CRect:: Operator lpcrect](#operator_lpcrect).

## <a name="crectoperator-"></a><a name="operator_eq"></a> CRect:: Operator =

Weist *srcRect* zu `CRect` .

```cpp
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>Parameter

*srcRect*<br/>
Verweist auf ein Quell Rechteck. Kann ein [Rect](/windows/win32/api/windef/ns-windef-rect) oder sein `CRect` .

### <a name="example"></a>Beispiel

```cpp
CRect rect(0, 0, 127, 168);
CRect rect2;

rect2 = rect;
ASSERT(rect2 == CRect(0, 0, 127, 168));
```

## <a name="crectoperator-"></a><a name="operator_eq_eq"></a> CRect:: Operator = =

Bestimmt `rect` , ob gleich ist, `CRect` indem die Koordinaten ihrer oberen linken und unteren rechten Ecke verglichen werden.

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Verweist auf ein Quell Rechteck. Kann ein [Rect](/windows/win32/api/windef/ns-windef-rect) oder sein `CRect` .

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn gleich andernfalls 0.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

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

## <a name="crectoperator-"></a><a name="operator_neq"></a> CRect:: Operator! =

Bestimmt, ob *Rect* nicht gleich ist, `CRect` indem die Koordinaten ihrer oberen linken und unteren rechten Ecke verglichen werden.

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Verweist auf ein Quell Rechteck. Kann ein [Rect](/windows/win32/api/windef/ns-windef-rect) oder sein `CRect` .

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn nicht gleich; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

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

## <a name="crectoperator-"></a><a name="operator_add_eq"></a> CRect:: Operator + =

Die ersten beiden über Ladungen bewegen sich `CRect` um die angegebenen Offsets.

```cpp
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Eine [Punkt](/windows/win32/api/windef/ns-windef-point) Struktur oder ein [CPoint](cpoint-class.md) -Objekt, das die Anzahl der Einheiten zum Verschieben des Rechtecks angibt.

*size*<br/>
Eine [Größen](/windows/win32/api/windef/ns-windef-size) Struktur oder ein [CSize](csize-class.md) -Objekt, das die Anzahl der Einheiten zum Verschieben des Rechtecks angibt.

*lprect*<br/>
Verweist auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder ein- `CRect` Objekt, das die Anzahl der Einheiten für die Vergrößerung der einzelnen Seiten von enthält `CRect` .

### <a name="remarks"></a>Bemerkungen

Die *x* -und *y* -Werte des-Parameters `cx` `cy` werden hinzugefügt `CRect` .

Die dritte Überladung `CRect` wird um die Anzahl der Einheiten vergrößert, die in jedem Member des Parameters angegeben werden.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint  pt(35, 65);
CRect   rect2(135, 300, 235, 400);

rect1 += pt;
ASSERT(rect1 == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-_eq"></a> CRect:: Operator-=

Die ersten beiden über Ladungen bewegen sich `CRect` um die angegebenen Offsets.

```cpp
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Eine [Punkt](/windows/win32/api/windef/ns-windef-point) Struktur oder ein [CPoint](cpoint-class.md) -Objekt, das die Anzahl der Einheiten zum Verschieben des Rechtecks angibt.

*size*<br/>
Eine [Größen](/windows/win32/api/windef/ns-windef-size) Struktur oder ein [CSize](csize-class.md) -Objekt, das die Anzahl der Einheiten zum Verschieben des Rechtecks angibt.

*lprect*<br/>
Verweist auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder ein- `CRect` Objekt, das die Anzahl der Einheiten für die Deflate der einzelnen Seiten von enthält `CRect` .

### <a name="remarks"></a>Bemerkungen

Der *x* -und *y* -Wert des-Parameters `cx` `cy` werden von subtrahiert `CRect` .

Die dritte Überladung `CRect` wird um die Anzahl der Einheiten defliert, die in jedem Element des Parameters angegeben werden. Beachten Sie, dass diese Überladung wie [deflaterect](#deflaterect)funktioniert.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);

rect1 -= pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect1 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp_eq"></a> CRect::-Operator &amp;=

Legt `CRect` den Wert für die Schnittmenge von `CRect` und fest `rect` .

```cpp
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Enthält ein [Rect](/windows/win32/api/windef/ns-windef-rect) oder `CRect` .

### <a name="remarks"></a>Bemerkungen

Die Schnittmenge ist das größte Rechteck, das in beiden Rechtecke enthalten ist.

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CRect:: intersectRect](#intersectrect).

## <a name="crectoperator-124"></a><a name="operator_or_eq"></a> CRect:: Operator &#124;=

Legt `CRect` die gleiche wie die Union von `CRect` und fest `rect` .

```cpp
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Enthält ein- `CRect` oder- [Rect](/windows/win32/api/windef/ns-windef-rect).

### <a name="remarks"></a>Bemerkungen

Die Union ist das kleinste Rechteck, das beide Quell Rechtecke enthält.

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);

rect1 |= rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect1);
```

## <a name="crectoperator-"></a><a name="operator_add"></a> CRect:: Operator +

Die ersten beiden-über Ladungen geben ein- `CRect` Objekt zurück, das `CRect` von den angegebenen Offsets zurückgesetzt wird.

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Eine [Punkt](/windows/win32/api/windef/ns-windef-point) Struktur oder ein [CPoint](cpoint-class.md) -Objekt, das die Anzahl der Einheiten angibt, mit denen der Rückgabewert verschoben wird.

*size*<br/>
Eine [Größen](/windows/win32/api/windef/ns-windef-size) Struktur oder ein [CSize](csize-class.md) -Objekt, das die Anzahl der Einheiten angibt, mit denen der Rückgabewert verschoben wird.

*lprect*<br/>
Verweist auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder ein- `CRect` Objekt, das die Anzahl der Einheiten enthält, um die einzelnen Seiten des Rückgabewerts aufzufüllen.

### <a name="return-value"></a>Rückgabewert

Der, der `CRect` sich aus der Verschiebung oder Vergrößerung `CRect` der im-Parameter angegebenen Anzahl von Einheiten ergibt.

### <a name="remarks"></a>Bemerkungen

Die *x* -und *y* -Parameter des Parameters werden der Position des Parameters `cx` `cy` hinzugefügt `CRect` .

Die dritte Überladung gibt eine neue zurück `CRect` , die gleich `CRect` der Anzahl der Einheiten ist, die in jedem Member des-Parameters angegeben ist.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 + pt;
CRect   rectResult(135, 300, 235, 400);
ASSERT(rectResult == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-"></a> CRect:: Operator-

Die ersten beiden-über Ladungen geben ein- `CRect` Objekt zurück, das `CRect` von den angegebenen Offsets zurückgesetzt wird.

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Eine [Punkt](/windows/win32/api/windef/ns-windef-point) Struktur oder ein `CPoint` Objekt, das die Anzahl der Einheiten angibt, mit denen der Rückgabewert verschoben wird.

*size*<br/>
Eine [Größen](/windows/win32/api/windef/ns-windef-size) Struktur oder ein `CSize` Objekt, das die Anzahl der Einheiten angibt, mit denen der Rückgabewert verschoben wird.

*lprect*<br/>
Verweist auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder ein- `CRect` Objekt, das die Anzahl der Einheiten für die Deflate der einzelnen Seiten des Rückgabewerts enthält.

### <a name="return-value"></a>Rückgabewert

Der, der `CRect` sich aus dem Verschieben oder deflating `CRect` durch die im-Parameter angegebene Anzahl von Einheiten ergibt.

### <a name="remarks"></a>Bemerkungen

Die *x* -und *y* -Parameter des Parameters werden von der Position des Parameters `cx` `cy` subtrahiert `CRect` .

Die dritte Überladung gibt einen neuen-Wert zurück `CRect` , der gleich `CRect` der Anzahl der Einheiten ist, die in jedem Member des-Parameters angegeben werden. Beachten Sie, dass diese Überladung wie [deflaterect](#deflaterect)funktioniert, nicht [subtractrect](#subtractrect).

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 - pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect2 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp"></a> CRect::-Operator &amp;

Gibt einen zurück `CRect` , der die Schnittmenge von `CRect` und *rect2*ist.

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>Parameter

*rect2*<br/>
Enthält ein [Rect](/windows/win32/api/windef/ns-windef-rect) oder `CRect` .

### <a name="return-value"></a>Rückgabewert

Eine `CRect` , die die Schnittmenge von `CRect` und *rect2*ist.

### <a name="remarks"></a>Bemerkungen

Die Schnittmenge ist das größte Rechteck, das in beiden Rechtecke enthalten ist.

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 & rect2;
CRect   rectResult(100, 100, 200, 200);
ASSERT(rectResult == rect3);
```

## <a name="crectoperator-124"></a><a name="operator_or"></a> CRect:: Operator &#124;

Gibt einen zurück `CRect` , der die Union von `CRect` und *rect2*ist.

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>Parameter

*rect2*<br/>
Enthält ein [Rect](/windows/win32/api/windef/ns-windef-rect) oder `CRect` .

### <a name="return-value"></a>Rückgabewert

Ein `CRect` , der die Union von `CRect` und *rect2*ist.

### <a name="remarks"></a>Bemerkungen

Die Union ist das kleinste Rechteck, das beide Rechtecke enthält.

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 | rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

## <a name="crectptinrect"></a><a name="ptinrect"></a> CRect::P tinrect

Bestimmt, ob der angegebene Punkt innerhalb von liegt `CRect` .

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Enthält eine [Punkt](/windows/win32/api/windef/ns-windef-point) Struktur oder ein [CPoint](cpoint-class.md) -Objekt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Punkt innerhalb von liegt `CRect` , andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ein Punkt liegt darin, `CRect` Wenn er auf der linken oder oberen Seite liegt oder sich auf allen vier Seiten befindet. Ein Punkt auf der rechten oder unteren Seite liegt außerhalb von `CRect` .

> [!NOTE]
> Das Rechteck muss normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um das Rechteck zu normalisieren, bevor Sie diese Funktion aufrufen.

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

## <a name="crectsetrect"></a><a name="setrect"></a> CRect:: SetRect

Legt die Dimensionen von `CRect` auf die angegebenen Koordinaten fest.

```cpp
void SetRect(int x1, int y1, int x2, int y2) throw();
```

### <a name="parameters"></a>Parameter

*x1*<br/>
Gibt die x-Koordinate der oberen linken Ecke an.

*Y1*<br/>
Gibt die y-Koordinate der oberen linken Ecke an.

*x2*<br/>
Gibt die x-Koordinate der unteren rechten Ecke an.

*Y2*<br/>
Gibt die y-Koordinate der unteren rechten Ecke an.

### <a name="example"></a>Beispiel

```cpp
CRect rect;
rect.SetRect(256, 256, 512, 512);
ASSERT(rect == CRect(256, 256, 512, 512));
```

## <a name="crectsetrectempty"></a><a name="setrectempty"></a> CRect:: setrectempty

Erstellt `CRect` ein NULL-Rechteck, indem alle Koordinaten auf NULL festgelegt werden.

```cpp
void SetRectEmpty() throw();
```

### <a name="example"></a>Beispiel

```cpp
CRect rect;
rect.SetRectEmpty();

// rect is now (0, 0, 0, 0)
ASSERT(rect.IsRectEmpty());
```

## <a name="crectsize"></a><a name="size"></a> CRect:: size

Die `cx` -und-Member `cy` des Rückgabewerts enthalten die Höhe und die Breite von `CRect` .

```
CSize Size() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein [CSize](csize-class.md) -Objekt, das die Größe von enthält `CRect` .

### <a name="remarks"></a>Bemerkungen

Entweder die Höhe oder die Breite kann negativ sein.

> [!NOTE]
> Das Rechteck muss normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um das Rechteck zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

## <a name="crectsubtractrect"></a><a name="subtractrect"></a> CRect:: subtractrect

Macht die Dimensionen von `CRect` gleich der Subtraktion von `lpRectSrc2` von `lpRectSrc1` .

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>Parameter

*lpRectSrc1*<br/>
Verweist auf die [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder das `CRect` Objekt, von dem ein Rechteck subtrahiert werden soll.

*lpRectSrc2*<br/>
Verweist auf die `RECT` Struktur oder das `CRect` Objekt, das von dem Rechteck subtrahiert werden soll, auf das der *lpRectSrc1* -Parameter verweist.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Bemerkungen

Die Subtraktion ist das kleinste Rechteck, das alle Punkte in *lpRectScr1* enthält, die sich nicht in der Schnittmenge von *lpRectScr1* und *lpRectScr2*befinden.

Das von *lpRectSrc1* angegebene Rechteck ist unverändert, wenn das von *lpRectSrc2* angegebene Rechteck nicht vollständig mit dem durch *lpRectSrc1* in mindestens einer der x-oder y-Richtung angegebenen Rechteck überlappt.

Wenn z. b. *lpRectSrc1* (10, 10, 100.100) und *lpRectSrc2* (50, 50, 150.150) waren, wäre das Rechteck, auf das von *lpRectSrc1* verwiesen wird, unverändert, wenn die Funktion zurückgegeben wird. Wenn *lpRectSrc1* (10, 10, 100.100) und *lpRectSrc2* (50, 10, 150.150) lauten, würde das Rechteck, auf das von *lpRectSrc1* gezeigt wird, die Koordinaten (10, 10, 50.100) enthalten, wenn die Funktion zurückgegeben wird.

`SubtractRect` ist nicht identisch mit [Operator-](#operator_-) oder [Operator-=](#operator_-_eq). Keiner dieser Operatoren ruft jemals auf `SubtractRect` .

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

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

## <a name="crecttopleft"></a><a name="topleft"></a> CRect:: TopLeft

Die Koordinaten werden als Verweis auf ein [CPoint](cpoint-class.md) -Objekt zurückgegeben, das in enthalten ist `CRect` .

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Koordinaten der linken oberen Ecke des Rechtecks.

### <a name="remarks"></a>Bemerkungen

Sie können diese Funktion verwenden, um die linke obere Ecke des Rechtecks zu erhalten oder festzulegen. Legen Sie die Ecke fest, indem Sie diese Funktion auf der linken Seite des Zuweisungs Operators verwenden.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CRect:: Centerpoint](#centerpoint).

## <a name="crectunionrect"></a><a name="unionrect"></a> CRect:: unionrect

Macht die Dimensionen von `CRect` gleich der Vereinigung der beiden Quell Rechtecke.

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parameter

*lpRect1*<br/>
Verweist auf ein [Rect](/windows/win32/api/windef/ns-windef-rect) oder `CRect` , das ein Quell Rechteck enthält.

*lpRect2*<br/>
Verweist auf ein `RECT` oder `CRect` , das ein Quell Rechteck enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Union nicht leer ist. 0, wenn die Union leer ist.

### <a name="remarks"></a>Bemerkungen

Die Union ist das kleinste Rechteck, das beide Quell Rechtecke enthält.

Die Abmessungen eines leeren Rechtecks werden von Windows ignoriert. Das heißt, ein Rechteck, das keine Höhe hat oder keine Breite hat.

> [!NOTE]
> Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3.UnionRect(&rect1, &rect2);
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

## <a name="crectwidth"></a><a name="width"></a> CRect:: width

Berechnet die Breite von, `CRect` indem der linke Wert von dem rechten Wert subtrahieren wird.

```
int Width() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Breite von `CRect` .

### <a name="remarks"></a>Bemerkungen

Die Breite kann negativ sein.

> [!NOTE]
> Das Rechteck muss normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um das Rechteck zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect rect(20, 30, 80, 70);
int nWid = rect.Width();
// nWid is now 60
ASSERT(nWid == 60);
```

## <a name="see-also"></a>Weitere Informationen

[CPoint-Klasse](cpoint-class.md)<br/>
[CSize-Klasse](csize-class.md)<br/>
[Rect](/windows/win32/api/windef/ns-windef-rect)

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
ms.openlocfilehash: 13f86c411cca98f5817d1b3b2d9162ae8af8b734
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866531"
---
# <a name="crect-class"></a>CRect-Klasse

Ähnelt einer Windows- [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur.

## <a name="syntax"></a>Syntax

```
class CRect : public tagRECT
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRect:: CRect](#crect)|Erstellt ein `CRect`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRect:: BottomRight](#bottomright)|Gibt den unteren rechten Punkt `CRect`zurück.|
|[CRect:: Centerpoint](#centerpoint)|Gibt den Mittelpunkt der `CRect`zurück.|
|[CRect:: copyrect](#copyrect)|Kopiert die Dimensionen eines Quell Rechtecks in `CRect`.|
|[CRect::D eflaterect](#deflaterect)|Verringert die Breite und Höhe der `CRect`.|
|[CRect:: equalrect](#equalrect)|Bestimmt, ob `CRect` gleich dem angegebenen Rechteck ist.|
|[CRect:: height](#height)|Berechnet die Höhe `CRect`.|
|[CRect:: inflaterect](#inflaterect)|Erhöht die Breite und Höhe der `CRect`.|
|[CRect:: intersectRect](#intersectrect)|Legt `CRect` gleich der Schnittmenge von zwei Rechtecke fest.|
|[CRect:: isrectempty](#isrectempty)|Bestimmt, ob `CRect` leer ist. `CRect` ist leer, wenn Breite und/oder Höhe 0 (null) ist.|
|[CRect:: isrectnull](#isrectnull)|Bestimmt, ob die `top`-, `bottom`-, `left`-und `right`-Element Variablen gleich 0 sind.|
|[CRect:: muvetox](#movetox)|Verschiebt `CRect` in die angegebene x-Koordinate.|
|[CRect:: muvedexy](#movetoxy)|Verschiebt `CRect` zu den angegebenen x-und y-Koordinaten.|
|[CRect:: muvetoy](#movetoy)|Verschiebt `CRect` in die angegebene y-Koordinate.|
|[CRect:: NormalizeRect](#normalizerect)|Standardisiert die Höhe und Breite der `CRect`.|
|[CRect:: offsetrect](#offsetrect)|Verschiebt `CRect` um die angegebenen Offsets.|
|[CRect::P tinrect](#ptinrect)|Bestimmt, ob der angegebene Punkt innerhalb `CRect`liegt.|
|[CRect:: SetRect](#setrect)|Legt die Dimensionen `CRect`fest.|
|[CRect:: setrectempty](#setrectempty)|Legt `CRect` auf ein leeres Rechteck (alle Koordinaten gleich 0) fest.|
|[CRect:: size](#size)|Berechnet die Größe der `CRect`.|
|[CRect:: subtractrect](#subtractrect)|Subtrahiert ein Rechteck von einem anderen.|
|[CRect:: TopLeft](#topleft)|Gibt den oberen linken Punkt der `CRect`zurück.|
|[CRect:: unionrect](#unionrect)|Legt `CRect` gleich der Union von zwei Rechtecke fest.|
|[CRect:: width](#width)|Berechnet die Breite des `CRect`.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CRect:: Operator-](#operator_-)|Subtrahiert die angegebenen Offsets von `CRect` oder defliert `CRect` und gibt die resultierende `CRect`zurück.|
|[CRect:: Operator lpcrect](#operator_lpcrect)|Konvertiert ein `CRect`-Element in ein `LPCRECT`-Element.|
|[CRect:: Operator lprect](#operator_lprect)|Konvertiert ein `CRect`-Element in ein `LPRECT`-Element.|
|[CRect:: Operator! =](#operator_neq)|Bestimmt, ob `CRect` nicht gleich einem Rechteck ist.|
|[CRect:: Operator &amp;](#operator_amp)|Erstellt die Schnittmenge `CRect` und eines Rechtecks und gibt die resultierende `CRect`zurück.|
|[CRect:: Operator &amp;=](#operator_amp_eq)|Legt `CRect` gleich der Schnittmenge `CRect` und eines Rechtecks fest.|
|[CRect::-Operator&#124;](#operator_or)|Erstellt die Vereinigung `CRect` und eines Rechtecks und gibt die resultierende `CRect`zurück.|
|[CRect:: Operator &#124;=](#operator_or_eq)|Legt `CRect` gleich der Vereinigung von `CRect` und einem Rechteck fest.|
|[CRect:: Operator +](#operator_add)|Fügt die angegebenen Offsets `CRect` oder vergrößert `CRect` und gibt die resultierende `CRect`zurück.|
|[CRect:: Operator + =](#operator_add_eq)|Fügt die angegebenen Offsets `CRect` oder vergrößert `CRect`.|
|[CRect:: Operator =](#operator_eq)|Kopiert die Dimensionen eines Rechtecks in `CRect`.|
|[CRect:: Operator-=](#operator_-_eq)|Subtrahiert die angegebenen Offsets von `CRect` oder entleert `CRect`.|
|[CRect:: Operator = =](#operator_eq_eq)|Bestimmt, ob `CRect` gleich einem Rechteck ist.|

## <a name="remarks"></a>Bemerkungen

`CRect` umfasst auch Element Funktionen zum Bearbeiten von `CRect` Objekten und Windows-`RECT` Strukturen.

Ein `CRect`-Objekt kann immer dann als Funktionsparameter übergeben werden, wenn eine `RECT` Struktur, `LPCRECT`oder `LPRECT` übergeben werden kann.

> [!NOTE]
> Diese Klasse wird von der `tagRECT` Struktur abgeleitet. (Der Name `tagRECT` ist ein Name für die `RECT` Struktur, der weniger häufig verwendet wird.) Dies bedeutet, dass die Datenmember (`left`, `top`, `right`und `bottom`) der `RECT` Struktur auf die Datenmember `CRect`zugreifen können.

Ein `CRect` der Element Variablen enthält, die die oberen linken und unteren rechten Punkte eines Rechtecks definieren.

Beim Angeben einer `CRect`müssen Sie darauf achten, Sie so zu erstellen, dass Sie normalisiert wird, d. –., dass der Wert der linken Koordinate kleiner als der Rechte und der obere kleiner als der untere Wert ist. Beispielsweise wird in einer oberen linken Ecke von (10, 10) und unten rechts von (20, 20) ein normalisiertes Rechteck definiert, aber von oben links (20, 20) und von unten rechts von (10, 10) wird ein nicht normalisiertes Rechteck definiert. Wenn das Rechteck nicht normalisiert ist, geben viele `CRect` Member-Funktionen möglicherweise falsche Ergebnisse zurück. (Eine Liste dieser Funktionen finden Sie unter [CRect:: NormalizeRect](#normalizerect) .) Bevor Sie eine Funktion aufrufen, die normalisierte Rechtecke erfordert, können Sie nicht normalisierte Rechtecke normalisieren, indem Sie die `NormalizeRect`-Funktion aufrufen.

Seien Sie vorsichtig, wenn Sie eine `CRect` mit den Member-Funktionen [CDC::D ptolp](../../mfc/reference/cdc-class.md#dptolp) und [CDC:: lptodp](../../mfc/reference/cdc-class.md#lptodp) bearbeiten. Wenn der Kartenmodus eines Anzeige Kontexts so ist, dass der y-Block negativ ist, wie z. b. `MM_LOENGLISH`, transformiert `CDC::DPtoLP` den `CRect`, sodass der obere Wert größer als der untere Wert ist. Funktionen wie `Height` und `Size` geben dann negative Werte für die Höhe des transformierten `CRect`zurück, und das Rechteck wird nicht normalisiert.

Wenn überladene `CRect` Operatoren verwendet werden, muss der erste Operand ein `CRect`sein. der zweite kann entweder eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder ein `CRect` Objekt sein.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`tagRECT`

`CRect`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** atltypes. h

##  <a name="bottomright"></a>CRect:: BottomRight

Die Koordinaten werden als Verweis auf ein [CPoint](cpoint-class.md) -Objekt zurückgegeben, das in `CRect`enthalten ist.

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

##  <a name="centerpoint"></a>CRect:: Centerpoint

Berechnet den Mittelpunkt `CRect` durch Hinzufügen der linken und rechten Werte und durch zwei Dividieren und durch das Hinzufügen der obersten und untersten Werte und durch zwei dividieren.

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein `CPoint`-Objekt, das der Mittelpunkt der `CRect`ist.

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

##  <a name="copyrect"></a>CRect:: copyrect

Kopiert das `lpSrcRect` Rechteck in `CRect`.

```
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>Parameter

*lpsrcrect*<br/>
Verweist auf die [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder `CRect` Objekt, das kopiert werden soll.

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

##  <a name="crect"></a>CRect:: CRect

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
Gibt die linke Position `CRect`an.

*t*<br/>
Gibt den Anfang `CRect`an.

*r*<br/>
Gibt die richtige Position `CRect`an.

*b*<br/>
Gibt den unteren `CRect`an.

*srcRect*<br/>
Verweist auf die [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur mit den Koordinaten für `CRect`.

*lpsrcrect*<br/>
Verweist auf die `RECT` Struktur mit den Koordinaten für `CRect`.

*Punkt*<br/>
Gibt den Ursprungs Punkt für das Rechteck an, das erstellt werden soll. Entspricht der linken oberen Ecke.

*size*<br/>
Gibt die Verschiebung von der linken oberen Ecke zur rechten unteren Ecke des zu erstellenden Rechtecks an.

*TopLeft*<br/>
Gibt die linke obere Position `CRect`an.

*BottomRight*<br/>
Gibt die untere rechte Position `CRect`an.

### <a name="remarks"></a>Bemerkungen

Wenn keine Argumente angegeben werden, werden `left`-, `top`-, `right`-und `bottom` Member nicht initialisiert.

Die `CRect`(`const RECT&`) und `CRect`(`LPCRECT`)-Konstruktoren führen ein [copyrect](#copyrect)aus. Die anderen Konstruktoren initialisieren die Element Variablen des-Objekts direkt.

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

##  <a name="deflaterect"></a>CRect::D eflaterect

`DeflateRect` defliert `CRect` durch Verschieben der Seiten in den Mittelpunkt.

```
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>Parameter

*x*<br/>
Gibt die Anzahl der Einheiten an, die die linke und die Rechte Seite des `CRect`deflieren.

*y*<br/>
Gibt die Anzahl der Einheiten an, um den oberen und unteren Rand `CRect`zu isolieren.

*size*<br/>
Eine [Größe](/windows/win32/api/windef/ns-windef-size) oder [CSize](csize-class.md) , die die Anzahl der Einheiten für die Deflate `CRect`angibt. Der `cx`-Wert gibt die Anzahl der Einheiten an, um die linke und die Rechte Seite zu isolieren, und der `cy` Wert gibt die Anzahl der Einheiten an, um den oberen und unteren Rand zu isolieren.

*lprect*<br/>
Verweist auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder `CRect`, die die Anzahl der Einheiten für die Deflate der einzelnen Seiten angibt.

*l*<br/>
Gibt die Anzahl der Einheiten an, um die linke Seite `CRect`zu deflieren.

*t*<br/>
Gibt die Anzahl der Einheiten an, um den Anfang `CRect`zu isolieren.

*r*<br/>
Gibt die Anzahl der Einheiten an, um die Rechte Seite `CRect`zu deflieren.

*b*<br/>
Gibt die Anzahl der Einheiten an, die das Ende der `CRect`deflate überwiegen.

### <a name="remarks"></a>Bemerkungen

Zu diesem Zweck fügt `DeflateRect` Einheiten Links und oben hinzu und subtrahiert Einheiten von rechts nach unten. Die Parameter `DeflateRect` sind signierte Werte. positive Werte deflate `CRect` und negative Werte erhöhen diese Werte.

Die ersten beiden über Ladungen isolieren beide Paare von gegenüberliegenden Seiten `CRect`, sodass die Gesamtbreite um das zweifache *x* (oder `cx`) verringert wird und die Gesamthöhe um das zwei *fache (oder* `cy`) verringert wird. Die anderen beiden über Ladungen deflieren jede Seite `CRect` unabhängig von den anderen.

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

##  <a name="equalrect"></a>CRect:: equalrect

Bestimmt, ob `CRect` gleich dem angegebenen Rechteck ist.

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parameter

*lprect*<br/>
Verweist auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder `CRect` Objekt, das die linke obere und untere rechte Eckkoordinaten eines Rechtecks enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die beiden Rechtecke dieselben Werte für Top, Left, Bottom und Right aufweisen; andernfalls 0.

> [!NOTE]
>  Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

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

##  <a name="height"></a>CRect:: height

Berechnet die Höhe `CRect` durch Subtrahieren des obersten Werts vom unteren Wert.

```
int Height() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Höhe `CRect`.

### <a name="remarks"></a>Bemerkungen

Der resultierende Wert kann negativ sein.

> [!NOTE]
>  Das Rechteck muss normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um das Rechteck zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

##  <a name="inflaterect"></a>CRect:: inflaterect

`InflateRect` vergrößert `CRect`, indem seine Seiten von seinem Mittelpunkt entfernt werden.

```
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>Parameter

*x*<br/>
Gibt die Anzahl der Einheiten an, um die linke und die Rechte Seite `CRect`zu erhöhen.

*y*<br/>
Gibt die Anzahl der Einheiten an, um den oberen und unteren Rand `CRect`zu erhöhen.

*size*<br/>
Eine [Größe](/windows/win32/api/windef/ns-windef-size) oder [CSize](csize-class.md) , die die Anzahl der Einheiten angibt, die `CRect`vergrößert werden soll. Der `cx`-Wert gibt die Anzahl der Einheiten an, um die linke und die Rechte Seite aufzufüllen, und der `cy` Wert gibt die Anzahl der Einheiten an, um den oberen und unteren Rand aufzufüllen.

*lprect*<br/>
Verweist auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder `CRect`, die die Anzahl von Einheiten angibt, mit denen die einzelnen Seiten vergrößert werden.

*l*<br/>
Gibt die Anzahl der Einheiten an, um die linke Seite `CRect`zu erhöhen.

*t*<br/>
Gibt die Anzahl der Einheiten an, um den Anfang `CRect`zu erhöhen.

*r*<br/>
Gibt die Anzahl der Einheiten an, die die Rechte Seite `CRect`erhöhen soll.

*b*<br/>
Gibt die Anzahl der Einheiten an, um den unteren `CRect`zu erhöhen.

### <a name="remarks"></a>Bemerkungen

Zu diesem Zweck `InflateRect` subtrahiert Einheiten von links nach oben und fügt Einheiten rechts und unten hinzu. Die Parameter `InflateRect` sind signierte Werte. positive Werte erhöhen `CRect` und negative Werte deflate.

Die ersten beiden über Ladungen erhöhen beide Paare von gegenüberliegenden Seiten `CRect`, sodass die Gesamtbreite um das zweifache *x* (oder `cx`) erhöht wird und die Gesamthöhe um das zwei *fache (oder* `cy`) erhöht wird. Die anderen beiden über Ladungen erhöhen jede Seite `CRect` unabhängig von den anderen.

### <a name="example"></a>Beispiel

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

##  <a name="intersectrect"></a>CRect:: intersectRect

Macht eine `CRect` gleich der Schnittmenge zweier bestehender Rechtecke.

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parameter

*lpRect1*<br/>
Verweist auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder `CRect` Objekt, das ein Quell Rechteck enthält.

*lpRect2*<br/>
Verweist auf eine `RECT` Struktur oder `CRect` Objekt, das ein Quell Rechteck enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Schnittmenge nicht leer ist. 0, wenn die Schnittmenge leer ist.

### <a name="remarks"></a>Bemerkungen

Die Schnittmenge ist das größte Rechteck, das in beiden vorhandenen Rechtecke enthalten ist.

> [!NOTE]
>  Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

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

##  <a name="isrectempty"></a>CRect:: isrectempty

Bestimmt, ob `CRect` leer ist.

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn `CRect` leer ist. 0, wenn `CRect` nicht leer ist.

### <a name="remarks"></a>Bemerkungen

Ein Rechteck ist leer, wenn Breite und/oder Höhe 0 oder negativ sind. Unterscheidet sich von `IsRectNull`, die bestimmt, ob alle Koordinaten des Rechtecks NULL sind.

> [!NOTE]
>  Das Rechteck muss normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um das Rechteck zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
ASSERT(rectEmpty.IsRectEmpty());
```

##  <a name="isrectnull"></a>CRect:: isrectnull

Bestimmt, ob die Werte für "Top", "Left", "Bottom" und "Right" `CRect` gleich 0 sind.

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn `CRect`die Werte Top, Left, Bottom und right gleich 0 sind. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Unterscheidet sich von `IsRectEmpty`, die bestimmt, ob das Rechteck leer ist.

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

##  <a name="movetox"></a>CRect:: muvetox

Mit dieser Funktion können Sie das Rechteck in die absolute x-Koordinate verschieben, die von *x*angegeben wird.

```
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

##  <a name="movetoxy"></a>CRect:: muvedexy

Mit dieser Funktion können Sie das Rechteck in die absolute x-und y-Koordinaten verschieben.

```
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>Parameter

*x*<br/>
Die absolute x-Koordinate für die linke obere Ecke des Rechtecks.

*y*<br/>
Die absolute y-Koordinate für die linke obere Ecke des Rechtecks.

*Punkt*<br/>
Eine `POINT`-Struktur, die die absolute linke obere Ecke des Rechtecks angibt.

### <a name="example"></a>Beispiel

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
ASSERT(rect == CRect(10, 10, 110, 110));
```

##  <a name="movetoy"></a>CRect:: muvetoy

Mit dieser Funktion können Sie das Rechteck in die absolute, von *y*angegebene y-Koordinate verschieben.

```
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

##  <a name="normalizerect"></a>CRect:: NormalizeRect

Normalisiert `CRect`, sodass sowohl die Höhe als auch die Breite positiv sind.

```
void NormalizeRect() throw();
```

### <a name="remarks"></a>Bemerkungen

Das Rechteck wird zur Positionierung des vierten Quadranten normalisiert, das Windows in der Regel für Koordinaten verwendet. `NormalizeRect` vergleicht die oberen und unteren Werte und tauscht Sie aus, wenn der obere Wert größer als der untere Wert ist. Entsprechend werden die linken und rechten Werte ausgetauscht, wenn die linke Seite größer als die Rechte ist. Diese Funktion ist nützlich, wenn Sie mit unterschiedlichen Karten Modi und umgekehrten Rechtecke umzugehen.

> [!NOTE]
> Die folgenden `CRect` Member-Funktionen erfordern normalisierte Rechtecke, damit Sie ordnungsgemäß funktionieren: [height](#height), [Width](#width), [size](#size), [isrectempty](#isrectempty), [PtInRect](#ptinrect), [equalrect](#equalrect), [unionrect](#unionrect), [intersectRect](#intersectrect), [subtractrect](#subtractrect), [Operator = =](#operator_eq_eq), [Operator! =](#operator_neq), [Operator &#124; ](#operator_or), [Operator &#124;=](#operator_or_eq), [Operator &](#operator_amp)und [Operator & =](#operator_amp_eq).

### <a name="example"></a>Beispiel

```cpp
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
rect2.NormalizeRect();
ASSERT(rect1 == rect2);
```

##  <a name="offsetrect"></a>CRect:: offsetrect

Verschiebt `CRect` um die angegebenen Offsets.

```
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

Verschiebt `CRect`*x* -Einheiten entlang der x-Achse und *y* -Einheiten entlang der y-Achse. Der *x* -und der *y* -Parameter sind signierte Werte, sodass `CRect` nach links oder rechts oder nach oben oder unten verschoben werden können.

### <a name="example"></a>Beispiel

```cpp
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

// rect is now (230, 230, 265, 265)
ASSERT(rect == CRect(230, 230, 265, 265));
```

##  <a name="operator_lpcrect"></a>CRect:: Operator lpcrect konvertiert eine `CRect` in ein [lpcrect](../../mfc/reference/data-types-mfc.md).

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Funktion verwenden, benötigen Sie den Address-of-Operator ( **&** ) nicht. Dieser Operator wird automatisch verwendet, wenn Sie ein `CRect` Objekt an eine Funktion übergeben, die eine `LPCRECT`erwartet.

##  <a name="operator_lprect"></a>CRect:: Operator lprect

Konvertiert einen `CRect` in einen [lprect](../../mfc/reference/data-types-mfc.md).

```
operator LPRECT() throw();
```

### <a name="remarks"></a>Bemerkungen

Wenn Sie diese Funktion verwenden, benötigen Sie den Address-of-Operator ( **&** ) nicht. Dieser Operator wird automatisch verwendet, wenn Sie ein `CRect` Objekt an eine Funktion übergeben, die eine `LPRECT`erwartet.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CRect:: Operator lpcrect](#operator_lpcrect).

##  <a name="operator_eq"></a>CRect:: Operator =

Weist *srcRect* `CRect`zu.

```
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>Parameter

*srcRect*<br/>
Verweist auf ein Quell Rechteck. Kann ein [Rect](/windows/win32/api/windef/ns-windef-rect) oder `CRect`sein.

### <a name="example"></a>Beispiel

```cpp
CRect rect(0, 0, 127, 168);
CRect rect2;

rect2 = rect;
ASSERT(rect2 == CRect(0, 0, 127, 168));
```

##  <a name="operator_eq_eq"></a>CRect:: Operator = =

Bestimmt, ob `rect` gleich `CRect` ist, indem die Koordinaten ihrer oberen linken und unteren rechten Ecke verglichen werden.

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Verweist auf ein Quell Rechteck. Kann ein [Rect](/windows/win32/api/windef/ns-windef-rect) oder `CRect`sein.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn gleich andernfalls 0.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
>  Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

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

##  <a name="operator_neq"></a>CRect:: Operator! =

Bestimmt, ob *Rect* nicht gleich `CRect` ist, indem die Koordinaten ihrer oberen linken und unteren rechten Ecke verglichen werden.

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Verweist auf ein Quell Rechteck. Kann ein [Rect](/windows/win32/api/windef/ns-windef-rect) oder `CRect`sein.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn nicht gleich; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
>  Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

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

##  <a name="operator_add_eq"></a>CRect:: Operator + =

Die ersten beiden über Ladungen verschieben `CRect` durch die angegebenen Offsets.

```
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
Verweist auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder `CRect` Objekt, das die Anzahl der Einheiten enthält, um jede Seite `CRect`aufzufüllen.

### <a name="remarks"></a>Bemerkungen

Die Werte *x* und *y* des Parameters (oder `cx` und `cy`) werden `CRect`hinzugefügt.

Die dritte Überladung vergrößert `CRect` um die in jedem Element des Parameters angegebene Anzahl von Einheiten.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint  pt(35, 65);
CRect   rect2(135, 300, 235, 400);

rect1 += pt;
ASSERT(rect1 == rect2);
```

##  <a name="operator_-_eq"></a>CRect:: Operator-=

Die ersten beiden über Ladungen verschieben `CRect` durch die angegebenen Offsets.

```
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
Verweist auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder `CRect` Objekt, das die Anzahl der Einheiten enthält, um jede Seite `CRect`zu isolieren.

### <a name="remarks"></a>Bemerkungen

Die Werte *x* und *y* des-Parameters (oder `cx` und `cy`) werden von `CRect`subtrahiert.

Die dritte Überladung defliert `CRect` durch die Anzahl der Einheiten, die in jedem Member des Parameters angegeben werden. Beachten Sie, dass diese Überladung wie [deflaterect](#deflaterect)funktioniert.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);

rect1 -= pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect1 == rectResult);
```

##  <a name="operator_amp_eq"></a>CRect:: Operator &amp;=

Legt `CRect` gleich der Schnittmenge von `CRect` und `rect`fest.

```
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Enthält ein [Rect](/windows/win32/api/windef/ns-windef-rect) -oder `CRect`.

### <a name="remarks"></a>Bemerkungen

Die Schnittmenge ist das größte Rechteck, das in beiden Rechtecke enthalten ist.

> [!NOTE]
>  Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel für [CRect:: intersectRect](#intersectrect).

##  <a name="operator_or_eq"></a>CRect:: Operator &#124;=

Legt `CRect` gleich der Union von `CRect` und `rect`fest.

```
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Enthält eine `CRect` oder ein [Rect](/windows/win32/api/windef/ns-windef-rect).

### <a name="remarks"></a>Bemerkungen

Die Union ist das kleinste Rechteck, das beide Quell Rechtecke enthält.

> [!NOTE]
>  Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);

rect1 |= rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect1);
```

##  <a name="operator_add"></a>CRect:: Operator +

Die ersten beiden-über Ladungen geben ein `CRect` Objekt zurück, das gleich `CRect` ist, das von den angegebenen Offsets vertrieben wird.

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
Verweist auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder `CRect` Objekt, das die Anzahl der Einheiten enthält, um die einzelnen Seiten des Rückgabewerts aufzufüllen.

### <a name="return-value"></a>Rückgabewert

Die `CRect`, die sich aus der Verschiebung oder Vergrößerung `CRect` durch die im-Parameter angegebene Anzahl von Einheiten ergeben.

### <a name="remarks"></a>Bemerkungen

Die *x* -und *y* -Parameter (oder `cx` und `cy`) des Parameters werden der Position `CRect`hinzugefügt.

Die dritte Überladung gibt eine neue `CRect` zurück, die gleich `CRect` durch die Anzahl der Einheiten ist, die in jedem Member des-Parameters angegeben ist.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 + pt;
CRect   rectResult(135, 300, 235, 400);
ASSERT(rectResult == rect2);
```

##  <a name="operator_-"></a>CRect:: Operator-

Die ersten beiden-über Ladungen geben ein `CRect` Objekt zurück, das gleich `CRect` ist, das von den angegebenen Offsets vertrieben wird.

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Eine [Punkt](/windows/win32/api/windef/ns-windef-point) Struktur oder `CPoint` Objekt, das die Anzahl der Einheiten angibt, mit denen der Rückgabewert verschoben wird.

*size*<br/>
Eine [Größen](/windows/win32/api/windef/ns-windef-size) Struktur oder `CSize` Objekt, das die Anzahl der Einheiten angibt, die der Rückgabewert verschieben soll.

*lprect*<br/>
Verweist auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder `CRect` Objekt, das die Anzahl der Einheiten enthält, um die einzelnen Seiten des Rückgabewerts zu deflieren.

### <a name="return-value"></a>Rückgabewert

Die `CRect`, die sich aus dem Verschieben oder deflating `CRect` durch die im-Parameter angegebene Anzahl von Einheiten ergeben.

### <a name="remarks"></a>Bemerkungen

Die *x* -und *y* -Parameter (oder `cx` und `cy`) des Parameters werden von der Position des `CRect`subtrahiert.

Die dritte Überladung gibt eine neue `CRect` zurück, die `CRect` gleich der Anzahl der Einheiten ist, die in jedem Member des-Parameters angegeben werden. Beachten Sie, dass diese Überladung wie [deflaterect](#deflaterect)funktioniert, nicht [subtractrect](#subtractrect).

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 - pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect2 == rectResult);
```

##  <a name="operator_amp"></a>CRect:: Operator &amp;

Gibt einen `CRect` zurück, der die Schnittmenge von `CRect` und *rect2*ist.

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>Parameter

*rect2*<br/>
Enthält ein [Rect](/windows/win32/api/windef/ns-windef-rect) -oder `CRect`.

### <a name="return-value"></a>Rückgabewert

Eine `CRect`, die die Schnittmenge von `CRect` und *rect2*ist.

### <a name="remarks"></a>Bemerkungen

Die Schnittmenge ist das größte Rechteck, das in beiden Rechtecke enthalten ist.

> [!NOTE]
>  Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 & rect2;
CRect   rectResult(100, 100, 200, 200);
ASSERT(rectResult == rect3);
```

##  <a name="operator_or"></a>CRect::-Operator&#124;

Gibt einen `CRect` zurück, der die Union von `CRect` und *rect2*ist.

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>Parameter

*rect2*<br/>
Enthält ein [Rect](/windows/win32/api/windef/ns-windef-rect) -oder `CRect`.

### <a name="return-value"></a>Rückgabewert

Eine `CRect`, die die Union von `CRect` und *rect2*ist.

### <a name="remarks"></a>Bemerkungen

Die Union ist das kleinste Rechteck, das beide Rechtecke enthält.

> [!NOTE]
>  Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 | rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

##  <a name="ptinrect"></a>CRect::P tinrect

Bestimmt, ob der angegebene Punkt innerhalb `CRect`liegt.

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Enthält eine [Punkt](/windows/win32/api/windef/ns-windef-point) Struktur oder ein [CPoint](cpoint-class.md) -Objekt.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der Punkt innerhalb `CRect`liegt. andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ein Punkt befindet sich innerhalb `CRect`, wenn er auf der linken oder oberen Seite liegt oder sich auf allen vier Seiten befindet. Ein Punkt auf der rechten oder unteren Seite liegt außerhalb `CRect`.

> [!NOTE]
>  Das Rechteck muss normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um das Rechteck zu normalisieren, bevor Sie diese Funktion aufrufen.

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

##  <a name="setrect"></a>CRect:: SetRect

Legt die Dimensionen der `CRect` auf die angegebenen Koordinaten fest.

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

*Y2*<br/>
Gibt die y-Koordinate der unteren rechten Ecke an.

### <a name="example"></a>Beispiel

```cpp
CRect rect;
rect.SetRect(256, 256, 512, 512);
ASSERT(rect == CRect(256, 256, 512, 512));
```

##  <a name="setrectempty"></a>CRect:: setrectempty

Macht `CRect` ein Rechteck NULL, indem alle Koordinaten auf NULL festgelegt werden.

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

##  <a name="size"></a>CRect:: size

Die `cx`-und `cy` Member des Rückgabewerts enthalten die Höhe und Breite der `CRect`.

```
CSize Size() const throw();
```

### <a name="return-value"></a>Rückgabewert

Ein [CSize](csize-class.md) -Objekt, das die Größe der `CRect`enthält.

### <a name="remarks"></a>Bemerkungen

Entweder die Höhe oder die Breite kann negativ sein.

> [!NOTE]
>  Das Rechteck muss normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um das Rechteck zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

##  <a name="subtractrect"></a>CRect:: subtractrect

Macht die Dimensionen der `CRect` gleich der Subtraktion von `lpRectSrc2` von `lpRectSrc1`.

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>Parameter

*lpRectSrc1*<br/>
Verweist auf die [Rect](/windows/win32/api/windef/ns-windef-rect) -Struktur oder `CRect` Objekt, von dem ein Rechteck subtrahiert werden soll.

*lpRectSrc2*<br/>
Verweist auf die `RECT` Struktur oder `CRect` Objekt, das von dem Rechteck subtrahiert werden soll, auf das der *lpRectSrc1* -Parameter zeigt.

### <a name="return-value"></a>Rückgabewert

Ist ungleich null (0), wenn die Funktion erfolgreich ausgeführt wird, andernfalls null (0).

### <a name="remarks"></a>Bemerkungen

Die Subtraktion ist das kleinste Rechteck, das alle Punkte in *lpRectScr1* enthält, die sich nicht in der Schnittmenge von *lpRectScr1* und *lpRectScr2*befinden.

Das von *lpRectSrc1* angegebene Rechteck ist unverändert, wenn das von *lpRectSrc2* angegebene Rechteck nicht vollständig mit dem durch *lpRectSrc1* in mindestens einer der x-oder y-Richtung angegebenen Rechteck überlappt.

Wenn z. b. *lpRectSrc1* (10, 10, 100.100) und *lpRectSrc2* (50, 50, 150.150) waren, wäre das Rechteck, auf das von *lpRectSrc1* verwiesen wird, unverändert, wenn die Funktion zurückgegeben wird. Wenn *lpRectSrc1* (10, 10, 100.100) und *lpRectSrc2* (50, 10, 150.150) lauten, würde das Rechteck, auf das von *lpRectSrc1* gezeigt wird, die Koordinaten (10, 10, 50.100) enthalten, wenn die Funktion zurückgegeben wird.

`SubtractRect` ist nicht identisch mit [Operator-](#operator_-) oder [Operator-=](#operator_-_eq). Keiner dieser Operatoren ruft jemals `SubtractRect`auf.

> [!NOTE]
>  Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

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

##  <a name="topleft"></a>CRect:: TopLeft

Die Koordinaten werden als Verweis auf ein [CPoint](cpoint-class.md) -Objekt zurückgegeben, das in `CRect`enthalten ist.

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

##  <a name="unionrect"></a>CRect:: unionrect

Macht die Dimensionen von `CRect` gleich der Vereinigung der beiden Quell Rechtecke.

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parameter

*lpRect1*<br/>
Verweist auf eine [Rect](/windows/win32/api/windef/ns-windef-rect) -oder `CRect`, die ein Quell Rechteck enthält.

*lpRect2*<br/>
Verweist auf einen `RECT` oder `CRect`, der ein Quell Rechteck enthält.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn die Union nicht leer ist. 0, wenn die Union leer ist.

### <a name="remarks"></a>Bemerkungen

Die Union ist das kleinste Rechteck, das beide Quell Rechtecke enthält.

Die Abmessungen eines leeren Rechtecks werden von Windows ignoriert. Das heißt, ein Rechteck, das keine Höhe hat oder keine Breite hat.

> [!NOTE]
>  Beide Rechtecke müssen normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um die Rechtecke zu normalisieren, bevor Sie diese Funktion aufrufen.

### <a name="example"></a>Beispiel

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3.UnionRect(&rect1, &rect2);
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

##  <a name="width"></a>CRect:: width

Berechnet die Breite der `CRect`, indem der linke Wert von dem rechten Wert subtrahieren wird.

```
int Width() const throw();
```

### <a name="return-value"></a>Rückgabewert

Die Breite der `CRect`.

### <a name="remarks"></a>Bemerkungen

Die Breite kann negativ sein.

> [!NOTE]
>  Das Rechteck muss normalisiert werden, da diese Funktion möglicherweise fehlschlägt. Sie können [NormalizeRect](#normalizerect) aufrufen, um das Rechteck zu normalisieren, bevor Sie diese Funktion aufrufen.

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

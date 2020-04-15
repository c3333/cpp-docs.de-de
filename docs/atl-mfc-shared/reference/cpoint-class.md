---
title: CPoint-Klasse
ms.date: 11/04/2016
f1_keywords:
- CPoint
- ATLTYPES/ATL::CPoint
- ATLTYPES/ATL::CPoint::CPoint
- ATLTYPES/ATL::CPoint::Offset
helpviewer_keywords:
- LPPOINT structure
- POINT structure
- CPoint class
ms.assetid: a6d4db93-35cc-444d-9221-c3e160f6edaa
ms.openlocfilehash: a806cfa18119df9beef3e070a65bc238a12580a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317718"
---
# <a name="cpoint-class"></a>CPoint-Klasse

Ähnlich der Windows-Struktur `POINT` .

## <a name="syntax"></a>Syntax

```
class CPoint : public tagPOINT
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPoint::CPoint](#cpoint)|Erstellt ein Objekt vom Typ `CPoint`.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPoint::Offset](#offset)|Fügt Werte `x` zu `y` der `CPoint`und Member der hinzu.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CPoint::Operator -](#operator_-)|Gibt die Differenz `CPoint` von a und einer Größe oder die Negation eines Punktes oder die Größendifferenz zwischen zwei Punkten oder den Offset durch eine negative Größe zurück.|
|[CPoint::operator !=](#operator_neq)|Überprüft die Ungleichheit zwischen zwei Punkten.|
|[CPoint::Operator +](#operator_add)|Gibt die Summe `CPoint` von a und einer `CRect` Größe oder einem Punkt oder einen Versatz um eine Größe zurück.|
|[CPoint::operator +=](#operator_add_eq)|Versatz `CPoint` durch Hinzufügen einer Größe oder eines Punkts.|
|[CPoint::operator -=](#operator_-_eq)|Versatz `CPoint` durch Subtrahieren einer Größe oder eines Punkts.|
|[CPoint::operator ==](#operator_eq_eq)|Überprüft die Gleichheit zwischen zwei Punkten.|

## <a name="remarks"></a>Bemerkungen

Es enthält auch Memberfunktionen zum Bearbeiten `CPoint` und [POINT-Strukturen.](/windows/win32/api/windef/ns-windef-point)

Ein `CPoint` Objekt kann überall `POINT` dort verwendet werden, wo eine Struktur verwendet wird. Die Operatoren dieser Klasse, die mit einer "Größe" interagieren, akzeptieren entweder [CSize-Objekte](../../atl-mfc-shared/reference/csize-class.md) oder [SIZE-Strukturen,](/windows/win32/api/windef/ns-windef-size) da die beiden austauschbar sind.

> [!NOTE]
> Diese Klasse wird `tagPOINT` von der Struktur abgeleitet. (Der `tagPOINT` Name ist ein weniger `POINT` gebräuchener Name für die Struktur.) `POINT` Dies bedeutet, `x` dass die Datenmember der Struktur und `y`der zugriff auf Datenmember von `CPoint`sind.

> [!NOTE]
> Weitere Informationen zu freigegebenen `CPoint`Dienstprogrammklassen (z. B. ) finden Sie unter [Freigegebene Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`tagPOINT`

`CPoint`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atltypes.h

## <a name="cpointcpoint"></a><a name="cpoint"></a>CPoint::CPoint

Erstellt ein `CPoint`-Objekt.

```
CPoint() throw();
CPoint(int initX, int initY) throw();
CPoint(POINT initPt) throw();
CPoint(SIZE initSize) throw();
CPoint(LPARAM dwPoint) throw();
```

### <a name="parameters"></a>Parameter

*initX*<br/>
Gibt den Wert des `x`-Members von `CPoint` an.

*initY*<br/>
Gibt den Wert des `y`-Members von `CPoint` an.

*initPt*<br/>
[POINT-Struktur](/windows/win32/api/windef/ns-windef-point) oder `CPoint` die die Werte `CPoint`angibt, die zum Initialisieren verwendet werden.

*initSize*<br/>
[SIZE-Struktur](/windows/win32/api/windef/ns-windef-size) oder [CSize,](../../atl-mfc-shared/reference/csize-class.md) die die `CPoint`Zum Initialisieren verwendeten Werte angibt.

*dwPoint*<br/>
Legt `x` das Element auf das Wort mit `y` niedriger Ordnung von *dwPoint* und das Element auf das Hochrangwort von *dwPoint*fest.

### <a name="remarks"></a>Bemerkungen

Wenn keine Argumente angegeben werden, werden die `x`- und `y`-Member auf 0 festgelegt.

### <a name="example"></a>Beispiel

```cpp
CPoint   ptTopLeft(0, 0);
// works from a POINT, too

POINT   ptHere;
ptHere.x = 35;
ptHere.y = 95;

CPoint   ptMFCHere(ptHere);

// works from a SIZE
SIZE   sHowBig;
sHowBig.cx = 300;
sHowBig.cy = 10;

CPoint ptMFCBig(sHowBig);
// or from a DWORD

DWORD   dwSize;
dwSize = MAKELONG(35, 95);

CPoint ptFromDouble(dwSize);
ASSERT(ptFromDouble == ptMFCHere);
```

## <a name="cpointoffset"></a><a name="offset"></a>CPoint::Offset

Fügt Werte `x` zu `y` der `CPoint`und Member der hinzu.

```
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### <a name="parameters"></a>Parameter

*xOffset*<br/>
Gibt den Betrag an, der das `x` Element der `CPoint`versetzt werden soll.

*yOffset*<br/>
Gibt den Betrag an, der das `y` Element der `CPoint`versetzt werden soll.

*Punkt*<br/>
Gibt den Betrag [POINT](/windows/win32/api/windef/ns-windef-point) ( `CPoint`POINT oder `CPoint`) an, um die zu verrechnen.

*Größe*<br/>
Gibt den Betrag ( [SIZE](/windows/win32/api/windef/ns-windef-size) oder [CSize )](../../atl-mfc-shared/reference/csize-class.md)an, um die `CPoint`zu versetzen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

## <a name="cpointoperator-"></a><a name="operator_eq_eq"></a>CPoint::operator ==

Überprüft die Gleichheit zwischen zwei Punkten.

```
BOOL operator==(POINT point) const throw();
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Enthält eine POINT-Struktur oder `CPoint` ein [PUNKTobjekt.](/windows/win32/api/windef/ns-windef-point)

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn die Punkte gleich sind; andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

## <a name="cpointoperator-"></a><a name="operator_neq"></a>CPoint::operator !=

Überprüft die Ungleichheit zwischen zwei Punkten.

```
BOOL operator!=(POINT point) const throw();
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Enthält eine POINT-Struktur oder `CPoint` ein [PUNKTobjekt.](/windows/win32/api/windef/ns-windef-point)

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn die Punkte nicht gleich sind; andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

## <a name="cpointoperator-"></a><a name="operator_add_eq"></a>CPoint::operator +=

Die erste Überladung fügt `CPoint`dem eine Größe hinzu.

```
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### <a name="parameters"></a>Parameter

*Größe*<br/>
Enthält eine [SIZE-Struktur](/windows/win32/api/windef/ns-windef-size) oder ein [CSize-Objekt.](../../atl-mfc-shared/reference/csize-class.md)

*Punkt*<br/>
Enthält eine [POINT-Struktur](/windows/win32/api/windef/ns-windef-point) oder ein [CPoint-Objekt.](../../atl-mfc-shared/reference/cpoint-class.md)

### <a name="remarks"></a>Bemerkungen

Die zweite Überladung fügt `CPoint`der einen Punkt hinzu.

In beiden `x` Fällen erfolgt das Hinzufügen `cx`des (oder ) Mitglieds des `x` rechten Operandens zum Member des `CPoint` und hinzufügen `y` des (oder `cy`) Elements des rechten Operandens `y` zum Member des . `CPoint`

Wenn Sie `CPoint(5, -7)` z. B. `CPoint(30, 40)` zu einer `CPoint(35, 33)`Variablen hinzufügen, die die Variable in enthält, wird geändert.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

## <a name="cpointoperator--"></a><a name="operator_-_eq"></a>CPoint::operator -=

Die erste Überladung subtrahiert `CPoint`eine Größe von der .

```
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### <a name="parameters"></a>Parameter

*Größe*<br/>
Enthält eine [SIZE-Struktur](/windows/win32/api/windef/ns-windef-size) oder ein [CSize-Objekt.](../../atl-mfc-shared/reference/csize-class.md)

*Punkt*<br/>
Enthält eine [POINT-Struktur](/windows/win32/api/windef/ns-windef-point) oder ein [CPoint-Objekt.](../../atl-mfc-shared/reference/cpoint-class.md)

### <a name="remarks"></a>Bemerkungen

Die zweite Überladung subtrahiert `CPoint`einen Punkt von der .

In beiden Fällen erfolgt die Subtraktion `x` durch `cx`Subtraktion des (oder ) Members `x` des `CPoint` rechten Operandens `cy`vom Member des und Subtraktion `y` des `y` (oder ) Members des rechten Operandens vom Member des . `CPoint`

Wenn Sie z. `CPoint(5, -7)` B. von `CPoint(30, 40)` einer Variablen `CPoint(25, 47)`subtrahieren, die die Variable in enthält.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

## <a name="cpointoperator-"></a><a name="operator_add"></a>CPoint::Operator +

Verwenden Sie diesen `CPoint` Operator, um `CPoint` durch ein `CRect` oder `CPoint`ein Objekt oder `CSize` einen durch einen zu verrechnen.

```
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="parameters"></a>Parameter

*Größe*<br/>
Enthält eine [SIZE-Struktur](/windows/win32/api/windef/ns-windef-size) oder ein [CSize-Objekt.](../../atl-mfc-shared/reference/csize-class.md)

*Punkt*<br/>
Enthält eine [POINT-Struktur](/windows/win32/api/windef/ns-windef-point) oder ein [CPoint-Objekt.](../../atl-mfc-shared/reference/cpoint-class.md)

*lpRect*<br/>
Enthält einen Zeiger auf eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) oder ein [CRect-Objekt.](../../atl-mfc-shared/reference/crect-class.md)

### <a name="return-value"></a>Rückgabewert

Eine, `CPoint` die durch eine `CPoint` Größe, eine, die durch `CRect` einen Punkt versetzt wird, oder durch einen Versatz durch einen Punkt versetzt wird.

### <a name="remarks"></a>Bemerkungen

Wenn Sie z. B. eine der ersten `CPoint(25, -19)` beiden `CPoint(15, 5)` Überladungen verwenden, um den Punkt um einen Punkt oder eine Größe zu versetzen, `CSize(15, 5)` wird der Wert `CPoint(40, -14)`zurückgegeben.

Wenn Sie einem Punkt ein Rechteck hinzufügen, `x` `y` wird das Rechteck zurückgegeben, nachdem es durch die und die im Punkt angegebenen Werte versetzt wurde. Wenn Sie z. B. die `CRect(125, 219, 325, 419)` letzte Überladung verwenden, um ein Rechteck um einen Punkt `CPoint(25, -19)` zu versetzen, wird zurückgegeben. `CRect(150, 200, 350, 400)`

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

## <a name="cpointoperator--"></a><a name="operator_-"></a>CPoint::Operator -

Verwenden Sie eine der ersten beiden `CPoint` Überladungen, um ein oder `CSize` ein Objekt von `CPoint`zu subtrahieren.

```
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Eine [POINT-Struktur](/windows/win32/api/windef/ns-windef-point) oder ein [CPoint-Objekt.](../../atl-mfc-shared/reference/cpoint-class.md)

*Größe*<br/>
Eine [SIZE-Struktur](/windows/win32/api/windef/ns-windef-size) oder ein [CSize-Objekt.](../../atl-mfc-shared/reference/csize-class.md)

*lpRect*<br/>
Ein Zeiger auf eine [RECT-Struktur](/windows/win32/api/windef/ns-windef-rect) oder ein [CRect-Objekt.](../../atl-mfc-shared/reference/crect-class.md)

### <a name="return-value"></a>Rückgabewert

A, `CSize` d. h. die `CPoint` Differenz zwischen zwei Punkten, einem, `CRect` der durch die Negation einer Größe `CPoint` ausgeglichen wird, eine, die durch die Negation eines Punktes ausgeglichen wird, oder eine, die die Negation eines Punktes ist.

### <a name="remarks"></a>Bemerkungen

Die dritte Überladung `CRect` kompensiert eine durch `CPoint`die Negation von . Verwenden Sie schließlich den unären `CPoint`Operator, um zu negieren.

Verwenden Sie z. B. die erste Überladung, um den Unterschied zwischen zwei Punkten `CPoint(25, -19)` und `CPoint(15, 5)` Zurückgegebenn `CSize(10, -24)`zu ermitteln.

Das `CSize` Subtrahieren eines von `CPoint` führt die `CPoint` gleiche Berechnung `CSize` wie oben durch, gibt jedoch ein Objekt zurück, nicht ein Objekt. Wenn Sie z. B. die zweite Überladung verwenden, um den Unterschied zwischen dem Punkt `CPoint(25, -19)` und der Größe `CSize(15, 5)` zu ermitteln, wird zurückgegeben. `CPoint(10, -24)`

Wenn Sie ein Rechteck von einem Punkt subtrahieren, wird das Rechteck durch die Negative der `x` und `y` der im Punkt angegebenen Werte versetzt. Wenn Sie z. B. die `CRect(125, 200, 325, 400)` letzte Überladung verwenden, um das Rechteck um den Punkt `CPoint(25, -19)` zu versetzen, wird zurückgegeben. `CRect(100, 219, 300, 419)`

Verwenden Sie den unären Operator, um einen Punkt zu negieren. Wenn Sie z. B. den `CPoint(25, -19)` `CPoint(-25, 19)`unären Operator mit dem Punkt-Rückgabeverwenden verwenden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel MDI](../../overview/visual-cpp-samples.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[POINT-Struktur](/windows/win32/api/windef/ns-windef-point)<br/>
[CRect-Klasse](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CSize-Klasse](../../atl-mfc-shared/reference/csize-class.md)

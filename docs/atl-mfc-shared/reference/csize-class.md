---
title: CSize-Klasse
ms.date: 10/18/2018
f1_keywords:
- CSize
- ATLTYPES/ATL::CSize
- ATLTYPES/ATL::CSize::CSize
helpviewer_keywords:
- SIZE
- dimensions, MFC
- dimensions
- CSize class
ms.assetid: fb2cf85a-0bc1-46f8-892b-309c108b52ae
ms.openlocfilehash: 6d1b82e3f60428e3a778709dc69de983a7f886bf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317676"
---
# <a name="csize-class"></a>CSize-Klasse

Ähnelt der Windows-Struktur [SIZE](/windows/win32/api/windef/ns-windef-size) , bei der eine relative Koordinate oder Position implementiert wird

## <a name="syntax"></a>Syntax

```
class CSize : public tagSIZE
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSize::CSize](#csize)|Erstellt ein `CSize`-Objekt.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSize::operator -](#operator_-)|Subtrahiert zwei Größen.|
|[CSize::operator !=](#operator_neq)|Überprüft die Ungleichheit `CSize` zwischen und einer Größe.|
|[CSize::operator +](#operator_add)|Fügt zwei Größen hinzu.|
|[CSize::operator +=](#operator_add_eq)|Fügt eine `CSize`Größe zu hinzu.|
|[CSize::operator -=](#operator_-_eq)|Subtrahiert eine `CSize`Größe von von .|
|[CSize::operator ==](#operator_eq_eq)|Überprüft die `CSize` Gleichheit zwischen und einer Größe.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse wird `SIZE` von der Struktur abgeleitet. Dies bedeutet, `CSize` dass Sie einen in `SIZE` einem Parameter übergeben `SIZE` können, der eine `CSize`fordert, und dass die Datenmember der Struktur auf Datenmember von zugreifen können.

Die `cx` `cy` und `SIZE` Mitglieder `CSize`von (und ) sind öffentlich. Darüber hinaus `CSize` implementiert Memberfunktionen, `SIZE` um die Struktur zu manipulieren.

> [!NOTE]
> Weitere Informationen zu freigegebenen `CSize`Dienstprogrammklassen (z. B. ) finden Sie unter [Freigegebene Klassen](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`tagSIZE`

`CSize`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atltypes.h

## <a name="csizecsize"></a><a name="csize"></a>CSize::CSize

Erstellt ein `CSize`-Objekt.

```
CSize() throw();
CSize( int initCX, int initCY) throw();
CSize( SIZE initSize) throw();
CSize( POINT initPt) throw();
CSize( DWORD dwSize) throw();
```

### <a name="parameters"></a>Parameter

*initCX*<br/>
Legt `cx` das Element `CSize`für die fest.

*initCY*<br/>
Legt `cy` das Element `CSize`für die fest.

*initSize*<br/>
[SIZE-Struktur](/windows/win32/api/windef/ns-windef-size) oder `CSize` -Objekt, das zum Initialisieren `CSize`von verwendet wird.

*initPt*<br/>
[POINT-Struktur](/windows/win32/api/windef/ns-windef-point) oder `CPoint` -Objekt, das zum Initialisieren `CSize`von verwendet wird.

*dwSize*<br/>
DWORD zum Initialisieren `CSize`von . Das Wort niedriger Ordnung `cx` ist das Element und `cy` das Wort hoher Ordnung ist das Element.

### <a name="remarks"></a>Bemerkungen

Wenn keine Argumente `cx` angegeben `cy` und auf Null initialisiert werden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

## <a name="csizeoperator-"></a><a name="operator_eq_eq"></a>CSize::operator ==

Überprüft die Gleichheit zwischen zwei Größen.

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt einen Wert ungleich Null zurück, wenn die Größen gleich sind, otherwize 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

## <a name="csizeoperator-"></a><a name="operator_neq"></a>CSize::operator !=

Überprüft die Ungleichheit zwischen zwei Größen.

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt einen Wert ungleich Null zurück, wenn die Größen nicht gleich sind, andernfalls 0.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

## <a name="csizeoperator-"></a><a name="operator_add_eq"></a>CSize::operator +=

Fügt dieser `CSize`eine Größe hinzu.

```
void operator+=(SIZE size) throw();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

## <a name="csizeoperator--"></a><a name="operator_-_eq"></a>CSize::operator -=

Subtrahiert eine `CSize`Größe von diesem .

```
void operator-=(SIZE size) throw();
```

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

## <a name="csizeoperator-"></a><a name="operator_add"></a>CSize::operator +

Diese Operatoren `CSize` fügen diesen Wert dem Wert des Parameters hinzu.

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>Bemerkungen

Siehe die folgenden Beschreibungen der einzelnen Operatoren:

- **Operator +(** *Größe* **)**

  Dieser Vorgang `CSize` fügt zwei Werte hinzu.

- **Operator +(** *Punkt* **)**

  Dieser Vorgang versetzt einen [POINT-Wert](/previous-versions/dd162805\(v=vs.85\)) (oder [CPoint)-Wert](../../atl-mfc-shared/reference/cpoint-class.md)um diesen `CSize` Wert. Die `cx` `cy` und Die `CSize` Member dieses `x` Werts werden den und `y` Datenelementen des `POINT` Werts hinzugefügt. Es ist analog zur Version von [CPoint::operator +,](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) die einen [SIZE-Parameter](/windows/win32/api/windef/ns-windef-size) annimmt.

- **Operator +(** *lpRect* **)**

   Dieser Vorgang versetzt einen [RECT-Wert](/previous-versions/dd162897\(v=vs.85\)) (oder [CRect)-Wert](../../atl-mfc-shared/reference/crect-class.md)um diesen `CSize` Wert. Die `cx` `cy` und Die `CSize` Member dieses `left`Werts werden `bottom` den , `RECT` `top`, `right`und den Datenmembern des Werts hinzugefügt. Es ist analog zur Version von [CRect::operator +,](../../atl-mfc-shared/reference/crect-class.md#operator_add) die einen [SIZE-Parameter](/windows/win32/api/windef/ns-windef-size) annimmt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

## <a name="csizeoperator--"></a><a name="operator_-"></a>CSize::operator -

Die ersten drei dieser Operatoren subtrahieren diesen `CSize` Wert in den Wert des Parameters.

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>Bemerkungen

Der vierte Operator, das unäre Minus, `CSize` ändert das Vorzeichen des Werts. Siehe die folgenden Beschreibungen der einzelnen Operatoren:

- **Operator -(** *Größe* **)**

  Bei diesem Vorgang `CSize` werden zwei Werte subtrahiert.

- **Operator -(** *Punkt* **)**

  Dieser Vorgang versetzt einen [POINT-](/previous-versions/dd162805\(v=vs.85\)) oder [CPoint-Wert](../../atl-mfc-shared/reference/cpoint-class.md) durch `CSize` die additive Umkehrung dieses Werts. Der `cx` `cy` und `CSize` dieser Wert werden von `x` `y` den und `POINT` Datenelementen des Werts subtrahiert. Es ist analog zur Version von [CPoint::operator -](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) das nimmt einen [SIZE-Parameter.](/windows/win32/api/windef/ns-windef-size)

- **Operator -(** *lpRect* **)**

  Dieser Vorgang versetzt einen [RECT-](/previous-versions/dd162897\(v=vs.85\)) oder [CRect-Wert](../../atl-mfc-shared/reference/crect-class.md) durch `CSize` die additive Umkehrung dieses Wertes. Die `cx` `cy` und die `CSize` Member dieses Werts `left` `top`werden `right`von `bottom` den , `RECT` , und den Datenmembern des Werts subtrahiert. Es ist analog zur Version von [CRect::operator -](../../atl-mfc-shared/reference/crect-class.md#operator_-) das nimmt einen [SIZE-Parameter.](/windows/win32/api/windef/ns-windef-size)

- **Operator -()**

  Dieser Vorgang gibt die additive `CSize` Umkehrung dieses Werts zurück.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>Siehe auch

[MFC-Beispiel MDI](../../overview/visual-cpp-samples.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CRect-Klasse](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint-Klasse](../../atl-mfc-shared/reference/cpoint-class.md)

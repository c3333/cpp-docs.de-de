---
title: CD2DGeometry-Klasse
ms.date: 11/04/2016
f1_keywords:
- CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::Attach
- AFXRENDERTARGET/CD2DGeometry::CombineWithGeometry
- AFXRENDERTARGET/CD2DGeometry::CompareWithGeometry
- AFXRENDERTARGET/CD2DGeometry::ComputeArea
- AFXRENDERTARGET/CD2DGeometry::ComputeLength
- AFXRENDERTARGET/CD2DGeometry::ComputePointAtLength
- AFXRENDERTARGET/CD2DGeometry::Destroy
- AFXRENDERTARGET/CD2DGeometry::Detach
- AFXRENDERTARGET/CD2DGeometry::FillContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Get
- AFXRENDERTARGET/CD2DGeometry::GetBounds
- AFXRENDERTARGET/CD2DGeometry::GetWidenedBounds
- AFXRENDERTARGET/CD2DGeometry::IsValid
- AFXRENDERTARGET/CD2DGeometry::Outline
- AFXRENDERTARGET/CD2DGeometry::Simplify
- AFXRENDERTARGET/CD2DGeometry::StrokeContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Tessellate
- AFXRENDERTARGET/CD2DGeometry::Widen
- AFXRENDERTARGET/CD2DGeometry::m_pGeometry
helpviewer_keywords:
- CD2DGeometry [MFC], CD2DGeometry
- CD2DGeometry [MFC], Attach
- CD2DGeometry [MFC], CombineWithGeometry
- CD2DGeometry [MFC], CompareWithGeometry
- CD2DGeometry [MFC], ComputeArea
- CD2DGeometry [MFC], ComputeLength
- CD2DGeometry [MFC], ComputePointAtLength
- CD2DGeometry [MFC], Destroy
- CD2DGeometry [MFC], Detach
- CD2DGeometry [MFC], FillContainsPoint
- CD2DGeometry [MFC], Get
- CD2DGeometry [MFC], GetBounds
- CD2DGeometry [MFC], GetWidenedBounds
- CD2DGeometry [MFC], IsValid
- CD2DGeometry [MFC], Outline
- CD2DGeometry [MFC], Simplify
- CD2DGeometry [MFC], StrokeContainsPoint
- CD2DGeometry [MFC], Tessellate
- CD2DGeometry [MFC], Widen
- CD2DGeometry [MFC], m_pGeometry
ms.assetid: 3f95054b-fdb8-4e87-87f2-9fc3df7279ec
ms.openlocfilehash: 4727f7b1799604001134ee2f4d2d2e1ce6db87fa
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754783"
---
# <a name="cd2dgeometry-class"></a>CD2DGeometry-Klasse

Ein Wrapper für ID2D1Geometry.

## <a name="syntax"></a>Syntax

```
class CD2DGeometry : public CD2DResource;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DGeometry::CD2DGeometry](#cd2dgeometry)|Erstellt ein CD2DGeometry-Objekt.|
|[CD2DGeometry::-CD2DGeometry](#_dtorcd2dgeometry)|Der Destruktor. Wird aufgerufen, wenn ein D2D-Geometrieobjekt zerstört wird.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DGeometry::Anfügen](#attach)|Fügt vorhandene Ressourcenschnittstelle an das Objekt an|
|[CD2DGeometry::CombineWithGeometry](#combinewithgeometry)|Kombiniert diese Geometrie mit der angegebenen Geometrie und speichert das Ergebnis in einem ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::CompareWithGeometry](#comparewithgeometry)|Beschreibt den Schnittpunkt zwischen dieser Geometrie und der angegebenen Geometrie. Der Vergleich wird mit der angegebenen Abflachungstoleranz durchgeführt.|
|[CD2DGeometry::ComputeArea](#computearea)|Berechnet die Fläche der Geometrie, nachdem sie von der angegebenen Matrix transformiert und mit der angegebenen Toleranz abgeflacht wurde.|
|[CD2DGeometry::ComputeLength](#computelength)|Berechnet die Länge der Geometrie so, als ob jedes Segment in einer Linie ausgerollt würde.|
|[CD2DGeometry::ComputePointAtLength](#computepointatlength)|Berechnet den Punkt- und Tangentenvektor in dem angegebenen Abstand entlang der Geometrie, nachdem er von der angegebenen Matrix transformiert und mit der angegebenen Toleranz abgeflacht wurde.|
|[CD2DGeometrie::Destroy](#destroy)|Zerstört ein CD2DGeometry-Objekt. (Überschreibt [CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy).)|
|[CD2DGeometrie::Detach](#detach)|Trennen der Ressourcenschnittstelle vom Objekt|
|[CD2DGeometry::FillContainsPoint](#fillcontainspoint)|Gibt an, ob der von der Geometrie gefüllte Bereich den angegebenen Punkt bei der angegebenen Abflachungstoleranz enthalten würde.|
|[CD2DGeometry::Get](#get)|Gibt ID2D1Geometry-Schnittstelle zurück|
|[CD2DGeometry::GetBounds](#getbounds)||
|[CD2DGeometry::GetWidenedBounds](#getwidenedbounds)|Ruft die Grenzen der Geometrie ab, nachdem sie um die angegebene Strichbreite und den angegebenen Stil erweitert und von der angegebenen Matrix transformiert wurde.|
|[CD2DGeometry::IsValid](#isvalid)|Überprüft die Ressourcengültigkeit (Überschreibt [CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid).)|
|[CD2DGeometry::Umriss](#outline)|Berechnet die Umrisse der Geometrie und schreibt das Ergebnis in eine ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::Vereinfachen](#simplify)|Erstellt eine vereinfachte Version der Geometrie, die nur Linien und (optional) kubische Bézierkurven enthält, und schreibt das Ergebnis in eine ID2D1SimplifiedGeometrySink.|
|[CD2DGeometry::StrokeContainsPoint](#strokecontainspoint)|Bestimmt, ob der Strich der Geometrie den angegebenen Punkt enthält, der die angegebene Strichstärke, den Stil und die Transformation enthält.|
|[CD2DGeometrie::Tessellate](#tessellate)|Erstellt einen Satz von Dreiecken in Uhrzeigerrichtung, die die Geometrie abdecken, nachdem sie mit der angegebenen Matrix transformiert und mit der angebenen Toleranz vereinfacht wurde.|
|[CD2DGeometry::Erweitern](#widen)|Erweitert die Geometrie um den angegebenen Strich und schreibt das Ergebnis in eine ID2D1SimplifiedGeometrySink, nachdem sie von der angegebenen Matrix transformiert und mit der angegebenen Toleranz abgeflacht wurde.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DGeometry::operator ID2D1Geometry*](#operator_id2d1geometry_star)|Gibt ID2D1Geometry-Schnittstelle zurück|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DGeometry::m_pGeometry](#m_pgeometry)|Ein Zeiger auf eine ID2D1Geometry.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DGeometry`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dgeometrycd2dgeometry"></a><a name="_dtorcd2dgeometry"></a>CD2DGeometry::-CD2DGeometry

Der Destruktor. Wird aufgerufen, wenn ein D2D-Geometrieobjekt zerstört wird.

```
virtual ~CD2DGeometry();
```

## <a name="cd2dgeometryattach"></a><a name="attach"></a>CD2DGeometry::Anfügen

Fügt vorhandene Ressourcenschnittstelle an das Objekt an

```cpp
void Attach(ID2D1Geometry* pResource);
```

### <a name="parameters"></a>Parameter

*pResource*<br/>
Vorhandene Ressourcenschnittstelle. Kann nicht NULL sein

## <a name="cd2dgeometrycd2dgeometry"></a><a name="cd2dgeometry"></a>CD2DGeometry::CD2DGeometry

Erstellt ein CD2DGeometry-Objekt.

```
CD2DGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parameter

*pParentTarget*<br/>
Ein Zeiger auf das Renderziel.

*bAutoDestroy*<br/>
Gibt an, dass das Objekt vom Besitzer (pParentTarget) zerstört wird.

## <a name="cd2dgeometrycombinewithgeometry"></a><a name="combinewithgeometry"></a>CD2DGeometry::CombineWithGeometry

Kombiniert diese Geometrie mit der angegebenen Geometrie und speichert das Ergebnis in einem ID2D1SimplifiedGeometrySink.

```
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,
    D2D1_COMBINE_MODE combineMode,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parameter

*inputGeometrie*<br/>
Die Geometrie, die mit dieser Instanz kombiniert werden soll.

*Combinemode*<br/>
Der Typ des auszuführenden Kombinationsvorgangs.

*inputGeometryTransform*<br/>
Die Transformation, die vor der Kombination auf inputGeometry angewendet werden soll.

*geometrySink*<br/>
Das Ergebnis des Kombinationsvorgangs.

*AbflachenToleranz*<br/>
Die maximalen Grenzen für die Entfernung zwischen Punkten in der polygonalen Approximation der Geometrien. Kleinere Werte liefern genauere Ergebnisse, führen jedoch zu einer langsameren Ausführung.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="cd2dgeometrycomparewithgeometry"></a><a name="comparewithgeometry"></a>CD2DGeometry::CompareWithGeometry

Beschreibt den Schnittpunkt zwischen dieser Geometrie und der angegebenen Geometrie. Der Vergleich wird mit der angegebenen Abflachungstoleranz durchgeführt.

```
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parameter

*inputGeometrie*<br/>
Die zu testende Geometrie.

*inputGeometryTransform*<br/>
Die Transformation, die auf inputGeometry angewendet werden soll.

*AbflachenToleranz*<br/>
Die maximalen Grenzen für die Entfernung zwischen Punkten in der polygonalen Approximation der Geometrien. Kleinere Werte liefern genauere Ergebnisse, führen jedoch zu einer langsameren Ausführung.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="cd2dgeometrycomputearea"></a><a name="computearea"></a>CD2DGeometry::ComputeArea

Berechnet die Fläche der Geometrie, nachdem sie von der angegebenen Matrix transformiert und mit der angegebenen Toleranz abgeflacht wurde.

```
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& area,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parameter

*worldTransform*<br/>
Die Transformation, die auf diese Geometrie angewendet werden soll, bevor ihr Bereich berechnet wird.

*Bereich*<br/>
Wenn diese Methode zurückgegeben wird, enthält ein Zeiger auf den Bereich der transformierten, abgeflachten Version dieser Geometrie. Sie müssen Speicher für diesen Parameter zuweisen.

*AbflachenToleranz*<br/>
Die maximalen Grenzen für die Entfernung zwischen Punkten in der polygonalen Approximation der Geometrie. Kleinere Werte liefern genauere Ergebnisse, führen jedoch zu einer langsameren Ausführung.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="cd2dgeometrycomputelength"></a><a name="computelength"></a>CD2DGeometry::ComputeLength

Berechnet die Länge der Geometrie so, als ob jedes Segment in einer Linie ausgerollt würde.

```
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& length,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parameter

*worldTransform*<br/>
Die Transformation, die auf die Geometrie angewendet werden soll, bevor die Länge berechnet wird.

*length*<br/>
Wenn diese Methode zurückgegeben wird, enthält ein Zeiger auf die Länge der Geometrie. Bei geschlossenen Geometrien enthält die Länge ein implizites Schließensegment. Sie müssen Speicher für diesen Parameter zuweisen.

*AbflachenToleranz*<br/>
Die maximalen Grenzen für die Entfernung zwischen Punkten in der polygonalen Approximation der Geometrie. Kleinere Werte liefern genauere Ergebnisse, führen jedoch zu einer langsameren Ausführung.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="cd2dgeometrycomputepointatlength"></a><a name="computepointatlength"></a>CD2DGeometry::ComputePointAtLength

Berechnet den Punkt- und Tangentenvektor in dem angegebenen Abstand entlang der Geometrie, nachdem er von der angegebenen Matrix transformiert und mit der angegebenen Toleranz abgeflacht wurde.

```
BOOL ComputePointAtLength(
    FLOAT length,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DPointF& point,
    CD2DPointF& unitTangentVector,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parameter

*length*<br/>
Der Abstand entlang der Geometrie des zu findenden Punkts und der Tangente. Wenn dieser Abstand kleiner als 0 ist, berechnet diese Methode den ersten Punkt in der Geometrie. Wenn dieser Abstand größer als die Länge der Geometrie ist, berechnet diese Methode den letzten Punkt in der Geometrie.

*worldTransform*<br/>
Die Transformation, die auf die Geometrie angewendet werden soll, bevor der angegebene Punkt und die Tangente berechnet werden.

*Punkt*<br/>
Die Position in der angegebenen Entfernung entlang der Geometrie. Wenn die Geometrie leer ist, enthält dieser Punkt NaN als x- und y-Werte.

*einheitTangentVector*<br/>
Wenn diese Methode zurückkehrt, enthält einen Zeiger auf den Tangentenvektor in der angegebenen Entfernung entlang der Geometrie. Wenn die Geometrie leer ist, enthält dieser Vektor NaN als x- und y-Werte. Sie müssen Speicher für diesen Parameter zuweisen.

*AbflachenToleranz*<br/>
Die maximalen Grenzen für die Entfernung zwischen Punkten in der polygonalen Approximation der Geometrie. Kleinere Werte liefern genauere Ergebnisse, führen jedoch zu einer langsameren Ausführung.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="cd2dgeometrydestroy"></a><a name="destroy"></a>CD2DGeometrie::Destroy

Zerstört ein CD2DGeometry-Objekt.

```
virtual void Destroy();
```

## <a name="cd2dgeometrydetach"></a><a name="detach"></a>CD2DGeometrie::Detach

Trennen der Ressourcenschnittstelle vom Objekt

```
ID2D1Geometry* Detach();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine getrennte Ressourcenschnittstelle.

## <a name="cd2dgeometryfillcontainspoint"></a><a name="fillcontainspoint"></a>CD2DGeometry::FillContainsPoint

Gibt an, ob der von der Geometrie gefüllte Bereich den angegebenen Punkt bei der angegebenen Abflachungstoleranz enthalten würde.

```
BOOL FillContainsPoint(
    CD2DPointF point,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Der zu testende Punkt.

*worldTransform*<br/>
Die Transformation, die vor dem Testen auf Containment auf die Geometrie angewendet werden soll.

*contains*<br/>
Wenn diese Methode zurückgegeben wird, enthält einen bool-Wert, der TRUE ist, wenn der von der Geometrie gefüllte Bereich Punkt enthält. andernfalls FALSE. Sie müssen Speicher für diesen Parameter zuweisen.

*AbflachenToleranz*<br/>
Die numerische Genauigkeit, mit der der genaue geometrische Pfad- und Pfadschnitt punktgenau berechnet wird. Punkte, die die Füllung um weniger als die Toleranz fehlen, werden weiterhin im Inneren berücksichtigt. Kleinere Werte liefern genauere Ergebnisse, führen jedoch zu einer langsameren Ausführung.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="cd2dgeometryget"></a><a name="get"></a>CD2DGeometry::Get

Gibt ID2D1Geometry-Schnittstelle zurück

```
ID2D1Geometry* Get();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1Geometry-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dgeometrygetbounds"></a><a name="getbounds"></a>CD2DGeometry::GetBounds

```
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,
CD2DRectF& bounds) const;
```

### <a name="parameters"></a>Parameter

*worldTransform*<br/>
*Grenzen*

### <a name="return-value"></a>Rückgabewert

## <a name="cd2dgeometrygetwidenedbounds"></a><a name="getwidenedbounds"></a>CD2DGeometry::GetWidenedBounds

Ruft die Grenzen der Geometrie ab, nachdem sie um die angegebene Strichbreite und den angegebenen Stil erweitert und von der angegebenen Matrix transformiert wurde.

```
BOOL GetWidenedBounds(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DRectF& bounds,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parameter

*strokeWidth*<br/>
Der Betrag, um den die Geometrie durch Streichen der Kontur erweitert werden soll.

*strokeStyle*<br/>
Der Stil des Strichs, der die Geometrie erweitert.

*worldTransform*<br/>
Eine Transformation, die auf die Geometrie angewendet werden soll, nachdem die Geometrie transformiert und die Geometrie gestrichelt wurde.

*Grenzen*<br/>
Wenn diese Methode zurückgegeben wird, enthält die Grenzen der erweiterten Geometrie. Sie müssen Speicher für diesen Parameter zuweisen.

*AbflachenToleranz*<br/>
Die maximalen Grenzen für die Entfernung zwischen Punkten in der polygonalen Approximation der Geometrien. Kleinere Werte liefern genauere Ergebnisse, führen jedoch zu einer langsameren Ausführung.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="cd2dgeometryisvalid"></a><a name="isvalid"></a>CD2DGeometry::IsValid

Überprüft die Gültigkeit der Ressource

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Ressource gültig ist; andernfalls FALSE.

## <a name="cd2dgeometrym_pgeometry"></a><a name="m_pgeometry"></a>CD2DGeometry::m_pGeometry

Ein Zeiger auf eine ID2D1Geometry.

```
ID2D1Geometry* m_pGeometry;
```

## <a name="cd2dgeometryoperator-id2d1geometry"></a><a name="operator_id2d1geometry_star"></a>CD2DGeometry::operator ID2D1Geometry*

Gibt ID2D1Geometry-Schnittstelle zurück

```
operator ID2D1Geometry*();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1Geometry-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dgeometryoutline"></a><a name="outline"></a>CD2DGeometry::Umriss

Berechnet die Umrisse der Geometrie und schreibt das Ergebnis in eine ID2D1SimplifiedGeometrySink.

```
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parameter

*worldTransform*<br/>
Die Transformation, die auf die Geometrieumrisslinie angewendet werden soll.

*geometrySink*<br/>
Die ID2D1SimplifiedGeometrySink, an die die Geometrie transformierte Umrisslinie angehängt wird.

*AbflachenToleranz*<br/>
Die maximalen Grenzen für die Entfernung zwischen Punkten in der polygonalen Approximation der Geometrie. Kleinere Werte liefern genauere Ergebnisse, führen jedoch zu einer langsameren Ausführung.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="cd2dgeometrysimplify"></a><a name="simplify"></a>CD2DGeometry::Vereinfachen

Erstellt eine vereinfachte Version der Geometrie, die nur Linien und (optional) kubische Bézierkurven enthält, und schreibt das Ergebnis in eine ID2D1SimplifiedGeometrySink.

```
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parameter

*VereinfachungOption*<br/>
Ein Wert, der angibt, ob die vereinfachte Geometrie Kurven enthalten soll.

*worldTransform*<br/>
Die Transformation, die auf die vereinfachte Geometrie angewendet werden soll.

*geometrySink*<br/>
Die ID2D1SimplifiedGeometrySink, an die die vereinfachte Geometrie angehängt wird.

*AbflachenToleranz*<br/>
Die maximalen Grenzen für die Entfernung zwischen Punkten in der polygonalen Approximation der Geometrie. Kleinere Werte liefern genauere Ergebnisse, führen jedoch zu einer langsameren Ausführung.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="cd2dgeometrystrokecontainspoint"></a><a name="strokecontainspoint"></a>CD2DGeometry::StrokeContainsPoint

Bestimmt, ob der Strich der Geometrie den angegebenen Punkt enthält, der die angegebene Strichstärke, den Stil und die Transformation enthält.

```
BOOL StrokeContainsPoint(
    CD2DPointF point,
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Der auf seine Position zu überprüfende Punkt.

*strokeWidth*<br/>
Die Dicke des anzuwendenden Strichs.

*strokeStyle*<br/>
Der Stil des anzuwendenden Strichs.

*worldTransform*<br/>
Die Transformation, die auf die gestrichelte Geometrie angewendet werden soll.

*contains*<br/>
Wenn diese Methode zurückgegeben wird, enthält einen booleschen Wert, der auf TRUE festgelegt ist, wenn der Strich der Geometrie den angegebenen Punkt enthält. andernfalls FALSE. Sie müssen Speicher für diesen Parameter zuweisen.

*AbflachenToleranz*<br/>
Die numerische Genauigkeit, mit der der genaue geometrische Pfad- und Pfadschnitt punktgenau berechnet wird. Punkte, die den Strich um weniger als die Toleranz verfehlen, werden weiterhin im Inneren berücksichtigt. Kleinere Werte liefern genauere Ergebnisse, führen jedoch zu einer langsameren Ausführung.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="cd2dgeometrytessellate"></a><a name="tessellate"></a>CD2DGeometrie::Tessellate

Erstellt einen Satz von Dreiecken in Uhrzeigerrichtung, die die Geometrie abdecken, nachdem sie mit der angegebenen Matrix transformiert und mit der angebenen Toleranz vereinfacht wurde.

```
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1TessellationSink* tessellationSink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parameter

*worldTransform*<br/>
Die Transformation, die auf diese Geometrie angewendet werden soll, oder NULL.

*tessellationSink*<br/>
Die ID2D1TessellationSink, an die der tessellierte angehängt ist.

*AbflachenToleranz*<br/>
Die maximalen Grenzen für die Entfernung zwischen Punkten in der polygonalen Approximation der Geometrie. Kleinere Werte liefern genauere Ergebnisse, führen jedoch zu einer langsameren Ausführung.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="cd2dgeometrywiden"></a><a name="widen"></a>CD2DGeometry::Erweitern

Erweitert die Geometrie um den angegebenen Strich und schreibt das Ergebnis in eine ID2D1SimplifiedGeometrySink, nachdem sie von der angegebenen Matrix transformiert und mit der angegebenen Toleranz abgeflacht wurde.

```
BOOL Widen(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>Parameter

*strokeWidth*<br/>
Der Betrag, um den die Geometrie erweitert werden soll.

*strokeStyle*<br/>
Der Stil des Strichs, der auf die Geometrie angewendet werden soll, oder NULL.

*worldTransform*<br/>
Die Transformation, die nach dem Erweitern auf die Geometrie angewendet werden soll.

*geometrySink*<br/>
Die ID2D1SimplifiedGeometrySink, an die die erweiterte Geometrie angehängt wird.

*AbflachenToleranz*<br/>
Die maximalen Grenzen für die Entfernung zwischen Punkten in der polygonalen Approximation der Geometrie. Kleinere Werte liefern genauere Ergebnisse, führen jedoch zu einer langsameren Ausführung.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird TRUE zurückgegeben. Andernfalls wird FALSE zurückgegeben.

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)

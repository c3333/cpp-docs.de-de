---
title: CD2DGeometrySink-Klasse
ms.date: 11/04/2016
f1_keywords:
- CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::AddArc
- AFXRENDERTARGET/CD2DGeometrySink::AddBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddBeziers
- AFXRENDERTARGET/CD2DGeometrySink::AddLine
- AFXRENDERTARGET/CD2DGeometrySink::AddLines
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBeziers
- AFXRENDERTARGET/CD2DGeometrySink::BeginFigure
- AFXRENDERTARGET/CD2DGeometrySink::Close
- AFXRENDERTARGET/CD2DGeometrySink::EndFigure
- AFXRENDERTARGET/CD2DGeometrySink::Get
- AFXRENDERTARGET/CD2DGeometrySink::IsValid
- AFXRENDERTARGET/CD2DGeometrySink::SetFillMode
- AFXRENDERTARGET/CD2DGeometrySink::SetSegmentFlags
- AFXRENDERTARGET/CD2DGeometrySink::m_pSink
helpviewer_keywords:
- CD2DGeometrySink [MFC], CD2DGeometrySink
- CD2DGeometrySink [MFC], AddArc
- CD2DGeometrySink [MFC], AddBezier
- CD2DGeometrySink [MFC], AddBeziers
- CD2DGeometrySink [MFC], AddLine
- CD2DGeometrySink [MFC], AddLines
- CD2DGeometrySink [MFC], AddQuadraticBezier
- CD2DGeometrySink [MFC], AddQuadraticBeziers
- CD2DGeometrySink [MFC], BeginFigure
- CD2DGeometrySink [MFC], Close
- CD2DGeometrySink [MFC], EndFigure
- CD2DGeometrySink [MFC], Get
- CD2DGeometrySink [MFC], IsValid
- CD2DGeometrySink [MFC], SetFillMode
- CD2DGeometrySink [MFC], SetSegmentFlags
- CD2DGeometrySink [MFC], m_pSink
ms.assetid: e5e07f41-0343-4ab1-9d6b-8c62ed33c04a
ms.openlocfilehash: cb51c7b11f75debece61105bf20a201b6eab80a9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369237"
---
# <a name="cd2dgeometrysink-class"></a>CD2DGeometrySink-Klasse

Ein Wrapper für ID2D1GeometrySink.

## <a name="syntax"></a>Syntax

```
class CD2DGeometrySink;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|Erstellt ein CD2DGeometrySink-Objekt aus dem CD2DPathGeometry-Objekt.|
|[CD2DGeometrySink::'CD2DGeometrySink'S](#_dtorcd2dgeometrysink)|Der Destruktor. Wird aufgerufen, wenn ein D2D-Geometriesenkenobjekt zerstört wird.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DGeometrySink::AddArc](#addarc)|Fügt der Pfadgeometrie einen einzelnen Bogen hinzu|
|[CD2DGeometrySink::AddBezier](#addbezier)|Erstellt eine kubische Bézierkurve zwischen dem aktuellen Punkt und dem angegebenen Endpunkt.|
|[CD2DGeometrySink::AddBeziers](#addbeziers)|Erstellt eine Sequenz von kubischen Bézierkurven und fügt sie der Geometriesenke hinzu.|
|[CD2DGeometrySink::AddLine](#addline)|Erstellt ein Liniensegment zwischen dem aktuellen Punkt und dem angegebenen Endpunkt und fügt es der Geometriesenke hinzu.|
|[CD2DGeometrySink::AddLines](#addlines)|Erstellt eine Sequenz von Linien mit den angegebenen Punkten und fügt sie der Geometriesenke hinzu.|
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|Erstellt eine quadratische Bézierkurve zwischen dem aktuellen Punkt und dem angegebenen Endpunkt.|
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|Fügt eine Sequenz quadratischer Béziersegmente als Array in einem einzelnen Aufruf hinzu.|
|[CD2DGeometrySink::BeginFigure](#beginfigure)|Startet eine neue Figur am angegebenen Punkt.|
|[CD2DGeometrySink::Schließen](#close)|Schließt die Geometriesenke|
|[CD2DGeometrySink::EndAbbildung](#endfigure)|Beendet die aktuelle Zahl; optional schließt es.|
|[CD2DGeometrySink::Get](#get)|Gibt ID2D1GeometrySink-Schnittstelle zurück|
|[CD2DGeometrySink::IsValid](#isvalid)|Überprüft die Gültigkeit der Geometriesenke|
|[CD2DGeometrySink::SetFillMode](#setfillmode)|Gibt die Methode an, die verwendet wird, um zu bestimmen, welche Punkte sich innerhalb der geometrie, die von dieser Geometriesenke beschrieben wird, und welche Punkte sich außerhalb befinden.|
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|Gibt Strich- und Verknüpfungsoptionen an, die auf neue Segmente angewendet werden sollen, die der Geometriesenke hinzugefügt werden.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DGeometrySink::operator ID2D1GeometrySink*](#operator_id2d1geometrysink_star)|Gibt ID2D1GeometrySink-Schnittstelle zurück|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CD2DGeometrySink::m_pSink](#m_psink)|Ein Zeiger auf eine ID2D1GeometrySink.|

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CD2DGeometrySink`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** afxrendertarget.h

## <a name="cd2dgeometrysinkcd2dgeometrysink"></a><a name="_dtorcd2dgeometrysink"></a>CD2DGeometrySink::'CD2DGeometrySink'S

Der Destruktor. Wird aufgerufen, wenn ein D2D-Geometriesenkenobjekt zerstört wird.

```
virtual ~CD2DGeometrySink();
```

## <a name="cd2dgeometrysinkaddarc"></a><a name="addarc"></a>CD2DGeometrySink::AddArc

Fügt der Pfadgeometrie einen einzelnen Bogen hinzu

```
void AddArc(const D2D1_ARC_SEGMENT& arc);
```

### <a name="parameters"></a>Parameter

*Arc*<br/>
Das Bogensegment, das der Figur hinzugefügt werden soll

## <a name="cd2dgeometrysinkaddbezier"></a><a name="addbezier"></a>CD2DGeometrySink::AddBezier

Erstellt eine kubische Bézierkurve zwischen dem aktuellen Punkt und dem angegebenen Endpunkt.

```
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Parameter

*Bezier*<br/>
Eine Struktur, die die Kontrollpunkte und den Endpunkt der hinzuzufügenden Bézierkurve beschreibt.

## <a name="cd2dgeometrysinkaddbeziers"></a><a name="addbeziers"></a>CD2DGeometrySink::AddBeziers

Erstellt eine Sequenz von kubischen Bézierkurven und fügt sie der Geometriesenke hinzu.

```
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,
    D2D1_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Parameter

*Beziers*<br/>
Ein Array von Bézier-Segmenten, das die zu erstellenden Bézierkurven beschreibt. Eine Kurve wird vom aktuellen Punkt der Geometriesenke (dem Endpunkt des zuletzt gezeichneten Segments oder der von BeginFigure angegebenen Position) bis zum Endpunkt des ersten Bézier-Segments im Array gezeichnet. Wenn das Array zusätzliche Bézier-Segmente enthält, verwendet jedes nachfolgende Bézier-Segment den Endpunkt des vorherigen Bézier-Segments als Startpunkt.

## <a name="cd2dgeometrysinkaddline"></a><a name="addline"></a>CD2DGeometrySink::AddLine

Erstellt ein Liniensegment zwischen dem aktuellen Punkt und dem angegebenen Endpunkt und fügt es der Geometriesenke hinzu.

```
void AddLine(CD2DPointF point);
```

### <a name="parameters"></a>Parameter

*Punkt*<br/>
Der Endpunkt der zu zeichnenden Linie.

## <a name="cd2dgeometrysinkaddlines"></a><a name="addlines"></a>CD2DGeometrySink::AddLines

Erstellt eine Sequenz von Linien mit den angegebenen Punkten und fügt sie der Geometriesenke hinzu.

```
void AddLines(
    const CArray<CD2DPointF,
    CD2DPointF>& points);
```

### <a name="parameters"></a>Parameter

*Punkte*<br/>
Ein Array von einem oder mehreren Punkten, die die zu zeichnenden Linien beschreiben. Eine Linie wird vom aktuellen Punkt der Geometriesenke (dem Endpunkt des zuletzt gezeichneten Segments oder der von BeginFigure angegebenen Position) bis zum ersten Punkt im Array gezeichnet. Wenn das Array zusätzliche Punkte enthält, wird eine Linie vom ersten Punkt zum zweiten Punkt im Array, vom zweiten Punkt zum dritten Punkt usw. gezogen. Ein Array einer Sequenz der Endpunkte der zu zeichnenden Linien.

## <a name="cd2dgeometrysinkaddquadraticbezier"></a><a name="addquadraticbezier"></a>CD2DGeometrySink::AddQuadraticBezier

Erstellt eine quadratische Bézierkurve zwischen dem aktuellen Punkt und dem angegebenen Endpunkt.

```
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>Parameter

*Bezier*<br/>
Eine Struktur, die den Kontrollpunkt und den Endpunkt der hinzuzufügenden quadratischen Bézierkurve beschreibt.

## <a name="cd2dgeometrysinkaddquadraticbeziers"></a><a name="addquadraticbeziers"></a>CD2DGeometrySink::AddQuadraticBeziers

Fügt eine Sequenz quadratischer Béziersegmente als Array in einem einzelnen Aufruf hinzu.

```
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>Parameter

*Beziers*<br/>
Ein Array einer Sequenz quadratischer Béziersegmente.

## <a name="cd2dgeometrysinkbeginfigure"></a><a name="beginfigure"></a>CD2DGeometrySink::BeginFigure

Startet eine neue Figur am angegebenen Punkt.

```
void BeginFigure(
    CD2DPointF startPoint,
    D2D1_FIGURE_BEGIN figureBegin);
```

### <a name="parameters"></a>Parameter

*startPoint*<br/>
Der Punkt, an dem die neue Figur beginnen soll.

*figureBegin*<br/>
Ob die neue Figur hohl oder gefüllt sein soll.

## <a name="cd2dgeometrysinkcd2dgeometrysink"></a><a name="cd2dgeometrysink"></a>CD2DGeometrySink::CD2DGeometrySink

Erstellt ein CD2DGeometrySink-Objekt aus dem CD2DPathGeometry-Objekt.

```
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```

### <a name="parameters"></a>Parameter

*Pathgeometry*<br/>
Ein vorhandenes CD2DPathGeometry-Objekt.

## <a name="cd2dgeometrysinkclose"></a><a name="close"></a>CD2DGeometrySink::Schließen

Schließt die Geometriesenke

```
BOOL Close();
```

### <a name="return-value"></a>Rückgabewert

Ungleich Null, wenn erfolgreich; andernfalls FALSE.

## <a name="cd2dgeometrysinkendfigure"></a><a name="endfigure"></a>CD2DGeometrySink::EndAbbildung

Beendet die aktuelle Zahl; optional schließt es.

```
void EndFigure(D2D1_FIGURE_END figureEnd);
```

### <a name="parameters"></a>Parameter

*figureEnd*<br/>
Ein Wert, der angibt, ob die aktuelle Zahl geschlossen ist. Wenn die Figur geschlossen ist, wird eine Linie zwischen dem aktuellen Punkt und dem von BeginFigure angegebenen Startpunkt gezeichnet.

## <a name="cd2dgeometrysinkget"></a><a name="get"></a>CD2DGeometrySink::Get

Gibt ID2D1GeometrySink-Schnittstelle zurück

```
ID2D1GeometrySink* Get();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1GeometrySink-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dgeometrysinkisvalid"></a><a name="isvalid"></a>CD2DGeometrySink::IsValid

Überprüft die Gültigkeit der Geometriesenke

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn Geometriesenke gültig ist; andernfalls FALSE.

## <a name="cd2dgeometrysinkm_psink"></a><a name="m_psink"></a>CD2DGeometrySink::m_pSink

Ein Zeiger auf eine ID2D1GeometrySink.

```
ID2D1GeometrySink* m_pSink;
```

## <a name="cd2dgeometrysinkoperator-id2d1geometrysink"></a><a name="operator_id2d1geometrysink_star"></a>CD2DGeometrySink::operator ID2D1GeometrySink*

Gibt ID2D1GeometrySink-Schnittstelle zurück

```
operator ID2D1GeometrySink*();
```

### <a name="return-value"></a>Rückgabewert

Zeiger auf eine ID2D1GeometrySink-Schnittstelle oder NULL, wenn das Objekt noch nicht initialisiert wurde.

## <a name="cd2dgeometrysinksetfillmode"></a><a name="setfillmode"></a>CD2DGeometrySink::SetFillMode

Gibt die Methode an, die verwendet wird, um zu bestimmen, welche Punkte sich innerhalb der geometrie, die von dieser Geometriesenke beschrieben wird, und welche Punkte sich außerhalb befinden.

```
void SetFillMode(D2D1_FILL_MODE fillMode);
```

### <a name="parameters"></a>Parameter

*Fillmode*<br/>
Die Methode, mit der bestimmt wird, ob ein bestimmter Punkt Teil der Geometrie ist.

## <a name="cd2dgeometrysinksetsegmentflags"></a><a name="setsegmentflags"></a>CD2DGeometrySink::SetSegmentFlags

Gibt Strich- und Verknüpfungsoptionen an, die auf neue Segmente angewendet werden sollen, die der Geometriesenke hinzugefügt werden.

```
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```

### <a name="parameters"></a>Parameter

*vertexFlags*<br/>
Strich- und Verknüpfungsoptionen, die auf neue Segmente angewendet werden sollen, die der Geometriesenke hinzugefügt werden.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)

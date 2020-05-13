---
title: CAnimationPoint-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetX
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetY
- AFXANIMATIONCONTROLLER/CAnimationPoint::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_xValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_yValue
helpviewer_keywords:
- CAnimationPoint [MFC], CAnimationPoint
- CAnimationPoint [MFC], AddTransition
- CAnimationPoint [MFC], GetDefaultValue
- CAnimationPoint [MFC], GetValue
- CAnimationPoint [MFC], GetX
- CAnimationPoint [MFC], GetY
- CAnimationPoint [MFC], SetDefaultValue
- CAnimationPoint [MFC], GetAnimationVariableList
- CAnimationPoint [MFC], m_xValue
- CAnimationPoint [MFC], m_yValue
ms.assetid: 5dc4d46f-e695-4681-b15c-544b78b3e317
ms.openlocfilehash: fcdd07efb46c97d27a9f1349c297688b5705f176
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755144"
---
# <a name="canimationpoint-class"></a>CAnimationPoint-Klasse

Implementiert die Funktion eines Punkts, dessen Koordinaten animiert werden können.

## <a name="syntax"></a>Syntax

```
class CAnimationPoint : public CAnimationBaseObject;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationPoint::CAnimationPoint](#canimationpoint)|Ist überladen. Erstellt das CAnimationPoint-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationPoint::AddTransition](#addtransition)|Fügt Übergänge für X- und Y-Koordinaten hinzu.|
|[CAnimationPoint::GetDefaultValue](#getdefaultvalue)|Gibt die Standardwerte für X- und Y-Koordinaten zurück.|
|[CAnimationPoint::GetValue](#getvalue)|Gibt den aktuellen Wert zurück.|
|[CAnimationPoint::GetX](#getx)|Bietet Zugriff auf CAnimationVariable für X-Koordinate.|
|[CAnimationPoint::GetY](#gety)|Bietet Zugriff auf CAnimationVariable für Y-Koordinate.|
|[CAnimationPoint::SetDefaultValue](#setdefaultvalue)|Legt den Standardwert fest.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationPoint::GetAnimationVariableList](#getanimationvariablelist)|Fügt die gekapselten Animationsvariablen in eine Liste ein. (Überschreibt [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationPoint::operator CPoint](#operator_cpoint)|Konvertiert einen CAnimationPoint in einen CPoint.|
|[CAnimationPoint::operator=](#operator_eq)|Weist cAnimationPoint ptSrc zu.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationPoint::m_xValue](#m_xvalue)|Die gekapselte Animationsvariable, die die X-Koordinate des Animationspunkts darstellt.|
|[CAnimationPoint::m_yValue](#m_yvalue)|Die gekapselte Animationsvariable, die die Y-Koordinate des Animationspunkts darstellt.|

## <a name="remarks"></a>Bemerkungen

Die CAnimationPoint-Klasse kapselt zwei CAnimationVariable-Objekte und kann in Anwendungen einen Punkt darstellen. Sie können diese Klasse beispielsweise verwenden, um eine Position eines beliebigen Objekts auf dem Bildschirm zu animieren (z. B. Textzeichenfolge, Kreis, Punkt usw.). Um diese Klasse in der Anwendung zu verwenden, instanziieren Sie einfach ein Objekt dieser Klasse, fügen Sie es dem Animationscontroller mit CAnimationController::AddAnimationObject hinzu, und rufen Sie AddTransition für jeden Übergang auf, der auf X- und/oder Y-Koordinaten angewendet werden soll.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationPoint`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxanimationcontroller.h

## <a name="canimationpointaddtransition"></a><a name="addtransition"></a>CAnimationPoint::AddTransition

Fügt Übergänge für X- und Y-Koordinaten hinzu.

```cpp
void AddTransition(
    CBaseTransition* pXTransition,
    CBaseTransition* pYTransition);
```

### <a name="parameters"></a>Parameter

*pXTransition*<br/>
Ein Zeiger auf den Übergang für X-Koordinaten.

*pYTransition*<br/>
Ein Zeiger auf den Übergang für Y-Koordinate.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um die angegebenen Übergänge zur internen Liste der Übergänge hinzuzufügen, die auf Animationsvariablen für X- und Y-Koordinaten angewendet werden sollen. Wenn Sie Übergänge hinzufügen, werden sie nicht sofort angewendet und in einer internen Liste gespeichert. Übergänge werden angewendet (zu einem Storyboard für einen bestimmten Wert hinzugefügt), wenn Sie CAnimationController::AnimateGroup aufrufen. Wenn Sie keinen Übergang zu einer der Koordinaten anwenden müssen, können Sie NULL übergeben.

## <a name="canimationpointcanimationpoint"></a><a name="canimationpoint"></a>CAnimationPoint::CAnimationPoint

Erstellt das CAnimationPoint-Objekt.

```
CAnimationPoint();

CAnimationPoint(
    const CPoint& ptDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parameter

*ptDefault*<br/>
Gibt Standardpunktkoordinaten an.

*nGroupID*<br/>
Gibt die Gruppen-ID an.

*nObjectID*<br/>
Gibt die Objekt-ID an.

*dwUserData*<br/>
Gibt benutzerdefinierte Daten an.

### <a name="remarks"></a>Bemerkungen

Erstellt CAnimationPoint-Objekte mit Standardeigenschaften: Standardpunktkoordinaten, Gruppen-ID und Objekt-ID werden auf 0 gesetzt.

## <a name="canimationpointgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationPoint::GetAnimationVariableList

Fügt die gekapselten Animationsvariablen in eine Liste ein.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parameter

*Lst*<br/>
Wenn die Funktion zurückkehrt, enthält sie Zeiger auf zwei CAnimationVariable-Objekte, die die X- und Y-Koordinaten darstellen.

## <a name="canimationpointgetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationPoint::GetDefaultValue

Gibt die Standardwerte für X- und Y-Koordinaten zurück.

```
CPoint GetDefaultValue();
```

### <a name="return-value"></a>Rückgabewert

Ein Punkt, der den Standardwert enthält.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um den Standardwert abzurufen, der zuvor vom Konstruktor oder SetDefaultValue festgelegt wurde.

## <a name="canimationpointgetvalue"></a><a name="getvalue"></a>CAnimationPoint::GetValue

Gibt den aktuellen Wert zurück.

```
BOOL GetValue(CPoint& ptValue);
```

### <a name="parameters"></a>Parameter

*ptValue*<br/>
Ausgabe Enthält den aktuellen Wert, wenn diese Methode zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der aktuelle Wert erfolgreich abgerufen wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um den aktuellen Wert des Animationspunkts abzurufen. Wenn diese Methode fehlschlägt oder zugrunde liegende COM-Objekte für X- und Y-Koordinaten nicht initialisiert wurden, enthält ptValue den Standardwert, der zuvor im Konstruktor oder durch SetDefaultValue festgelegt wurde.

## <a name="canimationpointgetx"></a><a name="getx"></a>CAnimationPoint::GetX

Bietet Zugriff auf CAnimationVariable für X-Koordinate.

```
CAnimationVariable& GetX();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf gekapselte CAnimationVariable, die X-Koordinate darstellt.

### <a name="remarks"></a>Bemerkungen

Sie können diese Methode aufrufen, um direkten Zugriff auf die zugrunde liegende CAnimationVariable zu erhalten, die X-Koordinate darstellt.

## <a name="canimationpointgety"></a><a name="gety"></a>CAnimationPoint::GetY

Bietet Zugriff auf CAnimationVariable für Y-Koordinate.

```
CAnimationVariable& GetY();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf gekapselte CAnimationVariable, die Y-Koordinate darstellt.

### <a name="remarks"></a>Bemerkungen

Sie können diese Methode aufrufen, um direkten Zugriff auf die zugrunde liegende CAnimationVariable zu erhalten, die Y-Koordinate darstellt.

## <a name="canimationpointm_xvalue"></a><a name="m_xvalue"></a>CAnimationPoint::m_xValue

Die gekapselte Animationsvariable, die die X-Koordinate des Animationspunkts darstellt.

```
CAnimationVariable m_xValue;
```

## <a name="canimationpointm_yvalue"></a><a name="m_yvalue"></a>CAnimationPoint::m_yValue

Die gekapselte Animationsvariable, die die Y-Koordinate des Animationspunkts darstellt.

```
CAnimationVariable m_yValue;
```

## <a name="canimationpointoperator-cpoint"></a><a name="operator_cpoint"></a>CAnimationPoint::operator CPoint

Konvertiert einen CAnimationPoint in einen CPoint.

```
operator CPoint();
```

### <a name="return-value"></a>Rückgabewert

Aktueller Wert von CAnimationPoint als CPoint.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ruft getValue intern auf. Wenn GetValue aus irgendeinem Grund fehlschlägt, enthält der zurückgegebene Punkt Standardwerte für X- und Y-Koordinaten.

## <a name="canimationpointoperator"></a><a name="operator_eq"></a>CAnimationPoint::operator=

Weist cAnimationPoint ptSrc zu.

```cpp
void operator=(const CPoint& ptSrc);
```

### <a name="parameters"></a>Parameter

*ptSrc*<br/>
Bezieht sich auf CPoint oder POINT.

### <a name="remarks"></a>Bemerkungen

Weist cAnimationPoint ptSrc zu. Es wird empfohlen, dies vor dem Starten der Animation zu tun, da dieser Operator SetDefaultValue aufruft, wodurch die zugrunde liegenden COM-Objekte für X- und Y-Koordinaten neu erstellt werden, wenn sie erstellt wurden. Wenn Sie dieses Animationsobjekt für Ereignisse (ValueChanged oder IntegerValueChanged) abonniert haben, müssen Sie diese Ereignisse erneut aktivieren.

## <a name="canimationpointsetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationPoint::SetDefaultValue

Legt den Standardwert fest.

```cpp
void SetDefaultValue(const POINT& ptDefault);
```

### <a name="parameters"></a>Parameter

*ptDefault*<br/>
Gibt den Standardpunktwert an.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um einen Standardwert für animationsobjekt festzulegen. Diese Methode weist X- und Y-Koordinaten des Animationspunkts Standardwerte zu. Außerdem werden zugrunde liegende COM-Objekte neu erstellt, wenn sie erstellt wurden. Wenn Sie dieses Animationsobjekt für Ereignisse (ValueChanged oder IntegerValueChanged) abonniert haben, müssen Sie diese Ereignisse erneut aktivieren.

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)

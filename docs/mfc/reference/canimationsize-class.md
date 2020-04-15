---
title: CAnimationSize-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCX
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCY
- AFXANIMATIONCONTROLLER/CAnimationSize::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetValue
- AFXANIMATIONCONTROLLER/CAnimationSize::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cxValue
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cyValue
helpviewer_keywords:
- CAnimationSize [MFC], CAnimationSize
- CAnimationSize [MFC], AddTransition
- CAnimationSize [MFC], GetCX
- CAnimationSize [MFC], GetCY
- CAnimationSize [MFC], GetDefaultValue
- CAnimationSize [MFC], GetValue
- CAnimationSize [MFC], SetDefaultValue
- CAnimationSize [MFC], GetAnimationVariableList
- CAnimationSize [MFC], m_cxValue
- CAnimationSize [MFC], m_cyValue
ms.assetid: ea06d1b5-502c-44a3-82ca-8bd6ba6a9364
ms.openlocfilehash: 80a90dfa37bc1d2c3c84e6451ae23af7ded767c2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369703"
---
# <a name="canimationsize-class"></a>CAnimationSize-Klasse

Implementiert die Funktion eines Größenobjekts, dessen Dimensionen animiert werden können.

## <a name="syntax"></a>Syntax

```
class CAnimationSize : public CAnimationBaseObject;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationSize::CAnimationSize](#canimationsize)|Ist überladen. Erstellt ein Animationsgrößenobjekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationSize::AddTransition](#addtransition)|Fügt Übergänge für Breite und Höhe hinzu.|
|[CAnimationSize::GetCX](#getcx)|Bietet Zugriff auf CAnimationVariable, das Width darstellt.|
|[CAnimationSize::GetCY](#getcy)|Bietet Zugriff auf CAnimationVariable, das Height darstellt.|
|[CAnimationSize::GetDefaultValue](#getdefaultvalue)|Gibt die Standardwerte für Breite und Höhe zurück.|
|[CAnimationSize::GetValue](#getvalue)|Gibt den aktuellen Wert zurück.|
|[CAnimationSize::SetDefaultValue](#setdefaultvalue)|Legt den Standardwert fest.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationSize::GetAnimationVariableList](#getanimationvariablelist)|Fügt die gekapselten Animationsvariablen in eine Liste ein. (Überschreibt [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationSize::operator CSize](#operator_csize)|Konvertiert eine CAnimationSize in eine CSize.|
|[CAnimationSize::operator=](#operator_eq)|Weist szSrc CAnimationSize zu.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationSize::m_cxValue](#m_cxvalue)|Die gekapselte Animationsvariable, die die Breite der Animationsgröße darstellt.|
|[CAnimationSize::m_cyValue](#m_cyvalue)|Die gekapselte Animationsvariable, die die Höhe der Animationsgröße darstellt.|

## <a name="remarks"></a>Bemerkungen

Die CAnimationSize-Klasse kapselt zwei CAnimationVariable-Objekte und kann in Anwendungen eine Größe darstellen. Sie können diese Klasse beispielsweise verwenden, um eine Größe eines beliebigen zweidimensionalen Objekts auf dem Bildschirm zu animieren (z. B. Rechteck, Steuerelement usw.). Um diese Klasse in der Anwendung zu verwenden, instanziieren Sie einfach ein Objekt dieser Klasse, fügen Sie es dem Animationscontroller mit CAnimationController::AddAnimationObject hinzu, und rufen Sie AddTransition für jeden Übergang auf, der auf Breite und/oder Höhe angewendet werden soll.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationSize`

## <a name="requirements"></a>Anforderungen

**Header:** afxanimationcontroller.h

## <a name="canimationsizeaddtransition"></a><a name="addtransition"></a>CAnimationSize::AddTransition

Fügt Übergänge für Breite und Höhe hinzu.

```
void AddTransition(
    CBaseTransition* pCXTransition,
    CBaseTransition* pCYTransition);
```

### <a name="parameters"></a>Parameter

*pCXTransition*<br/>
Ein Zeiger auf den Übergang für Breite.

*pCYTransition*<br/>
Ein Zeiger auf den Übergang für Höhe.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um die angegebenen Übergänge zur internen Liste der Übergänge hinzuzufügen, die auf Animationsvariablen für Breite und Höhe angewendet werden sollen. Wenn Sie Übergänge hinzufügen, werden sie nicht sofort angewendet und in einer internen Liste gespeichert. Übergänge werden angewendet (zu einem Storyboard für einen bestimmten Wert hinzugefügt), wenn Sie CAnimationController::AnimateGroup aufrufen. Wenn Sie keinen Übergang auf eine Dimension anwenden müssen, können Sie NULL übergeben.

## <a name="canimationsizecanimationsize"></a><a name="canimationsize"></a>CAnimationSize::CAnimationSize

Erstellt ein Animationsgrößenobjekt.

```
CAnimationSize();

CAnimationSize(
    const CSize& szDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parameter

*szDefault*<br/>
Gibt die Standardgröße an.

*nGroupID*<br/>
Gibt die Gruppen-ID an.

*nObjectID*<br/>
Gibt die Objekt-ID an.

*dwUserData*<br/>
Gibt benutzerdefinierte Daten an.

### <a name="remarks"></a>Bemerkungen

Das Objekt wird mit Standardwerten für Breite, Höhe, Objekt-ID und Gruppen-ID erstellt, die auf 0 festgelegt werden. Sie können später zur Laufzeit mit SetDefaultValue und SetID geändert werden.

## <a name="canimationsizegetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationSize::GetAnimationVariableList

Fügt die gekapselten Animationsvariablen in eine Liste ein.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parameter

*Lst*<br/>
Wenn die Funktion zurückkehrt, enthält sie Zeiger auf zwei CAnimationVariable-Objekte, die die Breite und Höhe darstellen.

## <a name="canimationsizegetcx"></a><a name="getcx"></a>CAnimationSize::GetCX

Bietet Zugriff auf CAnimationVariable, das Width darstellt.

```
CAnimationVariable& GetCX();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf gekapselte CAnimationVariable, die Width darstellt.

### <a name="remarks"></a>Bemerkungen

Sie können diese Methode aufrufen, um direkten Zugriff auf die zugrunde liegende CAnimationVariable zu erhalten, die Width darstellt.

## <a name="canimationsizegetcy"></a><a name="getcy"></a>CAnimationSize::GetCY

Bietet Zugriff auf CAnimationVariable, das Height darstellt.

```
CAnimationVariable& GetCY();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf gekapselte CAnimationVariable, die Height darstellt.

### <a name="remarks"></a>Bemerkungen

Sie können diese Methode aufrufen, um direkten Zugriff auf die zugrunde liegende CAnimationVariable zu erhalten, die Height darstellt.

## <a name="canimationsizegetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationSize::GetDefaultValue

Gibt die Standardwerte für Breite und Höhe zurück.

```
CSize GetDefaultValue();
```

### <a name="return-value"></a>Rückgabewert

Ein CSize-Objekt, das Standardwerte enthält.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um den Standardwert abzurufen, der zuvor vom Konstruktor oder SetDefaultValue festgelegt wurde.

## <a name="canimationsizegetvalue"></a><a name="getvalue"></a>CAnimationSize::GetValue

Gibt den aktuellen Wert zurück.

```
BOOL GetValue(CSize& szValue);
```

### <a name="parameters"></a>Parameter

*szValue*<br/>
Ausgabe Enthält den aktuellen Wert, wenn diese Methode zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der aktuelle Wert erfolgreich abgerufen wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um den aktuellen Wert der Animationsgröße abzurufen. Wenn diese Methode fehlschlägt oder zugrunde liegende COM-Objekte für Breite und Größe nicht initialisiert wurden, enthält szValue den Standardwert, der zuvor im Konstruktor oder durch SetDefaultValue festgelegt wurde.

## <a name="canimationsizem_cxvalue"></a><a name="m_cxvalue"></a>CAnimationSize::m_cxValue

Die gekapselte Animationsvariable, die die Breite der Animationsgröße darstellt.

```
CAnimationVariable m_cxValue;
```

## <a name="canimationsizem_cyvalue"></a><a name="m_cyvalue"></a>CAnimationSize::m_cyValue

Die gekapselte Animationsvariable, die die Höhe der Animationsgröße darstellt.

```
CAnimationVariable m_cyValue;
```

## <a name="canimationsizeoperator-csize"></a><a name="operator_csize"></a>CAnimationSize::operator CSize

Konvertiert eine CAnimationSize in eine CSize.

```
operator CSize();
```

### <a name="return-value"></a>Rückgabewert

Aktueller Wert der Animationsgröße als CSize.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ruft getValue intern auf. Wenn GetValue aus irgendeinem Grund fehlschlägt, enthält die zurückgegebene Größe Standardwerte für Breite und Höhe.

## <a name="canimationsizeoperator"></a><a name="operator_eq"></a>CAnimationSize::operator=

Weist szSrc CAnimationSize zu.

```
void operator=(const CSize& szSrc);
```

### <a name="parameters"></a>Parameter

*szSrc*<br/>
Bezieht sich auf CSize oder SIZE.

### <a name="remarks"></a>Bemerkungen

Weist szSrc CAnimationSize zu. Es wird empfohlen, dies vor dem Starten der Animation zu tun, da dieser Operator SetDefaultValue aufruft, wodurch die zugrunde liegenden COM-Objekte für Breite und Höhe neu erstellt werden, wenn sie erstellt wurden. Wenn Sie dieses Animationsobjekt für Ereignisse (ValueChanged oder IntegerValueChanged) abonniert haben, müssen Sie diese Ereignisse erneut aktivieren.

## <a name="canimationsizesetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationSize::SetDefaultValue

Legt den Standardwert fest.

```
void SetDefaultValue(const CSize& szDefault);
```

### <a name="parameters"></a>Parameter

*szDefault*<br/>
Gibt die neue Standardgröße an.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um einen Standardwert für animationsobjekt festzulegen. Diese Methode weist Standardwerte der Größe breite und der Höhe der Animation zu. Außerdem werden zugrunde liegende COM-Objekte neu erstellt, wenn sie erstellt wurden. Wenn Sie dieses Animationsobjekt für Ereignisse (ValueChanged oder IntegerValueChanged) abonniert haben, müssen Sie diese Ereignisse erneut aktivieren.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)

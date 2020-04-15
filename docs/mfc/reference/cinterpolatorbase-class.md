---
title: CInterpolatorBase-Klasse
ms.date: 11/04/2016
f1_keywords:
- CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CreateInstance
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDependencies
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetFinalValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetCustomInterpolator
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetInitialValueAndVelocity
helpviewer_keywords:
- CInterpolatorBase [MFC], CInterpolatorBase
- CInterpolatorBase [MFC], CreateInstance
- CInterpolatorBase [MFC], GetDependencies
- CInterpolatorBase [MFC], GetDuration
- CInterpolatorBase [MFC], GetFinalValue
- CInterpolatorBase [MFC], InterpolateValue
- CInterpolatorBase [MFC], InterpolateVelocity
- CInterpolatorBase [MFC], SetCustomInterpolator
- CInterpolatorBase [MFC], SetDuration
- CInterpolatorBase [MFC], SetInitialValueAndVelocity
ms.assetid: bbc3dce7-8398-47f9-b97e-e4fd2d737232
ms.openlocfilehash: e5294aabc42301e2f874d5b8328d648f4deeb3c9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372352"
---
# <a name="cinterpolatorbase-class"></a>CInterpolatorBase-Klasse

Implementiert einen Rückruf, der von der Animations-API aufgerufen wird, wenn ein neuer Wert einer Animationsvariablen berechnet werden muss.

## <a name="syntax"></a>Syntax

```
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CInterpolatorBase::CInterpolatorBase](#cinterpolatorbase)|Erstellt das `CInterpolatorBase` Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CInterpolatorBase::CreateInstance](#createinstance)|Erstellt eine `CInterpolatorBase` Instanz von und speichert einen Zeiger auf den benutzerdefinierten Interpolator, der Ereignisse verarbeitet.|
|[CInterpolatorBase::Abhängigkeiten abrufen](#getdependencies)|Ruft die Abhängigkeiten des Interpolators ab. (Überschreibt `CUIAnimationInterpolatorBase::GetDependencies`.)|
|[CInterpolatorBase::GetDuration](#getduration)|Ruft die Dauer des Interpolators ab. (Überschreibt `CUIAnimationInterpolatorBase::GetDuration`.)|
|[CInterpolatorBase::GetFinalValue](#getfinalvalue)|Ruft den endgültigen Wert ab, zu dem der Interpolator führt. (Überschreibt `CUIAnimationInterpolatorBase::GetFinalValue`.)|
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|Interpoliert den Wert bei einem bestimmten `CUIAnimationInterpolatorBase::InterpolateValue`Offset (Überschreibt .)|
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|Interpoliert die Geschwindigkeit bei einem bestimmten `CUIAnimationInterpolatorBase::InterpolateVelocity`Offset (Overrides .)|
|[CInterpolatorBase::SetCustomInterpolator](#setcustominterpolator)|Speichert einen Zeiger auf den benutzerdefinierten Interpolator, der Ereignisse verarbeitet.|
|[CInterpolatorBase::SetDuration](#setduration)|Legt die Dauer des Interpolators `CUIAnimationInterpolatorBase::SetDuration`fest (Überschreibt .)|
|[CInterpolatorBase::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Legt den Anfangswert und die Geschwindigkeit des Interpolators fest. (Überschreibt `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`.)|

## <a name="remarks"></a>Bemerkungen

Dieser Handler wird erstellt `IUIAnimationTransitionFactory::CreateTransition` und `CCustomTransition` übergeben, wenn ein Objekt als Teil des `CAnimationController::AnimateGroup`Animationsinitialisierungsprozesses erstellt wird (gestartet von ). Normalerweise müssen Sie diese Klasse nicht direkt verwenden, sie führt `CCustomInterpolator`lediglich alle Ereignisse an eine -derived-Klasse aus, deren Zeiger an den Konstruktor von `CCustomTransition`übergeben wird.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>Anforderungen

**Header:** afxanimationcontroller.h

## <a name="cinterpolatorbasecinterpolatorbase"></a><a name="cinterpolatorbase"></a>CInterpolatorBase::CInterpolatorBase

Erstellt das CInterpolatorBase-Objekt.

```
CInterpolatorBase();
```

## <a name="cinterpolatorbasecreateinstance"></a><a name="createinstance"></a>CInterpolatorBase::CreateInstance

Erstellt eine Instanz von CInterpolatorBase und speichert einen Zeiger auf den benutzerdefinierten Interpolator, der Ereignisse verarbeitet.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>Parameter

*pInterpolator*<br/>
Ein Zeiger auf den benutzerdefinierten Interpolator.

*ppHandler*<br/>
Ausgabe Enthält einen Zeiger auf die Instanz von CInterpolatorBase, wenn die Funktion zurückkehrt.

### <a name="return-value"></a>Rückgabewert

## <a name="cinterpolatorbasegetdependencies"></a><a name="getdependencies"></a>CInterpolatorBase::Abhängigkeiten abrufen

Ruft die Abhängigkeiten des Interpolators ab.

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Parameter

*initialValueAbhängigkeiten*<br/>
Ausgabe Aspekte des Interpolators, die vom Anfangswert abhängen, der an SetInitialValueAndVelocity übergeben wird.

*initialVelocityDependencies*<br/>
Ausgabe Aspekte des Interpolators, die von der Anfangsgeschwindigkeit abhängen, die an SetInitialValueAndVelocity übergeben wird.

*DauerAbhängigkeiten*<br/>
Ausgabe Aspekte des Interpolators, die von der Dauer abhängen, die an SetDuration übergeben wird.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Es gibt E_FAIL zurück, wenn CCustomInterpolator nicht festgelegt ist, oder eine benutzerdefinierte Implementierung FALSE von der GetDependencies-Methode zurückgibt.

## <a name="cinterpolatorbasegetduration"></a><a name="getduration"></a>CInterpolatorBase::GetDuration

Ruft die Dauer des Interpolators ab.

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Parameter

*duration*<br/>
Ausgabe Die Dauer des Übergangs in Sekunden.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Es gibt E_FAIL zurück, wenn CCustomInterpolator nicht festgelegt ist, oder eine benutzerdefinierte Implementierung FALSE von der GetDuration-Methode zurückgibt.

## <a name="cinterpolatorbasegetfinalvalue"></a><a name="getfinalvalue"></a>CInterpolatorBase::GetFinalValue

Ruft den endgültigen Wert ab, zu dem der Interpolator führt.

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>Parameter

*value*<br/>
Ausgabe Der endgültige Wert einer Variablen am Ende des Übergangs.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Es gibt E_FAIL zurück, wenn CCustomInterpolator nicht festgelegt ist, oder eine benutzerdefinierte Implementierung FALSE von der GetFinalValue-Methode zurückgibt.

## <a name="cinterpolatorbaseinterpolatevalue"></a><a name="interpolatevalue"></a>CInterpolatorBase::InterpolateValue

Interpoliert den Wert bei einem bestimmten Offset

```
IFACEMETHOD(InterpolateValue)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* value);
```

### <a name="parameters"></a>Parameter

*offset*<br/>
Der Offset vom Beginn des Übergangs. Der Offset ist immer größer oder gleich Null und kleiner als die Dauer des Übergangs. Diese Methode wird nicht aufgerufen, wenn die Dauer des Übergangs Null ist.

*value*<br/>
Ausgabe Der interpolierte Wert.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Es gibt E_FAIL zurück, wenn CCustomInterpolator nicht festgelegt ist, oder eine benutzerdefinierte Implementierung FALSE von der InterpolateValue-Methode zurückgibt.

## <a name="cinterpolatorbaseinterpolatevelocity"></a><a name="interpolatevelocity"></a>CInterpolatorBase::InterpolateVelocity

Interpoliert die Geschwindigkeit bei einem bestimmten Offset

```
IFACEMETHOD(InterpolateVelocity)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* velocity);
```

### <a name="parameters"></a>Parameter

*offset*<br/>
Der Offset vom Beginn des Übergangs. Der Offset ist immer größer oder gleich Null und kleiner oder gleich der Dauer des Übergangs. Diese Methode wird nicht aufgerufen, wenn die Dauer des Übergangs Null ist.

*velocity*<br/>
Ausgabe Die Geschwindigkeit der Variablen am Offset.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Es gibt E_FAIL zurück, wenn CCustomInterpolator nicht festgelegt ist, oder eine benutzerdefinierte Implementierung FALSE von der InterpolateVelocity-Methode zurückgibt.

## <a name="cinterpolatorbasesetcustominterpolator"></a><a name="setcustominterpolator"></a>CInterpolatorBase::SetCustomInterpolator

Speichert einen Zeiger auf den benutzerdefinierten Interpolator, der Ereignisse verarbeitet.

```
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Parameter

*pInterpolator*<br/>
Ein Zeiger auf den benutzerdefinierten Interpolator.

## <a name="cinterpolatorbasesetduration"></a><a name="setduration"></a>CInterpolatorBase::SetDuration

Legt die Dauer des Interpolators fest

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parameter

*duration*<br/>
Die Dauer des Übergangs.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Es gibt E_FAIL zurück, wenn CCustomInterpolator nicht festgelegt ist, oder eine benutzerdefinierte Implementierung FALSE von der SetDuration-Methode zurückgibt.

## <a name="cinterpolatorbasesetinitialvalueandvelocity"></a><a name="setinitialvalueandvelocity"></a>CInterpolatorBase::SetInitialValueAndVelocity

Legt den Anfangswert und die Geschwindigkeit des Interpolators fest.

```
IFACEMETHOD(SetInitialValueAndVelocity)(
    __in DOUBLE initialValue,
    __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parameter

*initialValue*<br/>
Der Wert der Variablen zu Beginn des Übergangs.

*initialVelocity*<br/>
Die Geschwindigkeit der Variablen zu Beginn des Übergangs.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Es gibt E_FAIL zurück, wenn CCustomInterpolator nicht festgelegt ist, oder eine benutzerdefinierte Implementierung FALSE von der SetInitialValueAndVelocity-Methode zurückgibt.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)

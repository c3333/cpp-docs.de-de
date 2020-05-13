---
title: CCustomInterpolator-Klasse
ms.date: 11/04/2016
f1_keywords:
- CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::CCustomInterpolator
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDependencies
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::GetFinalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::Init
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetDuration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::SetInitialValueAndVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_currentVelocity
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_duration
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_finalValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomInterpolator::m_initialVelocity
helpviewer_keywords:
- CCustomInterpolator [MFC], CCustomInterpolator
- CCustomInterpolator [MFC], GetDependencies
- CCustomInterpolator [MFC], GetDuration
- CCustomInterpolator [MFC], GetFinalValue
- CCustomInterpolator [MFC], Init
- CCustomInterpolator [MFC], InterpolateValue
- CCustomInterpolator [MFC], InterpolateVelocity
- CCustomInterpolator [MFC], SetDuration
- CCustomInterpolator [MFC], SetInitialValueAndVelocity
- CCustomInterpolator [MFC], m_currentValue
- CCustomInterpolator [MFC], m_currentVelocity
- CCustomInterpolator [MFC], m_duration
- CCustomInterpolator [MFC], m_finalValue
- CCustomInterpolator [MFC], m_initialValue
- CCustomInterpolator [MFC], m_initialVelocity
ms.assetid: 28d85595-989a-40a3-b003-e0e38437a94d
ms.openlocfilehash: 00ce0661fa3fbde714a7299ecbbd54df7c9bcc36
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749164"
---
# <a name="ccustominterpolator-class"></a>CCustomInterpolator-Klasse

Implementiert einen einfachen Interpolator.

## <a name="syntax"></a>Syntax

```
class CCustomInterpolator;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCustomInterpolator::CCustomInterpolator](#ccustominterpolator)|Ist überladen. Erstellt ein benutzerdefiniertes Interpolatorobjekt und initialisiert Dauer und Geschwindigkeit auf bestimmte Werte.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCustomInterpolator::Abhängigkeiten abrufen](#getdependencies)|Ruft die Abhängigkeiten des Interpolators ab.|
|[CCustomInterpolator::GetDuration](#getduration)|Ruft die Dauer des Interpolators ab.|
|[CCustomInterpolator::GetFinalValue](#getfinalvalue)|Ruft den endgültigen Wert ab, zu dem der Interpolator führt.|
|[CCustomInterpolator::Init](#init)|Initialisiert Dauer und Endwert.|
|[CCustomInterpolator::InterpolateValue](#interpolatevalue)|Interpoliert den Wert bei einem bestimmten Offset.|
|[CCustomInterpolator::InterpolateVelocity](#interpolatevelocity)|Interpoliert die Geschwindigkeit bei einem bestimmten Offset|
|[CCustomInterpolator::SetDuration](#setduration)|Legt die Dauer des Interpolators fest.|
|[CCustomInterpolator::SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Legt den Anfangswert und die Geschwindigkeit des Interpolators fest.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCustomInterpolator::m_currentValue](#m_currentvalue)|Der interpolierte Wert.|
|[CCustomInterpolator::m_currentVelocity](#m_currentvelocity)|Die interpolierte Geschwindigkeit.|
|[CCustomInterpolator::m_duration](#m_duration)|Die Dauer des Übergangs.|
|[CCustomInterpolator::m_finalValue](#m_finalvalue)|Der endgültige Wert einer Variablen am Ende des Übergangs.|
|[CCustomInterpolator::m_initialValue](#m_initialvalue)|Der Wert der Variablen zu Beginn des Übergangs.|
|[CCustomInterpolator::m_initialVelocity](#m_initialvelocity)|Die Geschwindigkeit der Variablen zu Beginn des Übergangs.|

## <a name="remarks"></a>Bemerkungen

Leiten Sie eine Klasse von CCustomInterpolator ab, und überschreiben Sie alle erforderlichen Methoden, um einen benutzerdefinierten Interpolationsalgorithmus zu implementieren. Ein Zeiger auf diese Klasse sollte als Parameter an CCustomTransition übergeben werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CCustomInterpolator`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxanimationcontroller.h

## <a name="ccustominterpolatorccustominterpolator"></a><a name="ccustominterpolator"></a>CCustomInterpolator::CCustomInterpolator

Erstellt ein benutzerdefiniertes Interpolatorobjekt und legt alle Werte auf die Standardeinstellung 0 fest.

```
CCustomInterpolator();

CCustomInterpolator(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>Parameter

*duration*<br/>
Die Dauer des Übergangs.

*finalValue*

### <a name="remarks"></a>Bemerkungen

Verwenden Sie CCustomInterpolator::Init, um Dauer und Endwert später im Code zu initialisieren.

## <a name="ccustominterpolatorgetdependencies"></a><a name="getdependencies"></a>CCustomInterpolator::Abhängigkeiten abrufen

Ruft die Abhängigkeiten des Interpolators ab.

```
virtual BOOL GetDependencies(
    UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>Parameter

*initialValueAbhängigkeiten*<br/>
Ausgabe Aspekte des Interpolators, die vom Anfangswert abhängen, der an SetInitialValueAndVelocity übergeben wird.

*initialVelocityDependencies*<br/>
Ausgabe Aspekte des Interpolators, die von der Anfangsgeschwindigkeit abhängen, die an SetInitialValueAndVelocity übergeben wird.

*DauerAbhängigkeiten*<br/>
Ausgabe Aspekte des Interpolators, die von der Dauer abhängen, die an SetDuration übergeben wird.

### <a name="return-value"></a>Rückgabewert

Die grundlegende Implementierung gibt immer TRUE zurück. Geben Sie FALSE von der überschriebenen Implementierung zurück, wenn Sie das Ereignis fehlschlagen möchten.

## <a name="ccustominterpolatorgetduration"></a><a name="getduration"></a>CCustomInterpolator::GetDuration

Ruft die Dauer des Interpolators ab.

```
virtual BOOL GetDuration(UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>Parameter

*duration*<br/>
Ausgabe Die Dauer des Übergangs in Sekunden.

### <a name="return-value"></a>Rückgabewert

Die grundlegende Implementierung gibt immer TRUE zurück. Geben Sie FALSE von der überschriebenen Implementierung zurück, wenn Sie das Ereignis fehlschlagen möchten.

## <a name="ccustominterpolatorgetfinalvalue"></a><a name="getfinalvalue"></a>CCustomInterpolator::GetFinalValue

Ruft den endgültigen Wert ab, zu dem der Interpolator führt.

```
virtual BOOL GetFinalValue(DOUBLE* value);
```

### <a name="parameters"></a>Parameter

*value*<br/>
Ausgabe Der endgültige Wert einer Variablen am Ende des Übergangs.

### <a name="return-value"></a>Rückgabewert

Die grundlegende Implementierung gibt immer TRUE zurück. Geben Sie FALSE von der überschriebenen Implementierung zurück, wenn Sie das Ereignis fehlschlagen möchten.

## <a name="ccustominterpolatorinit"></a><a name="init"></a>CCustomInterpolator::Init

Initialisiert Dauer und Endwert.

```cpp
void Init(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue);
```

### <a name="parameters"></a>Parameter

*duration*<br/>
Die Dauer des Übergangs.

*finalValue*<br/>
Der endgültige Wert einer Variablen am Ende des Übergangs.

## <a name="ccustominterpolatorinterpolatevalue"></a><a name="interpolatevalue"></a>CCustomInterpolator::InterpolateValue

Interpoliert den Wert bei einem bestimmten Offset.

```
virtual BOOL InterpolateValue(
    UI_ANIMATION_SECONDS */,
    DOUBLE* value);
```

### <a name="parameters"></a>Parameter

*value*<br/>
Ausgabe Der interpolierte Wert.

### <a name="return-value"></a>Rückgabewert

Die grundlegende Implementierung gibt immer TRUE zurück. Geben Sie FALSE von der überschriebenen Implementierung zurück, wenn Sie das Ereignis fehlschlagen möchten.

## <a name="ccustominterpolatorinterpolatevelocity"></a><a name="interpolatevelocity"></a>CCustomInterpolator::InterpolateVelocity

Interpoliert die Geschwindigkeit bei einem bestimmten Offset

```
virtual BOOL InterpolateVelocity(
    UI_ANIMATION_SECONDS */,
    DOUBLE* velocity);
```

### <a name="parameters"></a>Parameter

*velocity*<br/>
Ausgabe Die Geschwindigkeit der Variablen am Offset.

### <a name="return-value"></a>Rückgabewert

Die grundlegende Implementierung gibt immer TRUE zurück. Geben Sie FALSE von der überschriebenen Implementierung zurück, wenn Sie das Ereignis fehlschlagen möchten.

## <a name="ccustominterpolatorm_currentvalue"></a><a name="m_currentvalue"></a>CCustomInterpolator::m_currentValue

Der interpolierte Wert.

```
DOUBLE m_currentValue;
```

## <a name="ccustominterpolatorm_currentvelocity"></a><a name="m_currentvelocity"></a>CCustomInterpolator::m_currentVelocity

Die interpolierte Geschwindigkeit.

```
DOUBLE m_currentVelocity;
```

## <a name="ccustominterpolatorm_duration"></a><a name="m_duration"></a>CCustomInterpolator::m_duration

Die Dauer des Übergangs.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="ccustominterpolatorm_finalvalue"></a><a name="m_finalvalue"></a>CCustomInterpolator::m_finalValue

Der endgültige Wert einer Variablen am Ende des Übergangs.

```
DOUBLE m_finalValue;
```

## <a name="ccustominterpolatorm_initialvalue"></a><a name="m_initialvalue"></a>CCustomInterpolator::m_initialValue

Der Wert der Variablen zu Beginn des Übergangs.

```
DOUBLE m_initialValue;
```

## <a name="ccustominterpolatorm_initialvelocity"></a><a name="m_initialvelocity"></a>CCustomInterpolator::m_initialVelocity

Die Geschwindigkeit der Variablen zu Beginn des Übergangs.

```
DOUBLE m_initialVelocity;
```

## <a name="ccustominterpolatorsetduration"></a><a name="setduration"></a>CCustomInterpolator::SetDuration

Legt die Dauer des Interpolators fest.

```
virtual BOOL SetDuration(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parameter

*duration*<br/>
Die Dauer des Übergangs.

### <a name="return-value"></a>Rückgabewert

Die grundlegende Implementierung gibt immer TRUE zurück. Geben Sie FALSE von der überschriebenen Implementierung zurück, wenn Sie das Ereignis fehlschlagen möchten.

## <a name="ccustominterpolatorsetinitialvalueandvelocity"></a><a name="setinitialvalueandvelocity"></a>CCustomInterpolator::SetInitialValueAndVelocity

Legt den Anfangswert und die Geschwindigkeit des Interpolators fest.

```
virtual BOOL SetInitialValueAndVelocity(
    DOUBLE initialValue,
    DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parameter

*initialValue*<br/>
Der Wert der Variablen zu Beginn des Übergangs.

*initialVelocity*<br/>
Die Geschwindigkeit der Variablen zu Beginn des Übergangs.

### <a name="return-value"></a>Rückgabewert

Die grundlegende Implementierung gibt immer TRUE zurück. Geben Sie FALSE von der überschriebenen Implementierung zurück, wenn Sie das Ereignis fehlschlagen möchten.

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)

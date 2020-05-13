---
title: CCustomTransition-Klasse
ms.date: 11/04/2016
f1_keywords:
- CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::Create
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialValueSpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialVelocitySpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_pInterpolator
helpviewer_keywords:
- CCustomTransition [MFC], CCustomTransition
- CCustomTransition [MFC], Create
- CCustomTransition [MFC], SetInitialValue
- CCustomTransition [MFC], SetInitialVelocity
- CCustomTransition [MFC], m_bInitialValueSpecified
- CCustomTransition [MFC], m_bInitialVelocitySpecified
- CCustomTransition [MFC], m_initialValue
- CCustomTransition [MFC], m_initialVelocity
- CCustomTransition [MFC], m_pInterpolator
ms.assetid: 5bd3f492-940f-4290-a38b-fa68eb8f8401
ms.openlocfilehash: 76e0d12308ad579e4bdf9866dfcf1cde231a2d0c
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749154"
---
# <a name="ccustomtransition-class"></a>CCustomTransition-Klasse

Implementiert einen benutzerdefinierten Übergang.

## <a name="syntax"></a>Syntax

```
class CCustomTransition : public CBaseTransition;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCustomTransition::CCustomTransition](#ccustomtransition)|Erstellt ein benutzerdefiniertes Übergangsobjekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCustomTransition::Erstellen](#create)|Ruft die Übergangsbibliothek auf, um ein gekapseltes COM-Übergangsobjekt zu erstellen. (Überschreibt [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|
|[CCustomTransition::SetInitialValue](#setinitialvalue)|Legt einen Anfangswert fest, der auf eine Animationsvariable angewendet wird, die diesem Übergang zugeordnet ist.|
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|Legt eine Anfangsgeschwindigkeit fest, die auf eine Animationsvariable angewendet wird, die diesem Übergang zugeordnet ist.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|Gibt an, ob der Anfangswert mit SetInitialValue angegeben wurde.|
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|Gibt an, ob die Anfangsgeschwindigkeit mit SetInitialVelocity angegeben wurde.|
|[CCustomTransition::m_initialValue](#m_initialvalue)|Speichert den Anfangswert.|
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|Speichert die Anfangsgeschwindigkeit.|
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|Speichert einen Zeiger auf einen benutzerdefinierten Interpolator.|

## <a name="remarks"></a>Bemerkungen

Die CCustomTransitions-Klasse ermöglicht Entwicklern das Implementieren benutzerdefinierter Übergänge. Es wird erstellt und als Standardübergang verwendet, aber sein Konstruktor akzeptiert als Parameter einen Zeiger auf einen benutzerdefinierten Interpolator. Führen Sie die folgenden Schritte aus, um benutzerdefinierte Übergänge zu verwenden: 1. Leiten Sie eine Klasse von CCustomInterpolator ab, und implementieren Sie mindestens die InterpolateValue-Methode. 2. Stellen Sie sicher, dass die Lebensdauer des benutzerdefinierten Interpolatorobjekts länger sein muss als die Dauer der Animation, in der es verwendet wird. 3. Instanziieren (mit Operator neu) ein CCustomTransition-Objekt und übergeben Sie einen Zeiger an den benutzerdefinierten Interpolator im Konstruktor. 4. Rufen Sie CCustomTransition::SetInitialValue und CCustomTransition::SetInitialVelocity auf, wenn diese Parameter für die benutzerdefinierte Interpolation erforderlich sind. 5. Übergeben Sie den Zeiger an den benutzerdefinierten Übergang zur AddTransition-Methode des Animationsobjekts, dessen Wert mit dem benutzerdefinierten Algorithmus animiert werden soll. 6. Wenn der Wert des Animationsobjekts geändert werden soll, ruft die Windows-Animations-API InterpolateValue (und andere relevante Methoden) in CCustomInterpolator auf.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCustomTransition`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxanimationcontroller.h

## <a name="ccustomtransitionccustomtransition"></a><a name="ccustomtransition"></a>CCustomTransition::CCustomTransition

Erstellt ein benutzerdefiniertes Übergangsobjekt.

```
CCustomTransition(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>Parameter

*pInterpolator*<br/>
Ein Zeiger auf den benutzerdefinierten Interpolator.

## <a name="ccustomtransitioncreate"></a><a name="create"></a>CCustomTransition::Erstellen

Ruft die Übergangsbibliothek auf, um ein gekapseltes COM-Übergangsobjekt zu erstellen.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,
    IUIAnimationTransitionFactory* pFactory);
```

### <a name="parameters"></a>Parameter

*pFactory*<br/>
Ein Zeiger auf die Übergangsfabrik, die für die Erstellung von benutzerdefinierten Übergängen verantwortlich ist.

### <a name="return-value"></a>Rückgabewert

### <a name="remarks"></a>Bemerkungen

Diese Methode kann auch den Anfangswert und die Anfangsgeschwindigkeit festlegen, die auf eine Animationsvariable angewendet werden sollen, die diesem Übergang zugeordnet ist. Zu diesem Zweck müssen Sie SetInitialValue und SetInitialVelocity aufrufen, bevor das Framework das gekapselte COM-Übergangs-COM-Objekt erstellt (dies geschieht, wenn Sie CAnimationController::AnimateGroup aufrufen).

## <a name="ccustomtransitionm_binitialvaluespecified"></a><a name="m_binitialvaluespecified"></a>CCustomTransition::m_bInitialValueSpecified

Gibt an, ob der Anfangswert mit SetInitialValue angegeben wurde.

```
BOOL m_bInitialValueSpecified;
```

## <a name="ccustomtransitionm_binitialvelocityspecified"></a><a name="m_binitialvelocityspecified"></a>CCustomTransition::m_bInitialVelocitySpecified

Gibt an, ob die Anfangsgeschwindigkeit mit SetInitialVelocity angegeben wurde.

```
BOOL m_bInitialVelocitySpecified;
```

## <a name="ccustomtransitionm_initialvalue"></a><a name="m_initialvalue"></a>CCustomTransition::m_initialValue

Speichert den Anfangswert.

```
DOUBLE m_initialValue;
```

## <a name="ccustomtransitionm_initialvelocity"></a><a name="m_initialvelocity"></a>CCustomTransition::m_initialVelocity

Speichert die Anfangsgeschwindigkeit.

```
DOUBLE m_initialVelocity;
```

## <a name="ccustomtransitionm_pinterpolator"></a><a name="m_pinterpolator"></a>CCustomTransition::m_pInterpolator

Speichert einen Zeiger auf einen benutzerdefinierten Interpolator.

```
CCustomInterpolator* m_pInterpolator;
```

## <a name="ccustomtransitionsetinitialvalue"></a><a name="setinitialvalue"></a>CCustomTransition::SetInitialValue

Legt einen Anfangswert fest, der auf eine Animationsvariable angewendet wird, die diesem Übergang zugeordnet ist.

```cpp
void SetInitialValue(DOUBLE initialValue);
```

### <a name="parameters"></a>Parameter

*initialValue*

## <a name="ccustomtransitionsetinitialvelocity"></a><a name="setinitialvelocity"></a>CCustomTransition::SetInitialVelocity

Legt eine Anfangsgeschwindigkeit fest, die auf eine Animationsvariable angewendet wird, die diesem Übergang zugeordnet ist.

```cpp
void SetInitialVelocity(DOUBLE initialVelocity);
```

### <a name="parameters"></a>Parameter

*initialVelocity*

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)

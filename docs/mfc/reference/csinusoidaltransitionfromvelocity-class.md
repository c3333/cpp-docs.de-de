---
title: CSinusoidalTransitionFromVelocity-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSinusoidalTransitionFromVelocity
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::CSinusoidalTransitionFromVelocity
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::Create
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::m_duration
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromVelocity::m_period
helpviewer_keywords:
- CSinusoidalTransitionFromVelocity [MFC], CSinusoidalTransitionFromVelocity
- CSinusoidalTransitionFromVelocity [MFC], Create
- CSinusoidalTransitionFromVelocity [MFC], m_duration
- CSinusoidalTransitionFromVelocity [MFC], m_period
ms.assetid: cc885f17-b84b-45ee-8f1f-36a8bbb7adad
ms.openlocfilehash: 0df9ca6d140cb9e3ec85be3ce32760a66599c5d4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318247"
---
# <a name="csinusoidaltransitionfromvelocity-class"></a>CSinusoidalTransitionFromVelocity-Klasse

Kapselt einen Übergang mit sinusförmiger Geschwindigkeit und einer Amplitude, die von der ursprünglichen Geschwindigkeit der Animationsvariablen bestimmt wird.

## <a name="syntax"></a>Syntax

```
class CSinusoidalTransitionFromVelocity : public CBaseTransition;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSinusoidalTransitionFromVelocity::CSinusoidalTransitionFromVelocity](#csinusoidaltransitionfromvelocity)|Erstellt ein Übergangsobjekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSinusoidalTransitionFromVelocity::Erstellen](#create)|Ruft die Übergangsbibliothek auf, um ein gekapseltes COM-Übergangsobjekt zu erstellen. (Überschreibt [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSinusoidalÜbergangVonVelocity::m_duration](#m_duration)|Die Dauer des Übergangs.|
|[CSinusoidalÜbergangVonVelocity::m_period](#m_period)|Die Periode der Schwingung der sinusförmigen Welle in Sekunden.|

## <a name="remarks"></a>Bemerkungen

Der Wert der Animationsvariablen oszilliert um den Anfangswert über die gesamte Dauer eines Sinusbereichsübergangs. Die Amplitude der Schwingung wird durch die Geschwindigkeit der Animationsvariablen bestimmt, wenn der Übergang beginnt. Da alle Übergänge automatisch gelöscht werden, wird empfohlen, sie mit dem Operator new zuzuweisen. Das gekapselte IUIAnimationTransition COM-Objekt wird von CAnimationController::AnimateGroup erstellt, bis es NULL ist. Das Ändern von Membervariablen nach der Erstellung dieses COM-Objekts hat keine Auswirkungen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CSinusoidalTransitionFromVelocity](../../mfc/reference/csinusoidaltransitionfromvelocity-class.md)

## <a name="requirements"></a>Anforderungen

**Header:** afxanimationcontroller.h

## <a name="csinusoidaltransitionfromvelocitycreate"></a><a name="create"></a>CSinusoidalTransitionFromVelocity::Erstellen

Ruft die Übergangsbibliothek auf, um ein gekapseltes COM-Übergangsobjekt zu erstellen.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parameter

*pLibrary*<br/>
Ein Zeiger auf die Übergangsbibliothek, die für die Erstellung von Standardübergängen verantwortlich ist.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Übergang erfolgreich erstellt wurde; andernfalls FALSE.

## <a name="csinusoidaltransitionfromvelocitycsinusoidaltransitionfromvelocity"></a><a name="csinusoidaltransitionfromvelocity"></a>CSinusoidalTransitionFromVelocity::CSinusoidalTransitionFromVelocity

Erstellt ein Übergangsobjekt.

```
CSinusoidalTransitionFromVelocity(
    UI_ANIMATION_SECONDS duration,
    UI_ANIMATION_SECONDS period);
```

### <a name="parameters"></a>Parameter

*duration*<br/>
Die Dauer des Übergangs.

*Zeitraum*<br/>
Die Periode der Schwingung der sinusförmigen Welle in Sekunden.

## <a name="csinusoidaltransitionfromvelocitym_duration"></a><a name="m_duration"></a>CSinusoidalÜbergangVonVelocity::m_duration

Die Dauer des Übergangs.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="csinusoidaltransitionfromvelocitym_period"></a><a name="m_period"></a>CSinusoidalÜbergangVonVelocity::m_period

Die Periode der Schwingung der sinusförmigen Welle in Sekunden.

```
UI_ANIMATION_SECONDS m_period;
```

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)

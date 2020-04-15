---
title: CSinusoidalTransitionFromRange-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::Create
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMaximumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_dblMinimumValue
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_duration
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_period
- AFXANIMATIONCONTROLLER/CSinusoidalTransitionFromRange::m_slope
helpviewer_keywords:
- CSinusoidalTransitionFromRange [MFC], CSinusoidalTransitionFromRange
- CSinusoidalTransitionFromRange [MFC], Create
- CSinusoidalTransitionFromRange [MFC], m_dblMaximumValue
- CSinusoidalTransitionFromRange [MFC], m_dblMinimumValue
- CSinusoidalTransitionFromRange [MFC], m_duration
- CSinusoidalTransitionFromRange [MFC], m_period
- CSinusoidalTransitionFromRange [MFC], m_slope
ms.assetid: 8b66a729-5f10-431a-b055-e3600d0065da
ms.openlocfilehash: 0612a4b365b928d3c9be6d76168a76b4ee1caa85
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318257"
---
# <a name="csinusoidaltransitionfromrange-class"></a>CSinusoidalTransitionFromRange-Klasse

Kapselt einen Übergang mit sinusförmigem Bereich und angegebenem Schwingungsbereich.

## <a name="syntax"></a>Syntax

```
class CSinusoidalTransitionFromRange : public CBaseTransition;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange](#csinusoidaltransitionfromrange)|Erstellt ein Übergangsobjekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSinusoidalTransitionFromRange::Erstellen](#create)|Ruft die Übergangsbibliothek auf, um ein gekapseltes COM-Übergangsobjekt zu erstellen. (Überschreibt [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSinusoidalTransitionFromRange::m_dblMaximumValue](#m_dblmaximumvalue)|Der Wert der Animationsvariablen an einem Punkt der sinusförmigen Welle.|
|[CSinusoidalTransitionFromRange::m_dblMinimumValue](#m_dblminimumvalue)|Der Wert der Animationsvariablen an einem Trog der Sinuswelle.|
|[CSinusoidalTransitionFromRange::m_duration](#m_duration)|Die Dauer des Übergangs.|
|[CSinusoidalTransitionFromRange::m_period](#m_period)|Die Periode der Schwingung der sinusförmigen Welle in Sekunden.|
|[CSinusoidalTransitionFromRange::m_slope](#m_slope)|Die Steigung am Anfang des Übergangs.|

## <a name="remarks"></a>Bemerkungen

Der Wert der Animationsvariablen schwankt zwischen den angegebenen Minimal- und Maximalwerten über die gesamte Dauer eines Sinusbereichsübergangs. Der Neigungsparameter wird verwendet, um die beiden möglichen Sinuswellen, die durch die anderen Parameter angegeben werden, zu disambiguieren. Da alle Übergänge automatisch gelöscht werden, wird empfohlen, sie mit dem Operator new zuzuweisen. Das gekapselte IUIAnimationTransition COM-Objekt wird von CAnimationController::AnimateGroup erstellt, bis es NULL ist. Das Ändern von Membervariablen nach der Erstellung dieses COM-Objekts hat keine Auswirkungen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CSinusoidalTransitionFromRange](../../mfc/reference/csinusoidaltransitionfromrange-class.md)

## <a name="requirements"></a>Anforderungen

**Header:** afxanimationcontroller.h

## <a name="csinusoidaltransitionfromrangecreate"></a><a name="create"></a>CSinusoidalTransitionFromRange::Erstellen

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

## <a name="csinusoidaltransitionfromrangecsinusoidaltransitionfromrange"></a><a name="csinusoidaltransitionfromrange"></a>CSinusoidalTransitionFromRange::CSinusoidalTransitionFromRange

Erstellt ein Übergangsobjekt.

```
CSinusoidalTransitionFromRange(
    UI_ANIMATION_SECONDS duration,
    DOUBLE dblMinimumValue,
    DOUBLE dblMaximumValue,
    UI_ANIMATION_SECONDS period,
    UI_ANIMATION_SLOPE slope);
```

### <a name="parameters"></a>Parameter

*duration*<br/>
Die Dauer des Übergangs.

*dblMinimumValue*<br/>
Der Wert der Animationsvariablen an einem Trog der Sinuswelle.

*dblMaximumValue*<br/>
Der Wert der Animationsvariablen an einem Punkt der sinusförmigen Welle.

*Zeitraum*<br/>
Die Periode der Schwingung der sinusförmigen Welle in Sekunden.

*Steigung*<br/>
Die Steigung am Anfang des Übergangs.

## <a name="csinusoidaltransitionfromrangem_dblmaximumvalue"></a><a name="m_dblmaximumvalue"></a>CSinusoidalTransitionFromRange::m_dblMaximumValue

Der Wert der Animationsvariablen an einem Punkt der sinusförmigen Welle.

```
DOUBLE m_dblMaximumValue;
```

## <a name="csinusoidaltransitionfromrangem_dblminimumvalue"></a><a name="m_dblminimumvalue"></a>CSinusoidalTransitionFromRange::m_dblMinimumValue

Der Wert der Animationsvariablen an einem Trog der Sinuswelle.

```
DOUBLE m_dblMinimumValue;
```

## <a name="csinusoidaltransitionfromrangem_duration"></a><a name="m_duration"></a>CSinusoidalTransitionFromRange::m_duration

Die Dauer des Übergangs.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="csinusoidaltransitionfromrangem_period"></a><a name="m_period"></a>CSinusoidalTransitionFromRange::m_period

Die Periode der Schwingung der sinusförmigen Welle in Sekunden.

```
UI_ANIMATION_SECONDS m_period;
```

## <a name="csinusoidaltransitionfromrangem_slope"></a><a name="m_slope"></a>CSinusoidalTransitionFromRange::m_slope

Die Steigung am Anfang des Übergangs.

```
UI_ANIMATION_SLOPE m_slope;
```

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)

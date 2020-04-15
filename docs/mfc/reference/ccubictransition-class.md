---
title: CCubicTransition-Klasse
ms.date: 11/04/2016
f1_keywords:
- CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::Create
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalVelocity
- AFXANIMATIONCONTROLLER/CCubicTransition::m_duration
helpviewer_keywords:
- CCubicTransition [MFC], CCubicTransition
- CCubicTransition [MFC], Create
- CCubicTransition [MFC], m_dblFinalValue
- CCubicTransition [MFC], m_dblFinalVelocity
- CCubicTransition [MFC], m_duration
ms.assetid: 4fc30e9c-160c-45e1-bdbe-51adf8fee9c5
ms.openlocfilehash: de376503111dab157ca34744863fb1d35a58785e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369338"
---
# <a name="ccubictransition-class"></a>CCubicTransition-Klasse

Kapselt einen kubischen Übergang.

## <a name="syntax"></a>Syntax

```
class CCubicTransition : public CBaseTransition;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCubicTransition::CCubicTransition](#ccubictransition)|Erstellt ein Übergangsobjekt und initialisiert seine Parameter.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCubicTransition::Erstellen](#create)|Ruft die Übergangsbibliothek auf, um ein gekapseltes COM-Übergangsobjekt zu erstellen. (Überschreibt [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CCubicTransition::m_dblFinalValue](#m_dblfinalvalue)|Der Wert der Animationsvariablen am Ende des Übergangs.|
|[CCubicTransition::m_dblFinalVelocity](#m_dblfinalvelocity)|Die Geschwindigkeit der Variablen am Ende des Übergangs.|
|[CCubicTransition::m_duration](#m_duration)|Die Dauer des Übergangs.|

## <a name="remarks"></a>Bemerkungen

Während eines kubischen Übergangs ändert sich der Wert der Animationsvariablen von ihrem Anfangswert in einen angegebenen Endwert über die Dauer des Übergangs und endet mit einer angegebenen Geschwindigkeit. Da alle Übergänge automatisch gelöscht werden, wird empfohlen, sie mit dem Operator new zuzuweisen. Das gekapselte IUIAnimationTransition COM-Objekt wird von CAnimationController::AnimateGroup erstellt, bis es NULL ist. Das Ändern von Membervariablen nach der Erstellung dieses COM-Objekts hat keine Auswirkungen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCubicTransition`

## <a name="requirements"></a>Anforderungen

**Header:** afxanimationcontroller.h

## <a name="ccubictransitionccubictransition"></a><a name="ccubictransition"></a>CCubicTransition::CCubicTransition

Erstellt ein Übergangsobjekt und initialisiert seine Parameter.

```
CCubicTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE finalVelocity);
```

### <a name="parameters"></a>Parameter

*duration*<br/>
Die Dauer des Übergangs.

*finalValue*<br/>
Der Wert der Animationsvariablen am Ende des Übergangs.

*finalVelocity*<br/>
Die Geschwindigkeit der Variablen am Ende des Übergangs.

## <a name="ccubictransitioncreate"></a><a name="create"></a>CCubicTransition::Erstellen

Ruft die Übergangsbibliothek auf, um ein gekapseltes COM-Übergangsobjekt zu erstellen.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parameter

*pLibrary*<br/>
Ein Zeiger auf eine [IUIAnimationTransitionLibrary-Schnittstelle](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), die eine Bibliothek mit Standardübergängen definiert.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Übergang erfolgreich erstellt wurde; andernfalls FALSE.

## <a name="ccubictransitionm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>CCubicTransition::m_dblFinalValue

Der Wert der Animationsvariablen am Ende des Übergangs.

```
DOUBLE m_dblFinalValue;
```

## <a name="ccubictransitionm_dblfinalvelocity"></a><a name="m_dblfinalvelocity"></a>CCubicTransition::m_dblFinalVelocity

Die Geschwindigkeit der Variablen am Ende des Übergangs.

```
DOUBLE m_dblFinalVelocity;
```

## <a name="ccubictransitionm_duration"></a><a name="m_duration"></a>CCubicTransition::m_duration

Die Dauer des Übergangs.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)

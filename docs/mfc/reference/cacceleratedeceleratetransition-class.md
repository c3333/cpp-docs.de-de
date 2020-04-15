---
title: CAccelerateDecelerateTransition-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
ms.openlocfilehash: 356ba30e6d9a638672d2c356676735ebfaed8f3e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371148"
---
# <a name="cacceleratedeceleratetransition-class"></a>CAccelerateDecelerateTransition-Klasse

Implementiert einen Übergang mit Beschleunigung/Verlangsamung.

## <a name="syntax"></a>Syntax

```
class CAccelerateDecelerateTransition : public CBaseTransition;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|Erstellt ein Übergangsobjekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAccelerateDecelerateTransition::Erstellen](#create)|Ruft die Übergangsbibliothek auf, um ein gekapseltes COM-Übergangsobjekt zu erstellen. (Überschreibt [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAccelerateDecelerateÜbergang::m_accelerationRatio](#m_accelerationratio)|Das Verhältnis der Zeit, die für die Beschleunigung aufgewendet wurde, zur Dauer.|
|[CAccelerateDecelerateÜbergang::m_decelerationRatio](#m_decelerationratio)|Das Verhältnis der Zeit, die für die Verlangsamung aufgewendet wurde, zur Dauer.|
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|Die Dauer des Übergangs.|
|[CAccelerateDecelerateÜbergang::m_finalValue](#m_finalvalue)|Der Wert der Animationsvariablen am Ende des Übergangs.|

## <a name="remarks"></a>Bemerkungen

Während eines Beschleunigt-Verlangsamen-Übergangs beschleunigt sich die Animationsvariable und verlangsamt sich dann über die Dauer des Übergangs und endet bei einem angegebenen Wert. Sie können steuern, wie schnell die Variable unabhängig beschleunigt und verlangsamt wird, indem Sie unterschiedliche Beschleunigungs- und Verzögerungsverhältnisse angeben. Wenn die Anfangsgeschwindigkeit Null ist, ist das Beschleunigungsverhältnis der Bruchteil der Dauer, die die Variable für die Beschleunigung aufwendet. ebenfalls mit dem Verzögerungsverhältnis. Wenn die Anfangsgeschwindigkeit ungleich Null ist, ist dies der Bruchteil der Zeit zwischen der Geschwindigkeit, die Null erreicht, und dem Ende des Übergangs. Das Beschleunigungsverhältnis und das Verzögerungsverhältnis sollten auf maximal 1,0 summiert werden. Da alle Übergänge automatisch gelöscht werden, wird empfohlen, sie mit dem Operator new zuzuweisen. Das gekapselte IUIAnimationTransition COM-Objekt wird von CAnimationController::AnimateGroup erstellt, bis es NULL ist. Das Ändern von Membervariablen nach der Erstellung dieses COM-Objekts hat keine Auswirkungen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CAccelerateDecelerateTransition`

## <a name="requirements"></a>Anforderungen

**Header:** afxanimationcontroller.h

## <a name="cacceleratedeceleratetransitioncacceleratedeceleratetransition"></a><a name="cacceleratedeceleratetransition"></a>CAccelerateDecelerateTransition::CAccelerateDecelerateTransition

Erstellt ein Übergangsobjekt.

```
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE accelerationRatio = 0.3,
    DOUBLE decelerationRatio = 0.3);
```

### <a name="parameters"></a>Parameter

*duration*<br/>
Die Dauer des Übergangs.

*finalValue*<br/>
Der Wert der Animationsvariablen am Ende des Übergangs.

*Accelerationratio*<br/>
Das Verhältnis der Zeit, die für die Beschleunigung aufgewendet wurde, zur Dauer.

*Decelerationratio*<br/>
Das Verhältnis der Zeit, die für die Verlangsamung aufgewendet wurde, zur Dauer.

## <a name="cacceleratedeceleratetransitioncreate"></a><a name="create"></a>CAccelerateDecelerateTransition::Erstellen

Ruft die Übergangsbibliothek auf, um ein gekapseltes COM-Übergangsobjekt zu erstellen.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* *\not used*\);
```

### <a name="parameters"></a>Parameter

*pLibrary*<br/>
Ein Zeiger auf eine [IUIAnimationTransitionLibrary-Schnittstelle](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), die eine Bibliothek mit Standardübergängen definiert.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Übergang erfolgreich erstellt wurde; andernfalls FALSE.

## <a name="cacceleratedeceleratetransitionm_accelerationratio"></a><a name="m_accelerationratio"></a>CAccelerateDecelerateÜbergang::m_accelerationRatio

Das Verhältnis der Zeit, die für die Beschleunigung aufgewendet wurde, zur Dauer.

```
DOUBLE m_accelerationRatio;
```

## <a name="cacceleratedeceleratetransitionm_decelerationratio"></a><a name="m_decelerationratio"></a>CAccelerateDecelerateÜbergang::m_decelerationRatio

Das Verhältnis der Zeit, die für die Verlangsamung aufgewendet wurde, zur Dauer.

```
DOUBLE m_decelerationRatio;
```

## <a name="cacceleratedeceleratetransitionm_duration"></a><a name="m_duration"></a>CAccelerateDecelerateTransition::m_duration

Die Dauer des Übergangs.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="cacceleratedeceleratetransitionm_finalvalue"></a><a name="m_finalvalue"></a>CAccelerateDecelerateÜbergang::m_finalValue

Der Wert der Animationsvariablen am Ende des Übergangs.

```
DOUBLE m_finalValue;
```

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)

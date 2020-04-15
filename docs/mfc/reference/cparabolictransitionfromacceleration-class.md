---
title: CParabolicTransitionFromAcceleration-Klasse
ms.date: 11/04/2016
f1_keywords:
- CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::Create
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblAcceleration
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CParabolicTransitionFromAcceleration::m_dblFinalVelocity
helpviewer_keywords:
- CParabolicTransitionFromAcceleration [MFC], CParabolicTransitionFromAcceleration
- CParabolicTransitionFromAcceleration [MFC], Create
- CParabolicTransitionFromAcceleration [MFC], m_dblAcceleration
- CParabolicTransitionFromAcceleration [MFC], m_dblFinalValue
- CParabolicTransitionFromAcceleration [MFC], m_dblFinalVelocity
ms.assetid: 1e59b86f-358b-4da0-a4fd-8eaf5e85e00f
ms.openlocfilehash: 0aa5831e2262602ee46bd69031e5927a86b978e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364090"
---
# <a name="cparabolictransitionfromacceleration-class"></a>CParabolicTransitionFromAcceleration-Klasse

Kapselt einen Übergang mit parabelförmiger Beschleunigung.

## <a name="syntax"></a>Syntax

```
class CParabolicTransitionFromAcceleration : public CBaseTransition;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration](#cparabolictransitionfromacceleration)|Erstellt einen präbolischen Beschleunigungsübergang und initialisiert ihn mit angegebenen Parametern.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration::Erstellen](#create)|Ruft die Übergangsbibliothek auf, um ein gekapseltes COM-Übergangsobjekt zu erstellen. (Überschreibt [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CParabolicTransitionFromAcceleration::m_dblAcceleration](#m_dblacceleration)|Die Beschleunigung der Animationsvariablen während des Übergangs.|
|[CParabolicTransitionFromAcceleration::m_dblFinalValue](#m_dblfinalvalue)|Der Wert der Animationsvariablen am Ende des Übergangs.|
|[CParabolicTransitionFromAcceleration::m_dblFinalVelocity](#m_dblfinalvelocity)|Die Geschwindigkeit der Animationsvariablen am Ende des Übergangs.|

## <a name="remarks"></a>Bemerkungen

Während eines Präbolbeschleunigungsübergangs ändert sich der Wert der Animationsvariablen vom Anfangswert zum Endwert, der mit einer angegebenen Geschwindigkeit endet. Sie können steuern, wie schnell die Variable den Endwert erreicht, indem Sie die Beschleunigungsrate angeben. Da alle Übergänge automatisch gelöscht werden, wird empfohlen, sie mit dem Operator new zuzuweisen. Das gekapselte IUIAnimationTransition COM-Objekt wird von CAnimationController::AnimateGroup erstellt, bis es NULL ist. Das Ändern von Membervariablen nach der Erstellung dieses COM-Objekts hat keine Auswirkungen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CParabolicTransitionFromAcceleration](../../mfc/reference/cparabolictransitionfromacceleration-class.md)

## <a name="requirements"></a>Anforderungen

**Header:** afxanimationcontroller.h

## <a name="cparabolictransitionfromaccelerationcparabolictransitionfromacceleration"></a><a name="cparabolictransitionfromacceleration"></a>CParabolicTransitionFromAcceleration::CParabolicTransitionFromAcceleration

Erstellt einen präbolischen Beschleunigungsübergang und initialisiert ihn mit angegebenen Parametern.

```
CParabolicTransitionFromAcceleration(
    DOUBLE dblFinalValue,
    DOUBLE dblFinalVelocity,
    DOUBLE dblAcceleration);
```

### <a name="parameters"></a>Parameter

*dblFinalValue*<br/>
Der Wert der Animationsvariablen am Ende des Übergangs.

*dblFinalVelocity*<br/>
Die Geschwindigkeit der Animationsvariablen am Ende des Übergangs.

*dblAcceleration*<br/>
Die Beschleunigung der Animationsvariablen während des Übergangs.

## <a name="cparabolictransitionfromaccelerationcreate"></a><a name="create"></a>CParabolicTransitionFromAcceleration::Erstellen

Ruft die Übergangsbibliothek auf, um ein gekapseltes COM-Übergangsobjekt zu erstellen.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* /* not used */);
```

### <a name="parameters"></a>Parameter

*pLibrary*<br/>
Ein Zeiger auf die Übergangsbibliothek, die für die Erstellung von Standardübergängen verantwortlich ist.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Übergang erfolgreich erstellt wurde; andernfalls FALSE.

## <a name="cparabolictransitionfromaccelerationm_dblacceleration"></a><a name="m_dblacceleration"></a>CParabolicTransitionFromAcceleration::m_dblAcceleration

Die Beschleunigung der Animationsvariablen während des Übergangs.

```
DOUBLE m_dblAcceleration;
```

## <a name="cparabolictransitionfromaccelerationm_dblfinalvalue"></a><a name="m_dblfinalvalue"></a>CParabolicTransitionFromAcceleration::m_dblFinalValue

Der Wert der Animationsvariablen am Ende des Übergangs.

```
DOUBLE m_dblFinalValue;
```

## <a name="cparabolictransitionfromaccelerationm_dblfinalvelocity"></a><a name="m_dblfinalvelocity"></a>CParabolicTransitionFromAcceleration::m_dblFinalVelocity

Die Geschwindigkeit der Animationsvariablen am Ende des Übergangs.

```
DOUBLE m_dblFinalVelocity;
```

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)

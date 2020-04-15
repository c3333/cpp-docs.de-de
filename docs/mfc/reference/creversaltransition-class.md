---
title: CReversalTransition-Klasse
ms.date: 11/04/2016
f1_keywords:
- CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::CReversalTransition
- AFXANIMATIONCONTROLLER/CReversalTransition::Create
- AFXANIMATIONCONTROLLER/CReversalTransition::m_duration
helpviewer_keywords:
- CReversalTransition [MFC], CReversalTransition
- CReversalTransition [MFC], Create
- CReversalTransition [MFC], m_duration
ms.assetid: e89516be-2d07-4885-95a8-fc278f46e3ad
ms.openlocfilehash: 73d12fb6bbaefcfac1437248ebe11f3a5c24c45b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368318"
---
# <a name="creversaltransition-class"></a>CReversalTransition-Klasse

Kapselt einen Umkehrübergang.

## <a name="syntax"></a>Syntax

```
class CReversalTransition : public CBaseTransition;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CReversalTransition::CReversalTransition](#creversaltransition)|Erstellt ein Umkehrübergangsobjekt und initialisiert dessen Dauer.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CReversalTransition::Erstellen](#create)|Ruft die Übergangsbibliothek auf, um ein gekapseltes COM-Übergangsobjekt zu erstellen. (Überschreibt [CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create).)|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CReversalTransition::m_duration](#m_duration)|Die Dauer des Übergangs.|

## <a name="remarks"></a>Bemerkungen

Ein Umkehrübergang ändert sanft die Richtung über eine bestimmte Dauer. Der Endwert entspricht dem Anfangswert und die Endgeschwindigkeit ist das Negativ der Anfangsgeschwindigkeit. Da alle Übergänge automatisch gelöscht werden, wird empfohlen, sie mit dem Operator new zuzuweisen. Das gekapselte IUIAnimationTransition COM-Objekt wird von CAnimationController::AnimateGroup erstellt, bis es NULL ist. Das Ändern von Membervariablen nach der Erstellung dieses COM-Objekts hat keine Auswirkungen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CReversalTransition](../../mfc/reference/creversaltransition-class.md)

## <a name="requirements"></a>Anforderungen

**Header:** afxanimationcontroller.h

## <a name="creversaltransitioncreate"></a><a name="create"></a>CReversalTransition::Erstellen

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

## <a name="creversaltransitioncreversaltransition"></a><a name="creversaltransition"></a>CReversalTransition::CReversalTransition

Erstellt ein Umkehrübergangsobjekt und initialisiert dessen Dauer.

```
CReversalTransition(UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>Parameter

*duration*<br/>
Die Dauer des Übergangs.

## <a name="creversaltransitionm_duration"></a><a name="m_duration"></a>CReversalTransition::m_duration

Die Dauer des Übergangs.

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)

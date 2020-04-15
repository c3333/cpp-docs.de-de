---
title: CAnimationGroup-Klasse
ms.date: 03/27/2019
f1_keywords:
- CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::CAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationGroup::Animate
- AFXANIMATIONCONTROLLER/CAnimationGroup::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationGroup::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::Schedule
- AFXANIMATIONCONTROLLER/CAnimationGroup::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::AddTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutoclearTransitions
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_bAutodestroyKeyframes
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_lstKeyFrames
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pStoryboard
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationGroup::m_pParentController
helpviewer_keywords:
- CAnimationGroup [MFC], CAnimationGroup
- CAnimationGroup [MFC], Animate
- CAnimationGroup [MFC], ApplyTransitions
- CAnimationGroup [MFC], FindAnimationObject
- CAnimationGroup [MFC], GetGroupID
- CAnimationGroup [MFC], RemoveKeyframes
- CAnimationGroup [MFC], RemoveTransitions
- CAnimationGroup [MFC], Schedule
- CAnimationGroup [MFC], SetAutodestroyTransitions
- CAnimationGroup [MFC], AddKeyframes
- CAnimationGroup [MFC], AddTransitions
- CAnimationGroup [MFC], CreateTransitions
- CAnimationGroup [MFC], m_bAutoclearTransitions
- CAnimationGroup [MFC], m_bAutodestroyAnimationObjects
- CAnimationGroup [MFC], m_bAutodestroyKeyframes
- CAnimationGroup [MFC], m_lstAnimationObjects
- CAnimationGroup [MFC], m_lstKeyFrames
- CAnimationGroup [MFC], m_pStoryboard
- CAnimationGroup [MFC], m_nGroupID
- CAnimationGroup [MFC], m_pParentController
ms.assetid: 8bc18ceb-33a2-41d0-9731-71811adacab7
ms.openlocfilehash: 28d305e2107f7b9a8fd2164eb0ec9678d62ef8fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369744"
---
# <a name="canimationgroup-class"></a>CAnimationGroup-Klasse

Implementiert eine Animationsgruppe, die ein Animations-Storyboard, Animationsobjekte und Übergänge kombiniert, um eine Animation zu definieren.

## <a name="syntax"></a>Syntax

```
class CAnimationGroup;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationGroup::CAnimationGroup](#canimationgroup)|Erstellt eine Animationsgruppe.|
|[CAnimationGroup::'CAnimationGroup](#_dtorcanimationgroup)|Der Destruktor. Wird aufgerufen, wenn eine Animationsgruppe zerstört wird.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationGroup::Animieren](#animate)|Animiert eine Gruppe.|
|[CAnimationGroup::ApplyÜbergänge](#applytransitions)|Wendet Übergänge auf Animationsobjekte an.|
|[CAnimationGroup::FindAnimationObject](#findanimationobject)|Sucht ein Animationsobjekt, das die angegebene Animationsvariable enthält.|
|[CAnimationGroup::GetGroupID](#getgroupid)|Gibt GroupID zurück.|
|[CAnimationGroup::RemoveKeyframes](#removekeyframes)|Entfernt und zerstört optional alle Keyframes, die zu einer Animationsgruppe gehören.|
|[CAnimationGroup::EntfernenÜbergänge](#removetransitions)|Entfernt Übergänge aus Animationsobjekten, die zu einer Animationsgruppe gehören.|
|[CAnimationGroup::Zeitplan](#schedule)|Plant eine Animation zum angegebenen Zeitpunkt.|
|[CAnimationGroup::SetAutodestroyTransitions](#setautodestroytransitions)|Leitet alle Animationsobjekte, die zu Gruppe gehören, zerstört automatisch Übergänge.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationGroup::AddKeyframes](#addkeyframes)|Ein Helfer, der einem Storyboard Keyframes hinzufügt.|
|[CAnimationGroup::Übergangsübergänge hinzufügen](#addtransitions)|Ein Helfer, der einem Storyboard Übergänge hinzufügt.|
|[CAnimationGroup::Transitions erstellen](#createtransitions)|Ein Helfer, der COM-Übergangsobjekte erstellt.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationGroup::m_bAutoclearTransitions](#m_bautocleartransitions)|Gibt an, wie Übergänge aus Animationsobjekten, die zu einer Gruppe gehören, entfernt werden. Wenn dieses Element TRUE ist, werden Übergänge automatisch entfernt, wenn eine Animation geplant wurde. Andernfalls müssen Sie Übergänge manuell entfernen.|
|[CAnimationGroup::m_bAutodestroyAnimationObjects](#m_bautodestroyanimationobjects)|Gibt an, wie Animationsobjekte zerstört werden. Wenn dieser Parameter TRUE ist, werden Animationsobjekte automatisch zerstört, wenn die Gruppe zerstört wird. Andernfalls müssen Animationsobjekte manuell zerstört werden. Der Standardwert ist FALSE. Legen Sie diesen Wert nur dann auf TRUE fest, wenn alle Animationsobjekte, die zu group gehören, dynamisch mit dem Operator new zugewiesen werden.|
|[CAnimationGroup::m_bAutodestroyKeyframes](#m_bautodestroykeyframes)|Gibt an, wie Keyframes zerstört werden. Wenn dieser Wert TRUE ist, werden alle Keyframes entfernt und zerstört. Andernfalls werden sie nur aus der Liste entfernt. Der Standardwert ist TRUE.|
|[CAnimationGroup::m_lstAnimationObjects](#m_lstanimationobjects)|Enthält eine Liste von Animationsobjekten.|
|[CAnimationGroup::m_lstKeyFrames](#m_lstkeyframes)|Enthält eine Liste der Keyframes.|
|[CAnimationGroup::m_pStoryboard](#m_pstoryboard)|Zeigt auf das Animations-Storyboard. Dieser Zeiger ist nur nach dem Aufruf von Animate gültig.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationGroup::m_nGroupID](#m_ngroupid)|Ein eindeutiger Bezeichner der Animationsgruppe.|
|[CAnimationGroup::m_pParentController](#m_pparentcontroller)|Ein Zeiger auf den Animationscontroller, zu dem diese Gruppe gehört.|

## <a name="remarks"></a>Bemerkungen

Animationsgruppen werden automatisch vom Animationscontroller (CAnimationController) erstellt, wenn Sie Animationsobjekte mit CAnimationController::AddAnimationObject hinzufügen. Eine Animationsgruppe wird von GroupID identifiziert, die normalerweise als Parameter zum Bearbeiten von Animationsgruppen verwendet wird. Die GroupID wird aus dem ersten Animationsobjekt entnommen, das einer neuen Animationsgruppe hinzugefügt wird. Ein gekapseltes Animations-Storyboard wird erstellt, nachdem Sie CAnimationController::AnimateGroup aufgerufen haben und kann über öffentliche Mitglieder m_pStoryboard zugegriffen werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CAnimationGroup`

## <a name="requirements"></a>Anforderungen

**Header:** afxanimationcontroller.h

## <a name="canimationgroupcanimationgroup"></a><a name="_dtorcanimationgroup"></a>CAnimationGroup::'CAnimationGroup

Der Destruktor. Wird aufgerufen, wenn eine Animationsgruppe zerstört wird.

```
~CAnimationGroup();
```

## <a name="canimationgroupaddkeyframes"></a><a name="addkeyframes"></a>CAnimationGroup::AddKeyframes

Ein Helfer, der einem Storyboard Keyframes hinzufügt.

```
void AddKeyframes(IUIAnimationStoryboard* pStoryboard, BOOL bAddDeep);
```

### <a name="parameters"></a>Parameter

*pStoryboard*<br/>
Ein Zeiger auf ein Storyboard-COM-Objekt.

*bAddDeep*<br/>
Gibt an, ob diese Methode den Storyboard-Keyframes hinzugefügt werden soll, die von anderen Keyframes abhängen.

## <a name="canimationgroupaddtransitions"></a><a name="addtransitions"></a>CAnimationGroup::Übergangsübergänge hinzufügen

Ein Helfer, der einem Storyboard Übergänge hinzufügt.

```
void AddTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parameter

*pStoryboard*<br/>
Ein Zeiger auf ein Storyboard-COM-Objekt.

*bDependOnKeyframes*

## <a name="canimationgroupanimate"></a><a name="animate"></a>CAnimationGroup::Animieren

Animiert eine Gruppe.

```
BOOL Animate(
    IUIAnimationManager* pManager,
    IUIAnimationTimer* pTimer,
    BOOL bScheduleNow);
```

### <a name="parameters"></a>Parameter

*pManager*<br/>
*pTimer*
*bScheduleNow*

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode erstellt ein internes Storyboard, erstellt und wendet Übergänge an und plant eine Animation, wenn bScheduleNow TRUE ist. Wenn bScheduleNow FALSE ist, müssen Sie Schedule aufrufen, um die Animation zum angegebenen Zeitpunkt zu starten.

## <a name="canimationgroupapplytransitions"></a><a name="applytransitions"></a>CAnimationGroup::ApplyÜbergänge

Wendet Übergänge auf Animationsobjekte an.

```
void ApplyTransitions();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode ASSERTS im Debugmodus, wenn Storyboard nicht erstellt wurde. Es erstellt zuerst alle Übergänge, fügt dann "statische" Keyframes hinzu (Keyframes, die von Offsets abhängen), fügt Übergänge hinzu, die nicht von Keyframes abhängen, fügt Keyframes je nach Übergängen und anderen Keyframes hinzu und fügt schließlich Übergänge hinzu, die von Keyframes abhängen.

## <a name="canimationgroupcanimationgroup"></a><a name="canimationgroup"></a>CAnimationGroup::CAnimationGroup

Erstellt eine Animationsgruppe.

```
CAnimationGroup(CAnimationController* pParentController, UINT32 nGroupID);
```

### <a name="parameters"></a>Parameter

*pParentController*<br/>
Ein Zeiger auf den Animationscontroller, der eine Gruppe erstellt.

*nGroupID*<br/>
Gibt GroupID an.

## <a name="canimationgroupcreatetransitions"></a><a name="createtransitions"></a>CAnimationGroup::Transitions erstellen

Ein Helfer, der COM-Übergangsobjekte erstellt.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Rückgabewert

TRUE ist die Methode erfolgreich, andernfalls FALSE.

## <a name="canimationgroupfindanimationobject"></a><a name="findanimationobject"></a>CAnimationGroup::FindAnimationObject

Sucht ein Animationsobjekt, das die angegebene Animationsvariable enthält.

```
CAnimationBaseObject* FindAnimationObject(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parameter

*pVariable*<br/>
Ein Zeiger auf die Animationsvariable.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf ein Animationsobjekt oder NULL, wenn das Animationsobjekt nicht gefunden wird.

## <a name="canimationgroupgetgroupid"></a><a name="getgroupid"></a>CAnimationGroup::GetGroupID

Gibt GroupID zurück.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Gruppenbezeichner.

## <a name="canimationgroupm_bautocleartransitions"></a><a name="m_bautocleartransitions"></a>CAnimationGroup::m_bAutoclearTransitions

Gibt an, wie Übergänge aus Animationsobjekten, die zu einer Gruppe gehören, entfernt werden. Wenn dieses Element TRUE ist, werden Übergänge automatisch entfernt, wenn eine Animation geplant wurde. Andernfalls müssen Sie Übergänge manuell entfernen.

```
BOOL m_bAutoclearTransitions;
```

## <a name="canimationgroupm_bautodestroyanimationobjects"></a><a name="m_bautodestroyanimationobjects"></a>CAnimationGroup::m_bAutodestroyAnimationObjects

Gibt an, wie Animationsobjekte zerstört werden. Wenn dieser Parameter TRUE ist, werden Animationsobjekte automatisch zerstört, wenn die Gruppe zerstört wird. Andernfalls müssen Animationsobjekte manuell zerstört werden. Der Standardwert ist FALSE. Legen Sie diesen Wert nur dann auf TRUE fest, wenn alle Animationsobjekte, die zu group gehören, dynamisch mit dem Operator new zugewiesen werden.

```
BOOL m_bAutodestroyAnimationObjects;
```

## <a name="canimationgroupm_bautodestroykeyframes"></a><a name="m_bautodestroykeyframes"></a>CAnimationGroup::m_bAutodestroyKeyframes

Gibt an, wie Keyframes zerstört werden. Wenn dieser Wert TRUE ist, werden alle Keyframes entfernt und zerstört. Andernfalls werden sie nur aus der Liste entfernt. Der Standardwert ist TRUE.

```
BOOL m_bAutodestroyKeyframes;
```

## <a name="canimationgroupm_lstanimationobjects"></a><a name="m_lstanimationobjects"></a>CAnimationGroup::m_lstAnimationObjects

Enthält eine Liste von Animationsobjekten.

```
CObList m_lstAnimationObjects;
```

## <a name="canimationgroupm_lstkeyframes"></a><a name="m_lstkeyframes"></a>CAnimationGroup::m_lstKeyFrames

Enthält eine Liste der Keyframes.

```
CObList m_lstKeyFrames;
```

## <a name="canimationgroupm_ngroupid"></a><a name="m_ngroupid"></a>CAnimationGroup::m_nGroupID

Ein eindeutiger Bezeichner der Animationsgruppe.

```
UINT32 m_nGroupID;
```

## <a name="canimationgroupm_pparentcontroller"></a><a name="m_pparentcontroller"></a>CAnimationGroup::m_pParentController

Ein Zeiger auf den Animationscontroller, zu dem diese Gruppe gehört.

```
CAnimationController* m_pParentController;
```

## <a name="canimationgroupm_pstoryboard"></a><a name="m_pstoryboard"></a>CAnimationGroup::m_pStoryboard

Zeigt auf das Animations-Storyboard. Dieser Zeiger ist nur nach dem Aufruf von Animate gültig.

```
ATL::CComPtr<IUIAnimationStoryboard> m_pStoryboard;
```

## <a name="canimationgroupremovekeyframes"></a><a name="removekeyframes"></a>CAnimationGroup::RemoveKeyframes

Entfernt und zerstört optional alle Keyframes, die zu einer Animationsgruppe gehören.

```
void RemoveKeyframes();
```

### <a name="remarks"></a>Bemerkungen

Wenn m_bAutodestroyKeyframes Member TRUE ist, werden Keyframes entfernt und zerstört, andernfalls werden Keyframes einfach aus der internen Liste der Keyframes entfernt.

## <a name="canimationgroupremovetransitions"></a><a name="removetransitions"></a>CAnimationGroup::EntfernenÜbergänge

Entfernt Übergänge aus Animationsobjekten, die zu einer Animationsgruppe gehören.

```
void RemoveTransitions();
```

### <a name="remarks"></a>Bemerkungen

Wenn m_bAutoclearTransitions-Flag auf TRUE festgelegt ist, wird diese Methode über alle Animationsobjekte, die zur Gruppe gehören, durchlaufen und CAnimationObject::ClearTransitions(FALSE) aufrufen.

## <a name="canimationgroupschedule"></a><a name="schedule"></a>CAnimationGroup::Zeitplan

Plant eine Animation zum angegebenen Zeitpunkt.

```
BOOL Schedule(IUIAnimationTimer* pTimer, UI_ANIMATION_SECONDS time);
```

### <a name="parameters"></a>Parameter

*pTimer*<br/>
Ein Zeiger auf den Animationstimer.

*time*<br/>
Gibt die Zeit zum Planen der Animation an.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Methode erfolgreich ist; FALSE, wenn die Methode fehlschlägt oder Wenn Animate nicht aufgerufen wurde, wenn bScheduleNow auf FALSE festgelegt wurde.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um eine Animation zum angegebenen Zeitpunkt zu planen. Sie müssen Animate aufrufen, wobei bScheduleNow zuerst auf FALSE gesetzt ist.

## <a name="canimationgroupsetautodestroytransitions"></a><a name="setautodestroytransitions"></a>CAnimationGroup::SetAutodestroyTransitions

Leitet alle Animationsobjekte, die zu Gruppe gehören, zerstört automatisch Übergänge.

```
void SetAutodestroyTransitions(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parameter

*bAutoDestroy*<br/>
Gibt an, wie Übergänge zerstört werden.

### <a name="remarks"></a>Bemerkungen

Legen Sie diesen Wert nur dann auf FALSE fest, wenn Sie Übergänge auf dem Stapel zuweisen. Der Standardwert ist TRUE, daher wird dringend empfohlen, Übergangsobjekte mit Operator new zuzuweisen.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)

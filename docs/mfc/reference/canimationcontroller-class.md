---
title: CAnimationController-Klasse
ms.date: 03/27/2019
f1_keywords:
- CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::CAnimationController
- AFXANIMATIONCONTROLLER/CAnimationController::AddAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::AddKeyframeToGroup
- AFXANIMATIONCONTROLLER/CAnimationController::AnimateGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CleanUpGroup
- AFXANIMATIONCONTROLLER/CAnimationController::CreateKeyframe
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationManagerEvent
- AFXANIMATIONCONTROLLER/CAnimationController::EnableAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnablePriorityComparisonHandler
- AFXANIMATIONCONTROLLER/CAnimationController::EnableStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::FindAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::GetKeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::GetUIAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::GetUITransitionLibrary
- AFXANIMATIONCONTROLLER/CAnimationController::IsAnimationInProgress
- AFXANIMATIONCONTROLLER/CAnimationController::IsValid
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationIntegerValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationTimerRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationController::OnAnimationValueChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnBeforeAnimationStart
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCancel
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityCompress
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityConclude
- AFXANIMATIONCONTROLLER/CAnimationController::OnHasPriorityTrim
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationController::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAllAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationGroup
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationController::RemoveTransitions
- AFXANIMATIONCONTROLLER/CAnimationController::ScheduleGroup
- AFXANIMATIONCONTROLLER/CAnimationController::SetRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::UpdateAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::OnAfterSchedule
- AFXANIMATIONCONTROLLER/CAnimationController::gkeyframeStoryboardStart
- AFXANIMATIONCONTROLLER/CAnimationController::m_bIsValid
- AFXANIMATIONCONTROLLER/CAnimationController::m_lstAnimationGroups
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationManager
- AFXANIMATIONCONTROLLER/CAnimationController::m_pAnimationTimer
- AFXANIMATIONCONTROLLER/CAnimationController::m_pRelatedWnd
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionFactory
- AFXANIMATIONCONTROLLER/CAnimationController::m_pTransitionLibrary
helpviewer_keywords:
- CAnimationController [MFC], CAnimationController
- CAnimationController [MFC], AddAnimationObject
- CAnimationController [MFC], AddKeyframeToGroup
- CAnimationController [MFC], AnimateGroup
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], CreateKeyframe
- CAnimationController [MFC], EnableAnimationManagerEvent
- CAnimationController [MFC], EnableAnimationTimerEventHandler
- CAnimationController [MFC], EnablePriorityComparisonHandler
- CAnimationController [MFC], EnableStoryboardEventHandler
- CAnimationController [MFC], FindAnimationGroup
- CAnimationController [MFC], FindAnimationObject
- CAnimationController [MFC], GetKeyframeStoryboardStart
- CAnimationController [MFC], GetUIAnimationManager
- CAnimationController [MFC], GetUIAnimationTimer
- CAnimationController [MFC], GetUITransitionFactory
- CAnimationController [MFC], GetUITransitionLibrary
- CAnimationController [MFC], IsAnimationInProgress
- CAnimationController [MFC], IsValid
- CAnimationController [MFC], OnAnimationIntegerValueChanged
- CAnimationController [MFC], OnAnimationManagerStatusChanged
- CAnimationController [MFC], OnAnimationTimerPostUpdate
- CAnimationController [MFC], OnAnimationTimerPreUpdate
- CAnimationController [MFC], OnAnimationTimerRenderingTooSlow
- CAnimationController [MFC], OnAnimationValueChanged
- CAnimationController [MFC], OnBeforeAnimationStart
- CAnimationController [MFC], OnHasPriorityCancel
- CAnimationController [MFC], OnHasPriorityCompress
- CAnimationController [MFC], OnHasPriorityConclude
- CAnimationController [MFC], OnHasPriorityTrim
- CAnimationController [MFC], OnStoryboardStatusChanged
- CAnimationController [MFC], OnStoryboardUpdated
- CAnimationController [MFC], RemoveAllAnimationGroups
- CAnimationController [MFC], RemoveAnimationGroup
- CAnimationController [MFC], RemoveAnimationObject
- CAnimationController [MFC], RemoveTransitions
- CAnimationController [MFC], ScheduleGroup
- CAnimationController [MFC], SetRelatedWnd
- CAnimationController [MFC], UpdateAnimationManager
- CAnimationController [MFC], CleanUpGroup
- CAnimationController [MFC], OnAfterSchedule
- CAnimationController [MFC], gkeyframeStoryboardStart
- CAnimationController [MFC], m_bIsValid
- CAnimationController [MFC], m_lstAnimationGroups
- CAnimationController [MFC], m_pAnimationManager
- CAnimationController [MFC], m_pAnimationTimer
- CAnimationController [MFC], m_pRelatedWnd
- CAnimationController [MFC], m_pTransitionFactory
- CAnimationController [MFC], m_pTransitionLibrary
ms.assetid: ed294c98-695e-40a6-b940-33ef1d40aa6b
ms.openlocfilehash: 489e931c4063e7bf06ace1cb130b9891253c94d4
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750177"
---
# <a name="canimationcontroller-class"></a>CAnimationController-Klasse

Implementiert den Animationscontroller, der eine zentrale Schnittstelle zum Erstellen und Verwalten von Animationen bereitstellt.

## <a name="syntax"></a>Syntax

```
class CAnimationController : public CObject;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationController::CAnimationController](#canimationcontroller)|Erstellt einen Animationscontroller.|
|[CAnimationController::-CAnimationController](#_dtorcanimationcontroller)|Der Destruktor. Wird aufgerufen, wenn das Animationscontrollerobjekt zerstört wird.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationController::AddAnimationObject](#addanimationobject)|Fügt einer Gruppe, die zum Animationscontroller gehört, ein Animationsobjekt hinzu.|
|[CAnimationController::AddKeyframeToGroup](#addkeyframetogroup)|Fügt der Gruppe einen Keyframe hinzu.|
|[CAnimationController::AnimateGroup](#animategroup)|Bereitet eine Gruppe auf die Ausführung von Animationen vor und plant sie optional.|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Ist überladen. Wird vom Framework aufgerufen, um die Gruppe zu bereinigen, wenn die Animation geplant wurde.|
|[CAnimationController::CreateKeyframe](#createkeyframe)|Ist überladen. Erstellt einen Keyframe, der vom Übergang abhängig ist, und fügt ihn der angegebenen Gruppe hinzu.|
|[CAnimationController::EnableAnimationManagerEvent](#enableanimationmanagerevent)|Legt einen Handler fest oder gibt er frei, wenn sich der Status des Animations-Managers ändert.|
|[CAnimationController::EnableAnimationTimerEventHandler](#enableanimationtimereventhandler)|Legt einen Handler für Timingereignisse fest oder gibt er frei.|
|[CAnimationController::EnablePriorityComparisonHandler](#enableprioritycomparisonhandler)|Legt den zum Aufruf aufrufenden Prioritätsvergleichshandler fest oder gibt ihn frei, um zu bestimmen, ob ein geplantes Storyboard abgebrochen, abgeschlossen, getrimmt oder komprimiert werden kann.|
|[CAnimationController::EnableStoryboardEventHandler](#enablestoryboardeventhandler)|Legt einen Handler für Storyboardstatus und Aktualisierungsereignisse fest oder gibt ihn frei.|
|[CAnimationController::FindAnimationGroup](#findanimationgroup)|Ist überladen. Sucht eine Animationsgruppe anhand des Storyboards.|
|[CAnimationController::FindAnimationObject](#findanimationobject)|Sucht Animationsobjekt, das eine angegebene Animationsvariable enthält.|
|[CAnimationController::GetKeyframeStoryboardStart](#getkeyframestoryboardstart)|Gibt einen Keyframe zurück, der den Start des Storyboards identifiziert.|
|[CAnimationController::GetUIAnimationManager](#getuianimationmanager)|Bietet Zugriff auf gekapselte IUIAnimationManager-Objekte.|
|[CAnimationController::GetUIAnimationTimer](#getuianimationtimer)|Bietet Zugriff auf gekapselte IUIAnimationTimer-Objekte.|
|[CAnimationController::GetUITransitionFactory](#getuitransitionfactory)|Ein Zeiger auf die IUIAnimationTransitionFactory-Schnittstelle oder NULL, wenn die Erstellung der Übergangsbibliothek fehlgeschlagen ist.|
|[CAnimationController::GetUITransitionLibrary](#getuitransitionlibrary)|Bietet Zugriff auf gekapselte IUIAnimationTransitionLibrary-Objekte.|
|[CAnimationController::IsAnimationInProgress](#isanimationinprogress)|Gibt an, ob mindestens eine Gruppe Animationen abspielt.|
|[CAnimationController::IsValid](#isvalid)|Gibt an, ob der Animationscontroller gültig ist.|
|[CAnimationController::OnAnimationIntegerValueChanged](#onanimationintegervaluechanged)|Wird vom Framework aufgerufen, wenn sich der Ganzzahlwert der Animationsvariablen geändert hat.|
|[CAnimationController::OnAnimationManagerStatusGeändert](#onanimationmanagerstatuschanged)|Wird vom Framework als Reaktion auf das StatusChanged-Ereignis vom Animations-Manager aufgerufen.|
|[CanimationController::OnAnimationTimerpostUpdate](#onanimationtimerpostupdate)|Wird vom Framework aufgerufen, nachdem eine Animationsaktualisierung abgeschlossen wurde.|
|[CanimationController::OnAnimationTimerPreupdate](#onanimationtimerpreupdate)|Wird vom Framework aufgerufen, bevor eine Animationsaktualisierung beginnt.|
|[CanimationController::OnAnimationTimerRenderingTooSlow](#onanimationtimerrenderingtooslow)|Wird vom Framework aufgerufen, wenn die Renderbildrate für eine Animation unter eine wünschenswerte Mindestbildrate fällt.|
|[CAnimationController::OnAnimationValueChanged](#onanimationvaluechanged)|Wird vom Framework aufgerufen, wenn sich der Wert der Animationsvariablen geändert hat.|
|[CanimationController::OnBeforeAnimationStart](#onbeforeanimationstart)|Wird vom Framework direkt vor dem Geplanter der Animation aufgerufen.|
|[CanimationController::OnHasPrioritycancel](#onhasprioritycancel)|Wird vom Framework aufgerufen, um Konflikte bei der Planung zu beheben.|
|[CAnimationController::OnHasPriorityCompress](#onhasprioritycompress)|Wird vom Framework aufgerufen, um Konflikte bei der Planung zu beheben.|
|[CanimationController::OnHasPriorityConclude](#onhaspriorityconclude)|Wird vom Framework aufgerufen, um Konflikte bei der Planung zu beheben.|
|[CanimationController::OnHasPriorityTrim](#onhasprioritytrim)|Wird vom Framework aufgerufen, um Konflikte bei der Planung zu beheben.|
|[CAnimationController::OnStoryboardStatusStatusChanged](#onstoryboardstatuschanged)|Wird vom Framework aufgerufen, wenn sich der Storyboardstatus geändert hat.|
|[CAnimationController::OnStoryboardAktualisiert](#onstoryboardupdated)|Wird vom Framework aufgerufen, wenn das Storyboard aktualisiert wurde.|
|[CAnimationController::RemoveAllAnimationGroups](#removeallanimationgroups)|Entfernt alle Animationsgruppen aus dem Animationscontroller.|
|[CAnimationController::RemoveAnimationGroup](#removeanimationgroup)|Entfernt eine Animationsgruppe mit der angegebenen ID aus dem Animationscontroller.|
|[CAnimationController::RemoveAnimationObject](#removeanimationobject)|Entfernen Sie ein Animationsobjekt aus dem Animationscontroller.|
|[CAnimationController::EntfernenÜbergänge](#removetransitions)|Entfernt Übergänge aus Animationsobjekten, die zur angegebenen Gruppe gehören.|
|[CAnimationController::ScheduleGroup](#schedulegroup)|Plant eine Animation.|
|[CAnimationController::SetRelatedWnd](#setrelatedwnd)|Stellt eine Beziehung zwischen dem Animationscontroller und einem Fenster her.|
|[CAnimationController::UpdateAnimationManager](#updateanimationmanager)|Weist den Animations-Manager an, die Werte aller Animationsvariablen zu aktualisieren.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationController::CleanUpGroup](#cleanupgroup)|Ist überladen. Ein Helfer, der die Gruppe bereinigt.|
|[CAnimationController::OnAfterSchedule](#onafterschedule)|Wird vom Framework aufgerufen, wenn gerade eine Animation für die angegebene Gruppe geplant wurde.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationController::gkeyframeStoryboardStart](#g_keyframestoryboardstart)|Ein Keyframe, der den Anfang des Storyboards darstellt.|
|[CAnimationController::m_bIsValid](#m_bisvalid)|Gibt an, ob ein Animationscontroller gültig ist oder nicht. Dieses Mitglied ist auf FALSE festgelegt, wenn das aktuelle Betriebssystem die Windows-Animations-API nicht unterstützt.|
|[CAnimationController::m_lstAnimationGroups](#m_lstanimationgroups)|Eine Liste der Animationsgruppen, die zu diesem Animationscontroller gehören.|
|[CAnimationController::m_pAnimationManager](#m_panimationmanager)|Speichert einen Zeiger auf das Animations-Manager-COM-Objekt.|
|[CAnimationController::m_pAnimationTimer](#m_panimationtimer)|Speichert einen Zeiger auf das Animationstimer-COM-Objekt.|
|[CAnimationController::m_pRelatedWnd](#m_prelatedwnd)|Ein Zeiger auf ein verwandtes CWnd-Objekt, das automatisch neu gezeichnet werden kann, wenn sich der Status des Animations-Managers geändert hat oder ein Ereignis nach der Aktualisierung aufgetreten ist. Kann den Wert NULL haben.|
|[CAnimationController::m_pTransitionFactory](#m_ptransitionfactory)|Speichert einen Zeiger auf das Transition Factory COM-Objekt.|
|[CAnimationController::m_pTransitionLibrary](#m_ptransitionlibrary)|Speichert einen Zeiger auf das COM-Objekt der Übergangsbibliothek.|

## <a name="remarks"></a>Bemerkungen

Die CAnimationController-Klasse ist die Schlüsselklasse, die Animationen verwaltet. Sie können eine oder mehrere Instanzen des Animationscontrollers in einer Anwendung erstellen und optional eine Instanz des Animationscontrollers mit einem CWnd-Objekt mit CAnimationController::SetRelatedWnd verbinden. Diese Verbindung ist erforderlich, um WM_PAINT Nachrichten automatisch an das zugehörige Fenster zu senden, wenn sich der Animations-Manager-Status geändert oder der Animationstimer aktualisiert wurde. Wenn Sie diese Beziehung nicht aktivieren, müssen Sie ein Fenster neu zeichnen, in dem eine Animation manuell angezeigt wird. Zu diesem Zweck können Sie eine Klasse von CAnimationController ableiten und OnAnimationManagerStatusChanged und/oder OnAnimationTimerPostUpdate überschreiben und bei Bedarf ein oder mehrere Fenster ungültig machen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CAnimationController`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxanimationcontroller.h

## <a name="canimationcontrollercanimationcontroller"></a><a name="_dtorcanimationcontroller"></a>CAnimationController::-CAnimationController

Der Destruktor. Wird aufgerufen, wenn das Animationscontrollerobjekt zerstört wird.

```
virtual ~CAnimationController(void);
```

## <a name="canimationcontrolleraddanimationobject"></a><a name="addanimationobject"></a>CAnimationController::AddAnimationObject

Fügt einer Gruppe, die zum Animationscontroller gehört, ein Animationsobjekt hinzu.

```
CAnimationGroup* AddAnimationObject(CAnimationBaseObject* pObject);
```

### <a name="parameters"></a>Parameter

*pObject*<br/>
Ein Zeiger auf ein Animationsobjekt.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf eine vorhandene oder neue Animationsgruppe, in der pObject hinzugefügt wurde, wenn die Funktion erfolgreich ist. NULL, wenn pObject bereits einer Gruppe hinzugefügt wurde, die zu einem anderen Animationscontroller gehört.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um dem Animationscontroller ein Animationsobjekt hinzuzufügen. Ein Objekt wird einer Gruppe entsprechend der GroupID des Objekts hinzugefügt (siehe CAnimationBaseObject::SetID). Der Animationscontroller erstellt eine neue Gruppe, wenn es sich um das erste Objekt handelt, das mit der angegebenen GroupID hinzugefügt wird. Ein Animationsobjekt kann nur einem Animationscontroller hinzugefügt werden. Wenn Sie ein Objekt zu einem anderen Controller hinzufügen müssen, rufen Sie RemoveAnimationObject zuerst auf. Wenn Sie SetID mit neuer GroupID für ein Objekt aufrufen, das bereits einer Gruppe hinzugefügt wurde, wird das Objekt aus der alten Gruppe entfernt und einer anderen Gruppe mit der angegebenen ID hinzugefügt.

## <a name="canimationcontrolleraddkeyframetogroup"></a><a name="addkeyframetogroup"></a>CAnimationController::AddKeyframeToGroup

Fügt der Gruppe einen Keyframe hinzu.

```
BOOL AddKeyframeToGroup(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt die Gruppen-ID an.

*pKeyframe*<br/>
Ein Zeiger auf einen Keyframe.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Funktion erfolgreich ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Normalerweise müssen Sie diese Methode nicht aufrufen, verwenden Sie stattdessen CAnimationController::CreateKeyframe, das den erstellten Keyframe automatisch erstellt und einer Gruppe hinzufügt.

## <a name="canimationcontrolleranimategroup"></a><a name="animategroup"></a>CAnimationController::AnimateGroup

Bereitet eine Gruppe auf die Ausführung von Animationen vor und plant sie optional.

```
BOOL AnimateGroup(
    UINT32 nGroupID,
    BOOL bScheduleNow = TRUE);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt GroupID an.

*bScheduleNow*<br/>
Gibt an, ob Animationen sofort ausgeführt werden sollen.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Animation erfolgreich geplant und ausgeführt wurde.

### <a name="remarks"></a>Bemerkungen

Diese Methode führt die eigentliche Arbeit durch Erstellen von Storyboards, Hinzufügen von Animationsvariablen, Anwenden von Übergängen und Festlegen von Keyframes durch. Es ist möglich, die Terminierung zu verzögern, wenn Sie bScheduleNow auf FALSE setzen. In diesem Fall hält die angegebene Gruppe ein Storyboard, das für die Animation eingerichtet wurde. An diesem Punkt können Sie Ereignisse für das Storyboard und Animationsvariablen einrichten. Wenn Sie tatsächlich den Animationsaufruf CAnimationController::ScheduleGroup ausführen müssen.

## <a name="canimationcontrollercanimationcontroller"></a><a name="canimationcontroller"></a>CAnimationController::CAnimationController

Erstellt einen Animationscontroller.

```
CAnimationController(void);
```

## <a name="canimationcontrollercleanupgroup"></a><a name="cleanupgroup"></a>CAnimationController::CleanUpGroup

Wird vom Framework aufgerufen, um die Gruppe zu bereinigen, wenn die Animation geplant wurde.

```cpp
void CleanUpGroup(UINT32 nGroupID);
void CleanUpGroup(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt GroupID an.

*pGruppe*<br/>
Ein Zeiger auf die zu bereinigende Animationsgruppe.

### <a name="remarks"></a>Bemerkungen

Diese Methode entfernt alle Übergänge und Keyframes aus der angegebenen Gruppe, da sie nach dem Planen einer Animation nicht relevant sind.

## <a name="canimationcontrollercreatekeyframe"></a><a name="createkeyframe"></a>CAnimationController::CreateKeyframe

Erstellt einen Keyframe, der vom Übergang abhängig ist, und fügt ihn der angegebenen Gruppe hinzu.

```
CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,
    CBaseTransition* pTransition);

CKeyFrame* CreateKeyframe(
    UINT32 nGroupID,
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt die ID der Gruppe an, für die der Keyframe erstellt wird.

*pTransition*<br/>
Ein Zeiger auf den Übergang. Der Keyframe wird nach diesem Übergang in das Storyboard eingefügt.

*pKeyframe*<br/>
Ein Zeiger auf das Basiskeyframe für diesen Keyframe.

*offset*<br/>
Offset in Sekunden gegenüber dem vom „pKeyframe“ angegebenen Basiskeyframe.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das neu erstellte Keyframe, wenn die Funktion erfolgreich ausgeführt wurde.

### <a name="remarks"></a>Bemerkungen

Sie können den zurückgegebenen Zeiger speichern und weitere Keyframes auf dem neu erstellten Keyframe basieren lassen (siehe dazu die zweite Überladung). Es ist möglich, Übergänge an Keyframes zu beginnen – siehe dazu „CBaseTransition::SetKeyframes“. In dieser Weise erstellte Keyframes müssen nicht gelöscht werden, da sie von Animationsgruppen automatisch gelöscht werden. Gehen Sie beim Erstellen von Keyframes auf der Basis anderer Keyframes und Übergänge umsichtig vor, und vermeiden Sie Zirkelbezüge.

## <a name="canimationcontrollerenableanimationmanagerevent"></a><a name="enableanimationmanagerevent"></a>CAnimationController::EnableAnimationManagerEvent

Legt einen Handler fest oder gibt er frei, wenn sich der Status des Animations-Managers ändert.

```
virtual BOOL EnableAnimationManagerEvent(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
Gibt an, ob ein Handler festgelegt oder freigegeben werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Handler erfolgreich festgelegt oder freigegeben wurde.

### <a name="remarks"></a>Bemerkungen

Wenn ein Handler festgelegt (aktiviert) ist, ruft Windows Animation OnAnimationManagerStatusChanged auf, wenn sich der Status des Animations-Managers ändert.

## <a name="canimationcontrollerenableanimationtimereventhandler"></a><a name="enableanimationtimereventhandler"></a>CAnimationController::EnableAnimationTimerEventHandler

Legt einen Handler für Timingereignisse fest oder gibt er frei.

```
virtual BOOL EnableAnimationTimerEventHandler(
    BOOL bEnable = TRUE,
    UI_ANIMATION_IDLE_BEHAVIOR idleBehavior = UI_ANIMATION_IDLE_BEHAVIOR_DISABLE);
```

### <a name="parameters"></a>Parameter

*bEnable*<br/>
Gibt an, ob die Handler festgelegt oder freigegeben werden sollen.

*idleBehavior*<br/>
Gibt das Leerlaufverhalten für den Timeraktualisierungshandler an.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn Handler erfolgreich festgelegt oder freigegeben wurden; FALSE, wenn diese Methode ein zweites Mal aufgerufen wird, ohne die Handler zuerst freizugeben, oder wenn ein anderer Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Wenn die Handler festgelegt (aktiviert) sind, ruft die Windows-Animations-API OnAnimationTimerPreUpdate, OnAnimationTimerPostUpdate, OnRenderingTooSlow-Methoden auf. Sie müssen Animationstimer aktivieren, um Storyboards für Windows-Animations-API-Aktualisierungen zu ermöglichen. Andernfalls müssen Sie CAnimationController::UpdateAnimationManager aufrufen, um den Animations-Manager anzuweisen, die Werte aller Animationsvariablen zu aktualisieren.

## <a name="canimationcontrollerenableprioritycomparisonhandler"></a><a name="enableprioritycomparisonhandler"></a>CAnimationController::EnablePriorityComparisonHandler

Legt den zum Aufruf aufrufenden Prioritätsvergleichshandler fest oder gibt ihn frei, um zu bestimmen, ob ein geplantes Storyboard abgebrochen, abgeschlossen, getrimmt oder komprimiert werden kann.

```
virtual BOOL EnablePriorityComparisonHandler(DWORD dwHandlerType);
```

### <a name="parameters"></a>Parameter

*dwHandlerType*<br/>
Eine Kombination aus UI_ANIMATION_PHT_ Flags (siehe Anmerkungen), die angibt, welche Handler festgelegt oder freigegeben werden sollen.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Handler erfolgreich festgelegt oder freigegeben wurde.

### <a name="remarks"></a>Bemerkungen

Wenn ein Handler festgelegt (aktiviert) ist, ruft Windows Animation die folgenden virtuellen Methoden auf, abhängig von dwHandlerType: OnHasPriorityCancel, OnHasPriorityConclude, OnHasPriorityTrim, OnHasPriorityCompress. dwHandler kann eine Kombination der folgenden Flags sein: UI_ANIMATION_PHT_NONE - alle Handler UI_ANIMATION_PHT_CANCEL freigeben - Cancel-Vergleichshandler UI_ANIMATION_PHT_CONCLUDE setzen - Schlussvergleichshandler UI_ANIMATION_PHT_COMPRESS setzen - Komprimieren-Vergleichshandler UI_ANIMATION_PHT_TRIM setzen - Trim-Vergleichshandler UI_ANIMATION_PHT_CANCEL_REMOVE setzen - Abbruch-Vergleichshandler entfernen UI_ANIMATION_PHT_CONCLUDE_REMOVE entfernen - Schließen Vergleichshandler entfernen UI_ANIMATION_PHT_COMPRESS_REMOVE - Compress-Vergleichshandler entfernen UI_ANIMATION_PHT_TRIM_REMOVE - Trim-Vergleichshandler entfernen

## <a name="canimationcontrollerenablestoryboardeventhandler"></a><a name="enablestoryboardeventhandler"></a>CAnimationController::EnableStoryboardEventHandler

Legt einen Handler für Storyboardstatus und Aktualisierungsereignisse fest oder gibt ihn frei.

```
virtual BOOL EnableStoryboardEventHandler(
    UINT32 nGroupID,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt die Gruppen-ID an.

*bEnable*<br/>
Gibt an, ob ein Handler festgelegt oder freigegeben werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Handler erfolgreich festgelegt oder freigegeben wurde; FALSE, wenn die angegebene Animationsgruppe jetzt gefunden wird oder die Animation für die angegebene Gruppe nicht initiiert wurde und ihr internes Storyboard NULL ist.

### <a name="remarks"></a>Bemerkungen

Wenn ein Handler festgelegt (aktiviert) ist, ruft die Windows-Animations-API OnStoryboardStatusChanges und OnStoryboardUpdated virtuelle Methoden auf. Ein Handler muss festgelegt werden, nachdem CAnimationController::Animate für die angegebene Animationsgruppe aufgerufen wurde, da er ein gekapseltes IUIAnimationStoryboard-Objekt erstellt.

## <a name="canimationcontrollerfindanimationgroup"></a><a name="findanimationgroup"></a>CAnimationController::FindAnimationGroup

Sucht eine Animationsgruppe anhand ihrer Gruppen-ID.

```
CAnimationGroup* FindAnimationGroup(UINT32 nGroupID);
CAnimationGroup* FindAnimationGroup(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt eine GroupID an.

*pStoryboard*<br/>
Ein Zeiger auf ein Storyboard.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf Animationsgruppe oder NULL, wenn die Gruppe mit der angegebenen ID nicht gefunden wird.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um eine Animationsgruppe zur Laufzeit zu suchen. Eine Gruppe wird erstellt und der internen Liste der Animationsgruppen hinzugefügt, wenn ein erstes Animationsobjekt mit einer bestimmten GroupID zum Animationscontroller hinzugefügt wird.

## <a name="canimationcontrollerfindanimationobject"></a><a name="findanimationobject"></a>CAnimationController::FindAnimationObject

Sucht Animationsobjekt, das eine angegebene Animationsvariable enthält.

```
BOOL FindAnimationObject(
    IUIAnimationVariable* pVariable,
    CAnimationBaseObject** ppObject,
    CAnimationGroup** ppGroup);
```

### <a name="parameters"></a>Parameter

*pVariable*<br/>
Ein Zeiger auf die Animationsvariable.

*ppObject*<br/>
Ausgabe Enthält einen Zeiger auf animationsobjekt oder NULL.

*ppGroup*<br/>
Ausgabe Enthält einen Zeiger auf eine Animationsgruppe, die das Animationsobjekt enthält, oder NULL.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn ein Objekt gefunden wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wird von Ereignishandlern aufgerufen, wenn ein Animationsobjekt aus der eingehenden Animationsvariablen gefunden werden muss.

## <a name="canimationcontrollergkeyframestoryboardstart"></a><a name="g_keyframestoryboardstart"></a>CAnimationController::gkeyframeStoryboardStart

Ein Keyframe, der den Anfang des Storyboards darstellt.

```
static CBaseKeyFrame gkeyframeStoryboardStart;
```

## <a name="canimationcontrollergetkeyframestoryboardstart"></a><a name="getkeyframestoryboardstart"></a>CAnimationController::GetKeyframeStoryboardStart

Gibt einen Keyframe zurück, der den Start des Storyboards identifiziert.

```
static CBaseKeyFrame* GetKeyframeStoryboardStart();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf den Basis-Keyframe, der den Start des Storyboards identifiziert.

### <a name="remarks"></a>Bemerkungen

Erhalten Sie dieses Keyframe, um andere Keyframes oder Übergänge auf dem Zeitpunkt zu basieren, zu dem ein Storyboard beginnt.

## <a name="canimationcontrollergetuianimationmanager"></a><a name="getuianimationmanager"></a>CAnimationController::GetUIAnimationManager

Bietet Zugriff auf gekapselte IUIAnimationManager-Objekte.

```
IUIAnimationManager* GetUIAnimationManager();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf IUIAnimationManager-Schnittstelle oder NULL, wenn die Erstellung des Animations-Managers fehlgeschlagen ist.

### <a name="remarks"></a>Bemerkungen

Wenn das aktuelle Betriebssystem die Windows-Animations-API nicht unterstützt, gibt diese Methode NULL zurück, und danach geben alle nachfolgenden Aufrufe auf CAnimationController::IsValid FALSE zurück. Möglicherweise müssen Sie auf IUIAnimationManager zugreifen, um seine Schnittstellenmethoden aufzurufen, die nicht vom Animationscontroller umschlossen werden.

## <a name="canimationcontrollergetuianimationtimer"></a><a name="getuianimationtimer"></a>CAnimationController::GetUIAnimationTimer

Bietet Zugriff auf gekapselte IUIAnimationTimer-Objekte.

```
IUIAnimationTimer* GetUIAnimationTimer();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die IUIAnimationTimer-Schnittstelle oder NULL, wenn die Erstellung des Animationszeitgebers fehlgeschlagen ist.

### <a name="remarks"></a>Bemerkungen

Wenn das aktuelle Betriebssystem die Windows-Animations-API nicht unterstützt, gibt diese Methode NULL zurück, und danach geben alle nachfolgenden Aufrufe auf CAnimationController::IsValid FALSE zurück.

## <a name="canimationcontrollergetuitransitionfactory"></a><a name="getuitransitionfactory"></a>CAnimationController::GetUITransitionFactory

Ein Zeiger auf die IUIAnimationTransitionFactory-Schnittstelle oder NULL, wenn die Erstellung der Übergangsbibliothek fehlgeschlagen ist.

```
IUIAnimationTransitionFactory* GetUITransitionFactory();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf IUIAnimationTransitionFactory oder NULL, wenn die Erstellung der Transition Factory fehlgeschlagen ist.

### <a name="remarks"></a>Bemerkungen

Wenn das aktuelle Betriebssystem die Windows-Animations-API nicht unterstützt, gibt diese Methode NULL zurück, und danach geben alle nachfolgenden Aufrufe auf CAnimationController::IsValid FALSE zurück.

## <a name="canimationcontrollergetuitransitionlibrary"></a><a name="getuitransitionlibrary"></a>CAnimationController::GetUITransitionLibrary

Bietet Zugriff auf gekapselte IUIAnimationTransitionLibrary-Objekte.

```
IUIAnimationTransitionLibrary* GetUITransitionLibrary();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf die IUIAnimationTransitionLibrary-Schnittstelle oder NULL, wenn die Erstellung der Übergangsbibliothek fehlgeschlagen ist.

### <a name="remarks"></a>Bemerkungen

Wenn das aktuelle Betriebssystem die Windows-Animations-API nicht unterstützt, gibt diese Methode NULL zurück, und danach geben alle nachfolgenden Aufrufe auf CAnimationController::IsValid FALSE zurück.

## <a name="canimationcontrollerisanimationinprogress"></a><a name="isanimationinprogress"></a>CAnimationController::IsAnimationInProgress

Gibt an, ob mindestens eine Gruppe Animationen abspielt.

```
virtual BOOL IsAnimationInProgress();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn eine Animation für diesen Animationscontroller ausgeführt wird; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Überprüft den Status des Animations-Managers und gibt TRUE zurück, wenn der Status UI_ANIMATION_MANAGER_BUSY ist.

## <a name="canimationcontrollerisvalid"></a><a name="isvalid"></a>CAnimationController::IsValid

Gibt an, ob der Animationscontroller gültig ist.

```
BOOL IsValid() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Animationscontroller gültig ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt FALSE nur zurück, wenn die Windows-Animations-API auf dem aktuellen Betriebssystem nicht unterstützt wird und die Erstellung des Animations-Managers fehlgeschlagen ist, da sie nicht registriert ist. Sie müssen GetUIAnimationManager mindestens einmal nach der Initialisierung von COM-Bibliotheken aufrufen, um die Einstellung dieses Flags zu verursachen.

## <a name="canimationcontrollerm_bisvalid"></a><a name="m_bisvalid"></a>CAnimationController::m_bIsValid

Gibt an, ob ein Animationscontroller gültig ist oder nicht. Dieses Mitglied ist auf FALSE festgelegt, wenn das aktuelle Betriebssystem die Windows-Animations-API nicht unterstützt.

```
BOOL m_bIsValid;
```

## <a name="canimationcontrollerm_lstanimationgroups"></a><a name="m_lstanimationgroups"></a>CAnimationController::m_lstAnimationGroups

Eine Liste der Animationsgruppen, die zu diesem Animationscontroller gehören.

```
CList<CAnimationGroup*, CAnimationGroup*> m_lstAnimationGroups;
```

## <a name="canimationcontrollerm_panimationmanager"></a><a name="m_panimationmanager"></a>CAnimationController::m_pAnimationManager

Speichert einen Zeiger auf das Animations-Manager-COM-Objekt.

```
ATL::CComPtr<IUIAnimationManager> m_pAnimationManager;
```

## <a name="canimationcontrollerm_panimationtimer"></a><a name="m_panimationtimer"></a>CAnimationController::m_pAnimationTimer

Speichert einen Zeiger auf das Animationstimer-COM-Objekt.

```
ATL::CComPtr<IUIAnimationTimer> m_pAnimationTimer;
```

## <a name="canimationcontrollerm_prelatedwnd"></a><a name="m_prelatedwnd"></a>CAnimationController::m_pRelatedWnd

Ein Zeiger auf ein verwandtes CWnd-Objekt, das automatisch neu gezeichnet werden kann, wenn sich der Status des Animations-Managers geändert hat oder ein Ereignis nach der Aktualisierung aufgetreten ist. Kann den Wert NULL haben.

```
CWnd* m_pRelatedWnd;
```

## <a name="canimationcontrollerm_ptransitionfactory"></a><a name="m_ptransitionfactory"></a>CAnimationController::m_pTransitionFactory

Speichert einen Zeiger auf das Transition Factory COM-Objekt.

```
ATL::CComPtr<IUIAnimationTransitionFactory> m_pTransitionFactory;
```

## <a name="canimationcontrollerm_ptransitionlibrary"></a><a name="m_ptransitionlibrary"></a>CAnimationController::m_pTransitionLibrary

Speichert einen Zeiger auf das COM-Objekt der Übergangsbibliothek.

```
ATL::CComPtr<IUIAnimationTransitionLibrary> m_pTransitionLibrary;
```

## <a name="canimationcontrolleronafterschedule"></a><a name="onafterschedule"></a>CAnimationController::OnAfterSchedule

Wird vom Framework aufgerufen, wenn gerade eine Animation für die angegebene Gruppe geplant wurde.

```
virtual void OnAfterSchedule(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parameter

*pGruppe*<br/>
Ein Zeiger auf eine Animationsgruppe, die geplant wurde.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung entfernt Keyframes aus der angegebenen Gruppe und Übergänge aus Animationsvariablen, die zur angegebenen Gruppe gehören. Kann in einer abgeleiteten Klasse überschrieben werden, um zusätzliche Aktionen nach Animationszeitplan auszuführen.

## <a name="canimationcontrolleronanimationintegervaluechanged"></a><a name="onanimationintegervaluechanged"></a>CAnimationController::OnAnimationIntegerValueChanged

Wird vom Framework aufgerufen, wenn sich der Ganzzahlwert der Animationsvariablen geändert hat.

```
virtual void OnAnimationIntegerValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    INT32 newValue,
    INT32 prevValue);
```

### <a name="parameters"></a>Parameter

*pGruppe*<br/>
Ein Zeiger auf eine Animationsgruppe, die ein Animationsobjekt enthält, dessen Wert sich geändert hat.

*pObject*<br/>
Ein Zeiger auf ein Animationsobjekt, das eine Animationsvariable enthält, deren Wert sich geändert hat.

*Variable*<br/>
Ein Zeiger auf eine Animationsvariable.

*newValue*<br/>
Gibt einen neuen Wert an.

*prevValue*<br/>
Gibt den vorherigen Wert an.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, wenn Sie Animationsvariablenereignisse mit EnableIntegerValueChangedEvent aktivieren, das für eine bestimmte Animationsvariable oder ein bestimmtes Animationsobjekt aufgerufen wird. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden.

## <a name="canimationcontrolleronanimationmanagerstatuschanged"></a><a name="onanimationmanagerstatuschanged"></a>CAnimationController::OnAnimationManagerStatusGeändert

Wird vom Framework als Reaktion auf das StatusChanged-Ereignis vom Animations-Manager aufgerufen.

```
virtual void OnAnimationManagerStatusChanged(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Parameter

*newStatus*<br/>
Neuer Animations-Manager-Status.

*previousStatus*<br/>
Vorheriger Animations-Manager-Status.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, wenn Sie Animations-Manager-Ereignisse mit EnableAnimationManagerEvent aktivieren. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden. Die Standardimplementierung aktualisiert ein zugehöriges Fenster, wenn es mit SetRelatedWnd festgelegt wurde.

## <a name="canimationcontrolleronanimationtimerpostupdate"></a><a name="onanimationtimerpostupdate"></a>CanimationController::OnAnimationTimerpostUpdate

Wird vom Framework aufgerufen, nachdem eine Animationsaktualisierung abgeschlossen wurde.

```
virtual void OnAnimationTimerPostUpdate();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, wenn Sie Timerereignishandler mit EnableAnimationTimerEventHandler aktivieren. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden.

## <a name="canimationcontrolleronanimationtimerpreupdate"></a><a name="onanimationtimerpreupdate"></a>CanimationController::OnAnimationTimerPreupdate

Wird vom Framework aufgerufen, bevor eine Animationsaktualisierung beginnt.

```
virtual void OnAnimationTimerPreUpdate();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, wenn Sie Timerereignishandler mit EnableAnimationTimerEventHandler aktivieren. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden.

## <a name="canimationcontrolleronanimationtimerrenderingtooslow"></a><a name="onanimationtimerrenderingtooslow"></a>CanimationController::OnAnimationTimerRenderingTooSlow

Wird vom Framework aufgerufen, wenn die Renderbildrate für eine Animation unter eine wünschenswerte Mindestbildrate fällt.

```
virtual void OnAnimationTimerRenderingTooSlow(UINT32 fps);
```

### <a name="parameters"></a>Parameter

*Fps*<br/>
Die aktuelle Bildrate in Frames pro Sekunde.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, wenn Sie Timerereignishandler mit EnableAnimationTimerEventHandler aktivieren. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden. Die minimale wünschenswerte Bildrate wird durch Aufrufen von IUIAnimationTimer::SetFrameRateThreshold angegeben.

## <a name="canimationcontrolleronanimationvaluechanged"></a><a name="onanimationvaluechanged"></a>CAnimationController::OnAnimationValueChanged

Wird vom Framework aufgerufen, wenn sich der Wert der Animationsvariablen geändert hat.

```
virtual void OnAnimationValueChanged(
    CAnimationGroup* pGroup,
    CAnimationBaseObject* pObject,
    IUIAnimationVariable* variable,
    DOUBLE newValue,
    DOUBLE prevValue);
```

### <a name="parameters"></a>Parameter

*pGruppe*<br/>
Ein Zeiger auf eine Animationsgruppe, die ein Animationsobjekt enthält, dessen Wert sich geändert hat.

*pObject*<br/>
Ein Zeiger auf ein Animationsobjekt, das eine Animationsvariable enthält, deren Wert sich geändert hat.

*Variable*<br/>
Ein Zeiger auf eine Animationsvariable.

*newValue*<br/>
Gibt einen neuen Wert an.

*prevValue*<br/>
Gibt den vorherigen Wert an.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, wenn Sie Animationsvariablenereignisse mit EnableValueChangedEvent aktivieren, das für eine bestimmte Animationsvariable oder ein bestimmtes Animationsobjekt aufgerufen wird. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden.

## <a name="canimationcontrolleronbeforeanimationstart"></a><a name="onbeforeanimationstart"></a>CanimationController::OnBeforeAnimationStart

Wird vom Framework direkt vor dem Geplanter der Animation aufgerufen.

```
virtual void OnBeforeAnimationStart(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parameter

*pGruppe*<br/>
Ein Zeiger auf eine Animationsgruppe, deren Animation kurz vor dem Start steht.

### <a name="remarks"></a>Bemerkungen

Dieser Aufruf wird an verwandte CWnd weitergeleitet und kann in einer abgeleiteten Klasse überschrieben werden, um zusätzliche Aktionen auszuführen, bevor die Animation für die angegebene Gruppe gestartet wird.

## <a name="canimationcontrolleronhasprioritycancel"></a><a name="onhasprioritycancel"></a>CanimationController::OnHasPrioritycancel

Wird vom Framework aufgerufen, um Konflikte bei der Planung zu beheben.

```
virtual BOOL OnHasPriorityCancel(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parameter

*pGroupScheduled*<br/>
Die Gruppe, die das aktuell geplante Storyboard besitzt.

*pGroupNeu*<br/>
Die Gruppe, die das neue Storyboard besitzt, für das ein Planungskonflikt mit dem geplanten Storyboard im Besitz von pGroupScheduled besteht.

*priorityEffect*<br/>
Die möglichen Auswirkungen auf pGroupNew, wenn pGroupScheduled eine höhere Priorität hat.

### <a name="return-value"></a>Rückgabewert

Muss „true“ zurückgeben, wenn das Storyboard im Besitz von pGroupNew Priorität hat. Muss „false“ zurückgeben, wenn das Storyboard im Besitz von pGroupScheduled Priorität hat.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, wenn Sie Prioritätsvergleichsereignisse mit CAnimationController::EnablePriorityComparisonHandler aktivieren und UI_ANIMATION_PHT_CANCEL angeben. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden. Weitere Informationen zur [Konfliktverwaltung](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)finden Sie in der Dokumentation zur Windows Animation API .

## <a name="canimationcontrolleronhasprioritycompress"></a><a name="onhasprioritycompress"></a>CAnimationController::OnHasPriorityCompress

Wird vom Framework aufgerufen, um Konflikte bei der Planung zu beheben.

```
virtual BOOL OnHasPriorityCompress(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parameter

*pGroupScheduled*<br/>
Die Gruppe, die das aktuell geplante Storyboard besitzt.

*pGroupNeu*<br/>
Die Gruppe, die das neue Storyboard besitzt, für das ein Planungskonflikt mit dem geplanten Storyboard im Besitz von pGroupScheduled besteht.

*priorityEffect*<br/>
Die möglichen Auswirkungen auf pGroupNew, wenn pGroupScheduled eine höhere Priorität hat.

### <a name="return-value"></a>Rückgabewert

Muss „true“ zurückgeben, wenn das Storyboard im Besitz von pGroupNew Priorität hat. Muss „false“ zurückgeben, wenn das Storyboard im Besitz von pGroupScheduled Priorität hat.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, wenn Sie Prioritätsvergleichsereignisse mit CAnimationController::EnablePriorityComparisonHandler aktivieren und UI_ANIMATION_PHT_TRIM angeben. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden. Weitere Informationen zur [Konfliktverwaltung](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)finden Sie in der Dokumentation zur Windows Animation API .

## <a name="canimationcontrolleronhaspriorityconclude"></a><a name="onhaspriorityconclude"></a>CanimationController::OnHasPriorityConclude

Wird vom Framework aufgerufen, um Konflikte bei der Planung zu beheben.

```
virtual BOOL OnHasPriorityConclude(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parameter

*pGroupScheduled*<br/>
Die Gruppe, die das aktuell geplante Storyboard besitzt.

*pGroupNeu*<br/>
Die Gruppe, die das neue Storyboard besitzt, für das ein Planungskonflikt mit dem geplanten Storyboard im Besitz von pGroupScheduled besteht.

*priorityEffect*<br/>
Die möglichen Auswirkungen auf pGroupNew, wenn pGroupScheduled eine höhere Priorität hat.

### <a name="return-value"></a>Rückgabewert

Muss „true“ zurückgeben, wenn das Storyboard im Besitz von pGroupNew Priorität hat. Muss „false“ zurückgeben, wenn das Storyboard im Besitz von pGroupScheduled Priorität hat.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, wenn Sie Prioritätsvergleichsereignisse mit CAnimationController::EnablePriorityComparisonHandler aktivieren und UI_ANIMATION_PHT_CONCLUDE angeben. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden. Weitere Informationen zur [Konfliktverwaltung](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)finden Sie in der Dokumentation zur Windows Animation API .

## <a name="canimationcontrolleronhasprioritytrim"></a><a name="onhasprioritytrim"></a>CanimationController::OnHasPriorityTrim

Wird vom Framework aufgerufen, um Konflikte bei der Planung zu beheben.

```
virtual BOOL OnHasPriorityTrim(
    CAnimationGroup* pGroupScheduled,
    CAnimationGroup* pGroupNew,
    UI_ANIMATION_PRIORITY_EFFECT priorityEffect);
```

### <a name="parameters"></a>Parameter

*pGroupScheduled*<br/>
Die Gruppe, die das aktuell geplante Storyboard besitzt.

*pGroupNeu*<br/>
Die Gruppe, die das neue Storyboard besitzt, für das ein Planungskonflikt mit dem geplanten Storyboard im Besitz von pGroupScheduled besteht.

*priorityEffect*<br/>
Die möglichen Auswirkungen auf pGroupNew, wenn pGroupScheduled eine höhere Priorität hat.

### <a name="return-value"></a>Rückgabewert

Muss „true“ zurückgeben, wenn das Storyboard im Besitz von pGroupNew Priorität hat. Muss „false“ zurückgeben, wenn das Storyboard im Besitz von pGroupScheduled Priorität hat.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, wenn Sie Prioritätsvergleichsereignisse mit CAnimationController::EnablePriorityComparisonHandler aktivieren und UI_ANIMATION_PHT_TRIM angeben. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden. Weitere Informationen zur [Konfliktverwaltung](/windows/win32/api/uianimation/nf-uianimation-iuianimationprioritycomparison-haspriority)finden Sie in der Dokumentation zur Windows Animation API .

## <a name="canimationcontrolleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a>CAnimationController::OnStoryboardStatusStatusChanged

Wird vom Framework aufgerufen, wenn sich der Storyboardstatus geändert hat.

```
virtual void OnStoryboardStatusChanged(
    CAnimationGroup* pGroup,
    UI_ANIMATION_STORYBOARD_STATUS newStatus,
    UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Parameter

*pGruppe*<br/>
Ein Zeiger auf eine Animationsgruppe, der das Storyboard gehört, dessen Status sich geändert hat.

*newStatus*<br/>
Gibt den neuen Status an.

*previousStatus*<br/>
Gibt den vorherigen Status an.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, wenn Sie Storyboard-Ereignisse mit CAnimationController::EnableStoryboardEventHandler aktivieren. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden.

## <a name="canimationcontrolleronstoryboardupdated"></a><a name="onstoryboardupdated"></a>CAnimationController::OnStoryboardAktualisiert

Wird vom Framework aufgerufen, wenn das Storyboard aktualisiert wurde.

```
virtual void OnStoryboardUpdated(CAnimationGroup* pGroup);
```

### <a name="parameters"></a>Parameter

*pGruppe*<br/>
Ein Zeiger auf eine Gruppe, der das Storyboard gehört.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, wenn Sie Storyboard-Ereignisse mit CAnimationController::EnableStoryboardEventHandler aktivieren. Sie kann in einer abgeleiteten Klasse überschrieben werden, um anwendungsspezifische Aktionen zu verwenden.

## <a name="canimationcontrollerremoveallanimationgroups"></a><a name="removeallanimationgroups"></a>CAnimationController::RemoveAllAnimationGroups

Entfernt alle Animationsgruppen aus dem Animationscontroller.

```cpp
void RemoveAllAnimationGroups();
```

### <a name="remarks"></a>Bemerkungen

Alle Gruppen werden gelöscht, ihr Zeiger, wenn er auf Anwendungsebene gespeichert wird, muss ungültig werden. Wenn CAnimationGroup::m_bAutodestroyAnimationObjects für eine gelöschte Gruppe TRUE ist, werden alle Animationsobjekte, die zu dieser Gruppe gehören, gelöscht. Andernfalls werden ihre Verweise auf den übergeordneten Animationscontroller auf NULL gesetzt und können einem anderen Controller hinzugefügt werden.

## <a name="canimationcontrollerremoveanimationgroup"></a><a name="removeanimationgroup"></a>CAnimationController::RemoveAnimationGroup

Entfernt eine Animationsgruppe mit der angegebenen ID aus dem Animationscontroller.

```cpp
void RemoveAnimationGroup(UINT32 nGroupID);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt die Animationsgruppen-ID an.

### <a name="remarks"></a>Bemerkungen

Diese Methode entfernt eine Animationsgruppe aus der internen Liste von Gruppen und löscht sie, daher muss, wenn Sie einen Zeiger auf diese Animationsgruppe gespeichert haben, ungültig werden. Wenn CAnimationGroup::m_bAutodestroyAnimationObjects TRUE ist, werden alle Animationsobjekte, die zu dieser Gruppe gehören, gelöscht. Andernfalls werden ihre Verweise auf den übergeordneten Animationscontroller auf NULL gesetzt und können einem anderen Controller hinzugefügt werden.

## <a name="canimationcontrollerremoveanimationobject"></a><a name="removeanimationobject"></a>CAnimationController::RemoveAnimationObject

Entfernen Sie ein Animationsobjekt aus dem Animationscontroller.

```cpp
void RemoveAnimationObject(
    CAnimationBaseObject* pObject,
    BOOL bNoDelete = FALSE);
```

### <a name="parameters"></a>Parameter

*pObject*<br/>
Ein Zeiger auf ein Animationsobjekt.

*bNoDelete*<br/>
Wenn dieser Parameter TRUE ist, wird das Objekt beim Entfernen nicht gelöscht.

### <a name="remarks"></a>Bemerkungen

Entfernt ein Animationsobjekt aus dem Animationscontroller und der Animationsgruppe. Rufen Sie diese Funktion auf, wenn ein bestimmtes Objekt nicht mehr animiert werden soll oder wenn Sie das Objekt auf einen anderen Animationscontroller verschieben müssen. Im letzten Fall muss bNoDelete TRUE sein.

## <a name="canimationcontrollerremovetransitions"></a><a name="removetransitions"></a>CAnimationController::EntfernenÜbergänge

Entfernt Übergänge aus Animationsobjekten, die zur angegebenen Gruppe gehören.

```cpp
void RemoveTransitions(UINT32 nGroupID);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt die Gruppen-ID an.

### <a name="remarks"></a>Bemerkungen

Die Gruppe überläuft ihre Animationsobjekte und ruft ClearTransitions(FALSE) für jedes Animationsobjekt auf. Diese Methode wird vom Framework aufgerufen, nachdem die Animation geplant wurde.

## <a name="canimationcontrollerschedulegroup"></a><a name="schedulegroup"></a>CAnimationController::ScheduleGroup

Plant eine Animation.

```
BOOL ScheduleGroup(
    UINT32 nGroupID,
    UI_ANIMATION_SECONDS time = 0.0);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt die Animationsgruppen-ID zum Planen an.

*time*<br/>
Gibt die Zeit zum Planen an.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Animation erfolgreich geplant wurde. FALSE, wenn kein Storyboard erstellt wurde oder ein anderer Fehler auftritt.

### <a name="remarks"></a>Bemerkungen

Sie müssen AnimateGroup aufrufen, wobei der Parameter bScheduleNow auf FALSE before ScheduleGroup festgelegt ist. Sie können die gewünschte Animationszeit angeben, die von IUIAnimationTimer::GetTime abgerufen wird. Wenn der Zeitparameter 0,0 ist, wird die Animation für die aktuelle Zeit geplant.

## <a name="canimationcontrollersetrelatedwnd"></a><a name="setrelatedwnd"></a>CAnimationController::SetRelatedWnd

Stellt eine Beziehung zwischen dem Animationscontroller und einem Fenster her.

```cpp
void SetRelatedWnd(CWnd* pWnd);
```

### <a name="parameters"></a>Parameter

*pWnd*<br/>
Ein Zeiger auf ein zu setzendes Fensterobjekt.

### <a name="remarks"></a>Bemerkungen

Wenn ein verwandtes CWnd-Objekt festgelegt ist, kann der Animationscontroller es automatisch aktualisieren (WM_PAINT Nachricht senden), wenn sich der Status des Animations-Managers geändert hat oder ein Timer nach der Aktualisierung aufgetreten ist.

## <a name="canimationcontrollerupdateanimationmanager"></a><a name="updateanimationmanager"></a>CAnimationController::UpdateAnimationManager

Weist den Animations-Manager an, die Werte aller Animationsvariablen zu aktualisieren.

```
virtual void UpdateAnimationManager();
```

### <a name="remarks"></a>Bemerkungen

Durch aufrufende Methoden wird der Animations-Manager zur aktuellen Zeit gebracht, der Status von Storyboards bei Bedarf geändert und alle Animationsvariablen auf entsprechende interpolierte Werte aktualisiert. Intern ruft diese Methode IUIAnimationTimer::GetTime(timeNow) und IUIAnimationManager::Update(timeNow) auf. Überschreiben Sie diese Methode in einer abgeleiteten Klasse, um dieses Verhalten anzupassen.

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)

---
title: CAnimationBaseObject-Klasse
ms.date: 03/27/2019
f1_keywords:
- CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ContainsVariable
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::DetachFromController
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetParentAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_dwUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_pParentController
helpviewer_keywords:
- CAnimationBaseObject [MFC], CAnimationBaseObject
- CAnimationBaseObject [MFC], ApplyTransitions
- CAnimationBaseObject [MFC], ClearTransitions
- CAnimationBaseObject [MFC], ContainsVariable
- CAnimationBaseObject [MFC], CreateTransitions
- CAnimationBaseObject [MFC], DetachFromController
- CAnimationBaseObject [MFC], EnableIntegerValueChangedEvent
- CAnimationBaseObject [MFC], EnableValueChangedEvent
- CAnimationBaseObject [MFC], GetAutodestroyTransitions
- CAnimationBaseObject [MFC], GetGroupID
- CAnimationBaseObject [MFC], GetObjectID
- CAnimationBaseObject [MFC], GetUserData
- CAnimationBaseObject [MFC], SetAutodestroyTransitions
- CAnimationBaseObject [MFC], SetID
- CAnimationBaseObject [MFC], SetUserData
- CAnimationBaseObject [MFC], GetAnimationVariableList
- CAnimationBaseObject [MFC], SetParentAnimationObjects
- CAnimationBaseObject [MFC], m_bAutodestroyTransitions
- CAnimationBaseObject [MFC], m_dwUserData
- CAnimationBaseObject [MFC], m_nGroupID
- CAnimationBaseObject [MFC], m_nObjectID
- CAnimationBaseObject [MFC], m_pParentController
ms.assetid: 76b25917-940e-4eba-940f-31d270702603
ms.openlocfilehash: 1874ddfdd26b8dd371e32f7e68ea8f668c47d8e1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750225"
---
# <a name="canimationbaseobject-class"></a>CAnimationBaseObject-Klasse

Die Basisklasse für alle Animationsobjekte.

## <a name="syntax"></a>Syntax

```
class CAnimationBaseObject : public CObject;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationBaseObject::CAnimationBaseObject](#canimationbaseobject)|Ist überladen. Erstellt ein Animationsobjekt.|
|[CAnimationBaseObject::'canimationBaseObject](#_dtorcanimationbaseobject)|Der Destruktor. Wird aufgerufen, wenn ein Animationsobjekt zerstört wird.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationBaseObject::ApplyÜbergänge](#applytransitions)|Fügt Übergänge zum Storyboard mit gekapselter Animationsvariable hinzu.|
|[CAnimationBaseObject::ClearTransitions](#cleartransitions)|Entfernt alle zugehörigen Übergänge.|
|[CAnimationBaseObject::EnthältVariable](#containsvariable)|Bestimmt, ob ein Animationsobjekt eine bestimmte Animationsvariable enthält.|
|[CAnimationBaseObject::CreateTransitions](#createtransitions)|Erstellt Übergänge, die einem Animationsobjekt zugeordnet sind.|
|[CAnimationBaseObject::DetachFromController](#detachfromcontroller)|Trennt ein Animationsobjekt vom übergeordneten Animationscontroller.|
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Richtet den Ereignishandler Integer Value Changed ein.|
|[CAnimationBaseObject::EnableValueChangedEvent](#enablevaluechangedevent)|Richtet value Changed-Ereignishandler ein.|
|[CAnimationBaseObject::GetAutodestroyTransitions](#getautodestroytransitions)|Gibt an, ob der zugehörige Übergang automatisch zerstört wird.|
|[CAnimationBaseObject::GetGroupID](#getgroupid)|Gibt die aktuelle Gruppen-ID zurück.|
|[CAnimationBaseObject::GetObjectID](#getobjectid)|Gibt die aktuelle Objekt-ID zurück.|
|[CAnimationBaseObject::GetUserData](#getuserdata)|Gibt benutzerdefinierte Daten zurück.|
|[CAnimationBaseObject::SetAutodestroyTransitions](#setautodestroytransitions)|Legt ein Flag fest, um Übergänge automatisch zu zerstören.|
|[CAnimationBaseObject::SetID](#setid)|Legt neue IDs fest.|
|[CAnimationBaseObject::SetUserData](#setuserdata)|Legt benutzerdefinierte Daten fest.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationBaseObject::GetAnimationVariableList](#getanimationvariablelist)|Sammelt Zeiger auf enthaltene Animationsvariablen.|
|[CAnimationBaseObject::SetParentAnimationObjects](#setparentanimationobjects)|Stellt eine Beziehung zwischen Animationsvariablen, die in einem Animationsobjekt enthalten sind, und ihrem Container her.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationBaseObject::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Gibt an, ob verknüpfte Übergänge automatisch zerstört werden sollen.|
|[CAnimationBaseObject::m_dwUserData](#m_dwuserdata)|Speichert benutzerdefinierte Daten.|
|[CAnimationBaseObject::m_nGroupID](#m_ngroupid)|Gibt die Gruppen-ID des Animationsobjekts an.|
|[CAnimationBaseObject::m_nObjectID](#m_nobjectid)|Gibt die Objekt-ID des Animationsobjekts an.|
|[CAnimationBaseObject::m_pParentController](#m_pparentcontroller)|Ein Zeiger auf den übergeordneten Animationscontroller.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse implementiert grundlegende Methoden für alle Animationsobjekte. Ein Animationsobjekt kann einen Wert, einen Punkt, eine Größe, ein Rechteck oder eine Farbe in einer Anwendung sowie eine beliebige benutzerdefinierte Entität darstellen. Animationsobjekte werden in Animationsgruppen gespeichert (siehe CAnimationGroup). Jede Gruppe kann separat animiert werden und kann als Analogie des Storyboards behandelt werden. Ein Animationsobjekt kapselt je nach logischer Darstellung eine oder mehrere Animationsvariablen (siehe CAnimationVariable). CAnimationRect enthält beispielsweise vier Animationsvariablen - eine Variable für jede Seite des Rechtecks. Jede Animationsobjektklasse macht die überladene AddTransition-Methode verfügbar, die zum Anwenden von Übergängen auf gekapselte Animationsvariablen verwendet werden soll. Ein Animationsobjekt kann (optional) und gruppen-ID durch Objekt-ID identifiziert werden. Eine Gruppen-ID ist erforderlich, um ein Animationsobjekt zur korrekten Gruppe zu platzieren, aber wenn keine Gruppen-ID angegeben ist, wird ein Objekt in der Standardgruppe mit der ID 0 platziert. Wenn Sie SetID mit einer anderen GroupID aufrufen, wird ein Animationsobjekt in eine andere Gruppe verschoben (bei Bedarf wird eine neue Gruppe erstellt).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CAnimationBaseObject`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxanimationcontroller.h

## <a name="canimationbaseobjectcanimationbaseobject"></a><a name="_dtorcanimationbaseobject"></a>CAnimationBaseObject::'canimationBaseObject

Der Destruktor. Wird aufgerufen, wenn ein Animationsobjekt zerstört wird.

```
virtual ~CAnimationBaseObject();
```

## <a name="canimationbaseobjectapplytransitions"></a><a name="applytransitions"></a>CAnimationBaseObject::ApplyÜbergänge

Fügt Übergänge zum Storyboard mit gekapselter Animationsvariable hinzu.

```
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parameter

*pStoryboard*<br/>
Ein Zeiger auf ein Storyboard.

*bDependOnKeyframes*<br/>
Wenn FALSE, fügt diese Methode nur die Übergänge hinzu, die nicht von Keyframes abhängen.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn Übergänge erfolgreich hinzugefügt wurden.

### <a name="remarks"></a>Bemerkungen

Fügt dem Storyboard verwandte Übergänge hinzu, die mit AddTransition (überladene Methoden in abgeleiteten Klassen) hinzugefügt wurden.

## <a name="canimationbaseobjectcanimationbaseobject"></a><a name="canimationbaseobject"></a>CAnimationBaseObject::CAnimationBaseObject

Erstellt ein Animationsobjekt.

```
CAnimationBaseObject();

CAnimationBaseObject(
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parameter

*nGroupID*<br/>
Gibt die Gruppen-ID an.

*nObjectID*<br/>
Gibt die Objekt-ID an.

*dwUserData*<br/>
Benutzerdefinierte Daten, die Animationsobjekten zugeordnet und später zur Laufzeit abgerufen werden können.

### <a name="remarks"></a>Bemerkungen

Erstellt ein Animationsobjekt und weist die Standardobjekt-ID (0) und die Gruppen-ID (0) zu.

## <a name="canimationbaseobjectcleartransitions"></a><a name="cleartransitions"></a>CAnimationBaseObject::ClearTransitions

Entfernt alle zugehörigen Übergänge.

```
virtual void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>Parameter

*bAutodestroy*<br/>
Gibt an, ob Übergangsobjekte automatisch zerstört oder einfach aus der verknüpften Liste entfernt werden sollen.

### <a name="remarks"></a>Bemerkungen

Entfernt alle zugehörigen Übergänge und zerstört sie, wenn bAutodestroy oder m_bAutodestroyTransitions Flag TRUE ist. Übergänge sollten nur dann automatisch zerstört werden, wenn sie nicht auf dem Stapel zugeordnet sind. Wenn die obigen Flags FALSE sind, werden Übergänge einfach aus der internen Liste der zugehörigen Übergänge entfernt.

## <a name="canimationbaseobjectcontainsvariable"></a><a name="containsvariable"></a>CAnimationBaseObject::EnthältVariable

Bestimmt, ob ein Animationsobjekt eine bestimmte Animationsvariable enthält.

```
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parameter

*pVariable*<br/>
Ein Zeiger auf die Animationsvariable.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Animationsvariable im Animationsobjekt enthalten ist; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode kann verwendet werden, um zu bestimmen, ob eine von pVariable angegebene Animationsvariable in einem Animationsobjekt enthalten ist. Ein Animationsobjekt kann je nach Typ mehrere Animationsvariablen enthalten. Beispielsweise enthält CAnimationColor drei Variablen, eine für jede Farbkomponente (rot, grün und blau). Wenn sich ein Wert der Animationsvariablen geändert hat, sendet die Windows-Animations-API ValueChanged- oder IntegerValueChanged-Ereignisse (falls aktiviert), und der Parameter dieses Ereignisses ist ein Zeiger auf die Schnittstelle IUIAnimationVariable der Animationsvariablen. Diese Methode hilft, einen Zeiger auf animation en from a pointer to contained COM object zu erhalten.

## <a name="canimationbaseobjectcreatetransitions"></a><a name="createtransitions"></a>CAnimationBaseObject::CreateTransitions

Erstellt Übergänge, die einem Animationsobjekt zugeordnet sind.

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn Übergänge erfolgreich erstellt wurden; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Loops über liste der Animationsvariablen, die in einem abgeleiteten Animationsobjekt gekapselt sind, und erstellt Übergänge, die jeder Animationsvariablen zugeordnet sind.

## <a name="canimationbaseobjectdetachfromcontroller"></a><a name="detachfromcontroller"></a>CAnimationBaseObject::DetachFromController

Trennt ein Animationsobjekt vom übergeordneten Animationscontroller.

```cpp
void DetachFromController();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode wird intern verwendet.

## <a name="canimationbaseobjectenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a>CAnimationBaseObject::EnableIntegerValueChangedEvent

Richtet den Ereignishandler Integer Value Changed ein.

```
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parameter

*pController*<br/>
Ein Zeiger auf einen übergeordneten Controller.

*bEnable*<br/>
Gibt an, ob das Ereignis "Integer Value Changed" aktiviert oder deaktiviert werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn der Ereignishandler "Ganzzahlwert geändert" aktiviert ist, können Sie dieses Ereignis in der CAnimationController::OnAnimationIntegerValueChanged-Methode behandeln, die in einer von CAnimationController abgeleiteten Klasse überschrieben werden soll. Diese Methode wird jedes Mal aufgerufen, wenn sich der Wert der Animationsganzzahl geändert hat.

## <a name="canimationbaseobjectenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a>CAnimationBaseObject::EnableValueChangedEvent

Richtet value Changed-Ereignishandler ein.

```
virtual void EnableValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parameter

*pController*<br/>
Ein Zeiger auf einen übergeordneten Controller.

*bEnable*<br/>
Gibt an, ob das Value Changed-Ereignis aktiviert oder deaktiviert werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn der Value Changed-Ereignishandler aktiviert ist, können Sie dieses Ereignis in der CAnimationController::OnAnimationValueChanged-Methode behandeln, die in einer von CAnimationController abgeleiteten Klasse überschrieben werden soll. Diese Methode wird jedes Mal aufgerufen, wenn sich der Animationswert geändert hat.

## <a name="canimationbaseobjectgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationBaseObject::GetAnimationVariableList

Sammelt Zeiger auf enthaltene Animationsvariablen.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& list) = 0;
```

### <a name="parameters"></a>Parameter

*list*<br/>
Eine Liste, die mit Animationsvariablen gefüllt werden muss, die in einem Animationsobjekt enthalten sind.

### <a name="remarks"></a>Bemerkungen

Diese reine virtuelle Methode muss in einer abgeleiteten Klasse überschrieben werden. Ein Animationsobjekt enthält je nach Typ eine oder mehrere Animationsvariablen. CAnimationPoint enthält beispielsweise zwei Variablen für X- und Y-Koordinaten. Die Basisklasse CAnimationBaseObject implementiert einige generische Methoden, die auf eine Liste von Animationsvariablen reagieren: ApplyTransitions, ClearTransitions, EnableValueChangedEvent, EnableIntegerValueChangedEvent. Diese Methoden rufen GetAnimationVariableList auf, die in einer abgeleiteten Klasse mit tatsächlichen Animationsvariablen gefüllt wird, die in einem bestimmten Animationsobjekt enthalten sind, und durchlaufen dann eine Schleife über die Liste und führen die erforderlichen Aktionen aus. Wenn Sie ein benutzerdefiniertes Animationsobjekt erstellen, müssen Sie alle Animationsvariablen, die in diesem Objekt enthalten sind, *auflisten.*

## <a name="canimationbaseobjectgetautodestroytransitions"></a><a name="getautodestroytransitions"></a>CAnimationBaseObject::GetAutodestroyTransitions

Gibt an, ob der zugehörige Übergang automatisch zerstört wird.

```
BOOL GetAutodestroyTransitions() const;
```

### <a name="return-value"></a>Rückgabewert

Wenn TRUE, werden verwandte Übergänge automatisch zerstört; Wenn FALSE, sollten Übergangsobjekte durch Aufrufen der Anwendung verteilt werden.

### <a name="remarks"></a>Bemerkungen

Standardmäßig ist dieses Flag TRUE. Legen Sie dieses Flag nur fest, wenn Sie den Übergang auf dem Stapel zugewiesen haben und/oder Übergänge von der aufrufenden Anwendung zugewiesen werden sollen.

## <a name="canimationbaseobjectgetgroupid"></a><a name="getgroupid"></a>CAnimationBaseObject::GetGroupID

Gibt die aktuelle Gruppen-ID zurück.

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>Rückgabewert

Aktuelle Gruppen-ID.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um die Gruppen-ID abzurufen. Es ist 0, wenn die Gruppen-ID nicht explizit im Konstruktor oder mit SetID festgelegt wurde.

## <a name="canimationbaseobjectgetobjectid"></a><a name="getobjectid"></a>CAnimationBaseObject::GetObjectID

Gibt die aktuelle Objekt-ID zurück.

```
UINT32 GetObjectID() const;
```

### <a name="return-value"></a>Rückgabewert

Aktuelle Objekt-ID.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um die Objekt-ID abzurufen. Es ist 0, wenn die Objekt-ID nicht explizit im Konstruktor oder mit SetID festgelegt wurde.

## <a name="canimationbaseobjectgetuserdata"></a><a name="getuserdata"></a>CAnimationBaseObject::GetUserData

Gibt benutzerdefinierte Daten zurück.

```
DWORD GetUserData() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert von benutzerdefinierten Daten.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die benutzerdefinierten Daten zur Laufzeit abzurufen. Der zurückgegebene Wert ist 0, wenn er nicht explizit im Konstruktor oder mit SetUserData initialisiert wurde.

## <a name="canimationbaseobjectm_bautodestroytransitions"></a><a name="m_bautodestroytransitions"></a>CAnimationBaseObject::m_bAutodestroyTransitions

Gibt an, ob verknüpfte Übergänge automatisch zerstört werden sollen.

```
BOOL m_bAutodestroyTransitions;
```

## <a name="canimationbaseobjectm_dwuserdata"></a><a name="m_dwuserdata"></a>CAnimationBaseObject::m_dwUserData

Speichert benutzerdefinierte Daten.

```
DWORD m_dwUserData;
```

## <a name="canimationbaseobjectm_ngroupid"></a><a name="m_ngroupid"></a>CAnimationBaseObject::m_nGroupID

Gibt die Gruppen-ID des Animationsobjekts an.

```
UINT32 m_nGroupID;
```

## <a name="canimationbaseobjectm_nobjectid"></a><a name="m_nobjectid"></a>CAnimationBaseObject::m_nObjectID

Gibt die Objekt-ID des Animationsobjekts an.

```
UINT32 m_nObjectID;
```

## <a name="canimationbaseobjectm_pparentcontroller"></a><a name="m_pparentcontroller"></a>CAnimationBaseObject::m_pParentController

Ein Zeiger auf den übergeordneten Animationscontroller.

```
CAnimationController* m_pParentController;
```

## <a name="canimationbaseobjectsetautodestroytransitions"></a><a name="setautodestroytransitions"></a>CAnimationBaseObject::SetAutodestroyTransitions

Legt ein Flag fest, um Übergänge automatisch zu zerstören.

```cpp
void SetAutodestroyTransitions(BOOL bValue);
```

### <a name="parameters"></a>Parameter

*bValue*<br/>
Gibt das Auto-Destroy-Flag an.

### <a name="remarks"></a>Bemerkungen

Legen Sie dieses Flag nur fest, wenn Sie Übergangsobjekte mit Operator new zugewiesen haben. Wenn aus irgendeinem Grund Übergangsobjekte auf dem Stapel zugewiesen werden, sollte das Auto-Destroy-Flag FALSE sein. Standardmäßig ist dieses Flag TRUE.

## <a name="canimationbaseobjectsetid"></a><a name="setid"></a>CAnimationBaseObject::SetID

Legt neue IDs fest.

```cpp
void SetID(
    UINT32 nObjectID,
    UINT32 nGroupID = 0);
```

### <a name="parameters"></a>Parameter

*nObjectID*<br/>
Gibt eine neue Objekt-ID an.

*nGroupID*<br/>
Gibt eine neue Gruppen-ID an.

### <a name="remarks"></a>Bemerkungen

Ermöglicht das Ändern der Objekt- und Gruppen-ID. Wenn sich die neue Gruppen-ID von der aktuellen ID unterscheidet, wird ein Animationsobjekt in eine andere Gruppe verschoben (bei Bedarf wird eine neue Gruppe erstellt).

## <a name="canimationbaseobjectsetparentanimationobjects"></a><a name="setparentanimationobjects"></a>CAnimationBaseObject::SetParentAnimationObjects

Stellt eine Beziehung zwischen Animationsvariablen, die in einem Animationsobjekt enthalten sind, und ihrem Container her.

```
virtual void SetParentAnimationObjects();
```

### <a name="remarks"></a>Bemerkungen

Dieser Helfer kann verwendet werden, um eine Beziehung zwischen Animationsvariablen, die in einem Animationsobjekt enthalten sind, und ihrem Container herzustellen. Es wird über Animationsvariablen geschleift und ein Hintergrundzeiger auf ein übergeordnetes Animationsobjekt für jede Animationsvariable festgelegt. In der aktuellen Implementierung wird die tatsächliche Beziehung in CAnimationBaseObject::ApplyTransitions eingerichtet, daher werden Back-Zeiger erst festgelegt, wenn Sie CAnimationGroup::Animate aufrufen. Das Wissen um die Beziehung kann hilfreich sein, wenn Sie Ereignisse verarbeiten und ein übergeordnetes Animationsobjekt aus CAnimationVariable abrufen müssen. Verwenden Sie cAnimationVariable::GetParentAnimationObject.

## <a name="canimationbaseobjectsetuserdata"></a><a name="setuserdata"></a>CAnimationBaseObject::SetUserData

Legt benutzerdefinierte Daten fest.

```cpp
void SetUserData (DWORD dwUserData);
```

### <a name="parameters"></a>Parameter

*dwUserData*<br/>
Gibt die benutzerdefinierten Daten an.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um einem Animationsobjekt benutzerdefinierte Daten zuzuordnen. Diese Daten können später zur Laufzeit von GetUserData abgerufen werden.

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)

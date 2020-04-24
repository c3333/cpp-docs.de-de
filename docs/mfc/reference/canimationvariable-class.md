---
title: CAnimationVariable-Klasse
ms.date: 03/27/2019
f1_keywords:
- CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationVariable::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::Create
- AFXANIMATIONCONTROLLER/CAnimationVariable::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_dblDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_lstTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_pParentObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_variable
helpviewer_keywords:
- CAnimationVariable [MFC], CAnimationVariable
- CAnimationVariable [MFC], AddTransition
- CAnimationVariable [MFC], ApplyTransitions
- CAnimationVariable [MFC], ClearTransitions
- CAnimationVariable [MFC], Create
- CAnimationVariable [MFC], CreateTransitions
- CAnimationVariable [MFC], EnableIntegerValueChangedEvent
- CAnimationVariable [MFC], EnableValueChangedEvent
- CAnimationVariable [MFC], GetDefaultValue
- CAnimationVariable [MFC], GetParentAnimationObject
- CAnimationVariable [MFC], GetValue
- CAnimationVariable [MFC], GetVariable
- CAnimationVariable [MFC], SetDefaultValue
- CAnimationVariable [MFC], SetParentAnimationObject
- CAnimationVariable [MFC], m_bAutodestroyTransitions
- CAnimationVariable [MFC], m_dblDefaultValue
- CAnimationVariable [MFC], m_lstTransitions
- CAnimationVariable [MFC], m_pParentObject
- CAnimationVariable [MFC], m_variable
ms.assetid: 506e697e-31a8-4033-a27e-292f4d7b42d9
ms.openlocfilehash: b53a1338566a329fbdf5b91c41d0411a529afe8d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755069"
---
# <a name="canimationvariable-class"></a>CAnimationVariable-Klasse

Stellt eine Animationsvariable dar.

## <a name="syntax"></a>Syntax

```
class CAnimationVariable;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationVariable::CAnimationVariable](#canimationvariable)|Erstellt ein Animationsvariablenobjekt.|
|[CAnimationVariable::'CAnimationVariable](#_dtorcanimationvariable)|Der Destruktor. Wird aufgerufen, wenn ein CAnimationVariable-Objekt zerstört wird.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationVariable::AddTransition](#addtransition)|Fügt einen Übergang hinzu.|
|[CAnimationVariable::ApplyÜbergänge](#applytransitions)|Fügt Übergänge von der internen Liste zum Storyboard hinzu.|
|[CAnimationVariable::ClearTransitions](#cleartransitions)|Löscht Übergänge.|
|[CAnimationVariable::Erstellen](#create)|Erstellt das zugrunde liegende Animationsvariable COM-Objekt.|
|[CAnimationVariable::ErstellenVonÜbergänge](#createtransitions)|Erstellt alle Übergänge, die auf diese Animationsvariable angewendet werden sollen.|
|[CAnimationVariable::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|Aktiviert oder deaktiviert das IntegerValueChanged-Ereignis.|
|[CAnimationVariable::EnableValueChangedEvent](#enablevaluechangedevent)|Aktiviert oder deaktiviert das ValueChanged-Ereignis.|
|[CAnimationVariable::GetDefaultValue](#getdefaultvalue)|Gibt den Standardwert zurück.|
|[CAnimationVariable::GetParentAnimationObject](#getparentanimationobject)|Gibt das übergeordnete Animationsobjekt zurück.|
|[CAnimationVariable::GetValue](#getvalue)|Ist überladen. Gibt den aktuellen Wert der Animationsvariablen zurück.|
|[CAnimationVariable::GetVariable](#getvariable)|Gibt einen Zeiger auf das IUIAnimationVariable COM-Objekt zurück.|
|[CAnimationVariable::SetDefaultValue](#setdefaultvalue)|Legt den Standardwert fest und gibt das IUIAnimationVariable COM-Objekt frei.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationVariable::SetParentAnimationObject](#setparentanimationobject)|Legt die Beziehung zwischen einer Animationsvariablen und einem Animationsobjekt fest.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationVariable::m_bAutodestroyTransitions](#m_bautodestroytransitions)|Gibt an, ob verwandte Übergangsobjekte gelöscht werden sollen.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationVariable::m_dblDefaultValue](#m_dbldefaultvalue)|Gibt den Standardwert an, der an IUIAnimationVariable weitergegeben wird.|
|[CAnimationVariable::m_lstTransitions](#m_lsttransitions)|Enthält eine Liste von Übergängen, die diese Animationsvariable animieren.|
|[CAnimationVariable::m_pParentObject](#m_pparentobject)|Ein Zeiger auf ein Animationsobjekt, das diese Animationsvariable kapselt.|
|[CAnimationVariable::m_variable](#m_variable)|Speichert einen Zeiger auf das IUIAnimationVariable COM-Objekt. NULL, wenn das COM-Objekt noch nicht erstellt wurde oder wenn die Erstellung fehlgeschlagen ist.|

## <a name="remarks"></a>Bemerkungen

Die CAnimationVariable-Klasse kapselt das IUIAnimationVariable COM-Objekt. Es enthält auch eine Liste von Übergängen, die auf die Animationsvariable in einem Storyboard angewendet werden sollen. CAnimationVariable-Objekte werden in Animationsobjekte eingebettet, die in einer Anwendung einen animierten Wert, Punkt, Größe, Farbe und Rechteck darstellen können.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CAnimationVariable`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxanimationcontroller.h

## <a name="canimationvariablecanimationvariable"></a><a name="_dtorcanimationvariable"></a>CAnimationVariable::'CAnimationVariable

Der Destruktor. Wird aufgerufen, wenn ein CAnimationVariable-Objekt zerstört wird.

```
virtual ~CAnimationVariable();
```

## <a name="canimationvariableaddtransition"></a><a name="addtransition"></a>CAnimationVariable::AddTransition

Fügt einen Übergang hinzu.

```cpp
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>Parameter

*pTransition*<br/>
Ein Zeiger auf einen hinzuzufügenden Übergang.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, um einen Übergang zur internen Liste der Übergänge hinzuzufügen, die auf die Animationsvariable angewendet werden sollen. Diese Liste sollte gelöscht werden, wenn eine Animation geplant wurde.

## <a name="canimationvariableapplytransitions"></a><a name="applytransitions"></a>CAnimationVariable::ApplyÜbergänge

Fügt Übergänge von der internen Liste zum Storyboard hinzu.

```cpp
void ApplyTransitions(
    CAnimationController* pController,
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>Parameter

*pController*<br/>
Ein Zeiger auf den übergeordneten Animationscontroller.

*pStoryboard*<br/>
Ein Zeiger auf das Storyboard.

*bDependOnKeyframes*<br/>
TRUE, wenn diese Methode Übergänge hinzufügen soll, die von Keyframes abhängen.

### <a name="remarks"></a>Bemerkungen

Diese Methode fügt Übergänge von der internen Liste zum Storyboard hinzu. Es wird mehrmals aus dem Code der obersten Ebene aufgerufen, um Übergänge hinzuzufügen, die nicht von Keyframes abhängen, und Übergänge hinzuzufügen, die von Keyframes abhängen. Wenn das zugrunde liegende ANIMATIONSvariable COM-Objekt nicht erstellt wurde, wird es in dieser Phase von dieser Methode erstellt.

## <a name="canimationvariablecanimationvariable"></a><a name="canimationvariable"></a>CAnimationVariable::CAnimationVariable

Erstellt ein Animationsvariablenobjekt.

```
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```

### <a name="parameters"></a>Parameter

*dblDefaultValue*<br/>
Gibt den Standardwert an.

### <a name="remarks"></a>Bemerkungen

Erstellt ein Animationsvariablenobjekt und legt dessen Standardwert fest. Ein Standardwert wird verwendet, wenn eine Variable nicht animiert ist oder nicht animiert werden kann.

## <a name="canimationvariablecleartransitions"></a><a name="cleartransitions"></a>CAnimationVariable::ClearTransitions

Löscht Übergänge.

```cpp
void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>Parameter

*bAutodestroy*<br/>
Gibt an, ob diese Methode Übergangsobjekte löschen soll.

### <a name="remarks"></a>Bemerkungen

Diese Methode entfernt alle Übergänge aus der internen Liste der Übergänge. Wenn bAutodestroy TRUE oder m_bAutodestroyTransitions TRUE ist, werden Übergänge gelöscht. Andernfalls sollte der Aufrufer die Zuordnung der Übergangsobjekte aufteilen.

## <a name="canimationvariablecreate"></a><a name="create"></a>CAnimationVariable::Erstellen

Erstellt das zugrunde liegende Animationsvariable COM-Objekt.

```
virtual BOOL Create(IUIAnimationManager* pManager);
```

### <a name="parameters"></a>Parameter

*pManager*<br/>
Ein Zeiger auf den Animations-Manager.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn die Animationsvariable erfolgreich erstellt wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode erstellt das zugrunde liegende Animationsvariable COM-Objekt und legt dessen Standardwert fest.

## <a name="canimationvariablecreatetransitions"></a><a name="createtransitions"></a>CAnimationVariable::ErstellenVonÜbergänge

Erstellt alle Übergänge, die auf diese Animationsvariable angewendet werden sollen.

```
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>Parameter

*pLibrary*<br/>
Ein Zeiger auf eine [IUIAnimationTransitionLibrary-Schnittstelle](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary), die eine Bibliothek mit Standardübergängen definiert.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn Übergänge erfolgreich erstellt wurden; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird vom Framework aufgerufen, wenn es Übergänge erstellen muss, die der internen Liste der Übergänge der Variablen hinzugefügt wurden.

## <a name="canimationvariableenableintegervaluechangedevent"></a><a name="enableintegervaluechangedevent"></a>CAnimationVariable::EnableIntegerValueChangedEvent

Aktiviert oder deaktiviert das IntegerValueChanged-Ereignis.

```cpp
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parameter

*pController*<br/>
Ein Zeiger auf den übergeordneten Controller.

*bEnable*<br/>
TRUE - ereignis aktivieren, FALSE - ereignis deaktivieren.

### <a name="remarks"></a>Bemerkungen

Wenn das ValueChanged-Ereignis aktiviert ist, ruft das Framework die virtuelle Methode CAnimationController::OnAnimationIntegerValueChanged auf. Sie müssen es in einer von CAnimationController abgeleiteten Klasse überschreiben, um dieses Ereignis zu verarbeiten. Diese Methode wird jedes Mal aufgerufen, wenn der Ganzzahlwert der Animationsvariablen geändert wird.

## <a name="canimationvariableenablevaluechangedevent"></a><a name="enablevaluechangedevent"></a>CAnimationVariable::EnableValueChangedEvent

Aktiviert oder deaktiviert das ValueChanged-Ereignis.

```cpp
void EnableValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>Parameter

*pController*<br/>
Ein Zeiger auf den übergeordneten Controller.

*bEnable*<br/>
TRUE - ereignis aktivieren, FALSE - ereignis deaktivieren.

### <a name="remarks"></a>Bemerkungen

Wenn das ValueChanged-Ereignis aktiviert ist, ruft das Framework die virtuelle Methode CAnimationController::OnAnimationValueChanged auf. Sie müssen es in einer von CAnimationController abgeleiteten Klasse überschreiben, um dieses Ereignis zu verarbeiten. Diese Methode wird jedes Mal aufgerufen, wenn der Wert der Animationsvariablen geändert wird.

## <a name="canimationvariablegetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationVariable::GetDefaultValue

Gibt den Standardwert zurück.

```
DOUBLE GetDefaultValue() const;
```

### <a name="return-value"></a>Rückgabewert

Der Standardwert.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um den Standardwert der Animationsvariablen abzuerhalten. Der Standardwert kann im Konstruktor oder nach der SetDefaultValue-Methode festgelegt werden.

## <a name="canimationvariablegetparentanimationobject"></a><a name="getparentanimationobject"></a>CAnimationVariable::GetParentAnimationObject

Gibt das übergeordnete Animationsobjekt zurück.

```
CAnimationBaseObject* GetParentAnimationObject();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das übergeordnete Animationsobjekt, wenn eine Beziehung eingerichtet wurde, andernfalls NULL.

### <a name="remarks"></a>Bemerkungen

Diese Methode kann aufgerufen werden, um einen Zeiger auf ein übergeordnetes Animationsobjekt (einen Container) abzurufen.

## <a name="canimationvariablegetvalue"></a><a name="getvalue"></a>CAnimationVariable::GetValue

Gibt den aktuellen Wert der Animationsvariablen zurück.

```
HRESULT GetValue(DOUBLE& dblValue);
HRESULT GetValue(INT32& nValue);
```

### <a name="parameters"></a>Parameter

*dblValue*<br/>
Der aktuelle Wert der Animationsvariablen.

*nValue*<br/>
Der aktuelle Wert der Animationsvariablen.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn der Wert erfolgreich abgerufen wurde oder die zugrunde liegende Animationsvariable nicht erstellt wurde. Andernfalls HRESULT-Fehlercode.

### <a name="remarks"></a>Bemerkungen

Diese Methode kann aufgerufen werden, um den aktuellen Wert der Animationsvariablen abzurufen. Wenn das zugrunde liegende COM-Objekt nicht erstellt wurde, enthält dblValue einen Standardwert, wenn die Funktion zurückkehrt.

## <a name="canimationvariablegetvariable"></a><a name="getvariable"></a>CAnimationVariable::GetVariable

Gibt einen Zeiger auf das IUIAnimationVariable COM-Objekt zurück.

```
IUIAnimationVariable* GetVariable();
```

### <a name="return-value"></a>Rückgabewert

Ein gültiger Zeiger auf das IUIAnimationVariable COM-Objekt oder NULL, wenn die Animationsvariable nicht erstellt wurde oder nicht erstellt werden kann.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um auf das zugrunde liegende IUIAnimationVariable COM-Objekt zuzugreifen und seine Methoden bei Bedarf direkt aufzurufen.

## <a name="canimationvariablem_bautodestroytransitions"></a><a name="m_bautodestroytransitions"></a>CAnimationVariable::m_bAutodestroyTransitions

Gibt an, ob verwandte Übergangsobjekte gelöscht werden sollen.

```
BOOL m_bAutodestroyTransitions;
```

### <a name="remarks"></a>Bemerkungen

Legen Sie diesen Wert auf TRUE fest, um das Löschen von Übergangsobjekten zu erzwingen, wenn sie aus der internen Liste der Übergänge entfernt werden. Wenn dieser Wert FALSE ist, sollten die Übergänge durch Aufrufen der Anwendung gelöscht werden. Die Liste der Übergänge wird immer gelöscht, nachdem eine Animation geplant wurde. Der Standardwert ist FALSE.

## <a name="canimationvariablem_dbldefaultvalue"></a><a name="m_dbldefaultvalue"></a>CAnimationVariable::m_dblDefaultValue

Gibt den Standardwert an, der an IUIAnimationVariable weitergegeben wird.

```
DOUBLE m_dblDefaultValue;
```

## <a name="canimationvariablem_lsttransitions"></a><a name="m_lsttransitions"></a>CAnimationVariable::m_lstTransitions

Enthält eine Liste von Übergängen, die diese Animationsvariable animieren.

```
CObList m_lstTransitions;
```

## <a name="canimationvariablem_pparentobject"></a><a name="m_pparentobject"></a>CAnimationVariable::m_pParentObject

Ein Zeiger auf ein Animationsobjekt, das diese Animationsvariable kapselt.

```
CAnimationBaseObject* m_pParentObject;
```

## <a name="canimationvariablem_variable"></a><a name="m_variable"></a>CAnimationVariable::m_variable

Speichert einen Zeiger auf das IUIAnimationVariable COM-Objekt. NULL, wenn das COM-Objekt noch nicht erstellt wurde oder wenn die Erstellung fehlgeschlagen ist.

```
ATL::CComPtr<IUIAnimationVariable> m_variable;
```

## <a name="canimationvariablesetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationVariable::SetDefaultValue

Legt den Standardwert fest und gibt das IUIAnimationVariable COM-Objekt frei.

```cpp
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>Parameter

*dblDefaultValue*<br/>
Gibt den neuen Standardwert an.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um den Standardwert zurückzusetzen. Diese Methode gibt das interne IUIAnimationVariable COM-Objekt frei, daher erhält das zugrunde liegende COM-Objekt beim Neuerstellen der Animationsvariablen den neuen Standardwert. Der Standardwert wird von GetValue zurückgegeben, wenn das COM-Objekt, das die Animationsvariable darstellt, nicht erstellt wird oder wenn die Variable nicht animiert wurde.

## <a name="canimationvariablesetparentanimationobject"></a><a name="setparentanimationobject"></a>CAnimationVariable::SetParentAnimationObject

Legt die Beziehung zwischen einer Animationsvariablen und einem Animationsobjekt fest.

```cpp
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```

### <a name="parameters"></a>Parameter

*pParentObject*<br/>
Ein Zeiger auf ein Animationsobjekt, das diese Variable enthält.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird intern aufgerufen, um eine 1:1-Beziehung zwischen einer Animationsvariablen und einem Animationsobjekt herzustellen, das sie kapselt.

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)

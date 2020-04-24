---
title: CBaseTransition-Klasse
ms.date: 03/27/2019
f1_keywords:
- CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboardAtKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::Clear
- AFXANIMATIONCONTROLLER/CBaseTransition::Create
- AFXANIMATIONCONTROLLER/CBaseTransition::GetEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::GetStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::GetType
- AFXANIMATIONCONTROLLER/CBaseTransition::IsAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::SetKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::SetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_transition
- AFXANIMATIONCONTROLLER/CBaseTransition::m_type
helpviewer_keywords:
- CBaseTransition [MFC], CBaseTransition
- CBaseTransition [MFC], AddToStoryboard
- CBaseTransition [MFC], AddToStoryboardAtKeyframes
- CBaseTransition [MFC], Clear
- CBaseTransition [MFC], Create
- CBaseTransition [MFC], GetEndKeyframe
- CBaseTransition [MFC], GetRelatedVariable
- CBaseTransition [MFC], GetStartKeyframe
- CBaseTransition [MFC], GetTransition
- CBaseTransition [MFC], GetType
- CBaseTransition [MFC], IsAdded
- CBaseTransition [MFC], SetKeyframes
- CBaseTransition [MFC], SetRelatedVariable
- CBaseTransition [MFC], m_bAdded
- CBaseTransition [MFC], m_pEndKeyframe
- CBaseTransition [MFC], m_pRelatedVariable
- CBaseTransition [MFC], m_pStartKeyframe
- CBaseTransition [MFC], m_transition
- CBaseTransition [MFC], m_type
ms.assetid: dfe84007-bbc5-43b7-b5b8-fae9145573bf
ms.openlocfilehash: 9abe4ae55d9d84ea435cd5d82925ff8b8a544480
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752958"
---
# <a name="cbasetransition-class"></a>CBaseTransition-Klasse

Stellt einen einfachen Übergang dar.

## <a name="syntax"></a>Syntax

```
class CBaseTransition : public CObject;
```

## <a name="members"></a>Member

### <a name="public-enumerations"></a>Öffentliche Enumerationen

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBaseTransition::TRANSITION_TYPE-Enumeration](#transition_type_enumeration)|Definiert die Übergangstypen, die derzeit von der MFC-Implementierung der Windows-Animations-API unterstützt werden.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBaseTransition::CBaseTransition](#cbasetransition)|Erstellt ein Basisübergangsobjekt.|
|[CBaseTransition::'CBaseTransition](#_dtorcbasetransition)|Der Destruktor. Wird aufgerufen, wenn ein Übergangsobjekt zerstört wird.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBaseTransition::AddToStoryboard](#addtostoryboard)|Fügt einem Storyboard einen Übergang hinzu.|
|[CBaseTransition::AddToStoryboardAtKeyframes](#addtostoryboardatkeyframes)|Fügt einem Storyboard einen Übergang hinzu.|
|[CBaseTransition::Löschen](#clear)|Gibt gekapseltes IUIAnimationTransition COM-Objekt frei.|
|[CBaseTransition::Erstellen](#create)|Erstellt einen COM-Übergang.|
|[CBaseTransition::GetEndKeyframe](#getendkeyframe)|Gibt Start-Keyframe zurück.|
|[CBaseTransition::GetRelatedVariable](#getrelatedvariable)|Gibt einen Zeiger auf die verknüpfte Variable zurück.|
|[CBaseTransition::GetStartKeyframe](#getstartkeyframe)|Gibt Start-Keyframe zurück.|
|[CBaseTransition::GetTransition](#gettransition)|Ist überladen. Gibt einen Zeiger auf das zugrunde liegende COM-Übergangsobjekt zurück.|
|[CBaseTransition::GetType](#gettype)|Gibt den Übergangstyp zurück.|
|[CBaseTransition::IsAdded](#isadded)|Gibt an, ob einem Storyboard ein Übergang hinzugefügt wurde.|
|[CBaseTransition::SetKeyframes](#setkeyframes)|Legt Keyframes für einen Übergang fest.|
|[CBaseTransition::SetRelatedVariable](#setrelatedvariable)|Erstellt eine Beziehung zwischen Animationsvariable und Übergang.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBaseTransition::m_bAdded](#m_badded)|Gibt an, ob einem Storyboard ein Übergang hinzugefügt wurde.|
|[CBaseTransition::m_pEndKeyframe](#m_pendkeyframe)|Speichert einen Zeiger auf den Keyframe, der das Ende des Übergangs angibt.|
|[CBaseTransition::m_pRelatedVariable](#m_prelatedvariable)|Ein Zeiger auf eine Animationsvariable, die mit dem in m_transition gespeicherten Übergang animiert wird.|
|[CBaseTransition::m_pStartKeyframe](#m_pstartkeyframe)|Speichert einen Zeiger auf den Keyframe, der den Beginn des Übergangs angibt.|
|[CBaseTransition::m_transition](#m_transition)|Speichert einen Zeiger auf IUIAnimationTransition. NULL, wenn kein COM-Übergangsobjekt erstellt wurde.|
|[CBaseTransition::m_type](#m_type)|Speichert den Übergangstyp.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse kapselt die IUIAnimationTransition-Schnittstelle und dient als Basisklasse für alle Übergänge.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CBaseTransition`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxanimationcontroller.h

## <a name="cbasetransitioncbasetransition"></a><a name="_dtorcbasetransition"></a>CBaseTransition::'CBaseTransition

Der Destruktor. Wird aufgerufen, wenn ein Übergangsobjekt zerstört wird.

```
virtual ~CBaseTransition();
```

## <a name="cbasetransitionaddtostoryboard"></a><a name="addtostoryboard"></a>CBaseTransition::AddToStoryboard

Fügt einem Storyboard einen Übergang hinzu.

```
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parameter

*pStoryboard*<br/>
Ein Zeiger auf das Storyboard, das die zugehörige Variable animiert.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Übergang erfolgreich zu einem Storyboard hinzugefügt wurde.

### <a name="remarks"></a>Bemerkungen

Wendet den Übergang auf die zugehörige Variable im Storyboard an. Wenn dies der erste Übergang ist, der auf diese Variable in diesem Storyboard angewendet wird, beginnt der Übergang am Anfang des Storyboards. Andernfalls wird der Übergang an den Übergang angehängt, der zuletzt der Variablen hinzugefügt wurde.

## <a name="cbasetransitionaddtostoryboardatkeyframes"></a><a name="addtostoryboardatkeyframes"></a>CBaseTransition::AddToStoryboardAtKeyframes

Fügt einem Storyboard einen Übergang hinzu.

```
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>Parameter

*pStoryboard*<br/>
Ein Zeiger auf das Storyboard, das die zugehörige Variable animiert.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Übergang erfolgreich zu einem Storyboard hinzugefügt wurde.

### <a name="remarks"></a>Bemerkungen

Wendet den Übergang auf die zugehörige Variable im Storyboard an. Wenn der Startschlüssel angegeben wurde, beginnt der Übergang an diesem Keyframe. Wenn der End-Keyframe angegeben wurde, beginnt der Übergang am Start-Keyframe und endet am End-Keyframe. Wenn der Übergang mit einem angegebenen Dauerparameter erstellt wurde, wird diese Dauer mit der Dauer zwischen dem Start- und dem Endschlüsselüberschrieben überschrieben. Wenn kein Keyframe angegeben wurde, wird der Übergang an den Übergang angehängt, der zuletzt der Variablen hinzugefügt wurde.

## <a name="cbasetransitioncbasetransition"></a><a name="cbasetransition"></a>CBaseTransition::CBaseTransition

Erstellt ein Basisübergangsobjekt.

```
CBaseTransition();
```

## <a name="cbasetransitionclear"></a><a name="clear"></a>CBaseTransition::Löschen

Gibt gekapseltes IUIAnimationTransition COM-Objekt frei.

```cpp
void Clear();
```

### <a name="remarks"></a>Bemerkungen

Diese Methode sollte von der Create-Methode einer abgeleiteten Klasse aufgerufen werden, um ein IUITransition-Schnittstellenleck zu verhindern.

## <a name="cbasetransitioncreate"></a><a name="create"></a>CBaseTransition::Erstellen

Erstellt einen COM-Übergang.

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory) = 0;
```

### <a name="parameters"></a>Parameter

*pLibrary*<br/>
Ein Zeiger auf die Übergangsbibliothek, die Standardübergänge erstellt. Es kann NULL für benutzerdefinierte Übergänge sein.

*pFactory*<br/>
Ein Zeiger auf die Übergangsfactory, die benutzerdefinierte Übergänge erstellt. Es kann NULL für Standardübergänge sein.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn ein Übergangs-COM-Objekt erfolgreich erstellt wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Dies ist eine reine virtuelle Funktion, die in einer abgeleiteten Klasse überschrieben werden muss. Es wird vom Framework aufgerufen, um das zugrunde liegende COM-Übergangsobjekt zu instanziieren.

## <a name="cbasetransitiongetendkeyframe"></a><a name="getendkeyframe"></a>CBaseTransition::GetEndKeyframe

Gibt Start-Keyframe zurück.

```
CBaseKeyFrame* GetEndKeyframe();
```

### <a name="return-value"></a>Rückgabewert

Ein gültiger Zeiger auf ein Keyframe oder NULL, wenn ein Übergang nicht zwischen Keyframes eingefügt werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Methode kann verwendet werden, um auf ein Keyframe-Objekt zuzugreifen, das zuvor von SetKeyframes festgelegt wurde. Es wird durch Code der obersten Ebene aufgerufen, wenn Übergänge zum Storyboard hinzugefügt werden.

## <a name="cbasetransitiongetrelatedvariable"></a><a name="getrelatedvariable"></a>CBaseTransition::GetRelatedVariable

Gibt einen Zeiger auf die verknüpfte Variable zurück.

```
CAnimationVariable* GetRelatedVariable();
```

### <a name="return-value"></a>Rückgabewert

Ein gültiger Zeiger auf die Animationsvariable oder NULL, wenn eine Animationsvariable nicht von SetRelatedVariable festgelegt wurde.

### <a name="remarks"></a>Bemerkungen

Dies ist ein Accessor für verwandte Animationsvariablen.

## <a name="cbasetransitiongetstartkeyframe"></a><a name="getstartkeyframe"></a>CBaseTransition::GetStartKeyframe

Gibt Start-Keyframe zurück.

```
CBaseKeyFrame* GetStartKeyframe();
```

### <a name="return-value"></a>Rückgabewert

Ein gültiger Zeiger auf einen Keyframe oder NULL, wenn ein Übergang nicht nach einem Keyframe beginnen soll.

### <a name="remarks"></a>Bemerkungen

Diese Methode kann verwendet werden, um auf ein Keyframe-Objekt zuzugreifen, das zuvor von SetKeyframes festgelegt wurde. Es wird durch Code der obersten Ebene aufgerufen, wenn Übergänge zum Storyboard hinzugefügt werden.

## <a name="cbasetransitiongettransition"></a><a name="gettransition"></a>CBaseTransition::GetTransition

Gibt einen Zeiger auf das zugrunde liegende COM-Übergangsobjekt zurück.

```
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory);

IUIAnimationTransition* GetTransition();
```

### <a name="parameters"></a>Parameter

*pLibrary*<br/>
Ein Zeiger auf die Übergangsbibliothek, die Standardübergänge erstellt. Es kann NULL für benutzerdefinierte Übergänge sein.

*pFactory*<br/>
Ein Zeiger auf die Übergangsfactory, die benutzerdefinierte Übergänge erstellt. Es kann NULL für Standardübergänge sein.

### <a name="return-value"></a>Rückgabewert

Ein gültiger Zeiger auf IUIAnimationTransition oder NULL, wenn der zugrunde liegende Übergang nicht erstellt werden kann.

### <a name="remarks"></a>Bemerkungen

Diese Methode gibt einen Zeiger auf das zugrunde liegende COM-Übergangsobjekt zurück und erstellt ihn bei Bedarf.

## <a name="cbasetransitiongettype"></a><a name="gettype"></a>CBaseTransition::GetType

Gibt den Übergangstyp zurück.

```
TRANSITION_TYPE GetType() const;
```

### <a name="return-value"></a>Rückgabewert

Einer von TRANSITION_TYPE aufgezählten Werten.

### <a name="remarks"></a>Bemerkungen

Diese Methode kann verwendet werden, um ein Übergangsobjekt anhand seines Typs zu identifizieren. Der Typ wird in einem Konstruktor in einer abgeleiteten Klasse festgelegt.

## <a name="cbasetransitionisadded"></a><a name="isadded"></a>CBaseTransition::IsAdded

Gibt an, ob einem Storyboard ein Übergang hinzugefügt wurde.

```
BOOL IsAdded();
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn ein Übergang zu einem Storyboard hinzugefügt wurde, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Dieses Flag wird intern gesetzt, wenn der Code der obersten Ebene Übergänge zum Storyboard hinzufügt.

## <a name="cbasetransitionm_badded"></a><a name="m_badded"></a>CBaseTransition::m_bAdded

Gibt an, ob einem Storyboard ein Übergang hinzugefügt wurde.

```
BOOL m_bAdded;
```

## <a name="cbasetransitionm_pendkeyframe"></a><a name="m_pendkeyframe"></a>CBaseTransition::m_pEndKeyframe

Speichert einen Zeiger auf den Keyframe, der das Ende des Übergangs angibt.

```
CBaseKeyFrame* m_pEndKeyframe;
```

## <a name="cbasetransitionm_prelatedvariable"></a><a name="m_prelatedvariable"></a>CBaseTransition::m_pRelatedVariable

Ein Zeiger auf eine Animationsvariable, die mit dem in m_transition gespeicherten Übergang animiert wird.

```
CAnimationVariable* m_pRelatedVariable;
```

## <a name="cbasetransitionm_pstartkeyframe"></a><a name="m_pstartkeyframe"></a>CBaseTransition::m_pStartKeyframe

Speichert einen Zeiger auf den Keyframe, der den Beginn des Übergangs angibt.

```
CBaseKeyFrame* m_pStartKeyframe;
```

## <a name="cbasetransitionm_transition"></a><a name="m_transition"></a>CBaseTransition::m_transition

Speichert einen Zeiger auf IUIAnimationTransition. NULL, wenn kein COM-Übergangsobjekt erstellt wurde.

```
ATL::CComPtr<IUIAnimationTransition> m_transition;
```

## <a name="cbasetransitionm_type"></a><a name="m_type"></a>CBaseTransition::m_type

Speichert den Übergangstyp.

```
TRANSITION_TYPE m_type;
```

## <a name="cbasetransitionsetkeyframes"></a><a name="setkeyframes"></a>CBaseTransition::SetKeyframes

Legt Keyframes für einen Übergang fest.

```cpp
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,
    CBaseKeyFrame* pEnd = NULL);
```

### <a name="parameters"></a>Parameter

*pStart*<br/>
Ein Keyframe, der den Beginn des Übergangs angibt.

*Pend*<br/>
Ein Keyframe, der das Ende des Übergangs angibt.

### <a name="remarks"></a>Bemerkungen

Diese Methode weist den Übergang an, nach dem angegebenen Keyframe zu beginnen und optional, wenn pEnd nicht NULL ist, vor dem angegebenen Keyframe zu enden. Wenn der Übergang mit einem angegebenen Dauerparameter erstellt wurde, wird diese Dauer mit der Dauer zwischen dem Start- und dem Endschlüsselüberschrieben überschrieben.

## <a name="cbasetransitionsetrelatedvariable"></a><a name="setrelatedvariable"></a>CBaseTransition::SetRelatedVariable

Erstellt eine Beziehung zwischen Animationsvariable und Übergang.

```cpp
void SetRelatedVariable(CAnimationVariable* pVariable);
```

### <a name="parameters"></a>Parameter

*pVariable*<br/>
Ein Zeiger auf die zugehörige Animationsvariable.

### <a name="remarks"></a>Bemerkungen

Erstellt eine Beziehung zwischen Animationsvariable und Übergang. Ein Übergang kann nur auf eine Variable angewendet werden.

## <a name="cbasetransitiontransition_type-enumeration"></a><a name="transition_type_enumeration"></a>CBaseTransition::TRANSITION_TYPE-Enumeration

Definiert die Übergangstypen, die derzeit von der MFC-Implementierung der Windows-Animations-API unterstützt werden.

```
enum TRANSITION_TYPE;
```

### <a name="remarks"></a>Bemerkungen

Im Konstruktor eines bestimmten Übergangs wird ein Übergangstyp festgelegt. Beispielsweise legt CSinusoidalTransitionFromRange seinen Typ auf SINUSOIDAL_FROM_RANGE.

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)

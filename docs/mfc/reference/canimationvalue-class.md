---
title: CAnimationValue-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationValue::GetValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationValue::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationValue::m_value
helpviewer_keywords:
- CAnimationValue [MFC], CAnimationValue
- CAnimationValue [MFC], AddTransition
- CAnimationValue [MFC], GetValue
- CAnimationValue [MFC], GetVariable
- CAnimationValue [MFC], SetDefaultValue
- CAnimationValue [MFC], GetAnimationVariableList
- CAnimationValue [MFC], m_value
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
ms.openlocfilehash: e020e3e123bb5dc96a623e7a41896d75c611b81e
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755087"
---
# <a name="canimationvalue-class"></a>CAnimationValue-Klasse

Implementiert die Funktion eines Animationsobjekts, das über einen Wert verfügt.

## <a name="syntax"></a>Syntax

```
class CAnimationValue : public CAnimationBaseObject;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationValue::CAnimationValue](#canimationvalue)|Ist überladen. Erstellt ein CAnimationValue-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationValue::AddTransition](#addtransition)|Fügt einen Übergang hinzu, der auf einen Wert angewendet werden soll.|
|[CAnimationValue::GetValue](#getvalue)|Ist überladen. Ruft den aktuellen Wert ab.|
|[CAnimationValue::GetVariable](#getvariable)|Bietet Zugriff auf gekapselte Animationsvariable.|
|[CAnimationValue::SetDefaultValue](#setdefaultvalue)|Legt den Standardwert fest.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationValue::GetAnimationVariableList](#getanimationvariablelist)|Fügt die gekapselte Animationsvariable in eine Liste ein. (Überschreibt [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationValue::operator DOUBLE](#operator_double)|Stellt die Konvertierung zwischen CAnimationValue und DOUBLE bereit.|
|[CAnimationValue::operator INT32](#operator_int32)|Stellt die Konvertierung zwischen CAnimationValue und INT32 bereit.|
|[CAnimationValue::operator=](#operator_eq)|Ist überladen. Weist CAnimationValue einen INT32-Wert zu.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationValue::m_value](#m_value)|Die gekapselte Animationsvariable, die den Animationswert darstellt.|

## <a name="remarks"></a>Bemerkungen

Die CAnimationValue-Klasse kapselt ein einzelnes CAnimationVariable-Objekt und kann in Anwendungen einen einzelnen animierten Wert darstellen. Sie können diese Klasse beispielsweise für animierte Transparenz (Fade-Effekt), Winkel (zum Drehen von Objekten) oder für andere Fall verwenden, wenn Sie eine Animation je nach einem einzelnen animierten Wert erstellen müssen. Um diese Klasse in der Anwendung zu verwenden, instanziieren Sie einfach ein Objekt dieser Klasse, fügen Sie es dem Animationscontroller mit CAnimationController::AddAnimationObject hinzu, und rufen Sie AddTransition für jeden Übergang auf, der auf den Wert angewendet werden soll.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationValue`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxanimationcontroller.h

## <a name="canimationvalueaddtransition"></a><a name="addtransition"></a>CAnimationValue::AddTransition

Fügt einen Übergang hinzu, der auf einen Wert angewendet werden soll.

```cpp
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>Parameter

*pTransition*<br/>
Ein Zeiger auf das Übergangsobjekt.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um einen Übergang zur internen Liste der Übergänge hinzuzufügen, die auf eine Animationsvariable angewendet werden sollen. Wenn Sie Übergänge hinzufügen, werden sie nicht sofort angewendet und in einer internen Liste gespeichert. Übergänge werden angewendet (zu einem Storyboard für einen bestimmten Wert hinzugefügt), wenn Sie CAnimationController::AnimateGroup aufrufen.

## <a name="canimationvaluecanimationvalue"></a><a name="canimationvalue"></a>CAnimationValue::CAnimationValue

Erstellt ein CAnimationValue-Objekt.

```
CAnimationValue();

CAnimationValue(
    DOUBLE dblDefaultValue,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parameter

*dblDefaultValue*<br/>
Gibt den Standardwert an.

*nGroupID*<br/>
Gibt die Gruppen-ID an.

*nObjectID*<br/>
Gibt die Objekt-ID an.

*dwUserData*<br/>
gibt benutzerdefinierte Daten an.

### <a name="remarks"></a>Bemerkungen

Erstellt CAnimationValue-Objekte mit Standardeigenschaften: Standardwert, Gruppen-ID und Objekt-ID werden auf 0 gesetzt.

## <a name="canimationvaluegetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationValue::GetAnimationVariableList

Fügt die gekapselte Animationsvariable in eine Liste ein.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parameter

*Lst*<br/>
Wenn die Funktion zurückkehrt, enthält sie einen Zeiger auf CAnimationVariable, der den animierten Wert darstellt.

## <a name="canimationvaluegetvalue"></a><a name="getvalue"></a>CAnimationValue::GetValue

Ruft den aktuellen Wert ab.

```
BOOL GetValue(DOUBLE& dblValue);
BOOL GetValue(INT32& nValue);
```

### <a name="parameters"></a>Parameter

*dblValue*<br/>
Ausgabe Wenn die Funktion zurückkehrt, enthält sie einen aktuellen Wert der Animationsvariablen.

*nValue*<br/>
Ausgabe Wenn die Funktion zurückkehrt, enthält sie einen aktuellen Wert der Animationsvariablen.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der aktuelle Wert erfolgreich abgerufen wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um den aktuellen Wert abzurufen. Diese Implementierung ruft das gekapselte COM-Objekt auf, und wenn der Aufruf fehlschlägt, gibt diese Methode den Standardwert zurück, der zuvor im Konstruktor oder mit SetDefaultValue festgelegt wurde.

## <a name="canimationvaluegetvariable"></a><a name="getvariable"></a>CAnimationValue::GetVariable

Bietet Zugriff auf gekapselte Animationsvariable.

```
CAnimationVariable& GetVariable();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf die gekapselte Animationsvariable.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um auf die gekapselte Animationsvariable zuzugreifen. Von CAnimationVariable erhalten Sie Zugriff auf das zugrunde liegende IUIAnimationVariable-Objekt, dessen Zeiger NULL sein kann, wenn keine Animationsvariable erstellt wurde.

## <a name="canimationvaluem_value"></a><a name="m_value"></a>CAnimationValue::m_value

Die gekapselte Animationsvariable, die den Animationswert darstellt.

```
CAnimationVariable m_value;
```

## <a name="canimationvalueoperator-double"></a><a name="operator_double"></a>CAnimationValue::operator DOUBLE

Stellt die Konvertierung zwischen CAnimationValue und DOUBLE bereit.

```
operator DOUBLE();
```

### <a name="return-value"></a>Rückgabewert

Aktueller Wert von Animationswert.

### <a name="remarks"></a>Bemerkungen

Stellt die Konvertierung zwischen CAnimationValue und DOUBLE bereit. Diese Methode ruft getValue intern auf und überprüft nicht auf Fehler. Wenn GetValue fehlschlägt, enthält der zurückgegebene Wert einen Standardwert, der zuvor im Konstruktor oder mit SetDefaultValue festgelegt wurde.

## <a name="canimationvalueoperator-int32"></a><a name="operator_int32"></a>CAnimationValue::operator INT32

Stellt die Konvertierung zwischen CAnimationValue und INT32 bereit.

```
operator INT32();
```

### <a name="return-value"></a>Rückgabewert

Aktueller Wert des Animationswerts als ganzzahlige Datei.

### <a name="remarks"></a>Bemerkungen

Stellt die Konvertierung zwischen CAnimationValue und INT32 bereit. Diese Methode ruft getValue intern auf und überprüft nicht auf Fehler. Wenn GetValue fehlschlägt, enthält der zurückgegebene Wert einen Standardwert, der zuvor im Konstruktor oder mit SetDefaultValue festgelegt wurde.

## <a name="canimationvalueoperator"></a><a name="operator_eq"></a>CAnimationValue::operator=

Weist CAnimationValue einen DOUBLE-Wert zu.

```cpp
void operator=(DOUBLE dblVal);
void operator=(INT32 nVal);
```

### <a name="parameters"></a>Parameter

*dblVal*<br/>
Gibt den Wert an, der dem Animationswert zugewiesen werden soll.

*nVal*<br/>
Gibt den Wert an, der dem Animationswert zugewiesen werden soll.

### <a name="remarks"></a>Bemerkungen

Weist CAnimationValue einen DOUBLE-Wert zu. Dieser Wert wird als Standardwert für gekapselte Animationsvariable festgelegt. Wenn Sie dieses Animationsobjekt für Ereignisse (ValueChanged oder IntegerValueChanged) abonniert haben, müssen Sie diese Ereignisse erneut aktivieren.

## <a name="canimationvaluesetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationValue::SetDefaultValue

Legt den Standardwert fest.

```cpp
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>Parameter

*dblDefaultValue*<br/>
Gibt den Standardwert an.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Methode, um einen Standardwert festzulegen. Ein Standardwert wird an die Anwendung zurückgegeben, wenn die Animation nicht gestartet wurde und/oder das zugrunde liegende COM-Objekt nicht erstellt wurde. Wenn das zugrunde liegende COM-Objekt, das in CAnimationVarible gekapselt wurde, bereits erstellt wurde, erstellt diese Methode es neu, daher müssen Sie möglicherweise enableValueChanged/EnableIntegerValueChanged-Methoden erneut aufrufen.

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)

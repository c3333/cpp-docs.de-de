---
title: CAnimationColor-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationColor::GetB
- AFXANIMATIONCONTROLLER/CAnimationColor::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetG
- AFXANIMATIONCONTROLLER/CAnimationColor::GetR
- AFXANIMATIONCONTROLLER/CAnimationColor::GetValue
- AFXANIMATIONCONTROLLER/CAnimationColor::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationColor::m_bValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_gValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_rValue
helpviewer_keywords:
- CAnimationColor [MFC], CAnimationColor
- CAnimationColor [MFC], AddTransition
- CAnimationColor [MFC], GetB
- CAnimationColor [MFC], GetDefaultValue
- CAnimationColor [MFC], GetG
- CAnimationColor [MFC], GetR
- CAnimationColor [MFC], GetValue
- CAnimationColor [MFC], SetDefaultValue
- CAnimationColor [MFC], GetAnimationVariableList
- CAnimationColor [MFC], m_bValue
- CAnimationColor [MFC], m_gValue
- CAnimationColor [MFC], m_rValue
ms.assetid: 88bfabd4-efeb-4652-87e8-304253d8e48c
ms.openlocfilehash: 7c1c98d739aa1c17bb30df2d9d4ce8c41558c76d
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81750192"
---
# <a name="canimationcolor-class"></a>CAnimationColor-Klasse

Implementiert die Funktion einer Farbe, deren Rot-, Grün- und Blauanteil animiert werden kann.

## <a name="syntax"></a>Syntax

```
class CAnimationColor : public CAnimationBaseObject;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationColor::CAnimationColor](#canimationcolor)|Ist überladen. Erstellt ein Animationsfarbobjekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationColor::AddTransition](#addtransition)|Fügt Übergänge für rote, grüne und blaue Komponenten hinzu.|
|[CAnimationColor::GetB](#getb)|Bietet Zugriff auf CAnimationVariable, die die Blue-Komponente darstellt.|
|[CAnimationColor::GetDefaultValue](#getdefaultvalue)|Gibt die Standardwerte für Farbkomponenten zurück.|
|[CAnimationColor::GetG](#getg)|Bietet Zugriff auf CAnimationVariable, die die grüne Komponente darstellt.|
|[CAnimationColor::GetR](#getr)|Bietet Zugriff auf CAnimationVariable, die die red-Komponente darstellt.|
|[CAnimationColor::GetValue](#getvalue)|Gibt den aktuellen Wert zurück.|
|[CAnimationColor::SetDefaultValue](#setdefaultvalue)|Legt den Standardwert fest.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationColor::GetAnimationVariableList](#getanimationvariablelist)|Fügt die gekapselten Animationsvariablen in eine Liste ein. (Überschreibt [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationColor::operator COLORREF](#operator_colorref)||
|[CAnimationColor::operator=](#operator_eq)|Ordnet CAnimationColor Farbe zu.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationColor::m_bValue](#m_bvalue)|Die gekapselte Animationsvariable, die die blaue Komponente der Animationsfarbe darstellt.|
|[CAnimationColor::m_gValue](#m_gvalue)|Die gekapselte Animationsvariable, die die grüne Komponente der Animationsfarbe darstellt.|
|[CAnimationColor::m_rValue](#m_rvalue)|Die gekapselte Animationsvariable, die die rote Komponente der Animationsfarbe darstellt.|

## <a name="remarks"></a>Bemerkungen

Die CAnimationColor-Klasse kapselt drei CAnimationVariable-Objekte und kann in Anwendungen eine Farbe darstellen. Sie können diese Klasse beispielsweise verwenden, um Farben eines beliebigen Objekts auf dem Bildschirm zu animieren (z. B. Textfarbe, Hintergrundfarbe usw.). Um diese Klasse in der Anwendung zu verwenden, instanziieren Sie einfach ein Objekt dieser Klasse, fügen Sie es dem Animationscontroller mit CAnimationController::AddAnimationObject hinzu, und rufen Sie AddTransition für jeden Übergang auf, der auf rote, grüne und blaue Komponenten angewendet werden soll.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationColor`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxanimationcontroller.h

## <a name="canimationcoloraddtransition"></a><a name="addtransition"></a>CAnimationColor::AddTransition

Fügt Übergänge für rote, grüne und blaue Komponenten hinzu.

```cpp
void AddTransition(
    CBaseTransition* pRTransition,
    CBaseTransition* pGTransition,
    CBaseTransition* pBTransition);
```

### <a name="parameters"></a>Parameter

*pRTransition*<br/>
Übergang für rote Komponente.

*pGTransition*<br/>
Übergang für grüne Komponente.

*pBÜbergang*<br/>
Übergang für blaue Komponente.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um die angegebenen Übergänge zur internen Liste der Übergänge hinzuzufügen, die auf Animationsvariablen angewendet werden sollen, die Farbkomponenten darstellen. Wenn Sie Übergänge hinzufügen, werden sie nicht sofort angewendet und in einer internen Liste gespeichert. Übergänge werden angewendet (zu einem Storyboard für einen bestimmten Wert hinzugefügt), wenn Sie CAnimationController::AnimateGroup aufrufen. Wenn Sie keinen Übergang auf eine der Farbkomponenten anwenden müssen, können Sie NULL übergeben.

## <a name="canimationcolorcanimationcolor"></a><a name="canimationcolor"></a>CAnimationColor::CAnimationColor

Erstellt ein CAnimationColor-Objekt.

```
CAnimationColor();

CAnimationColor(
    COLORREF color,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parameter

*Farbe*<br/>
Gibt die Standardfarbe an.

*nGroupID*<br/>
Gibt die Gruppen-ID an.

*nObjectID*<br/>
Gibt die Objekt-ID an.

*dwUserData*<br/>
Gibt benutzerdefinierte Daten an.

### <a name="remarks"></a>Bemerkungen

Das Objekt wird mit Standardwerten für Rot, Grün, Blau, Objekt-ID und Gruppen-ID erstellt, die auf 0 gesetzt werden. Sie können später zur Laufzeit mit SetDefaultValue und SetID geändert werden.

## <a name="canimationcolorgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationColor::GetAnimationVariableList

Fügt die gekapselten Animationsvariablen in eine Liste ein.

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parameter

*Lst*<br/>
Wenn die Funktion zurückkehrt, enthält sie Zeiger auf drei CAnimationVariable-Objekte, die rote, grüne und blaue Komponenten darstellen.

## <a name="canimationcolorgetb"></a><a name="getb"></a>CAnimationColor::GetB

Bietet Zugriff auf CAnimationVariable, die die Blue-Komponente darstellt.

```
CAnimationVariable& GetB();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf gekapselte CAnimationVariable, die die blue-Komponente darstellt.

### <a name="remarks"></a>Bemerkungen

Sie können diese Methode aufrufen, um direkten Zugriff auf die zugrunde liegende CAnimationVariable-Komponente zu erhalten, die die Blue-Komponente darstellt.

## <a name="canimationcolorgetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationColor::GetDefaultValue

Gibt die Standardwerte für Farbkomponenten zurück.

```
COLORREF GetDefaultValue();
```

### <a name="return-value"></a>Rückgabewert

Ein COLORREF-Wert, der Standardwerte für RGB-Komponenten enthält.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um den Standardwert abzurufen, der zuvor vom Konstruktor oder SetDefaultValue festgelegt wurde.

## <a name="canimationcolorgetg"></a><a name="getg"></a>CAnimationColor::GetG

Bietet Zugriff auf CAnimationVariable, die die grüne Komponente darstellt.

```
CAnimationVariable& GetG();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf gekapselte CAnimationVariable, die die grüne Komponente darstellt.

### <a name="remarks"></a>Bemerkungen

Sie können diese Methode aufrufen, um direkten Zugriff auf die zugrunde liegende CAnimationVariable-Komponente zu erhalten, die die green-Komponente darstellt.

## <a name="canimationcolorgetr"></a><a name="getr"></a>CAnimationColor::GetR

Bietet Zugriff auf CAnimationVariable, die die red-Komponente darstellt.

```
CAnimationVariable& GetR();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf gekapselte CAnimationVariable, die die rote Komponente darstellt.

### <a name="remarks"></a>Bemerkungen

Sie können diese Methode aufrufen, um direkten Zugriff auf die zugrunde liegende CAnimationVariable zu erhalten, die die red-Komponente darstellt.

## <a name="canimationcolorgetvalue"></a><a name="getvalue"></a>CAnimationColor::GetValue

Gibt den aktuellen Wert zurück.

```
BOOL GetValue(COLORREF& color);
```

### <a name="parameters"></a>Parameter

*Farbe*<br/>
Ausgabe Enthält den aktuellen Wert, wenn diese Methode zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der aktuelle Wert erfolgreich abgerufen wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um den aktuellen Wert der Animationsfarbe abzurufen. Wenn diese Methode fehlschlägt oder zugrunde liegende COM-Objekte für Farbkomponenten nicht initialisiert wurden, enthält color den Standardwert, der zuvor im Konstruktor oder durch SetDefaultValue festgelegt wurde.

## <a name="canimationcolorm_bvalue"></a><a name="m_bvalue"></a>CAnimationColor::m_bValue

Die gekapselte Animationsvariable, die die blaue Komponente der Animationsfarbe darstellt.

```
CAnimationVariable m_bValue;
```

## <a name="canimationcolorm_gvalue"></a><a name="m_gvalue"></a>CAnimationColor::m_gValue

Die gekapselte Animationsvariable, die die grüne Komponente der Animationsfarbe darstellt.

```
CAnimationVariable m_gValue;
```

## <a name="canimationcolorm_rvalue"></a><a name="m_rvalue"></a>CAnimationColor::m_rValue

Die gekapselte Animationsvariable, die die rote Komponente der Animationsfarbe darstellt.

```
CAnimationVariable m_rValue;
```

## <a name="canimationcoloroperator-colorref"></a><a name="operator_colorref"></a>CAnimationColor::operator COLORREF

```
operator COLORREF();
```

### <a name="return-value"></a>Rückgabewert

## <a name="canimationcoloroperator"></a><a name="operator_eq"></a>CAnimationColor::operator=

Ordnet CAnimationColor Farbe zu.

```cpp
void operator=(COLORREF color);
```

### <a name="parameters"></a>Parameter

*Farbe*<br/>
Gibt den neuen Wert Animationsfarbe an.

### <a name="remarks"></a>Bemerkungen

Es wird empfohlen, dies vor dem Starten der Animation zu tun, da dieser Operator SetDefaultValue aufruft, wodurch die zugrunde liegenden COM-Objekte für Farbkomponenten neu erstellt werden, wenn sie erstellt wurden. Wenn Sie dieses Animationsobjekt für Ereignisse (ValueChanged oder IntegerValueChanged) abonniert haben, müssen Sie diese Ereignisse erneut aktivieren.

## <a name="canimationcolorsetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationColor::SetDefaultValue

Legt den Standardwert fest.

```cpp
void SetDefaultValue(COLORREF color);
```

### <a name="parameters"></a>Parameter

*Farbe*<br/>
Gibt neue Standardwerte für rote, grüne und blaue Komponenten an.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um einen Standardwert für animationsobjekt festzulegen. Diese Methode weist Farbkomponenten der Animationsfarbe Standardwerte zu. Außerdem werden zugrunde liegende COM-Objekte neu erstellt, wenn sie erstellt wurden. Wenn Sie dieses Animationsobjekt für Ereignisse (ValueChanged oder IntegerValueChanged) abonniert haben, müssen Sie diese Ereignisse erneut aktivieren.

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)

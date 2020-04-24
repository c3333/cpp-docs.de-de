---
title: CAnimationRect-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationRect::GetBottom
- AFXANIMATIONCONTROLLER/CAnimationRect::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetLeft
- AFXANIMATIONCONTROLLER/CAnimationRect::GetRight
- AFXANIMATIONCONTROLLER/CAnimationRect::GetTop
- AFXANIMATIONCONTROLLER/CAnimationRect::GetValue
- AFXANIMATIONCONTROLLER/CAnimationRect::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bFixedSize
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bottomValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_leftValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_rightValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_szInitial
- AFXANIMATIONCONTROLLER/CAnimationRect::m_topValue
helpviewer_keywords:
- CAnimationRect [MFC], CAnimationRect
- CAnimationRect [MFC], AddTransition
- CAnimationRect [MFC], GetBottom
- CAnimationRect [MFC], GetDefaultValue
- CAnimationRect [MFC], GetLeft
- CAnimationRect [MFC], GetRight
- CAnimationRect [MFC], GetTop
- CAnimationRect [MFC], GetValue
- CAnimationRect [MFC], SetDefaultValue
- CAnimationRect [MFC], GetAnimationVariableList
- CAnimationRect [MFC], m_bFixedSize
- CAnimationRect [MFC], m_bottomValue
- CAnimationRect [MFC], m_leftValue
- CAnimationRect [MFC], m_rightValue
- CAnimationRect [MFC], m_szInitial
- CAnimationRect [MFC], m_topValue
ms.assetid: 0294156d-241e-4a57-92b2-31234fe557d6
ms.openlocfilehash: 273ea2b548d35722ebf937d2db2b589fef5e69fa
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755138"
---
# <a name="canimationrect-class"></a>CAnimationRect-Klasse

Implementiert die Funktion eines Rechtecks, dessen Seiten animiert werden können.

## <a name="syntax"></a>Syntax

```
class CAnimationRect : public CAnimationBaseObject;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationRect::CAnimationRect](#canimationrect)|Ist überladen. Erstellt ein Animationsrekt-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationRect::AddTransition](#addtransition)|Fügt Übergänge für linke, obere, rechte und untere Koordinaten hinzu.|
|[CAnimationRect::GetBottom](#getbottom)|Bietet Zugriff auf CAnimationVariable, die die untere Koordinate darstellt.|
|[CAnimationRect::GetDefaultValue](#getdefaultvalue)|Gibt die Standardwerte für die Grenzen des Rechtecks zurück.|
|[CAnimationRect::GetLeft](#getleft)|Bietet Zugriff auf CAnimationVariable, das die linke Koordinate darstellt.|
|[CAnimationRect::GetRight](#getright)|Bietet Zugriff auf CAnimationVariable, die die rechte Koordinate darstellt.|
|[CAnimationRect::GetTop](#gettop)|Bietet Zugriff auf CAnimationVariable, die die obere Koordinate darstellt.|
|[CAnimationRect::GetValue](#getvalue)|Gibt den aktuellen Wert zurück.|
|[CAnimationRect::SetDefaultValue](#setdefaultvalue)|Legt den Standardwert fest.|

### <a name="protected-methods"></a>Geschützte Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationRect::GetAnimationVariableList](#getanimationvariablelist)|Fügt die gekapselten Animationsvariablen in eine Liste ein. (Überschreibt [CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist).)|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationRect::operator RECT](#operator_rect)|Konvertiert eine CAnimationRect in RECT.|
|[CAnimationRect::operator=](#operator_eq)|Weist CAnimationRect Korrektur zu.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationRect::m_bFixedSize](#m_bfixedsize)|Gibt an, ob das Rechteck eine feste Größe hat.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationRect::m_bottomValue](#m_bottomvalue)|Die gekapselte Animationsvariable, die den unteren Rand des Animationsrechtecks darstellt.|
|[CAnimationRect::m_leftValue](#m_leftvalue)|Die gekapselte Animationsvariable, die die linke Grenze des Animationsrechtecks darstellt.|
|[CAnimationRect::m_rightValue](#m_rightvalue)|Die gekapselte Animationsvariable, die die rechte Grenze des Animationsrechtecks darstellt.|
|[CAnimationRect::m_szInitial](#m_szinitial)|Gibt die Anfangsgröße des Animationsrechtecks an.|
|[CAnimationRect::m_topValue](#m_topvalue)|Die gekapselte Animationsvariable, die die obere Grenze des Animationsrechtecks darstellt.|

## <a name="remarks"></a>Bemerkungen

Die CAnimationRect-Klasse kapselt vier CAnimationVariable-Objekte und kann in Anwendungen ein Rechteck darstellen. Um diese Klasse in der Anwendung zu verwenden, instanziieren Sie einfach ein Objekt dieser Klasse, fügen Sie es dem Animationscontroller mit CAnimationController::AddAnimationObject hinzu, und rufen Sie AddTransition für jeden Übergang auf linke, rechte obere und untere Koordinaten auf.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationRect`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxanimationcontroller.h

## <a name="canimationrectaddtransition"></a><a name="addtransition"></a>CAnimationRect::AddTransition

Fügt Übergänge für linke, obere, rechte und untere Koordinaten hinzu.

```cpp
void AddTransition(
    CBaseTransition* pLeftTransition,
    CBaseTransition* pTopTransition,
    CBaseTransition* pRightTransition,
    CBaseTransition* pBottomTransition);
```

### <a name="parameters"></a>Parameter

*pLeftTransition*<br/>
Gibt den Übergang für die linke Seite an.

*pTopTransition*<br/>
Gibt den Übergang für die obere Seite an.

*pRightTransition*<br/>
Gibt den Übergang für die rechte Seite an.

*pBottomTransition*<br/>
Gibt den Übergang für die untere Seite an.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um die angegebenen Übergänge zur internen Liste der Übergänge hinzuzufügen, die auf Animationsvariablen für jede Rechteckseite angewendet werden sollen. Wenn Sie Übergänge hinzufügen, werden sie nicht sofort angewendet und in einer internen Liste gespeichert. Übergänge werden angewendet (zu einem Storyboard für einen bestimmten Wert hinzugefügt), wenn Sie CAnimationController::AnimateGroup aufrufen. Wenn Sie keinen Übergang auf eine der Rechteckseiten anwenden müssen, können Sie NULL übergeben.

## <a name="canimationrectcanimationrect"></a><a name="canimationrect"></a>CAnimationRect::CAnimationRect

Erstellt ein CAnimationRect-Objekt.

```
CAnimationRect();

CAnimationRect(
    const CRect& rect,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);

CAnimationRect(
    const CPoint& pt,
    const CSize& sz,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);

CAnimationRect(
    int nLeft,
    int nTop,
    int nRight,
    int nBottom,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Gibt das Standardrechteck an.

*nGroupID*<br/>
Gibt die Gruppen-ID an.

*nObjectID*<br/>
Gibt die Objekt-ID an.

*dwUserData*<br/>
Gibt benutzerdefinierte Daten an.

*Pt*<br/>
Koordinaten der linken oberen Ecke.

*Sz*<br/>
Größe des Rechtecks.

*nLeft*<br/>
Gibt die Koordinaten der linken Begrenzung an.

*Ntop*<br/>
Gibt die Koordinate der oberen Begrenzung an.

*nRight*<br/>
Gibt die Koordinaten der rechten Begrenzung an.

*nBottom*<br/>
Gibt die Koordinate der unteren Begrenzung an.

### <a name="remarks"></a>Bemerkungen

Das Objekt wird mit Standardwerten für links, oben, rechts und unten, Objekt-ID und Gruppen-ID erstellt, die auf 0 gesetzt werden. Sie können später zur Laufzeit mit SetDefaultValue und SetID geändert werden.

## <a name="canimationrectgetanimationvariablelist"></a><a name="getanimationvariablelist"></a>CAnimationRect::GetAnimationVariableList

Fügt die gekapselten Animationsvariablen in eine Liste ein.

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>Parameter

*Lst*<br/>
Wenn die Funktion zurückkehrt, enthält sie Zeiger auf vier CAnimationVariable-Objekte, die Koordinaten des Rechtecks darstellen.

## <a name="canimationrectgetbottom"></a><a name="getbottom"></a>CAnimationRect::GetBottom

Bietet Zugriff auf CAnimationVariable, die die untere Koordinate darstellt.

```
CAnimationVariable& GetBottom();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf gekapselte CAnimationVariable, die die untere Koordinate darstellt.

### <a name="remarks"></a>Bemerkungen

Sie können diese Methode aufrufen, um direkten Zugriff auf die zugrunde liegende CAnimationVariable zu erhalten, die die untere Koordinate darstellt.

## <a name="canimationrectgetdefaultvalue"></a><a name="getdefaultvalue"></a>CAnimationRect::GetDefaultValue

Gibt die Standardwerte für die Grenzen des Rechtecks zurück.

```
CRect GetDefaultValue();
```

### <a name="return-value"></a>Rückgabewert

Ein CRect-Wert, der Standardwerte für links, rechts, oben und unten enthält.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um den Standardwert abzurufen, der zuvor vom Konstruktor oder SetDefaultValue festgelegt wurde.

## <a name="canimationrectgetleft"></a><a name="getleft"></a>CAnimationRect::GetLeft

Bietet Zugriff auf CAnimationVariable, das die linke Koordinate darstellt.

```
CAnimationVariable& GetLeft();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf gekapselte CAnimationVariable, die die linke Koordinate darstellt.

### <a name="remarks"></a>Bemerkungen

Sie können diese Methode aufrufen, um direkten Zugriff auf die zugrunde liegende CAnimationVariable zu erhalten, die die linke Koordinate darstellt.

## <a name="canimationrectgetright"></a><a name="getright"></a>CAnimationRect::GetRight

Bietet Zugriff auf CAnimationVariable, die die rechte Koordinate darstellt.

```
CAnimationVariable& GetRight();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf gekapselte CAnimationVariable, die die rechte Koordinate darstellt.

### <a name="remarks"></a>Bemerkungen

Sie können diese Methode aufrufen, um direkten Zugriff auf die zugrunde liegende CAnimationVariable zu erhalten, die die richtige Koordinate darstellt.

## <a name="canimationrectgettop"></a><a name="gettop"></a>CAnimationRect::GetTop

Bietet Zugriff auf CAnimationVariable, die die obere Koordinate darstellt.

```
CAnimationVariable& GetTop();
```

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf gekapselte CAnimationVariable, die die obere Koordinate darstellt.

### <a name="remarks"></a>Bemerkungen

Sie können diese Methode aufrufen, um direkten Zugriff auf die zugrunde liegende CAnimationVariable zu erhalten, die die obere Koordinate darstellt.

## <a name="canimationrectgetvalue"></a><a name="getvalue"></a>CAnimationRect::GetValue

Gibt den aktuellen Wert zurück.

```
BOOL GetValue(CRect& rect);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Ausgabe Enthält den aktuellen Wert, wenn diese Methode zurückgegeben wird.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der aktuelle Wert erfolgreich abgerufen wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Funktion auf, um den aktuellen Wert des Animationsrechtecks abzurufen. Wenn diese Methode fehlschlägt oder zugrunde liegende COM-Objekte für links, oben, rechts und unten nicht initialisiert wurden, enthält rect den Standardwert, der zuvor im Konstruktor oder durch SetDefaultValue festgelegt wurde.

## <a name="canimationrectm_bfixedsize"></a><a name="m_bfixedsize"></a>CAnimationRect::m_bFixedSize

Gibt an, ob das Rechteck eine feste Größe hat.

```
BOOL m_bFixedSize;
```

### <a name="remarks"></a>Bemerkungen

Wenn dieses Element wahr ist, wird die Größe des Rechtecks festgelegt und die rechten und unteren Werte werden jedes Mal neu berechnet, wenn die obere linke Ecke entsprechend der festen Größe verschoben wird. Legen Sie diesen Wert auf TRUE fest, um das Rechteck einfach um den Bildschirm zu bewegen. In diesem Fall werden Übergänge, die auf die rechten und unteren Koordinaten angewendet werden, ignoriert. Die Größe wird intern gespeichert, wenn Sie das Objekt erstellen und/oder SetDefaultValue aufrufen. Standardmäßig ist dieses Element auf FALSE festgelegt.

## <a name="canimationrectm_bottomvalue"></a><a name="m_bottomvalue"></a>CAnimationRect::m_bottomValue

Die gekapselte Animationsvariable, die den unteren Rand des Animationsrechtecks darstellt.

```
CAnimationVariable m_bottomValue;
```

## <a name="canimationrectm_leftvalue"></a><a name="m_leftvalue"></a>CAnimationRect::m_leftValue

Die gekapselte Animationsvariable, die die linke Grenze des Animationsrechtecks darstellt.

```
CAnimationVariable m_leftValue;
```

## <a name="canimationrectm_rightvalue"></a><a name="m_rightvalue"></a>CAnimationRect::m_rightValue

Die gekapselte Animationsvariable, die die rechte Grenze des Animationsrechtecks darstellt.

```
CAnimationVariable m_rightValue;
```

## <a name="canimationrectm_szinitial"></a><a name="m_szinitial"></a>CAnimationRect::m_szInitial

Gibt die Anfangsgröße des Animationsrechtecks an.

```
CSize m_szInitial;
```

## <a name="canimationrectm_topvalue"></a><a name="m_topvalue"></a>CAnimationRect::m_topValue

Die gekapselte Animationsvariable, die die obere Grenze des Animationsrechtecks darstellt.

```
CAnimationVariable m_topValue;
```

## <a name="canimationrectoperator-rect"></a><a name="operator_rect"></a>CAnimationRect::operator RECT

Konvertiert eine CAnimationRect in RECT.

```
operator RECT();
```

### <a name="return-value"></a>Rückgabewert

Aktueller Wert des Animationsrechtecks als RECT.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ruft getValue intern auf. Wenn GetValue aus irgendeinem Grund fehlschlägt, enthält der zurückgegebene RECT Standardwerte für alle Rechteckkoordinaten.

## <a name="canimationrectoperator"></a><a name="operator_eq"></a>CAnimationRect::operator=

Weist CAnimationRect Korrektur zu.

```cpp
void operator=(const RECT& rect);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Der neue Wert des Animationsrechtecks.

### <a name="remarks"></a>Bemerkungen

Es wird empfohlen, dies vor dem Starten der Animation zu tun, da dieser Operator SetDefaultValue aufruft, wodurch die zugrunde liegenden COM-Objekte für Farbkomponenten neu erstellt werden, wenn sie erstellt wurden. Wenn Sie dieses Animationsobjekt für Ereignisse (ValueChanged oder IntegerValueChanged) abonniert haben, müssen Sie diese Ereignisse erneut aktivieren.

## <a name="canimationrectsetdefaultvalue"></a><a name="setdefaultvalue"></a>CAnimationRect::SetDefaultValue

Legt den Standardwert fest.

```cpp
void SetDefaultValue(const CRect& rect);
```

### <a name="parameters"></a>Parameter

*Rect*<br/>
Gibt neue Standardwerte für links, oben, rechts und unten an.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diese Funktion, um einen Standardwert für animationsobjekt festzulegen. Diese Methode weist den Grenzen des Rechtecks Standardwerte zu. Außerdem werden zugrunde liegende COM-Objekte neu erstellt, wenn sie erstellt wurden. Wenn Sie dieses Animationsobjekt für Ereignisse (ValueChanged oder IntegerValueChanged) abonniert haben, müssen Sie diese Ereignisse erneut aktivieren.

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)

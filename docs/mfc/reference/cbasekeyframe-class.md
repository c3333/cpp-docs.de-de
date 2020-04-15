---
title: CBaseKeyFrame-Klasse
ms.date: 11/04/2016
f1_keywords:
- CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::GetAnimationKeyframe
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::IsAdded
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::IsKeyframeAtOffset
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_bIsKeyframeAtOffset
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_keyframe
helpviewer_keywords:
- CBaseKeyFrame [MFC], CBaseKeyFrame
- CBaseKeyFrame [MFC], AddToStoryboard
- CBaseKeyFrame [MFC], GetAnimationKeyframe
- CBaseKeyFrame [MFC], IsAdded
- CBaseKeyFrame [MFC], IsKeyframeAtOffset
- CBaseKeyFrame [MFC], m_bAdded
- CBaseKeyFrame [MFC], m_bIsKeyframeAtOffset
- CBaseKeyFrame [MFC], m_keyframe
ms.assetid: 285a2eff-e7c4-43be-b5aa-737727e6866d
ms.openlocfilehash: 3fcd55f6a157f4b837090a3608fb509b870aae5d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352991"
---
# <a name="cbasekeyframe-class"></a>CBaseKeyFrame-Klasse

Implementiert die grundlegende Funktion eines Keyframe.

## <a name="syntax"></a>Syntax

```
class CBaseKeyFrame : public CObject;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBaseKeyFrame::CBaseKeyFrame](#cbasekeyframe)|Erstellt ein Keyframe-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBaseKeyFrame::AddToStoryboard](#addtostoryboard)|Fügt dem Storyboard ein Keyframe hinzu.|
|[CBaseKeyFrame::GetAnimationKeyframe](#getanimationkeyframe)|Gibt den zugrunde liegenden Keyframe-Wert zurück.|
|[CBaseKeyFrame::IsAdded](#isadded)|Gibt an, ob dem Storyboard ein Keyframe hinzugefügt wurde.|
|[CBaseKeyFrame::IsKeyframeAtOffset](#iskeyframeatoffset)|Gibt an, ob der Keyframe dem Storyboard beim Offset oder nach dem Übergang hinzugefügt werden soll.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CBaseKeyFrame::m_bAdded](#m_badded)|Gibt an, ob dieser Keyframe einem Storyboard hinzugefügt wurde.|
|[CBaseKeyFrame::m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|Gibt an, ob dieser Keyframe dem Storyboard bei einem Offset von einem anderen vorhandenen Keyframe oder am Ende eines Übergangs hinzugefügt werden soll.|
|[CBaseKeyFrame::m_keyframe](#m_keyframe)|Stellt einen Windows-Animations-API-Keyframe dar. Wenn ein Keyframe nicht initialisiert wird, wird er auf den vordefinierten Wert UI_ANIMATION_KEYFRAME_STORYBOARD_START festgelegt.|

## <a name="remarks"></a>Bemerkungen

Kapselt UI_ANIMATION_KEYFRAME Variable. Dient als Basisklasse für jede Keyframe-Implementierung. Ein Keyframe stellt einen Moment in der Zeit innerhalb eines Storyboards dar und kann verwendet werden, um die Anfangs- und Endzeiten von Übergängen anzugeben. Es gibt zwei Arten von Keyframes - Keyframes, die dem Storyboard beim angegebenen Offset (in der Zeit) hinzugefügt wurden, oder Keyframes, die nach dem angegebenen Übergang hinzugefügt wurden. Da die Dauer einiger Übergänge vor dem Start der Animation nicht bekannt sein kann, werden die tatsächlichen Werte einiger Keyframes nur zur Laufzeit bestimmt. Da Keyframes möglicherweise von Übergängen abhängen, die wiederum von Keyframes abhängen, ist es wichtig, beim Erstellen von Keyframe-Ketten unendliche Rekursionen zu vermeiden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CBaseKeyFrame`

## <a name="requirements"></a>Anforderungen

**Header:** afxanimationcontroller.h

## <a name="cbasekeyframeaddtostoryboard"></a><a name="addtostoryboard"></a>CBaseKeyFrame::AddToStoryboard

Fügt dem Storyboard ein Keyframe hinzu.

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parameter

*pStoryboard*<br/>
Ein Zeiger auf ein Storyboard.

*bDeepAdd*<br/>
Wenn dieser Parameter TRUE ist und der hinzugefügte Keyframe von einem anderen Keyframe oder Übergang abhängt, versucht diese Methode, diesen Keyframe oder Übergang zuerst zum Storyboard hinzuzufügen.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn Keyframe erfolgreich zum Storyboard hinzugefügt wurde; andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Diese Methode wird aufgerufen, um dem Storyboard einen Keyframe hinzuzufügen.

## <a name="cbasekeyframecbasekeyframe"></a><a name="cbasekeyframe"></a>CBaseKeyFrame::CBaseKeyFrame

Erstellt ein Keyframe-Objekt.

```
CBaseKeyFrame();
```

## <a name="cbasekeyframegetanimationkeyframe"></a><a name="getanimationkeyframe"></a>CBaseKeyFrame::GetAnimationKeyframe

Gibt den zugrunde liegenden Keyframe-Wert zurück.

```
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;
```

### <a name="return-value"></a>Rückgabewert

Ein aktueller Keyframe. Der Standardwert ist UI_ANIMATION_KEYFRAME_STORYBOARD_START.

### <a name="remarks"></a>Bemerkungen

Dies ist ein Accessor für den zugrunde liegenden Keyframe-Wert.

## <a name="cbasekeyframeisadded"></a><a name="isadded"></a>CBaseKeyFrame::IsAdded

Gibt an, ob dem Storyboard ein Keyframe hinzugefügt wurde.

```
BOOL IsAdded() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn einem Storyboard ein Keyframe hinzugefügt wird; otehrwise FALSE.

### <a name="remarks"></a>Bemerkungen

In der Basisklasse gibt IsAdded immer TRUE zurück, wird aber in abgeleiteten Klassen überschrieben.

## <a name="cbasekeyframeiskeyframeatoffset"></a><a name="iskeyframeatoffset"></a>CBaseKeyFrame::IsKeyframeAtOffset

Gibt an, ob der Keyframe dem Storyboard beim Offset oder nach dem Übergang hinzugefügt werden soll.

```
BOOL IsKeyframeAtOffset() const;
```

### <a name="return-value"></a>Rückgabewert

TRUE, wenn der Keyframe bei einem angegebenen Offset zum Storyboard hinzugefügt werden soll. FALSE, wenn der Keyframe nach einem Übergang zum Storyboard hinzugefügt werden soll.

### <a name="remarks"></a>Bemerkungen

Gibt an, ob der Keyframe beim Offset zum Storyboard hinzugefügt werden soll. Der Offset oder Übergang muss in einer abgeleiteten Klasse angegeben werden.

## <a name="cbasekeyframem_badded"></a><a name="m_badded"></a>CBaseKeyFrame::m_bAdded

Gibt an, ob dieser Keyframe einem Storyboard hinzugefügt wurde.

```
BOOL m_bAdded;
```

## <a name="cbasekeyframem_biskeyframeatoffset"></a><a name="m_biskeyframeatoffset"></a>CBaseKeyFrame::m_bIsKeyframeAtOffset

Gibt an, ob dieser Keyframe dem Storyboard bei einem Offset von einem anderen vorhandenen Keyframe oder am Ende eines Übergangs hinzugefügt werden soll.

```
BOOL m_bIsKeyframeAtOffset;
```

## <a name="cbasekeyframem_keyframe"></a><a name="m_keyframe"></a>CBaseKeyFrame::m_keyframe

Stellt einen Windows-Animations-API-Keyframe dar. Wenn ein Keyframe nicht initialisiert wird, wird er auf den vordefinierten Wert UI_ANIMATION_KEYFRAME_STORYBOARD_START festgelegt.

```
UI_ANIMATION_KEYFRAME m_keyframe;
```

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)

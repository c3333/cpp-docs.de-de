---
title: CKeyFrame-Klasse
ms.date: 11/04/2016
f1_keywords:
- CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAfterTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAtOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetExistingKeyframe
- AFXANIMATIONCONTROLLER/CKeyFrame::GetOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::m_offset
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pExistingKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pTransition
helpviewer_keywords:
- CKeyFrame [MFC], CKeyFrame
- CKeyFrame [MFC], AddToStoryboard
- CKeyFrame [MFC], AddToStoryboardAfterTransition
- CKeyFrame [MFC], AddToStoryboardAtOffset
- CKeyFrame [MFC], GetExistingKeyframe
- CKeyFrame [MFC], GetOffset
- CKeyFrame [MFC], GetTransition
- CKeyFrame [MFC], m_offset
- CKeyFrame [MFC], m_pExistingKeyFrame
- CKeyFrame [MFC], m_pTransition
ms.assetid: d050a562-20f6-4c65-8ce5-ccb3aef1a20e
ms.openlocfilehash: f535503338a82c7cc70455ae6a08cdab0f13c624
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372293"
---
# <a name="ckeyframe-class"></a>CKeyFrame-Klasse

Stellt einen Animationskeyframe dar.

## <a name="syntax"></a>Syntax

```
class CKeyFrame : public CBaseKeyFrame;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CKeyFrame::CKeyFrame](#ckeyframe)|Ist überladen. Erstellt einen Keyframe, der von anderen Keyframes abhängt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CKeyFrame::AddToStoryboard](#addtostoryboard)|Fügt einem Storyboard ein Keyframe hinzu. (Überschreibt [CBaseKeyFrame::AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard).)|
|[CKeyFrame::AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|Fügt dem Storyboard nach dem Übergang ein Keyframe hinzu.|
|[CKeyFrame::AddToStoryboardAtOffset](#addtostoryboardatoffset)|Fügt dem Storyboard beim Offset ein Keyframe hinzu.|
|[CKeyFrame::GetExistingKeyframe](#getexistingkeyframe)|Gibt einen Zeiger auf einen Keyframe zurück, von dem dieser Keyframe abhängt.|
|[CKeyFrame::GetOffset](#getoffset)|Gibt einen Offset von anderen Keyframes zurück.|
|[CKeyFrame::GetTransition](#gettransition)|Gibt einen Zeiger auf einen Übergang zurück, von dem dieser Keyframe abhängt.|

### <a name="protected-data-members"></a>Geschützte Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CKeyFrame::m_offset](#m_offset)|Gibt den Offset dieses Keyframes aus einem in m_pExistingKeyFrame gespeicherten Keyframe an.|
|[CKeyFrame::m_pExistingKeyFrame](#m_pexistingkeyframe)|Speichert einen Zeiger auf einen vorhandenen Keframe. Dieser Keyframe wird dem Storyboard mit m_offset zum vorhandenen Keyframe hinzugefügt.|
|[CKeyFrame::m_pTransition](#m_ptransition)|Speichert einen Zeiger auf die Transtion, der an diesem Keyframe beginnt.|

## <a name="remarks"></a>Bemerkungen

Diese Klasse implementiert einen Animations-Keyframe. Ein Keyframe stellt einen Moment in der Zeit innerhalb eines Storyboards dar und kann verwendet werden, um die Anfangs- und Endzeiten von Übergängen anzugeben. Ein Keyframe kann auf einem anderen Keyframe basieren und einen Offset (in Sekunden) davon haben, oder kann auf einem Übergang basieren und einen Moment darstellen, in dem dieser Übergang endet.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

[CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)

[CKeyFrame](../../mfc/reference/ckeyframe-class.md)

## <a name="requirements"></a>Anforderungen

**Header:** afxanimationcontroller.h

## <a name="ckeyframeaddtostoryboard"></a><a name="addtostoryboard"></a>CKeyFrame::AddToStoryboard

Fügt einem Storyboard ein Keyframe hinzu.

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parameter

*pStoryboard*<br/>
Ein Zeiger auf ein Storyboard.

*bDeepAdd*<br/>
Gibt an, ob Keyframe oder Übergang rekursiv hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn Keyframe erfolgreich hinzugefügt wurde.

### <a name="remarks"></a>Bemerkungen

Diese Methode fügt dem Storyboard einen Keyframe hinzu. Wenn es von anderen Keyframe oder Übergang abhängt und bDeepAdd TRUE ist, versucht diese Methode, sie rekursiv hinzuzufügen.

## <a name="ckeyframeaddtostoryboardaftertransition"></a><a name="addtostoryboardaftertransition"></a>CKeyFrame::AddToStoryboardAfterTransition

Fügt dem Storyboard nach dem Übergang ein Keyframe hinzu.

```
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parameter

*pStoryboard*<br/>
Ein Zeiger auf ein Storyboard.

*bDeepAdd*<br/>
Gibt an, ob ein Übergang rekursiv hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn Keyframe erfolgreich hinzugefügt wurde.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird vom Framework aufgerufen, um dem Storyboard nach dem Übergang einen Keyframe hinzuzufügen.

## <a name="ckeyframeaddtostoryboardatoffset"></a><a name="addtostoryboardatoffset"></a>CKeyFrame::AddToStoryboardAtOffset

Fügt dem Storyboard beim Offset ein Keyframe hinzu.

```
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>Parameter

*pStoryboard*<br/>
Ein Zeiger auf ein Storyboard.

*bDeepAdd*<br/>
Gibt an, ob ein Keyframe hinzugefügt werden soll, von dem dieser Keyframe rekursiv abhängt.

### <a name="return-value"></a>Rückgabewert

TRUE, wenn Keyframe erfolgreich hinzugefügt wurde.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird vom Framework aufgerufen, um dem Storyboard beim Offset einen Keyframe hinzuzufügen.

## <a name="ckeyframeckeyframe"></a><a name="ckeyframe"></a>CKeyFrame::CKeyFrame

Erstellt einen Keyframe, der von einem Übergang abhängt.

```
CKeyFrame(CBaseTransition* pTransition);

CKeyFrame(
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>Parameter

*pTransition*<br/>
Ein Zeiger auf einen Übergang.

*pKeyframe*<br/>
Ein Zeiger auf keyframe.

*offset*<br/>
Offset in Sekunden von Keyframe, der von pKeyframe angegeben wird.

### <a name="remarks"></a>Bemerkungen

Der konstruierte Keyframe stellt einen Moment in der Zeit innerhalb eines Storyboards dar, wenn der angegebene Übergang endet.

## <a name="ckeyframegetexistingkeyframe"></a><a name="getexistingkeyframe"></a>CKeyFrame::GetExistingKeyframe

Gibt einen Zeiger auf einen Keyframe zurück, von dem dieser Keyframe abhängt.

```
CBaseKeyFrame* GetExistingKeyframe();
```

### <a name="return-value"></a>Rückgabewert

Ein gültiger Zeiger auf Keyframe oder NULL, wenn dieser Keyframe nicht von anderen Keyframes abhängt.

### <a name="remarks"></a>Bemerkungen

Dies ist ein Accessor für einen Keyframe, von dem dieser Keyframe abhängt.

## <a name="ckeyframegetoffset"></a><a name="getoffset"></a>CKeyFrame::GetOffset

Gibt einen Offset von anderen Keyframes zurück.

```
UI_ANIMATION_SECONDS GetOffset();
```

### <a name="return-value"></a>Rückgabewert

Ein Offset in Sekunden von anderen Keyframes.

### <a name="remarks"></a>Bemerkungen

Diese Methode sollte aufgerufen werden, um einen Offset in Sekunden von anderen Keyframes zu bestimmen.

## <a name="ckeyframegettransition"></a><a name="gettransition"></a>CKeyFrame::GetTransition

Gibt einen Zeiger auf einen Übergang zurück, von dem dieser Keyframe abhängt.

```
CBaseTransition* GetTransition();
```

### <a name="return-value"></a>Rückgabewert

Ein gültiger Zeiger auf den Übergang oder NULL, wenn dieser Keyframe nicht vom Übergang abhängt.

### <a name="remarks"></a>Bemerkungen

Dies ist ein Accessor für einen Übergang, von dem dieser Keyframe abhängt.

## <a name="ckeyframem_offset"></a><a name="m_offset"></a>CKeyFrame::m_offset

Gibt den Offset dieses Keyframes aus einem in m_pExistingKeyFrame gespeicherten Keyframe an.

```
UI_ANIMATION_SECONDS m_offset;
```

## <a name="ckeyframem_pexistingkeyframe"></a><a name="m_pexistingkeyframe"></a>CKeyFrame::m_pExistingKeyFrame

Speichert einen Zeiger auf einen vorhandenen Keframe. Dieser Keyframe wird dem Storyboard mit m_offset zum vorhandenen Keyframe hinzugefügt.

```
CBaseKeyFrame* m_pExistingKeyFrame;
```

## <a name="ckeyframem_ptransition"></a><a name="m_ptransition"></a>CKeyFrame::m_pTransition

Speichert einen Zeiger auf die Transtion, der an diesem Keyframe beginnt.

```
CBaseTransition* m_pTransition;
```

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)

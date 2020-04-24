---
title: CAnimationTimerEventHandler-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPostUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnPreUpdate
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::OnRenderingTooSlow
- AFXANIMATIONCONTROLLER/CAnimationTimerEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationTimerEventHandler [MFC], CreateInstance
- CAnimationTimerEventHandler [MFC], OnPostUpdate
- CAnimationTimerEventHandler [MFC], OnPreUpdate
- CAnimationTimerEventHandler [MFC], OnRenderingTooSlow
- CAnimationTimerEventHandler [MFC], SetAnimationController
ms.assetid: 188dea3b-4b5e-4f6b-8df9-09d993a21619
ms.openlocfilehash: d1653e50fef03deb8eb23dd9a989d1ca2a529dd8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81755089"
---
# <a name="canimationtimereventhandler-class"></a>CAnimationTimerEventHandler-Klasse

Implementiert einen Rückruf, der von der Animations-API beim Auftreten von Zeitsteuerungsereignissen aufgerufen wird.

## <a name="syntax"></a>Syntax

```
class CAnimationTimerEventHandler : public CUIAnimationTimerEventHandlerBase<CAnimationTimerEventHandler>;
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationTimerEventHandler::CreateInstance](#createinstance)|Erstellt eine `CAnimationTimerEventHandler` Instanz des Rückrufs.|
|[CanimationTimerEventhandler::OnPostUpdate](#onpostupdate)|Behandelt Ereignisse, die nach Abschluss einer Animationsaktualisierung auftreten. (Überschreibt `CUIAnimationTimerEventHandlerBase::OnPostUpdate`.)|
|[CanimationTimerEventhandler::OnPreupdate](#onpreupdate)|Behandelt Ereignisse, die auftreten, bevor eine Animationsaktualisierung beginnt. (Überschreibt `CUIAnimationTimerEventHandlerBase::OnPreUpdate`.)|
|[CanimationTimerEventhandler::OnRenderingTooSlow](#onrenderingtooslow)|Behandelt Ereignisse, die auftreten, wenn die Renderbildrate für eine Animation unter die wünschenswerte Mindestbildrate fällt. (Überschreibt `CUIAnimationTimerEventHandlerBase::OnRenderingTooSlow`.)|
|[CAnimationTimerEventHandler::SetAnimationController](#setanimationcontroller)|Speichert einen Zeiger auf den Animationscontroller, um Ereignisse weiterzuleiten.|

## <a name="remarks"></a>Bemerkungen

Dieser Ereignishandler wird erstellt und an IUIAnimationTimer::SetTimerEventHandler übergeben, wenn Sie CAnimationController::EnableAnimationTimerEventHandler aufrufen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CUIAnimationCallbackBase`

`CUIAnimationTimerEventHandlerBase`

`CAnimationTimerEventHandler`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxanimationcontroller.h

## <a name="canimationtimereventhandlercreateinstance"></a><a name="createinstance"></a>CAnimationTimerEventHandler::CreateInstance

Erstellt eine Instanz von CAnimationTimerEventHandler-Rückruf.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationTimerEventHandler** ppTimerEventHandler);
```

### <a name="parameters"></a>Parameter

*pAnimationController*<br/>
Ein Zeiger auf den Animationscontroller, der Ereignisse empfängt.

*ppTimerEventHandler*

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="canimationtimereventhandleronpostupdate"></a><a name="onpostupdate"></a>CanimationTimerEventhandler::OnPostUpdate

Behandelt Ereignisse, die nach Abschluss einer Animationsaktualisierung auftreten.

```
IFACEMETHOD(OnPostUpdate)();
```

### <a name="return-value"></a>Rückgabewert

S_OK, ob die Methode erfolgreich ist. andernfalls E_FAIL.

## <a name="canimationtimereventhandleronpreupdate"></a><a name="onpreupdate"></a>CanimationTimerEventhandler::OnPreupdate

Behandelt Ereignisse, die auftreten, bevor eine Animationsaktualisierung beginnt.

```
IFACEMETHOD(OnPreUpdate)();
```

### <a name="return-value"></a>Rückgabewert

S_OK, ob die Methode erfolgreich ist. andernfalls E_FAIL.

## <a name="canimationtimereventhandleronrenderingtooslow"></a><a name="onrenderingtooslow"></a>CanimationTimerEventhandler::OnRenderingTooSlow

Behandelt Ereignisse, die auftreten, wenn die Renderbildrate für eine Animation unter die wünschenswerte Mindestbildrate fällt.

```
IFACEMETHOD(OnRenderingTooSlow)(UINT32 fps);
```

### <a name="parameters"></a>Parameter

*Fps*

### <a name="return-value"></a>Rückgabewert

S_OK, ob die Methode erfolgreich ist. andernfalls E_FAIL.

## <a name="canimationtimereventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationTimerEventHandler::SetAnimationController

Speichert einen Zeiger auf den Animationscontroller, um Ereignisse weiterzuleiten.

```cpp
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parameter

*pAnimationController*<br/>
Ein Zeiger auf den Animationscontroller, der Ereignisse empfängt.

## <a name="see-also"></a>Weitere Informationen

[Klassen](../../mfc/reference/mfc-classes.md)

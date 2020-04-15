---
title: CAnimationStoryboardEventHandler-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationStoryboardEventHandler [MFC], CAnimationStoryboardEventHandler
- CAnimationStoryboardEventHandler [MFC], CreateInstance
- CAnimationStoryboardEventHandler [MFC], OnStoryboardStatusChanged
- CAnimationStoryboardEventHandler [MFC], OnStoryboardUpdated
- CAnimationStoryboardEventHandler [MFC], SetAnimationController
ms.assetid: 10a7e86b-c02d-4124-9a2e-61ecf8ac62fc
ms.openlocfilehash: 36b8b524591693775403d66fdc1f0754aaf67778
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365000"
---
# <a name="canimationstoryboardeventhandler-class"></a>CAnimationStoryboardEventHandler-Klasse

Implementiert einen Rückruf, der von der Animations-API aufgerufen wird, wenn der Status eines Drehbuchs geändert oder ein Storyboard aktualisiert wird.

## <a name="syntax"></a>Syntax

```
class CAnimationStoryboardEventHandler : public CUIAnimationStoryboardEventHandlerBase<CAnimationStoryboardEventHandler>;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler](#canimationstoryboardeventhandler)|Erstellt ein `CAnimationStoryboardEventHandler`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationStoryboardEventHandler::CreateInstance](#createinstance)|Erstellt eine `CAnimationStoryboardEventHandler` Instanz des Rückrufs.|
|[CAnimationStoryboardEventHandler::OnStoryboardStatusStatusChanged](#onstoryboardstatuschanged)|Behandelt `OnStoryboardStatusChanged` Ereignisse, die auftreten, wenn sich der Status `CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged`eines Storyboards ändert (Überschreibt .)|
|[CAnimationStoryboardEventHandler::OnStoryboardAktualisiert](#onstoryboardupdated)|Behandelt `OnStoryboardUpdated` Ereignisse, die auftreten, wenn ein Storyboard aktualisiert wird (Überschreibt `CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated`.)|
|[CAnimationStoryboardEventHandler::SetAnimationController](#setanimationcontroller)|Speichert einen Zeiger auf den Animationscontroller, um Ereignisse weiterzuleiten.|

## <a name="remarks"></a>Bemerkungen

Dieser Ereignishandler wird beim `IUIAnimationStoryboard::SetStoryboardEventHandler` Aufrufen `CAnimationController::EnableStoryboardEventHandler`erstellt und an die Methode übergeben.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CUIAnimationCallbackBase`

`CUIAnimationStoryboardEventHandlerBase`

`CAnimationStoryboardEventHandler`

## <a name="requirements"></a>Anforderungen

**Header:** afxanimationcontroller.h

## <a name="canimationstoryboardeventhandlercanimationstoryboardeventhandler"></a><a name="canimationstoryboardeventhandler"></a>CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler

Erstellt ein CAnimationStoryboardEventHandler-Objekt.

```
CAnimationStoryboardEventHandler();
```

## <a name="canimationstoryboardeventhandlercreateinstance"></a><a name="createinstance"></a>CAnimationStoryboardEventHandler::CreateInstance

Erstellt eine Instanz von CAnimationStoryboardEventHandler-Rückruf.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationStoryboardEventHandler** ppHandler);
```

### <a name="parameters"></a>Parameter

*pAnimationController*<br/>
Ein Zeiger auf den Animationscontroller, der Ereignisse empfängt.

*ppHandler*

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="canimationstoryboardeventhandleronstoryboardstatuschanged"></a><a name="onstoryboardstatuschanged"></a>CAnimationStoryboardEventHandler::OnStoryboardStatusStatusChanged

Behandelt OnStoryboardStatusChanged-Ereignisse, die auftreten, wenn sich der Status eines Storyboards ändert

```
IFACEMETHOD(OnStoryboardStatusChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in UI_ANIMATION_STORYBOARD_STATUS newStatus,
    __in UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>Parameter

*Storyboard*<br/>
Ein Zeiger auf das Storyboard, dessen Status sich geändert hat.

*newStatus*<br/>
Gibt den neuen Storyboardstatus an.

*previousStatus*<br/>
Gibt den vorherigen Storyboardstatus an.

### <a name="return-value"></a>Rückgabewert

S_OK, ob die Methode erfolgreich ist. andernfalls E_FAIL.

## <a name="canimationstoryboardeventhandleronstoryboardupdated"></a><a name="onstoryboardupdated"></a>CAnimationStoryboardEventHandler::OnStoryboardAktualisiert

Behandelt OnStoryboardAktualisierte Ereignisse, die auftreten, wenn ein Storyboard aktualisiert wird

```
IFACEMETHOD(OnStoryboardUpdated) (__in IUIAnimationStoryboard* storyboard);
```

### <a name="parameters"></a>Parameter

*Storyboard*<br/>
Ein Zeiger auf das Storyboard, das aktualisiert wurde.

### <a name="return-value"></a>Rückgabewert

S_OK, ob die Methode erfolgreich ist. andernfalls E_FAIL.

## <a name="canimationstoryboardeventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationStoryboardEventHandler::SetAnimationController

Speichert einen Zeiger auf den Animationscontroller, um Ereignisse weiterzuleiten.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parameter

*pAnimationController*<br/>
Ein Zeiger auf den Animationscontroller, der Ereignisse empfängt.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)

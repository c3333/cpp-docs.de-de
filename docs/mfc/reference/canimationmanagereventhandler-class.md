---
title: CAnimationManagerEventHandler-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CAnimationManagerEventHandler
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::OnManagerStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationManagerEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationManagerEventHandler [MFC], CAnimationManagerEventHandler
- CAnimationManagerEventHandler [MFC], CreateInstance
- CAnimationManagerEventHandler [MFC], OnManagerStatusChanged
- CAnimationManagerEventHandler [MFC], SetAnimationController
ms.assetid: 6089ec07-e661-4805-b227-823b4652aade
ms.openlocfilehash: a4e97c2a1188071b5bde0781630d0dfe52e8a72f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369723"
---
# <a name="canimationmanagereventhandler-class"></a>CAnimationManagerEventHandler-Klasse

Implementiert einen Rückruf, der von der Animations-API aufgerufen wird, wenn der Status eines Animations-Managers geändert wird.

## <a name="syntax"></a>Syntax

```
class CAnimationManagerEventHandler : public CUIAnimationManagerEventHandlerBase<CAnimationManagerEventHandler>;
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationManagerEventHandler::CAnimationManagerEventHandler](#canimationmanagereventhandler)|Erstellt ein `CAnimationManagerEventHandler`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CAnimationManagerEventHandler::CreateInstance](#createinstance)|Erstellt eine `CAnimationManagerEventHandler` Instanz des Objekts.|
|[CanimationManagerEventHandler::OnManagerStatusChanged](#onmanagerstatuschanged)|Wird aufgerufen, wenn sich der Status des Animations-Managers geändert hat. (Überschreibt `CUIAnimationManagerEventHandlerBase::OnManagerStatusChanged`.)|
|[CAnimationManagerEventHandler::SetAnimationController](#setanimationcontroller)|Speichert einen Zeiger auf den Animationscontroller, um Ereignisse weiterzuleiten.|

## <a name="remarks"></a>Bemerkungen

Dieser Ereignishandler wird erstellt und an iUIAnimationManager::SetManagerEventHandler-Methode übergeben, wenn Sie CAnimationController::EnableAnimationManagerEvent aufrufen.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CUIAnimationCallbackBase`

`CUIAnimationManagerEventHandlerBase`

`CAnimationManagerEventHandler`

## <a name="requirements"></a>Anforderungen

**Header:** afxanimationcontroller.h

## <a name="canimationmanagereventhandlercanimationmanagereventhandler"></a><a name="canimationmanagereventhandler"></a>CAnimationManagerEventHandler::CAnimationManagerEventHandler

Visual Studio 2010 SP1 wird benötigt.

Erstellt ein CAnimationManagerEventHandler-Objekt.

```
CAnimationManagerEventHandler();
```

## <a name="canimationmanagereventhandlercreateinstance"></a><a name="createinstance"></a>CAnimationManagerEventHandler::CreateInstance

Visual Studio 2010 SP1 wird benötigt.

Erstellt eine Instanz des CAnimationManagerEventHandler-Objekts.

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationManagerEventHandler** ppManagerEventHandler);
```

### <a name="parameters"></a>Parameter

*pAnimationController*<br/>
Ein Zeiger auf den Animationscontroller, der Ereignisse empfängt.

*ppManagerEventHandler*<br/>
Ausgabe Wenn die Methode erfolgreich ist, enthält sie einen Zeiger auf das COM-Objekt, das Statusaktualisierungen an einen Animations-Manager verarbeitet.

### <a name="return-value"></a>Rückgabewert

Wenn die Methode erfolgreich ist, wird S_OK zurückgegeben. Andernfalls wird ein HRESULT-Fehlercode zurückgegeben.

## <a name="canimationmanagereventhandleronmanagerstatuschanged"></a><a name="onmanagerstatuschanged"></a>CanimationManagerEventHandler::OnManagerStatusChanged

Visual Studio 2010 SP1 wird benötigt.

Wird aufgerufen, wenn sich der Status des Animations-Managers geändert hat.

```
IFACEMETHOD(OnManagerStatusChanged)(
    UI_ANIMATION_MANAGER_STATUS newStatus,
    UI_ANIMATION_MANAGER_STATUS previousStatus);
```

### <a name="parameters"></a>Parameter

*newStatus*<br/>
Neuer Status.

*previousStatus*<br/>
Vorheriger Status.

### <a name="return-value"></a>Rückgabewert

Die aktuelle Implementierung gibt immer S_OK zurück.

## <a name="canimationmanagereventhandlersetanimationcontroller"></a><a name="setanimationcontroller"></a>CAnimationManagerEventHandler::SetAnimationController

Visual Studio 2010 SP1 wird benötigt.

Speichert einen Zeiger auf den Animationscontroller, um Ereignisse weiterzuleiten.

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>Parameter

*pAnimationController*<br/>
Ein Zeiger auf den Animationscontroller, der Ereignisse empfängt.

## <a name="see-also"></a>Siehe auch

[Klassen](../../mfc/reference/mfc-classes.md)

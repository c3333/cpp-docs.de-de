---
title: AsyncBase-Klasse
ms.date: 10/08/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase
- async/Microsoft::WRL::AsyncBase::AsyncBase
- async/Microsoft::WRL::AsyncBase::Cancel
- async/Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall
- async/Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall
- async/Microsoft::WRL::AsyncBase::Close
- async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
- async/Microsoft::WRL::AsyncBase::CurrentStatus
- async/Microsoft::WRL::AsyncBase::ErrorCode
- async/Microsoft::WRL::AsyncBase::FireCompletion
- async/Microsoft::WRL::AsyncBase::FireProgress
- async/Microsoft::WRL::AsyncBase::get_ErrorCode
- async/Microsoft::WRL::AsyncBase::get_Id
- async/Microsoft::WRL::AsyncBase::get_Status
- async/Microsoft::WRL::AsyncBase::GetOnComplete
- async/Microsoft::WRL::AsyncBase::GetOnProgress
- async/Microsoft::WRL::AsyncBase::OnCancel
- async/Microsoft::WRL::AsyncBase::OnClose
- async/Microsoft::WRL::AsyncBase::OnStart
- async/Microsoft::WRL::AsyncBase::put_Id
- async/Microsoft::WRL::AsyncBase::PutOnComplete
- async/Microsoft::WRL::AsyncBase::PutOnProgress
- async/Microsoft::WRL::AsyncBase::TryTransitionToCompleted
- async/Microsoft::WRL::AsyncBase::TryTransitionToError
helpviewer_keywords:
- Microsoft::WRL::AsyncBase class
- Microsoft::WRL::AsyncBase::AsyncBase, constructor
- Microsoft::WRL::AsyncBase::Cancel method
- Microsoft::WRL::AsyncBase::CheckValidStateForDelegateCall method
- Microsoft::WRL::AsyncBase::CheckValidStateForResultsCall method
- Microsoft::WRL::AsyncBase::Close method
- Microsoft::WRL::AsyncBase::ContinueAsyncOperation method
- Microsoft::WRL::AsyncBase::CurrentStatus method
- Microsoft::WRL::AsyncBase::ErrorCode method
- Microsoft::WRL::AsyncBase::FireCompletion method
- Microsoft::WRL::AsyncBase::FireProgress method
- Microsoft::WRL::AsyncBase::get_ErrorCode method
- Microsoft::WRL::AsyncBase::get_Id method
- Microsoft::WRL::AsyncBase::get_Status method
- Microsoft::WRL::AsyncBase::GetOnComplete method
- Microsoft::WRL::AsyncBase::GetOnProgress method
- Microsoft::WRL::AsyncBase::OnCancel method
- Microsoft::WRL::AsyncBase::OnClose method
- Microsoft::WRL::AsyncBase::OnStart method
- Microsoft::WRL::AsyncBase::put_Id method
- Microsoft::WRL::AsyncBase::PutOnComplete method
- Microsoft::WRL::AsyncBase::PutOnProgress method
- Microsoft::WRL::AsyncBase::TryTransitionToCompleted method
- Microsoft::WRL::AsyncBase::TryTransitionToError method
ms.assetid: 64259b9b-f427-4ffd-a611-e7a2f82362b2
ms.openlocfilehash: 0254aa4dc243eeffa43850c437a833a6530c01e2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371863"
---
# <a name="asyncbase-class"></a>AsyncBase-Klasse

Implementiert den asynchronen Zustandsautomat der Windows-Runtime.

## <a name="syntax"></a>Syntax

```cpp
template <
    typename TComplete,
    typename TProgress = Details::Nil,
    AsyncResultType resultType = SingleResult
>
class AsyncBase : public AsyncBase<TComplete, Details::Nil, resultType>;

template <typename TComplete, AsyncResultType resultType>
class AsyncBase<TComplete, Details::Nil, resultType> :
    public Microsoft::WRL::Implements<IAsyncInfo>;
```

### <a name="parameters"></a>Parameter

*TComplete*<br/>
Ein Ereignishandler, der aufgerufen wird, wenn ein asynchroner Vorgang abgeschlossen wird.

*TProgress*<br/>
Ein Ereignishandler, der aufgerufen wird, wenn ein ausgeführter asynchroner Vorgang den aktuellen Fortschritt des Vorgangs meldet.

*resultType*<br/>
Einer der AsyncResultType-Enumerationswerte. [AsyncResultType](asyncresulttype-enumeration.md) Standardmäßig `SingleResult`.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                               | BESCHREIBUNG
---------------------------------- | -------------------------------------------------
[AsyncBase::AsyncBase](#asyncbase) | Initialisiert eine Instanz der `AsyncBase`-Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                         | BESCHREIBUNG
-------------------------------------------- | -------------------------------------------------------------------------------------
[AsyncBase::Abbrechen](#cancel)                 | Bricht einen asynchronen Vorgang ab.
[AsyncBase::Schließen](#close)                   | Schließt den asynchronen Vorgang.
[AsyncBase::FireCompletion](#firecompletion) | Ruft den Abschlussereignishandler auf oder setzt den internen Fortschrittsdelegaten zurück.
[AsyncBase::FireProgress](#fireprogress)     | Ruft den aktuellen Fortschrittsereignishandler auf.
[AsyncBase::get_ErrorCode](#get-errorcode)   | Ruft den Fehlercode für den aktuellen asynchronen Vorgang ab.
[AsyncBase::get_Id](#get-id)                 | Ruft das Handle des asynchronen Vorgangs ab.
[AsyncBase::get_Status](#get-status)         | Ruft einen Wert ab, der den Status des asynchronen Vorgangs angibt.
[AsyncBase::GetOnComplete](#getoncomplete)   | Kopiert die Adresse des aktuellen Abschlussereignishandlers in die angegebene Variable.
[AsyncBase::GetOnProgress](#getonprogress)   | Kopiert die Adresse des aktuellen Fortschrittsereignishandlers in die angegebene Variable.
[AsyncBase::put_Id](#put-id)                 | Legt das Handle des asynchronen Vorgangs fest.
[AsyncBase::PutOnComplete](#putoncomplete)   | Legt die Adresse des Abschlussereignishandlers auf den angegebenen Wert fest.
[AsyncBase::PutOnFortschritt](#putonprogress)   | Legt die Adresse des Fortschrittsereignishandlers auf den angegebenen Wert fest.

### <a name="protected-methods"></a>Geschützte Methoden

Name                                                                         | BESCHREIBUNG
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[AsyncBase::CheckValidStateForDelegateCall](#checkvalidstatefordelegatecall) | Testet, ob Delegateigenschaften im aktuellen asynchronen Zustand geändert werden können.
[AsyncBase::CheckValidStateForResultsCall](#checkvalidstateforresultscall)   | Testet, ob die Ergebnisse eines asynchronen Vorgangs im aktuellen asynchronen Zustand erfasst werden können.
[AsyncBase::ContinueAsyncOperation](#continueasyncoperation)                 | Legt fest, ob der asynchrone Vorgang die Verarbeitung fortsetzen oder anhalten soll.
[AsyncBase::CurrentStatus](#currentstatus)                                   | Ruft den Status des aktuellen asynchronen Vorgangs ab.
[AsyncBase::ErrorCode](#errorcode)                                           | Ruft den Fehlercode für den aktuellen asynchronen Vorgang ab.
[AsyncBase::OnCancel](#oncancel)                                             | Wenn in einer abgeleiteten Klasse überschrieben wird, wird ein asynchroner Vorgang abgebrochen.
[AsyncBase::OnClose](#onclose)                                               | Wenn in einer abgeleiteten Klasse überschrieben wird, wird ein asynchroner Vorgang geschlossen.
[AsyncBase::OnStart](#onstart)                                               | Wenn in einer abgeleiteten Klasse überschrieben wird, wird ein asynchroner Vorgang gestartet.
[AsyncBase::Start](#start)                                                   | Startet den asynchronen Vorgang.
[AsyncBase::TryTransitionToCompleted](#trytransitiontocompleted)             | Gibt an, ob der aktuelle asynchrone Vorgang abgeschlossen wurde.
[AsyncBase::TryTransitionToError](#trytransitiontoerror)                     | Gibt an, ob der angegebene Fehlercode den internen Fehlerstatus ändern kann.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** async.h

**Namespace:** Microsoft::WRL

## <a name="asyncbaseasyncbase"></a><a name="asyncbase"></a>AsyncBase::AsyncBase

Initialisiert eine Instanz der `AsyncBase`-Klasse.

```cpp
AsyncBase();
```

## <a name="asyncbasecancel"></a><a name="cancel"></a>AsyncBase::Abbrechen

Bricht einen asynchronen Vorgang ab.

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>Rückgabewert

Standardmäßig wird immer S_OK zurückgegeben.

### <a name="remarks"></a>Bemerkungen

`Cancel()`ist eine Standardimplementierung von `IAsyncInfo::Cancel`, und leistet keine tatsächliche Arbeit. Um einen asynchronen Vorgang tatsächlich `OnCancel()` abzubrechen, überschreiben Sie die reine virtuelle Methode.

## <a name="asyncbasecheckvalidstatefordelegatecall"></a><a name="checkvalidstatefordelegatecall"></a>AsyncBase::CheckValidStateForDelegateCall

Testet, ob Delegateigenschaften im aktuellen asynchronen Zustand geändert werden können.

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>Rückgabewert

S_OK, wenn Delegateigenschaften geändert werden können; andernfalls E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasecheckvalidstateforresultscall"></a><a name="checkvalidstateforresultscall"></a>AsyncBase::CheckValidStateForResultsCall

Testet, ob die Ergebnisse eines asynchronen Vorgangs im aktuellen asynchronen Zustand erfasst werden können.

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>Rückgabewert

S_OK, ob Ergebnisse gesammelt werden können; andernfalls E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseclose"></a><a name="close"></a>AsyncBase::Schließen

Schließt den asynchronen Vorgang.

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>Rückgabewert

S_OK, wenn der Vorgang geschlossen wird oder bereits geschlossen ist. andernfalls E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Bemerkungen

`Close()`ist eine Standardimplementierung von `IAsyncInfo::Close`, und leistet keine tatsächliche Arbeit. Um einen asynchronen Vorgang tatsächlich `OnClose()` zu schließen, überschreiben Sie die reine virtuelle Methode.

## <a name="asyncbasecontinueasyncoperation"></a><a name="continueasyncoperation"></a>AsyncBase::ContinueAsyncOperation

Legt fest, ob der asynchrone Vorgang die Verarbeitung fortsetzen oder anhalten soll.

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>Rückgabewert

**true,** wenn der aktuelle Status des asynchronen Vorgangs *gestartet*wird, was bedeutet, dass der Vorgang fortgesetzt werden soll. Andernfalls **false**, was bedeutet, dass der Vorgang angehalten werden sollte.

## <a name="asyncbasecurrentstatus"></a><a name="currentstatus"></a>AsyncBase::CurrentStatus

Ruft den Status des aktuellen asynchronen Vorgangs ab.

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>Parameter

*Status*<br/>
Der Speicherort, an dem der aktuelle Status gespeichert wird.

### <a name="remarks"></a>Bemerkungen

Dieser Vorgang ist threadsicher.

## <a name="asyncbaseerrorcode"></a><a name="errorcode"></a>AsyncBase::ErrorCode

Ruft den Fehlercode für den aktuellen asynchronen Vorgang ab.

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>Parameter

*error*<br/>
Der Speicherort, an dem der aktuelle Fehlercode gespeichert wird.

### <a name="remarks"></a>Bemerkungen

Dieser Vorgang ist threadsicher.

## <a name="asyncbasefirecompletion"></a><a name="firecompletion"></a>AsyncBase::FireCompletion

Ruft den Abschlussereignishandler auf oder setzt den internen Fortschrittsdelegaten zurück.

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>Bemerkungen

Die erste `FireCompletion()` Version von setzt die interne Fortschrittsdelegatvariable zurück. Die zweite Version ruft den Abschlussereignishandler auf, wenn der asynchrone Vorgang abgeschlossen ist.

## <a name="asyncbasefireprogress"></a><a name="fireprogress"></a>AsyncBase::FireProgress

Ruft den aktuellen Fortschrittsereignishandler auf.

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>Parameter

*arg*<br/>
Die aufzurufende Ereignishandlermethode.

### <a name="remarks"></a>Bemerkungen

`ProgressTraits`wird von [ArgTraitsHelper Structure](argtraitshelper-structure.md)abgeleitet.

## <a name="asyncbaseget_errorcode"></a><a name="get-errorcode"></a>AsyncBase::get_ErrorCode

Ruft den Fehlercode für den aktuellen asynchronen Vorgang ab.

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>Parameter

*Errorcode*<br/>
Der Speicherort, an dem der aktuelle Fehlercode gespeichert wird.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; Andernfalls E_ILLEGAL_METHOD_CALL, wenn der aktuelle asynchrone Vorgang geschlossen wird.

## <a name="asyncbaseget_id"></a><a name="get-id"></a>AsyncBase::get_Id

Ruft das Handle des asynchronen Vorgangs ab.

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>Parameter

*id*<br/>
Der Speicherort, an dem das Handle gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Bemerkungen

Diese Methode implementiert `IAsyncInfo::get_Id`.

## <a name="asyncbaseget_status"></a><a name="get-status"></a>AsyncBase::get_Status

Ruft einen Wert ab, der den Status des asynchronen Vorgangs angibt.

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>Parameter

*Status*<br/>
Der Speicherort, an dem der Status gespeichert werden soll. Weitere Informationen finden `Windows::Foundation::AsyncStatus` Sie unter Enumeration.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Bemerkungen

Diese Methode implementiert `IAsyncInfo::get_Status`.

## <a name="asyncbasegetoncomplete"></a><a name="getoncomplete"></a>AsyncBase::GetOnComplete

Kopiert die Adresse des aktuellen Abschlussereignishandlers in die angegebene Variable.

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>Parameter

*completeHandler*<br/>
Der Speicherort, an dem die Adresse des aktuellen Abschlussereignishandlers gespeichert wird.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasegetonprogress"></a><a name="getonprogress"></a>AsyncBase::GetOnProgress

Kopiert die Adresse des aktuellen Fortschrittsereignishandlers in die angegebene Variable.

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>Parameter

*progressHandler*<br/>
Der Speicherort, an dem die Adresse des aktuellen Fortschrittsereignishandlers gespeichert wird.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseoncancel"></a><a name="oncancel"></a>AsyncBase::OnCancel

Wenn in einer abgeleiteten Klasse überschrieben wird, wird ein asynchroner Vorgang abgebrochen.

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="asyncbaseonclose"></a><a name="onclose"></a>AsyncBase::OnClose

Wenn in einer abgeleiteten Klasse überschrieben wird, wird ein asynchroner Vorgang geschlossen.

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="asyncbaseonstart"></a><a name="onstart"></a>AsyncBase::OnStart

Wenn in einer abgeleiteten Klasse überschrieben wird, wird ein asynchroner Vorgang gestartet.

```cpp
virtual HRESULT OnStart(
   void
) = 0;
```

## <a name="asyncbaseput_id"></a><a name="put-id"></a>AsyncBase::put_Id

Legt das Handle des asynchronen Vorgangs fest.

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>Parameter

*id*<br/>
Ein Nicht-Null-Handle.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls E_INVALIDARG oder E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseputoncomplete"></a><a name="putoncomplete"></a>AsyncBase::PutOnComplete

Legt die Adresse des Abschlussereignishandlers auf den angegebenen Wert fest.

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>Parameter

*completeHandler*<br/>
Die Adresse, auf die der Abschlussereignishandler festgelegt ist.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseputonprogress"></a><a name="putonprogress"></a>AsyncBase::PutOnFortschritt

Legt die Adresse des Fortschrittsereignishandlers auf den angegebenen Wert fest.

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>Parameter

*progressHandler*<br/>
Die Adresse, auf die der Fortschrittsereignishandler festgelegt ist.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasestart"></a><a name="start"></a>AsyncBase::Start

Startet den asynchronen Vorgang.

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>Rückgabewert

S_OK, wenn der Vorgang gestartet wird oder bereits gestartet wurde. andernfalls E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Bemerkungen

`Start()`ist eine geschützte Methode, die extern nicht sichtbar ist, da async-Vorgänge "Hot Start" vor der Rückkehr zum Aufrufer.

## <a name="asyncbasetrytransitiontocompleted"></a><a name="trytransitiontocompleted"></a>AsyncBase::TryTransitionToCompleted

Gibt an, ob der aktuelle asynchrone Vorgang abgeschlossen wurde.

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>Rückgabewert

**true,** wenn der asynchrone Vorgang abgeschlossen wurde; andernfalls **false**.

## <a name="asyncbasetrytransitiontoerror"></a><a name="trytransitiontoerror"></a>AsyncBase::TryTransitionToError

Gibt an, ob der angegebene Fehlercode den internen Fehlerstatus ändern kann.

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>Parameter

*error*<br/>
Ein Fehler HRESULT.

### <a name="return-value"></a>Rückgabewert

**true,** wenn der interne Fehlerstatus geändert wurde; andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Dieser Vorgang ändert den Fehlerstatus nur, wenn der Fehlerstatus bereits auf S_OK festgelegt ist. Dieser Vorgang hat keine Auswirkungen, wenn der Fehlerstatus bereits fehlerhaft, abgebrochen, abgeschlossen oder geschlossen ist.

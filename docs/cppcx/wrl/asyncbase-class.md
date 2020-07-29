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
ms.openlocfilehash: 8684096e76c08456a9c6813b7f04d79b820e41e5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211553"
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

*Tcomplete*<br/>
Ein Ereignishandler, der aufgerufen wird, wenn ein asynchroner Vorgang abgeschlossen wird.

*TProgress*<br/>
Ein Ereignishandler, der aufgerufen wird, wenn ein asynchroner Vorgang ausgeführt wird, der den aktuellen Fortschritt des Vorgangs meldet.

*resultType*<br/>
Einer der [asynkresulttype](asyncresulttype-enumeration.md) -Enumerationswerte. Standardmäßig `SingleResult`.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                               | BESCHREIBUNG
---------------------------------- | -------------------------------------------------
[Asyncbase:: asyncbase](#asyncbase) | Initialisiert eine Instanz der `AsyncBase`-Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

name                                         | BESCHREIBUNG
-------------------------------------------- | -------------------------------------------------------------------------------------
[Asyncbase:: Cancel](#cancel)                 | Bricht einen asynchronen Vorgang ab.
[Asyncbase:: Close](#close)                   | Schließt den asynchronen Vorgang.
[Asyncbase:: firecompletion](#firecompletion) | Ruft den Abschluss Ereignishandler auf oder setzt den internen Fortschritts Delegaten zurück.
[Asyncbase:: FireProgress](#fireprogress)     | Ruft den aktuellen Fortschritts Ereignishandler auf.
[Asyncbase:: get_ErrorCode](#get-errorcode)   | Ruft den Fehlercode für den aktuellen asynchronen Vorgang ab.
[Asyncbase:: get_Id](#get-id)                 | Ruft das Handle des asynchronen Vorgangs ab.
[Asyncbase:: get_Status](#get-status)         | Ruft einen Wert ab, der den Status des asynchronen Vorgangs angibt.
[Asyncbase:: getoncomplete](#getoncomplete)   | Kopiert die Adresse des aktuellen Vervollständigungs Ereignis Handlers in die angegebene Variable.
[Asyncbase:: getonprogress](#getonprogress)   | Kopiert die Adresse des aktuellen Fortschritts Ereignis Handlers in die angegebene Variable.
[Asyncbase::p ut_Id](#put-id)                 | Legt das Handle des asynchronen Vorgangs fest.
[Asyncbase::P utoncomplete](#putoncomplete)   | Legt die Adresse des Vervollständigungs Ereignis Handlers auf den angegebenen Wert fest.
[Asyncbase::P utonprogress](#putonprogress)   | Legt die Adresse des Fortschritts Ereignis Handlers auf den angegebenen Wert fest.

### <a name="protected-methods"></a>Geschützte Methoden

Name                                                                         | BESCHREIBUNG
---------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[Asyncbase:: checkvalidstatefordelegatecall](#checkvalidstatefordelegatecall) | Testet, ob delegateigenschaften im aktuellen asynchronen Zustand geändert werden können.
[Asyncbase:: checkvalidstateforresultscall](#checkvalidstateforresultscall)   | Testet, ob die Ergebnisse eines asynchronen Vorgangs im aktuellen asynchronen Zustand erfasst werden können.
[Asyncbase:: continueasyncoperation](#continueasyncoperation)                 | Bestimmt, ob der asynchrone Vorgang die Verarbeitung fortsetzen soll oder angehalten werden soll.
[Asyncbase:: currentStatus](#currentstatus)                                   | Ruft den Status des aktuellen asynchronen Vorgangs ab.
[Asyncbase:: ErrorCode](#errorcode)                                           | Ruft den Fehlercode für den aktuellen asynchronen Vorgang ab.
[Asyncbase:: OnCancel](#oncancel)                                             | Bricht beim Überschreiben in einer abgeleiteten Klasse einen asynchronen Vorgang ab.
[Asyncbase:: OnClose](#onclose)                                               | Schließt beim Überschreiben in einer abgeleiteten Klasse einen asynchronen Vorgang.
[Asyncbase:: OnStart](#onstart)                                               | Startet beim Überschreiben in einer abgeleiteten Klasse einen asynchronen Vorgang.
[Asyncbase:: Start](#start)                                                   | Startet den asynchronen Vorgang.
[Asyncbase:: trytransitiondeabgeschlossene](#trytransitiontocompleted)             | Gibt an, ob der aktuelle asynchrone Vorgang abgeschlossen wurde.
[Asyncbase:: trytransitiondeerror](#trytransitiontoerror)                     | Gibt an, ob der angegebene Fehlercode den internen Fehlerzustand ändern kann.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`AsyncBase`

`AsyncBase`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Async. h

**Namespace:** Microsoft::WRL

## <a name="asyncbaseasyncbase"></a><a name="asyncbase"></a>Asyncbase:: asyncbase

Initialisiert eine Instanz der `AsyncBase`-Klasse.

```cpp
AsyncBase();
```

## <a name="asyncbasecancel"></a><a name="cancel"></a>Asyncbase:: Cancel

Bricht einen asynchronen Vorgang ab.

```cpp
STDMETHOD(
   Cancel
)(void);
```

### <a name="return-value"></a>Rückgabewert

Standardmäßig gibt immer S_OK zurück.

### <a name="remarks"></a>Bemerkungen

`Cancel()`ist eine Standard Implementierung von `IAsyncInfo::Cancel` , und macht keine tatsächliche Arbeit. Um einen asynchronen Vorgang tatsächlich abzubrechen, überschreiben Sie die `OnCancel()` reine virtuelle Methode.

## <a name="asyncbasecheckvalidstatefordelegatecall"></a><a name="checkvalidstatefordelegatecall"></a>Asyncbase:: checkvalidstatefordelegatecall

Testet, ob delegateigenschaften im aktuellen asynchronen Zustand geändert werden können.

```cpp
inline HRESULT CheckValidStateForDelegateCall();
```

### <a name="return-value"></a>Rückgabewert

S_OK, wenn die delegateigenschaften geändert werden können. Andernfalls E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasecheckvalidstateforresultscall"></a><a name="checkvalidstateforresultscall"></a>Asyncbase:: checkvalidstateforresultscall

Testet, ob die Ergebnisse eines asynchronen Vorgangs im aktuellen asynchronen Zustand erfasst werden können.

```cpp
inline HRESULT CheckValidStateForResultsCall();
```

### <a name="return-value"></a>Rückgabewert

S_OK, wenn Ergebnisse gesammelt werden können. Andernfalls E_ILLEGAL_METHOD_CALLE_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseclose"></a><a name="close"></a>Asyncbase:: Close

Schließt den asynchronen Vorgang.

```cpp
STDMETHOD(
   Close
)(void) override;
```

### <a name="return-value"></a>Rückgabewert

S_OK, wenn der Vorgang geschlossen oder bereits geschlossen wurde. Andernfalls E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Bemerkungen

`Close()`ist eine Standard Implementierung von `IAsyncInfo::Close` , und macht keine tatsächliche Arbeit. Um einen asynchronen Vorgang tatsächlich zu schließen, überschreiben Sie die `OnClose()` reine virtuelle Methode.

## <a name="asyncbasecontinueasyncoperation"></a><a name="continueasyncoperation"></a>Asyncbase:: continueasyncoperation

Bestimmt, ob der asynchrone Vorgang die Verarbeitung fortsetzen soll oder angehalten werden soll.

```cpp
inline bool ContinueAsyncOperation();
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der aktuelle Zustand des asynchronen Vorgangs *gestartet*wird, was bedeutet, dass der Vorgang fortgesetzt werden soll. Andernfalls **`false`** , was bedeutet, dass der Vorgang angehalten werden soll.

## <a name="asyncbasecurrentstatus"></a><a name="currentstatus"></a>Asyncbase:: currentStatus

Ruft den Status des aktuellen asynchronen Vorgangs ab.

```cpp
inline void CurrentStatus(
   Details::AsyncStatusInternal *status
);
```

### <a name="parameters"></a>Parameter

*status*<br/>
Der Speicherort, an dem dieser Vorgang den aktuellen Status speichert.

### <a name="remarks"></a>Bemerkungen

Dieser Vorgang ist Thread sicher.

## <a name="asyncbaseerrorcode"></a><a name="errorcode"></a>Asyncbase:: ErrorCode

Ruft den Fehlercode für den aktuellen asynchronen Vorgang ab.

```cpp
inline void ErrorCode(
   HRESULT *error
);
```

### <a name="parameters"></a>Parameter

*error*<br/>
Der Speicherort, an dem dieser Vorgang den aktuellen Fehlercode speichert.

### <a name="remarks"></a>Bemerkungen

Dieser Vorgang ist Thread sicher.

## <a name="asyncbasefirecompletion"></a><a name="firecompletion"></a>Asyncbase:: firecompletion

Ruft den Abschluss Ereignishandler auf oder setzt den internen Fortschritts Delegaten zurück.

```cpp
void FireCompletion(
   void
) override;

virtual void FireCompletion();
```

### <a name="remarks"></a>Bemerkungen

Die erste Version von `FireCompletion()` setzt die interne Status delegatvariable zurück. Die zweite Version Ruft den Abschluss Ereignishandler auf, wenn der asynchrone Vorgang abgeschlossen ist.

## <a name="asyncbasefireprogress"></a><a name="fireprogress"></a>Asyncbase:: FireProgress

Ruft den aktuellen Fortschritts Ereignishandler auf.

```cpp
void FireProgress(
   const typename ProgressTraits::Arg2Type arg
);
```

### <a name="parameters"></a>Parameter

*gebeut*<br/>
Die aufzurufende Ereignishandlermethode.

### <a name="remarks"></a>Bemerkungen

`ProgressTraits`wird von [argtraitshelper-Struktur](argtraitshelper-structure.md)abgeleitet.

## <a name="asyncbaseget_errorcode"></a><a name="get-errorcode"></a>Asyncbase:: get_ErrorCode

Ruft den Fehlercode für den aktuellen asynchronen Vorgang ab.

```cpp
STDMETHOD(
   get_ErrorCode
)(HRESULT* errorCode) override;
```

### <a name="parameters"></a>Parameter

*ErrorCode*<br/>
Der Speicherort, an dem der aktuelle Fehlercode gespeichert wird.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; Andernfalls E_ILLEGAL_METHOD_CALL, wenn der aktuelle asynchrone Vorgang geschlossen wird.

## <a name="asyncbaseget_id"></a><a name="get-id"></a>Asyncbase:: get_Id

Ruft das Handle des asynchronen Vorgangs ab.

```cpp
STDMETHOD(
   get_Id
)(unsigned int *id) override;
```

### <a name="parameters"></a>Parameter

*id*<br/>
Die Position, an der das Handle gespeichert werden soll.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; Andernfalls E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Bemerkungen

Diese Methode implementiert `IAsyncInfo::get_Id`.

## <a name="asyncbaseget_status"></a><a name="get-status"></a>Asyncbase:: get_Status

Ruft einen Wert ab, der den Status des asynchronen Vorgangs angibt.

```cpp
STDMETHOD(
   get_Status
)(AsyncStatus *status) override;
```

### <a name="parameters"></a>Parameter

*status*<br/>
Der Speicherort, an dem der Status gespeichert werden soll. Weitere Informationen finden Sie unter `Windows::Foundation::AsyncStatus` Enumeration.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; Andernfalls E_ILLEGAL_METHOD_CALL.

### <a name="remarks"></a>Bemerkungen

Diese Methode implementiert `IAsyncInfo::get_Status`.

## <a name="asyncbasegetoncomplete"></a><a name="getoncomplete"></a>Asyncbase:: getoncomplete

Kopiert die Adresse des aktuellen Vervollständigungs Ereignis Handlers in die angegebene Variable.

```cpp
STDMETHOD(
   GetOnComplete
)(TComplete** completeHandler);
```

### <a name="parameters"></a>Parameter

*completeHandler*<br/>
Der Speicherort, an dem die Adresse des aktuellen Vervollständigungs Ereignis Handlers gespeichert wird.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; Andernfalls E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasegetonprogress"></a><a name="getonprogress"></a>Asyncbase:: getonprogress

Kopiert die Adresse des aktuellen Fortschritts Ereignis Handlers in die angegebene Variable.

```cpp
STDMETHOD(
   GetOnProgress
)(TProgress** progressHandler);
```

### <a name="parameters"></a>Parameter

*progressHandler*<br/>
Der Speicherort, an dem die Adresse des aktuellen Fortschritts Ereignis Handlers gespeichert wird.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; Andernfalls E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseoncancel"></a><a name="oncancel"></a>Asyncbase:: OnCancel

Bricht beim Überschreiben in einer abgeleiteten Klasse einen asynchronen Vorgang ab.

```cpp
virtual void OnCancel(
   void
) = 0;
```

## <a name="asyncbaseonclose"></a><a name="onclose"></a>Asyncbase:: OnClose

Schließt beim Überschreiben in einer abgeleiteten Klasse einen asynchronen Vorgang.

```cpp
virtual void OnClose(
   void
) = 0;
```

## <a name="asyncbaseonstart"></a><a name="onstart"></a>Asyncbase:: OnStart

Startet beim Überschreiben in einer abgeleiteten Klasse einen asynchronen Vorgang.

```cpp
virtual HRESULT OnStart(
   void
) = 0;
```

## <a name="asyncbaseput_id"></a><a name="put-id"></a>Asyncbase::p ut_Id

Legt das Handle des asynchronen Vorgangs fest.

```cpp
STDMETHOD(
   put_Id
)(const unsigned int id);
```

### <a name="parameters"></a>Parameter

*id*<br/>
Ein Handle ungleich 0 (null).

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; Andernfalls E_INVALIDARG oder E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseputoncomplete"></a><a name="putoncomplete"></a>Asyncbase::P utoncomplete

Legt die Adresse des Vervollständigungs Ereignis Handlers auf den angegebenen Wert fest.

```cpp
STDMETHOD(
   PutOnComplete
)(TComplete* completeHandler);
```

### <a name="parameters"></a>Parameter

*completeHandler*<br/>
Die Adresse, auf die der Vervollständigungs Ereignishandler festgelegt ist.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; Andernfalls E_ILLEGAL_METHOD_CALL.

## <a name="asyncbaseputonprogress"></a><a name="putonprogress"></a>Asyncbase::P utonprogress

Legt die Adresse des Fortschritts Ereignis Handlers auf den angegebenen Wert fest.

```cpp
STDMETHOD(
   PutOnProgress
)(TProgress* progressHandler);
```

### <a name="parameters"></a>Parameter

*progressHandler*<br/>
Die Adresse, auf die der Fortschritts Ereignishandler festgelegt ist.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; Andernfalls E_ILLEGAL_METHOD_CALL.

## <a name="asyncbasestart"></a><a name="start"></a>Asyncbase:: Start

Startet den asynchronen Vorgang.

```cpp
STDMETHOD(
   Start
)(void);
```

### <a name="return-value"></a>Rückgabewert

S_OK, wenn der Vorgang gestartet oder bereits gestartet wurde. Andernfalls E_ILLEGAL_STATE_CHANGE.

### <a name="remarks"></a>Bemerkungen

`Start()`ist eine geschützte Methode, die nicht extern sichtbar ist, da asynchrone Vorgänge "Hot Start" vor der Rückgabe an den Aufrufer.

## <a name="asyncbasetrytransitiontocompleted"></a><a name="trytransitiontocompleted"></a>Asyncbase:: trytransitiondeabgeschlossene

Gibt an, ob der aktuelle asynchrone Vorgang abgeschlossen wurde.

```cpp
bool TryTransitionToCompleted(
   void
);
```

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der asynchrone Vorgang abgeschlossen wurde. andernfalls **`false`** .

## <a name="asyncbasetrytransitiontoerror"></a><a name="trytransitiontoerror"></a>Asyncbase:: trytransitiondeerror

Gibt an, ob der angegebene Fehlercode den internen Fehlerzustand ändern kann.

```cpp
bool TryTransitionToError(
   const HRESULT error
);
```

### <a name="parameters"></a>Parameter

*error*<br/>
Ein HRESULT-Fehler.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn der interne Fehlerzustand geändert wurde. andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Durch diesen Vorgang wird der Fehlerzustand nur geändert, wenn der Fehlerzustand bereits auf S_OK festgelegt ist. Dieser Vorgang hat keine Auswirkungen, wenn der Fehlerzustand bereits fehlerhaft ist, abgebrochen, abgeschlossen oder geschlossen ist.

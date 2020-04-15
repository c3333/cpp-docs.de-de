---
title: DeferrableEventArgs-Klasse
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::DeferrableEventArgs
- event/Microsoft::WRL::DeferrableEventArgs::GetDeferral
- event/Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished
helpviewer_keywords:
- Microsoft::WRL::DeferrableEventArgs class
- Microsoft::WRL::DeferrableEventArgs::GetDeferral method
- Microsoft::WRL::DeferrableEventArgs::InvokeAllFinished method
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
ms.openlocfilehash: bae2472a75ab77f138fcee0951a6b869cc7c8e82
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372566"
---
# <a name="deferrableeventargs-class"></a>DeferrableEventArgs-Klasse

Eine für die Ereignisargumenttypen für Verzögerungen verwendete Vorlagenklasse.

## <a name="syntax"></a>Syntax

```cpp
template <typename TEventArgsInterface, typename TEventArgsClass>
class DeferrableEventArgs : public TEventArgsInterface;
```

### <a name="parameters"></a>Parameter

*TEventArgsInterface*<br/>
Der Schnittstellentyp, der die Argumente für ein zurückgestelltes Ereignis deklariert.

*TEventArgsClass*<br/>
Die Klasse, die *TEventArgsInterface*implementiert.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

Name                                                         | BESCHREIBUNG
------------------------------------------------------------ | -----------------------------------------------------------------------------------------------------------------------------
[DeferrableEventArgs::GetDeferral](#getdeferral)             | Ruft einen Verweis auf das [Deferral-Objekt](/uwp/api/windows.foundation.deferral) ab, das ein verzögertes Ereignis darstellt.
[DeferrableEventArgs::InvokeAllFinished](#invokeallfinished) | Wird aufgerufen, um anzugeben, dass das Behandeln eines zurückgestellten Ereignisses abgeschlossen ist.

## <a name="remarks"></a>Bemerkungen

Instanzen dieser Klasse werden an die Ereignishandler für zurückgestellte Ereignisse übergeben. Der Vorlagenparameter stellt eine Schnittstelle, die die Details der Ereignisargumente für einen bestimmten Typ eines zurückgestellten Ereignisses definiert, und eine Klasse dar, die diese Schnittstelle implementiert.

Die Klasse wird als erstes Argument in einem Ereignishandler für ein zurückgestelltes Ereignis angezeigt. Sie können die [GetDeferral-Methode](#getdeferral) aufrufen, um das [Deferral-Objekt](/uwp/api/windows.foundation.deferral) abzurufen, von dem Sie alle Informationen über das verzögerte Ereignis abrufen können. Wenn die Ereignisbehandlung abgeschlossen ist, müssen Sie „Complete“ für das Deferral-Objekt aufrufen. Sie sollten dann [InvokeAllFinished](#invokeallfinished) am Ende der Ereignishandlermethode aufrufen, wodurch sichergestellt wird, dass der Abschluss aller verzögerten Ereignisse ordnungsgemäß kommuniziert wird.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** event.h

**Namespace:** Microsoft::WRL

## <a name="deferrableeventargsgetdeferral"></a><a name="getdeferral"></a>DeferrableEventArgs::GetDeferral

Ruft einen Verweis auf das [Deferral-Objekt](/uwp/api/windows.foundation.deferral) ab, das ein verzögertes Ereignis darstellt.

```cpp
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)
```

### <a name="parameters"></a>Parameter

*result*<br/>
Ein Zeiger, der auf das [Deferral-Objekt](/uwp/api/windows.foundation.deferral) verweist, wenn der Aufruf abgeschlossen ist.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

## <a name="deferrableeventargsinvokeallfinished"></a><a name="invokeallfinished"></a>DeferrableEventArgs::InvokeAllFinished

Wird aufgerufen, um anzugeben, dass das Behandeln eines zurückgestellten Ereignisses abgeschlossen ist.

```cpp
void InvokeAllFinished()
```

### <a name="remarks"></a>Bemerkungen

Sie sollten diese Methode aufrufen, nachdem die Ereignisquelle [InvokeAll](eventsource-class.md#invokeall)aufruft. Das Aufrufen dieser Methode verhindert weitere Verzögerungen und erzwingt die Ausführung des Abschlusshandlers, wenn keine Verzögerungen ausgeführt wurden.

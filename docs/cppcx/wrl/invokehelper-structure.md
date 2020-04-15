---
title: InvokeHelper-Struktur
ms.date: 10/18/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper
- event/Microsoft::WRL::Details::InvokeHelper::callback_
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
helpviewer_keywords:
- Microsoft::WRL::Details::InvokeHelper structure
- Microsoft::WRL::Details::callback_ data member
- Microsoft::WRL::Details::Invoke method
- Microsoft::WRL::Details::InvokeHelper, constructor
ms.assetid: 555ad2bc-4dd6-4e65-a2e2-1242c395f0e5
ms.openlocfilehash: 9cb4e166628a6b5e7671494446d467e73c9f8cc3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371386"
---
# <a name="invokehelper-structure"></a>InvokeHelper-Struktur

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template<typename TDelegateInterface, typename TCallback, unsigned int argCount>
struct InvokeHelper;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 0> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 1> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 2> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 3> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 4> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 5> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 6> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 7> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 8> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 9> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;
```

### <a name="parameters"></a>Parameter

*TDelegateInterface*<br/>
Der Delegatschnittstellentyp.

*TCallback*<br/>
Der Typ der Ereignishandlerfunktion.

*argCount*<br/>
Die Anzahl der `InvokeHelper` Argumente in einer Spezialisierung.

## <a name="remarks"></a>Bemerkungen

Stellt eine Implementierung `Invoke()` der Methode basierend auf der angegebenen Anzahl und dem angegebenen Argumenttyp bereit.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

Name     | BESCHREIBUNG
-------- | -----------------------------------------------------------------------------
`Traits` | Ein Synonym für die Klasse, die den Typ jedes Ereignishandlerarguments definiert.

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                        | BESCHREIBUNG
------------------------------------------- | -------------------------------------------------------
[InvokeHelper::InvokeHelper](#invokehelper) | Initialisiert eine neue Instanz der Klasse `InvokeHelper`.

### <a name="public-methods"></a>Öffentliche Methoden

Name                            | BESCHREIBUNG
------------------------------- | -----------------------------------------------------------------------------------
[InvokeHelper::Invoke](#invoke) | Ruft den Ereignishandler auf, dessen Signatur die angegebene Anzahl von Argumenten enthält.

### <a name="public-data-members"></a>Öffentliche Datenmember

Name                                 | BESCHREIBUNG
------------------------------------ | ----------------------------------------------------------
[InvokeHelper::callback_](#callback) | Stellt den Ereignishandler dar, der aufruft, wenn ein Ereignis auftritt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`InvokeHelper`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** event.h

**Namespace:** Microsoft::WRL::Details

## <a name="invokehelpercallback_"></a><a name="callback"></a>InvokeHelper::callback_

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
TCallback callback_;
```

### <a name="remarks"></a>Bemerkungen

Stellt den Ereignishandler dar, der aufruft, wenn ein Ereignis auftritt.

Der `TCallback` Vorlagenparameter gibt den Typ des Ereignishandlers an.

## <a name="invokehelperinvoke"></a><a name="invoke"></a>InvokeHelper::Invoke

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
STDMETHOD(
   Invoke
)();
STDMETHOD(
   Invoke
)(typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
```

### <a name="parameters"></a>Parameter

*arg1*<br/>
Argument 1.

*arg2*<br/>
Argument 2.

*arg3*<br/>
Argument 3.

*arg4*<br/>
Argument 4.

*arg5*<br/>
Argument 5.

*arg6*<br/>
Argument 6.

*arg7*<br/>
Argument 7.

*arg8*<br/>
Argument 8.

*arg9*<br/>
Argument 9.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler beschreibt.

### <a name="remarks"></a>Bemerkungen

Ruft den Ereignishandler auf, dessen Signatur die angegebene Anzahl von Argumenten enthält.

## <a name="invokehelperinvokehelper"></a><a name="invokehelper"></a>InvokeHelper::InvokeHelper

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>Parameter

*Rückruf*<br/>
Ein Ereignishandler.

### <a name="remarks"></a>Bemerkungen

Initialisiert eine neue Instanz der Klasse `InvokeHelper`.

Der `TCallback` Vorlagenparameter gibt den Typ des Ereignishandlers an.

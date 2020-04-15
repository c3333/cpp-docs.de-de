---
title: ActivationFactory-Klasse
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::AddRef
- module/Microsoft::WRL::ActivationFactory::GetIids
- module/Microsoft::WRL::ActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::ActivationFactory::GetTrustLevel
- module/Microsoft::WRL::ActivationFactory::QueryInterface
- module/Microsoft::WRL::ActivationFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ActivationFactory class
- Microsoft::WRL::ActivationFactory::ActivationFactory, constructor
- Microsoft::WRL::ActivationFactory::AddRef method
- Microsoft::WRL::ActivationFactory::GetIids method
- Microsoft::WRL::ActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::ActivationFactory::GetTrustLevel method
- Microsoft::WRL::ActivationFactory::QueryInterface method
- Microsoft::WRL::ActivationFactory::Release method
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
ms.openlocfilehash: 0655caeb3f49a18e9c57c78f0008901aaaedda4a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368706"
---
# <a name="activationfactory-class"></a>ActivationFactory-Klasse

Ermöglicht, dass eine oder mehrere Klassen durch die Windows-Runtime aktiviert werden.

## <a name="syntax"></a>Syntax

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil
>
class ActivationFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IActivationFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<WinRt | InhibitWeakReference>,
        false
    >;
```

### <a name="parameters"></a>Parameter

*I0*<br/>
Die Null-Schnittstelle.

*I1*<br/>
Die erste Schnittstelle.

*I2*<br/>
Die zweite Schnittstelle.

## <a name="remarks"></a>Bemerkungen

`ActivationFactory`bietet Registrierungsmethoden und grundlegende `IActivationFactory` Funktionen für die Schnittstelle. `ActivationFactory`ermöglicht es Ihnen auch, eine benutzerdefinierte Factoryimplementierung bereitzustellen.

Das folgende Codefragment veranschaulicht symbolisch, wie ActivationFactory verwendet wird.

[!code-cpp[wrl-microsoft__wrl__activationfactory#1](../codesnippet/CPP/activationfactory-class_1.cpp)]

Das folgende Codefragment zeigt, wie Sie die [Implements-Struktur](implements-structure.md) verwenden, um mehr als drei Schnittstellen-IDs anzugeben.

`struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                                       | BESCHREIBUNG
---------------------------------------------------------- | ------------------------------------------
[ActivationFactory::ActivationFactory](#activationfactory) | Initialisiert die `ActivationFactory`-Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                                           | BESCHREIBUNG
-------------------------------------------------------------- | --------------------------------------------------------------------------------------------
[ActivationFactory::AddRef](#addref)                           | Inkrementiert die Referenzanzahl des aktuellen `ActivationFactory` Objekts.
[AktivierungFactory::GetIids](#getiids)                         | Ruft ein Array implementierter Schnittstellen-IDs ab.
[ActivationFactory::GetRuntimeClassName](#getruntimeclassname) | Ruft den Laufzeitklassennamen des Objekts `ActivationFactory` ab, das das aktuelle Instanziiert.
[ActivationFactory::GetTrustLevel](#gettrustlevel)             | Ruft die Vertrauensstufe des Objekts ab, das das aktuelle `ActivationFactory` Instanziiert wird.
[ActivationFactory::QueryInterface](#queryinterface)           | Ruft einen Zeiger auf die angegebene Schnittstelle ab.
[ActivationFactory::Release](#release)                         | Dekrementiert die Referenzanzahl `ActivationFactory` des aktuellen Objekts.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`I0`

`ChainInterfaces`

`I0`

`RuntimeClassBase`

`ImplementsHelper`

`DontUseNewUseMake`

`RuntimeClassFlags`

`RuntimeClassBaseT`

`RuntimeClass`

`ActivationFactory`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** module.h

**Namespace:** Microsoft::WRL

## <a name="activationfactoryactivationfactory"></a><a name="activationfactory"></a>ActivationFactory::ActivationFactory

Initialisiert die `ActivationFactory`-Klasse.

```cpp
ActivationFactory();
```

## <a name="activationfactoryaddref"></a><a name="addref"></a>ActivationFactory::AddRef

Inkrementiert die Referenzanzahl des aktuellen `ActivationFactory` Objekts.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Rückgabewert

„S_OK“ im Erfolgsfall, andernfalls ein HRESULT, das den Fehler beschreibt.

## <a name="activationfactorygetiids"></a><a name="getiids"></a>AktivierungFactory::GetIids

Ruft ein Array implementierter Schnittstellen-IDs ab.

```cpp
STDMETHOD(
   GetIids
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Parameter

*iidCount*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird die Anzahl der Interace-IDs im *iids-Array.*

*iids*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird ein Array implementierter Schnittstellen-IDs verwendet.

### <a name="return-value"></a>Rückgabewert

„S_OK“ im Erfolgsfall, andernfalls ein HRESULT, das den Fehler beschreibt. E_OUTOFMEMORY ist ein möglicher Fehler HRESULT.

## <a name="activationfactorygetruntimeclassname"></a><a name="getruntimeclassname"></a>ActivationFactory::GetRuntimeClassName

Ruft den Laufzeitklassennamen des Objekts `ActivationFactory` ab, das das aktuelle Instanziiert.

```cpp
STDMETHOD(
   GetRuntimeClassName
)(_Out_ HSTRING* runtimeName);
```

### <a name="parameters"></a>Parameter

*runtimeName*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird ein Handle für eine Zeichenfolge, `ActivationFactory` die den Laufzeitklassennamen des Objekts enthält, das das aktuelle Instanziiert behandelt.

### <a name="return-value"></a>Rückgabewert

„S_OK“ im Erfolgsfall, andernfalls ein HRESULT, das den Fehler beschreibt.

## <a name="activationfactorygettrustlevel"></a><a name="gettrustlevel"></a>ActivationFactory::GetTrustLevel

Ruft die Vertrauensstufe des Objekts ab, das das aktuelle `ActivationFactory` Instanziiert wird.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>Parameter

*trustLvl*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird die Vertrauensstufe der Laufzeitklasse, die die `ActivationFactory` Instanziiert-

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; Andernfalls wird ein Assertionsfehler ausgesendet, und `FullTrust` *trustLvl* wird auf festgelegt.

## <a name="activationfactoryqueryinterface"></a><a name="queryinterface"></a>ActivationFactory::QueryInterface

Ruft einen Zeiger auf die angegebene Schnittstelle ab.

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Parameter

*riid*<br/>
Eine Schnittstellen-ID.

*ppvObject*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird ein Zeiger auf die Schnittstelle angezeigt, die durch den Parameter *riid*angegeben wird.

### <a name="return-value"></a>Rückgabewert

„S_OK“ im Erfolgsfall, andernfalls ein HRESULT, das den Fehler beschreibt.

## <a name="activationfactoryrelease"></a><a name="release"></a>ActivationFactory::Release

Dekrementiert die Referenzanzahl `ActivationFactory` des aktuellen Objekts.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Rückgabewert

„S_OK“ im Erfolgsfall, andernfalls ein HRESULT, das den Fehler beschreibt.

---
title: ClassFactory-Klasse
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory
- module/Microsoft::WRL::ClassFactory::AddRef
- module/Microsoft::WRL::ClassFactory::ClassFactory
- module/Microsoft::WRL::ClassFactory::LockServer
- module/Microsoft::WRL::ClassFactory::QueryInterface
- module/Microsoft::WRL::ClassFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ClassFactory class
- Microsoft::WRL::ClassFactory::AddRef method
- Microsoft::WRL::ClassFactory::ClassFactory, constructor
- Microsoft::WRL::ClassFactory::LockServer method
- Microsoft::WRL::ClassFactory::QueryInterface method
- Microsoft::WRL::ClassFactory::Release method
ms.assetid: f13e6bce-722b-4f18-b7cf-3ffa6345c1db
ms.openlocfilehash: 3b738cc8f439e6653162ab99b0a26e87aa8fee36
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372666"
---
# <a name="classfactory-class"></a>ClassFactory-Klasse

Implementiert die grundlegende Funktion der `IClassFactory`-Schnittstelle.

## <a name="syntax"></a>Syntax

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil
>
class ClassFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IClassFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<ClassicCom | InhibitWeakReference>,
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

Verwenden `ClassFactory` Sie diese, um eine benutzerdefinierte Factoryimplementierung bereitzustellen.

Das folgende Programmiermuster veranschaulicht, wie die [Implements-Struktur](implements-structure.md) verwendet wird, um mehr als drei Schnittstellen in einer Klassenfactory anzugeben.

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                        | BESCHREIBUNG
------------------------------------------- | -----------
[ClassFactory::ClassFactory](#classfactory) |

### <a name="public-methods"></a>Öffentliche Methoden

Name                                            | BESCHREIBUNG
----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------
[ClassFactory::AddRef](#addref)                 | Inkrementiert die Referenzanzahl für das aktuelle `ClassFactory` Objekt.
[ClassFactory::LockServer](#lockserver)         | Erhöht oder dekrementiert die Anzahl der zugrunde liegenden `ClassFactory` Objekte, die vom aktuellen Objekt nachverfolgt werden.
[ClassFactory::QueryInterface](#queryinterface) | Ruft einen Zeiger auf die schnittstelle ab, die durch Parameter angegeben wird.
[ClassFactory::Release](#release)               | Dekrementiert die Referenzanzahl `ClassFactory` für das aktuelle Objekt.

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

`ClassFactory`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** module.h

**Namespace:** Microsoft::WRL

## <a name="classfactoryaddref"></a><a name="addref"></a>ClassFactory::AddRef

Inkrementiert die Referenzanzahl für das aktuelle `ClassFactory` Objekt.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Rückgabewert

„S_OK“ im Erfolgsfall, andernfalls ein HRESULT, das den Fehler beschreibt.

## <a name="classfactoryclassfactory"></a><a name="classfactory"></a>ClassFactory::ClassFactory

```cpp
WRL_NOTHROW ClassFactory();
```

## <a name="classfactorylockserver"></a><a name="lockserver"></a>ClassFactory::LockServer

Erhöht oder dekrementiert die Anzahl der zugrunde liegenden `ClassFactory` Objekte, die vom aktuellen Objekt nachverfolgt werden.

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>Parameter

*Herde*<br/>
**true,** um die Anzahl der nachverfolgten Objekte zu erhöhen. **false,** um die Anzahl der verfolgten Objekte zu dekrementodienen.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls E_FAIL.

### <a name="remarks"></a>Bemerkungen

`ClassFactory`verfolgt Objekte in einer zugrunde liegenden Instanz der [Modulklasse.](module-class.md)

## <a name="classfactoryqueryinterface"></a><a name="queryinterface"></a>ClassFactory::QueryInterface

Ruft einen Zeiger auf die schnittstelle ab, die durch Parameter angegeben wird.

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

## <a name="classfactoryrelease"></a><a name="release"></a>ClassFactory::Release

Dekrementiert die Referenzanzahl `ClassFactory` für das aktuelle Objekt.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Rückgabewert

„S_OK“ im Erfolgsfall, andernfalls ein HRESULT, das den Fehler beschreibt.

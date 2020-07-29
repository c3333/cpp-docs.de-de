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
ms.openlocfilehash: bbf20e2269e6d62206e06e748174d7b88898cd68
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87198098"
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
Die nullten-Schnittstelle.

*I1*<br/>
Die erste Schnittstelle.

*I2*<br/>
Die zweite-Schnittstelle.

## <a name="remarks"></a>Bemerkungen

Verwenden `ClassFactory` Sie, um eine benutzerdefinierte Factory-Implementierung bereitzustellen.

Das folgende Programmier Muster veranschaulicht, wie die [implementierte](implements-structure.md) -Struktur verwendet wird, um mehr als drei Schnittstellen in einer Klassenfactory anzugeben.

`struct MyFactory : ClassFactory<Implements<I1, I2, I3>, I4, I5>`

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                        | BESCHREIBUNG
------------------------------------------- | -----------
[ClassFactory:: ClassFactory](#classfactory) |

### <a name="public-methods"></a>Öffentliche Methoden

name                                            | BESCHREIBUNG
----------------------------------------------- | ----------------------------------------------------------------------------------------------------------------
[ClassFactory:: adressf](#addref)                 | Erhöht den Verweis Zähler für das aktuelle- `ClassFactory` Objekt.
[ClassFactory:: LockServer](#lockserver)         | Erhöht oder verringert die Anzahl der zugrunde liegenden Objekte, die vom aktuellen-Objekt nachverfolgt werden `ClassFactory` .
[ClassFactory:: QueryInterface](#queryinterface) | Ruft einen Zeiger auf die durch den-Parameter angegebene Schnittstelle ab.
[ClassFactory:: Release](#release)               | Dekremente den Verweis Zähler für das aktuelle- `ClassFactory` Objekt.

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

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Module. h

**Namespace:** Microsoft::WRL

## <a name="classfactoryaddref"></a><a name="addref"></a>ClassFactory:: adressf

Erhöht den Verweis Zähler für das aktuelle- `ClassFactory` Objekt.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Rückgabewert

„S_OK“ im Erfolgsfall, andernfalls ein HRESULT, das den Fehler beschreibt.

## <a name="classfactoryclassfactory"></a><a name="classfactory"></a>ClassFactory:: ClassFactory

```cpp
WRL_NOTHROW ClassFactory();
```

## <a name="classfactorylockserver"></a><a name="lockserver"></a>ClassFactory:: LockServer

Erhöht oder verringert die Anzahl der zugrunde liegenden Objekte, die vom aktuellen-Objekt nachverfolgt werden `ClassFactory` .

```cpp
STDMETHOD(
   LockServer
)(BOOL fLock);
```

### <a name="parameters"></a>Parameter

*Vögel*<br/>
**`true`** um die Anzahl der überwachten Objekte zu erhöhen. **`false`**, um die Anzahl der überwachten Objekte zu verringern.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls E_FAIL.

### <a name="remarks"></a>Bemerkungen

`ClassFactory`verfolgt Objekte in einer zugrunde liegenden Instanz der [Modul](module-class.md) Klasse.

## <a name="classfactoryqueryinterface"></a><a name="queryinterface"></a>ClassFactory:: QueryInterface

Ruft einen Zeiger auf die durch den-Parameter angegebene Schnittstelle ab.

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Parameter

*riid*<br/>
Eine Schnittstellen-ID.

*ppvObject*<br/>
Wenn dieser Vorgang abgeschlossen ist, ein Zeiger auf die Schnittstelle, die durch den Parameter *riid*angegeben wird.

### <a name="return-value"></a>Rückgabewert

„S_OK“ im Erfolgsfall, andernfalls ein HRESULT, das den Fehler beschreibt.

## <a name="classfactoryrelease"></a><a name="release"></a>ClassFactory:: Release

Dekremente den Verweis Zähler für das aktuelle- `ClassFactory` Objekt.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Rückgabewert

„S_OK“ im Erfolgsfall, andernfalls ein HRESULT, das den Fehler beschreibt.

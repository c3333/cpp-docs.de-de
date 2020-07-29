---
title: SimpleClassFactory-Klasse
ms.date: 09/7/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory
- module/Microsoft::WRL::SimpleClassFactory::CreateInstance
helpviewer_keywords:
- Microsoft::WRL::SimpleClassFactory class
- Microsoft::WRL::SimpleClassFactory::CreateInstance method
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
ms.openlocfilehash: 66794789e51a2635fae646cca49e4fae8385dfe0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211150"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory-Klasse

Stellt einen grundlegenden Mechanismus zum Erstellen einer Basisklasse bereit.

## <a name="syntax"></a>Syntax

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>Parameter

*Sock*<br/>
Eine Basisklasse.

## <a name="remarks"></a>Bemerkungen

Die Basisklasse muss einen Standardkonstruktor bereitstellen.

Im folgenden Codebeispiel wird die Verwendung `SimpleClassFactory` von mit dem [activatableclasswithfactoryex](activatableclass-macros.md) -Makro veranschaulicht.

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[SimpleClassFactory::CreateInstance-Methode](#createinstance)|Erstellt eine Instanz der angegebenen-Schnittstelle.|

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

`SimpleClassFactory`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** Module. h

**Namespace:** Microsoft::WRL

## <a name="simpleclassfactorycreateinstance-method"></a><a name="createinstance"></a>Simpleclassfactory:: kreateinstance-Methode

Erstellt eine Instanz der angegebenen-Schnittstelle.

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

#### <a name="parameters"></a>Parameter

*pUnkOuter*<br/>
Muss sein **`nullptr`** ; andernfalls ist der Rückgabewert CLASS_E_NOAGGREGATION.

Simpleclassfactory unterstützt keine Aggregation. Wenn Aggregationen unterstützt werden und das zu erstellende Objekt Teil eines Aggregats war, wäre *pUnkOuter* ein Zeiger auf die Steuerungs `IUnknown` Schnittstelle des Aggregats.

*riid*<br/>
Die Schnittstellen-ID des zu erstellenden Objekts.

*ppvObject*<br/>
Wenn dieser Vorgang abgeschlossen ist, Zeiger auf eine Instanz des Objekts, das durch den *riid* -Parameter angegeben wird.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

### <a name="remarks"></a>Bemerkungen

Wenn `__WRL_STRICT__` definiert ist, wird ein Fehler vom Typ Assert ausgegeben, wenn die im Klassen Vorlagen Parameter angegebene Basisklasse nicht von [runtimeclass](runtimeclass-class.md)abgeleitet ist oder nicht mit dem-Enumerationswert classiccom oder winrtclassiccommix [runtimeclasstype](runtimeclasstype-enumeration.md) konfiguriert wurde.

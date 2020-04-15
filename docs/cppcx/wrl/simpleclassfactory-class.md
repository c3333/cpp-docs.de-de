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
ms.openlocfilehash: 924b9d2c30f11e6f0444d9c647807f1c86dcc411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373550"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory-Klasse

Stellt einen grundlegenden Mechanismus zum Erstellen einer Basisklasse bereit.

## <a name="syntax"></a>Syntax

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>Parameter

*Basis*<br/>
Eine Basisklasse.

## <a name="remarks"></a>Bemerkungen

Die Basisklasse muss einen Standardkonstruktor bereitstellen.

Im folgenden Codebeispiel wird `SimpleClassFactory` veranschaulicht, wie Sie das [ActivatableClassWithFactoryEx-Makro](activatableclass-macros.md) verwenden.

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[SimpleClassFactory::CreateInstance-Methode](#createinstance)|Erstellt eine Instanz der angegebenen Schnittstelle.|

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

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** module.h

**Namespace:** Microsoft::WRL

## <a name="simpleclassfactorycreateinstance-method"></a><a name="createinstance"></a>SimpleClassFactory::CreateInstance-Methode

Erstellt eine Instanz der angegebenen Schnittstelle.

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

#### <a name="parameters"></a>Parameter

*pUnkOuter*<br/>
Muss `nullptr`sein ; Andernfalls wird der Rückgabewert CLASS_E_NOAGGREGATION.

SimpleClassFactory unterstützt keine Aggregation. Wenn die Aggregation unterstützt würde und das zu erstellende Objekt Teil eines Aggregats `IUnknown` wäre, wäre *pUnkOuter* ein Zeiger auf die steuernde Schnittstelle des Aggregats.

*riid*<br/>
Schnittstellen-ID des zu erstellenden Objekts.

*ppvObject*<br/>
Wenn dieser Vorgang abgeschlossen ist, zeigen Sie auf eine Instanz des Objekts, die durch den *riid-Parameter* angegeben wird.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

### <a name="remarks"></a>Bemerkungen

Wenn `__WRL_STRICT__` definiert, wird ein Assert-Fehler angezeigt, wenn die im Klassenvorlagenparameter angegebene Basisklasse nicht von [RuntimeClass](runtimeclass-class.md)abgeleitet oder nicht mit dem Enumerationswert ClassicCom oder WinRtClassicComMix [RuntimeClassType](runtimeclasstype-enumeration.md) konfiguriert ist.

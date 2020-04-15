---
title: SimpleActivationFactory-Klasse
ms.date: 09/07/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory
- module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
- module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
helpviewer_keywords:
- Microsoft::WRL::SimpleActivationFactory class
- Microsoft::WRL::SimpleActivationFactory::ActivateInstance method
- Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::SimpleActivationFactory::GetTrustLevel method
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
ms.openlocfilehash: 39e539c63e91b508f51656114ee8fbd68150991f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370937"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory-Klasse

Stellt einen grundlegenden Mechanismus für das Erstellen einer Windows-Runtime oder einer klassischen COM-Basisklasse bereit.

## <a name="syntax"></a>Syntax

```cpp
template<typename Base>
class SimpleActivationFactory : public ActivationFactory<>;
```

### <a name="parameters"></a>Parameter

*Basis*<br/>
Eine Basisklasse.

## <a name="remarks"></a>Bemerkungen

Die Basisklasse muss einen Standardkonstruktor bereitstellen.

Im folgenden Codebeispiel wird veranschaulicht, wie SimpleActivationFactory mit dem [ActivatableClassWithFactoryEx-Makro](activatableclass-macros.md) verwendet wird.

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance-Methode](#activateinstance)|Erstellt eine Instanz der angegebenen Schnittstelle.|
|[SimpleActivationFactory::GetRuntimeClassName-Methode](#getruntimeclassname)|Ruft den Laufzeitklassennamen einer Instanz der Klasse ab, die durch den *Vorlagenparameter der Basisklasse* angegeben wird.|
|[SimpleActivationFactory::GetTrustLevel-Methode](#gettrustlevel)|Ruft die Vertrauensstufe einer Instanz der Klasse ab, die durch den *Vorlagenparameter der Basisklasse* angegeben wird.|

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

`SimpleActivationFactory`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** module.h

**Namespace:** Microsoft::WRL

## <a name="simpleactivationfactoryactivateinstance-method"></a><a name="activateinstance"></a>SimpleActivationFactory::ActivateInstance-Methode

Erstellt eine Instanz der angegebenen Schnittstelle.

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

#### <a name="parameters"></a>Parameter

*ppvObject*<br/>
Wenn dieser Vorgang abgeschlossen ist, zeigen Sie auf `Base` eine Instanz des Objekts, die durch den Klassenvorlagenparameter angegeben wird.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

### <a name="remarks"></a>Bemerkungen

Wenn `__WRL_STRICT__` definiert, wird ein Assert-Fehler angezeigt, wenn die im Klassenvorlagenparameter angegebene Basisklasse nicht von [RuntimeClass](runtimeclass-class.md)abgeleitet oder nicht mit dem Enumerationswert WinRt oder WinRtClassicComMix [RuntimeClassType](runtimeclasstype-enumeration.md) konfiguriert ist.

## <a name="simpleactivationfactorygetruntimeclassname-method"></a><a name="getruntimeclassname"></a>SimpleActivationFactory::GetRuntimeClassName-Methode

Ruft den Laufzeitklassennamen einer Instanz der Klasse `Base` ab, die durch den Klassenvorlagenparameter angegeben wird.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

#### <a name="parameters"></a>Parameter

*runtimeName*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird der Name der Laufzeitklasse ausgeführt.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

### <a name="remarks"></a>Bemerkungen

Wenn `__WRL_STRICT__` definiert, wird ein Assert-Fehler angezeigt, wenn `Base` die vom Klassenvorlagenparameter angegebene Klasse nicht von [RuntimeClass](runtimeclass-class.md)abgeleitet oder nicht mit dem Enumerationswert WinRt oder WinRtClassicComMix [RuntimeClassType](runtimeclasstype-enumeration.md) konfiguriert ist.

## <a name="simpleactivationfactorygettrustlevel-method"></a><a name="gettrustlevel"></a>SimpleActivationFactory::GetTrustLevel-Methode

Ruft die Vertrauensstufe einer Instanz der `Base` Klasse ab, die durch den Klassenvorlagenparameter angegeben wird.

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

#### <a name="parameters"></a>Parameter

*trustLvl*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird die Vertrauensstufe des aktuellen Klassenobjekts abgeschlossen.

### <a name="return-value"></a>Rückgabewert

Immer S_OK.

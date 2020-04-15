---
title: RuntimeClass-Klasse
ms.date: 09/11/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass
- implements/Microsoft::WRL::RuntimeClass::AddRef
- implements/Microsoft::WRL::RuntimeClass::DecrementReference
- implements/Microsoft::WRL::RuntimeClass::GetIids
- implements/Microsoft::WRL::RuntimeClass::GetRuntimeClassName
- implements/Microsoft::WRL::RuntimeClass::GetTrustLevel
- implements/Microsoft::WRL::RuntimeClass::GetWeakReference
- implements/Microsoft::WRL::RuntimeClass::InternalAddRef
- implements/Microsoft::WRL::RuntimeClass::QueryInterface
- implements/Microsoft::WRL::RuntimeClass::Release
- implements/Microsoft::WRL::RuntimeClass::RuntimeClass
- implements/Microsoft::WRL::RuntimeClass::~RuntimeClass
helpviewer_keywords:
- Microsoft::WRL::RuntimeClass class
- Microsoft::WRL::RuntimeClass::AddRef method
- Microsoft::WRL::RuntimeClass::DecrementReference method
- Microsoft::WRL::RuntimeClass::GetIids method
- Microsoft::WRL::RuntimeClass::GetRuntimeClassName method
- Microsoft::WRL::RuntimeClass::GetTrustLevel method
- Microsoft::WRL::RuntimeClass::GetWeakReference method
- Microsoft::WRL::RuntimeClass::InternalAddRef method
- Microsoft::WRL::RuntimeClass::QueryInterface method
- Microsoft::WRL::RuntimeClass::Release method
- Microsoft::WRL::RuntimeClass::RuntimeClass, constructor
- Microsoft::WRL::RuntimeClass::~RuntimeClass, destructor
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
ms.openlocfilehash: 64b4124ba3c60fdcb53fc29c7b791c0f73a49579
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376233"
---
# <a name="runtimeclass-class"></a>RuntimeClass-Klasse

Stellt eine WinRT- oder COM-Klasse dar, die die angegebenen Schnittstellen erbt und die angegebene Windows-Runtime, klassische COM- und schwache Referenzunterstützung bereitstellt.

Diese Klasse stellt die Boilerplate-Implementierung von WinRT- `QueryInterface` `AddRef`und `Release` COM-Klassen bereit und stellt die Implementierung von , usw. bereit, verwaltet die Referenzanzahl des Moduls und unterstützt die Bereitstellung der Klassenfactory für aktivierbare Objekte.

## <a name="syntax"></a>Syntax

```cpp
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```

### <a name="parameters"></a>Parameter

*classFlags*<br/>
Dieser Parameter ist optional. Eine Kombination aus einem oder mehreren RuntimeClassType-Enumerationswerten. [RuntimeClassType](runtimeclasstype-enumeration.md) Das `__WRL_CONFIGURATION_LEGACY__` Makro kann definiert werden, um den Standardwert von classFlags für alle Laufzeitklassen im Projekt zu ändern. Wenn definiert, sind RuntimeClass-Instanzen standardmäßig nicht agil. Wenn nicht definiert, sind RuntimeClass-Instanzen standardmäßig agil. Um Mehrdeutigkeiten zu `Microsoft::WRL::FtmBase` `TInterfaces` vermeiden, geben Sie immer die in oder `RuntimeClassType::InhibitFtmBase`an. Beachten Sie, dass das Objekt agil ist, wenn InhibitFtmBase und FtmBase beide verwendet werden.

*TInterfaces*<br/>
Die Liste der Schnittstellen, die `IUnknown` `IInspectable` das Objekt über implementiert, oder andere Schnittstellen, die von [RuntimeClassType](runtimeclasstype-enumeration.md)gesteuert werden. Es kann auch andere Klassen auflisten, von die abgeleitet werden soll, insbesondere `Microsoft::WRL::FtmBase` um das Objekt agil zu machen und zu bewirken, dass es implementiert `IMarshal`wird.

## <a name="members"></a>Member

`RuntimeClassInitialize`<br/>
Eine Funktion, die das Objekt `MakeAndInitialize` initialisiert, wenn die Vorlagenfunktion zum Erstellen des Objekts verwendet wird. Es gibt S_OK zurück, wenn das Objekt erfolgreich initialisiert wurde, oder einen COM-Fehlercode, wenn die Initialisierung fehlgeschlagen ist. Der COM-Fehlercode wird als Rückgabewert `MakeAndInitialize`von weitergegeben. Beachten Sie, dass die `RuntimeClassInitialize` `Make` Methode nicht aufgerufen wird, wenn die Vorlagenfunktion zum Erstellen des Objekts verwendet wird.

### <a name="public-constructors"></a>Öffentliche Konstruktoren

| Name                                               | BESCHREIBUNG                                                     |
| -------------------------------------------------- | --------------------------------------------------------------- |
| [RuntimeClass::RuntimeClass](#runtimeclass)        | Initialisiert die aktuelle Instanz `RuntimeClass` der Klasse.   |
| [RuntimeClass::-RuntimeClass](#tilde-runtimeclass) | Deinitialisiert die aktuelle Instanz `RuntimeClass` der Klasse. |

### <a name="public-methods"></a>Öffentliche Methoden

| Name                                                      | BESCHREIBUNG                                                                                        |
| --------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| [RuntimeClass::AddRef](#addref)                           | Inkrementiert die Referenzanzahl für das aktuelle `RuntimeClass` Objekt.                              |
| [RuntimeClass::DecrementReference](#decrementreference)   | Dekrementiert die Referenzanzahl `RuntimeClass` für das aktuelle Objekt.                              |
| [RuntimeClass::GetIids](#getiids)                         | Ruft ein Array ab, das die vom `RuntimeClass` aktuellen Objekt implementierten Schnittstellen-IDs enthalten kann. |
| [RuntimeClass::GetRuntimeClassName](#getruntimeclassname) | Ruft den Laufzeitklassennamen des `RuntimeClass` aktuellen Objekts ab.                                  |
| [RuntimeClass::GetTrustLevel](#gettrustlevel)             | Ruft die Vertrauensstufe `RuntimeClass` des aktuellen Objekts ab.                                         |
| [RuntimeClass::GetWeakReference](#getweakreference)       | Ruft einen Zeiger auf das schwache `RuntimeClass` Referenzobjekt für das aktuelle Objekt ab.                 |
| [RuntimeClass::InternalAddRef](#internaladdref)           | Inkrementiert die Verweisanzahl auf das aktuelle `RuntimeClass` Objekt.                               |
| [RuntimeClass::QueryInterface](#queryinterface)           | Ruft einen Zeiger auf die angegebene Schnittstellen-ID ab.                                                 |
| [RuntimeClass::Release](#release)                         | Führt einen COM-Freigabevorgang `RuntimeClass` für das aktuelle Objekt aus.                             |

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

Dies ist ein Implementierungsdetail.

## <a name="requirements"></a>Anforderungen

**Header:** implements.h

**Namespace:** Microsoft::WRL

## <a name="runtimeclassruntimeclass"></a><a name="tilde-runtimeclass"></a>RuntimeClass::-RuntimeClass

Deinitialisiert die aktuelle Instanz `RuntimeClass` der Klasse.

```cpp
virtual ~RuntimeClass();
```

## <a name="runtimeclassaddref"></a><a name="addref"></a>RuntimeClass::AddRef

Inkrementiert die Referenzanzahl für das aktuelle `RuntimeClass` Objekt.

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

## <a name="runtimeclassdecrementreference"></a><a name="decrementreference"></a>RuntimeClass::DecrementReference

Dekrementiert die Referenzanzahl `RuntimeClass` für das aktuelle Objekt.

```cpp
ULONG DecrementReference();
```

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

## <a name="runtimeclassgetiids"></a><a name="getiids"></a>RuntimeClass::GetIids

Ruft ein Array ab, das die vom `RuntimeClass` aktuellen Objekt implementierten Schnittstellen-IDs enthalten kann.

```cpp
STDMETHOD(
   GetIids
)
   (_Out_ ULONG *iidCount,
   _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>Parameter

*iidCount*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird die Gesamtzahl der Elemente in *Array-iids*.

*iids*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird ein Zeiger auf ein Array von Schnittstellen-IDs angezeigt.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls E_OUTOFMEMORY.

## <a name="runtimeclassgetruntimeclassname"></a><a name="getruntimeclassname"></a>RuntimeClass::GetRuntimeClassName

Ruft den Laufzeitklassennamen des `RuntimeClass` aktuellen Objekts ab.

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>Parameter

*runtimeName*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird der Name der Laufzeitklasse ausgeführt.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

### <a name="remarks"></a>Bemerkungen

Ein Assert-Fehler wird `__WRL_STRICT__` angezeigt, wenn oder `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` nicht definiert ist.

## <a name="runtimeclassgettrustlevel"></a><a name="gettrustlevel"></a>RuntimeClass::GetTrustLevel

Ruft die Vertrauensstufe `RuntimeClass` des aktuellen Objekts ab.

```cpp
STDMETHOD(GetTrustLevel)(
    _Out_ TrustLevel* trustLvl
);
```

### <a name="parameters"></a>Parameter

*trustLvl*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird `RuntimeClass` die Vertrauensstufe des aktuellen Objekts abgeschlossen.

### <a name="return-value"></a>Rückgabewert

Immer S_OK.

### <a name="remarks"></a>Bemerkungen

Ein Assert-Fehler wird `__WRL_STRICT__` angezeigt, wenn oder `__WRL_FORCE_INSPECTABLE_CLASS_MACRO__` nicht definiert ist.

## <a name="runtimeclassgetweakreference"></a><a name="getweakreference"></a>RuntimeClass::GetWeakReference

Ruft einen Zeiger auf das schwache `RuntimeClass` Referenzobjekt für das aktuelle Objekt ab.

```cpp
STDMETHOD(
   GetWeakReference
)(_Deref_out_ IWeakReference **weakReference);
```

### <a name="parameters"></a>Parameter

*Weakreference*<br/>
Wenn dieser Vorgang abgeschlossen ist, wird ein Zeiger auf ein schwaches Referenzobjekt zeiger.

### <a name="return-value"></a>Rückgabewert

Immer S_OK.

## <a name="runtimeclassinternaladdref"></a><a name="internaladdref"></a>RuntimeClass::InternalAddRef

Inkrementiert die Verweisanzahl auf das aktuelle `RuntimeClass` Objekt.

```cpp
ULONG InternalAddRef();
```

### <a name="return-value"></a>Rückgabewert

Die resultierende Referenzanzahl.

## <a name="runtimeclassqueryinterface"></a><a name="queryinterface"></a>RuntimeClass::QueryInterface

Ruft einen Zeiger auf die angegebene Schnittstellen-ID ab.

```cpp
STDMETHOD(
   QueryInterface
)
   (REFIID riid,
   _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>Parameter

*riid*<br/>
Eine Schnittstellen-ID.

*ppvObject*<br/>
Wenn diese Betätigung abgeschlossen ist, wird ein Zeiger auf die Schnittstelle angezeigt, die durch den *riid-Parameter* angegeben wird.

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

## <a name="runtimeclassrelease"></a><a name="release"></a>RuntimeClass::Release

Führt einen COM-Freigabevorgang `RuntimeClass` für das aktuelle Objekt aus.

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>Rückgabewert

S_OK, wenn erfolgreich; andernfalls ein HRESULT, das den Fehler angibt.

### <a name="remarks"></a>Bemerkungen

Wenn die Referenzanzahl Null `RuntimeClass` wird, wird das Objekt gelöscht.

## <a name="runtimeclassruntimeclass"></a><a name="runtimeclass"></a>RuntimeClass::RuntimeClass

Initialisiert die aktuelle Instanz `RuntimeClass` der Klasse.

```cpp
RuntimeClass();
```

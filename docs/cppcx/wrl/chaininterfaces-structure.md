---
title: ChainInterfaces-Struktur
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces
- implements/Microsoft::WRL::ChainInterfaces::CanCastTo
- implements/Microsoft::WRL::ChainInterfaces::CastToUnknown
- implements/Microsoft::WRL::ChainInterfaces::FillArrayWithIid
- implements/Microsoft::WRL::ChainInterfaces::IidCount
- implements/Microsoft::WRL::ChainInterfaces::Verify
helpviewer_keywords:
- Microsoft::WRL::ChainInterfaces structure
- Microsoft::WRL::ChainInterfaces::CanCastTo method
- Microsoft::WRL::ChainInterfaces::CastToUnknown method
- Microsoft::WRL::ChainInterfaces::FillArrayWithIid method
- Microsoft::WRL::ChainInterfaces::IidCount constant
- Microsoft::WRL::ChainInterfaces::Verify method
ms.assetid: d7415b59-5468-4bef-a3fd-8d82b12f0e9c
ms.openlocfilehash: dd1af3fb5c1079a40d8248dc71ae4972537aa856
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372652"
---
# <a name="chaininterfaces-structure"></a>ChainInterfaces-Struktur

Gibt Überprüfungs- und Initialisierungsfunktionen an, die auf einen Satz von Schnittstellen-IDs angewendet werden können.

## <a name="syntax"></a>Syntax

```cpp
template <
    typename I0,
    typename I1,
    typename I2 = Details::Nil,
    typename I3 = Details::Nil,
    typename I4 = Details::Nil,
    typename I5 = Details::Nil,
    typename I6 = Details::Nil,
    typename I7 = Details::Nil,
    typename I8 = Details::Nil,
    typename I9 = Details::Nil
>
struct ChainInterfaces : I0;

template <
    typename DerivedType,
    typename BaseType,
    bool hasImplements,
    typename I1,
    typename I2,
    typename I3,
    typename I4,
    typename I5,
    typename I6,
    typename I7,
    typename I8,
    typename I9
>
struct ChainInterfaces<
    MixIn<
        DerivedType,
        BaseType,
        hasImplements
    >, I1, I2, I3, I4, I5, I6, I7, I8, I9
>;
```

### <a name="parameters"></a>Parameter

*I0*<br/>
(Erforderlich) Schnittstellen-ID 0.

*I1*<br/>
(Erforderlich) Schnittstellen-ID 1.

*I2*<br/>
(Optional) Schnittstellen-ID 2.

*I3*<br/>
(Optional) Schnittstellen-ID 3.

*I4*<br/>
(Optional) Schnittstellen-ID 4.

*I5*<br/>
(Optional) Schnittstellen-ID 5.

*I6*<br/>
(Optional) Schnittstellen-ID 6.

*I7*<br/>
(Optional) Schnittstellen-ID 7.

*I8*<br/>
(Optional) Schnittstellen-ID 8.

*I9*<br/>
(Optional) Schnittstellen-ID 9.

*DerivedType*<br/>
Ein abgeleiteter Typ.

*BaseType*<br/>
Der Basistyp eines abgeleiteten Typs.

*hasImplements*<br/>
Ein boolescher Wert, der, wenn **true**, bedeutet, dass Sie keine [MixIn-Struktur](mixin-structure.md) mit einer Klasse verwenden können, die nicht von der [Implementierungsstruktur](implements-structure.md) abstammt.

## <a name="members"></a>Member

### <a name="protected-methods"></a>Geschützte Methoden

Name                                                   | BESCHREIBUNG
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ChainInterfaces::CanCastTo](#cancastto)               | Gibt an, ob die angegebene Schnittstellen-ID in jede `ChainInterface` der durch die Vorlagenparameter definierten Spezialisierungen umgegeuzt werden kann.
[ChainInterfaces::CastToUnknown](#casttounknown)       | Übergibt den Schnittstellenzeiger des Typs, der durch den I0-Vorlagenparameter definiert *ist,* auf einen Zeiger auf `IUnknown`.
[ChainInterfaces::FillArrayWithIid](#fillarraywithiid) | Speichert die durch den *I0-Vorlagenparameter* definierte Schnittstellen-ID an einem angegebenen Speicherort in einem angegebenen Array von Schnittstellen-IDs.
[ChainInterfaces::Überprüfen](#verify)                     | Überprüft, ob jede Durch vorlageparameter *I0* bis *I9* `IUnknown` definierte `IInspectable`Schnittstelle von und/oder erbt und dass *I0* von *I1* bis *I9*erbt.

### <a name="protected-constants"></a>Geschützte Konstanten

Name                                   | BESCHREIBUNG
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[ChainInterfaces::IidCount](#iidcount) | Die Gesamtanzahl der Schnittstellen-IDs, die in den Schnittstellen enthalten sind, die durch die Vorlagenparameter *I0* bis *I9*angegeben sind.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`I0`

`ChainInterfaces`

## <a name="requirements"></a>Anforderungen

**Header:** implements.h

**Namespace:** Microsoft::WRL

## <a name="chaininterfacescancastto"></a><a name="cancastto"></a>ChainInterfaces::CanCastTo

Gibt an, ob die angegebene Schnittstellen-ID in jede der Spezialisierungen umgecastet werden kann, die durch die nicht standardmäßigen Vorlagenparameter definiert sind.

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parameter

*riid*<br/>
Eine Schnittstellen-ID.

*Ppv*<br/>
Ein Zeiger auf die letzte Schnittstellen-ID, die erfolgreich gecastet wurde.

### <a name="return-value"></a>Rückgabewert

**true,** wenn alle Umwandlungsvorgänge erfolgreich waren; andernfalls **false**.

## <a name="chaininterfacescasttounknown"></a><a name="casttounknown"></a>ChainInterfaces::CastToUnknown

Übergibt den Schnittstellenzeiger des Typs, der durch den I0-Vorlagenparameter definiert *ist,* auf einen Zeiger auf `IUnknown`.

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `IUnknown`.

## <a name="chaininterfacesfillarraywithiid"></a><a name="fillarraywithiid"></a>ChainInterfaces::FillArrayWithIid

Speichert die durch den *I0-Vorlagenparameter* definierte Schnittstellen-ID an einem angegebenen Speicherort in einem angegebenen Array von Schnittstellen-IDs.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Zeiger auf einen Indexwert im *iids-Array.*

*iids*<br/>
Ein Array von Schnittstellen-IDs.

## <a name="chaininterfacesiidcount"></a><a name="iidcount"></a>ChainInterfaces::IidCount

Die Gesamtanzahl der Schnittstellen-IDs, die in den Schnittstellen enthalten sind, die durch die Vorlagenparameter *I0* bis *I9*angegeben sind.

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>Rückgabewert

Die Gesamtanzahl der Schnittstellen-IDs.

### <a name="remarks"></a>Bemerkungen

Die Vorlagenparameter *I0* und *I1* sind erforderlich, und die Parameter *I2* bis *I9* sind optional. Die IID-Anzahl jeder Schnittstelle ist in der Regel 1.

## <a name="chaininterfacesverify"></a><a name="verify"></a>ChainInterfaces::Überprüfen

Überprüft, ob jede Durch vorlageparameter *I0* bis *I9* `IUnknown` definierte `IInspectable`Schnittstelle von und/oder erbt und dass *I0* von *I1* bis *I9*erbt.

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>Bemerkungen

Wenn der Überprüfungsvorgang `static_assert` fehlschlägt, wird eine Fehlermeldung gesendet, die den Fehler beschreibt.

Die Vorlagenparameter *I0* und *I1* sind erforderlich, und die Parameter *I2* bis *I9* sind optional.

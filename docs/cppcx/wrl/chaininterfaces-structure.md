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
ms.openlocfilehash: 48b663f2042ff0095466d83fe872ef6196112f76
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211540"
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
Benötigten Schnittstellen-ID 0.

*I1*<br/>
Benötigten Schnittstellen-ID 1.

*I2*<br/>
Optionale Schnittstellen-ID 2.

*I3*<br/>
Optionale Schnittstelle-ID 3.

*I4*<br/>
Optionale Schnittstelle-ID 4.

*I5*<br/>
Optionale Schnittstellen-ID 5.

*I6*<br/>
Optionale Schnittstellen-ID 6.

*I7*<br/>
Optionale Schnittstelle-ID 7.

*I8*<br/>
Optionale Schnittstellen-ID 8.

*I9*<br/>
Optionale Schnittstelle-ID 9.

*DerivedType*<br/>
Ein abgeleiteter Typ.

*BaseType*<br/>
Der Basistyp eines abgeleiteten Typs.

*hasimplements*<br/>
Ein boolescher Wert, der **`true`** bedeutet, dass Sie eine [Mixin](mixin-structure.md) -Struktur nicht mit einer Klasse verwenden können, die nicht von der [implementierten](implements-structure.md) Stuktur abgeleitet ist.

## <a name="members"></a>Member

### <a name="protected-methods"></a>Geschützte Methoden

Name                                                   | BESCHREIBUNG
------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[Chaininterfaces:: CanCastTo](#cancastto)               | Gibt an, ob die angegebene Schnittstellen-ID in jede der von den Vorlagen Parametern definierten Spezialisierungs Umwandlungen umgewandelt werden kann `ChainInterface` .
[Chaininterfaces:: castdeunknown](#casttounknown)       | Wandelt den Schnittstellen Zeiger des Typs, der durch den *I0* Template-Parameter definiert ist, in einen Zeiger auf um `IUnknown` .
[Chaininterfaces:: fillarraywithiid](#fillarraywithiid) | Speichert die vom *I0* Template-Parameter definierte Schnittstellen-ID an einer angegebenen Position in einem angegebenen Array von Schnittstellen-IDs.
[Chaininterfaces:: Verify](#verify)                     | Überprüft, ob jede Schnittstelle, die durch Vorlagen Parameter *I0* bis *i9* definiert `IUnknown` ist, von und/oder erbt `IInspectable` und dass *I0* von *I1* bis *i9*erbt.

### <a name="protected-constants"></a>Geschützte Konstanten

Name                                   | BESCHREIBUNG
-------------------------------------- | -----------------------------------------------------------------------------------------------------------------
[Chaininterfaces:: iidcount](#iidcount) | Die Gesamtanzahl der Schnittstellen-IDs in den Schnittstellen, die von den Vorlagen Parametern *I0* bis *i9*angegeben werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`I0`

`ChainInterfaces`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** implementiert. h

**Namespace:** Microsoft::WRL

## <a name="chaininterfacescancastto"></a><a name="cancastto"></a>Chaininterfaces:: CanCastTo

Gibt an, ob die angegebene Schnittstellen-ID in jede der von den nicht standardmäßigen Vorlagen Parametern definierten Spezialisierungs Umwandlungen umgewandelt werden kann.

```cpp
__forceinline bool CanCastTo(
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parameter

*riid*<br/>
Eine Schnittstellen-ID.

*PPV*<br/>
Ein Zeiger auf die letzte Schnittstellen-ID, die erfolgreich umgewandelt wurde.

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn alle Umwandlungs Vorgänge erfolgreich waren. andernfalls **`false`** .

## <a name="chaininterfacescasttounknown"></a><a name="casttounknown"></a>Chaininterfaces:: castdeunknown

Wandelt den Schnittstellen Zeiger des Typs, der durch den *I0* Template-Parameter definiert ist, in einen Zeiger auf um `IUnknown` .

```cpp
__forceinline IUnknown* CastToUnknown();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `IUnknown`.

## <a name="chaininterfacesfillarraywithiid"></a><a name="fillarraywithiid"></a>Chaininterfaces:: fillarraywithiid

Speichert die vom *I0* Template-Parameter definierte Schnittstellen-ID an einer angegebenen Position in einem angegebenen Array von Schnittstellen-IDs.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Zeiger auf einen Indexwert in das *IIDs* -Array.

*IIDs*<br/>
Ein Array von Schnittstellen-IDs.

## <a name="chaininterfacesiidcount"></a><a name="iidcount"></a>Chaininterfaces:: iidcount

Die Gesamtanzahl der Schnittstellen-IDs in den Schnittstellen, die von den Vorlagen Parametern *I0* bis *i9*angegeben werden.

```cpp
static const unsigned long IidCount = Details::InterfaceTraits<I0>::IidCount + Details::InterfaceTraits<I1>::IidCount + Details::InterfaceTraits<I2>::IidCount + Details::InterfaceTraits<I3>::IidCount + Details::InterfaceTraits<I4>::IidCount + Details::InterfaceTraits<I5>::IidCount + Details::InterfaceTraits<I6>::IidCount + Details::InterfaceTraits<I7>::IidCount + Details::InterfaceTraits<I8>::IidCount + Details::InterfaceTraits<I9>::IidCount;
```

### <a name="return-value"></a>Rückgabewert

Die Gesamtanzahl der Schnittstellen-IDs.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Parameter *I0* und *I1* sind erforderlich, und die Parameter *I2* bis *i9* sind optional. Der IID-Zähler jeder Schnittstelle ist in der Regel 1.

## <a name="chaininterfacesverify"></a><a name="verify"></a>Chaininterfaces:: Verify

Überprüft, ob jede Schnittstelle, die durch Vorlagen Parameter *I0* bis *i9* definiert `IUnknown` ist, von und/oder erbt `IInspectable` und dass *I0* von *I1* bis *i9*erbt.

```cpp
WRL_NOTHROW __forceinline static void Verify();
```

### <a name="remarks"></a>Bemerkungen

Wenn der Überprüfungs Vorgang fehlschlägt, gibt eine **`static_assert`** Fehlermeldung aus, die den Fehler beschreibt.

Die Vorlagen Parameter *I0* und *I1* sind erforderlich, und die Parameter *I2* bis *i9* sind optional.

---
title: InterfaceTraits-Struktur
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits
- implements/Microsoft::WRL::Details::InterfaceTraits::CanCastTo
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToBase
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown
- implements/Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid
- implements/Microsoft::WRL::Details::InterfaceTraits::IidCount
- implements/Microsoft::WRL::Details::InterfaceTraits::Verify
helpviewer_keywords:
- Microsoft::WRL::Details::InterfaceTraits structure
- Microsoft::WRL::Details::InterfaceTraits::CanCastTo method
- Microsoft::WRL::Details::InterfaceTraits::CastToBase method
- Microsoft::WRL::Details::InterfaceTraits::CastToUnknown method
- Microsoft::WRL::Details::InterfaceTraits::FillArrayWithIid method
- Microsoft::WRL::Details::InterfaceTraits::IidCount constant
- Microsoft::WRL::Details::InterfaceTraits::Verify method
ms.assetid: ede0c284-19a7-4892-9738-ff3da4923d0a
ms.openlocfilehash: c08c6e8bbcc16120dd44da69a2933fc3ec42f387
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216569"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits-Struktur

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template<typename I0>
struct __declspec(novtable) InterfaceTraits;

template<typename CloakedType>
struct __declspec(novtable) InterfaceTraits<
    CloakedIid<CloakedType>
>;

template<>
struct __declspec(novtable) InterfaceTraits<Nil>;
```

### <a name="parameters"></a>Parameter

*I0*<br/>
Der Name einer Schnittstelle.

*Cloakedtype*<br/>
Für `RuntimeClass` `Implements` und `ChainInterfaces` eine Schnittstelle, die nicht in der Liste der unterstützten Schnittstellen-IDs enthalten ist.

## <a name="remarks"></a>Bemerkungen

Implementiert allgemeine Merkmale einer Schnittstelle.

Die zweite Vorlage ist eine Spezialisierung für getarnte Schnittstellen. Die dritte Vorlage ist eine Spezialisierung für Nil-Parameter.

## <a name="members"></a>Member

### <a name="public-typedefs"></a><a name="public-typedefs"></a>Öffentliche Typedefs

Name   | BESCHREIBUNG
------ | ------------------------------------------
`Base` | Ein Synonym für den *I0* -Vorlagen Parameter.

### <a name="public-methods"></a>Öffentliche Methoden

name                                                   | BESCHREIBUNG
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[Interfacecharakteristika:: CanCastTo](#cancastto)               | Gibt an, ob der angegebene Zeiger in einen Zeiger auf umgewandelt werden kann `Base` .
[Interfacecharakteristika:: castto Base](#casttobase)             | Wandelt den angegebenen Zeiger auf einen Zeiger auf `Base` .
[Interfacemerkmalen:: castto Unknown](#casttounknown)       | Wandelt den angegebenen Zeiger auf einen Zeiger auf `IUnknown` .
[Interfacecharakteristika:: fillarraywithiid](#fillarraywithiid) | Weist dem `Base` Array Element, das vom Index-Argument angegeben wird, die Schnittstellen-ID von zu.
[Interfacecharakteristika:: Verify](#verify)                     | Überprüft, ob `Base` ordnungsgemäß abgeleitet ist.

### <a name="public-constants"></a>Öffentliche Konstanten

Name                                   | BESCHREIBUNG
-------------------------------------- | ---------------------------------------------------------------------------------------
[Interfacecharakteristika:: iidcount](#iidcount) | Enthält die Anzahl der dem aktuellen-Objekt zugeordneten Schnittstellen-IDs `InterfaceTraits` .

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`InterfaceTraits`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** implementiert. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="interfacetraitscancastto"></a><a name="cancastto"></a>Interfacecharakteristika:: CanCastTo

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parameter

*ptr*<br/>
Der Name eines Zeigers auf einen Typ.

*riid*<br/>
Die Schnittstellen-ID von `Base` .

*PPV*<br/>
Wenn dieser Vorgang erfolgreich ist, verweist *PPV* auf die durch angegebene Schnittstelle `Base` . Andernfalls wird *PPV* auf festgelegt **`nullptr`** .

### <a name="return-value"></a>Rückgabewert

**`true`**, wenn dieser Vorgang erfolgreich ist und *ptr* in einen Zeiger auf umgewandelt wird `Base` ; andernfalls **`false`** .

### <a name="remarks"></a>Bemerkungen

Gibt an, ob der angegebene Zeiger in einen Zeiger auf umgewandelt werden kann `Base` .

Weitere Informationen zu `Base` finden Sie im Abschnitt " [öffentliche Typedefs](#public-typedefs) ".

## <a name="interfacetraitscasttobase"></a><a name="casttobase"></a>Interfacecharakteristika:: castto Base

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des Parameters *ptr*.

*ptr*<br/>
Zeiger auf einen Typ *T*.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `Base`.

### <a name="remarks"></a>Bemerkungen

Wandelt den angegebenen Zeiger auf einen Zeiger auf `Base` .

Weitere Informationen zu `Base` finden Sie im Abschnitt " [öffentliche Typedefs](#public-typedefs) ".

## <a name="interfacetraitscasttounknown"></a><a name="casttounknown"></a>Interfacemerkmalen:: castto Unknown

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des Parameters *ptr*.

*ptr*<br/>
Zeiger auf Typ *T*.

### <a name="return-value"></a>Rückgabewert

Zeiger auf den IUnknown, von dem `Base` abgeleitet wird.

### <a name="remarks"></a>Bemerkungen

Wandelt den angegebenen Zeiger auf einen Zeiger auf `IUnknown` .

Weitere Informationen zu `Base` finden Sie im Abschnitt " [öffentliche Typedefs](#public-typedefs) ".

## <a name="interfacetraitsfillarraywithiid"></a><a name="fillarraywithiid"></a>Interfacecharakteristika:: fillarraywithiid

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Ein Zeiger auf ein Feld, das einen NULL basierten Indexwert enthält.

*IIDs*<br/>
Ein Array von Schnittstellen-IDs.

### <a name="remarks"></a>Bemerkungen

Weist dem `Base` Array Element, das vom Index-Argument angegeben wird, die Schnittstellen-ID von zu.

Im Gegensatz zum Namen dieser API wird nur ein Array Element geändert. nicht das gesamte Array.

Weitere Informationen zu `Base` finden Sie im Abschnitt " [öffentliche Typedefs](#public-typedefs) ".

## <a name="interfacetraitsiidcount"></a><a name="iidcount"></a>Interfacecharakteristika:: iidcount

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>Bemerkungen

Enthält die Anzahl der dem aktuellen-Objekt zugeordneten Schnittstellen-IDs `InterfaceTraits` .

## <a name="interfacetraitsverify"></a><a name="verify"></a>Interfacecharakteristika:: Verify

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>Bemerkungen

Überprüft, ob `Base` ordnungsgemäß abgeleitet ist.

Weitere Informationen zu `Base` finden Sie im Abschnitt " [öffentliche Typedefs](#public-typedefs) ".

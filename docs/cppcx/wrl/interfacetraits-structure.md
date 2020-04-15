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
ms.openlocfilehash: 17f743a38af3ddc600a55e38905d19868d076a22
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371369"
---
# <a name="interfacetraits-structure"></a>InterfaceTraits-Struktur

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

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

*CloakedType*<br/>
Für `RuntimeClass` `Implements` und `ChainInterfaces`eine Schnittstelle, die nicht in der Liste der unterstützten Schnittstellen-IDs enthalten ist.

## <a name="remarks"></a>Bemerkungen

Implementiert gemeinsame Merkmale einer Schnittstelle.

Die zweite Vorlage ist eine Spezialisierung für getarnte Schnittstellen. Die dritte Vorlage ist eine Spezialisierung für Nil-Parameter.

## <a name="members"></a>Member

### <a name="public-typedefs"></a><a name="public-typedefs"></a>Öffentliche Typdefs

Name   | BESCHREIBUNG
------ | ------------------------------------------
`Base` | Ein Synonym für den Vorlagenparameter *I0.*

### <a name="public-methods"></a>Öffentliche Methoden

Name                                                   | BESCHREIBUNG
------------------------------------------------------ | ----------------------------------------------------------------------------------------
[InterfaceTraits::CanCastTo](#cancastto)               | Gibt an, ob der angegebene Zeiger auf `Base`einen Zeiger auf umgegossen werden kann.
[InterfaceTraits::CastToBase](#casttobase)             | Gibt den angegebenen Zeiger auf einen `Base`Zeiger auf .
[InterfaceTraits::CastToUnknown](#casttounknown)       | Gibt den angegebenen Zeiger auf einen `IUnknown`Zeiger auf .
[InterfaceTraits::FillArrayWithIid](#fillarraywithiid) | Weist dem Arrayelement `Base` die Schnittstellen-ID des Arrayelements zu, das durch das Indexargument angegeben wird.
[InterfaceTraits::Überprüfen](#verify)                     | Überprüft, dass `Base` die korrekt abgeleitete Datei korrekt abgeleitet ist.

### <a name="public-constants"></a>Öffentliche Konstanten

Name                                   | BESCHREIBUNG
-------------------------------------- | ---------------------------------------------------------------------------------------
[InterfaceTraits::IidCount](#iidcount) | Enthält die Anzahl der Schnittstellen-IDs, die dem aktuellen `InterfaceTraits` Objekt zugeordnet sind.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`InterfaceTraits`

## <a name="requirements"></a>Anforderungen

**Header:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="interfacetraitscancastto"></a><a name="cancastto"></a>InterfaceTraits::CanCastTo

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
template<typename T>
static __forceinline bool CanCastTo(
   _In_ T* ptr,
   REFIID riid,
   _Deref_out_ void **ppv
);
```

### <a name="parameters"></a>Parameter

*Ptr*<br/>
Der Name eines Zeigers auf einen Typ.

*riid*<br/>
Die Schnittstellen-ID von `Base`.

*Ppv*<br/>
Wenn dieser Vorgang erfolgreich ist, zeigt *ppv* auf die von `Base`angegebene Schnittstelle . Andernfalls wird *ppv* `nullptr`auf gesetzt.

### <a name="return-value"></a>Rückgabewert

**true,** wenn dieser Vorgang erfolgreich ist und *ptr* auf einen Zeiger auf `Base`geworfen wird; andernfalls **false**.

### <a name="remarks"></a>Bemerkungen

Gibt an, ob der angegebene Zeiger auf `Base`einen Zeiger auf umgegossen werden kann.

Weitere Informationen `Base`zu finden Sie im Abschnitt [Public Typedefs.](#public-typedefs)

## <a name="interfacetraitscasttobase"></a><a name="casttobase"></a>InterfaceTraits::CastToBase

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
template<typename T>
static __forceinline Base* CastToBase(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des Parameters *ptr*.

*Ptr*<br/>
Zeiger auf einen Typ *T*.

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf `Base`.

### <a name="remarks"></a>Bemerkungen

Gibt den angegebenen Zeiger auf einen `Base`Zeiger auf .

Weitere Informationen `Base`zu finden Sie im Abschnitt [Public Typedefs.](#public-typedefs)

## <a name="interfacetraitscasttounknown"></a><a name="casttounknown"></a>InterfaceTraits::CastToUnknown

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ des Parameters *ptr*.

*Ptr*<br/>
Zeiger auf den Typ *T*.

### <a name="return-value"></a>Rückgabewert

Zeiger auf das IUnknown, von dem `Base` abgeleitet wird.

### <a name="remarks"></a>Bemerkungen

Gibt den angegebenen Zeiger auf einen `IUnknown`Zeiger auf .

Weitere Informationen `Base`zu finden Sie im Abschnitt [Public Typedefs.](#public-typedefs)

## <a name="interfacetraitsfillarraywithiid"></a><a name="fillarraywithiid"></a>InterfaceTraits::FillArrayWithIid

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
__forceinline static void FillArrayWithIid(
   _Inout_ unsigned long &index,
   _In_ IID* iids
);
```

### <a name="parameters"></a>Parameter

*Index*<br/>
Zeiger auf ein Feld, das einen nullbasierten Indexwert enthält.

*iids*<br/>
Ein Array von Schnittstellen-IDs.

### <a name="remarks"></a>Bemerkungen

Weist dem Arrayelement `Base` die Schnittstellen-ID des Arrayelements zu, das durch das Indexargument angegeben wird.

Im Gegensatz zum Namen dieser API wird nur ein Arrayelement geändert. nicht das gesamte Array.

Weitere Informationen `Base`zu finden Sie im Abschnitt [Public Typedefs.](#public-typedefs)

## <a name="interfacetraitsiidcount"></a><a name="iidcount"></a>InterfaceTraits::IidCount

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
static const unsigned long IidCount = 1;
```

### <a name="remarks"></a>Bemerkungen

Enthält die Anzahl der Schnittstellen-IDs, die dem aktuellen `InterfaceTraits` Objekt zugeordnet sind.

## <a name="interfacetraitsverify"></a><a name="verify"></a>InterfaceTraits::Überprüfen

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
__forceinline static void Verify();
```

### <a name="remarks"></a>Bemerkungen

Überprüft, dass `Base` die korrekt abgeleitete Datei korrekt abgeleitet ist.

Weitere Informationen `Base`zu finden Sie im Abschnitt [Public Typedefs.](#public-typedefs)

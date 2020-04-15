---
title: IsBaseOfStrict-Struktur
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::IsBaseOfStrict
- internal/Microsoft::WRL::Details::IsBaseOfStrict::value
helpviewer_keywords:
- Microsoft::WRL::Details::IsBaseOfStrict structure
- Microsoft::WRL::Details::IsBaseOfStrict::value constant
ms.assetid: 6fed7366-c8d4-4991-b4fb-43ed93f8e1bf
ms.openlocfilehash: 71db5a1b52a7d7d5471c15591fb34d954b465d07
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371353"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict-Struktur

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <typename Base, typename Derived>
struct IsBaseOfStrict;

template <typename Base>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>Parameter

*Basis*<br/>
Der Basistyp.

*Abgeleiteten*<br/>
Der abgeleitete Typ.

## <a name="remarks"></a>Bemerkungen

Testet, ob ein Typ die Basis eines anderen ist.

Die erste Vorlage testet, ob ein Typ von einem Basistyp abgeleitet wird, was true **oder** **false**ergeben kann. Die zweite Vorlage testet, ob ein Typ von sich selbst abgeleitet wird, was immer **false**ergibt.

## <a name="members"></a>Member

### <a name="public-constants"></a>Öffentliche Konstanten

Name                            | BESCHREIBUNG
------------------------------- | --------------------------------------------------
[IsBaseOfStrict::wert](#value) | Gibt an, ob ein Typ die Basis eines anderen Typs ist.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IsBaseOfStrict`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="isbaseofstrictvalue"></a><a name="value"></a>IsBaseOfStrict::wert

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>Bemerkungen

Gibt an, ob ein Typ die Basis eines anderen Typs ist.

`value`ist **true,** wenn type `Base` eine `Derived`Basisklasse des Typs ist, andernfalls ist er **false**.

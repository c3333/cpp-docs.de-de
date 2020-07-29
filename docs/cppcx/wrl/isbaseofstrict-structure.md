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
ms.openlocfilehash: 11acb4c7162a17ff763a574c27c186061ae476a7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211527"
---
# <a name="isbaseofstrict-structure"></a>IsBaseOfStrict-Struktur

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
template <typename Base, typename Derived>
struct IsBaseOfStrict;

template <typename Base>
struct IsBaseOfStrict<Base, Base>;
```

### <a name="parameters"></a>Parameter

*Sock*<br/>
Der Basistyp.

*Abgeleitet*<br/>
Der abgeleitete Typ.

## <a name="remarks"></a>Bemerkungen

Testet, ob ein Typ die Basis eines anderen ist.

Die erste Vorlage testet, ob ein Typ von einem Basistyp abgeleitet ist, der möglicherweise **`true`** oder liefert **`false`** . Die zweite Vorlage testet, ob ein Typ von sich selbst abgeleitet ist, was immer ergibt **`false`** .

## <a name="members"></a>Member

### <a name="public-constants"></a>Öffentliche Konstanten

Name                            | BESCHREIBUNG
------------------------------- | --------------------------------------------------
[Isbaseosstrict:: Wert](#value) | Gibt an, ob ein Typ die Basis eines anderen Typs ist.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`IsBaseOfStrict`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** intern. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="isbaseofstrictvalue"></a><a name="value"></a>Isbaseosstrict:: Wert

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
static const bool value = __is_base_of(Base, Derived);
```

### <a name="remarks"></a>Bemerkungen

Gibt an, ob ein Typ die Basis eines anderen Typs ist.

`value`gibt **`true`** `Base` an, ob der Typ eine Basisklasse des Typs ist; `Derived` andernfalls ist er **`false`** .

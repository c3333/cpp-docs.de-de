---
title: BoolStruct-Struktur
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::BoolStruct
- internal/Microsoft::WRL::Details::BoolStruct::Member
helpviewer_keywords:
- Microsoft::WRL::Details::BoolStruct structure
- Microsoft::WRL::Details::BoolStruct::Member data member
ms.assetid: 666eae78-e81d-4fb7-a9e4-1ba617d6d4cd
ms.openlocfilehash: cdec425e317585abbd9730447e2c4fbb19b8250a
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423657"
---
# <a name="boolstruct-structure"></a>BoolStruct-Struktur

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Hinweise

Die `BoolStruct` Struktur definiert, ob ein `ComPtr` die Objekt Lebensdauer einer Schnittstelle verwaltet. `BoolStruct` wird intern vom [booltype ()](comptr-class.md#operator-microsoft-wrl-details-booltype) -Operator verwendet.

## <a name="members"></a>Member

### <a name="public-data-members"></a>Öffentliche Datenelemente

Name                          | Beschreibung
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[Boolstruct:: Member](#member) | Gibt an, dass ein [comptr](comptr-class.md) -Objekt ist oder nicht, das die Objekt Lebensdauer einer Schnittstelle verwaltet.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`BoolStruct`

## <a name="requirements"></a>Voraussetzungen

**Header:** intern. h

**Namespace:** Microsoft:: WRL::D etails

## <a name="member"></a>Boolstruct:: Member

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung im Code vorgesehen.

```cpp
int Member;
```

### <a name="remarks"></a>Hinweise

Gibt an, dass ein [comptr](comptr-class.md) -Objekt ist oder nicht, das die Objekt Lebensdauer einer Schnittstelle verwaltet.

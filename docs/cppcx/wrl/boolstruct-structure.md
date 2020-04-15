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
ms.openlocfilehash: 4f2a5acf6edb824cff2121c1b6444181b5cfcf98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371853"
---
# <a name="boolstruct-structure"></a>BoolStruct-Struktur

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
struct BoolStruct;
```

## <a name="remarks"></a>Bemerkungen

Die `BoolStruct` Struktur definiert, `ComPtr` ob a die Objektlebensdauer einer Schnittstelle verwaltet. `BoolStruct`wird intern vom [BoolType()-Operator](comptr-class.md#operator-microsoft-wrl-details-booltype) verwendet.

## <a name="members"></a>Member

### <a name="public-data-members"></a>Öffentliche Datenmember

Name                          | BESCHREIBUNG
----------------------------- | ------------------------------------------------------------------------------------------------------------------
[BoolStruct::Mitglied](#member) | Gibt an, dass ein [ComPtr](comptr-class.md) die Objektlebensdauer einer Schnittstelle verwaltet oder nicht.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`BoolStruct`

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** internal.h

**Namespace:** Microsoft::WRL::Details

## <a name="boolstructmember"></a><a name="member"></a>BoolStruct::Mitglied

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
int Member;
```

### <a name="remarks"></a>Bemerkungen

Gibt an, dass ein [ComPtr](comptr-class.md) die Objektlebensdauer einer Schnittstelle verwaltet oder nicht.

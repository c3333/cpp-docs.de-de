---
title: ModuleBase-Klasse
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::DecrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::IncrementObjectCount
- implements/Microsoft::WRL::Details::ModuleBase::ModuleBase
- implements/Microsoft::WRL::Details::ModuleBase::~ModuleBase
helpviewer_keywords:
- ModuleBase class
- Microsoft::WRL::Details::ModuleBase::DecrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::IncrementObjectCount method
- Microsoft::WRL::Details::ModuleBase::ModuleBase, constructor
- Microsoft::WRL::Details::ModuleBase::~ModuleBase, destructor
ms.assetid: edce7591-6893-46f7-94a7-382827775548
ms.openlocfilehash: 13a8ceef3133e9946524e1fcd02e96535eccd7fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371262"
---
# <a name="modulebase-class"></a>ModuleBase-Klasse

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

## <a name="syntax"></a>Syntax

```cpp
class ModuleBase;
```

## <a name="remarks"></a>Bemerkungen

Stellt die Basisklasse der [Modulklassen](module-class.md) dar.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

Name                                         | BESCHREIBUNG
-------------------------------------------- | ---------------------------------------------------------
[ModuleBase::ModuleBase](#modulebase)        | Initialisiert eine Instanz der `Module`-Klasse.
[ModuleBase::-ModuleBase](#tilde-modulebase) | Deinitialisiert die aktuelle Instanz `Module` der Klasse.

### <a name="public-methods"></a>Öffentliche Methoden

Name                                                      | BESCHREIBUNG
--------------------------------------------------------- | -------------------------------------------------------------------------
[ModuleBase::DecrementObjectCount](#decrementobjectcount) | Wenn implementiert, wird die Anzahl der vom Modul nachverfolgten Objekte dekrementiert.
[ModuleBase::IncrementObjectCount](#incrementobjectcount) | Wenn implementiert, erhöht die Anzahl der Objekte, die vom Modul nachverfolgt werden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`ModuleBase`

## <a name="requirements"></a>Anforderungen

**Header:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="modulebasemodulebase"></a><a name="tilde-modulebase"></a>ModuleBase::-ModuleBase

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
virtual ~ModuleBase();
```

### <a name="remarks"></a>Bemerkungen

Deinitialisiert die aktuelle Instanz `ModuleBase` der Klasse.

## <a name="modulebasedecrementobjectcount"></a><a name="decrementobjectcount"></a>ModuleBase::DecrementObjectCount

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
virtual long DecrementObjectCount() = 0;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl vor dem Dekrementvorgang.

### <a name="remarks"></a>Bemerkungen

Wenn implementiert, wird die Anzahl der vom Modul nachverfolgten Objekte dekrementiert.

## <a name="modulebaseincrementobjectcount"></a><a name="incrementobjectcount"></a>ModuleBase::IncrementObjectCount

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
virtual long IncrementObjectCount() = 0;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl vor dem Inkrementvorgang.

### <a name="remarks"></a>Bemerkungen

Wenn implementiert, erhöht die Anzahl der Objekte, die vom Modul nachverfolgt werden.

## <a name="modulebasemodulebase"></a><a name="modulebase"></a>ModuleBase::ModuleBase

Unterstützt die WRL-Infrastruktur und ist nicht für die direkte Verwendung aus dem Code vorgesehen.

```cpp
ModuleBase();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert eine Instanz der `Module`-Klasse.

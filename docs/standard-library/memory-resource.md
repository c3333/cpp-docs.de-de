---
title: '&lt;memory_resource&gt;'
ms.date: 04/04/2019
f1_keywords:
- <memory_resource>
helpviewer_keywords:
- memory_resource header
ms.openlocfilehash: de88feb691d0ec1bc9bf9b9dc2bc40cbc31a1cfe
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831046"
---
# <a name="ltmemory_resourcegt"></a>&lt;memory_resource&gt;

Definiert die Container-Klassen Vorlage memory_resource und deren unterstützende Vorlagen.

## <a name="syntax"></a>Syntax

```cpp
#include <memory_resource>
```

## <a name="members"></a>Member

### <a name="operators"></a>Operatoren

|Name|Beschreibung|
|-|-|
|[Operator! =](../standard-library/memory-resource-operators.md#op_neq)|Testet, ob das memory_resource Objekt links vom Operator ungleich dem memory_resource Objekt rechts vom Operator ist.|
|[Operator = =](../standard-library/memory-resource-operators.md#op_eq_eq)|Testet, ob das memory_resource Objekt links vom Operator gleich dem memory_resource Objekt rechts vom Operator ist.|

### <a name="specialized-template-functions"></a>Spezialisierte Vorlagenfunktionen

|Name|Beschreibung|
|-|-|
|[polymorphic_allocator](../standard-library/memory-resource-functions.md#poly_alloc)||

### <a name="functions"></a>Functions

|Name|Beschreibung|
|-|-|
|[get_default_resource](../standard-library/memory-resource-functions.md#get_default)||
|[new_delete_resource](../standard-library/memory-resource-functions.md#new_delete)||
|[null_memory_resource](../standard-library/memory-resource-functions.md#null_memory)||
|[set_default_resource](../standard-library/memory-resource-functions.md#set_default)||

### <a name="classes-and-structs"></a>Klassen und Strukturen

|Name|Beschreibung|
|-|-|
|[memory_resource-Klasse](../standard-library/memory-resource-class.md)||
|[monotonic_buffer_resource-Klasse](../standard-library/monotonic-buffer-resource-class.md)||
|[pool_options-Struktur](../standard-library/pool-options-structure.md)||
|[synchronized_pool_resource-Klasse](../standard-library/synchronized-pool-resource-class.md)||
|[unsynchronized_pool_resource-Klasse](../standard-library/unsynchronized-pool-resource-class.md)||

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standard Bibliotheks Referenz](../standard-library/cpp-standard-library-reference.md)

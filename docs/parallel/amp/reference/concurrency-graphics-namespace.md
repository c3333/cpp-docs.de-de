---
title: Concurrency::graphics-Namespace
ms.date: 11/04/2016
f1_keywords:
- AMP_GRAPHICS/Concurrency
ms.assetid: 4529d3b1-d7da-4ffb-82bf-080915e0f23e
ms.openlocfilehash: 942b3bbace85fa297bba6cd4b509f67006a4aed3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226736"
---
# <a name="concurrencygraphics-namespace"></a>Concurrency::graphics-Namespace

Der Grafiknamespace stellt Typen und Funktionen bereit, die für die Grafikprogrammierung vorgesehen sind.

## <a name="syntax"></a>Syntax

```cpp
namespace graphics;
```

## <a name="members"></a>Member

### <a name="namespaces"></a>Namespaces

|Name|Beschreibung|
|----------|-----------------|
|[Parallelcurrency:: Graphics::d irect3d-Namespace](concurrency-graphics-direct3d-namespace.md)|Stellt Funktionen für Direct3D-Interop bereit.|

### <a name="typedefs"></a>TypeDefs

|Name|Beschreibung|
|----------|-----------------|
|`uint`|Der Elementtyp für [uint_2 Klasse](uint-2-class.md), [uint_3 Klasse](uint-3-class.md)und [uint_4 Klasse](uint-4-class.md). Sie sind als `typedef unsigned int uint;` definiert.|

### <a name="enumerations"></a>Enumerationen

|Name|Beschreibung|
|----------|-----------------|
|[address_mode Enumeration](concurrency-graphics-namespace-enums.md#address_mode).|Gibt die unterstützten Adressmodi für das Textursampling an.|
|[filter_mode-Enumeration](concurrency-graphics-namespace-enums.md#filter_mode)|Gibt die unterstützten Filtermodi für das Textursampling an.|

### <a name="classes"></a>Klassen

|name|Beschreibung|
|----------|-----------------|
|[Texture-Klasse](texture-class.md)|Eine Textur ist ein Datenaggregat in einer "accelerator_view" in der extent-Domäne. Es ist eine Auflistung von Variablen, eine für jedes Element in einer extent-Domäne. Jede Variable enthält einen Wert gemäß primitivem C++-Typ ohne Vorzeichen (int, int, Float, Double) oder skalarer Typnorm bzw. unorm (definiert in concurrency::graphics) oder zulässige kurze Vektortypen, die in concurrency::graphics definiert werden.|
|[writeonly_texture_view-Klasse](writeonly-texture-view-class.md)|Eine "writeonly_texture_view" bietet Nur-Schreib-Zugriff auf eine Textur.|
|[double_2-Klasse](double-2-class.md)|Stellt einen kurzen Vektor von 2 **`double`** Werten dar.|
|[double_3-Klasse](double-3-class.md)|Stellt einen kurzen Vektor aus drei **`double`** Werten dar.|
|[double_4-Klasse](double-4-class.md)|Stellt einen kurzen Vektor von 4 **`double`** Werten dar.|
|[float_2-Klasse](float-2-class.md)|Stellt einen kurzen Vektor von 2 **`float`** Werten dar.|
|[float_3-Klasse](float-3-class.md)|Stellt einen kurzen Vektor aus drei **`float`** Werten dar.|
|[float_4-Klasse](float-4-class.md)|Stellt einen kurzen Vektor von 4 **`float`** Werten dar.|
|[int_2-Klasse](int-2-class.md)|Stellt einen kurzen Vektor von 2 **`int`** Werten dar.|
|[int_3-Klasse](int-3-class.md)|Stellt einen kurzen Vektor aus drei **`int`** Werten dar.|
|[int_4-Klasse](int-4-class.md)|Stellt einen kurzen Vektor von 4 **`int`** Werten dar.|
|[norm_2-Klasse](norm-2-class.md)|Stellt einen kurzen Vektor von 2 `norm`-Werten dar.|
|[norm_3-Klasse](norm-3-class.md)|Stellt einen kurzen Vektor aus drei `norm` Werten dar.|
|[norm_4-Klasse](norm-4-class.md)|Stellt einen kurzen Vektor von 4 `norm` Werten dar.|
|[uint_2-Klasse](uint-2-class.md)|Stellt einen kurzen Vektor von 2 `uint`-Werten dar.|
|[uint_3-Klasse](uint-3-class.md)|Stellt einen kurzen Vektor aus drei `uint` Werten dar.|
|[uint_4-Klasse](uint-4-class.md)|Stellt einen kurzen Vektor von 4 `uint` Werten dar.|
|[unorm_2-Klasse](unorm-2-class.md)|Stellt einen kurzen Vektor von 2 `unorm`-Werten dar.|
|[unorm_3-Klasse](unorm-3-class.md)|Stellt einen kurzen Vektor aus drei `unorm` Werten dar.|
|[unorm_4-Klasse](unorm-4-class.md)|Stellt einen kurzen Vektor von 4 `unorm` Werten dar.|
|[samplerklasse](sampler-class.md)|Stellt die Samplerkonfiguration dar, die für Textursampling verwendet wird.|
|[short_vector-Struktur](short-vector-structure.md)|Stellt eine grundlegende Implementierung eines kurzen Vektors von Werten bereit.|
|[short_vector_traits-Struktur](short-vector-traits-structure.md)|Stellt das Abrufen der Länge und des Typs eines kurzen Vektors bereit.|
|[texture_view-Klasse](texture-view-class.md)|Stellt einer Textur Lese- und Schreibzugriff zur Verfügung.|

### <a name="functions"></a>Functions

|Name|Beschreibung|
|----------|-----------------|
|[copy](concurrency-graphics-namespace-functions.md#copy)|Ist überladen. Kopiert den Inhalt der Quelltextur in den Zielhostpuffer.|
|[copy_async](concurrency-graphics-namespace-functions.md#copy_async)|Ist überladen. Kopiert den Inhalt der Quelltextur asynchron in den Zielhostpuffer.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** amp_graphics. h

**Namespace:** Parallelität

## <a name="see-also"></a>Weitere Informationen

[Parallelitäts Namespace (C++ amp)](concurrency-namespace-cpp-amp.md)

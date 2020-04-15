---
title: '&lt;allocators&gt;-Makros'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::ALLOCATOR_DECL
- allocators/std::CACHE_CHUNKLIST
- allocators/std::CACHE_FREELIST
- allocators/std::CACHE_SUBALLOC
- allocators/std::SYNC_DEFAULT
ms.assetid: 9cb5ee07-1ff9-4594-ae32-3c8c6efb511a
helpviewer_keywords:
- std::ALLOCATOR_DECL [C++]
- std::CACHE_CHUNKLIST [C++]
- std::CACHE_FREELIST [C++]
- std::CACHE_SUBALLOC [C++]
- std::SYNC_DEFAULT [C++]
ms.openlocfilehash: a8b988511d0cdd46ae7f41bce29eb26f593a57c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364967"
---
# <a name="ltallocatorsgt-macros"></a>&lt;allocators&gt;-Makros

||||
|-|-|-|
|[ALLOCATOR_DECL](#allocator_decl)|[CACHE_CHUNKLIST](#cache_chunklist)|[Cache_freelist](#cache_freelist)|
|[CACHE_SUBALLOC](#cache_suballoc)|[SYNC_DEFAULT](#sync_default)|

## <a name="allocator_decl"></a><a name="allocator_decl"></a>ALLOCATOR_DECL

Gibt eine Zuweisungsklassenvorlage ab.

```cpp
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```

### <a name="remarks"></a>Bemerkungen

Das Makro liefert eine `template <class Type> class name {.....}` Vorlagendefinition `template <> class name<void> {.....}` und eine Spezialisierung, die zusammen eine Zuweisungsklassenvorlage definieren, die den Synchronisierungsfilter `sync` und einen Cache vom Typ `cache`verwendet.

Für Compiler, die Neubindungen kompilieren können, sieht die resultierende Vorlagendefinition wie folgt aus:

```cpp
struct rebind
   {    /* convert a name<Type> to a name<Other> */
   typedef name<Other> other;
   };
```

Für Compiler, die Neubindungen nicht kompilieren können, sieht die resultierende Vorlagendefinition wie folgt aus:

```cpp
template <class Type<class name
    : public stdext::allocators::allocator_base<Type,
    sync<stdext::allocators::rts_alloc<cache>>>
{
public:
    name() {}
    template <class Other>
    name(const name<Other>&) {}
    template <class Other>
    name& operator= (const name<Other>&)
    {
        return *this;
    }
};
```

## <a name="cache_chunklist"></a><a name="cache_chunklist"></a>CACHE_CHUNKLIST

Gibt `stdext::allocators::cache_chunklist<sizeof(Type)>` aus.

```cpp
#define CACHE_CHUNKLIST <cache_class>
```

### <a name="remarks"></a>Bemerkungen

## <a name="cache_freelist"></a><a name="cache_freelist"></a>Cache_freelist

Gibt `stdext::allocators::cache_freelist<sizeof(Type), max>` aus.

```cpp
#define CACHE_FREELIST(max) <cache_class>
```

### <a name="remarks"></a>Bemerkungen

## <a name="cache_suballoc"></a><a name="cache_suballoc"></a>CACHE_SUBALLOC

Gibt `stdext::allocators::cache_suballoc<sizeof(Type)>` aus.

```cpp
#define CACHE_SUBALLOC <cache_class>
```

### <a name="remarks"></a>Bemerkungen

## <a name="sync_default"></a><a name="sync_default"></a>SYNC_DEFAULT

Gibt einen Synchronisierungsfilter aus.

```cpp
#define SYNC_DEFAULT <sync_template>
```

### <a name="remarks"></a>Bemerkungen

Wenn ein Compiler das Kompilieren sowohl von Singlethread- als auch von Multithread-Anwendungen unterstützt, gibt das Makro für die Singlethread-Anwendung `stdext::allocators::sync_none` aus; andernfalls gibt es `stdext::allocators::sync_shared` aus.

## <a name="see-also"></a>Siehe auch

[\<Zuallokatoren>](../standard-library/allocators-header.md)

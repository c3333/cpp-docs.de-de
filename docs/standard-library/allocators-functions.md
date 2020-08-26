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
ms.openlocfilehash: dbf7577969ec43de47339bf80327007ac857a5a7
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834972"
---
# <a name="ltallocatorsgt-macros"></a>&lt;allocators&gt;-Makros

:::row:::
   :::column span="":::
      [`ALLOCATOR_DECL`](#allocator_decl)\
      [`CACHE_CHUNKLIST`](#cache_chunklist)
   :::column-end:::
   :::column span="":::
      [`CACHE_FREELIST`](#cache_freelist)
   :::column-end:::
   :::column span="":::
      [`CACHE_SUBALLOC`](#cache_suballoc)
   :::column-end:::
   :::column span="":::
      [`SYNC_DEFAULT`](#sync_default)
   :::column-end:::
:::row-end:::

## <a name="allocator_decl"></a><a name="allocator_decl"></a> ALLOCATOR_DECL

Ergibt eine zuordnerklassenvorlage.

```cpp
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```

### <a name="remarks"></a>Bemerkungen

Das-Makro gibt eine Vorlagen Definition `template <class Type> class name {.....}` und eine Spezialisierung `template <> class name<void> {.....}` aus, die gemeinsame eine zuordnerklassenvorlage definieren, die den Synchronisierungs Filter `sync` und einen Cache des Typs verwendet `cache` .

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

## <a name="cache_chunklist"></a><a name="cache_chunklist"></a> CACHE_CHUNKLIST

Gibt `stdext::allocators::cache_chunklist<sizeof(Type)>` aus.

```cpp
#define CACHE_CHUNKLIST <cache_class>
```

### <a name="remarks"></a>Bemerkungen

## <a name="cache_freelist"></a><a name="cache_freelist"></a> CACHE_FREELIST

Gibt `stdext::allocators::cache_freelist<sizeof(Type), max>` aus.

```cpp
#define CACHE_FREELIST(max) <cache_class>
```

### <a name="remarks"></a>Bemerkungen

## <a name="cache_suballoc"></a><a name="cache_suballoc"></a> CACHE_SUBALLOC

Gibt `stdext::allocators::cache_suballoc<sizeof(Type)>` aus.

```cpp
#define CACHE_SUBALLOC <cache_class>
```

### <a name="remarks"></a>Bemerkungen

## <a name="sync_default"></a><a name="sync_default"></a> SYNC_DEFAULT

Gibt einen Synchronisierungsfilter aus.

```cpp
#define SYNC_DEFAULT <sync_template>
```

### <a name="remarks"></a>Bemerkungen

Wenn ein Compiler das Kompilieren sowohl von Singlethread- als auch von Multithread-Anwendungen unterstützt, gibt das Makro für die Singlethread-Anwendung `stdext::allocators::sync_none` aus; andernfalls gibt es `stdext::allocators::sync_shared` aus.

## <a name="see-also"></a>Weitere Informationen

[\<allocators>](allocators-header.md)

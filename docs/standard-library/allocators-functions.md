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
ms.openlocfilehash: 5355661e370daf8826541c036f7301e5c25788d7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875922"
---
# <a name="ltallocatorsgt-macros"></a>&lt;allocators&gt;-Makros

||||
|-|-|-|
|[ALLOCATOR_DECL](#allocator_decl)|[CACHE_CHUNKLIST](#cache_chunklist)|[CACHE_FREELIST](#cache_freelist)|
|[CACHE_SUBALLOC](#cache_suballoc)|[SYNC_DEFAULT](#sync_default)|

## <a name="allocator_decl"></a> ALLOCATOR_DECL

Ergibt eine zuordnerklassenvorlage.

```cpp
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```

### <a name="remarks"></a>Bemerkungen

Das-Makro ergibt eine Vorlagen Definition `template <class Type> class name {.....}` und eine Spezialisierung `template <> class name<void> {.....}` die eine zuordnerklassenvorlage definieren, die den Synchronisierungs Filter verwendet `sync` und einen Cache vom Typ `cache`.

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

## <a name="cache_chunklist"></a> CACHE_CHUNKLIST

Gibt `stdext::allocators::cache_chunklist<sizeof(Type)>` aus.

```cpp
#define CACHE_CHUNKLIST <cache_class>
```

### <a name="remarks"></a>Bemerkungen

## <a name="cache_freelist"></a> CACHE_FREELIST

Gibt `stdext::allocators::cache_freelist<sizeof(Type), max>` aus.

```cpp
#define CACHE_FREELIST(max) <cache_class>
```

### <a name="remarks"></a>Bemerkungen

## <a name="cache_suballoc"></a> CACHE_SUBALLOC

Gibt `stdext::allocators::cache_suballoc<sizeof(Type)>` aus.

```cpp
#define CACHE_SUBALLOC <cache_class>
```

### <a name="remarks"></a>Bemerkungen

## <a name="sync_default"></a> SYNC_DEFAULT

Gibt einen Synchronisierungsfilter aus.

```cpp
#define SYNC_DEFAULT <sync_template>
```

### <a name="remarks"></a>Bemerkungen

Wenn ein Compiler das Kompilieren sowohl von Singlethread- als auch von Multithread-Anwendungen unterstützt, gibt das Makro für die Singlethread-Anwendung `stdext::allocators::sync_none` aus; andernfalls gibt es `stdext::allocators::sync_shared` aus.

## <a name="see-also"></a>Weitere Informationen

[\<allocators>](../standard-library/allocators-header.md)

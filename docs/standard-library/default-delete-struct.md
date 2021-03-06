---
title: default_delete-Struktur
ms.date: 04/04/2019
f1_keywords:
- memory/std::default_delete
helpviewer_keywords:
- default_delete struct
ms.openlocfilehash: 8baa9f5d294cf083fd55414cd529e438f328d1a1
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845080"
---
# <a name="default_delete-struct"></a>default_delete-Struktur

Ein vordefiniertes Funktionsobjekt, das den Divisionsvorgang (`operator/`) auf den Argumenten ausführt.

## <a name="syntax"></a>Syntax

```cpp
template <class T>
    struct default_delete
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<memory>

**Namespace:** std

## <a name="members"></a>Member

### <a name="constructors"></a>Konstruktoren

|Name|Beschreibung|
|-|-|
|[default_delete](#default_delete)|Der Konstruktor für Objekte des Typs `default_delete`.|

### <a name="operators"></a>Operatoren

|Name|Beschreibung|
|-|-|
|[Operator ()](#op_paren)|Ein Verweis Operator, auf den zugegriffen werden soll `default_delete` .|

## <a name="default_delete"></a><a name="default_delete"></a> default_delete

Der Konstruktor für Objekte des Typs `default_delete`.

```cpp
constexpr default_delete() noexcept = default;
template <class U>
    default_delete(const default_delete<U>&) noexcept;
```

## <a name="operator"></a><a name="op_paren"></a> Operator ()

Ein Verweis Operator, auf den zugegriffen werden soll `default_delete` .

```cpp
void operator()(T*) const;
```

## <a name="see-also"></a>Weitere Informationen

[\<memory>](../standard-library/memory.md)

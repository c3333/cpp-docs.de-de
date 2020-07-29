---
title: Allocator&lt;void&gt;-Klasse
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator<void>
- allocator<void>
helpviewer_keywords:
- allocator<void> class
ms.assetid: abfb40f5-c600-46a6-b130-f42c6535b2bd
ms.openlocfilehash: b6ca3f8b994756a21d85860fd8aff429ee38e58b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87204929"
---
# <a name="allocatorltvoidgt-class"></a>Allocator&lt;void&gt;-Klasse

Eine Spezialisierung der Klassen Vorlagen Zuweisung zum Typ **`void`** , die die Typen definiert, die in diesem Kontext sinnvoll sind.

## <a name="syntax"></a>Syntax

```cpp
template <>
class allocator<void> {
    typedef void *pointer;
    typedef const void *const_pointer;
    typedef void value_type;
    template <class Other>
    struct rebind;
    allocator();
    allocator(const allocator<void>&);

    template <class Other>
    allocator(const allocator<Other>&);

    template <class Other>
    allocator<void>& operator=(const allocator<Other>&);
};
```

## <a name="remarks"></a>Bemerkungen

Die Klasse spezialisiert explizit die Klassen Vorlagen [Zuweisung](allocator-class.md) für den Typ **`void`** . Die Konstruktoren und der Zuweisungs Operator Verhalten sich genauso wie für die Klassen Vorlage, Sie definieren jedoch nur die folgenden Typen:

- [const_pointer](allocator-class.md#const_pointer).

- [Zeiger](allocator-class.md#pointer).

- [value_type](allocator-class.md#value_type).

- [binden](allocator-class.md#rebind), eine Vorlage für eine vorgebundene Klasse.

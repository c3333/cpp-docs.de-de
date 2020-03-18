---
title: '&lt;new&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- new/std::new_handler
ms.assetid: aef01de1-06b5-4b6c-aebc-2c9f423d7e47
ms.openlocfilehash: 80123bc35422984ef92bdba6da45052d3461b1d7
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425376"
---
# <a name="ltnewgt-typedefs"></a>&lt;new&gt; typedefs

## <a name="hardware_constructive_interference_size"></a>hardware_constructive_interference_size

```cpp
inline constexpr size_t hardware_constructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Hinweise

Diese Zahl ist die empfohlene maximale Größe von zusammenhängenden Arbeitsspeicher, die von zwei Objekten belegt wird, auf die von gleichzeitigen Threads aus zugegriffen wird. Es muss mindestens `alignof(max_align_t)`sein.

### <a name="example"></a>Beispiel

```cpp
struct together { 
    atomic<int> dog;
    int puppy;
};

struct kennel {
    // Other data members...
    alignas(sizeof(together)) together pack;
    // Other data members...
};

static_assert(sizeof(together) <= hardware_constructive_interference_size);
```

## <a name="hardware_destructive_interference_size"></a>hardware_destructive_interference_size

```cpp
inline constexpr size_t hardware_destructive_interference_size = implementation-defined;
```

### <a name="remarks"></a>Hinweise

Diese Zahl ist der minimal Empfohlene Offset zwischen zwei Objekten, auf die gleichzeitig zugegriffen wird, um eine zusätzliche Leistungsminderung aufgrund von Konflikten zu vermeiden, die durch die Implementierung entstehen. Es muss mindestens `alignof(max_align_t)`sein.

### <a name="example"></a>Beispiel

```cpp
struct keep_apart {
    alignas(hardware_destructive_interference_size) atomic<int> cat;
    alignas(hardware_destructive_interference_size) atomic<int> dog;
};
```

## <a name="new_handler"></a>new_handler

Der Typ verweist auf eine Funktion, die als neuer Handler geeignet ist.

```cpp
typedef void (*new_handler)();
```

### <a name="remarks"></a>Hinweise

Diese Art von Handlerfunktion wird von **Operator new** oder `operator new[]` aufgerufen, wenn Sie eine Anforderung für zusätzlichen Speicher nicht erfüllen können.

### <a name="example"></a>Beispiel

Unter [set_new_handler](../standard-library/new-functions.md#set_new_handler) finden Sie ein Beispiel mit `new_handler` als Rückgabewert.

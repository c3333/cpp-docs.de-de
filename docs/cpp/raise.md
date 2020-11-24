---
title: __raise
description: Erfahren Sie, wie Sie das Microsoft C++-Erweiterungs Schlüsselwort `__raise` für die native Ereignis Behandlung verwenden.
ms.date: 11/20/2020
f1_keywords:
- __raise
- __raise_cpp
helpviewer_keywords:
- __raise keyword [C++]
ms.openlocfilehash: c9df602803062bc51b8c0cee13f17263cdc91786
ms.sourcegitcommit: b02c61667ff7f38e7add266d0aabd8463f2dbfa1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2020
ms.locfileid: "95483146"
---
# <a name="__raise-keyword"></a>`__raise` Schlüsselwort

Hebt die Aufrufsite eines Ereignisses hervor.

> [!NOTE]
> Ereignis Attribute in nativem C++ sind mit Standard-C++ nicht kompatibel. Sie werden nicht kompiliert, wenn Sie den [`/permissive-`](../build/reference/permissive-standards-conformance.md) Konformitäts Modus angeben.

## <a name="syntax"></a>Syntax

> **`__raise`** *`method-declarator`* **`;`**

## <a name="remarks"></a>Bemerkungen

Aus verwaltetem Code kann ein Ereignis nur aus der Klasse ausgelöst werden, in der es definiert ist. Weitere Informationen finden Sie unter [`event`](../extensions/event-cpp-component-extensions.md).

Das-Schlüsselwort **`__raise`** bewirkt, dass ein Fehler ausgegeben wird, wenn Sie ein nicht--Ereignis aufzurufen.

> [!NOTE]
> Eine von einer Vorlage gebildete Klasse oder Struktur kann keine Ereignisse enthalten.

## <a name="example"></a>Beispiel

```cpp
// EventHandlingRef_raise.cpp
struct E {
   __event void func1();
   void func1(int) {}

   void func2() {}

   void b() {
      __raise func1();
      __raise func1(1);  // C3745: 'int Event::bar(int)':
                         // only an event can be 'raised'
      __raise func2();   // C3745
   }
};

int main() {
   E e;
   __raise e.func1();
   __raise e.func1(1);  // C3745
   __raise e.func2();   // C3745
}
```

## <a name="see-also"></a>Siehe auch

[Keywords](../cpp/keywords-cpp.md)\
[Ereignis Behandlung](../cpp/event-handling.md)\
[`__event`](../cpp/event.md)\
[`__hook`](../cpp/hook.md)\
[`__unhook`](../cpp/unhook.md)\
[Komponentenerweiterungen für .NET und UWP](../extensions/component-extensions-for-runtime-platforms.md)

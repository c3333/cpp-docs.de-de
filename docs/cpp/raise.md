---
title: __raise
ms.date: 11/04/2016
f1_keywords:
- __raise
- __raise_cpp
helpviewer_keywords:
- __raise keyword [C++]
ms.assetid: 6f1ae418-5f0f-48b6-9f6e-8ea7e66b239a
ms.openlocfilehash: 9238e8e3e2fcd2c2f8b6431cfb0a79d452c5adf3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179171"
---
# <a name="__raise"></a>__raise

Hebt die Aufrufsite eines Ereignisses hervor.

## <a name="syntax"></a>Syntax

```
__raise method-declarator;
```

## <a name="remarks"></a>Bemerkungen

Aus verwaltetem Code kann ein Ereignis nur innerhalb der Klasse ausgelöst werden, in der es definiert ist. Weitere Informationen finden Sie unter [Event](../extensions/event-cpp-component-extensions.md) .

Das Schlüsselwort **__raise** bewirkt, dass ein Fehler ausgegeben wird, wenn Sie ein nicht--Ereignis aufzurufen.

> [!NOTE]
>  Eine von einer Vorlage gebildete Klasse oder Struktur kann keine Ereignisse enthalten.

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

## <a name="see-also"></a>Weitere Informationen

[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[Ereignisbehandlung](../cpp/event-handling.md)<br/>
[Komponentenerweiterungen für Laufzeitplattformen](../extensions/component-extensions-for-runtime-platforms.md)

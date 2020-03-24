---
title: Klassen und Strukturen (C++)
ms.date: 05/07/2019
helpviewer_keywords:
- C++, classes and structs
ms.assetid: 516dd496-13fb-4f17-845a-e9ca45437873
ms.openlocfilehash: 19d95c9519670db39f3ca467aff794233823d7ba
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180887"
---
# <a name="classes-and-structs-c"></a>Klassen und Strukturen (C++)

In diesem Abschnitt werden die C++-Klassen und -Strukturen vorgestellt. Die zwei Konstrukte sind identisch in C++. Der Unterschied besteht jedoch darin, dass der Standardzugriff in Strukturen öffentlich ist, während der Standard in Klassen privat ist.

Klassen und Strukturen sind die Konstrukte, anhand denen Sie Ihre eigenen Typen definieren. Klassen und Strukturen können Datenmember und Memberfunktionen enthalten. Mit diesen können Sie den Status und das Verhalten des Typs beschreiben.

Die folgenden Themen werden behandelt:

- [class](../cpp/class-cpp.md)

- [struct](../cpp/struct-cpp.md)

- [Klassenmembers (Übersicht)](../cpp/class-member-overview.md)

- [Memberzugriffssteuerung](../cpp/member-access-control-cpp.md)

- [Vererbung](../cpp/inheritance-cpp.md)

- [Statische Member](../cpp/static-members-cpp.md)

- [Benutzerdefinierte Typkonvertierungen](../cpp/user-defined-type-conversions-cpp.md)

- [Änderbare Datenmember (änderbarer Spezifizierer)](../cpp/mutable-data-members-cpp.md)

- [Geschachtelte Klassendeklarationen](../cpp/nested-class-declarations.md)

- [Anonyme Klassentypen](../cpp/anonymous-class-types.md)

- [Zeiger auf Member](../cpp/pointers-to-members.md)

- [this-Zeiger](../cpp/this-pointer.md)

- [C++-Bitfelder](../cpp/cpp-bit-fields.md)

Die drei Klassentypen sind "structure", "class" und "union". Sie werden mit den Schlüsselwörtern " [struct](../cpp/struct-cpp.md)", " [Class](../cpp/class-cpp.md)" und " [Union](../cpp/unions.md) " deklariert. In der folgenden Tabelle werden die Unterschiede zwischen den drei Klassentypen gezeigt.

Weitere Informationen zu Unions finden Sie unter [Unions](../cpp/unions.md). Informationen zu Klassen und Strukturen in C++/CLI und C++/CX finden Sie unter [Klassen und Strukturen](../extensions/classes-and-structs-cpp-component-extensions.md).

### <a name="access-control-and-constraints-of-structures-classes-and-unions"></a>Zugriffssteuerung und Einschränkungen von Strukturen, Klassen und Unions

|Strukturen|Klassen|Unions|
|----------------|-------------|------------|
|Klassen Schlüssel ist **struct**|Klassen Schlüssel ist **Klasse**|Klassen Schlüssel ist **Union**|
|Der Standardzugriff ist öffentlich.|Der Standardzugriff ist privat.|Der Standardzugriff ist öffentlich.|
|Keine Verwendungseinschränkungen|Keine Verwendungseinschränkungen|Verwenden Sie jeweils nur einen Member.|

## <a name="see-also"></a>Weitere Informationen

[C++-Programmiersprachenreferenz](../cpp/cpp-language-reference.md)

---
title: Klassen und Strukturen (C++)
ms.date: 05/07/2019
helpviewer_keywords:
- C++, classes and structs
ms.assetid: 516dd496-13fb-4f17-845a-e9ca45437873
ms.openlocfilehash: d593f6575fec64aa0eb14c7aa0fcbb5c4eb66691
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220599"
---
# <a name="classes-and-structs-c"></a>Klassen und Strukturen (C++)

In diesem Abschnitt werden die C++-Klassen und -Strukturen vorgestellt. Die zwei Konstrukte sind identisch in C++. Der Unterschied besteht jedoch darin, dass der Standardzugriff in Strukturen öffentlich ist, während der Standard in Klassen privat ist.

Klassen und Strukturen sind die Konstrukte, anhand denen Sie Ihre eigenen Typen definieren. Klassen und Strukturen können Datenmember und Memberfunktionen enthalten. Mit diesen können Sie den Status und das Verhalten des Typs beschreiben.

Die folgenden Themen werden behandelt:

- [class](../cpp/class-cpp.md)

- [struct](../cpp/struct-cpp.md)

- [Übersicht über Klassenmember](../cpp/class-member-overview.md)

- [Mitglied Access Control](../cpp/member-access-control-cpp.md)

- [Vererbung](../cpp/inheritance-cpp.md)

- [Statische Member](../cpp/static-members-cpp.md)

- [Benutzerdefinierte Typkonvertierungen](../cpp/user-defined-type-conversions-cpp.md)

- [Änderbare Datenmember (mutable Spezifizierer)](../cpp/mutable-data-members-cpp.md)

- [Klassen Deklarationen in der Liste](../cpp/nested-class-declarations.md)

- [Anonyme Klassentypen](../cpp/anonymous-class-types.md)

- [Zeiger auf Member](../cpp/pointers-to-members.md)

- [this-Zeiger](../cpp/this-pointer.md)

- [C++-Bitfelder](../cpp/cpp-bit-fields.md)

Die drei Klassentypen sind "structure", "class" und "union". Sie werden mit den Schlüsselwörtern " [struct](../cpp/struct-cpp.md)", " [Class](../cpp/class-cpp.md)" und " [Union](../cpp/unions.md) " deklariert. In der folgenden Tabelle werden die Unterschiede zwischen den drei Klassentypen gezeigt.

Weitere Informationen zu Unions finden Sie unter [Unions](../cpp/unions.md). Informationen zu Klassen und Strukturen in C++/CLI und C++/CX finden Sie unter [Klassen und Strukturen](../extensions/classes-and-structs-cpp-component-extensions.md).

### <a name="access-control-and-constraints-of-structures-classes-and-unions"></a>Zugriffssteuerung und Einschränkungen von Strukturen, Klassen und Unions

|Strukturen|Klassen|Unions|
|----------------|-------------|------------|
|Klassen Schlüssel ist**`struct`**|Klassen Schlüssel ist**`class`**|Klassen Schlüssel ist**`union`**|
|Der Standardzugriff ist öffentlich.|Der Standardzugriff ist privat.|Der Standardzugriff ist öffentlich.|
|Keine Verwendungseinschränkungen|Keine Verwendungseinschränkungen|Verwenden Sie jeweils nur einen Member.|

## <a name="see-also"></a>Siehe auch

[C++-Programmiersprachenreferenz](../cpp/cpp-language-reference.md)

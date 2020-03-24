---
title: Vererbung  (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
ms.openlocfilehash: 214900f8f36de0fa90ffcd6ca75f3a4e6e2c0777
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178255"
---
# <a name="inheritance--c"></a>Vererbung  (C++)

In diesem Abschnitt wird beschrieben, wie abgeleitete Klassen verwendet werden, um erweiterbare Programme zu erzeugen.

## <a name="overview"></a>Übersicht

Neue Klassen können aus vorhandenen Klassen abgeleitet werden, die einen Mechanismus namens "Vererbung" verwenden (siehe die Informationen, die in einer [einzelnen Vererbung](../cpp/single-inheritance.md)beginnen). Klassen, die zur Ableitung verwendet werden, werden als "Basisklassen" einer bestimmten abgeleiteten Klasse bezeichnet. Eine abgeleitete Klasse wird mit der folgenden Syntax deklariert:

```cpp
class Derived : [virtual] [access-specifier] Base
{
   // member list
};
class Derived : [virtual] [access-specifier] Base1,
   [virtual] [access-specifier] Base2, . . .
{
   // member list
};
```

Nach dem Tag für die Klasse wird ein Doppelpunkt gefolgt von einer Liste mit grundlegenden Spezifikationen angezeigt.  Die sogenannten Basisklassen müssen zuvor deklariert werden.  Die Basis Spezifikationen können einen Zugriffsspezifizierer enthalten, bei dem es sich um eines der Schlüsselwörter **Public**, **Protected** oder **private**handelt.  Diese Zugriffsspezifizierer werden vor dem Basisklassennamen angezeigt und gelten nur für diese Basisklasse.  Diese Spezifizierer steuern die Berechtigung der abgeleiteten Klasse, die für Member der Basisklasse zu verwenden sind.  Informationen zum Zugriff auf Basisklassenmember finden Sie unter Members [-Access Control](../cpp/member-access-control-cpp.md) .  Wenn der Zugriffsspezifizierer weggelassen wird, wird der Zugriff auf diese Basis als **Privat**betrachtet.  Die Basis Spezifikationen können das Schlüsselwort **Virtual** enthalten, um die virtuelle Vererbung anzugeben.  Dieses Schlüsselwort kann vor oder nach dem Zugriffsspezifizierer angezeigt werden, falls vorhanden.  Wenn virtuelle Vererbung verwendet wird, wird die Basisklasse als virtuelle Basisklasse bezeichnet.

Es können mehrere durch Kommas getrennte Basisklasse angegeben werden.  Wenn eine einzelne Basisklasse angegeben wird, ist das Vererbungs Modell eine [einzelne Vererbung](../cpp/single-inheritance.md). Wenn mehr als eine Basisklasse angegeben ist, wird das Vererbungs Modell als [mehrfache Vererbung](../cpp/multiple-base-classes.md)bezeichnet.

Die folgenden Themen werden behandelt:

- [Einfache Vererbung](../cpp/single-inheritance.md)

- [Mehrere Basisklassen](../cpp/multiple-base-classes.md)

- [Virtuelle Funktionen](../cpp/virtual-functions.md)

- [Explizite über schreibungen](../cpp/explicit-overrides-cpp.md)

- [Abstrakte Klassen](../cpp/abstract-classes-cpp.md)

- [Zusammenfassung der Bereichs Regeln](../cpp/summary-of-scope-rules.md)

Die [__super](../cpp/super.md) -und [__interface](../cpp/interface.md) Schlüsselwörter sind in diesem Abschnitt dokumentiert.

## <a name="see-also"></a>Weitere Informationen

[C++-Programmiersprachenreferenz](../cpp/cpp-language-reference.md)

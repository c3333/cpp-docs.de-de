---
title: Makros und C++
ms.date: 08/29/2019
helpviewer_keywords:
- macros, C++
- macros
ms.assetid: 83a344c1-73c9-4ace-8b93-cccfb62c6133
ms.openlocfilehash: 3b8721644e49a8bd289939d216c233da3286fd0a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219403"
---
# <a name="macros-and-c"></a>Makros und C++

C++ bietet neue Funktionen, von denen einige von der ANSI C-präprozessorbereitstellung unterstützt werden. Diese neuen Funktionen erweitern die Typsicherheit und die Voraussagbarkeit der Sprache:

- In C++ können Objekte, die als deklariert **`const`** werden, in konstanten Ausdrücken verwendet werden. Sie ermöglicht es Programmen, Konstanten zu deklarieren, die über Typ-und Wert Informationen verfügen. Sie können Enumerationen deklarieren, die mit dem Debugger symbolisch angezeigt werden können. Wenn Sie die `#define` Präprozessordirektive zum Definieren von Konstanten verwenden, ist Sie nicht so präzise und nicht typsicher. Für ein-Objekt ist kein Speicher zugeordnet **`const`** , es sei denn, das Programm enthält einen Ausdruck, der seine Adresse annimmt.

- Funktionstypmakros werden von der C++-Inlinefunktion abgelöst. Im Vergleich zu Makros haben Inlinefunktionen folgende Vorteile:

  - Typsicherheit. Inlinefunktionen unterliegen derselben Typüberprüfung wie normale Funktionen. Makros sind nicht typsicher.

  - Korrekte Behandlung von Argumenten, die Nebeneffekte haben. Inline Funktionen Werten die Ausdrücke aus, die als Argumente bereitgestellt werden, bevor der Funktions Text eingegeben wird. Daher besteht keine Möglichkeit, dass ein Ausdruck mit Nebeneffekten unsicher ist.

Weitere Informationen zu Inline Funktionen finden Sie unter [Inline, __inline \_ _forceinline](../cpp/inline-functions-cpp.md).

Aus Gründen der Abwärtskompatibilität werden alle Präprozessorfunktionen, die in ANSI C und in früheren C++-Spezifikationen vorhanden sind, für Microsoft C++ beibehalten.

## <a name="see-also"></a>Weitere Informationen

[Vordefinierte Makros](../preprocessor/predefined-macros.md)\
[Makros (C/C++)](../preprocessor/macros-c-cpp.md)

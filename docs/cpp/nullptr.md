---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 51df20ea00e5dd77ab1fc1a2a01253b8f788ad0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358855"
---
# <a name="nullptr"></a>nullptr

Legt eine NULL-Zeiger-Konstante vom Typ `std::nullptr_t` fest, der in einen beliebigen unformatierten Zeigertyp konvertiert werden kann.  Obwohl Sie das Schlüsselwort **nullptr** verwenden können, ohne Header `std::nullptr_t`einzuschließen, müssen Sie `<cstddef>`ihn definieren, wenn der Code den Typ verwendet.

> [!NOTE]
> Das **Schlüsselwort nullptr** ist auch in C++/CLI für Anwendungen mit verwaltetem Code definiert und kann nicht mit dem Schlüsselwort ISO Standard C++ ausgetauscht werden. Wenn Der Code mithilfe der [/clr-Compileroption](../build/reference/clr-common-language-runtime-compilation.md) kompiliert werden `__nullptr` kann, die auf verwalteten Code abzielt, verwenden Sie sie in einer beliebigen Codezeile, in der Sie sicherstellen müssen, dass der Compiler die systemeigene C++-Interpretation verwendet. Weitere Informationen finden Sie unter [nullptr](../extensions/nullptr-cpp-component-extensions.md).

## <a name="remarks"></a>Bemerkungen

Vermeiden Sie die`0`Verwendung von NULL oder Null ( ) als Nullzeigerkonstante; **nullptr** ist weniger anfällig für Missbrauch und funktioniert in den meisten Situationen besser.  Beispiel: Wenn `func(std::pair<const char *, double>)` vorgegeben ist, verursacht der Aufruf von `func(std::make_pair(NULL, 3.14))` einen Compilerfehler.  Die Makro-NULL wird auf `0` erweitert, sodass der Aufruf `std::make_pair(0, 3.14)` den Wert `std::pair<int, double>` zurückgibt, der nicht in den Parametertyp `std::pair<const char *, double>` von func() konvertierbar ist.  Durch Aufrufen von `func(std::make_pair(nullptr, 3.14))` ist die Kompilierung erfolgreich, da `std::make_pair(nullptr, 3.14)` den Wert `std::pair<std::nullptr_t, double>` zurückgibt, der in `std::pair<const char *, double>` konvertiert werden kann.

## <a name="see-also"></a>Siehe auch

[Keywords](../cpp/keywords-cpp.md)<br/>
[nullptr](../extensions/nullptr-cpp-component-extensions.md)(C++/CLI)

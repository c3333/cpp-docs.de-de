---
title: nullptr
ms.date: 11/04/2016
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 223f4c3e8c838698f9716e241543db405c9394af
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177767"
---
# <a name="nullptr"></a>nullptr

Legt eine NULL-Zeiger-Konstante vom Typ `std::nullptr_t` fest, der in einen beliebigen unformatierten Zeigertyp konvertiert werden kann.  Obwohl Sie das-Schlüsselwort **nullptr** verwenden können, ohne Header einzuschließen, müssen Sie, wenn der Code den Typ `std::nullptr_t`verwendet, ihn definieren, indem Sie den Header `<cstddef>`einschließen.

> [!NOTE]
>  Das **nullptr** -Schlüsselwort wird auch C++in/CLI für verwaltete Code Anwendungen definiert und ist nicht mit dem ISO C++ -Standard Schlüsselwort austauschbar. Wenn Ihr Code mithilfe der [/CLR](../build/reference/clr-common-language-runtime-compilation.md) -Compileroption kompiliert werden kann, die verwalteten Code als Ziel verwendet, verwenden Sie `__nullptr` in einer beliebigen Codezeile, in der Sie sicherstellen müssen C++ , dass der Compiler die native Interpretation verwendet. Weitere Informationen finden Sie unter [nullptr](../extensions/nullptr-cpp-component-extensions.md).

## <a name="remarks"></a>Bemerkungen

Vermeiden Sie die Verwendung von NULL oder 0 (`0`) als NULL-Zeiger Konstante. **nullptr** ist weniger anfällig für Missbrauch und funktioniert in den meisten Situationen besser.  Beispiel: Wenn `func(std::pair<const char *, double>)` vorgegeben ist, verursacht der Aufruf von `func(std::make_pair(NULL, 3.14))` einen Compilerfehler.  Die Makro-NULL wird auf `0` erweitert, sodass der Aufruf `std::make_pair(0, 3.14)` den Wert `std::pair<int, double>` zurückgibt, der nicht in den Parametertyp `std::pair<const char *, double>` von func() konvertierbar ist.  Durch Aufrufen von `func(std::make_pair(nullptr, 3.14))` ist die Kompilierung erfolgreich, da `std::make_pair(nullptr, 3.14)` den Wert `std::pair<std::nullptr_t, double>` zurückgibt, der in `std::pair<const char *, double>` konvertiert werden kann.

## <a name="see-also"></a>Weitere Informationen

[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[nullptr](../extensions/nullptr-cpp-component-extensions.md)(C++/CLI)

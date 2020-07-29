---
title: nullptr
ms.date: 07/22/2020
f1_keywords:
- nullptr_cpp
helpviewer_keywords:
- nullptr keyword [C++]
ms.assetid: e9d80ea6-2506-4eb5-b47b-2349df085832
ms.openlocfilehash: 801ae927d6c9fb70c3187d10269e87097a879bfc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223628"
---
# <a name="nullptr"></a>nullptr

Das **`nullptr`** Schlüsselwort gibt eine NULL-Zeiger Konstante vom Typ an `std::nullptr_t` , die in einen beliebigen unformatierten Zeigertyp konvertiert werden kann.  Obwohl Sie das-Schlüsselwort verwenden können **`nullptr`** , ohne Header einzuschließen, `std::nullptr_t` müssen Sie es durch Einschließen des-Headers definieren, wenn der Code den-Typ verwendet `<cstddef>` .

> [!NOTE]
> Das **`nullptr`** Schlüsselwort wird auch in C++/CLI für verwaltete Code Anwendungen definiert und ist nicht mit dem ISO-Standard-C++-Schlüsselwort austauschbar. Wenn Ihr Code mithilfe der- [`/clr`](../build/reference/clr-common-language-runtime-compilation.md) Compileroption kompiliert werden kann, die verwalteten Code als Ziel verwendet, verwenden `__nullptr` Sie in jeder Codezeile, in der Sie sicherstellen müssen, dass der Compiler die native C++-Interpretation verwendet. Weitere Informationen finden Sie unter [ `nullptr` (C++/CLI und C++/CX)](../extensions/nullptr-cpp-component-extensions.md).

## <a name="remarks"></a>Bemerkungen

Vermeiden Sie `NULL` die Verwendung von oder NULL ( `0` ) als NULL-Zeiger Konstante; **`nullptr`** ist weniger anfällig für Missbrauch und funktioniert in den meisten Situationen besser.  Beispiel: Wenn `func(std::pair<const char *, double>)` vorgegeben ist, verursacht der Aufruf von `func(std::make_pair(NULL, 3.14))` einen Compilerfehler.  Das-Makro `NULL` wird auf erweitert `0` , sodass der-Rückruf `std::make_pair(0, 3.14)` zurückgibt `std::pair<int, double>` , der nicht `std::pair<const char *, double>` in den Parametertyp in konvertierbar ist `func` .  Durch Aufrufen von `func(std::make_pair(nullptr, 3.14))` ist die Kompilierung erfolgreich, da `std::make_pair(nullptr, 3.14)` den Wert `std::pair<std::nullptr_t, double>` zurückgibt, der in `std::pair<const char *, double>` konvertiert werden kann.

## <a name="see-also"></a>Siehe auch

[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[`nullptr`(C++/CLI und C++/CX)](../extensions/nullptr-cpp-component-extensions.md)

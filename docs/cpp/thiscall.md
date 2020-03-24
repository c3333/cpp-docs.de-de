---
title: __thiscall
ms.date: 11/04/2016
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: 8772159dca71bb7605af5e5919425065423d503d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188154"
---
# <a name="__thiscall"></a>__thiscall

**Microsoft-spezifisch**

Die **__thiscall** Aufruf Konvention wird für Element Funktionen verwendet und ist die Standard Aufruf Konvention, die C++ von Element Funktionen verwendet wird, die keine Variablen Argumente verwenden. Unter **__thiscall**bereinigt der aufgerufene den Stapel, was für `vararg` Funktionen nicht möglich ist. Argumente werden von rechts nach links auf dem Stapel abgelegt, wobei **dieser** Zeiger über Register ECX und nicht auf dem Stapel in der x86-Architektur übergeben wird.

Ein Grund für die Verwendung von **__thiscall** ist in Klassen, deren Element Funktionen `__clrcall` standardmäßig verwenden. In diesem Fall können Sie **__thiscall** verwenden, um einzelne Member-Funktionen aus nativem Code aufrufbar zu machen.

Beim Kompilieren mit [/clr: pure](../build/reference/clr-common-language-runtime-compilation.md)werden alle Funktionen und Funktionszeiger `__clrcall`, sofern nichts anderes angegeben ist. Die Compileroptionen **/clr: pure** und **/clr: Safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

In Releases vor Visual Studio 2005 konnte die **__thiscall** Aufruf Konvention nicht explizit in einem Programm angegeben werden, da **__thiscall** kein Schlüsselwort war.

`vararg` Member-Funktionen verwenden die **__cdecl** Aufruf Konvention. Alle Funktionsargumente werden auf dem Stapel abgelegt, wobei **dieser** Zeiger zuletzt auf dem Stapel abgelegt wurde.

Da diese Aufrufkonvention nur für C++ gültig ist, gibt es kein Schema zur C-Namensergänzung.

Auf Arm-und x64-Computern wird **__thiscall** vom Compiler akzeptiert und ignoriert.

Wenn die Funktion bei nicht statischen Klassenfunktionen abweichend definiert ist, muss der Aufrufkonventionsmodifizierer nicht in der abweichenden Definition angegeben werden. Das bedeutet, dass für nicht statische Membermethoden der Klasse zum Zeitpunkt der Definition die während der Deklaration angegebene Aufrufkonvention angenommen wird.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Argumentübergabe und Benennungskonventionen](../cpp/argument-passing-and-naming-conventions.md)

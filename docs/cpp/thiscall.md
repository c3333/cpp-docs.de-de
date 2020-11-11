---
title: __thiscall
description: Erfahren Sie mehr über die Microsoft-spezifische __thiscall Aufruf Konvention für x86-Klassenmember-Funktionen in Microsoft C++.
ms.date: 05/22/2020
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: 9b11dcf8dee928b687f942639ed72ead3659614b
ms.sourcegitcommit: 25f6d52eb9e5d84bd0218c46372db85572af81da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94448450"
---
# `__thiscall`

Die **Microsoft-spezifische** **`__thiscall`** Aufruf Konvention wird für C++-Klassenmember-Funktionen in der x86-Architektur verwendet. Dabei handelt es sich um die Standard Aufruf Konvention, die von Element Funktionen verwendet wird, die keine Variablen Argumente ( `vararg` Funktionen) verwenden.

Unter wird der Stapel durch den aufgerufenen **`__thiscall`** bereinigt, was für Funktionen nicht möglich ist `vararg` . Argumente werden von rechts nach links auf dem Stapel abgelegt. Der **`this`** Zeiger wird über Register ECX und nicht auf dem Stapel übermittelt.

Auf arm-, ARM64-und x64-Computern **`__thiscall`** wird vom Compiler akzeptiert und ignoriert. Dies liegt daran, dass Sie standardmäßig eine Register basierte Aufruf Konvention verwenden.

Ein Grund für die Verwendung **`__thiscall`** von ist die Verwendung von Klassen, deren Member-Funktionen **`__clrcall`** standardmäßig verwenden. In diesem Fall können Sie verwenden, **`__thiscall`** um einzelne Member-Funktionen aus nativem Code aufrufbar zu machen.

Beim Kompilieren mit [`/clr:pure`](../build/reference/clr-common-language-runtime-compilation.md) sind alle Funktionen und Funktionszeiger, **`__clrcall`** sofern nicht anders angegeben. Die **`/clr:pure`** **`/clr:safe`** Compileroptionen und sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 nicht unterstützt.

`vararg` Member-Funktionen verwenden die **`__cdecl`** Aufruf Konvention. Alle Funktionsargumente werden auf dem Stapel abgelegt, wobei der **`this`** Zeiger zuletzt auf dem Stapel abgelegt wird.

Da diese Aufruf Konvention nur auf C++ angewendet wird, verfügt sie über kein C-namens Dekorationsschema.

Wenn Sie eine nicht statische Klassenmember-Funktion out-of-Line definieren, geben Sie den Modifizierer für die Aufruf Konvention nur in der Deklaration an. Sie müssen ihn nicht erneut in der Out-of-Line-Definition angeben. Der Compiler verwendet die Aufruf Konvention, die während der Deklaration zum Zeitpunkt der Definition angegeben wird.

## <a name="see-also"></a>Siehe auch

[Argument Übergabe und Benennungs Konventionen](../cpp/argument-passing-and-naming-conventions.md)

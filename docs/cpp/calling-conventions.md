---
title: Aufrufkonventionen
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
ms.openlocfilehash: 432cb1b6910db5ea735288edfbf6aa9e10f0a486
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190286"
---
# <a name="calling-conventions"></a>Aufrufkonventionen

Der Compiler für Visual C/C++ stellt mehrere unterschiedliche Konventionen für das Aufrufen von internen und externen Funktionen bereit. Das Verständnis dieser verschiedenen Ansätze hilft Ihnen, Ihr Programm zu debuggen und den Code mit Routinen in Assemblysprache zu verknüpfen.

In diesen Themen werden die Unterschiede zwischen den Aufrufkonventionen, wie Argumente übergeben werden und wie Werte über Funktionen zurückgegeben werden, erläutert. Es werden auch reine Funktionsaufrufe, eine erweiterte Funktion, die es erlaubt, Ihren eigenen Einleitungs- und Epilogcode zu schreiben, besprochen.

Weitere Informationen zu Aufruf Konventionen für x64-Prozessoren finden Sie unter [Aufruf Konvention](../build/x64-calling-convention.md).

## <a name="topics-in-this-section"></a>Themen in diesem Abschnitt

- [Argument Übergabe und Benennungs Konventionen](../cpp/argument-passing-and-naming-conventions.md) (`__cdecl`, `__stdcall`, `__fastcall`und andere)

- [Aufrufbeispiel:Funktionsprototyp und Aufruf](../cpp/calling-example-function-prototype-and-call.md)

- [Verwenden von Naked-Funktionsaufrufen zum Schreiben von benutzerdefiniertem Prolog-/Epilogcode](../cpp/naked-function-calls.md)

- [Gleitkomma-Coprozessor und Aufrufkonventionen](../cpp/floating-point-coprocessor-and-calling-conventions.md)

- [Veraltete Aufruf Konventionen](../cpp/obsolete-calling-conventions.md)

## <a name="see-also"></a>Weitere Informationen

[Microsoft-spezifische Modifizierer](../cpp/microsoft-specific-modifiers.md)

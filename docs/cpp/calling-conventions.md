---
title: Aufrufkonventionen
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions
ms.assetid: 11b1e45c-8fd1-420b-bca0-a19e294c1d85
ms.openlocfilehash: d351ae064b8c9bdd0599a1d6981166371a62af58
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216608"
---
# <a name="calling-conventions"></a>Aufrufkonventionen

Der Compiler für Visual C/C++ stellt mehrere unterschiedliche Konventionen für das Aufrufen von internen und externen Funktionen bereit. Das Verständnis dieser verschiedenen Ansätze hilft Ihnen, Ihr Programm zu debuggen und den Code mit Routinen in Assemblysprache zu verknüpfen.

In diesen Themen werden die Unterschiede zwischen den Aufrufkonventionen, wie Argumente übergeben werden und wie Werte über Funktionen zurückgegeben werden, erläutert. Es werden auch reine Funktionsaufrufe, eine erweiterte Funktion, die es erlaubt, Ihren eigenen Einleitungs- und Epilogcode zu schreiben, besprochen.

Weitere Informationen zu Aufruf Konventionen für x64-Prozessoren finden Sie unter [Aufruf Konvention](../build/x64-calling-convention.md).

## <a name="topics-in-this-section"></a>Themen in diesem Abschnitt

- [Argument Übergabe und Benennungs Konventionen](../cpp/argument-passing-and-naming-conventions.md) ( **`__cdecl`** , **`__stdcall`** , **`__fastcall`** und andere)

- [Aufruf Beispiel: Funktionsprototyp und Aufruf](../cpp/calling-example-function-prototype-and-call.md)

- [Verwenden von reinen Funktionsaufrufen, um den benutzerdefinierten Einleitungs-/Epilogcode zu schreiben](../cpp/naked-function-calls.md)

- [Gleit Komma-Coprozessor und Aufruf Konventionen](../cpp/floating-point-coprocessor-and-calling-conventions.md)

- [Veraltete Aufrufkonventionen](../cpp/obsolete-calling-conventions.md)

## <a name="see-also"></a>Weitere Informationen

[Microsoft-spezifische modifiziererer](../cpp/microsoft-specific-modifiers.md)

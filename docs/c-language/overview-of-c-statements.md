---
title: Übersicht über C-Anweisungen
ms.date: 11/04/2016
helpviewer_keywords:
- semicolon, in C statements
- statements, C
- semicolon
- statements, about statements
- Visual C, statements
ms.assetid: 0d49837a-5399-4881-b60c-af5f4e9720de
ms.openlocfilehash: 6b6cf9ee7aab3f14b3cb4b48c10e59125391c14c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87211774"
---
# <a name="overview-of-c-statements"></a>Übersicht über C-Anweisungen

C-Anweisungen bestehen aus Token, Ausdrücken und anderen Anweisungen. Eine Anweisung, die eine Komponente einer andere Anweisung bildet, wird als "Text" der einschließenden Anweisung bezeichnet. Jeder Anweisungstyp, der von der folgenden Syntax angegeben wird, wird in diesem Abschnitt erläutert.

## <a name="syntax"></a>Syntax

*statement*: [labeled-statement](../c-language/goto-and-labeled-statements-c.md)

[compound-statement](../c-language/compound-statement-c.md)

[expression-statement](../c-language/expression-statement-c.md)

[selection-statement](../c-language/if-statement-c.md)

[iteration-statement](../c-language/do-while-statement-c.md)

[jump-statement](../c-language/break-statement-c.md)

[try-except-Anweisung](../c-language/try-except-statement-c.md) /* Microsoft-spezifisch \*/

[try-finally-Anweisung](../c-language/try-finally-statement-c.md) /\* Microsoft-spezifisch \*/

Häufig handelt es sich bei einem Anweisungstext um eine "Verbundanweisung ". Eine Verbundanweisung besteht aus anderen Anweisungen, die Schlüsselwörter enthalten können. Die Verbundanweisung steht in geschweiften Klammern ( **{ }** ). Alle anderen C-Anweisungen enden mit einem Semikolon ( **;** ). Das Semikolon ist ein Anweisungsabschlusszeichen.

Die Ausdrucksanweisung enthält einen C-Ausdruck, der die arithmetischen oder logischen Operatoren, die in [Ausdrücke und Zuweisungen](../c-language/expressions-and-assignments.md) eingeführt werden, enthalten kann. Die Null-Anweisung ist eine leere Anweisung.

Jede C-Anweisung kann mit einer identifizierende Bezeichnung, die aus einem Namen und einem Doppelpunkt besteht, beginnen. Da nur die **`goto`** -Anweisung Anweisungsbezeichnungen erkennt, werden Anweisungsbezeichnungen mit **`goto`** erläutert. Weitere Informationen finden Sie unter [The goto and Labeled Statements](../c-language/goto-and-labeled-statements-c.md) (Die goto- und Labeled-Anweisung).

## <a name="see-also"></a>Siehe auch

[Anweisungen](../c-language/statements-c.md)

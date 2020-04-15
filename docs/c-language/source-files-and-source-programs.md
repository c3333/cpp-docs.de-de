---
title: Quelldateien und Quellprogramme
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], source
- programs [C++], source
- source files, specifying in compiler
- source programs
ms.assetid: 18bb2826-17da-48e5-92a2-10e649f1bc9f
ms.openlocfilehash: ac906925be551c6ee4da08e200d4028047b3d041
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349881"
---
# <a name="source-files-and-source-programs"></a>Quelldateien und Quellprogramme

Ein Quellprogramm kann in eine oder mehrere "Quelldateien" oder in "Übersetzungseinheiten" aufgeteilt werden. Die Eingabe in den Compiler wird als "Übersetzungseinheit" bezeichnet.

## <a name="syntax"></a>Syntax

*translation-unit*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*external-declaration* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*translation-unit* *external-declaration*

*externe Erklärung*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*function-definition*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Erklärung*

[Übersicht über Deklarationen](../c-language/overview-of-declarations.md) gibt die Syntax für das `declaration`-Nichtterminal an, und in der *Präprozessorreferenz* wird erläutert, wie die [Übersetzungseinheit](../preprocessor/phases-of-translation.md) verarbeitet wird.

> [!NOTE]
> Eine Erläuterung der ANSI-Syntaxkonventionen finden Sie in der Einführung in die [C Language Syntax Summary](../c-language/c-language-syntax-summary.md).

Die Komponenten einer Übersetzungseinheit sind externe Deklarationen, die Funktionsdefinitionen und Bezeichnerdeklarationen enthalten. Diese Deklarationen und Definitionen können sich in den Quelldateien, Headerdateien, Bibliotheken und anderen Dateien befinden, die das Programm benötigt. Sie müssen jede Übersetzungseinheit kompilieren und die resultierenden Objektdateien verknüpfen, um ein Programm zu erstellen.

Ein Quellprogramm ist bei C eine Auflistung von Direktiven, Pragmas, Deklarationen, Definitionen, Anweisungsblöcken und Funktionen. Um als gültige Komponenten eines Microsoft-C-Programms zu gelten, muss jede Komponente die Syntax aufweisen, die in diesem Buch beschrieben wird. Die Komponenten können jedoch (gemäß den Regeln in diesem Buch) in beliebiger Reihenfolge im Programm angezeigt werden. Allerdings wirkt sich der Speicherort dieser Komponenten in einem Programm darauf aus, wie Variablen und Funktionen in einem Programm verwendet werden können. (Weitere Informationen erhalten Sie unter [Lebensdauer, Bereich, Sichtbarkeit und Verknüpfung](../c-language/lifetime-scope-visibility-and-linkage.md).)

Quelldateien müssen keine ausführbaren Anweisungen enthalten. Beispielsweise finden Sie es vielleicht hilfreich, Definitionen von Variablen in einer Quelldatei einzufügen und dann Verweise auf diese Variablen in anderen Quelldateien, die diese verwenden, zu deklarieren. Diese Vorgehensweise erleichtert das Suchen und ggf. Aktualisieren der Definitionen. Aus demselben Grund werden Konstanten und Makros häufig in separaten Dateien strukturiert, die "Includedateien" oder "Headerdateien" genannt werden und auf die nach Bedarf in Quelldateien verwiesen werden kann. Weitere Informationen zu [Makros](../preprocessor/macros-c-cpp.md) und [Includedateien](../preprocessor/hash-include-directive-c-cpp.md) finden Sie in der *Präprozessorreferenz*.

## <a name="see-also"></a>Siehe auch

[Programmstruktur](../c-language/program-structure.md)

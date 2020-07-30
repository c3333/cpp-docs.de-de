---
title: Compilerwarnung (Stufe 4) C4985
ms.date: 11/04/2016
f1_keywords:
- C4985
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
ms.openlocfilehash: 87537e960c858cc6741108cf191fbeb2a7a2a8d7
ms.sourcegitcommit: 6e55aeb538b1c39af754f82d6f7738a18f5aa031
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/29/2020
ms.locfileid: "87390012"
---
# <a name="compiler-warning-level-4-c4985"></a>Compilerwarnung (Stufe 4) C4985

> "*Symbol Name*": Attribute sind in vorheriger Deklaration nicht vorhanden.

Die Microsoft SAL-Anmerkungen (Source Code Annotation Language, Quellcodeanmerkungssprache) zur aktuellen Methodendeklaration oder -definition unterscheiden sich von den Anmerkungen zu einer früheren Deklaration. In der Definition und den Deklarationen einer Methode müssen dieselben SAL-Anmerkungen verwendet werden.

Die SAL stellt einen Satz Anmerkungen bereit, mit denen Sie beschreiben können, wie eine Funktion ihre Parameter verwendet, welche Annahmen sie über diese Parameter trifft, und wie ihr garantierte Ergebnis aussieht, wenn sie abgeschlossen wird. Die Anmerkungen sind in der Headerdatei „sal.h“ definiert.

Beachten Sie, dass die SAL-Makros nur dann erweitert werden, wenn das-Flag für das Projekt [`/analyze`](../../build/reference/analyze-code-analysis.md) angegeben wurde. Wenn Sie angeben **`/analyze`** , kann der Compiler C4985 auch dann auslösen, wenn keine Warnungen oder Fehler ohne auftreten **`/analyze`** .

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Verwenden Sie für die Definition einer Methode und deren Deklarationen dieselben SAL-Anmerkungen.

## <a name="see-also"></a>Siehe auch

[SAL-Anmerkungen](../../c-runtime-library/sal-annotations.md)

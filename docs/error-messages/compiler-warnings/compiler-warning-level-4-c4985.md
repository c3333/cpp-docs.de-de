---
title: Compilerwarnung (Stufe 4) C4985
ms.date: 11/04/2016
f1_keywords:
- C4985
helpviewer_keywords:
- C4985
ms.assetid: 832f001c-afe7-403d-a8b4-02334724c79e
ms.openlocfilehash: 82adb80310fb43c848c253f9bf5e436c8c379f35
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198094"
---
# <a name="compiler-warning-level-4-c4985"></a>Compilerwarnung (Stufe 4) C4985

"Symbolname": Attribute sind in vorheriger Deklaration nicht vorhanden.

Die Microsoft SAL-Anmerkungen (Source Code Annotation Language, Quellcodeanmerkungssprache) zur aktuellen Methodendeklaration oder -definition unterscheiden sich von den Anmerkungen zu einer früheren Deklaration. In der Definition und den Deklarationen einer Methode müssen dieselben SAL-Anmerkungen verwendet werden.

Die SAL stellt einen Satz Anmerkungen bereit, mit denen Sie beschreiben können, wie eine Funktion ihre Parameter verwendet, welche Annahmen sie über diese Parameter trifft, und wie ihr garantierte Ergebnis aussieht, wenn sie abgeschlossen wird. Die Anmerkungen sind in der Headerdatei „sal.h“ definiert.

Beachten Sie, dass die SAL-Makros nicht erweitert werden, es sei denn, für das Projekt ist das Kennzeichen [/ analyze](../../build/reference/analyze-code-analysis.md) angegeben. Wenn Sie **/analyze**angeben, kann der Compiler C4985 auslösen, selbst wenn ohne **/analyze**keine Warnungen oder Fehler angezeigt würden.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

1. Verwenden Sie für die Definition einer Methode und deren Deklarationen dieselben SAL-Anmerkungen.

## <a name="see-also"></a>Weitere Informationen

[SAL-Anmerkungen](../../c-runtime-library/sal-annotations.md)

---
title: try-finally-Anweisung (C)
ms.date: 11/04/2016
helpviewer_keywords:
- try-finally keyword [C]
- __finally keyword [C], try-finally statement syntax
- __finally keyword [C]
- structured exception handling, try-finally
ms.assetid: 514400c1-c322-4bf3-9e48-3047240b8a82
ms.openlocfilehash: b800daa7689cef769ce3a3b070c957f18e8794c9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213709"
---
# <a name="try-finally-statement-c"></a>try-finally-Anweisung (C)

**Microsoft-spezifisch**

Die `try-finally`-Anweisung ist eine Microsoft-Erweiterung zur Programmiersprache C, die es Zielanwendungen ermöglicht, den Bereinigungscode auszuführen, auch wenn die Ausführung eines Codeblocks unterbrochen wird. Die Bereinigung besteht aus Aufgaben wie z. B. Neuzuweisung von Arbeitsspeicher, Schließen von Dateien und Freigeben von Dateihandles. Die `try-finally`-Anweisung ist besonders nützlich für Routinen, in denen an mehreren Stellen eine Fehlerüberprüfung durchgeführt wird, die eine vorzeitige Rückgabe von der Routine verursachen könnte.

*try-finally-Anweisung*: **__try**  *compound-Anweisung*

**`__finally`**  *Verbundanweisung*

Die Verbundanweisung nach der `__try`-Klausel ist der abgesicherte Abschnitt. Die Verbundanweisung nach der **`__finally`** -Klausel ist der Beendigungshandler. Der Handler gibt eine Reihe von Aktionen an, die beim Verlassen des abgesicherten Abschnitts ausgeführt werden, ungeachtet dessen, ob der abgesicherte Abschnitt durch eine Ausnahme (ungewöhnlicher Abbruch) oder durch ein standardmäßiges Fortfahren (gewöhnlicher Abbruch) verlassen wird.

Die Steuerung erreicht eine `__try`-Anweisung durch einfache sequenzielle Ausführung (Fortfahren). Wenn die Steuerung zur `__try`-Anweisung wechselt, wird der zugehörige Handler aktiv. Die Ausführung erfolgt folgendermaßen:

1. Der geschützte Bereich wird ausgeführt.

1. Der Beendigungshandler wird aufgerufen.

1. Nach Abschluss des Beendigungshandlers wird die Ausführung nach der **`__finally`** -Anweisung fortgesetzt. Unabhängig davon, wie der geschützte Abschnitt endet (z. B. Verlassen des geschützten Teils über eine **`goto`** -Anweisung oder über eine **`return`** -Anweisung), wird der Beendigungshandler ausgeführt, bevor die Ablaufsteuerung den geschützten Abschnitt verlässt.

**`__leave** keyword is valid within a `try-finally` statement block. The effect of **`__leave** wird verwendet, um zum Ende des `try-finally`-Blocks zu springen. Der Beendigungshandler wird sofort ausgeführt. Zwar kann dasselbe Ergebnis mit einer **`goto`** -Anweisung erzielt werden, eine **`goto`** -Anweisung verursacht jedoch eine Stapelentladung. Die **__leave**-Anweisung ist effizienter, da sie keine Stapelentladung verursacht.

Das Beenden einer `try-finally`-Anweisung mithilfe einer **`return`** -Anweisung oder der `longjmp`-Laufzeitfunktion wird als nicht ordnungsgemäße Beendigung angesehen. Es ist nicht zulässig, in eine `__try`-Anweisung zu springen, wohingegen das Herausspringen aus einer solchen zulässig ist. Alle **`__finally`** -Anweisungen, die zwischen dem Anfangspunkt und dem Ziel aktiv sind, müssen ausgeführt werden. Dies ist eine so genannte "lokale Entladung".

Der Beendigungshandler wird nicht aufgerufen, wenn ein Prozess während der Ausführung einer `try-finally`-Anweisung abgebrochen wird.

> [!NOTE]
> Die strukturierte Ausnahmebehandlung arbeitet mit C- und C++-Quelldateien. Sie ist jedoch nicht speziell für C++ entwickelt. Sie können sicherstellen, dass der Code portabler ist, indem Sie die C++-Ausnahmebehandlung verwenden. Der C++-Ausnahmebehandlungsmechanismus ist außerdem viel flexibler, da er Ausnahmen eines beliebigen Typs behandeln kann.

> [!NOTE]
> Für C++-Programme sollte die C++-Ausnahmebehandlung anstelle der strukturierten Ausnahmebehandlung verwendet werden. Weitere Informationen finden Sie unter [Ausnahmebehandlung](../cpp/exception-handling-in-visual-cpp.md) in *C++-Sprachreferenz*.

Weitere Informationen zur Funktionsweise der `try-finally`-Anweisung finden Sie im Beispiel für die [try-except-Anweisung](../c-language/try-except-statement-c.md).

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[try-finally-Anweisung](../cpp/try-finally-statement.md)

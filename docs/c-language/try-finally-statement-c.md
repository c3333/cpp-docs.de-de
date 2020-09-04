---
title: try-finally-Anweisung (C)
description: Microsoft C/C++ implementiert die strukturierte Ausnahmebehandlung (Structured Exception Handling, SEH) über eine Spracherweiterung für die try-finally-Anweisung.
ms.date: 08/24/2020
helpviewer_keywords:
- try-finally keyword [C]
- __finally keyword [C], try-finally statement syntax
- __finally keyword [C]
- structured exception handling, try-finally
ms.assetid: 514400c1-c322-4bf3-9e48-3047240b8a82
ms.openlocfilehash: 6f9cf901ed0a82b355880225c902ec4fc3e1082b
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898705"
---
# <a name="try-finally-statement-c"></a>try-finally-Anweisung (C)

**Microsoft-spezifisch**

Die `try-finally`-Anweisung ist eine Microsoft-Erweiterung zur Programmiersprache C, die es Zielanwendungen ermöglicht, den Bereinigungscode auszuführen, auch wenn die Ausführung eines Codeblocks unterbrochen wird. Die Bereinigung besteht aus Aufgaben wie z. B. Neuzuweisung von Arbeitsspeicher, Schließen von Dateien und Freigeben von Dateihandles. Die `try-finally`-Anweisung ist besonders nützlich für Routinen, in denen an mehreren Stellen eine Fehlerüberprüfung durchgeführt wird, die eine vorzeitige Rückgabe von der Routine verursachen könnte.

> *`try-finally-statement`*:\
> &emsp;**`__try`** *`compound-statement`* **`__finally`** *`compound-statement`*

Die Verbundanweisung nach der **`__try`** -Klausel ist der geschützte Abschnitt. Die Verbundanweisung nach der **`__finally`** -Klausel ist der Beendigungshandler. Der Handler gibt eine Reihe von Aktionen an, die bei Beendigung des geschützten Abschnitts ausgeführt werden. Es spielt keine Rolle, ob der geschützte Abschnitt durch eine Ausnahme (nicht ordnungsgemäße Beendigung) oder durch standardmäßiges Fortfahren (normale Beendigung) beendet wird.

Die Steuerung erreicht eine **`__try`** -Anweisung durch einfache sequenzielle Ausführung (Fortfahren). Wenn die Steuerung zur **`__try`** -Anweisung wechselt, wird der zugehörige Handler aktiv. Die Ausführung erfolgt folgendermaßen:

1. Der geschützte Bereich wird ausgeführt.

1. Der Beendigungshandler wird aufgerufen.

1. Nach Abschluss des Beendigungshandlers wird die Ausführung nach der **`__finally`** -Anweisung fortgesetzt. Unabhängig davon, wie der geschützte Abschnitt beendet wird (z. B. durch eine **`goto`** -Anweisung zum Verlassen des geschützten Teils oder durch eine **`return`** -Anweisung), wird der Beendigungshandler ausgeführt, bevor die Ablaufsteuerung den geschützten Abschnitt verlässt.

Das Schlüsselwort **`__leave`** ist innerhalb eines `try-finally`-Anweisungsblocks gültig. Der Zweck von **`__leave`** besteht darin, zum Ende des `try-finally`-Blocks zu springen. Der Beendigungshandler wird sofort ausgeführt. Zwar kann dasselbe Ergebnis mit einer **`goto`** -Anweisung erzielt werden, eine **`goto`** -Anweisung verursacht jedoch eine Stapelentladung. Die **`__leave`** -Anweisung ist effizienter, weil sie keine Stapelentladung verursacht.

Das Beenden einer `try-finally`-Anweisung mithilfe einer **`return`** -Anweisung oder der `longjmp`-Laufzeitfunktion wird als nicht ordnungsgemäße Beendigung angesehen. Es ist nicht zulässig, in eine **`__try`** -Anweisung zu springen, wohingegen das Herausspringen aus einer solchen zulässig ist. Alle **`__finally`** -Anweisungen, die zwischen dem Anfangspunkt und dem Ziel aktiv sind, müssen ausgeführt werden. Dies wird als *lokale Entladung* bezeichnet.

Der Beendigungshandler wird nicht aufgerufen, wenn ein Prozess während der Ausführung einer `try-finally`-Anweisung beendet wird.

> [!NOTE]
> Die strukturierte Ausnahmebehandlung arbeitet mit C- und C++-Quelldateien. Sie wurde jedoch nicht speziell für C++ entwickelt. Für portierbare C++-Programme sollte die C++-Ausnahmebehandlung anstelle der strukturierten Ausnahmebehandlung verwendet werden. Der C++-Ausnahmebehandlungsmechanismus ist außerdem viel flexibler, da er Ausnahmen eines beliebigen Typs behandeln kann. Weitere Informationen finden Sie unter [Ausnahmebehandlung](../cpp/exception-handling-in-visual-cpp.md) in der *C++-Sprachreferenz*.

Informationen zur Funktionsweise der `try-finally`-Anweisung finden Sie im Beispiel für die [`try-except`-Anweisung](../c-language/try-except-statement-c.md).

**ENDE der Microsoft-spezifischen Informationen**

## <a name="see-also"></a>Siehe auch

[`try-finally`-Anweisung (C++)](../cpp/try-finally-statement.md)

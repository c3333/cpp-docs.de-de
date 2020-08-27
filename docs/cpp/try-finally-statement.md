---
title: try-finally-Anweisung
description: Der Microsoft C++-Verweis auf die Anweisungen für die __try und __finally strukturierte Ausnahmebehandlung.
ms.date: 08/25/2020
f1_keywords:
- __try
- _try
- __leave_cpp
- __leave
- __finally_cpp
- __try_cpp
- __finally
- _finally
helpviewer_keywords:
- __try keyword [C++]
- __finally keyword [C++]
- __leave keyword [C++]
- try-catch keyword [C++], try-finally keyword
- try-finally keyword [C++]
- __finally keyword [C++], try-finally statement syntax
- __leave keyword [C++], try-finally statement
- structured exception handling [C++], try-finally
ms.assetid: 826e0347-ddfe-4f6e-a7bc-0398e0edc7c2
ms.openlocfilehash: edabbbe35c86f0305e31f36584c4dfe01f2f88cd
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898644"
---
# <a name="try-finally-statement"></a>`try-finally`-Anweisung

Die `try-finally` -Anweisung ist eine **Microsoft-spezifische** Erweiterung, die die strukturierte Ausnahmebehandlung in den Programmiersprachen C und C++ unterstützt.

## <a name="syntax"></a>Syntax

Die folgende Syntax beschreibt die- `try-finally` Anweisung:

```cpp
    // . . .
    __try {
        // guarded code
    }
    __finally {
        // termination code
    }
    // . . .
```

## <a name="grammar"></a>Grammatik

> *`try-finally-statement`*:\
> &emsp;**`__try`** *`compound-statement`* **`__finally`** *`compound-statement`*

Die `try-finally` -Anweisung ist eine Microsoft-Erweiterung der Programmiersprachen C und C++, mit denen Zielanwendungen die Ausführung von Bereinigungs Code gewährleisten können, wenn die Ausführung eines Code Blocks unterbrochen wird. Die Bereinigung besteht aus Aufgaben wie z. B. Neuzuweisung von Arbeitsspeicher, Schließen von Dateien und Freigeben von Dateihandles. Die `try-finally`-Anweisung ist besonders nützlich für Routinen, in denen an mehreren Stellen eine Fehlerüberprüfung durchgeführt wird, die eine vorzeitige Rückgabe von der Routine verursachen könnte.

Verwandte Informationen und ein Codebeispiel finden Sie unter- [ `try-except` Anweisung](../cpp/try-except-statement.md). Weitere Informationen über die strukturierte Ausnahmebehandlung im Allgemeinen finden Sie unter [strukturierte Ausnahmebehandlung](../cpp/structured-exception-handling-c-cpp.md). Weitere Informationen zur Behandlung von Ausnahmen in verwalteten Anwendungen mit C++/CLI finden Sie [unter Ausnahmebehandlung `/clr` unter ](../extensions/exception-handling-cpp-component-extensions.md).

> [!NOTE]
> Die strukturierte Ausnahmebehandlung arbeitet mit Win32 für C- und C++-Quelldateien. Sie ist jedoch nicht speziell für C++ entwickelt. Sie können sicherstellen, dass der Code portabler ist, indem Sie die C++-Ausnahmebehandlung verwenden. Die C++-Ausnahmebehandlung ist auch flexibler, da sie Ausnahmen eines beliebigen Typs behandeln kann. Für C++-Programme wird empfohlen, dass Sie den C++-Mechanismus zur Ausnahmebehandlung verwenden ([ `try` `catch` -, `throw` -und](../cpp/try-throw-and-catch-statements-cpp.md) -Anweisungen).

Die Verbund Anweisung nach der- **`__try`** Klausel ist der geschützte Abschnitt. Die Verbundanweisung nach der **`__finally`** -Klausel ist der Beendigungshandler. Der Handler gibt eine Reihe von Aktionen an, die ausgeführt werden, wenn der geschützte Abschnitt beendet wird, unabhängig davon, ob er den geschützten Abschnitt durch eine Ausnahme beendet (nicht ordnungsgemäße Beendigung) oder standardmäßig (normale Beendigung).

Die Steuerung erreicht eine- **`__try`** Anweisung durch einfache sequenzielle Ausführung (durchlaufen). Wenn das Steuerelement in den Eintritt **`__try`** , wird der zugehörige Handler aktiv. Wenn die Ablaufsteuerung das Ende des try-Blocks erreicht, wird die Ausführung wie folgt fortgesetzt:

1. Der Beendigungshandler wird aufgerufen.

1. Nach Abschluss des Beendigungshandlers wird die Ausführung nach der **`__finally`** -Anweisung fortgesetzt. Der geschützte Abschnitt wird jedoch beendet (z. b. über einen **`goto`** aus dem abgesicherten Text oder über eine- **`return`** Anweisung), der Beendigungs Handler wird ausgeführt, *bevor* die Ablauf Steuerung aus dem geschützten Abschnitt heraus bewegt wird.

   Eine- **`__finally`** Anweisung blockiert nicht das Suchen nach einem entsprechenden Ausnahmehandler.

Wenn eine Ausnahme im- **`__try`** Block auftritt, muss das Betriebssystem einen Handler für die Ausnahme finden, oder das Programm schlägt fehl. Wenn ein Handler gefunden wird, werden alle-und- **`__finally`** Blöcke ausgeführt, und die Ausführung wird im-Handler fortgesetzt.

Nehmen Sie z. B. an, eine Reihe von Funktionsaufrufen verbindet Funktion A mit Funktion D, wie in der folgenden Abbildung dargestellt. Jede Funktion verfügt über einen Beendigungshandler. Wenn eine Ausnahme in Funktion D ausgelöst und in A behandelt wird, werden die Beendigungshandler in folgender Reihenfolge aufgerufen, während das System den Stapel abwickelt: D, C, B.

![Reihenfolge der Beendigung&#45;handlerausführung](../cpp/media/vc38cx1.gif "Reihenfolge der Beendigung&#45;handlerausführung") <br/>
Reihenfolge für das Beenden bei Handlerausführung

> [!NOTE]
> Das Verhalten von try-endlich unterscheidet sich von einigen anderen Sprachen, die die Verwendung von unterstützen **`finally`** , wie z. b. c#.  Ein einzelner **`__try`** kann entweder, aber nicht beides von und enthalten **`__finally`** **`__except`** .  Wenn beide zusammen verwendet werden sollen, muss eine äußere try-except-Anweisung die innere try-finally-Anweisung einschließen.  Es gelten andere Regeln für die Angabe, wann ein einzelner Block ausgeführt wird.

Aus Kompatibilitätsgründen mit früheren **`_try`** Versionen **`_finally`** sind, und **`_leave`** Synonyme für **`__try`** , und, **`__finally`** **`__leave`** es sei denn, die Compileroption [ `/Za` (Spracherweiterungen deaktivieren)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

## <a name="the-__leave-keyword"></a>Das __leave-Schlüsselwort

Das **`__leave`** Schlüsselwort ist nur innerhalb des geschützten Abschnitts einer `try-finally` Anweisung gültig, und seine Auswirkung besteht darin, zum Ende des geschützten Abschnitts zu springen. Die Ausführung wird mit der ersten Anweisung im Beendigungshandler fortgesetzt.

Eine- **`goto`** Anweisung kann auch aus dem abgesicherten Abschnitt herausspringen, die Leistung wird jedoch beeinträchtigt, da die Stapel Auflösung aufgerufen wird. Die- **`__leave`** Anweisung ist effizienter, da Sie keine Stapel Auflösung verursacht.

## <a name="abnormal-termination"></a>Nicht ordnungsgemäße Beendigung

Das Beenden einer `try-finally` Anweisung mit der [longjmp](../c-runtime-library/reference/longjmp.md) -Lauf Zeitfunktion wird als nicht ordnungsgemäße Beendigung angesehen. Es ist nicht zulässig, in eine-Anweisung zu springen **`__try`** , aber es ist zulässig, von einem zu springen. Alle **`__finally`** -Anweisungen, die zwischen dem Punkt der Abfahrt (normale Beendigung des- **`__try`** Blocks) und dem Ziel (der- **`__except`** Block, der die Ausnahme behandelt) aktiv sind, müssen ausgeführt werden. Dies wird als *lokale*Entladung bezeichnet.

Wenn ein- **`__try`** Block aus irgendeinem Grund vorzeitig beendet wird, einschließlich eines Ausschnitts aus dem-Block, führt das System den zugeordneten- **`__finally`** Block als Teil des entsperrungs Vorgangs des Stapels aus. In solchen Fällen gibt die [`AbnormalTermination`](/windows/win32/Debug/abnormaltermination) Funktion zurück, **`true`** Wenn Sie von innerhalb des-Blocks aufgerufen wird **`__finally`** . andernfalls wird zurückgegeben **`false`** .

Der Beendigungs Handler wird nicht aufgerufen, wenn ein Prozess in der Mitte der Ausführung einer-Anweisung abgebrochen wird `try-finally` .

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Beendigungshandlers](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[Beendigungs HandlerSyntax](/windows/win32/Debug/termination-handler-syntax)

---
title: 'Zeitliche Steuerung der Ausnahmebehandlung: Zusammenfassung'
description: Der zeitlichen Ablauf und die Reihenfolge der Ausführung der Ausnahmebehandlung in Microsoft C++.
ms.date: 08/24/2020
helpviewer_keywords:
- sequence [C++]
- sequence, of handlers
- exception handling [C++], timing
- setjmpex.h
- termination handlers [C++], timing
- setjmp.h
- handlers [C++], order of exception
- structured exception handling [C++], timing
ms.assetid: 5d1da546-73fd-4673-aa1a-7ac0f776c420
ms.openlocfilehash: 2ce501d8d74b6f0f7ca92e193c39f8ce58a66053
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898361"
---
# <a name="timing-of-exception-handling-a-summary"></a>Zeitliche Steuerung der Ausnahmebehandlung: Zusammenfassung

Ein Beendigungs Handler wird ausgeführt, unabhängig davon, wie der **`__try`** Anweisungsblock beendet wird. Zu den Ursachen gehören das springen aus dem **`__try`** -Block, eine `longjmp` -Anweisung, die die Steuerung aus dem-Block überträgt, und das Entwickeln des Stapels aufgrund der Ausnahmebehandlung.

> [!NOTE]
> Der Microsoft C++-Compiler unterstützt zwei Formen der `setjmp` -Anweisung und der- `longjmp` Anweisung. Die schnelle Version umgeht die Abbruchbehandlung, ist jedoch effizienter. Um diese Version zu verwenden, schließen Sie die Datei ein \<setjmp.h> . Die andere Version unterstützt die Abbruchbehandlung, wie im vorherigen Abschnitt beschrieben. Um diese Version zu verwenden, schließen Sie die Datei ein \<setjmpex.h> . Die Leistungssteigerung der schnellen Version hängt von der Hardwarekonfiguration ab.

Das Betriebssystem führt alle Abbruchbehandlungen in der richtigen Reihenfolge aus, bevor ein anderer Code ausgeführt werden kann, einschließlich des Texts eines Ausnahmehandlers.

Wenn die Ursache für die Unterbrechung eine Ausnahme ist, muss das System erst den Filterteil einer oder mehrerer Ausnahmehandler ausführen, bevor entschieden wird, was beendet werden soll. Die Reihenfolge der Ereignisse lautet:

1. Eine Ausnahme wird ausgelöst.

1. Das System untersucht die Hierarchie der aktiven Ausnahmehandler und führt den Filter des Handler mit der höchsten Rangfolge aus. Dabei handelt es sich um den Ausnahmehandler, der zuletzt installiert und am tiefsten geschachtelt wurde, wobei Blöcke und Funktionsaufrufe ausgeführt werden.

1. Wenn dieser Filter die Steuerung übergibt (gibt 0 zurück), wird der Prozess fortgesetzt, bis ein Filter gefunden wird, der die Steuerung nicht übergibt.

1. Wenn dieser Filter "-1" zurückgibt, wird die Ausführung fortgesetzt, wo die Ausnahme ausgelöst wurde, und es findet keine Beendigung statt.

1. Wenn der Filter 1 zurückgibt, werden folgende Ereignisse ausgelöst:

   - Das System entlädt den Stapel: er löscht alle Stapel Rahmen, zwischen denen die Ausnahme ausgelöst wurde, und den Stapel Rahmen, der den Ausnahmehandler enthält.

   - Beim Entladen des Stapels wird jeder Beendigungshandler im Stapel ausgeführt.

   - Der Ausnahmehandler selbst wird ausgeführt.

   - Die Steuerung wird nach dem Ende des Ausnahmehandlers an die Codezeile übergeben.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Beendigungshandlers](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)

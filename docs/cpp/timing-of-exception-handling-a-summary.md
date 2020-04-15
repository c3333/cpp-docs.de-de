---
title: 'Zeitpunkt der Ausnahmebehandlung: Eine Zusammenfassung'
ms.date: 05/07/2019
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
ms.openlocfilehash: 17d1c250a98afc2b86c198735602df7d80118bd4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81316596"
---
# <a name="timing-of-exception-handling-a-summary"></a>Zeitpunkt der Ausnahmebehandlung: Eine Zusammenfassung

Ein Beendigungshandler wird ausgeführt, unabhängig davon, wie der **__try** Anweisungsblock beendet wird. Zu den Ursachen gehören das `longjmp` Springen aus dem **__try-Block,** eine Anweisung, die das Steuerelement aus dem Block überträgt, und das Entladen des Stapels aufgrund der Ausnahmebehandlung.

> [!NOTE]
> Der Microsoft C++-Compiler unterstützt `setjmp` `longjmp` zwei Formen der und-Anweisungen. Die schnelle Version umgeht die Abbruchbehandlung, ist jedoch effizienter. Um diese Version zu \<verwenden, fügen Sie die Datei setjmp.h> ein. Die andere Version unterstützt die Abbruchbehandlung, wie im vorherigen Abschnitt beschrieben. Um diese Version zu \<verwenden, schließen Sie die Datei setjmpex.h> ein. Die Leistungssteigerung der schnellen Version hängt von der Hardwarekonfiguration ab.

Das Betriebssystem führt alle Abbruchbehandlungen in der richtigen Reihenfolge aus, bevor ein anderer Code ausgeführt werden kann, einschließlich des Texts eines Ausnahmehandlers.

Wenn die Ursache für die Unterbrechung eine Ausnahme ist, muss das System erst den Filterteil einer oder mehrerer Ausnahmehandler ausführen, bevor entschieden wird, was beendet werden soll. Die Reihenfolge der Ereignisse lautet:

1. Eine Ausnahme wird ausgelöst.

1. Das System untersucht die Hierarchie der aktiven Ereignishandler und führt den Filter des Handlers mit der höchsten Rangstufe aus. Hierbei handelt es sich um den Ausnahmehandler, der im Hinblick auf Blöcke und Funktionsaufrufe zuletzt installiert wurde und am tiefsten geschachtelt ist.

1. Wenn dieser Filter die Steuerung übergibt (0 zurückgibt), wird der Prozess fortgesetzt, bis ein Filter gefunden wird, der die Steuerung nicht übergibt.

1. Wenn dieser Filter -1 zurückgibt, wird die Ausführung dort fortgesetzt, wo die Ausnahme ausgelöst wurde, und es findet keine Beendigung statt.

1. Wenn der Filter 1 zurückgibt, werden folgende Ereignisse ausgelöst:

   - Das System entlädt den Stapel und löscht alle Stapelrahmen zwischen dem gerade ausgeführten Code (bei dem die Ausnahme ausgelöst wurde) und dem Stapelrahmen, der den Ausnahmehandler enthält, der nun die Steuerung übernimmt.

   - Beim Entladen des Stapels wird jeder Beendigungshandler im Stapel ausgeführt.

   - Der Ausnahmehandler selbst wird ausgeführt.

   - Die Steuerung wird nach dem Ende des Ausnahmehandlers an die Codezeile übergeben.

## <a name="see-also"></a>Siehe auch

[Schreiben eines Beendigungshandlers](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)

---
title: C-Laufzeitfehler R6016
ms.date: 11/04/2016
f1_keywords:
- R6016
helpviewer_keywords:
- R6016
ms.assetid: 7bd3f274-d9c4-4bc4-8252-80bf168c4c3a
ms.openlocfilehash: 22bf4b7e8951215d1a013edb29af1ebff7517ffc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197339"
---
# <a name="c-runtime-error-r6016"></a>C-Laufzeitfehler R6016

Nicht genügend Speicher für Threaddaten

> [!NOTE]
> Wenn diese Fehlermeldung beim Ausführen einer App angezeigt wird, wurde die APP heruntergefahren, weil Sie über ein internes Speicherproblem verfügt. Es gibt viele mögliche Ursachen für diesen Fehler, aber häufig wird er durch einen extrem wenig Arbeitsspeicher, einen Fehler in der APP oder durch einen Fehler in einem Add-in oder einer Erweiterung verursacht, die von der APP verwendet wird.
>
> Sie können versuchen, diesen Fehler zu beheben, indem Sie folgende Schritte ausführen:
>
> - Schließen Sie andere laufende Anwendungen, oder starten Sie den Computer neu, um Arbeitsspeicher freizugeben.
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um die APP zu reparieren oder neu zu installieren.
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um Add-Ins oder Erweiterungen zu entfernen, zu reparieren oder neu zu installieren, die von der APP verwendet werden.
> - Überprüfen Sie **Windows Update** in der **Systemsteuerung** auf Software Updates.
> - Überprüfen Sie, ob eine aktualisierte Version der App angezeigt wird. Wenn das Problem weiterhin besteht, wenden Sie sich an den Anbieter der APP

**Informationen für Programmierer**

Dieser Fehler tritt auf, weil das Programm nicht genügend Arbeitsspeicher vom Betriebssystem empfangen hat, um einen [_beginthread](../../c-runtime-library/reference/beginthread-beginthreadex.md) oder einen `_beginthreadex`-Aufrufvorgang abzuschließen, oder wenn der Thread lokale Speicher nicht durch `_beginthread` oder `_beginthreadex`initialisiert wurde.

Beim Start eines neuen Threads muss die Bibliothek für diesen eine interne Datenbank anlegen. Wenn der vom Betriebssystem bereitgestellte Speicher nicht zum Erweitern dieser Datenbank ausreicht, wird der Thread nicht gestartet, und der Aufrufprozess wird angehalten. Das kann vorkommen, wenn durch den Prozess zu viele Threads erstellt wurden oder der threadlokale Speicher ausgeschöpft ist.

Es wird empfohlen, dass eine ausführbare Datei, die die C-Lauf Zeit Bibliothek (CRT) aufruft, `_beginthreadex` für die Thread Erstellung anstelle der Windows-API-`CreateThread`verwendet. `_beginthreadex` initialisiert den internen statischen Speicher, der von vielen CRT-Funktionen im lokalen Threadspeicher verwendet wird. Wenn Sie zur Erstellung eines Threads die `CreateThread`-Funktion verwenden, beendet das CRT den Prozess beim Aufruf einer CRT-Funktion, die initialisierten internen statischen Speicher benötigt, möglicherweise mit R6016.

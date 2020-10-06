---
title: Parameterüberprüfung
description: Eine Beschreibung der Parameter Validierung in der Microsoft C-Lauf Zeit Bibliothek.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parameters, validation
ms.assetid: 019dd5f0-dc61-4d2e-b4e9-b66409ddf1f2
ms.openlocfilehash: 8378e4bf9bdfc950002c3ed8c3ef50c27a3c162d
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765259"
---
# <a name="parameter-validation"></a>Parameterüberprüfung

Die meisten der von der Sicherheit verbesserten CRT-Funktionen, und viele nicht, überprüfen Ihre Parameter, wie z. b. das Überprüfen von Zeigern auf **null**, ob ganze Zahlen in einen gültigen Bereich fallen oder ob Enumerationswerte gültig sind. Wenn ein ungültiger Parameter gefunden wird, wird der Handler für ungültige Parameter aufgerufen.

## <a name="invalid-parameter-handler-routine"></a>Routine für ungültige Parameterhandler

Wenn eine C-Lauf Zeit Bibliotheksfunktion einen ungültigen Parameter erkennt, werden einige Informationen über den Fehler erfasst, und anschließend wird ein Makro aufgerufen, das eine ungültige dispatchhandlerfunktion umschließt. Dabei handelt es sich um einen [_invalid_parameter](../c-runtime-library/reference/invalid-parameter-functions.md), [_invalid_parameter_noinfo](../c-runtime-library/reference/invalid-parameter-functions.md)oder [_invalid_parameter_noinfo_noreturn](../c-runtime-library/reference/invalid-parameter-functions.md). Welche dispatchfunktion aufgerufen wird, hängt davon ab, ob Ihr Code bzw. ein Debugbuild, ein Einzelhandels Build oder der Fehler nicht als wiederherstellbar eingestuft wird.

In Debugbuilds löst das ungültige Parameter Makro in der Regel eine fehlgeschlagene und einen Debugger-Haltepunkt aus, bevor die Dispatch-Funktion aufgerufen wird. Wenn der Code ausgeführt wird, kann der Benutzer in einem Dialogfeld, das "Abbruch", "Wiederholen" und "Continue" enthält, oder ähnliche Optionen in Abhängigkeit von der Version des Betriebssystems und der Lauf Zeit Bibliothek angezeigt werden. Mit diesen Optionen kann der Benutzer das Programm sofort beenden, einen Debugger anfügen oder den vorhandenen Code weiter ausführen lassen, wodurch die Dispatch-Funktion aufgerufen wird.

Die Sende Funktion für ungültige Parameter Handler Ruft den derzeit zugewiesenen Handler für ungültige Parameter auf. Standardmäßig ruft der ungültige Parameter `_invoke_watson` auf, wodurch die Anwendung geschlossen und ein Mini Abbild generiert wird. Wenn das Betriebssystem aktiviert ist, wird der Benutzer in einem Dialogfeld aufgefordert, das Absturz Abbild zur Analyse an Microsoft zu senden.

Sie können dieses Verhalten ändern, indem Sie die Funktionen [_set_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) oder [_set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) verwenden, um den Handler für ungültige Parameter auf Ihre eigene Funktion festzulegen. Wenn die Funktion, die Sie angeben, die Anwendung nicht beendet, wird die Steuerung an die Funktion zurückgegeben, die ungültige Parameter empfangen hat. In der CRT beenden diese Funktionen normalerweise die Funktions Ausführung, legen `errno` auf einen Fehlercode fest und geben einen Fehlercode zurück. In vielen Fällen sind der `errno` Wert und der Rückgabewert beide `EINVAL` , um einen ungültigen Parameter anzugeben. In einigen Fällen wird ein spezifischerer Fehlercode zurückgegeben, wie z.B. `EBADF` für einen ungültigen Dateizeiger, der als Parameter übergeben wird.

Weitere Informationen zu `errno` finden Sie unter [errno, _doserrno, _sys_errlist und _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="see-also"></a>Siehe auch

[Sicherheitsfunktionen in der CRT](../c-runtime-library/security-features-in-the-crt.md)\
[Funktionen der CRT-Bibliothek](../c-runtime-library/crt-library-features.md)

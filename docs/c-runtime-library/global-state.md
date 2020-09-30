---
title: Globaler Status in der CRT
description: Beschreibt, wie der gemeinsame globale Zustand in der Microsoft Universal C-Laufzeit behandelt wird.
ms.topic: conceptual
ms.date: 04/02/2020
helpviewer_keywords:
- CRT global state
ms.openlocfilehash: 60532fbdb905bd8ea78b4ce705ec8ecc3e374d9d
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589730"
---
# <a name="global-state-in-the-crt"></a>Globaler Status in der CRT

Einige Funktionen in der universellen C-Laufzeit (ucrt) verwenden den globalen Zustand. Beispielsweise `setlocale()` legt das Gebiets Schema für das gesamte Programm fest, das die Ziffern Trennzeichen, die Text Codepage usw. beeinflusst.

Der globale Status der ucrt wird nicht für Anwendungen und das Betriebssystem freigegeben. Wenn die Anwendung beispielsweise aufruft `setlocale()` , wirkt sie sich nicht auf das Gebiets Schema für Betriebssystemkomponenten aus, die die C-Laufzeit verwenden, oder umgekehrt.

## <a name="os-specific-versions-of-crt-functions"></a>Betriebssystemspezifische Versionen von CRT-Funktionen

In der ucrt verfügen Funktionen, die mit dem globalen Zustand interagieren, über eine "Zwillings Funktion" mit dem Präfix `_o_` . Beispiel:

- `setlocale()` wirkt sich auf den globalen Zustand der APP aus.
- `_o_setlocale()` wirkt sich auf den globalen Status aus, der von allen Betriebssystemkomponenten gemeinsam genutzt wird

Der einzige Unterschied zwischen diesen "Zwillings Funktionen" besteht darin, dass die betriebssystemspezifischen Versionen (d. h. die Versionen, die mit beginnen `_o_` ) die Betriebssystem Kopie des globalen Zustands anstelle der APP-Kopie des globalen Zustands verwenden, wenn Sie den globalen CRT-Zustand lesen/schreiben.

Die betriebssystemspezifischen Versionen dieser Funktionen sind in `ucrt.osmode.lib` . Die betriebssystemspezifische Version von lautet z. b. `setlocale()``_o_setlocale()`

Es gibt zwei Möglichkeiten, den CRT-Zustand Ihrer Komponente vom CRT-Zustand einer APP zu isolieren:

- Verknüpfen Sie die Komponente statisch mithilfe der Compileroptionen/MT (Release) oder mtd (Debug). Weitere Informationen finden Sie unter [/MD,/MT,/LD](../build/reference/md-mt-ld-use-run-time-library.md). Beachten Sie, dass das statische verknüpfen die binäre Größe erheblich erhöhen kann.
- Ab Windows 10 20h2 können Sie die CRT-Zustands Isolation durch dynamisches Verknüpfen mit der CRT abrufen, aber Sie müssen die Exporte im Betriebssystem Modus (die Funktionen, die mit _o_beginnen) abrufen. Um die Betriebssystem-Modus-Exporte aufzurufen, wird statisch wie zuvor verknüpft, aber die statische ucrt wird mithilfe der Linkeroption `/NODEFAULTLIB:libucrt.lib` (Release) oder `/NODEFAULTLIB:libucrtd.lib` (Debuggen) ignoriert. Weitere Informationen finden Sie unter [/NODEFAULTLIB (Bibliotheken ignorieren)](../build/reference/nodefaultlib-ignore-libraries.md) . Und `ucrt.osmode.lib` der Linker-Eingabe hinzufügen.

> [!Note]
> Schreiben Sie im Quellcode, `setlocale()` nicht `_o_setlocale()` . Wenn Sie einen Link `ucrt.osmode.lib` zu durchführt, ersetzt der Linker automatisch die betriebssystemspezifische Version der Funktion. Das heißt, `setlocale()` wird durch ersetzt `_o_setlocale()` .

Durch das Verknüpfen `ucrt.osmode.lib` mit werden einige ucrt-Aufrufe deaktiviert, die nur im APP-Modus verfügbar sind. Der Versuch, diese aufzurufen, führt zu einem Link Fehler.

## <a name="global-state-affected-by-appos-separation"></a>Globaler Zustand, der von der APP/Betriebssystem Trennung betroffen

Der globale Status, der durch die Trennung von App-und Betriebssystem Status beeinträchtigt wird, umfasst

- [Gebiets Schema Daten](locale.md)
- Signalhandler festgelegt durch [Signal](reference/signal.md)
- Durch [Beenden](reference/set-terminate-crt.md) festgelegte Beendigungs Routinen
- [errno und _doserrno](errno-doserrno-sys-errlist-and-sys-nerr.md)
- Von [Rand](reference/rand.md) und [srand](reference/srand.md) verwendeter Zufallszahlen Generierungs Status
- Funktionen, die einen Puffer zurückgeben, den der Benutzer nicht freigeben muss: " [Strauch", "wcstok", "_mbstok](reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) [tmpnam", "_wtmpnam](reference/tempnam-wtempnam-tmpnam-wtmpnam.md) [Asctime", "_wasctime](reference/asctime-wasctime.md) [gmtime](reference/gmtime-gmtime32-gmtime64.md) ", "_gmtime32" _gmtime64 [_fcvt](reference/fcvt.md) [_ecvt "](reference/ecvt.md) _strerror" [,](reference/strerror-strerror-wcserror-wcserror.md) "_wcserror", __wcserror
- Der von _putch verwendete Puffer [_putwch](reference/putch-putwch.md)
- [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)
- [_set_new_handler](reference/set-new-handler.md) und [_set_new_mode](reference/set-new-mode.md)
- [f-Modus] (Text-and-Binary-Mode-File-i-o.MD)
- [Zeitzoneninformationen](time-management.md)

## <a name="see-also"></a>Weitere Informationen

[C-Lauf Zeit Bibliotheks Referenz](c-run-time-library-reference.md)

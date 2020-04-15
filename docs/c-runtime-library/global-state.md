---
title: Globaler Zustand in der CRT
ms.date: 04/02/2020
helpviewer_keywords:
- CRT global state
ms.openlocfilehash: 487418da104b2edbc45b5d3a664e4385394ada31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377599"
---
# <a name="global-state-in-the-crt"></a>Globaler Zustand in der CRT

Einige Funktionen in der Universellen C-Laufzeit (UNIVERSAL C Runtime, UCRT) verwenden den globalen Status. `setlocale()` Legt beispielsweise das Gebietsschema für das gesamte Programm fest, das sich auf die Zifferntrennzeichen, die Textcodepage usw. auswirkt.

Der globale Status der UCRT wird nicht zwischen Anwendungen und dem Betriebssystem gemeinsam genutzt. Wenn Ihre Anwendung beispielsweise `setlocale()`aufruft, wirkt sich dies nicht auf das Gebietsschema für Betriebssystemkomponenten aus, die die C-Laufzeit verwenden, oder umgekehrt.

## <a name="os-specific-versions-of-crt-functions"></a>OS-spezifische Versionen von CRT-Funktionen

In der UCRT haben Funktionen, die mit dem globalen Zustand `_o_`interagieren, eine "Zwillingsfunktion" mit dem Präfix . Beispiel:

    `setlocale()` affects global state specific to the app.
    `_o_setlocale()` affects global state shared by all OS components, but not apps.

Der einzige Unterschied zwischen diesen "Zwillings"-Funktionen besteht darin, dass beim Lesen/Schreiben des globalen CRT-Status die OS-spezifischen Versionen (d. h. die Versionen, die mit `_o_`beginnen) die Betriebssystemkopie des globalen Status anstelle der Kopie des globalen Status der App verwenden.

Die OS-spezifischen Versionen dieser `ucrt.osmode.lib`Funktionen sind in . Beispielsweise ist die OS-spezifische `setlocale()` Version von`_o_setlocale()`

Es gibt zwei Möglichkeiten, den CRT-Status Ihrer Komponente vom CRT-Status einer App zu isolieren:

- Verknüpfen Sie Ihre Komponente statisch mithilfe der Compileroptionen /MT (Release) oder MTd (Debug). Weitere Informationen finden Sie unter [/MD, /MT, /LD](https://docs.microsoft.com/cpp/build/reference/md-mt-ld-use-run-time-library?view=vs-2019). Beachten Sie, dass die statische Verknüpfung die binäre Größe erheblich erhöhen kann.
- Ab Windows 10 20H2 erhalten Sie crT-Statusisolation durch dynamische Verknüpfung mit der CRT, rufen jedoch die OS-Modus-Exporte auf (die Funktionen, die mit _o_beginnen). Um die OS-Modus-Exporte aufzurufen, verknüpfen Sie statisch wie zuvor, `/NODEFAULTLIB:libucrt.lib` ignorieren Sie `/NODEFAULTLIB:libucrtd.lib` jedoch die statische UCRT, indem Sie die Linker-Option (Release) oder (Debug) siehe [/NODEFAULTLIB (Bibliotheken ignorieren)](https://docs.microsoft.com/cpp/build/reference/nodefaultlib-ignore-libraries?view=vs-2019) für Details verwenden. Und `ucrt.osmode.lib` fügen Sie der Linker-Eingabe hinzu.

> [!Note]
> Schreiben Sie im `setlocale()`Quellcode `_o_setlocale()`, nicht . Wenn Sie `ucrt.osmode.lib`eine Verknüpfung mit verknüpfen, ersetzt der Linker automatisch die BETRIEBSSYSTEMspezifische Version der Funktion. Das heißt, `setlocale()` wird durch `_o_setlocale()`ersetzt werden.

Durch `ucrt.osmode.lib` Das Verknüpfen mit deaktiviert einige UCRT-Aufrufe, die nur im App-Modus verfügbar sind. Der Versuch, diese aufzurufen, führt zu einem Linkfehler.

## <a name="global-state-affected-by-appos-separation"></a>Globaler Zustand, der von der App/OS-Trennung betroffen ist

Der globale Status, der von der Trennung von App und Betriebssystemstatus betroffen ist, umfasst:

- [Gebietsschemadaten](locale.md)
- Signalhandler, die durch [Signal](reference/signal.md) eingestellt werden
- Kündigungsroutinen, die durch [Beenden](reference/set-terminate-crt.md) festgelegt werden
- [errno und _doserrno](errno-doserrno-sys-errlist-and-sys-nerr.md)
- Zufallszahlengenerierungszustand, der von [Rand](reference/rand.md) und [Srand](reference/srand.md) verwendet wird
- Funktionen, die einen Puffer zurückgeben, den der Benutzer nicht freigeben muss: [strtok, wcstok, _mbstok](reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) [Tmpnam, _wtmpnam](reference/tempnam-wtempnam-tmpnam-wtmpnam.md) [asctime, _wasctime](reference/asctime-wasctime.md) [gmtime, _gmtime32, _gmtime64](reference/gmtime-gmtime32-gmtime64.md) _fcvt [_ecvt](reference/fcvt.md) [_ecvt](reference/ecvt.md) [strerror, _strerror, _wcserror, __wcserror](reference/strerror-strerror-wcserror-wcserror.md)
- Der von [_putch, _putwch](reference/putch-putwch.md)
- [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)
- [_set_new_handler](reference/set-new-handler.md) und [_set_new_mode](reference/set-new-mode.md)
- [fmode] (text-and-binary-mode-file-i-o.md)
- [Zeitzoneninformationen](time-management.md)

## <a name="see-also"></a>Siehe auch

[C Laufzeitbibliotheksreferenz](c-run-time-library-reference.md)
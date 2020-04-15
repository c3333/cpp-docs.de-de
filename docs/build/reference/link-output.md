---
title: LINK-Ausgabe
ms.date: 11/04/2016
helpviewer_keywords:
- mapfiles [C++]
- ILK files
- output files [C++], linker
- files [C++], LINK
- .ilk files
- LINK tool [C++], output
- import libraries [C++], creating
- executable files [C++], as linker output
- mapfiles [C++], LINK output
- linker [C++], output files
- DLLs [C++], as linker output
- LINK tool [C++], mapfile
ms.assetid: a98b557c-1947-447a-be1f-616fb45a9580
ms.openlocfilehash: 253f88ed50b9f064edf976277a4618e4f101ec7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331795"
---
# <a name="link-output"></a>LINK-Ausgabe

Die Linkausgabe umfasst EXE-Dateien, DLLs, Mapfiles und Nachrichten.

## <a name="output-files"></a><a name="_core_output_files"></a>Ausgabedateien

Die Standardausgabedatei von LINK ist eine EXE-Datei. Wenn die Option [/DLL](dll-build-a-dll.md) angegeben ist, erstellt LINK eine DLL-Datei. Sie können den Namen der Ausgabedatei mit der Option [Ausgabedateiname (/OUT)](out-output-file-name.md) steuern.

Im inkrementellen Modus erstellt LINK eine .ilk-Datei, die Statusinformationen für spätere inkrementelle Builds des Programms enthält. Weitere Informationen zu .ilk-Dateien finden Sie unter [.ilk Files](dot-ilk-files-as-linker-input.md). Weitere Informationen zur inkrementellen Verknüpfung finden Sie unter die Option [Inkrementell verknüpfen (/INCREMENTAL).](incremental-link-incrementally.md)

Wenn LINK ein Programm erstellt, das Exporte enthält (in der Regel eine DLL), erstellt es auch eine .lib-Datei, es sei denn, eine .exp-Datei wurde im Build verwendet. Sie können den Dateinamen der Importbibliothek mit der Option [/IMPLIB](implib-name-import-library.md) steuern.

Wenn die Option [Mapfile (/MAP generieren)](map-generate-mapfile.md) angegeben ist, erstellt LINK eine Mapfile.

Wenn die Option [Debug-Info generieren (/DEBUG)](debug-generate-debug-info.md) angegeben ist, erstellt LINK eine PDB, die Debuginformationen für das Programm enthält.

## <a name="other-output"></a><a name="_core_other_output"></a>Sonstige Ausgabe

Wenn Sie `link` ohne andere Befehlszeileneingabe eingeben, zeigt LINK eine Verwendungsanweisung an, die ihre Optionen zusammenfasst.

LINK zeigt eine Copyright- und Versionsmeldung an und gibt die Eingabe von Befehlsdateien wieder, es sei denn, die Option [Startbanner (/NOLOGO unterdrücken)](nologo-suppress-startup-banner-linker.md) wird verwendet.

Sie können die Option [Fortschrittsnachrichten (/VERBOSE)](verbose-print-progress-messages.md) drucken verwenden, um zusätzliche Details zum Build anzuzeigen.

LINK gibt Fehler- und Warnmeldungen in der Form LNK*nnnn*aus. Dieses Fehlerpräfix und der Zahlenbereich werden auch von LIB, DUMPBIN und EDITBIN verwendet.

## <a name="see-also"></a>Siehe auch

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)

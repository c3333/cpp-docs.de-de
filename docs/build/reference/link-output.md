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
ms.openlocfilehash: 8323723f2049d3db469e874c91b99f4cfb561c72
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439314"
---
# <a name="link-output"></a>LINK-Ausgabe

Die Link Ausgabe enthält exe-Dateien, DLLs, Mapfiles und Nachrichten.

##  <a name="_core_output_files"></a>Ausgabedateien

Die Standardausgabe Datei von Link ist eine exe-Datei. Wenn die [/dll](dll-build-a-dll.md) -Option angegeben ist, erstellt Link eine DLL-Datei. Sie können den Namen der Ausgabedatei mit der Option [Name der Ausgabedatei (/Out)](out-output-file-name.md) steuern.

Im inkrementellen Modus erstellt Link eine ILK-Datei, die Statusinformationen für spätere inkrementelle Builds des Programms enthält. Weitere Informationen zu. ILK-Dateien finden Sie unter [. ILK-Dateien](dot-ilk-files-as-linker-input.md). Weitere Informationen zum inkrementellen Verknüpfen finden Sie unter der [Link inkrementelle Option (/incremental)](incremental-link-incrementally.md) .

Wenn Link ein Programm erstellt, das Exporte (in der Regel eine DLL) enthält, wird auch eine LIB-Datei erstellt, es sei denn, eine EXP-Datei wurde im Build verwendet. Sie können den Dateinamen der Import Bibliothek mit der [/IMPLIB](implib-name-import-library.md) -Option steuern.

Wenn die Option [Mapfile generieren (/Map)](map-generate-mapfile.md) angegeben ist, erstellt Link eine Mapfile.

Wenn die Option zum [Generieren von Debuginformationen (/Debug)](debug-generate-debug-info.md) angegeben ist, erstellt Link eine PDB, die Debuginformationen für das Programm enthält.

##  <a name="_core_other_output"></a>Andere Ausgabe

Wenn Sie `link` ohne eine andere Befehlszeilen Eingabe eingeben, zeigt Link eine Verwendungs Anweisung an, die die zugehörigen Optionen zusammenfasst.

Link zeigt eine Copyright-und Versions Meldung an und gibt Befehlszeilen Eingaben aus, es sei denn, die Option [Start Banner unterdrücken (/nologo)](nologo-suppress-startup-banner-linker.md) wird verwendet.

Sie können die Option Status [Meldungen drucken (/verbose)](verbose-print-progress-messages.md) verwenden, um weitere Details zum Build anzuzeigen.

Link gibt Fehler-und Warnmeldungen im Format lnk*nnnn*aus. Dieses Fehler Präfix und der Bereich von Zahlen werden auch von lib, DUMPBIN und EDITBIN verwendet.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)

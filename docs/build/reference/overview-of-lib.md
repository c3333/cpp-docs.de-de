---
title: Übersicht über LIB
description: Übersicht über die Verwendung und die Optionen des Bibliotheks Tools "lib. exe".
ms.date: 02/09/2020
helpviewer_keywords:
- LIB [C++], modes
ms.assetid: e997d423-f574-434f-8b56-25585d137ee0
ms.openlocfilehash: 4ed725f383d956adf7abcf1c68002dee51703013
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439000"
---
# <a name="overview-of-lib"></a>Übersicht über LIB

Lib (lib. exe) erstellt Standardbibliotheken, importiert Bibliotheken und exportiert Dateien, die Sie mit [Link](linker-options.md) verwenden können, wenn Sie ein Programm erstellen. LIB wird über eine Eingabeaufforderung ausgeführt.

Sie können lib in den folgenden Modi verwenden:

- [Aufbauen oder Ändern einer COFF-Bibliothek](managing-a-library.md)

- [Extrahieren eines Member-Objekts in eine Datei](extracting-a-library-member.md)

- [Erstellen einer Exportdatei und einer Import Bibliothek](working-with-import-libraries-and-export-files.md)

Diese Modi schließen sich gegenseitig aus. Sie können lib jeweils nur in einem Modus verwenden.

## <a name="lib-options"></a>LIB-Optionen

In der folgenden Tabelle sind die Optionen für "lib. exe" mit einem Link zu weiteren Informationen aufgeführt.

|Option|BESCHREIBUNG|
|-|-|
|**/DEF**|Erstellen Sie eine Import Bibliothek und eine Exportdatei.<br/><br/>Weitere Informationen finden Sie unter [aufbauen einer Import Bibliothek und einer Export Datei](building-an-import-library-and-export-file.md).|
|**/ERRORREPORT**| Veraltet. Weitere Informationen finden Sie unter [Ausführen von LIB](running-lib.md).|
|**/EXPORT**|   Exportiert eine Funktion aus dem Programm.<br/><br/>Weitere Informationen finden Sie unter [aufbauen einer Import Bibliothek und einer Export Datei](building-an-import-library-and-export-file.md).|
|**/Extract**|   Erstellen Sie eine Objektdatei (. obj), die eine Kopie eines Members einer vorhandenen Bibliothek enthält.<br/><br/>Weitere Informationen finden Sie unter [Extrahieren eines Bibliotheks](extracting-a-library-member.md)Members.|
|**/INCLUDE**|   Fügt der Symboltabelle ein Symbol hinzu.<br/><br/>Weitere Informationen finden Sie unter [aufbauen einer Import Bibliothek und einer Export Datei](building-an-import-library-and-export-file.md).|
|**/LIBPATH**|   Überschreibt den Bibliothekspfad der Umgebung.<br/><br/>Weitere Informationen finden Sie unter [Verwalten einer Bibliothek](managing-a-library.md).|
|**/LINKREPRO**|   Erstellt Artefakte, die zum reproduzieren eines lib. exe-Absturzes oder eines internen Fehlers benötigt werden.<br/><br/>Weitere Informationen finden Sie unter [Ausführen von LIB](running-lib.md).|
|**/LINKREPROTARGET**|   Generiert nur die **/LINKREPRO** -Artefakte, wenn lib. exe mit einer angegebenen Datei verwendet wird.<br/><br/>Weitere Informationen finden Sie unter [Ausführen von LIB](running-lib.md).|
|**/List**|   Zeigt Informationen zur Ausgabe Bibliothek in der Standardausgabe an.<br/><br/>Weitere Informationen finden Sie unter [Verwalten einer Bibliothek](managing-a-library.md).|
|**/LTCG**|   Bewirkt, dass die Bibliothek mithilfe der Link-Zeit Codegenerierung erstellt wird.<br/><br/>Weitere Informationen finden Sie unter [Ausführen von LIB](running-lib.md).|
|**/MACHINE**|   Gibt die Zielplattform für das Programm an.<br/><br/>Weitere Informationen finden Sie unter [Ausführen von LIB](running-lib.md).|
|**/Name**|   Gibt beim Erstellen einer Import Bibliothek den Namen der dll an, für die die Import Bibliothek erstellt wird.<br/><br/>Weitere Informationen finden Sie unter [Verwalten einer Bibliothek](managing-a-library.md).|
|**/NODEFAULTLIB**|   Entfernt mindestens eine Standardbibliothek aus der Liste der Bibliotheken, die beim Auflösen externer Verweise durchsucht werden.<br/><br/>Weitere Informationen finden Sie unter [Verwalten einer Bibliothek](managing-a-library.md).|
|**/NOLOGO**|   Unterdrückt die Anzeige der lib-Copyright Meldung und der Versionsnummer und verhindert das Wiederholen von Befehls Dateien.<br/><br/>Weitere Informationen finden Sie unter [Ausführen von LIB](running-lib.md).|
|**/OUT**|   Überschreibt den Standardausgabe Dateinamen.<br/><br/>Weitere Informationen finden Sie unter [Verwalten einer Bibliothek](managing-a-library.md).|
|**/Remove**|   Lässt ein Objekt aus der Ausgabe Bibliothek aus.<br/><br/>Weitere Informationen finden Sie unter [Verwalten einer Bibliothek](managing-a-library.md).|
|**/SUBSYSTEM**|   Teilt dem Betriebssystem mit, wie ein Programm ausgeführt werden soll, das durch das Verknüpfen mit der Ausgabe Bibliothek erstellt wurde.<br/><br/>Weitere Informationen finden Sie unter [Verwalten einer Bibliothek](managing-a-library.md).|
|**/VERBOSE**|   Zeigt Details zum Fortschritt der Sitzung an, einschließlich der Namen der OBJ-Dateien, die hinzugefügt werden.<br/><br/>Weitere Informationen finden Sie unter [Ausführen von LIB](running-lib.md).|
|**/WX**|   Behandeln Sie Warnungen als Fehler.<br/><br/>Weitere Informationen finden Sie unter [Ausführen von LIB](running-lib.md).|

## <a name="see-also"></a>Weitere Informationen

[LIB-Referenz](lib-reference.md)\
[Lib-Eingabedateien](lib-input-files.md)\
[Lib-Ausgabedateien](lib-output-files.md)\
[Andere lib-Ausgabe](other-lib-output.md)\
[Struktur einer Bibliothek](structure-of-a-library.md)

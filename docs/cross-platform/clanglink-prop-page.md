---
title: Clang-Linkereigenschaften (Android C++)
ms.date: 10/23/2017
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
f1_keywords:
- VC.Project.VCLinkerTool.Clang.OutputFile
- VC.Project.VCLinkerTool.Clang.Soname
- VC.Project.VCLinkerTool.Clang.ShowProgress
- VC.Project.VCLinkerTool.Clang.Version
- VC.Project.VCLinkerTool.Clang.VerboseOutput
- VC.Project.VCLinkerTool.Clang.IncrementalLink
- VC.Project.VCLinkerTool.Clang.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.Clang.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.Clang.UnresolvedReferences
- VC.Project.VCLinkerTool.Clang.OptimizeForMemory
- VC.Project.VCLinkerTool.Clang.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.Clang.ForceSymbolReferences
- VC.Project.VCLinkerTool.Clang.ForceFileOutput
- VC.Project.VCLinkerTool.Clang.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.Clang.GenerateMapFile
- VC.Project.VCLinkerTool.Clang.Relocation
- VC.Project.VCLinkerTool.Clang.FunctionBinding
- VC.Project.VCLinkerTool.Clang.NoExecStackRequired
- VC.Project.VCLinkerTool.Clang.WholeArchive
- VC.Project.VCLinkerTool.Clang.AdditionalOptionsPage
- VC.Project.VCLinkerTool.Clang.AdditionalDependencies
- VC.Project.VCLinkerTool.Clang.LibraryDependencies
ms.openlocfilehash: 55b944040157d13741b992f4ec66c35d1b117d95
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79470250"
---
# <a name="clang-linker-properties-android-c"></a>Clang-Linkereigenschaften (Android C++)

| Eigenschaft | BESCHREIBUNG | Auswahl |
|--|--|--|
| Ausgabedatei | Die Option überschreibt den Standardnamen und den Speicherort des Programms, das der Linker erstellt. (-o) |
| Status anzeigen | Gibt Linkerstatusmeldungen aus. |
| Version | Die Option -version weist den Linker an, eine Versionsnummer in den Header der ausführbaren Datei einzufügen. |
| Ausführliche Ausgabe aktivieren | Die Option -verbose weist den Linker an, ausführliche Meldungen zum Debuggen auszugeben. |
| Inkrementelle Verknüpfung aktivieren | Diese Option weist den Linker an, die inkrementelle Verknüpfung zu aktivieren. |
| Suchpfad freigegebene Bibliothek | Ermöglicht dem Benutzer, den Suchpfad für die freigegebene Bibliothek mit Daten aufzufüllen. |
| Zusätzliche Bibliotheksverzeichnisse | Ermöglicht dem Benutzer das Überschreiben des umgebungsbedingten Bibliothekspfads. (-L Ordner). |
| Nicht aufgelöste Symbolverweise melden | Wenn diese Option aktiviert ist, werden nicht aufgelöste Symbol Verweise gemeldet. |
| Für Speicherverbrauch optimieren | Optimiert den Speicherverbrauch, indem die Symboltabellen bei Bedarf erneut gelesen werden. |
| Bestimmte Standardbibliotheken ignorieren | Gibt einen oder mehrere Namen der zu ignorierenden Standardbibliotheken an. |
| Symbolverweise erzwingen | Erzwingt, dass das Symbol als undefiniertes Symbol in die Ausgabedatei eingegeben wird. |
| Debuggersymbolinformationen | Debuggersymbolinformationen aus der Ausgabedatei. | **Alle einschließen**<br /><br />**Nicht benötigte Symbole für Umsetzungsvorgänge auslassen**<br /><br />**Nur Debuggersymbolinformationen auslassen**<br /><br />**Alle Symbolinformationen auslassen** |
| Debuggersymbolinformationen packen | Entfernen Sie die Debuggersymbolinformationen vor dem Packen.  Eine Kopie der ursprünglichen Binärdatei wird zum Debuggen verwendet. |
| Name der Zuordnungsdatei | Die Option Map weist den Linker an, eine Zuordnungsdatei mit dem vom Benutzer angegebenen Namen zu erstellen. |
| Variablen nach dem Umsetzen als ReadOnly kennzeichnen | Diese Option kennzeichnet Variablen nach dem Umsetzen als schreibgeschützt. |
| Sofortige Funktionsbindung aktivieren | Diese Option kennzeichnet das Objekt für sofortige Funktionsbindung. |
| Ausführbaren Stapel erfordern | Diese Option gibt an, dass die Ausgabe keinen ausführbaren Stapel erfordert. |
| Gesamtes Archiv | Diese Option verwendet den gesamten Code aus den Quellen und zusätzlichen Abhängigkeiten. |
| Zusätzliche Optionen | Zusätzliche Optionen |
| Zusätzliche Abhängigkeiten | Gibt zusätzliche Elemente an, die der Linkerbefehlszeile hinzugefügt werden sollen. |
| Bibliothekabhängigkeiten | Mit dieser Option können zusätzliche Bibliotheken angegeben werden, die der Linkerbefehlszeile hinzugefügt werden sollen. Die zusätzlichen Bibliotheken werden am Ende der Linkerbefehlszeile hinzugefügt, die mit *lib* beginnt und mit der Erweiterung " *. a* " oder " *. so* " endet.  (-lFILE) |

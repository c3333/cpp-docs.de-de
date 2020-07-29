---
title: Erstellen einer Importbibliothek und einer Exportdatei
ms.date: 09/05/2018
f1_keywords:
- VC.Project.VCLibrarianTool.ModuleDefinitionFile
- VC.Project.VCLibrarianTool.ExportNamedFunctions
- VC.Project.VCLibrarianTool.GenerateDebug
- VC.Project.VCLibrarianTool.ForceSymbolReferences
helpviewer_keywords:
- OUT library manager option
- INCLUDE library manager option
- /DEF library manager option
- exporting data
- import libraries, building
- -INCLUDE library manager option
- /OUT library manager option
- DEF library manager option
- -DEF library manager option
- -OUT library manager option
- /INCLUDE library manager option
- -EXPORT library manager option
- exporting data, export (.exp) files
- /EXPORT library manager option
- EXPORT library manager option
- .lib files
- EXP files
ms.assetid: 2fe4f30a-1dd6-4b05-84b5-0752e1dee354
ms.openlocfilehash: 5cb5224b3edaf84dbcb7c0429044a647fb5ac19a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229752"
---
# <a name="building-an-import-library-and-export-file"></a>Erstellen einer Importbibliothek und einer Exportdatei

Verwenden Sie die folgende Syntax, um eine Import Bibliothek und eine Exportdatei zu erstellen:

> **LIB/DEF**[**:**<em>deffile</em>] [*Optionen*] [*objfiles*] [*Bibliotheken*]

Wenn/DEF angegeben wird, erstellt LIB die Ausgabedateien aus den Export Spezifikationen, die im LIB-Befehl übermittelt werden. Es gibt drei Methoden zum Angeben von Exporten, die in der empfohlenen Reihenfolge der Verwendung aufgeführt sind:

1. Eine **`__declspec(dllexport)`** Definition in einer der *objfiles* -oder- *Bibliotheken*

1. Eine Spezifikation von/Export:*Name* in der LIB-Befehlszeile

1. Eine Definition in einer **Exports** -Anweisung in einem " *unffile* ".

Dabei handelt es sich um dieselben Methoden, die Sie zum Angeben von Exporten verwenden, wenn Sie ein Exportprogramm verknüpfen. Ein Programm kann mehr als eine Methode verwenden. Sie können Teile des LIB-Befehls (z. b. mehrere *objfiles* -oder/Export-Spezifikationen) in einer Befehlsdatei im LIB-Befehl angeben, wie Sie dies in einem Link Befehl tun können.

Die folgenden Optionen gelten für das Aufbauen einer Import Bibliothek und einer Exportdatei:

> **/Out:** *importieren*

Überschreibt den Standardausgabe Dateinamen für die *Import* Bibliothek, die erstellt wird. Wenn/out nicht angegeben wird, ist der Standardname der Basis Name der ersten Objektdatei oder-Bibliothek im Befehl lib und der Erweiterung. lib. Die Exportdatei erhält denselben Basis Namen wie die Import Bibliothek und die Erweiterung. Exp.

> **/Export:** *entryname* \[ **=** *internalname*] \[ , **\@** <em>Ordnungszahl</em> \[ , **Noname**]] \[ , **Daten**]

Exportiert eine Funktion aus dem Programm, um anderen Programmen das Abrufen der Funktion zu ermöglichen. Sie können auch Daten (mit dem Schlüsselwort " **Data** ") exportieren. Exporte werden in der Regel in einer DLL definiert.

*Entryname* ist der Name der Funktion oder des Datenelements, wie er vom aufrufenden Programm verwendet werden soll. Optional können Sie den *internalname* als Funktion angeben, die im definierenden Programm bekannt ist. Standardmäßig entspricht *internalname* dem *entryname*. Die *Ordinalzahl* gibt einen Index für die Export Tabelle im Bereich von 1 bis 65.535 an. Wenn Sie keine *Ordinalzahl*angeben, weist lib eine Zuweisung zu. Das **Noname** -Schlüsselwort exportiert die Funktion nur als Ordinalzahl ohne *entryname*. Das **Data** -Schlüsselwort wird zum Exportieren von Datenobjekten verwendet.

> **/Include:** *Symbol*

Fügt der Symboltabelle das angegebene *Symbol* hinzu. Diese Option ist nützlich, um die Verwendung eines Bibliotheks Objekts zu erzwingen, das andernfalls nicht eingeschlossen wäre.

Beachten Sie Folgendes: Wenn Sie die Import Bibliothek in einem vorläufigen Schritt erstellen, müssen Sie vor dem Erstellen der DLL-Datei beim Erstellen der dll denselben Satz von Objektdateien übergeben, wie Sie beim Erstellen der Import Bibliothek übergeben haben.

## <a name="see-also"></a>Siehe auch

[Arbeiten mit Importbibliotheken und Exportdateien](working-with-import-libraries-and-export-files.md)

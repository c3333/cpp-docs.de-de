---
title: Verwalten einer Bibliothek
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLibrarianTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLibrarianTool.AdditionalDependencies
- VC.Project.VCLibrarianTool.RemoveObjects
- VC.Project.VCLibrarianTool.LibraryPaths
- VC.Project.VCLibrarianTool.OutputFile
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryNames
- VC.Project.VCLibrarianTool.AdditionalLibraryDirectories
- VC.Project.VCLibrarianTool.ListContentsFile
- VC.Project.VCLibrarianTool.ListContents
- VC.Project.VCLibrarianTool.SubSystemVersion
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryName
- VC.Project.VCLibrarianTool.SubSystem
helpviewer_keywords:
- /LIBPATH library manager option
- OUT library manager option
- CONVERT library manager option
- LIBPATH library manager option
- /LIST library manager option
- object files, building and modifying
- -LINK50COMPAT library manager option
- REMOVE library manager option
- SUBSYSTEM library manager option
- /LINK50COMPAT library manager option
- /OUT library manager option
- LIB [C++], managing COFF libraries
- -CONVERT library manager option
- LINK50COMPAT library manager option
- -OUT library manager option
- -REMOVE library manager option
- -LIST library manager option
- /SUBSYSTEM library manager option
- -SUBSYSTEM library manager option
- /REMOVE library manager option
- -LIBPATH library manager option
- object files
- LIST library manager option
- /CONVERT library manager option
ms.assetid: f56a8b85-fbdc-4c09-8d8e-00f0ffe1da53
ms.openlocfilehash: de55059834a0887d487b7be38377af9984512b75
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336404"
---
# <a name="managing-a-library"></a>Verwalten einer Bibliothek

Der Standardmodus für LIB besteht darin, eine Bibliothek von COFF-Objekten zu erstellen oder zu ändern. LIB wird in diesem Modus ausgeführt, wenn Sie nicht /EXTRACT (um ein Objekt in eine Datei zu kopieren) oder /DEF (zum Erstellen einer Importbibliothek) angeben.

Verwenden Sie die folgende Syntax, um eine Bibliothek aus Objekten und/oder Bibliotheken zu erstellen:

```
LIB [options...] files...
```

Mit diesem Befehl wird eine Bibliothek aus einer oder mehreren *Eingabedateien*erstellt. Bei den *Dateien* kann es sich um COFF-Objektdateien, 32-Bit-OMF-Objektdateien oder vorhandene COFF-Bibliotheken erachten. LIB erstellt eine Bibliothek, die alle Objekte in den angegebenen Dateien enthält. Wenn es sich bei einer Eingabedatei um eine 32-Bit-OMF-Objektdatei handelt, konvertiert LIB sie in COFF, bevor die Bibliothek erstellt wird. LIB kann kein 32-Bit-OMF-Objekt akzeptieren, das sich in einer Bibliothek befindet, die von der 16-Bit-Version von LIB erstellt wurde. Sie müssen zuerst die 16-Bit-LIB verwenden, um das Objekt zu extrahieren. dann können Sie die extrahierte Objektdatei als Eingabe für die 32-Bit-LIB verwenden.

Standardmäßig benennt LIB die Ausgabedatei mit dem Basisnamen des ersten Objekts oder der ersten Bibliotheksdatei und der Erweiterung .lib. Die Ausgabedatei wird im aktuellen Verzeichnis abgelegt. Wenn bereits eine Datei mit demselben Namen vorhanden ist, ersetzt die Ausgabedatei die vorhandene Datei. Um eine vorhandene Bibliothek beizubehalten, verwenden Sie die Option /OUT, um einen Namen für die Ausgabedatei anzugeben.

Die folgenden Optionen gelten für das Erstellen und Ändern einer Bibliothek:

**/LIBPATH:** *dir*<br/>
Überschreibt den Bibliothekspfad der Umgebung. Weitere Informationen finden Sie in der Beschreibung der Option LINK [/LIBPATH.](libpath-additional-libpath.md)

**/LISTE**<br/>
Zeigt Informationen über die Ausgabebibliothek für die Standardausgabe an. Die Ausgabe kann in eine Datei umgeleitet werden. Sie können /LIST verwenden, um den Inhalt einer vorhandenen Bibliothek zu bestimmen, ohne sie zu ändern.

**/NAME:** *Dateiname*<br/>
Gibt beim Erstellen einer Importbibliothek den Namen der DLL an, für die die Importbibliothek erstellt wird.

**/NODEFAULTLIB**<br/>
Entfernt eine oder mehrere Standardbibliotheken aus der Liste der Bibliotheken, die beim Auflösen externer Verweise durchsucht werden. Weitere Informationen finden Sie unter [/NODEFAULTLIB.](nodefaultlib-ignore-libraries.md)

**/OUT:** *Dateiname*<br/>
Überschreibt den Standardausgabedateinamen. Standardmäßig wird die Ausgabebibliothek im aktuellen Verzeichnis mit dem Basisnamen der ersten Bibliothek oder Objektdatei in der Befehlszeile und der Erweiterung .lib erstellt.

**/REMOVE:** *Objekt*<br/>
Lässt das angegebene *Objekt* aus der Ausgabebibliothek aus. LIB erstellt eine Ausgabebibliothek, indem alle Objekte (in Objektdateien oder Bibliotheken) kombiniert und dann alle objekte gelöscht werden, die mit /REMOVE angegeben sind.

**/SUBSYSTEM:****"CONSOLE** &#124; **EFI_APPLICATION** &#124; EFI_APPLICATION **EFI_BOOT_SERVICE_DRIVER &#124; &#124; &#124;** EFI_ROM **&#124;** **EFI_RUNTIME_DRIVER &#124;** &#124; **NATIVE** &#124; **POSIX** &#124; **WINDOWS** &#124; **WINDOWSCE**<br/>
Teilt dem Betriebssystem mit, wie ein Programm ausgeführt wird, das durch Verknüpfen mit der Ausgabebibliothek erstellt wurde. Weitere Informationen finden Sie in der Beschreibung der Option LINK [/SUBSYSTEM.](subsystem-specify-subsystem.md)

Lib-Optionen, die in der Befehlszeile angegeben sind, werden nicht berücksichtigt.

Sie können LIB verwenden, um die folgenden Bibliotheksverwaltungsaufgaben auszuführen:

- Um einer Bibliothek Objekte hinzuzufügen, geben Sie den Dateinamen für die vorhandene Bibliothek und die Dateinamen für die neuen Objekte an.

- Um Bibliotheken zu kombinieren, geben Sie die Bibliotheksdateinamen an. Sie können Objekte hinzufügen und Bibliotheken mit einem einzigen LIB-Befehl kombinieren.

- Um einen Bibliotheksmember durch ein neues Objekt zu ersetzen, geben Sie die Bibliothek mit dem zu ersetzenden Memberobjekt und den Dateinamen für das neue Objekt (oder die Bibliothek, die es enthält) an. Wenn ein Objekt mit demselben Namen in mehr als einer Eingabedatei vorhanden ist, legt LIB das letzte im Befehl LIB angegebene Objekt in die Ausgabebibliothek ein. Wenn Sie einen Bibliotheksmember ersetzen, müssen Sie das neue Objekt oder die neue Bibliothek nach der Bibliothek angeben, die das alte Objekt enthält.

- Um ein Mitglied aus einer Bibliothek zu löschen, verwenden Sie die Option /REMOVE. LIB verarbeitet alle Spezifikationen von /REMOVE, nachdem alle Eingabeobjekte kombiniert wurden, unabhängig von der Befehlszeilenreihenfolge.

> [!NOTE]
> Sie können ein Element nicht sowohl löschen als auch im gleichen Schritt in eine Datei extrahieren. Sie müssen zuerst das Memberobjekt mit /EXTRACT extrahieren und dann LIB erneut mit /REMOVE ausführen. Dieses Verhalten unterscheidet sich von dem der 16-Bit-LIB (für OMF-Bibliotheken), die in anderen Microsoft-Produkten bereitgestellt wird.

## <a name="see-also"></a>Siehe auch

[LIB-Referenz](lib-reference.md)

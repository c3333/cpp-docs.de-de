---
title: /Fe (Name der EXE-Datei)
ms.date: 11/04/2016
f1_keywords:
- /fe
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
ms.openlocfilehash: f0bd8f3a96555cc29d06f74fb44a73bbed32889b
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825577"
---
# <a name="fe-name-exe-file"></a>/Fe (Name der EXE-Datei)

Gibt einen Namen und ein Verzeichnis für die exe-Datei oder dll an, die vom Compiler erstellt wurde.

## <a name="syntax"></a>Syntax

> **/FE**[_Pfadname_] \
> **/Fe:** _Pfadname_

### <a name="arguments"></a>Argumente

*Pfadnamen*<br/>
Der relative oder absolute Pfad und Basis Dateiname oder der relative oder absolute Pfad zu einem Verzeichnis oder der Basis Dateiname, der für die generierte ausführbare Datei verwendet werden soll.

## <a name="remarks"></a>Bemerkungen

Mit der **/FE** -Option können Sie das Ausgabeverzeichnis, den ausführbaren Namen der Ausgabe oder beides für die generierte ausführbare Datei angeben. Wenn *Pfadnamen* in einem Pfad Trennzeichen (**&#92;**) endet, wird davon ausgegangen, dass nur das Ausgabeverzeichnis angegeben wird. Andernfalls wird die letzte Komponente von *Pfadnamen* als Basis Name der Ausgabedatei verwendet, und der Rest von *Pfadnamen* gibt das Ausgabeverzeichnis an. Wenn *Pfadnamen* keine Pfad Trennzeichen enthält, wird davon ausgegangen, dass der Name der Ausgabedatei im aktuellen Verzeichnis angegeben wird. Der *Pfadname* muss in doppelte Anführungszeichen (**"**) eingeschlossen werden, wenn er Zeichen enthält, die sich nicht in einem kurzen Pfad befinden dürfen, z. b. Leerzeichen, erweiterte Zeichen oder Pfad Komponenten, die mehr als acht Zeichen lang sind.

Wenn die **/FE** -Option nicht angegeben ist oder ein Dateibasisname nicht in *Pfadnamen*angegeben ist, übergibt der Compiler der Ausgabedatei einen Standardnamen, wobei der Basisname der ersten Quell-oder Objektdatei, die in der Befehlszeile angegeben ist, und die Erweiterung. exe oder. dll verwendet wird.

Wenn Sie die Option [/c (Kompilieren ohne Verknüpfen)](c-compile-without-linking.md) angeben, hat **/FE** keine Auswirkung.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Öffnen Sie die **Eigenschaften** > Seite**Allgemeine** Linker-Eigenschaft für den**Linker** > .

1. Ändern Sie die Eigenschaft **Ausgabedatei** . Klicken Sie auf **OK**, um die Änderungen zu speichern.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="example"></a>Beispiel

Die folgende Befehlszeile kompiliert alle C-Quelldateien und verknüpft Sie mit dem aktuellen Verzeichnis. Die resultierende ausführbare Datei hat den Namen "Process. exe" und wird im Verzeichnis "c:\benutzer\benutzername\repos\my project\bin" erstellt.

```
CL /Fe"C:\Users\User Name\repos\My Project\bin\PROCESS" *.C
```

## <a name="example"></a>Beispiel

Mit der folgenden Befehlszeile wird eine ausführbare `C:\BIN` Datei in mit dem gleichen Basis Namen wie die erste Quelldatei im aktuellen Verzeichnis erstellt:

```
CL /FeC:\BIN\ *.C
```

## <a name="see-also"></a>Weitere Informationen

[Ausgabedatei (/F) Optionen](output-file-f-options.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
[Festlegen des Pfadnamens](specifying-the-pathname.md)<br/>

---
title: /Fi (Ausgabedateiname vorverarbeiten)
ms.date: 08/12/2020
f1_keywords:
- /Fi
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
ms.openlocfilehash: 82bf09a8f01f656f90ad9971530b05f108fc95a4
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561088"
---
# <a name="fi-preprocess-output-file-name"></a>`/Fi` (Ausgabe Dateiname vorverarbeiten)

Gibt den Namen der Ausgabedatei an, in die die Compileroption [ `/P` (Vorverarbeitung in einer Datei)](p-preprocess-to-a-file.md) die vorverarbeitete Ausgabe schreibt.

## <a name="syntax"></a>Syntax

> **`/Fi`**_`pathname`_

### <a name="parameters"></a>Parameter

*`pathname`*\
Der relative oder absolute Pfad und Dateiname der Ausgabedatei, die von der **`/P`** Compileroption erzeugt wird. Oder der Verzeichnispfad für die *`.i`* Ausgabedateien, wenn mehr als eine Eingabedatei angegeben wird. Platzieren Sie keinen Leerraum zwischen der **`/Fi`** -Option und der-Option *`pathname`* .

## <a name="remarks"></a>Bemerkungen

Verwenden Sie die- **`/Fi`** Compileroption in Verbindung mit der- **`/P`** Compileroption. Wenn **`/P`** nicht angegeben ist, wird die **`/Fi`** Befehlszeilen Warnung D9007 ausgelöst.

Wenn Sie nur einen Verzeichnispfad (einen Pfad, der mit einem umgekehrten Schrägstrich endet **`\`** ) für den- *`pathname`* Parameter angeben, wird der Basisname der Quelldatei als Basis Name der vorverarbeiteten Ausgabedatei verwendet. Der- *`pathname`* Parameter erfordert keine bestimmte Dateinamenerweiterung. Es wird jedoch eine Erweiterung von ". i" verwendet, wenn Sie keine Dateinamenerweiterung angeben.

### <a name="example"></a>Beispiel

Die folgende Befehlszeile führt eine Vorverarbeitung *`PROGRAM.cpp`* durch, behält Kommentare bei, fügt [`#line`](../../preprocessor/hash-line-directive-c-cpp.md) Anweisungen hinzu und schreibt das Ergebnis in die *`MYPROCESS.i`* Datei:

```cmd
CL /P /FiMYPROCESS.I PROGRAM.CPP
```

Diese Befehlszeile führt *`main.cpp`* vor und *`helper.cpp`* in *`main.i`* *`helper.i`* ein Unterverzeichnis mit dem Namen *`preprocessed`* :

```cmd
CL /P /Fi".\\preprocessed\\" main.cpp helper.cpp
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie die Quelldatei oder das Dialogfeld **Eigenschaften Seiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Präprozessor** aus.

1. Legen Sie für die **Vorverarbeitung eine Datei** Eigenschaft den Wert **Ja**fest.

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Geben Sie die **`/Fi`** Compileroption und *`pathname`* im Feld **zusätzliche Optionen** ein. Geben Sie beim Festlegen dieser Eigenschaft für ein Projekt nur einen Verzeichnispfad und keinen Dateinamen an.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[`/P` (In einer Datei vorverarbeiten)](p-preprocess-to-a-file.md)<br/>
[Festlegen des Pfadnamens](specifying-the-pathname.md)

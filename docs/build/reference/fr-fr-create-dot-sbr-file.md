---
title: /FR, /Fr (SBR-Datei erstellen)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BrowseInformation
- VC.Project.VCCLCompilerTool.BrowseInformation
- /fr
- VC.Project.VCCLCompilerTool.BrowseInformationFile
- VC.Project.VCCLWCECompilerTool.BrowseInformationFile
helpviewer_keywords:
- /FR compiler option [C++]
- -FR compiler option [C++]
- FR compiler option [C++]
- symbolic browser information
ms.assetid: 3fd8f88b-3924-4feb-9393-287036a28896
ms.openlocfilehash: 58f55811f5d2bb81bc77da38a87c35bae91ce6cb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320516"
---
# <a name="fr-fr-create-sbr-file"></a>/FR, /Fr (SBR-Datei erstellen)

Erstellt SBR-Dateien.

## <a name="syntax"></a>Syntax

```
/FR[pathname[\filename]]
/Fr[pathname[\filename]]
```

## <a name="remarks"></a>Bemerkungen

> [!WARNING]
> Obwohl BSCMAKE weiterhin mit Visual Studio installiert wird, wird es nicht mehr von der IDE verwendet. Seit Visual Studio 2008 werden Browse- und Symbolinformationen automatisch in einer SQL Server-.SDF-Datei im Projektmappenordner gespeichert.

Beim Erstellungsvorgang erstellt das Microsoft Browse Information Maintenance-Hilfsprogramm (BSCMAKE) anhand dieser Dateien eine BSC-Datei, die zur Darstellung von Browseinformationen verwendet wird.

Mit **/FR** wird eine SBR-Datei mit vollständigen symbolischen Informationen erstellt.

Mit **/Fr** wird eine SBR-Datei ohne Informationen über lokale Variablen erstellt.

Wenn Sie keinen Wert für `filename`angeben, erhält die SBR-Datei denselben Basisnamen wie die Quelldatei.

**/Fr** ist veraltet. Verwenden Sie stattdessen **/FR** . Weitere Informationen hierzu finden Sie unter „Veraltete und entfernte Compileroptionen“ in [Compiler Options Listed by Category](compiler-options-listed-by-category.md).

> [!NOTE]
> Ändern Sie nicht die Erweiterung SBR. BSCMAKE erfordert, dass die Zwischendateien diese Erweiterung haben.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie im Navigationsbereich die Eigenschaftenseite **C/C++**, **Browseinformationsdatei** aus.

1. Ändern Sie die Eigenschaft **Browseinformationsdatei** oder **Durchsuchen der Informationen aktivieren** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Prüfen Sie <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> und <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>.

## <a name="see-also"></a>Siehe auch

[Ausgabedatei (/F) Optionen](output-file-f-options.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
[Festlegen des Pfadnamens](specifying-the-pathname.md)

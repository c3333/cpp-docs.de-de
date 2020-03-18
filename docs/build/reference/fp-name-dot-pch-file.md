---
title: /FP (Name &period;PCH-Datei)
description: Verwenden Sie die/FP-Compileroption, um den Namen der vorkompilierten Header Datei anzugeben.
ms.date: 05/31/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderFile
helpviewer_keywords:
- Fp compiler option [C++]
- -Fp compiler option [C++]
- naming precompiler header files
- PCH files, naming
- names [C++], PCH
- .pch files, naming
- precompiled header files, naming
- /Fp compiler option [C++]
ms.assetid: 0fcd9cbd-e09f-44d3-9715-b41efb5d0be2
ms.openlocfilehash: d62c5bd9fc7920c0a2a5530879680fad2a01d39a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439781"
---
# <a name="fp-name-periodpch-file"></a>/FP (Name &period;PCH-Datei)

Stellt einen Pfadnamen für einen vorkompilierten Header bereit, anstatt den Standard Pfadnamen zu verwenden.

## <a name="syntax"></a>Syntax

> **/FP**<em>Pfadname</em>

## <a name="remarks"></a>Bemerkungen

Verwenden Sie die Option **/FP** mit [/Yc (Vorkompilierte Header Datei erstellen)](yc-create-precompiled-header-file.md) oder [/Yu (Vorkompilierte Header Datei verwenden)](yu-use-precompiled-header-file.md) , um den Pfad und den Dateinamen für die vorkompilierte Header Datei (PCH) anzugeben. Standardmäßig erstellt die Option **/Yc** einen PCH-Dateinamen, indem der Basis Name der Quelldatei und eine *PCH* -Erweiterung verwendet werden.

Wenn Sie keine Erweiterung als Teil von *Pfadname*angeben, wird eine *PCH* -Erweiterung angenommen. Wenn Sie einen Verzeichnisnamen mithilfe eines Schrägstrichs ( **/** ) am Ende von *Pfadname*angeben, lautet der Standard Dateiname VC*Version*0. pch, wobei *Version* die Hauptversion des Visual Studio-Toolsets ist. Dieses Verzeichnis muss vorhanden sein, oder es wird ein Fehler C1083 generiert.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Öffnen Sie die **Eigenschaften Seite Konfigurations Eigenschaften** > **C++ C/**  > **Vorkompilierte Header** .

1. Ändern Sie die Eigenschaft der **vorkompilierten Header Ausgabedatei** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="examples"></a>Beispiele

Zum Erstellen einer separaten benannten Version der vorkompilierten Header Datei für den Debugbuild des Programms können Sie einen Befehl wie den folgenden angeben:

```CMD
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

Der folgende Befehl gibt die Verwendung einer vorkompilierten Header Datei mit dem Namen MYPCH. pch an. Der Compiler kompiliert den Quellcode in Prog. cpp bis zum Ende von MyApp. h und legt den vorkompilierten Code in MYPCH. pch ab. Anschließend wird der Inhalt von MYPCH. pch verwendet und der Rest von PROG. cpp kompiliert, um eine OBJ-Datei zu erstellen. Die Ausgabe dieses Beispiels ist eine Datei mit dem Namen "PROG. exe".

```CMD
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>Weitere Informationen

[Ausgabedatei (/F) Optionen](output-file-f-options.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
[Festlegen des Pfadnamens](specifying-the-pathname.md)

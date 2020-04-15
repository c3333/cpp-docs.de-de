---
title: /SOURCELINK (SourceLink-Datei in die PDB-Datei einschließen)
description: Referenzhandbuch zur Linkeroption /SOURCELINK in Microsoft C++.
ms.date: 03/31/2020
f1_keywords:
- /sourcelink
helpviewer_keywords:
- /SOURCELINK linker option
- /SOURCELINK
ms.openlocfilehash: bde55c401e17f7b3c84ffcdad29dda2badcc260b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336071"
---
# <a name="sourcelink-include-source-link-file-in-pdb"></a>/SOURCELINK (Source Link-Datei in PDB einschließen)

Gibt eine Source Link-Konfigurationsdatei an, die in die vom Linker generierte PDB-Datei aufgenommen werden soll.

## <a name="syntax"></a>Syntax

> **`/SOURCELINK:`**_`filename`_

## <a name="arguments"></a>Argumente

*Dateiname*<br/>
Gibt eine JSON-formatierte Konfigurationsdatei an, die eine einfache Zuordnung lokaler Dateipfade zu URLs für Quelldateien enthält, die im Debugger angezeigt werden sollen. Weitere Informationen zum Format dieser Datei finden Sie unter [Quelllink-JSON-Schema](https://github.com/dotnet/designs/blob/master/accepted/2020/diagnostics/source-link.md#source-link-json-schema).

## <a name="remarks"></a>Bemerkungen

Source Link ist ein sprach- und quellcodegesteuertes Agnostiksystem zur Bereitstellung von Quelldebugging für Binärdateien. Source Link wird für systemeigene C++-Binärdateien ab Visual Studio 2017 Version 15.8 unterstützt. Eine Übersicht über den Quelllink finden Sie unter [Quelllink](https://github.com/dotnet/designs/blob/master/accepted/2020/diagnostics/source-link.md). Informationen zur Verwendung von Quellverknüpfung in Ihren Projekten und zum Generieren der SourceLink-Datei als Teil Ihres Projekts finden Sie unter Verwenden von [Quellverknüpfung](https://github.com/dotnet/sourcelink#using-source-link-in-c-projects).

### <a name="to-set-the-sourcelink-linker-option-in-visual-studio"></a>So legen Sie die Linkeroption /SOURCELINK in Visual Studio fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** für das Projekt. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die Eigenschaftenseite **Configuration Properties** > **Linker** > **Command Line** aus.

1. Fügen **Additional options** Sie **`/SOURCELINK:`** _`filename`_ im Feld Zusätzliche Optionen **hinzu,** und wählen Sie dann OK oder **Anwenden** aus, um Ihre Änderungen zu speichern.

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

- Diese Option hat kein programmgesteuertes Äquivalent.

## <a name="see-also"></a>Siehe auch

[MSVC-Linkerreferenz](linking.md)<br/>
[MSVC-Linkeroptionen](linker-options.md)

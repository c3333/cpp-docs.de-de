---
title: Ressourcen
ms.date: 08/28/2019
ms.topic: article
ms.assetid: dade2f6b-c51f-4c33-9023-41956ae4b5f6
f1_keywords:
- VC.Project.VCResourceCompilerTool.PreprocessorDefinitions
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- VC.Project.VCResourceCompilerTool.Culture
- VC.Project.VCResourceCompilerTool.AdditionalIncludeDirectories
- VC.Project.VCResourceCompilerTool.IgnoreStandardIncludePath
- VC.Project.VCResourceCompilerTool.ShowProgress
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.ResourceOutputFileName
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
- vc.project.AdditionalOptionsPage
ms.openlocfilehash: c4a3048bfa07e9635662534b510fa57caa091f00
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336075"
---
# <a name="resources-property-page"></a>Ressourcen-Eigenschaftenseite

Bei systemeigenen Windows-Desktopprogrammen ruft der Build den [Ressourcencompiler (rc.exe)](/windows/win32/menurc/resource-compiler) auf, um der Binärdatei Bilder, Zeichenfolgentabellen und *.res-Dateien* hinzuzufügen. Die auf dieser Eigenschaftenseite verfügbar gemachten Eigenschaften werden an den Ressourcencompiler und nicht an den C++-Compiler oder den Linker übergeben. Weitere Informationen zu den hier aufgeführten Eigenschaften und deren Zuordnung zu RC-Befehlszeilenoptionen finden Sie unter [Verwenden von RC (Die RC-Befehlszeile)](/windows/win32/menurc/using-rc-the-rc-command-line-). Informationen zum Zugriff auf **Resources** die Ressourcen-Eigenschaftenseiten finden Sie unter Festlegen von [C++-Compiler- und Buildeigenschaften in Visual Studio](../working-with-project-properties.md). Informationen zum programmgesteuerten Zugriff auf diese Eigenschaften finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCResourceCompilerTool>.

Eigenschaften für .NET-Ressourcen in C++/CLI-Anwendungen werden auf der [Eigenschaftenseite Verwaltete Ressourcen](managed-resources-property-page.md)verfügbar gemacht.

## <a name="preprocessor-definitions"></a>Präprozessordefinitionen

Gibt eine oder mehrere Definitionen für den Ressourcencompiler an. (/d[makro])

## <a name="undefine-preprocessor-definitions"></a>Präprozessordefinitionen aufheben

Dedefine eines Symbols. (/u)

## <a name="culture"></a>culture

Listet die Kultur (z. B. US-Englisch oder Italienisch) auf, die in den Ressourcen verwendet wird. (/l [num])

## <a name="additional-include-directories"></a>Zusätzliche Includeverzeichnisse

Gibt ein oder mehrere Verzeichnisse an, die dem Includepfad hinzugefügt werden sollen. Verwenden Sie das Semikolon-Trennzeichen, wenn mehr als ein. (/I[Pfad])

## <a name="ignore-standard-include-paths"></a>Standard-Includepfade ignorieren

Verhindert, dass der Ressourcencompiler nach Include-Dateien in Verzeichnissen sucht, die in den INCLUDE-Umgebungsvariablen angegeben sind. (/X)

## <a name="show-progress"></a>Status anzeigen

Senden Sie Fortschrittsmeldungen an das Ausgabefenster. (/v)

## <a name="suppress-startup-banner"></a>Startbanner unterdrücken

Unterdrücken der Anzeige des Startbanners und der Informationsmeldung (/nologo)

## <a name="resource-file-name"></a>Ressourcendateiname

Gibt den Namen der Ressourcendatei an (/fo[Datei])

## <a name="null-terminate-strings"></a>Null-Beendigungszeichenfolgen

Fügen Sie NULL an alle Zeichenfolgen in den Zeichenfolgentabellen an. (/n)

## <a name="see-also"></a>Siehe auch

[C++-Projekteigenschaftsseitenverweis](property-pages-visual-cpp.md)

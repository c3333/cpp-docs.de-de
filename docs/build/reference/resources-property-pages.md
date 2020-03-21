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
ms.openlocfilehash: 4f3688da4feb11f673e11372e5df086dc8c7e21a
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078290"
---
# <a name="resources-property-page"></a>Ressourcen (Eigenschaften Seite)

Bei nativen Windows-Desktop Programmen ruft der Build den [Ressourcen Compiler (RC. exe)](/windows/win32/menurc/resource-compiler) auf, um der Binärdatei Bilder, Zeichen folgen Tabellen und *Res* -Dateien hinzuzufügen. Die Eigenschaften, die auf dieser Eigenschaften Seite verfügbar gemacht werden, werden an den Ressourcen Compiler C++ und nicht an den Compiler oder den Linker übermittelt. Weitere Informationen zu den hier aufgeführten Eigenschaften und deren Zuordnung zu den RC-Befehlszeilenoptionen finden Sie unter [Verwenden von RC (RC-Befehlszeile)](/windows/win32/menurc/using-rc-the-rc-command-line-). Informationen zum Zugreifen auf die Eigenschaften Seiten für **Ressourcen** finden Sie unter [festlegen C++ von Compiler-und Buildeigenschaften in Visual Studio](../working-with-project-properties.md). Informationen zum programmgesteuerten Zugriff auf diese Eigenschaften finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCResourceCompilerTool>.

Eigenschaften für .NET-Ressourcen C++in/CLI-Anwendungen werden auf der Eigenschaften [Seite verwaltete Ressourcen](managed-resources-property-page.md)verfügbar gemacht.

## <a name="preprocessor-definitions"></a>Präprozessordefinitionen

Gibt eine oder mehrere Definitionen für den Ressourcen Compiler an. (/d [Makro])

## <a name="undefine-preprocessor-definitions"></a>Präprozessordefinitionen aufheben

Aufheben der Definition eines Symbols. /u

## <a name="culture"></a>Kultur

Listet die in den Ressourcen verwendete Kultur (z. b. US-Englisch oder Italienisch) auf. (/l [NUM])

## <a name="additional-include-directories"></a>Zusätzliche Includeverzeichnisse

Gibt mindestens ein Verzeichnis an, das dem Include-Pfad hinzugefügt werden soll. Verwenden Sie Semikolons als Trennzeichen, wenn mehr als ein Trennzeichen verwendet wird. (/I [Pfad])

## <a name="ignore-standard-include-paths"></a>Standardincludepfade ignorieren

Verhindert, dass der Ressourcen Compiler in Verzeichnissen, die in den INCLUDE-Umgebungsvariablen angegeben sind, nach Includedateien sucht. /X

## <a name="show-progress"></a>Status anzeigen

Statusmeldungen an Ausgabefenster senden. /v

## <a name="suppress-startup-banner"></a>Startbanner unterdrücken

Unterdrücken der Anzeige des Start Banners und der Informations Meldung (/nologo)

## <a name="resource-file-name"></a>Ressourcen Dateiname

Gibt den Namen der Ressourcen Datei an (/FO [File]).

## <a name="null-terminate-strings"></a>NULL-Zeichen folgen beenden

Fügen Sie NULL an alle Zeichen folgen in den Zeichen folgen Tabellen an. /n

## <a name="see-also"></a>Weitere Informationen

[C++Referenz zur Projekteigenschaften Seite](property-pages-visual-cpp.md)
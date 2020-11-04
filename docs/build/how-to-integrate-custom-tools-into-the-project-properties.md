---
title: 'Vorgehensweise: Integrieren von benutzerdefinierten Tools in die Projekteigenschaften'
description: In diesem Artikel erfahren Sie, wie Sie benutzerdefinierte Tools in die Projekteigenschaften in Visual Studio-C++-Projekten integrieren.
ms.date: 10/08/2020
helpviewer_keywords:
- 'MSBuild (C++), howto: integrate custom tools'
ms.openlocfilehash: 58626101d54c5b1f9749174e5f3e8938c431d025
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92922152"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>Vorgehensweise: Integrieren von benutzerdefinierten Tools in die Projekteigenschaften

Sie können dem Visual Studio-Fenster **Eigenschaftenseiten** durch Erstellen einer XML-Datei benutzerdefinierte Tooloptionen hinzufügen.

Im Abschnitt **Konfigurationseigenschaften** des Fensters **Eigenschaftenseiten** werden Einstellungsgruppen angezeigt, die als *Regeln* bezeichnet werden. Jede Regel enthält die Einstellungen für ein Tool oder eine Gruppe Features. Beispielsweise enthält die **Linker** -Regel die Einstellungen für das Linkertool. Die Einstellungen in einer Regel können weiter in *Kategorien* unterteilt werden.

Sie können eine Regeldatei erstellen, die Eigenschaften für Ihr benutzerdefiniertes Tool enthält, sodass die Eigenschaften beim Starten von Visual Studio geladen werden. Informationen zum Ändern der Datei finden Sie unter [Plattformerweiterbarkeit, Teil 2](/archive/blogs/vsproject/platform-extensibility-part-2) auf dem Blog des Visual Studio Project Team (Visual Studio-Projektteam).

::: moniker range="msvc-140"

Der Ordner zum Ablegen der Regeldatei hängt vom Gebietsschema und der verwendeten Visual Studio-Version ab. Bei der Developer-Eingabeaufforderung in Visual Studio 2015 oder einer früheren Version ist der Regelordner *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\<locale>`* . In Visual Studio 2015 ist der Wert für `<version>` *`v140`* . `<locale>` ist eine LCID, z. B. `1033` für Englisch. Für jede installierte Edition von Visual Studio und jede Sprache gibt es einen eigenen Pfad. Beispielsweise könnte der Standardpfad für den Regelordner für Visual Studio 2015 Community Edition in englischer Sprache *`C:\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\v140\1033\`* sein.

::: moniker-end

::: moniker range="msvc-150"

Der Ordner zum Ablegen der Regeldatei hängt vom Gebietsschema und der verwendeten Visual Studio-Version ab. Bei der Developer-Eingabeaufforderung in Visual Studio 2017 ist der Regelordner *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\<locale>\`* . `<locale>` ist eine LCID, z. B. `1033` für Englisch. Bei der Developer-Eingabeaufforderung in Visual Studio 2015 oder einer früheren Version ist der Regelordner *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\<locale>\`* mit *`v140`* als Wert für `<version>` in Visual Studio 2015. Für jede installierte Edition von Visual Studio und jede Sprache gibt es einen eigenen Pfad. Beispielsweise könnte der Standardpfad für den Regelordner für Visual Studio 2017 Community Edition in englischer Sprache *`C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\VC\VCTargets\1033\`* sein.

::: moniker-end

::: moniker range=">=msvc-160"

Der Ordner zum Ablegen der Regeldatei hängt vom Gebietsschema und der verwendeten Visual Studio-Version ab. Bei der Developer-Eingabeaufforderung in Visual Studio 2019 oder einer höheren Version ist der Regelordner *`%VSINSTALLDIR%MSBuild\Microsoft\VC\<version>\<locale>\`* mit *`v160`* als Wert für `<version>` in Visual Studio 2019. `<locale>` ist eine LCID, z. B. `1033` für Englisch. In Visual Studio 2017 ist der Regelordner *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\<locale>\`* . Bei der Developer-Eingabeaufforderung in Visual Studio 2015 oder einer früheren Version ist der Regelordner *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\<locale>\`* . Für jede installierte Edition von Visual Studio und jede Sprache gibt es einen eigenen Pfad. Beispielsweise könnte der Standardpfad für den Regelordner für Visual Studio 2019 Community Edition in englischer Sprache *`C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\MSBuild\Microsoft\VC\v160\1033\`* sein.

::: moniker-end

### <a name="to-add-or-change-project-properties"></a>Hinzufügen oder Ändern von Projekteigenschaften

1. Erstellen Sie im XML-Editor eine XML-Datei.

1. Speichern Sie die Datei im Standardregelordner. Passen Sie den Pfad für Ihre Sprache und Visual Studio-Edition an. Jede Regel im Fenster **Eigenschaftenseiten** wird durch eine XML-Datei in diesem Ordner dargestellt. Achten Sie darauf, dass die Datei im Ordner eindeutig benannt ist.

1. Kopieren Sie den Inhalt einer vorhandenen Regeldatei, z. B. *`rc.xml`* , schließen Sie sie, ohne die Änderungen zu speichern, und fügen Sie dann den Inhalt in Ihre neue XML-Datei ein. Sie können jede beliebige XML-Schemadatei kopieren, um sie als Vorlage zu verwenden. Verwenden Sie eine, die Ihrem Tool ähnelt.

1. Ändern Sie in der neuen XML-Datei die Inhalte nach Ihren Anforderungen. Achten Sie darauf, den **Rule Name** (Regelname) und **Rule.DisplayName** (Regel.Anzeigename) oben in der Datei zu ändern.

1. Speichern Sie Ihre Änderungen, und schließen Sie die Datei.

1. Die XML-Dateien im Regelordner werden beim Starten von Visual Studio geladen. Starten Sie Visual Studio neu, um die neue Datei zu testen.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf ein Projekt, und klicken Sie dann auf **Eigenschaften**. Überprüfen Sie im Fenster **Eigenschaftenseiten** , ob ein neuer Knoten mit dem Namen Ihrer Regel vorhanden ist.

## <a name="see-also"></a>Siehe auch

[MSBuild on the Command Line – C++ (C++: MSBuild in der Befehlszeile)](msbuild-visual-cpp.md)

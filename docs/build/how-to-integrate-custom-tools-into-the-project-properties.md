---
title: 'Vorgehensweise: Integrieren von benutzerdefinierten Tools in die Projekteigenschaften'
ms.date: 05/16/2019
helpviewer_keywords:
- 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
ms.openlocfilehash: 0c0233ad6715a3adb7d47f021a87207f288d5139
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837034"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>Vorgehensweise: Integrieren von benutzerdefinierten Tools in die Projekteigenschaften

Sie können dem Visual Studio-Fenster **Eigenschaftenseiten** benutzerdefinierte Tooloptionen hinzufügen, indem Sie eine zugrundeliegende XML-Schemadatei erstellen.

Im Abschnitt **Konfigurationseigenschaften** des Fensters **Eigenschaftenseiten** werden Einstellungsgruppen angezeigt, die als *Regeln* bezeichnet werden. Jede Regel enthält die Einstellungen für ein Tool oder eine Gruppe Features. Beispielsweise enthält die **Linker**-Regel die Einstellungen für das Linkertool. Die Einstellungen in einer Regel können weiter in *Kategorien* unterteilt werden.

Dieses Dokument erläutert, wie eine Datei in einem festgelegten Verzeichnis erstellt wird, die Eigenschaften für Ihr benutzerdefiniertes Tool enthält, so dass die Eigenschaften beim Starten von Visual Studio geladen werden. Informationen zum Ändern der Datei finden Sie unter [Platform Extensibility Part 2](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/) (Plattformerweiterbarkeit Teil 2) im Visual Studio Project-Teamblog.

### <a name="to-add-or-change-project-properties"></a>Hinzufügen oder Ändern von Projekteigenschaften

1. Erstellen Sie im XML-Editor eine XML-Datei.

1. Speichern Sie die Datei im Visual Studio-Ordner `VCTargets\1033`. Für jede installierte Edition von Visual Studio und jede Sprache gibt es einen anderen Pfad. Beispielsweise ist der standardmäßige Ordnerpfad für Visual Studio 2019 Community Edition in englischer Sprache `C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\VC\VCTargets`. Passen Sie den Pfad für Ihre Sprache und Visual Studio-Edition an. Jede Regel im Fenster **Eigenschaftenseiten** wird durch eine XML-Datei in diesem Ordner dargestellt. Achten Sie darauf, dass die Datei im Ordner eindeutig benannt ist.

1. Kopieren Sie den Inhalt von `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml` (oder was auch immer Ihr Pfad ist), schließen Sie, ohne die Änderungen zu speichern, und fügen Sie dann den Inhalt in Ihre neue XML-Datei ein. Sie können eine beliebige XML-Schemadatei verwenden – diese ist nur eine, die verwendet werden kann, damit Sie mit einer Vorlage starten können.

1. Ändern Sie in der neuen XML-Datei die Inhalte nach Ihren Anforderungen. Achten Sie darauf, den **Rule Name** (Regelname) und **Rule.DisplayName** (Regel.Anzeigename) oben in der Datei zu ändern.

1. Speichern Sie die Änderungen, und schließen Sie die Datei.

1. Die XML-Dateien in `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>` (oder wo auch immer Sie sie gespeichert haben) werden beim Starten von Visual Studio geladen. Um die neue Datei zu testen, führen Sie daher einen Neustart von Visual Studio aus.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf ein Projekt, und klicken Sie dann auf **Eigenschaften**. Überprüfen Sie im Fenster **Eigenschaftenseiten** im linken Bereich, ob ein neuer Knoten mit dem Namen Ihrer Regel vorhanden ist.

## <a name="see-also"></a>Siehe auch

[MSBuild on the Command Line – C++ (C++: MSBuild in der Befehlszeile)](msbuild-visual-cpp.md)

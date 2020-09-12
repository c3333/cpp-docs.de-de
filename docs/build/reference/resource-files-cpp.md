---
title: Projektressourcen Dateien (C++)
ms.date: 05/14/2019
helpviewer_keywords:
- resource files
- resources [C++]
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
ms.openlocfilehash: d37c3602d8939db609fc8af42dd764655195b24b
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041015"
---
# <a name="project-resource-files-c"></a>Projektressourcen Dateien (C++)

Ressourcen sind Schnittstellenelemente, die dem Benutzer Informationen bereitstellen. Bitmaps, Symbole, Symbolleisten und Cursor sind Ressourcen. Einige Ressourcen können eine Aktion ausführen, etwa Auswählen aus einem Menü oder Eingeben von Daten in einem Dialogfeld.

Weitere Informationen finden Sie unter [Arbeiten mit Ressourcen](../../windows/working-with-resource-files.md).

|Dateiname|Speicherort für das Verzeichnis|Speicherort für den Projektmappen-Explorer|BESCHREIBUNG|
|---------------|------------------------|--------------------------------|-----------------|
|*Projname*.rc|*Projektname*|Quelldateien|Die Ressourcenskriptdatei für das Projekt. Die Ressourcenskriptdatei enthält abhängig von der Art des Projekts und der ausgewählten Unterstützung für das Projekt (z.B. Symbolleisten, Dialogfelder oder HTML) Folgendes:<br /><br />– Standardmenüdefinition<br />– Tastenkombinations- und Zeichenfolgentabellen<br />– Standarddialogfeld **Info**<br />– Weitere Dialogfelder<br />– Symboldatei (res\\*Projname*.ico)<br />– Versionsinformationen<br />– Bitmaps<br />– Symbolleiste<br />– HTML-Dateien<br /><br /> Die Ressourcendatei enthält die Datei „Afxres.rc“ für MFC-Standardressourcen.|
|Resource.h|*Projektname*|Headerdateien|Die Headerdatei für Ressourcen, die Definitionen für die vom Projekt verwendeten Ressourcen enthält.|
|*Projname*.rc2|*Projname*\res|Quelldateien|Die Skriptdatei, die zusätzliche vom Projekt verwendete Ressourcen enthält. Sie können die RC2-Datei unter der RC-Datei des Projekts einfügen.<br /><br /> Eine RC2-Datei ist nützlich, um Ressourcen einzufügen, die von mehreren verschiedenen Projekten verwendet werden. Anstatt die gleichen Ressourcen mehrmals für verschiedene Projekte zu erstellen, können Sie sie in eine RC2-Datei einfügen und diese dann in die RC-Hauptdatei einfügen.|
|*Projname*.def|*Projektname*|Quelldateien|Die Moduldefinitionsdatei für ein DLL-Projekt. Sie stellt einem Steuerelement den Namen und die Beschreibung des Steuerelements bereit. Außerdem gibt Sie die Größe des Heaps der Runtime an.|
|*Projname*.ico|*Projname*\res|Ressourcendateien|Die Symboldatei für das Projekt oder Steuerelement. Dieses Symbol wird angezeigt, wenn die Anwendung minimiert wird. Es wird in der Anwendung auch im Feld **Info** verwendet. MFC stellt standardmäßig das MFC-Symbol bereit, und ATL stellt das ATL-Symbol bereit.|
|*Projname*Doc.ico|*Projname*\res|Ressourcendateien|Die Symboldatei für ein MFC-Projekt, das Unterstützung für die Dokument- oder Ansichtsarchitektur enthält.|
|Toolbar.bmp|*Projname*\res|Ressourcendateien|Die Bitmapdatei, die die Anwendung oder das Steuerelement in einer Symbolleiste oder Palette darstellt. Diese Bitmap ist in der Ressourcendatei des Projekts enthalten. Die erste Symbolleiste und Statusleiste werden in der Klasse **CMainFrame** erstellt.|
|ribbon.mfcribbon-ms|*Projname*\res|Ressourcendateien|Die Ressourcendatei, die den XML-Code enthält, der die Schaltflächen, Steuerelemente und Attribute im Menüband definiert. Weitere Informationen finden Sie unter [Ribbon Designer (MFC)](../../mfc/ribbon-designer-mfc.md).|

## <a name="see-also"></a>Weitere Informationen

[Für Visual Studio C++-Projekte erstellte Dateitypen](file-types-created-for-visual-cpp-projects.md)

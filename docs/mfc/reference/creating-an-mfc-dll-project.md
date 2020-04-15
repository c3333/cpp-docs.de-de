---
title: Erstellen eines MFC-DLL-Projekts
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.mfcdll.project
helpviewer_keywords:
- MFC DLLs [MFC], creating projects
- DLLs [MFC], MFC
- projects [MFC], creating
- DLLs [MFC], creating
ms.assetid: 05540b93-4781-4a90-aadf-55158313f5b2
ms.openlocfilehash: 6367b2a4b85b2c586c5a4420a8be1f80d334b2e4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363960"
---
# <a name="creating-an-mfc-dll-project"></a>Erstellen eines MFC-DLL-Projekts

Eine MFC-DLL ist eine Binärdatei und fungiert als gemeinsam genutzte Funktionsbibliothek, die von mehreren Anwendungen gleichzeitig verwendet werden kann. Am einfachsten erstellen Sie ein MFC-DLL-Projekt mit dem MFC-DLL-Assistenten.

> [!NOTE]
> Die in der IDE dargestellten Features können sich je nach den aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen Features unterscheiden. Um Ihre Einstellungen zu ändern, wählen Sie **Einstellungen importieren und exportieren** im Menü **Extras** aus. Weitere Informationen finden Sie unter [Personalisieren der Visual Studio-IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-create-an-mfc-dll-project-using-the-mfc-dll-wizard"></a>So erstellen Sie ein MFC-DLL-Projekt mit dem MFC-DLL-Assistenten

1. Folgen Sie den Anweisungen im Hilfethema [Erstellen einer MFC-Anwendung,](creating-an-mfc-application.md) wählen Sie jedoch **MFC Dynamic Link Library** oder **MFC DLL** aus der Liste der verfügbaren Vorlagen aus.

1. Definieren Sie Ihre Anwendungseinstellungen mithilfe der Seite mit den [Anwendungseinstellungen](../../mfc/reference/application-settings-mfc-dll-wizard.md) des [MFC-DLL-Assistenten](../../mfc/reference/mfc-dll-wizard.md).

    > [!NOTE]
    >  Überspringen Sie diesen Schritt, um die Standardeinstellungen des Assistenten beizubehalten.

1. Klicken Sie auf **Fertig stellen,** um den Assistenten zu schließen und das neue Projekt im **Projektmappen-Explorer**zu öffnen.

Nachdem das Projekt erstellt wurde, können Sie die generierten Dateien im **Projektmappen-Explorer** anzeigen lassen. Weitere Informationen zu den vom Assistenten erstellten Dateien im Projekt finden Sie in der projekteigenen Datei "Readme.txt". Weitere Informationen zu den Dateitypen finden Sie unter [Für Visual Studio C++-Projekte erstellte Dateitypen](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Siehe auch

[C++-Projektvorlagen](/visualstudio/debugger/debugging-preparation-visual-cpp-project-types)<br/>
[Adding Functionality with Code Wizards (Hinzufügen neuer Funktionen mit Code-Assistenten)](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Eigenschaftenseiten](../../build/reference/property-pages-visual-cpp.md)

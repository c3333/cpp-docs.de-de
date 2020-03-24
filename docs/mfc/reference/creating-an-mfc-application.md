---
title: Erstellen einer MFC-Anwendung
ms.date: 08/28/2019
helpviewer_keywords:
- applications [MFC]
- MFC, creating applications
- MFC applications
ms.assetid: b8b8aa08-9c49-404c-8078-b42079ac18f0
ms.openlocfilehash: f0d0287c9914bbefc2c5659e5f5d4386ab566c1a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215136"
---
# <a name="creating-an-mfc-application"></a>Erstellen einer MFC-Anwendung

Eine MFC-Anwendung ist eine ausführbare Anwendung für Windows, die auf der Microsoft Foundation Class (MFC)-Bibliothek basiert. Ausführbare MFC-Dateien werden im Allgemeinen in fünf Typen unterteilt: standardmäßige Windows-Anwendungen, Dialogfelder, Formular basierte Anwendungen, Explorer-Anwendungen und Webbrowser-Anwendungen. Weitere Informationen finden Sie unter

- [Verwenden der Klassen zum Schreiben von Windows-Anwendungen](../../mfc/using-the-classes-to-write-applications-for-windows.md)

- [Erstellen und Anzeigen von Dialogfeldern](../../mfc/creating-and-displaying-dialog-boxes.md)

- [Erstellen einer formularbasierten MFC-Anwendung](../../mfc/reference/creating-a-forms-based-mfc-application.md)

- [Erstellen einer MFC-Anwendung im Stil des Datei-Explorers](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)

- [Erstellen einer MFC-Anwendung im Webbrowserstil](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)

Abhängig von den im Assistenten ausgewählten Optionen erstellt der MFC-Anwendungs-Assistent die geeigneten Klassen und Dateien für diese Anwendungstypen.

Die einfachste Möglichkeit zum Erstellen einer MFC-Anwendung ist die Verwendung des MFC-Anwendungs-Assistenten (**MFC-App-Projekt** in Visual Studio 2019). Verwenden Sie zum Erstellen einer MFC-Konsolenanwendung (ein Befehlszeilenprogramm, das MFC-Bibliotheken verwendet, aber im Konsolenfenster ausgeführt wird) den Windows-Desktop-Assistenten, und wählen Sie die Optionen **Konsolenanwendung** und **MFC-Header** aus.

::: moniker range=">=vs-2019"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>So erstellen Sie eine MFC-Formular-oder-Dialogfeld basierte Anwendung

1. Wählen Sie im Hauptmenü **Datei** > **neue** > **Projekt**aus.
1. Geben Sie "MFC" in das Suchfeld ein, und wählen Sie dann in der Ergebnisliste die Option **MFC-App** aus.
1. Ändern Sie die Standardwerte nach Bedarf, **und drücken** Sie dann die Taste zum Öffnen des **MFC-Anwendungs-Assistenten**.
1. Ändern Sie die Konfigurationswerte nach Bedarf, und klicken Sie dann auf **Fertig**stellen.

Weitere Informationen finden Sie unter [Erstellen einer Formular basierten MFC-Anwendung](creating-a-forms-based-mfc-application.md).

![MFC-Anwendungs-Assistent](media/mfc-app-wizard.png)

## <a name="to-create-an-mfc-console-application"></a>So erstellen Sie eine MFC-Konsolenanwendung

Bei einer MFC-Konsolenanwendung handelt es sich um ein Befehlszeilenprogramm, das MFC-Bibliotheken verwendet, aber im Konsolenfenster ausgeführt wird.

1. Wählen Sie im Hauptmenü **Datei** > **neue** > **Projekt**aus.
1. Geben Sie "Desktop" in das Suchfeld ein, und wählen Sie dann in der Ergebnisliste den **Windows-Desktop-Assistenten** aus.
1. Ändern Sie den Projektnamen nach Bedarf, und klicken Sie auf **weiter** , um den **Windows-Desktop-Assistenten**zu öffnen.
1. Aktivieren Sie das Feld **MFC-Header** , und legen Sie bei Bedarf weitere Werte **fest.**

![MFC-Anwendungs-Assistent](media/windows-desktop-wizard.png)

::: moniker-end

::: moniker range="=vs-2017"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>So erstellen Sie eine MFC-Formular-oder-Dialogfeld basierte Anwendung

1. Wählen Sie im Hauptmenü **Datei** > **neue** > **Projekt**aus.
1. Wählen Sie unter **installierte** Vorlagen die **Option C++ Visual** > **MFC/ATL**aus. Wenn diese nicht angezeigt werden, verwenden Sie die Visual Studio-Installer, um Sie hinzuzufügen.
1. Wählen Sie im mittleren Bereich die Option **MFC-Anwendung** aus.
1. Ändern Sie die Konfigurationswerte nach Bedarf, und klicken Sie dann auf **Fertig**stellen.

Weitere Informationen finden Sie unter [Erstellen einer Formular basierten MFC-Anwendung](creating-a-forms-based-mfc-application.md).

![MFC-Anwendungs-Assistent](media/mfc-app-wizard.png)

## <a name="to-create-an-mfc-console-application"></a>So erstellen Sie eine MFC-Konsolenanwendung

Bei einer MFC-Konsolenanwendung handelt es sich um ein Befehlszeilenprogramm, das MFC-Bibliotheken verwendet, aber im Konsolenfenster ausgeführt wird.

1. Wählen Sie im Hauptmenü **Datei** > **neue** > **Projekt**aus.
1. Wählen Sie unter **installierte** Vorlagen die **Option C++ Visual** > **Windows-Desktop**aus.
1. Wählen Sie im mittleren Bereich **Windows-Desktop-Assistent** aus.
1. Ändern Sie den Projektnamen nach Bedarf, und klicken Sie auf **OK** , um den **Windows-Desktop-Assistenten**zu öffnen.
1. Aktivieren Sie das Feld **MFC-Header** , und legen Sie bei Bedarf weitere Werte **fest.**

![MFC-Anwendungs-Assistent](media/windows-desktop-wizard-2017.png)

::: moniker-end

::: moniker range="=vs-2015"

## <a name="to-create-an-mfc-forms-or-dialog-based-application"></a>So erstellen Sie eine MFC-Formular-oder-Dialogfeld basierte Anwendung

1. Wählen Sie im Hauptmenü **Datei** > **neue** > **Projekt**aus.
1. Wählen Sie unter **installierte** Vorlagen die **Option C++ Visual** > **MFC**aus.
1. Wählen Sie im mittleren Bereich die Option **MFC-Anwendung** aus.
1. Klicken Sie auf **weiter** , um den **MFC-Anwendungs Assistenten**zu starten.

Weitere Informationen finden Sie unter [Erstellen einer Formular basierten MFC-Anwendung](creating-a-forms-based-mfc-application.md).

![MFC-Anwendungs-Assistent](media/mfc-app-wizard-2015.png)

## <a name="to-create-an-mfc-console-application"></a>So erstellen Sie eine MFC-Konsolenanwendung

Bei einer MFC-Konsolenanwendung handelt es sich um ein Befehlszeilenprogramm, das MFC-Bibliotheken verwendet, aber im Konsolenfenster ausgeführt wird.

1. Wählen Sie im Hauptmenü **Datei** > **neue** > **Projekt**aus.
1. Wählen Sie unter **installierte** Vorlagen die **Option C++ Visual** > **Win32**aus.
1. Wählen Sie im mittleren Bereich **Win32-Konsolenanwendung** aus.
1. Ändern Sie den Projektnamen nach Bedarf, und klicken Sie dann auf **OK**.
1. Aktivieren Sie auf der zweiten Seite des Assistenten das Kontrollkästchen **allgemeine Header für MFC hinzufügen** , und legen Sie bei Bedarf weitere Werte fest. Drücken Sie anschließend die Option **Fertig**stellen.

::: moniker-end

Nachdem das Projekt erstellt wurde, können Sie die generierten Dateien im **Projektmappen-Explorer** anzeigen lassen. Weitere Informationen zu den vom Assistenten erstellten Dateien im Projekt finden Sie in der projekteigenen Datei "Readme.txt". Weitere Informationen zu den Dateitypen finden Sie unter [Für Visual Studio C++-Projekte erstellte Dateitypen](../../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Weitere Informationen

[Hinzufügen neuer Funktionen mit Code-Assistenten](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Eigenschaftenseiten](../../build/reference/property-pages-visual-cpp.md)

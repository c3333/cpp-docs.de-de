---
title: 'Exemplarische Vorgehensweise: Bereitstellen des Programms (C++)'
ms.date: 05/14/2019
helpviewer_keywords:
- deploying applications [C++], walkthroughs
- setup projects [C++]
- program deployments [C++]
- projects [C++], setup
- projects [C++], deploying programs
- application deployment [C++], walkthroughs
ms.assetid: 79e6cc4e-dced-419d-aaf7-d62d1367603f
ms.openlocfilehash: eacbcef82f240589e71b59f80d8e19602ceda869
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365009"
---
# <a name="walkthrough-deploying-your-program-c"></a>Exemplarische Vorgehensweise: Bereitstellen des Programms (C++)

Nachdem Sie die Anwendung erstellt haben, indem Sie die früheren exemplarischen Vorgehensweisen dazu vorgenommen haben, besteht der letzte Schritt in der Erstellung eines Installationsprogramms, damit andere Benutzer das Programm auf ihren Computern installieren können. Für den Installer fügen Sie der vorhandenen Projektmappe ein neues Projekt hinzu. Die Ausgabe dieses neuen Projekts ist eine setup.exe-Datei , mit der die Anwendung auf einem anderen Computer installiert wird.

In dieser exemplarischen Vorgehensweise wird der Windows Installer zum Bereitstellen der Anwendung verwendet. Sie können auch ClickOnce verwenden, um eine Anwendung bereitzustellen. Weitere Informationen finden Sie unter [ClickOnce Deployment for Visual C++ Applications](../windows/clickonce-deployment-for-visual-cpp-applications.md). Weitere Informationen über die allgemeine Bereitstellung finden Sie unter [Deploying Applications, Services, and Components (Bereitstellen von Anwendungen, Diensten und Komponenten)](/visualstudio/deployment/deploying-applications-services-and-components).

## <a name="prerequisites"></a>Voraussetzungen

- In dieser exemplarischen Vorgehensweise wird davon ausgegangen, dass Sie die Grundlagen der Programmiersprache C++ beherrschen.

- Es wird ebenfalls davon ausgegangen, dass Sie die früheren exemplarischen Vorgehensweisen abgeschlossen haben, die unter [Verwenden der Visual Studio-IDE für die C++-Desktopentwicklung](using-the-visual-studio-ide-for-cpp-desktop-development.md) aufgeführt sind.

- Diese exemplarische Vorgehensweise kann nicht in den Express-Editionen von Visual Studio ausgeführt werden.

## <a name="install-the-visual-studio-setup-and-deployment-project-template"></a>Installieren der Setup- und Bereitstellungsprojektvorlage für Visual Studio

Die Schritte in diesem Abschnitt variieren, je nachdem, welche Version von Visual Studio installiert ist. Verwenden Sie das Versionsauswahlsteuerelement, um die **Version** Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

<!-- markdownlint-disable MD034 -->

::: moniker range="vs-2019"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2019"></a>Installieren der Setup- und Bereitstellungsprojektvorlage für Visual Studio 2019

1. Wenn Sie dies noch nicht getan haben, laden Sie die Erweiterung Microsoft Visual Studio Installer Projects herunter. Die Erweiterung ist für Visual Studio-Entwickler kostenlos und fügt Visual Studio die Funktionen der Projektvorlagen für Setup und Bereitstellung hinzu. Wenn Sie mit dem Internet verbunden sind, wählen Sie in Visual Studio **Erweiterungen** > Verwalten von**Erweiterungen**aus. Wählen Sie im Dialogfeld **Erweiterungen und Updates** die Registerkarte **Online** aus, und geben Sie *Microsoft Visual Studio-Installerprojekte* in das Suchfeld ein. Drücken Sie die **EINGABETASTE**, wählen Sie **Microsoft Visual Studio \<Version > Installerprojekte** aus, und klicken Sie auf **Herunterladen**. Wählen Sie die Ausführung und Installation der Erweiterung aus, und starten Sie Visual Studio neu.

1. Klicken Sie in der Menüleiste in Visual Studio auf **Datei** > ** Zuletzt geöffnete Projekte und Projektmappen**, und öffnen Sie Ihr Projekt dann wieder.

1. Wählen Sie in der Menüleiste **Datei** > **neues** > **Projekt** aus, um das Dialogfeld Neues **Projekt erstellen** zu öffnen. Geben Sie im Suchfeld „Setup“ ein, und wählen Sie aus der Ergebnisliste die Option **Setup-Projekt** aus.

1. Geben Sie im Feld **Name** einen Namen für das Setup-Projekt ein. Wählen Sie in der Dropdownliste **Projektmappe** die Option **Zu Projektmappe hinzufügen** aus. Klicken Sie auf die Schaltfläche **OK**, um das Setup-Projekt zu erstellen. Eine Registerkarte **Datei-Assistent (ProjektName)** wird im Editor-Fenster geöffnet.

1. Klicken Sie mit der rechten Maustaste auf den Knoten **Anwendungsordner**, und wählen Sie **Hinzufügen** > **Projektausgabe** aus, um das Dialogfeld **Projektausgabegruppe hinzufügen** zu öffnen.

1. Wählen Sie im Dialogfeld **Primäre Ausgabe** aus, und klicken Sie dann auf **OK**. Ein neues Element mit dem Namen **Primäre Ausgabe aus Game (aktiv)** wird angezeigt.

1. Wählen Sie das Element **Primäre Ausgabe aus Game (aktiv)** aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Verknüpfung mit primärer Ausgabe aus Game (aktiv) erstellen** aus. Ein neues Element mit dem Namen **Verknüpfung mit primärer Ausgabe aus Game (aktiv)** wird angezeigt.

1. Benennen Sie das Verknüpfungselement in *Game* um, und legen Si es im Knoten **Menü Benutzerprogramme** auf der linken Seite des Fensters ab.

1. Wählen Sie im **Projektmappen-Explorer** das Projekt **Game Installer** aus, und wählen Sie **Ansicht** > **Eigenschaftenfenster** aus, oder drücken Sie **F4**, um das Fenster **Eigenschaften** zu öffnen.

1. Geben Sie zusätzliche Details an, die im Installer angezeigt werden sollen.  Verwenden Sie beispielsweise *Contoso* for **Manufacturer**, *Game Installer* for **Product Name**und https *\:/www.contoso.com* für **SupportUrl**.

1. Wählen Sie in der Menüleiste **Build** > **Configuration Manager**aus. Aktivieren Sie in der Tabelle **Projekt** unter der Spalte **Erstellen** das Kontrollkästchen für **Game Installer**. Klicken Sie auf **Schließen**.

1. Klicken Sie in der Menüleiste auf **Erstellen** > **Projektmappe erstellen**, um das Game-Projekt und das Game Installer-Projekt zu erstellen.

1. Suchen Sie im Projektmappenordner das setup.exe-Programm, das mit dem Game Installer-Projekt erstellt wurde, und führen Sie es dann zum Installieren der Spielanwendung auf dem Computer aus. Sie können diese Datei (und die Datei „GameInstaller.msi“) kopieren, um die Anwendung und die erforderlichen Bibliotheksdateien auf einem anderen Computer zu installieren.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-install-the-setup-and-deployment-project-template-for-visual-studio-2017-and-earlier"></a>Installieren der Setup- und Bereitstellungsprojektvorlage für Visual Studio 2017 und ältere Versionen

1. Wenn Sie mit dem Internet verbunden sind, wählen Sie in Visual Studio **Extras** > **Erweiterungen und Updates** aus.

1. Wählen Sie unter **Erweiterungen und Updates** die Registerkarte **Online** aus, und geben Sie *Microsoft Visual Studio-Installerprojekte* in das Suchfeld ein. Drücken Sie die **EINGABETASTE**, wählen Sie **Microsoft Visual Studio \<Version > Installerprojekte** aus, und klicken Sie auf **Herunterladen**.

1. Wählen Sie die Installation der Erweiterung aus, und starten Sie Visual Studio neu.

1. Klicken Sie in der Menüleiste auf **Datei** > **Zuletzt geöffnete Projekte und Projektmappen**, und wählen Sie dann Sie Projektmappe **Game** aus, um sie erneut zu öffnen.

### <a name="to-create-a-setup-project-and-install-your-program"></a>So erstellen Sie ein Setupprojekt und installieren das Programm

1. Ändern Sie die aktive Lösungskonfiguration in Release. Wählen Sie in der Menüleiste **Build** > **Configuration Manager**aus. Wählen Sie **Release** in der Dropdownliste **Konfiguration der aktuellen Projektmappe** im Dialogfeld **Konfigurations-Manager** aus. Klicken Sie auf die Schaltfläche **Schließen**, um die Konfiguration zu speichern.

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**, um das Dialogfeld **Neues Projekt** zu öffnen.

1. Erweitern Sie im linken Bereich des Dialogfelds die Knoten **Installierte** > **andere Projekttypen,** und wählen Sie dann **Visual Studio Installer aus.** Wählen Sie im mittleren Bereich die Option **Setupprojekt** aus.

1. Geben Sie im Feld **Name** einen Namen für das Setup-Projekt ein. Geben Sie im Rahmen dieses Beispiels *Game Installer* ein. Wählen Sie in der Dropdownliste **Projektmappe** die Option **Zu Projektmappe hinzufügen** aus. Klicken Sie auf die Schaltfläche **OK**, um das Setup-Projekt zu erstellen. Eine Registerkarte **Datei-Assistent (Game Installer)** wird im Editor-Fenster geöffnet.

1. Klicken Sie mit der rechten Maustaste auf den Knoten **Anwendungsordner**, und wählen Sie **Hinzufügen** > **Projektausgabe** aus, um das Dialogfeld **Projektausgabegruppe hinzufügen** zu öffnen.

1. Wählen Sie im Dialogfeld **Primäre Ausgabe** aus, und klicken Sie dann auf **OK**. Ein neues Element mit dem Namen **Primäre Ausgabe aus Game (aktiv)** wird angezeigt.

1. Wählen Sie das Element **Primäre Ausgabe aus Game (aktiv)** aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Verknüpfung mit primärer Ausgabe aus Game (aktiv) erstellen** aus. Ein neues Element mit dem Namen **Verknüpfung mit primärer Ausgabe aus Game (aktiv)** wird angezeigt.

1. Benennen Sie das Verknüpfungselement in *Game* um, und legen Si es im Knoten **Menü Benutzerprogramme** auf der linken Seite des Fensters ab.

1. Wählen Sie im **Projektmappen-Explorer** das Projekt **Game Installer** aus, und wählen Sie **Ansicht** > **Eigenschaftenfenster** aus, oder drücken Sie **F4**, um das Fenster **Eigenschaften** zu öffnen.

1. Geben Sie zusätzliche Details an, die im Installer angezeigt werden sollen.  Verwenden Sie beispielsweise *Contoso* for **Manufacturer**, *Game Installer* for **Product Name**und https *\:/www.contoso.com* für **SupportUrl**.

1. Wählen Sie in der Menüleiste **Build** > **Configuration Manager**aus. Aktivieren Sie in der Tabelle **Projekt** unter der Spalte **Erstellen** das Kontrollkästchen für **Game Installer**. Klicken Sie auf **Schließen**.

1. Klicken Sie in der Menüleiste auf **Erstellen** > **Projektmappe erstellen**, um das Game-Projekt und das Game Installer-Projekt zu erstellen.

1. Suchen Sie im Projektmappenordner das setup.exe-Programm, das mit dem Game Installer-Projekt erstellt wurde, und führen Sie es dann zum Installieren der Spielanwendung auf dem Computer aus. Sie können diese Datei (und die Datei „GameInstaller.msi“) kopieren, um die Anwendung und die erforderlichen Bibliotheksdateien auf einem anderen Computer zu installieren.

::: moniker-end

## <a name="next-steps"></a>Nächste Schritte

**Zurück:** [Exemplarische Vorgehensweise: Debuggen eines Projekts (C++)](walkthrough-debugging-a-project-cpp.md)

## <a name="see-also"></a>Siehe auch

[C++-Sprachreferenz](../cpp/cpp-language-reference.md)<br/>
[Projekte und Buildsysteme](../build/projects-and-build-systems-cpp.md)<br/>
[Deploying Desktop Applications (Bereitstellen von Desktopanwendungen)](../windows/deploying-native-desktop-applications-visual-cpp.md)<br/>

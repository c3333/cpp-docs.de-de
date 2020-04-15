---
title: Bereitstellen einer Visual C++-Anwendung mithilfe eines Setup-Projekts
ms.date: 04/25/2019
helpviewer_keywords:
- deployment for Visual C++
ms.assetid: 66735cda-8fe3-4211-a19a-2cf717a12a3f
ms.openlocfilehash: 8a1242140154c5a0123d71b83983fae20cab5d7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374365"
---
# <a name="walkthrough-deploying-a-visual-c-application-by-using-a-setup-project"></a>Exemplarische Vorgehensweise: Bereitstellen einer Visual C++-Anwendung mithilfe eines Setup-Projekts

In diesem Artikel wird beschrieben, wie Sie ein Setup-Projekt verwenden, um eine Visual C++-Anwendung bereitzustellen.

## <a name="prerequisites"></a>Voraussetzungen

Zum Abschließen dieser exemplarischen Vorgehensweise benötigen Sie Folgendes:

- Einen Computer, auf dem Visual Studio installiert ist.

- Einen zusätzlichen Computer, auf dem keine Visual C++-Bibliotheken vorhanden sind.

## <a name="create-the-setup-project"></a>Erstellen des Setupprojekts

Die Anweisungen zum Erstellen eines Setupprojekts hängen davon ab, welche Version von Visual Studio Sie installiert haben. Verwenden Sie das Versionsauswahlsteuerelement, um die **Version** Dokumentation für Ihre bevorzugte Version von Visual Studio anzuzeigen. Es befindet sich oben im Inhaltsverzeichnis auf dieser Seite.

::: moniker range="=vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>So erstellen Sie das Projekt in Visual Studio 2019

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**, um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

   ![MFC-App-Projekt](media/vs2019-mfc-app-new-project.png "Neue MFC-App")

1. Geben Sie `MFC` oben im Dialogfeld das Suchfeld ein, und wählen Sie dann **MFC App** aus der Ergebnisliste aus. Wenn sie nicht angezeigt wird, müssen Sie das Visual Studio Installer-Programm über das Windows-Startmenü starten und auf die **Arbeitsauslastungskachel C++ Desktop Development** klicken. Stellen Sie unter **Einzelkomponenten**sicher, dass die MFC-Komponente überprüft wird.

1. Geben Sie auf der nächsten Seite einen Namen für das Projekt ein, und geben Sie ggf. den Projektspeicherort an.

1. Klicken Sie auf die Schaltfläche **Erstellen**, um das Clientprojekt zu erstellen. Wenn der **MFC-Anwendungs-Assistent** angezeigt wird, akzeptieren Sie alle Standardeinstellungen.

1. Ändern Sie die aktive Lösungskonfiguration in **Release**. Klicken Sie im Menü **Build** auf **Konfigurations-Manager**. Wählen Sie im Dialogfeld **Konfigurations-Manager** im Dropdownfeld **Aktive Projektmappenkonfiguration** die Option **Release** aus. Klicken Sie auf **Schließen**.

1. Drücken Sie **Strg-Umschalttaste**+**Shift**+**B,** um die Anwendung zu erstellen. Oder klicken Sie im Menü **Build** auf **Projektmappe erstellen**. Das Erstellen der Anwendung ermöglicht es dem Setupprojekt, die Ausgabe dieses MFC-Anwendungsprojekts zu verwenden.

1. Wenn Sie dies noch nicht getan haben, laden Sie die Erweiterung Microsoft Visual Studio Installer Projects herunter. Die Erweiterung ist für Visual Studio-Entwickler kostenlos und fügt Visual Studio die Funktionen der Projektvorlagen für Setup und Bereitstellung hinzu. Wenn Sie mit dem Internet verbunden sind, wählen Sie in Visual Studio **Erweiterungen** > Verwalten von**Erweiterungen**aus. Wählen Sie im Dialogfeld **Erweiterungen und Updates** die Registerkarte **Online** aus, und geben Sie *Microsoft Visual Studio-Installerprojekte* in das Suchfeld ein. Drücken **Sie Enter**, wählen Sie Microsoft Visual ** \<Studio-Version> Installer-Projekte**aus, und klicken Sie auf **Herunterladen**. Wählen Sie die Ausführung und Installation der Erweiterung aus, und starten Sie Visual Studio neu.

   ![Visual Studio-Setupprojekt](media/vs2019-extension-dialog-installer-project.png "Benennen des Clientprojekts")

1. Klicken Sie in der Menüleiste in Visual Studio auf **Datei** > ** Zuletzt geöffnete Projekte und Projektmappen**, und öffnen Sie Ihr Projekt dann wieder.

1. Wählen Sie in der Menüleiste **Datei** > **neues** > **Projekt** aus, um das Dialogfeld Neues **Projekt erstellen** zu öffnen. Geben Sie im Suchfeld „Setup“ ein, und wählen Sie aus der Ergebnisliste die Option **Setup-Projekt** aus.

1. Geben Sie im Feld **Name** einen Namen für das Setup-Projekt ein. Wählen Sie in der Dropdownliste **Projektmappe** die Option **Zu Projektmappe hinzufügen** aus. Klicken Sie auf die Schaltfläche **OK**, um das Setup-Projekt zu erstellen. Eine Registerkarte **Datei-Assistent (ProjektName)** wird im Editor-Fenster geöffnet.

::: moniker-end

::: moniker range="=vs-2017"

### <a name="to-create-the-project-in-visual-studio-2017"></a>So erstellen Sie das Projekt in Visual Studio 2017

1. Erstellen Sie ein neues Projekt. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

1. Verwenden Sie den **MFC-Anwendungs-Assistenten,** um eine neue Visual Studio-Lösung zu erstellen. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual C++**, klicken Sie auf **MFC** und dann auf **MFC-Anwendung**, geben Sie dann einen Namen für das Projekt ein, und klicken Sie auf **OK**, um den Assistenten zu finden. Klicken Sie auf **Fertig stellen**.

   > [!NOTE]
   > Wenn der **MFC-Anwendungstyp** fehlt, wählen Sie **Visual Studio Installer** im linken Bereich des Dialogfelds Neues **Projekt** öffnen aus. Installieren Sie die Option unter **Desktopentwicklung mit C++** im Abschnitt **Optionale Komponenten** mit dem Namen **Visual C++ MFC für x86 und x64**.

1. Ändern Sie die aktive Lösungskonfiguration in **Release**. Klicken Sie im Menü **Build** auf **Konfigurations-Manager**. Wählen Sie im Dialogfeld **Konfigurations-Manager** im Dropdownfeld **Aktive Projektmappenkonfiguration** die Option **Release** aus. Klicken Sie auf **Schließen**.

1. Drücken Sie **Strg-Umschalttaste**+**Shift**+**B,** um die Anwendung zu erstellen. Oder klicken Sie im Menü **Build** auf **Projektmappe erstellen**. Das Erstellen der Anwendung ermöglicht es dem Setupprojekt, die Ausgabe dieses MFC-Anwendungsprojekts zu verwenden.

1. Wenn Sie dies noch nicht getan haben, laden Sie die Erweiterung Microsoft Visual Studio Installer Projects herunter. Die Erweiterung ist für Visual Studio-Entwickler kostenlos und fügt Visual Studio die Funktionen der Projektvorlagen für Setup und Bereitstellung hinzu. Wenn Sie mit dem Internet verbunden sind, wählen Sie in Visual Studio > **Tools-Erweiterungen und Updates**aus. **Tools** Wählen Sie im Dialogfeld **Erweiterungen und Updates** die Registerkarte **Online** aus, und geben Sie *Microsoft Visual Studio-Installerprojekte* in das Suchfeld ein. Drücken **Sie Enter**, wählen Sie Microsoft Visual ** \<Studio-Version> Installer-Projekte**aus, und klicken Sie auf **Herunterladen**. Wählen Sie die Ausführung und Installation der Erweiterung aus, und starten Sie Visual Studio neu.

1. Klicken Sie in der Menüleiste auf **Datei** > ** Zuletzt geöffnete Projekte und Projektmappen**, und öffnen Sie Ihr Projekt dann erneut.

1. Wählen Sie in der Menüleiste **Datei** > **neues** > **Projekt** aus, um das Dialogfeld Neues **Projekt** zu öffnen. Erweitern Sie dann im linken Bereich des Dialogfelds die Knoten **Installierte** > **andere Projekttypen,** und wählen Sie **Visual Studio Installer aus.** Wählen Sie im mittleren Bereich die Option **Setupprojekt** aus.

1. Geben Sie im Feld **Name** einen Namen für das Setup-Projekt ein. Wählen Sie in der Dropdownliste **Projektmappe** die Option **Zu Projektmappe hinzufügen** aus. Klicken Sie auf die Schaltfläche **OK**, um das Setup-Projekt zu erstellen. Eine Registerkarte **Datei-Assistent (ProjektName)** wird im Editor-Fenster geöffnet.

::: moniker-end

::: moniker range="=vs-2015"

### <a name="to-create-the-project-in-visual-studio-2015"></a>So erstellen Sie das Projekt in Visual Studio 2015

1. Erstellen Sie ein neues Projekt. Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.

1. Verwenden Sie den **MFC-Anwendungs-Assistenten,** um eine neue Visual Studio-Lösung zu erstellen. Erweitern Sie im Dialogfeld **Neues Projekt** den Knoten **Visual C++**, klicken Sie auf **MFC** und dann auf **MFC-Anwendung**, geben Sie dann einen Namen für das Projekt ein, und klicken Sie auf **OK**, um den Assistenten zu finden. Klicken Sie auf **Fertig stellen**.

   > [!NOTE]
   > Wenn der **MFC-Anwendungstyp** fehlt, klicken Sie auf die Schaltfläche Windows-Start, und geben Sie **"Programme entfernen" ein.** Öffnen Sie das Programm aus der Ergebnisliste, und suchen Sie dann Ihre Microsoft Visual Studio 2015-Installation in der Liste der installierten Programme. Doppelklicken Sie darauf, und wählen Sie dann **Ändern** und die Komponente **Microsoft Foundation Classes** unter **Visual C++** aus.

1. Ändern Sie die aktive Lösungskonfiguration in **Release**. Wählen Sie im Menü **Build** **Configuration Manager**aus. Wählen Sie im Dialogfeld **Konfigurations-Manager** im Dropdownfeld **Aktive Projektmappenkonfiguration** die Option **Release** aus. Klicken Sie auf **Schließen**.

1. Drücken Sie **Strg-Umschalttaste**+**Shift**+**B,** um die Anwendung zu erstellen. Oder klicken Sie im Menü **Build** auf **Projektmappe erstellen**. Das Erstellen der Anwendung ermöglicht es dem Setupprojekt, die Ausgabe dieses MFC-Anwendungsprojekts zu verwenden.

1. Wenn Sie dies noch nicht getan haben, laden Sie die Erweiterung Microsoft Visual Studio Installer Projects herunter. Die Erweiterung ist für Visual Studio-Entwickler kostenlos und fügt Visual Studio die Funktionen der Projektvorlagen für Setup und Bereitstellung hinzu. Wenn Sie mit dem Internet verbunden sind, wählen Sie in Visual Studio > **Tools-Erweiterungen und Updates**aus. **Tools** Wählen Sie im Dialogfeld **Erweiterungen und Updates** die Registerkarte **Online** aus, und geben Sie *Microsoft Visual Studio-Installerprojekte* in das Suchfeld ein. Drücken **Sie Enter**, wählen Sie Microsoft Visual ** \<Studio-Version> Installer-Projekte**aus, und klicken Sie auf **Herunterladen**. Wählen Sie die Ausführung und Installation der Erweiterung aus, und starten Sie Visual Studio neu.

1. Klicken Sie in der Menüleiste auf **Datei** > ** Zuletzt geöffnete Projekte und Projektmappen**, und öffnen Sie Ihr Projekt dann erneut.

1. Wählen Sie in der Menüleiste **Datei** > **neues** > **Projekt** aus, um das Dialogfeld Neues **Projekt** zu öffnen. Erweitern Sie dann im linken Bereich des Dialogfelds die Knoten **Installierte** > **andere Projekttypen,** und wählen Sie **Visual Studio Installer aus.** Wählen Sie im mittleren Bereich die Option **Setupprojekt** aus.

1. Geben Sie im Feld **Name** einen Namen für das Setup-Projekt ein. Wählen Sie in der Dropdownliste **Projektmappe** die Option **Zu Projektmappe hinzufügen** aus. Klicken Sie auf die Schaltfläche **OK**, um das Setup-Projekt zu erstellen. Eine Registerkarte **Datei-Assistent (ProjektName)** wird im Editor-Fenster geöffnet.

::: moniker-end

## <a name="add-items-to-the-project"></a>Hinzufügen von Elementen zum Projekt

1. Klicken Sie mit der rechten Maustaste auf den Knoten **Anwendungsordner**, und wählen Sie **Hinzufügen** > **Projektausgabe** aus, um das Dialogfeld **Projektausgabegruppe hinzufügen** zu öffnen. Wählen Sie im Dialogfeld **Primäre Ausgabe** aus, und klicken Sie dann auf **OK**. Ein neues Element mit dem Namen **Primäre Ausgabe aus ProjektName (aktiv)** wird angezeigt.

1. Klicken Sie mit der rechten Maustaste auf den Knoten **Anwendungsordner**, und wählen Sie **Hinzufügen** > **Assembly** aus, um das Dialogfeld **Komponente auswählen** zu öffnen. Wählen Sie alle erforderlichen DLLs aus, die das Programm benötigt, und fügen Sie sie hinzu, wie im Artikel [Ermitteln der zu verteilenden DLLs](determining-which-dlls-to-redistribute.md) beschrieben.

1. Wählen Sie das Element **Primäre Ausgabe aus ProjektName (aktiv)** aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Verknüpfung mit primärer Ausgabe aus ProjektName (aktiv) erstellen** aus. Ein neues Element mit dem Namen **Verknüpfung mit primärer Ausgabe aus ProjektName (aktiv)** wird angezeigt. Sie können das Verknüpfungselement umbenennen und dann mithilfe von Drag & Drop in den Knoten **Menü Benutzerprogramme** auf der linken Seite des Fensters ziehen.

1. Wählen Sie in der Menüleiste **Build** > **Configuration Manager**aus. Aktivieren Sie in der Tabelle **Projekt** unter der Spalte **Erstellen** das Kontrollkästchen für das Bereitstellungsprojekt. Klicken Sie auf **Schließen**.

1. Wählen Sie in der Menüleiste > **Buildlösung** erstellen aus, um das MFC-Projekt und das Bereitstellungsprojekt zu erstellen. **Build**

1. Suchen Sie im Projektmappenordner nach dem Programm „setup.exe“, das aus dem Bereitstellungsprojekt erstellt wurde. Sie können diese Datei (und die MSI-Datei) kopieren, um die Anwendung und die erforderlichen Bibliotheksdateien auf einem anderen Computer zu installieren. Führen Sie das Setupprogramm auf einem zweiten Computer aus, der über keine der Visual C++-Bibliotheken verfügt.

## <a name="see-also"></a>Siehe auch

[Bereitstellungsbeispiele](deployment-examples.md)<br/>

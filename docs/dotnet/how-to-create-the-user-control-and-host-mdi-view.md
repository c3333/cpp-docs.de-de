---
title: 'Gewusst wie: Erstellen des Benutzersteuerelements und Hosten der MDI-Ansicht'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: 72501ba32d3b8b9a5c5fd8dd0c56f0628642b147
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374467"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>Gewusst wie: Erstellen des Benutzersteuerelements und Hosten der MDI-Ansicht

In den folgenden Schritten wird das Erstellen eines .NET Framework-Benutzersteuerelements und das Erstellen des Steuerelements in einer Steuerelementklassenbibliothek (speziell in einem Projekt einer Windows-Steuerelementbibliothek) sowie das Kompilieren des Projekts in eine Assembly veranschaulicht. Das Steuerelement kann dann von einer MFC-Anwendung verwendet werden, die Klassen verwendet, die von [CView Class](../mfc/reference/cview-class.md) und [CWinFormsView Class](../mfc/reference/cwinformsview-class.md)abgeleitet sind.

Informationen zum Erstellen eines Windows Forms-Benutzersteuerelements und Erstellen einer Steuerelementklassenbibliothek finden Sie unter [Gewusst wie: Erstellen von Benutzersteuerelementen](/dotnet/framework/winforms/controls/how-to-author-composite-controls).

> [!NOTE]
> In einigen Fällen verhalten sich Windows Forms-Steuerelemente, z. B. ein Datenblattsteuerelement eines Drittanbieters, nicht zuverlässig, wenn sie in einer MFC-Anwendung gehostet werden. Um dies zu umgehen, wird empfohlen, ein Windows Forms-Benutzersteuerelement in der MFC-Anwendung und das Datenblattsteuerelement des Drittanbieters innerhalb des Benutzersteuerelements zu platzieren.

Bei diesem Verfahren wird davon ausgegangen, dass Sie ein Windows Forms Controls Library-Projekt mit dem Namen WindowsFormsControlLibrary1 erstellt haben, wie es in der Prozedur [unter Erstellen der Benutzersteuerung und](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)des Hosts in einem Dialogfeld vorgeht.

### <a name="to-create-the-mfc-host-application"></a>So erstellen Sie die MFC-Hostanwendung

1. Erstellen Sie ein MFC-Anwendungsprojekt.

   Wählen Sie im Menü **Datei** **Neue**aus, und klicken Sie dann auf **Projekt**. Wählen Sie im Ordner **Visual C++** **MFC-Anwendung**aus.

   Geben **Name** Sie im `MFC02` Feld Name die Einstellung **"Lösung"** in **Lösung**hinzufügen ein, und ändern Sie sie in . Klicken Sie auf **OK**.

   Akzeptieren Sie im **MFC-Anwendungs-Assistenten**alle Standardeinstellungen, und klicken Sie dann auf **Fertig stellen**. Dies erstellt eine MFC-Anwendung mit einem MDI (Multiple Document Interface).

1. Konfigurieren Sie das Projekt für Common Language Runtime (CLR)-Unterstützung.

   Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den `MFC01` Projektknoten, und wählen Sie **Eigenschaften** aus dem Kontextmenü aus. Das Dialogfeld **Eigenschaftenseiten** wird angezeigt.

   Wählen Sie unter **Konfigurationseigenschaften**die Option **Allgemein**aus. Legen Sie im Abschnitt **Projektstandard** die **Common Language Runtime-Unterstützung** auf **Common Language Runtime Support (/clr)** fest.

   Erweitern Sie unter **Konfigurationseigenschaften** **C/C++** und klicken Sie auf den Knoten **Allgemein.** Legen Sie **das Debug-Informationsformat** auf **Programmdatenbank (/Zi)** fest.

   Klicken Sie auf den Knoten **Codegenerierung.** Stellen Sie **Minimal Rebuild** auf **No (/Gm-)** ein. Legen Sie außerdem **die Standardlaufzeitprüfungen** auf **Standard**fest.

   Klicken Sie auf **OK,** um Ihre Änderungen anzuwenden.

1. Fügen Sie in *pch.h* (*stdafx.h* in Visual Studio 2017 und früher) die folgende Zeile hinzu:

    ```
    #using <System.Windows.Forms.dll>
    ```

1. Fügen Sie dem .NET-Steuerelement einen Verweis hinzu.

   Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den `MFC02` Projektknoten, und wählen Sie **Hinzufügen**, **Referenzen**. Klicken Sie auf der **Eigenschaftenseite**auf **Neue Referenz hinzufügen**, wählen Sie WindowsFormsControlLibrary1 (unter der Registerkarte **Projekte)** und klicken Sie auf **OK**. Dadurch wird ein Verweis in Form einer [/FU-Compileroption](../build/reference/fu-name-forced-hash-using-file.md) hinzugefügt, sodass das Programm kompiliert wird. Außerdem wird WindowsFormsControlLibrary1.dll `MFC02` in das Projektverzeichnis kopiert, sodass das Programm ausgeführt wird.

1. Suchen Sie in stdafx.h folgende Zeile:

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   Fügen Sie davor folgende Zeilen ein:

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. Ändern Sie die Ansichtsklasse so, dass sie von [CWinFormsView](../mfc/reference/cwinformsview-class.md)erbt.

   Ersetzen Sie in MFC02View.h [CView](../mfc/reference/cview-class.md) durch [CWinFormsView,](../mfc/reference/cwinformsview-class.md) sodass der Code wie folgt angezeigt wird:

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   Wenn Sie Ihrer MDI-Anwendung zusätzliche Ansichten hinzufügen möchten, müssen Sie [CWinApp::AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) für jede von Ihnen erstellte Ansicht aufrufen.

1. Ändern Sie in der Datei MFC02View.cpp im IMPLEMENT_DYNCREATE-Makro und in der Meldungszuordnung CView in CWinFormsView um, und ersetzen Sie den vorhandenen leeren Konstruktor durch den folgenden:

    ```
    IMPLEMENT_DYNCREATE(CMFC02View, CWinFormsView)

    CMFC02View::CMFC02View(): CWinFormsView(WindowsFormsControlLibrary1::UserControl1::typeid)
    {
    }
    BEGIN_MESSAGE_MAP(CMFC02View, CWinFormsView)
    //leave existing body as is
    END_MESSAGE_MAP()
    ```

1. Erstellen Sie das Projekt, und führen Sie es aus.

   Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf MFC02, und wählen Sie **Als StartUp-Projekt festlegen**aus.

   Klicken Sie im Menü **Build** auf **Projektmappe erstellen**.

   Klicken Sie im **Menü Debuggen** auf **Start ohne Debugging**.

## <a name="see-also"></a>Siehe auch

[Hosten eines Windows Forms-Benutzersteuerelements als MFC-Ansicht](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)

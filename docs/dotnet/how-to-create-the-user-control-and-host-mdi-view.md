---
title: 'Gewusst wie: Erstellen des Benutzersteuerelements und Hosten der MDI-Ansicht'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms Controls
- Windows Forms [C++], MFC support
ms.assetid: 625b5821-f923-4701-aca0-c1a4ceca4f63
ms.openlocfilehash: 634dd9c1ad2ce9199cec0dfa7ef067bd45f242f6
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2019
ms.locfileid: "79544723"
---
# <a name="how-to-create-the-user-control-and-host-mdi-view"></a>Gewusst wie: Erstellen des Benutzersteuerelements und Hosten der MDI-Ansicht

In den folgenden Schritten wird das Erstellen eines .NET Framework-Benutzersteuerelements und das Erstellen des Steuerelements in einer Steuerelementklassenbibliothek (speziell in einem Projekt einer Windows-Steuerelementbibliothek) sowie das Kompilieren des Projekts in eine Assembly veranschaulicht. Das Steuerelement kann dann von einer MFC-Anwendung verwendet werden, die von der [CView-Klasse](../mfc/reference/cview-class.md) und der [CWinFormsView-Klasse](../mfc/reference/cwinformsview-class.md)abgeleitete Klassen verwendet.

Weitere Informationen zum Erstellen eines Windows Forms Benutzer Steuer Elements und zum Erstellen einer Steuerelement Klassenbibliothek finden Sie unter Gewusst [wie:](/dotnet/framework/winforms/controls/how-to-author-composite-controls)Erstellen von Benutzer Steuerelementen.

> [!NOTE]
>  In einigen Fällen verhalten sich Windows Forms-Steuerelemente, z. B. ein Datenblattsteuerelement eines Drittanbieters, nicht zuverlässig, wenn sie in einer MFC-Anwendung gehostet werden. Um dies zu umgehen, wird empfohlen, ein Windows Forms-Benutzersteuerelement in der MFC-Anwendung und das Datenblattsteuerelement des Drittanbieters innerhalb des Benutzersteuerelements zu platzieren.

Bei diesem Verfahren wird davon ausgegangen, dass Sie ein Windows Forms Controls-Bibliotheksprojekt mit dem Namen WindowsFormsControlLibrary1 erstellt haben, wie gemäß dem Verfahren unter Gewusst [wie: Erstellen des Benutzer Steuer Elements und des Hosts in einem Dialog Feld](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)beschrieben.

### <a name="to-create-the-mfc-host-application"></a>So erstellen Sie die MFC-Hostanwendung

1. Erstellen Sie ein MFC-Anwendungsprojekt.

   Wählen Sie im Menü **Datei** die Option **neu**aus, und klicken Sie dann auf **Projekt**. Wählen Sie im Ordner " **Visual C++**  " die Option **MFC-Anwendung**aus.

   Geben Sie im Feld **Name** `MFC02` ein, und ändern **Sie die** Projektmappeneinstellung zu Projekt Mappe **Hinzufügen**. Klicken Sie auf **OK**.

   Akzeptieren Sie im **MFC-Anwendungs-Assistenten**alle Standardwerte, und klicken Sie dann auf **Fertig**stellen. Dies erstellt eine MFC-Anwendung mit einem MDI (Multiple Document Interface).

1. Konfigurieren Sie das Projekt für Common Language Runtime (CLR)-Unterstützung.

   Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Projekt Knoten `MFC01`, und wählen Sie im Kontextmenü **Eigenschaften** aus. Das Dialogfeld **Eigenschaften Seiten** wird angezeigt.

   Wählen Sie unter **Konfigurations Eigenschaften**die Option **Allgemein**aus. Legen Sie im Abschnitt **Projekt** Standards die **Common Language Runtime** -Unterstützung auf **Common Language Runtime-Unterstützung (/CLR)** fest.

   Erweitern Sie unter **Konfigurations Eigenschaften**die Option **C/C++**  , und klicken Sie auf den Knoten **Allgemein** . Legen Sie das **Format der Debuginformationen** auf **Program Database (/Zi)** fest.

   Klicken Sie auf den Knoten **Code Generierung** . Legen Sie minimale Neuerstellung **aktivieren** auf **Nein (/GM-)** fest. Legen Sie außerdem **grundlegende Laufzeitüberprüfungen** auf **Standard**fest

   Klicken Sie auf **OK** , um die Änderungen zu übernehmen.

1. Fügen Sie in " *PCH. h* " (*stdafx. h* in Visual Studio 2017 und früher) die folgende Zeile hinzu:

    ```
    #using <System.Windows.Forms.dll>
    ```

1. Fügen Sie dem .NET-Steuerelement einen Verweis hinzu.

   Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Projekt Knoten `MFC02`, und wählen Sie **Hinzufügen**, **Verweise**aus. Klicken Sie auf der **Eigenschaften Seite**auf **neuen Verweis hinzufügen**, wählen Sie WindowsFormsControlLibrary1 (unter der Registerkarte **Projekte** ) aus, und klicken Sie auf **OK**. Dadurch wird ein Verweis in Form einer [/Fu](../build/reference/fu-name-forced-hash-using-file.md) -Compileroption hinzugefügt, damit das Programm kompiliert wird. Außerdem wird WindowsFormsControlLibrary1. dll in das `MFC02`-Projektverzeichnis kopiert, damit das Programm ausgeführt wird.

1. Suchen Sie in stdafx.h folgende Zeile:

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   Fügen Sie davor folgende Zeilen ein:

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. Ändern Sie die Ansichts Klasse so, dass Sie von [CWinFormsView](../mfc/reference/cwinformsview-class.md)erbt.

   Ersetzen Sie in MFC02View. h [CView](../mfc/reference/cview-class.md) durch [CWinFormsView](../mfc/reference/cwinformsview-class.md) , sodass der Code wie folgt aussieht:

    ```
    class CMFC02View : public CWinFormsView
    {
    };
    ```

   Wenn Sie der MDI-Anwendung zusätzliche Ansichten hinzufügen möchten, müssen Sie für jede erstellte Ansicht [CWinApp:: AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate) aufrufen.

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

   Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf MFC02, und wählen Sie **als Startprojekt festlegen**aus.

   Klicken Sie im Menü **Build** auf **Projektmappe erstellen**.

   Klicken Sie im Menü **Debuggen** auf **Starten ohne Debuggen**.

## <a name="see-also"></a>Siehe auch

[Hosten eines Windows Forms-Benutzersteuerelements als MFC-Ansicht](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)

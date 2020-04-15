---
title: 'Gewusst wie: Hinzufügen von Befehlsrouting zum Windows Forms-Steuerelement'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
ms.openlocfilehash: ad64a12051c22a0cfca99d3ec9c5abef579902f4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365169"
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>Gewusst wie: Hinzufügen von Befehlsrouting zum Windows Forms-Steuerelement

[CWinFormsView](../mfc/reference/cwinformsview-class.md) leitet Befehle und Befehlsnachrichten mit Update-Befehlen an das Benutzersteuerelement weiter, damit es MFC-Befehle verarbeiten kann (z. B. Framemenüelemente und Symbolleistenschaltflächen).

Das Benutzersteuerelement verwendet [ICommandTarget::Initialize,](../mfc/reference/icommandtarget-interface.md#initialize) um einen Verweis `m_CmdSrc`auf das Befehlsquellobjekt in zu speichern, wie im folgenden Beispiel gezeigt. Um `ICommandTarget` zu verwenden, müssen Sie einen Verweis auf mfcmifc80.dll hinzufügen.

Durch `CWinFormsView` werden einige der allgemeinen MFC-Anzeigenbenachrichtigungen verarbeitet, indem diese an das verwaltete Benutzersteuerelement weitergeleitet werden. Zu diesen Benachrichtigungen gehören die Methoden [OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate), [OnUpdate](../mfc/reference/iview-interface.md#onupdate) und [OnActivateView.](../mfc/reference/iview-interface.md#onactivateview)

In diesem Thema wird davon ausgegangen, dass Sie [zuvor die Folgenden: Erstellen der Benutzersteuerung und des Hosts in einem Dialogfeld](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) und [Gewusst wie: Erstellen der Benutzersteuerung und der Host-MDI-Ansicht](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)abgeschlossen haben.

### <a name="to-create-the-mfc-host-application"></a>So erstellen Sie die MFC-Hostanwendung

1. Öffnen Sie die Windows Forms Control Library, die Sie in [Gewusst wie: Erstellen der Benutzersteuerung und](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)des Hosts in einem Dialogfeld erstellt haben.

1. Fügen Sie einen Verweis auf mfcmifc80.dll hinzu, den Sie tun können, indem Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten klicken, **Hinzufügen**auswählen , **Referenz**, und dann zu Microsoft Visual Studio 10.0-VC-atlmfc-lib navigieren.

1. Öffnen Sie UserControl1.Designer.cs, und fügen Sie die folgende using-Anweisung hinzu:

    ```
    using Microsoft.VisualC.MFC;
    ```

1. Ändern Sie außerdem in UserControl1.Designer.cs die folgende Zeile:

    ```
    partial class UserControl1
    ```

   Und zwar in diesen Code:

    ```
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget
    ```

1. Fügen Sie diese Zeile als erste Zeile der Klassendefinition für `UserControl1` hinzu:

    ```
    private ICommandSource m_CmdSrc;
    ```

1. Fügen Sie die folgenden Methodendefinitionen zu `UserControl1` hinzu (die ID des MFC-Steuerelements wird im nächsten Schritt erstellt):

    ```
    public void Initialize (ICommandSource cmdSrc)
    {
       m_CmdSrc = cmdSrc;
       // need ID of control in MFC dialog and callback function
       m_CmdSrc.AddCommandHandler(32771, new CommandHandler (singleMenuHandler));
    }

    private void singleMenuHandler (uint cmdUI)
    {
       // User command handler code
       System.Windows.Forms.MessageBox.Show("Custom menu option was clicked.");
    }
    ```

1. Öffnen Sie die MFC-Anwendung, die Sie unter [Gewusst wie: Erstellen der Benutzersteuerung und der Host-MDI-Ansicht](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)erstellt haben.

1. Fügen Sie eine Menüoption hinzu, die `singleMenuHandler` aufruft.

   Wechseln Sie **zu Ressourcenansicht** (Strg+Umschalt+E), erweitern Sie den **Menüordner,** und doppelklicken Sie dann auf **IDR_MFC02TYPE**. Der Menü-Editor wird angezeigt.

   Fügen Sie eine Menüoption am unteren Rand des **Menüs Ansicht** hinzu. Beachten Sie die ID der Menüoption im **Eigenschaftenfenster.** Speichern Sie die Datei .

   Öffnen Sie im **Projektmappen-Explorer**die Datei Resource.h, kopieren Sie den ID-Wert für `m_CmdSrc.AddCommandHandler` die Menüoption, die `Initialize` Sie gerade `32771` hinzugefügt haben, und fügen Sie diesen Wert als ersten Parameter in die Methode des C-Projekts ein (ggf. ersetzt).

1. Erstellen Sie das Projekt, und führen Sie es aus.

   Klicken Sie im Menü **Build** auf **Projektmappe erstellen**.

   Klicken Sie im **Menü Debuggen** auf **Start ohne Debugging**.

   Wählen Sie die hinzugefügte Menüoption aus. Beachten Sie, dass die Methode in der DLL aufgerufen wird.

## <a name="see-also"></a>Siehe auch

[Hosten eines Windows Forms-Benutzersteuerelements als MFC-Ansicht](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[ICommandSource-Schnittstelle](../mfc/reference/icommandsource-interface.md)<br/>
[ICommandTarget-Schnittstelle](../mfc/reference/icommandtarget-interface.md)

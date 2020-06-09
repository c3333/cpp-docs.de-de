---
title: 'Vorgehensweise: Hinzufügen, bearbeiten oder Löschen von Steuerelementen (C++)'
ms.date: 02/15/2019
f1_keywords:
- vc.controls.activex
- vc.editors.dialog.insertActiveXControls
helpviewer_keywords:
- Dialog Editor [C++], creating controls
- dialog boxes [C++], adding controls to
- Toolbox [C++], Dialog Editor tab
- controls [C++], types
- syslink controls in dialog boxes
- custom controls [C++], dialog boxes
- controls [C++], standard
- Dialog Editor [C++], creating controls
- controls [C++], adding to dialog boxes
- controls [C++], adding multiple
- dialog box controls [C++], size
- controls [C++], sizing
- dialog boxes [C++], adding ActiveX controls
- ActiveX controls [C++], adding to dialog boxes
- Insert ActiveX Control dialog box [C++]
- controls [C++], editing properties
- ActiveX controls [C++], properties
- controls [C++], undoing changes
- controls [C++], editing properties
- dialog box controls [C++], editing properties
- dialog box controls [C++], deleting
- controls [C++], deleting
- Dialog Editor [C++], default control events
- controls [C++], default control events
- events [C++], controls
- dialog box controls [C++], events
- member variables, defining for controls
- variables, dialog box control member variables
- controls [C++], member variables
- Dialog Editor [C++], defining member variables for controls
- controls [C++], troubleshooting
- Dialog Editor [C++], troubleshooting
- dialog boxes [C++], troubleshooting
- InitCommonControls
- RichEdit 1.0 control
- rich edit controls [C++], RichEdit 1.0
ms.assetid: 73cef03f-5c8c-456a-87d1-1458dff185cf
ms.openlocfilehash: 9c1596b66f4387ea1f7ce309a5012ecd0f63d5de
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623460"
---
# <a name="how-to-add-edit-or-delete-controls-c"></a>Vorgehensweise: Hinzufügen, bearbeiten oder Löschen von Steuerelementen (C++)

Mit dem **Dialog-Editor**können Sie Steuerelemente in Dialog Feldern hinzufügen, die Größe ändern, bearbeiten und löschen. Sie können auch die Eigenschaften eines Steuer Elements bearbeiten, z. b. die zugehörige ID oder ob es anfänglich zur Laufzeit sichtbar ist.

Die Registerkarte " **Dialog-Editor** " wird im [Fenster "Toolbox](/visualstudio/ide/reference/toolbox) " angezeigt, wenn Sie im Dialog- **Editor**arbeiten. Sie können das **Toolbox** Fenster auch für eine einfachere Verwendung anpassen. Weitere Informationen finden Sie unter [Verwenden der Toolbox](/visualstudio/ide/using-the-toolbox) und [anzeigen oder Ausblenden des Fenster "Toolbox](showing-or-hiding-the-dialog-editor-toolbar.md)".

> [!TIP]
> Wenn Sie den **Dialog-Editor**verwenden, können Sie in vielen Fällen die Rechte Maustaste auswählen, um ein Kontextmenü mit häufig verwendeten Befehlen anzuzeigen.

## <a name="add-controls"></a>Hinzufügen von Steuerelementen

### <a name="to-add-a-control"></a>So fügen Sie ein Steuerelement hinzu

1. Stellen Sie sicher, dass das Dialogfeld im Registerkartenformat das aktuelle Dokument im Editor-Fenster darstellt. Wenn ein Dialogfeld nicht das aktuelle Dokument ist, wird die **Registerkarte "Dialog-Editor** " in der **Toolbox**nicht angezeigt.

1. Wählen Sie auf der Registerkarte **Dialog-Editor** des Fensters **Toolbox** das gewünschte Steuerelement aus, und wählen Sie dann eine der folgenden Optionen:

   - Wählen Sie das Dialogfeld an der Stelle aus, an der Sie das Steuerelement platzieren möchten, und das Steuerelement wird angezeigt, wo Sie es ausgewählt haben.

   - Ziehen Sie das Steuerelement per Drag & amp; Drop aus dem Fenster **Toolbox** an die Position im Dialogfeld. Anschließend können Sie das Steuerelement verschieben oder seine Größe und Form ändern.

   - Doppelklicken Sie im Fenster **Toolbox** auf das-Steuerelement, und es wird im Dialogfeld angezeigt. Positionieren Sie das Steuerelement am gewünschten Speicherort neu.

### <a name="to-add-multiple-controls"></a>So fügen Sie mehrere Steuerelemente hinzu

1. Wählen Sie ein Steuerelement im Fenster **Toolbox** aus, während Sie die **STRG** -Taste gedrückt halten.

1. Geben Sie die **STRG** -Taste ein, und wählen Sie das Dialogfeld so oft aus, wie Sie das jeweilige Steuerelement hinzufügen möchten.

1. Drücken Sie **ESC** , um das Platzieren von Steuerelementen zu verhindern

### <a name="to-size-a-control-while-you-add-it"></a>So verkleinern Sie ein Steuerelement beim Hinzufügen

1. Wählen Sie im Fenster **Toolbox** ein Steuerelement aus.

1. Platzieren Sie den Cursor, der als kreuzhaare angezeigt wird, wobei die obere linke Ecke des neuen Steuer Elements in Ihrem Dialogfeld angezeigt werden soll.

1. Aktivieren und halten Sie die Maustaste gedrückt, um die linke obere Ecke des Steuer Elements im Dialogfeld zu verankern. Ziehen Sie dann den Cursor nach rechts und unten, bis die gewünschte Größe für das Steuerelement festgelegt ist.

   > [!NOTE]
   > Sie können jede der vier Ecken des Steuer Elements verankern, das Sie zeichnen. In diesem Verfahren wurde die linke obere Ecke als Beispiel verwendet.

1. Lassen Sie die Maustaste los. Das-Steuerelement wird im Dialogfeld in der von Ihnen angegebenen Größe festgelegt.

> [!TIP]
> Sie können die Größe des Steuer Elements nach dem ablegen im Dialogfeld ändern, indem Sie die Zieh Punkte am Rahmen des Steuer Elements verschieben. Weitere Informationen finden Sie unter [dimensionieren einzelner Steuerelemente](../windows/sizing-individual-controls.md).

### <a name="to-add-a-custom-control"></a>So fügen Sie ein benutzerdefiniertes Steuerelement hinzu

Sie können dem Dialogfeld benutzerdefinierte Steuerelemente hinzufügen. Wählen Sie das Symbol **benutzerdefiniertes Steuer** Element in der **Toolbox** aus, und ziehen Sie es in das Dialogfeld. Wenn Sie ein Steuerelement hinzufügen möchten `Syslink` , fügen Sie ein benutzerdefiniertes Steuerelement hinzu, und ändern Sie dann die- **Klassen** Eigenschaft `Syslink` Diese Aktion bewirkt, dass die Eigenschaften aktualisiert werden und die `Syslink` Steuerelement Eigenschaften angezeigt werden. Weitere Informationen zur MFC-Wrapper Klasse finden Sie unter [ClinkCtrl](../mfc/reference/clinkctrl-class.md).

## <a name="edit-controls"></a>Steuerelemente bearbeiten

### <a name="to-edit-the-properties-of-a-control-or-controls"></a>So bearbeiten Sie die Eigenschaften eines Steuer Elements oder von Steuerelementen

1. Wählen Sie im Dialogfeld das Steuerelement aus, das Sie ändern möchten.

   > [!NOTE]
   > Wenn Sie mehrere Steuerelemente auswählen, können nur die Eigenschaften bearbeitet werden, die den ausgewählten Steuerelementen gemeinsam sind.

1. Ändern Sie im [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window)die Eigenschaften des Steuer Elements.

   > [!NOTE]
   > Wenn Sie die **Bitmap** -Eigenschaft für eine Schaltfläche, ein Optionsfeld oder ein Kontrollkästchen-Steuerelement auf **true**festlegen, wird der Stil BS_BITMAP für das Steuerelement implementiert. Weitere Informationen finden Sie unter [Schaltflächen Stile](../mfc/reference/styles-used-by-mfc.md#button-styles). Ein Beispiel für das Zuordnen einer Bitmap zu einem Steuerelement finden Sie unter [CButton:: SetBitmap](../mfc/reference/cbutton-class.md#setbitmap). Bitmaps werden nicht auf dem Steuerelement angezeigt, wenn Sie sich im **Dialog-Editor**befinden.

### <a name="to-undo-changes-to-the-properties-of-a-control"></a>So machen Sie Änderungen an den Eigenschaften eines Steuer Elements rückgängig

1. Stellen Sie sicher, dass das Steuerelement im **Dialog-Editor**den Fokus besitzt.

1. Wechseln Sie zum Menü **Bearbeiten**  >  **Rückgängig**. Wenn sich der Fokus nicht auf dem Steuerelement befindet, ist der Befehl **Rückgängig** nicht verfügbar.

### <a name="to-define-a-member-variable-for-a-non-button-dialog-box-control"></a>So definieren Sie eine Membervariable für ein Dialogfeld-Steuerelement (kein Schaltflächen-Steuerelement)

> [!NOTE]
> Dieser Vorgang gilt nur für Dialogfeld Steuerelemente innerhalb eines MFC-Projekts. ATL-Projekte sollten das Dialogfeld **neue Windows-Meldungen und Ereignishandler** verwenden. Weitere Informationen finden Sie unter [Nachrichten Typen im Zusammenhang mit Benutzeroberflächen Objekten](../mfc/reference/message-types-associated-with-user-interface-objects.md), [Bearbeiten eines Nachrichten Handlers](../mfc/reference/editing-a-message-handler.md)und [Definieren eines Meldungs Handlers für eine reflektierte Nachricht](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

1. Wählen Sie im [Dialog-Editor](dialog-editor.md)ein Steuerelement aus.

1. Beim Drücken der **STRG** -Taste Doppelklicken Sie auf das Dialogfeld-Steuerelement.

   Der [Assistent zum Hinzufügen](../ide/add-member-variable-wizard.md) von Element Variablen wird angezeigt.

1. Geben Sie die entsprechenden Informationen in den Assistenten zum **Hinzufügen von Mitgliedsvariablen** ein. Weitere Informationen finden Sie unter [Dialog Datenaustausch](../mfc/dialog-data-exchange.md).

1. Wählen Sie **OK** aus, um zum **Dialog-Editor**zurückzukehren.

> [!TIP]
> Doppelklicken Sie auf das Steuerelement, um von einem Dialogfeld-Steuerelement zu seinem vorhandenen Handler zu wechseln.

Sie können auch die Registerkarte Element **Variablen** im [MFC-Klassen-Assistenten](../mfc/reference/mfc-class-wizard.md) verwenden, um neue Element Variablen für eine angegebene Klasse hinzuzufügen und bereits definierte Element Variablen anzuzeigen.

## <a name="delete-controls"></a>Löschen von Steuerelementen

Wählen Sie im Dialog **Feld das Steuer** Element aus, und drücken Sie dann die ENTF-Taste, oder wechseln Sie zum Menü **Bearbeiten**  >  **Löschen**.

## <a name="other-issues"></a>Andere Probleme

### <a name="troubleshooting"></a>Problembehandlung

Nach dem Hinzufügen eines allgemeinen Steuer Elements oder eines Rich-Edit-Steuer Elements zu einem Dialogfeld wird es nicht angezeigt, wenn Sie das Dialogfeld testen. Oder das Dialogfeld selbst wird nicht angezeigt. Beispiel:

1. Erstellen Sie ein Win32-Projekt, indem Sie die Anwendungseinstellungen so ändern, dass Sie eine Windows-Anwendung erstellen (keine Konsolenanwendung).

1. Doppelklicken Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)auf die *RC* -Datei.

1. Doppelklicken Sie **unter der Dialogfeld Option** auf das Feld Info.

1. Fügen Sie dem Dialogfeld ein **IP-Adress Steuer** Element hinzu.

1. Alle speichern und **neu erstellen**.

1. Führen Sie das Programm aus.

1. Wählen Sie im **Hilfemenü** des Dialog Felds **den Befehl Info** aus, und beachten Sie, dass kein Dialogfeld angezeigt wird.

Derzeit fügt der **Dialog-Editor** dem Projekt nicht automatisch Code hinzu, wenn Sie die folgenden allgemeinen Steuerelemente oder Rich Edit-Steuerelemente in ein Dialog Feld ziehen und ablegen. Außerdem bietet Visual Studio bei Auftreten dieses Problems einen Fehler oder eine Warnung an. Fügen Sie den Code für das Steuerelement manuell hinzu, um es zu beheben.

||||
|-|-|-|
|Schiebereglersteuerung|Tree-Steuerelement|Datums-/Zeitauswahl|
|Dreh Steuerelement|Register Steuerelement|Month Calendar|
|Fortschrittskontrolle|Animations Steuerelement|IP-Adressensteuerelement|
|Abkürzungs Taste|Rich Edit-Steuerelement|Erweitertes Kombinations Feld|
|Listen Steuerelement|Rich Edit 2,0-Steuerelement|Benutzerdefiniertes Steuerelement|

Um allgemeine Steuerelemente in einem Dialogfeld zu verwenden, müssen Sie [InitCommonControlsEx](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex) oder `AFXInitCommonControls` vor dem Erstellen des Dialog Felds anrufen.

Um RichEdit-Steuerelemente verwenden zu können, müssen Sie aufzurufen `LoadLibrary` . Weitere Informationen finden Sie unter Informationen [zu Rich Edit](/windows/win32/Controls/about-rich-edit-controls) -Steuerelementen im Windows SDK und [Übersicht über das Rich Edit-Steuer](../mfc/overview-of-the-rich-edit-control.md)Element.

> [!NOTE]
> Wenn Sie ein RichEdit-Steuerelement mit MFC verwenden möchten, müssen Sie zuerst [AfxInitRichEdit2](../mfc/reference/application-information-and-management.md#afxinitrichedit2) aufzurufen, um das RichEdit 2,0-Steuerelement (Riched20 zu laden. DLL), oder Sie können das ältere RichEdit 1,0-Steuerelement (RICHED32) mit [afxiniterchedit](../mfc/reference/application-information-and-management.md#afxinitrichedit) laden. DLL).
>
> Sie können die aktuelle [CRichEditCtrl](../mfc/reference/cricheditctrl-class.md) -Klasse mit dem älteren RichEdit 1,0-Steuerelement verwenden, `CRichEditCtrl` ist jedoch nur für die Unterstützung des RichEdit-Steuer Elements 2,0 vorgesehen. Da RichEdit 1,0 und RichEdit 2,0 ähnlich sind, funktionieren die meisten Methoden. Es gibt jedoch einige Unterschiede zwischen den Steuerelementen 1,0 und 2,0, sodass einige Methoden möglicherweise falsch funktionieren oder überhaupt nicht funktionieren.

### <a name="activex-controls"></a>ActiveX-Steuerelemente

Visual Studio ermöglicht Ihnen das Einfügen von ActiveX-Steuerelementen in Ihr Dialogfeld. Weitere Informationen finden Sie unter [MFC-ActiveX](../mfc/mfc-activex-controls.md) - [Steuer](../mfc/activex-control-containers.md)Elemente und ActiveX-Steuerelement Container.

Im Dialogfeld **ActiveX-Steuerelement einfügen** können Sie ActiveX-Steuerelemente in das Dialogfeld einfügen, während Sie den Dialogfeld- [Editor](dialog-editor.md)verwenden. Dieses Dialogfeld enthält die folgenden Eigenschaften:

|Eigenschaft|Beschreibung|
|---|---|
|**ActiveX-Steuerelement**|Zeigt eine Liste von ActiveX-Steuerelementen an.<br/><br/>Das Einfügen eines Steuer Elements aus diesem Dialogfeld generiert keine Wrapper Klasse. Wenn Sie eine Wrapper Klasse benötigen, verwenden Sie [Klassenansicht](/visualstudio/ide/viewing-the-structure-of-code) , um einen zu erstellen, siehe [Hinzufügen einer Klasse](../ide/adding-a-class-visual-cpp.md).<br/><br/>Wenn ein ActiveX-Steuerelement in diesem Dialogfeld nicht angezeigt wird, versuchen Sie, das Steuerelement gemäß den Anweisungen des Herstellers zu installieren.|
|**Pfad**|Zeigt die Datei an, in der das ActiveX-Steuerelement gefunden wurde.|

> [!CAUTION]
> Der Vertrieb ist möglicherweise nicht für alle ActiveX-Steuerelemente auf Ihrem System rechtlich zulässig. Lesen Sie den Lizenzvertrag für die Software, die die Steuerelemente installiert hat, oder wenden Sie sich an das Softwareunternehmen.

#### <a name="to-add-an-activex-control"></a>Hinzufügen eines ActiveX-Steuer Elements

1. Öffnen Sie ein Dialogfeld im **Dialog-Editor**.

1. Klicken Sie mit der rechten Maustaste auf eine beliebige Stelle im Text des Dialog Felds, und wählen Sie **ActiveX-Steuerelement einfügen**

   Das Dialogfeld **ActiveX-Steuerelement einfügen** wird angezeigt, in dem alle ActiveX-Steuerelemente auf dem System angezeigt werden. Unten im Dialogfeld wird der Pfad der Datei des ActiveX-Steuerelements angezeigt.

1. Wählen Sie das Steuerelement aus, das Sie Ihrem Dialogfeld hinzufügen möchten, und klicken Sie auf **OK**.

   Das Steuerelement wird im Dialogfeld angezeigt, wo Sie es bearbeiten oder Handler für es erstellen können, ganz wie bei jedem anderen Steuerelement.

> [!TIP]
> Mithilfe des Kontextmenüs im **Dialog-Editor** können Sie schnell registrierte ActiveX-Steuerelemente zu einem Dialog Feld hinzufügen, oder Sie können dem Fenster **Toolbox** ActiveX-Steuerelemente hinzufügen, um den Zugriff zu vereinfachen.

#### <a name="to-edit-properties-for-an-activex-control"></a>So bearbeiten Sie die Eigenschaften für ein ActiveX-Steuerelement

ActiveX-Steuerelemente, die von unabhängigen Anbietern bereitgestellt werden, verfügen möglicherweise über eigene Eigenschaften und Merkmale. Diese Eigenschaften werden im **Eigenschaften** Fenster angezeigt. Alle Eigenschaften Seiten, die von den Writern des ActiveX-Steuer Elements erstellt werden, werden im Dialogfeld **Eigenschaften Seiten** angezeigt. (Um die **Eigenschaften Seite** für ein bestimmtes ActiveX-Steuerelement anzuzeigen, wählen Sie die Schaltfläche **Eigenschaften Seite** in der [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window)) aus.

- Wählen Sie das **ActiveX** -Steuerelement aus, und wechseln Sie zur Eigenschaften Seite Menü **Ansicht**  >  **Property Page** , um die Eigenschaften anzuzeigen. Nehmen Sie nach Bedarf Änderungen auf der Eigenschaften Seite vor.

   Verschiedene Registerkarten werden auf der Eigenschaften Seite für ein ActiveX-Steuerelement angezeigt, abhängig von den Eigenschaften Blättern, die Teil des ActiveX-Steuer Elements sind.

> [!NOTE]
> Dieses Verfahren gilt für die Verwendung der Eigenschaften Seite zum Bearbeiten von ActiveX-Steuerelementen. Sie können im Fenster "neue **Eigenschaften** " auch ActiveX-Eigenschaften durchsuchen und bearbeiten.

## <a name="requirements"></a>Requirements (Anforderungen)

Win32

## <a name="see-also"></a>Siehe auch

[Dialog Feld-Steuerelemente verwalten](controls-in-dialog-boxes.md)<br/>
[Gewusst wie: Layout von Steuerelementen](arrangement-of-controls-on-dialog-boxes.md)<br/>
[Gewusst wie: Definieren von Steuerelement Zugriff und-Werten](defining-mnemonics-access-keys.md)

<!-- excluded links
[Mapping Messages to Functions](../mfc/reference/mapping-messages-to-functions.md)<br/>
[Adding Functionality with Code Wizards](../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Adding a Class](../ide/adding-a-class-visual-cpp.md)<br/>
[Adding a Member Function](../ide/adding-a-member-function-visual-cpp.md)<br/>
[Adding a Member Variable](../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Overriding a Virtual Function](../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[MFC Message Handler](../mfc/reference/adding-an-mfc-message-handler.md)
[Declaring a Variable Based on Your New Control Class](../mfc/reference/declaring-a-variable-based-on-your-new-control-class.md)<br/>
-->

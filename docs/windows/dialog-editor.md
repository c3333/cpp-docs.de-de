---
title: Dialog-Editor (C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.dialog
- vc.editors.dialog.F1
- vc.editors.dialog
helpviewer_keywords:
- resource editors [C++], Dialog editor
- editors, dialog boxes
- Dialog editor
- dialog boxes [C++], editing
- controls [C++], showing or hiding Dialog editor toolbar
- toolbars [C++], showing
- toolbars [C++], hiding
- Dialog Editor [C++], showing or hiding toolbar
- events [C++], viewing for controls
- Windows messages [C++], controls
- messages [C++], viewing for dialog boxes
- Dialog Editor [C++], accessing code
- code [C++], switching from Dialog Editor
- controls [C++], jumping to code
- Dialog Editor [C++], switching between controls and code
- Dialog Editor [C++], shortcut keys
ms.assetid: d94884ef-2cca-49d8-9b58-775f34848134
ms.openlocfilehash: f1544d3a8e14f9373e21b77d888860d24ab1ed6a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370296"
---
# <a name="dialog-editor-c"></a>Dialog-Editor (C++)

Im **Dialog-Editor** können Sie Dialogfeldressourcen erstellen oder bearbeiten.

- Um den Editor zu öffnen, doppelklicken Sie im Fenster **Ressourcenansicht** auf die **View** > .rc-Datei eines Dialogfelds, oder wechseln Sie zum Menü Andere**Windows-Ressourcenansicht****Other Windows** > anzeigen .

Einer der ersten Schritte beim Erstellen einer neuen Dialogfeld- oder Dialogfeldvorlage ist das Hinzufügen von Steuerelementen. Im **Dialog-Editor**können Sie Steuerelemente so anordnen, dass sie an eine bestimmte Größe, Form oder Ausrichtung anpassen, oder Sie können sie verschieben, um im Dialogfeld zu arbeiten. Steuerelemente lassen sich darüber hinaus problemlos löschen.

Um ein Dialogfeld später wiederzuverwenden, können Sie es als Vorlage speichern. Auch das Wechseln zwischen dem Entwurf des Dialogfelds und dem Bearbeiten des Codes, mit dem das Feld implementiert wird, ist denkbar einfach.

Es ist auch möglich, Eigenschaften einzelner oder mehrerer Steuerelemente im **Dialog-Editor**zu bearbeiten. Sie können die Tabstoppreihenfolge ändern, d. h. die Reihenfolge, in der Steuerelemente den Fokus erhalten, wenn die **Tabulatortaste** gedrückt wird, oder Sie können eine Zugriffstaste oder Tastenkombination definieren, mit der Benutzer ein Steuerelement über die Tastatur auswählen können.

Im **Dialog-Editor** können Sie auch benutzerdefinierte Steuerelemente verwenden, einschließlich ActiveX-Steuerelemente. Sie können auch eine [Formularansicht](../mfc/reference/cformview-class.md)bearbeiten, Ansichten oder [Dialogfenster](../mfc/dialog-bars.md) [aufzeichnen.](../data/record-views-mfc-data-access.md)

Ab Visual Studio 2015 können Sie mit dem **Dialog-Editor** dynamische Layouts definieren, die angeben, wie Steuerelemente verschoben und die Größe geändert werden, wenn der Benutzer die Größe eines Dialogfelds ändert. Weitere Informationen finden Sie unter [Dynamic Layout](../mfc/dynamic-layout.md).

Weitere Informationen zu Ressourcen finden Sie unter [Erstellen eines Dialogfelds](../windows/creating-a-new-dialog-box.md) und [dialogfeldsteuerelemente Steuerelemente](../windows/controls-in-dialog-boxes.md).

> [!TIP]
> Wenn Sie den **Dialog-Editor**verwenden, können Sie in vielen Fällen mit der rechten Maustaste auswählen, ob ein Kontextmenü mit häufig verwendeten Befehlen angezeigt wird.

## <a name="dialog-editor-toolbar"></a>Symbolleiste des Dialog-Editors

Die Symbolleiste **Dialog-Editor** enthält Schaltflächen zum Anordnen des Layouts von Steuerelementen im Dialogfeld, z. B. Größe und Ausrichtung. **Dialog-Editor-Symbolleistenschaltflächen** entsprechen Denbefehlen im Menü **Format.**

|Symbol|Bedeutung|Symbol|Bedeutung|
|----------|-------------|----------|-------------|
|![Schaltfläche "Testdialogfeld"](../mfc/media/vcdialogeditortestdialog.png "vcDialogEditorTestDialog")|Testdialogfeld|![Schaltfläche "Horizontal anordnen"](../mfc/media/vcdialogeditoracross.png "vcDialogEditorAcross")|Über|
|![Schaltfläche "Links ausrichten"](../mfc/media/vcdialogeditoralignlefts.png "vcDialogEditorAlignLefts")|Nach links ausrichten|![Schaltfläche "Vertikal anordnen"](../mfc/media/vcdialogeditordown.png "vcDialogEditorDown")|Nach unten|
|![Schaltfläche "Rechts ausrichten"](../mfc/media/vcdialogeditoralignrights.png "vcDialogEditorAlignRights")|Nach rechts ausrichten|![Schaltfläche "Breite angleichen"](../mfc/media/vcdialogeditorsamewidth.png "vcDialogEditorSameWidth")|Breite angleichen|
|![Schaltfläche "Oben ausrichten"](../mfc/media/vcdialogeditoraligntops.png "vcDialogEditorAlignTops")|Nach oben ausrichten|![Schaltfläche "Höhe angleichen"](../mfc/media/vcdialogeditormakesameheight.png "vcDialogEditorMakeSameHeight")|Höhe angleichen|
|![Schaltfläche "Unten ausrichten"](../mfc/media/vcdialogeditoralignbottoms.png "vcDialogEditorAlignBottoms")|Nach unten ausrichten|![Schaltfläche "Größe angleichen"](../mfc/media/vcdialogeditorsamesize.png "vcDialogEditorSameSize")|Größe angleichen|
|![Schaltfläche "Vertikal zentrieren"](../mfc/media/vcdialogeditorvertical.png "vcDialogEditorVertikal")|Vertical|![Schaltfläche "Raster umschalten"](../mfc/media/vcdialogeditortogglegrid.png "vcDialogEditorToggleGrid")|Raster umschalten|
|![Schaltfläche "Horizontal zentrieren"](../mfc/media/vcdialogeditorhorizontal.png "vcDialogEditorHorizontal")|Horizontal|![Schaltfläche "Führungslinien umschalten"](../mfc/media/vcdialogeditortoggleguides.png "vcDialogEditorToggleGuides")|Führungslinien ein-/ausschalten|

- Um die Symbolleiste **des Dialog-Editors** **View** > ein- oder auszublenden, gehen Sie zum Menü > **Symbolleisten-Dialog-Editor**anzeigen .**Toolbars**

Wenn Sie den **Dialog-Editor** in einem C++-Projekt öffnen, wird die Symbolleiste dialog **editor** automatisch oben in der Projektmappe angezeigt, wenn Sie jedoch die Symbolleiste explizit schließen, müssen Sie sie beim nächsten Öffnen des **Dialog-Editors**aufrufen. Sie können die Anzeige umschalten, indem Sie sie aus der Liste der verfügbaren Symbolleisten und Fenster auswählen.

## <a name="switch-between-dialog-box-controls-and-code"></a>Wechseln zwischen Dialogfeldsteuerelementen und Code

In MFC-Anwendungen können Sie auf Dialogfeldsteuerelemente doppelklicken, um zu ihrem Handlercode zu springen oder stubhandlerfunktionen schnell zu erstellen.

Wenn ein Steuerelement ausgewählt ist, wählen Sie im [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window) die Schaltfläche **ControlEvents** oder die Schaltfläche **Nachrichten** aus, um eine vollständige Liste der für das ausgewählte Element verfügbaren Windows-Meldungen und -Ereignisse anzuzeigen. Wählen Sie aus der Liste aus, um Handlerfunktionen zu erstellen oder zu bearbeiten.

- Um aus dem **Dialog-Editor**zum Code zu springen, doppelklicken Sie auf ein Steuerelement im Dialogfeld, um zur Deklaration für die zuletzt implementierte Nachrichtenbehandlungsfunktion zu springen.

   Bei ATL-basierten Dialogklassen springen Sie immer zur Konstruktordefinition.

- Um Ereignisse für ein Steuerelement anzuzeigen, wählen Sie die Schaltfläche **ControlEvents** im **Eigenschaftenfenster** aus, um Ereignisse für ein Steuerelement anzuzeigen.

   Wenn ein einzelnes Steuerelement den Fokus im Dialogfeld hat, können Sie mit der rechten Maustaste klicken und **Ereignishandler hinzufügen**auswählen. Auf diese Weise können Sie die Klasse angeben, der der Handler hinzugefügt wird. Weitere Informationen finden Sie unter [Hinzufügen eines Ereignishandlers](../ide/adding-an-event-handler-visual-cpp.md).

   > [!NOTE]
   > Wenn Sie die Schaltfläche **ControlEvents** auswählen, wenn das Dialogfeld den Fokus hat, wird eine Liste aller Steuerelemente im Dialogfeld verfügbar gemacht, die Sie dann erweitern können, um die Ereignisse für die einzelnen Steuerelemente zu bearbeiten.

- Um Nachrichten für ein Dialogfeld anzuzeigen, wählen Sie mit aktiviertem Dialogfeld die Schaltfläche **Nachrichten** im **Eigenschaftenfenster** aus.

## <a name="accelerator-keys"></a>Zugriffstasten

Im Folgenden finden Sie die Standard-Beschleunigerschlüssel für die **Dialog-Editor-Befehle.**  

|Get-Help|Schlüssel|BESCHREIBUNG|
|-------------|----------|-----------------|
|Format.AlignBottoms|**Ctrl** + **Strg-Umschaltpfeil** + **Down Arrow**|Richtet die unteren Ränder der ausgewählten Steuerelemente an der dominanten Steuerung aus.|
|Format.AlignCenters|**Shift** + **F9**|Richtet die vertikalen Zentren der ausgewählten Steuerelemente an der dominanten Steuerung aus.|
|Format.AlignLefts|**Strg-Verschiebung** + **Shift** + **nach links**|Richtet die linken Ränder der ausgewählten Steuerelemente an der dominanten Steuerung aus.|
|Format.AlignMiddles|**F9**|Richtet die horizontalen Zentren der ausgewählten Steuerelemente an der dominanten Steuerung aus.|
|Format.AlignRights|**Ctrl** + **Strg-Umschalt-Rechtspfeil** + **Right Arrow**|Richtet die rechten Ränder der ausgewählten Steuerelemente an der dominanten Steuerung aus.|
|Format.AlignTops|**Ctrl** + **Strg-Umschaltpfeil** + **Up Arrow**|Richtet die oberen Kanten der ausgewählten Steuerelemente an der dominanten Steuerung aus.|
|Format.ButtonBottom|**Strg** + **B**|Platziert die ausgewählten Schaltflächen in der unteren Mitte des Dialogfelds.|
|Format.ButtonRight|**Strg** + **R**|Platziert die ausgewählten Schaltflächen in der oberen rechten Ecke des Dialogfelds.|
|Format.CenterHorizontal|**Strg** + **umschalt** + **F9**|Zentriert die Steuerelemente horizontal innerhalb des Dialogfelds.|
|Format.CenterVertical|**Strg** + **F9**|Zentriert die Steuerelemente vertikal innerhalb des Dialogfelds.|
|Format.CheckMnemonics|**Strg** + **M**|Überprüft die Einzigartigkeit von Mnemonics.|
|Format.SizeToContent|**Shift** + **F7**|Ändert die Größe der ausgewählten Steuerelemente an den Beschriftungstext.|
|Format.SpaceAcross|**Alt** + **Linker Pfeil**|Gleichmäßige Leerzeichen der ausgewählten Steuerelemente horizontal.|
|Format.SpaceDown|**Alt** + **Down Arrow**|Gleichmäßige Leerzeichen der ausgewählten Steuerelemente vertikal.|
|Format.TabOrder|**Strg** + **D**|Legt die Reihenfolge der Steuerelemente innerhalb des Dialogfelds fest.|
|Format.TestDialog|**Strg** + **T**|Führt das Dialogfeld aus, um Aussehen und Verhalten zu testen.|
|Format.ToggleGuides|**Strg** + **G**|Zyklen zwischen keinem Raster, Richtlinien und Raster für die Dialogbearbeitung.|

- Um Tastenkombinationen zu ändern, gehen **Keyboard** Sie zum Menü **Extraoptionen** > **Options**, und wählen Sie Tastatur im Ordner **Umgebung** aus.

   Weitere Informationen finden Sie unter [Identifizieren und Anpassen von Tastenkombinationen in Visual Studio](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

- Um Ihre Einstellungen zu ändern, gehen Sie zum Menü **Extras** > **Import und Export Einstellungen**.

   Die in den Dialogfeldern verfügbaren Optionen und die Namen und Speicherorte der angezeigten Menübefehle können je nach ihren aktiven Einstellungen oder Ihrer Edition von den in der **Hilfe** beschriebenen Optionen abweichen.  Weitere Informationen finden Sie unter [Personalisieren der Visual Studio-IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="requirements"></a>Anforderungen

Win32

## <a name="see-also"></a>Siehe auch

[Ressourcen-Editor](../windows/resource-editors.md)<br/>
[Gewusst wie: Erstellen eines Dialogfelds](../windows/creating-a-new-dialog-box.md)<br/>
[Dialogfeldsteuerelemente](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)-->

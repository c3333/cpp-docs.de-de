---
title: Dialog-EditorC++()
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
ms.openlocfilehash: 9d0f9993d81c499f67a08e5401c5e56dba7b281c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215253"
---
# <a name="dialog-editor-c"></a>Dialog-EditorC++()

Der **Dialog-Editor** ermöglicht es Ihnen, Dialog Feld Ressourcen zu erstellen oder zu bearbeiten.

- Um den Editor zu öffnen, doppelklicken Sie im Fenster **Ressourcenansicht** auf die RC-Datei eines Dialog Felds, oder wechseln Sie zur Menü **Ansicht** > **anderen Windows** - > **Ressourcenansicht**.

Einer der ersten Schritte beim Erstellen eines neuen Dialog Felds oder einer Dialogfeld Vorlage ist das Hinzufügen von Steuerelementen. Im **Dialog-Editor**können Sie Steuerelemente so anordnen, dass Sie einer bestimmten Größe, Form oder Ausrichtung entsprechen, oder Sie können Sie verschieben, um im Dialogfeld zu arbeiten. Steuerelemente lassen sich darüber hinaus problemlos löschen.

Um ein Dialogfeld später wiederzuverwenden, können Sie es als Vorlage speichern. Auch das Wechseln zwischen dem Entwurf des Dialogfelds und dem Bearbeiten des Codes, mit dem das Feld implementiert wird, ist denkbar einfach.

Es ist auch möglich, die Eigenschaften einzelner oder mehrerer Steuerelemente im **Dialog-Editor**zu bearbeiten. Sie können die Aktivier Reihenfolge ändern, d. h. die Reihenfolge, in der Steuerelemente den Fokus erhalten, wenn die **Tab** -Taste gedrückt wird, oder Sie können eine Zugriffstaste oder Tastenkombination definieren, mit der Benutzer ein Steuerelement mithilfe der Tastatur auswählen können.

Mit dem **Dialog-Editor** können Sie auch benutzerdefinierte Steuerelemente verwenden, einschließlich ActiveX-Steuerelementen. Sie können auch eine [Formularansicht](../mfc/reference/cformview-class.md), [Daten Satz Ansichten](../data/record-views-mfc-data-access.md)oder [Dialog leisten](../mfc/dialog-bars.md)bearbeiten.

Ab Visual Studio 2015 können Sie mit dem Dialog- **Editor** dynamische Layouts definieren, die angeben, wie die Steuerelemente verschoben und die Größe geändert werden, wenn der Benutzer die Größe eines Dialog Felds ändert. Weitere Informationen finden Sie unter [Dynamic Layout](../mfc/dynamic-layout.md).

Weitere Informationen zu Ressourcen finden Sie unter How to [Create a Dialog Box](../windows/creating-a-new-dialog-box.md) and [Dialog Box Controls](../windows/controls-in-dialog-boxes.md).

> [!TIP]
> Mit dem **Dialog-Editor**können Sie in vielen Fällen mit der rechten Maustaste auswählen, um ein Kontextmenü mit häufig verwendeten Befehlen anzuzeigen.

## <a name="dialog-editor-toolbar"></a>Symbolleiste des Dialog-Editors

Die Symbolleiste des **Dialog-Editors** enthält Schaltflächen zum Anordnen des Layouts der Steuerelemente im Dialogfeld, z. b. Größe und Ausrichtung. Symbolleisten Schaltflächen des **Dialog-Editors** entsprechen Befehlen im Menü " **Format** ".

|Symbol|Bedeutung|Symbol|Bedeutung|
|----------|-------------|----------|-------------|
|![Schaltfläche "Test"](../mfc/media/vcdialogeditortestdialog.png "vcdialogeditor testDialog")|Testdialogfeld|![Leertaste](../mfc/media/vcdialogeditoracross.png "vcdialogeditor")|Über|
|![Schaltfläche "lefts ausrichten"](../mfc/media/vcdialogeditoralignlefts.png "vcdialogeditoralignlefts")|Nach links ausrichten|![Leertaste](../mfc/media/vcdialogeditordown.png "vcdialogeditor")|Nach unten|
|![Schaltfläche Rechte ausrichten](../mfc/media/vcdialogeditoralignrights.png "vcdialogeditoralignrights")|Nach rechts ausrichten|![Schaltfläche für die gleiche Breite](../mfc/media/vcdialogeditorsamewidth.png "vcdialogedirensamewidth")|Breite angleichen|
|![Spitze ausrichten](../mfc/media/vcdialogeditoraligntops.png "vcdialogeditor aligntops")|Nach oben ausrichten|![Schaltfläche "Höhe erhöhen"](../mfc/media/vcdialogeditormakesameheight.png "vcdialogeditor makesameheight")|Höhe angleichen|
|![Schaltfläche "Bottoms ausrichten"](../mfc/media/vcdialogeditoralignbottoms.png "vcdialogeditoralignbottoms")|Nach unten ausrichten|![Schaltfläche "Größe angleichen"](../mfc/media/vcdialogeditorsamesize.png "vcdialogeditor SameSize")|Größe angleichen|
|![Vertikale Mitteltaste](../mfc/media/vcdialogeditorvertical.png "vcdialogedirenvertikal")|Vertical|![Raster Schaltfläche Umschalten](../mfc/media/vcdialogeditortogglegrid.png "vcdialogeditortogglegrid")|Raster umschalten|
|![Horizontale Mitteltaste](../mfc/media/vcdialogeditorhorizontal.png "vcdialogeditor horizontal")|Horizontal|![Schaltfläche zum Umschalten der Führungslinien](../mfc/media/vcdialogeditortoggleguides.png "vcdialogeditortoggleguides")|Führungslinien ein-/ausschalten|

- Zum Anzeigen oder Ausblenden der Symbolleiste des **Dialog-Editors** wechseln Sie zur Menü **Ansicht** > Symbol **leisten** > **Dialog-Editor**.

Wenn Sie den **Dialog-Editor** in einem C++ Projekt öffnen, wird die Symbolleiste des **Dialog-Editors** automatisch am oberen Rand der Projekt Mappe angezeigt. Wenn Sie die Symbolleiste jedoch explizit schließen, müssen Sie Sie beim nächsten Öffnen des **Dialog-Editors**aufrufen. Sie können die Anzeige umschalten, indem Sie Sie in der Liste der verfügbaren Symbolleisten und Fenster auswählen.

## <a name="switch-between-dialog-box-controls-and-code"></a>Zwischen Dialog Feld-Steuerelementen und Code wechseln

In MFC-Anwendungen können Sie auf Dialogfeld-Steuerelemente doppelklicken, um zu Ihrem Handlercode zu springen oder um schnell Stub-Handlerfunktionen zu erstellen.

Wenn Sie ein Steuerelement ausgewählt haben, wählen Sie die Schaltfläche **ControlEvents** oder die Schaltfläche **Meldungen** im [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window) aus, um eine komplette Liste der für das ausgewählte Element verfügbaren Windows-Meldungen und-Ereignisse anzuzeigen. Wählen Sie eine Liste aus, um Handlerfunktionen zu erstellen oder zu bearbeiten.

- Um im Dialogfeld- **Editor**zu Code zu wechseln, doppelklicken Sie auf ein Steuerelement im Dialogfeld, um zur Deklaration für die zuletzt implementierte Nachrichten Behandlungs Funktion zu springen.

   Bei ATL-basierten Dialog Klassen springen Sie immer zur Konstruktordefinition.

- Wenn Sie Ereignisse für ein Steuerelement anzeigen möchten, wählen Sie im **Eigenschaften** Fenster die Schaltfläche **ControlEvents** aus, wenn Sie ein Steuerelement ausgewählt haben.

   Wenn ein einzelnes Steuerelement im Dialogfeld den Fokus hat, können Sie mit der rechten Maustaste klicken und **Ereignis Handler hinzufügen**auswählen. Dies ermöglicht es Ihnen, die Klasse anzugeben, der der Handler hinzugefügt wird. Weitere Informationen finden Sie unter [Hinzufügen eines Ereignis Handlers](../ide/adding-an-event-handler-visual-cpp.md).

   > [!NOTE]
   > Wenn Sie die Schaltfläche **ControlEvents** auswählen, wenn das Dialogfeld den Fokus besitzt, wird eine Liste aller Steuerelemente im Dialogfeld angezeigt, die Sie dann erweitern können, um die Ereignisse für die einzelnen Steuerelemente zu bearbeiten.

- Klicken Sie im **Eigenschaften** Fenster auf die Schaltfläche **Meldungen** , um Meldungen für ein Dialogfeld anzuzeigen, während das Dialogfeld ausgewählt ist.

## <a name="accelerator-keys"></a>Zugriffstasten

Im folgenden finden Sie die Standard Zugriffstasten für die Befehle des **Dialog-Editors** .  

|Get-Help|Schlüssel|BESCHREIBUNG|
|-------------|----------|-----------------|
|Format.AlignBottoms|**STRG** + **UMSCHALT** + **Pfeil nach unten**|Richtet die unteren Ränder der ausgewählten Steuerelemente mit dem vorherrschenden Steuerelement aus.|
|Format.AlignCenters|**UMSCHALT** + **F9**|Richtet die vertikalen zentriert der ausgewählten Steuerelemente mit dem vorherrschenden Steuerelement aus.|
|Format.AlignLefts|**STRG** + **UMSCHALT** + nach- **Links-Taste**|Richtet die linken Ränder der ausgewählten Steuerelemente mit dem vorherrschenden Steuerelement aus.|
|Format.AlignMiddles|**F9**|Richtet die horizontalen zentriert der ausgewählten Steuerelemente mit dem vorherrschenden Steuerelement aus.|
|Format.AlignRights|**STRG** + **UMSCHALT** + **Pfeil nach rechts**|Richtet die rechten Ränder der ausgewählten Steuerelemente mit dem vorherrschenden Steuerelement aus.|
|Format.AlignTops|**STRG** + **UMSCHALT** + **Pfeil nach oben**|Richtet die oberen Ränder der ausgewählten Steuerelemente mit dem vorherrschenden Steuerelement aus.|
|Format.ButtonBottom|**STRG** + **B**|Platziert die ausgewählten Schaltflächen in der unteren Mitte des Dialog Felds.|
|Format.ButtonRight|**STRG** + **R**|Platziert die ausgewählten Schaltflächen in der oberen rechten Ecke des Dialog Felds.|
|Format.CenterHorizontal|**STRG** + **UMSCHALT** + **F9**|Zentriert die Steuerelemente horizontal im Dialogfeld.|
|Format.CenterVertical|**STRG** + **F9**|Zentriert die Steuerelemente im Dialogfeld vertikal.|
|Format.CheckMnemonics|**STRG** + **M**|Überprüft die Eindeutigkeit von mnetmonics.|
|Format.SizeToContent|**UMSCHALT** + **F7**|Ändert die Größe der ausgewählten Steuerelemente an den Beschriftungs Text.|
|Format.SpaceAcross|**ALT** + **NACH-LINKS-TASTE**|Die ausgewählten Steuerelemente werden gleichmäßig horizontal angeordnet.|
|Format.SpaceDown|**Alt** + **Pfeil nach unten**|Gibt die ausgewählten Steuerelemente gleichmäßig vertikal an.|
|Format.TabOrder|**STRG** + **D**|Legt die Reihenfolge der Steuerelemente innerhalb des Dialog Felds fest.|
|Format.TestDialog|**STRG** + **T**|Führt das Dialogfeld aus, um Darstellung und Verhalten zu testen.|
|Format.ToggleGuides|**STRG** + **G**|Zyklen zwischen keinem Raster, Richtlinien und einem Raster für die Bearbeitung des Dialog Felds.|

- Um die Tastenkombinationen zu ändern, wechseln Sie zu Menü **Tools** > Optionen, und wählen Sie im Ordner **Umgebung** die **Option** **Tastatur** aus.

   Weitere Informationen finden Sie unter [Identifizieren und Anpassen von Tastenkombinationen](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

- Um die Einstellungen zu ändern, wechseln Sie zu Menü **Tools** > **Einstellungen importieren und exportieren**.

   Die in den Dialogfeldern verfügbaren Optionen sowie die Namen und Positionen der angezeigten Menübefehle können sich von den in der **Hilfe** beschriebenen Optionen abhängig von den aktiven Einstellungen oder der Version unterscheiden.  Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).

## <a name="requirements"></a>Requirements (Anforderungen)

Win32

## <a name="see-also"></a>Weitere Informationen

[Ressourcen-Editor](../windows/resource-editors.md)<br/>
[Vorgehensweise: Erstellen eines Dialog Felds](../windows/creating-a-new-dialog-box.md)<br/>
[Dialogfeldsteuerelemente](../windows/controls-in-dialog-boxes.md)<br/>
<!--
[Controls](../mfc/controls-mfc.md)<br/>
[Control Classes](../mfc/control-classes.md)<br/>
[Dialog Box Classes](../mfc/dialog-box-classes.md)<br/>
[Dialog Box Controls and Variable Types](../ide/dialog-box-controls-and-variable-types.md)-->

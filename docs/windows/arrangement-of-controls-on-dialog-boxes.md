---
title: 'Gewusst wie: Layoutsteuerelemente (C++) | Microsoft-Dokumentation'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog.grouping
- vc.editors.dialog.combo
helpviewer_keywords:
- controls [C++], positioning
- dialog box controls [C++], placement
- Dialog Editor [C++], arranging controls
- Dialog Editor [C++], guides and margins
- guides, clearing
- guides
- dialog box controls [C++], placement
- controls [C++], guides and margins
- guides, creating
- guides, moving
- margins, moving
- DLUs (dialog units)
- controls [C++], aligning
- Dialog Editor [C++], snap to guides
- guides, tick mark interval
- dialog box controls [C++], placement
- guides, aligning controls
- dialog units (DLUs)
- snap to guides (Dialog editor)
- controls [C++], sizing
- tick mark interval in Dialog editor
- controls [C++], snap to guides/grid
- guides, disabling snapping
- controls [C++], snap to guides/grid
- controls [C++], layout grid
- snap to layout grid
- grids, turning on or off
- layout grid in Dialog Editor
- grids, changing size
- grid spacing
- guides, settings
- layout grid in Dialog Editor
- controls [C++], snap to guides/grid
- Guide Settings dialog box (Dialog editor)
- controls [C++], aligning
- controls [C++], positioning
- Space Evenly command
- dialog box controls [C++], placement
- Center in Dialog command
- Arrange Buttons command
- buttons, arranging push buttons in dialog boxes
- push buttons
- member variables, adding to radio button groups
- variables, dialog box control member variables
- dialog box controls [C++], grouping radio buttons
- grouping controls
- radio buttons [C++], grouping on dialog boxes
- controls [C++], tab order
- focus, tab order
- tab controls [C++], tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls [C++], tab order
- Dialog Editor [C++], selecting controls
- dominant controls
- dialog box controls [C++], selecting in editor
- controls [C++], selecting
- size, controls
- controls [C++], dominant
- controls [C++], removing from groups
- Dialog Editor [C++], dominant control
- Size to Content command
- size, controls
- text, autosizing controls to fit text
- controls [C++], sizing
- Make Same Size command
- combo boxes, sizing
- list controls [C++], scroll bar width
- CListBox::SetHorizontalExtent
- controls [C++], scroll bar
- scroll bars [C++], displaying in controls
- horizontal scroll bar width
- CListBox class, scroll bar width
- scroll bars [C++], width
ms.assetid: 832491cf-98af-42e5-a854-2cb135fd45c6
ms.openlocfilehash: ee732cfb414f011e95edbbb57b218d81179d44f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168576"
---
# <a name="how-to-layout-controls-c"></a>Gewusst wie: Layoutsteuerelemente (C++)

Der **Dialog-Editor** bietet Layouttools, mit denen Steuerelemente automatisch ausgerichtet und angepasst werden. Für die meisten Aufgaben können Sie die [Symbolleiste des Dialog-Editors](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)verwenden. Alle Symbolleisten Befehle des **Dialog-Editors** sind auch im Menü **Format** verfügbar, und die meisten verfügen über [Tastenkombinationen](../windows/accelerator-keys-for-the-dialog-editor.md).

Viele Layoutbefehle für Dialogfelder sind nur verfügbar, wenn mehr als ein Steuerelement ausgewählt ist. Sie können ein einzelnes Steuerelement oder mehrere Steuerelemente auswählen, und wenn mehr als ein Steuerelement ausgewählt ist, wird das erste Steuerelement standardmäßig als beherrschendes Steuerelement ausgewählt.

Der Speicherort, die Höhe und die Breite des aktuellen Steuer Elements werden in der unteren rechten Ecke der Statusleiste angezeigt. Wenn das gesamte Dialogfeld ausgewählt ist, wird in der Statusleiste die Position des Dialog Felds als Ganzes und seine Höhe und Breite angezeigt.

## <a name="arrange-controls"></a>Steuerelemente anordnen

Sie können Steuerelemente in Dialogfeldern mit dem **Dialog-Editor** in einem von drei verschiedenen Zuständen anordnen:

- Legen Sie mit Führungslinien und Rändern in als Standard fest.

- Mit dem Layoutraster in.

- Ohne Snap-oder Ausrichtungs Features.

Die [Symbolleiste des Dialog-Editors](../windows/showing-or-hiding-the-dialog-editor-toolbar.md) enthält Schaltflächen, die den Zustand Steuern.

- Um den Status zu ändern, wählen Sie das entsprechende Symbol aus, oder wechseln Sie zum Menü **Format** > Einstellungen für die **Richt**Linie.

Das Dialogfeld " **Führungslinien Einstellungen** " verfügt über die folgenden Eigenschaften:

|Eigenschaft|BESCHREIBUNG|
|---|---|
|**Layouthandbücher**|Zeigt die Einstellungen für die layouthandbücher an.|
|**None**|Blendet Layouttools aus.|
|**Lineale und Führungslinien**|Wenn diese Option aktiviert ist, werden den Layouttools Lineale hinzugefügt, und Sie können Führungslinien in den Linealen platzieren. Die Standard Handbücher sind die Ränder.|
|**Raster**|Erstellt ein Layoutraster. Neue Steuerelemente werden automatisch am Raster ausgerichtet.|
|**Raster Abstand**|Zeigt die Einstellungen für den Raster Abstand in Dialogfeld Einheiten (DLUs) an.|
|**Breite: DLUs**|Legt die Breite des Layoutrasters in DLUs fest. Eine horizontale dlu ist die durchschnittliche Breite der Dialogfeld Schriftart dividiert durch 4.|
|**Höhe: DLUs**|Legt die Höhe des Layoutrasters in DLUs fest. Eine vertikale DLU ist die durchschnittliche Höhe der Dialogfeld Schriftart dividiert durch 8.|

### <a name="guides-and-margins"></a>Führungslinien und Ränder

Unabhängig davon, ob Sie Steuerelemente verschieben, Steuerelemente hinzufügen oder ein aktuelles Layout neu anordnen, können Sie mithilfe von Führungslinien und Rändern Steuerelemente in einem Dialogfeld genau ausrichten.

Wenn Sie ein Dialogfeld erstellen, werden vier geänderte Führungslinien, die als Ränder bezeichnet werden, bereitgestellt und als blaue gepunktete Linien angezeigt.

- Wenn Sie Ränder verschieben möchten, ziehen Sie den Rand an die neue Position.

- Um einen Rand zu entfernen, verschieben Sie den Rand an eine Nullposition.

- Um den Rand zurückzukehren, platzieren Sie den Mauszeiger über der Null-Position des Rangs und bewegen den Rand in die Position.

Führungslinien werden als blaue gepunktete Linien über das Dialogfeld angezeigt, das im Editor angezeigt wird, und die entsprechenden Pfeile in den Linealen am oberen und linken Rand des **Dialog-Editors**. Die Zieh Punkte von Steuerelementen werden an Führungslinien ausgerichtet, wenn die Steuerelemente verschoben werden, und Führungslinien werden an Steuerelemente angedockt, wenn keine Steuerelemente vorhanden sind, die zuvor an den Wenn ein Leitfaden verschoben wird, werden auch Steuerelemente, die an ihn ausgerichtet sind, ebenfalls verschoben. Die Größe von Steuerelementen, die an mehr als einem Leitfaden geleitet werden, wird geändert, wenn eine der Führungslinien verschoben wird.

- Um einen Leitfaden innerhalb des Lineals zu erstellen, wählen Sie einmal aus, um eine Anleitung zu erstellen, oder Doppelklicken Sie auf, um das Dialogfeld " **Führungslinien Einstellungen** " zu öffnen, in dem Sie die Einstellungen

- Wenn Sie eine Anleitung im Dialogfeld festlegen möchten, wählen Sie das Handbuch aus, und ziehen Sie es an eine neue Position, oder wählen Sie den Pfeil im Lineal aus, um das zugehörige Handbuch zu ziehen.

   Die Koordinaten des Handbuchs werden in der Statusleiste am unteren Rand des Fensters und im Lineal angezeigt, oder bewegen Sie den Mauszeiger über den Pfeil im Lineal, um die genaue Position des Handbuchs anzuzeigen.

- Wenn Sie ein Handbuch löschen möchten, ziehen Sie das Handbuch aus dem Dialogfeld heraus, oder ziehen Sie den entsprechenden Pfeil aus dem Lineal.

Die Teil Striche in den Linealen, die den Abstand von Führungslinien und Steuerelementen bestimmen, werden durch Dialog Einheiten (DLUs) definiert. Eine DLU basiert auf der Größe der Dialogfeld Schriftart, normalerweise 8-Punkt-MS-Shell-Dlg. Eine horizontale dlu ist die durchschnittliche Breite der Dialogfeld Schriftart dividiert durch vier. Eine vertikale DLU ist die durchschnittliche Höhe der Schriftart dividiert durch 8.

- Um die Intervalle der Teil Striche zu ändern, wechseln Sie zu Menü **Format** > Einstellungen für die **Richt**Linie, und geben Sie dann im Feld **Raster Abstand** eine neue Breite und Höhe in DLUs an.

### <a name="layout-grid"></a>Layoutraster

Wenn Sie Steuerelemente in einem Dialogfeld platzieren oder anordnen, verwenden Sie das Layoutraster für eine präzisere Positionierung. Wenn das Raster aktiviert ist, werden die Steuerelemente an die gepunkteten Linien des Rasters angedockt, als wäre sie magnetisiert.

- Um das Layoutraster ein-oder auszuschalten, wechseln Sie zum Menü **Format** > Einstellungen für das- **Handbuch** , und aktivieren oder deaktivieren Sie die **Raster** Schaltfläche.

   Sie können das Raster in einzelnen Dialog- **Editor** -Fenstern weiterhin mithilfe der **UMSCHALT Fläche Raster** auf der [Symbolleiste des Dialog-Editors](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)steuern.

- Um die Größe des Layoutrasters zu ändern, wechseln Sie zu Menü **Format** > **Einstellungen** für das Layout, und geben Sie die Höhe und Breite in DLUs für die Zellen im Raster ein. Die minimale Höhe oder Breite ist 4.

### <a name="disable-guides"></a>Deaktivieren von Führungslinien

Sie können in Verbindung mit der Maus spezielle Tasten verwenden, um die Richtungslinien der Handbücher zu deaktivieren. Wenn Sie die **alt** -Taste verwenden, werden die Ausrichtungs Effekte des ausgewählten Handbuchs deaktiviert. Wenn Sie eine Führungslinie mit der **UMSCHALT** Taste verschieben, wird verhindert, dass sich die Steuerelemente mit dem Leitfaden bewegen.

- Ziehen Sie das Steuerelement, während Sie die **alt** -Taste gedrückt halten, um den Richtungs Effekt der Handbücher zu deaktivieren.

- Wenn Sie Führungslinien verschieben möchten, ohne die gedockten Steuerelemente zu verschieben, ziehen Sie den Leitfaden, während die **UMSCHALT** Taste gedrückt ist

- Um die Führungslinien zu deaktivieren, wechseln Sie zu Menü **Format** > **Einstellungen**. Wählen Sie dann unter **layouthandbücher**die Option **keine**aus.

   > [!TIP]
   > Sie können auch die Verknüpfung im Menü **Format** verwenden, um die Handbücher zu **wechseln > .**

## <a name="select-controls"></a>Steuerelemente auswählen

Wählen Sie Steuerelemente aus, um Sie zu verkleinern, auszurichten, zu verschieben, zu kopieren oder zu löschen, und schließen Sie dann den gewünschten Vorgang ab. In den meisten Fällen müssen Sie mehr als ein Steuerelement auswählen, um die Größen Anpassungs-und Ausrichtungs Tools auf der [Symbolleiste des Dialog-Editors](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)zu verwenden.

Wenn ein Steuerelement ausgewählt ist, verfügt es über einen schattierten Rahmen um das Steuerelement mit Solid (aktiven) oder hohlen (inaktiven) Größen Anpassungs Handles, kleinen Quadraten, die im Auswahl Rahmen angezeigt werden. Wenn mehrere Steuerelemente ausgewählt sind, verfügt das bestimmende Steuerelement über ein solides Größen Anpassungs handle, und alle anderen ausgewählten Steuerelemente verfügen über ein leeres Steuerelement.

- Wählen Sie zum Auswählen von Steuerelementen im [Fenster Toolbox](/visualstudio/ide/reference/toolbox)das Tool **Zeiger** aus, und führen Sie einen der folgenden Schritte aus, um die Auswahl vorzunehmen:

  - Ziehen Sie den Mauszeiger, um ein Auswahlfeld um die Steuerelemente zu zeichnen, die Sie im Dialogfeld auswählen möchten. Wenn Sie die Maustaste loslassen, werden alle Steuerelemente innerhalb und überschneidende das Auswahlfeld ausgewählt.

  - Halten Sie die **UMSCHALT** Taste gedrückt, und wählen Sie die Steuerelemente aus, die Sie in die Auswahl einschließen möchten.

  - Halten Sie die **STRG** -Taste gedrückt, und wählen Sie die Steuerelemente aus, die Sie in die Auswahl einschließen möchten.

- Halten Sie die **UMSCHALT** Taste gedrückt, und wählen Sie das Steuerelement aus, das Sie hinzufügen oder entfernen möchten, um ein Steuerelement aus der Gruppe ausgewählter Steuerelemente hinzuzufügen oder zu entfernen.

### <a name="dominant-controls"></a>Vorherrschende Steuerelemente

Wenn Sie mehrere Steuerelemente anpassen oder ausrichten, verwendet der **Dialog-Editor** das dominante Steuerelement, um zu bestimmen, wie die anderen Steuerelemente dimensioniert oder ausgerichtet werden. Standardmäßig ist das bestimmende Steuerelement das erste Steuerelement, das ausgewählt wird.

- Halten Sie zum Angeben des bestimmenden Steuer Elements die **STRG** -Taste gedrückt, und wählen Sie das Steuerelement aus, das Sie verwenden möchten, um die Größe oder Position anderer Steuerelemente *zuerst*zu beeinflussen. Wenn Sie die **STRG** -Taste gedrückt halten und ein Steuerelement in einer Auswahl auswählen, wird dieses Steuerelement auch das bestimmende Steuerelement in dieser Auswahl.

- Wenn Sie das bestimmende Steuerelement ändern möchten, löschen Sie die aktuelle Auswahl, indem Sie außerhalb aller aktuell *ausgewählten Steuerelemente*auswählen und das oben beschriebene Verfahren wiederholen.

> [!NOTE]
> Die Größen Zieh Punkte des bestimmenden Steuer Elements sind solide, während die Handles der untergeordneten Steuerelemente hohl sind. Alle weiteren Anpassungen der Größe oder Ausrichtung basieren auf dem vorherrschenden Steuerelement.

## <a name="size-controls"></a>Größen Steuerelemente

Verwenden Sie die Zieh Punkte, um die Größe eines Steuer Elements zu ändern. Wenn der Zeiger auf einem Größen Anpassungs handle positioniert ist, wird die Form geändert, um die Richtung anzugeben, in der die Größe des Steuer Elements geändert werden kann. Aktive Größen Zieh Punkte sind solide, und wenn ein Größen Anpassungs handle hohl ist, kann die Größe des Steuer Elements entlang dieser Achse nicht geändert werden.

- Wählen Sie das Steuerelement aus, und ziehen Sie die Zieh Punkte, um die Größe eines Steuer Elements zu ändern.

  - Größen Handles am oberen und der Seite ändern die horizontale oder vertikale Größe.

  - Größen Zieh Punkte an den Ecken ändern sowohl die horizontale als auch die vertikale Größe.

   > [!TIP]
   > Sie können die Größe des Steuer Elements eine Dialog Einheit (DLU) gleichzeitig ändern, indem Sie die **UMSCHALT** Taste gedrückt halten und die Pfeiltasten nach **Rechts** und **nach unten** verwenden.

- Zum automatischen Anpassen der Größe eines Steuer Elements an den darin enthaltenen Text wechseln Sie zum Menü **Format** , oder klicken Sie mit der rechten Maustaste auf das Steuerelement, und wählen Sie **Größe für Inhalt**.

- Um die Größe der Steuerelemente zu ändern, wählen Sie die Steuerelemente aus, die Sie ändern möchten, und wechseln Sie zum Menü **Format** , > die **gleiche Größe**zu ändern, und wählen Sie dann entweder **sowohl**, **Höhe**oder **Breite**.

   Sie ändern die Größe einer Gruppe von Steuerelementen basierend auf der Größe des bestimmenden Steuer Elements, bei dem es sich um das zuerst in der Reihe ausgewählte Steuerelement handelt. Die endgültige Größe der Steuerelemente in der Gruppe hängt von der Größe des herrschenden Steuer Elements ab.

- Um eine Gruppe von Steuerelementen mit Führungslinien zu verkleinern, können Sie eine Seite des Steuer Elements (oder Steuerelemente) an eine Führungslinie ausrichten und dann einen Leitfaden auf die andere Seite des Steuer Elements (oder Steuerelemente) ziehen. Nun können Sie eine der beiden Führungslinien in die Größe des Steuer Elements (oder Steuerelemente) verschieben.

   Wenn erforderlich mit mehreren Steuerelementen, wird jede Größe an die zweite Stelle geleitet.

### <a name="other-controls"></a>Andere Steuerelemente

Sie können ein Kombinations Feld anpassen, wenn Sie es dem Dialogfeld hinzufügen. Sie können auch die Größe des Dropdown-Listen Felds angeben. Weitere Informationen finden Sie unter [Hinzufügen von Werten zu einem Kombinations Feld-Steuer](../windows/adding-values-to-a-combo-box-control.md)Element.

1. Wählen Sie die Dropdown Schaltfläche rechts neben dem Kombinations Feld aus.

   ![Pfeil in einem Kombinations Feld in einem MFC-Projekt](../mfc/media/vccomboboxarrow.gif "vccomboboxpfeil")

   Der Umriss des-Steuer Elements wird geändert, um die Größe des Kombinations Felds mit dem erweiterten Dropdown-Listen Bereich anzuzeigen.

1. Verwenden Sie den unteren Größen Zieh Punkt, um die Anfangs Größe des Dropdown-Listen Bereichs zu ändern.

   ![Kombinations&#45;Feld-Größenanpassung in einem MFC-Projekt](../mfc/media/vccomboboxsizing.gif "vccomboboxsizing")

1. Klicken Sie erneut auf den Dropdown Pfeil, um die Dropdown Liste des Kombinations Felds zu schließen.

> [!NOTE]
> Wenn Sie einem Dialogfeld mithilfe von MFC ein Listenfeld mit horizontaler Bild Lauf Leiste hinzufügen, wird die Schiebe Leiste nicht automatisch in der Anwendung angezeigt.
>
> Legen Sie eine maximale Breite für das breiteste Element fest, indem Sie [CListBox:: sethorizontalblock](../mfc/reference/clistbox-class.md#sethorizontalextent) in Ihrem Code aufrufen. Wenn dieser Wert nicht festgelegt ist, wird die Schiebe Leiste nicht angezeigt, auch wenn die Elemente im Listenfeld breiter als das Feld sind.

## <a name="align-controls"></a>Ausrichten von Steuerelementen

- Wählen Sie zum Ausrichten von Steuerelementen die Steuerelemente aus, die Sie ausrichten möchten. Wechseln Sie zum Menü **Format** > **Ausrichten** , und wählen Sie eine der folgenden Ausrichtungen aus:

   |Ausrichtung|BESCHREIBUNG|
   |-----|-----------|
   |**Links**|Richtet die ausgewählten Steuerelemente an der linken Seite aus.|
   |**Zentren**|Richtet die ausgewählten Steuerelemente horizontal entlang ihrer Mittelpunkte aus.|
   |**Rechte**|Richtet die ausgewählten Steuerelemente an der rechten Seite aus.|
   |**Flächen**|Richtet die ausgewählten Steuerelemente an Ihren oberen Rändern aus.|
   |**Mittig**|Richtet die ausgewählten Steuerelemente vertikal entlang ihrer mittleren Punkte aus.|
   |**Ausrichten**|Richtet die ausgewählten Steuerelemente an den unteren Rändern aus.|

   Stellen Sie sicher, dass Sie zuerst das Steuerelement auswählen, das Sie als beherrschend festlegen möchten, oder legen Sie es als beherrschendes Steuerelement fest, bevor Sie den Befehl "Alignment" oder "Sizing" ausführen, da die letzte Position der Gruppe von Steuerelementen von der Position des herrschenden

- Wählen Sie die Steuerelemente aus, die Sie neu anordnen möchten. Wechseln Sie > **Bereich gleichmäßig** zum Menü **Format** , und wählen Sie eine der folgenden Abstands Ausrichtungen:

   |Spacing|BESCHREIBUNG|
   |---|---|
   |**Über**|Die Leerzeichen-Steuerelemente werden gleichmäßig zwischen dem linken und dem äußersten rechten Steuerelement ausgewählt.|
   |**Nach unten**|Die Leerzeichen-Steuerelemente werden gleichmäßig zwischen dem obersten und dem untersten Steuerelement ausgewählt.|

- Wählen Sie zum Zentrieren der Steuerelemente das Steuerelement oder die Steuerelemente, die Sie neu anordnen möchten Wechseln Sie in das Menü **Format** > **Center in Dialog** Feld, und wählen Sie eine der folgenden Optionen aus:

   |Vorbereitung|BESCHREIBUNG|
   |---|---|
   |**Vertikal**|Zentrieren Sie Steuerelemente vertikal im Dialogfeld.|
   |**Horizontal**|Zentrieren Sie die Steuerelemente horizontal im Dialogfeld.|

- Zum Ausrichten von Push-Schaltflächen wählen Sie eine oder mehrere Schaltflächen aus. Wechseln Sie zum Menü **Format** > **Schaltflächen anordnen**, und wählen Sie dann eine der folgenden Optionen aus:

   |Vorbereitung|BESCHREIBUNG|
   |---|---|
   |**Right**|Richtet die pushschaltflächen am rechten Rand des Dialog Felds aus.|
   |**Bottom** (Unten)|Richtet die pushschaltflächen am unteren Rand des Dialog Felds aus.|

   Wenn Sie ein anderes Steuerelement als eine Schaltfläche für den Push auswählen, ist seine Position nicht betroffen.

## <a name="requirements"></a>Requirements (Anforderungen)

Win32

## <a name="see-also"></a>Weitere Informationen

[Dialog Feld-Steuerelemente verwalten](controls-in-dialog-boxes.md)<br/>
[Gewusst wie: Hinzufügen, bearbeiten oder Löschen von Steuerelementen](adding-editing-or-deleting-controls.md)<br/>
[Gewusst wie: Definieren von Steuerelement Zugriff und-Werten](defining-mnemonics-access-keys.md)<br/>

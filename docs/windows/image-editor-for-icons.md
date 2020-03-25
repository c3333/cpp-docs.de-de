---
title: Bildbearbeitung für Symbole (C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.cursor.F1
- vc.editors.icon.F1
- vc.editors.cursor
- vc.editors.bitmap.F1
- vc.editors.bitmap
- vc.editors.dialog.GridSettings
- vc.editors.gridsettings
- vc.editors.icon
- vc.editors.texttool
helpviewer_keywords:
- editors, images
- resource editors [C++], graphics
- Image editor [C++]
- resource editors [C++], Image editor
- Image menu
- Grid Settings dialog box [C++]
- Graphics toolbar
- Image editor [C++], toolbar
- Image editor [C++], Option selector
- Properties window
- Option selector, Image editor
- toolbars [C++], showing
- toolbars [C++], hiding
- text, adding to an image
- Text Tool dialog box [C++]
- Text Tool Font dialog box [C++]
- fonts, changing on an image
- text, on images
- graphics editor [C++]
- Image editor [C++], panes
- Image editor [C++], magnification
- grids, pixel
- pixel grid, Image editor
- Image editor [C++], pixel grid
- Image editor [C++], grid settings
- grid settings, Image editor
ms.assetid: 586d2b8b-0348-4883-a85d-1ff0ddbf14dd
ms.openlocfilehash: 47798b5d628484482dffdc963d6e8c7a809f42ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168015"
---
# <a name="image-editor-for-icons-c"></a>Bildbearbeitung für Symbole (C++)

Wenn Sie in **Projektmappen-Explorer**eine Bilddatei (z. b. ico, BMP, PNG) auswählen, wird das Bild im Bild- **Editor** auf die gleiche Weise geöffnet, wie Code Dateien im **Code-Editor**geöffnet werden. Wenn eine Registerkarte **Bild** Bearbeitung aktiv ist, werden Symbolleisten mit vielen Tools zum Erstellen und Bearbeiten von Bildern angezeigt. Zusammen mit Bitmaps, Symbolen und Cursorn können Sie Bilder im GIF-oder JPEG-Format bearbeiten. verwenden Sie dazu die Befehle im Menü **Bild** und die Tools auf der Symbolleiste des **Bild-Editors** .

Grafische Ressourcen sind die Images, die Sie für Ihre Anwendung definieren. Sie können frei handlinie zeichnen oder mithilfe von Formen zeichnen. Sie können Teile eines Bilds zum Bearbeiten, kippen oder Ändern der Größe auswählen, oder Sie können einen benutzerdefinierten Pinsel aus einem ausgewählten Teil eines Bilds erstellen und mit diesem Pinsel zeichnen. Sie können Bildeigenschaften definieren, Bilder in verschiedenen Formaten speichern und Bilder von einem Format in ein anderes konvertieren.

> [!NOTE]
> Mit dem **Bild-Editor**können Sie 32-Bit-Bilder anzeigen, Sie können Sie jedoch nicht bearbeiten.

Sie können auch die **Bild** Bearbeitung und den [Binär-Editor](binary-editor.md) verwenden, um mit Ressourcen Dateien in verwalteten Projekten zu arbeiten. Bei den zu bearbeitenden verwalteten Ressourcen muss es sich um verknüpfte Ressourcen handeln. Die Ressourcen-Editoren von Visual Studio unterstützen die Bearbeitung von eingebetteten Ressourcen nicht

Zusätzlich zum Erstellen neuer grafischer Ressourcen können Sie [vorhandene Images](../windows/how-to-copy-resources.md#import-and-export-resources) zur Bearbeitung importieren und Sie dann zu Ihrem Projekt hinzufügen. Sie können auch Bilder öffnen und bearbeiten, die nicht Teil eines Projekts für die [eigenständige Bildbearbeitung](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md)sind.

Informationen zum Bild- **Editor**finden Sie unter [Erstellen eines Symbols oder eines anderen Bilds](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md), [Bearbeiten eines Bilds](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), [Verwenden eines Zeichnungs Tools](../windows/using-a-drawing-tool-image-editor-for-icons.md), [Arbeiten mit Farben](../windows/working-with-color-image-editor-for-icons.md)und [Tasten](../windows/accelerator-keys-image-editor-for-icons.md)Kombinationen.

> [!NOTE]
> Laden Sie die **Visual Studio-Bildbibliothek** kostenlos herunter. Sie enthält zahlreiche Animationen, Bitmaps und Symbole, die Sie in Ihren Anwendungen verwenden können. Weitere Informationen zum Herunterladen der Bibliothek finden Sie in der [Visual Studio-Bildbibliothek](/visualstudio/designers/the-visual-studio-image-library).

## <a name="image-menu"></a>Menü "Bild"

Das Menü **Bild** , das nur angezeigt wird, wenn der **Bild-Editor** aktiv ist, über Befehle zum Bearbeiten von Bildern, zum Verwalten von Farbpaletten und zum Festlegen der Fenster Optionen für den Bild- **Editor** verfügt. Außerdem sind Befehle zum Verwenden von Geräte Images bei der Arbeit mit Symbolen und Cursorn verfügbar.

|Get-Help|BESCHREIBUNG|
|---|---|
|**Farben umkehren**|Kehrt Ihre Farben um.|
|**Horizontal spiegeln**|Kippt das Bild oder die Markierung horizontal.|
|**Vertikal spiegeln**|Kippt das Bild oder die Auswahl vertikal.|
|**Drehen von 90 Grad**|Dreht das Bild oder die Auswahl um 90 Grad.|
|**Fenster "Farben" anzeigen**|Öffnet das Fenster **Farben** , in dem Sie die Farben auswählen können, die für das Bild verwendet werden sollen.|
|**Auswahl als Pinsel verwenden**|Ermöglicht es Ihnen, einen benutzerdefinierten Pinsel aus einem Teil eines Bilds zu erstellen.<br/><br/>Ihre Auswahl wird zu einem benutzerdefinierten Pinsel, der die Farben in der Auswahl über das Bild verteilt. Kopien der Auswahl bleiben entlang des Zieh Pfades. Wenn Sie langsamer ziehen, werden weitere Kopien erstellt.|
|**Auswahl kopieren und gliedern**|Erstellt eine Kopie der aktuellen Auswahl und versieht sie mit einer Umrisslinie.<br/><br/>Wenn die Hintergrundfarbe in der aktuellen Auswahl enthalten ist, wird Sie ausgeschlossen, wenn Sie die Option transparent ausgewählt haben.
|**Farben anpassen**|Öffnet die **Benutzerdefinierte Farbauswahl**, mit der Sie die Farben anpassen können, die Sie für Ihr Bild verwenden.|
|**Palette laden**|Öffnet das Dialogfeld **Farb Palette laden** , in dem Sie Palettenfarben laden können, die zuvor in eine PAL-Datei gespeichert wurden.|
|**Palette speichern**|Speichert die Palettenfarben in einer PAL-Datei.|
|**Nicht transparent zeichnen**|Wenn diese Option ausgewählt ist, wird die aktuelle Auswahl nicht transparent.<br/><br/>Wenn diese Option deaktiviert ist, wird die aktuelle Auswahl transparent.|
|**Symbolleisten-Editor**|Öffnet das [Dialogfeld neue Symbolleisten Ressource](../windows/new-toolbar-resource-dialog-box.md).|
|**Raster Einstellungen**|Öffnet das Dialogfeld **Raster Einstellungen** , in dem Sie Raster für das Bild angeben können.|
|**Neuer Bildtyp**|Öffnet das [Dialogfeld Neuer \<Gerät > Bildtyp](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md).<br/><br/>Eine einzelne Symbol Ressource kann mehrere Bilder verschiedener Größen enthalten, und Windows kann abhängig davon, wie Sie angezeigt wird, die entsprechende Symbolgröße verwenden. Ein neuer Gerätetyp ändert nicht die Größe des Symbols, sondern erstellt stattdessen ein neues Bild innerhalb des Symbols. Gilt nur für Symbole und Cursor.|
|**Aktuelles Symbol/Cursor Bildtyp**|Öffnet ein Untermenü, in dem die ersten neun verfügbaren Cursor-oder Symbolbilder aufgelistet sind. Mit dem letzten Befehl im Untermenü ( **mehr**) wird das [Dialogfeld \<Gerät > Abbild Öffnen geöffnet](../windows/open-device-image-dialog-box-image-editor-for-icons.md).|
|**Bildtyp löschen**|Löscht das ausgewählte Geräte Image.|
|**Tools**|Öffnet ein Untermenü, das alle Tools enthält, die auf der **Bild-Editor** -Symbolleiste verfügbar sind.|

Im Dialogfeld **Raster Einstellungen** können Sie die Raster Einstellungen für das Bild angeben und Rasterlinien über dem bearbeiteten Bild anzeigen. Die Zeilen sind nützlich für die Bearbeitung des Bilds, werden jedoch nicht als Teil des Bilds gespeichert.

|Eigenschaft|BESCHREIBUNG|
|---|---|
|**Pixel Raster**|Wenn dieses Kontrollkästchen aktiviert ist, wird ein Raster um jedes Pixel im **Bild-Editor**angezeigt.<br/><br/>Das Raster wird nur bei 4 × und höherer Auflösung angezeigt.|
|**Kachel Raster**|Wenn diese Option ausgewählt ist, wird ein Raster um die Pixelblöcke im **Bild-Editor**angezeigt, die durch die Werte für den Raster Abstand angegeben werden.|
|**Width**|Gibt die Breite jedes Kachel Blocks an.<br/><br/>Diese Eigenschaft ist nützlich, wenn Bitmaps gezeichnet werden, die mehrere Bilder enthalten, die in regelmäßigen Abständen angeordnet werden.|
|**Height**|Gibt die Höhe jedes Kachel Blocks an.<br/><br/>Diese Eigenschaft ist nützlich, wenn Bitmaps gezeichnet werden, die mehrere Bilder enthalten, die in regelmäßigen Abständen angeordnet werden.|

## <a name="toolbar"></a>Symbolleiste

Die Symbolleiste des **Bild-Editors** enthält Tools zum Zeichnen, zeichnen, eingeben von Text, löschen und Bearbeiten von Sichten. Sie enthält auch eine Options Auswahl, mit der Sie Optionen für die Verwendung der einzelnen Tools auswählen können. Beispielsweise können Sie aus verschiedenen Pinsel breiten, Vergrößerungsfaktoren und Linienstilen auswählen.

Alle Tools, die auf der Symbolleiste des **Bild-Editors** verfügbar sind, sind auch über das Menü **Bild** > **Tools**verfügbar. Wählen Sie das gewünschte Tool oder die gewünschte Option aus, um die **Bild-Editor** -Symbolleiste und die **options** Auswahl zu verwenden.

![Symbolleiste der Bildbearbeitung](../mfc/media/vcimageeditortoolbar.gif "vcimageeditor Toolbar")<br/>
Symbolleiste der **Bild** Bearbeitung

> [!TIP]
> Quick Infos werden angezeigt, wenn Sie den Cursor über eine Symbolleisten Schaltfläche bewegen. Diese Tipps können Ihnen helfen, die Funktion der einzelnen Schaltflächen zu identifizieren.

Da viele der Zeichnungs Tools über die [Tastatur](../windows/accelerator-keys-image-editor-for-icons.md)verfügbar sind, ist es manchmal sinnvoll, die Bild- **Editor** -Symbolleiste auszublenden.

- Zum Anzeigen oder Ausblenden der Symbolleiste des **Bild-Editors** wechseln Sie > **Symbolleisten** zur Menü **Ansicht** , und wählen Sie **Bild-Editor**aus.

> [!NOTE]
> Elemente aus dieser Symbolleiste werden nicht verfügbar angezeigt, wenn eine Bilddatei aus dem aktuellen Projekt oder der aktuellen Projekt Mappe nicht im **Bild-Editor**geöffnet ist.

### <a name="option-selector"></a>Optionsauswahl

Mit der **Option** Selector können Sie die Breite einer Linie, eines Pinselstrichs usw. angeben. Das Symbol auf der **options** Auswahl Schaltfläche ändert sich je nach ausgewähltem Tool.

![Zeichnungs&#45;Form Auswahl auf der Symbolleiste des Bild-Editors](../mfc/media/vcimageeditortoolbaroptionselector.gif "vcimageeditortoolbaroptionselector")<br/>
**Options** Auswahl auf der Symbolleiste des **Bild-Editors**

### <a name="text-tool"></a>Texttool

Mit dem Dialogfeld **Text Tool** können Sie einer Cursor-, Bitmap-oder Symbol Ressource Text hinzufügen.

Um auf dieses Dialogfeld zuzugreifen, öffnen Sie den **Bild-Editor** , und navigieren Sie zu Menü **Bild** > **Tools**, und wählen Sie dann den Befehl **Text Tool** aus.

> [!TIP]
> Sie können mit der rechten Maustaste auf das Dialogfeld **Text Tool** klicken, um auf ein Standardkontext Menü zuzugreifen, das eine Liste der standardmäßigen Windows-Befehle enthält.

Öffnen Sie das Dialogfeld **Text Tool Schriftart** , um die Schriftart, den Stil oder die Größe der Cursor Schriftart zu ändern. Änderungen werden auf den Text angewendet, der im **Text** Bereich angezeigt wird.

Um auf dieses Dialogfeld zuzugreifen, wählen Sie die Schaltfläche **Schriftart** im Dialogfeld **Text Tool** aus. Es stehen folgende Eigenschaften zur Verfügung:

|Eigenschaft|BESCHREIBUNG|
|---|---|
|**Schriftart**|Listet die verfügbaren Schriftarten auf.|
|**Schriftschnitt**|Listet die verfügbaren Stile für die angegebene Schriftart auf.|
|**Größe**|Listet die verfügbaren Punktgrößen für die angegebene Schriftart auf.|
|**Beispiel**|Zeigt ein Beispiel dazu, wie Text mit den angegebenen Schriftart Einstellungen angezeigt wird.|
|**Skript**|Listet die verfügbaren sprach Skripts für die angegebene Schriftart auf.<br/><br/>Wenn Sie ein anderes sprach Skript auswählen, steht der Zeichensatz für diese Sprache zum Erstellen von mehrsprachigen Dokumenten zur Verfügung.|

#### <a name="to-change-the-font-of-text-on-an-image"></a>So ändern Sie die Schriftart des Texts eines Bilds

Im folgenden finden Sie ein Beispiel für das Hinzufügen von Text zu einem Symbol in einer Windows-Anwendung und das Bearbeiten der Schriftart des Texts.

1. Erstellen Sie C++ eine Windows Forms-Anwendung. Weitere Informationen finden Sie unter Vorgehens [Weise: Erstellen von Windows Forms Anwendungen](/previous-versions/visualstudio/visual-studio-2008/s69bf10x(v%3dvs.90)). Dem Projekt wird standardmäßig eine Datei " *app. ico* " hinzugefügt.

1. Doppelklicken Sie in **Projektmappen-Explorer**auf die Datei *app. ico*. Der **Bild-Editor** wird geöffnet.

1. Wechseln Sie zu Menü **Bild** > **Tools** , und wählen Sie **Text Tool**aus.

1. Geben *C++* Sie im Dialogfeld **Text Tool** den leeren Textbereich ein. Dieser Text wird in einem Feld, das in der Größe geändert werden kann, in der oberen linken Ecke von *app. ico* im **Bild-Editor**angezeigt.

1. Ziehen Sie im **Bild-Editor**das Feld mit der Größe der Größe in den Mittelpunkt der *app. ico* , um die Lesbarkeit des Texts zu verbessern.

1. Wählen Sie im Dialogfeld **Text Tool** die Schaltfläche **Schriftart** aus.

1. Im Dialogfeld **Schriftart des Texttools** :

   - Wählen Sie in der Liste der verfügbaren Schriftarten, die im Listenfeld **Schriftart** aufgeführt sind, **Times New Roman** aus.

   - Wählen Sie **Fett** in der Liste der verfügbaren Schriftart Stile aus, die im Listenfeld **Schriftart Stil** aufgeführt sind.

   - Wählen Sie **10** aus der Liste der verfügbaren Punktgrößen aus, die im Listenfeld **Größe** aufgelistet sind.

   - Klicken Sie auf **OK**. Das **Texttool** -Dialogfeld Schriftart wird geschlossen, und die neuen Schriftart Einstellungen werden auf Ihren Text angewendet.

1. Wählen Sie im Dialogfeld **Text Tool** die Option **Schließen** aus. Das Textfeld, das in der Größe geändert werden kann, wird im **Bild-Editor**ausgeblendet.

Im Textbereich wird der Text angezeigt, der als Teil der Ressource angezeigt wird. Anfänglich ist dieser Bereich leer.

> [!NOTE]
> Wenn **transparenter Hintergrund** festgelegt ist, wird nur der Text in das Bild eingefügt. Wenn nicht transparenter **Hintergrund** festgelegt ist, wird ein umgebenden Rechteck, das mit der Hintergrundfarbe gefüllt ist, hinter dem Text platziert.

## <a name="window-panes"></a>Fensterbereiche

Das Fenster **Bild-Editor** zeigt zwei Ansichten eines Bilds an, wobei die beiden Bereiche durch einen geteilten Balken getrennt werden. Zum Ändern der relativen Größe der Fensterbereiche kann der Fensterteiler seitlich gezogen werden. Der aktive Bereich ist von einem Markierungsrahmen umgeben.

Eine Ansicht ist die tatsächliche Größe, und die andere wird durch einen Standard Erweiterungs Faktor von 6 vergrößert. Die Ansichten in diesen beiden Bereichen werden automatisch aktualisiert. alle Änderungen, die Sie in einem Bereich vornehmen, werden sofort in der anderen angezeigt. Die beiden Bereiche erleichtern Ihnen das Arbeiten mit einer erweiterten Ansicht Ihres Bilds, in dem Sie einzelne Pixel unterscheiden und gleichzeitig die Auswirkung ihrer Arbeit auf die Ansicht der tatsächlichen Größe des Bilds beobachten können.

Im linken Bereich wird so viel Speicherplatz wie benötigt (bis zur Hälfte des **Bild** Fensters) verwendet, um die standardmäßige 1:1-Vergrößerungs Ansicht des Bilds anzuzeigen. Im rechten Bereich wird ein Standardbild mit der Größe 6:1 vergrößert. Sie können die Vergrößerung in jedem Bereich ändern, indem Sie auf der Symbolleiste des **Bild-Editors** oder mithilfe der Tastenkombinationen die Tastenkombination verwenden. **Magnify**

Sie können den kleineren Bereich des Bild- **Editor** -Fensters vergrößern und die beiden Bereiche verwenden, um unterschiedliche Bereiche eines großen Bilds anzuzeigen. Wählen Sie im Bereich aus, um ihn auszuwählen.

Sie können die relativen Größen der Bereiche ändern, indem Sie den Mauszeiger auf dem Trennbalken positionieren und den Trennbalken nach rechts oder links verschieben. Wenn Sie nur an einem Bereich arbeiten möchten, können Sie die Aufteilung auf eine beliebige Seite verschieben.

Wenn der **Bild Bearbeitungs** Bereich um den Faktor 4 oder höher vergrößert wird, können Sie ein Pixelraster anzeigen, das die einzelnen Pixel im Bild begrenzt.

### <a name="to-change-the-magnification-factor"></a>So ändern Sie den Vergrößerungsfaktor

Standardmäßig zeigt der **Bild-Editor** die Ansicht im linken Bereich in der tatsächlichen Größe und die Ansicht im rechten Bereich der 6-fachen tatsächlichen Größe an. Der Vergrößerungsfaktor (in der Statusleiste am unteren Rand des Arbeitsbereichs angezeigt) ist das Verhältnis zwischen der tatsächlichen Größe des Bilds und der angezeigten Größe. Der Standardfaktor ist 6, und der Bereich liegt zwischen 1 und 10.

1. Wählen Sie den Bereich **Bild-Editor** aus, dessen Vergrößerungsfaktor Sie ändern möchten.

1. Wählen Sie auf der Symbolleiste **Bild** Bearbeitung den Pfeil rechts neben dem **Vergrößerungs** Tool aus, und wählen Sie den Vergrößerungsfaktor aus dem Untermenü: **1X**, **2X**, **6x**oder **8X**aus.

   > [!NOTE]
   > Verwenden Sie die Tastenkombinationen, um einen anderen Vergrößerungsfaktor als die im Tool zum **vergrößern** zu wählen.

### <a name="to-display-or-hide-the-pixel-grid"></a>So zeigen Sie das Pixelraster an oder blenden es aus

Für alle **Bild Bearbeitungs** Bereiche mit einem Vergrößerungsfaktor von 4 oder höher können Sie ein Raster anzeigen, in dem die einzelnen Pixel im Bild getrennt sind.

1. Wechseln Sie zu Menü **Bild** > **Raster Einstellungen**.

1. Aktivieren Sie das Kontrollkästchen **Pixel Raster** , um das Raster anzuzeigen, oder deaktivieren Sie das Kontrollkästchen, um das Raster auszublenden.

## <a name="requirements"></a>Requirements (Anforderungen)

Keine

## <a name="see-also"></a>Weitere Informationen

[Ressourcen-Editor](../windows/resource-editors.md)<br/>
[Symbole](/windows/win32/menurc/icons)

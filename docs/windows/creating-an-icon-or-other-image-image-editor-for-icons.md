---
title: 'Gewusst wie: Erstellen eines Symbols oder eines anderen Bilds'
ms.date: 02/15/2019
helpviewer_keywords:
- bitmaps [C++]
- images [C++], creating
- resources [C++], creating images
- bitmaps [C++], creating
- graphics [C++], creating
- Image editor [C++], creating images
- cursors [C++], creating
- image resources [C++], display devices
- icons [C++], creating
- cursors [C++], types
- icons [C++]
- Image editor [C++], icons and cursors
- cursors [C++]
- display devices [C++], creating icons for
- cursors [C++], hot spots
- icons [C++], types
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
- New <Device> Image Type dialog box [C++]
- Custom Image dialog box [C++]
- Open <Device> Image dialog box [C++]
- New Device Image command
- display devices [C++], adding images
- cursors [C++], adding
- icons, adding
- display devices [C++], copying images
- cursors [C++], copying
- icons, copying
- cursors [C++], deleting
- display devices [C++], deleting device image
- icons, erasing
- icons, deleting
- cursors [C++], undoing changes
- icons, undoing changes
- cursors [C++], screen regions
- inverse colors [C++], device images
- transparent regions, device images
- transparency, device images
- Image editor [C++], device images
- inverse regions, device images
- cursors [C++], transparent regions
- screen colors
- regions, transparent
- icons [C++], transparent regions
- display devices [C++], transparent and screen regions
- transparent regions in devices
- regions, inverse
- colors [C++], Image editor
- device projects [C++], transparent images
- icons [C++], screen regions
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
- colors [C++], icons and cursors
- color palettes, 256-color
- palettes, 256-color
- cursors [C++], hot spots
- hot spots
- .gif files [C++], saving bitmaps as
- jpg files [C++], saving bitmaps as
- jpeg files [C++], saving bitmaps as
- .jpg files [C++], saving bitmaps as
- Image editor [C++], converting image formats
- gif files [C++], saving bitmaps as
- bitmaps [C++], converting formats
- .jpeg files [C++], saving bitmaps as
- graphics [C++], converting formats
- images [C++], converting formats
- images [C++], stand-alone editing
- Image editor [C++], converting image formats
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
ms.openlocfilehash: 931d84f16b46ea8fe21ecc0a63d20dac958ce960
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160437"
---
# <a name="how-to-create-an-icon-or-other-image"></a>Gewusst wie: Erstellen eines Symbols oder eines anderen Bilds

Sie können ein neues Bild, eine Bitmap, ein Symbol, einen Cursor oder eine Symbolleiste erstellen und dann mit dem **Bild-Editor** die Darstellung anpassen. Sie können auch eine neue Bitmap erstellen, die nach einer [Ressourcen Vorlage](../windows/how-to-use-resource-templates.md)gemustert ist.

## <a name="icons-and-cursors-image-resources-for-display-devices"></a>Symbole und Cursor: Bildressourcen für Anzeigegeräte

Symbole und Cursor sind grafische Ressourcen, die mehrere Bilder in verschiedenen Größen und Farbschemas für verschiedene Arten von Anzeigegeräten enthalten können. Ein Cursor verfügt auch über einen Hotspot, den Speicherort, den Windows zum Nachverfolgen seiner Position verwendet. Sowohl Symbole als auch Cursor werden mit dem Bild- **Editor**erstellt und bearbeitet, ebenso wie Bitmaps und andere Bilder.

Wenn Sie ein neues Symbol oder einen neuen Cursor erstellen, erstellt der **Bild-Editor** zunächst ein Bild eines Standard Typs. Das Bild ist anfänglich mit der Bildschirmfarbe (transparent) gefüllt. Wenn es sich bei dem Bild um einen Cursor handelt, befindet sich der Hotspot anfänglich in der oberen linken Ecke mit den Koordinaten `0,0`.

Standardmäßig unterstützt der **Bild-Editor** die Erstellung zusätzlicher Images für die Geräte, die in der folgenden Tabelle aufgeführt sind. Sie können Bilder für andere Geräte erstellen, indem Sie im Dialogfeld **benutzerdefiniertes Bild** die Parameter width, Height und Color-count eingeben.

|Color|Breite (in Pixel)|Höhe (in Pixel)|
|-----------|----------------------|-----------------------|
|Monochrom|16|16|
|Monochrom|32|32|
|Monochrom|48|48|
|Monochrom|64|64|
|Monochrom|96|96|
|16|16|16|
|16|32|32|
|16|64|64|
|16|48|48|
|16|96|96|
|256|16|16|
|256|32|32|
|256|48|48|
|256|64|64|
|256|96|96|

### <a name="create-a-device-image-icon-or-cursor"></a>Erstellen eines Geräte Bilds (Symbol oder Cursor)

Wenn Sie ein neues Symbol oder eine neue Cursor Ressource erstellen, erstellt der **Bild-Editor** zunächst ein Bild in einem bestimmten Format (32 × 32, 16 Farben für Symbole und 32 × 32, monochrome für Cursor). Anschließend können Sie dem ersten Symbol oder Cursor Bilder in verschiedenen Größen und Formaten hinzufügen und jedes weitere Bild nach Bedarf für die verschiedenen Anzeigegeräte bearbeiten. Sie können ein Bild auch bearbeiten, indem Sie einen Ausschneide-und Einfügevorgang aus einem vorhandenen Bildtyp oder einer Bitmap verwenden, die in einem Grafikprogramm erstellt wurde.

Wenn Sie das Symbol bzw. die Cursor Ressource im [Bild-Editor](../windows/image-editor-for-icons.md)öffnen, wird das Bild, das mit dem aktuellen Anzeigegerät am ehesten übereinstimmt, standardmäßig geöffnet.

> [!NOTE]
> Wenn das Projekt noch keine RC-Datei enthält, finden Sie weitere Informationen unter [Erstellen einer neuen Ressourcen Skriptdatei](../windows/how-to-create-a-resource-script-file.md).

Im Dialogfeld **neuer &lt;Gerät&gt; Bildtyp** können Sie ein neues Geräte Image eines bestimmten Typs erstellen. Um das Dialogfeld **Neues \<Gerät >** Abbild zu öffnen, navigieren Sie zu Menü **Bild** > **Neuer Bildtyp**. Die folgenden Eigenschaften sind **Ziel Bildtyp** und **Benutzer**definiert.

Die Eigenschaft **Ziel Bildtyp** listet die verfügbaren Bildtypen auf, in denen Sie den Bildtyp auswählen, den Sie öffnen möchten:

||||
|-|-|-|
|-16 x 16, 16 Farben|-48 x 48, 16 Farben|-96 x 96, 16 Farben|
|-16 x 16, 256 Farben|-48 x 48, 256 Farben|-96 x 96, 256 Farben|
|-16 x 16, monochrome|-48 x 48, monochrome|-96 x 96, monochrome|
|-32 x 32, 16 Farben|-64 x 64, 16 Farben||
|-32 x 32, 256 Farben|-64 x 64, 256 Farben||
|-32 x 32, monochrome|-64 x 64, monochrome||

> [!NOTE]
> Alle vorhandenen Images werden in dieser Liste nicht angezeigt.

Die **benutzerdefinierte** Eigenschaft öffnet das Dialogfeld **benutzerdefiniertes Bild** , in dem Sie ein neues Bild mit einer benutzerdefinierten Größe und einer benutzerdefinierten Anzahl von Farben erstellen können.

Das Dialogfeld **benutzerdefiniertes Bild** ermöglicht das Erstellen eines neuen Bilds mit benutzerdefinierter Größe und Anzahl von Farben. Die folgenden Eigenschaften sind enthalten:

|Eigenschaft|BESCHREIBUNG|
|---|---|
|**Width**|Ermöglicht das Eingeben der Breite des benutzerdefinierten Bilds in Pixel (1-512, Limit von 2048).|
|**Height**|Ermöglicht das Eingeben der Höhe des benutzerdefinierten Bilds in Pixel (1-512, Limit von 2048).|
|**Farben**|Bietet Ihnen die Möglichkeit, die Anzahl der Farben für das benutzerdefinierte Image auszuwählen: 2, 16 oder 256.|

Verwenden Sie das Dialogfeld **&lt;Gerät&gt; Abbild öffnen** , um Geräte C++ Images in-Projekten zu öffnen. Sie listet vorhandene Geräte Images in der aktuellen Ressource auf (Images, die Teil der aktuellen Ressource sind). Die folgende Eigenschaft ist enthalten:

|Eigenschaft|BESCHREIBUNG|
|---|---|
|**Aktuelle Bilder**|Listet die Bilder auf, die in der Ressource enthalten sind. Wählen Sie den Bildtyp aus, den Sie öffnen möchten.|

#### <a name="to-create-a-new-icon-or-cursor"></a>So erstellen Sie ein neues Symbol oder einen neuen Cursor

1. Klicken Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)mit der rechten Maustaste auf die *RC* -Datei, und wählen Sie dann **Ressource einfügen**aus. Wenn Sie bereits über eine vorhandene Image-Ressource in der RC-Datei verfügen (z *.* b. einen Cursor), können Sie mit der rechten Maustaste auf den **Cursor** Ordner klicken und **Cursor einfügen**auswählen.

1. Wählen Sie im [Dialogfeld Ressource einfügen](../windows/add-resource-dialog-box.md)das **Symbol** oder den **Cursor** aus, und wählen Sie **neu**aus. Bei Symbolen erstellt diese Aktion eine Symbol Ressource mit einem Symbol 32 × 32 und 16 Farben. Bei Cursorn wird ein 32 × 32, monochrome Bild (2 Farben) erstellt.

   Wenn im Dialogfeld **Ressource einfügen** neben dem Bild Ressourcentyp ein Pluszeichen ( **+** ) angezeigt wird, bedeutet dies, dass Toolbar-Vorlagen verfügbar sind. Wählen Sie das Pluszeichen aus, um die Liste der Vorlagen zu erweitern, wählen Sie eine Vorlage aus, und wählen Sie **neu**aus.

### <a name="to-add-an-image-for-a-different-display-device"></a>So fügen Sie ein Bild für ein anderes Anzeigegerät hinzu

1. Wechseln Sie zum Menü **Bild** > **Neues Geräte Image**, oder klicken Sie mit der rechten Maustaste in den Bereich **Bild** Bearbeitung, und wählen Sie **Neues Geräte Image**aus.

1. Wählen Sie den Typ des Bilds aus, das Sie hinzufügen möchten. Sie können auch **Benutzer** definiert auswählen, um ein Symbol zu erstellen, dessen Größe nicht in der Standardliste verfügbar ist.

### <a name="to-copy-a-device-image"></a>So kopieren Sie ein Geräte Image

1. Wechseln Sie zum Menü **Bild** , > **Geräte Abbild zu öffnen** , und wählen Sie ein Bild aus der Liste Aktuelle Bilder aus. Wählen Sie z. b. die Version 32 × 32, 16 Farben eines Symbols aus.

1. Kopiert das aktuell angezeigte Symbolbild (**STRG**+**C**).

1. Öffnen Sie ein anderes Bild des Symbols in einem anderen **Bild-Editor** -Fenster. Öffnen Sie z. b. die 16 × 16-farbige Version des Symbols.

1. Fügen Sie das Symbolbild (**STRG**+**V**) aus einem **Bild-Editor** -Fenster in das andere ein. Wenn Sie eine größere Größe in eine kleinere Größe einfügen, können Sie die Symbol Handles verwenden, um die Größe des Bilds zu ändern.

### <a name="to-delete-a-device-image"></a>So löschen Sie ein Geräte Abbild

Wenn das Symbolbild im **Bild-Editor**angezeigt wird, wechseln Sie zum Menü **Bild** , > **Geräte Abbild zu löschen**. Wenn Sie das letzte Symbolbild in der Ressource löschen, wird auch die Ressource gelöscht.

> [!NOTE]
> Wenn Sie die Taste ENTF drücken, **werden die Bilder** und Farben, die Sie auf einem Symbol gezeichnet haben, gelöscht, aber das Symbol bleibt erhalten, und Sie können es nun umgestalten. Wenn Sie " **del** " per Fehler drücken, drücken Sie **STRG**+**Z** , um die Aktion rückgängig zu machen.

### <a name="to-create-transparent-or-inverse-regions-in-device-images"></a>So erstellen Sie transparente oder umgekehrte Bereiche in Geräte Bildern

Im [Bild-Editor](../windows/image-editor-for-icons.md)weist das erste Symbol oder das Cursor Bild ein transparentes Attribut auf. Obwohl Symbol-und Cursor Bilder rechteckig sind, werden viele nicht angezeigt, da Teile des Bilds transparent sind und das zugrunde liegende Bild auf dem Bildschirm durch das Symbol oder den Cursor angezeigt wird. Wenn Sie ein Symbol ziehen, werden Teile des Bilds möglicherweise in einer umgekehrten Farbe angezeigt. Sie erstellen diesen Effekt, indem Sie die Bildschirm Farbe und die umgekehrte Farbe im [Fenster "Farben](../windows/colors-window-image-editor-for-icons.md)" festlegen.

Der Bildschirm und die umgekehrten Farben, die Sie auf Symbole und Cursor anwenden, werden entweder vom abgeleiteten Bild geformt und gefärbt, oder es werden umgekehrte Bereiche zugewiesen Die Farben geben Teile des Bilds an, die über diese Attribute verfügen. Sie können die Farben, die die Attribute für die Bildschirm Farbe und die Umkehrung der Farbe darstellen, bei der Bearbeitung ändern. Diese Änderungen wirken sich nicht auf die Darstellung des Symbols oder Cursors in der Anwendung aus.

> [!NOTE]
> Je nach den aktiven Einstellungen oder der Version unterscheiden sich die Dialogfelder und Menübefehle auf Ihrem Bildschirm möglicherweise von den in der **Hilfe** beschriebenen. Um die Einstellungen zu ändern, wechseln Sie zu Menü **Tools** > **Einstellungen importieren und exportieren**. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).

#### <a name="to-create-transparent-or-inverse-regions"></a>So erstellen Sie transparente oder umgekehrte Bereiche

1. Wählen Sie im Fenster **Farben** die Auswahl **Bildschirm Farbe** oder die **umgekehrte Farbe**aus.

1. Wenden Sie den Bildschirm oder die umgekehrte Farbe mithilfe eines Zeichnungs Tools auf das Bild an. Weitere Informationen zu Zeichnungs Tools finden Sie unter [Verwenden eines Zeichnungs](using-a-drawing-tool-image-editor-for-icons.md)Tools.

#### <a name="to-change-the-screen-or-inverse-color"></a>So ändern Sie den Bildschirm oder die umgekehrte Farbe

1. Wählen Sie entweder den **Bildschirm farbselektor** oder den **umgekehrten farbselektor** aus.

1. Wählen Sie im Fenster **Farben** aus der **Farbpalette eine** Farbe aus.

   Die ergänzende Farbe wird automatisch für den anderen Selektor zugewiesen.

   > [!TIP]
   > Wenn Sie auf die **Bildschirm Farbe** doppelklicken, wird **Inverse-Color** das [Dialogfeld Benutzerdefinierte Farbauswahl](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md) angezeigt.

### <a name="use-the-256-color-palette"></a>Verwenden der 256-Farbpalette

Mit dem **Bild-Editor**können Symbole und Cursor groß sein (64 × 64) mit einer zu wählenden Palette von 256 Farben. Nach dem Erstellen der Ressource wird ein Geräte Abbild Stil ausgewählt.

#### <a name="to-create-a-256-color-icon-or-cursor"></a>So erstellen Sie ein Symbol oder einen Cursor mit der 256-Farbe

1. Klicken Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)mit der rechten Maustaste auf die *RC* -Datei, und wählen Sie dann **Ressource einfügen**aus. Wenn Sie bereits über eine vorhandene Image-Ressource in der RC-Datei verfügen (z *.* b. einen Cursor), können Sie mit der rechten Maustaste auf den **Cursor** Ordner klicken und **Cursor einfügen**auswählen.

1. Wählen Sie im [Dialogfeld Ressource einfügen](../windows/add-resource-dialog-box.md)das **Symbol** oder den **Cursor** aus, und wählen Sie **neu**aus.

1. Wechseln Sie zum Menü **Bild** > **Neues Geräte Image** , und wählen Sie das gewünschte 256-farbige Bildformat aus.

#### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>So wählen Sie eine Farbe aus der 256-Farbpalette für große Symbole aus

Um mit einer Auswahl aus der 256-Farbpalette zu zeichnen, müssen Sie die Farben aus der Farb **Palette im** [Fenster Farben](../windows/colors-window-image-editor-for-icons.md)auswählen.

1. Wählen Sie das große Symbol oder den Cursor aus, oder erstellen Sie ein neues großes Symbol oder einen neuen Cursor.

1. Wählen Sie eine Farbe aus den 256 Farben aus, die im Fenster **Farben** in der Palette **Farben** angezeigt werden.

   Die ausgewählte Farbe wird zur aktuellen Farbe in der Farb **Palette im** Fenster " **Farben** ".

   > [!NOTE]
   > Die anfängliche Palette für 256-farbige Bilder stimmt mit der Palette überein, die von der `CreateHalftonePalette` Windows-API zurückgegeben wird. Bei allen für die Windows-Shell vorgesehenen Symbolen sollte diese Palette verwendet werden, um Flimmern während der palettenrealisierung zu verhindern.

### <a name="to-set-a-cursors-hot-spot"></a>So legen Sie den Hotspot eines Cursors fest

Der Hotspot eines Cursors ist der Punkt, auf den sich Windows bei der Nachverfolgung der Cursorposition bezieht. Standardmäßig wird der Hotspot auf die obere linke Ecke des Cursors mit Koordinaten `0,0`festgelegt. Die Eigenschaft "Hotspot" in der [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window) zeigt die **Hotspot** Koordinaten an.

1. Wählen Sie auf der [Symbolleiste Bild](../windows/toolbar-image-editor-for-icons.md)Bearbeitung das Tool **Hotspot festlegen** aus.

1. Wählen Sie das Pixel aus, das Sie als Hotspot des Cursors zuweisen möchten.

   Die Eigenschaft " **Hotspot** " im Fenster " **Eigenschaften** " zeigt die neuen Koordinaten an.

### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>So erstellen und speichern Sie eine Bitmap als GIF-oder JPEG-Datei

Wenn Sie eine Bitmap erstellen, wird das Bild im Bitmapformat (BMP) erstellt. Sie können das Bild jedoch als GIF oder JPEG oder in anderen Grafikformaten speichern.

> [!NOTE]
> Dieser Vorgang gilt nicht für Symbole und Cursor.

1. Wechseln Sie zu Menü **Datei** > **Öffnen**, und wählen Sie dann **Datei**aus.

1. Wählen Sie im **Dialogfeld neue Datei**den Ordner **Visual C++**  aus, und wählen Sie dann im Feld **Vorlagen** die Option **Bitmapdatei (. BMP)** aus, und wählen Sie **Öffnen**aus.

   Die Bitmap wird im **Bild-Editor**geöffnet.

1. Nehmen Sie bei Bedarf Änderungen an der neuen Bitmap vor.

1. Wenn die Bitmap weiterhin im Bild- **Editor**geöffnet ist, wechseln Sie zur Menü **Datei** > **Speichern Sie *Dateiname*. bmp als**.

1. Geben Sie im Dialogfeld **Datei speichern** unter im Feld **Dateiname** den gewünschten Namen für die Datei und die Erweiterung ein, die das gewünschte Dateiformat angibt. Beispiel: *MyFile. gif*.

   > [!NOTE]
   > Sie müssen die Bitmap außerhalb des Projekts erstellen oder öffnen, um Sie in einem anderen Dateiformat zu speichern. Wenn Sie die Datei in Ihrem Projekt erstellen oder öffnen, ist der Befehl " **Speichern** unter" nicht verfügbar. Weitere Informationen finden Sie unter [Anzeigen von Ressourcen in einer Ressourcen Skriptdatei außerhalb eines Projekts (eigenständig)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

1. Wählen Sie **Speichern** aus.

### <a name="to-convert-an-image-from-one-format-to-another"></a>So konvertieren Sie ein Bild von einem Format in ein anderes

Sie können GIF-oder JPEG-Bilder im **Bild-Editor** öffnen und als Bitmaps speichern. Außerdem können Sie eine Bitmapdatei öffnen und als GIF oder JPEG speichern. Images, mit denen Sie arbeiten, müssen nicht Teil eines Projekts zur Bearbeitung in der Entwicklungsumgebung sein (siehe [eigenständige Bildbearbeitung](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md)).

1. Öffnen Sie das Bild im **Bild-Editor**.

1. Wechseln Sie zur Menü **Datei** > speichern Sie den  ***Dateinamen* als**.

1. Geben Sie im Dialogfeld **Datei speichern** unter im Feld **Dateiname** den Dateinamen und die Erweiterung ein, die das gewünschte Format angibt.

1. Wählen Sie **Speichern** aus.

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>So fügen Sie einem nicht verwalteten C++ Projekt eine neue Bildressource hinzu

1. Klicken Sie in [Ressourcenansicht](how-to-create-a-resource-script-file.md#create-resources)mit der rechten Maustaste auf die *RC* -Datei, und wählen Sie dann **Ressource einfügen**aus. Wenn Sie bereits über eine vorhandene Image-Ressource in der RC-Datei verfügen (z *.* b. einen Cursor), können Sie einfach mit der rechten Maustaste auf den **Cursor** Ordner klicken und **Cursor einfügen**auswählen.

1. Wählen Sie im [Dialogfeld Ressource einfügen](../windows/add-resource-dialog-box.md)den Typ der Abbild Ressource aus, den Sie erstellen möchten (z. b.**Bitmap**), und wählen Sie dann **neu**aus.

   Wenn im Dialogfeld **Ressource einfügen** neben dem Bild Ressourcentyp ein Pluszeichen ( **+** ) angezeigt wird, bedeutet dies, dass Toolbar-Vorlagen verfügbar sind. Wählen Sie das Pluszeichen aus, um die Liste der Vorlagen zu erweitern, wählen Sie eine Vorlage aus, und wählen Sie **neu**aus.

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>So fügen Sie einem Projekt eine neue Bildressource in einer .NET-Programmiersprache hinzu

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektordner (z. b. *WindowsApplication1*).

1. Klicken Sie im Kontextmenü auf **Hinzufügen**, und wählen Sie dann **Neues Element hinzufügen**aus.

1. Erweitern Sie im Bereich **Kategorien** den Ordner **lokale Projekt Elemente** , und wählen Sie dann **Ressourcen**aus.

1. Wählen Sie im Bereich **Vorlagen** den Ressourcentyp aus, den Sie dem Projekt hinzufügen möchten.

   Die Ressource wird in **Projektmappen-Explorer** dem Projekt hinzugefügt, und die Ressource wird im [Bild-Editor](../windows/image-editor-for-icons.md)geöffnet. Sie können jetzt alle im **Bild-Editor** verfügbaren Tools verwenden, um das Bild zu ändern. Weitere Informationen zum Hinzufügen von Bildern zu einem verwalteten Projekt finden Sie [unter Laden eines Bilds zur Entwurfszeit](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms).

## <a name="requirements"></a>Requirements (Anforderungen)

Keine

## <a name="see-also"></a>Weitere Informationen

[Bildbearbeitung für Symbole](../windows/image-editor-for-icons.md)<br/>
[Gewusst wie: Bearbeiten eines Bilds](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Gewusst wie: Verwenden eines Zeichnungs Tools](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Gewusst wie: Arbeiten mit Farben](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Zugriffstasten](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
<!--
[Converting Bitmaps to Toolbars](../windows/converting-bitmaps-to-toolbars.md)<br/>
[Creating New Toolbars](../windows/creating-new-toolbars.md)<br/>
[Icons](/windows/win32/menurc/icons)<br/>
[Cursors](/windows/win32/menurc/cursors)<br/>-->

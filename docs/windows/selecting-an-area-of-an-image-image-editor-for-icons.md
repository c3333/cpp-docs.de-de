---
title: 'Gewusst wie: Bearbeiten eines Bilds'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.editing
helpviewer_keywords:
- Image editor [C++], image selection
- Image editor [C++], selecting images
- images [C++], selecting
- cursors [C++], selecting areas of
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
- Image editor [C++], flipping and rotating images
- images [C++], flipping
- images [C++], rotating
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
- size [C++], images
- images [C++], cropping
- images [C++], extending
- Image editor [C++], cropping or extending images
- Image editor [C++], shrinking and stretching images
- images [C++], stretching
- images [C++], shrinking
- bitmaps [C++], shrinking
- bitmaps [C++], stretching
- Image editor [C++], editing images
- images [C++], editing
- images [C++], properties
- Image editor [C++], Properties window
- Properties window, image editor
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
ms.openlocfilehash: 9324e3dc5c6691a7b50f137da1fad446b416e968
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167848"
---
# <a name="how-to-edit-an-image"></a>Gewusst wie: Bearbeiten eines Bilds

Mithilfe von Auswahl Tools können Sie einen Bereich eines Bilds definieren, das Sie Ausschneiden, kopieren, löschen, Größe ändern, umkehren oder verschieben möchten. Mit dem **Rechteck Auswahl** Tool können Sie einen rechteckigen Bereich des Bilds definieren und auswählen. Mit dem **unregelmäßigen Auswahl** Werkzeug können Sie einen frei Hand Umriss für den Bereich zeichnen, den Sie für den Ausschneide-, Kopier-oder anderen Vorgang auswählen möchten.

> [!NOTE]
> Weitere Informationen finden Sie in der [Symbolleiste](../windows/toolbar-image-editor-for-icons.md) **des Bild-** Editors in den Tools für **Rechteck Auswahl** und **irreguläre Auswahl** .

Sie können auch einen benutzerdefinierten Pinsel aus einer Auswahl erstellen. Weitere Informationen finden Sie unter [Erstellen eines benutzerdefinierten Pinsels](../windows/creating-a-custom-brush-image-editor-for-icons.md).

## <a name="how-to"></a>Vorgehensweise

Informationen zum Bearbeiten eines Bilds finden Sie unter Gewusst wie:

### <a name="to-select-an-image"></a>So wählen Sie ein Bild aus

1. Verwenden Sie die Symbolleiste des **Bild-Editors** , oder wechseln Sie zu Menü **Bild** > **Tools** , und wählen Sie das gewünschte Auswahl Tool aus.

1. Verschieben Sie die Einfügemarke in eine Ecke des Bildbereichs, den Sie auswählen möchten. Kreuzhaare werden angezeigt, wenn sich die Einfügemarke über dem Bild befindet.

1. Ziehen Sie die Einfügemarke in die umgekehrte Ecke des Bereichs, den Sie auswählen möchten. Ein Rechteck zeigt, welche Pixel ausgewählt werden. Alle Pixel innerhalb des Rechtecks, einschließlich der unter dem Rechteck, sind in der Auswahl enthalten.

1. Lassen Sie die Maustaste los. Der Auswahl Rahmen schließt den ausgewählten Bereich ein.

#### <a name="to-select-an-entire-image"></a>So wählen Sie ein gesamtes Bild aus

Wählen Sie das Bild außerhalb der aktuellen Auswahl aus. Der Auswahl Rahmen ändert den Fokus und umfasst das gesamte Bild erneut.

### <a name="to-edit-parts-of-an-image"></a>So bearbeiten Sie Teile eines Bilds

Sie können Standardbearbeitungsvorgänge ausführen – das Ausschneiden, kopieren, löschen und Verschieben von – bei einer [Auswahl](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), unabhängig davon, ob es sich bei der Auswahl um das gesamte Bild oder nur um einen Teil handelt. Da der **Bild-Editor** die **Windows-Zwischenablage**verwendet, können Sie Bilder zwischen der **Bild** Bearbeitung und anderen Anwendungen für Windows übertragen.

Außerdem können Sie die Größe der Auswahl ändern, unabhängig davon, ob Sie das gesamte Bild oder nur einen Teil enthält.

#### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>So schneiden Sie die aktuelle Auswahl aus und verschieben Sie in die Zwischenablage

Wechseln Sie zum Menü **Bearbeiten** > **Ausschneiden**.

#### <a name="to-copy-the-selection"></a>So kopieren Sie die Auswahl

1. Positionieren Sie den Zeiger innerhalb des Auswahl Rahmens oder an einer beliebigen Stelle, mit Ausnahme der Zieh Punkte.

1. Halten Sie die **STRG** -Taste gedrückt, während Sie die Auswahl an eine neue Position ziehen. Der Bereich der ursprünglichen Auswahl ist unverändert.

1. Um die Auswahl in das Bild an der aktuellen Position zu kopieren, wählen Sie außerhalb des Auswahl Cursors aus.

#### <a name="to-paste-the-clipboard-contents-into-an-image"></a>So fügen Sie den Inhalt der Zwischenablage in ein Bild ein

1. Wechseln Sie zum Menü **Bearbeiten** > **Einfügen**.

   Der Inhalt der Zwischenablage, der vom Auswahl Rahmen umgeben ist, wird in der oberen linken Ecke des Bereichs angezeigt.

1. Positionieren Sie den Zeiger innerhalb des Auswahl Rahmens, und ziehen Sie das Bild an die gewünschte Position auf dem Bild.

1. Um das Bild am neuen Speicherort zu verankern, wählen Sie außerhalb des Auswahl Rahmens aus.

#### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>So löschen Sie die aktuelle Auswahl, ohne Sie in die Zwischenablage zu verschieben

Wechseln Sie zum Menü **Bearbeiten** > **Löschen**.

   Der ursprüngliche Bereich der Auswahl wird mit der aktuellen Hintergrundfarbe ausgefüllt.

> [!NOTE]
> Sie können auf die Befehle zum **Ausschneiden**, **Kopieren**, **Einfügen**und **Löschen** zugreifen, indem Sie mit der rechten Maustaste auf das Fenster **Ressourcenansicht** klicken.

#### <a name="to-move-the-selection"></a>So verschieben Sie die Auswahl

1. Positionieren Sie den Zeiger innerhalb des Auswahl Rahmens oder an einer beliebigen Stelle, mit Ausnahme der Zieh Punkte.

1. Ziehen Sie die Auswahl an die neue Position.

1. Um die Auswahl im Bild an der neuen Position zu verankern, wählen Sie außerhalb des Auswahl Rahmens aus.

Weitere Informationen zum Zeichnen mit einer Auswahl finden Sie unter [Erstellen eines benutzerdefinierten Pinsels](../windows/creating-a-custom-brush-image-editor-for-icons.md).

### <a name="to-flip-an-image"></a>So kippen Sie ein Bild

Sie können ein Bild kippen oder drehen, um entweder ein Spiegelbild des Originals zu erstellen, das Bild nach oben zu drehen oder das Bild nach rechts um 90 Grad zu drehen.

- Um das Bild horizontal zu kippen (Spiegelbild), wechseln Sie zu Menü **Bild** > **Horizontal kippen**.

- Um das Bild vertikal zu kippen (nach oben), wechseln Sie zu Menü **Bild** > **Vertikal kippen**.

- Um das Bild um 90 Grad zu drehen, wechseln Sie zum Menü **Bild** > **drehen Sie 90 Grad**.

   > [!NOTE]
   > Sie können auch die [Tastenkombinationen (Tastenkombinationen)](../windows/accelerator-keys-image-editor-for-icons.md) für diese Befehle verwenden oder über das Kontextmenü auf die Befehle zugreifen (Wählen Sie im Bild- **Editor**außerhalb des Bilds aus).

### <a name="to-resize-an-image"></a>So ändern Sie die Größe eines Bilds

Das Verhalten des **Bild-Editors** beim Ändern der Größe eines Bilds hängt davon ab, ob Sie das gesamte Bild oder nur einen Teil davon [ausgewählt](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) haben.

Wenn die Auswahl nur einen Teil des Bilds enthält, verkleinert der **Bild-Editor** die Auswahl durch Löschen von Zeilen oder Spalten aus Pixel und Auffüllen der frei gewordenen Bereiche mit der aktuellen Hintergrundfarbe. Die Auswahl kann auch durch Duplizieren von Zeilen oder Spalten von Pixeln gestreckt werden.

Wenn die Auswahl das gesamte Bild enthält, verkleinert und erweitert der **Bild-Editor** das Bild, um es zu erweitern und zu erweitern.

Es gibt zwei Mechanismen zum Ändern der Größe eines Bilds: die Zieh Punkte und die [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window). Sie ziehen die Zieh Punkte, um die Größe eines vollständig oder eines Teils eines Bilds zu ändern. Zieh Punkte, die Sie ziehen können, sind solide. Sie können keine Zieh Punkte ziehen, die hohl sind. Verwenden Sie das **Eigenschaften** Fenster, um die Größe des gesamten Bilds nur zu ändern, nicht für ein ausgewähltes Element.

![Größen Zieh Punkte in einer Bitmap](../mfc/media/vcimageeditorsizinghandles.gif "vcimageeditor sizinghandles")<br/>
Größen Zieh Punkte

> [!NOTE]
> Wenn Sie die Option **Kachel Raster** im [Dialogfeld Raster Einstellungen](../windows/grid-settings-dialog-box-image-editor-for-icons.md)ausgewählt haben, ändern Sie die Größe von dockt zur nächsten Kachel Raster Linie. Wenn nur die **Pixel Raster** -Option ausgewählt ist (Standardeinstellung), wird die Größe von dockt zum nächsten verfügbaren Pixel angepasst.

#### <a name="to-resize-an-entire-image-using-the-properties-window"></a>So ändern Sie die Größe eines gesamten Bilds mithilfe des Fensters "Eigenschaften"

1. Öffnen Sie das Bild, dessen Eigenschaften Sie ändern möchten.

1. Geben Sie in den Feldern **Breite** und **Höhe** des [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window)die gewünschten Dimensionen ein.

   Wenn Sie die Größe des Bilds vergrößern, erweitert der **Bild-Editor** das Bild nach rechts, nach unten oder beides und füllt die neue Region mit der aktuellen Hintergrundfarbe aus. Das Bild wird nicht gestreckt.

   Wenn Sie die Größe des Bilds verkürzen, wird das Bild im **Bild-Editor** am rechten oder unteren Rand oder beides auf beide Knoten.

   > [!NOTE]
   > Sie können die Eigenschaften " **Width** " und " **height** " verwenden, um die Größe des gesamten Bilds zu ändern, nicht um die Größe einer Teilauswahl zu ändern.

#### <a name="to-crop-or-extend-an-entire-image"></a>So können Sie ein gesamtes Bild zuschneiden oder erweitern

1. Wählen Sie das gesamte Bild aus.

   Wenn ein Teil des Bilds aktuell ausgewählt ist und Sie das gesamte Bild auswählen möchten, wählen Sie eine beliebige Stelle des Bilds außerhalb des aktuellen Auswahl Rahmens aus.

1. Ziehen Sie einen Ziehpunkt, bis das Bild die richtige Größe ist.

Normalerweise wird ein Bild von der **Bild** Bearbeitung beim Ändern der Größe durch Verschieben eines Größen Zieh Punkts in ein Bild-oder vergrößert. Wenn Sie die **UMSCHALT** Taste gedrückt halten, während Sie ein Größen Anpassungs handle verschieben, verkleinert oder dehnt der **Bild-Editor** das Bild.

#### <a name="to-shrink-or-stretch-an-entire-image"></a>So verkleinern oder Strecken Sie ein gesamtes Bild

1. Wählen Sie das gesamte Bild aus.

   Wenn ein Teil des Bilds aktuell ausgewählt ist und Sie das gesamte Bild auswählen möchten, wählen Sie eine beliebige Stelle des Bilds außerhalb des aktuellen Auswahl Rahmens aus.

1. Halten Sie die **UMSCHALT** Taste gedrückt, und ziehen Sie einen Ziehpunkt, bis das Bild die richtige Größe ist.

#### <a name="to-shrink-or-stretch-part-of-an-image"></a>So verkleinern oder Strecken Sie einen Teil eines Bilds

1. Wählen Sie den Teil des Images aus, dessen Größe Sie ändern möchten. Weitere Informationen finden Sie unter [Auswählen eines Bildbereichs](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md).

1. Ziehen Sie eine der Größen Zieh Punkte, bis die richtige Größe ausgewählt ist.

### <a name="to-edit-an-image-outside-of-a-project"></a>So bearbeiten Sie ein Bild außerhalb eines Projekts

Sie können Bilder in der Entwicklungsumgebung genauso wie in jeder beliebigen Grafikanwendung öffnen und bearbeiten, z. b. das Öffnen einer Bitmap für die eigenständige Bearbeitung. Die Images, mit denen Sie arbeiten, müssen nicht Teil eines Visual Studio-Projekts sein.

1. Wechseln Sie zu Menü **Datei** > **Öffnen**.

1. Wählen Sie im Feld **Dateityp** die Option **alle Dateien**aus.

1. Suchen und öffnen Sie das Abbild, das Sie bearbeiten möchten.

### <a name="to-change-image-properties"></a>So ändern Sie die Bildeigenschaften

Sie können die Eigenschaften eines Bilds mithilfe des [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window)festlegen oder ändern.

1. Öffnen Sie das Bild im **Bild-Editor**.

1. Ändern Sie im **Eigenschaften** Fenster eine beliebige oder alle Eigenschaften für das Bild.

   |Eigenschaft|BESCHREIBUNG|
   |--------------|-----------------|
   |**Farben**|Gibt das Farbschema für das Bild an. Wählen Sie **Monochrom**, **16**oder **256**oder **wahr Farbe**aus.<br/><br/>Wenn Sie das Bild bereits mit einer 16-Farbpalette gezeichnet haben, bewirkt die Auswahl von **Chrome** , dass die Farben des Bilds in schwarz und weiß ersetzt werden. Der Kontrast wird nicht immer beibehalten: beispielsweise werden angrenzende Bereiche von rot und Grün in schwarz konvertiert.|
   |**Filename**|Gibt den Namen der Bilddatei an.<br/><br/>Standardmäßig weist Visual Studio einen Basis Dateinamen zu, der durch Entfernen der ersten vier Zeichen ("IDB_") aus dem Standard Ressourcen Bezeichner (IDB_BITMAP1) und durch Hinzufügen der entsprechenden Erweiterung erstellt wurde. Der Dateiname für das Bild in diesem Beispiel wäre *bitmap1. bmp*. Sie können Sie *MYBITMAP1. bmp*umbenennen.|
   |**Height**|Legt die Höhe des Bilds (in Pixel) fest. Der Standardwert ist 48.<br/><br/>Das Bild wird abgeschnitten, oder unterhalb des vorhandenen Bilds wird Leerraum hinzugefügt.|
   |**ID**|Legt den Bezeichner der Ressource fest.<br/><br/>Bei einem Bild weist Microsoft Visual Studio standardmäßig den nächsten verfügbaren Bezeichner in einer Reihe zu: IDB_BITMAP1, IDB_BITMAP2 usw. Ähnliche Namen werden für Symbole und Cursor verwendet.|
   |**Messer**|Ändert Farbeigenschaften.<br/><br/>Doppelklicken Sie, um eine Farbe auszuwählen, und zeigen Sie das [Dialogfeld Benutzerdefinierte Farbauswahl](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md)an. Definieren Sie die Farbe, indem Sie RGB-oder HSL-Werte in die entsprechenden Textfelder eingeben.|
   |**Savekomprimiert**|Gibt an, ob das Bild in einem komprimierten Format vorliegt. Diese Eigenschaft ist schreibgeschützt.<br/><br/>Visual Studio ermöglicht nicht das Speichern von Bildern in komprimiertem Format. für alle Bilder, die in Visual Studio erstellt werden, lautet diese Eigenschaft also **false**. Wenn Sie ein komprimiertes Bild (das in einem anderen Programm erstellt wurde) in Visual Studio öffnen, ist diese Eigenschaft " **true**". Wenn Sie ein komprimiertes Bild mithilfe von Visual Studio speichern, wird es nicht komprimiert, und diese Eigenschaft wird auf **false**zurückgesetzt.|
   |**Width**|Legt die Breite des Bilds (in Pixel) fest. Der Standardwert für Bitmaps ist 48.<br/><br/>Das Bild wird abgeschnitten, oder es wird ein Leerzeichen auf der rechten Seite des vorhandenen Bilds hinzugefügt.|

## <a name="requirements"></a>Requirements (Anforderungen)

Keine

## <a name="see-also"></a>Weitere Informationen

[Bildbearbeitung für Symbole](../windows/image-editor-for-icons.md)<br/>
[Gewusst wie: Erstellen eines Symbols oder eines anderen Bilds](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Gewusst wie: Verwenden eines Zeichnungs Tools](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Gewusst wie: Arbeiten mit Farben](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Zugriffstasten](../windows/accelerator-keys-image-editor-for-icons.md)<br/>

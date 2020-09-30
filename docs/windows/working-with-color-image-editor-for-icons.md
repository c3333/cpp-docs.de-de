---
title: 'Gewusst wie: Arbeiten mit Farben'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.color
- vc.editors.customcolorselector
- vc.editors.loadcolorpalette
- vc.editors.colorswindow
helpviewer_keywords:
- images [C++], background colors
- Image editor [C++], Colors Palette
- colors [C++], image
- Colors Palette, Image editor
- palettes, Image editor colors
- foreground colors [C++], Image editor
- colors [C++]
- Image editor [C++], colors
- colors [C++], Image editor
- colors [C++], image
- images [C++], colors
- Image editor [C++], colors
- Fill tool
- colors [C++], image
- images [C++], colors
- colors [C++], selection tools
- Image editor [C++], colors
- Select Color tool
- dithered color, Image editor
- Custom Color Selector dialog box [C++]
- Image editor [C++], Colors Palette
- colors [C++], image
- bitmaps [C++], colors
- images [C++], colors
- HSL values
- Colors Palette, Image editor
- RGB color values
- Adjust Colors command [C++]
- Image editor [C++], dithered color
- Image editor [C++], Colors Palette
- Colors Palette, Image editor
- colors [C++], inverting
- colors [C++]
- Color Indicator
- colors [C++], Colors window
- Colors window, hiding colors
- Show Colors Window command
- Colors window, displaying colors
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
- color palettes
- Load Palette Colors dialog box [C++]
- opaque backgrounds [C++]
- colors [C++], image
- Image editor [C++], transparent or opague backgrounds
- images [C++], transparency
- images [C++], opaque background
- colors [C++], image
- Image editor [C++], color inversion
- images [C++], colors
- colors [C++], inverting
ms.assetid: d34ff96f-241d-494f-abdd-13811ada8cd3
ms.openlocfilehash: 3c9134fde9053f57f8848a37b1442728f6111c98
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502949"
---
# <a name="how-to-work-with-color"></a>Gewusst wie: Arbeiten mit Farben

Der **Bild-Editor** enthält viele Funktionen, mit denen Farben speziell behandelt und angepasst werden. Sie können eine Vordergrund-oder Hintergrundfarbe festlegen, gebundene Bereiche mit Farben Auffüllen oder eine Farbe auf einem Bild auswählen, die als aktuelle Vordergrund-oder Hintergrundfarbe verwendet werden soll. Sie können die Tools auf der [Bild-Editor-Symbolleiste](./image-editor-for-icons.md) zusammen mit der Farbpalette im Fenster **Farben** zum Erstellen von Bildern verwenden.

Alle Farben für monochrome und 16-farbige Bilder werden in der **Farbpalette im** Fenster **Farben** angezeigt. Zusammen mit den 16 Standardfarben können Sie eigene benutzerdefinierte Farben erstellen. Wenn Sie die Farben in der Palette ändern, wird die entsprechende Farbe im Bild sofort geändert.

Beim Arbeiten mit 256-Farben-Symbol-und Cursor Bildern wird die **Colors** -Eigenschaft in der [Eigenschaftenfenster](/visualstudio/ide/reference/properties-window) verwendet. Weitere Informationen finden Sie unter [Erstellen eines 256-Farben-Symbols oder-Cursors](./creating-an-icon-or-other-image-image-editor-for-icons.md).

Es können auch True-Color-Bilder erstellt werden. Echte farbbeispiele werden jedoch nicht in der vollständigen Palette im Fenster **Farben** angezeigt. Sie werden nur im Vordergrund-oder Hintergrund Farbindikator Bereich angezeigt. Echte Farben werden mithilfe des Dialog Felds **Benutzerdefinierte Farbauswahl** erstellt.

Sie können angepasste Farbpaletten auf der Festplatte speichern und nach Bedarf erneut laden. Die verwendete Farbpalette wird in der Registrierung gespeichert und beim nächsten Start von Visual Studio automatisch geladen.

Das Fenster " **Farben** " besteht aus zwei Teilen:

- Die Farb **Palette**, bei der es sich um ein Array von Farb Beispielen handelt, die Farben darstellen, die Sie verwenden können. Wenn Sie die Grafiktools verwenden, können Sie die Beispiele auswählen, um Vordergrund-und Hintergrundfarben auszuwählen.

- Der **Farbindikator**, der die Vordergrund-und Hintergrundfarben und Selektoren für Bildschirm-und umgekehrter Farbe anzeigt.

   ![Colors window](../windows/media/vccolorswindow.gif "vccolorswindow")<br/>
   Fenster " **Farben** "

> [!NOTE]
> Die Tools für die **Bildschirm Farbe** und die **Umkehrung der Farbe** sind nur für Symbole und Cursor verfügbar.

Sie können das Fenster " **Farben** " mit der [Bild-Editor-Symbolleiste](./image-editor-for-icons.md)verwenden.

- Um das Fenster **Farben** anzuzeigen, klicken Sie mit der rechten Maustaste in einen **Bild Bearbeitungs** Bereich, und wählen Sie **Fenster Farben anzeigen**aus, oder wechseln Sie zum Menü [Bild](./image-editor-for-icons.md)  >  **Fenster Farben anzeigen**.

- Um das Fenster " **Farben** " auszublenden, lösen Sie das Fenster aus (durch diese Aktion kann das Fenster automatisch ausgeblendet werden, wenn es nicht verwendet wird), oder klicken Sie auf die Schaltfläche " **Schließen** ".

In der **Farb** Palette werden anfänglich 16 Standardfarben angezeigt. Mit den angezeigten Farben können Sie auch eigene benutzerdefinierte Farben erstellen. Sie können dann eine benutzerdefinierte Farbpalette speichern und laden.

Mit dem Dialogfeld **Benutzerdefinierte Farbauswahl** können Sie die Farben, die Sie für Ihr Bild verwenden, mit den folgenden Eigenschaften anpassen:

|Eigenschaft|Beschreibung|
|--------------------------|--------------------------|
|**Farbverlaufs Farbe anzeigen**|Ändert die Werte einer ausgewählten Farbe.<br/><br/>Positionieren Sie das Fadenkreuz auf der Farbe, die Sie ändern möchten, und verschieben Sie den Schieberegler nach oben oder unten, um die Werte für die Helligkeit oder RGB der Farbe zu ändern.|
|**Leuchtkraft Leiste**|Legt die Helligkeit für die Farbe fest, die Sie im Anzeige Feld für Farb **Verlaufs Farben** auswählen.<br/><br/>Wählen Sie den weißen Pfeil nach oben aus, um die Helligkeit zu erhöhen oder um weniger Helligkeit zu drücken. Das Feld **Farbe** zeigt die Farbe an, die Sie ausgewählt haben, und die Auswirkung der von Ihnen festgelegten Helligkeit.|
|**Farbe**|Listet den Farbton (Farbrad Wert) der Farbe auf, die Sie definieren. Die Werte liegen im Bereich von 0 bis 240, wobei 0 für Rot, 60 für Gelb, 120 für Grün, 180 den Wert Cyan, 200 den Wert Magenta und 240 den Wert Blue hat.|
|**Farbton**|Listet den Farbton (Farbrad Wert) der Farbe auf, die Sie definieren. Die Werte liegen im Bereich von 0 bis 240, wobei 0 für Rot, 60 für Gelb, 120 für Grün, 180 den Wert Cyan, 200 den Wert Magenta und 240 den Wert Blue hat.|
|**Sat**|Gibt den Sättigungswert der Farbe an, die Sie definieren. Sättigung ist die Menge der Farbe in einem angegebenen Farbton. Die Werte reichen von 0 bis 240.|
|**Hell.:**|Listet die Helligkeit (Helligkeit) der Farbe auf, die Sie definieren. Die Werte reichen von 0 bis 240.|
|**Rot**|Gibt den roten Wert der Farbe an, die Sie definieren. Die Werte reichen von 0 bis 255.|
|**Grün**|Gibt den grünen Wert der Farbe an, die Sie definieren. Die Werte reichen von 0 bis 255.|
|**Blau**|Gibt den blauen Wert der Farbe an, die Sie definieren. Die Werte reichen von 0 bis 255.|

Sie können eine **Farb** Palette, die angepasste Farben enthält, speichern und laden. Standardmäßig wird die zuletzt verwendete **Farb** Palette automatisch geladen, wenn Sie Visual Studio starten.

> [!TIP]
> Da der **Bild-Editor** keine Möglichkeit zum Wiederherstellen der **Standard Farb** Palette hat, sollten Sie die **Standard** Farbpalette unter einem Namen wie " *Standard. PAL* " oder " *default. PAL* " speichern, damit Sie die Standardeinstellungen problemlos wiederherstellen können.

Verwenden Sie das Dialogfeld **Palettenfarben laden** , um besondere Farbpaletten für die Verwendung in Ihrem C++-Projekt mit folgenden Eigenschaften zu laden:

|Eigenschaft|Beschreibung|
|-----------------|-----------------|
|**Look in**|Gibt den Speicherort an, an dem Sie eine Datei oder einen Ordner suchen möchten.<br/><br/>Wählen Sie den Pfeil aus, um einen anderen Speicherort auszuwählen, oder wählen Sie auf der Symbolleiste das Ordnersymbol, um die Ebenen zu verschieben|
|**Dateiname**|Hier können Sie den Namen der Datei eingeben, die Sie öffnen möchten.<br/><br/>Um schnell eine Datei zu finden, die Sie zuvor geöffnet haben, wählen Sie den Dateinamen in der Dropdown Liste aus, falls verfügbar.<br/><br/>Wenn Sie nach einer Datei suchen, können Sie Sternchen (*) als Platzhalter verwenden. Beispielsweise können Sie eingeben, \* \* um eine Liste aller Dateien anzuzeigen. Sie können auch den vollständigen Pfad einer Datei eingeben, z. b. *c:\My documents\mycolorpalette.PAL* oder * \\ \networkserver\myfolder\mycolorpalette.PAL*.|
|**Dateityp**|Listet die anzuzeigenden Dateitypen auf.<br/><br/>Die Palette (*. PAL) ist der Standard Dateityp für Farbpaletten.|

## <a name="how-to"></a>Vorgehensweise

### <a name="to-select-foreground-or-background-colors"></a>So wählen Sie Vordergrund-oder Hintergrundfarben aus

Mit Ausnahme des **radiers**zeichnen Tools auf der **Bild-Editor** -Symbolleiste mit der aktuellen Vordergrund-oder Hintergrundfarbe, wenn Sie die linke oder Rechte Maustaste drücken.

- Um eine Vordergrundfarbe auszuwählen, wählen Sie mit der linken Maustaste die gewünschte Farbe auf der Farb **Palette aus** .

- Um eine Hintergrundfarbe auszuwählen, wählen Sie mit der rechten Maustaste die gewünschte Farbe auf der **Farbpalette aus** .

### <a name="to-fill-a-bounded-area-of-an-image-with-a-color"></a>So füllen Sie einen begrenzten Bereich eines Bilds mit einer Farbe aus

Der **Bild-Editor** bietet das **Füll** Tool zum Auffüllen eines beliebigen eingeschlossenen Bildbereichs mit der aktuellen Zeichenfarbe oder der aktuellen Hintergrundfarbe.

### <a name="to-use-the-fill-tool"></a>So verwenden Sie das Füll Tool

1. Verwenden Sie die Symbolleiste **Bild** Bearbeitung, oder wechseln Sie zu Menü **Bild**  >  **Tools** , und wählen Sie das **Füll** Tool aus.

1. Wählen Sie bei Bedarf Zeichnungs Farben aus. Wählen Sie in der [Palette Farben](./image-editor-for-icons.md)die linke Maustaste aus, um eine Vordergrundfarbe oder die Rechte Maustaste auszuwählen, um eine Hintergrundfarbe auszuwählen.

1. Verschieben Sie das **Füll** Werkzeug in den Bereich, den Sie ausfüllen möchten.

1. Klicken Sie mit der linken oder rechten Maustaste auf die Vordergrundfarbe bzw. die Hintergrundfarbe.

### <a name="to-pick-up-a-color-from-an-image-to-use-elsewhere"></a>So wählen Sie eine Farbe von einem Bild für eine andere Verwendung aus

Die **Auswahl Farbe**oder das Farb Pickup-Tool bewirkt, dass jede Farbe im Bild die aktuelle Vordergrundfarbe oder Hintergrundfarbe hat, je nachdem, ob Sie die linke oder die Rechte Maustaste drücken. Um das **Select Color** -Tool abzubrechen, wählen Sie ein anderes Tool aus.

1. Verwenden Sie die Symbolleiste des **Bild-Editors** oder wechseln Sie zu Menü **Bild**  >  **Tools** , und wählen Sie das **Farb** Tool aus.

1. Wählen Sie die Farbe aus, die Sie aus dem Bild aufnehmen möchten.

   > [!NOTE]
   > Nachdem Sie eine Farbe ausgewählt haben, aktiviert der **Bild-Editor** das zuletzt verwendete Tool erneut.

1. Zeichnen Sie mit der linken Maustaste der Vordergrundfarbe oder mit der rechten Maustaste auf die Hintergrundfarbe.

### <a name="to-choose-the-background"></a>So wählen Sie den Hintergrund aus

Wenn Sie eine Auswahl aus einem Bild verschieben oder kopieren, sind alle Pixel in der Auswahl, die mit der aktuellen Hintergrundfarbe identisch sind, standardmäßig transparent, und Sie verbergen keine Pixel am Ziel Speicherort.

Sie können von einem transparenten Hintergrund (Standard) zu einem nicht transparenten Hintergrund und wieder zurück wechseln. Wenn Sie ein Auswahlwerkzeug verwenden, werden die Optionen **transparenter Hintergrund** und **undurchsichtiger Hintergrund** im **options** -Editor auf der Symbolleiste der **Bild** Bearbeitung angezeigt.

![Hintergrund Optionen &#45; nicht transparent oder transparent](../windows/media/vcimageeditoropaqtranspback.gif "Hintergrund Optionen &#45; nicht transparent oder transparent")<br/>
**Transparente und nicht transparente Optionen** auf der **Symbolleiste des Bild-Editors**

#### <a name="to-switch-between-a-transparent-and-opaque-background"></a>So wechseln Sie zwischen transparentem und undurchsichtigem Hintergrund

Wählen Sie in der **Bild-Editor** -Symbolleiste die **Option** Auswahl aus, und wählen Sie dann den entsprechenden Hintergrund aus:

- **Undurchsichtiger Hintergrund (O)**: das vorhandene Bild wird von allen Teilen der Auswahl verdeckt.

- **Transparenter Hintergrund (T)**: ein vorhandenes Bild wird durch Teile der Auswahl angezeigt, die der aktuellen Hintergrundfarbe entsprechen.

> [!TIP]
> Wählen Sie für eine Verknüpfung im Menü **Bild** die Option nicht transparent **Zeichnen**aus, oder löschen Sie Sie.

Sie können die Hintergrundfarbe ändern, während eine Auswahl bereits wirksam ist, um zu ändern, welche Teile des Bilds transparent sind.

### <a name="to-invert-the-colors-in-a-selection"></a>So kehren Sie die Farben in einer Auswahl um

Der **Bild-Editor** bietet eine bequeme Möglichkeit, Farben im ausgewählten Teil des Bilds umzukehren, damit Sie feststellen können, wie ein Bild mit umgekehrten Farben angezeigt wird.

Zum Umkehren der Farben in der aktuellen Auswahl wechseln Sie zu Menü **Bild**  >  **Farben umkehren**.

### <a name="to-customize-or-change-colors-on-the-colors-palette"></a>So passen Sie Farben in der Farbpalette an oder ändern Sie

1. Wechseln Sie zu Menü **Bild**  >  **Farben anpassen**.

1. Definieren Sie im Dialogfeld **Benutzerdefinierte Farbauswahl** die Farbe, indem Sie RGB-oder HSL-Werte in die entsprechenden Textfelder eingeben, oder wählen Sie eine Farbe im Anzeige Feld Farb **Verlaufs Farbe** aus.

1. Legen Sie die Helligkeit fest, indem Sie den Schieberegler auf der Leiste für die **Leucht** Kraft bewegen.

1. Viele benutzerdefinierte Farben werden gedithert. Wenn Sie möchten, dass die voll Tonfarbe der Dithering-Farbe am nächsten ist, doppelklicken Sie auf das **Textfeld.**

   Wenn Sie später entscheiden, dass Sie die Dithering-Farbe wünschen, verschieben Sie den Schieberegler auf der Leiste **Helligkeit** , oder verschieben Sie die kreuzhaare im Anzeige Feld Farb **Verlaufs Farbe** erneut, um das Dithering wiederherzustellen.

1. Wählen Sie **OK** aus, um die neue Farbe hinzuzufügen.

### <a name="to-save-a-custom-colors-palette"></a>So speichern Sie eine benutzerdefinierte Farbpalette

1. Wechseln Sie zu Menü **Bild**  >  **Palette speichern**.

1. Navigieren Sie zu dem Verzeichnis, in dem Sie die Farbpalette speichern möchten, und geben Sie einen Namen für die Palette ein.

1. Wählen Sie **Speichern** aus.

### <a name="to-load-a-custom-colors-palette"></a>So laden Sie eine benutzerdefinierte Farbpalette

1. Wechseln Sie zum Menü **Bild**  >  **Laden Palette**.

1. Navigieren Sie im Dialogfeld **Farb Palette laden** zum richtigen Verzeichnis, und wählen Sie die Palette aus, die Sie laden möchten. **Farb** Paletten werden mit der Dateierweiterung ". PAL" gespeichert.

## <a name="requirements"></a>Requirements (Anforderungen)

Keine

## <a name="see-also"></a>Weitere Informationen

[Bildbearbeitung für Symbole](../windows/image-editor-for-icons.md)<br/>
[Gewusst wie: Erstellen eines Symbols oder eines anderen Bilds](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Gewusst wie: Bearbeiten eines Bilds](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Gewusst wie: Verwenden eines Zeichnungs Tools](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Zugriffstasten](../windows/accelerator-keys-image-editor-for-icons.md)<br/>

---
title: Zugriffstasten (C++ Bildbearbeitung für Symbole)
ms.date: 02/15/2019
helpviewer_keywords:
- accelerator keys
- Image editor [C++], accelerator keys
ms.assetid: add37861-3e17-4a6f-89e8-46df12e74a90
ms.openlocfilehash: 35aeeb7e644849d215cd4782a1d06576449746ef
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447203"
---
# <a name="accelerator-keys-c-image-editor-for-icons"></a>Zugriffstasten (C++ Bildbearbeitung für Symbole)

Im folgenden finden Sie die Tastenkombinationen für die Bild-Editor-Befehle, die standardmäßig an Schlüssel gebunden sind. Um Zugriffstasten zu ändern, wechseln Sie zu Menü **Tools** > Optionen, und wählen Sie im Ordner **Umgebung** die **Option** **Tastatur** aus. Weitere Informationen finden Sie unter [Identifizieren und Anpassen von Tastenkombinationen](/visualstudio/ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio).

> [!NOTE]
> Die in einem Dialogfeld verfügbaren Optionen sowie die Namen und Positionen der angezeigten Menübefehle können sich je nach den persönlichen aktiven Einstellungen oder der verwendeten Version von den in der Hilfe beschriebenen Optionen unterscheiden. Um die Einstellungen zu ändern, wechseln Sie zu Menü **Tools** > **Einstellungen importieren und exportieren**. Weitere Informationen finden Sie unter [Personalisieren von Visual Studio-IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).

|Get-Help|Schlüssel|BESCHREIBUNG|
|-------------|----------|-----------------|
|Image. Airbrushtool|**STRG** + **A**|Zeichnet mithilfe einer Airbrush mit ausgewählter Größe und Farbe.|
|Image.BrushTool|**STRG** + **B**|Zeichnet mithilfe eines Pinsels mit der ausgewählten Form, Größe und Farbe.|
|Image.CopyAndOutlineSelection|**STRG** + **UMSCHALT** + **U**|Erstellt eine Kopie der aktuellen Auswahl und versieht sie mit einer Umrisslinie. Wenn die Hintergrundfarbe in der aktuellen Auswahl enthalten ist, wird Sie ausgeschlossen, wenn Sie die Option [transparent](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md) ausgewählt haben.|
|Image.DrawOpaque|**STRG** + **J**|Macht die aktuelle Auswahl entweder [undurchsichtig oder transparent](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).|
|Image.EllipseTool|**STRG** + **P**|Zeichnet eine Ellipse mit der ausgewählten Linienstärke und-Farbe.|
|Image.EraserTool|**STRG** + **UMSCHALT** + **I**|Löscht einen Teil des Bilds (mit der aktuellen Hintergrundfarbe).|
|Image.FilledEllipseTool|**STRG** + **UMSCHALT** + **alt** + **P**|Zeichnet eine ausgefüllte Ellipse.|
|Image.FilledRectangleTool|**STRG** + **UMSCHALT** + **alt** + **R**|Zeichnet ein ausgefülltes Rechteck.|
|Image.FilledRoundRectangleTool|**STRG** + **UMSCHALT** + **alt** + **W**|Zeichnet ein ausgefülltes, abgerundetes Rechteck.|
|Image.FillTool|**STRG** + **F**|Füllt einen Bereich.|
|Image.FlipHorizontal|**STRG** + **H**|Kippt das Bild oder die Markierung horizontal.|
|Image.FlipVertical|**UMSCHALT**+ **alt** + **H**|Kippt das Bild oder die Auswahl vertikal.|
|Image.LargerBrush|**STRG** +  **=**|Erhöht die Pinselgröße in jede Richtung um ein Pixel. Um die Pinselgröße zu verringern, siehe "Image.SmallerBrush" in dieser Tabelle.|
|Image.LineTool|**STRG** + **L**|Zeichnet eine gerade Linie von der ausgewählten Form, Größe und Farbe.|
|Image.MagnificationTool|**STRG** + **M**|Aktiviert das Tool " **vergrößern** ", mit dem Sie bestimmte Abschnitte des Bilds vergrößern können.|
|Image.Magnify|**STRG** + **UMSCHALT** + **M**|Schaltet zwischen der aktuellen Vergrößerung und dem Vergrößerungsfaktor 1:1 um.|
|Image.NewImageType|**Einfügen**|Öffnet das [Dialogfeld Neuer \<Geräte > Bildtyp](../windows/new-device-image-type-dialog-box-image-editor-for-icons.md) , in dem Sie ein Bild für einen anderen Bildtyp erstellen können.|
|Image.NextColor|**STRG** +  **]**<br /><br /> - oder -<br /><br /> **STRG** + **Pfeil nach rechts**|Wechselt von der zum Zeichnen verwendeten Vordergrundfarbe zur nächsten Palettenfarbe.|
|Image.NextRightColor|**STRG** + **UMSCHALTTASTE** +  **]**<br /><br /> - oder -<br /><br /> **UMSCHALT** + **STRG** + **Pfeil nach rechts**|Wechselt von der zum Zeichnen verwendeten Hintergrundfarbe zur nächsten Palettenfarbe.|
|Image.OutlinedEllipseTool|**UMSCHALT** + **alt** + **P**|Zeichnet eine ausgefüllte Ellipse mit einem Rand.|
|Image.OutlinedRectangleTool|**UMSCHALT** + **alt** + **R**|Zeichnet ein ausgefülltes Rechteck mit einem Rand.|
|Image.OutlinedRoundRectangleTool|**UMSCHALT** + **alt** + **W**|Zeichnet ein ausgefülltes, abgerundetes Rechteck mit einem Rand.|
|Image.PencilTool|**STRG** + **I**|Zeichnet mit einem Stift von einem Pixel Breite.|
|Image.PreviousColor|**STRG** +  **[**<br /><br /> - oder -<br /><br /> **STRG** + nach- **Links-Taste**|Wechselt von der zum Zeichnen verwendeten Vordergrundfarbe zur vorherigen Palettenfarbe.|
|Image.PreviousRightColor|**STRG** + **UMSCHALTTASTE** +  **[**<br /><br /> - oder -<br /><br /> **UMSCHALT** + **STRG** + nach- **Links-Taste**|Wechselt von der zum Zeichnen verwendeten Hintergrundfarbe zur vorherigen Palettenfarbe.|
|Image.RectangleSelectionTool|**UMSCHALT** + **alt** + **S**|Wählt einen rechteckigen Teil des Bilds zum Verschieben, kopieren oder bearbeiten aus.|
|Image.RectangleTool|ATL + R|Zeichnet ein Rechteck mit der ausgewählten Linienstärke und-Farbe.|
|Image.Rotate90Degrees|**STRG** + **UMSCHALT** + **H**|Dreht das Bild oder die Auswahl um 90 Grad.|
|Image.RoundedRectangleTool|**Alt** + **W**|Zeichnet ein Runden Rechteck mit der ausgewählten Linienstärke und-Farbe.|
|Image.ShowGrid|**STRG** + **alt** + **S**|Schaltet das Pixelraster um (aktiviert oder deaktiviert die Option **Pixelraster** im [Dialogfeld Raster Einstellungen](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|
|Image.ShowTileGrid|**STRG** + **UMSCHALT** + **alt** + **S**|Schaltet das Kachel Raster um (aktiviert oder deaktiviert die Option **Kachel Raster** im [Dialogfeld Raster Einstellungen](../windows/grid-settings-dialog-box-image-editor-for-icons.md)).|
|Image.SmallBrush|**STRG** +  **.** (Punkt).|Reduziert die **Pinsel** Größe auf ein Pixel. (Siehe auch "Image.LargerBrush" und "Image.SmallerBrush" in dieser Tabelle.)|
|Image.SmallerBrush|**STRG** +  **-** (minus)|Verringert die Pinselgröße in jede Richtung um ein Pixel. Um die Pinselgröße wieder zu erhöhen, siehe "Image.LargerBrush" in dieser Tabelle.|
|Image.TextTool|**STRG** + **T**|Öffnet das [Dialogfeld Text Tool](../windows/text-tool-dialog-box-image-editor-for-icons.md).|
|Image.UseSelectionAsBrush|**STRG** + **U**|Zeichnet unter Verwendung der aktuellen Markierung als Pinsel.|
|Image.ZoomIn|**STRG** + **UMSCHALT** +  **.** (Punkt).<br /><br /> - oder -<br /><br /> **STRG** + **Pfeil nach oben**|Erhöht den Vergrößerungsfaktor für die aktuelle Ansicht.|
|Image.ZoomOut|**STRG** +  **,** (Komma)<br /><br /> - oder -<br /><br /> **STRG** + **Pfeil nach unten**|Verringert den Vergrößerungsfaktor für die aktuelle Ansicht.|

## <a name="requirements"></a>Requirements (Anforderungen)

Keine

## <a name="see-also"></a>Weitere Informationen

[Bildbearbeitung für Symbole](../windows/image-editor-for-icons.md)<br/>
[Gewusst wie: Erstellen eines Symbols oder eines anderen Bilds](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Gewusst wie: Bearbeiten eines Bilds](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Gewusst wie: Verwenden eines Zeichnungs Tools](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Gewusst wie: Arbeiten mit Farben](../windows/working-with-color-image-editor-for-icons.md)<br/>
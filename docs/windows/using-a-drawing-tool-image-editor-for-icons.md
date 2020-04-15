---
title: 'Gewusst wie: Verwenden eines Zeichenwerkzeugs'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.drawing
helpviewer_keywords:
- Image editor [C++], selecting drawing tools
- Image editor [C++], toolbar
- drawing tools
- Image editor [C++], drawing lines
- shapes, drawing
- colors [C++], brush
- brushes, colors
- brushes, creating custom
- images [C++], creating custom brushes
- graphics [C++], custom brushes
- custom brushes
ms.assetid: 1f8c6eef-7760-45a9-a5cb-9e15c6f91245
ms.openlocfilehash: b0041124c35414a0c1c998642b5321319602c872
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359852"
---
# <a name="how-to-use-a-drawing-tool"></a>Gewusst wie: Verwenden eines Zeichenwerkzeugs

Der **Bild-Editor** verfügt über Freihand-Zeichnungs- und Löschwerkzeuge, die alle auf die gleiche Weise funktionieren. Sie wählen das Werkzeug und bei Bedarf [Vordergrund- und Hintergrundfarben](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) sowie Größen- und Formoptionen aus. Anschließend bewegen Sie den Mauszeiger auf das Bild und klicken oder ziehen, um zu zeichnen und zu löschen.

## <a name="drawing-tools"></a>Zeichnungswerkzeuge

Sie können Zeichenwerkzeuge entweder in der **Symbolleiste des Bild-Editors** oder im Menü **Bild** auswählen. Wenn Sie das **Werkzeug Löschen,** **Pinsel** oder **Airbrush** auswählen, zeigt die Optionsauswahl die Optionen dieses Werkzeugs an.

> [!TIP]
> Werkzeugtipps werden angezeigt, wenn Sie den Mauszeiger über die Schaltflächen auf der [Symbolleiste des Bild-Editors](../windows/toolbar-image-editor-for-icons.md)bewegen. Diese Tipps helfen Ihnen, die hier genannten spezifischen Schaltflächen zu identifizieren.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>So wählen Sie ein Zeichenwerkzeug aus der Symbolleiste des Bild-Editors aus und verwenden es

1. Wählen Sie eine Schaltfläche auf der **Symbolleiste des Bild-Editors** aus.

   - Das **Eraser-Werkzeug** zeichnet das Bild mit der aktuellen Hintergrundfarbe über, wenn Sie die linke Maustaste drücken.

      > [!TIP]
      > Anstatt das **Eraser-Werkzeug** zu verwenden, können Sie es bequemer finden, in der Hintergrundfarbe mit einem der Zeichenwerkzeuge zu zeichnen.

   - Das **Bleistiftwerkzeug** zeichnet Freihand in einer konstanten Breite von einem Pixel.

   - Das **Pinselwerkzeug** hat verschiedene Formen und Größen.

   - Das **Airbrush-Werkzeug** verteilt Farbpixel nach dem Zufallsprinzip um die Mitte des Pinsels.

1. Wählen Sie bei Bedarf Farben und einen Pinsel aus:

   - Wählen Sie in der [Farbpalette](../windows/colors-window-image-editor-for-icons.md)die linke Maustaste aus, um eine Vordergrundfarbe oder die rechte Maustaste auszuwählen, um eine Hintergrundfarbe auszuwählen.

   - Wählen Sie im [Auswahlselektor Optionen](../windows/toolbar-image-editor-for-icons.md)eine Form aus, die den Pinsel darstellt, den Sie verwenden möchten.

1. Zeigen Sie auf die Stelle auf dem Bild, an der Sie mit dem Zeichnen oder Malen beginnen möchten. Der Zeiger ändert die Form entsprechend dem ausgewählten Werkzeug.

1. Drücken Sie die linke Maustaste (für die Vordergrundfarbe) oder die rechte Maustaste (für die Hintergrundfarbe), und halten Sie sie beim Zeichnen gedrückt.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>So wählen Sie ein Zeichenwerkzeug aus dem Menü Bild aus und verwenden es

1. Gehen Sie zum Menü > **Bildwerkzeuge**. **Image**

1. Wählen Sie im Untermenü kaskadieren das Werkzeug aus, das Sie verwenden möchten.

## <a name="lines-or-closed-figures"></a>Linien oder geschlossene Zahlen

Die **Bildeditor-Werkzeuge** zum Zeichnen von Linien und geschlossenen Figuren funktionieren alle auf die gleiche Weise: Sie platzieren die Einfügemarke an einer Stelle und ziehen an einen anderen. Bei Linien sind diese Punkte die Endpunkte. Bei geschlossenen Figuren sind diese Punkte gegenüberliegende Ecken eines Rechtecks, das die Figur umschließt.

Linien werden in einer Breite gezeichnet, die durch die aktuelle Pinselauswahl bestimmt wird, und gerahmte Figuren werden in einer Breite gezeichnet, die durch die aktuelle Breitenauswahl bestimmt wird. Linien und alle Figuren, sowohl gerahmt als auch gefüllt, werden in der aktuellen Vordergrundfarbe gezeichnet, wenn Sie die linke Maustaste drücken, oder in der aktuellen Hintergrundfarbe, wenn Sie die rechte Maustaste drücken.

### <a name="to-draw-a-line"></a>So zeichnen Sie eine Linie

1. Verwenden Sie die [Symbolleiste des Bildeditors](../windows/toolbar-image-editor-for-icons.md) oder **Line** gehen Sie zum Menü **Bildwerkzeuge**> **Tools** und wählen Sie das Werkzeug Linie aus.

1. Wählen Sie bei Bedarf Farben und einen Pinsel aus:

   - Wählen Sie in der [Farbpalette](../windows/colors-window-image-editor-for-icons.md)die linke Maustaste aus, um eine Vordergrundfarbe oder die rechte Maustaste auszuwählen, um eine Hintergrundfarbe auszuwählen.

   - Wählen Sie im [Auswahlselektor Optionen](../windows/toolbar-image-editor-for-icons.md)eine Form aus, die den Pinsel darstellt, den Sie verwenden möchten.

1. Platzieren Sie den Zeiger am Startpunkt der Linie.

1. Ziehen Sie den Ziehpunkt an den Endpunkt der Linie.

### <a name="to-draw-a-closed-figure"></a>So zeichnen Sie eine geschlossene Figur

1. Verwenden Sie die **Symbolleiste des Bildeditors,** oder gehen Sie zum Menü > **Bildwerkzeuge** und wählen Sie ein Werkzeug für **die Zeichnung geschlossener Figuren** aus. **Image**

   Die Werkzeuge für **die Zeichnung geschlossener Figuren** erstellen Zahlen, wie auf den jeweiligen Schaltflächen angegeben.

1. Wählen Sie bei Bedarf Farben und eine Linienbreite aus.

1. Bewegen Sie den Zeiger in eine Ecke des rechteckigen Bereichs, in dem Sie die Figur zeichnen möchten.

1. Ziehen Sie den Zeiger in die diagonal gegenüberliegende Ecke.

## <a name="custom-brushes"></a>Benutzerdefinierte Pinsel

Ein benutzerdefinierter Pinsel ist ein rechteckiger Teil eines Bildes, den Sie wie einen der vorgefertigten Pinsel des **Bildeditors**aufnehmen und verwenden. Alle Vorgänge, die Sie für eine Auswahl ausführen können, können Sie auch auf einem benutzerdefinierten Pinsel ausführen.

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>So erstellen Sie einen benutzerdefinierten Pinsel aus einem Teil eines Bildes

1. Wählen Sie den Teil des Bildes aus, den Sie für einen Pinsel verwenden möchten.

1. Halten Sie die **Umschalttaste** gedrückt, wählen Sie in der Auswahl und ziehen Sie sie über das Bild, oder gehen Sie zum Menü **Bild** > **verwenden Auswahl als Pinsel**.

   Ihre Auswahl wird zu einem benutzerdefinierten Pinsel, der die Farben in der Auswahl über das Bild verteilt. Kopien der Auswahl werden entlang des Ziehpfads hinterlassen. Je langsamer Sie ziehen, desto mehr Kopien werden gemacht.

   > [!NOTE]
   > Wenn Sie die **Option Auswahl als Pinsel verwenden auswählen,** ohne vorher einen Teil des Bildes auszuwählen, wird das gesamte Bild als Pinsel verwendet. Das Ergebnis der Verwendung eines benutzerdefinierten Pinsels hängt auch davon ab, ob Sie einen [opaken oder transparenten Hintergrund](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)ausgewählt haben.

Pixel in einem benutzerdefinierten Pinsel, die der aktuellen Hintergrundfarbe entsprechen, sind normalerweise transparent: Sie malen nicht über das vorhandene Bild. Sie können dieses Verhalten so ändern, dass Hintergrundfarbpixel über das vorhandene Bild malen.

Sie können den benutzerdefinierten Pinsel wie einen Stempel oder eine Schablone verwenden, um verschiedene Spezialeffekte zu erstellen.

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>So zeichnen Sie benutzerdefinierte Pinselformen in der Hintergrundfarbe

1. Wählen Sie einen undurchsichtigen oder transparenten Hintergrund aus.

1. Legen Sie die Hintergrundfarbe auf die Farbe fest, in der Sie zeichnen möchten.

1. Positionieren Sie den benutzerdefinierten Pinsel an der Stelle, an der Sie zeichnen möchten.

1. Wählen Sie die rechte Maustaste. Alle undurchsichtigen Bereiche des benutzerdefinierten Pinsels werden in der Hintergrundfarbe gezeichnet.

### <a name="to-double-or-halve-the-custom-brush-size"></a>So verdoppeln oder halbieren Sie die benutzerdefinierte Pinselgröße

Drücken Sie die**+** **Plus-Zeichen-** ( ), um die**-** Pinselgröße zu verdoppeln, oder die **Minuszeichen** ( ), um sie zu halbieren.

### <a name="to-cancel-the-custom-brush"></a>So brechen Sie den benutzerdefinierten Pinsel ab

Drücken Sie **Esc,** oder wählen Sie ein anderes Zeichenwerkzeug aus.

## <a name="requirements"></a>Anforderungen

Keine

## <a name="see-also"></a>Siehe auch

[Bildbearbeitung für Symbole](../windows/image-editor-for-icons.md)<br/>
[Gewusst wie: Erstellen eines Symbols oder eines anderen Bildes](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Gewusst wie: Bearbeiten eines Bildes](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Gewusst wie: Arbeiten mit Farbe](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Beschleunigerschlüssel](../windows/accelerator-keys-image-editor-for-icons.md)<br/>

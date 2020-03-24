---
title: 'Gewusst wie: Verwenden eines Zeichnungs Tools'
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
ms.openlocfilehash: 61c06ee3fecac18fb95663c0d13474b8bd3b94f4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214382"
---
# <a name="how-to-use-a-drawing-tool"></a>Gewusst wie: Verwenden eines Zeichnungs Tools

Der **Bild-Editor** verfügt über freasing-Zeichnungs-und Lösch Tools, die alle auf dieselbe Weise funktionieren. Wählen Sie das Tool aus, und wählen Sie ggf. [Vordergrund-und Hintergrundfarben](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) sowie Optionen für Größe und Form aus. Dann bewegen Sie den Zeiger auf das Bild, und klicken oder ziehen Sie auf Zeichnen und löschen.

## <a name="drawing-tools"></a>Zeichnungs Tools

Sie können Zeichnungs Tools entweder auf der **Bild-Editor** -Symbolleiste oder im Menü **Bild** auswählen. Wenn Sie das **Radierertool** , das **Pinsel** Tool oder das **Airbrush** -Tool auswählen, zeigt die Option Selector die Optionen des Tools an.

> [!TIP]
>  Quick Infos werden angezeigt, wenn Sie mit dem Mauszeiger auf die Schaltflächen auf der [Symbolleiste Bild-Editor](../windows/toolbar-image-editor-for-icons.md)zeigen. Diese Tipps helfen Ihnen, die hier erwähnten spezifischen Schaltflächen zu identifizieren.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-editor-toolbar"></a>So wählen Sie ein Zeichnungs Tool aus der Symbolleiste des Bild-Editors aus und verwenden es

1. Wählen Sie auf der Symbolleiste der **Bild** Bearbeitung eine Schaltfläche aus.

   - Das **erradiertool** zeichnet über das Bild mit der aktuellen Hintergrundfarbe, wenn Sie mit der linken Maustaste klicken.

      > [!TIP]
      > Anstatt das **Radierertool** zu verwenden, ist es möglicherweise bequemer, mit einem der Zeichnungs Tools in der Hintergrundfarbe zu zeichnen.

   - Das **Stift** Werkzeug zeichnet frei handlinie in einer Konstanten Breite von einem Pixel.

   - Das **Pinsel** Tool hat verschiedene Formen und Größen.

   - Das **Airbrush** -Tool verteilt nach dem Zufallsprinzip Farb Pixel um den Mittelpunkt des Pinsels.

1. Wählen Sie ggf. Farben und einen Pinsel aus:

   - Wählen Sie in der [Palette Farben](../windows/colors-window-image-editor-for-icons.md)die linke Maustaste aus, um eine Vordergrundfarbe oder die Rechte Maustaste auszuwählen, um eine Hintergrundfarbe auszuwählen.

   - Wählen Sie im [options-Selektor](../windows/toolbar-image-editor-for-icons.md)eine Form aus, die den zu verwendenden Pinsel darstellt.

1. Zeigen Sie auf die Position auf dem Bild, an der Sie mit dem Zeichnen oder Zeichnen beginnen möchten. Die Form des Zeigers ändert sich je nach ausgewähltem Tool.

1. Drücken Sie die linke Maustaste (für die Vordergrundfarbe) oder die Rechte Maustaste (für die Hintergrundfarbe), und halten Sie die Maustaste gedrückt, während Sie zeichnen.

### <a name="to-select-and-use-a-drawing-tool-from-the-image-menu"></a>So wählen Sie ein Zeichnungs Tool aus dem Menü "Bild" aus und verwenden es

1. Wechseln Sie zu Menü **Bild** > **Tools**.

1. Wählen Sie im Untermenü Cascading das Tool aus, das Sie verwenden möchten.

## <a name="lines-or-closed-figures"></a>Zeilen oder geschlossene Abbildungen

Die **Bild-Editor** -Tools zum Zeichnen von Linien und geschlossenen Abbildungen funktionieren auf die gleiche Weise: Sie platzieren die Einfügemarke an einem Punkt und ziehen Sie in einen anderen. Für Zeilen sind diese Punkte die Endpunkte. Bei geschlossenen Abbildungen sind diese Punkte gegen Ende Ecken eines Rechtecks, das die Figur schließt.

Zeilen werden in einer Breite gezeichnet, die von der aktuellen Pinsel Auswahl bestimmt wird, und die eingezogenen Abbildungen werden in einer Breite gezeichnet, die von der aktuellen breiten Auswahl bestimmt wird. Zeilen und alle Abbildungen, die sowohl eingeschlossen als auch ausgefüllt sind, werden in der aktuellen Vordergrundfarbe gezeichnet, wenn Sie die linke Maustaste drücken, oder in der aktuellen Hintergrundfarbe, wenn Sie mit der rechten Maustaste klicken.

### <a name="to-draw-a-line"></a>So zeichnen Sie eine Linie

1. Verwenden Sie die [Symbolleiste Bild](../windows/toolbar-image-editor-for-icons.md) Bearbeitung, oder wechseln Sie zu Menü **Bild**> **Tools** , und wählen Sie das **Linien** Tool aus.

1. Wählen Sie ggf. Farben und einen Pinsel aus:

   - Wählen Sie in der [Palette Farben](../windows/colors-window-image-editor-for-icons.md)die linke Maustaste aus, um eine Vordergrundfarbe oder die Rechte Maustaste auszuwählen, um eine Hintergrundfarbe auszuwählen.

   - Wählen Sie im [options-Selektor](../windows/toolbar-image-editor-for-icons.md)eine Form aus, die den zu verwendenden Pinsel darstellt.

1. Platzieren Sie den Zeiger am Ausgangspunkt der Zeile.

1. Ziehen Sie zum Endpunkt der Zeile.

### <a name="to-draw-a-closed-figure"></a>So zeichnen Sie eine geschlossene Abbildung

1. Verwenden Sie die Symbolleiste des **Bild-Editors** , oder wechseln Sie zu Menü **Bild** > **Tools** , und wählen Sie ein **geschlossenes Zeichnungs** Tool aus.

   Die **Closed-Figure-Zeichnungs** Tools erstellen Abbildungen entsprechend den jeweiligen Schaltflächen.

1. Wählen Sie ggf. Farben und eine Linienstärke aus.

1. Bewegen Sie den Zeiger in eine Ecke des rechteckigen Bereichs, in dem Sie die Abbildung zeichnen möchten.

1. Ziehen Sie den Zeiger auf die diagonal entgegengesetzte Ecke.

## <a name="custom-brushes"></a>Benutzerdefinierte Pinsel

Ein benutzerdefinierter Pinsel ist ein rechteckiger Teil eines Bilds, das Sie auswählen und wie einen der vorgefertigten Pinsel des **Bild-Editors**verwenden. Alle Vorgänge, die Sie für eine Auswahl ausführen können, können auch für einen benutzerdefinierten Pinsel durchgeführt werden.

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>So erstellen Sie einen benutzerdefinierten Pinsel aus einem Teil eines Bilds

1. Wählen Sie den Teil des Bilds aus, den Sie für einen Pinsel verwenden möchten.

1. Halten Sie die UMSCHALTTASTE gedrückt, wählen Sie in der Auswahl aus, und ziehen Sie Sie auf das Bild, oder **wechseln** Sie zum Menü **Bild** , > **Auswahl als Pinsel zu verwenden**.

   Ihre Auswahl wird zu einem benutzerdefinierten Pinsel, der die Farben in der Auswahl über das Bild verteilt. Kopien der Auswahl bleiben entlang des Zieh Pfades. Wenn Sie langsamer ziehen, werden weitere Kopien erstellt.

   > [!NOTE]
   > Wenn Sie die Option **Auswahl als Pinsel verwenden** auswählen, ohne zuerst einen Teil des Bilds auszuwählen, wird das gesamte Bild als Pinsel verwendet. Das Ergebnis der Verwendung eines benutzerdefinierten Pinsels hängt auch davon ab, ob Sie einen nicht [transparenten oder transparenten Hintergrund](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md)ausgewählt haben.

Pixel in einem benutzerdefinierten Pinsel, die der aktuellen Hintergrundfarbe entsprechen, sind normalerweise transparent: Sie zeichnen sich nicht über das vorhandene Bild aus. Sie können dieses Verhalten ändern, damit die Hintergrundfarbe der Pixel über dem vorhandenen Bild gezeichnet wird.

Sie können den benutzerdefinierten Pinsel wie einen Stempel oder eine Schablone verwenden, um unterschiedliche besondere Effekte zu erstellen.

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>So zeichnen Sie benutzerdefinierte Pinselformen in der Hintergrundfarbe

1. Wählen Sie einen transparenten oder transparenten Hintergrund aus.

1. Legen Sie die Hintergrundfarbe auf die Farbe fest, in der Sie zeichnen möchten.

1. Positionieren Sie den benutzerdefinierten Pinsel, an dem gezeichnet werden soll.

1. Klicken Sie mit der rechten Maustaste. Alle nicht transparenten Bereiche des benutzerdefinierten Pinsels werden in der Hintergrundfarbe gezeichnet.

### <a name="to-double-or-halve-the-custom-brush-size"></a>So verdoppeln oder halbieren Sie die benutzerdefinierte Pinselgröße

Drücken Sie die Taste mit dem **Plus Zeichen** ( **+** ), um die Pinselgröße zu verdoppeln, oder die **Minus Zeichen** Taste ( **-** ), um Sie zu halbieren.

### <a name="to-cancel-the-custom-brush"></a>So brechen Sie den benutzerdefinierten Pinsel ab

Drücken Sie **ESC** , oder wählen Sie ein anderes Zeichnungs Tool.

## <a name="requirements"></a>Requirements (Anforderungen)

Keine

## <a name="see-also"></a>Weitere Informationen

[Bildbearbeitung für Symbole](../windows/image-editor-for-icons.md)<br/>
[Gewusst wie: Erstellen eines Symbols oder eines anderen Bilds](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Gewusst wie: Bearbeiten eines Bilds](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Gewusst wie: Arbeiten mit Farben](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Zugriffstasten](../windows/accelerator-keys-image-editor-for-icons.md)<br/>

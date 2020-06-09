---
title: 'MFC-ActiveX-Steuerelemente: Darstellen eines ActiveX-Steuerelements'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
ms.openlocfilehash: a01a66402471b295a6e57af8af265c50685b4a1f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618220"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>MFC-ActiveX-Steuerelemente: Darstellen eines ActiveX-Steuerelements

In diesem Artikel wird der Zeichnungsprozess des ActiveX-Steuer Elements beschrieben und erläutert, wie Sie Paint Code ändern können, um den Prozess zu optimieren (Weitere Informationen zum Optimieren der Zeichnung finden Sie unter [Optimieren der Steuerelement Zeichnung](optimizing-control-drawing.md) , indem Sie die zuvor ausgewählten GDI-Objekte nicht einzeln wiederherstellen. Nachdem alle Steuerelemente gezeichnet wurden, kann der Container die ursprünglichen Objekte automatisch wiederherstellen.)

>[!IMPORTANT]
> ActiveX ist eine ältere Technologie, die nicht für die neue Entwicklung verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ersetzen, finden Sie unter ActiveX-Steuer [Elemente](activex-controls.md).

Die Beispiele in diesem Artikel stammen aus einem Steuerelement, das vom MFC-ActiveX-Steuerelement-Assistenten mit Standardeinstellungen erstellt wurde. Weitere Informationen zum Erstellen einer Skeleton-Steuerungsanwendung mithilfe des MFC-ActiveX-Steuerelement-Assistenten finden Sie im Artikel [MFC-ActiveX-Steuer](reference/mfc-activex-control-wizard.md)Element-Assistent.

Die folgenden Themen werden erörtert:

- [Der Gesamtprozess zum Zeichnen eines Steuer Elements und des vom ActiveX-Steuerelement-Assistenten erstellten Codes zur Unterstützung von Zeichnungen](#_core_the_painting_process_of_an_activex_control)

- [Optimieren des Zeichnungsprozesses](#_core_optimizing_your_paint_code)

- [So zeichnen Sie das Steuerelement mithilfe von Metadateien](#_core_painting_your_control_using_metafiles)

## <a name="the-painting-process-of-an-activex-control"></a><a name="_core_the_painting_process_of_an_activex_control"></a>Der Zeichnungsprozess eines ActiveX-Steuer Elements.

Wenn ActiveX-Steuerelemente anfänglich angezeigt oder neu gezeichnet werden, befolgen Sie einen Zeichnungsprozess, der mit anderen Anwendungen vergleichbar ist, die mit MFC entwickelt wurden, mit einem wichtigen Unterschied: ActiveX-Steuerelemente können sich in einem aktiven oder inaktiven Zustand befinden.

Ein aktives Steuerelement wird in einem ActiveX-Steuerelement Container durch ein untergeordnetes Fenster dargestellt. Wie bei anderen Fenstern ist es für das Zeichnen selbst zuständig, wenn eine WM_PAINT Nachricht empfangen wird. Diese Meldung wird von der Basisklasse [COleControl](reference/colecontrol-class.md)des Steuer Elements in der `OnPaint` Funktion behandelt. Diese Standard Implementierung ruft die- `OnDraw` Funktion des Steuer Elements auf.

Ein inaktives Steuerelement wird anders gezeichnet. Wenn das Steuerelement inaktiv ist, ist sein Fenster unsichtbar oder nicht vorhanden, sodass keine Zeichnungs Nachricht empfangen werden kann. Stattdessen ruft der Steuerelement Container direkt die- `OnDraw` Funktion des Steuer Elements auf. Dies unterscheidet sich vom Zeichnungsprozess eines aktiven Steuer Elements darin, dass die `OnPaint` Member-Funktion niemals aufgerufen wird.

Wie in den vorangehenden Abschnitten erläutert, hängt die Aktualisierung des ActiveX-Steuer Elements vom Zustand des-Steuer Elements ab. Da das Framework jedoch `OnDraw` in beiden Fällen die Member-Funktion aufruft, fügen Sie den Großteil ihres Zeichnungs Codes in diese Element Funktion ein.

Die `OnDraw` Member-Funktion behandelt das Zeichnen von Steuerelementen. Wenn ein Steuerelement inaktiv ist, ruft der Steuerelement Container `OnDraw` auf und übergibt dabei den Gerätekontext des Steuerelement Containers und die Koordinaten des rechteckigen Bereichs, der vom Steuerelement besetzt ist.

Das vom Framework an die Member-Funktion über gegebene Rechteck `OnDraw` enthält den Bereich, der vom-Steuerelement belegt wird. Wenn das Steuerelement aktiv ist, ist die linke obere Ecke (0,0) und der übergebenen Gerätekontext für das untergeordnete Fenster, das das Steuerelement enthält. Wenn das Steuerelement inaktiv ist, ist die linke obere Koordinate nicht notwendigerweise (0,0), und der übergebenen Gerätekontext ist für den Steuerelement Container, der das Steuerelement enthält.

> [!NOTE]
> Es ist wichtig, dass die Änderungen an `OnDraw` nicht davon abhängen, dass die obere linke Ecke des Rechtecks gleich (0,0) ist und Sie nur innerhalb des Rechtecks zeichnen, das an weitergegeben wurde `OnDraw` . Unerwartete Ergebnisse können auftreten, wenn Sie über den Bereich des Rechtecks hinaus zeichnen.

Die vom MFC-ActiveX-Steuerelement-Assistenten in der Implementierungs Datei des Steuer Elements bereitgestellte Standard Implementierung (. Cpp), wie unten gezeigt, zeichnet das Rechteck mit einem weißen Pinsel und füllt die Ellipse mit der aktuellen Hintergrundfarbe aus.

[!code-cpp[NVC_MFC_AxUI#1](codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]

> [!NOTE]
> Wenn Sie ein Steuerelement zeichnen, sollten Sie keine Annahmen über den Zustand des Geräte Kontexts treffen, der als *PDC* -Parameter an die Funktion übergeben wird `OnDraw` . Der Gerätekontext wird gelegentlich von der Containeranwendung bereitgestellt und nicht unbedingt mit dem Standardzustand initialisiert. Insbesondere können Sie die Stifte, Pinsel, Farben, Schriftarten und andere Ressourcen, von denen Ihr Zeichnungs Code abhängt, explizit auswählen.

## <a name="optimizing-your-paint-code"></a><a name="_core_optimizing_your_paint_code"></a>Optimieren Ihres Zeichnungs Codes

Nachdem das Steuerelement sich selbst erfolgreich gezeichnet hat, besteht der nächste Schritt in der Optimierung der `OnDraw` Funktion.

Die Standard Implementierung des ActiveX-Steuerelement Gemäldes zeichnet den gesamten Steuerelement Bereich. Dies ist für einfache Steuerelemente ausreichend, aber in vielen Fällen wäre das Neuzeichnen des Steuer Elements schneller, wenn nur der Teil, der aktualisiert werden musste, anstelle des gesamten Steuer Elements neu gezeichnet wurde.

Die- `OnDraw` Funktion bietet eine einfache Optimierungsmethode, indem *rcInvalid*übergeben wird, der rechteckige Bereich des-Steuer Elements, das neu gezeichnet werden muss. Verwenden Sie diesen Bereich, der normalerweise kleiner als der gesamte Steuerungs Bereich ist, um den Zeichnungsprozess zu beschleunigen.

## <a name="painting-your-control-using-metafiles"></a><a name="_core_painting_your_control_using_metafiles"></a>Zeichnen Ihres Steuer Elements mithilfe von Metafiles

In den meisten Fällen zeigt der *PDC* -Parameter für die `OnDraw` Funktion auf einen Bildschirm Gerätekontext (DC). Beim Drucken von Bildern des Steuer Elements oder während einer Seiten Ansichts Sitzung ist der für das Rendering empfangene DC jedoch ein spezieller Typ, der als "metadateidc" bezeichnet wird. Im Gegensatz zu einem Bildschirm-DC, der sofort an ihn gesendete Anforderungen verarbeitet, speichert ein metadateidc Anforderungen, die zu einem späteren Zeitpunkt wiedergegeben werden. Einige Container Anwendungen können das Steuerelement Bild auch im Entwurfs Modus mithilfe eines metadateicontrollers Renderern.

Metafile-Zeichnungs Anforderungen können durch den Container über zwei Schnittstellen Funktionen hergestellt werden: `IViewObject::Draw` (diese Funktion kann auch für das Zeichnen von nicht-Metadateien aufgerufen werden) und `IDataObject::GetData` . Wenn ein metadateidc als einer der Parameter übergeben wird, ruft das MFC-Framework [COleControl:: OnDrawMetafile](reference/colecontrol-class.md#ondrawmetafile)auf. Da es sich hierbei um eine virtuelle Element Funktion handelt, überschreiben Sie diese Funktion in der Steuerelement Klasse, um eine bestimmte Verarbeitung durchzuführen. Das Standardverhalten Ruft auf `COleControl::OnDraw` .

Um sicherzustellen, dass das Steuerelement sowohl im Bildschirm-als auch im Metadatei-Gerätekontext gezeichnet werden kann, müssen Sie nur Element Funktionen verwenden, die sowohl auf einem Bildschirm als auch auf einem metadateidc Beachten Sie, dass das Koordinatensystem möglicherweise nicht in Pixel gemessen wird.

Da die Standard Implementierung von `OnDrawMetafile` die-Funktion des-Steuer Elements aufruft `OnDraw` , verwenden Sie nur Member-Funktionen, die für eine Metadatei und einen Bildschirm-Gerätekontext geeignet sind, es sei denn, Sie überschreiben `OnDrawMetafile` . Im folgenden finden Sie eine Liste der Teilmenge der Element `CDC` Funktionen, die sowohl in einem Metadatei-als auch auf einem Bildschirm-Gerätekontext verwendet werden kann. Weitere Informationen zu diesen Funktionen finden Sie unter Class [CDC](reference/cdc-class.md) in der *MFC-Referenz*.

|Arc|Bibblt|Chord|
|---------|------------|-----------|
|`Ellipse`|`Escape`|`ExcludeClipRect`|
|`ExtTextOut`|`FloodFill`|`IntersectClipRect`|
|`LineTo`|`MoveTo`|`OffsetClipRgn`|
|`OffsetViewportOrg`|`OffsetWindowOrg`|`PatBlt`|
|`Pie`|`Polygon`|`Polyline`|
|`PolyPolygon`|`RealizePalette`|`RestoreDC`|
|`RoundRect`|`SaveDC`|`ScaleViewportExt`|
|`ScaleWindowExt`|`SelectClipRgn`|`SelectObject`|
|`SelectPalette`|`SetBkColor`|`SetBkMode`|
|`SetMapMode`|`SetMapperFlags`|`SetPixel`|
|`SetPolyFillMode`|`SetROP2`|`SetStretchBltMode`|
|`SetTextColor`|`SetTextJustification`|`SetViewportExt`|
|`SetViewportOrg`|`SetWindowExt`|`SetWindowORg`|
|`StretchBlt`|`TextOut`||

Zusätzlich zu den `CDC` Member-Funktionen gibt es mehrere andere Funktionen, die in einem metadateidc kompatibel sind. Hierzu gehören [CPalette:: AnimatePalette](reference/cpalette-class.md#animatepalette), [CFont:: kreatefontindirekte](reference/cfont-class.md#createfontindirect)und drei Member-Funktionen von `CBrush` : " [kreatebrushindirekte](reference/cbrush-class.md#createbrushindirect)", " [kreatedibpatternbrush](reference/cbrush-class.md#createdibpatternbrush)" und " [kreatepatternbrush](reference/cbrush-class.md#createpatternbrush)".

Funktionen, die nicht in einer Metadatei aufgezeichnet werden, sind: [drawfoclaufrect](reference/cdc-class.md#drawfocusrect), [DrawIcon](reference/cdc-class.md#drawicon), [DrawText](reference/cdc-class.md#drawtext), [excludeupdatergn](reference/cdc-class.md#excludeupdatergn), [fillRect](reference/cdc-class.md#fillrect), [frameRect](reference/cdc-class.md#framerect), [graystring](reference/cdc-class.md#graystring), [invertrect](reference/cdc-class.md#invertrect), [scrolldc](reference/cdc-class.md#scrolldc)und [tabbedtextout](reference/cdc-class.md#tabbedtextout). Da ein metadateidc nicht tatsächlich einem Gerät zugeordnet ist, können Sie SetDIBits, GetDIBits und kreatedibitmap nicht mit einem metadateidc verwenden. Sie können SetDIBitsToDevice und StretchDIBits mit einem metadateidc als Ziel verwenden. " [Kreatecompatibledc](reference/cdc-class.md#createcompatibledc)", " [kreatecompatiblebitmap](reference/cbitmap-class.md#createcompatiblebitmap)" und " [kreateverwerdablebitmap](reference/cbitmap-class.md#creatediscardablebitmap) " sind mit einem metadateidc nicht sinnvoll.

Ein weiterer Punkt, der bei der Verwendung eines metadateidc zu beachten ist, besteht darin, dass das Koordinatensystem in Pixel nicht gemessen werden kann Aus diesem Grund sollte der gesamte Zeichnungs Code so angepasst werden, dass er in das Rechteck passt, das `OnDraw` im *rcBounds* -Parameter an übergeben wird. Dadurch wird das versehentliche zeichnen außerhalb des Steuer Elements verhindert, da *rcBounds* die Größe des Steuer Elements des Steuer Elements darstellt.

Nachdem Sie das Metadatei-Rendering für das-Steuerelement implementiert haben, testen Sie die Metadatei mit dem Test Container. Informationen zum Zugriff auf den Testcontainer finden Sie unter [Testen von Eigenschaften und Ereignissen mit dem Testcontainer](testing-properties-and-events-with-test-container.md) .

#### <a name="to-test-the-controls-metafile-using-test-container"></a>So testen Sie die Metadatei des Steuer Elements mit dem Test Container

1. Klicken Sie im Menü **Bearbeiten** des Test Containers auf **neues Steuerelement einfügen**.

1. Wählen Sie im Feld **neues Steuerelement einfügen** das Steuerelement aus, und klicken Sie auf **OK**.

   Das Steuerelement wird im Test Container angezeigt.

1. Klicken Sie im Menü **Steuerung** auf **Metadatei zeichnen**.

   Ein separates Fenster wird angezeigt, in dem die Metadatei angezeigt wird. Sie können die Größe dieses Fensters ändern, um zu sehen, wie sich die Skalierung auf die Metadatei des Steuer Elements auswirkt. Sie können dieses Fenster jederzeit schließen.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)

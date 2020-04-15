---
title: 'MFC-ActiveX-Steuerelemente: Darstellen eines ActiveX-Steuerelements'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], painting
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 25fff9c0-4dab-4704-aaae-8dfb1065dee3
ms.openlocfilehash: fd98af90e86b6b98a856e633e50c5bf266cc466a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364585"
---
# <a name="mfc-activex-controls-painting-an-activex-control"></a>MFC-ActiveX-Steuerelemente: Darstellen eines ActiveX-Steuerelements

In diesem Artikel wird der ActiveX-Steuerelementlackierungsprozess beschrieben und erläutert, wie Sie Denlackcode ändern können, um den Prozess zu optimieren. ((Siehe Optimieren der [Steuerungszeichnung](../mfc/optimizing-control-drawing.md) für Techniken zum Optimieren der Zeichnung, indem Steuerelemente nicht einzeln wiederhergestellt werden, um zuvor ausgewählte GDI-Objekte wiederherzustellen. Nachdem alle Steuerelemente gezeichnet wurden, kann der Container die ursprünglichen Objekte automatisch wiederherstellen.)

>[!IMPORTANT]
> ActiveX ist eine legacy Technologie, die nicht für Neuentwicklungen verwendet werden sollte. Weitere Informationen zu modernen Technologien, die ActiveX ablösen, finden Sie unter [ActiveX Controls](activex-controls.md).

Beispiele in diesem Artikel sind ein Steuerelement, das vom MFC ActiveX Control Wizard mit Standardeinstellungen erstellt wurde. Weitere Informationen zum Erstellen einer Skelettsteuerungsanwendung mit dem MFC ActiveX Control Wizard finden Sie im Artikel [MFC ActiveX Control Wizard](../mfc/reference/mfc-activex-control-wizard.md).

Die folgenden Themen werden erörtert:

- [Der gesamte Prozess zum Malen eines Steuerelements und des Codes, der vom ActiveX Control Wizard zur Unterstützung des Lackierens erstellt wurde.](#_core_the_painting_process_of_an_activex_control)

- [So optimieren Sie den Lackierprozess](#_core_optimizing_your_paint_code)

- [So malen Sie Ihr Steuerelement mit Metadateien](#_core_painting_your_control_using_metafiles)

## <a name="the-painting-process-of-an-activex-control"></a><a name="_core_the_painting_process_of_an_activex_control"></a>Der Malprozess eines ActiveX-Steuerelements

Wenn ActiveX-Steuerelemente anfänglich angezeigt oder neu gezeichnet werden, folgen sie einem Malprozess, der anderen Anwendungen ähnelt, die mit MFC entwickelt wurden, mit einem wichtigen Unterschied: ActiveX-Steuerelemente können sich in einem aktiven oder inaktiven Zustand befinden.

Ein aktives Steuerelement wird in einem ActiveX-Steuerelementcontainer durch ein untergeordnetes Fenster dargestellt. Wie andere Fenster ist es für das Malen selbst verantwortlich, wenn eine WM_PAINT Nachricht empfangen wird. Die Basisklasse des Steuerelements, [COleControl](../mfc/reference/colecontrol-class.md), `OnPaint` verarbeitet diese Meldung in ihrer Funktion. Diese Standardimplementierung `OnDraw` ruft die Funktion Ihres Steuerelements auf.

Ein inaktives Steuerelement wird anders dargestellt. Wenn das Steuerelement inaktiv ist, ist das Fenster entweder unsichtbar oder nicht vorhanden, sodass es keine Paint-Nachricht empfangen kann. Stattdessen ruft der Steuerelementcontainer `OnDraw` direkt die Funktion des Steuerelements auf. Dies unterscheidet sich vom Malprozess eines `OnPaint` aktiven Steuerelements dadurch, dass die Memberfunktion nie aufgerufen wird.

Wie in den vorherigen Absätzen erläutert, hängt die Aktualisierung eines ActiveX-Steuerelements vom Status des Steuerelements ab. Da das Framework jedoch `OnDraw` in beiden Fällen die Memberfunktion aufruft, fügen Sie den Großteil des Malcodes in dieser Memberfunktion hinzu.

Die `OnDraw` Memberfunktion behandelt die Steuerungsmalerei. Wenn ein Steuerelement inaktiv ist, `OnDraw`ruft der Steuerelementcontainer auf, indem er den Gerätekontext des Steuerelementcontainers und die Koordinaten des rechteckigen Bereichs, der vom Steuerelement belegt wird, übergibt.

Das Rechteck, das vom `OnDraw` Framework an die Memberfunktion übergeben wird, enthält den bereich, der vom Steuerelement belegt wird. Wenn das Steuerelement aktiv ist, ist die obere linke Ecke (0, 0) und der übergebene Gerätekontext ist für das untergeordnete Fenster, das das Steuerelement enthält. Wenn das Steuerelement inaktiv ist, ist die obere linke Koordinate nicht notwendigerweise (0, 0) und der übergebene Gerätekontext ist für den Steuerelementcontainer, der das Steuerelement enthält.

> [!NOTE]
> Es ist wichtig, `OnDraw` dass Ihre Änderungen nicht davon abhängen, ob der obere linke Punkt des Rechtecks gleich `OnDraw`(0, 0) ist, und dass Sie nur innerhalb des Rechtecks zeichnen, das an übergeben wird. Unerwartete Ergebnisse können auftreten, wenn Sie über den Bereich des Rechtecks hinaus zeichnen.

Die Standardimplementierung, die vom MFC ActiveX Control Wizard in der Steuerelementimplementierungsdatei (. CPP), siehe unten, malt das Rechteck mit einem weißen Pinsel und füllt die Ellipse mit der aktuellen Hintergrundfarbe.

[!code-cpp[NVC_MFC_AxUI#1](../mfc/codesnippet/cpp/mfc-activex-controls-painting-an-activex-control_1.cpp)]

> [!NOTE]
> Beim Zeichnen eines Steuerelements sollten Sie keine Annahmen über den Zustand des Gerätekontexts `OnDraw` treffen, der als *pdc-Parameter* an die Funktion übergeben wird. Gelegentlich wird der Gerätekontext von der Containeranwendung bereitgestellt und nicht unbedingt in den Standardzustand initialisiert. Wählen Sie insbesondere explizit die Stifte, Pinsel, Farben, Schriftarten und andere Ressourcen aus, von denen Ihr Zeichencode abhängt.

## <a name="optimizing-your-paint-code"></a><a name="_core_optimizing_your_paint_code"></a>Optimieren Ihres Farbcodes

Nachdem das Steuerelement sich erfolgreich selbst gemalt hat, besteht der nächste Schritt darin, die `OnDraw` Funktion zu optimieren.

Die Standardimplementierung der ActiveX-Steuerelementlackierung zeichnet den gesamten Kontrollbereich. Dies ist für einfache Steuerelemente ausreichend, aber in vielen Fällen wäre das Neulackieren des Steuerelements schneller, wenn nur der Teil, der aktualisiert werden musste, anstelle des gesamten Steuerelements neu lackiert würde.

Die `OnDraw` Funktion bietet eine einfache Methode der Optimierung durch Übergeben *von rcInvalid*, der rechteckige Bereich des Steuerelements, das neu gezeichnet werden muss. Verwenden Sie diesen Bereich, der in der Regel kleiner als der gesamte Kontrollbereich ist, um den Lackiervorgang zu beschleunigen.

## <a name="painting-your-control-using-metafiles"></a><a name="_core_painting_your_control_using_metafiles"></a>Malen Sie Ihr Steuerelement mit Metadateien

In den meisten Fällen zeigt `OnDraw` der *pdc-Parameter* zur Funktion auf einen Bildschirmgerätekontext (DC). Beim Drucken von Bildern des Steuerelements oder während einer Druckvorschausitzung ist der für das Rendern empfangene Domänencontroller jedoch ein spezieller Typ, der als "Metadatei-DC" bezeichnet wird. Im Gegensatz zu einem Bildschirm-DC, der sofort an ihn gesendete Anforderungen verarbeitet, speichert ein Metadatei-DC Anforderungen, die zu einem späteren Zeitpunkt wiedergegeben werden sollen. Einige Containeranwendungen können das Steuerelementabbild auch mithilfe eines Metadatei-DC im Entwurfsmodus rendern.

Metadateizeichnungsanforderungen können vom Container über zwei `IViewObject::Draw` Schnittstellenfunktionen gestellt werden: (diese Funktion kann `IDataObject::GetData`auch für nicht-Metafile-Zeichnung aufgerufen werden) und . Wenn ein Metadatei-DC als einer der Parameter übergeben wird, ruft das MFC-Framework [COleControl::OnDrawMetafile](../mfc/reference/colecontrol-class.md#ondrawmetafile)auf. Da es sich um eine virtuelle Memberfunktion handelt, überschreiben Sie diese Funktion in der Steuerelementklasse, um eine spezielle Verarbeitung zu übernehmen. Das Standardverhalten `COleControl::OnDraw`ruft auf.

Um sicherzustellen, dass das Steuerelement sowohl in Bildschirm- als auch in Metadateigerätekontexten gezeichnet werden kann, dürfen Sie nur Memberfunktionen verwenden, die sowohl in einem Bildschirm als auch in einem Metadatei-DC unterstützt werden. Beachten Sie, dass das Koordinatensystem möglicherweise nicht in Pixeln gemessen wird.

Da die Standardimplementierung von `OnDrawMetafile` Aufrufen `OnDraw` der Funktion des Steuerelements, verwenden Sie nur Memberfunktionen, die sowohl `OnDrawMetafile`für eine Metadatei als auch für einen Bildschirmgerätekontext geeignet sind, es sei denn, Sie überschreiben . Im Folgenden wird die `CDC` Teilmenge der Memberfunktionen aufgeführt, die sowohl in einer Metadatei als auch in einem Bildschirmgerätekontext verwendet werden können. Weitere Informationen zu diesen Funktionen finden Sie unter Klasse [CDC](../mfc/reference/cdc-class.md) in der *MFC-Referenz*.

|Arc|BibBlt|Chord|
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

Zusätzlich zu `CDC` den Memberfunktionen gibt es mehrere weitere Funktionen, die in einem Metadatei-DC kompatibel sind. Dazu gehören [CPalette::AnimatePalette](../mfc/reference/cpalette-class.md#animatepalette), [CFont::CreateFontIndirect](../mfc/reference/cfont-class.md#createfontindirect)und `CBrush`drei Memberfunktionen von : [CreateBrushIndirect](../mfc/reference/cbrush-class.md#createbrushindirect), [CreateDIBPatternBrush](../mfc/reference/cbrush-class.md#createdibpatternbrush)und [CreatePatternBrush](../mfc/reference/cbrush-class.md#createpatternbrush).

Funktionen, die nicht in einer Metadatei aufgezeichnet werden, sind: [DrawFocusRect](../mfc/reference/cdc-class.md#drawfocusrect), [DrawIcon](../mfc/reference/cdc-class.md#drawicon), [DrawText](../mfc/reference/cdc-class.md#drawtext), [ExcludeUpdateRgn](../mfc/reference/cdc-class.md#excludeupdatergn), [FillRect](../mfc/reference/cdc-class.md#fillrect), [FrameRect](../mfc/reference/cdc-class.md#framerect), [GrayString](../mfc/reference/cdc-class.md#graystring), [InvertRect](../mfc/reference/cdc-class.md#invertrect), [ScrollDC](../mfc/reference/cdc-class.md#scrolldc)und [TabbedTextOut](../mfc/reference/cdc-class.md#tabbedtextout). Da ein Metadatei-DC nicht tatsächlich einem Gerät zugeordnet ist, können Sie SetDIBits, GetDIBits und CreateDIBitmap nicht mit einem Metadatei-DC verwenden. Sie können SetDIBitsToDevice und StretchDIBits mit einem Metadatei-DC als Ziel verwenden. [CreateCompatibleDC](../mfc/reference/cdc-class.md#createcompatibledc), [CreateCompatibleBitmap](../mfc/reference/cbitmap-class.md#createcompatiblebitmap)und [CreateDiscardableBitmap](../mfc/reference/cbitmap-class.md#creatediscardablebitmap) sind mit einem Metadatei-DC nicht aussagekräftig.

Ein weiterer Punkt, der bei der Verwendung eines Metadatei-DC zu berücksichtigen ist, ist, dass das Koordinatensystem möglicherweise nicht in Pixeln gemessen wird. Aus diesem Grund sollte der gesamte Zeichnungscode so `OnDraw` angepasst werden, dass er in das Rechteck passt, an das im Parameter *rcBounds* übergeben wird. Dadurch wird ein versehentliches Lackieren außerhalb des Steuerelements verhindert, da *rcBounds* die Größe des Fensters des Steuerelements darstellt.

Nachdem Sie das Metadateirendering für das Steuerelement implementiert haben, verwenden Sie Testcontainer, um die Metadatei zu testen. Informationen zum Zugriff auf den Testcontainer finden Sie unter [Testen von Eigenschaften und Ereignissen mit dem Testcontainer](../mfc/testing-properties-and-events-with-test-container.md) .

#### <a name="to-test-the-controls-metafile-using-test-container"></a>So testen Sie die Metadatei des Steuerelements mithilfe des Testcontainers

1. Klicken Sie im Menü **Bearbeiten** des Testcontainers auf **Neues Steuerelement einfügen**.

1. Wählen Sie im Feld **Neue Steuerung einfügen** das Steuerelement aus, und klicken Sie auf **OK**.

   Das Steuerelement wird im Testcontainer angezeigt.

1. Klicken Sie im Menü **Steuerung** auf **Metadatei zeichnen**.

   Es wird ein separates Fenster angezeigt, in dem die Metadatei angezeigt wird. Sie können die Größe dieses Fensters ändern, um zu sehen, wie sich die Skalierung auf die Metadatei des Steuerelements auswirkt. Sie können dieses Fenster jederzeit schließen.

## <a name="see-also"></a>Siehe auch

[MFC-ActiveX-Steuerelemente](../mfc/mfc-activex-controls.md)

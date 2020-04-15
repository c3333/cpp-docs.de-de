---
title: 'TN040: MFC-OLE In-Place-Größenänderung und Zoomen'
ms.date: 11/04/2016
helpviewer_keywords:
- resizing in-place
- TN040
- zooming and in-place activation
- in-place activation, zooming and resizing
ms.assetid: 4d7859bd-0b2e-4254-be62-2735cecf02c6
ms.openlocfilehash: 65f9ef04c9740e8e6f0a8e72d9d6c39008198755
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372167"
---
# <a name="tn040-mfcole-in-place-resizing-and-zooming"></a>TN040: MFC/OLE direkte Größenanpassung und Zoomen

> [!NOTE]
> Der folgende technische Hinweis wurde seit dem ersten Erscheinen in der Onlinedokumentation nicht aktualisiert. Daher können einige Verfahren und Themen veraltet oder falsch sein. Um aktuelle Informationen zu erhalten, wird empfohlen, das gewünschte Thema im Index der Onlinedokumentation zu suchen.

In diesem Hinweis werden die Probleme im Zusammenhang mit der ortsansässigen Bearbeitung und wie ein Server das korrekte Zoomen und die richtige Größenänderung durchführen sollte, erläutert. Mit der Ortsaktivierung geht das WYSIWYG-Konzept einen Schritt weiter, da Container und Server zusammenarbeiten und insbesondere die OLE-Spezifikation in gleicher Weise interpretieren.

Aufgrund der engen Interaktion zwischen einem Container und einem Server, der die direkte Aktivierung unterstützt, gibt es eine Reihe von Erwartungen vom Endbenutzer, die beibehalten werden sollten:

- Die Präsentationsanzeige (die in `COleServerItem::OnDraw` der Außerkraftsetzung gezeichnete Metadatei) sollte genau so aussehen wie beim Zeichnen zur Bearbeitung (mit der Ausnahme, dass Bearbeitungswerkzeuge nicht sichtbar sind).

- Wenn der Container zoomt, sollte auch das Serverfenster!

- Sowohl der Container als auch der Server sollten Objekte zur Bearbeitung mit denselben Metriken anzeigen. Dies bedeutet, dass beim Rendern auf dem Anzeigegerät ein Mapping-Modus verwendet wird, der auf der Anzahl der *logischen* Pixel pro Zoll basiert – nicht auf physischen Pixeln pro Zoll.

> [!NOTE]
> Da die direkte Aktivierung nur für Elemente gilt, die eingebettet (nicht verknüpft) sind, gilt das Zoomen nur für eingebettete Objekte. Sie sehen APIs `COleServerDoc` in `COleServerItem` beiden und die zum Zoomen verwendet werden. Der Grund für diese Dichotomie ist, dass nur Funktionen vorhanden `COleServerItem` sind, die sowohl für verknüpfte als auch für eingebettete Elemente `COleServerDoc` gültig sind (dies ermöglicht eine gemeinsame Implementierung) und Funktionen, die nur für eingebettete Objekte gültig sind, sich in der Klasse befinden (aus Der Sicht des Servers ist es das **Dokument,** das eingebettet ist).

Der größte Teil der Belastung wird dem Serverimplementierer auferlegt, da der Server den Zoomfaktor des Containers kennen und seine Bearbeitungsschnittstelle entsprechend ändern muss. Aber wie bestimmt der Server den Zoomfaktor, den der Container verwendet?

## <a name="mfc-support-for-zooming"></a>MFC-Unterstützung für Zoomen

Der aktuelle Zoomfaktor kann `COleServerDoc::GetZoomFactor`durch Aufrufen von bestimmt werden. Wenn dies aufgerufen wird, wenn das Dokument nicht aktiv ist, führt dies immer zu einem Zoomfaktor von 100 %(oder 1:1-Verhältnis). Wenn Sie es aufrufen, während es aktiv ist, kann etwas anderes als 100 % zurückgegeben werden.

Ein Beispiel für das richtige Zoomen finden Sie im MFC OLE-Beispiel [HIERSVR](../overview/visual-cpp-samples.md). Das Zoomen in HIERSVR wird dadurch erschwert, dass Text angezeigt wird und Text im Allgemeinen nicht linear skaliert wird (Hinweise, typografische Konventionen, Entwurfsbreiten und Höhen erschweren die Angelegenheit). Dennoch ist HIERSVR eine vernünftige Referenz für die korrekte Implementierung des Zoomens, ebenso wie das MFC Tutorial [SCRIBBLE](../overview/visual-cpp-samples.md) (Schritt 7).

`COleServerDoc::GetZoomFactor`bestimmt den Zoomfaktor basierend auf einer Reihe unterschiedlicher Metriken, die `COleServerItem` entweder `COleServerDoc` aus dem Container oder aus der Implementierung von Ihr und Klassen verfügbar sind. Kurz gesagt, der aktuelle Zoomfaktor wird durch die folgende Formel bestimmt:

```
Position Rectangle (PR) / Container Extent (CE)
```

Die POSITION RECTANGLE wird durch den Behälter bestimmt. Sie wird während der ortsseitigen Aktivierung `COleClientItem::OnGetItemPosition` an den Server zurückgegeben, wenn sie `COleServerDoc::OnSetItemRects` aufgerufen wird, `COleClientItem::SetItemRects`und aktualisiert, wenn der Container den Server aufruft (mit einem Aufruf von ).

Die CONTAINER EXTENT ist etwas komplexer zu berechnen. Wenn der Container `COleServerItem::OnSetExtent` aufgerufen hat `COleClientItem::SetExtent`(mit einem Aufruf von ), ist die CONTAINER EXTENT dieser Wert, der basierend auf der Anzahl der Pixel pro logischem Zoll in Pixel konvertiert wird. Wenn der Container SetExtent nicht aufgerufen hat (was normalerweise der Fall `COleServerItem::OnGetExtent`ist), ist die CONTAINER EXTENT die Größe, die von zurückgegeben wird. Wenn der Container also setExtent nicht aufgerufen hat, geht das Framework davon aus, dass der Container ihn mit `COleServerItem::GetExtent`100 % der natürlichen Ausdehnung (dem von zurückgegebenen Wert) aufgerufen hätte. Anders ausgedrückt geht das Framework davon aus, dass der Container 100 % (nicht mehr, nicht weniger) des Elements anzeigt.

Es ist wichtig zu `COleServerItem::OnSetExtent` `COleServerItem::OnGetExtent` beachten, dass, obwohl und haben ähnliche Namen, sie nicht das gleiche Attribut des Elements manipulieren. `OnSetExtent`wird aufgerufen, um den Server darüber zu informieren, wie viel des Objekts im Container sichtbar ist (unabhängig vom Zoomfaktor) und `OnGetExtent` vom Container aufgerufen wird, um die ideale Größe des Objekts zu bestimmen.

Wenn Sie sich die einzelnen APIs ansehen, erhalten Sie ein klareres Bild:

## <a name="coleserveritemongetextent"></a>COleServerItem::OnGetExtent

Diese Funktion sollte die "natürliche Größe" in HIMETRIC-Einheiten des Artikels zurückgeben. Der beste Weg, um die "natürliche Größe" zu denken, ist es als die Größe zu definieren, die es beim Drucken erscheinen könnte. Die hier zurückgegebene Größe ist für einen bestimmten Elementinhalt konstant (ähnlich wie die Metadatei, die für ein bestimmtes Element konstant ist). Diese Größe ändert sich nicht, wenn das Zoomen auf das Element angewendet wird. Es ändert sich in der Regel nicht, wenn `OnSetExtent`der Container dem Element mehr oder weniger Platz durch Aufrufen gibt. Ein Beispiel für eine Änderung könnte das eines einfachen Texteditors ohne "Margin"-Funktion sein, der Text basierend auf der letzten vom Container gesendeten Ausdehnung umschlossen hat. Wenn sich ein Server ändert, sollte der Server wahrscheinlich das OLEMISC_RECOMPOSEONRESIZE Bit in der Systemregistrierung festlegen (weitere Informationen zu dieser Option finden Sie in der OLE SDK-Dokumentation).

## <a name="coleserveritemonsetextent"></a>COleServerItem::OnSetExtent

Diese Funktion wird aufgerufen, wenn der Container "mehr oder weniger" des Objekts anzeigt. Die meisten Container rufen dies überhaupt nicht an. Die Standardimplementierung speichert den letzten vom Container empfangenen Wert `COleServerDoc::GetZoomFactor` in "m_sizeExtent", der bei der Berechnung des oben beschriebenen CONTAINER EXTENT-Werts verwendet wird.

## <a name="coleserverdoconsetitemrects"></a>COleServerDoc::OnSetItemRects

Diese Funktion wird nur aufgerufen, wenn das Dokument aktiv ist. Sie wird aufgerufen, wenn der Container entweder die Position des Elements oder den auf das Element angewendeten Clipping aktualisiert. Das POSITION RECTANGLE stellt, wie oben erläutert, den Zähler für die Zoomfaktorberechnung bereit. Ein Server kann anfordern, dass `COleServerDoc::RequestPositionChange`die Elementposition durch Aufrufen geändert wird. Der Container kann auf diese Anforderung `OnSetItemRects` durch Aufrufen (mit einem Aufruf an `COleServerItem::SetItemRects`) reagieren oder nicht.

## <a name="coleserverdocondraw"></a>COleServerdoc::OnDraw

Es ist wichtig zu erkennen, dass die `COleServerItem::OnDraw` Metadatei, die durch Überschreiben von erstellt wird, genau die gleiche Metadatei erzeugt, unabhängig vom aktuellen Zoomfaktor. Der Container skaliert die Metadatei entsprechend. Dies ist ein wichtiger Unterschied `OnDraw` zwischen der Ansicht `OnDraw`und dem Serverelement . Die Ansicht behandelt das Zoomen, das Element erstellt nur eine *zoombare* Metadatei und überlässt es dem Container, um das entsprechende Zoomen zu erledigen.

Die beste Möglichkeit, sicherzustellen, dass sich Ihr Server korrekt `COleServerDoc::GetZoomFactor` verhält, besteht darin, die Implementierung von zu verwenden, wenn das Dokument aktiv ist.

## <a name="mfc-support-for-in-place-resizing"></a>MFC-Unterstützung für in-Place-Größenänderung

MFC implementiert die in der OLE 2-Spezifikation beschriebene anortende Größenänderungsschnittstelle vollständig. Die Benutzeroberfläche wird von `COleResizeBar` der Klasse, einer benutzerdefinierten Meldung WM_SIZECHILD `COleIPFrameWnd`und einer speziellen Behandlung dieser Nachricht in unterstützt.

Möglicherweise möchten Sie eine andere Behandlung dieser Nachricht implementieren als die vom Framework bereitgestellte. Wie oben beschrieben, lässt das Framework die Ergebnisse der direkten Größenänderung bis zum Container – der Server reagiert auf die Änderung des Zoomfaktors. Wenn der Container reagiert, indem er sowohl CONTAINER EXTENT `COleClientItem::OnChangeItemPosition` als auch POSITION RECTANGLE während `COleServerDoc::RequestPositionChange`der Verarbeitung seiner (als Ergebnis eines Aufrufs von ) gesetzt, dann führt die an Ort und Stelle Größenänderung dazu, dass "mehr oder weniger" des Elements im Bearbeitungsfenster angezeigt wird. Wenn der Container reagiert, indem er nur `COleClientItem::OnChangeItemPosition`die POSITION RECTANGLE während der Verarbeitung von einstellt, ändert sich der Zoomfaktor und das Element wird "ein- oder ausgezoomt" angezeigt.

Ein Server kann (bis zu einem gewissen Grad) steuern, was während dieser Aushandlung geschieht. Eine Kalkulationstabelle kann z. B. mehr oder weniger Zellen anzeigen, wenn der Benutzer die Größe des Fensters ändert, während das Element an Ort und Stelle bearbeitet wird. Ein Textverarbeitungsprogramm kann die "Seitenränder" so ändern, dass sie mit dem Fenster identisch sind, und den Text an den neuen Rand umschließen. Server implementieren dies, indem sie die `COleServerItem::OnGetExtent`natürliche Ausdehnung (die Größe, die von zurückgegeben wird ) ändern, wenn die Größenänderung abgeschlossen ist. Dadurch ändern sich sowohl das POSITION-RECHTECK als auch die CONTAINER-EXTENT um den gleichen Betrag, was zu demselben Zoomfaktor, aber zu einem größeren oder kleineren Anzeigebereich führt. Darüber hinaus wird mehr oder weniger des Dokuments in `OnDraw`der Metadatei angezeigt, die von generiert wird. In diesem Fall ändert sich das Dokument selbst, wenn der Benutzer die Größe des Elements ändert, anstatt nur den Anzeigebereich.

Sie können die benutzerdefinierte Größenänderung implementieren und `COleResizeBar` dennoch die Benutzeroberfläche `COleIPFrameWnd` nutzen, indem Sie die WM_SIZECHILD Nachricht in Ihrer Klasse überschreiben. Weitere Informationen zu den Besonderheiten von WM_SIZECHILD finden Sie unter [Technischer Hinweis 24](../mfc/tn024-mfc-defined-messages-and-resources.md).

## <a name="see-also"></a>Siehe auch

[Technische Hinweise – nach Nummern geordnet](../mfc/technical-notes-by-number.md)<br/>
[Technische Hinweise – nach Kategorien geordnet](../mfc/technical-notes-by-category.md)

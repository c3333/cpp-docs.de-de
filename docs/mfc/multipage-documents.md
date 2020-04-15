---
title: Mehrseitige Dokumente
ms.date: 11/19/2018
helpviewer_keywords:
- pagination [MFC]
- overriding [MFC], View class functions for printing
- OnPrepareDC method [MFC]
- CPrintInfo structure [MFC], multipage documents
- OnEndPrinting method [MFC]
- protocols [MFC], printing protocol
- document pages vs. printer pages [MFC]
- printer mode [MFC]
- printing [MFC], multipage documents
- printers [MFC], printer mode
- documents [MFC], printing
- OnPreparePrinting method [MFC]
- OnPrint method [MFC]
- DoPreparePrinting method and pagination [MFC]
- OnDraw method [MFC], printing
- pagination [MFC], printing multipage documents
- printing [MFC], protocol
- pages [MFC], printing
- OnBeginPrinting method [MFC]
- multipage documents [MFC]
- printing [MFC], pagination
- documents [MFC], paginating
ms.assetid: 69626b86-73ac-4b74-b126-9955034835ef
ms.openlocfilehash: 87912c06a40740d25530235ee421c6c8bfa11aab
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370736"
---
# <a name="multipage-documents"></a>Mehrseitige Dokumente

In diesem Artikel wird das Windows-Druckprotokoll beschrieben und erläutert, wie Dokumente gedruckt werden, die mehr als eine Seite enthalten. Der Artikel behandelt die folgenden Themen:

- [Druckprotokoll](#_core_the_printing_protocol)

- [Überschreiben von Ansichtsklassenfunktionen](#_core_overriding_view_class_functions)

- [Paginierung](#_core_pagination)

- [Druckerseiten im Vergleich zu Dokumentseiten](#_core_printer_pages_vs.._document_pages)

- [Print-Time-Paginierung](#_core_print.2d.time_pagination)

## <a name="the-printing-protocol"></a><a name="_core_the_printing_protocol"></a>Das Druckprotokoll

Um ein mehrseitiges Dokument zu drucken, interagieren das Framework und die Ansicht auf folgende Weise. Zuerst zeigt das Framework das Dialogfeld **Drucken** an, erstellt einen Gerätekontext für den Drucker und ruft die [StartDoc-Memberfunktion](../mfc/reference/cdc-class.md#startdoc) des [CDC-Objekts](../mfc/reference/cdc-class.md) auf. Anschließend ruft das Framework für jede Seite des Dokuments `CDC` die [StartPage-Memberfunktion](../mfc/reference/cdc-class.md#startpage) des Objekts auf, weist das Ansichtsobjekt an, die Seite zu drucken, und ruft die [EndPage-Memberfunktion](../mfc/reference/cdc-class.md#endpage) auf. Wenn der Druckermodus vor dem Starten einer bestimmten Seite geändert werden muss, ruft die Ansicht [ResetDC](../mfc/reference/cdc-class.md#resetdc)auf, wodurch die [DEVMODE-Struktur](/windows/win32/api/wingdi/ns-wingdi-devmodea) aktualisiert wird, die die neuen Druckermodusinformationen enthält. Wenn das gesamte Dokument gedruckt wurde, ruft das Framework die [EndDoc-Memberfunktion](../mfc/reference/cdc-class.md#enddoc) auf.

## <a name="overriding-view-class-functions"></a><a name="_core_overriding_view_class_functions"></a>Überschreiben von Ansichtsklassenfunktionen

Die [CView-Klasse](../mfc/reference/cview-class.md) definiert mehrere Memberfunktionen, die vom Framework während des Druckvorgangs aufgerufen werden. Durch Das Überschreiben dieser Funktionen in Ihrer Ansichtsklasse stellen Sie die Verbindungen zwischen der Drucklogik des Frameworks und der Drucklogik der Ansichtsklasse bereit. In der folgenden Tabelle sind diese Memberfunktionen aufgeführt.

### <a name="cviews-overridable-functions-for-printing"></a>Die überschreibbaren Funktionen von CView für den Druck

|Name|Grund für die Überbelegung|
|----------|---------------------------|
|[OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)|So fügen Sie Werte in das Dialogfeld Drucken ein, insbesondere die Länge des Dokuments|
|[OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting)|So weisen Sie Schriftarten oder andere GDI-Ressourcen zu|
|[OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc)|So passen Sie Attribute des Gerätekontexts für eine bestimmte Seite an oder führen Druckzeitpaginierung durch|
|[OnPrint](../mfc/reference/cview-class.md#onprint)|So drucken Sie eine bestimmte Seite|
|[OnEndPrinting](../mfc/reference/cview-class.md#onendprinting)|So deallocateen Sie GDI-Ressourcen|

Sie können auch in anderen Funktionen druckbezogene Verarbeitungen übernehmen, aber diese Funktionen sind es, die den Druckprozess antreiben.

Die folgende Abbildung veranschaulicht die Schritte im Druckprozess `CView`und zeigt, wo die einzelnen Druckelementfunktionen aufgerufen werden. Im weiteren Verlauf dieses Artikels werden die meisten dieser Schritte ausführlicher erläutert. Weitere Teile des Druckprozesses werden im Artikel [Allocating GDI Resources](../mfc/allocating-gdi-resources.md)beschrieben.

![Druckschleifenprozess](../mfc/media/vc37c71.gif "Druckschleifenprozess") <br/>
Druckschleife

## <a name="pagination"></a><a name="_core_pagination"></a>Paginierung

Das Framework speichert einen Großteil der Informationen über einen Druckauftrag in einer [CPrintInfo-Struktur.](../mfc/reference/cprintinfo-structure.md) Mehrere der Werte `CPrintInfo` in beziehen sich auf pagination; Auf diese Werte kann zugegriffen werden, wie in der folgenden Tabelle dargestellt.

### <a name="page-number-information-stored-in-cprintinfo"></a>In CPrintInfo gespeicherte Seitennummerninformationen

|Membervariable oder<br /><br /> Funktionsname(e)|Seitenzahl referenziert|
|-----------------------------------------------|----------------------------|
|`GetMinPage`/`SetMinPage`|Erste Seite des Dokuments|
|`GetMaxPage`/`SetMaxPage`|Letzte Seite des Dokuments|
|`GetFromPage`|Erste Seite, die gedruckt werden soll|
|`GetToPage`|Letzte zu druckende Seite|
|`m_nCurPage`|Seite, die gerade gedruckt wird|

Seitenzahlen beginnen bei 1, d. h., die erste Seite ist mit 1 nummeriert, nicht mit 0. Weitere Informationen zu diesen und anderen Mitgliedern von [CPrintInfo](../mfc/reference/cprintinfo-structure.md)finden Sie unter *MFC-Referenz*.

Zu Beginn des Druckvorgangs ruft das Framework die [OnPreparePrinting-Memberfunktion](../mfc/reference/cview-class.md#onprepareprinting) der `CPrintInfo` Ansicht auf und übergibt einen Zeiger an eine Struktur. Der Anwendungs-Assistent stellt `OnPreparePrinting` eine Implementierung des Aufrufts `CView` [DoPreparePrinting](../mfc/reference/cview-class.md#doprepareprinting), einer weiteren Memberfunktion von bereit. `DoPreparePrinting`ist die Funktion, die das Dialogfeld Drucken anzeigt und einen Druckergerätekontext erstellt.

Zu diesem Zeitpunkt weiß die Anwendung nicht, wie viele Seiten sich im Dokument befinden. Es verwendet die Standardwerte 1 und 0xFFFF für die Zahlen der ersten und letzten Seite des Dokuments. Wenn Sie wissen, wie viele Seiten `OnPreparePrinting` Ihr Dokument hat, überschreiben und rufen Sie [SetMaxPage]--brokenlink--(reference/cprintinfo-class.md-setmaxpage) für die `CPrintInfo` Struktur auf, bevor Sie es an `DoPreparePrinting`senden. Auf diese Weise können Sie die Länge des Dokuments angeben.

`DoPreparePrinting`zeigt dann das Dialogfeld Drucken an. Wenn sie zurückgegeben `CPrintInfo` wird, enthält die Struktur die vom Benutzer angegebenen Werte. Wenn der Benutzer nur einen ausgewählten Seitenbereich drucken möchte, kann er die Start- und Endseitenzahlen im Dialogfeld Drucken angeben. Das Framework ruft diese `GetFromPage` Werte `GetToPage` mithilfe der und Funktionen von [CPrintInfo](../mfc/reference/cprintinfo-structure.md)ab. Wenn der Benutzer keinen Seitenbereich angibt, `GetMinPage` `GetMaxPage` ruft das Framework die zurückgegebenen Werte auf, um das gesamte Dokument zu drucken.

Für jede Seite eines dokuments, das gedruckt werden soll, ruft das Framework zwei Memberfunktionen in Ihrer Ansichtsklasse auf, [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc) und `CPrintInfo` [OnPrint](../mfc/reference/cview-class.md#onprint), und übergibt jede Funktion zwei Parameter: einen Zeiger auf ein [CDC-Objekt](../mfc/reference/cdc-class.md) und einen Zeiger auf eine Struktur. Jedes Mal, `OnPrepareDC` wenn `OnPrint`das Framework aufruft und , `CPrintInfo` gibt es einen anderen Wert im *m_nCurPage* Member der Struktur. Auf diese Weise teilt das Framework der Ansicht mit, welche Seite gedruckt werden soll.

Die [OnPrepareDC-Memberfunktion](../mfc/reference/cview-class.md#onpreparedc) wird auch für die Bildschirmanzeige verwendet. Es nimmt Anpassungen am Gerätekontext vor, bevor das Zeichnen stattfindet. `OnPrepareDC`spielt eine ähnliche Rolle beim Drucken, aber es gibt `CDC` einige Unterschiede: Erstens stellt das Objekt einen Druckergerätekontext anstelle eines Bildschirmgerätekontexts dar, und zweitens wird ein `CPrintInfo` Objekt als zweiter Parameter übergeben. (Dieser Parameter ist `OnPrepareDC` **NULL,** wenn die Bildschirmanzeige aufgerufen wird.) Überschreiben, `OnPrepareDC` um Anpassungen am Gerätekontext basierend auf der Seite vorzunehmen, die gedruckt wird. Sie können z. B. den Herkunftsursprung des Ansichtsfensters und den Zuschneidebereich verschieben, um sicherzustellen, dass der entsprechende Teil des Dokuments gedruckt wird.

Die [OnPrint-Memberfunktion](../mfc/reference/cview-class.md#onprint) führt den tatsächlichen Druck der Seite durch. Der Artikel [Wie Standarddruck ausgeführt wird,](../mfc/how-default-printing-is-done.md) wird gezeigt, wie das Framework [OnDraw](../mfc/reference/cview-class.md#ondraw) mit einem Druckergerätekontext aufruft, um den Druckvorgang durchzuführen. Genauer `OnPrint` gesagt ruft das `CPrintInfo` Framework eine Struktur und `OnPrint` einen Gerätekontext `OnDraw`auf und übergibt den Gerätekontext an . Überschreiben `OnPrint` Sie, um Rendering sendemittelzuführen, das nur während des Druckvorgangs und nicht für die Bildschirmanzeige ausgeführt werden soll. Zum Drucken von Kopf- oder Fußzeilen (weitere Informationen finden Sie im Artikel [Kopf- und Fußzeilen).](../mfc/headers-and-footers.md) Rufen `OnDraw` Sie dann von `OnPrint` der Außerkraftsetzung von auf, um das Rendering zu erledigen, das sowohl für die Bildschirmanzeige als auch für den Druck gemeinsam ist.

Die Tatsache, dass `OnDraw` das Rendering sowohl für die Bildschirmanzeige als auch für den Druck erfolgt, bedeutet, dass Ihre Anwendung WYSIWYG ist: "Was Sie sehen, ist, was Sie bekommen." Angenommen, Sie schreiben keine WYSIWYG-Anwendung. Betrachten Sie beispielsweise einen Texteditor, der eine fett formatierte Schriftart zum Drucken verwendet, aber Steuercodes anzeigt, um fett formatierten Text auf dem Bildschirm anzuzeigen. In einer solchen Situation `OnDraw` verwenden Sie ausschließlich für die Bildschirmanzeige. Wenn Sie `OnPrint`überschreiben, ersetzen `OnDraw` Sie den Aufruf an durch einen Aufruf einer separaten Zeichnungsfunktion. Diese Funktion zeichnet das Dokument so, wie es auf Papier angezeigt wird, mit den Attributen, die Sie nicht auf dem Bildschirm anzeigen.

## <a name="printer-pages-vs-document-pages"></a><a name="_core_printer_pages_vs.._document_pages"></a>Druckerseiten im Vergleich zu Dokumentseiten

Wenn Sie sich auf Seitenzahlen beziehen, ist es manchmal notwendig, zwischen dem Konzept einer Seite durch den Drucker und dem Konzept einer Seite durch ein Dokument zu unterscheiden. Aus Der Sicht des Druckers ist eine Seite ein Blatt Papier. Ein Blatt Papier entspricht jedoch nicht unbedingt einer Seite des Dokuments. Wenn Sie z. B. einen Newsletter drucken, in dem die Blätter gefaltet werden sollen, kann ein Blatt Papier sowohl die erste als auch die letzte Seite des Dokuments nebeneinander enthalten. Wenn Sie eine Kalkulationstabelle drucken, besteht das Dokument ebenfalls überhaupt nicht aus Seiten. Stattdessen kann ein Blatt Papier die Zeilen 1 bis 20, die Spalten 6 bis 10 enthalten.

Alle Seitenzahlen in der [CPrintInfo-Struktur](../mfc/reference/cprintinfo-structure.md) beziehen sich auf Druckerseiten. Das Framework `OnPrepareDC` `OnPrint` ruft und einmal für jedes Blatt Papier, das durch den Drucker geht. Wenn Sie die [OnPreparePrinting-Funktion](../mfc/reference/cview-class.md#onprepareprinting) überschreiben, um die Länge des Dokuments anzugeben, müssen Sie Druckerseiten verwenden. Wenn es eine 1:1-Entsprechung gibt (d. h., eine Druckerseite entspricht einer Dokumentseite), ist dies einfach. Wenn hingegen Dokument- und Druckerseiten nicht direkt übereinstimmen, müssen Sie zwischen ihnen übersetzen. Erwägen Sie beispielsweise, eine Kalkulationstabelle zu drucken. Beim Überschreiben `OnPreparePrinting`müssen Sie berechnen, wie viele Blatt Papier zum Drucken der gesamten `SetMaxPage` Kalkulationstabelle `CPrintInfo`erforderlich sind, und diesen Wert dann beim Aufrufen der Memberfunktion von verwenden. Ebenso müssen Sie `OnPrepareDC`beim Überschreiben *m_nCurPage* in den Bereich der Zeilen und Spalten übersetzen, die auf diesem bestimmten Blatt angezeigt werden, und dann den Ursprung des Ansichtsfensters entsprechend anpassen.

## <a name="print-time-pagination"></a><a name="_core_print.2d.time_pagination"></a>Print-Time Pagination

In einigen Situationen weiß die Ansichtsklasse möglicherweise nicht im Voraus, wie lange das Dokument dauert, bis es tatsächlich gedruckt wurde. Angenommen, Ihre Anwendung ist nicht WYSIWYG, sodass die Länge eines Dokuments auf dem Bildschirm beim Drucken nicht der Länge entspricht.

Dies verursacht ein Problem, wenn Sie [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) für Ihre Ansichtsklasse `SetMaxPage` überschreiben: Sie können keinen Wert an die Funktion der [CPrintInfo-Struktur](../mfc/reference/cprintinfo-structure.md) übergeben, da Sie die Länge eines Dokuments nicht kennen. Wenn der Benutzer keine Seitenzahl angibt, die mit der Verwendung des Dialogfelds Drucken beendet werden soll, weiß das Framework nicht, wann die Druckschleife beendet werden soll. Die einzige Möglichkeit, zu bestimmen, wann die Druckschleife beendet werden soll, besteht darin, das Dokument auszudrucken und zu sehen, wann es endet. Die Ansichtsklasse muss beim Drucken nach dem Ende des Dokuments suchen und dann das Framework informieren, wenn das Ende erreicht ist.

Das Framework basiert auf der [OnPrepareDC-Funktion](../mfc/reference/cview-class.md#onpreparedc) Ihrer Ansichtsklasse, um ihr mitzuteilen, wann beendet werden soll. Nach jedem `OnPrepareDC`Aufruf von überprüft das `CPrintInfo` Framework ein Element der Struktur *namens m_bContinuePrinting*. Der Standardwert ist **TRUE.** Solange dies so bleibt, setzt das Framework die Druckschleife fort. Wenn es auf **FALSE**gesetzt ist, wird das Framework beendet. Um die Druckzeitpaginierung durchzuführen, überschreiben `OnPrepareDC` Sie, um zu überprüfen, ob das Ende des Dokuments erreicht wurde, und legen Sie *m_bContinuePrinting* auf **FALSE** fest.

Die Standardimplementierung `OnPrepareDC` von Sätzen *m_bContinuePrinting* auf **FALSE,** wenn die aktuelle Seite größer als 1 ist. Dies bedeutet, dass, wenn die Länge des Dokuments nicht angegeben wurde, das Framework davon ausgeht, dass das Dokument eine Seite lang ist. Eine Folge davon ist, dass Sie vorsichtig sein müssen, wenn Sie die Basisklassenversion von `OnPrepareDC`aufrufen. Gehen Sie nicht davon aus, dass *m_bContinuePrinting* **true** ist, nachdem sie die Basisklassenversion aufgerufen haben.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- [Kopf- und Fußzeilen](../mfc/headers-and-footers.md)

- [Zuweisen von GDI-Ressourcen](../mfc/allocating-gdi-resources.md)

## <a name="see-also"></a>Siehe auch

[Drucken](../mfc/printing.md)<br/>
[CView-Klasse](../mfc/reference/cview-class.md)<br/>
[CDC-Klasse](../mfc/reference/cdc-class.md)

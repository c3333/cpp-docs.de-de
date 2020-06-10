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
ms.openlocfilehash: c73692c315b07d6b690180886d494ee12f85f52d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621057"
---
# <a name="multipage-documents"></a>Mehrseitige Dokumente

In diesem Artikel wird das Windows-Druck Protokoll beschrieben und erläutert, wie Dokumente gedruckt werden, die mehr als eine Seite enthalten. In diesem Artikel werden die folgenden Themen behandelt:

- [Druck Protokoll](#_core_the_printing_protocol)

- [Überschreiben von Ansichts Klassen Funktionen](#_core_overriding_view_class_functions)

- [Paginierung](#_core_pagination)

- [Drucker Seiten im Vergleich zu Dokument Seiten](#_core_printer_pages_vs.._document_pages)

- [Druck Zeit Paginierung](#_core_print.2d.time_pagination)

## <a name="the-printing-protocol"></a><a name="_core_the_printing_protocol"></a>Das Druck Protokoll

Zum Drucken eines mehrseitigen Dokuments interagieren das Framework und die Ansicht wie folgt. Zuerst zeigt das Framework das Dialogfeld **Drucken** an, erstellt einen Gerätekontext für den Drucker und ruft die [StartDoc](reference/cdc-class.md#startdoc) -Member-Funktion des [CDC](reference/cdc-class.md) -Objekts auf. Dann ruft das Framework für jede Seite des Dokuments die [Startpage](reference/cdc-class.md#startpage) -Member-Funktion des- `CDC` Objekts auf, weist das Ansichts Objekt an, die Seite zu drucken, und ruft die [EndPage](reference/cdc-class.md#endpage) -Member-Funktion auf. Wenn der Drucker Modus vor dem Starten einer bestimmten Seite geändert werden muss, ruft die Ansicht [ResetDC](reference/cdc-class.md#resetdc)auf, wodurch die [DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea) -Struktur aktualisiert wird, die die neuen druckermodusinformationen enthält. Wenn das gesamte Dokument gedruckt wurde, ruft das Framework die [EndDoc](reference/cdc-class.md#enddoc) -Member-Funktion auf.

## <a name="overriding-view-class-functions"></a><a name="_core_overriding_view_class_functions"></a>Überschreiben von Ansichts Klassen Funktionen

Die [CView](reference/cview-class.md) -Klasse definiert mehrere Element Funktionen, die während des Druckens vom Framework aufgerufen werden. Wenn Sie diese Funktionen in der Ansichts Klasse überschreiben, stellen Sie die Verbindungen zwischen der Druck Logik des Frameworks und der Druck Logik der Ansichts Klasse bereit. In der folgenden Tabelle sind diese Element Funktionen aufgeführt.

### <a name="cviews-overridable-functions-for-printing"></a>Über schreibbare Funktionen von CView zum Drucken

|name|Grund für das Überschreiben|
|----------|---------------------------|
|[OnPreparePrinting](reference/cview-class.md#onprepareprinting)|So fügen Sie Werte im Dialogfeld "Drucken" ein, insbesondere die Länge des Dokuments|
|[OnBeginPrinting](reference/cview-class.md#onbeginprinting)|So weisen Sie Schriftarten oder andere GDI-Ressourcen zu|
|[OnPrepareDC](reference/cview-class.md#onpreparedc)|So passen Sie die Attribute des Geräte Kontexts für eine bestimmte Seite an oder für die Druck Zeit Paginierung|
|[OnPrint](reference/cview-class.md#onprint)|So drucken Sie eine bestimmte Seite|
|[OnEndPrinting](reference/cview-class.md#onendprinting)|So teilen Sie GDI-Ressourcen auf|

Sie können auch druckbezogene Verarbeitung in anderen Funktionen durchführen, aber diese Funktionen sind die, die den Druckvorgang steuern.

In der folgenden Abbildung werden die Schritte erläutert, die beim Druckprozess ausgeführt werden, und es wird gezeigt, wo die Druckelement Funktionen der einzelnen `CView` Funktionen aufgerufen werden. Im restlichen Teil dieses Artikels werden die meisten dieser Schritte ausführlicher erläutert. Weitere Teile des Druckvorgangs werden im Artikel [Zuordnen von GDI-Ressourcen](allocating-gdi-resources.md)beschrieben.

![Druckschleifenprozess](../mfc/media/vc37c71.gif "Druckschleifenprozess") <br/>
Druckschleife

## <a name="pagination"></a><a name="_core_pagination"></a>Paginierung

Das Framework speichert einen Großteil der Informationen zu einem Druckauftrag in einer [CPrintInfo](reference/cprintinfo-structure.md) -Struktur. Einige der Werte in `CPrintInfo` beziehen sich auf die Paginierung. diese Werte sind wie in der folgenden Tabelle dargestellt zugänglich.

### <a name="page-number-information-stored-in-cprintinfo"></a>In CPrintInfo gespeicherte Informationen zur Seitenzahl

|Member-Variable oder<br /><br /> Funktionsname (n)|Seitenzahl referenziert|
|-----------------------------------------------|----------------------------|
|`GetMinPage`/`SetMinPage`|Erste Seite des Dokuments|
|`GetMaxPage`/`SetMaxPage`|Letzte Seite des Dokuments|
|`GetFromPage`|Erste zu druckende Seite|
|`GetToPage`|Letzte zu druckende Seite|
|`m_nCurPage`|Die aktuell gedruckte Seite|

Seitenzahlen beginnen bei 1, d. h. die erste Seite ist 1, nicht 0. Weitere Informationen zu diesen und anderen Membern von [CPrintInfo](reference/cprintinfo-structure.md)finden Sie in der *MFC-Referenz*.

Zu Beginn des Druckvorgangs Ruft das Framework die [OnPreparePrinting](reference/cview-class.md#onprepareprinting) -Member-Funktion der Sicht auf und übergibt einen Zeiger auf eine- `CPrintInfo` Struktur. Der Anwendungs-Assistent stellt eine Implementierung von bereit, `OnPreparePrinting` die " [DoPreparePrinting](reference/cview-class.md#doprepareprinting)", eine andere Member-Funktion von, aufruft `CView` . `DoPreparePrinting`die Funktion, die das Dialogfeld Drucken anzeigt und einen Drucker Gerätekontext erstellt.

An diesem Punkt weiß die Anwendung nicht, wie viele Seiten im Dokument enthalten sind. Dabei werden die Standardwerte 1 und 0xFFFF für die Zahlen der ersten und letzten Seite des Dokuments verwendet. Wenn Sie wissen, wie viele Seiten das Dokument enthält, überschreiben Sie, `OnPreparePrinting` und nennen Sie [SetMaxPage]--brokenlink--(Reference/CPrintInfo-Class. MD # SetMaxPage) für die `CPrintInfo` Struktur, bevor Sie Sie an senden `DoPreparePrinting` . Auf diese Weise können Sie die Länge des Dokuments angeben.

`DoPreparePrinting`zeigt das Dialogfeld Drucken an. Wenn die-Struktur zurückgegeben wird, `CPrintInfo` enthält Sie die vom Benutzer festgelegten Werte. Wenn der Benutzer nur einen ausgewählten Seitenbereich drucken möchte, kann er die Start-und Endseiten Nummern im Dialogfeld Drucken angeben. Das Framework ruft diese Werte mithilfe der `GetFromPage` - `GetToPage` Funktion und der-Funktion von [CPrintInfo](reference/cprintinfo-structure.md)ab. Wenn der Benutzer keinen Seitenbereich angibt, ruft das Framework `GetMinPage` und `GetMaxPage` auf und verwendet die zurückgegebenen Werte, um das gesamte Dokument zu drucken.

Für jede Seite eines Dokuments, das gedruckt werden soll, ruft das Framework zwei Member-Funktionen in ihrer Ansichts Klasse, [OnPrepareDC](reference/cview-class.md#onpreparedc) und [OnPrint](reference/cview-class.md#onprint), auf und übergibt jede Funktion mit zwei Parametern: einem Zeiger auf ein [CDC](reference/cdc-class.md) -Objekt und einem Zeiger auf eine- `CPrintInfo` Struktur. Jedes Mal, wenn das Framework `OnPrepareDC` und aufruft `OnPrint` , übergibt es einen anderen Wert in der *m_nCurPage* -Member der- `CPrintInfo` Struktur. Auf diese Weise teilt das Framework der Ansicht mit, welche Seite gedruckt werden soll.

Die [OnPrepareDC](reference/cview-class.md#onpreparedc) -Member-Funktion wird auch für die Bildschirm Anzeige verwendet. Vor dem Zeichnen erfolgt eine Anpassung des Geräte Kontexts. `OnPrepareDC`bietet eine ähnliche Rolle beim Drucken. es gibt jedoch einige Unterschiede: Erstens stellt das- `CDC` Objekt einen Drucker Gerätekontext anstelle eines Bildschirm-Geräte Kontexts dar, und zweitens wird ein- `CPrintInfo` Objekt als zweiter Parameter übergeben. (Dieser Parameter ist **null** , wenn `OnPrepareDC` für die Bildschirm Anzeige aufgerufen wird.) Überschreiben `OnPrepareDC` Sie, um den Gerätekontext basierend auf der zu Druck Ende Seite anzupassen. Beispielsweise können Sie den Viewportursprung und den Clippingbereich verschieben, um sicherzustellen, dass der entsprechende Teil des Dokuments gedruckt wird.

Die Member-Funktion von [OnPrint](reference/cview-class.md#onprint) führt den eigentlichen Druck der Seite aus. Der Artikel [Funktionsweise des Standard Drucks](how-default-printing-is-done.md) zeigt, wie das Framework [OnDraw](reference/cview-class.md#ondraw) mit einem Drucker Gerätekontext aufruft, um den Druck auszuführen. Genauer ist, ruft das Framework `OnPrint` mit einer `CPrintInfo` Struktur und einem Gerätekontext auf und `OnPrint` übergibt den Gerätekontext an `OnDraw` . `OnPrint`Überschreiben Sie, um ein Rendering auszuführen, das nur während des Druckens und nicht für die Bildschirm Anzeige ausgeführt werden soll. Beispielsweise zum Drucken von Kopf-oder Fußzeilen (Weitere Informationen finden Sie in den Artikeln [Kopf-und Fußzeilen](headers-and-footers.md) ). Anschließend wird `OnDraw` von der-Überschreibung von aufgerufen `OnPrint` , um das gemeinsame Rendering für die Bildschirm Anzeige und den Druckvorgang durchzuführen

Die Tatsache, dass `OnDraw` das Rendering sowohl für Bildschirm Anzeige als auch für Drucken durchführt, bedeutet, dass es sich bei der Anwendung um WYSIWYG handelt: "was Sie sehen." Nehmen Sie jedoch an, Sie schreiben keine WYSIWYG-Anwendung. Nehmen Sie beispielsweise einen Text-Editor, der eine Fett formatierte Schriftart zum Drucken verwendet, aber Steuercodes anzeigt, um fett formatierten Text auf dem Bildschirm anzuzeigen. In einer solchen Situation verwenden Sie `OnDraw` ausschließlich die Bildschirm Anzeige. Wenn Sie überschreiben `OnPrint` , ersetzen Sie den-Befehl durch einen-Befehl durch einen-Befehl `OnDraw` für eine separate Zeichnungs Funktion. Diese Funktion zeichnet das Dokument mit den Attributen, die nicht auf dem Bildschirm angezeigt werden, auf die Art und Weise, wie Sie auf dem Blatt angezeigt wird.

## <a name="printer-pages-vs-document-pages"></a><a name="_core_printer_pages_vs.._document_pages"></a>Drucker Seiten im Vergleich zu Dokument Seiten

Wenn Sie auf Seitenzahlen verweisen, ist es manchmal erforderlich, das Konzept einer Seite und das Konzept einer Seite eines Dokuments zu unterscheiden. Aus der Sicht des Druckers ist eine Seite ein Papierblatt. Ein Papierblatt ist jedoch nicht notwendigerweise gleich einer Seite des Dokuments. Wenn Sie z. b. einen Newsletter drucken, in dem die Blätter gefaltet werden sollen, kann ein Papierblatt nebeneinander sowohl die erste als auch die letzte Seite des Dokuments enthalten. Wenn Sie eine Kalkulations Tabelle drucken, besteht das Dokument auch nicht aus Seiten. Stattdessen kann ein Papierblatt die Zeilen 1 bis 20, Spalten 6 bis 10 enthalten.

Alle Seitenzahlen in der [CPrintInfo](reference/cprintinfo-structure.md) -Struktur verweisen auf Drucker Seiten. Das Framework ruft `OnPrepareDC` und `OnPrint` einmal für jedes Papierblatt auf, das den Drucker übergibt. Wenn Sie die [OnPreparePrinting](reference/cview-class.md#onprepareprinting) -Funktion überschreiben, um die Länge des Dokuments anzugeben, müssen Sie Drucker Seiten verwenden. Wenn eine eins-zu-eins-Entsprechung vorliegt (d. h. eine Drucker Seite entspricht einer Dokument Seite), dann ist dies ganz einfach. Wenn auf der anderen Seite Dokument Seiten und Drucker Seiten nicht direkt übereinstimmen, müssen Sie zwischen Ihnen übersetzen. Sie sollten z. b. eine Tabelle drucken. Wenn Sie überschreiben `OnPreparePrinting` , müssen Sie berechnen, wie viele Papierblätter erforderlich sind, um die gesamte Kalkulations Tabelle auszugeben, und dann diesen Wert verwenden, wenn Sie die `SetMaxPage` Member-Funktion von Aufrufen `CPrintInfo` . Ebenso `OnPrepareDC` müssen Sie beim Überschreiben *m_nCurPage* in den Bereich der Zeilen und Spalten übersetzen, die auf dem jeweiligen Blatt angezeigt werden, und dann den Viewportursprung entsprechend anpassen.

## <a name="print-time-pagination"></a><a name="_core_print.2d.time_pagination"></a>Druck Zeit Paginierung

In einigen Fällen weiß Ihre Ansichts Klasse möglicherweise nicht im voraus, wie lange das Dokument ist, bis es tatsächlich gedruckt wurde. Nehmen Sie beispielsweise an, dass Ihre Anwendung nicht WYSIWYG ist, sodass die Länge eines Dokuments auf dem Bildschirm nicht der Länge entspricht, wenn Sie gedruckt werden.

Dies verursacht ein Problem, wenn Sie [OnPreparePrinting](reference/cview-class.md#onprepareprinting) für Ihre Ansichts Klasse überschreiben: Sie können keinen Wert an die `SetMaxPage` Funktion der [CPrintInfo](reference/cprintinfo-structure.md) -Struktur übergeben, da Sie die Länge eines Dokuments nicht kennen. Wenn der Benutzer im Dialogfeld Drucken keine Seitenzahl angibt, die angehalten werden soll, weiß das Framework nicht, wann die Druck Schleife beendet werden soll. Die einzige Möglichkeit, zu bestimmen, wann die Druck Schleife beendet werden soll, besteht darin, das Dokument auszugeben und zu sehen, wann es endet. Ihre Ansichts Klasse muss das Ende des Dokuments während des Druckens überprüfen und dann das Framework informieren, wenn das Ende erreicht ist.

Das Framework basiert auf der [OnPrepareDC](reference/cview-class.md#onpreparedc) -Funktion Ihrer Ansichts Klasse, um Sie darüber zu informieren, wann Sie beendet werden soll. Nach jedem Aufruf `OnPrepareDC` von prüft das Framework einen Member der Struktur mit dem `CPrintInfo` Namen *m_bContinuePrinting*. Der Standardwert ist " **true".** Solange dies nicht der Fall ist, setzt das Framework die Druck Schleife fort. Wenn der Wert auf **false**festgelegt ist, wird das Framework angehalten. Überschreiben Sie zum Durchführen der Druck Zeit Paginierung, `OnPrepareDC` um zu überprüfen, ob das Ende des Dokuments erreicht wurde, und legen Sie *m_bContinuePrinting* auf **false** fest.

Die Standard Implementierung von `OnPrepareDC` legt *m_bContinuePrinting* auf **false** fest, wenn die aktuelle Seite größer als 1 ist. Dies bedeutet Folgendes: Wenn die Länge des Dokuments nicht angegeben wurde, geht das Framework davon aus, dass das Dokument eine Seite lang ist. Eine Folge davon ist, dass Sie vorsichtig sein müssen, wenn Sie die Basisklassen Version von aufzurufen `OnPrepareDC` . Gehen Sie nicht davon aus, dass *m_bContinuePrinting* nach dem Aufruf der Basisklassen Version " **true** " ist.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Kopf-und Fußzeilen](headers-and-footers.md)

- [Zuordnen von GDI-Ressourcen](allocating-gdi-resources.md)

## <a name="see-also"></a>Siehe auch

[Drucken](printing.md)<br/>
[CView-Klasse](reference/cview-class.md)<br/>
[CDC-Klasse](reference/cdc-class.md)

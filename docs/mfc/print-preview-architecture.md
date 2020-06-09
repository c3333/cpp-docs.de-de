---
title: Druckvorschauarchitektur
ms.date: 11/04/2016
helpviewer_keywords:
- print preview [MFC], process
- previewing printing
- print preview [MFC], architecture
- printing [MFC], print preview
- print preview [MFC], modifications to MFC
ms.assetid: 0efc87e6-ff8d-43c5-9d72-9b729a169115
ms.openlocfilehash: 1956313d4e904255ba59e79690fe3d7144669a29
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623940"
---
# <a name="print-preview-architecture"></a>Druckvorschauarchitektur

In diesem Artikel wird erläutert, wie das MFC-Framework die Funktionen der Druckvorschau implementiert. Folgende Themen werden behandelt:

- [Druckvorschau Prozess](#_core_the_print_preview_process)

- [Ändern der Seitenansicht](#_core_modifying_print_preview)

Die Seitenansicht unterscheidet sich etwas von der Bildschirm Anzeige und dem Druckvorgang, da die Anwendung den Drucker mithilfe des Bildschirms simulieren muss, anstatt ein Bild direkt auf einem Gerät zu zeichnen. Um dies zu ermöglichen, definiert die Microsoft Foundation Class-Bibliothek eine spezielle (nicht dokumentierte) Klasse, die von der [CDC-Klasse](reference/cdc-class.md)abgeleitet wird `CPreviewDC` . Alle- `CDC` Objekte enthalten zwei Geräte Kontexte, aber in der Regel sind Sie identisch. In einem- `CPreviewDC` Objekt unterscheiden sich diese: der erste stellt den zu simulierenden Drucker dar, während der zweite den Bildschirm darstellt, auf dem die Ausgabe tatsächlich angezeigt wird.

## <a name="the-print-preview-process"></a><a name="_core_the_print_preview_process"></a>Der Druckvorschau Prozess

Wenn der Benutzer im Menü **Datei** den Befehl Druckvorschau auswählt, erstellt das Framework ein- `CPreviewDC` Objekt. Jedes Mal, wenn Ihre Anwendung einen Vorgang ausführt, mit dem ein Merkmal des Drucker Geräte Kontexts festgelegt wird, führt das Framework auch einen ähnlichen Vorgang auf dem Bildschirm Gerätekontext aus. Wenn Ihre Anwendung z. b. eine Schriftart zum Drucken auswählt, wählt das Framework eine Schriftart für die Bildschirm Anzeige aus, die die Drucker Schriftart simuliert. Wenn die Anwendung die Ausgabe an den Drucker sendet, sendet das Framework stattdessen die Ausgabe an den Bildschirm.

Die Seitenansicht unterscheidet sich auch vom Drucken in der Reihenfolge, in der die Seiten eines Dokuments gezeichnet werden. Während des Druckens wird das Framework eine Druck Schleife fortgesetzt, bis ein bestimmter Seitenbereich gerendert wurde. Während der Seitenansicht werden eine oder zwei Seiten zu einem beliebigen Zeitpunkt angezeigt, und dann wartet die Anwendung. Weitere Seiten werden erst angezeigt, wenn der Benutzer antwortet. Während der Seitenansicht muss die Anwendung auch auf WM_PAINT Meldungen reagieren, ebenso wie bei der normalen Bildschirm Anzeige.

Die [CView:: OnPreparePrinting](reference/cview-class.md#onprepareprinting) -Funktion wird aufgerufen, wenn der Vorschaumodus aufgerufen wird, so wie dies am Anfang eines Druckauftrags der Fall ist. Die [CPrintInfo-Struktur](reference/cprintinfo-structure.md) , die an die Funktion übergeben wird, enthält mehrere Elemente, deren Werte Sie festlegen können, um bestimmte Merkmale des Druckvor Schau Vorgangs anzupassen. Beispielsweise können Sie das *m_nNumPreviewPages* -Element festlegen, um anzugeben, ob Sie das Dokument im ein-oder zweiseitigen Modus in der Vorschau anzeigen möchten.

## <a name="modifying-print-preview"></a><a name="_core_modifying_print_preview"></a>Ändern der Seitenansicht

Sie können das Verhalten und die Darstellung der Druckvorschau auf verschiedene Weise ändern. Beispielsweise können Sie u. a. Folgendes tun:

- Bewirkt, dass im Seiten Ansichts Fenster eine Schiebe Leiste angezeigt wird, um den Zugriff auf eine beliebige Seite des Dokuments zu vereinfachen.

- Bewirkt, dass die Druckvorschau die Position des Benutzers im Dokument beibehält, indem er die Anzeige auf der aktuellen Seite beginnt.

- Bewirken, dass eine andere Initialisierung für die Druckvorschau und den Druckvorgang durchgeführt wird.

- Bewirkt, dass die Seitenzahlen in der Druckvorschau in ihren eigenen Formaten angezeigt werden.

Wenn Sie wissen, wie lange das Dokument ist und `SetMaxPage` mit dem entsprechenden Wert aufruft, kann das Framework diese Informationen sowohl im Vorschaumodus als auch während des Druckens verwenden. Wenn das Framework die Länge des Dokuments kennt, kann es das Vorschaufenster mit einer Schiebe Leiste bereitstellen, sodass der Benutzer das Dokument im Vorschaumodus hin-und herdurch laufen kann. Wenn Sie die Länge des Dokuments nicht festgelegt haben, kann das Framework das Bild Lauf Feld nicht positionieren, um die aktuelle Position anzugeben, sodass das Framework keine Scrollleiste hinzufügt. In diesem Fall muss der Benutzer auf der Steuerleiste des Vorschau Fensters die Schaltflächen Nächste Seite und vorherige Seite verwenden, um das Dokument zu durchlaufen.

Für die Seitenansicht ist es möglicherweise hilfreich, dem *m_nCurPage* -Element von einen Wert zuzuweisen `CPrintInfo` , auch wenn Sie dies nie für das normale Drucken tun würden. Beim normalen Drucken werden von diesem Member Informationen aus dem Framework in die Ansichts Klasse übernommen. Auf diese Weise teilt das Framework der Ansicht mit, welche Seite gedruckt werden soll.

Wenn der seitenvor Schau Modus gestartet wird, werden vom *m_nCurPage* Member dagegen Informationen in umgekehrter Richtung angezeigt: von der Ansicht bis zum Framework. Das Framework verwendet den Wert dieses Members, um zu bestimmen, welche Seite zuerst in der Vorschau angezeigt werden soll. Der Standardwert dieses Members ist 1, sodass zunächst die erste Seite des Dokuments angezeigt wird. Sie können `OnPreparePrinting` überschreiben, um diesen Member auf die Nummer der Seite festzulegen, die zum Zeitpunkt des aufgerufenen der Druckvorschau angezeigt wird. Auf diese Weise behält die Anwendung die aktuelle Position des Benutzers bei der Umstellung vom normalen Anzeigemodus in den Seiten Vorschaumodus bei.

Manchmal möchten Sie möglicherweise `OnPreparePrinting` eine andere Initialisierung durchführen, je nachdem, ob Sie für einen Druckauftrag oder eine Seitenansicht aufgerufen wird. Dies können Sie ermitteln, indem Sie die *m_bPreview* Member-Variable in der-Struktur überprüfen `CPrintInfo` . Dieser Member wird auf " **true** " festgelegt, wenn die Seitenansicht aufgerufen wird.

Die `CPrintInfo` Struktur enthält auch einen Member mit dem Namen *m_strPageDesc*, der zum Formatieren der Zeichen folgen verwendet wird, die am unteren Rand des Bildschirms im Einzelseiten-und mehreren Seitenmodus angezeigt werden. Standardmäßig haben diese Zeichen folgen die Form "page *n*" und "pages *n*  -  *m*", Sie können jedoch die *m_strPageDesc* in ändern `OnPreparePrinting` und die Zeichen folgen auf etwas ausführlichere festlegen. Weitere Informationen finden Sie unter [CPrintInfo-Struktur](reference/cprintinfo-structure.md) in der *MFC-Referenz* .

## <a name="see-also"></a>Siehe auch

[Drucken und Druckvorschau](printing-and-print-preview.md)<br/>
[Drucken](printing.md)<br/>
[CView-Klasse](reference/cview-class.md)<br/>
[CDC-Klasse](reference/cdc-class.md)

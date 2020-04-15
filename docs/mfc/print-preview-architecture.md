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
ms.openlocfilehash: 5943edc22cd48ed10d152f72624467ff87104b96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375947"
---
# <a name="print-preview-architecture"></a>Druckvorschauarchitektur

In diesem Artikel wird erläutert, wie das MFC-Framework die Druckvorschaufunktionalität implementiert. Folgende Themen werden behandelt:

- [Druckvorschauprozess](#_core_the_print_preview_process)

- [Ändern der Druckvorschau](#_core_modifying_print_preview)

Die Druckvorschau unterscheidet sich etwas von der Bildschirmanzeige und dem Drucken, da die Anwendung den Drucker nicht direkt auf einem Gerät zeichnet, sondern den Drucker mithilfe des Bildschirms simulieren muss. Um dies zu ermöglichen, definiert die Microsoft Foundation-Klassenbibliothek eine spezielle `CPreviewDC`(nicht dokumentierte) Klasse, die von der [CDC-Klasse](../mfc/reference/cdc-class.md)abgeleitet wurde, die als . Alle `CDC` Objekte enthalten zwei Gerätekontexte, sind aber in der Regel identisch. In `CPreviewDC` einem Objekt unterscheiden sie sich: Der erste stellt den zu simulierenden Drucker dar, und das zweite stellt den Bildschirm dar, auf dem die Ausgabe tatsächlich angezeigt wird.

## <a name="the-print-preview-process"></a><a name="_core_the_print_preview_process"></a>Der Druckvorschauprozess

Wenn der Benutzer den Befehl Druckvorschau aus dem Menü `CPreviewDC` **Datei** auswählt, erstellt das Framework ein Objekt. Wenn Ihre Anwendung einen Vorgang ausführt, der ein Merkmal des Druckergerätekontexts festlegt, führt das Framework auch einen ähnlichen Vorgang im Bildschirmgerätekontext aus. Wenn Ihre Anwendung beispielsweise eine Schriftart zum Drucken auswählt, wählt das Framework eine Schriftart für die Bildschirmanzeige aus, die die Druckerschriftart simuliert. Wenn Ihre Anwendung die Ausgabe an den Drucker sendet, sendet das Framework stattdessen die Ausgabe an den Bildschirm.

Die Druckvorschau unterscheidet sich auch in der Reihenfolge, in der die Seiten eines Dokuments gezeichnet werden. Während des Druckens setzt das Framework eine Druckschleife fort, bis ein bestimmter Seitenbereich gerendert wurde. Während der Druckvorschau werden jeweils ein oder zwei Seiten angezeigt, und dann wartet die Anwendung. Es werden keine weiteren Seiten angezeigt, bis der Benutzer antwortet. Während der Druckvorschau muss die Anwendung auch auf WM_PAINT Nachrichten reagieren, genau wie bei der normalen Bildschirmanzeige.

Die [Funktion CView::OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting) wird aufgerufen, wenn der Vorschaumodus aufgerufen wird, genau wie am Anfang eines Druckauftrags. Die an die Funktion [übergebene CPrintInfo-Strukturstruktur](../mfc/reference/cprintinfo-structure.md) enthält mehrere Elemente, deren Werte Sie festlegen können, um bestimmte Merkmale des Druckvorschauvorgangs anzupassen. Sie können z. B. das *m_nNumPreviewPages-Member* festlegen, um anzugeben, ob Sie eine Vorschau des Dokuments im ein- oder zweiseitigen Modus anzeigen möchten.

## <a name="modifying-print-preview"></a><a name="_core_modifying_print_preview"></a>Ändern der Druckvorschau

Sie können das Verhalten und die Darstellung der Druckvorschau auf verschiedene Arten relativ einfach ändern. Sie können unter anderem:

- Bewirkt, dass das Druckvorschaufenster eine Bildlaufleiste für den einfachen Zugriff auf eine beliebige Seite des Dokuments anzeigt.

- Bewirken Sie, dass die Druckvorschau die Position des Benutzers im Dokument beibehält, indem Sie die Anzeige auf der aktuellen Seite beginnen.

- Bewirkt, dass eine andere Initialisierung für die Druckvorschau und den Druck durchgeführt wird.

- Bewirken Sie, dass die Seitenansicht Seitenzahlen in Ihren eigenen Formaten angezeigt wird.

Wenn Sie wissen, wie lange `SetMaxPage` das Dokument ist, und mit dem entsprechenden Wert aufrufen, kann das Framework diese Informationen sowohl im Vorschaumodus als auch während des Druckens verwenden. Sobald das Framework die Länge des Dokuments kennt, kann es dem Vorschaufenster eine Bildlaufleiste zur Verfügung stellen, sodass der Benutzer im Vorschaumodus durch das Dokument hin und her blättern kann. Wenn Sie die Länge des Dokuments nicht festgelegt haben, kann das Framework das Bildlauffeld nicht positionieren, um die aktuelle Position anzugeben, sodass das Framework keine Bildlaufleiste hinzufügt. In diesem Fall muss der Benutzer die Schaltflächen Nächste Seite und Vorherige Seite in der Steuerleiste des Vorschaufensters verwenden, um das Dokument zu durchblättern.

Für die Druckvorschau ist es möglicherweise nützlich, *m_nCurPage* dem `CPrintInfo`m_nCurPage Member von einen Wert zuzuweisen, auch wenn Sie dies beim normalen Drucken nie tun würden. Während des normalen Druckens überträgt dieses Element Informationen aus dem Framework in Ihre Ansichtsklasse. Auf diese Weise teilt das Framework der Ansicht mit, welche Seite gedruckt werden soll.

Wenn hingegen der Druckvorschaumodus gestartet wird, trägt das *m_nCurPage-Member* Informationen in die entgegengesetzte Richtung: von der Ansicht zum Framework. Das Framework verwendet den Wert dieses Elements, um zu bestimmen, welche Seite zuerst in der Vorschau angezeigt werden soll. Der Standardwert dieses Elements ist 1, daher wird die erste Seite des Dokuments zunächst angezeigt. Sie können `OnPreparePrinting` überschreiben, um dieses Element auf die Nummer der Seite festzulegen, die zum Zeitpunkt des Aufrufs des Befehls Druckvorschau angezeigt wird. Auf diese Weise behält die Anwendung die aktuelle Position des Benutzers bei, wenn sie vom normalen Anzeigemodus in den Druckvorschaumodus wechselt.

Manchmal möchten `OnPreparePrinting` Sie möglicherweise eine unterschiedliche Initialisierung durchführen, je nachdem, ob sie für einen Druckauftrag oder für die Druckvorschau aufgerufen wird. Sie können dies *m_bPreview* bestimmen, indem `CPrintInfo` Sie die m_bPreview Membervariable in der Struktur untersuchen. Dieses Element wird auf **TRUE** festgelegt, wenn die Druckvorschau aufgerufen wird.

Die `CPrintInfo` Struktur enthält auch ein Element mit dem Namen *m_strPageDesc*, das verwendet wird, um die am unteren Bildschirmrand angezeigten Zeichenfolgen in einseitigen und mehrseitigen Modi zu formatieren. Standardmäßig haben diese Zeichenfolgen die Form "Seite *n*" und "Seiten *n* - *m",* aber Sie können *m_strPageDesc* von innen `OnPreparePrinting` ändern und die Zeichenfolgen auf etwas aufwendigeres setzen. Weitere Informationen finden Sie unter [CPrintInfo-Struktur](../mfc/reference/cprintinfo-structure.md) in der *MFC-Referenz.*

## <a name="see-also"></a>Siehe auch

[Drucken und Druckvorschau](../mfc/printing-and-print-preview.md)<br/>
[Drucken](../mfc/printing.md)<br/>
[CView-Klasse](../mfc/reference/cview-class.md)<br/>
[CDC-Klasse](../mfc/reference/cdc-class.md)

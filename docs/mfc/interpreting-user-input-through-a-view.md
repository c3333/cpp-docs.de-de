---
title: Interpretieren der Benutzereingaben in einer Ansicht
ms.date: 11/04/2016
helpviewer_keywords:
- interpreting user input through views [MFC]
- views [MFC], user interface and input
- input [MFC], view class [MFC]
- CView class [MFC], interpreting user input
- user input [MFC], interpreting through view class [MFC]
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
ms.openlocfilehash: 43fb903fa169233ce532e41ecdf02c23ab6037c8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621455"
---
# <a name="interpreting-user-input-through-a-view"></a>Interpretieren der Benutzereingaben in einer Ansicht

Andere Element Funktionen der Ansicht Handle und interpretieren alle Benutzereingaben. In der Regel definieren Sie Nachrichten Handler-Member-Funktionen in der Ansichts Klasse, die verarbeitet werden sollen:

- Windows- [Meldungen](messages.md) , die von Maus-und Tastatur Aktionen generiert werden.

- [Befehle](user-interface-objects-and-command-ids.md) aus Menüs, Symbolleisten-Schaltflächen und Tastenkombinationen.

Diese nachrichtenhandlermember-Funktionen interpretieren die folgenden Aktionen als Dateneingabe,-Auswahl oder-Bearbeitung, einschließlich Verschieben von Daten in und aus der Zwischenablage:

- Mausbewegungen und-Klicks, Drags und Doppelklicks

- Tastatureingaben

- Menübefehle

Welche Windows-Meldungen Ihre Ansicht behandelt, hängt von den Anforderungen Ihrer Anwendung ab.

[Themen zur Nachrichten Behandlung und-Zuordnung](message-handling-and-mapping.md) erläutert, wie Menü Elemente und andere Benutzeroberflächen Objekte Befehlen zugewiesen werden und wie die Befehle an Handlerfunktionen gebunden werden. [Themen zur Nachrichten Behandlung und-Zuordnung](message-handling-and-mapping.md) erläutert auch, wie MFC Befehle weiterleitet und standardmäßige Windows-Meldungen an die Objekte sendet, die Handler für Sie enthalten.

Die Anwendung muss z. b. die direkte Maus Zeichnung in der Ansicht implementieren. Das Scribble-Beispiel zeigt, wie Sie die WM_LBUTTONDOWN, WM_MOUSEMOVE und WM_LBUTTONUP Nachrichten verarbeiten können, um das Zeichnen eines Linien Segments zu beginnen, fortzusetzen und zu beenden. Auf der anderen Seite müssen Sie in der Ansicht manchmal einen Mausklick als Auswahl interpretieren. `OnLButtonDown`Die Handlerfunktion der Ansicht bestimmt, ob der Benutzer gezeichnet oder ausgewählt hat. Wenn Sie auswählen, würde der Handler ermitteln, ob sich der Klick innerhalb der Grenzen eines Objekts in der Ansicht befunden hat, und wenn dies der Fall ist, ändern Sie die Anzeige, um das Objekt als ausgewählt anzuzeigen.

In ihrer Ansicht können auch bestimmte Menübefehle behandelt werden, z. b. über das Menü "Bearbeiten", um die ausgewählten Daten mithilfe der Zwischenablage auszuschneiden, zu kopieren, einzufügen oder zu löschen. Ein solcher Handler würde einige der in der Zwischenablage bezogenen Element Funktionen der-Klasse aufzurufen `CWnd` , um ein ausgewähltes Datenelement in die oder aus der Zwischenablage zu übertragen.

## <a name="see-also"></a>Siehe auch

[Verwenden von Ansichten](using-views.md)

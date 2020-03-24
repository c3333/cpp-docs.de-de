---
title: Zeichnen in einer Ansicht
ms.date: 11/04/2016
helpviewer_keywords:
- drawing [MFC], in views
- views [MFC], printing
- views [MFC], updating
- printing [MFC], views
- views [MFC], rendering
- printing views [MFC]
- paint messages in view class [MFC]
- device contexts, screen drawings
ms.assetid: e3761db6-0f19-4482-a4cd-ac38ef7c4d3a
ms.openlocfilehash: 227c4614bad42706893301c69882c3f40af12e2f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214343"
---
# <a name="drawing-in-a-view"></a>Zeichnen in einer Ansicht

Fast alle Zeichnungen in der Anwendung treten in der `OnDraw` Member-Funktion der Sicht auf, die Sie in der Ansichts Klasse überschreiben müssen. (Die Ausnahme ist die Maus Zeichnung, die unter [Interpretieren von Benutzereingaben durch eine Sicht](../mfc/interpreting-user-input-through-a-view.md)erläutert wird.) Ihr `OnDraw` außer Kraft Setzung:

1. Ruft Daten durch Aufrufen der von Ihnen bereitgestellten dokumentmember-Funktionen ab.

1. Zeigt die Daten an, indem Sie die Element Funktionen eines Gerätekontext Objekts aufrufen, das das Framework an `OnDraw`übergibt.

Wenn sich die Daten eines Dokuments auf irgendeine Weise ändern, muss die Sicht neu gezeichnet werden, um die Änderungen widerzuspiegeln. Dies geschieht in der Regel, wenn der Benutzer eine Änderung durch eine Ansicht des Dokuments vornimmt. In diesem Fall ruft die Sicht die [UpdateAllViews](../mfc/reference/cdocument-class.md#updateallviews) -Member-Funktion des Dokuments auf, um alle Sichten desselben Dokuments zu benachrichtigen, um sich selbst zu aktualisieren. `UpdateAllViews` die die [OnUpdate](../mfc/reference/cview-class.md#onupdate) -Member-Funktion jeder Ansicht aufruft. Die Standard Implementierung von `OnUpdate` den gesamten Client Bereich der Ansicht für ungültig erklären. Sie können Sie außer Kraft setzen, sodass nur die Regionen des Client Bereichs ungültig werden, die den geänderten Teilen des Dokuments zugeordnet sind.

Mit der `UpdateAllViews` Member-Funktion der-Klasse `CDocument` und der `OnUpdate` Member-Funktion der-Klasse `CView` können Sie Informationen übergeben, die beschreiben, welche Teile des Dokuments geändert wurden. Mit diesem "Hint"-Mechanismus können Sie den Bereich einschränken, den die Sicht neu zeichnen muss. `OnUpdate` nimmt zwei "Hint"-Argumente an. Der erste *lHint*-Typ des Typs **LPARAM**ermöglicht Ihnen das übergeben beliebiger Daten, während das zweite, *phint*-Objekt vom Typ "`CObject`*" einen Zeiger an ein beliebiges Objekt übergibt, das von `CObject`abgeleitet ist.

Wenn eine Ansicht ungültig wird, sendet Windows eine **WM_PAINT** Meldung. Die [OnPaint](../mfc/reference/cwnd-class.md#onpaint) -Handlerfunktion der Ansicht antwortet auf die Nachricht, indem Sie ein Gerätekontext Objekt der Klasse [CPaintDC](../mfc/reference/cpaintdc-class.md) erstellt und die `OnDraw` Member-Funktion der Ansicht aufruft. Sie müssen normalerweise keine über schreibende `OnPaint` Handlerfunktion schreiben.

Ein [Gerätekontext](../mfc/device-contexts.md) ist eine Windows-Datenstruktur, die Informationen über die Zeichnungs Attribute eines Geräts (z. b. eine Anzeige oder einen Drucker) enthält. Alle Zeichnungs Aufrufe werden über ein Gerätekontext Objekt durchgeführt. Zum Zeichnen auf dem Bildschirm wird `OnDraw` ein `CPaintDC` Objekt übermittelt. Zum Zeichnen auf einem Drucker wird ein [CDC](../mfc/reference/cdc-class.md) -Objekt an den aktuellen Drucker übermittelt.

Der Code zum Zeichnen in der Ansicht ruft zunächst einen Zeiger auf das Dokument ab und führt dann Zeichnungs Aufrufe über den Gerätekontext durch. Im folgenden einfachen `OnDraw` Beispiel wird der Prozess veranschaulicht:

[!code-cpp[NVC_MFCDocView#1](../mfc/codesnippet/cpp/drawing-in-a-view_1.cpp)]

In diesem Beispiel definieren Sie die `GetData`-Funktion als Member der abgeleiteten Document-Klasse.

Im Beispiel wird jede beliebige Zeichenfolge, die aus dem Dokument abgerufen wird, in der Ansicht gedruckt. Wenn der `OnDraw` Aufruf zum Zeichnen des Bildschirms dient, ist das `CDC` Objekt, das in *PDC* übergeben wird, ein `CPaintDC`, dessen Konstruktor bereits `BeginPaint`aufgerufen hat. Aufrufe von Zeichnungsfunktionen werden über den Gerätekontext Zeiger durchgeführt. Weitere Informationen zu Geräte Kontexten und Zeichnungs aufrufen finden Sie unter Class [CDC](../mfc/reference/cdc-class.md) in der *MFC-Referenz* und [Arbeiten mit Fenster Objekten](../mfc/working-with-window-objects.md).

Weitere Beispiele zum Schreiben von `OnDraw`finden Sie in den [MFC-Beispielen](../overview/visual-cpp-samples.md#mfc-samples).

## <a name="see-also"></a>Weitere Informationen

[Verwenden von Ansichten](../mfc/using-views.md)

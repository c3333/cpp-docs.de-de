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
ms.openlocfilehash: c60d99fdebcd64ad844bc19918a30beb90b86af3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618934"
---
# <a name="drawing-in-a-view"></a>Zeichnen in einer Ansicht

Fast alle Zeichnungen in der Anwendung treten in der Member-Funktion der Ansicht auf `OnDraw` , die Sie in der Ansichts Klasse überschreiben müssen. (Die Ausnahme ist die Maus Zeichnung, die unter [Interpretieren von Benutzereingaben durch eine Sicht](interpreting-user-input-through-a-view.md)erläutert wird.) Ihre `OnDraw` außer Kraft Setzung:

1. Ruft Daten durch Aufrufen der von Ihnen bereitgestellten dokumentmember-Funktionen ab.

1. Zeigt die Daten an, indem Sie Member-Funktionen eines Gerätekontext Objekts aufrufen, an das das Framework übergibt `OnDraw` .

Wenn sich die Daten eines Dokuments auf irgendeine Weise ändern, muss die Sicht neu gezeichnet werden, um die Änderungen widerzuspiegeln. Dies geschieht in der Regel, wenn der Benutzer eine Änderung durch eine Ansicht des Dokuments vornimmt. In diesem Fall ruft die Sicht die [UpdateAllViews](reference/cdocument-class.md#updateallviews) -Member-Funktion des Dokuments auf, um alle Sichten desselben Dokuments zu benachrichtigen, um sich selbst zu aktualisieren. `UpdateAllViews`Ruft die [OnUpdate](reference/cview-class.md#onupdate) -Member-Funktion jeder Ansicht auf. Die Standard Implementierung von `OnUpdate` macht den gesamten Client Bereich der Ansicht ungültig. Sie können Sie außer Kraft setzen, sodass nur die Regionen des Client Bereichs ungültig werden, die den geänderten Teilen des Dokuments zugeordnet sind.

Mit der `UpdateAllViews` Member-Funktion der `CDocument` -Klasse und der Member- `OnUpdate` Funktion der-Klasse `CView` können Sie Informationen übergeben, die beschreiben, welche Teile des Dokuments geändert wurden. Mit diesem "Hint"-Mechanismus können Sie den Bereich einschränken, den die Sicht neu zeichnen muss. `OnUpdate`nimmt zwei "Hint"-Argumente an. Der erste *lHint*-Typ des Typs **LPARAM**ermöglicht Ihnen das übergeben beliebiger Daten, während der zweite, *phint*vom Typ `CObject` * einen Zeiger an ein beliebiges von abgeleitetes Objekt übergibt `CObject` .

Wenn eine Ansicht ungültig wird, sendet Windows eine **WM_PAINT** Meldung. Die [OnPaint](reference/cwnd-class.md#onpaint) -Handlerfunktion der Ansicht antwortet auf die Nachricht, indem Sie ein Gerätekontext Objekt der Klasse [CPaintDC](reference/cpaintdc-class.md) erstellt und die Member-Funktion der Ansicht aufruft `OnDraw` . Sie müssen normalerweise keine über schreibende `OnPaint` Handlerfunktion schreiben.

Ein [Gerätekontext](device-contexts.md) ist eine Windows-Datenstruktur, die Informationen über die Zeichnungs Attribute eines Geräts (z. b. eine Anzeige oder einen Drucker) enthält. Alle Zeichnungs Aufrufe werden über ein Gerätekontext Objekt durchgeführt. Zum Zeichnen auf dem Bildschirm `OnDraw` wird ein- `CPaintDC` Objekt übermittelt. Zum Zeichnen auf einem Drucker wird ein [CDC](reference/cdc-class.md) -Objekt an den aktuellen Drucker übermittelt.

Der Code zum Zeichnen in der Ansicht ruft zunächst einen Zeiger auf das Dokument ab und führt dann Zeichnungs Aufrufe über den Gerätekontext durch. Das folgende einfache `OnDraw` Beispiel veranschaulicht den Prozess:

[!code-cpp[NVC_MFCDocView#1](codesnippet/cpp/drawing-in-a-view_1.cpp)]

In diesem Beispiel würden Sie die `GetData` Funktion als Member der abgeleiteten Dokument Klasse definieren.

Im Beispiel wird jede beliebige Zeichenfolge, die aus dem Dokument abgerufen wird, in der Ansicht gedruckt. Wenn der `OnDraw` Aufruf zum Zeichnen des Bildschirms dient, `CDC` ist das in *PDC* weiter gegebene Objekt ein, `CPaintDC` dessen Konstruktor bereits aufgerufen hat `BeginPaint` . Aufrufe von Zeichnungsfunktionen werden über den Gerätekontext Zeiger durchgeführt. Weitere Informationen zu Geräte Kontexten und Zeichnungs aufrufen finden Sie unter Class [CDC](reference/cdc-class.md) in der *MFC-Referenz* und [Arbeiten mit Fenster Objekten](working-with-window-objects.md).

Weitere Beispiele zum Schreiben von finden Sie in `OnDraw` den [MFC-Beispielen](../overview/visual-cpp-samples.md#mfc-samples).

## <a name="see-also"></a>Siehe auch

[Verwenden von Ansichten](using-views.md)

---
title: Verwenden von Rückruffeldern in einem Steuerelement für die Datums- und Zeitauswahl
ms.date: 11/04/2016
f1_keywords:
- DTN_FORMATQUERY
- DTN_FORMAT
helpviewer_keywords:
- DateTimePicker control [MFC], callback fields
- callback fields in CDateTimeCtrl class [MFC]
- CDateTimeCtrl class [MFC], callback fields
- CDateTimeCtrl class [MFC], handling DTN_FORMAT and DTN_FORMATQ
- DTN_FORMATQUERY notification [MFC]
- DTN_FORMAT notification [MFC]
- DateTimePicker control [MFC]
ms.assetid: 404f4ba9-cba7-4718-9faa-bc6b274a723f
ms.openlocfilehash: 50350e51b6747d8c010db9d0dcaa9dff2e56e1f3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366558"
---
# <a name="using-callback-fields-in-a-date-and-time-picker-control"></a>Verwenden von Rückruffeldern in einem Steuerelement für die Datums- und Zeitauswahl

Zusätzlich zu den Standardformatzeichen, die Datums- und Uhrzeitauswahlfelder definieren, können Sie die Ausgabe anpassen, indem Sie bestimmte Teile einer benutzerdefinierten Formatzeichenfolge als Rückruffelder angeben. Um ein Rückruffeld zu deklarieren, fügen Sie ein oder mehrere "X"-Zeichen (ASCII-Code 88) an einer beliebigen Stelle im Textkörper der Formatzeichenfolge ein. Die folgende Zeichenfolge "'Heute ist z. B.: 'yy'/'MM'/'dd' (Tag 'X')'" bewirkt, dass das Datums- und Uhrzeitauswahlsteuerelement den aktuellen Wert als Jahr gefolgt von Monat, Datum und schließlich dem Tag des Jahres anzeigt.

> [!NOTE]
> Die Anzahl der X in einem Rückruffeld entspricht nicht der Anzahl der Zeichen, die angezeigt werden.

Sie können zwischen mehreren Rückruffeldern in einer benutzerdefinierten Zeichenfolge unterscheiden, indem Sie das Zeichen "X" wiederholen. So enthält die Formatzeichenfolge "XXddddMMMdd", 'yyyXXX' zwei eindeutige Rückruffelder, "XX" und "XXX".

> [!NOTE]
> Rückruffelder werden als gültige Felder behandelt, daher muss Ihre Anwendung darauf vorbereitet sein, DTN_WMKEYDOWN Benachrichtigungen zu verarbeiten.

Das Implementieren von Rückruffeldern in Der Datums- und Zeitauswahlsteuerung besteht aus drei Teilen:

- Initialisieren der benutzerdefinierten Formatzeichenfolge

- Behandeln der DTN_FORMATQUERY Benachrichtigung

- Behandeln der DTN_FORMAT-Benachrichtigung

## <a name="initializing-the-custom-format-string"></a>Initialisieren der benutzerdefinierten Formatzeichenfolge

Initialisieren Sie die benutzerdefinierte `CDateTimeCtrl::SetFormat`Zeichenfolge mit einem Aufruf von . Weitere Informationen finden Sie unter [Verwenden von benutzerdefinierten Formatzeichenfolgen in einem Datums- und Zeitauswahlsteuerelement](../mfc/using-custom-format-strings-in-a-date-and-time-picker-control.md). Ein häufiger Ort zum Festlegen der `OnInitDialog` benutzerdefinierten Formatzeichenfolge ist `OnInitialUpdate` die Funktion der enthaltenden Dialogklasse oder Funktion der enthaltenden Ansichtsklasse.

## <a name="handling-the-dtn_formatquery-notification"></a>Behandeln der DTN_FORMATQUERY Benachrichtigung

Wenn das Steuerelement die Formatzeichenfolge analysiert und auf ein Rückruffeld stößt, sendet die Anwendung DTN_FORMAT und DTN_FORMATQUERY Benachrichtigungen. Die Rückruffeldzeichenfolge ist in den Benachrichtigungen enthalten, sodass Sie bestimmen können, welches Rückruffeld abgefragt wird.

Die DTN_FORMATQUERY Benachrichtigung wird gesendet, um die maximal zulässige Größe in Pixeln der Zeichenfolge abzurufen, die im aktuellen Rückruffeld angezeigt wird.

Um diesen Wert richtig zu berechnen, müssen Sie die Höhe und Breite der Zeichenfolge berechnen, die durch das Feld ersetzt werden soll, indem Sie die Anzeigeschriftart des Steuerelements verwenden. Die eigentliche Berechnung der Zeichenfolge kann leicht mit einem Aufruf der [GetTextExtentPoint32](/windows/win32/api/wingdi/nf-wingdi-gettextextentpoint32w) Win32-Funktion erreicht werden. Nachdem die Größe ermittelt wurde, übergeben Sie den Wert an die Anwendung zurück, und beenden Sie die Handlerfunktion.

Das folgende Beispiel ist eine Methode zum Bereitstellen der Größe der Rückrufzeichenfolge:

[!code-cpp[NVC_MFCControlLadenDialog#8](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_1.cpp)]

Nachdem die Größe des aktuellen Rückruffelds berechnet wurde, müssen Sie einen Wert für das Feld angeben. Dies geschieht im Handler für die DTN_FORMAT Benachrichtigung.

## <a name="handling-the-dtn_format-notification"></a>Behandeln der DTN_FORMAT-Benachrichtigung

Die DTN_FORMAT Benachrichtigung wird von der Anwendung verwendet, um die Zeichenkette anzufordern, die ersetzt wird. Das folgende Beispiel veranschaulicht eine mögliche Methode:

[!code-cpp[NVC_MFCControlLadenDialog#9](../mfc/codesnippet/cpp/using-callback-fields-in-a-date-and-time-picker-control_2.cpp)]

> [!NOTE]
> Der Zeiger auf die **NMDATETIMEFORMAT-Struktur** wird gefunden, indem der erste Parameter des Benachrichtigungshandlers auf den richtigen Typ umgegossen wird.

## <a name="see-also"></a>Siehe auch

[Verwenden von CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)

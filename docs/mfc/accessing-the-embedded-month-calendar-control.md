---
title: Zugreifen auf das eingebettete Monatskalender-Steuerelement
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], accessing month calendar
- CDateTimeCtrl class [MFC], accessing embedded control
- month calendar controls [MFC], embedded in date/time picker
- CMonthCalCtrl class [MFC], changing the font
- month calendar controls [MFC], changing the font
- DateTimePicker control [MFC]
ms.assetid: 355e97ed-cf81-4df3-a2f8-9ddbbde93227
ms.openlocfilehash: 66a9ef7fd49ea81ddac4779aa6d1c3f12fbe4c55
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617379"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>Zugreifen auf das eingebettete Monatskalender-Steuerelement

Der Zugriff auf das eingebettete Monatskalender-Steuer Objekt ist vom- `CDateTimeCtrl` Objekt mit einem Aufrufen der [GetMonthCalCtrl](reference/cdatetimectrl-class.md#getmonthcalctrl) -Member-Funktion möglich.

> [!NOTE]
> Das eingebettete Monatskalender-Steuerelement wird nur verwendet, wenn das Steuerelement für die Datums-und Uhrzeit Auswahl nicht den **DTS_UPDOWN** Stil festgelegt hat.

Dies ist nützlich, wenn Sie bestimmte Attribute ändern möchten, bevor das eingebettete Steuerelement angezeigt wird. Um dies zu erreichen, behandeln Sie die **DTN_DROPDOWN** Benachrichtigung, rufen Sie das Monatskalender-Steuerelement (mithilfe von [CDateTimeCtrl:: GetMonthCalCtrl](reference/cdatetimectrl-class.md#getmonthcalctrl)) ab, und nehmen Sie die Änderungen vor. Leider ist das Monatskalender-Steuerelement nicht persistent.

Anders ausgedrückt: Wenn der Benutzer die Anzeige des Monatskalender-Steuer Elements anfordert, wird ein neues Monatskalender-Steuerelement erstellt (vor der **DTN_DROPDOWN** Benachrichtigung). Das Steuerelement wird (nach der **DTN_CLOSEUP** Benachrichtigung) zerstört, wenn es vom Benutzer verworfen wurde. Dies bedeutet, dass alle Attribute, die Sie ändern, bevor das eingebettete Steuerelement angezeigt wird, verloren gehen, wenn das eingebettete Steuerelement verworfen wird.

Das folgende Beispiel veranschaulicht dieses Verfahren mithilfe eines Handlers für die **DTN_DROPDOWN** Benachrichtigung. Im Code wird die Hintergrundfarbe des Monatskalender-Steuer Elements mit einem [callmonthcalcolor](reference/cdatetimectrl-class.md#setmonthcalcolor)-Befehl in Grau geändert. Der Code lautet wie folgt:

[!code-cpp[NVC_MFCControlLadenDialog#5](codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

Wie bereits erwähnt, gehen alle Änderungen an den Eigenschaften des Monatskalender-Steuer Elements mit zwei Ausnahmen verloren, wenn das eingebettete Steuerelement verworfen wird. Die erste Ausnahme, die Farben des Monatskalender-Steuer Elements, wurde bereits erläutert. Die zweite Ausnahme ist die Schriftart, die vom Monatskalender-Steuerelement verwendet wird. Sie können die Standard Schriftart ändern, indem Sie [CDateTimeCtrl:: SetMonthCalFont](reference/cdatetimectrl-class.md#setmonthcalfont)aufrufen, indem Sie das Handle einer vorhandenen Schriftart übergeben. Das folgende Beispiel (wobei `m_dtPicker` das Date-und Time-Steuerelement Objekt ist) veranschaulicht eine mögliche Methode:

[!code-cpp[NVC_MFCControlLadenDialog#6](codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

Nachdem die Schriftart mit einem Aufruf von geändert wurde `CDateTimeCtrl::SetMonthCalFont` , wird die neue Schriftart gespeichert und verwendet, wenn ein Monatskalender das nächste Mal angezeigt wird.

## <a name="see-also"></a>Siehe auch

[Verwenden von CDateTimeCtrl](using-cdatetimectrl.md)<br/>
[Steuerelemente](controls-mfc.md)

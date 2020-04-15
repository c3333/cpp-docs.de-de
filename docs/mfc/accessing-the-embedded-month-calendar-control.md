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
ms.openlocfilehash: 69270cc5663406f2c5d38ffccdbd35f39298a3d5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354180"
---
# <a name="accessing-the-embedded-month-calendar-control"></a>Zugreifen auf das eingebettete Monatskalender-Steuerelement

Auf das eingebettete Monatskalender-Steuerelementobjekt kann vom `CDateTimeCtrl` Objekt mit einem Aufruf der [GetMonthCalCtrl-Memberfunktion](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl) zugegriffen werden.

> [!NOTE]
> Das eingebettete Monatskalendersteuerelement wird nur verwendet, wenn das Datums- und Uhrzeitauswahlsteuerelement nicht über den **DTS_UPDOWN** Stilsatz festgelegt ist.

Dies ist nützlich, wenn Sie bestimmte Attribute ändern möchten, bevor das eingebettete Steuerelement angezeigt wird. Behandeln Sie dazu die **DTN_DROPDOWN** Benachrichtigung, rufen Sie das Monatskalendersteuerelement ab (mit [CDateTimeCtrl::GetMonthCalCtrl](../mfc/reference/cdatetimectrl-class.md#getmonthcalctrl)), und nehmen Sie Ihre Änderungen vor. Leider ist das Monatskalendersteuerelement nicht persistent.

Mit anderen Worten, wenn der Benutzer die Anzeige des Monatskalendersteuerelements anfordert, wird ein neues Monatskalendersteuerelement erstellt (vor der **DTN_DROPDOWN** Benachrichtigung). Das Steuerelement wird (nach der **DTN_CLOSEUP** Benachrichtigung) zerstört, wenn es vom Benutzer verworfen wird. Dies bedeutet, dass alle Attribute, die Sie ändern, bevor das eingebettete Steuerelement angezeigt wird, verloren gehen, wenn das eingebettete Steuerelement verworfen wird.

Im folgenden Beispiel wird dieses Verfahren mithilfe eines Handlers für die **DTN_DROPDOWN-Benachrichtigung** veranschaulicht. Der Code ändert die Hintergrundfarbe des Monatskalendersteuerelements mit einem Aufruf von [SetMonthCalColor](../mfc/reference/cdatetimectrl-class.md#setmonthcalcolor), in Grau. Der Code lautet wie folgt:

[!code-cpp[NVC_MFCControlLadenDialog#5](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_1.cpp)]

Wie bereits erwähnt, gehen alle Änderungen an den Eigenschaften des Monatskalendersteuerelements verloren, mit zwei Ausnahmen, wenn das eingebettete Steuerelement verworfen wird. Die erste Ausnahme, die Farben des Monatskalendersteuerelements, wurde bereits diskutiert. Die zweite Ausnahme ist die Schriftart, die vom Monatskalendersteuerelement verwendet wird. Sie können die Standardschriftart ändern, indem Sie [CDateTimeCtrl::SetMonthCalFont](../mfc/reference/cdatetimectrl-class.md#setmonthcalfont)aufrufen und das Handle einer vorhandenen Schriftart übergeben. Das folgende Beispiel `m_dtPicker` (wobei ist das Datums- und Uhrzeitsteuerungsobjekt) veranschaulicht eine mögliche Methode:

[!code-cpp[NVC_MFCControlLadenDialog#6](../mfc/codesnippet/cpp/accessing-the-embedded-month-calendar-control_2.cpp)]

Sobald die Schriftart geändert wurde, `CDateTimeCtrl::SetMonthCalFont`wird die neue Schriftart mit einem Aufruf von gespeichert und verwendet, wenn das nächste Mal ein Monatskalender angezeigt wird.

## <a name="see-also"></a>Siehe auch

[Verwenden von CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)

---
title: Einstellen des Tagesstatus für ein Monatskalender-Steuerelement
ms.date: 11/04/2016
f1_keywords:
- MCN_GETDAYSTATE
helpviewer_keywords:
- CMonthCalCtrl class [MFC], setting day state info
- MCN_GETDAYSTATE notification [MFC]
- month calendar controls [MFC], day state info
ms.assetid: 435d1b11-ec0e-4121-9e25-aaa6af812a3c
ms.openlocfilehash: 9892f2d853687787dd76428fc9bc95f3a4f74565
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365430"
---
# <a name="setting-the-day-state-of-a-month-calendar-control"></a>Einstellen des Tagesstatus für ein Monatskalender-Steuerelement

Eines der Attribute eines Monatskalendersteuerelements ist die Möglichkeit, Informationen, die als Tagesstatus des Steuerelements bezeichnet werden, für jeden Tag des Monats zu speichern. Diese Informationen werden verwendet, um bestimmte Daten für den aktuell angezeigten Monat hervorzuheben.

> [!NOTE]
> Das `CMonthCalCtrl` Objekt muss über den MCS_DAYSTATE Stil verfügen, um Tagesstatusinformationen anzuzeigen.

Tagesstatusinformationen werden als 32-Bit-Datentyp **MONTHDAYSTATE**ausgedrückt. Jedes Bit in einem **MONTHDAYSTATE-Bitfeld** (1 bis 31) stellt den Zustand eines Tages in einem Monat dar. Wenn ein Bit eingeschaltet ist, wird der entsprechende Tag fett angezeigt. andernfalls wird es ohne Betonung angezeigt.

Es gibt zwei Methoden zum Festlegen des Tagesstatus des Monatskalendersteuerelements: explizit mit einem Aufruf von [CMonthCalCtrl::SetDayState](../mfc/reference/cmonthcalctrl-class.md#setdaystate) oder durch Die Behandlung der MCN_GETDAYSTATE Benachrichtigung.

## <a name="handling-the-mcn_getdaystate-notification-message"></a>Behandeln der MCN_GETDAYSTATE Benachrichtigung

Die MCN_GETDAYSTATE Nachricht wird vom Steuerelement gesendet, um zu bestimmen, wie die Tage innerhalb der sichtbaren Monate angezeigt werden sollen.

> [!NOTE]
> Da das Steuerelement die vorherigen und folgenden Monate in Bezug auf den sichtbaren Monat zwischenspeichert, erhalten Sie diese Benachrichtigung jedes Mal, wenn ein neuer Monat ausgewählt wird.

Um diese Nachricht ordnungsgemäß behandeln zu können, müssen Sie bestimmen, für wie viele Monate Statusinformationen angefordert werden, ein Array von **MONTHDAYSTATE-Strukturen** mit den richtigen Werten initialisieren und das zugehörige Strukturelement mit den neuen Informationen initialisieren. Bei der folgenden Vorgehensweise wird die erforderlichen Schritte `CMonthCalCtrl` erläutert, und es wird davon ausgegangen, dass Sie über ein Objekt *mit* dem Namen m_monthcal und ein Array von **MONTHDAYSTATE-Objekten,** *mdState*, verfügen.

#### <a name="to-handle-the-mcn_getdaystate-notification-message"></a>So behandeln Sie die MCN_GETDAYSTATE Benachrichtigung

1. Fügen Sie dem *m_monthcal-Objekt* mithilfe des [Klassen-Assistenten](reference/mfc-class-wizard.md)einen Benachrichtigungshandler für die MCN_GETDAYSTATE Nachricht hinzu (siehe [Zuordnen von Nachrichten zu Funktionen](../mfc/reference/mapping-messages-to-functions.md)).

1. Fügen Sie im Hauptteil des Handlers den folgenden Code hinzu:

   [!code-cpp[NVC_MFCControlLadenDialog#26](../mfc/codesnippet/cpp/setting-the-day-state-of-a-month-calendar-control_1.cpp)]

   Das Beispiel konvertiert den *pNMHDR-Zeiger* in den richtigen Typ und bestimmt`pDayState->cDayState`dann, wie viele Monate Informationen angefordert werden ( ). Für jeden Monat wird das`pDayState->prgDayState[i]`aktuelle Bitfeld ( ) auf Null initialisiert und dann die erforderlichen Datumsangaben festgelegt (in diesem Fall das 15. eines jeden Monats).

## <a name="see-also"></a>Siehe auch

[Verwenden von CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Steuerelemente](../mfc/controls-mfc.md)

---
title: Behandeln der TTN_NEEDTEXT-Benachrichtigung für QuickInfos
ms.date: 11/04/2016
f1_keywords:
- TTN_NEEDTEXT
helpviewer_keywords:
- TTN_NEEDTEXT message [MFC]
- notifications [MFC], tool tips
- tool tips [MFC], notifications
ms.assetid: d0370a65-21ba-4676-bcc5-8cf851bbb15c
ms.openlocfilehash: 75850dbf92587cf654d4f7a39ea54af1fd9dd5bd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620082"
---
# <a name="handling-ttn_needtext-notification-for-tool-tips"></a>Behandeln der TTN_NEEDTEXT-Benachrichtigung für QuickInfos

Im Rahmen der [Aktivierung](enabling-tool-tips.md)von Quick Infos verarbeiten Sie die **TTN_NEEDTEXT** Nachricht, indem Sie den folgenden Eintrag zur Meldungs Zuordnung Ihres Besitzer Fensters hinzufügen:

[!code-cpp[NVC_MFCControlLadenDialog#40](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_1.cpp)]

*Mitgliedschaft*<br/>
Die Member-Funktion, die aufgerufen werden soll, wenn Text für diese Schaltfläche benötigt wird.

Beachten Sie, dass die ID einer QuickInfo immer 0 ist.

Deklarieren Sie die Handlerfunktion in der Klassendefinition wie folgt:

[!code-cpp[NVC_MFCControlLadenDialog#53](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_2.h)]

die kursiv formatierten Parameter lauten wie folgt:

*id*<br/>
Der Bezeichner des Steuer Elements, das die Benachrichtigung gesendet hat. Wird nicht verwendet. Die Steuerelement-ID wird aus der **NMHDR** -Struktur entnommen.

*pNMHDR*<br/>
Ein Zeiger auf die [nmttdispinfo](/windows/win32/api/commctrl/ns-commctrl-nmttdispinfow) -Struktur. Diese Struktur wird auch weiter unten in [der ToolTipText-Struktur](tooltiptext-structure.md)erläutert.

*pResult*<br/>
Ein Zeiger auf den Ergebniscode, den Sie vor der Rückgabe festlegen können. **TTN_NEEDTEXT** Handler können den *pResult* -Parameter ignorieren.

Als Beispiel für einen Formular Ansichts Benachrichtigungs Handler:

[!code-cpp[NVC_MFCControlLadenDialog#54](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_3.cpp)]

Aufrufen `EnableToolTips` (dieses Fragment stammt aus `OnInitDialog` ):

[!code-cpp[NVC_MFCControlLadenDialog#55](codesnippet/cpp/handling-ttn-needtext-notification-for-tool-tips_4.cpp)]

## <a name="see-also"></a>Siehe auch

[QuickInfos in Fenstern, die nicht von CFrameWnd abgeleitet sind](tool-tips-in-windows-not-derived-from-cframewnd.md)

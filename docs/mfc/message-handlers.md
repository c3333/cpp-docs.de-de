---
title: Meldungshandler
ms.date: 11/04/2016
helpviewer_keywords:
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
ms.openlocfilehash: f9c5272b513a92dc6dcfa37559b00ae79b658918
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619979"
---
# <a name="message-handlers"></a>Meldungshandler

In MFC verarbeitet eine dedizierte *Handlerfunktion* jede separate Nachricht. Nachrichtenhandlerfunktionen sind Element Funktionen einer-Klasse. In dieser Dokumentation werden die Begriffe der *Nachrichten Handler-Member* *, der Nachrichten Handler*, der Meldungs *Handler*und der *Handler* austauschbar verwendet. Einige Arten von Meldungs Handlern werden auch als "Befehls Handler" bezeichnet.

Das Schreiben von Meldungs Handlern ist ein großer Teil ihrer Arbeit beim Schreiben einer Framework-Anwendung. In dieser Artikel Familie wird beschrieben, wie der Mechanismus für die Nachrichtenverarbeitung funktioniert.

Was bewirkt, dass der Handler für eine Nachricht eine beliebige Aktion als Reaktion auf diese Nachricht durchführt. Sie können die Handler mit dem [Klassen-Assistenten](reference/mfc-class-wizard.md) der-Klasse erstellen und dann den Code des Handler mithilfe des Quell Code-Editors ausfüllen.

Sie können alle Funktionen von Microsoft Visual C++ und MFC zum Schreiben von Handlern verwenden. Eine Liste aller Klassen finden Sie unter [Übersicht über die Klassenbibliothek](class-library-overview.md) in der *MFC-Referenz*.

## <a name="see-also"></a>Siehe auch

[Meldungen und Befehle im Framework](messages-and-commands-in-the-framework.md)

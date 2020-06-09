---
title: Meldungen
ms.date: 11/04/2016
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
ms.openlocfilehash: f36dab679a2e41910b2445a7dab36f5786081563
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624282"
---
# <a name="messages"></a>Meldungen

Die Message-Schleife in der `Run` Member-Funktion der-Klasse `CWinApp` Ruft von verschiedenen Ereignissen generierte Nachrichten in der Warteschlange ab. Wenn der Benutzer z. b. auf die Maus klickt, sendet Windows mehrere Maus bezogene Meldungen, z. b. WM_LBUTTONDOWN, wenn die linke Maustaste gedrückt wird, und WM_LBUTTONUP, wenn die linke Maustaste losgelassen wird. Durch die Implementierung des Frameworks der Anwendungs Nachrichten Schleife wird die Nachricht an das entsprechende Fenster gesendet.

Die wichtigen Kategorien von Nachrichten werden in [Nachrichten Kategorien](message-categories.md)beschrieben.

## <a name="see-also"></a>Siehe auch

[Meldungen und Befehle im Framework](messages-and-commands-in-the-framework.md)

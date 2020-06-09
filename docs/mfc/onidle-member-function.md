---
title: OnIdle-Memberfunktion
ms.date: 11/19/2018
f1_keywords:
- OnIdle
helpviewer_keywords:
- processing messages [MFC]
- OnIdle method [MFC]
- idle loop processing [MFC]
- CWinApp class [MFC], OnIdle method [MFC]
- message handling [MFC], OnIdle method [MFC]
ms.assetid: 51adc874-0075-4f76-be1c-79283f46c10b
ms.openlocfilehash: 17595713f942c7fe7784fa2a12adbcc583cad418
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619846"
---
# <a name="onidle-member-function"></a>OnIdle-Memberfunktion

Wenn keine Windows-Meldungen verarbeitet werden, ruft das Framework die [CWinApp](reference/cwinapp-class.md) -Member-Funktion ( [OnIdle](reference/cwinapp-class.md#onidle) ) auf (beschrieben in der MFC-Bibliotheks Referenz).

`OnIdle`Überschreiben, um Hintergrundaufgaben auszuführen. Die Standardversion aktualisiert den Zustand von Benutzeroberflächen Objekten, wie z. b. Symbolleisten Schaltflächen, und führt eine Bereinigung temporärer Objekte aus, die vom Framework im Verlauf der Vorgänge erstellt werden. In der folgenden Abbildung wird veranschaulicht, wie die Nachrichten Schleife aufruft, `OnIdle` Wenn keine Nachrichten in der Warteschlange vorhanden sind.

![Nachrichten Schleifen Prozess](../mfc/media/vc387c1.gif "Nachrichtenschleifenprozess") <br/>
Nachrichtenschleife

Weitere Informationen dazu, was Sie in der Leerlauf Schleife tun können, finden Sie unter [Leerlauf Schleifen Verarbeitung](idle-loop-processing.md).

## <a name="see-also"></a>Siehe auch

[CWinApp: Die Anwendungsklasse](cwinapp-the-application-class.md)

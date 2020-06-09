---
title: OnCmdMsg-Handler
ms.date: 11/04/2016
f1_keywords:
- OnCmdMsg
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
ms.openlocfilehash: 5114fe53a5bac345eb6a55fb6c371f7bc1f698ef
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624029"
---
# <a name="oncmdmsg-handler"></a>OnCmdMsg-Handler

Um das Routing von Befehlen durchzuführen, ruft jedes Befehls Ziel die `OnCmdMsg` Member-Funktion des nächsten Befehls Ziels in der Sequenz auf. Befehls Ziele verwenden `OnCmdMsg` , um zu bestimmen, ob Sie einen Befehl verarbeiten und an ein anderes Befehls Ziel weiterleiten können, wenn Sie ihn nicht verarbeiten können.

Jede Befehls Zielklasse kann die Member- `OnCmdMsg` Funktion überschreiben. Die über schreibungen ermöglichen es jeder Klasse, Befehle an ein bestimmtes nächstes Ziel weiterzuleiten. Ein Rahmen Fenster leitet z. b. Befehle immer an das aktuelle untergeordnete Fenster oder die Ansicht weiter, wie in der Tabelle [Standard Befehls Route](command-routing.md)gezeigt.

Die Standard `CCmdTarget` Implementierung von verwendet die Meldungs Zuordnung der `OnCmdMsg` Befehls Zielklasse, um nach einer Handlerfunktion für jede empfangene Befehlsnachricht zu suchen – auf dieselbe Weise, wie Standard Meldungen durchsucht werden. Wenn eine Entsprechung gefunden wird, wird der-Handler aufgerufen. Die Nachrichten-Zuordnungs Suche wird erläutert, [wie das Framework](how-the-framework-searches-message-maps.md)Meldungs Zuordnungen durchsucht.

## <a name="see-also"></a>Siehe auch

[So ruft das Framework einen Handler auf](how-the-framework-calls-a-handler.md)

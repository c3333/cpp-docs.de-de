---
title: Zuordnen von Meldungen
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], about message maps
- mappings [MFC], commands
- commands [MFC], mapping
- command mapping [MFC]
- message handling [MFC], connecting to handler functions
- commands [MFC], connecting to handler functions
- mappings [MFC], messages
- messages [MFC], mapping
ms.assetid: 996f0652-0698-4b8c-b893-cdaa836d9d0f
ms.openlocfilehash: 16d6d7725d82bed6c9bfc02e408b68dcf7ffe5e4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625491"
---
# <a name="mapping-messages"></a>Zuordnen von Meldungen

Jede Framework-Klasse, die Nachrichten oder Befehle empfangen kann, verfügt über eine eigene "Meldungs Zuordnung". Das Framework verwendet Nachrichten Zuordnungen, um Nachrichten und Befehle mit ihren Handlerfunktionen zu verbinden. Jede von der-Klasse abgeleitete Klasse `CCmdTarget` kann über eine Meldungs Zuordnung verfügen. In anderen Artikeln werden Meldungs Zuordnungen ausführlich erläutert und beschrieben, wie Sie verwendet werden.

Trotz des Namens "Message Map" verarbeiten Nachrichten Zuordnungen sowohl Nachrichten als auch Befehle – alle drei Kategorien von Nachrichten, die in [Nachrichten Kategorien](message-categories.md)aufgelistet sind.

## <a name="see-also"></a>Siehe auch

[Meldungen und Befehle im Framework](messages-and-commands-in-the-framework.md)

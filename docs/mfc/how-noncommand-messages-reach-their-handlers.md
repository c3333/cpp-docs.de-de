---
title: Wie nicht befehlsbasierte Meldungen ihre Handler erreichen
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
ms.openlocfilehash: c7b2bf819c5305da4039fae172578298d3b4e609
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618505"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>Wie nicht befehlsbasierte Meldungen ihre Handler erreichen

Im Gegensatz zu Befehlen werden standardmäßige Windows-Meldungen nicht durch eine Kette von Befehls Zielen weitergeleitet, sondern normalerweise von dem Fenster verarbeitet, an das die Nachricht von Windows gesendet wird. Das Fenster ist möglicherweise ein Hauptrahmen Fenster, ein untergeordnetes MDI-Fenster, ein Standard Steuerelement, ein Dialogfeld, eine Ansicht oder eine andere Art von untergeordnetem Fenster.

Zur Laufzeit wird jedes Windows-Fenster an ein Fenster Objekt angefügt (direkt oder indirekt von abgeleitet `CWnd` ), das über eine eigene zugeordnete Meldungs Zuordnung und Handlerfunktionen verfügt. Das Framework verwendet die Message Map – wie bei einem Command –, um eingehende Nachrichten den Handlern zuzuordnen.

## <a name="see-also"></a>Siehe auch

[So ruft das Framework einen Handler auf](how-the-framework-calls-a-handler.md)

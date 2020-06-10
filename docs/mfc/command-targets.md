---
title: Befehlsziele
ms.date: 11/04/2016
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
ms.openlocfilehash: 59ba197174e95e42cd237c875f39f07801cb3dbe
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619309"
---
# <a name="command-targets"></a>Befehlsziele

Die Figure- [Befehle im Framework](user-interface-objects-and-command-ids.md) zeigen die Verbindung zwischen einem Benutzeroberflächen Objekt (z. b. einem Menü Element) und der Handlerfunktion, die das Framework aufruft, um den resultierenden Befehl auszuführen, wenn auf das Objekt geklickt wird.

Windows sendet Nachrichten, bei denen es sich nicht um Befehls Meldungen handelt, direkt an ein Fenster, dessen Handler für die Nachricht aufgerufen wird. Das Framework leitet jedoch Befehle an eine Reihe von Kandidaten Objekten weiter – die als "Befehls Ziele" bezeichnet werden – von denen eine normalerweise einen Handler für den Befehl aufruft. Die Handlerfunktionen funktionieren sowohl für Befehle als auch für standardmäßige Windows-Meldungen, aber die Mechanismen, mit denen Sie aufgerufen werden, unterscheiden sich in der Art und Weise, [wie das Framework einen Handler aufruft](how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>Siehe auch

[Meldungen und Befehle im Framework](messages-and-commands-in-the-framework.md)

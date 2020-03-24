---
title: Linkertoolwarnung LNK4022
ms.date: 11/04/2016
f1_keywords:
- LNK4022
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
ms.openlocfilehash: 9b9ce09a7133c0bdc18957f6ade213583e9540eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194186"
---
# <a name="linker-tools-warning-lnk4022"></a>Linkertoolwarnung LNK4022

Es wurde keine eindeutige Entsprechung für Symbol ' Symbol ' gefunden.

Link oder lib hat mehrere Übereinstimmungen für das angegebene nicht ergänzte Symbol gefunden, und die Mehrdeutigkeit konnte nicht aufgelöst werden. Es wird keine Ausgabedatei (. exe,. dll,. exp oder. lib) erstellt. Auf diese Warnung folgt eine Warnung [Linkertoolwarnung LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) für jedes doppelte Symbol und schließlich wird ein schwerwiegender Fehler [Linkertoolfehler LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md)gefolgt.

Um diese Warnung zu vermeiden, geben Sie das Symbol in seiner ergänzten Form an. Führen Sie [DUMPBIN](../../build/reference/dumpbin-options.md) für das-Objekt aus, um ergänzte Namen anzuzeigen.

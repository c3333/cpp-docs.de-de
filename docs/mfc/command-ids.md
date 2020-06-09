---
title: Befehls-IDs
ms.date: 11/04/2016
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
ms.openlocfilehash: f7d675891904301b16aafe3acb2c294eede6d8d8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619037"
---
# <a name="command-ids"></a>Befehls-IDs

Ein Befehl wird vollständig durch die Befehls-ID (in der **WM_COMMAND** Meldung codiert) beschrieben. Diese ID wird dem Benutzeroberflächen Objekt zugewiesen, das den Befehl generiert. IDs werden in der Regel für die Funktionalität des Benutzeroberflächen Objekts benannt, dem Sie zugewiesen sind.

Beispielsweise kann dem Menü "Bearbeiten" im Menü "Bearbeiten" eine ID zugewiesen werden, z. b. **ID_EDIT_CLEAR_ALL**. Die Klassenbibliothek definiert einige IDs vordefiniert, insbesondere für Befehle, die das Framework selbst behandelt, wie z. b. **ID_EDIT_CLEAR_ALL** oder **ID_FILE_OPEN**. Sie erstellen selbst andere Befehls-IDs.

Wenn Sie im Menü-Editor für Visual C++ eigene Menüs erstellen, empfiehlt es sich, die Benennungs Konvention der Klassenbibliothek wie in **ID_FILE_OPEN**dargestellt zu befolgen. [Standard Befehle](standard-commands.md) erläutert die Standard Befehle, die von der-Klassenbibliothek definiert werden.

## <a name="see-also"></a>Siehe auch

[Benutzeroberflächenobjekte und Befehls-IDs](user-interface-objects-and-command-ids.md)

---
title: 'Gewusst wie: Aktualisieren von Benutzeroberflächenobjekten'
ms.date: 11/04/2016
helpviewer_keywords:
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- user interface objects [MFC]
- update handlers [MFC]
- enabling UI elements [MFC]
- disabling menus [MFC]
- updating user-interface objects [MFC]
- disabling UI elements [MFC]
- commands [MFC], updating UI
- enabling menus [MFC]
ms.assetid: 82f09773-c978-427b-b321-05a6143b7369
ms.openlocfilehash: aec4067a7b5854ef872cfcef19a15db8438dd795
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626388"
---
# <a name="how-to-update-user-interface-objects"></a>Gewusst wie: Aktualisieren von Benutzeroberflächenobjekten

Menü Elemente und Symbolleisten Schaltflächen verfügen in der Regel über mehr als einen Status. Beispielsweise ist ein Menü Element ausgegraut (abgeblendet), wenn es im aktuellen Kontext nicht verfügbar ist. Menü Elemente können auch überprüft oder deaktiviert werden. Eine Symbolleisten-Schaltfläche kann auch deaktiviert werden, wenn Sie nicht verfügbar ist, oder Sie kann aktiviert werden.

Wenn ein Menü Element einen Befehl generiert, der von (z. a. einem Dokument) bearbeitet wird, wird der Zustand dieser Elemente durch das logische ändern von Programmbedingungen aktualisiert, und das Dokument muss das Menü Element aktualisieren. Das Dokument enthält wahrscheinlich die Informationen, auf denen das Update basiert.

Wenn ein Befehl über mehrere Benutzeroberflächen Objekte (z. a. ein Menü Element und eine Symbolleisten Schaltfläche) verfügt, werden beide zur gleichen Handlerfunktion weitergeleitet. Dadurch wird der Code für die Benutzeroberflächen Aktualisierung für alle äquivalenten Benutzerschnittstellen Objekte an einer zentralen Stelle gekapselt.

Das Framework stellt eine bequeme Oberfläche für das automatische Aktualisieren von Benutzeroberflächen Objekten bereit. Sie können die Aktualisierung auf andere Weise durchführen, aber die bereitgestellte Schnittstelle ist effizient und einfach zu verwenden.

In den folgenden Themen wird die Verwendung von Update Handlern erläutert:

- [Wenn Update Handler aufgerufen werden](when-update-handlers-are-called.md)

- [Das ON_UPDATE_COMMAND_UI-Makro](on-update-command-ui-macro.md)

- [Die CCmdUI-Klasse](the-ccmdui-class.md)

## <a name="see-also"></a>Siehe auch

[Menüs](menus-mfc.md)

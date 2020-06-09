---
title: Behandeln von reflektierten Meldungen
ms.date: 11/04/2016
helpviewer_keywords:
- message handling [MFC], reflected messages
- reflected messages, handling
ms.assetid: 147a4e0c-51cc-4447-a8e1-c28b4cece578
ms.openlocfilehash: 8907b432cf4dabad33c0925b841f65dfc57c6295
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620142"
---
# <a name="handling-reflected-messages"></a>Behandeln von reflektierten Meldungen

Mithilfe der Nachrichten Reflektion können Sie Nachrichten für ein Steuerelement, z. b. **WM_CTLCOLOR**, **WM_COMMAND**und **WM_NOTIFY**, im Steuerelement selbst verarbeiten. Dadurch wird das Steuerelement eigenständig und portabel. Der Mechanismus funktioniert mit allgemeinen Windows-Steuerelementen und mit ActiveX-Steuerelementen (früher als OLE-Steuerelemente bezeichnet).

Mithilfe der Nachrichten Reflektion können Sie die von `CWnd` abgeleiteten Klassen leichter wieder verwenden. Die Nachrichten Reflektion funktioniert mithilfe von [CWnd:: OnChildNotify](reference/cwnd-class.md#onchildnotify)mithilfe spezieller **ON_XXX_REFLECT** Zuordnungs Einträge in der Nachricht, z. b. **ON_CTLCOLOR_REFLECT** und **ON_CONTROL_REFLECT**. [Technische Notiz 62](tn062-message-reflection-for-windows-controls.md) erläutert die Nachrichten Spiegelung ausführlicher.

## <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?

- [Weitere Informationen zur Nachrichten Reflektion](tn062-message-reflection-for-windows-controls.md)

- [Implementieren der Nachrichten Reflektion für ein gemeinsames Steuerelement](tn062-message-reflection-for-windows-controls.md)

- [Implementieren der Nachrichten Reflektion für ein ActiveX-Steuerelement](mfc-activex-controls-subclassing-a-windows-control.md)

## <a name="see-also"></a>Siehe auch

[Deklarieren von Meldungshandlerfunktionen](declaring-message-handler-functions.md)

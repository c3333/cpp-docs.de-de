---
title: 'OLE-Hintergrund: Implementierungsstrategien'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE [MFC], development strategy
- OLE applications [MFC], implementing OLE
- applications [OLE], implementing OLE
ms.assetid: 0875ddae-99df-488c-82c6-164074a81058
ms.openlocfilehash: 90517f9b37872dd7de0ce1a2d08da94c93e6f8f8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619900"
---
# <a name="ole-background-implementation-strategies"></a>OLE-Hintergrund: Implementierungsstrategien

Abhängig von Ihrer Anwendung gibt es vier mögliche Implementierungs Strategien zum Hinzufügen von OLE-Unterstützung:

- Sie schreiben eine neue Anwendung.

   Diese Situation erfordert in der Regel die geringste Arbeit. Sie führen den MFC-Anwendungs-Assistenten aus und wählen entweder erweiterte Features oder Verbund Dokument Unterstützung aus, um eine Skeleton-Anwendung zu erstellen. Informationen zu diesen Optionen und deren Funktionsumfang finden Sie im Artikel [Erstellen eines MFC-exe-Programms](reference/mfc-application-wizard.md).

- Sie verfügen über ein Programm, das mit dem Microsoft Foundation Class-Bibliothek Version 2,0 oder höher geschrieben wurde, das OLE nicht unterstützt.

   Erstellen Sie wie oben beschrieben eine neue Anwendung mit dem MFC-Anwendungs-Assistenten, kopieren Sie den Code, und fügen Sie ihn aus der neuen Anwendung in Ihre vorhandene Anwendung ein. Dies funktioniert bei Servern, Containern oder automatisierten Anwendungen. Ein Beispiel für diese Strategie finden Sie im MFC [Scribble](../overview/visual-cpp-samples.md) -Beispiel.

- Sie verfügen über ein Microsoft Foundation Class-Bibliothek Programm, das die Unterstützung der OLE-Version 1,0 implementiert.

   Weitere Informationen zu dieser Konvertierungs Strategie finden [Sie unter MFC Technical Note 41](tn041-mfc-ole1-migration-to-mfc-ole-2.md) .

- Sie verfügen über eine Anwendung, die nicht mit dem Microsoft Foundation Classes geschrieben wurde und die OLE-Unterstützung möglicherweise implementiert hat.

   Diese Situation erfordert die meiste Arbeit. Ein Ansatz besteht darin, eine neue Anwendung zu erstellen, wie in der ersten Strategie, und dann den vorhandenen Code zu kopieren und einzufügen. Wenn Ihr vorhandener Code in C geschrieben ist, müssen Sie ihn möglicherweise ändern, damit er als C++-Code kompiliert werden kann. Wenn Ihr C-Code die Windows-API aufruft, müssen Sie Sie nicht ändern, damit die Microsoft Foundation Classes verwendet werden kann. Dieser Ansatz erfordert möglicherweise eine Umstrukturierung Ihres Programms, um die Dokument-/Ansichtarchitektur zu unterstützen, die von den Versionen 2,0 und höher der Microsoft Foundation Classes verwendet wird. Weitere Informationen zu dieser Architektur finden Sie in der [technischen Notiz 25](tn025-document-view-and-frame-creation.md).

Nachdem Sie sich für eine Strategie entschieden haben, sollten Sie entweder die [Container](containers.md) -oder [Server](servers.md) Artikel lesen (abhängig vom Typ der Anwendung, die Sie schreiben) oder die Beispiel Programme überprüfen. Die MFC-OLE-Beispiele [OCLIENT](../overview/visual-cpp-samples.md) und [HIERSVR](../overview/visual-cpp-samples.md) veranschaulichen, wie die verschiedenen Aspekte von Containern bzw. Servern implementiert werden. An verschiedenen Punkten in diesen Artikeln werden Sie auf bestimmte Funktionen in diesen Beispielen als Beispiele für die beschriebenen Techniken verwiesen.

## <a name="see-also"></a>Siehe auch

[OLE-Hintergrund](ole-background.md)<br/>
[Container: Implementieren eines Containers](containers-implementing-a-container.md)<br/>
[Server: Implementieren eines Servers](servers-implementing-a-server.md)<br/>
[MFC-Anwendungs-Assistent](reference/mfc-application-wizard.md)

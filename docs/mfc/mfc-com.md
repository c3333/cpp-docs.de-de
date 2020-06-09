---
title: MFC COM
ms.date: 09/12/2018
f1_keywords:
- MFC COM (MFC)
helpviewer_keywords:
- MFC, COM support
- MFC ActiveX controls [MFC], COM support in MFC
- MFC COM [MFC]
- ActiveX controls [MFC], COM object model
- Active technology [MFC]
- COM [MFC], MFC support
ms.assetid: 7646bdcb-3a06-4ed5-9386-9b00f3979dcb
ms.openlocfilehash: da194510938e3fe02eba5993182e811fdf2e1b7c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618013"
---
# <a name="mfc-com"></a>MFC COM

Eine Teilmenge von MFC ist für die Unterstützung von com konzipiert, während die meisten Active Template Library (ATL) für die COM-Programmierung entwickelt wurden. In diesem Abschnitt von Themen wird die MFC-Unterstützung für com beschrieben.

Aktive Technologien (z. b. ActiveX-Steuerelemente, Active Document Containment, OLE usw.) verwenden die Component Object Model (com), damit Softwarekomponenten in einer Netzwerkumgebung interagieren können, unabhängig von der Sprache, mit der Sie erstellt wurden. Aktive Technologien können verwendet werden, um Anwendungen zu erstellen, die auf dem Desktop oder im Internet ausgeführt werden. Weitere Informationen finden [Sie unter Einführung in com](../atl/introduction-to-com.md) oder [die Component Object Model](/windows/win32/com/the-component-object-model).

Zu den aktiven Technologien zählen sowohl Client-als auch Server Technologien, einschließlich der folgenden:

- ActiveX-Steuerelemente sind interaktive Objekte, die in Containern wie z. b. einer Website verwendet werden können. Weitere Informationen zu ActiveX-Steuerelementen finden Sie unter:

  - [MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)

  - [ActiveX-Steuerelemente für das Internet](activex-controls-on-the-internet.md)

  - [Übersicht: Internet](mfc-internet-programming-basics.md)

  - [Aktualisieren eines vorhandenen ActiveX-Steuer Elements für die Verwendung im Internet](upgrading-an-existing-activex-control.md)

  - [Debugging eines ActiveX-Steuer Elements](/visualstudio/debugger/how-to-debug-an-activex-control)

- Active Scripting steuert das integrierte Verhalten von mindestens einem ActiveX-Steuerelement von einem Browser oder Server aus. Weitere Informationen zur aktiven Skripterstellung finden Sie unter [aktive Technologie im Internet](active-technology-on-the-internet.md).

- [Automation](automation.md) (früher als OLE-Automatisierung bezeichnet) ermöglicht es einer Anwendung, die in einer anderen Anwendung implementierten Objekte zu bearbeiten oder Objekte verfügbar zu machen, sodass Sie bearbeitet werden können.

   Das automatisierte Objekt kann lokal oder Remote sein (auf einem anderen Computer, auf den über ein Netzwerk zugegriffen werden kann). Automation ist für OLE und COM-Objekte verfügbar.

- In diesem Abschnitt finden Sie auch Informationen zum Schreiben von COM-Komponenten mithilfe von MFC, z. b. in [Verbindungs Punkten](connection-points.md).

Eine Erläuterung dazu, was noch als OLE bezeichnet wird und was jetzt als "aktive Technologie" bezeichnet wird, finden Sie in den Themen zu [OLE](ole-in-mfc.md).

## <a name="in-this-section"></a>In diesem Abschnitt

[Active Document-Container](active-document-containment.md)

[Automation](automation.md)

[Verbindungspunkte](connection-points.md)

[MFC-ActiveX-Steuerelemente](mfc-activex-controls.md)

## <a name="see-also"></a>Siehe auch

[Konzepte](mfc-concepts.md)

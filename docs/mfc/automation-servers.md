---
title: Automatisierungsserver
ms.date: 11/04/2016
helpviewer_keywords:
- Automation servers
- COM components, Automation servers
- dispatch maps [MFC], Automation servers
- servers, Automation
ms.assetid: 523fd155-51ce-4f91-b986-b74bdbdd7d92
ms.openlocfilehash: 391cb2f6ff5673296f40e21113e3a6510f71d475
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370841"
---
# <a name="automation-servers"></a>Automatisierungsserver

Die Automatisierung ermöglicht es Ihrer Anwendung, Objekte zu bearbeiten, die in einer anderen Anwendung implementiert wurden, oder Objekte verfügbar zu machen, damit sie bearbeitet werden können. Ein Automatisierungsserver ist eine Anwendung, die programmierbare Objekte (so genannte Automatisierungsobjekte) für andere Anwendungen verfügbar macht (so genannte [Automatisierungsclients](../mfc/automation-clients.md)). Automatisierungsserver werden manchmal als Automatisierungskomponenten bezeichnet.

Durch das Verfügbarmachen von Automatisierungsobjekten können Clients bestimmte Prozeduren automatisieren, indem sie direkt auf die vom Server zur Verfügung gestellten Objekte und Funktionen zugreifen. Das Aufstellen von Objekten auf diese Weise ist von Vorteil, wenn Anwendungen Funktionen bereitstellen, die für andere Anwendungen nützlich sind. Beispielsweise kann ein Textverarbeitungsprogramm seine Rechtschreibprüfungsfunktionalität verfügbar machen, damit andere Programme sie verwenden können. Die Belichtung von Objekten ermöglicht es Anbietern, die Funktionalität ihrer Anwendungen durch die Verwendung der vorgefertigten Funktionalität anderer Anwendungen zu verbessern.

Diese Automatisierungsobjekte verfügen über Eigenschaften und Methoden als externe Schnittstelle. Eigenschaften sind benannte Attribute des Automation-Objekts. Eigenschaften ähneln den Datenmembern einer C++-Klasse. Methoden sind Funktionen, die an Automatisierungsobjekten arbeiten. Methoden ähneln den öffentlichen Memberfunktionen einer C++-Klasse.

> [!NOTE]
> Obwohl Eigenschaften wie C++-Datenmember sind, sind sie nicht direkt zugänglich. Um einen transparenten Zugriff zu ermöglichen, richten Sie eine interne Variable im Automation-Objekt mit einem Paar von get/set-Memberfunktionen ein, um darauf zuzugreifen.

Durch die Bereitstellung von Anwendungsfunktionen über eine gemeinsame, klar definierte Schnittstelle ermöglicht Automation das Erstellen von Anwendungen in einer einzigen allgemeinen Programmiersprache wie Microsoft Visual Basic anstelle in verschiedenen, anwendungsspezifischen Makrosprachen.

## <a name="support-for-automation-servers"></a><a name="_core_support_for_automation_servers"></a>Unterstützung für Automatisierungsserver

Visual C++ und das MFC-Framework bieten umfassende Unterstützung für Automatisierungsserver. Sie übernehmen einen Großteil des Aufwands, der mit der Erstellung eines Automatisierungsservers verbunden ist, sodass Sie sich auf die Funktionalität Ihrer Anwendung konzentrieren können.

Der Hauptmechanismus des Frameworks zur Unterstützung von Automation ist die Dispatchzuordnung, eine Gruppe von Makros, die in die Deklarationen und Aufrufe erweitert wird, die zum Verfügbarmachen von Methoden und Eigenschaften für OLE erforderlich sind. Eine typische Dispatch-Map sieht wie folgt aus:

[!code-cpp[NVC_MFCAutomation#1](../mfc/codesnippet/cpp/automation-servers_1.cpp)]

Der [Klassen-Assistent](reference/mfc-class-wizard.md) und die Klassenansicht unterstützen die Verwaltung von Dispatchkarten. Wenn Sie einer Klasse eine neue Methode oder Eigenschaft `DISP_FUNCTION` `DISP_PROPERTY` hinzufügen, fügt Visual Studio ein entsprechendes Oder Makro mit Parametern hinzu, die den Klassennamen, die externen und internen Namen der Methode oder Eigenschaft sowie Datentypen angeben.

Das Dialogfeld **Klassen hinzufügen** vereinfacht auch die Deklaration von Automatisierungsklassen und die Verwaltung ihrer Eigenschaften und Vorgänge. Wenn Sie das Dialogfeld Klassen hinzufügen verwenden, um dem Projekt eine Klasse hinzuzufügen, geben Sie dessen Basisklasse an. Wenn die Basisklasse Automatisierung zulässt, zeigt das Dialogfeld Klassen hinzufügen Steuerelemente an, mit denen Sie angeben, ob die neue Klasse Automation unterstützen soll, ob es sich um "OLE-Creatable" (d. h. ob Objekte der Klasse auf einer Anforderung von einem COM-Client erstellt werden können) und den externen Namen für den zu verwendenden COM-Client anzeigt.

Im Dialogfeld **Klassen** hinzufügen wird dann eine Klassendeklaration erstellt, einschließlich der entsprechenden Makros für die von Ihnen angegebenen OLE-Features. Außerdem wird der Skelettcode für die Implementierung der Memberfunktionen Ihrer Klasse hinzugefügt.

Der MFC-Anwendungs-Assistent vereinfacht die Schritte, die erforderlich sind, um Ihre Automatisierungsserveranwendung auf den Weg zu bringen. Wenn Sie auf der Seite **Erweiterte Funktionen** das Kontrollkästchen **Automatisierung** aktivieren, fügt `InitInstance` der MFC-Anwendungs-Assistent der Funktion Ihrer Anwendung die Aufrufe hinzu, die zum Registrieren Ihrer Automatisierungsobjekte und Ausführen ihrer Anwendung als Automatisierungsserver erforderlich sind.

### <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?

- [Erfahren Sie mehr über Automation-Clients](../mfc/automation-clients.md)

- [Erfahren Sie mehr über klasse CCmdTarget](../mfc/reference/ccmdtarget-class.md)

- [Weitere Informationen zur Klasse COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)

## <a name="see-also"></a>Siehe auch

[Automation](../mfc/automation.md)<br/>
[MFC-Anwendungs-Assistent](../mfc/reference/mfc-application-wizard.md)

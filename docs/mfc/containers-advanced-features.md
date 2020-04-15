---
title: 'Container: Erweiterte Funktionen'
ms.date: 11/04/2016
helpviewer_keywords:
- links [MFC], to embedded OLE objects
- containers [MFC], links to embedded OLE objects
- containers [MFC], advanced features
- container/server applications [MFC]
- embedded objects [MFC]
- OLE controls [MFC], containers
- OLE containers [MFC], advanced features
- server/container applications [MFC]
- containers [MFC], container applications
ms.assetid: 221fd99c-b138-40fa-ad6a-974e3b3ad1f8
ms.openlocfilehash: cf130bf8dead5c59548821658b979785c4d54726
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376494"
---
# <a name="containers-advanced-features"></a>Container: Erweiterte Funktionen

In diesem Artikel werden die Schritte beschrieben, die erforderlich sind, um optionale erweiterte Funktionen in vorhandene Containeranwendungen zu integrieren. Diese Funktionen sind:

- [Eine Anwendung, die sowohl ein Container als auch ein Server ist](#_core_creating_a_container_server_application)

- [Eine OLE-Verknüpfung zu einem eingebetteten Objekt](#_core_links_to_embedded_objects)

## <a name="creating-a-containerserver-application"></a><a name="_core_creating_a_container_server_application"></a>Erstellen einer Container/Server-Anwendung

Eine Container-/Serveranwendung ist eine Anwendung, die sowohl als Container als auch als Server fungiert. Microsoft Word für Windows ist ein Beispiel dafür. Sie können Word für Windows-Dokumente in andere Anwendungen einbetten und Elemente auch in Word für Windows-Dokumente einbetten. Der Prozess zum Ändern der Containeranwendung als Container und vollständiger Server (Sie können keine Kombinationscontainer-/Miniserveranwendung erstellen) ähnelt dem Prozess zum Erstellen eines vollständigen Servers.

Der Artikel [Server: Implementieren eines Servers](../mfc/servers-implementing-a-server.md) listet eine Reihe von Aufgaben auf, die zum Implementieren einer Serveranwendung erforderlich sind. Wenn Sie eine Containeranwendung in eine Container-/Serveranwendung konvertieren, müssen Sie einige der gleichen Aufgaben ausführen und dem Container Code hinzufügen. Im Folgenden sind die wichtigen Punkte aufgeführt, die Zu beachten sind:

- Der vom Anwendungs-Assistenten erstellte Containercode initialisiert bereits das OLE-Subsystem. Sie müssen nichts für diese Unterstützung ändern oder hinzufügen.

- Unabhängig davon, wo sich `COleDocument`die Basisklasse einer `COleServerDoc`Dokumentklasse befindet, ändern Sie die Basisklasse in .

- Überschreiben, `COleClientItem::CanActivate` um zu vermeiden, dass Elemente bearbeitet werden, während der Server selbst zum Bearbeiten verwendet wird.

   Beispielsweise hat das MFC OLE-Beispiel [OCLIENT](../overview/visual-cpp-samples.md) ein Element eingebettet, das von Ihrer Container-/Serveranwendung erstellt wurde. Sie öffnen die OCLIENT-Anwendung und bearbeiten das von Ihrer Container/Server-Anwendung erstellte Element. Beim Bearbeiten des Anwendungselements entscheiden Sie, dass Sie ein Element einbetten möchten, das vom MFC OLE-Beispiel [HIERSVR](../overview/visual-cpp-samples.md)erstellt wurde. Dazu können Sie keine Ortsaktivierung verwenden. Sie müssen HIERSVR vollständig öffnen, um dieses Element zu aktivieren. Da die Microsoft Foundation-Klassenbibliothek diese OLE-Funktion nicht unterstützt, können Sie durch das Überschreiben `COleClientItem::CanActivate` nach dieser Situation suchen und einen möglichen Laufzeitfehler in Ihrer Anwendung verhindern.

Wenn Sie eine neue Anwendung erstellen und möchten, dass sie als Container-/Serveranwendung funktioniert, wählen Sie diese Option im Dialogfeld OLE-Optionen im Anwendungsassistenten aus, und diese Unterstützung wird automatisch erstellt. Weitere Informationen finden Sie im Artikel [Übersicht: Erstellen eines ActiveX-Steuerelementcontainers](../mfc/reference/creating-an-mfc-activex-control-container.md). Informationen zu MFC-Beispielen finden Sie unter [MFC-Beispiele](../overview/visual-cpp-samples.md#mfc-samples).

Beachten Sie, dass Sie keine MDI-Anwendung in sich selbst einfügen können. Eine Anwendung, die ein Container/Server ist, kann nur in sich selbst eingefügt werden, wenn es sich um eine SDI-Anwendung handelt.

## <a name="links-to-embedded-objects"></a><a name="_core_links_to_embedded_objects"></a>Links zu eingebetteten Objekten

Mit der Funktion Links zu eingebetteten Objekten kann ein Benutzer ein Dokument mit einer OLE-Verknüpfung zu einem eingebetteten Objekt in der Containeranwendung erstellen. Erstellen Sie beispielsweise ein Dokument in einem Textverarbeitungsprogramm, das eine eingebettete Kalkulationstabelle enthält. Wenn Ihre Anwendung Links zu eingebetteten Objekten unterstützt, kann sie einen Link zur Kalkulationstabelle einfügen, die im Dokument des Textverarbeitungsauftrags enthalten ist. Diese Funktion ermöglicht es Ihrer Anwendung, die in der Kalkulationstabelle enthaltenen Informationen zu verwenden, ohne zu wissen, wo der Textverarbeitungsprogramm sie ursprünglich erhalten hat.

#### <a name="to-link-to-embedded-objects-in-your-application"></a>So verknüpfen Sie eingebettete Objekte in Ihrer Anwendung

1. Leiten Sie Ihre `COleLinkingDoc` Dokumentklasse `COleDocument`von anstelle von ab.

1. Erstellen Sie eine OLE-Klassen-ID (**CLSID**) für Ihre Anwendung, indem Sie den Klassen-ID-Generator verwenden, der in den OLE-Entwicklungstools enthalten ist.

1. Registrieren Sie die Anwendung bei OLE.

1. Erstellen `COleTemplateServer` Sie ein Objekt als Member Ihrer Anwendungsklasse.

1. Gehen Sie in `InitInstance` der Memberfunktion Ihrer Anwendungsklasse wie folgt vor:

   - Verbinden `COleTemplateServer` Sie das Objekt mit den Dokumentvorlagen, indem Sie die Memberfunktion des Objekts `ConnectTemplate` aufrufen.

   - Rufen `COleTemplateServer::RegisterAll` Sie die Memberfunktion auf, um alle Klassenobjekte beim OLE-System zu registrieren.

   - Rufen Sie `COleTemplateServer::UpdateRegistry` auf. Der einzige `UpdateRegistry` Parameter sollte *OAT_CONTAINER* werden, wenn die Anwendung nicht mit dem Schalter "/Embedded" gestartet wird. Dadurch wird die Anwendung als Container registriert, der Links zu eingebetteten Objekten unterstützen kann.

      Wenn die Anwendung mit dem Schalter "/Embedded" gestartet wird, sollte sie ihr Hauptfenster nicht anzeigen, ähnlich einer Serveranwendung.

Das MFC OLE-Beispiel [OCLIENT](../overview/visual-cpp-samples.md) implementiert diese Funktion. Ein Beispiel dafür finden Sie in `InitInstance` der Funktion im *OCLIENT. CPP-Datei* dieser Beispielanwendung.

## <a name="see-also"></a>Siehe auch

[Container](../mfc/containers.md)<br/>
[Server](../mfc/servers.md)

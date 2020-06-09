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
ms.openlocfilehash: 1ef4ed9865d3a88a6ff85f777984b856d03cc48e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616359"
---
# <a name="containers-advanced-features"></a>Container: Erweiterte Funktionen

In diesem Artikel werden die Schritte beschrieben, die erforderlich sind, um optionale erweiterte Funktionen in vorhandene Container Anwendungen einzubinden. Diese Features sind:

- [Eine Anwendung, bei der es sich um einen Container und einen Server handelt](#_core_creating_a_container_server_application)

- [Einen OLE-Link zu einem eingebetteten Objekt](#_core_links_to_embedded_objects)

## <a name="creating-a-containerserver-application"></a><a name="_core_creating_a_container_server_application"></a>Erstellen einer Container-/Serveranwendung

Eine Container-/Serveranwendung ist eine Anwendung, die sowohl als Container als auch als Server fungiert. Microsoft Word für Windows ist ein Beispiel dafür. Sie können Word für Windows-Dokumente in andere Anwendungen einbetten und auch Elemente in Word für Windows-Dokumente einbetten. Der Prozess zum Ändern der Containeranwendung in einen Container und einen vollständigen Server (Sie können keine Kombination aus Container/Miniserver-Anwendung erstellen) ähnelt dem Verfahren zum Erstellen eines vollständigen Servers.

Der Artikel [Server: Implementieren eines Servers](servers-implementing-a-server.md) listet eine Reihe von Aufgaben auf, die zum Implementieren einer Serveranwendung erforderlich sind. Wenn Sie eine Containeranwendung in eine Container-/Serveranwendung konvertieren, müssen Sie einige dieser Aufgaben ausführen und dem Container Code hinzufügen. Im folgenden sind wichtige Aspekte aufgeführt, die beachtet werden sollten:

- Der vom Anwendungs-Assistenten erstellte Container Code initialisiert bereits das OLE-Subsystem. Sie müssen für diese Unterstützung nichts ändern oder hinzufügen.

- Wenn die Basisklasse einer Dokument Klasse ist `COleDocument` , ändern Sie die Basisklasse in `COleServerDoc` .

- Außer Kraft Setzung `COleClientItem::CanActivate` , um zu vermeiden, dass Elemente an Ort und Stelle bearbeitet werden, während der Server selbst zur direkten Bearbeitung verwendet wird.

   Beispielsweise hat das MFC-OLE-Beispiel [OCLIENT](../overview/visual-cpp-samples.md) ein Element eingebettet, das von ihrer Container-/Serveranwendung erstellt wurde. Öffnen Sie die OCLIENT-Anwendung, und bearbeiten Sie das Element, das von ihrer Container-/Serveranwendung erstellt wurde. Wenn Sie das Element der Anwendung bearbeiten, legen Sie fest, dass Sie ein Element einbetten möchten, das von der MFC-OLE-Beispiel [Hierarchie](../overview/visual-cpp-samples.md)erstellt wurde. Zu diesem Zweck können Sie keine direkte Aktivierung verwenden. Sie müssen HIERSVR vollständig öffnen, um dieses Element zu aktivieren. Da das Microsoft Foundation Class-Bibliothek diese OLE-Funktion nicht unterstützt, `COleClientItem::CanActivate` können Sie mit überschreiben diese Situation überprüfen und einen möglichen Laufzeitfehler in der Anwendung verhindern.

Wenn Sie eine neue Anwendung erstellen und diese als Container-/Serveranwendung fungieren möchten, wählen Sie diese Option im Dialogfeld OLE-Optionen im Anwendungs-Assistenten aus, und diese Unterstützung wird automatisch erstellt. Weitere Informationen finden Sie im Artikel [Übersicht: Erstellen eines ActiveX-Steuerelement Containers](reference/creating-an-mfc-activex-control-container.md). Weitere Informationen zu MFC-Beispielen finden Sie unter [MFC-Beispiele](../overview/visual-cpp-samples.md#mfc-samples).

Beachten Sie, dass eine MDI-Anwendung nicht in sich selbst eingefügt werden kann. Eine Anwendung, die ein Container/Server ist, kann nur in sich selbst eingefügt werden, wenn es sich um eine SDI-Anwendung handelt.

## <a name="links-to-embedded-objects"></a><a name="_core_links_to_embedded_objects"></a>Links zu eingebetteten Objekten

Mithilfe der Funktion "Links zu eingebetteten Objekten" kann ein Benutzer ein Dokument mit einem OLE-Link zu einem eingebetteten Objekt in ihrer Containeranwendung erstellen. Erstellen Sie z. b. ein Dokument in einem Textverarbeitungs Tool, das eine eingebettete Tabelle enthält. Wenn Ihre Anwendung Links zu eingebetteten Objekten unterstützt, könnte Sie einen Link in das Arbeitsblatt einfügen, das im Dokument des Textprozessors enthalten ist. Diese Funktion ermöglicht es der Anwendung, die in der Tabelle enthaltenen Informationen zu verwenden, ohne zu wissen, wo der Textprozessor Sie ursprünglich erhalten hat.

#### <a name="to-link-to-embedded-objects-in-your-application"></a>So verknüpfen Sie eine Verknüpfung mit eingebetteten Objekten in der Anwendung

1. Leiten Sie die Dokument Klasse von `COleLinkingDoc` anstelle von ab `COleDocument` .

1. Erstellen Sie eine OLE Class ID (**CLSID**) für Ihre Anwendung, indem Sie den Klassen-ID-Generator verwenden, der in den OLE-Entwicklungs Tools enthalten ist.

1. Registrieren Sie die Anwendung bei OLE.

1. Erstellen Sie ein- `COleTemplateServer` Objekt als Member Ihrer Anwendungsklasse.

1. Führen Sie in der Member-Funktion Ihrer Anwendungsklasse `InitInstance` die folgenden Schritte aus:

   - Verbinden Sie Ihr `COleTemplateServer` Objekt mit den Dokumentvorlagen, indem Sie die Member-Funktion des Objekts aufrufen `ConnectTemplate` .

   - Ruft die `COleTemplateServer::RegisterAll` Member-Funktion auf, um alle Klassen Objekte beim OLE-System zu registrieren.

   - Rufen Sie `COleTemplateServer::UpdateRegistry` auf. Der einzige Parameter für `UpdateRegistry` sollte *OAT_CONTAINER* sein, wenn die Anwendung nicht mit dem Schalter "/Embedded" gestartet wird. Dadurch wird die Anwendung als Container registriert, der Links zu eingebetteten Objekten unterstützen kann.

      Wenn die Anwendung mit dem Schalter "/Embedded" gestartet wird, sollte das Hauptfenster, ähnlich einer Serveranwendung, nicht angezeigt werden.

Das MFC-OLE-Beispiel [OCLIENT](../overview/visual-cpp-samples.md) implementiert diese Funktion. Ein Beispiel dafür finden Sie unter der- `InitInstance` Funktion in *OCLIENT. Cpp* -Datei dieser Beispielanwendung.

## <a name="see-also"></a>Siehe auch

[Container](containers.md)<br/>
[Server](servers.md)

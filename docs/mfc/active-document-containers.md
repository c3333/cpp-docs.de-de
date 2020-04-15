---
title: Active Document-Container
ms.date: 11/19/2018
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
ms.openlocfilehash: e2005ffed592fa1de278e0f6339d94687a20fd06
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377388"
---
# <a name="active-document-containers"></a>Active Document-Container

Mit einem aktiven Dokumentcontainer, z. B. Microsoft Office Binder oder Internet Explorer, können Sie mit mehreren Dokumenten unterschiedlicher Anwendungstypen innerhalb eines einzelnen Frames arbeiten (anstatt Sie zum Erstellen und Verwenden mehrerer Anwendungsframes für jeden Dokumenttyp zu zwingen).

MFC bietet vollständige Unterstützung für `COleDocObjectItem` aktive Dokumentcontainer in der Klasse. Sie können den MFC-Anwendungs-Assistenten verwenden, um einen aktiven Dokumentcontainer zu erstellen, indem Sie das Kontrollkästchen **Aktiver Dokumentcontainer** auf der Seite **"Unterstützung für zusammengesetzte Dokumente"** des MFC-Anwendungs-Assistenten aktivieren. Weitere Informationen finden Sie unter [Erstellen einer Active Document Container Application](../mfc/creating-an-active-document-container-application.md).

Weitere Informationen zu aktiven Dokumentcontainern finden Sie unter:

- [Container-Anforderungen](#container_requirements)

- [Dokumentwebsiteobjekte](#document_site_objects)

- [Websiteobjekte anzeigen](#view_site_objects)

- [Rahmenobjekt](#frame_object)

- [Verschachteln des Hilfemenüs](../mfc/help-menu-merging.md)

- [Programmgesteuertes Drucken](../mfc/programmatic-printing.md)

- [Befehlsziele](../mfc/message-handling-and-command-targets.md)

## <a name="container-requirements"></a><a name="container_requirements"></a>Container-Anforderungen

Aktive Dokumentunterstützung in einem aktiven Dokumentcontainer bedeutet mehr als nur Schnittstellenimplementierungen: Es erfordert auch Kenntnisse über die Verwendung der Schnittstellen eines enthaltenen Objekts. Dasselbe gilt für aktive Dokumenterweiterungen, bei denen der Container auch wissen muss, wie diese Erweiterungsschnittstellen in den aktiven Dokumenten selbst verwendet werden.

Ein aktiver Dokumentcontainer, der aktive Dokumente integriert, muss:

- In der Lage sein, `IPersistStorage` Objektspeicher über die Schnittstelle `IStorage` zu verarbeiten, d. h., es muss eine Instanz für jedes aktive Dokument bereitstellen.

- Unterstützen Sie die grundlegenden Einbettungsfunktionen von OLE-Dokumenten, die "Site"-Objekte (eine pro Dokument oder Einbettung) erfordern, die implementiert `IOleClientSite` und `IAdviseSink`.

- Unterstützen Sie die ortsspezifische Aktivierung eingebetteter Objekte oder aktiver Dokumente. Die Standortobjekte des Containers `IOleInPlaceSite` müssen implementiert werden, und `IOleInPlaceFrame`das Frameobjekt des Containers muss bereitstellen.

- Unterstützen Sie die Erweiterungen `IOleDocumentSite` der aktiven Dokumente, indem Sie den Mechanismus implementieren, mit dem der Container mit dem Dokument sprechen kann. Optional kann der Container die aktiven `IOleCommandTarget` Dokumentschnittstellen implementieren und `IContinueCallback` einfache Befehle wie Drucken oder Speichern aufnehmen.

Das Frameobjekt, die Ansichtsobjekte und das `IOleCommandTarget` Containerobjekt können optional implementiert werden, um das Senden bestimmter Befehle zu unterstützen, wie unter [Befehlsziele](../mfc/message-handling-and-command-targets.md)erläutert. View- und Containerobjekte können `IPrint` `IContinueCallback`optional auch implementieren und zur Unterstützung des programmgesteuerten Druckens, wie in [Programmatic Printing](../mfc/programmatic-printing.md)erläutert.

Die folgende Abbildung zeigt die konzeptionellen Beziehungen zwischen einem Container und seinen Komponenten (links) und dem aktiven Dokument und seinen Ansichten (rechts). Das aktive Dokument verwaltet Speicher und Daten, und die Ansicht zeigt diese Daten an oder druckt sie optional. Schnittstellen in Fettdruck sind diejenigen, die für die aktive Teilnahme an Dokumenten erforderlich sind; die fett und kursiv sind optional. Alle anderen Schnittstellen sind erforderlich.

![Schnittstellen des Containers für das aktive Dokument](../mfc/media/vc37gj1.gif "Schnittstellen des Containers für das aktive Dokument")

Ein Dokument, das nur eine einzelne Ansicht unterstützt, kann sowohl die Ansichts- als auch die Dokumentkomponenten (d. h. die entsprechenden Schnittstellen) für eine einzelne Konkreteklasse implementieren. Darüber hinaus kann eine Containersite, die jeweils nur eine Ansicht unterstützt, die Dokumentwebsite und die Ansichtssite in einer einzelnen konkreten Standortklasse kombinieren. Das Frameobjekt des Containers muss jedoch getrennt bleiben, und die Dokumentkomponente des Containers ist hier lediglich enthalten, um ein vollständiges Bild der Architektur zu erhalten. Sie wird von der aktiven Dokumentbeschränkungsarchitektur nicht beeinflusst.

## <a name="document-site-objects"></a><a name="document_site_objects"></a>Dokumentwebsiteobjekte

In der aktiven Dokumentbeschränkungsarchitektur ist eine Dokumentwebsite mit einem Clientwebsiteobjekt in `IOleDocument` OLE-Dokumenten identisch, wobei die Schnittstelle hinzugefügt wird:

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

Die Dokumentwebsite ist konzeptionell der Container für ein oder mehrere "Ansichtssite"-Objekte. Jedes Ansichtswebsiteobjekt ist einzelnen Ansichtsobjekten des Dokuments zugeordnet, das von der Dokumentwebsite verwaltet wird. Wenn der Container nur eine einzelne Ansicht pro Dokumentsite unterstützt, kann er die Dokumentwebsite und die Ansichtssite mit einer einzelnen Betonklasse implementieren.

## <a name="view-site-objects"></a><a name="view_site_objects"></a>Websiteobjekte anzeigen

Das Ansichtswebsiteobjekt eines Containers verwaltet den Anzeigebereich für eine bestimmte Ansicht eines Dokuments. Neben der Unterstützung `IOleInPlaceSite` der Standardschnittstelle wird eine `IContinueCallback` View-Site in der Regel auch für die programmgesteuerte Drucksteuerung implementiert. (Beachten Sie, dass das `IContinueCallback` Ansichtsobjekt nie nachfragt, sodass es tatsächlich für jedes Objekt implementiert werden kann, das der Container wünscht.)

Ein Container, der mehrere Ansichten unterstützt, muss in der Lage sein, mehrere Ansichtswebsiteobjekte innerhalb der Dokumentwebsite zu erstellen. Dadurch erhalten Sie für jede Ansicht separate `IOleInPlaceSite`Aktivierungs- und Deaktivierungsdienste, wie sie über bereitgestellt werden.

## <a name="frame-object"></a><a name="frame_object"></a>Frame-Objekt

Das Frameobjekt des Containers ist zum größten Teil derselbe Frame, der für die ortsspezifische Aktivierung in OLE-Dokumenten verwendet wird, d. h. der Frame, der die Aushandlung von Menü s. Und Symbolleisten behandelt. Ein Ansichtsobjekt hat Zugriff `IOleInPlaceSite::GetWindowContext`auf dieses Frameobjekt über , das auch Zugriff auf das Containerobjekt bietet, das das Containerdokument darstellt (das die Werkzeugleistenaushandlung auf Bereichsebene und die enthaltene Objektenumeration verarbeiten kann).

Ein aktiver Dokumentcontainer kann den `IOleCommandTarget`Frame durch Hinzufügen von erweitern. Auf diese Weise kann es Befehle empfangen, die in der Benutzeroberfläche des aktiven Dokuments auf die gleiche Weise stammen, wie diese Schnittstelle es einem Container ermöglichen kann, dieselben Befehle zu senden (z. B. **Datei neu**, **Öffnen**, **Speichern unter**, **Drucken**; **Bearbeiten Sie Kopieren**, **Einfügen**, **Rückgängig**machen und andere) in ein aktives Dokument. Weitere Informationen finden Sie unter [Befehlsziele](../mfc/message-handling-and-command-targets.md).

## <a name="see-also"></a>Siehe auch

[Active Document-Container](../mfc/active-document-containment.md)

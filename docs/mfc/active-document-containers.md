---
title: Active Document-Container
ms.date: 11/19/2018
helpviewer_keywords:
- active documents [MFC], containers
- active document containers [MFC]
- containers [MFC], active document
- MFC COM, active document containment
ms.assetid: ba20183a-8b4c-440f-9031-e5fcc41d391b
ms.openlocfilehash: dc7017a205bedd716e5c87aa23ac96b257af2e16
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626022"
---
# <a name="active-document-containers"></a>Active Document-Container

Ein aktiver Dokument Container (z. b. Microsoft Office Binder oder Internet Explorer) ermöglicht Ihnen das Arbeiten mit mehreren Dokumenten verschiedener Anwendungs Typen innerhalb eines einzelnen Frames (anstatt mehrere Anwendungs Frames für jeden Dokumenttyp zu erstellen und zu verwenden).

MFC bietet vollständige Unterstützung für aktive Dokument Container in der- `COleDocObjectItem` Klasse. Mithilfe des MFC-Anwendungs-Assistenten können Sie einen aktiven Dokument Container erstellen, indem Sie auf der Seite **Unterstützung für Verbund Dokumente** des MFC-Anwendungs-Assistenten das Kontrollkästchen **aktiver Dokument Container** auswählen. Weitere Informationen finden Sie unter [Erstellen einer Container Anwendung für aktive Dokumente](creating-an-active-document-container-application.md).

Weitere Informationen über aktive Dokument Container finden Sie unter:

- [Container Anforderungen](#container_requirements)

- [Dokument Standort Objekte](#document_site_objects)

- [Anzeigen von Standort Objekten](#view_site_objects)

- [Rahmenobjekt](#frame_object)

- [Verschachteln des Hilfemenüs](help-menu-merging.md)

- [Programmgesteuertes Drucken](programmatic-printing.md)

- [Befehlsziele](message-handling-and-command-targets.md)

## <a name="container-requirements"></a><a name="container_requirements"></a>Container Anforderungen

Die Unterstützung aktiver Dokumente in einem aktiven Dokument Container impliziert mehr als nur Schnittstellen Implementierungen: Sie erfordert auch Kenntnisse in der Verwendung der Schnittstellen eines enthaltenen Objekts. Das gleiche gilt für aktive Dokument Erweiterungen, bei denen der Container auch wissen muss, wie diese Erweiterungs Schnittstellen in den aktiven Dokumenten selbst verwendet werden.

Ein aktiver Dokument Container, der aktive Dokumente integriert, muss folgende Aktionen ausführen:

- Sie können den Objektspeicher über die- `IPersistStorage` Schnittstelle verarbeiten, d. h., Sie müssen `IStorage` jedem aktiven Dokument eine-Instanz bereitstellen.

- Unterstützung der grundlegenden Einbettungs Funktionen von OLE-Dokumenten, die das "Site"-Objekt (eines pro Dokument oder Einbettungs Funktion) erfordern, das `IOleClientSite` und implementiert `IAdviseSink` .

- Unterstützung der direkten Aktivierung von eingebetteten Objekten oder aktiven Dokumenten. Die Site Objekte des Containers müssen implementieren, `IOleInPlaceSite` und das Frame-Objekt des Containers muss bereitstellen `IOleInPlaceFrame` .

- Unterstützen Sie die Erweiterungen der aktiven Dokumente `IOleDocumentSite` , indem Sie implementieren, um den Mechanismus bereitzustellen, mit dem der Container mit dem Dokument kommunizieren soll. Optional kann der Container die aktiven Dokument Schnittstellen implementieren `IOleCommandTarget` und `IContinueCallback` einfache Befehle, z. b. Drucken oder speichern, abrufen.

Das Frame-Objekt, die Ansichts Objekte und das Container Objekt können optional implementiert `IOleCommandTarget` werden, um die Verteilung bestimmter Befehle zu unterstützen, wie in den [Befehls Zielen](message-handling-and-command-targets.md)erläutert. Sicht-und Containerobjekte können optional auch `IPrint` und implementieren `IContinueCallback` , um programmgesteuerte Druckunterstützung zu unterstützen, wie Unterprogramm gesteuertes [Drucken](programmatic-printing.md)erläutert.

In der folgenden Abbildung werden die konzeptionellen Beziehungen zwischen einem Container und seinen Komponenten (auf der linken Seite) sowie dem aktiven Dokument und seinen Ansichten (auf der rechten Seite) gezeigt. Das aktive Dokument verwaltet den Speicher und die Daten, und die Sicht zeigt diese Daten an oder druckt Sie optional. Fett formatierte Schnittstellen sind die für die aktive Dokument Teilnahme erforderlichen. Diese Fett und kursiv sind optional. Alle anderen Schnittstellen sind erforderlich.

![Schnittstellen des Containers für das aktive Dokument](../mfc/media/vc37gj1.gif "Schnittstellen des Containers für das aktive Dokument")

Ein Dokument, das nur eine einzige Ansicht unterstützt, kann sowohl die Ansichts-als auch die Dokument Komponente (d. h. die zugehörigen Schnittstellen) für eine einzelne konkrete Klasse implementieren. Außerdem kann eine Container Site, die nur jeweils eine Ansicht unterstützt, den Dokument Standort und den Ansichts Standort in einer einzelnen konkreten Standort Klasse kombinieren. Das Frame Objekt des Containers muss jedoch unterschiedlich bleiben, und die Dokument Komponente des Containers ist nur hier enthalten, um ein umfassendes Bild der Architektur zu erhalten. die aktive Dokument Kapselungs Architektur ist nicht betroffen.

## <a name="document-site-objects"></a><a name="document_site_objects"></a>Dokument Standort Objekte

In der Active Document Containment-Architektur ist eine Dokument Site mit dem Hinzufügen der-Schnittstelle mit einem Client Standort Objekt in OLE-Dokumenten identisch `IOleDocument` :

```cpp
interface IOleDocumentSite : IUnknown
{
    HRESULT ActivateMe(IOleDocumentView *pViewToActivate);
}
```

Die Dokument Website ist konzeptionell der Container für ein oder mehrere "View Site"-Objekte. Jedes Ansichts Site Objekt ist einzelnen Ansichts Objekten des Dokuments zugeordnet, das von der Dokument Website verwaltet wird. Wenn der Container nur eine einzelne Ansicht pro Dokument Site unterstützt, kann er die Dokument Website und die Ansichts Website mit einer einzelnen konkreten Klasse implementieren.

## <a name="view-site-objects"></a><a name="view_site_objects"></a>Anzeigen von Standort Objekten

Das Ansichts Site Objekt eines Containers verwaltet den Anzeigebereich für eine bestimmte Ansicht eines Dokuments. Neben der Unterstützung der Standard `IOleInPlaceSite` Schnittstelle implementiert eine Ansichts Site auch im Allgemeinen für die programmgesteuerte `IContinueCallback` Drucksteuerung. (Beachten Sie, dass das Ansichts Objekt nie nach fragt, `IContinueCallback` sodass es tatsächlich für ein beliebiges Objekt implementiert werden kann, das der Container wünscht.)

Ein Container, der mehrere Ansichten unterstützt, muss in der Lage sein, mehrere View Site Objects innerhalb der Dokument Website zu erstellen. Dadurch wird jede Ansicht mit separaten Aktivierungs-und Aktivierungs Diensten bereitgestellt, die über bereitgestellt werden `IOleInPlaceSite` .

## <a name="frame-object"></a><a name="frame_object"></a>Frame-Objekt

Das Frame-Objekt des Containers ist größtenteils derselbe Frame, der für die direkte Aktivierung in OLE-Dokumenten verwendet wird, d. h. der, der die Menü-und Symbolleisten Aushandlung behandelt. Ein View-Objekt kann über Zugriff auf dieses Frame Objekt über verfügen `IOleInPlaceSite::GetWindowContext` , das auch Zugriff auf das Container Objekt bietet, das das Container Dokument darstellt (das die Symbolleisten Aushandlung auf Bereichs Ebene und enthaltene Objektenumeration verarbeiten kann).

Ein aktiver Dokument Container kann den Frame durch Hinzufügen von erweitern `IOleCommandTarget` . Dies ermöglicht es, Befehle, die aus der Benutzeroberfläche des aktiven Dokuments stammen, auf dieselbe Weise zu empfangen, wie diese Schnittstelle es einem Container ermöglicht, dieselben Befehle zu senden ( **z. b**. " **Datei neu**", " **Öffnen**", " **Speichern**unter"). **Bearbeiten Sie kopieren**, **Einfügen**, **Rückgängig**und andere) in ein aktives Dokument. Weitere Informationen finden Sie unter [Befehls Ziele](message-handling-and-command-targets.md).

## <a name="see-also"></a>Siehe auch

[Active Document-Container](active-document-containment.md)

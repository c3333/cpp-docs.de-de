---
title: OLE-Server-Klassen
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
ms.openlocfilehash: 06f5cf0985756506e42c7ad9fde24641b5a0ce93
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619852"
---
# <a name="ole-server-classes"></a>OLE-Server-Klassen

Diese Klassen werden von Server Anwendungen verwendet. Server Dokumente werden von abgeleitet `COleServerDoc` und nicht von `CDocument` . Beachten Sie, dass `COleServerDoc` `COleLinkingDoc` Server Dokumente auch Container sein können, die das Verknüpfen unterstützen, da von abgeleitet ist.

Die- `COleServerItem` Klasse stellt ein Dokument oder einen Teil eines Dokuments dar, das in ein anderes Dokument eingebettet oder verknüpft werden kann.

`COleIPFrameWnd`und `COleResizeBar` unterstützen direkte Bearbeitung, während sich das Objekt in einem Container befindet, und `COleTemplateServer` unterstützt die Erstellung von Dokumenten/Ansichts Paaren, damit OLE-Objekte aus anderen Anwendungen bearbeitet werden können.

[COleServerDoc](reference/coleserverdoc-class.md)<br/>
Wird als Basisklasse für Server Anwendungs Dokument Klassen verwendet. `COleServerDoc`-Objekte bieten den größten Teil der Serverunterstützung durch Interaktionen mit- `COleServerItem` Objekten. Die visuelle Bearbeitungsfunktion wird mithilfe der Dokument-/Ansichtsarchitektur der Klassenbibliothek bereitgestellt.

[CDocItem](reference/cdocitem-class.md)<br/>
Abstrakte Basisklasse von `COleClientItem` und `COleServerItem` . Objekte von Klassen, die von abgeleitet werden, `CDocItem` stellen Teile von Dokumenten dar.

[COleServerItem](reference/coleserveritem-class.md)<br/>
Wird zur Darstellung der OLE-Schnittstelle für `COleServerDoc` Elemente verwendet. Es gibt in der Regel ein- `COleServerDoc` Objekt, das den eingebetteten Teil eines Dokuments darstellt. In Servern, die Links zu Teilen von Dokumenten unterstützen, können viele `COleServerItem` Objekte vorhanden sein, die jeweils einen Link zu einem Teil des Dokuments darstellen.

[COleIPFrameWnd](reference/coleipframewnd-class.md)<br/>
Stellt das Rahmen Fenster für eine Ansicht bereit, wenn ein Server Dokument an Ort und Stelle bearbeitet wird.

[COleResizeBar](reference/coleresizebar-class.md)<br/>
Stellt die Standardbenutzer Oberfläche für die direkte Größe der Größe bereit. Objekte dieser Klasse werden immer in Verbindung mit- `COleIPFrameWnd` Objekten verwendet.

[COleTemplateServer](reference/coletemplateserver-class.md)<br/>
Wird verwendet, um Dokumente mithilfe der Dokument-/Ansichtarchitektur des Frameworks zu erstellen. Ein- `COleTemplateServer` Objekt delegiert den größten Teil seiner Arbeit an ein zugeordnetes- `CDocTemplate` Objekt.

[COleException](reference/coleexception-class.md)<br/>
Eine Ausnahme, die sich aus einem Fehler bei der OLE-Verarbeitung ergibt. Diese Klasse wird sowohl von Containern als auch von Servern verwendet.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)

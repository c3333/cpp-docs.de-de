---
title: OLE-Containerklassen
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
ms.openlocfilehash: 596b94e7fdbb5d9dc1862867001f6c01c1aea7b2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617806"
---
# <a name="ole-container-classes"></a>OLE-Containerklassen

Diese Klassen werden von Container Anwendungen verwendet. Und verwalten Auflistungen `COleLinkingDoc` `COleDocument` von- `COleClientItem` Objekten. Anstatt die Dokument Klasse von abzuleiten `CDocument` , leiten Sie Sie von oder ab `COleLinkingDoc` `COleDocument` , abhängig davon, ob Sie Links zu Objekten unterstützen möchten, die in das Dokument eingebettet sind.

Verwenden Sie ein- `COleClientItem` Objekt, um jedes OLE-Element in Ihrem Dokument darzustellen, das aus einem anderen Dokument eingebettet ist, oder ein Link zu einem anderen Dokument.

[COleDocObjectItem](reference/coledocobjectitem-class.md)<br/>
Unterstützt aktives Dokument Containment.

[COleDocument](reference/coledocument-class.md)<br/>
Wird für die Implementierung von Verbund Dokumenten sowie grundlegende Container Unterstützung verwendet. Dient als Container für Klassen, die von abgeleitet werden `CDocItem` . Diese Klasse kann als Basisklasse für Container Dokumente verwendet werden und ist die Basisklasse für `COleServerDoc` .

[COleLinkingDoc](reference/colelinkingdoc-class.md)<br/>
Eine von abgeleitete Klasse `COleDocument` , die die Infrastruktur für Verknüpfungen bereitstellt. Sie sollten die Dokument Klassen für Ihre Container Anwendungen von dieser Klasse anstelle von ableiten `COleDocument` , wenn Sie Links zu eingebetteten Objekten unterstützen sollen.

[CRichEditDoc](reference/cricheditdoc-class.md)<br/>
Verwaltet die Liste der OLE-Client Elemente, die sich im Rich Edit-Steuerelement befinden. Wird mit [CRichEditView](reference/cricheditview-class.md) und [cricheditcnztem](reference/cricheditcntritem-class.md)verwendet.

[CDocItem](reference/cdocitem-class.md)<br/>
Abstrakte Basisklasse von `COleClientItem` und `COleServerItem` . Objekte von Klassen, die von abgeleitet werden, `CDocItem` stellen Teile von Dokumenten dar.

[COleClientItem](reference/coleclientitem-class.md)<br/>
Eine Client Element Klasse, die die Seite des Clients der Verbindung mit einem eingebetteten oder verknüpften OLE-Element darstellt. Leiten Sie Ihre Client Elemente von dieser Klasse ab.

[CRichEditCntrItem](reference/cricheditcntritem-class.md)<br/>
Bietet Client seitigen Zugriff auf ein OLE-Element, das in einem Rich Edit-Steuerelement gespeichert ist, wenn es mit und verwendet wird `CRichEditView` `CRichEditDoc` .

[COleException](reference/coleexception-class.md)<br/>
Eine Ausnahme, die sich aus einem Fehler bei der OLE-Verarbeitung ergibt. Diese Klasse wird sowohl von Containern als auch von Servern verwendet.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)

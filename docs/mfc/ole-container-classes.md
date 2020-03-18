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
ms.openlocfilehash: 61db5310637d13da2d2cc183f12f8f62aa60e328
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447652"
---
# <a name="ole-container-classes"></a>OLE-Containerklassen

Diese Klassen werden von Container Anwendungen verwendet. Sowohl `COleLinkingDoc` als auch `COleDocument` Sammlungen von `COleClientItem` Objekten verwalten. Anstatt die Dokument Klasse von `CDocument`abzuleiten, leiten Sie Sie von `COleLinkingDoc` oder `COleDocument`ab, abhängig davon, ob Sie Links zu Objekten unterstützen möchten, die in das Dokument eingebettet sind.

Verwenden Sie ein `COleClientItem` Objekt, um jedes OLE-Element in Ihrem Dokument darzustellen, das aus einem anderen Dokument eingebettet ist, oder ein Link zu einem anderen Dokument.

[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)<br/>
Unterstützt aktives Dokument Containment.

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
Wird für die Implementierung von Verbund Dokumenten sowie grundlegende Container Unterstützung verwendet. Dient als Container für Klassen, die von `CDocItem`abgeleitet werden. Diese Klasse kann als Basisklasse für Container Dokumente verwendet werden und ist die Basisklasse für `COleServerDoc`.

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
Eine von `COleDocument` abgeleitete Klasse, die die Infrastruktur für die Verknüpfung bereitstellt. Sie sollten die Dokument Klassen für Ihre Container Anwendungen von dieser Klasse anstelle von `COleDocument` ableiten, wenn Sie Links zu eingebetteten Objekten unterstützen sollen.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Verwaltet die Liste der OLE-Client Elemente, die sich im Rich Edit-Steuerelement befinden. Wird mit [CRichEditView](../mfc/reference/cricheditview-class.md) und [cricheditcnztem](../mfc/reference/cricheditcntritem-class.md)verwendet.

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
Abstrakte Basisklasse von `COleClientItem` und `COleServerItem`. Objekte von Klassen, die von `CDocItem` abgeleitet sind, stellen Teile von Dokumenten dar.

[COleClientItem](../mfc/reference/coleclientitem-class.md)<br/>
Eine Client Element Klasse, die die Seite des Clients der Verbindung mit einem eingebetteten oder verknüpften OLE-Element darstellt. Leiten Sie Ihre Client Elemente von dieser Klasse ab.

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Bietet Client seitigen Zugriff auf ein OLE-Element, das in einem Rich Edit-Steuerelement gespeichert ist, wenn es mit `CRichEditView` und `CRichEditDoc`verwendet wird.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Eine Ausnahme, die sich aus einem Fehler bei der OLE-Verarbeitung ergibt. Diese Klasse wird sowohl von Containern als auch von Servern verwendet.

## <a name="see-also"></a>Weitere Informationen

[Klassen Übersicht](../mfc/class-library-overview.md)

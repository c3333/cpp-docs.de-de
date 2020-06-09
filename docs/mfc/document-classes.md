---
title: Dokumentklassen
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
ms.openlocfilehash: 012d107d7bcc630c4bc02a9dc697172080787eac
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615804"
---
# <a name="document-classes"></a>Dokumentklassen

Dokument Klassen Objekte, die von Dokumentvorlagen Objekten erstellt wurden, verwalten die Daten der Anwendung. Sie leiten eine Klasse für Ihre Dokumente von einer dieser Klassen ab.

Dokument Klassen Objekte interagieren mit Ansichts Objekten. Objekte anzeigen stellt den Client Bereich eines Fensters dar, zeigt die Daten eines Dokuments an und ermöglicht Benutzern die Interaktion mit der Anwendung. Dokumente und Sichten werden von einem Document-Template-Objekt erstellt.

[CDocument](reference/cdocument-class.md)<br/>
Die Basisklasse für anwendungsspezifische Dokumente. Leiten Sie die Dokument Klasse oder die Klassen von ab `CDocument` .

[COleDocument](reference/coledocument-class.md)<br/>
Wird für die Implementierung von Verbund Dokumenten sowie grundlegende Container Unterstützung verwendet. Dient als Container für Klassen, die von [CDocItem](reference/cdocitem-class.md)abgeleitet werden. Diese Klasse kann als Basisklasse für Container Dokumente verwendet werden und ist die Basisklasse für `COleServerDoc` .

[COleLinkingDoc](reference/colelinkingdoc-class.md)<br/>
Eine von abgeleitete Klasse `COleDocument` , die die Infrastruktur für Verknüpfungen bereitstellt. Sie sollten die Dokument Klassen für Ihre Container Anwendungen von dieser Klasse anstelle von ableiten `COleDocument` , wenn Sie Links zu eingebetteten Objekten unterstützen sollen.

[CRichEditDoc](reference/cricheditdoc-class.md)<br/>
Verwaltet die Liste der OLE-Client Elemente, die sich im Rich Edit-Steuerelement befinden. Wird mit [CRichEditView](reference/cricheditview-class.md) und [cricheditcnztem](reference/cricheditcntritem-class.md)verwendet.

[COleServerDoc](reference/coleserverdoc-class.md)<br/>
Wird als Basisklasse für Server Anwendungs Dokument Klassen verwendet. `COleServerDoc`-Objekte bieten den größten Teil der Serverunterstützung durch Interaktionen mit [COleServerItem](reference/coleserveritem-class.md) -Objekten. Die visuelle Bearbeitungsfunktion wird mithilfe der Dokument-/Ansichtsarchitektur der Klassenbibliothek bereitgestellt.

[CHtmlEditDoc](reference/chtmleditdoc-class.md)<br/>
Stellt mit [CHtmlEditView](reference/chtmleditview-class.md)die Funktionalität der Webbrowser-HTML-Bearbeitungs Plattform im Kontext der MFC-Dokument-/Ansichtsarchitektur bereit.

## <a name="related-classes"></a>Verwandte Klassen

Dokument Klassen Objekte können persistent sein – mit anderen Worten, Sie können Ihren Zustand in ein Speichermedium schreiben und wieder lesen. MFC stellt die `CArchive` -Klasse bereit, um die Übertragung der Dokument Daten an ein Speichermedium zu vereinfachen.

[CArchive](reference/carchive-class.md)<br/>
Kooperiert mit einem [CFile](reference/cfile-class.md) -Objekt, um mithilfe der Serialisierung permanenten Speicher für Objekte zu implementieren (siehe [CObject:: Serialize](reference/cobject-class.md#serialize)).

Dokumente können auch OLE-Objekte enthalten. `CDocItem`ist die Basisklasse von Server-und Client Elementen.

[CDocItem](reference/cdocitem-class.md)<br/>
Abstrakte Basisklasse von [COleClientItem](reference/coleclientitem-class.md) und [COleServerItem](reference/coleserveritem-class.md). Objekte von Klassen, die von abgeleitet werden, `CDocItem` stellen Teile von Dokumenten dar.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)

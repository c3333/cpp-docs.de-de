---
title: 'Container: Clientelemente'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client items
- client items and OLE containers
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
ms.openlocfilehash: ad347c78fb6aa7af94b306a3edb538b9f740c305
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619017"
---
# <a name="containers-client-items"></a>Container: Clientelemente

In diesem Artikel wird erläutert, was Client Elemente sind und aus welchen Klassen Ihre Anwendung Ihre Client Elemente ableiten sollte.

Client Elemente sind Datenelemente, die zu einer anderen Anwendung gehören, die entweder in oder im Dokument einer OLE-Containeranwendung enthalten ist. Client Elemente, deren Daten im Dokument enthalten sind, sind eingebettet. die Daten, deren Daten an einem anderen Speicherort gespeichert werden, auf den das Container Dokument verweist, sind verknüpft.

Die Document-Klasse in einer OLE-Anwendung wird von der-Klasse [COleDocument](reference/coledocument-class.md) anstelle von abgeleitet `CDocument` . Die- `COleDocument` Klasse erbt von `CDocument` allen Funktionen, die für die Verwendung der Dokument-/Ansichtarchitektur erforderlich sind, auf der MFC-Anwendungen basieren. `COleDocument`definiert außerdem eine Schnittstelle, die ein Dokument als eine Auflistung von- `CDocItem` Objekten behandelt. `COleDocument`Zum Hinzufügen, abrufen und Löschen von Elementen dieser Auflistung werden mehrere Element Funktionen bereitgestellt.

Jede Containeranwendung sollte mindestens eine Klasse von ableiten `COleClientItem` . Objekte dieser Klasse stellen im OLE-Dokument eingebettete oder verknüpfte Elemente dar. Diese Objekte sind für die Lebensdauer des Dokuments vorhanden, in dem Sie enthalten sind, es sei denn, Sie werden aus dem Dokument gelöscht.

`CDocItem`ist die Basisklasse für `COleClientItem` und `COleServerItem` . Objekte von Klassen, die von diesen beiden abgeleitet werden, fungieren als Vermittler zwischen dem OLE-Element und den Client-bzw. Server Anwendungen. Jedes Mal, wenn dem Dokument ein neues OLE-Element hinzugefügt wird, fügt das MFC-Framework der Auflistung von-Objekten des Dokuments ein neues-Objekt der von `COleClientItem` abgeleiteten-Klasse der Client Anwendung hinzu `CDocItem` .

## <a name="see-also"></a>Siehe auch

[Container](containers.md)<br/>
[Container: Verbunddateien](containers-compound-files.md)<br/>
[Container: Probleme mit der Benutzeroberfläche](containers-user-interface-issues.md)<br/>
[Container: Erweiterte Funktionen](containers-advanced-features.md)<br/>
[COleClientItem-Klasse](reference/coleclientitem-class.md)<br/>
[COleServerItem-Klasse](reference/coleserveritem-class.md)

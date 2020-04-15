---
title: 'Server: Serverelemente'
ms.date: 11/04/2016
helpviewer_keywords:
- server items, implementing
- servers [MFC], server items
- architecture [MFC], server-item
- server items
- OLE server applications [MFC], server items
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
ms.openlocfilehash: 8ae24104a30a0b44e92b889006907911124310f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355113"
---
# <a name="servers-server-items"></a>Server: Serverelemente

Wenn ein Container einen Server startet, damit ein Benutzer ein eingebettetes oder verknüpftes OLE-Element bearbeiten kann, erstellt die Serveranwendung ein "Serverelement". Das Serverelement, das ein Objekt einer `COleServerItem`von abgeleiteten Klasse ist, stellt eine Schnittstelle zwischen dem Serverdokument und der Containeranwendung bereit.

Die `COleServerItem` Klasse definiert mehrere überschreibbare Memberfunktionen, die von OLE aufgerufen werden, in der Regel als Reaktion auf Anforderungen aus dem Container. Serverelemente können einen Teil des Serverdokuments oder des gesamten Dokuments darstellen. Wenn ein OLE-Element in das Containerdokument eingebettet ist, stellt das Serverelement das gesamte Serverdokument dar. Wenn das OLE-Element verknüpft ist, kann das Serverelement einen Teil des Serverdokuments oder des gesamten Dokuments darstellen, je nachdem, ob die Verknüpfung zu einem Teil oder zum Ganzen besteht.

Im [HIERSVR-Beispiel](../overview/visual-cpp-samples.md) hat z. B. `CServerItem`die Serverelementklasse , einen Member, der `CServerNode`ein Zeiger auf ein Objekt der Klasse ist. Das `CServerNode` Objekt ist ein Knoten im Dokument der HIERSVR-Anwendung, bei dem es sich um eine Struktur handelt. Wenn `CServerNode` das Objekt der Stammknoten ist, stellt das `CServerItem` Objekt das gesamte Dokument dar. Wenn `CServerNode` es sich bei dem `CServerItem` Objekt um einen untergeordneten Knoten handelt, stellt das Objekt einen Teil des Dokuments dar. Ein Beispiel für diese Interaktion finden Sie im MFC OLE-Beispiel [HIERSVR.](../overview/visual-cpp-samples.md)

## <a name="implementing-server-items"></a><a name="_core_implementing_server_items"></a>Implementieren von Serverelementen

Wenn Sie den Anwendungsassistenten verwenden, um "Starter"-Code für Ihre Anwendung zu erstellen, müssen Sie nur serverelemente in Ihren Startcode aufnehmen, um eine der Serveroptionen auf der Seite OLE-Optionen auszuwählen. Wenn Sie einer vorhandenen Anwendung Serverelemente hinzufügen, führen Sie die folgenden Schritte aus:

#### <a name="to-implement-a-server-item"></a>So implementieren Sie ein Serverelement

1. Leiten Sie eine Klasse von `COleServerItem` ab.

1. Überschreiben Sie in ihrer `OnDraw` abgeleiteten Klasse die Memberfunktion.

   Das Framework `OnDraw` ruft auf, um das OLE-Element in eine Metadatei zu rendern. Die Containeranwendung verwendet diese Metadatei, um das Element zu rendern. Die Ansichtsklasse Ihrer Anwendung `OnDraw` verfügt auch über eine Memberfunktion, die zum Rendern des Elements verwendet wird, wenn die Serveranwendung aktiv ist.

1. Implementieren Sie eine `OnGetEmbeddedItem` Außerkraftsetzung von für Ihre Serverdokumentklasse. Weitere Informationen finden Sie im Artikel [Server: Implementieren von Serverdokumenten](../mfc/servers-implementing-server-documents.md) und dem MFC OLE-Beispiel [HIERSVR](../overview/visual-cpp-samples.md).

1. Implementieren Sie die `OnGetExtent` Memberfunktion der Serverelementklasse. Das Framework ruft diese Funktion auf, um die Größe des Elements abzurufen. Bei der Standardimplementierung wird keine Aktion ausgeführt.

## <a name="a-tip-for-server-item-architecture"></a><a name="_core_a_tip_for_server.2d.item_architecture"></a>Ein Tipp für die Server-Item-Architektur

Wie unter [Implementieren von Serverelementen](#_core_implementing_server_items)erwähnt, müssen Serveranwendungen in der Lage sein, Elemente sowohl in der Ansicht des Servers als auch in einer Metadatei zu rendern, die von der Containeranwendung verwendet wird. In der Anwendungsarchitektur der Microsoft Foundation-Klassenbibliothek `OnDraw` rendert die Memberfunktion der Ansichtsklasse das Element beim Bearbeiten (siehe [CView::OnDraw](../mfc/reference/cview-class.md#ondraw) in der *Klassenbibliotheksreferenz*). Das Serverelement `OnDraw` rendert das Element in allen anderen Fällen in eine Metadatei (siehe [COleServerItem::OnDraw](../mfc/reference/coleserveritem-class.md#ondraw)).

Sie können eine Duplizierung von Code vermeiden, indem Sie Hilfsfunktionen `OnDraw` in Ihre Serverdokumentklasse schreiben und sie aus den Funktionen in DerAnsicht und Serverelementklassen aufrufen. Das MFC OLE-Beispiel [HIERSVR](../overview/visual-cpp-samples.md) verwendet `CServerView::OnDraw` `CServerItem::OnDraw` diese `CServerDoc::DrawTree` Strategie: die Funktionen und beide aufrufen, um das Element zu rendern.

Die Ansicht und das `OnDraw` Element haben beide Memberfunktionen, da sie unter unterschiedlichen Bedingungen gezeichnet werden. Die Ansicht muss Faktoren wie Zoomen, Auswahlgröße und -ausdehnung, Clipping und Benutzeroberflächenelemente wie Bildlaufleisten berücksichtigen. Das Serverelement hingegen zeichnet immer das gesamte OLE-Objekt.

Weitere Informationen finden Sie unter [CView::OnDraw](../mfc/reference/cview-class.md#ondraw), [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerItem::OnDraw](../mfc/reference/coleserveritem-class.md#ondraw)und [cOleServerDoc::OnGetEmbeddedItem](../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) in der *Klassenbibliotheksreferenz*.

## <a name="see-also"></a>Siehe auch

[Server](../mfc/servers.md)

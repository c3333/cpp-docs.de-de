---
title: Server für aktive Dokumente
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC], servers
- servers [MFC], active document
- active document servers [MFC]
ms.assetid: 131fec1e-02a0-4305-a7ab-903b911232a7
ms.openlocfilehash: 58f2a63a8c640e6ae31640af680894763603e1d0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619140"
---
# <a name="active-document-servers"></a>Server für aktive Dokumente

Aktive Dokument Server wie Word, Excel oder PowerPoint hosten Dokumente von anderen Anwendungs Typen, die als aktive Dokumente bezeichnet werden. Im Gegensatz zu OLE Embedded-Objekten (die einfach auf der Seite eines anderen Dokuments angezeigt werden) bieten aktive Dokumente die vollständige Benutzeroberfläche und vollständige native Funktionalität der Serveranwendung, die Sie erstellt. Benutzer können Dokumente mit der vollen Leistung Ihrer bevorzugten Anwendungen erstellen (wenn Sie aktives Dokument aktivieren), aber das resultierende Projekt als eine einzelne Entität behandeln.

Aktive Dokumente können mehr als eine Seite aufweisen und sind immer direkt aktiv. Aktive Dokumente Steuern einen Teil der Benutzeroberfläche, wobei die Menüs mit den Menüs " **Datei** " und " **Hilfe** " des Containers zusammengeführt werden. Sie belegen den gesamten Bearbeitungsbereich des Containers und steuern die Ansichten und das Layout der Drucker Seite (Ränder, Fußzeilen usw.).

MFC implementiert aktive Dokument Server mit Dokument-/ansichtschnittstellen, Befehls Dispatchzuordnungen, Druck, Menüverwaltung und Registrierungs Verwaltung. Bestimmte Programmier Anforderungen werden in [aktive Dokumente](active-documents.md)erörtert.

MFC unterstützt aktive Dokumente mit der " [CDocObjectServer](reference/cdocobjectserver-class.md) "-Klasse, die von " [CCmdTarget](reference/ccmdtarget-class.md)" abgeleitet ist, und " [CDocObjectServerItem](reference/cdocobjectserveritem-class.md)", die von [COleServerItem](reference/coleserveritem-class.md)abgeleitet ist. MFC unterstützt aktive Dokument Container mit der [COleDocObjectItem](reference/coledocobjectitem-class.md) -Klasse, die von [COleClientItem](reference/coleclientitem-class.md)abgeleitet ist.

`CDocObjectServer`ordnet die aktiven Dokument Schnittstellen zu und initialisiert und aktiviert ein aktives Dokument. MFC stellt auch Makros zum Verarbeiten des Befehls Routings in aktiven Dokumenten bereit. Wenn Sie aktive Dokumente in Ihrer Anwendung verwenden möchten, schließen Sie afxdocob. h in die Datei "stdafx. h" ein.

Ein regulärer MFC-Server verknüpft seine eigene, von `COleServerItem` abgeleitete Klasse. Der MFC-Anwendungs-Assistent generiert diese Klasse für Sie, wenn Sie das Kontrollkästchen **Mini Server** oder **Vollversion Server** aktivieren, um die Unterstützung von Verbund Dokumenten für den Anwendungsserver zu aktivieren. Wenn Sie auch das Kontrollkästchen **aktiver Dokument Server** aktivieren, generiert der MFC-Anwendungs-Assistent stattdessen eine von abgeleitete Klasse `CDocObjectServerItem` .

Mit der- `COleDocObjectItem` Klasse kann ein OLE-Container zu einem aktiven Dokument Container werden. Mithilfe des MFC-Anwendungs-Assistenten können Sie einen aktiven Dokument Container erstellen, indem Sie auf der Seite zusammengesetzte Dokument Unterstützung des MFC-Anwendungs-Assistenten das Kontrollkästchen **aktiver Dokument Container** auswählen. Weitere Informationen finden Sie unter [Erstellen einer Container Anwendung für aktive Dokumente](creating-an-active-document-container-application.md).

## <a name="see-also"></a>Siehe auch

[Active Document-Container](active-document-containment.md)

---
title: 'OLE-Hintergrund: Container und Server'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE full-server applications [MFC]
- server applications [MFC], communication with containers
- full-server [MFC]
- server applications [MFC], requirements
- server applications [MFC], defined
- OLE server applications [MFC], about server applications
- server applications [MFC], full-server vs. mini-server
- OLE server applications [MFC], mini-server applications
- OLE containers [MFC], container applications
- containers [MFC], OLE container applications
- server applications [MFC]
ms.assetid: dafbb31d-096c-4654-b774-12900d832919
ms.openlocfilehash: 7c3130ab9d8dff6551ef0ecbec43e5422dbdc4c4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617914"
---
# <a name="ole-background-containers-and-servers"></a>OLE-Hintergrund: Container und Server

Eine Containeranwendung ist eine Anwendung, die eingebettete oder verknüpfte Elemente in Ihre eigenen Dokumente integrieren kann. Die von einer Containeranwendung verwalteten Dokumente müssen OLE-Dokument Komponenten sowie die von der Anwendung selbst erstellten Daten speichern und anzeigen können. Eine Containeranwendung muss außerdem Benutzern das Einfügen neuer Elemente oder das Bearbeiten vorhandener Elemente ermöglichen, indem Server Anwendungen bei Bedarf aktiviert werden. Die Benutzeroberflächen Anforderungen einer Containeranwendung sind im Artikel [Container: Probleme mit der Benutzeroberfläche](containers-user-interface-issues.md)aufgeführt.

Eine Serveranwendung oder Komponenten Anwendung ist eine Anwendung, mit der OLE-Dokument Komponenten zur Verwendung durch Container Anwendungen erstellt werden können. Server Anwendungen unterstützen in der Regel Drag & Drop oder das Kopieren Ihrer Daten in die Zwischenablage, damit eine Containeranwendung die Daten als eingebettetes oder verknüpftes Element einfügen kann. Bei einer Anwendung kann es sich um einen Container und einen Server handeln.

Die meisten Server sind eigenständige Anwendungen oder vollständige Server. Sie können entweder als eigenständige Anwendungen ausgeführt werden oder können von einer Containeranwendung gestartet werden. Ein Miniserver ist eine besondere Art von Serveranwendung, die nur von einem Container gestartet werden kann. Sie kann nicht als eigenständige Anwendung ausgeführt werden. Microsoft Draw-und Microsoft Graph-Server sind Beispiele für Miniservers.

Container und Server kommunizieren nicht direkt. Stattdessen kommunizieren Sie über die OLE-System-DLL (Dynamic-Link Libraries). Diese DLLs stellen Funktionen bereit, die von Containern und Servern aufgerufen werden, und die Container und Server bieten Rückruf Funktionen, die von den DLLs aufgerufen werden.

Mit dieser Kommunikationsmethode muss ein Container die Implementierungsdetails der Serveranwendung nicht kennen. Dadurch kann ein Container von einem beliebigen Server erstellte Elemente akzeptieren, ohne die Server Typen definieren zu müssen, mit denen er arbeiten kann. Folglich kann der Benutzer einer Containeranwendung zukünftige Anwendungen und Datenformate nutzen. Wenn es sich bei diesen neuen Anwendungen um OLE-Komponenten handelt, kann ein Verbund Dokument von diesen Anwendungen erstellte Elemente integrieren.

## <a name="see-also"></a>Siehe auch

[OLE-Hintergrund](ole-background.md)<br/>
[OLE-Hintergrund: MFC-Implementierung](ole-background-mfc-implementation.md)<br/>
[Container](containers.md)<br/>
[Server](servers.md)<br/>
[Container: Clientelemente](containers-client-items.md)<br/>
[Server: Serverelemente](servers-server-items.md)

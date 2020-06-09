---
title: Menüs und Ressourcen (OLE)
ms.date: 11/04/2016
helpviewer_keywords:
- OLE visual editing servers [MFC]
- status bars [MFC], OLE document applications
- visual editing [MFC], application menus and resources
- string tables [MFC], visual editing applications
- OLE containers [MFC], menus and resources
- OLE applications [MFC], menus and resources
- OLE server applications [MFC], menus and resources
- toolbars [MFC], OLE document applications
- string editing [MFC], visual editing applications
- server applications [MFC], OLE menus and resources
- applications [OLE], menus and resources
- menus [MFC], OLE document applications
- in-place activation [MFC], OLE menus and resources
- containers [MFC], OLE container applications
- OLE menus and resources [MFC]
ms.assetid: 52bfa086-7d3d-466f-94c7-c7061f3bdb3a
ms.openlocfilehash: e705f28476df7b594f9648aee8317759211c66c9
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626211"
---
# <a name="menus-and-resources-ole"></a>Menüs und Ressourcen (OLE)

In dieser Gruppe von Artikeln wird die Verwendung von Menüs und Ressourcen in MFC-OLE-Dokument Anwendungen erläutert.

Bei der OLE-visuellen Bearbeitung werden zusätzliche Anforderungen im Menü und in anderen von OLE-Dokument Anwendungen bereitgestellten Ressourcen gestellt, da es eine Reihe von Modi gibt, in denen Container-und Server Anwendungen (Komponenten Anwendungen) gestartet und verwendet werden können. Beispielsweise kann eine vollständige Serveranwendung in einem der folgenden drei Modi ausgeführt werden:

- Eigenständig.

- Direkt zum Bearbeiten eines Elements im Kontext eines Containers.

- Öffnen Sie, um ein Element außerhalb des Kontexts seines Containers zu bearbeiten, häufig in einem separaten Fenster.

Hierfür sind drei separate Menü Layouts erforderlich, eine für jeden möglichen Modus der Anwendung. Zugriffstasten Tabellen sind auch für jeden neuen Modus erforderlich. Eine Containeranwendung unterstützt möglicherweise die direkte Aktivierung. Wenn dies der Fall ist, benötigen Sie eine neue Menüstruktur und zugehörige Zugriffstasten Tabellen.

Die direkte Aktivierung erfordert, dass die Container-und Server Anwendungen für den Menü-, Symbolleisten-und Status Leistenbereich aushandeln müssen. Alle Ressourcen müssen in diesem Sinne entworfen werden. Die Artikel [Menüs und-Ressourcen:](menus-and-resources-menu-merging.md) die Zusammenführung des Menüs behandelt dieses Thema ausführlich.

Aufgrund dieser Probleme können OLE-Dokument Anwendungen, die mit dem Anwendungs-Assistenten erstellt wurden, bis zu vier separate Menüs und Zugriffstasten für Tabellen Ressourcen haben. Diese werden aus den folgenden Gründen verwendet:

|Ressourcenname|Verwendung|
|-------------------|---------|
|IDR_MAINFRAME|Wird in einer MDI-Anwendung verwendet, wenn keine Datei geöffnet ist, oder in einer SDI-Anwendung, unabhängig von geöffneten Dateien. Dies ist das Standardmenü, das in nicht-OLE-Anwendungen verwendet wird.|
|IDR_- \<project> Typ|Wird in einer MDI-Anwendung verwendet, wenn Dateien geöffnet sind. Wird verwendet, wenn eine Anwendung eigenständig ausgeführt wird. Dies ist das Standardmenü, das in nicht-OLE-Anwendungen verwendet wird.|
|IDR_ \<project> TYPE_SRVR_IP|Wird vom Server oder Container verwendet, wenn ein Objekt an Ort und Stelle geöffnet ist.|
|IDR_ \<project> TYPE_SRVR_EMB|Wird von einer Serveranwendung verwendet, wenn ein Objekt ohne direkte Aktivierung geöffnet wird.|

Jeder dieser Ressourcennamen stellt ein Menü und in der Regel eine Zugriffstasten Tabelle dar. Ein ähnliches Schema sollte in MFC-Anwendungen verwendet werden, die nicht mit dem Anwendungs-Assistenten erstellt werden.

In den folgenden Artikeln werden Themen im Zusammenhang mit Containern, Servern und der Zusammenführung des Menüs erläutert, die zum Implementieren der direkten Aktivierung erforderlich sind:

- [Menüs und Ressourcen: Containererweiterungen](menus-and-resources-container-additions.md)

- [Menüs und Ressourcen: Servererweiterungen](menus-and-resources-server-additions.md)

- [Menüs und Ressourcen: Menüs schachteln](menus-and-resources-menu-merging.md)

## <a name="see-also"></a>Siehe auch

[OLE](ole-in-mfc.md)

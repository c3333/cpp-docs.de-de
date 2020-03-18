---
title: 'Menüs und Ressourcen: Servererweiterungen'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE visual editing servers [MFC]
- accelerator tables [MFC], server applications
- visual editing [MFC], application menus and resources
- server applications [MFC], accelerator table
- string tables [MFC], visual editing applications
- servers [MFC], menu additions
- resources [MFC], server applications
- OLE server applications [MFC], menus and resources
- string editing [MFC], visual editing applications
- IDP_OLE_INIT_FAILED macro [MFC]
- server applications [MFC], OLE menus and resources
- OLE initialization failure [MFC]
ms.assetid: 56ce9e8d-8f41-4db8-8dee-e8b0702d057c
ms.openlocfilehash: c1dfd059572c433e8fd7ccaf6e5c48e880f59cad
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445184"
---
# <a name="menus-and-resources-server-additions"></a>Menüs und Ressourcen: Servererweiterungen

In diesem Artikel werden die Änderungen erläutert, die an den Menüs und anderen Ressourcen in einer Anwendung für die visuelle Bearbeitung von Servern (Komponenten) vorgenommen werden müssen. Eine Serveranwendung erfordert viele Ergänzungen der Menüstruktur und anderer Ressourcen, da Sie in einem von drei Modi gestartet werden kann: eigenständig, eingebettet oder direkt. Wie im Artikel [Menüs und Ressourcen (OLE)](../mfc/menus-and-resources-ole.md) beschrieben, gibt es maximal vier Sätze von Menüs. Alle vier werden für eine MDI-voll Serveranwendung verwendet, während nur drei für einen Miniserver verwendet werden. Der Anwendungs-Assistent erstellt das Menü Layout, das für den gewünschten Servertyp erforderlich ist. Möglicherweise sind einige Anpassungen erforderlich.

Wenn Sie den Anwendungs-Assistenten nicht verwenden, sollten Sie sich Hierarchie SVR ansehen. RC, das Ressourcen Skript für die MFC-Beispielanwendung [HIERSVR](../overview/visual-cpp-samples.md), um zu sehen, wie diese Änderungen implementiert werden.

Zu den in diesem Artikel behandelten Themen gehören:

- [Server Menü Ergänzungen](#_core_server_menu_additions)

- [Erweiterungen der Zugriffstasten Tabelle](#_core_server_application_accelerator_table_additions)

- [Zeichen folgen Tabellen Ergänzungen](../mfc/menus-and-resources-container-additions.md)

- [Miniserver Ergänzungen](#_core_mini.2d.server_additions)

##  <a name="_core_server_menu_additions"></a>Server Menü Ergänzungen

Server-(Component) Anwendungen müssen Menü Ressourcen hinzugefügt werden, um die visuelle OLE-Bearbeitung zu unterstützen. Die Menüs, die verwendet werden, wenn die Anwendung im eigenständigen Modus ausgeführt wird, müssen nicht geändert werden. Sie müssen jedoch zwei neue Menü Ressourcen hinzufügen, bevor Sie die Anwendung entwickeln: eine zur Unterstützung der direkten Aktivierung und eine zur Unterstützung des Servers, der vollständig geöffnet ist. Beide Menü Ressourcen werden von vollständigen und Miniserver-Anwendungen verwendet.

- Um die direkte Aktivierung zu unterstützen, müssen Sie eine Menü Ressource erstellen, die der Menü Ressource ähnlich ist, die bei der Verwendung im eigenständigen Modus verwendet wird. Der Unterschied in diesem Menü besteht darin, dass die Datei-und Fensterelemente (und alle anderen Menü Elemente, die mit der Anwendung und nicht den Daten behandelt werden) fehlen. Diese Menü Elemente werden von der Containeranwendung bereitgestellt. Weitere Informationen zu und einem Beispiel für diese Zusammenführung dieses Menüs finden Sie in den Artikeln [Menüs und Ressourcen:](../mfc/menus-and-resources-menu-merging.md)Zusammenführen von Menüs.

- Zur Unterstützung der vollständigen Öffnungs Aktivierung müssen Sie eine Menü Ressource erstellen, die nahezu identisch mit der Menü Ressource ist, die bei der Verwendung im eigenständigen Modus verwendet wird. Die einzige Änderung an dieser Menü Ressource besteht darin, dass einige Elemente neu formuliert werden, um die Tatsache widerzuspiegeln, dass der Server auf einem in einem Verbund Dokument eingebetteten Element arbeitet.

Zusätzlich zu den in diesem Artikel aufgeführten Änderungen muss ihre Ressourcen Datei afxolesv enthalten. RC, das für die Microsoft Foundation Class-Bibliothek-Implementierung erforderlich ist. Diese Datei befindet sich im Unterverzeichnis "mfc\include".

##  <a name="_core_server_application_accelerator_table_additions"></a>Hinzufügungen der Server Anwendungsbeschleunigung

Der Server Anwendungen müssen zwei neue Ressourcen für Zugriffstasten Tabellen hinzugefügt werden. Sie entsprechen direkt den neuen Menü Ressourcen, die zuvor beschrieben wurden. Die erste Zugriffstasten Tabelle wird verwendet, wenn die Serveranwendung an Ort und Stelle aktiviert wird. Sie besteht aus allen Einträgen in der Zugriffstasten Tabelle der Ansicht, mit Ausnahme derjenigen, die an die Menüs Datei und Fenster gebunden sind.

Die zweite Tabelle ist fast eine exakte Kopie der Zugriffstasten Tabelle der Sicht. Alle Unterschiede bei parallelen Änderungen, [die im Menü](#_core_server_menu_additions)"vollständig geöffnet" durchgeführt werden

Wenn Sie ein Beispiel für diese Änderungen an der Zugriffstasten Tabelle finden, vergleichen Sie die Tabellen "IDR_HIERSVRTYPE_SRVR_IP" und "IDR_HIERSVRTYPE_SRVR_EMB Accelerator" mit IDR_MAINFRAME in der Hierarchien. RC-Datei, die in der MFC-OLE-Beispiel [Hierarchie](../overview/visual-cpp-samples.md)enthalten ist. Die Datei-und Fenster Beschleuniger fehlen in der direkten Tabelle, und exakte Kopien von Ihnen sind in der eingebetteten Tabelle enthalten.

##  <a name="_core_string_table_additions_for_server_applications"></a>Zeichen folgen-Tabellen Ergänzungen für Server Anwendungen

In einer Serveranwendung ist nur eine Zeichen folgen-Tabellen Addition erforderlich – eine Zeichenfolge, die besagt, dass die OLE-Initialisierung fehlgeschlagen ist. Im folgenden finden Sie ein Beispiel für einen Eintrag in der Zeichen folgen Tabelle, den der Anwendungs-Assistent generiert:

|id|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|Fehler bei der OLE-Initialisierung. Stellen Sie sicher, dass die OLE-Bibliotheken die richtige Version sind.|

##  <a name="_core_mini.2d.server_additions"></a>Miniserver Ergänzungen

Die gleichen Ergänzungen gelten für Miniserver, die oben für vollständige Server aufgeführt sind. Da ein Miniserver nicht im eigenständigen Modus ausgeführt werden kann, ist das Hauptmenü viel kleiner. Das Hauptmenü, das vom Anwendungs-Assistenten erstellt wurde, verfügt nur über ein Menü Datei, das nur die Elemente Exit und about enthält. Eingebettete und direkte Menüs und Beschleuniger für Miniserver sind identisch mit denen für vollständige Server.

## <a name="see-also"></a>Weitere Informationen

[Menüs und Ressourcen (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Menüs und Ressourcen: Menüs schachteln](../mfc/menus-and-resources-menu-merging.md)

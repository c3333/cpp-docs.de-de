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
ms.openlocfilehash: 8366cd8b0376766b7914c94a24cef6598761a805
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375989"
---
# <a name="menus-and-resources-server-additions"></a>Menüs und Ressourcen: Servererweiterungen

In diesem Artikel werden die Änderungen erläutert, die an den Menüs und anderen Ressourcen in einer Anwendung für visuelle Bearbeitungsserver (Komponenten) vorgenommen werden müssen. Eine Serveranwendung erfordert viele Ergänzungen zur Menüstruktur und anderen Ressourcen, da sie in einem von drei Modi gestartet werden kann: stand alone, embedded oder on place. Wie im Artikel [Menüs und Ressourcen (OLE)](../mfc/menus-and-resources-ole.md) beschrieben, gibt es maximal vier Menüsätze. Alle vier werden für eine MDI-Vollserveranwendung verwendet, während nur drei für einen Miniserver verwendet werden. Der Anwendungsassistent erstellt das Menülayout, das für den gewünschten Servertyp erforderlich ist. Einige Anpassungen können erforderlich sein.

Wenn Sie den Anwendungsassistenten nicht verwenden, sollten Sie sich HIERSVR ansehen. RC, das Ressourcenskript für die MFC-Beispielanwendung [HIERSVR](../overview/visual-cpp-samples.md), um zu sehen, wie diese Änderungen implementiert werden.

Zu den in diesem Artikel behandelten Themen gehören:

- [Servermenü-Erweiterungen](#_core_server_menu_additions)

- [Accelerator Table Ergänzungen](#_core_server_application_accelerator_table_additions)

- [Zeichenfolgentabellenerweiterungen](../mfc/menus-and-resources-container-additions.md)

- [Miniserver-Erweiterungen](#_core_mini.2d.server_additions)

## <a name="server-menu-additions"></a><a name="_core_server_menu_additions"></a>Servermenü-Erweiterungen

Serveranwendungen (Komponentenanwendungen) müssen Menüressourcen hinzugefügt haben, um die visuelle OLE-Bearbeitung zu unterstützen. Die Menüs, die verwendet werden, wenn die Anwendung im eigenständigen Modus ausgeführt wird, müssen nicht geändert werden, aber Sie müssen zwei neue Menüressourcen hinzufügen, bevor Sie die Anwendung erstellen: eine zur Unterstützung der in-Place-Aktivierung und eine zur Unterstützung des vollständig geöffneten Servers. Beide Menüressourcen werden von Voll- und Miniserveranwendungen verwendet.

- Um die ortsnahe Aktivierung zu unterstützen, müssen Sie eine Menüressource erstellen, die der Menüressource sehr ähnlich ist, die bei der Ausführung im eigenständigen Modus verwendet wird. Der Unterschied in diesem Menü besteht darin, dass die Datei- und Fensterelemente (und alle anderen Menüelemente, die sich mit der Anwendung befassen, und nicht die Daten) fehlen. Die Containeranwendung stellt diese Menüelemente zur Verfügung. Weitere Informationen zu dieser Menüzusammenführungstechnik finden Sie im Artikel [Menüs und Ressourcen: Menüzusammenführen](../mfc/menus-and-resources-menu-merging.md).

- Um die vollständig geöffnete Aktivierung zu unterstützen, müssen Sie eine Menüressource erstellen, die fast identisch mit der Menüressource ist, die bei der Ausführung im eigenständigen Modus verwendet wird. Die einzige Änderung an dieser Menüressource besteht darin, dass einige Elemente neu formuliert werden, um die Tatsache widerzuspiegeln, dass der Server auf einem Element arbeitet, das in ein zusammengesetztes Dokument eingebettet ist.

Zusätzlich zu den in diesem Artikel aufgeführten Änderungen muss Ihre Ressourcendatei AUCH AFXOLESV enthalten. RC, das für die Implementierung der Microsoft Foundation-Klassenbibliothek erforderlich ist. Diese Datei befindet sich im Unterverzeichnis MFC-Include.

## <a name="server-application-accelerator-table-additions"></a><a name="_core_server_application_accelerator_table_additions"></a>Server Application Accelerator-Tabellenerweiterungen

Zwei neue Beschleunigertabellenressourcen müssen Serveranwendungen hinzugefügt werden. sie entsprechen direkt den zuvor beschriebenen neuen Menüressourcen. Die erste Beschleunigertabelle wird verwendet, wenn die Serveranwendung aktiviert ist. Sie besteht aus allen Einträgen in der Beschleunigertabelle der Ansicht mit Ausnahme der Einträge, die an die Menüs Datei und Fenster gebunden sind.

Die zweite Tabelle ist fast eine exakte Kopie der Beschleunigertabelle der Ansicht. Alle Unterschiede parallele Änderungen im vollständig geöffneten Menü in [Server Menü-Erweiterungen](#_core_server_menu_additions)erwähnt .

Vergleichen Sie zum Beispiel dieser Änderungen der Beschleunigertabelle die IDR_HIERSVRTYPE_SRVR_IP- und IDR_HIERSVRTYPE_SRVR_EMB-Beschleunigertabellen mit IDR_MAINFRAME im HIERSVR. RC-Datei im MFC OLE-Beispiel [HIERSVR](../overview/visual-cpp-samples.md)enthalten . Die Datei- und Fensterbeschleuniger fehlen in der Tabelle an Ort und Stelle, und genaue Kopien davon befinden sich in der eingebetteten Tabelle.

## <a name="string-table-additions-for-server-applications"></a><a name="_core_string_table_additions_for_server_applications"></a>Zeichenfolgentabellenerweiterungen für Serveranwendungen

In einer Serveranwendung ist nur eine Zeichenfolgentabellenaddition erforderlich – eine Zeichenfolge, um zu anbedeuten, dass die OLE-Initialisierung fehlgeschlagen ist. Hier ist beispielsweise der Zeichenfolgentabelleneintrag, den der Anwendungsassistent generiert:

|id|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|Fehler bei der OLE-Initialisierung. Stellen Sie sicher, dass die OLE-Bibliotheken die richtige Version sind.|

## <a name="miniserver-additions"></a><a name="_core_mini.2d.server_additions"></a>Miniserver-Erweiterungen

Für Miniserver gelten dieselben Ergänzungen wie die oben aufgeführten für Vollserver. Da ein Miniserver nicht im eigenständigen Modus ausgeführt werden kann, ist das Hauptmenü viel kleiner. Das Hauptmenü, das vom Anwendungsassistenten erstellt wurde, verfügt nur über ein Dateimenü, das nur die Elemente Exit und About enthält. Eingebettete und ortsbezogene Menüs und Beschleuniger für Miniserver sind die gleichen wie für Vollserver.

## <a name="see-also"></a>Siehe auch

[Menüs und Ressourcen (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Menüs und Ressourcen: Menüs schachteln](../mfc/menus-and-resources-menu-merging.md)

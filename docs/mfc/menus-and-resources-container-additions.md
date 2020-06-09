---
title: 'Menüs und Ressourcen: Containererweiterungen'
ms.date: 11/04/2016
f1_keywords:
- IDP_OLE_INIT_FAILED
- IDP_FAILED_TO_CREATE
- VK_ESCAPE
helpviewer_keywords:
- application accelerator table [MFC]
- VK_ESCAPE key [MFC]
- IDP_FAILED_TO_CREATE macro [MFC]
- visual editing, application menus and resources
- OLE containers [MFC], menus and resources
- accelerator tables [MFC], container applications
- IDP_OLE_INIT_FAILED macro [MFC]
- CONTAIN tutorial [MFC]
- Links menu item [MFC]
ms.assetid: 425448be-8ca0-412e-909a-a3a9ce845288
ms.openlocfilehash: a082a75ef0292e190e597f29be0cdc0bd0b497ef
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626236"
---
# <a name="menus-and-resources-container-additions"></a>Menüs und Ressourcen: Containererweiterungen

In diesem Artikel werden die Änderungen erläutert, die an den Menüs und anderen Ressourcen in einer Anwendung für die visuelle Bearbeitung von Containern vorgenommen werden müssen.

In Container Anwendungen müssen zwei Arten von Änderungen vorgenommen werden: Änderungen an vorhandenen Ressourcen zur Unterstützung der visuellen OLE-Bearbeitung und zum Hinzufügen neuer Ressourcen, die für die direkte Aktivierung verwendet werden. Wenn Sie die Containeranwendung mit dem Anwendungs-Assistenten erstellen, werden diese Schritte für Sie ausgeführt, Sie erfordern jedoch möglicherweise einige Anpassungen.

Wenn Sie den Anwendungs-Assistenten nicht verwenden, sollten Sie OCLIENT untersuchen. RC, das Ressourcen Skript für die OCLIENT-Beispielanwendung, um zu sehen, wie diese Änderungen implementiert werden. Weitere Informationen finden Sie unter MFC-OLE-Beispiel [OCLIENT](../overview/visual-cpp-samples.md).

Zu den in diesem Artikel behandelten Themen gehören:

- [Container-Menü Ergänzungen](#_core_container_menu_additions)

- [Erweiterungen der Zugriffstasten Tabelle](#_core_container_application_accelerator_table_additions)

- [Zeichen folgen Tabellen Ergänzungen](#_core_string_table_additions_for_container_applications)

## <a name="container-menu-additions"></a><a name="_core_container_menu_additions"></a>Container-Menü Ergänzungen

Sie müssen dem Menü Bearbeiten die folgenden Elemente hinzufügen:

|Element|Zweck|
|----------|-------------|
|**Neues Objekt einfügen**|Öffnet das OLE-Dialogfeld "Objekt einfügen", um ein verknüpftes oder eingebettetes Element in das Dokument einzufügen.|
|**Link einfügen**|Fügt einen Link zum Element in der Zwischenablage in das Dokument ein.|
|**OLE-Verb**|Ruft das primäre Verb des ausgewählten Elements auf. Der Text dieses Menü Elements wird geändert, um das primäre Verb des ausgewählten Elements widerzuspiegeln.|
|**Links**|Öffnet das Dialogfeld "Links bearbeiten", um vorhandene verknüpfte Elemente zu ändern.|

Zusätzlich zu den in diesem Artikel aufgeführten Änderungen muss die Quelldatei AFXOLECL enthalten. RC, das für die Microsoft Foundation Class-Bibliothek-Implementierung erforderlich ist. Das Einfügen eines neuen Objekts ist die einzige erforderliche Menü Addition. Es können auch andere Elemente hinzugefügt werden, die hier aufgeführten werden jedoch am häufigsten aufgeführt.

Sie müssen ein neues Menü für Ihre Containeranwendung erstellen, wenn Sie die direkte Aktivierung von enthaltenen Elementen unterstützen möchten. Dieses Menü besteht aus den gleichen Menü-und Fenster-Popup Menüs, die beim Öffnen von Dateien verwendet werden, aber es werden zwei Trennzeichen zwischen Ihnen platziert. Diese Trennzeichen werden verwendet, um anzugeben, wo das Server-(Komponenten-) Element (Anwendung) seine Menüs platzieren soll, wenn es direkt aktiviert wird. Weitere Informationen zu dieser Menü Zusammenführungs Methode finden Sie unter [Menüs und Ressourcen:](menus-and-resources-menu-merging.md)Zusammenführen von Menüs.

## <a name="container-application-accelerator-table-additions"></a><a name="_core_container_application_accelerator_table_additions"></a>Hinzufügungen zu Container Application Accelerators

Wenn Sie die direkte Aktivierung unterstützen, sind kleine Änderungen an den Zugriffstasten Tabellen Ressourcen einer Containeranwendung erforderlich. Die erste Änderung ermöglicht dem Benutzer, die Escape-Taste (ESC) zu drücken, um den direkten Bearbeitungsmodus abzubrechen. Fügen Sie der Tabelle Haupt Beschleunigung den folgenden Eintrag hinzu:

|id|Schlüssel|type|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

Die zweite Änderung besteht darin, eine neue Zugriffstasten Tabelle zu erstellen, die der neuen Menü Ressource entspricht, die für die direkte Aktivierung erstellt wurde. Diese Tabelle enthält Einträge für die Datei-und Fenstermenüs zusätzlich zum oben aufgeführten VK_ESCAPE Eintrag. Das folgende Beispiel zeigt die Zugriffstasten Tabelle, die für die direkte Aktivierung im MFC-Beispiel [Container](../overview/visual-cpp-samples.md)erstellt wurde:

|id|Schlüssel|type|
|--------|---------|----------|
|ID_FILE_NEW|STRG+N|**VIRTKEY**|
|ID_FILE_OPEN|STRG+O|**VIRTKEY**|
|ID_FILE_SAVE|STRG+S|**VIRTKEY**|
|ID_FILE_PRINT|STRG+P|**VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|
|ID_PREV_PANE|UMSCHALT + VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

## <a name="string-table-additions-for-container-applications"></a><a name="_core_string_table_additions_for_container_applications"></a>Zeichen folgen-Tabellen Ergänzungen für Container Anwendungen

Die meisten Änderungen an Zeichen folgen Tabellen für Container Anwendungen entsprechen den zusätzlichen Menü Elementen, die in den [Container-Menü Ergänzungen](#_core_container_menu_additions)erwähnt werden. Sie stellen den Text bereit, der in der Statusleiste angezeigt wird, wenn jedes Menü Element angezeigt wird. Im folgenden finden Sie ein Beispiel für die Zeichen folgen Tabelleneinträge, die der Anwendungs-Assistent generiert:

|id|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|Fehler bei der OLE-Initialisierung. Stellen Sie sicher, dass die OLE-Bibliotheken die richtige Version sind.|
|IDP_FAILED_TO_CREATE|Fehler beim Erstellen des Objekts. Stellen Sie sicher, dass das Objekt in der Systemregistrierung eingegeben wird.|

## <a name="see-also"></a>Siehe auch

[Menüs und Ressourcen (OLE)](menus-and-resources-ole.md)<br/>
[Menüs und Ressourcen: Servererweiterungen](menus-and-resources-server-additions.md)

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
ms.openlocfilehash: c8da58316f471f7b7d26e142cc1dd1ccaa6ad8b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364792"
---
# <a name="menus-and-resources-container-additions"></a>Menüs und Ressourcen: Containererweiterungen

In diesem Artikel werden die Änderungen erläutert, die an den Menüs und anderen Ressourcen in einer visuellen Bearbeitungscontaineranwendung vorgenommen werden müssen.

In Containeranwendungen müssen zwei Arten von Änderungen vorgenommen werden: Änderungen an vorhandenen Ressourcen zur Unterstützung der visuellen OLE-Bearbeitung und Hinzufügen neuer Ressourcen, die für die ortsnahe Aktivierung verwendet werden. Wenn Sie den Anwendungsassistenten zum Erstellen ihrer Containeranwendung verwenden, werden diese Schritte für Sie ausgeführt, sie erfordern jedoch möglicherweise eine gewisse Anpassung.

Wenn Sie den Anwendungsassistenten nicht verwenden, sollten Sie sich OCLIENT ansehen. RC, das Ressourcenskript für die OCLIENT-Beispielanwendung, um zu sehen, wie diese Änderungen implementiert werden. Siehe MFC OLE-Beispiel [OCLIENT](../overview/visual-cpp-samples.md).

Zu den in diesem Artikel behandelten Themen gehören:

- [Containermenü-Erweiterungen](#_core_container_menu_additions)

- [Accelerator Table Ergänzungen](#_core_container_application_accelerator_table_additions)

- [Zeichenfolgentabellenerweiterungen](#_core_string_table_additions_for_container_applications)

## <a name="container-menu-additions"></a><a name="_core_container_menu_additions"></a>Containermenü-Erweiterungen

Sie müssen die folgenden Elemente zum Menü Bearbeiten hinzufügen:

|Element|Zweck|
|----------|-------------|
|**Einfügen eines neuen Objekts**|Öffnet das Dialogfeld OLE-Objekt einfügen, um ein verknüpftes oder eingebettetes Element in das Dokument einzufügen.|
|**Einfügen von Link**|Fügt einen Link zu dem Element in der Zwischenablage in das Dokument ein.|
|**OLE Verb**|Ruft das primäre Verb des ausgewählten Elements auf. Der Text dieses Menüelements ändert sich, um das primäre Verb des ausgewählten Elements widerzuspiegeln.|
|**Links**|Öffnet das Dialogfeld OLE-Bearbeitungsverknüpfungen, um vorhandene verknüpfte Elemente zu ändern.|

Zusätzlich zu den in diesem Artikel aufgeführten Änderungen muss die Quelldatei AFXOLECL enthalten. RC, das für die Implementierung der Microsoft Foundation-Klassenbibliothek erforderlich ist. Einfügen von neuen Objekten ist die einzige erforderliche Menüerweiterung. Andere Elemente können hinzugefügt werden, aber die hier aufgeführten sind die häufigsten.

Sie müssen ein neues Menü für Ihre Containeranwendung erstellen, wenn Sie die ortsnahe Aktivierung enthaltener Elemente unterstützen möchten. Dieses Menü besteht aus dem gleichen Dateimenü und Fenster-Popup-Menüs, die verwendet werden, wenn Dateien geöffnet sind, aber es hat zwei Trennzeichen zwischen ihnen platziert. Diese Trennzeichen werden verwendet, um anzugeben, wo das Serverelement (Komponente) (Anwendung) seine Menüs platzieren soll, wenn es aktiviert ist. Weitere Informationen zu dieser Menü-Zusammenführungs-Technik finden Sie unter [Menüs und Ressourcen: Menüzusammenführen](../mfc/menus-and-resources-menu-merging.md).

## <a name="container-application-accelerator-table-additions"></a><a name="_core_container_application_accelerator_table_additions"></a>Container Application Accelerator-Tabellenerweiterungen

Kleine Änderungen an den Beschleunigertabellenressourcen einer Containeranwendung sind erforderlich, wenn Sie die an Ort und Stelle aktivieren. Die erste Änderung ermöglicht es dem Benutzer, die Escape-Taste (ESC) zu drücken, um den an Ort und Stelle Bearbeitungsmodus abzubrechen. Fügen Sie der Hauptbeschleunigertabelle den folgenden Eintrag hinzu:

|id|Schlüssel|type|
|--------|---------|----------|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

Die zweite Änderung besteht darin, eine neue Beschleunigertabelle zu erstellen, die der neuen Menüressource entspricht, die für die ortsnahe Aktivierung erstellt wurde. Diese Tabelle enthält Einträge für die Menüs Datei und Fenster sowie den oben VK_ESCAPE Eintrag. Das folgende Beispiel ist die Beschleunigertabelle, die für die ortsspezifische Aktivierung im MFC-Beispiel [CONTAINER](../overview/visual-cpp-samples.md)erstellt wurde:

|id|Schlüssel|type|
|--------|---------|----------|
|ID_FILE_NEW|STRG+N|**VIRTKEY**|
|ID_FILE_OPEN|STRG+O|**VIRTKEY**|
|ID_FILE_SAVE|STRG+S|**VIRTKEY**|
|ID_FILE_PRINT|STRG+P|**VIRTKEY**|
|ID_NEXT_PANE|VK_F6|**VIRTKEY**|
|ID_PREV_PANE|SHIFT+VK_F6|**VIRTKEY**|
|ID_CANCEL_EDIT_CNTR|VK_ESCAPE|**VIRTKEY**|

## <a name="string-table-additions-for-container-applications"></a><a name="_core_string_table_additions_for_container_applications"></a>Zeichenfolgentabellenerweiterungen für Containeranwendungen

Die meisten Änderungen an Zeichenfolgentabellen für Containeranwendungen entsprechen den zusätzlichen Menüelementen, die in [Containermenü-Zugängen](#_core_container_menu_additions)erwähnt werden. Sie geben den Text an, der in der Statusleiste angezeigt wird, wenn jedes Menüelement angezeigt wird. Hier sind beispielsweise die Zeichenfolgentabelleneinträge, die der Anwendungsassistent generiert:

|id|String|
|--------|------------|
|IDP_OLE_INIT_FAILED|Fehler bei der OLE-Initialisierung. Stellen Sie sicher, dass die OLE-Bibliotheken die richtige Version sind.|
|IDP_FAILED_TO_CREATE|Fehler beim Erstellen des Objekts. Stellen Sie sicher, dass das Objekt in der Systemregistrierung eingegeben wurde.|

## <a name="see-also"></a>Siehe auch

[Menüs und Ressourcen (OLE)](../mfc/menus-and-resources-ole.md)<br/>
[Menüs und Ressourcen: Servererweiterungen](../mfc/menus-and-resources-server-additions.md)

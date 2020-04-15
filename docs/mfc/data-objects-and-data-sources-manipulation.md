---
title: 'Datenobjekte und Datenquellen: Bearbeitung'
ms.date: 11/04/2016
helpviewer_keywords:
- data objects [MFC], manipulating
- data sources [MFC], data operations
- data sources [MFC], inserting data
- Clipboard [MFC], determining available formats
- OLE [MFC], data objects
- Clipboard [MFC], passing format information
- data sources [MFC], determining available formats
- delayed rendering [MFC]
- OLE [MFC], data sources
ms.assetid: f7f27e77-bb5d-4131-b819-d71bf929ebaf
ms.openlocfilehash: a08b6ff274c73d301c156d65aa56fbecca49128c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370554"
---
# <a name="data-objects-and-data-sources-manipulation"></a>Datenobjekte und Datenquellen: Bearbeitung

Nachdem ein Datenobjekt oder eine Datenquelle erstellt wurde, können Sie eine Reihe allgemeiner Vorgänge für die Daten ausführen, z. B. das Einfügen und Entfernen von Daten, das Aufzählen der Formate, in denen sich die Daten befinden, und vieles mehr. In diesem Artikel werden die Techniken beschrieben, die zum Abschließen der gängigsten Vorgänge erforderlich sind. Dabei werden folgende Themen behandelt:

- [Einfügen von Daten in eine Datenquelle](#_core_inserting_data_into_a_data_source)

- [Bestimmen der in einem Datenobjekt verfügbaren Formate](#_core_determining_the_formats_available_in_a_data_object)

- [Abrufen von Daten aus einem Datenobjekt](#_core_retrieving_data_from_a_data_object)

## <a name="inserting-data-into-a-data-source"></a><a name="_core_inserting_data_into_a_data_source"></a>Einfügen von Daten in eine Datenquelle

Wie Daten in eine Datenquelle eingefügt werden, hängt davon ab, ob die Daten sofort oder bei Bedarf bereitgestellt werden und in welchem Medium sie bereitgestellt werden. Die Möglichkeiten sind wie folgt.

### <a name="supplying-data-immediately-immediate-rendering"></a>Sofortige Bereitstellung von Daten (sofortiges Rendering)

- Rufen `COleDataSource::CacheGlobalData` Sie wiederholt für jedes Zwischenablageformat auf, in dem Sie Daten bereitstellen. Übergeben Sie das zu verwendende Zwischenablageformat, ein Handle an den Speicher, der die Daten enthält, und optional eine **FORMATETC-Struktur,** die die Daten beschreibt.

     - oder -

- Wenn Sie direkt mit **STGMEDIUM-Strukturen** `COleDataSource::CacheData` arbeiten `COleDataSource::CacheGlobalData` möchten, rufen Sie anstelle der obigen Option an.

### <a name="supplying-data-on-demand-delayed-rendering"></a>Bereitstellen von Daten bei Bedarf (verzögertes Rendering)

Dies ist ein fortgeschrittenes Thema.

- Rufen `COleDataSource::DelayRenderData` Sie wiederholt für jedes Zwischenablageformat auf, in dem Sie Daten bereitstellen. Übergeben Sie das zu verwendende Zwischenablageformat und optional eine **FORMATETC-Struktur,** die die Daten beschreibt. Wenn die Daten angefordert werden, `COleDataSource::OnRenderData`ruft das Framework auf , die Sie überschreiben müssen.

     - oder -

- Wenn Sie `CFile` ein Objekt zum Bereitstellen `COleDataSource::DelayRenderFileData` der `COleDataSource::DelayRenderData` Daten verwenden, rufen Sie die Daten auf und nicht in der vorherigen Option. Wenn die Daten angefordert werden, `COleDataSource::OnRenderFileData`ruft das Framework auf , die Sie überschreiben müssen.

## <a name="determining-the-formats-available-in-a-data-object"></a><a name="_core_determining_the_formats_available_in_a_data_object"></a>Bestimmen der in einem Datenobjekt verfügbaren Formate

Bevor eine Anwendung dem Benutzer das Einfügen von Daten ermöglicht, muss er wissen, ob es Formate in der Zwischenablage gibt, die er verarbeiten kann. Dazu sollte Ihre Anwendung wie folgt vorgehen:

1. Erstellen `COleDataObject` Sie ein Objekt und eine **FORMATETC-Struktur.**

1. Rufen Sie die `AttachClipboard` Memberfunktion des Datenobjekts auf, um das Datenobjekt den Daten in der Zwischenablage zuzuordnen.

1. Führen Sie eines der folgenden Verfahren aus:

   - Rufen Sie die `IsDataAvailable` Memberfunktion des Datenobjekts auf, wenn Sie nur ein oder zwei Formate benötigen. Dies spart Ihnen Zeit in Fällen, in denen die Daten in der Zwischenablage deutlich mehr Formate als Ihre Anwendung unterstützen.

     \- oder -

   - Rufen Sie die `BeginEnumFormats` Memberfunktion des Datenobjekts auf, um mit der Aufzählung der in der Zwischenablage verfügbaren Formate zu beginnen. Rufen `GetNextFormat` Sie dann auf, bis die Zwischenablage ein Format zurückgibt, das Ihre Anwendung unterstützt, oder es keine weiteren Formate mehr gibt.

Wenn Sie **ON_UPDATE_COMMAND_UI**verwenden, können Sie jetzt die Elemente Einfügen und möglicherweise Einfügen spezieller Elemente im Menü Bearbeiten aktivieren. Rufen Sie dazu `CMenu::EnableMenuItem` entweder `CCmdUI::Enable`oder an. Weitere Informationen dazu, was Containeranwendungen mit Menüelementen und wann tun sollten, finden Sie unter [Menüs und Ressourcen: Containererweiterungen](../mfc/menus-and-resources-container-additions.md).

## <a name="retrieving-data-from-a-data-object"></a><a name="_core_retrieving_data_from_a_data_object"></a>Abrufen von Daten aus einem Datenobjekt

Sobald Sie sich für ein Datenformat entschieden haben, bleibt nur noch das Abrufen der Daten aus dem Datenobjekt. Dazu entscheidet der Benutzer, wo die Daten abgelegt werden sollen, und die Anwendung ruft die entsprechende Funktion auf. Die Daten werden in einem der folgenden Medien verfügbar sein:

|Medium|Funktion zum Aufrufen|
|------------|----------------------|
|Globaler Speicher`HGLOBAL`( )|`COleDataObject::GetGlobalData`|
|Datei`CFile`( )|`COleDataObject::GetFileData`|
|**STGMEDIUM** Struktur`IStorage`( )|`COleDataObject::GetData`|

In der Regel wird das Medium zusammen mit dem Zwischenablageformat angegeben. Ein **CF_EMBEDDEDSTRUCT** Objekt befindet sich `IStorage` beispielsweise immer in einem Medium, das eine **STGMEDIUM-Struktur** erfordert. Daher würden Sie `GetData` verwenden, weil es die einzige dieser Funktionen ist, die eine **STGMEDIUM-Struktur** akzeptieren können.

Für Fälle, in denen sich `IStream` `HGLOBAL` das Zwischenablageformat `CFile` in einem oder einem Medium befindet, kann das Framework einen Zeiger bereitstellen, der auf die Daten verweist. Die Anwendung kann dann Dateilesen verwenden, um die Daten auf die gleiche Weise wie das Importieren von Daten aus einer Datei abrufe. Im Wesentlichen ist dies die `OnRenderData` clientseitige Schnittstelle zu den und-Routinen `OnRenderFileData` in der Datenquelle.

Der Benutzer kann nun wie bei allen anderen Daten im gleichen Format Daten in das Dokument einfügen.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- [Drag &amp; Drop](../mfc/drag-and-drop-ole.md)

- [Zwischenablage](../mfc/clipboard.md)

## <a name="see-also"></a>Siehe auch

[Datenobjekte und Datenquellen (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject-Klasse](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource-Klasse](../mfc/reference/coledatasource-class.md)

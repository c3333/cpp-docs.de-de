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
ms.openlocfilehash: adbe2a77fb0069e9874ab20a51b3ab08aabbe1f6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447002"
---
# <a name="data-objects-and-data-sources-manipulation"></a>Datenobjekte und Datenquellen: Bearbeitung

Nachdem ein Datenobjekt oder eine Datenquelle erstellt wurde, können Sie eine Reihe allgemeiner Vorgänge für die Daten ausführen, z. b. das Einfügen und Entfernen von Daten, das Auflisten der Formate, in denen sich die Daten befinden, usw. In diesem Artikel werden die Verfahren beschrieben, die zum Ausführen der gängigsten Vorgänge erforderlich sind. Dabei werden folgende Themen behandelt:

- [Einfügen von Daten in eine Datenquelle](#_core_inserting_data_into_a_data_source)

- [Bestimmen der in einem Datenobjekt verfügbaren Formate](#_core_determining_the_formats_available_in_a_data_object)

- [Abrufen von Daten aus einem Datenobjekt](#_core_retrieving_data_from_a_data_object)

##  <a name="_core_inserting_data_into_a_data_source"></a>Einfügen von Daten in eine Datenquelle

Die Art und Weise, wie Daten in eine Datenquelle eingefügt werden, hängt davon ab, ob die Daten sofort oder Bedarfs gesteuert bereitgestellt werden und in welchem Medium Sie bereitgestellt werden. Es gibt folgende Möglichkeiten:

### <a name="supplying-data-immediately-immediate-rendering"></a>Sofortiges Bereitstellen von Daten (sofortiges Rendering)

- Ruft `COleDataSource::CacheGlobalData` wiederholt für jedes Zwischenablage Format auf, in dem Sie Daten bereitstellen. Übergeben Sie das zu verwendende Zwischenablage Format, ein Handle für den Arbeitsspeicher, der die Daten enthält, und optional eine **FORMATETC** -Struktur, die die Daten beschreibt.

     Oder

- Wenn Sie direkt mit **STGMEDIUM** -Strukturen arbeiten möchten, können Sie `COleDataSource::CacheData` anstelle `COleDataSource::CacheGlobalData` in der obigen Option verwenden.

### <a name="supplying-data-on-demand-delayed-rendering"></a>Bereitstellen von Daten bei Bedarf (verzögertes Rendering)

Dies ist ein erweitertes Thema.

- Ruft `COleDataSource::DelayRenderData` wiederholt für jedes Zwischenablage Format auf, in dem Sie Daten bereitstellen. Übergeben Sie das zu verwendende Zwischenablage Format und optional eine **FORMATETC** -Struktur, die die Daten beschreibt. Wenn die Daten angefordert werden, ruft das Framework `COleDataSource::OnRenderData`auf, das Sie überschreiben müssen.

     Oder

- Wenn Sie zum Bereitstellen der Daten ein `CFile` Objekt verwenden, müssen Sie `COleDataSource::DelayRenderFileData` anstelle von `COleDataSource::DelayRenderData` in der vorherigen Option abrufen. Wenn die Daten angefordert werden, ruft das Framework `COleDataSource::OnRenderFileData`auf, das Sie überschreiben müssen.

##  <a name="_core_determining_the_formats_available_in_a_data_object"></a>Bestimmen der in einem Datenobjekt verfügbaren Formate

Bevor eine Anwendung den Benutzern das Einfügen von Daten ermöglicht, muss Sie wissen, ob es Formate in der Zwischenablage gibt, die Sie verarbeiten kann. Zu diesem Zweck sollte Ihre Anwendung folgende Aktionen ausführen:

1. Erstellen Sie ein `COleDataObject`-Objekt und eine **FORMATETC** -Struktur.

1. Ruft die `AttachClipboard` Member-Funktion des Datenobjekts auf, um das Datenobjekt den Daten in der Zwischenablage zuzuordnen.

1. Führen Sie eines der folgenden Verfahren aus:

   - Wenn Sie nur ein oder zwei Formate benötigen, können Sie die `IsDataAvailable` Member-Funktion des Datenobjekts aufzurufen. Dadurch sparen Sie Zeit in Fällen, in denen die Daten in der Zwischenablage erheblich mehr Formate als Ihre Anwendung unterstützen.

     \- oder -

   - Ruft die `BeginEnumFormats` Member-Funktion des Datenobjekts auf, um mit dem Auflisten der in der Zwischenablage verfügbaren Formate zu beginnen. Dann wird `GetNextFormat` aufgerufen, bis die Zwischenablage ein von der Anwendung unterstützte Format zurückgibt, oder es sind keine weiteren Formate vorhanden.

Wenn Sie **ON_UPDATE_COMMAND_UI**verwenden, können Sie jetzt das Einfügen aktivieren und ggf. spezielle Elemente in das Menü Bearbeiten einfügen. Um dies zu erreichen, müssen Sie entweder `CMenu::EnableMenuItem` oder `CCmdUI::Enable`abrufen. Weitere Informationen dazu, welche Container Anwendungen mit Menü Elementen und wann zu tun sind, finden Sie unter [Menüs und Ressourcen: Container Ergänzungen](../mfc/menus-and-resources-container-additions.md).

##  <a name="_core_retrieving_data_from_a_data_object"></a>Abrufen von Daten aus einem Datenobjekt

Nachdem Sie sich für ein Datenformat entschieden haben, müssen Sie nur noch die Daten aus dem Datenobjekt abrufen. Zu diesem Zweck entscheidet der Benutzer, wo die Daten abgelegt werden sollen, und die Anwendung ruft die entsprechende Funktion auf. Die Daten sind in einem der folgenden Medien verfügbar:

|Medium|Aufzurufende Funktion|
|------------|----------------------|
|Globaler Speicher (`HGLOBAL`)|`COleDataObject::GetGlobalData`|
|Datei (`CFile`)|`COleDataObject::GetFileData`|
|**STGMEDIUM** -Struktur (`IStorage`)|`COleDataObject::GetData`|

Im Allgemeinen wird das Medium zusammen mit seinem Zwischenablage Format angegeben. Ein **CF_EMBEDDEDSTRUCT** -Objekt befindet sich z. b. immer in einem `IStorage` Medium, das eine **STGMEDIUM** -Struktur erfordert. Daher verwenden Sie `GetData`, da es sich dabei um die einzige dieser Funktionen handelt, die eine **STGMEDIUM** -Struktur akzeptieren können.

In Fällen, in denen sich das Zwischenablage Format in einem `IStream` oder `HGLOBAL` Medium befindet, kann das Framework einen `CFile` Zeiger bereitstellen, der auf die Daten verweist. Die Anwendung kann dann mit dem Datei Lesevorgang die Daten auf die gleiche Weise wie Daten aus einer Datei importieren. Im Wesentlichen handelt es sich hierbei um die Client seitige Schnittstelle zu den `OnRenderData`-und `OnRenderFileData` Routinen in der Datenquelle.

Der Benutzer kann jetzt genau wie für alle anderen Daten im gleichen Format Daten in das Dokument einfügen.

### <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr erfahren?

- [Drag & Drop](../mfc/drag-and-drop-ole.md)

- [Zwischenablage](../mfc/clipboard.md)

## <a name="see-also"></a>Weitere Informationen

[Datenobjekte und Datenquellen (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject-Klasse](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource-Klasse](../mfc/reference/coledatasource-class.md)

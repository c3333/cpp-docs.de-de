---
title: 'Datenobjekte und Datenquellen: Erstellen und Zerstören'
ms.date: 11/04/2016
helpviewer_keywords:
- destroying data objects [MFC]
- object creation [MFC], data source objects
- data sources [MFC], and data objects
- data source objects [MFC], creating
- destruction [MFC], data sources
- data source objects [MFC], destroying
- data objects [MFC], creating
- data objects [MFC], destroying
- data sources [MFC], role
- data sources [MFC], destroying
- destruction [MFC], data objects
- data sources [MFC], creating
ms.assetid: ac216d54-3ca5-4ce7-850d-cd1f6a90d4f1
ms.openlocfilehash: 58b68ca9597fd2a03cffb2bbab327dbc72d09599
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371218"
---
# <a name="data-objects-and-data-sources-creation-and-destruction"></a>Datenobjekte und Datenquellen: Erstellen und Zerstören

Wie im Artikel [Datenobjekte und Datenquellen (OLE)](../mfc/data-objects-and-data-sources-ole.md)erläutert, stellen Datenobjekte und Datenquellen beide Seiten einer Datenübertragung dar. In diesem Artikel wird erläutert, wann diese Objekte und Quellen erstellt und zerstört werden, um die Datenübertragungen ordnungsgemäß durchführen zu können, einschließlich:

- [Erstellen von Datenobjekten](#_core_creating_data_objects)

- [Zerstören von Datenobjekten](#_core_destroying_data_objects)

- [Erstellen von Datenquellen](#_core_creating_data_sources)

- [Zerstören von Datenquellen](#_core_destroying_data_sources)

## <a name="creating-data-objects"></a><a name="_core_creating_data_objects"></a>Erstellen von Datenobjekten

Datenobjekte werden von der Zielanwendung verwendet, wobei es sich entweder um den Client oder Server handelt. Ein Datenobjekt in der Zielanwendung ist ein Ende der Verbindung zwischen der Quellanwendung und der Zielanwendung. Ein Datenobjekt in der Zielanwendung wird verwendet, um auf die Daten in der Datenquelle zuzugreifen und damit zu interagieren.

Es gibt zwei häufige Situationen, in denen ein Datenobjekt erforderlich ist. Die erste Situation: Daten werden mithilfe von Drag &amp; Drop in Ihrer Anwendung abgelegt. Die zweite Situation: Im Menü „Bearbeiten“ wird die Option „Einfügen“ oder „Inhalte einfügen“ ausgewählt.

In einer Drag-and-Drop-Situation müssen Sie kein Datenobjekt erstellen. Ein Zeiger auf ein vorhandenes Datenobjekt wird an die `OnDrop`-Funktion übergeben. Dieses Datenobjekt wird vom Framework als Teil des Drag-and-Drop-Vorgangs erstellt und auch durch es zerstört. Dies ist nicht immer der Fall, wenn das Einfügen mit einer anderen Methode erfolgt. Weitere Informationen finden Sie unter [zerstören von Datenobjekten](#_core_destroying_data_objects).

Wenn die Anwendung einen „Einfügen“- oder „Inhalte einfügen“-Vorgang durchführt, sollten Sie ein `COleDataObject`-Objekt erstellen und seine `AttachClipboard`-Memberfunktion aufrufen. Hierdurch wird das Datenobjekt den Daten in der Zwischenablage zugeordnet. Sie können dieses Datenobjekt dann in Ihrer Einfügefunktion verwenden.

## <a name="destroying-data-objects"></a><a name="_core_destroying_data_objects"></a>Zerstören von Datenobjekten

Wenn Sie dem unter [Erstellen von Datenobjekten](#_core_creating_data_objects)beschriebenen Schema folgen, ist das zerstören von Datenobjekten ein trivialer Aspekt der Datenübertragungen. Das beim Einfügen erstellte Datenobjekt wird von MFC zerstört, wenn die Einfügefunktion zurückkehrt.

Wenn Sie eine andere Methode für Einfügeoperationen anwenden, stellen Sie sicher, dass das Datenobjekt nach Abschluss des Einfügevorgangs zerstört wird. Solange das Datenobjekt nicht zerstört ist, kann keine Anwendung Daten in die Zwischenablage kopieren.

## <a name="creating-data-sources"></a><a name="_core_creating_data_sources"></a>Erstellen von Datenquellen

Datenquellen werden von der Quelle der Datenübertragung verwendet, bei der es sich entweder um die Clientseite oder die Serverseite der Datenübertragung handelt. Eine Datenquelle in der Quellanwendung ist ein Ende der Verbindung zwischen der Quellanwendung und der Zielanwendung. Ein Datenobjekt in der Zielanwendung wird verwendet, um auf die Daten in der Datenquelle zuzugreifen und damit zu interagieren.

Datenquellen werden erstellt, wenn eine Anwendung Daten in die Zwischenablage kopieren muss. Ein typisches Szenario sieht folgendermaßen aus:

1. Der Benutzer wählt einige Daten aus.

1. Der Benutzer wählt im Menü **Bearbeiten** die Option **Kopieren** (oder **Ausschneiden**) aus oder beginnt einen Drag & Drop-Vorgang.

1. Je nach Entwurf des Programms erstellt die Anwendung entweder ein `COleDataSource`-Objekt oder ein Objekt von einer Klasse, die von der `COleDataSource` abgeleitet wird.

1. Die ausgewählten Daten werden in die Datenquelle eingefügt, indem eine der Funktionen in der `COleDataSource::CacheData`-Gruppe oder `COleDataSource::DelayRenderData`-Gruppe aufgerufen wird.

1. Die Anwendung ruft die `SetClipboard`-Memberfunktion auf (bzw. die `DoDragDrop`-Memberfunktion, wenn es sich um einen Drag-and-Drop-Vorgang handelt), die zu dem in Schritt 3 erstellten Objekt gehört.

1. Wenn dies ein **Ausschneide** Vorgang ist `DoDragDrop` oder **DROPEFFECT_MOVE**zurückgibt, werden die in Schritt 1 ausgewählten Daten aus dem Dokument gelöscht.

Dieses Szenario wird von den MFC-OLE-Beispielen [OCLIENT](../overview/visual-cpp-samples.md) und [HIERSVR](../overview/visual-cpp-samples.md)implementiert. Suchen Sie in der Quelle nach der von `CView` abgeleiteten Klasse der einzelnen Anwendungen, außer nach den Funktionen `GetClipboardData` und `OnGetClipboardData`. Diese beiden Funktionen befinden sich in den Implementierungen der von `COleClientItem` oder `COleServerItem` abgeleiteten Klassen. Diese Programme sind ein gutes Beispiel dafür, wie diese Konzepte implementiert werden können.

Eine andere Situation, in der Sie möglicherweise ein `COleDataSource`-Objekt erstellen möchten, besteht dann, wenn Sie das Standardverhalten eines Drag-and-Drop-Vorgangs ändern. Weitere Informationen finden Sie im Artikel [Drag & Drop: Anpassen des Drag](../mfc/drag-and-drop-ole.md#customize-drag-and-drop) & Drop-Artikels.

## <a name="destroying-data-sources"></a><a name="_core_destroying_data_sources"></a>Zerstören von Datenquellen

Datenquellen müssen von der Anwendung zerstört werden, die derzeit für sie verantwortlich ist. In Situationen, in denen Sie die Datenquelle an OLE übergeben, z. b. das Aufrufen von [COleDataSource::D odragdrop](../mfc/reference/coledatasource-class.md#dodragdrop), müssen Sie aufrufen `pDataSrc->InternalRelease`. Beispiel:

[!code-cpp[NVC_MFCListView#1](../atl/reference/codesnippet/cpp/data-objects-and-data-sources-creation-and-destruction_1.cpp)]

Wenn Sie die Datenquelle nicht an OLE übergeben haben, sind Sie verantwortlich dafür, sie zu zerstören, wie dies bei jedem typischen C++-Objekt der Fall ist.

Weitere Informationen finden Sie unter [Drag & Drop](../mfc/drag-and-drop-ole.md), [Clipboard](../mfc/clipboard.md)und [Manipulation von Datenobjekten und Datenquellen](../mfc/data-objects-and-data-sources-manipulation.md).

## <a name="see-also"></a>Weitere Informationen

[Datenobjekte und Datenquellen (OLE)](../mfc/data-objects-and-data-sources-ole.md)<br/>
[COleDataObject-Klasse](../mfc/reference/coledataobject-class.md)<br/>
[COleDataSource-Klasse](../mfc/reference/coledatasource-class.md)

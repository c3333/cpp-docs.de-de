---
title: 'Container: Verbunddateien'
ms.date: 11/04/2016
helpviewer_keywords:
- compound files [MFC]
- compound documents
- containers [MFC], compound files
- OLE documents [MFC], compound files
- performance [MFC], compound files
- files [MFC], compound
- standardized file structure compound files
- documents [MFC], compound
- documents [MFC], OLE
- OLE containers [MFC], compound files
- access modes for files [MFC]
ms.assetid: 8b83cb3e-76c8-4bbe-ba16-737092b36f49
ms.openlocfilehash: 344c444602555e2b5c145e58d237586199b9e1ed
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624819"
---
# <a name="containers-compound-files"></a>Container: Verbunddateien

In diesem Artikel werden die Komponenten und die Implementierung von Verbund Dateien sowie die vor-und Nachteile der Verwendung von Verbund Dateien in ihren OLE-Anwendungen erläutert.

Verbund Dateien sind integraler Bestandteil von OLE. Sie werden verwendet, um die Datenübertragung und den OLE-Dokument Speicher zu vereinfachen. Verbund Dateien sind eine Implementierung des aktiven strukturierten Speicher Modells. Es gibt konsistente Schnittstellen, die die Serialisierung in einem Speicher, einem Stream oder einem Datei Objekt unterstützen. Verbund Dateien werden im-Microsoft Foundation Class-Bibliothek von den-Klassen `COleStreamFile` und unterstützt `COleDocument` .

> [!NOTE]
> Die Verwendung einer Verbund Datei impliziert nicht, dass die Informationen aus einem OLE-Dokument oder einem Verbund Dokument stammen. Verbund Dateien sind nur eine der Möglichkeiten, Verbund Dokumente, OLE-Dokumente und andere Daten zu speichern.

## <a name="components-of-a-compound-file"></a><a name="_core_components_of_a_compound_file"></a>Komponenten einer Verbund Datei

Die OLE-Implementierung von Verbund Dateien verwendet drei Objekttypen: Streamobjekte, Speicher Objekte und `ILockBytes` Objekte. Diese Objekte ähneln den Komponenten eines Standarddatei Systems auf folgende Weise:

- Stream-Objekte, wie z. b. Dateien, speichern Daten eines beliebigen Typs.

- Speicher Objekte, wie z. b. Verzeichnisse, können andere Speicher-und Streamobjekte enthalten.

- `LockBytes`-Objekte stellen die Schnittstelle zwischen den Speicher Objekten und der physischen Hardware dar. Sie bestimmen, wie die tatsächlichen Bytes auf das Speichergerät geschrieben werden, auf das das `LockBytes` Objekt zugreift, z. b. auf eine Festplatte oder einen Bereich des globalen Speichers. Weitere Informationen zu `LockBytes` Objekten und der `ILockBytes` -Schnittstelle finden Sie in der *OLE-Programmier Referenz*.

## <a name="advantages-and-disadvantages-of-compound-files"></a><a name="_core_advantages_and_disadvantages_of_compound_files"></a>Vor-und Nachteile von Verbund Dateien

Verbund Dateien bieten Vorteile, die mit früheren Methoden zum Speichern von Dateien nicht verfügbar sind. Dazu gehören:

- Inkrementeller Dateizugriff.

- Datei Zugriffs Modi.

- Standardisierung der Dateistruktur.

Mögliche Nachteile von Verbund Dateien – große Größen-und Leistungsprobleme im Zusammenhang mit dem Speicher auf Disketten Scheiben – sollten bei der Entscheidung berücksichtigt werden, ob Sie in Ihrer Anwendung verwendet werden sollen.

### <a name="incremental-access-to-files"></a><a name="_core_incremental_access_to_files"></a>Inkrementeller Zugriff auf Dateien

Der inkrementelle zugreifen auf Dateien ist ein automatischer Vorteil der Verwendung von Verbund Dateien. Da eine Verbund Datei als "Dateisystem in einer Datei" angezeigt werden kann, kann auf einzelne Objekttypen wie Stream oder Speicher zugegriffen werden, ohne dass die gesamte Datei geladen werden muss. Dies kann die Zeit, die eine Anwendung benötigt, um für die Bearbeitung durch den Benutzer auf neue Objekte zuzugreifen, drastisch verkürzen. Ein inkrementelles Update, das auf dem gleichen Konzept basiert, bietet ähnliche Vorteile. Anstatt die gesamte Datei zu speichern, um die an einem Objekt vorgenommenen Änderungen zu speichern, speichert OLE nur den Stream oder das Speicher Objekt, das vom Benutzer bearbeitet wurde.

### <a name="file-access-modes"></a><a name="_core_file_access_modes"></a>Datei Zugriffs Modi

Wenn Sie feststellen können, wann Änderungen an Objekten in einer Verbund Datei auf den Datenträger übertragen werden, ist dies ein weiterer Vorteil der Verwendung von Verbund Dateien. Der Modus, in dem auf Dateien zugegriffen wird, entweder transaktiv oder direkt, bestimmt, wann für Änderungen ein Commit ausgeführt wird.

- Der transaktive Modus verwendet einen Zweiphasencommit-Vorgang, um Änderungen an Objekten in einer Verbund Datei vorzunehmen, sodass sowohl die alte als auch die neue Kopie des Dokuments verfügbar bleiben, bis der Benutzer die Änderungen entweder speichern oder rückgängig machen möchte.

- Der direkte Modus schließt Änderungen am Dokument ein, während diese vorgenommen werden, ohne dass diese später rückgängig gemacht werden können.

Weitere Informationen zu Zugriffs Modi finden Sie in der *OLE-Programmier Referenz*.

### <a name="standardization"></a><a name="_core_standardization"></a>Standardisierung

Die standardisierte Struktur von Verbund Dateien ermöglicht unterschiedlichen OLE-Anwendungen das Durchsuchen von Verbund Dateien, die von Ihrer OLE-Anwendung erstellt wurden, ohne dass die Anwendung, die die Datei tatsächlich erstellt hat, bekannt ist.

### <a name="size-and-performance-considerations"></a><a name="_core_size_and_performance_considerations"></a>Überlegungen zur Größe und Leistung

Aufgrund der Komplexität der Verbund Dateispeicher Struktur und der inkrementellen Speicherung von Daten sind Dateien, die dieses Format verwenden, tendenziell größer als andere Dateien, die unstrukturierte oder Flatfile-Speicher verwenden. Wenn Ihre Anwendung häufig Dateien lädt und speichert, kann die Verwendung von Verbund Dateien dazu führen, dass die Dateigröße viel schneller als nicht Verbund Dateien erhöht wird. Da Verbund Dateien sehr groß werden können, kann die Zugriffszeit für Dateien, die auf Disketten Datenträgern gespeichert und geladen werden, ebenfalls beeinträchtigt werden, wodurch der Zugriff auf Dateien langsamer wird.

Ein weiteres Problem, das die Leistung beeinträchtigt, ist die Fragmentierung der Verbund Datei. Die Größe einer Verbund Datei wird durch den Unterschied zwischen der ersten und der letzten Datenträger Sektoren festgelegt, die von der Datei verwendet werden. Eine fragmentierte Datei kann viele Bereiche von freiem Speicherplatz enthalten, die keine Daten enthalten, sondern beim Berechnen der Größe gezählt werden. Während der Lebensdauer einer Verbund Datei werden diese Bereiche durch das Einfügen oder Löschen von Speicher Objekten erstellt.

## <a name="using-compound-files-format-for-your-data"></a><a name="_core_using_compound_files_format_for_your_data"></a>Verwenden des zusammengesetzten Datei Formats für Ihre Daten

Nachdem Sie eine Anwendung erfolgreich erstellt haben, die über eine von abgeleitete Dokument Klasse verfügt `COleDocument` , stellen Sie sicher, dass der Hauptdokumentkonstruktor aufruft `EnableCompoundFile` . Wenn der Anwendungs-Assistent OLE-Container Anwendungen erstellt, wird dieser Befehl für Sie eingefügt.

Informationen zum *OLE-Programmierer*finden Sie unter [IStream](/windows/win32/api/objidl/nn-objidl-istream), [IStorage](/windows/win32/api/objidl/nn-objidl-istorage)und [ILockBytes](/windows/win32/api/objidl/nn-objidl-ilockbytes).

## <a name="see-also"></a>Siehe auch

[Container](containers.md)<br/>
[Container: Probleme mit der Benutzeroberfläche](containers-user-interface-issues.md)<br/>
[Colestreamfile-Klasse](reference/colestreamfile-class.md)<br/>
[COleDocument-Klasse](reference/coledocument-class.md)

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
ms.openlocfilehash: 98166a355fd267ecbec0a7f0cc1d18fd0b2e7cd0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353589"
---
# <a name="containers-compound-files"></a>Container: Verbunddateien

In diesem Artikel werden die Komponenten und die Implementierung zusammengesetzter Dateien sowie die Vor- und Nachteile der Verwendung zusammengesetzter Dateien in Ihren OLE-Anwendungen erläutert.

Zusammengesetzte Dateien sind ein integraler Bestandteil von OLE. Sie werden verwendet, um die Datenübertragung und die Ole-Dokumentspeicherung zu erleichtern. Zusammengesetzte Dateien sind eine Implementierung des Active-Strukturspeichermodells. Es gibt konsistente Schnittstellen, die die Serialisierung in einen Speicher, einen Stream oder ein Dateiobjekt unterstützen. Zusammengesetzte Dateien werden in der Microsoft `COleStreamFile` Foundation-Klassenbibliothek von den Klassen und `COleDocument`unterstützt.

> [!NOTE]
> Die Verwendung einer zusammengesetzten Datei bedeutet nicht, dass die Informationen aus einem OLE-Dokument oder einem zusammengesetzten Dokument stammen. Zusammengesetzte Dateien sind nur eine der Möglichkeiten zum Speichern zusammengesetzter Dokumente, OLE-Dokumente und anderer Daten.

## <a name="components-of-a-compound-file"></a><a name="_core_components_of_a_compound_file"></a>Komponenten einer zusammengesetzten Datei

Die OLE-Implementierung zusammengesetzter Dateien verwendet drei Objekttypen: `ILockBytes` Streamobjekte, Speicherobjekte und Objekte. Diese Objekte ähneln den Komponenten eines Standarddateisystems auf folgende Weise:

- Streamen von Objekten, wie Dateien, speichern Daten jedes Typs.

- Speicherobjekte können, z. B. Verzeichnisse, andere Speicher- und Streamobjekte enthalten.

- `LockBytes`Objekte stellen die Schnittstelle zwischen den Speicherobjekten und der physischen Hardware dar. Sie bestimmen, wie die tatsächlichen Bytes `LockBytes` auf das Speichergerät geschrieben werden, auf das das Objekt zugreift, z. B. auf eine Festplatte oder einen Bereich des globalen Speichers. Weitere Informationen `LockBytes` zu Objekten `ILockBytes` und der Schnittstelle finden Sie in der *Referenz des OLE-Programmierers*.

## <a name="advantages-and-disadvantages-of-compound-files"></a><a name="_core_advantages_and_disadvantages_of_compound_files"></a>Vor- und Nachteile von Verbunddateien

Zusammengesetzte Dateien bieten Vorteile, die mit früheren Methoden der Dateispeicherung nicht verfügbar sind. Dazu gehören:

- Inkrementeller Dateizugriff.

- Dateizugriffsmodi.

- Standardisierung der Dateistruktur.

Die potenziellen Nachteile von zusammengesetzten Dateien – große Größe und Leistungsprobleme im Zusammenhang mit der Speicherung auf Disketten – sollten bei der Entscheidung, ob sie in Ihrer Anwendung verwendet werden sollen, berücksichtigt werden.

### <a name="incremental-access-to-files"></a><a name="_core_incremental_access_to_files"></a>Inkrementeller Zugriff auf Dateien

Der inkrementelle Zugriff auf Dateien ist ein automatischer Vorteil der Verwendung zusammengesetzter Dateien. Da eine zusammengesetzte Datei als "Dateisystem innerhalb einer Datei" angezeigt werden kann, kann auf einzelne Objekttypen, z. B. Stream oder Speicher, zugegriffen werden, ohne dass die gesamte Datei geladen werden muss. Dies kann die Zeit, die eine Anwendung für den Zugriff auf neue Objekte zur Bearbeitung durch den Benutzer benötigt, drastisch verringern. Die inkrementelle Aktualisierung, die auf dem gleichen Konzept basiert, bietet ähnliche Vorteile. Anstatt die gesamte Datei zu speichern, nur um die an einem Objekt vorgenommenen Änderungen zu speichern, speichert OLE nur den Vom Benutzer bearbeiteten Stream oder Speicherobjekt.

### <a name="file-access-modes"></a><a name="_core_file_access_modes"></a>Dateizugriffsmodi

Die Möglichkeit zu bestimmen, wann Änderungen an Objekten in einer zusammengesetzten Datei an den Datenträger übertragen werden, ist ein weiterer Vorteil der Verwendung zusammengesetzter Dateien. Der Modus, in dem auf Dateien zugegriffen wird, entweder transacted oder direct, bestimmt, wann Änderungen festgeschrieben werden.

- Der transacted-Modus verwendet einen zweiphasigen Commit-Vorgang, um Änderungen an Objekten in einer zusammengesetzten Datei vorzunehmen, wodurch sowohl die alte als auch die neue Kopie des Dokuments verfügbar bleiben, bis der Benutzer die Änderungen entweder speichern oder rückgängig machen möchte.

- Der Direktmodus enthält Änderungen am Dokument, während sie vorgenommen werden, ohne dass sie später rückgängig gemacht werden können.

Weitere Informationen zu Zugriffsmodi finden Sie in der *Referenz des OLE-Programmierers*.

### <a name="standardization"></a><a name="_core_standardization"></a>Standardisierung

Die standardisierte Struktur von zusammengesetzten Dateien ermöglicht es verschiedenen OLE-Anwendungen, zusammengesetzte Dateien zu durchsuchen, die von Ihrer OLE-Anwendung erstellt wurden, ohne Kenntnis der Anwendung, die die Datei tatsächlich erstellt hat.

### <a name="size-and-performance-considerations"></a><a name="_core_size_and_performance_considerations"></a>Größen- und Leistungsüberlegungen

Aufgrund der Komplexität der zusammengesetzten Dateispeicherstruktur und der Möglichkeit, Daten inkrementell zu speichern, sind Dateien, die dieses Format verwenden, in der Regel größer als andere Dateien, die unstrukturierten oder "flachen" Speicher verwenden. Wenn Ihre Anwendung häufig Dateien lädt und speichert, kann die Verwendung von zusammengesetzten Dateien dazu führen, dass die Dateigröße viel schneller ansteigt als nicht zusammengesetzte Dateien. Da zusammengesetzte Dateien groß werden können, kann auch die Zugriffszeit für Dateien beeinflusst werden, die auf Disketten gespeichert und von Disketten geladen werden, was zu einem langsameren Zugriff auf Dateien führt.

Ein weiteres Problem, das sich auf die Leistung auswirkt, ist die Fragmentierung von Zusammengesetzten Dateien. Die Größe einer zusammengesetzten Datei wird durch den Unterschied zwischen dem ersten und dem letzten Datenträgersektor bestimmt, der von der Datei verwendet wird. Eine fragmentierte Datei kann viele Bereiche des freien Speicherplatzes enthalten, die keine Daten enthalten, aber bei der Berechnung der Größe gezählt werden. Während der Lebensdauer einer zusammengesetzten Datei werden diese Bereiche durch Einfügen oder Löschen von Speicherobjekten erstellt.

## <a name="using-compound-files-format-for-your-data"></a><a name="_core_using_compound_files_format_for_your_data"></a>Verwenden des Formats für zusammengesetzte Dateien für Ihre Daten

Nach dem erfolgreichen Erstellen einer Anwendung, `COleDocument`die über eine dokumentklasse `EnableCompoundFile`verfügt, die von abgeleitet ist, stellen Sie sicher, dass der Hauptdokumentkonstruktor aufruft. Wenn der Anwendungsassistent OLE-Containeranwendungen erstellt, wird dieser Aufruf für Sie eingefügt.

In der *Referenz des OLE-Programmierers*siehe [IStream](/windows/win32/api/objidl/nn-objidl-istream), [IStorage](/windows/win32/api/objidl/nn-objidl-istorage)und [ILockBytes](/windows/win32/api/objidl/nn-objidl-ilockbytes).

## <a name="see-also"></a>Siehe auch

[Container](../mfc/containers.md)<br/>
[Container: Probleme mit der Benutzeroberfläche](../mfc/containers-user-interface-issues.md)<br/>
[COleStreamFile-Klasse](../mfc/reference/colestreamfile-class.md)<br/>
[COleDocument-Klasse](../mfc/reference/coledocument-class.md)

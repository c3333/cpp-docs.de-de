---
title: Dateien in MFC
ms.date: 11/04/2016
helpviewer_keywords:
- serialization [MFC], MFC files
- I/O [MFC], MFC classes
- files [MFC], MFC
- files [MFC], serialization
- binary access, binary file operations in MFC
- file I/O classes [MFC]
- I/O [MFC]
- persistence [MFC]
- MFC, file operations
- files [MFC], manipulating
- binary access [MFC]
ms.assetid: ae25e2c5-2859-4679-ab97-438824e93ce1
ms.openlocfilehash: 8b8859e188e42f4419ca7ee7f683cc31de0c75b3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625882"
---
# <a name="files-in-mfc"></a>Dateien in MFC

In der Microsoft Foundation Class-Bibliothek (MFC) verarbeitet Class [CFile](reference/cfile-class.md) normale Datei-e/a-Vorgänge. Diese Artikel Familie erläutert das Öffnen und Schließen von Dateien sowie das Lesen und Schreiben von Daten in diese Dateien. Außerdem werden Dateistatus Vorgänge erörtert. Eine Beschreibung der Verwendung der objektbasierten Serialisierungsfeatures von MFC als Alternative zum Lesen und Schreiben von Daten in Dateien finden Sie im Artikel [Serialisierung](serialization-in-mfc.md).

> [!NOTE]
> Wenn Sie MFC- `CDocument` Objekte verwenden, führt das Framework einen Großteil der serialisierungsaufgaben für Sie aus. Insbesondere das-Framework erstellt und verwendet das- `CFile` Objekt. Sie müssen nur Code in der Überschreibung der Member- `Serialize` Funktion der-Klasse schreiben `CDocument` .

Die- `CFile` Klasse stellt eine Schnittstelle für allgemeine Binärdatei Vorgänge bereit. Die `CStdioFile` Klassen und, die `CMemFile` von abgeleitet werden, `CFile` und die `CSharedFile` von abgeleitete Klasse `CMemFile` stellen speziellere Dateidienste bereit.

Weitere Informationen zu Alternativen zur MFC-Datei Behandlung finden Sie unter [Datei Behandlung](../c-runtime-library/file-handling.md) in der *Lauf Zeit Bibliotheks Referenz*.

Informationen zu abgeleiteten `CFile` Klassen finden Sie im [MFC-Hierarchie Diagramm](hierarchy-chart.md).

## <a name="what-do-you-want-to-do"></a>Was möchten Sie tun?

*CFile verwenden*

- [Öffnen einer Datei mit CFile](opening-files.md)

- [Lesen und Schreiben einer Datei mit CFile](reading-and-writing-files.md)

- [Datei mit CFile schließen](closing-files.md)

- [Zugreifen auf den Dateistatus mit CFile](accessing-file-status.md)

*Verwenden der MFC-Serialisierung (Objekt Persistenz)*

- [Erstellen einer serialisierbaren Klasse](serialization-making-a-serializable-class.md)

- [Serialisieren eines Objekts über ein CArchive-Objekt](serialization-serializing-an-object.md)

- [Erstellen eines CArchive-Objekts](two-ways-to-create-a-carchive-object.md)

- [Verwenden von CArchive-<\< and >>-Operatoren](using-the-carchive-output-and-input-operators.md)

- [Speichern und Laden von CObjects und mit CObject abgeleiteten Objekten über ein Archiv](storing-and-loading-cobjects-via-an-archive.md)

## <a name="see-also"></a>Siehe auch

[Konzepte](mfc-concepts.md)<br/>
[Allgemeine MFC-Themen](general-mfc-topics.md)<br/>
[CArchive-Klasse](reference/carchive-class.md)<br/>
[CObject-Klasse](reference/cobject-class.md)

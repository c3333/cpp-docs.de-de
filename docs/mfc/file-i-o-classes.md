---
title: Datei-e/a-Klassen
ms.date: 11/04/2016
f1_keywords:
- vc.classes.file
helpviewer_keywords:
- disk file classes [MFC]
- stdio classes [MFC]
- OLE streams [MFC]
- I/O [MFC], MFC classes
- translated stream classes [MFC]
- file I/O classes [MFC]
- I/O [MFC], classes
- sockets classes [MFC]
- stream classes [MFC]
- memory file classes [MFC]
ms.assetid: 92821c3f-d9e1-47f6-98c9-3b632d86e811
ms.openlocfilehash: 2fcf4dfc1388df0df2bc25928ec8541486c6bb2d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615672"
---
# <a name="file-io-classes"></a>Klassen für Datei-E/A

Diese Klassen stellen eine Schnittstelle zu herkömmlichen Datenträger Dateien, in-Memory-Dateien, aktiven Streams und Windows Sockets bereit. Alle von abgeleiteten Klassen `CFile` können mit einem-Objekt verwendet werden `CArchive` , um die Serialisierung auszuführen.

Verwenden Sie die folgenden Klassen, insbesondere `CArchive` und `CFile` , wenn Sie Ihre eigene Eingabe-/Ausgabeverarbeitung schreiben. Normalerweise müssen Sie diese Klassen nicht ableiten. Wenn Sie das Anwendungs Framework verwenden, verarbeiten die Standard Implementierungen der Befehle zum **Öffnen** und **Speichern** im Menü **Datei** die Datei-e/a (mithilfe der `CArchive` -Klasse), solange Sie die Funktion des Dokuments überschreiben, `Serialize` um Details dazu bereitzustellen, wie ein Dokument seinen Inhalt serialisiert. Weitere Informationen zu den Datei Klassen und der Serialisierung finden Sie in den Artikeln zu den [Dateien in MFC](files-in-mfc.md) und im Artikel [Serialization](serialization-in-mfc.md).

[CFile](reference/cfile-class.md)<br/>
Stellt eine Datei Schnittstelle für Binär Datenträgerdateien bereit.

[CStdioFile](reference/cstdiofile-class.md)<br/>
Stellt eine `CFile` Schnittstelle für gepufferte Datenstrom-Datenträger Dateien bereit, normalerweise im Textmodus.

[CMemFile](reference/cmemfile-class.md)<br/>
Stellt eine `CFile` Schnittstelle für in-Memory-Dateien bereit.

[CSharedFile](reference/csharedfile-class.md)<br/>
Stellt eine- `CFile` Schnittstelle für freigegebene in-Memory-Dateien bereit.

[COleStreamFile](reference/colestreamfile-class.md)<br/>
Verwendet die com- `IStream` Schnittstelle, um `CFile` Zugriff auf Verbund Dateien bereitzustellen.

[CSocketFile](reference/csocketfile-class.md)<br/>
Stellt eine `CFile` Schnittstelle für einen Windows-Socket bereit.

## <a name="related-classes"></a>Verwandte Klassen

[CArchive](reference/carchive-class.md)<br/>
Kooperiert mit einem- `CFile` Objekt, um mithilfe der Serialisierung permanenten Speicher für Objekte zu implementieren (siehe [CObject:: Serialize](reference/cobject-class.md#serialize)).

[CArchiveException](reference/carchiveexception-class.md)<br/>
Eine Archiv Ausnahme.

[CFileException](reference/cfileexception-class.md)<br/>
Eine Datei orientierte Ausnahme.

[CFileDialog](reference/cfiledialog-class.md)<br/>
Stellt ein Standard Dialogfeld zum Öffnen oder Speichern einer Datei bereit.

[CRecentFileList](reference/crecentfilelist-class.md)<br/>
Verwaltet die zuletzt verwendete Datei Liste (MRU).

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](class-library-overview.md)

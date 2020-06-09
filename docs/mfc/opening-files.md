---
title: Öffnen von Dateien
ms.date: 11/04/2016
helpviewer_keywords:
- Open member functions [MFC]
- CFile class [MFC], variable
- opening files, in MFC
- Open calls [MFC]
- Open method, CFile class [MFC]
- examples [MFC], opening files
- opening files, handling exceptions
- exception handling [MFC], when opening files
- files [MFC], opening
- file objects [MFC]
- MFC, file operations
- opening files [MFC]
- exception handling [MFC], opening files
ms.assetid: a991b8ec-b04a-4766-b47e-7485b5dd0b01
ms.openlocfilehash: 73407eba802b7640e880b821144954fa6442f177
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622163"
---
# <a name="opening-files"></a>Öffnen von Dateien

In MFC ist die gängigste Art, eine Datei zu öffnen, ein zweistufiger Prozess.

#### <a name="to-open-a-file"></a>So öffnen Sie eine Datei

1. Erstellen Sie das Datei Objekt ohne Angabe eines Pfads oder Berechtigungs Flags.

   Normalerweise erstellen Sie ein Datei Objekt, indem Sie eine [CFile](reference/cfile-class.md) -Variable im Stapel Rahmen deklarieren.

1. Ruft die [Open](reference/cfile-class.md#open) Member-Funktion für das File-Objekt auf, wobei ein Pfad und Berechtigungs Flags bereitgestellt werden.

   Der Rückgabewert für ist `Open` nicht 0 (null), wenn die Datei erfolgreich geöffnet wurde, oder 0, wenn die angegebene Datei nicht geöffnet werden konnte. Die `Open` Member-Funktion ist wie folgt prototyptypisiert:

   `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`

   Die öffnenden Flags geben an, welche Berechtigungen, z. b. "schreibgeschützt", für die Datei benötigen. Die möglichen Flagwerte werden als Enumerationskonstanten innerhalb der `CFile` Klasse definiert, sodass Sie mit " `CFile::` " wie in qualifiziert werden `CFile::modeRead` . Verwenden Sie das- `CFile::modeCreate` Flag, wenn Sie die Datei erstellen möchten.

Im folgenden Beispiel wird gezeigt, wie eine neue Datei mit Lese-/Schreibberechtigung erstellt wird (wobei alle vorherigen Dateien durch denselben Pfad ersetzt werden):

[!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]

> [!NOTE]
> In diesem Beispiel wird eine Datei erstellt und geöffnet. Wenn Probleme auftreten, kann der-Befehl `Open` ein- `CFileException` Objekt in seinem letzten Parameter zurückgeben, wie hier gezeigt. Das Trace-Makro gibt sowohl den Dateinamen als auch einen Code aus, der den Grund für den Fehler angibt. Sie können die-Funktion aufzurufen, `AfxThrowFileException` Wenn Sie eine ausführlichere Fehlerberichterstattung benötigen.

## <a name="see-also"></a>Siehe auch

[CFile-Klasse](reference/cfile-class.md)<br/>
[CFile:: Open](reference/cfile-class.md#open)<br/>
[Dateien](files-in-mfc.md)

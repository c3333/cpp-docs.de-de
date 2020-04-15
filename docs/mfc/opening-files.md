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
ms.openlocfilehash: 6119bf922b05c30a14d8421800e3931c4a038779
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375958"
---
# <a name="opening-files"></a>Öffnen von Dateien

In MFC ist die häufigste Möglichkeit, eine Datei zu öffnen, ein zweistufiger Prozess.

#### <a name="to-open-a-file"></a>So öffnen Sie eine Datei

1. Erstellen Sie das Dateiobjekt, ohne einen Pfad oder Berechtigungsflags anzugeben.

   Normalerweise erstellen Sie ein Dateiobjekt, indem Sie eine [CFile-Variable](../mfc/reference/cfile-class.md) auf dem Stapelrahmen deklarieren.

1. Rufen [Open](../mfc/reference/cfile-class.md#open) Sie die Open-Member-Funktion für das Dateiobjekt auf und geben Sie einen Pfad und Berechtigungsflags an.

   Der Rückgabewert `Open` für ist ungleich Null, wenn die Datei erfolgreich geöffnet wurde, oder 0, wenn die angegebene Datei nicht geöffnet werden konnte. Die `Open` Memberfunktion wird wie folgt prototypiert:

   `virtual BOOL Open( LPCTSTR lpszFileName, UINT nOpenFlags, CFileException* pError = NULL );`

   Die geöffneten Flags geben an, welche Berechtigungen, z. B. schreibgeschützt, für die Datei erforderlich sind. Die möglichen Flagwerte werden als aufgezählte `CFile` Konstanten innerhalb der Klasse`CFile::`definiert, `CFile::modeRead`sodass sie mit " " wie in qualifiziert sind. Verwenden `CFile::modeCreate` Sie das Flag, wenn Sie die Datei erstellen möchten.

Das folgende Beispiel zeigt, wie Sie eine neue Datei mit Lese-/Schreibberechtigung erstellen (ersetzen Sie jede vorherige Datei durch denselben Pfad):

[!code-cpp[NVC_MFCFiles#1](../atl-mfc-shared/reference/codesnippet/cpp/opening-files_1.cpp)]

> [!NOTE]
> In diesem Beispiel wird eine Datei erstellt und geöffnet. Wenn Probleme auftreten, `Open` kann der `CFileException` Aufruf ein Objekt im letzten Parameter zurückgeben, wie hier gezeigt. Das TRACE-Makro druckt sowohl den Dateinamen als auch einen Code, der den Grund für den Fehler angibt. Sie können `AfxThrowFileException` die Funktion aufrufen, wenn Sie eine detailliertere Fehlerberichterstattung benötigen.

## <a name="see-also"></a>Siehe auch

[CFile-Klasse](../mfc/reference/cfile-class.md)<br/>
[CFile::Öffnen](../mfc/reference/cfile-class.md#open)<br/>
[Dateien](../mfc/files-in-mfc.md)

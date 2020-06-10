---
title: Zugreifen auf den Dateistatus
ms.date: 11/04/2016
helpviewer_keywords:
- files [MFC], status information
- examples [MFC], file status
- files [MFC], accessing
- file status [MFC]
- status of files [MFC]
ms.assetid: 1b8891d6-eb0f-4037-a837-4928fe595222
ms.openlocfilehash: 23c626940e700d3e9827ef6a7cf849d970e40d5d
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619775"
---
# <a name="accessing-file-status"></a>Zugreifen auf den Dateistatus

`CFile`unterstützt auch das Überprüfen des Dateistatus, einschließlich der Angabe, ob die Datei vorhanden ist, das Erstellen und Ändern von Datumsangaben und Uhrzeiten, die logische Größe

### <a name="to-get-file-status"></a>So erhalten Sie den Dateistatus

1. Verwenden Sie die [CFile](reference/cfile-class.md) -Klasse, um Informationen zu einer Datei zu erhalten und festzulegen. Eine nützliche Anwendung ist die Verwendung der `CFile` statischen Member-Funktion **GetStatus** , um zu bestimmen, ob eine Datei vorhanden ist. " **GetStatus** " gibt "0" zurück, wenn die angegebene Datei nicht vorhanden ist.

Daher können Sie das Ergebnis von " **GetStatus** " verwenden, um zu bestimmen, ob beim Öffnen einer Datei das Flag " **CFile:: modeCreate** " verwendet werden soll, wie im folgenden Beispiel gezeigt:

[!code-cpp[NVC_MFCFiles#3](../atl-mfc-shared/reference/codesnippet/cpp/accessing-file-status_1.cpp)]

Weitere Informationen finden Sie unter [Serialization](serialization-in-mfc.md).

## <a name="see-also"></a>Siehe auch

[Dateien](files-in-mfc.md)

---
title: Bereinigen von Dokumenten und Ansichten
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 8cb6e9337b69daf78286f57898c9badf513c7921
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626523"
---
# <a name="cleaning-up-documents-and-views"></a>Bereinigen von Dokumenten und Ansichten

Wenn ein Dokument geschlossen wird, ruft das Framework zuerst seine [DeleteContents](reference/cdocument-class.md#deletecontents) -Member-Funktion auf. Wenn Sie im Rahmen des Vorgangs des Dokuments einen Arbeitsspeicher auf dem Heap zugeordnet haben, `DeleteContents` ist der beste Ort zum Aufheben der Zuordnung.

> [!NOTE]
> Die Zuordnungen von Dokument Daten im Dekonstruktor des Dokuments sollten nicht aufgehoben werden. Im Fall einer SDI-Anwendung kann das Dokument Objekt wieder verwendet werden.

Sie können den Dekonstruktor einer Ansicht überschreiben, um den Speicherplatz zuzuweisen, den Sie dem Heap zugewiesen haben.

## <a name="see-also"></a>Siehe auch

[Initialisieren und Bereinigen von Dokumenten und Ansichten](initializing-and-cleaning-up-documents-and-views.md)

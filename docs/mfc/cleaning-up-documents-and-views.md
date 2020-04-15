---
title: Bereinigen von Dokumenten und Ansichten
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 06ff60a2cf6245f64e80d899c13a8444558fcf0b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374622"
---
# <a name="cleaning-up-documents-and-views"></a>Bereinigen von Dokumenten und Ansichten

Wenn ein Dokument geschlossen wird, ruft das Framework zuerst seine [DeleteContents-Memberfunktion](../mfc/reference/cdocument-class.md#deletecontents) auf. Wenn Sie während des Vorgangs des Dokuments Speicher `DeleteContents` auf dem Heap zugewiesen haben, ist dies der beste Ort, um die Zuweisung zu zuweisen.

> [!NOTE]
> Sie sollten die Zuordnung von Dokumentdaten im Destruktor des Dokuments nicht aufteilen. Im Fall einer SDI-Anwendung kann das Dokumentobjekt wiederverwendet werden.

Sie können den Destruktor einer Ansicht überschreiben, um den speicherzuweisungsspeicher, der Auf dem Heap zugewiesen wurde, zu verteilen.

## <a name="see-also"></a>Siehe auch

[Initialisieren und Bereinigen von Dokumenten und Ansichten](../mfc/initializing-and-cleaning-up-documents-and-views.md)

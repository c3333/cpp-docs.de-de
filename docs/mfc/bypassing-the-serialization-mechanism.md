---
title: Umgehen des Serialisierungsmechanismus
ms.date: 11/04/2016
helpviewer_keywords:
- archive objects [MFC]
- bypassing serialization
- archives [MFC], serialization
- serialization [MFC], bypassing
- archives [MFC]
- serialization [MFC], role of framework
- serialization [MFC], overriding
ms.assetid: 48d4a279-b51c-4ba5-81cd-ed043312b582
ms.openlocfilehash: f47cac34f6cdbdae01af98ec28be5af17edf0e25
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620961"
---
# <a name="bypassing-the-serialization-mechanism"></a>Umgehen des Serialisierungsmechanismus

Wie Sie gesehen haben, bietet das Framework eine Standardmethode zum Lesen und Schreiben von Daten in und aus Dateien. Die Serialisierung über ein Archive-Objekt ist für die Anforderungen vieler Anwendungen geeignet. Eine solche Anwendung liest eine Datei vollständig in den Arbeitsspeicher, ermöglicht dem Benutzer, die Datei zu aktualisieren, und schreibt die aktualisierte Version dann wieder auf den Datenträger.

Einige Anwendungen arbeiten jedoch ganz anders, und für diese Anwendungen ist die Serialisierung über ein Archiv nicht geeignet. Beispiele hierfür sind Datenbankprogramme, Programme, die nur Teile großer Dateien bearbeiten, Programme, die nur-Text-Dateien schreiben, und Programme, die Datendateien freigeben.

In diesen Fällen können Sie die [serialize](reference/cobject-class.md#serialize) -Funktion auf eine andere Weise überschreiben, um Dateiaktionen über ein [CFile](reference/cfile-class.md) -Objekt anstelle eines [CArchive](reference/carchive-class.md) -Objekts zu vermitteln.

Sie können die `Open` -, `Read` - `Write` , `Close` -,-und-Element `Seek` Funktionen der-Klasse verwenden, `CFile` um eine Datei zu öffnen, den Dateizeiger (Seek) zu einem bestimmten Punkt in der Datei zu verschieben, einen Datensatz (eine angegebene Anzahl von Bytes) zu diesem Zeitpunkt zu lesen, den Benutzer zum Aktualisieren des Datensatzes zu verwenden und den Datensatz wieder in die Datei zu schreiben. Das Framework öffnet die Datei für Sie, und Sie können die Member- `GetFile` Funktion der-Klasse verwenden, `CArchive` um einen Zeiger auf das-Objekt zu erhalten `CFile` . Für eine noch anspruchsvollere und flexiblere Verwendung können Sie die Member-Funktionen von [OnOpenDocument](reference/cdocument-class.md#onopendocument) und [OnSaveDocument](reference/cdocument-class.md#onsavedocument) der-Klasse überschreiben `CWinApp` . Weitere Informationen finden Sie unter Class [CFile](reference/cfile-class.md) in der *MFC-Referenz*.

In diesem Szenario führt die `Serialize` außer Kraft Setzung keine Aktionen aus, es sei denn, Sie möchten einen Dateiheader lesen und schreiben, um ihn auf dem neuesten Stand zu halten, wenn das Dokument geschlossen wird.

## <a name="see-also"></a>Siehe auch

[Verwenden von Dokumenten](using-documents.md)

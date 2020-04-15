---
title: Serialisieren von Daten in und aus Dateien
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], serialization
- documents [MFC], saving
- saving documents
- deserialization [MFC]
- serialization [MFC], role of document
- serialization [MFC], role of data
- data [MFC]
- data [MFC], serializing
- document data [MFC]
ms.assetid: b42a0c68-4bc4-4012-9938-5433a26d2c24
ms.openlocfilehash: 043ba019c6b5ad79db2cedb6314c9e65f14b14b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376935"
---
# <a name="serializing-data-to-and-from-files"></a>Serialisieren von Daten in und aus Dateien

Die Grundidee der Persistenz ist, dass ein Objekt in der Lage sein sollte, seinen aktuellen Zustand, der durch die Werte seiner Membervariablen angezeigt wird, in persistenten Speicher zu schreiben. Später kann das Objekt durch Lesen oder "Deserialisieren" des Objektstatus aus persistentem Speicher neu erstellt werden. Ein wichtiger Punkt dabei ist, dass das Objekt selbst für das Lesen und Schreiben seines eigenen Zustands verantwortlich ist. Damit eine Klasse persistent ist, muss sie daher die grundlegenden Serialisierungsvorgänge implementieren.

Das Framework bietet eine Standardimplementierung zum Speichern von Dokumenten in Festplattendateien als Reaktion auf die Befehle Speichern und Speichern unter als im Menü Datei und zum Laden von Dokumenten aus Datenträgerdateien als Reaktion auf den Befehl Öffnen. Mit sehr wenig Arbeit können Sie die Fähigkeit eines Dokuments implementieren, seine Daten in und aus einer Datei zu schreiben und zu lesen. Die Hauptsache, die Sie tun müssen, ist die [Serialize-Memberfunktion](../mfc/reference/cobject-class.md#serialize) in Ihrer Dokumentklasse zu überschreiben.

Der MFC-Anwendungs-Assistent platziert eine Skelettüberschreibung der `CDocument` Memberfunktion `Serialize` in der Dokumentklasse, die er für Sie erstellt. Nachdem Sie die Membervariablen Ihrer Anwendung implementiert haben, können Sie ihre `Serialize` Außerkraftsetzung mit Code ausfüllen, der die Daten an ein mit einer Datei verbundenes "Archivobjekt" sendet. Ein [CArchive-Objekt](../mfc/reference/carchive-class.md) ähnelt den **Cin-** und cout-Eingabe-/Ausgabeobjekten aus der C++-Iostream-Bibliothek. **cout** `CArchive` Schreibt und liest jedoch binäres Format, nicht formatierten Text.

## <a name="what-do-you-want-to-know-more-about"></a>Was möchten Sie mehr darüber wissen?

- [Serialisierung](../mfc/serialization-in-mfc.md)

- [Die Rolle des Dokuments bei der Serialisierung](#_core_the_document.92.s_role_in_serialization)

- [Die Rolle der Daten bei der Serialisierung](#_core_the_data.92.s_role_in_serialization)

- [Umgehung des Serialisierungsmechanismus](../mfc/bypassing-the-serialization-mechanism.md)

## <a name="the-documents-role-in-serialization"></a><a name="_core_the_document.92.s_role_in_serialization"></a>Die Rolle des Dokuments bei der Serialisierung

Das Framework reagiert automatisch auf die Befehle Öffnen, Speichern und Speichern unter `Serialize` dem Menü, indem die Memberfunktion des Dokuments aufgerufen wird, wenn es implementiert ist. Ein ID_FILE_OPEN-Befehl ruft z. B. eine Handlerfunktion im Anwendungsobjekt auf. Während dieses Vorgangs sieht und reagiert der Benutzer auf das Dialogfeld Dateiöffnen, und das Framework ruft den vom Benutzer auswählten Dateinamen ab. Das Framework `CArchive` erstellt ein Objekt, das zum Laden von `Serialize`Daten in das Dokument eingerichtet wurde, und übergibt das Archiv an . Das Framework hat die Datei bereits geöffnet. Der Code in der `Serialize` Memberfunktion Ihres Dokuments liest die Daten durch das Archiv ein und rekonstruiert Datenobjekte nach Bedarf. Weitere Informationen zur Serialisierung finden Sie im Artikel [Serialisierung](../mfc/serialization-in-mfc.md).

## <a name="the-datas-role-in-serialization"></a><a name="_core_the_data.92.s_role_in_serialization"></a>Die Rolle der Daten bei der Serialisierung

Im Allgemeinen sollten Klassentypdaten in der Lage sein, sich selbst zu serialisieren. Das heißt, wenn Sie ein Objekt an ein Archiv übergeben, sollte das Objekt wissen, wie es sich selbst in das Archiv schreibt und wie man sich selbst aus dem Archiv liest. MFC bietet Unterstützung, um Klassen auf diese Weise serialisierbar zu machen. Wenn Sie eine Klasse entwerfen, um einen Datentyp zu definieren, und Sie beabsichtigen, Daten dieses Typs zu serialisieren, entwerfen Sie für die Serialisierung.

## <a name="see-also"></a>Siehe auch

[Verwenden von Dokumenten](../mfc/using-documents.md)

---
title: Serialisierung in MFC
ms.date: 11/04/2016
helpviewer_keywords:
- collection classes [MFC], serialization
- bypassing serialization [MFC]
- MFC, serialization
- serialization [MFC], MFC
- serialization [MFC], bypassing
ms.assetid: fb596a18-4522-47e0-96e0-192732d24c12
ms.openlocfilehash: eca4d0357977bc7ef21063718c738ae5bd8e7431
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372752"
---
# <a name="serialization-in-mfc"></a>Serialisierung in MFC

In diesem Artikel wird der Serialisierungsmechanismus erläutert, der in der Microsoft Foundation-Klassenbibliothek (MFC) bereitgestellt wird, damit Objekte zwischen den Ausführungen des Programms beibehalten werden können.

Serialisierung ist der Prozess des Schreibens oder Lesens eines Objekts auf oder von einem persistenten Speichermedium, z. B. einer Datenträgerdatei. Serialisierung ist ideal für Situationen, in denen der Status strukturierter Daten (z. B. C++-Klassen oder -Strukturen) während oder nach der Ausführung eines Programms beibehalten werden soll. Die Verwendung der von MFC bereitgestellten Serialisierungsobjekte ermöglicht dies auf eine standard- und konsistente Weise, wodurch der Benutzer von der Notwendigkeit befreit wird, Dateioperationen von Hand auszuführen.

MFC bietet integrierte Unterstützung für die `CObject`Serialisierung in der Klasse . Daher können alle `CObject` von abgeleiteten `CObject`Klassen das Serialisierungsprotokoll von nutzen.

Die Grundidee der Serialisierung ist, dass ein Objekt in der Lage sein sollte, seinen aktuellen Zustand, der normalerweise durch den Wert seiner Membervariablen angezeigt wird, in persistenten Speicher zu schreiben. Später kann das Objekt neu erstellt werden, indem der Status des Objekts aus dem Speicher gelesen oder deserialisiert wird. Serialisierung behandelt alle Details von Objektzeigern und Zirkelverweisen auf Objekte, die beim Serialisieren eines Objekts verwendet werden. Ein wichtiger Punkt ist, dass das Objekt selbst für das Lesen und Schreiben seines eigenen Zustands verantwortlich ist. Damit also eine Klasse serialisierbar ist, muss sie die grundlegenden Serialisierungsvorgänge implementieren. Wie in der Artikelgruppe Serialisierung gezeigt, ist es einfach, diese Funktionalität einer Klasse hinzuzufügen.

MFC verwendet ein `CArchive` Objekt der Klasse als Zwischenhändler zwischen dem zu serialisierenden Objekt und dem Speichermedium. Dieses Objekt ist immer `CFile` einem Objekt zugeordnet, von dem es die erforderlichen Informationen für die Serialisierung erhält, einschließlich des Dateinamens und ob der angeforderte Vorgang ein Lese- oder Schreibvorgang ist. Das Objekt, das einen Serialisierungsvorgang ausführt, kann das `CArchive` Objekt ohne Rücksicht auf die Art des Speichermediums verwenden.

Ein `CArchive` Objekt verwendet überladene Einfügevorgänge (**<**) und Extraktionsoperatoren (**>>**), um Schreib- und Lesevorgänge auszuführen. Weitere Informationen finden Sie unter [Speichern und Laden von CObjects über ein Archiv](../mfc/storing-and-loading-cobjects-via-an-archive.md) im Artikel Serialisierung: Serialisieren eines Objekts.

> [!NOTE]
> Verwechseln Sie `CArchive` die Klasse nicht mit allgemeinen Iostream-Klassen, die nur für formatierten Text gedacht sind. Die `CArchive` Klasse ist für serialisierte Binärformatobjekte.

Wenn Sie möchten, können Sie die MFC-Serialisierung umgehen, um einen eigenen Mechanismus für die persistente Datenspeicherung zu erstellen. Sie müssen die Klassenmemberfunktionen überschreiben, die die Serialisierung auf Befehl des Benutzers initiieren. Weitere Informationen finden Sie in der Diskussion in [Technischer Anmerkung 22](../mfc/tn022-standard-commands-implementation.md) des ID_FILE_OPEN, ID_FILE_SAVE und ID_FILE_SAVE_AS Standardbefehlen.

Die folgenden Artikel behandeln die beiden Hauptaufgaben, die für die Serialisierung erforderlich sind:

- [Serialisierung: Erstellen einer serialisierbaren Klasse](../mfc/serialization-making-a-serializable-class.md)

- [Serialisierung: Serialisieren eines Objekts](../mfc/serialization-serializing-an-object.md)

Der Artikel [Serialization: Serialization vs. Database Input/Output](../mfc/serialization-serialization-vs-database-input-output.md) beschreibt, ob serialisieren eine geeignete Eingabe-/Ausgabetechnik in Datenbankanwendungen ist.

## <a name="see-also"></a>Siehe auch

[Konzepte](../mfc/mfc-concepts.md)<br/>
[Allgemeine MFC-Themen](../mfc/general-mfc-topics.md)<br/>
[CArchive-Klasse](../mfc/reference/carchive-class.md)<br/>
[CObject-Klasse](../mfc/reference/cobject-class.md)<br/>
[CDocument-Klasse](../mfc/reference/cdocument-class.md)<br/>
[CFile-Klasse](../mfc/reference/cfile-class.md)

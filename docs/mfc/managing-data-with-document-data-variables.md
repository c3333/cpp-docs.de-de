---
title: Verwalten von Daten mit Dokumentdatenvariablen
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], data storage
- friend classes [MFC]
- classes [MFC], friend
- data [MFC]
- data [MFC], documents
- collection classes [MFC], used by document object
- document data [MFC]
- member variables [MFC], document class [MFC]
ms.assetid: e70b87f4-8c30-49e5-8986-521c2ff91704
ms.openlocfilehash: 3d845b0fc3d00369d44c21c04a3fb7e3b8d6189e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618324"
---
# <a name="managing-data-with-document-data-variables"></a>Verwalten von Daten mit Dokumentdatenvariablen

Implementieren Sie die Daten Ihres Dokuments als Element Variablen ihrer Document-Klasse. Beispielsweise deklariert das Scribble-Programm einen Datenmember vom Typ `CObList` – eine verknüpfte Liste, in der Zeiger auf-Objekte gespeichert werden `CObject` . Diese Liste wird zum Speichern von Arrays von Punkten verwendet, aus denen sich ein Zeilen Zeichnungs Zeichen besteht.

Die Art und Weise, wie Sie die Mitgliedsdaten Ihres Dokuments implementieren, hängt von der Art der Anwendung ab. Zur Unterstützung bietet MFC eine Gruppe von "Auflistungs Klassen" – Arrays, Listen und Zuordnungen (Wörterbücher), einschließlich Auflistungen, die auf C++-Vorlagen basieren – zusammen mit Klassen, die eine Vielzahl von gängigen Datentypen wie `CString` , `CRect` , `CPoint` , `CSize` und Kapseln `CTime` . Weitere Informationen zu diesen Klassen finden Sie in der [Übersicht über die Klassenbibliothek](class-library-overview.md) in der *MFC-Referenz*.

Wenn Sie die Elementdaten Ihres Dokuments definieren, fügen Sie in der Regel der Document-Klasse Element Funktionen hinzu, um Datenelemente festzulegen und zu erhalten und andere nützliche Vorgänge für diese auszuführen.

Die Ansichten greifen auf das Dokument Objekt zu, indem Sie den Zeiger der Ansicht auf das Dokument verwenden, das zum Zeitpunkt der Erstellung in der Ansicht installiert ist. Sie können diesen Zeiger in den Element Funktionen einer Ansicht abrufen, indem Sie die `CView` Member-Funktion aufrufen `GetDocument` . Stellen Sie sicher, dass Sie diesen Zeiger in ihren eigenen Dokumenttyp umwandeln. Anschließend können Sie über den-Zeiger auf öffentliche dokumentmember zugreifen.

Wenn die häufige Datenübertragung einen direkten Zugriff erfordert oder Sie die nicht öffentlichen Member der Document-Klasse verwenden möchten, können Sie die Ansichts Klasse zu einem Friend (in C++ Terms) der Document-Klasse machen.

## <a name="see-also"></a>Siehe auch

[Verwenden von Dokumenten](using-documents.md)

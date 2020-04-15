---
title: Weitere Empfehlungen für Handling Input-Output
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
ms.openlocfilehash: c365120a385c440f09f0ee4c0a2fc52afb55834f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371736"
---
# <a name="recommendations-for-handling-inputoutput"></a>Empfehlungen zur Eingabe-/Ausgabebehandlung

Ob Sie dateibasierte E/A-E verwenden oder nicht, hängt davon ab, wie Sie auf die Fragen in der folgenden Entscheidungsstruktur antworten:

**Befinden sich die primären Daten in Ihrer Anwendung in einer Datenträgerdatei?**

- Ja, die primären Daten befinden sich in einer Datenträgerdatei:

   **Liest die Anwendung die gesamte Datei in den Speicher bei File Open und schreibt die gesamte Datei auf dateispeichern zurück auf den Datenträger**

  - Ja: Dies ist der standardmäßige MFC-Dokumentfall. Verwenden `CDocument` Sie die Serialisierung.

  - Nein: Dies ist in der Regel der Fall bei der transaktionsbasierten Aktualisierung der Datei. Sie aktualisieren die Datei pro Transaktion und benötigen `CDocument` keine Serialisierung.

- Nein, die primären Daten befinden sich nicht in einer Datenträgerdatei:

   **Befinden sich die Daten in einer ODBC-Datenquelle?**

  - Ja, die Daten befinden sich in einer ODBC-Datenquelle:

      Verwenden Sie die Datenbankunterstützung von MFC. Die Standardmäßige MFC-Implementierung `CDatabase` für diesen Fall enthält ein Objekt, wie im Artikel [MFC: Verwenden von Datenbankklassen mit Dokumenten und Ansichten](../data/mfc-using-database-classes-with-documents-and-views.md)erläutert. Die Anwendung kann auch lesen und schreiben Sie eine Hilfsdatei – der Zweck des Anwendungs-Assistenten "sowohl eine Datenbankansicht und Dateiunterstützung" Option. In diesem Fall würden Sie die Serialisierung für die Hilfsdatei verwenden.

  - Nein, die Daten befinden sich nicht in einer ODBC-Datenquelle.

      Beispiele für diesen Fall: Die Daten befinden sich in einem Nicht-ODBC-DBMS; Die Daten werden über einen anderen Mechanismus gelesen, z. B. OLE oder DDE.

      In solchen Fällen verwenden Sie keine Serialisierung, und Ihre Anwendung hat keine Menüelemente öffnen und speichern. Möglicherweise möchten Sie eine `CDocument` als Basis verwenden, genauso wie eine MFC ODBC-Anwendung das Dokument zum Speichern von `CRecordset` Objekten verwendet. Sie verwenden jedoch nicht die standardmäßige Dateiöffnen/Speichern von Dokumentenserialisierung des Frameworks.

Um die Befehle Öffnen, Speichern und Speichern unter als im Menü Datei zu unterstützen, bietet das Framework die Dokumentserialisierung. Serialisierung liest und schreibt Daten, `CObject`einschließlich Von der Klasse abgeleitete Objekte, in den permanenten Speicher, normalerweise eine Datenträgerdatei. Serialisierung ist einfach zu bedienen und erfüllt viele Ihrer Anforderungen, aber sie kann in vielen Datenzugriffsanwendungen unangemessen sein. Datenzugriffsanwendungen aktualisieren Daten in der Regel pro Transaktion. Sie aktualisieren die von der Transaktion betroffenen Datensätze, anstatt eine ganze Datendatei auf einmal zu lesen und zu schreiben.

Informationen zur Serialisierung finden Sie unter [Serialisierung](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Siehe auch

[Serialisierung: Serialisierung im Vergleich zur Datenbankeingabe/-ausgabe](../mfc/serialization-serialization-vs-database-input-output.md)

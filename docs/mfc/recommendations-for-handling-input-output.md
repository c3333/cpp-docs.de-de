---
title: Empfehlungen für die Behandlung von Eingabe-und Ausgabe
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
ms.openlocfilehash: 956a92fd1761f61081afa2eb9c6cb35fe72b46d6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446901"
---
# <a name="recommendations-for-handling-inputoutput"></a>Empfehlungen zur Eingabe-/Ausgabebehandlung

Ob Sie dateibasierte e/a verwenden oder nicht, hängt davon ab, wie Sie auf die Fragen in der folgenden Entscheidungsstruktur reagieren:

**Befinden sich die primären Daten in der Anwendung in einer Datenträger Datei**

- Ja, die primären Daten befinden sich in einer Datenträger Datei:

     **Liest die Anwendung die gesamte Datei in den Arbeitsspeicher der Datei, die geöffnet ist, und schreibt die gesamte Datei auf dem Datenträger beim Speichern von Dateien.**

   - Ja: Dies ist der Standardfall für MFC-Dokumente. Verwenden Sie `CDocument` Serialisierung.

   - Nein: Dies ist in der Regel der Fall einer transaktionsbasierten Aktualisierung der Datei. Sie aktualisieren die Datei auf Transaktionsbasis und benötigen keine `CDocument` Serialisierung.

- Nein, die primären Daten befinden sich nicht in einer Datenträger Datei:

     **Befinden sich die Daten in einer ODBC-Datenquelle**

   - Ja, die Daten befinden sich in einer ODBC-Datenquelle:

      Verwenden Sie die MFC-Datenbankunterstützung. Die MFC-Standard Implementierung für diesen Fall enthält ein `CDatabase` Objekt, wie im Artikel [MFC: Verwenden von Datenbankklassen mit Dokumenten und Sichten](../data/mfc-using-database-classes-with-documents-and-views.md)erläutert. Die Anwendung kann auch eine zusätzliche Datei lesen und Schreiben – der Zweck des Anwendungs-Assistenten für die Option "Daten Bank Ansicht und Dateiunterstützung". In diesem Fall verwenden Sie die Serialisierung für die zusätzliche Datei.

   - Nein, die Daten befinden sich nicht in einer ODBC-Datenquelle.

      Beispiele für diesen Fall: die Daten befinden sich in einem nicht-ODBC-DBMS. die Daten werden über einen anderen Mechanismus, z. b. OLE oder DDE, gelesen.

      In solchen Fällen wird die Serialisierung nicht verwendet, und die Anwendung verfügt nicht über die Menü Elemente "Öffnen" und "Speichern". Sie möchten möglicherweise trotzdem eine `CDocument` als Basis Basis verwenden, ebenso wie eine MFC-ODBC-Anwendung das Dokument zum Speichern von `CRecordset` Objekten verwendet. Sie verwenden jedoch nicht die Standarddatei zum Öffnen/Speichern von Dokumenten für das Framework.

Zur Unterstützung der Befehle "Öffnen", "Speichern" und "Speichern unter" im Menü Datei bietet das Framework Dokumentserialisierung. Die Serialisierung liest und schreibt Daten, einschließlich von Klassen `CObject`abgeleiteter Objekte, in einen permanenten Speicher, normalerweise eine Datenträger Datei. Die Serialisierung ist einfach zu verwenden und bietet viele Ihrer Anforderungen, kann aber in vielen Datenzugriffs Anwendungen ungeeignet sein. Datenzugriffs Anwendungen aktualisieren Daten in der Regel pro Transaktion. Sie aktualisieren die Datensätze, die von der Transaktion betroffen sind, anstatt eine gesamte Datendatei gleichzeitig zu lesen und zu schreiben.

Weitere Informationen zur Serialisierung finden Sie unter [Serialization](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Weitere Informationen

[Serialisierung: Serialisierung im Vergleich zur Daten Bank Eingabe/-Ausgabe](../mfc/serialization-serialization-vs-database-input-output.md)

---
title: Recordset (ODBC)
ms.date: 05/09/2019
helpviewer_keywords:
- recordsets, snapshots
- recordsets, creating
- dynamic recordsets
- forward-only recordsets
- recordsets, dynasets
- ODBC recordsets, CRecordset objects
- ODBC recordsets
- recordsets, about recordsets
- snapshots, ODBC recordsets
- dynasets
ms.assetid: 333337c5-575e-4d26-b5f6-47166ad7874d
ms.openlocfilehash: 011191b99170b8a8338b5ca1a440a32404c4d793
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212822"
---
# <a name="recordset-odbc"></a>Recordset (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

Ein [CRecordset](../../mfc/reference/crecordset-class.md)-Objekt stellt eine Gruppe von Datensätzen dar, die in einer Datenquelle ausgewählt wurden. Die Datensätze können aus einem der folgenden Objekte stammen:

- Tabelle

- Eine Abfrage

- Eine gespeicherte Prozedur, aus der auf mindestens eine Tabelle zugegriffen wird

Ein Beispiel für ein Recordset, das auf einer Tabelle basiert, ist „alle Kunden“, wobei auf eine Kunden-Tabelle zugegriffen wird. Ein Beispiel für eine Abfrage ist „alle Rechnungen für Lena Koch“. Ein Beispiel für ein Recordset, das auf einer gespeicherten Prozedur (manchmal als vordefinierte Abfrage bezeichnet) basiert, ist „alle Konten mit Verzug“, wobei eine gespeicherte Prozedur in der Back-End-Datenbank aufgerufen wird. In einem Recordset können mehrere Tabellen aus derselben Datenquelle, aber keine Tabellen aus unterschiedlichen Datenquellen verknüpft werden.

> [!NOTE]
>  Einige ODBC-Treiber unterstützen Sichten der Datenbank. Eine Sicht in diesem Sinn ist eine Abfrage, die ursprünglich mit der SQL-Anweisung `CREATE VIEW` erstellt wurde.

##  <a name="recordset-capabilities"></a><a name="_core_recordset_capabilities"></a> Recordset-Eigenschaften

Alle Recordset-Objekte haben die folgenden Eigenschaften:

- Wenn die Datenquelle nicht schreibgeschützt ist, können Sie angeben, dass das Recordset [aktualisierbar](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md), [erweiterbar](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md) oder schreibgeschützt sein soll. Ist das Recordset aktualisierbar, können Sie entweder die pessimistische oder die optimistische [Sperr](../../data/odbc/recordset-locking-records-odbc.md)-Methode angeben, sofern der Treiber die entsprechende Methode unterstützt. Ist die Datenquelle schreibgeschützt, ist auch das Recordset schreibgeschützt.

- Sie können Memberfunktionen aufrufen, um durch die ausgewählten Datensätze zu [scrollen](../../data/odbc/recordset-scrolling-odbc.md).

- Sie können die Datensätze [filtern](../../data/odbc/recordset-filtering-records-odbc.md), um einzuschränken, welche der verfügbaren Datensätze ausgewählt werden.

- Sie können die Datensätze anhand von Spalten in aufsteigender oder absteigender Reihenfolge[sortieren](../../data/odbc/recordset-sorting-records-odbc.md).

- Sie können das Recordset [parametrisieren](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md), um die Recordsetauswahl zur Laufzeit festzulegen.

##  <a name="snapshots-and-dynasets"></a><a name="_core_snapshots_and_dynasets"></a> Momentaufnahmen und Dynasets

Es gibt zwei Hauptarten von Recordsets: [Momentaufnahmen](../../data/odbc/snapshot.md) und [Dynasets](../../data/odbc/dynaset.md). Beide werden von der Klasse `CRecordset` unterstützt. Beide Recordsetarten haben die allgemeinen Merkmale aller Recordsets, aber in jeder Art wird die allgemeine Funktionalität in einer jeweils speziellen Weise erweitert. Momentaufnahmen bieten eine statische Ansicht der Daten und sind nützlich für Berichte und andere Situationen, in denen Sie eine Ansicht der Daten in der Form wünschen, in der sie zu einem bestimmten Zeitpunkt vorhanden waren. Dynasets sind nützlich, wenn Sie möchten, dass von anderen Benutzern vorgenommene Aktualisierungen im Recordset sichtbar sind, ohne dass das Recordset erneut abgefragt oder aktualisiert werden muss. Momentaufnahmen und Dynasets können aktualisierbar oder schreibgeschützt sein. Um Datensätze zu berücksichtigen, die von anderen Benutzern hinzugefügt oder gelöscht wurden, rufen Sie [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery) auf.

`CRecordset` unterstützt auch zwei andere Arten von Recordsets: dynamische Recordsets und Vorwärtsrecordsets. Dynamische Recordsets sind mit Dynasets vergleichbar. In dynamischen Recordsets werden jedoch alle hinzugefügten oder gelöschten Datensätze berücksichtigt, ohne dass `CRecordset::Requery` aufgerufen wird. Aus diesem Grund sind dynamische Recordsets in der Regel teuer in Bezug auf die Verarbeitungszeit für das DBMS, und viele ODBC-Treiber unterstützen diese nicht. Im Gegensatz dazu bieten Vorwärtsrecordsets die effizienteste Methode des Datenzugriffs für Recordsets, die keine Updates oder kein Rückwärtsscrollen erfordern. Sie könnten beispielsweise ein Vorwärtsrecordset verwenden, um Daten von einer Datenquelle in eine andere zu migrieren, wobei Sie die Daten nur in Vorwärtsrichtung durchlaufen müssen. Um ein Vorwärtsrecordset zu verwenden, müssen Sie die beiden folgenden Schritte ausführen:

- Übergeben Sie die Option `CRecordset::forwardOnly` als *nOpenType*-Parameter der [Open](../../mfc/reference/crecordset-class.md#open)-Memberfunktion.

- Geben Sie `CRecordset::readOnly` im *DwOptions*-Parameter von `Open` an.

    > [!NOTE]
    >  Informationen zu den ODBC-Treiberanforderungen für Dynasetunterstützung finden Sie unter [ODBC](../../data/odbc/odbc-basics.md). Eine Liste der in dieser Version von Visual C++ mitgelieferten ODBC-Treiber sowie Informationen über den Erwerb zusätzlicher Treiber finden Sie unter [Liste der ODBC-Treiber](../../data/odbc/odbc-driver-list.md).

##  <a name="your-recordsets"></a><a name="_core_your_recordsets"></a> Ihre Recordsets

Für jede einzelne Tabelle, Sicht oder gespeicherte Prozedur, auf die Sie zugreifen möchten, definieren Sie üblicherweise eine Klasse, die aus `CRecordset` abgeleitet ist. (Bei der Ausnahme handelt es sich um einen datenbankjoin, bei dem ein Recordset Spalten aus zwei oder mehr Tabellen darstellt.) Wenn Sie eine Recordsetklasse ableiten, aktivieren Sie den Mechanismus für den Daten Satz Feld Austausch (RFX) oder den Massendaten Satz Feld Austauschmechanismus (Bulk RFX), der dem DDX-Mechanismus (Dialog Datenaustausch) ähnelt. RFX und Massen-RFX vereinfachen die Übertragung von Daten aus der Datenquelle in Ihr Recordset. Außerdem überträgt RFX Daten aus Ihrem Recordset in die Datenquelle. Weitere Informationen finden Sie unter Daten [Satz Feld Austausch (RFX)](../../data/odbc/record-field-exchange-rfx.md) und [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Ein Recordset-Objekt ermöglicht Ihnen Zugriff auf alle ausgewählten Datensätze. Zum Scrollen durch die ausgewählten Datensätze verwenden Sie `CRecordset`-Memberfunktionen, etwa `MoveNext` und `MovePrev`. Gleichzeitig entspricht ein Recordset-Objekt nur einem der ausgewählten Datensätze, dem aktuellen Datensatz. Sie können sich die Felder des aktuellen Datensatzes ansehen, indem Sie Recordset-Klassenmembervariablen deklarieren, die den Spalten der Tabelle oder den Datensätzen entsprechen, die aus der Datenbankabfrage resultieren. Informationen zu Recordset-Datenmembern finden Sie unter [Recordset: Architecture (ODBC)](../../data/odbc/recordset-architecture-odbc.md).

In den folgenden Themen finden Sie ausführliche Informationen zur Verwendung von Recordset-Objekten. Die Themen sind in funktionsbezogenen Kategorien und in natürlicher Suchreihenfolge aufgeführt, um sequenzielles Lesen zu ermöglichen.

### <a name="topics-about-the-mechanics-of-opening-reading-and-closing-recordsets"></a>Themen über die Vorgehensweisen zum Öffnen, Lesen und Schließen von Recordsets

- [Recordset: Architektur (ODBC)](../../data/odbc/recordset-architecture-odbc.md)

- [Recordset: Deklarieren einer Klasse für eine Tabelle (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)

- [Recordset: Erstellen und Schließen von Recordsets (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)

- [Recordset: Scrollen (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)

- [Recordset: Lesezeichen und absolute Positionen (ODBC)](../../data/odbc/recordset-bookmarks-and-absolute-positions-odbc.md)

- [Recordset: Filtern von Datensätzen (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)

- [Recordset: Sortieren von Datensätzen (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)

- [Recordset: Parametrisieren eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

### <a name="topics-about-the-mechanics-of-modifying-recordsets"></a>Themen über die Vorgehensweisen zum Ändern von Recordsets

- [Recordset: Hinzufügen, Aktualisieren und Löschen von Datensätzen (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

- [Recordset: Sperren von Datensätzen (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

- [Recordset: Erneutes Abfragen eines Recordsets (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md)

### <a name="topics-about-somewhat-more-advanced-techniques"></a>Themen über etwas fortgeschrittenere Techniken

- [Recordset: Ausführen eines Join (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)

- [Recordset: Deklarieren einer Klasse für eine vordefinierte Abfrage (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md)

- [Recordset: Dynamisches Binden von Datenspalten (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)

- [Recordset: Abrufen von Datensätzen in einer Sammeloperation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

- [Recordset: Arbeiten mit großen Datenelementen (ODBC)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)

- [Recordset: Abrufen von Summen und anderen Aggregatergebnissen (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)

### <a name="topics-about-how-recordsets-work"></a>Themen zur Funktionsweise von Recordsets

- [Recordset: Wie Recordsets Datensätze auswählen (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)

- [Recordset: Wie Recordsets Datensätze aktualisieren (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)

## <a name="see-also"></a>Weitere Informationen

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[Nutzen von MFC-ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Transaktion (ODBC)](../../data/odbc/transaction-odbc.md)

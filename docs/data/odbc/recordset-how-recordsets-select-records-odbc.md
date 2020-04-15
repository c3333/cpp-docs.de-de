---
title: 'Recordset: Datensatzauswahl durch Recordsets (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
ms.openlocfilehash: 0aa9c082d2d04416358d948476f2ae0f9e2a35af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366990"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>Recordset: Datensatzauswahl durch Recordsets (ODBC)

> [!NOTE]
> Der MFC-ODBC-Consumer-Assistent ist in Visual Studio 2019 und höher nicht verfügbar. Sie können einen Consumer weiterhin manuell erstellen.

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In diesem Thema wird Folgendes erläutert:

- [Ihre Rolle und Ihre Optionen beim Auswählen von Datensätzen](#_core_your_options_in_selecting_records)

- [Erstellen der SQL-Anweisung und Auswählen von Datensätzen für ein Recordset](#_core_how_a_recordset_constructs_its_sql_statement)

- [Ihre Vorgehensweise zum Anpassen der Auswahl](#_core_customizing_the_selection)

Für Recordsets werden Datensätze über einen ODBC-Treiber in einer Datenquelle ausgewählt, indem SQL-Anweisungen an den Treiber gesendet werden. Die gesendeten SQL-Anweisungen hängen davon ab, wie Sie Ihre Recordset-Klasse konzipiert haben und öffnen.

## <a name="your-options-in-selecting-records"></a><a name="_core_your_options_in_selecting_records"></a> Ihre Optionen beim Auswählen von Datensätzen

In der folgenden Tabelle sind die Optionen aufgeführt, die Sie für das Auswählen von Datensätzen haben.

### <a name="how-and-when-you-can-affect-a-recordset"></a>Wie und wann Sie ein Recordset beeinflussen können

|Wenn Sie|Sie haben folgende Möglichkeiten:|
|--------------|-------------|
|Sie können Ihre Recordset-Klasse mit dem **Klasse hinzufügen**-Assistenten deklarieren.|Sie können die Tabelle angeben, in der ausgewählt werden soll.<br /><br /> Sie können angeben, welche Spalten einbezogen werden sollen.<br /><br /> Weitere Informationen finden Sie unter [Hinzufügen eines MFC-ODBC-Consumers](../../mfc/reference/adding-an-mfc-odbc-consumer.md).|
|Die Implementierung Ihrer Recordset-Klasse abschließen|Memberkunktionen, z. B. `OnSetOptions` (erweitert), überschreiben, um anwendungsspezifische Optionen festzulegen oder Standardwerte zu ändern. Geben Sie Parameterdatenmember an, wenn Sie ein parametrisiertes Recordset wünschen.|
|Ein Recordset-Objekt erstellen (vor dem Aufruf von `Open`)|Sie können eine Suchbedingung (möglicherweise kombiniert) zur Verwendung in einer **WHERE**-Klausel angeben, in der die Datensätze gefiltert werden. Siehe [Recordset: Filtering Records (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).<br /><br /> Sie können eine Sortierreihenfolge angeben, die in einer **ORDER BY**-Klausel verwendet wird, in der die Datensätze sortiert werden. Siehe [Recordset: Sorting Records (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).<br /><br /> Sie können Parameterwerte für alle Parameter angeben, die Sie der Klasse hinzugefügt haben. Siehe [Recordset: Parametrierung eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).|

|Die Abfrage des Recordsets durch Aufrufen von `Open` ausführen| Sie können eine benutzerdefinierte SQL-Zeichenfolge angeben, um die Standard-SQL-Zeichenfolge zu ersetzen, die der Assistent eingerichtet hat. Siehe [CRecordset::Öffnen](../../mfc/reference/crecordset-class.md#open) in der *Klassenbibliotheksreferenz* und SQL: Anpassen der [SQL-Anweisung (ODBC) Ihres Recordsets](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).|

|`Requery` aufrufen, um das Recordset mit den neuesten Werten in der Datenquelle erneut abzufragen | Sie können neue Parameter angeben oder filtern oder sortieren. Siehe [Recordset: Erneutes Abfragen eines Recordsets (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).|

## <a name="how-a-recordset-constructs-its-sql-statement"></a><a name="_core_how_a_recordset_constructs_its_sql_statement"></a> Erstellen der SQL-Anweisung für ein Recordset

Wenn Sie die [Open](../../mfc/reference/crecordset-class.md#open)-Memberfunktion eines Recordset-Objekts aufrufen, erstellt `Open` eine SQL-Anweisung mit einigen oder allen der folgenden Bestandteile:

- Der *lpszSQL*-Parameter wird an `Open` übergeben. Ist er ungleich NULL, gibt dieser Parameter eine benutzerdefinierte SQL-Zeichenfolge oder einen Teil einer solchen Zeichenfolge an. Das Framework analysiert die Zeichenfolge. Ist die Zeichenfolge eine **SELECT**-SQL-Anweisung oder eine **CALL**-ODBC-Anweisung, verwendet das Framework die Zeichenfolge als SQL-Anweisung des Recordsets. Beginnt die Zeichenfolge nicht mit „SELECT“ oder „{CALL“, verwendet das Framework die bereitgestellten Bestandteile dazu, eine **FROM**-SQL-Klausel zu erstellen.

- Die Zeichenfolge, die von [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) zurückgegeben wird. Standardmäßig ist dies der Name der Tabelle, die Sie für das Recordset im Assistenten angegeben haben. Sie können aber ändern, was die Funktion zurückgibt. Das Framework ruft `GetDefaultSQL` auf; beginnt die Zeichenfolge nicht mit „SELECT“ oder „{CALL“, wird angenommen, dass sie ein Tabellenname ist, der dann verwendet wird, um eine SQL-Zeichenfolge zu erstellen.

- Die Felddatenmember des Recordset-Objekts, die an bestimmte Spalten der Tabelle gebunden werden müssen. Das Framework bindet Datensatzspalten an die Adressen dieser Member und verwendet diese als Puffer. Das Framework bestimmt die Zuordnung der Felddatenmember zu Tabellenspalten aus dem [RFX](../../data/odbc/record-field-exchange-using-rfx.md)- oder Massen-RFX-Funktionsaufruf in der [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)- oder [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)-Memberfunktion des Recordsets.

- Der [Filter](../../data/odbc/recordset-filtering-records-odbc.md) für das Recordset, sofern vorhanden, der im [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter)-Datenmember enthalten ist. Das Framework verwendet diese Zeichenfolge, um eine **WHERE**-SQL-Klausel zu erstellen.

- Die [Sortier](../../data/odbc/recordset-sorting-records-odbc.md)reihenfolge für das Recordset, sofern vorhanden, die im [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort)-Datenmember enthalten ist. Das Framework verwendet diese Zeichenfolge, um eine **ORDER BY**-SQL-Klausel zu erstellen.

   > [!TIP]
   > Möchten Sie die **GROUP BY**-SQL-Klausel (und möglicherweise die **HAVING**-Klausel) verwenden, fügen Sie die Klauseln am Ende Ihrer Filterzeichenfolge an.

- Die Werte eines beliebigen [Parameterdatenmembers](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md), das Sie für die Klasse angeben. Sie legen Parameterwerte fest, unmittelbar bevor Sie `Open` oder `Requery` aufrufen. Das Framework bindet die Parameterwerte an „?“-Platzhalter in der SQL-Zeichenfolge. Zur Kompilierzeit geben Sie die Zeichenfolge mit Platzhaltern an. Zur Laufzeit füllt das Framework die Details anhand der Parameterwerte aus, die Sie übergeben.

`Open` erstellt eine **SELECT**-SQL-Anweisung aus diesen Bestandteilen. Ausführlichere Informationen darüber, wie das Framework die Bestandteile verwendet, finden Sie unter [Anpassen der Auswahl](#_core_customizing_the_selection).

Nachdem die Anweisung erstellt ist, sendet `Open` die SQL-Anweisung an den ODBC-Treiber-Manager (und die ODBC-Cursorbibliothek, wenn sie sich im Speicher befindet), der sie an den ODBC-Treiber für das spezielle DBMS sendet. Der Treiber kommuniziert mit dem DBMS, um die Auswahl für die Datenquelle auszuführen, und ruft den ersten Datensatz ab. Das Framework lädt den Datensatz in die Felddatenmember des Recordset-Objekts.

Sie können eine Kombination dieser Techniken verwenden, um [Tabellen](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md) zu öffnen und eine Abfrage zu erstellen, die auf einer [Verknüpfung](../../data/odbc/recordset-performing-a-join-odbc.md) (Join) mehrerer Tabellen basiert. In einer weiteren Anpassung können Sie [vordefinierte Abfragen](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) (gespeicherte Prozeduren) aufrufen, die Tabellenspalten auswählen, die zur Entwurfszeit nicht bekannt waren, und diese Spalten an die Recordset-Felder [binden](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md), oder Sie können die meisten anderen Datenzugriffsaufgaben ausführen. Aufgaben, die Sie nicht durch Anpassen von Recordsets erledigen können, lassen sich weiterhin durch [Aufrufen von ODBC-API-Funktionen](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) oder direkt durch Ausführen von SQL-Anweisungen mit [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) erledigen.

## <a name="customizing-the-selection"></a><a name="_core_customizing_the_selection"></a> Anpassen der Auswahl

Neben der Bereitstellung eines Filters, einer Sortierreihenfolge oder von Parametern können Sie die Auswahl Ihres Recordsets mit den folgenden Aktionen anpassen:

- Übergeben Sie eine benutzerdefinierte SQL-Zeichenfolge in *lpszSQL*, wenn Sie [Open](../../mfc/reference/crecordset-class.md#open) für das Recordset aufrufen. Alle Werte, die Sie in *lpsqSQL* übergeben, haben Vorrang vor den Werten, die von der [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql)-Memberfunktion zurückgegeben werden.

   Weitere Informationen finden Sie unter [SQL: Customizing Your Recordset es SQL Statement (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md), das die `Open` Typen von SQL-Anweisungen (oder Teilanweisungen) beschreibt, die Sie übergeben können, und was das Framework mit ihnen macht.

    > [!NOTE]
    >  Wenn die benutzerdefinierte Zeichenfolge, die Sie übergeben, nicht mit „SELECT“ oder „{CALL“ beginnt, geht MFC davon aus, dass sie einen Tabellennamen enthält. Dies gilt auch für den nächsten aufgezählten Punkt.

- Ändern Sie die Zeichenfolge, die der Assistent in die `GetDefaultSQL`-Memberfunktion Ihres Recordsets schreibt. Bearbeiten Sie den Code der Funktion, um deren Rückgabewerte zu ändern. Standardmäßig schreibt der Assistent eine `GetDefaultSQL`-Funktion, die einen einzigen Tabellennamen zurückgibt.

   Sie können veranlassen, dass `GetDefaultSQL` jedes beliebige der Elemente zurückgibt, die Sie im *lpszSQL*Parameter an `Open` übergeben können. Wenn Sie keine benutzerdefinierte SQL-Zeichenfolge in *lpszSQL* übergeben, verwendet das Framework die Zeichenfolge, die `GetDefaultSQL` zurückgibt. Als Mindestanforderung muss `GetDefaultSQL` den Namen einer einzelnen Tabelle zurückgeben. Sie können für diese Funktion aber auch festlegen, dass sie mehrere Tabellennamen, eine vollständige **SELECT**-Anweisung, eine **CALL**-ODBC-Anweisung usw. zurückgibt. Eine Liste dessen, was Sie an *lpszSQL* übergeben können – oder zurück haben `GetDefaultSQL` – finden Sie unter [SQL: Customizing Your Recordset es SQL Statement (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

   Wenn Sie mehrere Tabellen verknüpfen, schreiben Sie `GetDefaultSQL` um, damit die Tabellenliste angepasst wird, die in der **FROM**-SQL-Klausel verwendet wird. Weitere Informationen finden Sie unter [Recordset: Ausführen eines Joins (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

- Binden Sie weitere Felddatenmember manuell, vielleicht anhand von Informationen, die Sie zur Laufzeit über das Schema Ihrer Datenquelle erhalten. Fügen Sie Felddatenmember zur Recordset-Klasse, [RFX](../../data/odbc/record-field-exchange-using-rfx.md)- oder Bulk-RFX-Funktionsaafrufe für diese zur [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange)- oder [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)-Memberfunktion und Initialisierungen der Datenmember im Klassenkonstruktor hinzu. Weitere Informationen finden Sie unter [Recordset: Dynamically Binding Data Columns (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Überschreiben Sie Memberkunktionen, z. B. `OnSetOptions`, um anwendungsspezifische Optionen festzulegen oder Standardwerte zu überschreiben.

Wenn Sie für das Recordset eine komplexe SQL­-Anweisung verwenden möchten, müssen Sie eine Kombination dieser Anpassungstechniken verwenden. Es könnte beispielsweise sein, dass Sie SQL-Klauseln und -Schlüsselwörter verwenden möchten, die nicht direkt von Recordsets unterstützt werden, oder dass Sie mehrere Tabellen verknüpfen.

## <a name="see-also"></a>Siehe auch

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Datensatzaktualisierung durch Recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[ODBC Grundlagen](../../data/odbc/odbc-basics.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Recordset: Sperren von Datensätzen (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

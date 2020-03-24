---
title: 'Recordset: Erstellen und Schließen von Recordsets (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- ODBC recordsets, creating
- recordsets, creating
- recordsets, opening
- recordsets, closing
- ODBC recordsets, closing
- ODBC recordsets, opening
ms.assetid: 8d2aac23-4396-4ce2-8c60-5ecf1b360d3d
ms.openlocfilehash: 155b51debfb6eacd3cbdd3293875274ca2dc4ab5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212978"
---
# <a name="recordset-creating-and-closing-recordsets-odbc"></a>Recordset: Erstellen und Schließen von Recordsets (ODBC)

> [!NOTE]
> Der MFC-ODBC-Consumer-Assistent ist in Visual Studio 2019 und höher nicht verfügbar. Sie können einen Consumer weiterhin manuell erstellen.

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

Um ein Recordset zu verwenden, erstellen Sie ein Recordset-Objekt, und rufen Sie dann dessen `Open`-Memberfunktion auf, um die Abfrage des Recordsets auszuführen und Datensätze auszuwählen. Wenn Sie das Arbeiten mit dem Recordset beenden möchten, schließen und zerstören Sie das Objekt.

In diesem Thema wird Folgendes erläutert:

- [Wann und wie Sie ein Recordset-Objekt erstellen können](#_core_creating_recordsets_at_run_time).

- [Wann und wie Sie das Verhalten des Recordsets durch Parametrisieren, Filtern, Sortieren oder Sperren bestimmen können](#_core_setting_recordset_options).

- [Wann und wie Sie ein Recordset-Objekt schließen können](#_core_closing_a_recordset).

##  <a name="creating-recordsets-at-run-time"></a><a name="_core_creating_recordsets_at_run_time"></a> Erstellen von Recordsets zur Laufzeit

Bevor Sie Recordset-Objekte in Ihrem Programm erstellen können, schreiben Sie üblicherweise anwendungsspezifische Recordset-Klassen. Weitere Informationen zu diesem vorbereitenden Schritt finden Sie unter [Hinzufügen eines MFC-ODBC-Consumers](../../mfc/reference/adding-an-mfc-odbc-consumer.md).

Öffnen Sie ein Dynaset- oder Momentaufnahmeobjekt, wenn Sie Datensätze in einer Datenquelle auswählen möchten. Der Typ des zu erstellenden Objekts hängt davon ab, welche Aktionen Sie mit den Daten in Ihrer Anwendung ausführen möchten und welche Aktionen Ihr ODBC-Treiber unterstützt. Weitere Informationen finden Sie unter [Dynaset](../../data/odbc/dynaset.md) und [Momentaufnahme](../../data/odbc/snapshot.md).

#### <a name="to-open-a-recordset"></a>So öffnen Sie ein Recordset

1. Erstellen Sie ein Objekt von Ihrer aus `CRecordset` abgeleiteten Klasse.

   Sie können das Objekt auf dem Heap oder dem m Stapelrahmen einer Funktion erstellen.

1. Ändern Sie ggf. das Standardverhalten des Recordsets. Die verfügbaren Optionen finden Sie unter [Festlegen von Recordset-Optionen](#_core_setting_recordset_options).

1. Rufen Sie die [Open](../../mfc/reference/crecordset-class.md#open)-Memberfunktion des Objekts auf.

Übergeben Sie im Konstruktor einen Zeiger zu einem `CDatabase`-Objekt, oder übergeben Sie NULL, um ein temporäres Objekt zu verwenden, das vom Framework anhand der Verbindungszeichenfolge erstellt und geöffnet wird, die von der [GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect)-Memberfunktion zurückgegeben wurde. Das `CDatabase`-Objekt ist möglicherweise bereits mit einer Datenquelle verbunden.

Im Aufruf von `Open` wird SQL verwendet, um Datensätze in der Datenquelle auszuwählen. Der erste ausgewählte Datensatz (sofern vorhanden) ist der aktuelle Datensatz. Die Werte der Felder dieses Datensatzes werden in den Felddatenmembern des Recordset-Objekts gespeichert. Wurden irgendwelche Datensätze ausgewählt, gibt sowohl die `IsBOF`- als auch die `IsEOF`-Memberfunktion „0“ zurück.

In Ihrem [Open](../../mfc/reference/crecordset-class.md#open)-Aufruf können Sie:

- Angeben, ob das Recordset ein Dynaset oder eine Momentaufnahme ist. Recordsets werden standardmäßig als Momentaufnahmen geöffnet. Alternativ können Sie ein Vorwärtsrecordset angeben, das nur Vorwärtsscrollen um jeweils einen Datensatz ermöglicht.

   Standardmäßig wird für ein Recordset der Standardtyp verwendet, der im `CRecordset`-Datenmember `m_nDefaultType` gespeichert ist. Assistenten schreiben Code, mit dem `m_nDefaultType` auf den Recordsettyp initialisiert wird, den Sie im Assistenten ausgewählt haben. Anstatt diese Standardeinstellung zu übernehmen, können Sie den Typ durch einen anderen Recordsettyp ersetzen.

- Geben Sie eine Zeichenfolge an, durch die die standardmäßige **SELECT**-SQL-Anweisung ersetzt wird, die das Recordset erstellt.

- Geben Sie an, ob das Recordset schreibgeschützt (readOnly) oder nur erweiterbar (appendOnly) ist. Recordsets ermöglichen standardmäßig vollständige Aktualisierung, Sie können dies aber auf das Hinzufügen neuer Datensätze beschränken, oder Sie können jegliche Aktualisierungen verhindern.

Das folgende Beispiel zeigt, wie ein schreibgeschütztes Momentaufnahmeobjekt der Klasse `CStudentSet` (eine anwendungsspezifische Klasse) geöffnet wird:

```cpp
// Construct the snapshot object
CStudentSet rsStudent( NULL );
// Set options if desired, then open the recordset
if(!rsStudent.Open(CRecordset::snapshot, NULL, CRecordset::readOnly))
    return FALSE;
// Use the snapshot to operate on its records...
```

Nachdem Sie `Open` aufgerufen haben, verwenden Sie die Memberfunktionen und Datenmember des Objekts, um mit den Datensätzen zu arbeiten. In einigen Fällen möchten Sie das Recordset möglicherweise erneut abfragen oder aktualisieren, damit die Änderungen einbezogen werden, die in der Datenquelle vorgenommen wurden. Weitere Informationen finden Sie unter [Recordset: anweisen eines Recordsets (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).

> [!TIP]
>  Die Verbindungszeichenfolge, die Sie während der Entwicklung verwenden, ist möglicherweise nicht mit der identisch, die die eigentlichen Benutzer benötigen. Ideen zum generalisieren Ihrer Anwendung in dieser Hinsicht finden Sie unter [Datenquelle: Verwalten von Verbindungen (ODBC)](../../data/odbc/data-source-managing-connections-odbc.md).

##  <a name="setting-recordset-options"></a><a name="_core_setting_recordset_options"></a> Festlegen von Recordset-Optionen

Nachdem Sie Ihr Recordset-Objekt erstellt haben, aber vor dem Aufrufen von `Open`, um Datensätze auszuwählen, möchten Sie möglicherweise einige Optionen festlegen, mit denen das Verhalten des Recordsets gesteuert wird. Für alle Recordsets können Sie folgende Aktionen ausführen:

- Angeben eines [Filters](../../data/odbc/recordset-filtering-records-odbc.md), um die Datensatzauswahl einzuschränken

- Angeben einer [Sortierreihenfolge](../../data/odbc/recordset-sorting-records-odbc.md) für das Recordset

- Angeben von [Parametern](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md), damit Datensätze anhand von Informationen ausgewählt werden können, die zur Laufzeit abgerufen oder berechnet wurden

Sie können auch die folgende Option festlegen, wenn die Bedingungen geeignet sind:

- Wenn das Recordset aktualisierbar ist und Sperroptionen unterstützt, geben Sie die [Sperr](../../data/odbc/recordset-locking-records-odbc.md)methode an, die für Aktualisierungen verwendet werden soll.

> [!NOTE]
>  Damit sich diese Optionen auf die jeweilige Datensatzauswahl auswirken, müssen Sie sie festlegen, bevor die `Open`-Memberfunktion aufgerufen wird.

##  <a name="closing-a-recordset"></a><a name="_core_closing_a_recordset"></a> Schließen eines Recordsets

Wenn Sie nicht weiter mit dem Recordset arbeiten möchten, müssen Sie es löschen und dessen reservierten Speicher freigeben.

#### <a name="to-close-a-recordset"></a>So schließen Sie ein Recordset

1. Rufen Sie dessen [Close](../../mfc/reference/crecordset-class.md#close)-Memberfunktion auf.

1. Zerstören Sie das Recordset-Objekt.

   Wenn Sie das Objekt auf dem Stapelrahmen einer Funktion deklariert haben, wird das Objekt automatisch zerstört, wenn es aus dem Gültigkeitsbereich herausfällt. Verwenden Sie andernfalls den **delete**-Operator.

`Close` bewirkt, dass das `HSTMT`-Handle des Recordsets freigegeben wird. „Close“ zerstört nicht das C++ Objekt.

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Scrollen (ODBC)](../../data/odbc/recordset-scrolling-odbc.md)<br/>
[Recordset: Hinzufügen, Aktualisieren und Löschen von Datensätzen (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)

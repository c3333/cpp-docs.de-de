---
title: 'Recordset: Filtern von Datensätzen (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
ms.openlocfilehash: 56b8c4f52ec294f58a760e1309d32aa81286ddec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367018"
---
# <a name="recordset-filtering-records-odbc"></a>Recordset: Filtern von Datensätzen (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In diesem Thema wird erläutert, wie ein Recordset gefiltert wird, sodass nur eine bestimmte Teilmenge der verfügbaren Datensätze ausgewählt wird. Sie können z. B. nur die Klassenabschnitte für einen bestimmten Kurs auswählen, z. B. MATH101. Ein Filter ist eine Suchbedingung, die durch den Inhalt einer SQL **WHERE-Klausel** definiert ist. Wenn das Framework es an die SQL-Anweisung des Recordsets anfügt, schränkt die **WHERE-Klausel** die Auswahl ein.

Sie müssen den Filter eines Recordset-Objekts einrichten, nachdem `Open` Sie das Objekt erstellt `Requery` haben, aber bevor Sie `Open` seine Memberfunktion aufrufen (oder bevor Sie die Memberfunktion für ein vorhandenes Recordset-Objekt aufrufen, dessen Memberfunktion zuvor aufgerufen wurde).

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>So geben Sie einen Filter für ein Recordset-Objekt an

1. Erstellen Sie ein neues Recordset-Objekt (oder bereiten Sie sich auf den Aufruf `Requery` eines vorhandenen Objekts vor).

1. Legen Sie den Wert des [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) Datenmembers des Objekts fest.

   Der Filter ist eine null-terminierte Zeichenfolge, die den Inhalt der SQL **WHERE-Klausel** enthält, jedoch nicht das Schlüsselwort **WHERE**. Verwenden Sie z.B. Folgendes:

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   not

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  Die Literalzeichenfolge "MATH101" wird oben mit einzelnen Anführungszeichen angezeigt. In der ODBC SQL-Spezifikation werden einfache Anführungszeichen verwendet, um ein Zeichenfolgenliteral zu bezeichnen. Überprüfen Sie in ihrer ODBC-Treiberdokumentation die Angebotsanforderungen Ihres DBMS in diesem Fall. Diese Syntax wird auch am Ende dieses Themas weiter diskutiert.

1. Legen Sie alle anderen Optionen fest, die Sie benötigen, z. B. Sortierreihenfolge, Sperrmodus oder Parameter. Die Angabe eines Parameters ist besonders nützlich. Informationen zur Parametrierung Ihres Filters finden Sie unter [Recordset: Parametrierung eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Rufen `Open` Sie das neue `Requery` Objekt (oder ein zuvor geöffnetes Objekt) auf.

> [!TIP]
> Die Verwendung von Parametern in Ihrem Filter ist möglicherweise die effizienteste Methode zum Abrufen von Datensätzen.

> [!TIP]
> Recordset-Filter eignen sich zum [Verknüpfen](../../data/odbc/recordset-performing-a-join-odbc.md) von Tabellen und zur Verwendung von [Parametern,](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) die auf Informationen basieren, die zur Laufzeit abgerufen oder berechnet werden.

Das Recordset wählt nur die Datensätze aus, die die von Ihnen angegebene Suchbedingung erfüllen. Um z. B. den oben beschriebenen `strCourseID` Kursfilter anzugeben (vorausgesetzt, eine Variable, die derzeit z. B. auf "MATH101" festgelegt ist), gehen Sie wie folgt vor:

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

Das Recordset enthält Datensätze für alle Klassenabschnitte für MATH101.

Beachten Sie, wie die Filterzeichenfolge im obigen Beispiel mithilfe einer Zeichenfolgenvariablen festgelegt wurde. Dies ist die typische Verwendung. Angenommen, Sie möchten den Literalwert 100 für die Kurs-ID angeben. Der folgende Code zeigt, wie die Filterzeichenfolge mit einem Literalwert richtig festgelegt wird:

```
m_strFilter = "StudentID = '100'";   // correct
```

Beachten Sie die Verwendung von Zeichen mit einem einzigen Anführungszeichen; Wenn Sie die Filterzeichenfolge direkt festlegen, lautet die Filterzeichenfolge **nicht:**

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

Das oben gezeigte Zitat entspricht der ODBC-Spezifikation, aber einige DBMS erfordern möglicherweise andere Anführungszeichen. Weitere Informationen finden Sie unter SQL: Anpassen der [SQL-Anweisung (ODBC) Ihres Recordsets](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

> [!NOTE]
> Wenn Sie die SQL-Standardzeichenfolge des Recordsets überschreiben möchten, `Open`indem Sie Ihre eigene SQL-Zeichenfolge an übergeben, sollten Sie keinen Filter festlegen, wenn Ihre benutzerdefinierte Zeichenfolge über eine **WHERE-Klausel** verfügt. Weitere Informationen zum Überschreiben von SQL standardfinden Sie unter [SQL: Customizing Your Recordset es SQL Statement (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Siehe auch

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Sortieren von Datensätzen (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[Recordset: Datensatzauswahl durch Recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Recordset: Datensatzaktualisierung durch Recordsets (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Recordset: Sperren von Datensätzen (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

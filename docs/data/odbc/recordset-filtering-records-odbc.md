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
ms.openlocfilehash: 2e742ee02e142fd87df3f149379d9971c4acd166
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212906"
---
# <a name="recordset-filtering-records-odbc"></a>Recordset: Filtern von Datensätzen (ODBC)

Dieses Thema bezieht sich auf die MFC-ODBC-Klassen.

In diesem Thema wird erläutert, wie ein Recordset so gefiltert wird, dass nur eine bestimmte Teilmenge der verfügbaren Datensätze ausgewählt wird. Beispielsweise möchten Sie möglicherweise nur die Klassen Abschnitte für einen bestimmten Kurs auswählen, z. b. MATH101. Ein Filter ist eine Such Bedingung, die durch den Inhalt einer SQL- **Where** -Klausel definiert wird. Wenn das Framework es an die SQL-Anweisung des Recordsets anfügt, schränkt die **Where** -Klausel die Auswahl ein.

Sie müssen den Filter eines Recordset-Objekts einrichten, nachdem Sie das-Objekt erstellt haben, aber bevor Sie seine `Open` Member-Funktion aufrufen (oder bevor Sie die `Requery` Member-Funktion für ein vorhandenes Recordset-Objekt aufrufen, dessen `Open` Member-Funktion zuvor aufgerufen wurde).

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>So geben Sie einen Filter für ein Recordset-Objekt an

1. Erstellen Sie ein neues Recordset-Objekt (oder bereiten Sie das aufzurufen `Requery` für ein vorhandenes Objekt vor).

1. Legen Sie den Wert für das [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) Datenmember des Objekts fest.

   Der Filter ist eine NULL-terminierte Zeichenfolge, die den Inhalt der **Where** -Klausel von SQL, jedoch nicht das Schlüsselwort **Where**enthält. Verwenden Sie z.B. Folgendes:

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   not

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  Die Literalzeichenfolge "MATH101" wird oben in einfache Anführungszeichen angezeigt. In der ODBC-SQL-Spezifikation werden einfache Anführungszeichen verwendet, um ein Zeichenfolgenliteralzeichen anzugeben. In der Dokumentation zum ODBC-Treiber finden Sie Informationen zu den Anforderungen Ihres DBMS in dieser Situation. Diese Syntax wird auch weiter unten in diesem Thema erläutert.

1. Legen Sie alle anderen benötigten Optionen fest, z. b. die Sortierreihenfolge, den Sperrmodus oder Parameter. Die Angabe eines-Parameters ist besonders nützlich. Weitere Informationen zum parametrisierten Filtern finden Sie unter [Recordset: parametrialisieren eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Ruft `Open` für das neue Objekt (oder für ein zuvor geöffnetes Objekt `Requery`) auf.

> [!TIP]
>  Die Verwendung von Parametern in Ihrem Filter ist möglicherweise die effizienteste Methode zum Abrufen von Datensätzen.

> [!TIP]
>  Recordsetfilter sind nützlich zum [verbinden](../../data/odbc/recordset-performing-a-join-odbc.md) von Tabellen und zum Verwenden von [Parametern](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) , die auf Informationen basieren, die zur Laufzeit abgerufen oder berechnet werden.

Das Recordset wählt nur die Datensätze aus, die die angegebene Such Bedingung erfüllen. Um z. b. den oben beschriebenen Kurs Filter anzugeben (vorausgesetzt, eine Variable `strCourseID` aktuell festgelegt, z. b. auf "MATH101"), gehen Sie wie folgt vor:

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

Das Recordset enthält Datensätze für alle Klassen Abschnitte für MATH101.

Beachten Sie, wie die Filter Zeichenfolge im obigen Beispiel mithilfe einer Zeichen folgen Variablen festgelegt wurde. Dies ist die typische Verwendung. Angenommen, Sie möchten den Literalwert 100 für die Kurs-ID angeben. Der folgende Code zeigt, wie Sie die Filter Zeichenfolge mit einem Literalwert ordnungsgemäß festlegen:

```
m_strFilter = "StudentID = '100'";   // correct
```

Beachten Sie die Verwendung von einfachen Anführungszeichen. Wenn Sie die Filter Zeichenfolge direkt festlegen, lautet die Filter Zeichenfolge **nicht**wie folgt:

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

Die oben gezeigten Anführungszeichen entsprechen der ODBC-Spezifikation, aber einige DBMSs erfordern möglicherweise andere Anführungszeichen. Weitere Informationen finden Sie unter [SQL: Anpassen der SQL-Anweisung ihres Recordsets (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

> [!NOTE]
>  Wenn Sie die standardmäßige SQL-Zeichenfolge des Recordsets überschreiben möchten, indem Sie Ihre eigene SQL-Zeichenfolge an `Open`übergeben, sollten Sie keinen Filter festlegen, wenn die benutzerdefinierte Zeichenfolge über eine **Where** -Klausel verfügt. Weitere Informationen zum Überschreiben der Standard [-SQL-Anweisung finden Sie unter SQL: Anpassen der SQL-Anweisung ihres Recordsets (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Weitere Informationen

[Recordset (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Sortieren von Datensätzen (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[Recordset: Wie Recordsets Datensätze auswählen (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Recordset: Wie Recordsets Datensätze aktualisieren (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Recordset: Sperren von Datensätzen (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)

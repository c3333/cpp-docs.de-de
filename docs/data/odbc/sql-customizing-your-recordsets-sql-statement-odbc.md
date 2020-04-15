---
title: 'SQL: Anpassen der SQL-Anweisung eines Recordsets (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, SQL statements
- ODBC recordsets, SQL statements
- SQL statements, customizing
- SQL statements, recordset
- customizing SQL statements
- overriding, SQL statements
- SQL, opening recordsets
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
ms.openlocfilehash: 083d268d2b2f2eef072809b1afde9d6ea34f6996
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374521"
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL: Anpassen der SQL-Anweisung eines Recordsets (ODBC)

In diesem Thema wird Folgendes erläutert:

- Wie das Framework eine SQL-Anweisung erstellt

- Überschreiben der SQL-Anweisung

> [!NOTE]
> Diese Informationen gelten für die MFC-ODBC-Klassen. Wenn Sie mit den MFC DAO-Klassen arbeiten, lesen Sie das Thema "Vergleich von Microsoft Jet Database Engine SQL und ANSI SQL" in der DAO-Hilfe.

## <a name="sql-statement-construction"></a>SQL-Anweisungskonstruktion

Ihr Recordset basiert die Datensatzauswahl in erster Linie auf einer SQL **SELECT-Anweisung.** Wenn Sie Ihre Klasse mit einem Assistenten deklarieren, schreibt sie eine übergeordnete Version der Memberfunktion, die `GetDefaultSQL` etwa so aussieht (für eine Recordset-Klasse namens `CAuthors`).

```cpp
CString CAuthors::GetDefaultSQL()
{
    return "AUTHORS";
}
```

Standardmäßig gibt diese Außerkraftsetzung den Tabellennamen zurück, den Sie mit dem Assistenten angegeben haben. Im Beispiel lautet der Tabellenname "AUTHORS". Wenn Sie später die Memberfunktion `Open` des `Open` Recordsets aufrufen, wird eine endgültige **SELECT-Anweisung** des Formulars erstellt:

```
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]
       [ORDER BY m_strSort]
```

wobei `table-name` durch Aufrufen `GetDefaultSQL` `rfx-field-list` abgerufen wird und von den `DoFieldExchange`RFX-Funktionsaufrufen in abgerufen wird. Dies ist das, was Sie für eine **SELECT-Anweisung** erhalten, es sei denn, Sie ersetzen sie durch eine übergeordnete Version zur Laufzeit, obwohl Sie auch die Standardanweisung mit Parametern oder einem Filter ändern können.

> [!NOTE]
> Wenn Sie einen Spaltennamen angeben, der Leerzeichen enthält (oder enthalten könnte), müssen Sie den Namen in eckige Klammern einschließen. Der Name "Vorname" sollte z. B. "[Vorname]" sein.

Um die standardmäßige **SELECT-Anweisung** zu überschreiben, übergeben `Open`Sie beim Aufrufen eine Zeichenfolge mit einer vollständigen **SELECT-Anweisung.** Anstatt eine eigene Standardzeichenfolge zu erstellen, verwendet das Recordset die von Ihnen gelieferte Zeichenfolge. Wenn Ihre Ersatzanweisung eine **WHERE-Klausel** enthält, `m_strFilter` geben Sie keinen Filter in an, da Sie dann über zwei Filteranweisungen verfügen würden. Wenn Ihre Ersatzanweisung eine **ORDER BY-Klausel** enthält, `m_strSort` geben Sie auch keine Sortierung an, damit Sie nicht über zwei Sortierungsanweisungen verfügen.

> [!NOTE]
> Wenn Sie Literalzeichenfolgen in Ihren Filtern (oder anderen Teilen der SQL-Anweisung) verwenden, müssen Sie solche Zeichenfolgen mit einem DBMS-spezifischen Literalpräfix und einem Literalsuffixzeichen (oder Zeichen) "zitieren" (in bestimmte Trennzeichen einschließen).

Je nach DBMS können auch spezielle syntaktische Anforderungen für Vorgänge wie äußere Verknüpfungen auftreten. Verwenden Sie ODBC-Funktionen, um diese Informationen von Ihrem Treiber für das DBMS abzuholen. Rufen Sie `::SQLGetTypeInfo` beispielsweise einen bestimmten Datentyp `SQL_VARCHAR`auf, z. B. , um die LITERAL_PREFIX und LITERAL_SUFFIX Zeichen anzufordern. Wenn Sie datenbankunabhängigen Code schreiben, finden Sie detaillierte Syntaxinformationen unter [Anhang C: SQL Grammar](/sql/odbc/reference/appendixes/appendix-c-sql-grammar) in der [ODBC-Programmiererreferenz.](/sql/odbc/reference/odbc-programmer-s-reference)

Ein Recordset-Objekt erstellt die SQL-Anweisung, die es zum Auswählen von Datensätzen verwendet, es sei denn, Sie übergeben eine benutzerdefinierte SQL-Anweisung. Wie dies geschieht, hängt hauptsächlich von dem Wert ab, den Sie im *lpszSQL-Parameter* der `Open` Memberfunktion übergeben.

Die allgemeine Form einer SQL **SELECT-Anweisung** lautet:

```
SELECT [ALL | DISTINCT] column-list FROM table-list
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]
```

Eine Möglichkeit, das **DISTINCT-Schlüsselwort** zur SQL-Anweisung Ihres Recordsets hinzuzufügen, besteht darin, das Schlüsselwort in den ersten RFX-Funktionsaufruf in `DoFieldExchange`einzubetten. Beispiel:

```
...
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);
...
```

> [!NOTE]
> Verwenden Sie diese Technik nur mit einem Recordset, das als schreibgeschützt geöffnet ist.

## <a name="overriding-the-sql-statement"></a>Überschreiben der SQL-Anweisung

Die folgende Tabelle zeigt die Möglichkeiten für `Open`den *lpszSQL-Parameter* zu . Die Fälle in der Tabelle werden im Anschluss an die Tabelle erläutert.

**Der lpszSQL-Parameter und der resultierende SQL-String**

|Fall|Was Sie in lpszSQL passieren|Die resultierende SELECT-Anweisung|
|----------|------------------------------|------------------------------------|
|1|NULL|**SELECT** *rfx-field-list* **VON** *Tabellenname*<br /><br /> `CRecordset::Open`, `GetDefaultSQL` um den Tabellennamen abzubekommen. Die resultierende Zeichenfolge ist einer der Fälle `GetDefaultSQL` 2 bis 5, je nachdem, was zurückkehrt.|
|2|Einen Tabellennamen|**SELECT** *rfx-field-list* **VON** *Tabellenname*<br /><br /> Die Feldliste wird den RFX-Anweisungen in `DoFieldExchange`entnommen. Wenn `m_strFilter` `m_strSort` und nicht leer sind, fügen Sie die **WHERE-** und/oder **ORDER BY-Klauseln** hinzu.|
|3\*|Eine **SELECT** vollständige SELECT-Anweisung, jedoch ohne **WHERE-** oder **ORDER BY-Klausel**|Wie bestanden. Wenn `m_strFilter` `m_strSort` und nicht leer sind, fügen Sie die **WHERE-** und/oder **ORDER BY-Klauseln** hinzu.|
|4\*|Eine vollständige **SELECT-Anweisung** mit einer **WHERE-** und/oder **ORDER BY-Klausel**|Wie bestanden. `m_strFilter`und/oder `m_strSort` müssen leer bleiben, oder es werden zwei Filter- und/oder Sortieranweisungen erstellt.|
|5\*|Ein Aufruf einer gespeicherten Prozedur|Wie bestanden.|

\*`m_nFields` muss kleiner oder gleich der Anzahl der Spalten sein, die in der **SELECT-Anweisung** angegeben sind. Der Datentyp jeder Spalte, die in der **SELECT-Anweisung** angegeben ist, muss mit dem Datentyp der entsprechenden RFX-Ausgabespalte identisch sein.

### <a name="case-1---lpszsql--null"></a>Fall 1 lpszSQL = NULL

Die Recordset-Auswahl `GetDefaultSQL` hängt `CRecordset::Open` davon ab, was beim Aufrufen zurückgegeben wird. Die Fälle 2 bis 5 beschreiben die möglichen Strings.

### <a name="case-2---lpszsql--a-table-name"></a>Fall 2 lpszSQL = ein Tabellenname

Das Recordset verwendet Datensatzfeldaustausch (Record Field Exchange, RFX), um die Spaltenliste aus den Spaltennamen `DoFieldExchange`zu erstellen, die in den RFX-Funktionsaufrufen in der Überschreibung von der Recordset-Klasse bereitgestellt werden. Wenn Sie einen Assistenten verwendet haben, um Ihre Recordset-Klasse zu deklarieren, hat diese Anfrage das gleiche Ergebnis wie Fall 1 (vorausgesetzt, Sie übergeben denselben Tabellennamen, den Sie im Assistenten angegeben haben). Wenn Sie zum Schreiben Ihrer Klasse keinen Assistenten verwenden, ist Fall 2 die einfachste Möglichkeit, die SQL-Anweisung zu erstellen.

Im folgenden Beispiel wird eine SQL-Anweisung erstellt, die Datensätze aus einer MFC-Datenbankanwendung auswählt. Wenn das Framework `GetDefaultSQL` die Memberfunktion aufruft, gibt `SECTION`die Funktion den Namen der Tabelle zurück.

```cpp
CString CEnrollSet::GetDefaultSQL()
{
    return "SECTION";
}
```

Um die Namen der Spalten für die SQL **SELECT-Anweisung** abzuerhalten, ruft das Framework die `DoFieldExchange` Memberfunktion auf.

```cpp
void CEnrollSet::DoFieldExchange(CFieldExchange* pFX)
{
    pFX->SetFieldType(CFieldExchange::outputColumn);
    RFX_Text(pFX, "CourseID", m_strCourseID);
    RFX_Text(pFX, "InstructorID", m_strInstructorID);
    RFX_Text(pFX, "RoomNo", m_strRoomNo);
    RFX_Text(pFX, "Schedule", m_strSchedule);
    RFX_Text(pFX, "SectionNo", m_strSectionNo);
}
```

Wenn die SQL-Anweisung abgeschlossen ist, sieht sie wie folgt aus:

```sql
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo
    FROM SECTION
```

### <a name="case-3---lpszsql--a-selectfrom-statement"></a>Fall 3 lpszSQL = eine SELECT/FROM-Anweisung

Sie geben die Spaltenliste von Hand an, anstatt sich auf RFX zu verlassen, um sie automatisch zu erstellen. Sie können dies tun, wenn:

- Sie möchten das **Schlüsselwort DISTINCT** nach **SELECT**angeben.

   Die Spaltenliste sollte mit den Spaltennamen und -typen `DoFieldExchange`in der gleichen Reihenfolge übereinstimmen, in der sie in aufgeführt sind.

- Sie haben Grund, Spaltenwerte manuell mithilfe `::SQLGetData` der ODBC-Funktion abzurufen, anstatt sich auf RFX zu verlassen, um Spalten für Sie zu binden und abzurufen.

   Sie können z. B. neue Spalten aufnehmen, die ein Kunde Ihrer Anwendung den Datenbanktabellen hinzugefügt hat, nachdem die Anwendung verteilt wurde. Sie müssen diese zusätzlichen Felddatenmember hinzufügen, die zum Zeitpunkt der Demeldete der Klasse mit einem Assistenten nicht bekannt waren.

   Die Spaltenliste sollte mit den Spaltennamen und -typen `DoFieldExchange`in der gleichen Reihenfolge übereinstimmen, in der sie in aufgeführt sind, gefolgt von den Namen der manuell gebundenen Spalten. Weitere Informationen finden Sie unter [Recordset: Dynamically Binding Data Columns (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Sie möchten Tabellen verknüpfen, indem Sie mehrere Tabellen in der **FROM-Klausel** angeben.

   Weitere Informationen und ein Beispiel finden Sie unter [Recordset: Performing a Join (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>Fall 4 lpszSQL = SELECT/FROM Plus WHERE und/oder ORDER BY

Sie geben alles an: die Spaltenliste (basierend auf den RFX-Aufrufen in `DoFieldExchange`), die Tabellenliste und den Inhalt einer **WHERE-** und/oder ORDER **BY-Klausel.** Wenn Sie Ihre **WHERE-** und/oder ORDER BY-Klauseln auf `m_strSort`diese Weise angeben, verwenden **ORDER BY** `m_strFilter` Sie nicht und/oder .

### <a name="case-5---lpszsql--a-stored-procedure-call"></a>Fall 5 lpszSQL = ein gespeicherter Prozeduraufruf

Wenn Sie eine vordefinierte Abfrage aufrufen müssen (z. B. eine gespeicherte Prozedur in einer Microsoft SQL Server-Datenbank), müssen Sie eine **CALL-Anweisung** in die Zeichenfolge schreiben, die Sie an *lpszSQL*übergeben. Die Assistenten unterstützen das Deklarieren einer Recordset-Klasse zum Aufrufen einer vordefinierten Abfrage nicht. Nicht alle vordefinierten Abfragen geben Datensätze zurück.

Wenn eine vordefinierte Abfrage keine Datensätze zurückgibt, können Sie die `CDatabase` Memberfunktion `ExecuteSQL` direkt verwenden. Für eine vordefinierte Abfrage, die Datensätze zurückgibt, müssen Sie `DoFieldExchange` die RFX-Aufrufe auch manuell für alle Spalten schreiben, die die Prozedur zurückgibt. Die RFX-Aufrufe müssen in derselben Reihenfolge sein und dieselben Typen zurückgeben wie die vordefinierte Abfrage. Weitere Informationen finden Sie unter [Recordset: Deklarieren einer Klasse für eine vordefinierte Abfrage (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).

## <a name="see-also"></a>Siehe auch

[SQL: SQL- und C++-Datentypen (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)<br/>
[SQL: Durchführen direkter SQL-Aufrufe (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

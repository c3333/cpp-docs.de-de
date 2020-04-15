---
title: 'SQL: Durchführen direkter SQL-Aufrufe (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- SQL, direct calls from ODBC
- SQL, calling directly from ODBC
- ODBC, SQL calls
- SQL calls
- direct SQL calls from ODBC
ms.assetid: 091988d2-f5a5-4c2d-aa09-8779a9fb9607
ms.openlocfilehash: e2421e047d217fdc7a138509385399fa37d36a1f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374499"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL: Durchführen direkter SQL-Aufrufe (ODBC)

In diesem Thema wird Folgendes erläutert:

- Verwenden direkter SQL-Aufrufe.

- [Wie Sie direkte SQL-Aufrufe an die Datenquelle tätigen](#_core_making_direct_sql_function_calls).

> [!NOTE]
> Diese Informationen gelten für die MFC-ODBC-Klassen. Wenn Sie mit den MFC DAO-Klassen arbeiten, lesen Sie das Thema "Vergleich von Microsoft Jet Database Engine SQL und ANSI SQL" in der DAO-Hilfe.

## <a name="when-to-call-sql-directly"></a><a name="_core_when_to_call_sql_directly"></a>Wann SQL direkt aufrufen

Um neue Tabellen zu erstellen, Tabellen zu löschen, vorhandene Tabellen zu ändern, Indizes zu erstellen und andere SQL-Funktionen auszuführen, die das [ODBC-Schema (Data Source)](../../data/odbc/data-source-odbc.md) ändern, müssen Sie eine SQL-Anweisung mithilfe der Datenbankdefinitionssprache (Data Definition Language, DDL) direkt an die Datenquelle ausstellen. Wenn Sie einen Assistenten verwenden, um ein Recordset für eine Tabelle (zur Entwurfszeit) zu erstellen, können Sie auswählen, welche Spalten der Tabelle im Recordset dargestellt werden sollen. Dies erlaubt keine Spalten, die Sie oder ein anderer Benutzer der Datenquelle später der Tabelle hinzufügen, nachdem das Programm kompiliert wurde. Die Datenbankklassen unterstützen DDL nicht direkt, aber Sie können weiterhin Code schreiben, um eine neue Spalte zur Laufzeit dynamisch an Ihr Recordset zu binden. Informationen zum Erstellen dieser Bindung finden Sie unter [Recordset: Dynamically Binding Data Columns (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Sie können das DBMS selbst verwenden, um das Schema oder ein anderes Tool zu ändern, mit dem Sie DDL-Funktionen ausführen können. Sie können auch ODBC-Funktionsaufrufe zum Senden von SQL-Anweisungen verwenden, z. B. aufrufen einer vordefinierten Abfrage (gespeicherte Prozedur), die keine Datensätze zurückgibt.

## <a name="making-direct-sql-function-calls"></a><a name="_core_making_direct_sql_function_calls"></a>Erstellen direkter SQL-Funktionsaufrufe

Sie können einen SQL-Aufruf direkt mit einem [CDatabase Class-Objekt](../../mfc/reference/cdatabase-class.md) ausführen. Richten Sie Ihre SQL-Anweisungszeichenfolge (in der Regel in a `CString`) ein und übergeben Sie sie an die [CDatabase::ExecuteSQL-Memberfunktion](../../mfc/reference/cdatabase-class.md#executesql) Ihres `CDatabase` Objekts. Wenn Sie ODBC-Funktionsaufrufe verwenden, um eine SQL-Anweisung zu senden, die normalerweise Datensätze zurückgibt, werden die Datensätze ignoriert.

## <a name="see-also"></a>Siehe auch

[SQL](../../data/odbc/sql.md)

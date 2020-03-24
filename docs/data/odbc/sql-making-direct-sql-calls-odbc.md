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
ms.openlocfilehash: 9240a227cdc4004d1e6e2b7ac26946ca233b71ec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212627"
---
# <a name="sql-making-direct-sql-calls-odbc"></a>SQL: Durchführen direkter SQL-Aufrufe (ODBC)

In diesem Thema wird Folgendes erläutert:

- Verwendung von direkten SQL-aufrufen.

- [So führen Sie direkte SQL-Aufrufe an die Datenquelle](#_core_making_direct_sql_function_calls)aus.

> [!NOTE]
>  Diese Informationen gelten für die MFC-ODBC-Klassen. Wenn Sie mit den MFC-DAO-Klassenarbeiten, finden Sie weitere Informationen im Thema "Vergleich von Microsoft Jet Datenbank-Engine SQL und ANSI SQL" in der DAO-Hilfe.

##  <a name="when-to-call-sql-directly"></a><a name="_core_when_to_call_sql_directly"></a>Wann sollte SQL direkt aufgerufen werden?

Zum Erstellen neuer Tabellen, löschen (Löschen) von Tabellen, Ändern vorhandener Tabellen, Erstellen von Indizes und Ausführen anderer SQL-Funktionen, die das [Datenquellen Schema (ODBC)](../../data/odbc/data-source-odbc.md) ändern, müssen Sie eine SQL-Anweisung direkt in der Datenquelle mithilfe der Daten Bank Definitions Sprache (DDL) ausgeben. Wenn Sie einen Assistenten zum Erstellen eines Recordsets für eine Tabelle (zur Entwurfszeit) verwenden, können Sie auswählen, welche Spalten der Tabelle im Recordset dargestellt werden. Dies ermöglicht es nicht, dass Spalten, die Sie oder ein anderer Benutzer der Datenquelle hinzufügen, später nach der Kompilierung des Programms der Tabelle hinzugefügt werden. DDL wird von den Datenbankklassen nicht direkt unterstützt. Sie können jedoch weiterhin Code schreiben, um eine neue Spalte zur Laufzeit dynamisch an das Recordset zu binden. Weitere Informationen zur Vorgehensweise bei dieser Bindung finden Sie unter [Recordset: Dynamisches Binden von Datenspalten (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

Sie können das DBMS selbst zum Ändern des Schemas oder eines anderen Tools verwenden, mit dem Sie DDL-Funktionen ausführen können. Sie können auch ODBC-Funktionsaufrufe zum Senden von SQL-Anweisungen verwenden, z. b. das Aufrufen einer vordefinierten Abfrage (gespeicherte Prozedur), die keine Datensätze zurückgibt.

##  <a name="making-direct-sql-function-calls"></a><a name="_core_making_direct_sql_function_calls"></a>Erstellen von direkten SQL-Funktionsaufrufen

Sie können einen SQL-Befehl mithilfe eines [CDatabase-Klassen](../../mfc/reference/cdatabase-class.md) Objekts direkt ausführen. Richten Sie die SQL-Anweisungs Zeichenfolge (in der Regel in einem `CString`) ein, und übergeben Sie Sie an die [CDatabase:: ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql) -Member-Funktion Ihres `CDatabase` Objekts. Wenn Sie ODBC-Funktionsaufrufe zum Senden einer SQL-Anweisung verwenden, die normalerweise Datensätze zurückgibt, werden die Datensätze ignoriert.

## <a name="see-also"></a>Weitere Informationen

[SQL](../../data/odbc/sql.md)

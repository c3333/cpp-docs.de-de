---
title: SQL
ms.date: 05/09/2019
helpviewer_keywords:
- database classes [C++], SQL statements
- SQL [C++]
- SQL [C++], ODBC
- ODBC [C++], SQL implementation
ms.assetid: e3923bc4-b317-4e0b-afd8-3cd403eb0faf
ms.openlocfilehash: cdceec9f4a6a39e9e1a50fc002d4220801e8d15a
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404267"
---
# <a name="sql"></a>SQL

SQL (Structured Query Language) ist eine Möglichkeit zum Arbeiten mit einer relationalen Datenbank, indem Sie über SQL Daten definieren, abfragen, ändern und verarbeiten können. Mit SQL-Syntax können Sie eine Anweisung erstellen, die Datensätze gemäß den Kriterien extrahiert, die Sie angeben.

> [!NOTE]
> Diese Informationen gelten für die MFC-ODBC-Klassen. Wenn Sie mit den MFC-DAO-Klassen arbeiten, lesen Sie das Thema „Comparison of Microsoft Jet Database Engine SQL and ANSI SQL“ in der DAO-Hilfe.

Eine SQL-Anweisung beginnt mit einem Schlüsselwortverb wie **CREATE** oder **SELECT**. SQL ist eine sehr leistungsfähige Programmiersprache. Eine einzelne Anweisung kann sich auf eine gesamte Tabelle auswirken.

Es gibt viele Versionen von SQL, wobei jede für ein bestimmtes DBMS entwickelt wurde. Für die MFC-Datenbankklassen wird ein Satz von SQL-Anweisungen unterstützt, die dem SQL-CAE-Spezifikationsentwurf (Common Applications Environment, 1991) von X/Open und SQL Access Group entspricht. Weitere Informationen zur Syntax dieser Anweisungen finden Sie in Anhang C in der [ODBC Programmer es Reference-](/sql/odbc/reference/odbc-programmer-s-reference) Dokumentation.

In diesem Thema wird Folgendes erläutert:

- [Die Beziehung zwischen ODBC und SQL](#_core_open_database_connectivity_.28.odbc.29)

- [Die üblichsten SQL-Schlüsselwörter, die in den Datenbankklassen verwendet werden](#_core_the_database_classes)

- Gibt an, [wie die Datenbankklassen SQL verwenden](#_core_how_the_database_classes_use_sql).

## <a name="open-database-connectivity-odbc"></a><a name="_core_open_database_connectivity_.28.odbc.29"></a>Open Database Connectivity (ODBC)

Die Datenbankklassen sind mit ODBC implementiert, in der SQL-Befehle in einem Call-Level-Interface statt durch Einbetten in den Code verwendet werden. In ODBC wird SQL verwendet, um über ODBC-Treiber mit einer [Datenquelle](../../data/odbc/data-source-odbc.md) zu kommunizieren. Diese Treiber interpretieren die SQL-Befehle und übersetzen diese ggf., damit sie mit einem bestimmten Datenbankformat, z. B. Microsoft Access, verwendet werden können. Weitere Informationen zur Verwendung von SQL durch ODBC finden Sie unter [ODBC](../../data/odbc/odbc-basics.md) und in der [ODBC Programmer es Reference-](/sql/odbc/reference/odbc-programmer-s-reference) Dokumentation.

## <a name="database-classes"></a><a name="_core_the_database_classes"></a> Datenbankklassen

> [!NOTE]
> Der MFC-ODBC-Consumer-Assistent ist in Visual Studio 2019 und höher nicht verfügbar. Sie können einen Consumer weiterhin manuell erstellen.

Die Datenbankklassen sind so konzipiert, dass Sie Daten in einer vorhandenen [Datenquelle](../../data/odbc/data-source-odbc.md) verarbeiten und aktualisieren können. Der [MFC-Anwendungs-Assistent](../../mfc/reference/database-support-mfc-application-wizard.md), der [MFC-ODBC-Consumer-Assistent](../../mfc/reference/adding-an-mfc-odbc-consumer.md) (auf den über **Klasse hinzufügen** zugegriffen wird) und die Datenbankklassen erstellen die meisten SQL-Anweisungen für Sie.

Für die Datenbankklassen wird ein Bestandteil von SQL verwendet, der als die Datenbearbeitungssprache (Data Manipulation Language, DML) bezeichnet wird. Mit diesen Befehlen können Sie mit der gesamten oder einem Teil der Datenquelle arbeiten, neue Datensätze hinzufügen, Datensätze bearbeiten und Datensätze löschen. In der folgenden Tabelle sind die am häufigsten verwendeten SQL-Schlüsselwörter samt den Möglichkeiten aufgelistet, wie diese von Datenbankklassen verwendet werden können.

### <a name="some-common-sql-keywords"></a>Einige übliche SQL-Schlüsselwörter

|SQL-Schlüsselwort|Verwendung in den Assistenten und Datenbankklassen|
|-----------------|---------------------------------------------|
|**SELECT**|Ermitteln, welche Tabellen und Spalten in der Datenquelle zu verwenden sind|
|**WHERE**|Anwenden eines Filters, mit dem die Auswahl eingeschränkt wird|
|**ORDER BY**|Anwenden einer Sortierreihenfolge auf das Recordset|
|**INSERT**|Hinzufügen neuer Datensätze zu einem Recordset|
|**DELETE**|Löschen von Datensätzen aus einem Recordset|
|**UPDATE**|Ändern der Felder eines Datensatzes|

Darüber hinaus erkennen die Datenbankklassen **CALL**-ODBC-Anweisungen, die Sie verwenden können, um eine vordefinierte Abfrage (oder eine gespeicherte Prozedur) für einige Datenquellen aufzurufen. Der ODBC-Datenbanktreiber interpretiert diese Anweisungen und ersetzt den Befehl entsprechend für jedes DBMS.

> [!NOTE]
> Nicht alle DBMS unterstützen **CALL**-Anweisungen.

Kann in einer Klasse eine vom Benutzer in `CRecordset::Open` bereitgestellte Anweisung nicht erkannt werden, wird sie als der Name einer Tabelle interpretiert.

Eine Erläuterung der Art und Weise, wie das Framework SQL-Anweisungen erstellt, finden [Sie unter Recordset: Wie Recordsets Select Records (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md) und [SQL: Anpassen der SQL-Anweisung ihres Recordsets (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

Für SQL-Datenbanken werden Datentypen verwendet, die denen ähneln, die in C und C++ verwendet werden. Eine Erläuterung dieser Ähnlichkeiten finden Sie unter [SQL: SQL-und C++-Datentypen (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

Weitere Informationen zu SQL sowie eine Liste der unterstützten SQL-Anweisungen, Datentypen, SQL Core-Grammatik und eine Liste der empfohlenen Veröffentlichungen zu SQL finden Sie in der [Microsoft SQL](/sql/) -Dokumentation.

## <a name="how-the-database-classes-use-sql"></a><a name="_core_how_the_database_classes_use_sql"></a> Verwenden von SQL durch die Datenbankklassen

Für die Recordsets, die Sie aus Datenbankklassen ableiten, wird über ODBC mit einer Datenquelle kommuniziert, und ODBC ruft durch Senden von SQL-Anweisungen Datensätze aus der Datenquelle ab. In diesem Thema wird die Beziehung zwischen den Datenbankklassen und SQL erläutert.

Für ein Recordset wird eine SQL-Anweisung erstellt, indem die Teile einer SQL­-Anweisung in einem `CString`-Objekt zusammengestellt werden. Die Zeichenfolge wird als eine **SELECT**-Anweisung erstellt, die eine Menge von Datensätzen zurückgibt.

Wird für das Recordset ODBC aufgerufen, um eine SQL-Anweisung an die Datenquelle zu senden, übergibt der ODBC-Treiber-Manager die Anweisung an den ODBC-Treiber, und der Treiber sendet sie an das zugrunde liegende DBMS. Das DBMS gibt ein Resultset aus Datensätzen zurück, und der ODBC-Treiber gibt die Datensätze an die Anwendung zurück. Über die Datenbankklassen kann Ihr Programm auf das Resultset in einer typsicheren C++-Klasse zugreifen, die aus `CRecordset` abgeleitet wurde.

In den folgenden Themen finden Sie weitere Informationen darüber, wie SQL für die Datenbankklassen verwendet wird:

- [SQL: Anpassen der SQL-Anweisung ihres Recordsets (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)

- [SQL: SQL-und C++-Datentypen (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

- [SQL: Durchführen direkter SQL-Aufrufe (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

## <a name="see-also"></a>Weitere Informationen

[Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)<br/>
[ODBC-Grundlagen](../../data/odbc/odbc-basics.md)

---
title: 'SQL: SQL- und C++-Datentypen (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: 424ae09f6462d4d34b5a847fc210f9329e76d788
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218337"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL: SQL- und C++-Datentypen (ODBC)

> [!NOTE]
> Diese Informationen gelten für die MFC-ODBC-Klassen. Wenn Sie mit den MFC-DAO-Klassenarbeiten, finden Sie weitere Informationen im Thema "Vergleich von Microsoft Jet Datenbank-Engine SQL und ANSI SQL" in der DAO-Hilfe.

In der folgenden Tabelle sind die ANSI-SQL-Datentypen den C++-Datentypen zugeordnet. Dies erweitert die C-Sprachinformationen, die in Anhang D der [ODBC-Programmier Referenz](/sql/odbc/reference/odbc-programmer-s-reference) Dokumentation angegeben sind. Die meisten Datentyp Zuordnung wird von den Assistenten für Sie verwaltet. Wenn Sie keinen Assistenten verwenden, können Sie die Zuordnungsinformationen verwenden, um den Code für den Feld Austausch manuell zu schreiben.

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>ANSI-SQL-Datentypen, die C++-Datentypen zugeordnet sind

|ANSI-SQL-Datentyp|C++-Datentyp|
|------------------------|---------------------|
|**CHAR**|`CString`|
|**DECIMAL**|`CString`1|
|**SMALLINT**|**`int`**|
|**Wirkliche**|**`float`**|
|**Zah**|**`long`**|
|**Hafen**|**`double`**|
|**Maß**|**`double`**|
|**Isch**|`CString`1|
|**VARCHAR**|`CString`|
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|
|**Trate**|**BOOL**|
|**TINYINT**|**Hobby**|
|**BIGINT**|`CString`1|
|**Ärer**|`CByteArray`|
|**VARBINARY**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|
|**DATE**|`CTime`, `CString`|
|**Zeit**|`CTime`, `CString`|
|**Zeitstempel**|`CTime`, `CString`|

1. Die ANSI- **Dezimal** Zahl und die **numerische** Zuordnung, `CString` da **SQL_C_CHAR** der standardodbc-Übertragungstyp ist.

2. Zeichendaten, die über 255 Zeichen hinausgehen, werden standardmäßig abgeschnitten, wenn Sie zugeordnet werden `CString` . Sie können die abkürzen Länge erweitern, indem Sie das *nMaxLength* -Argument von explizit festlegen `RFX_Text` .

3. Binäre Daten, die über 255 Zeichen hinausgehen, werden standardmäßig abgeschnitten, wenn Sie zugeordnet werden `CByteArray` . Sie können die abkürzen Länge erweitern, indem Sie das *nMaxLength* -Argument von explizit festlegen `RFX_Binary` .

Wenn Sie die ODBC-Cursor Bibliothek nicht verwenden, tritt möglicherweise ein Problem auf, wenn Sie versuchen, zwei oder mehr lange Felder variabler Länge mithilfe des Microsoft SQL Server ODBC-Treibers und der MFC-ODBC-Datenbankklassen zu aktualisieren. Die ODBC-Typen, **SQL_LONGVARCHAR** und **SQL_LONGVARBINARY**, werden Text-und Bild SQL Server Typen zugeordnet. Eine `CDBException` wird ausgelöst, wenn Sie zwei oder mehr lange Felder variabler Länge für denselben-Befehl aktualisieren `CRecordset::Update` . Aktualisieren Sie daher nicht mehrere lange Spalten gleichzeitig mit `CRecordset::Update` . Sie können mehrere lange Spalten gleichzeitig mit der ODBC-API aktualisieren `SQLPutData` . Sie können auch die ODBC-Cursor Bibliothek verwenden. Dies wird jedoch nicht empfohlen für Treiber, wie z. b. den SQL Server-Treiber, die Cursor unterstützen und die Cursor Bibliothek nicht benötigen.

Wenn Sie die ODBC-Cursor Bibliothek mit den MFC-ODBC-Datenbankklassen und dem Microsoft SQL Server ODBC-Treibers verwenden, kann eine **Assert** -Datei zusammen mit einer auftreten, `CDBException` Wenn ein-Befehl auf einen-Befehl `CRecordset::Update` folgt `CRecordset::Requery` . Stattdessen wird und anstelle von aufgerufen `CRecordset::Close` `CRecordset::Open` `CRecordset::Requery` . Eine andere Lösung besteht darin, die ODBC-Cursor Bibliothek nicht zu verwenden, da die SQL Server und der SQL Server ODBC-Treiber systemeigene Unterstützung für Cursor bereitstellen und die ODBC-Cursor Bibliothek nicht benötigt wird.

## <a name="see-also"></a>Weitere Informationen

[SQL](../../data/odbc/sql.md)<br/>
[SQL: Durchführen direkter SQL-Aufrufe (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

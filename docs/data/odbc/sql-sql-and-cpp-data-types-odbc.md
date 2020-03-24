---
title: 'SQL: SQL- und C++-Datentypen (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: 1c1ce908b5c8d345906d49adc79e322225ed49f5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212614"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL: SQL- und C++-Datentypen (ODBC)

> [!NOTE]
>  Diese Informationen gelten für die MFC-ODBC-Klassen. Wenn Sie mit den MFC-DAO-Klassenarbeiten, finden Sie weitere Informationen im Thema "Vergleich von Microsoft Jet Datenbank-Engine SQL und ANSI SQL" in der DAO-Hilfe.

In der folgenden Tabelle sind die ANSI-SQL C++ -Datentypen zu-Datentypen zugeordnet. Dies erweitert die C-Sprachinformationen, die in Anhang D der *ODBC SDK* *-Programmier Referenz* auf der MSDN Library-CD angegeben sind. Die meisten Datentyp Zuordnung wird von den Assistenten für Sie verwaltet. Wenn Sie keinen Assistenten verwenden, können Sie die Zuordnungsinformationen verwenden, um den Code für den Feld Austausch manuell zu schreiben.

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>ANSI-SQL-Datentypen C++ , die Datentypen zugeordnet sind

|ANSI-SQL-Datentyp|C++-Datentyp|
|------------------------|---------------------|
|**CHAR**|`CString`|
|**DECIMAL**|`CString` 1|
|**SMALLINT**|**int**|
|**REAL**|**float**|
|**INTEGER**|**long**|
|**FLOAT**|**double**|
|**DOUBLE**|**double**|
|**NUMERIC**|`CString` 1|
|**VARCHAR**|`CString`|
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|
|**BIT**|**BOOL**|
|**TINYINT**|**BYTE**|
|**BIGINT**|`CString` 1|
|**Ärer**|`CByteArray`|
|**VARBINARY**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|
|**DATE**|`CTime`, `CString`|
|**TIME**|`CTime`, `CString`|
|**TIMESTAMP**|`CTime`, `CString`|

1. Die ANSI- **Dezimal** Zahl und die **numerische** Zuordnung `CString`, da **SQL_C_CHAR** der standardodbc-Übertragungstyp ist.

2. Zeichendaten, die über 255 Zeichen hinausgehen, werden standardmäßig abgeschnitten, wenn Sie `CString`zugeordnet werden. Sie können die abkürzen Länge erweitern, indem Sie das *nMaxLength* -Argument von `RFX_Text`explizit festlegen.

3. Binäre Daten, die über 255 Zeichen hinausgehen, werden standardmäßig abgeschnitten, wenn Sie `CByteArray`zugeordnet werden. Sie können die abkürzen Länge erweitern, indem Sie das *nMaxLength* -Argument von `RFX_Binary`explizit festlegen.

Wenn Sie die ODBC-Cursor Bibliothek nicht verwenden, tritt möglicherweise ein Problem auf, wenn Sie versuchen, zwei oder mehr lange Felder variabler Länge mithilfe des Microsoft SQL Server ODBC-Treibers und der MFC-ODBC-Datenbankklassen zu aktualisieren. Die ODBC-Typen, **SQL_LONGVARCHAR** und **SQL_LONGVARBINARY**, werden Text-und Bild SQL Server Typen zugeordnet. Eine `CDBException` wird ausgelöst, wenn Sie mindestens zwei lange Felder mit variabler Länge für denselben `CRecordset::Update`-Auflistungen aktualisieren. Aktualisieren Sie daher nicht mehrere lange Spalten gleichzeitig mit `CRecordset::Update`. Sie können mehrere lange Spalten gleichzeitig mit der ODBC-API-`SQLPutData`aktualisieren. Sie können auch die ODBC-Cursor Bibliothek verwenden. Dies wird jedoch nicht empfohlen für Treiber, wie z. b. den SQL Server-Treiber, die Cursor unterstützen und die Cursor Bibliothek nicht benötigen.

Wenn Sie die ODBC-Cursor Bibliothek mit den MFC-ODBC-Datenbankklassen und dem Microsoft SQL Server ODBC-Treiber verwenden **, kann eine** Bestätigung zusammen mit einer `CDBException` auftreten, wenn ein-`CRecordset::Update` auf einen `CRecordset::Requery`aufgerufen wird. Verwenden Sie stattdessen `CRecordset::Close` und `CRecordset::Open` anstelle von `CRecordset::Requery`. Eine andere Lösung besteht darin, die ODBC-Cursor Bibliothek nicht zu verwenden, da die SQL Server und der SQL Server ODBC-Treiber systemeigene Unterstützung für Cursor bereitstellen und die ODBC-Cursor Bibliothek nicht benötigt wird.

## <a name="see-also"></a>Weitere Informationen

[SQL](../../data/odbc/sql.md)<br/>
[SQL: Durchführen direkter SQL-Aufrufe (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

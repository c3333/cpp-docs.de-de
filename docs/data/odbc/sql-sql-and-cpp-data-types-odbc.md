---
title: 'SQL: SQL- und C++-Datentypen (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], SQL vs. C++
- SQL data types [C++]
- SQL [C++], vs. C++ data types
ms.assetid: 066e0070-d4da-435c-9c4b-f7cab3352c86
ms.openlocfilehash: cffe44b832ac1eb28d368072b8f0e92ea9f57feb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374479"
---
# <a name="sql-sql-and-c-data-types-odbc"></a>SQL: SQL- und C++-Datentypen (ODBC)

> [!NOTE]
> Diese Informationen gelten für die MFC-ODBC-Klassen. Wenn Sie mit den MFC DAO-Klassen arbeiten, lesen Sie das Thema "Vergleich von Microsoft Jet Database Engine SQL und ANSI SQL" in der DAO-Hilfe.

In der folgenden Tabelle werden ANSI SQL-Datentypen C++-Datentypen zugeordnet. Dadurch werden die C-Sprachinformationen in Anhang D der *ODBC SDK-Programmierreferenz* auf der MSDN-Bibliotheks-CD erweitert. *ODBC SDK* Die Assistenten verwalten die meisten Datentypzuordnungen für Sie. Wenn Sie keinen Assistenten verwenden, können Sie die Zuordnungsinformationen verwenden, um den Feldaustauschcode manuell zu schreiben.

### <a name="ansi-sql-data-types-mapped-to-c-data-types"></a>ANSI SQL-Datentypen zugeordnet, die C++-Datentypen zugeordnet sind

|ANSI SQL-Datentyp|C++-Datentyp|
|------------------------|---------------------|
|**Char**|`CString`|
|**Decimal**|`CString`1|
|**Smallint**|**int**|
|**Real**|**float**|
|**Ganzzahl**|**Lange**|
|**schweben**|**double**|
|**Doppel**|**double**|
|**Numerischen**|`CString`1|
|**Varchar**|`CString`|
|**LONGVARCHAR**|`CLongBinary`, `CString` 2|
|**Bit**|**Bool**|
|**Tinyint**|**Byte**|
|**Bigint**|`CString`1|
|**Binäre**|`CByteArray`|
|**Varbinary**|`CByteArray`|
|**LONGVARBINARY**|`CLongBinary`, `CByteArray` 3|
|**Datum**|`CTime`, `CString`|
|**Zeit**|`CTime`, `CString`|
|**Timestamp**|`CTime`, `CString`|

1. ANSI **DECIMAL** und `CString` **NUMERIC** zuordnung zu, weil **SQL_C_CHAR** der Standard-ODBC-Übertragungstyp ist.

2. Zeichendaten über 255 Zeichen werden standardmäßig abgeschnitten, `CString`wenn sie zugeordnet werden. Sie können die Schnittlänge erweitern, indem Sie explizit `RFX_Text`das *argument nMaxLength* von festlegen.

3. Binäre Daten über 255 Zeichen hinaus werden standardmäßig `CByteArray`abgeschnitten, wenn sie zugeordnet werden. Sie können die Schnittlänge erweitern, indem Sie explizit `RFX_Binary`das *argument nMaxLength* von festlegen.

Wenn Sie die ODBC-Cursorbibliothek nicht verwenden, tritt möglicherweise ein Problem auf, wenn Sie versuchen, zwei oder mehr felder mit variabler Länge mithilfe des Microsoft SQL Server ODBC-Treibers und der MFC ODBC-Datenbankklassen zu aktualisieren. Die ODBC-Typen **SQL_LONGVARCHAR** und **SQL_LONGVARBINARY**sql Server-Typen zutexten und abbilden. A `CDBException` wird ausgelöst, wenn Sie zwei oder mehr lange `CRecordset::Update`Felder mit variabler Länge für denselben Aufruf von aktualisieren. Aktualisieren Sie daher nicht mehrere `CRecordset::Update`lange Spalten gleichzeitig mit . Sie können mehrere lange Spalten gleichzeitig `SQLPutData`mit der ODBC-API aktualisieren. Sie können auch die ODBC-Cursorbibliothek verwenden, dies wird jedoch nicht für Treiber wie den SQL Server-Treiber empfohlen, die Cursor unterstützen und die Cursorbibliothek nicht benötigen.

Wenn Sie die ODBC-Cursorbibliothek mit den MFC ODBC-Datenbankklassen und **ASSERT** dem Microsoft SQL `CDBException` Server ODBC-Treiber verwenden, kann ein ASSERT zusammen mit einem, wenn ein Aufruf nach `CRecordset::Update` einem Aufruf von `CRecordset::Requery`folgt, auftreten. Rufen Sie `CRecordset::Close` `CRecordset::Open` stattdessen `CRecordset::Requery`an und anstatt . Eine andere Lösung besteht darin, die ODBC-Cursorbibliothek nicht zu verwenden, da SQL Server und der SQL Server ODBC-Treiber systemeigene Unterstützung für Cursor nativ bereitstellen und die ODBC-Cursorbibliothek nicht benötigt wird.

## <a name="see-also"></a>Siehe auch

[SQL](../../data/odbc/sql.md)<br/>
[SQL: Durchführen direkter SQL-Aufrufe (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)

---
title: 'Datensatzfeldaustausch: Verwenden der RFX-Funktionen'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC [C++], data types
- data types [C++], ODBC record field exchange
- RFX (ODBC) [C++], function syntax and parameters
- DoFieldExchange method, and RFX functions
- ODBC [C++], RFX
- RFX (ODBC) [C++], data types
- function calls, RFX functions
ms.assetid: c594300b-5a29-4119-a68b-e7ca32def696
ms.openlocfilehash: f1afded360cfeff564f1f3d8bb9b294aa33cb733
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367131"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Datensatzfeldaustausch: Verwenden der RFX-Funktionen

In diesem Thema wird erläutert, wie sie die RFX-Funktionsaufrufe verwenden, aus denen der Hauptteil Der `DoFieldExchange` Außerkraftsetzung besteht.

> [!NOTE]
> Dieses Thema gilt für Klassen, die von [CRecordset](../../mfc/reference/crecordset-class.md) abgeleitet wurden und in denen das Abrufen von Massenzeilen nicht implementiert wurde. Wenn Sie Massenabrufen von Zeilen verwenden, wird der Massen-Datensatzfeldaustausch (Bulk-RFX) implementiert. Bulk-RFX ist RFX sehr ähnlich. Informationen zu den Unterschieden finden Sie unter [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Die globalen RFX-Funktionen tauschen Daten zwischen Spalten in der Datenquelle und Felddatenmembern in Ihrem Recordset aus. Sie schreiben die RFX-Funktionsaufrufe in die [DoFieldExchange-Memberfunktion](../../mfc/reference/crecordset-class.md#dofieldexchange) Ihres Recordsets. In diesem Thema werden die Funktionen kurz beschrieben und die Datentypen angezeigt, für die RFX-Funktionen verfügbar sind. [Technical Note 43](../../mfc/tn043-rfx-routines.md) beschreibt, wie Sie Ihre eigenen RFX-Funktionen für zusätzliche Datentypen schreiben.

## <a name="rfx-function-syntax"></a><a name="_core_rfx_function_syntax"></a>RFX-Funktionssyntax

Jede RFX-Funktion nimmt drei Parameter an (und einige nehmen einen optionalen vierten oder fünften Parameter):

- Ein Zeiger auf ein [CFieldExchange-Objekt.](../../mfc/reference/cfieldexchange-class.md) Sie übergeben einfach `pFX` den Zeiger `DoFieldExchange`an übergeben.

- Der Name der Spalte, wie sie in der Datenquelle angezeigt wird.

- Der Name des entsprechenden Felddatenmembers oder Parameterdatenmembers in der Recordset-Klasse.

- (Optional) In einigen Funktionen wird die maximale Länge der Zeichenfolge oder des Arrays übertragen. Dies entspricht standardmäßig 255 Byte, aber Sie können es ändern. Die maximale Größe basiert auf der `CString` maximalen Größe eines Objekts – **INT_MAX** (2.147.483.647) Bytes –, aber Sie werden wahrscheinlich vor dieser Größe auf Treiberlimits stoßen.

- (Optional) In `RFX_Text` der Funktion verwenden Sie manchmal einen fünften Parameter, um den Datentyp einer Spalte anzugeben.

Weitere Informationen finden Sie in den RFX-Funktionen unter [Makros und Globals](../../mfc/reference/mfc-macros-and-globals.md) in der *Klassenbibliotheksreferenz*. Ein Beispiel dafür, wann Sie die Parameter speziell verwenden können, finden Sie unter [Recordset: Abrufen von SUMs und anderen Aggregierten Ergebnissen (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).

## <a name="rfx-data-types"></a><a name="_core_rfx_data_types"></a>RFX-Datentypen

Die Klassenbibliothek stellt RFX-Funktionen bereit, um viele verschiedene Datentypen zwischen der Datenquelle und Ihren Recordsets zu übertragen. Die folgende Liste fasst die RFX-Funktionen nach Datentyp zusammen. In Fällen, in denen Sie eigene RFX-Funktionsaufrufe schreiben müssen, wählen Sie aus diesen Funktionen nach Datentyp aus.

|Funktion|Datentyp|
|--------------|---------------|
|`RFX_Bool`|**Bool**|
|`RFX_Byte`|**Byte**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**double**|
|`RFX_Single`|**float**|
|`RFX_Int`|**int**|
|`RFX_Long`|**Lange**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|

Weitere Informationen finden Sie in der RFX-Funktionsdokumentation unter [Makros und Globals](../../mfc/reference/mfc-macros-and-globals.md) in der *Klassenbibliotheksreferenz*. Informationen dazu, wie C++-Datentypen SQL-Datentypen zugeordnet werden, finden Sie in der Tabelle ANSI SQL Data Types Mapped to C++ Data Types in [SQL: SQL and C++ Data Types (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

## <a name="see-also"></a>Siehe auch

[Datensatzfeldaustausch (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Datensatzfeldaustausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Recordset: Parametrisieren eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Recordset: Dynamisches Binden von Datenspalten (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange-Klasse](../../mfc/reference/cfieldexchange-class.md)

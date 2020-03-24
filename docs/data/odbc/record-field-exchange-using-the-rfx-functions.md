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
ms.openlocfilehash: d281f801349527a065f4975b7cc3d88888f88367
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213030"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Datensatzfeldaustausch: Verwenden der RFX-Funktionen

In diesem Thema wird erläutert, wie Sie die RFX-Funktionsaufrufe verwenden, die den Textkörper der `DoFieldExchange` Überschreibung bilden.

> [!NOTE]
>  Dieses Thema bezieht sich auf Klassen, die von [CRecordset](../../mfc/reference/crecordset-class.md) abgeleitet sind, in dem das Abrufen von Massen Zeilen nicht implementiert wurde. Wenn Sie Massenabrufen von Zeilen verwenden, wird der Massen-Datensatzfeldaustausch (Bulk-RFX) implementiert. Bulk-RFX ist RFX sehr ähnlich. Informationen zu den Unterschieden finden Sie unter [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Die globalen RFX-Funktionen tauschen Daten zwischen Spalten in der Datenquelle und den Felddatenmembern in Ihrem Recordset aus. Sie schreiben die RFX-Funktionsaufrufe in der [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) -Member-Funktion Ihres Recordsets. In diesem Thema werden die-Funktionen kurz beschrieben und die Datentypen angezeigt, für die RFX-Funktionen verfügbar sind. [Technischer Hinweis 43](../../mfc/tn043-rfx-routines.md) in diesem Thema wird beschrieben, wie Sie eigene RFX-Funktionen für zusätzliche Datentypen schreiben.

##  <a name="rfx-function-syntax"></a><a name="_core_rfx_function_syntax"></a>RFX-Funktions Syntax

Jede RFX-Funktion nimmt drei Parameter an (und einige akzeptieren einen optionalen vierten oder fünften Parameter):

- Ein Zeiger auf ein [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) -Objekt. Sie übergeben einfach den `pFX` Zeiger, der an `DoFieldExchange`übergeben wird.

- Der Name der Spalte, wie er in der Datenquelle angezeigt wird.

- Der Name des entsprechenden Felddatenmembers oder Parameterdaten Elements in der Recordset-Klasse.

- Optionale In einigen der Funktionen die maximale Länge der Zeichenfolge oder des Arrays, das übertragen wird. Der Standardwert ist 255 bytes, Sie können ihn jedoch ändern. Die maximale Größe basiert auf der maximalen Größe eines `CString` Objekts – **INT_MAX** (2.147.483.647) Bytes – es treten jedoch wahrscheinlich Treiber Limits vor dieser Größe auf.

- Optionale In der `RFX_Text`-Funktion verwenden Sie manchmal einen fünften Parameter, um den Datentyp einer Spalte anzugeben.

Weitere Informationen finden Sie unter den RFX-Funktionen unter [Makros und Globals](../../mfc/reference/mfc-macros-and-globals.md) in der *Klassen Bibliotheks Referenz*. Ein Beispiel für die besondere Verwendung der Parameter finden Sie unter [Recordset: Abrufen von Summen und anderen Aggregat Ergebnissen (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).

##  <a name="rfx-data-types"></a><a name="_core_rfx_data_types"></a>RFX-Datentypen

Die-Klassenbibliothek stellt RFX-Funktionen bereit, mit denen viele verschiedene Datentypen zwischen der Datenquelle und den Recordsets übertragen werden. In der folgenden Liste werden die RFX-Funktionen nach Datentyp zusammengefasst. In Fällen, in denen Sie eigene RFX-Funktionsaufrufe schreiben müssen, wählen Sie aus diesen Funktionen nach Datentyp aus.

|Funktion|Datentyp|
|--------------|---------------|
|`RFX_Bool`|**BOOL**|
|`RFX_Byte`|**BYTE**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**double**|
|`RFX_Single`|**float**|
|`RFX_Int`|**int**|
|`RFX_Long`|**long**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|

Weitere Informationen finden Sie in der Dokumentation zur RFX-Funktion unter [Makros und Globals](../../mfc/reference/mfc-macros-and-globals.md) in der *Klassen Bibliotheks Referenz*. Informationen zur Zuordnung von C++ Datentypen zu SQL-Datentypen finden Sie in der Tabelle ANSI SQL-Datentypen C++ , die Datentypen in SQL zugeordnet sind [: SQL und C++ Datentypen (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

## <a name="see-also"></a>Weitere Informationen

[Datensatzfeldaustausch (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Datensatzfeldaustausch: Funktionsweise von RFX](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Recordset: Parametrisieren eines Recordsets (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Recordset: Dynamisches Binden von Datenspalten (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange-Klasse](../../mfc/reference/cfieldexchange-class.md)

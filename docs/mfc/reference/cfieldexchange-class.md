---
title: CFieldExchange-Klasse
ms.date: 11/04/2016
f1_keywords:
- CFieldExchange
- AFXDB/CFieldExchange
- AFXDB/CFieldExchange::IsFieldType
- AFXDB/CFieldExchange::SetFieldType
helpviewer_keywords:
- CFieldExchange [MFC], IsFieldType
- CFieldExchange [MFC], SetFieldType
ms.assetid: 24c5c0b3-06a6-430e-9b6f-005a2c65e29f
ms.openlocfilehash: d10bfc436297a5f861f17843007347dcef9e58ca
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212474"
---
# <a name="cfieldexchange-class"></a>CFieldExchange-Klasse

Unterstützt die von den Datenbankklassen verwendeten Routinen für den Datensatzfeldaustausch (Record Field Exchange, RFX) und den Massen-Datensatzfeldaustausch (Bulk-RFX).

## <a name="syntax"></a>Syntax

```
class CFieldExchange
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CFieldExchange:: isfieldtype](#isfieldtype)|Gibt einen Wert ungleich 0 (null) zurück, wenn der aktuelle Vorgang für den Typ des aktualisierten Felds geeignet ist.|
|[CFieldExchange:: SetFieldType](#setfieldtype)|Gibt den Typ des Recordset-Daten Members – Spalte oder Parameter – an, der durch alle folgenden Aufrufe von RFX-Funktionen dargestellt wird, bis zum nächsten Aufruf von `SetFieldType` .|

## <a name="remarks"></a>Bemerkungen

`CFieldExchange`weist keine Basisklasse auf.

Verwenden Sie diese Klasse, wenn Sie Datenaustausch Routinen für benutzerdefinierte Datentypen schreiben oder wenn Sie das Massen Abrufen von Zeilen implementieren. Andernfalls verwenden Sie diese Klasse nicht direkt. RFX und Bulk RFX tauschen Daten zwischen den Felddatenmembern des Recordset-Objekts und den entsprechenden Feldern des aktuellen Datensatzes in der Datenquelle aus.

> [!NOTE]
> Verwenden Sie stattdessen die Klasse [CDaoFieldExchange](../../mfc/reference/cdaofieldexchange-class.md) , wenn Sie mit den DAO-Klassen (Data Access Objects) anstelle der Open Database Connectivity-Klassen (ODBC) arbeiten. Weitere Informationen finden Sie im Artikel [Übersicht: Datenbankprogrammierung](../../data/data-access-programming-mfc-atl.md).

Ein- `CFieldExchange` Objekt stellt die Kontextinformationen bereit, die für den Daten Satz Feld Austausch oder den Massendaten Satz Feld Austausch benötigt werden. `CFieldExchange`-Objekte unterstützen eine Reihe von Vorgängen, einschließlich Bindungs Parametern und Felddatenmember und Festlegen verschiedener Flags für die Felder des aktuellen Datensatzes. RFX-und Bulk-RFX-Vorgänge werden für Recordset-Klassendatenmember von Typen ausgeführt, die durch den **`enum`** **FieldType** in definiert werden `CFieldExchange` . Mögliche **FieldType** -Werte sind:

- `CFieldExchange::outputColumn`für Felddatenmember.

- `CFieldExchange::inputParam`oder `CFieldExchange::param` für Eingabeparameter-Datenmember.

- `CFieldExchange::outputParam`für Ausgabeparameter-Datenmember.

- `CFieldExchange::inoutParam`für Eingabe-/ausgabeparameterdatenmember.

Die meisten Element Funktionen und Datenmember der-Klasse werden zum Schreiben Ihrer eigenen benutzerdefinierten RFX-Routinen bereitgestellt. Sie werden `SetFieldType` häufig verwenden. Weitere Informationen finden Sie in den Artikeln [Daten Satz Feld Austausch (RFX)](../../data/odbc/record-field-exchange-rfx.md) und [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Weitere Informationen zum Abrufen von Massen Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Ausführliche Informationen zu den globalen Funktionen RFX und Bulk RFX finden Sie unter [Daten Satz Feld Austausch-Funktionen](../../mfc/reference/record-field-exchange-functions.md) im Abschnitt MFC-Makros und Globals in dieser Referenz.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CFieldExchange`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** AFXDB. h

## <a name="cfieldexchangeisfieldtype"></a><a name="isfieldtype"></a>CFieldExchange:: isfieldtype

Wenn Sie Ihre eigene RFX-Funktion schreiben, `IsFieldType` müssen Sie am Anfang der Funktion aufrufen, um zu bestimmen, ob der aktuelle Vorgang für einen bestimmten Feld-oder Parameter-Daten Elementtyp (,,, `CFieldExchange::outputColumn` `CFieldExchange::inputParam` `CFieldExchange::param` `CFieldExchange::outputParam` oder `CFieldExchange::inoutParam` ) ausgeführt werden kann.

```
BOOL IsFieldType(UINT* pnField);
```

### <a name="parameters"></a>Parameter

*pnfield*<br/>
Die sequenzielle Nummer des Felds oder Parameterdaten Elements wird in diesem Parameter zurückgegeben. Diese Zahl entspricht der Reihenfolge des Datenelements im [CRecordset::D ofieldexchange](../../mfc/reference/crecordset-class.md#dofieldexchange) -oder [CRecordset::D obulkfieldexchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) -Funktion.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0, wenn der aktuelle Vorgang für den aktuellen Feld-oder Parametertyp ausgeführt werden kann.

### <a name="remarks"></a>Bemerkungen

Befolgen Sie das Modell der vorhandenen RFX-Funktionen.

## <a name="cfieldexchangesetfieldtype"></a><a name="setfieldtype"></a>CFieldExchange:: SetFieldType

Sie benötigen einen-Rückruf `SetFieldType` in der [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) -Klasse oder der [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) -außer Kraft setzung ihrer Recordsetklasse.

```cpp
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Parameter

*nfieldtype*<br/>
Ein Wert von `enum FieldType` , der in deklariert `CFieldExchange` wurde. folgende Werte sind möglich:

- `CFieldExchange::outputColumn`

- `CFieldExchange::inputParam`

- `CFieldExchange::param`

- `CFieldExchange::outputParam`

- `CFieldExchange::inoutParam`

### <a name="remarks"></a>Bemerkungen

Bei Felddatenmembern müssen Sie mit dem- `SetFieldType` Parameter aufrufen `CFieldExchange::outputColumn` , gefolgt von Aufrufen der RFX-Funktion oder der Bulk-RFX-Funktion. Wenn Sie das Massen Abrufen von Zeilen nicht implementiert haben, fügt der ClassWizard diesen Befehl `SetFieldType` im Feld Map-Abschnitt von ein `DoFieldExchange` .

Wenn Sie die Recordset-Klasse parametrisieren, müssen Sie `SetFieldType` erneut aufrufen, außerhalb von Feld Zuordnungs Abschnitten, gefolgt von RFX-Aufrufen für alle Parameter Datenmember. Jeder Parameterdatenmember muss über einen eigenen- `SetFieldType` Rückruf verfügen. In der folgenden Tabelle werden die verschiedenen Werte unterschieden, die Sie an übergeben können `SetFieldType` , um die Parameter Datenmember ihrer Klasse darzustellen:

|SetFieldType-Parameterwert|Typ des Parameterdaten Elements|
|----------------------------------|-----------------------------------|
|`CFieldExchange::inputParam`|Eingabeparameter Ein Wert, der an die Abfrage oder die gespeicherte Prozedur des Recordsets übermittelt wird.|
|`CFieldExchange::param` | identisch mit `CFieldExchange::inputParam` .|
|`CFieldExchange::outputParam`|Ausgabeparameter Ein Rückgabewert der gespeicherten Prozedur des Recordsets.|
|`CFieldExchange::inoutParam`|Eingabe-/Ausgabeparameter. Ein Wert, der an die gespeicherte Prozedur des Recordsets übermittelt und von dieser zurückgegeben wird.|

Im Allgemeinen muss jeder Gruppe von RFX-Funktionsaufrufen, die den Felddatenmembern oder Parameter Datenmembern zugeordnet ist, ein Aufruf von vorangestellt sein `SetFieldType` . Der *nfieldtype* -Parameter jedes `SetFieldType` Aufrufs identifiziert den Typ der Datenmember, die von den RFX-Funktionsaufrufen dargestellt werden, die dem `SetFieldType` Aufruf folgen.

Weitere Informationen zum Verarbeiten von Ausgabe-und Eingabe-/Ausgabeparametern finden Sie in der `CRecordset` Member-Funktion [flushresultset](../../mfc/reference/crecordset-class.md#flushresultset). Weitere Informationen zu den RFX-und Bulk-RFX-Funktionen finden Sie im Thema [Daten Satz Feld Austausch-Funktionen](../../mfc/reference/record-field-exchange-functions.md). Weitere Informationen zum Abrufen von Massen Zeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in einer Sammel Operation (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Beispiel

Dieses Beispiel zeigt mehrere Aufrufe von RFX-Funktionen mit begleitenden Aufrufen von `SetFieldType` . Beachten Sie, dass `SetFieldType` durch den `pFX` Zeiger auf ein-Objekt aufgerufen wird `CFieldExchange` .

[!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]

## <a name="see-also"></a>Weitere Informationen

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)

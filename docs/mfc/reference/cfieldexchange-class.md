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
ms.openlocfilehash: de9db2713a25b232bbd7f936958d1c10e96c511a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753170"
---
# <a name="cfieldexchange-class"></a>CFieldExchange-Klasse

Unterstützt die von den Datenbankklassen verwendeten Routinen für den Datensatzfeldaustausch (Record Field Exchange, RFX) und den Massen-Datensatzfeldaustausch (Bulk-RFX).

## <a name="syntax"></a>Syntax

```
class CFieldExchange
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CFieldExchange::IsFieldType](#isfieldtype)|Gibt einen Wert ungleich Null zurück, wenn der aktuelle Vorgang für den Typ des zu aktualisierenden Felds geeignet ist.|
|[CFieldExchange::SetFieldType](#setfieldtype)|Gibt den Typ des Recordset-Datenmembers (Spalte oder Parameter ) an, der `SetFieldType`durch alle folgenden Aufrufe von RFX-Funktionen bis zum nächsten Aufruf von dargestellt wird.|

## <a name="remarks"></a>Bemerkungen

`CFieldExchange`hat keine Basisklasse.

Verwenden Sie diese Klasse, wenn Sie Datenaustauschroutinen für benutzerdefinierte Datentypen schreiben oder wenn Sie das Abrufen von Massenzeilen implementieren. Andernfalls verwenden Sie diese Klasse nicht direkt. RFX und Bulk RFX tauschen Daten zwischen den Felddatenmembern Ihres Recordset-Objekts und den entsprechenden Feldern des aktuellen Datensatzes in der Datenquelle aus.

> [!NOTE]
> Wenn Sie mit den DAO-Klassen (Data Access Objects) und nicht mit den ODBC-Klassen (Open Database Connectivity) arbeiten, verwenden Sie stattdessen die Klasse [CDaoFieldExchange.](../../mfc/reference/cdaofieldexchange-class.md) Weitere Informationen finden Sie im Artikel [Übersicht:Datenbankprogrammierung](../../data/data-access-programming-mfc-atl.md).

Ein `CFieldExchange` Objekt stellt die Kontextinformationen bereit, die für den Datensatzfeldaustausch oder den Massendatensatzfeldaustausch erforderlich sind. `CFieldExchange`Objekte unterstützen eine Reihe von Vorgängen, einschließlich Bindungsparametern und Felddatenmembern und Festlegen verschiedener Flags für die Felder des aktuellen Datensatzes. RFX- und Bulk-RFX-Vorgänge werden für Datensatzklassen-Datenmember von Typen `CFieldExchange`ausgeführt, die durch die **Enumere** **FieldType** in definiert sind. Mögliche **FieldType-Werte** sind:

- `CFieldExchange::outputColumn`für Felddatenmember.

- `CFieldExchange::inputParam`oder `CFieldExchange::param` für Eingabeparameterdatenmember.

- `CFieldExchange::outputParam`für Ausgabeparameterdatenmember.

- `CFieldExchange::inoutParam`für Eingabe-/Ausgabeparameterdatenmember.

Die meisten Memberfunktionen und Datenmember der Klasse werden zum Schreiben Ihrer eigenen benutzerdefinierten RFX-Routinen bereitgestellt. Sie werden `SetFieldType` häufig verwenden. Weitere Informationen finden Sie in den Artikeln [Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md) und [Recordset (ODBC)](../../data/odbc/recordset-odbc.md). Informationen zum Abrufen von Massenzeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md). Weitere Informationen zu den globalen Funktionen RFX und Bulk RFX finden Sie unter [Datensatzfeldaustauschfunktionen](../../mfc/reference/record-field-exchange-functions.md) im Abschnitt MFC-Makros und Globale in dieser Referenz.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CFieldExchange`

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** afxdb.h

## <a name="cfieldexchangeisfieldtype"></a><a name="isfieldtype"></a>CFieldExchange::IsFieldType

Wenn Sie eine eigene RFX-Funktion schreiben, rufen Sie am `IsFieldType` Anfang Ihrer Funktion an, um zu bestimmen, ob der aktuelle Vorgang für einen bestimmten Feld- oder Parameterdatenmembertyp (a `CFieldExchange::outputColumn`, `CFieldExchange::inputParam`, `CFieldExchange::param`, `CFieldExchange::outputParam`, oder `CFieldExchange::inoutParam`) ausgeführt werden kann.

```
BOOL IsFieldType(UINT* pnField);
```

### <a name="parameters"></a>Parameter

*pnField*<br/>
Die fortlaufende Nummer des Feld- oder Parameterdatenelements wird in diesem Parameter zurückgegeben. Diese Zahl entspricht der Reihenfolge des Datenmembers in der Funktion [CRecordset::DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) oder [CRecordset::DoBulkFieldExchange.](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der aktuelle Vorgang für das aktuelle Feld oder den Parametertyp ausgeführt werden kann.

### <a name="remarks"></a>Bemerkungen

Folgen Sie dem Modell der vorhandenen RFX-Funktionen.

## <a name="cfieldexchangesetfieldtype"></a><a name="setfieldtype"></a>CFieldExchange::SetFieldType

Sie benötigen einen `SetFieldType` Aufruf in der [DoFieldExchange-](../../mfc/reference/crecordset-class.md#dofieldexchange) oder [DoBulkFieldExchange-Überschreibung](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) Ihrer Recordset-Klasse.

```cpp
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Parameter

*nFieldType*<br/>
Ein Wert `enum FieldType`der , `CFieldExchange`der in deklariert ist, der einer der folgenden sein kann:

- `CFieldExchange::outputColumn`

- `CFieldExchange::inputParam`

- `CFieldExchange::param`

- `CFieldExchange::outputParam`

- `CFieldExchange::inoutParam`

### <a name="remarks"></a>Bemerkungen

Für Felddatenmember müssen `SetFieldType` Sie mit `CFieldExchange::outputColumn`dem Parameter " gefolgt von Aufrufen der RFX- oder Bulk-RFX-Funktionen aufrufen. Wenn Sie das Abrufen von Massenzeilen nicht `SetFieldType` implementiert haben, platziert ClassWizard `DoFieldExchange`diesen Aufruf für Sie im Feldkartenabschnitt von .

Wenn Sie Ihre Recordset-Klasse parametrisieren, müssen Sie außerhalb eines Feldzuordnungsabschnitts erneut aufrufen, `SetFieldType` gefolgt von RFX-Aufrufen für alle Parameterdatenmember. Jeder Typ des Parameterdatenmembers `SetFieldType` muss einen eigenen Aufruf haben. In der folgenden Tabelle werden die `SetFieldType` verschiedenen Werte unterschieden, an die Sie übergeben können, um die Parameterdatenmember Ihrer Klasse darzustellen:

|SetFieldType-Parameterwert|Typ des Parameterdatenmembers|
|----------------------------------|-----------------------------------|
|`CFieldExchange::inputParam`|Eingabeparameter Ein Wert, der an die Abfrage oder gespeicherte Prozedur des Recordsets übergeben wird.|
|`CFieldExchange::param` | wie `CFieldExchange::inputParam`.|
|`CFieldExchange::outputParam`|Ausgabeparameter Ein Rückgabewert der gespeicherten Prozedur des Recordsets.|
|`CFieldExchange::inoutParam`|Ein-/Ausgabeparameter. Ein Wert, der an die gespeicherte Prozedur des Recordsets übergeben und von ihr zurückgegeben wird.|

Im Allgemeinen muss jeder Gruppe von RFX-Funktionsaufrufen, die Felddatenmembern `SetFieldType`oder Parameterdatenelementen zugeordnet sind, ein Aufruf von vorangestellt werden. Der *nFieldType-Parameter* jedes `SetFieldType` Aufrufs identifiziert den Typ der Datenmember, `SetFieldType` die durch die RFX-Funktionsaufrufe dargestellt werden, die dem Aufruf folgen.

Weitere Informationen zur Handhabung von Ausgabe- und `CRecordset` Eingabe-/Ausgabeparametern finden Sie in der Memberfunktion [FlushResultSet](../../mfc/reference/crecordset-class.md#flushresultset). Weitere Informationen zu den RFX- und Bulk-RFX-Funktionen finden Sie im Thema [Datensatzfeldaustauschfunktionen](../../mfc/reference/record-field-exchange-functions.md). Weitere Informationen zum Abrufen von Massenzeilen finden Sie im Artikel [Recordset: Abrufen von Datensätzen in Bulk (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

### <a name="example"></a>Beispiel

Dieses Beispiel zeigt mehrere Aufrufe von RFX-Funktionen mit begleitenden Aufrufen von `SetFieldType`. Hinweis, `SetFieldType` der über `pFX` den Zeiger `CFieldExchange` auf ein Objekt aufgerufen wird.

[!code-cpp[NVC_MFCDatabase#33](../../mfc/codesnippet/cpp/cfieldexchange-class_1.cpp)]

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)

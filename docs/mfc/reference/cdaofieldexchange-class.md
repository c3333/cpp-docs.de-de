---
title: CDaoFieldExchange-Klasse
ms.date: 09/17/2019
f1_keywords:
- CDaoFieldExchange
- AFXDAO/CDaoFieldExchange
- AFXDAO/CDaoFieldExchange::IsValidOperation
- AFXDAO/CDaoFieldExchange::SetFieldType
- AFXDAO/CDaoFieldExchange::m_nOperation
- AFXDAO/CDaoFieldExchange::m_prs
helpviewer_keywords:
- CDaoFieldExchange [MFC], IsValidOperation
- CDaoFieldExchange [MFC], SetFieldType
- CDaoFieldExchange [MFC], m_nOperation
- CDaoFieldExchange [MFC], m_prs
ms.assetid: 350a663e-92ff-44ab-ad53-d94efa2e5823
ms.openlocfilehash: 86f12f78338d1c60e3dd13614ccedc2868f28d81
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754719"
---
# <a name="cdaofieldexchange-class"></a>CDaoFieldExchange-Klasse

Unterstützt die Routinen für den DAO-Datensatzfeldaustausch (DAO record field exchange, DFX), die von den DAO-Datenbankklassen verwendet werden.

DAO wird über Office 2013 unterstützt. DAO 3.6 ist die endgültige Version und gilt als veraltet.

## <a name="syntax"></a>Syntax

```
class CDaoFieldExchange
```

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoFieldExchange::IsValidOperation](#isvalidoperation)|Gibt einen Wert ungleich Null zurück, wenn der aktuelle Vorgang für den Typ des zu aktualisierenden Felds geeignet ist.|
|[CDaoFieldExchange::SetFieldType](#setfieldtype)|Gibt den Typ des Recordset-Datenmembers (Spalte oder Parameter) an, der durch `SetFieldType`alle nachfolgenden Aufrufe von DFX-Funktionen bis zum nächsten Aufruf von dargestellt wird.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoFieldExchange::m_nOperation](#m_noperation)|Der DFX-Vorgang, der vom aktuellen Aufruf `DoFieldExchange` der Memberfunktion des Recordsets ausgeführt wird.|
|[CDaoFieldExchange::m_prs](#m_prs)|Ein Zeiger auf das Recordset, auf dem DFX-Vorgänge ausgeführt werden.|

## <a name="remarks"></a>Bemerkungen

`CDaoFieldExchange`hat keine Basisklasse.

Verwenden Sie diese Klasse, wenn Sie Datenaustauschroutinen für benutzerdefinierte Datentypen schreiben. Andernfalls verwenden Sie diese Klasse nicht direkt. DFX tauscht Daten zwischen den Felddatenmembern Ihres [CDaoRecordset-Objekts](../../mfc/reference/cdaorecordset-class.md) und den entsprechenden Feldern des aktuellen Datensatzes in der Datenquelle aus. DFX verwaltet den Austausch in beide Richtungen, von der Datenquelle bis zur Datenquelle. Weitere Informationen zum Schreiben benutzerdefinierter DFX-Routinen finden Sie in [Technical Note 53.](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md)

> [!NOTE]
> Die DAO-Datenbankklassen unterscheiden sich von den MFC-Datenbankklassen, die auf Open Database Connectivity (ODBC) basieren. Alle DAO-Datenbankklassennamen haben das Präfix "CDao". Sie können weiterhin mit den DAO-Klassen auf ODBC-Datenquellen zugreifen. Im Allgemeinen sind die Aufbasis von DAO basierenden MFC-Klassen leistungsfähiger als die MFC-Klassen, die auf ODBC basieren. Die DAO-basierten Klassen können über ihre eigene Datenbank-Engine auf Daten zugreifen, auch über ODBC-Treiber. Sie unterstützen auch DDL-Vorgänge (Data Definition Language), z. B. das Hinzufügen von Tabellen über die Klassen, anstatt DAO selbst aufrufen zu müssen.

> [!NOTE]
> DAO-Datensatzfeldaustausch (DFX) ist dem Datensatzfeldaustausch (RFX) in den ODBC-basierten MFC-Datenbankklassen ( `CDatabase`, `CRecordset`) sehr ähnlich. Wenn Sie RFX verstehen, finden Sie es einfach, DFX zu verwenden.

Ein `CDaoFieldExchange` Objekt stellt die Kontextinformationen bereit, die für den DAO-Datensatzfeldaustausch erforderlich sind. `CDaoFieldExchange`Objekte unterstützen eine Reihe von Vorgängen, einschließlich Bindungsparametern und Felddatenmembern und Festlegen verschiedener Flags für die Felder des aktuellen Datensatzes. DFX-Vorgänge werden für Datensatzklassen-Datenmember von Typen ausgeführt, `CDaoFieldExchange`die durch die **Enumerat** **FieldType** in definiert sind. Mögliche **FieldType-Werte** sind:

- `CDaoFieldExchange::outputColumn`für Felddatenmember.

- `CDaoFieldExchange::param`für Parameterdatenmember.

Die [IsValidOperation-Memberfunktion](#isvalidoperation) wird zum Schreiben eigener benutzerdefinierter DFX-Routinen bereitgestellt. Sie verwenden [SetFieldType](#setfieldtype) häufig in Ihren [CDaoRecordset::DoFieldExchange-Funktionen.](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) Weitere Informationen zu den globalen DFX-Funktionen finden Sie unter [Datensatzfeldaustauschfunktionen](../../mfc/reference/record-field-exchange-functions.md). Informationen zum Schreiben benutzerdefinierter DFX-Routinen für Ihre eigenen Datentypen finden Sie unter [Technische Anmerkung 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CDaoFieldExchange`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="cdaofieldexchangeisvalidoperation"></a><a name="isvalidoperation"></a>CDaoFieldExchange::IsValidOperation

Wenn Sie eine eigene DFX-Funktion schreiben, rufen Sie am Anfang Ihrer Funktion an, `IsValidOperation` um zu `CDaoFieldExchange::outputColumn` bestimmen, ob der aktuelle Vorgang für einen bestimmten Felddatenmembertyp (a oder a `CDaoFieldExchange::param`) ausgeführt werden kann.

```
BOOL IsValidOperation();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der aktuelle Vorgang für den Typ des zu aktualisierenden Felds geeignet ist.

### <a name="remarks"></a>Bemerkungen

Einige der vom DFX-Mechanismus ausgeführten Vorgänge gelten nur für einen der möglichen Feldtypen. Folgen Sie dem Modell der vorhandenen DFX-Funktionen.

Weitere Informationen zum Schreiben benutzerdefinierter DFX-Routinen finden Sie unter [Technische Anmerkung 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

## <a name="cdaofieldexchangem_noperation"></a><a name="m_noperation"></a>CDaoFieldExchange::m_nOperation

Identifiziert den Vorgang, der für das [CDaoRecordset-Objekt](../../mfc/reference/cdaorecordset-class.md) ausgeführt werden soll, das dem Feldaustauschobjekt zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Das `CDaoFieldExchange` Objekt stellt den Kontext für eine Reihe verschiedener DFX-Operationen im Recordset zur Verfügung.

> [!NOTE]
> Der unter den folgenden Aktionen MarkForAddNew und SetFieldNull beschriebene PSEUDONULL-Wert ist ein Wert, der zum Markieren der Felder Null verwendet wird. Der DAO-Datensatzfeldaustauschmechanismus (DFX) verwendet diesen Wert, um zu bestimmen, welche Felder explizit als Null markiert wurden. PSEUDONULL ist für [COleDateTime-](../../atl-mfc-shared/reference/coledatetime-class.md) und [COleCurrency-Felder](../../mfc/reference/colecurrency-class.md) nicht erforderlich.

Mögliche Werte `m_nOperation` sind:

|Vorgang|BESCHREIBUNG|
|---------------|-----------------|
|`AddToParameterList`|Erstellt die **PARAMETERS-Klausel** der SQL-Anweisung.|
|`AddToSelectList`|Erstellt die **SELECT-Klausel** der SQL-Anweisung.|
|`BindField`|Bindet ein Feld in der Datenbank an einen Speicherort in der Anwendung.|
|`BindParam`|Legt Parameterwerte für die Abfrage des Recordsets fest.|
|`Fixup`|Legt den Nullstatus für ein Feld fest.|
|`AllocCache`|Ordnet den Cache zu, der verwendet wird, um nach "schmutzigen" Feldern im Recordset zu suchen.|
|`StoreField`|Speichert den aktuellen Datensatz im Cache.|
|`LoadField`|Stellt die zwischengespeicherten Datenmembervariablen im Recordset wieder her.|
|`FreeCache`|Gibt den Cache frei, der verwendet wird, um nach "schmutzigen" Feldern im Recordset zu suchen.|
|`SetFieldNull`|Legt den Status eines Felds auf Null und den Wert auf PSEUDONULL fest.|
|`MarkForAddNew`|Markiert Felder "schmutzig", wenn nicht PSEUDONULL.|
|`MarkForEdit`|Markiert Felder als "schmutzig", wenn sie nicht mit dem Cache übereinstimmen.|
|`SetDirtyField`|Legt Feldwerte fest, die als "schmutzig" markiert sind.|
|`DumpField`|Dumpt den Inhalt eines Felds (nur Debug).|
|`MaxDFXOperation`|Wird für die Eingabeprüfung verwendet.|

## <a name="cdaofieldexchangem_prs"></a><a name="m_prs"></a>CDaoFieldExchange::m_prs

Enthält einen Zeiger auf das [CDaoRecordset-Objekt,](../../mfc/reference/cdaorecordset-class.md) das dem `CDaoFieldExchange` Objekt zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

## <a name="cdaofieldexchangesetfieldtype"></a><a name="setfieldtype"></a>CDaoFieldExchange::SetFieldType

Rufen `SetFieldType` Sie `CDaoRecordset` die `DoFieldExchange` Außerkraftsetzung Ihrer Klasse auf.

```cpp
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Parameter

*nFieldType*<br/>
Ein Wert der **enum FieldType**, deklariert in `CDaoFieldExchange`, die einer der folgenden sein kann:

- `CDaoFieldExchange::outputColumn`

- `CDaoFieldExchange::param`

### <a name="remarks"></a>Bemerkungen

Normalerweise schreibt ClassWizard diesen Aufruf für Sie. Wenn Sie Eine eigene Funktion schreiben und `DoFieldExchange` den Assistenten zum Schreiben Ihrer Funktion verwenden, fügen Sie Aufrufe zu Ihrer eigenen Funktion außerhalb der Feldzuordnung hinzu. Wenn Sie den Assistenten nicht verwenden, wird keine Feldzuordnung vorhanden sein. Der Aufruf geht Aufrufen von DFX-Funktionen voraus, eine für jeden Felddatenmember `CDaoFieldExchange::outputColumn`Ihrer Klasse, und identifiziert den Feldtyp als .

Wenn Sie Ihre Recordset-Klasse parametrisieren, sollten Sie DFX-Aufrufe für alle Parameterdatenmember (außerhalb der Feldzuordnung) hinzufügen und diesen Aufrufen einen Aufruf von `SetFieldType`voranstellen. Übergeben Sie `CDaoFieldExchange::param`den Wert . (Sie können stattdessen eine [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) verwenden und deren Parameterwerte festlegen.)

Im Allgemeinen muss jeder Gruppe von DFX-Funktionsaufrufen, die Felddatenmembern `SetFieldType`oder Parameterdatenelementen zugeordnet sind, ein Aufruf von vorangestellt werden. Der *nFieldType-Parameter* jedes `SetFieldType` Aufrufs identifiziert den Typ der Datenmember, `SetFieldType` die durch die DFX-Funktionsaufrufe dargestellt werden, die dem Aufruf folgen.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset-Klasse](../../mfc/reference/cdaorecordset-class.md)

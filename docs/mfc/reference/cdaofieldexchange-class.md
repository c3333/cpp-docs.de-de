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
ms.openlocfilehash: cfffebd16c3c1d62dc4084b962c22911e4b46ae5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78872472"
---
# <a name="cdaofieldexchange-class"></a>CDaoFieldExchange-Klasse

Unterstützt die Routinen für den DAO-Datensatzfeldaustausch (DAO record field exchange, DFX), die von den DAO-Datenbankklassen verwendet werden.

DAO wird über Office 2013 unterstützt. DAO 3,6 ist die endgültige Version, die als veraltet eingestuft wird.

## <a name="syntax"></a>Syntax

```
class CDaoFieldExchange
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoFieldExchange:: isvalidoperation](#isvalidoperation)|Gibt einen Wert ungleich 0 (null) zurück, wenn der aktuelle Vorgang für den Typ des aktualisierten Felds geeignet ist.|
|[CDaoFieldExchange:: SetFieldType](#setfieldtype)|Gibt den Typ des Recordset-Daten Members – Spalte oder Parameter – an, der durch alle nachfolgenden Aufrufe von DFX-Funktionen dargestellt wird, bis zum nächsten Aufruf von `SetFieldType`.|

### <a name="public-data-members"></a>Öffentliche Datenelemente

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoFieldExchange:: m_nOperation](#m_noperation)|Der DFX-Vorgang, der vom aktuellen aufrufsvorgang der `DoFieldExchange` Member-Funktion des Recordsets ausgeführt wird.|
|[CDaoFieldExchange:: m_prs](#m_prs)|Ein Zeiger auf das Recordset, für das DFX-Vorgänge ausgeführt werden.|

## <a name="remarks"></a>Bemerkungen

`CDaoFieldExchange` verfügt nicht über eine Basisklasse.

Verwenden Sie diese Klasse, wenn Sie Datenaustausch Routinen für benutzerdefinierte Datentypen schreiben. Andernfalls verwenden Sie diese Klasse nicht direkt. DFX tauscht Daten zwischen den Felddatenmembern des [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekts und den entsprechenden Feldern des aktuellen Datensatzes in der Datenquelle aus. DFX verwaltet den Austausch in beide Richtungen, von der Datenquelle und der Datenquelle. Weitere Informationen zum Schreiben von benutzerdefinierten DFX-Routinen finden [Sie im technischen Hinweis 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md) .

> [!NOTE]
>  Die DAO-Datenbankklassen unterscheiden sich von der MFC-Datenbankklassen in Bezug auf Open Database Connectivity (ODBC). Alle DAO-Datenbank-Klassennamen haben das Präfix "CDao". Sie können weiterhin mit den DAO-Klassen auf ODBC-Datenquellen zugreifen. Im Allgemeinen sind die MFC-Klassen basierend auf DAO leistungsfähiger als die MFC-Klassen basierend auf ODBC. Die DAO-basierten Klassen können über Ihre eigene Datenbank-Engine auf Daten zugreifen, auch über ODBC-Treiber. Außerdem unterstützen Sie DDL-Vorgänge (Data Definition Language), z. b. das Hinzufügen von Tabellen über die Klassen, anstatt DAO selbst aufrufen zu müssen.

> [!NOTE]
>  Der DAO-Daten Satz Feld Austausch (DFX) ähnelt dem Daten Satz Feld Austausch (RFX) in den ODBC-basierten MFC-Datenbankklassen (`CDatabase``CRecordset`). Wenn Sie RFX verstanden haben, ist es einfach, DFX zu verwenden.

Ein `CDaoFieldExchange`-Objekt stellt die Kontextinformationen bereit, die für den DAO-Daten Satz Feld Austausch benötigt werden. `CDaoFieldExchange` Objekte unterstützen eine Reihe von Vorgängen, einschließlich Bindungs Parametern und Felddatenmember und Festlegen verschiedener Flags für die Felder des aktuellen Datensatzes. DFX-Vorgänge werden für Recordset-Klassendatenmember von Typen ausgeführt, die durch den **Enumeration** - **FieldType** in `CDaoFieldExchange`definiert sind. Mögliche **FieldType** -Werte sind:

- `CDaoFieldExchange::outputColumn` für Felddatenmember.

- `CDaoFieldExchange::param` für Parameterdatenmember.

Die Member-Funktion von [isvalidoperation](#isvalidoperation) wird zum Schreiben eigener benutzerdefinierter DFX-Routinen bereitgestellt. [SetFieldType](#setfieldtype) wird häufig in Ihrem [CDaoRecordset::D ofieldexchange](../../mfc/reference/cdaorecordset-class.md#dofieldexchange) -Funktionen verwendet. Ausführliche Informationen zu den globalen DFX-Funktionen finden Sie unter Daten [Satz Feld Austausch-Funktionen](../../mfc/reference/record-field-exchange-functions.md). Weitere Informationen zum Schreiben von benutzerdefinierten DFX-Routinen für Ihre eigenen Datentypen finden Sie im [technischen Hinweis 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`CDaoFieldExchange`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

##  <a name="isvalidoperation"></a>CDaoFieldExchange:: isvalidoperation

Wenn Sie Ihre eigene DFX-Funktion schreiben, müssen Sie `IsValidOperation` am Anfang der Funktion aufzurufen, um zu bestimmen, ob der aktuelle Vorgang für einen bestimmten Felddatenmember (ein `CDaoFieldExchange::outputColumn` oder ein `CDaoFieldExchange::param`) ausgeführt werden kann.

```
BOOL IsValidOperation();
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn der aktuelle Vorgang für den Typ des zu aktualisierenden Felds geeignet ist.

### <a name="remarks"></a>Bemerkungen

Einige der Vorgänge, die vom DFX-Mechanismus ausgeführt werden, gelten nur für einen der möglichen Feldtypen. Befolgen Sie das Modell der vorhandenen DFX-Funktionen.

Weitere Informationen zum Schreiben von benutzerdefinierten DFX-Routinen finden [Sie im technischen Hinweis 53](../../mfc/tn053-custom-dfx-routines-for-dao-database-classes.md).

##  <a name="m_noperation"></a>CDaoFieldExchange:: m_nOperation

Gibt den Vorgang an, der für das [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekt ausgeführt werden soll, das dem Feld Austausch Objekt zugeordnet ist.

### <a name="remarks"></a>Bemerkungen

Das `CDaoFieldExchange`-Objekt stellt den Kontext für eine Reihe von unterschiedlichen DFX-Vorgängen für das Recordset bereit.

> [!NOTE]
>  Der in den Vorgängen markforaddnew und SetFieldNull beschriebene Wert von pseudonull ist ein Wert, der zum Markieren von Feldern NULL verwendet wird. Der DAO-Daten Satz Feld Austausch-Mechanismus (DFX) verwendet diesen Wert, um zu bestimmen, welche Felder explizit als NULL markiert wurden. Für die Felder " [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) " und " [COleCurrency](../../mfc/reference/colecurrency-class.md) " ist keine pseudonull erforderlich.

Mögliche Werte `m_nOperation` sind:

|Vorgang|BESCHREIBUNG|
|---------------|-----------------|
|`AddToParameterList`|Erstellt die **Parameters** -Klausel der SQL-Anweisung.|
|`AddToSelectList`|Erstellt die **Select** -Klausel der SQL-Anweisung.|
|`BindField`|Bindet ein Feld in der Datenbank an einen Speicherort in der Anwendung.|
|`BindParam`|Legt Parameterwerte für die Abfrage des Recordsets fest.|
|`Fixup`|Legt den NULL-Status für ein Feld fest.|
|`AllocCache`|Ordnet den Cache zu, der verwendet wird, um nach "Dirty"-Feldern im Recordset zu suchen.|
|`StoreField`|Speichert den aktuellen Datensatz im Cache.|
|`LoadField`|Stellt die zwischengespeicherten Datenmember-Variablen im Recordset wieder her.|
|`FreeCache`|Gibt den Cache frei, der zum Überprüfen auf "Dirty"-Felder im Recordset verwendet wird.|
|`SetFieldNull`|Legt den Status eines Felds auf NULL und den Wert auf pseudonull fest.|
|`MarkForAddNew`|Markiert Felder "Dirty", wenn Sie nicht pseudonull sind.|
|`MarkForEdit`|Markiert Felder "Dirty", wenn Sie nicht mit dem Cache identisch sind.|
|`SetDirtyField`|Legt Feldwerte fest, die als "geändert" gekennzeichnet sind.|
|`DumpField`|Sichert den Inhalt eines Felds (nur Debuggen).|
|`MaxDFXOperation`|Wird für die Eingabe Überprüfung verwendet.|

##  <a name="m_prs"></a>CDaoFieldExchange:: m_prs

Enthält einen Zeiger auf das [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekt, das mit dem `CDaoFieldExchange`-Objekt verknüpft ist.

### <a name="remarks"></a>Bemerkungen

##  <a name="setfieldtype"></a>CDaoFieldExchange:: SetFieldType

Ruft `SetFieldType` in der `DoFieldExchange` Überschreibung ihrer `CDaoRecordset` Klasse auf.

```
void SetFieldType(UINT nFieldType);
```

### <a name="parameters"></a>Parameter

*nfieldtype*<br/>
Ein Wert des in `CDaoFieldExchange`deklarierten **enumerationsfieldtype**, der einen der folgenden Werte aufweisen kann:

- `CDaoFieldExchange::outputColumn`

- `CDaoFieldExchange::param`

### <a name="remarks"></a>Bemerkungen

Normalerweise schreibt der Klassen-Assistent diesen-Befehl für Sie. Wenn Sie Ihre eigene Funktion schreiben und den Assistenten zum Schreiben Ihrer `DoFieldExchange` Funktion verwenden, fügen Sie Ihrer eigenen Funktion außerhalb der Feld Zuordnung Aufrufe hinzu. Wenn Sie den Assistenten nicht verwenden, wird keine Feld Zuordnung angezeigt. Der Aufruf geht vor den Aufrufen von DFX-Funktionen vor, eine für jedes Feld Datenelement ihrer Klasse und identifiziert den Feldtyp als `CDaoFieldExchange::outputColumn`.

Wenn Sie die Recordset-Klasse parametrisieren, sollten Sie DFX-Aufrufe für alle Parameterdatenmember (außerhalb der Feld Zuordnung) hinzufügen und diesen Aufrufen einen Aufruf von `SetFieldType`voranstellen. Übergeben Sie den Wert `CDaoFieldExchange::param`. (Sie können stattdessen einen [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) verwenden und dessen Parameterwerte festlegen.)

Im Allgemeinen muss jeder Gruppe von DFX-Funktionsaufrufen, die den Felddatenmembern oder Parameter Datenmembern zugeordnet ist, ein Aufruf von `SetFieldType`vorangestellt sein. Der *nfieldtype* -Parameter jedes `SetFieldType` Aufrufs identifiziert den Typ der Datenmember, die durch die DFX-Funktionsaufrufe dargestellt werden, die dem `SetFieldType` Aufruf folgen.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDaoRecordset-Klasse](../../mfc/reference/cdaorecordset-class.md)

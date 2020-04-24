---
title: CDaoTableDef-Klasse
ms.date: 11/04/2016
f1_keywords:
- CDaoTableDef
- AFXDAO/CDaoTableDef
- AFXDAO/CDaoTableDef::CDaoTableDef
- AFXDAO/CDaoTableDef::Append
- AFXDAO/CDaoTableDef::CanUpdate
- AFXDAO/CDaoTableDef::Close
- AFXDAO/CDaoTableDef::Create
- AFXDAO/CDaoTableDef::CreateField
- AFXDAO/CDaoTableDef::CreateIndex
- AFXDAO/CDaoTableDef::DeleteField
- AFXDAO/CDaoTableDef::DeleteIndex
- AFXDAO/CDaoTableDef::GetAttributes
- AFXDAO/CDaoTableDef::GetConnect
- AFXDAO/CDaoTableDef::GetDateCreated
- AFXDAO/CDaoTableDef::GetDateLastUpdated
- AFXDAO/CDaoTableDef::GetFieldCount
- AFXDAO/CDaoTableDef::GetFieldInfo
- AFXDAO/CDaoTableDef::GetIndexCount
- AFXDAO/CDaoTableDef::GetIndexInfo
- AFXDAO/CDaoTableDef::GetName
- AFXDAO/CDaoTableDef::GetRecordCount
- AFXDAO/CDaoTableDef::GetSourceTableName
- AFXDAO/CDaoTableDef::GetValidationRule
- AFXDAO/CDaoTableDef::GetValidationText
- AFXDAO/CDaoTableDef::IsOpen
- AFXDAO/CDaoTableDef::Open
- AFXDAO/CDaoTableDef::RefreshLink
- AFXDAO/CDaoTableDef::SetAttributes
- AFXDAO/CDaoTableDef::SetConnect
- AFXDAO/CDaoTableDef::SetName
- AFXDAO/CDaoTableDef::SetSourceTableName
- AFXDAO/CDaoTableDef::SetValidationRule
- AFXDAO/CDaoTableDef::SetValidationText
- AFXDAO/CDaoTableDef::m_pDAOTableDef
- AFXDAO/CDaoTableDef::m_pDatabase
helpviewer_keywords:
- CDaoTableDef [MFC], CDaoTableDef
- CDaoTableDef [MFC], Append
- CDaoTableDef [MFC], CanUpdate
- CDaoTableDef [MFC], Close
- CDaoTableDef [MFC], Create
- CDaoTableDef [MFC], CreateField
- CDaoTableDef [MFC], CreateIndex
- CDaoTableDef [MFC], DeleteField
- CDaoTableDef [MFC], DeleteIndex
- CDaoTableDef [MFC], GetAttributes
- CDaoTableDef [MFC], GetConnect
- CDaoTableDef [MFC], GetDateCreated
- CDaoTableDef [MFC], GetDateLastUpdated
- CDaoTableDef [MFC], GetFieldCount
- CDaoTableDef [MFC], GetFieldInfo
- CDaoTableDef [MFC], GetIndexCount
- CDaoTableDef [MFC], GetIndexInfo
- CDaoTableDef [MFC], GetName
- CDaoTableDef [MFC], GetRecordCount
- CDaoTableDef [MFC], GetSourceTableName
- CDaoTableDef [MFC], GetValidationRule
- CDaoTableDef [MFC], GetValidationText
- CDaoTableDef [MFC], IsOpen
- CDaoTableDef [MFC], Open
- CDaoTableDef [MFC], RefreshLink
- CDaoTableDef [MFC], SetAttributes
- CDaoTableDef [MFC], SetConnect
- CDaoTableDef [MFC], SetName
- CDaoTableDef [MFC], SetSourceTableName
- CDaoTableDef [MFC], SetValidationRule
- CDaoTableDef [MFC], SetValidationText
- CDaoTableDef [MFC], m_pDAOTableDef
- CDaoTableDef [MFC], m_pDatabase
ms.assetid: 7c5d2254-8475-43c4-8a6c-2d32ead194c9
ms.openlocfilehash: adc31ccbf2be34aa1df1fa56111d1990701a6329
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754690"
---
# <a name="cdaotabledef-class"></a>CDaoTableDef-Klasse

Stellt die gespeicherte Definition einer Basistabelle oder einer angefügten Tabelle dar.

## <a name="syntax"></a>Syntax

```
class CDaoTableDef : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|Erstellt ein `CDaoTableDef`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoTableDef::Anfügen](#append)|Fügt der Datenbank eine neue Tabelle hinzu.|
|[CDaoTableDef::CanUpdate](#canupdate)|Gibt einen Wert ungleich Null zurück, wenn die Tabelle aktualisiert werden kann (Sie können die Definition von Feldern oder die Tabelleneigenschaften ändern).|
|[CDaoTableDef::Schließen](#close)|Schließt eine geöffnete tabledef.|
|[CDaoTableDef::Erstellen](#create)|Erstellt eine Tabelle, die der Datenbank mithilfe von [Append](#append)hinzugefügt werden kann.|
|[CDaoTableDef::CreateField](#createfield)|Wird aufgerufen, um ein Feld für eine Tabelle zu erstellen.|
|[CDaoTableDef::CreateIndex](#createindex)|Wird aufgerufen, um einen Index für eine Tabelle zu erstellen.|
|[CDaoTableDef::DeleteField](#deletefield)|Wird aufgerufen, um ein Feld aus einer Tabelle zu löschen.|
|[CDaoTableDef::DeleteIndex](#deleteindex)|Wird aufgerufen, um einen Index aus einer Tabelle zu löschen.|
|[CDaoTableDef::GetAttributes](#getattributes)|Gibt einen Wert zurück, der `CDaoTableDef` ein oder mehrere Merkmale eines Objekts angibt.|
|[CDaoTableDef::GetConnect](#getconnect)|Gibt einen Wert zurück, der Informationen über die Quelle einer Tabelle bereitstellt.|
|[CDaoTableDef::GetDateErstellt](#getdatecreated)|Gibt das Datum und die `CDaoTableDef` Uhrzeit zurück, zu der die Basistabelle, die einem Objekt zugrunde liegt, erstellt wurde.|
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|Gibt das Datum und die Uhrzeit der letzten Änderung zurück, die am Entwurf der Basistabelle vorgenommen wurde.|
|[CDaoTableDef::GetFieldCount](#getfieldcount)|Gibt einen Wert zurück, der die Anzahl der Felder in der Tabelle darstellt.|
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|Gibt bestimmte Arten von Informationen zu den Feldern in der Tabelle zurück.|
|[CDaoTableDef::GetIndexCount](#getindexcount)|Gibt die Anzahl der Indizes für die Tabelle zurück.|
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|Gibt bestimmte Arten von Informationen zu den Indizes für die Tabelle zurück.|
|[CDaoTableDef::GetName](#getname)|Gibt den benutzerdefinierten Namen der Tabelle zurück.|
|[CDaoTableDef::GetRecordCount](#getrecordcount)|Gibt die Anzahl der Datensätze in der Tabelle zurück.|
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|Gibt einen Wert zurück, der den Namen der angefügten Tabelle in der Quelldatenbank angibt.|
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|Gibt einen Wert zurück, der die Daten in einem Feld überprüft, wenn sie geändert oder einer Tabelle hinzugefügt werden.|
|[CDaoTableDef::GetValidationText](#getvalidationtext)|Gibt einen Wert zurück, der den Text der Nachricht angibt, die ihre Anwendung anzeigt, wenn der Wert eines Field-Objekts nicht die angegebene Validierungsregel erfüllt.|
|[CDaoTableDef::IsOpen](#isopen)|Gibt einen Wert ungleich Null zurück, wenn die Tabelle geöffnet ist.|
|[CDaoTableDef::Öffnen](#open)|Öffnet eine vorhandene tabledef, die in der TableDef-Auflistung der Datenbank gespeichert ist.|
|[CDaoTableDef::RefreshLink](#refreshlink)|Aktualisiert die Verbindungsinformationen für eine angehängte Tabelle.|
|[CDaoTableDef::SetAttributes](#setattributes)|Legt einen Wert fest, der `CDaoTableDef` ein oder mehrere Merkmale eines Objekts angibt.|
|[CDaoTableDef::SetConnect](#setconnect)|Legt einen Wert fest, der Informationen über die Quelle einer Tabelle bereitstellt.|
|[CDaoTableDef::SetName](#setname)|Legt den Namen der Tabelle fest.|
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|Legt einen Wert fest, der den Namen einer angefügten Tabelle in der Quelldatenbank angibt.|
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|Legt einen Wert fest, der die Daten in einem Feld überprüft, wenn sie geändert oder einer Tabelle hinzugefügt werden.|
|[CDaoTableDef::SetValidationText](#setvalidationtext)|Legt einen Wert fest, der den Text der Nachricht angibt, die ihre Anwendung anzeigt, wenn der Wert eines Field-Objekts nicht die angegebene Validierungsregel erfüllt.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CDaoTableDef::m_pDAOTableDef](#m_pdaotabledef)|Ein Zeiger auf die DAO-Schnittstelle, die dem tabledef-Objekt zugrunde liegt.|
|[CDaoTableDef::m_pDatabase](#m_pdatabase)|Quelldatenbank für diese Tabelle.|

## <a name="remarks"></a>Bemerkungen

Jedes DAO-Datenbankobjekt verwaltet eine Auflistung namens TableDefs, die alle gespeicherten DAO tabledef-Objekte enthält.

Sie bearbeiten eine Tabellendefinition mithilfe eines Objekts. `CDaoTableDef` Beispielsweise können Sie folgende Aktionen ausführen:

- Untersuchen Sie die Feld- und Indexstruktur einer lokalen, angefügten oder externen Tabelle in einer Datenbank.

- Rufen `SetConnect` Sie `SetSourceTableName` die und Memberfunktionen für `RefreshLink` angefügte Tabellen auf, und verwenden Sie die Memberfunktion, um Verbindungen zu angehängten Tabellen zu aktualisieren.

- Rufen `CanUpdate` Sie die Memberfunktion auf, um zu bestimmen, ob Sie Felddefinitionen in der Tabelle bearbeiten können.

- Abrufen oder Festlegen von `GetValidationRule` `SetValidationRule`Validierungsbedingungen `GetValidationText` `SetValidationText` mithilfe der und und der Memberfunktionen.

- Verwenden `Open` Sie die Memberfunktion, um ein Tabellen-, `CDaoRecordset` Dynaset- oder Snapshot-Objekt zu erstellen.

    > [!NOTE]
    >  Die DAO-Datenbankklassen unterscheiden sich von den MFC-Datenbankklassen, die auf Open Database Connectivity (ODBC) basieren. Alle DAO-Datenbankklassennamen haben das Präfix "CDao". Sie können weiterhin mit den DAO-Klassen auf ODBC-Datenquellen zugreifen. Die DAO-Klassen bieten im Allgemeinen überlegene Funktionen, da sie für das Microsoft Jet-Datenbankmodul spezifisch sind.

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>So verwenden Sie tabledef-Objekte, um entweder mit einer vorhandenen Tabelle zu arbeiten oder eine neue Tabelle zu erstellen

1. Erstellen Sie in allen `CDaoTableDef` Fällen zuerst ein Objekt und geben Sie einen Zeiger auf ein [CDaoDatabase-Objekt](../../mfc/reference/cdaodatabase-class.md) an, zu dem die Tabelle gehört.

1. Gehen Sie dann wie folgt vor, je nachdem, was Sie möchten:

   - Um eine vorhandene gespeicherte Tabelle zu verwenden, rufen Sie die [Memberfunktion "Öffnen"](#open) des tabledef-Objekts auf und geben den Namen der gespeicherten Tabelle an.

   - Um eine neue Tabelle zu erstellen, rufen Sie die Memberfunktion [Create](#create) des tabledef-Objekts auf und geben sie den Namen der Tabelle an. Rufen Sie [CreateField](#createfield) und [CreateIndex](#createindex) auf, um der Tabelle Felder und Indizes hinzuzufügen.

   - Rufen Sie [Append](#append) auf, um die Tabelle zu speichern, indem Sie sie an die TableDefs-Auflistung der Datenbank anhängen. `Create`setzt die tabledef in einen offenen `Create` Zustand, `Open`sodass Sie nach dem Aufruf nicht anrufen.

        > [!TIP]
        >  Die einfachste Möglichkeit, gespeicherte Tabellen zu erstellen, besteht darin, sie zu erstellen und mit Microsoft Access in Ihrer Datenbank zu speichern. Dann können Sie sie öffnen und in Ihrem MFC-Code verwenden.

Um das von Ihnen geöffnete oder erstellte `CDaoRecordset` tabledef-Objekt zu verwenden, erstellen `dbOpenTable` und öffnen Sie ein Objekt, wobei Sie den Namen der tabledef mit einem Wert im Parameter *nOpenType* angeben.

Um ein tabledef-Objekt `CDaoRecordset` zum Erstellen eines Objekts zu verwenden, erstellen oder öffnen Sie in der Regel eine tabledef wie oben beschrieben, erstellen oder öffnen sie dann ein Recordset-Objekt, indem Sie beim Aufrufen von [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open)einen Zeiger an das tabledef-Objekt übergeben. Die tabledef, die Sie übergeben, muss sich in einem offenen Zustand befinden. Weitere Informationen finden Sie unter Klasse [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Wenn Sie mit einem tabledef-Objekt fertig sind, rufen Sie die Memberfunktion [Schließen](../../mfc/reference/cdaorecordset-class.md#close) auf. dann das tabledef-Objekt zerstören.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdao.h

## <a name="cdaotabledefappend"></a><a name="append"></a>CDaoTableDef::Anfügen

Rufen Sie diese Memberfunktion auf, nachdem Sie [Create](#create) aufrufen, um ein neues tabledef-Objekt zu erstellen, um die tabledef in der Datenbank zu speichern.

```
virtual void Append();
```

### <a name="remarks"></a>Bemerkungen

Die Funktion fügt das Objekt an die TableDefs-Auflistung der Datenbank an. Sie können die tabledef als temporäres Objekt verwenden, während Sie es definieren, indem Sie `Append`es nicht anhängen, aber wenn Sie es speichern und verwenden möchten, müssen Sie aufrufen.

> [!NOTE]
> Wenn Sie versuchen, eine unbenannte tabledef anzufügen (die eine Null- oder leere Zeichenfolge enthält), löst MFC eine Ausnahme aus.

Weitere Informationen finden Sie im Thema "Append-Methode" in der DAO-Hilfe.

## <a name="cdaotabledefcanupdate"></a><a name="canupdate"></a>CDaoTableDef::CanUpdate

Rufen Sie diese Memberfunktion auf, um `CDaoTableDef` zu bestimmen, ob die Definition der Tabelle, die einem Objekt zugrunde liegt, geändert werden kann.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn die Tabellenstruktur (Schema) geändert werden kann (Felder und Indizes hinzufügen oder löschen), andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Standardmäßig kann eine neu erstellte Tabelle, die einem `CDaoTableDef` Objekt `CDaoTableDef` zugrunde liegt, aktualisiert werden, und eine angehängte Tabelle, die einem Objekt zugrunde liegt, kann nicht aktualisiert werden. Ein `CDaoTableDef` Objekt kann aktualisierbar sein, auch wenn das resultierende Recordset nicht aufrüstbar ist.

Weitere Informationen finden Sie im Thema "Updatable-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaotabledefcdaotabledef"></a><a name="cdaotabledef"></a>CDaoTableDef::CDaoTableDef

Erstellt ein `CDaoTableDef`-Objekt.

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parameter

*pDatabase*<br/>
Ein Zeiger auf ein [CDaoDatabase-Objekt.](../../mfc/reference/cdaodatabase-class.md)

### <a name="remarks"></a>Bemerkungen

Nach dem Erstellen des Objekts müssen Sie die Memberfunktion [Erstellen](#create) oder [Öffnen](#open) aufrufen. Wenn Sie mit dem Objekt fertig [Close](#close) sind, müssen `CDaoTableDef` Sie die Memberfunktion Schließen aufrufen und das Objekt zerstören.

## <a name="cdaotabledefclose"></a><a name="close"></a>CDaoTableDef::Schließen

Rufen Sie diese Memberfunktion auf, um das tabledef-Objekt zu schließen und freizugeben.

```
virtual void Close();
```

### <a name="remarks"></a>Bemerkungen

Normalerweise löschen `Close`Sie nach dem Aufruf das tabledef-Objekt, wenn es mit **neuen**zugeordnet wurde.

Sie können [Open](#open) nach `Close`dem Aufruf erneut aufrufen. Auf diese Weise können Sie das tabledef-Objekt wiederverwenden.

Weitere Informationen finden Sie im Thema "Close-Methode" in der DAO-Hilfe.

## <a name="cdaotabledefcreate"></a><a name="create"></a>CDaoTableDef::Erstellen

Rufen Sie diese Memberfunktion auf, um eine neue gespeicherte Tabelle zu erstellen.

```
virtual void Create(
    LPCTSTR lpszName,
    long lAttributes = 0,
    LPCTSTR lpszSrcTable = NULL,
    LPCTSTR lpszConnect = NULL);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen der Tabelle enthält.

*lAttributes*<br/>
Ein Wert, der den Merkmalen der Tabelle entspricht, die durch das tabledef-Objekt dargestellt wird. Sie können den bitwise-OR verwenden, um eine der folgenden Konstanten zu kombinieren:

|Konstante|BESCHREIBUNG|
|--------------|-----------------|
|`dbAttachExclusive`|Für Datenbanken, die das Microsoft Jet-Datenbankmodul verwenden, gibt die Tabelle an, dass es sich um eine angefügte Tabelle handelt, die exklusiv verwendet wird.|
|`dbAttachSavePWD`|Gibt für Datenbanken an, die das Microsoft Jet-Datenbankmodul verwenden, dass die Benutzer-ID und das Kennwort für die angefügte Tabelle mit den Verbindungsinformationen gespeichert werden.|
|`dbSystemObject`|Gibt an, dass es sich bei der Tabelle um eine Systemtabelle handelt, die vom Microsoft Jet-Datenbankmodul bereitgestellt wird.|
|`dbHiddenObject`|Gibt an, dass es sich bei der Tabelle um eine ausgeblendete Tabelle handelt, die vom Microsoft Jet-Datenbankmodul bereitgestellt wird.|

*lpszSrcTabelle*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Quelltabellennamen enthält. Standardmäßig wird dieser Wert als NULL initialisiert.

*lpszConnect*<br/>
Ein Zeiger auf eine Zeichenfolge, die die Standardverbindungszeichenfolge enthält. Standardmäßig wird dieser Wert als NULL initialisiert.

### <a name="remarks"></a>Bemerkungen

Nachdem Sie die tabledef benannt haben, können Sie [Append](#append) aufrufen, um die tabledef in der TableDefs-Auflistung der Datenbank zu speichern. Nach `Append`dem Aufruf befindet sich tabledef in einem offenen Zustand, und Sie können es verwenden, um ein [CDaoRecordset-Objekt](../../mfc/reference/cdaorecordset-class.md) zu erstellen.

Weitere Informationen finden Sie im Thema "CreateTableDef-Methode" in der DAO-Hilfe.

## <a name="cdaotabledefcreatefield"></a><a name="createfield"></a>CDaoTableDef::CreateField

Rufen Sie diese Memberfunktion auf, um der Tabelle ein Feld hinzuzufügen.

```cpp
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Ein Zeiger auf einen Zeichenfolgenausdruck, der den Namen dieses Felds angibt.

*nType*<br/>
Ein Wert, der den Datentyp des Felds angibt. Die Einstellung kann einer der folgenden Werte sein:

|type|Größe (Byte)|BESCHREIBUNG|
|----------|--------------------|-----------------|
|`dbBoolean`|1 Byte|BOOL|
|`dbByte`|BYTE|
|`dbInteger`|2|INT|
|`dbLong`|4|long|
|`dbCurrency`|8|Währung ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|float|
|`dbDouble`|8|double|
|`dbDate`|8|Datum/Uhrzeit ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Text ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Lange Binärdatei (OLE-Objekt), [CLongBinary](../../mfc/reference/clongbinary-class.md) oder [CByteArray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|Memo ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|

*lGröße*<br/>
Ein Wert, der die maximale Größe eines Felds, das Text enthält, in Bytes oder die feste Größe eines Felds angibt, das Text oder numerische Werte enthält. Der *Parameter lSize* wird für alle Textfelder außer Text ignoriert.

*lAttributes*<br/>
Ein Wert, der den Merkmalen des Feldes entspricht und mit einem bitweisen-ODER kombiniert werden kann.

|Konstante|BESCHREIBUNG|
|--------------|-----------------|
|`dbFixedField`|Die Feldgröße ist festgelegt (Standard für numerische Felder).|
|`dbVariableField`|Die Feldgröße ist variabel (nur Textfelder).|
|`dbAutoIncrField`|Der Feldwert für neue Datensätze wird automatisch in eine eindeutige lange ganze Zahl erhöht, die nicht geändert werden kann. Nur für Microsoft Jet-Datenbanktabellen unterstützt.|
|`dbUpdatableField`|Der Feldwert kann geändert werden.|
|`dbDescending`|Das Feld wird in absteigender Reihenfolge (Z - A oder 100 - 0) sortiert (gilt nur für ein Field-Objekt in einer Fields-Auflistung eines Indexobjekts). Wenn Sie diese Konstante weglassen, wird das Feld in aufsteigender (A - Z oder 0 - 100) Reihenfolge (Standard) sortiert.|

*Fieldinfo*<br/>
Ein Verweis auf eine [CDaoFieldInfo-Struktur.](../../mfc/reference/cdaofieldinfo-structure.md)

### <a name="remarks"></a>Bemerkungen

Ein `DAOField` (OLE)-Objekt wird erstellt und an `DAOTableDef` die Fields-Auflistung des (OLE)-Objekts angehängt. Neben der Verwendung zum Untersuchen von `CDaoFieldInfo` Objekteigenschaften können Sie auch einen Eingabeparameter zum Erstellen neuer Felder in einer tabledef erstellen. Die erste `CreateField` Version von ist einfacher zu verwenden, aber wenn Sie eine `CreateField`feinere `CDaoFieldInfo` Steuerung wünschen, können Sie die zweite Version von verwenden, die einen Parameter annimmt.

Wenn Sie die `CreateField` Version dieses `CDaoFieldInfo` Parameters verwenden, müssen Sie jedes der `CDaoFieldInfo` folgenden Elemente der Struktur sorgfältig festlegen:

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

Die verbleibenden `CDaoFieldInfo` Member von sollten auf **0**, FALSE oder eine leere `CDaoException` Zeichenfolge gesetzt werden, je nach Element, oder eine auftreten kann.

Weitere Informationen finden Sie im Thema "CreateField-Methode" in der DAO-Hilfe.

## <a name="cdaotabledefcreateindex"></a><a name="createindex"></a>CDaoTableDef::CreateIndex

Rufen Sie diese Funktion auf, um einer Tabelle einen Index hinzuzufügen.

```cpp
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>Parameter

*indexinfo*<br/>
Ein Verweis auf eine [CDaoIndexInfo-Struktur.](../../mfc/reference/cdaoindexinfo-structure.md)

### <a name="remarks"></a>Bemerkungen

Indizes geben die Reihenfolge der Datensätze an, auf die aus Datenbanktabellen zugegriffen wird, und angeben, ob doppelte Datensätze akzeptiert werden. Indizes bieten auch einen effizienten Zugriff auf Daten.

Sie müssen keine Indizes für Tabellen erstellen, aber in großen, nicht indizierten Tabellen kann der Zugriff auf einen bestimmten Datensatz oder das Erstellen eines Recordsets sehr lange dauern. Andererseits verlangsamt das Erstellen zu vieler Indizes Aktualisierungs-, An- und Löschvorgänge, da alle Indizes automatisch aktualisiert werden. Berücksichtigen Sie diese Faktoren, wenn Sie entscheiden, welche Indizes erstellt werden sollen.

Folgende Elemente der `CDaoIndexInfo` Struktur müssen festgelegt werden:

- `m_strName`Es muss ein Name angegeben werden.

- `m_pFieldInfos`Muss auf ein `CDaoIndexFieldInfo` Array von Strukturen verweisen.

- `m_nFields`Muss die Anzahl der Felder `CDaoFieldInfo` im Array von Strukturen angeben.

Die verbleibenden Member werden ignoriert, wenn sie auf FALSE festgelegt sind. Darüber hinaus `m_lDistinctCount` wird das Element bei der Erstellung des Indexes ignoriert.

## <a name="cdaotabledefdeletefield"></a><a name="deletefield"></a>CDaoTableDef::DeleteField

Rufen Sie diese Memberfunktion auf, um ein Feld zu entfernen und nicht darauf zu zugreifen.

```cpp
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Ein Zeiger auf einen Zeichenfolgenausdruck, der der Name eines vorhandenen Felds ist.

*nIndex*<br/>
Der Index des Feldes in der Null-basierten Fields-Auflistung der Tabelle für die Suche nach Index.

### <a name="remarks"></a>Bemerkungen

Sie können diese Memberfunktion für ein neues Objekt verwenden, das nicht an die Datenbank angehängt wurde oder wenn [CanUpdate](#canupdate) einen Wert ungleich Null zurückgibt.

Weitere Informationen finden Sie im Thema "Methode löschen" in der DAO-Hilfe.

## <a name="cdaotabledefdeleteindex"></a><a name="deleteindex"></a>CDaoTableDef::DeleteIndex

Rufen Sie diese Memberfunktion auf, um einen Index in einer zugrunde liegenden Tabelle zu löschen.

```cpp
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Ein Zeiger auf einen Zeichenfolgenausdruck, der der Name eines vorhandenen Indexes ist.

*nIndex*<br/>
Der Arrayindex des Indexobjekts in der Zero-basierten TableDefs-Auflistung der Datenbank für die Suche nach Index.

### <a name="remarks"></a>Bemerkungen

Sie können diese Memberfunktion für ein neues Objekt verwenden, das nicht an die Datenbank angehängt wurde oder wenn [CanUpdate](#canupdate) einen Wert ungleich Null zurückgibt.

Weitere Informationen finden Sie im Thema "Methode löschen" in der DAO-Hilfe.

## <a name="cdaotabledefgetattributes"></a><a name="getattributes"></a>CDaoTableDef::GetAttributes

Für `CDaoTableDef` ein Objekt gibt der Rückgabewert die Merkmale `CDaoTableDef` der Tabelle an, die durch das Objekt dargestellt wird, und kann eine Summe dieser Konstanten sein:

```
long GetAttributes();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert zurück, der `CDaoTableDef` ein oder mehrere Merkmale eines Objekts angibt.

### <a name="remarks"></a>Bemerkungen

|Konstante|BESCHREIBUNG|
|--------------|-----------------|
|`dbAttachExclusive`|Für Datenbanken, die das Microsoft Jet-Datenbankmodul verwenden, gibt die Tabelle an, dass es sich um eine angefügte Tabelle handelt, die exklusiv verwendet wird.|
|`dbAttachSavePWD`|Gibt für Datenbanken an, die das Microsoft Jet-Datenbankmodul verwenden, dass die Benutzer-ID und das Kennwort für die angefügte Tabelle mit den Verbindungsinformationen gespeichert werden.|
|`dbSystemObject`|Gibt an, dass es sich bei der Tabelle um eine Systemtabelle handelt, die vom Microsoft Jet-Datenbankmodul bereitgestellt wird.|
|`dbHiddenObject`|Gibt an, dass es sich bei der Tabelle um eine ausgeblendete Tabelle handelt, die vom Microsoft Jet-Datenbankmodul bereitgestellt wird.|
|`dbAttachedTable`|Gibt an, dass es sich bei der Tabelle um eine angefügte Tabelle aus einer Nicht-ODBC-Datenbank handelt, z. B. einer Paradox-Datenbank.|
|`dbAttachedODBC`|Gibt an, dass es sich bei der Tabelle um eine angefügte Tabelle aus einer ODBC-Datenbank, z. B. Microsoft SQL Server, handelt.|

Eine Systemtabelle ist eine Tabelle, die vom Microsoft Jet-Datenbankmodul erstellt wurde und verschiedene interne Informationen enthält.

Eine ausgeblendete Tabelle ist eine Tabelle, die für die temporäre Verwendung durch das Microsoft Jet-Datenbankmodul erstellt wurde.

Weitere Informationen finden Sie im Thema "Attributes Property" in der DAO-Hilfe.

## <a name="cdaotabledefgetconnect"></a><a name="getconnect"></a>CDaoTableDef::GetConnect

Rufen Sie diese Memberfunktion auf, um die Verbindungszeichenfolge für eine Datenquelle abzurufen.

```
CString GetConnect();
```

### <a name="return-value"></a>Rückgabewert

Ein `CString` Objekt, das den Pfad und den Datenbanktyp für die Tabelle enthält.

### <a name="remarks"></a>Bemerkungen

Für `CDaoTableDef` ein Objekt, das eine `CString` angefügte Tabelle darstellt, besteht das Objekt aus einem oder zwei Teilen (ein Datenbanktypbezeichner und ein Pfad zur Datenbank).

Der Pfad, wie in der folgenden Tabelle gezeigt, ist der vollständige Pfad für das Verzeichnis, das die Datenbankdateien enthält, und muss dem Bezeichner "DATABASE=" vorangestellt werden. In einigen Fällen (wie bei Microsoft Jet- und Microsoft Excel-Datenbanken) ist ein bestimmter Dateiname im Argument des Datenbankpfads enthalten.

Die Tabelle in [CDaoTableDef::SetConnect](#setconnect) zeigt mögliche Datenbanktypen und die entsprechenden Datenbankbezeichner und Pfade:

Bei Microsoft Jet-Datenbankbasistabellen ist der Bezeichner eine leere Zeichenfolge ("").

Wenn ein Kennwort erforderlich, aber nicht angegeben ist, zeigt der ODBC-Treiber ein Anmeldedialogfeld an, wenn zum ersten Mal auf eine Tabelle zugegriffen wird, und erneut, wenn die Verbindung geschlossen und erneut geöffnet wird. Wenn eine angefügte `dbAttachSavePWD` Tabelle das Attribut hat, wird die Anmeldeaufforderung nicht angezeigt, wenn die Tabelle erneut geöffnet wird.

Weitere Informationen finden Sie im Thema "Verbindungseigenschaft" in der DAO-Hilfe.

## <a name="cdaotabledefgetdatecreated"></a><a name="getdatecreated"></a>CDaoTableDef::GetDateErstellt

Rufen Sie diese Funktion auf, um `CDaoTableDef` das Datum und die Uhrzeit zu bestimmen, zu der die dem Objekt zugrunde liegende Tabelle erstellt wurde.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der das Datum und die `CDaoTableDef` Uhrzeit der Erstellung der dem Objekt zugrunde liegenden Tabelle enthält.

### <a name="remarks"></a>Bemerkungen

Die Datums- und Uhrzeiteinstellungen werden von dem Computer abgeleitet, auf dem die Basistabelle erstellt oder zuletzt aktualisiert wurde. In einer Mehrbenutzerumgebung sollten Benutzer diese Einstellungen direkt vom Dateiserver abrufen, um Abweichungen zu vermeiden. Das heißt, alle Clients sollten eine "Standard"-Zeitquelle verwenden – möglicherweise von einem Server aus.

Weitere Informationen finden Sie im Thema "DateCreated, LastUpdated Properties" in der DAO-Hilfe.

## <a name="cdaotabledefgetdatelastupdated"></a><a name="getdatelastupdated"></a>CDaoTableDef::GetDateLastUpdated

Rufen Sie diese Funktion auf, um `CDaoTableDef` das Datum und die Uhrzeit zu bestimmen, zu der die dem Objekt zugrunde liegende Tabelle zuletzt aktualisiert wurde.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert, der das Datum und `CDaoTableDef` die Uhrzeit enthält, zu der die Tabelle, die dem Objekt zugrunde liegt, zuletzt aktualisiert wurde.

### <a name="remarks"></a>Bemerkungen

Die Datums- und Uhrzeiteinstellungen werden von dem Computer abgeleitet, auf dem die Basistabelle erstellt oder zuletzt aktualisiert wurde. In einer Mehrbenutzerumgebung sollten Benutzer diese Einstellungen direkt vom Dateiserver abrufen, um Abweichungen zu vermeiden. Das heißt, alle Clients sollten eine "Standard"-Zeitquelle verwenden – möglicherweise von einem Server aus.

Weitere Informationen finden Sie im Thema "DateCreated, LastUpdated Properties" in der DAO-Hilfe.

## <a name="cdaotabledefgetfieldcount"></a><a name="getfieldcount"></a>CDaoTableDef::GetFieldCount

Rufen Sie diese Memberfunktion auf, um die Anzahl der in der Tabelle definierten Felder abzurufen.

```
short GetFieldCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Felder in der Tabelle.

### <a name="remarks"></a>Bemerkungen

Wenn der Wert 0 ist, sind keine Objekte in der Auflistung vorhanden.

Weitere Informationen finden Sie im Thema "Count Property" in der DAO-Hilfe.

## <a name="cdaotabledefgetfieldinfo"></a><a name="getfieldinfo"></a>CDaoTableDef::GetFieldInfo

Rufen Sie diese Memberfunktion auf, um verschiedene Arten von Informationen zu einem feld zu erhalten, das in der tabledef definiert ist.

```cpp
void GetFieldInfo(
    int nIndex,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetFieldInfo(
    LPCTSTR lpszName,
    CDaoFieldInfo& fieldinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der Index des Feldobjekts in der Null-basierten Fields-Auflistung der Tabelle für die Suche nach Index.

*Fieldinfo*<br/>
Ein Verweis auf eine [CDaoFieldInfo-Struktur.](../../mfc/reference/cdaofieldinfo-structure.md)

*dwInfoOptionen*<br/>
Optionen, die angeben, welche Informationen über das abzurufende Feld abgerufen werden sollen. Die verfügbaren Optionen sind hier zusammen mit dem, was die Funktion zurückgeben lässt aufgeführt:

- `AFX_DAO_PRIMARY_INFO`(Standard) Name, Typ, Größe, Attribute. Verwenden Sie diese Option für die schnellste Leistung.

- `AFX_DAO_SECONDARY_INFO`Primärinformationen, plus: Ordinalposition, Erforderlich, Nulllänge zulassen, Sortierreihenfolge, Fremdname, Quellfeld, Quelltabelle

- `AFX_DAO_ALL_INFO`Primäre und sekundäre Informationen sowie: Validierungsregel, Validierungstext, Standardwert

*lpszName*<br/>
Ein Zeiger auf den Namen des Feldobjekts für die Suche nach Namen. Der Name ist eine Zeichenfolge mit bis zu 64 Zeichen, die das Feld eindeutig benennt.

### <a name="remarks"></a>Bemerkungen

Mit einer Version der Funktion können Sie ein Feld nach Index suchen. Mit der anderen Version können Sie ein Feld nach Namen suchen.

Eine Beschreibung der zurückgegebenen Informationen finden Sie in der [CDaoFieldInfo-Struktur.](../../mfc/reference/cdaofieldinfo-structure.md) Diese Struktur verfügt über Member, die den oben aufgeführten Informationen in der Beschreibung von *dwInfoOptions*entsprechen. Wenn Sie Informationen auf einer Ebene anfordern, erhalten Sie auch Informationen für alle vorherigen Ebenen.

Weitere Informationen finden Sie im Thema "Attributes Property" in der DAO-Hilfe.

## <a name="cdaotabledefgetindexcount"></a><a name="getindexcount"></a>CDaoTableDef::GetIndexCount

Rufen Sie diese Memberfunktion auf, um die Anzahl der Indizes für eine Tabelle abzurufen.

```
short GetIndexCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Indizes für die Tabelle.

### <a name="remarks"></a>Bemerkungen

Wenn der Wert 0 ist, sind keine Indizes in der Auflistung vorhanden.

Weitere Informationen finden Sie im Thema "Count Property" in der DAO-Hilfe.

## <a name="cdaotabledefgetindexinfo"></a><a name="getindexinfo"></a>CDaoTableDef::GetIndexInfo

Rufen Sie diese Memberfunktion auf, um verschiedene Arten von Informationen über einen in der tabledef definierten Index abzurufen.

```cpp
void GetIndexInfo(
    int nIndex,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetIndexInfo(
    LPCTSTR lpszName,
    CDaoIndexInfo& indexinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der numerische Index des Indexobjekts in der Null-basierten Indexauflistung der Tabelle für die Suche nach seiner Position in der Auflistung.

*indexinfo*<br/>
Ein Verweis auf eine [CDaoIndexInfo-Struktur.](../../mfc/reference/cdaoindexinfo-structure.md)

*dwInfoOptionen*<br/>
Optionen, die angeben, welche Informationen über den abzurufenden Index abgerufen werden sollen. Die verfügbaren Optionen sind hier zusammen mit dem, was die Funktion zurückgeben lässt aufgeführt:

- `AFX_DAO_PRIMARY_INFO`Name, Feldinfo, Felder. Verwenden Sie diese Option für die schnellste Leistung.

- `AFX_DAO_SECONDARY_INFO`Primärinformationen, plus: Primär, Eindeutig, Gruppiert, Nullen ignorieren, Erforderlich, Fremd

- `AFX_DAO_ALL_INFO`Primäre und sekundäre Informationen, plus: Distinct Count

*lpszName*<br/>
Ein Zeiger auf den Namen des Indexobjekts für die Suche nach Namen.

### <a name="remarks"></a>Bemerkungen

Mit einer Version der Funktion können Sie einen Index anhand seiner Position in der Auflistung nachschlagen. Mit der anderen Version können Sie einen Index nach Namen suchen.

Eine Beschreibung der zurückgegebenen Informationen finden Sie in der [CDaoIndexInfo-Struktur.](../../mfc/reference/cdaoindexinfo-structure.md) Diese Struktur verfügt über Member, die den oben aufgeführten Informationen in der Beschreibung von *dwInfoOptions*entsprechen. Wenn Sie Informationen auf einer Ebene anfordern, erhalten Sie auch Informationen für alle vorherigen Ebenen.

Weitere Informationen finden Sie im Thema "Attributes Property" in der DAO-Hilfe.

## <a name="cdaotabledefgetname"></a><a name="getname"></a>CDaoTableDef::GetName

Rufen Sie diese Memberfunktion auf, um den benutzerdefinierten Namen der zugrunde liegenden Tabelle abzurufen.

```
CString GetName();
```

### <a name="return-value"></a>Rückgabewert

Ein benutzerdefinierter Name für eine Tabelle.

### <a name="remarks"></a>Bemerkungen

Dieser Name beginnt mit einem Buchstaben und kann maximal 64 Zeichen enthalten. Sie kann Zahlen und Unterstrichzeichen enthalten, aber keine Interpunktion oder Leerzeichen.

Weitere Informationen finden Sie im Thema "Name-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaotabledefgetrecordcount"></a><a name="getrecordcount"></a>CDaoTableDef::GetRecordCount

Rufen Sie diese Memberfunktion auf, um `CDaoTableDef` herauszufinden, wie viele Datensätze sich in einem Objekt befinden.

```
long GetRecordCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Datensätze, auf die in einem tabledef-Objekt zugegriffen wird.

### <a name="remarks"></a>Bemerkungen

Das `GetRecordCount` Aufrufen eines `CDaoTableDef` Tabellentypobjekts spiegelt die ungefähre Anzahl von Datensätzen in der Tabelle wider und wird sofort beeinflusst, wenn Tabellendatensätze hinzugefügt und gelöscht werden. Rollbacktransaktionen werden als Teil der Datensatzanzahl angezeigt, bis Sie [CDaoWorkSpace::CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase)aufrufen. Ein `CDaoTableDef` Objekt ohne Datensätze hat die Eigenschaftseinstellung 0 für die Datensatzanzahl. Wenn Sie mit angefügten Tabellen `GetRecordCount` oder ODBC-Datenbanken arbeiten, gibt immer -1 zurück.

Weitere Informationen finden Sie im Thema "RecordCount-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaotabledefgetsourcetablename"></a><a name="getsourcetablename"></a>CDaoTableDef::GetSourceTableName

Rufen Sie diese Memberfunktion auf, um den Namen einer angehängten Tabelle in einer Quelldatenbank abzurufen.

```
CString GetSourceTableName();
```

### <a name="return-value"></a>Rückgabewert

Ein `CString` Objekt, das den Quellnamen einer angefügten Tabelle angibt, oder eine leere Zeichenfolge, wenn eine systemeigene Datentabelle.

### <a name="remarks"></a>Bemerkungen

Eine angefügte Tabelle ist eine Tabelle in einer anderen Datenbank, die mit einer Microsoft Jet-Datenbank verknüpft ist. Daten für angefügte Tabellen verbleiben in der externen Datenbank, wo sie von anderen Anwendungen bearbeitet werden können.

Weitere Informationen finden Sie im Thema "SourceTableName-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaotabledefgetvalidationrule"></a><a name="getvalidationrule"></a>CDaoTableDef::GetValidationRule

Rufen Sie diese Memberfunktion auf, um die Validierungsregel für eine tabledef abzurufen.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Rückgabewert

Ein `CString` Objekt, das die Daten in einem Feld überprüft, wenn sie geändert oder einer Tabelle hinzugefügt werden.

### <a name="remarks"></a>Bemerkungen

Validierungsregeln werden in Verbindung mit Aktualisierungsvorgängen verwendet. Wenn eine tabledef eine Validierungsregel enthält, müssen Aktualisierungen dieser tabledef vorbestimmten Kriterien übereinstimmen, bevor die Daten geändert werden. Wenn die Änderung nicht den Kriterien entspricht, wird eine Ausnahme ausgelöst, die den Wert [GetValidationText](#getvalidationtext) enthält. Für `CDaoTableDef` ein Objekt `CString` ist dies schreibgeschützt für eine angefügte Tabelle und Lese-/Schreibzugriff für eine Basistabelle.

Weitere Informationen finden Sie im Thema "ValidationRule-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaotabledefgetvalidationtext"></a><a name="getvalidationtext"></a>CDaoTableDef::GetValidationText

Rufen Sie diese Funktion auf, um die Zeichenfolge abzurufen, die angezeigt wird, wenn ein Benutzer Daten eingibt, die nicht mit der Validierungsregel übereinstimmen.

```
CString GetValidationText();
```

### <a name="return-value"></a>Rückgabewert

Ein `CString` Objekt, das den angezeigten Text angibt, wenn der Benutzer Daten eingibt, die nicht mit der Validierungsregel übereinstimmen.

### <a name="remarks"></a>Bemerkungen

Für `CDaoTableDef` ein Objekt `CString` ist dies schreibgeschützt für eine angefügte Tabelle und Lese-/Schreibzugriff für eine Basistabelle.

Weitere Informationen finden Sie im Thema "ValidationText-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaotabledefisopen"></a><a name="isopen"></a>CDaoTableDef::IsOpen

Rufen Sie diese Memberfunktion `CDaoTableDef` auf, um zu bestimmen, ob das Objekt derzeit geöffnet ist.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert `CDaoTableDef` ungleich Null, wenn das Objekt geöffnet ist; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

## <a name="cdaotabledefm_pdatabase"></a><a name="m_pdatabase"></a>CDaoTableDef::m_pDatabase

Enthält einen Zeiger auf das [CDaoDatabase-Objekt](../../mfc/reference/cdaodatabase-class.md) für diese Tabelle.

### <a name="remarks"></a>Bemerkungen

## <a name="cdaotabledefm_pdaotabledef"></a><a name="m_pdaotabledef"></a>CDaoTableDef::m_pDAOTableDef

Enthält einen Zeiger auf die OLE-Schnittstelle für das `CDaoTableDef` DAO tabledef-Objekt, das dem Objekt zugrunde liegt.

### <a name="remarks"></a>Bemerkungen

Verwenden Sie diesen Zeiger, wenn Sie direkt auf die DAO-Schnittstelle zugreifen müssen.

## <a name="cdaotabledefopen"></a><a name="open"></a>CDaoTableDef::Öffnen

Rufen Sie diese Memberfunktion auf, um eine Tabledef zu öffnen, die zuvor in der TableDef-Auflistung der Datenbank gespeichert war.

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Ein Zeiger auf eine Zeichenfolge, die einen Tabellennamen angibt.

### <a name="remarks"></a>Bemerkungen

## <a name="cdaotabledefrefreshlink"></a><a name="refreshlink"></a>CDaoTableDef::RefreshLink

Rufen Sie diese Memberfunktion auf, um die Verbindungsinformationen für eine angehängte Tabelle zu aktualisieren.

```cpp
void RefreshLink();
```

### <a name="remarks"></a>Bemerkungen

Sie ändern die Verbindungsinformationen für eine angefügte `CDaoTableDef` Tabelle, indem `RefreshLink` Sie [SetConnect](#setconnect) für das entsprechende Objekt aufrufen und dann die Memberfunktion verwenden, um die Informationen zu aktualisieren. Wenn Sie `RefreshLink`aufrufen, werden die Eigenschaften der angefügten Tabelle nicht geändert.

Damit die geänderten Verbindungsinformationen wirksam werden, müssen alle geöffneten [CDaoRecordset-Objekte,](../../mfc/reference/cdaorecordset-class.md) die auf dieser tabledef basieren, geschlossen werden.

Weitere Informationen finden Sie im Thema "RefreshLink-Methode" in der DAO-Hilfe.

## <a name="cdaotabledefsetattributes"></a><a name="setattributes"></a>CDaoTableDef::SetAttributes

Legt einen Wert fest, der `CDaoTableDef` ein oder mehrere Merkmale eines Objekts angibt.

```cpp
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>Parameter

*lAttributes*<br/>
Merkmale der Tabelle, `CDaoTableDef` die durch das Objekt dargestellt wird und eine Summe dieser Konstanten sein kann:

|Konstante|BESCHREIBUNG|
|--------------|-----------------|
|`dbAttachExclusive`|Für Datenbanken, die das Microsoft Jet-Datenbankmodul verwenden, gibt die Tabelle an, dass es sich um eine angefügte Tabelle handelt, die exklusiv verwendet wird.|
|`dbAttachSavePWD`|Gibt für Datenbanken an, die das Microsoft Jet-Datenbankmodul verwenden, dass die Benutzer-ID und das Kennwort für die angefügte Tabelle mit den Verbindungsinformationen gespeichert werden.|
|`dbSystemObject`|Gibt an, dass es sich bei der Tabelle um eine Systemtabelle handelt, die vom Microsoft Jet-Datenbankmodul bereitgestellt wird.|
|`dbHiddenObject`|Gibt an, dass es sich bei der Tabelle um eine ausgeblendete Tabelle handelt, die vom Microsoft Jet-Datenbankmodul bereitgestellt wird.|

### <a name="remarks"></a>Bemerkungen

Wenn Sie mehrere Attribute festlegen, können Sie diese kombinieren, indem Sie die entsprechenden Konstanten mithilfe des Bitwise-OR-Operators summieren. Das `dbAttachExclusive` Festlegen einer nicht angefügten Tabelle führt zu einer Ausnahme. Das Kombinieren der folgenden Werte bildet auch eine Ausnahme:

- **dbAttachExclusive &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dbAttachedTable**

Weitere Informationen finden Sie im Thema "Attributes Property" in der DAO-Hilfe.

## <a name="cdaotabledefsetconnect"></a><a name="setconnect"></a>CDaoTableDef::SetConnect

Für `CDaoTableDef` ein Objekt, das eine angefügte Tabelle darstellt, besteht das Zeichenfolgenobjekt aus einem oder zwei Teilen (ein Datenbanktypbezeichner und ein Pfad zur Datenbank).

```cpp
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parameter

*lpszConnect*<br/>
Ein Zeiger auf einen Zeichenfolgenausdruck, der zusätzliche Parameter angibt, die an ODBC- oder installierbare ISAM-Treiber übergeben werden sollen.

### <a name="remarks"></a>Bemerkungen

Der Pfad, wie in der folgenden Tabelle gezeigt, ist der vollständige Pfad für das Verzeichnis, das die Datenbankdateien enthält, und muss dem Bezeichner "DATABASE=" vorangestellt werden. In einigen Fällen (wie bei Microsoft Jet- und Microsoft Excel-Datenbanken) ist ein bestimmter Dateiname im Argument des Datenbankpfads enthalten.

> [!NOTE]
> Schließen Sie keine Leerzeichen um das Gleichheitszeichen in Pfadanweisungen des Formulars "DATABASE=drive: épath"\\ein. Dies führt dazu, dass eine Ausnahme ausgelöst wird und die Verbindung fehlschlägt.

Die folgende Tabelle zeigt mögliche Datenbanktypen und die entsprechenden Datenbankbezeichner und Pfade:

|Datenbanktyp|Bezeichner|`Path`|
|-------------------|---------------|----------|
|Datenbank mit dem Jet-Datenbankmodul|"[ `database`];"|" `drive`\\\ :\\\ *Pfaddateiname*.*path* MDB"|
|dBASE III|"dBASE III;"|" `drive`\\\ :*Pfad*"|
|dBASE IV|"dBASE IV;"|" `drive`\\\ :*Pfad*"|
|dBASE 5|"dBASE 5.0;"|" `drive`\\\ :*Pfad*"|
|Paradox 3.x|"Paradox 3.x;"|" `drive`\\\ :*Pfad*"|
|Paradox 4.x|"Paradox 4.x;"|" `drive`\\\ :*Pfad*"|
|Paradox 5.x|"Paradox 5.x;"|" `drive`\\\ :*Pfad*"|
|Excel 3.0|"Excel 3.0;"|" `drive`\\\ :\\\ *Pfaddateiname*.*path* XLS"|
|Excel 4.0|"Excel 4.0;"|" `drive`\\\ :\\\ *Pfaddateiname*.*path* XLS"|
|Excel 5.0 oder Excel 95|"Excel 5.0;"|" `drive`\\\ :\\\ *Pfaddateiname*.*path* XLS"|
|Excel 97|"Excel 8.0;"|" `drive`\\\ :*Pfaddateiname**path*\ . XLS"|
|HTML-Import|"HTML-Import;"|" `drive`\\\ :*Pfaddateiname**path*\ "|
|HTML-Export|"HTML-Export;"|" `drive`\\\ :*Pfad*"|
|Text|"Text;"|"Antrieb:\\'Pfad'|
|ODBC|"ODBC; DATENBANK= `database`; UID= *Benutzer*; PWD= *Passwort*; DSN= *Datenquellenname;* LOGINTIMEOUT= *Sekunden;*" (Dies ist möglicherweise nicht eine vollständige Verbindungszeichenfolge für alle Server; es ist nur ein Beispiel. Es ist sehr wichtig, keine Leerzeichen zwischen den Parametern zu haben.)|Keine|
|Exchange|"Austausch;<br /><br /> MAPILEVEL= *Ordnerpfad*;<br /><br /> [TABLETYPE= 0 &#124; 1;]<br /><br /> [PROFILE= *Profil*;]<br /><br /> [PWD= *Kennwort*;]<br /><br /> [DATENBANK= `database`;]"|*"drive*\\\ :\\\ *Pfaddateiname*.*path* MDB"|

> [!NOTE]
> Btrieve wird ab DAO 3.5 nicht mehr unterstützt.

Sie müssen einen doppelten umgekehrten Schrägstrich (\\\\) in den Verbindungszeichenfolgen verwenden. Wenn Sie die Eigenschaften einer vorhandenen `SetConnect`Verbindung mithilfe von geändert haben, müssen Sie anschließend [RefreshLink](#refreshlink)aufrufen. Wenn Sie die Verbindungseigenschaften `SetConnect`mit initialisieren, `RefreshLink`müssen Sie nicht aufrufen, sollten Sie dies jedoch zuerst an die tabledef anhängen.

Wenn ein Kennwort erforderlich, aber nicht angegeben ist, zeigt der ODBC-Treiber ein Anmeldedialogfeld an, wenn zum ersten Mal auf eine Tabelle zugegriffen wird, und erneut, wenn die Verbindung geschlossen und erneut geöffnet wird.

Sie können die Verbindungszeichenfolge `CDaoTableDef` für ein Objekt festlegen, indem Sie der `Create` Memberfunktion ein Quellargument bereitstellen. Sie können die Einstellung überprüfen, um den Typ, pfad, benutzer-ID, das Kennwort oder die ODBC-Datenquelle der Datenbank zu bestimmen. Weitere Informationen finden Sie in der Dokumentation zum jeweiligen Treiber.

Weitere Informationen finden Sie im Thema "Verbindungseigenschaft" in der DAO-Hilfe.

## <a name="cdaotabledefsetname"></a><a name="setname"></a>CDaoTableDef::SetName

Rufen Sie diese Memberfunktion auf, um einen benutzerdefinierten Namen für eine Tabelle festzulegen.

```cpp
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*lpszName*<br/>
Ein Zeiger auf einen Zeichenfolgenausdruck, der einen Namen für eine Tabelle angibt.

### <a name="remarks"></a>Bemerkungen

Der Name muss mit einem Buchstaben beginnen und darf maximal 64 Zeichen enthalten. Sie kann Zahlen und Unterstrichzeichen enthalten, aber keine Interpunktion oder Leerzeichen.

Weitere Informationen finden Sie im Thema "Name-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaotabledefsetsourcetablename"></a><a name="setsourcetablename"></a>CDaoTableDef::SetSourceTableName

Rufen Sie diese Memberfunktion auf, um den Namen einer angefügten Tabelle oder den Namen der Basistabelle anzugeben, auf der das `CDaoTableDef` Objekt basiert, wie er in der ursprünglichen Datenquelle der Daten vorhanden ist.

```cpp
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>Parameter

*lpszSrcTableName*<br/>
Ein Zeiger auf einen Zeichenfolgenausdruck, der einen Tabellennamen in der externen Datenbank angibt. Bei einer Basistabelle ist die Einstellung eine leere Zeichenfolge ("").

### <a name="remarks"></a>Bemerkungen

Sie müssen dann [RefreshLink](#refreshlink)aufrufen. Diese Eigenschaftseinstellung ist für eine Basistabelle und Für eine angefügte Tabelle oder ein Objekt, das nicht an eine Auflistung angehängt ist, leer.

Weitere Informationen finden Sie im Thema "SourceTableName-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaotabledefsetvalidationrule"></a><a name="setvalidationrule"></a>CDaoTableDef::SetValidationRule

Rufen Sie diese Memberfunktion auf, um eine Validierungsregel für eine tabledef festzulegen.

```cpp
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>Parameter

*lpszValidationRule*<br/>
Ein Zeiger auf einen Zeichenfolgenausdruck, der einen Vorgang überprüft.

### <a name="remarks"></a>Bemerkungen

Validierungsregeln werden in Verbindung mit Aktualisierungsvorgängen verwendet. Wenn eine tabledef eine Validierungsregel enthält, müssen Aktualisierungen dieser tabledef vorbestimmten Kriterien übereinstimmen, bevor die Daten geändert werden. Wenn die Änderung nicht den Kriterien entspricht, wird eine Ausnahme angezeigt, die den Text von [GetValidationText](#getvalidationtext) enthält.

Die Validierung wird nur für Datenbanken unterstützt, die das Microsoft Jet-Datenbankmodul verwenden. Der Ausdruck kann nicht auf benutzerdefinierte Funktionen, Domänenaggregatfunktionen, SQL-Aggregatfunktionen oder Abfragen verweisen. Eine Validierungsregel `CDaoTableDef` für ein Objekt kann auf mehrere Felder in diesem Objekt verweisen.

Für Felder mit dem Namen *hire_date* und *termination_date*kann eine Validierungsregel z. B. sein:

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

Weitere Informationen finden Sie im Thema "ValidationRule-Eigenschaft" in der DAO-Hilfe.

## <a name="cdaotabledefsetvalidationtext"></a><a name="setvalidationtext"></a>CDaoTableDef::SetValidationText

Rufen Sie diese Memberfunktion auf, um den `CDaoTableDef` Ausnahmetext einer Validierungsregel für ein Objekt mit einer zugrunde liegenden Basistabelle festzulegen, die vom Microsoft Jet-Datenbankmodul unterstützt wird.

```cpp
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>Parameter

*lpszValidationText*<br/>
Ein Zeiger auf einen Zeichenfolgenausdruck, der den angezeigten Text angibt, wenn eingegebene Daten ungültig sind.

### <a name="remarks"></a>Bemerkungen

Sie können den Validierungstext einer angehängten Tabelle nicht festlegen.

Weitere Informationen finden Sie im Thema "ValidationText-Eigenschaft" in der DAO-Hilfe.

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase-Klasse](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset-Klasse](../../mfc/reference/cdaorecordset-class.md)

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
ms.openlocfilehash: 485fe3533916e5e59bc87084f58acfb37368ac32
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424512"
---
# <a name="cdaotabledef-class"></a>CDaoTableDef-Klasse

Stellt die gespeicherte Definition einer Basistabelle oder einer angefügten Tabelle dar.

## <a name="syntax"></a>Syntax

```
class CDaoTableDef : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|-Name|Beschreibung|
|----------|-----------------|
|[CDaoTableDef::CDaoTableDef](#cdaotabledef)|Erstellt ein `CDaoTableDef`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|-Name|Beschreibung|
|----------|-----------------|
|[CDaoTableDef::Append](#append)|Fügt der Datenbank eine neue Tabelle hinzu.|
|[CDaoTableDef::CanUpdate](#canupdate)|Gibt einen Wert ungleich 0 (null) zurück, wenn die Tabelle aktualisiert werden kann (Sie können die Definition von Feldern oder Tabellen Eigenschaften ändern).|
|[CDaoTableDef::Close](#close)|Schließt eine geöffnete Tabledef.|
|[CDaoTableDef::Create](#create)|Erstellt eine Tabelle, die mithilfe von [Append](#append)der Datenbank hinzugefügt werden kann.|
|[CDaoTableDef::CreateField](#createfield)|Wird aufgerufen, um ein Feld für eine Tabelle zu erstellen.|
|[CDaoTableDef::CreateIndex](#createindex)|Wird aufgerufen, um einen Index für eine Tabelle zu erstellen.|
|[CDaoTableDef::DeleteField](#deletefield)|Wird aufgerufen, um ein Feld aus einer Tabelle zu löschen.|
|[CDaoTableDef::DeleteIndex](#deleteindex)|Wird aufgerufen, um einen Index aus einer Tabelle zu löschen.|
|[CDaoTableDef::GetAttributes](#getattributes)|Gibt einen Wert zurück, der eine oder mehrere Eigenschaften eines `CDaoTableDef`-Objekts angibt.|
|[CDaoTableDef::GetConnect](#getconnect)|Gibt einen Wert zurück, der Informationen über die Quelle einer Tabelle bereitstellt.|
|[CDaoTableDef::GetDateCreated](#getdatecreated)|Gibt das Datum und die Uhrzeit der Erstellung der Basistabelle zurück, die einem `CDaoTableDef`-Objekt zugrunde liegt.|
|[CDaoTableDef::GetDateLastUpdated](#getdatelastupdated)|Gibt das Datum und die Uhrzeit der letzten Änderung an, die am Entwurf der Basistabelle vorgenommen wurden.|
|[CDaoTableDef::GetFieldCount](#getfieldcount)|Gibt einen Wert zurück, der die Anzahl der Felder in der Tabelle darstellt.|
|[CDaoTableDef::GetFieldInfo](#getfieldinfo)|Gibt bestimmte Arten von Informationen zu den Feldern in der Tabelle zurück.|
|[CDaoTableDef::GetIndexCount](#getindexcount)|Gibt die Anzahl der Indizes für die Tabelle zurück.|
|[CDaoTableDef::GetIndexInfo](#getindexinfo)|Gibt bestimmte Arten von Informationen über die Indizes für die Tabelle zurück.|
|[CDaoTableDef::GetName](#getname)|Gibt den benutzerdefinierten Namen der Tabelle zurück.|
|[CDaoTableDef::GetRecordCount](#getrecordcount)|Gibt die Anzahl der Datensätze in der Tabelle zurück.|
|[CDaoTableDef::GetSourceTableName](#getsourcetablename)|Gibt einen-Wert zurück, der den Namen der angefügten Tabelle in der Quelldatenbank angibt.|
|[CDaoTableDef::GetValidationRule](#getvalidationrule)|Gibt einen Wert zurück, der die Daten in einem Feld überprüft, wenn es geändert oder einer Tabelle hinzugefügt wird.|
|[CDaoTableDef::GetValidationText](#getvalidationtext)|Gibt einen Wert zurück, der den Text der Meldung angibt, die von der Anwendung angezeigt wird, wenn der Wert eines Feld Objekts die angegebene Validierungs Regel nicht erfüllt.|
|[CDaoTableDef::IsOpen](#isopen)|Gibt einen Wert ungleich 0 zurück, wenn die Tabelle geöffnet ist.|
|[CDaoTableDef::Open](#open)|Öffnet eine vorhandene Tabledef, die in der tabledefes-Auflistung der Datenbank gespeichert ist.|
|[CDaoTableDef::RefreshLink](#refreshlink)|Aktualisiert die Verbindungsinformationen für eine angefügte Tabelle.|
|[CDaoTableDef::SetAttributes](#setattributes)|Legt einen Wert fest, der eine oder mehrere Eigenschaften eines `CDaoTableDef`-Objekts angibt.|
|[CDaoTableDef::SetConnect](#setconnect)|Legt einen Wert fest, der Informationen über die Quelle einer Tabelle bereitstellt.|
|[CDaoTableDef::SetName](#setname)|Legt den Namen der Tabelle fest.|
|[CDaoTableDef::SetSourceTableName](#setsourcetablename)|Legt einen Wert fest, der den Namen einer angefügten Tabelle in der Quelldatenbank angibt.|
|[CDaoTableDef::SetValidationRule](#setvalidationrule)|Legt einen Wert fest, der die Daten in einem Feld überprüft, während Sie geändert oder einer Tabelle hinzugefügt werden.|
|[CDaoTableDef::SetValidationText](#setvalidationtext)|Legt einen Wert fest, der den Text der Meldung angibt, die von der Anwendung angezeigt wird, wenn der Wert eines Feld Objekts die angegebene Validierungs Regel nicht erfüllt.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|Beschreibung|
|----------|-----------------|
|[CDaoTableDef::m_pDAOTableDef](#m_pdaotabledef)|Ein Zeiger auf die DAO-Schnittstelle, die dem Tabledef-Objekt zugrunde liegt.|
|[CDaoTableDef::m_pDatabase](#m_pdatabase)|Die Quelldatenbank für diese Tabelle.|

## <a name="remarks"></a>Hinweise

Jedes DAO-Datenbankobjekt verwaltet eine Sammlung namens Tabledefs, die alle gespeicherten DAO Tabledef-Objekte enthält.

Sie bearbeiten eine Tabellendefinition mit einem `CDaoTableDef`-Objekt. Sie haben unter anderem folgende Möglichkeiten:

- Untersuchen Sie die Feld-und Indexstruktur beliebiger lokaler, angefügter oder externer Tabellen in einer Datenbank.

- Nennen Sie die Funktionen `SetConnect` und `SetSourceTableName` Member für angefügte Tabellen, und verwenden Sie die Funktion `RefreshLink` Member, um Verbindungen mit angefügten Tabellen zu aktualisieren.

- Ruft die `CanUpdate` Member-Funktion auf, um zu bestimmen, ob Sie Feld Definitionen in der Tabelle bearbeiten können.

- Sie können Überprüfungs Bedingungen mithilfe der `GetValidationRule` und `SetValidationRule`sowie der Funktionen `GetValidationText` und `SetValidationText` Member erhalten oder festlegen.

- Verwenden Sie die `Open` Member-Funktion, um einen Table-, Dynaset-oder Snapshot-Type `CDaoRecordset`-Objekts zu erstellen.

    > [!NOTE]
    >  Die DAO-Datenbankklassen unterscheiden sich von der MFC-Datenbankklassen in Bezug auf Open Database Connectivity (ODBC). Alle DAO-Datenbank-Klassennamen haben das Präfix "CDao". Sie können weiterhin mit den DAO-Klassen auf ODBC-Datenquellen zugreifen. die DAO-Klassen bieten im allgemeinen überlegene Funktionen, da Sie für die Microsoft Jet-Datenbank-Engine spezifisch sind.

### <a name="to-use-tabledef-objects-either-to-work-with-an-existing-table-or-to-create-a-new-table"></a>So verwenden Sie Tabledef-Objekte entweder zum Arbeiten mit einer vorhandenen Tabelle oder zum Erstellen einer neuen Tabelle

1. Erstellen Sie in allen Fällen zuerst ein `CDaoTableDef` Objekt, und stellen Sie einen Zeiger auf ein [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) -Objekt bereit, zu dem die Tabelle gehört.

1. Führen Sie dann die folgenden Schritte aus, je nachdem, was Sie möchten:

   - Um eine vorhandene gespeicherte Tabelle zu verwenden, müssen Sie die [Open](#open) Member-Funktion des Tabledef-Objekts mit dem Namen der gespeicherten Tabelle abrufen.

   - Um eine neue Tabelle zu erstellen, rufen Sie die [Create](#create) Member-Funktion des Tabledef-Objekts auf und stellen den Namen der Tabelle bereit. Aufrufen von " [kreatefield](#createfield) " und " [kreateindex](#createindex) ", um der Tabelle Felder und Indizes hinzuzufügen.

   - Rufen Sie [Append](#append) auf, um die Tabelle zu speichern, indem Sie Sie an die TableDefs-Sammlung der Datenbank anhängen. `Create` versetzt die Tabledef in einen geöffneten Zustand, sodass Sie nach dem Aufrufen `Create` nicht `Open`aufrufen.

        > [!TIP]
        >  Die einfachste Möglichkeit zum Erstellen gespeicherter Tabellen besteht darin, Sie zu erstellen und in Ihrer Datenbank mithilfe von Microsoft Access zu speichern. Anschließend können Sie diese in Ihrem MFC-Code öffnen und verwenden.

Um das Tabledef-Objekt zu verwenden, das Sie geöffnet oder erstellt haben, erstellen Sie ein `CDaoRecordset` Objekt, und öffnen Sie es, indem Sie den Namen der Tabledef mit einem `dbOpenTable`-Wert im *nOpenType* -Parameter angeben.

Wenn Sie ein Tabledef-Objekt zum Erstellen eines `CDaoRecordset` Objekts verwenden möchten, erstellen oder öffnen Sie in der Regel eine Tabledef, wie oben beschrieben, und erstellen Sie dann ein Recordset-Objekt, und übergeben Sie einen Zeiger auf das Tabledef-Objekt, wenn Sie [CDaoRecordset:: Open](../../mfc/reference/cdaorecordset-class.md#open)aufgerufen haben. Die von Ihnen übergebene Tabledef muss sich in einem geöffneten Zustand befinden. Weitere Informationen finden Sie unter Class [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Wenn Sie die Verwendung eines Tabledef-Objekts abgeschlossen haben, müssen Sie dessen [Close](../../mfc/reference/cdaorecordset-class.md#close) Member-Funktion aufzurufen. zerstören Sie dann das Tabledef-Objekt.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CDaoTableDef`

## <a name="requirements"></a>Anforderungen

**Header:** afxdao.h

##  <a name="append"></a>CDaoTableDef:: Append

Rufen Sie diese Member-Funktion auf, nachdem Sie [Create](#create) aufgerufen haben, um ein neues Tabledef-Objekt zum Speichern der Tabledef in der Datenbank zu erstellen.

```
virtual void Append();
```

### <a name="remarks"></a>Hinweise

Die-Funktion fügt das-Objekt an die TableDefs-Auflistung der Datenbank an. Sie können Tabledef als temporäres Objekt verwenden, wenn Sie es nicht anhängen, aber wenn Sie es speichern und verwenden möchten, müssen Sie `Append`abrufen.

> [!NOTE]
>  Wenn Sie versuchen, eine unbenannte Tabledef anzufügen (die eine NULL-Zeichenfolge oder eine leere Zeichenfolge enthält), löst MFC eine Ausnahme aus.

Weitere Informationen finden Sie unter dem Thema "Fügen Sie der Methode" in-DAO-Hilfe.

##  <a name="canupdate"></a>CDaoTableDef:: CanUpdate

Mit dieser Member-Funktion können Sie ermitteln, ob die Definition der Tabelle, die einem `CDaoTableDef`-Objekt zugrunde liegt, geändert werden kann.

```
BOOL CanUpdate();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null), wenn die Tabellenstruktur (Schema) geändert werden kann (hinzufügen oder Löschen von Feldern und Indizes), andernfalls 0.

### <a name="remarks"></a>Hinweise

Standardmäßig kann eine neu erstellte Tabelle, die einem `CDaoTableDef` Objekt zugrunde liegt, aktualisiert werden, und eine angefügte Tabelle, die einem `CDaoTableDef` Objekt zugrunde liegt, kann nicht aktualisiert werden. Ein `CDaoTableDef` Objekt ist möglicherweise aktualisierbar, auch wenn das resultierende Recordset nicht aktualisierbar ist.

Weitere Informationen finden Sie im Thema "aktualisierbare Eigenschaft" in der DAO-Hilfe.

##  <a name="cdaotabledef"></a>CDaoTableDef:: CDaoTableDef

Erstellt ein `CDaoTableDef`-Objekt.

```
CDaoTableDef(CDaoDatabase* pDatabase);
```

### <a name="parameters"></a>Parameter

*pDatabase*<br/>
Ein Zeiger auf ein [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) -Objekt.

### <a name="remarks"></a>Hinweise

Nachdem Sie das-Objekt erstellt haben, müssen Sie die [Create](#create) -oder [Open](#open) Member-Funktion aufzurufen. Wenn Sie mit dem-Objekt fertig sind, müssen Sie die Funktion zum [Schließen](#close) des Members aufzurufen und das `CDaoTableDef` Objekt zerstören.

##  <a name="close"></a>CDaoTableDef:: Close

Mit dieser Member-Funktion können Sie das Tabledef-Objekt schließen und freigeben.

```
virtual void Close();
```

### <a name="remarks"></a>Hinweise

In der Regel nach dem Aufrufen von `Close`löschen Sie das Tabledef-Objekt, wenn es mit **New**zugeordnet wurde.

Sie können " [Öffnen](#open) " erneut aufrufen, nachdem Sie `Close`aufgerufen haben. Auf diese Weise können Sie das Tabledef-Objekt wieder verwenden.

Verwandte Informationen finden Sie im Thema "Close-Methode" in-DAO-Hilfe.

##  <a name="create"></a>CDaoTableDef:: Create

Rufen Sie diese Member-Funktion auf, um eine neue gespeicherte Tabelle zu erstellen.

```
virtual void Create(
    LPCTSTR lpszName,
    long lAttributes = 0,
    LPCTSTR lpszSrcTable = NULL,
    LPCTSTR lpszConnect = NULL);
```

### <a name="parameters"></a>Parameter

*Wert*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Namen der Tabelle enthält.

*lAttributes*<br/>
Ein-Wert, der den Merkmalen der Tabelle entspricht, die durch das Tabledef-Objekt dargestellt wird. Sie können den bitweisen OR-Operator verwenden, um eine der folgenden Konstanten zu kombinieren:

|Konstante|Beschreibung|
|--------------|-----------------|
|`dbAttachExclusive`|Gibt bei Datenbanken, die das Microsoft Jet-Datenbankmodul verwenden, an, dass die Tabelle eine angefügte Tabelle ist, die zur exklusiven Verwendung|
|`dbAttachSavePWD`|Gibt bei Datenbanken, die die Microsoft Jet-Datenbank-Engine verwenden, an, dass die Benutzer-ID und das Kennwort für die angefügte Tabelle mit den Verbindungsinformationen gespeichert werden.|
|`dbSystemObject`|Gibt an, dass die Tabelle eine von der Microsoft Jet-Datenbank-Engine bereitgestellte Systemtabelle ist.|
|`dbHiddenObject`|Gibt an, dass die Tabelle eine verborgene, von der Microsoft Jet-Datenbank-Engine bereitgestellte Tabelle ist.|

*lpszSrcTable*<br/>
Ein Zeiger auf eine Zeichenfolge, die den Quell Tabellennamen enthält. Standardmäßig wird dieser Wert als NULL initialisiert.

*lpszConnect*<br/>
Ein Zeiger auf eine Zeichenfolge, die die Standard Verbindungs Zeichenfolge enthält. Standardmäßig wird dieser Wert als NULL initialisiert.

### <a name="remarks"></a>Hinweise

Nachdem Sie die Tabledef benannt haben, können Sie " [Append](#append) " anrufen, um die Tabledef-Auflistung in der Tabledefs-Sammlung der Datenbank zu speichern. Nachdem Sie `Append`aufgerufen haben, befindet sich die Tabledef in einem geöffneten Zustand, und Sie können Sie verwenden, um ein [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekt zu erstellen.

Weitere Informationen finden Sie im Thema "Methode" der Methode "Methode" in der DAO-Hilfe.

##  <a name="createfield"></a>CDaoTableDef:: kreatefield

Diese Member-Funktion wird aufgerufen, um der Tabelle ein Feld hinzuzufügen.

```
void CreateField(
    LPCTSTR lpszName,
    short nType,
    long lSize,
    long lAttributes = 0);

void CreateField(CDaoFieldInfo& fieldinfo);
```

### <a name="parameters"></a>Parameter

*Wert*<br/>
Ein Zeiger auf einen Zeichen folgen Ausdruck, der den Namen dieses Felds angibt.

*nType*<br/>
Ein-Wert, der den Datentyp des Felds angibt. Die Einstellung kann einen der folgenden Werte aufweisen:

|Typ|Größe (Byte)|Beschreibung|
|----------|--------------------|-----------------|
|`dbBoolean`|1 Byte|BOOL|
|`dbByte`|BYTE|
|`dbInteger`|2|ssNoversion|
|`dbLong`|4|long|
|`dbCurrency`|8|Währung ( [COleCurrency](../../mfc/reference/colecurrency-class.md))|
|`dbSingle`|4|float|
|`dbDouble`|8|double|
|`dbDate`|8|Datum/Uhrzeit ( [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md))|
|`dbText`|1 - 255|Text ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|
|`dbLongBinary`|0|Long Binary (OLE-Objekt), [CLongBinary](../../mfc/reference/clongbinary-class.md) oder [CByteArray](../../mfc/reference/cbytearray-class.md)|
|`dbMemo`|0|Memo ( [CString](../../atl-mfc-shared/reference/cstringt-class.md))|

*lSize*<br/>
Ein Wert, der die maximale Größe (in Bytes) eines Felds angibt, das Text enthält, oder die festgelegte Größe eines Felds, das Text-oder numerische Werte enthält. Der *LSIZE* -Parameter wird nur für Textfelder ignoriert.

*lAttributes*<br/>
Ein-Wert, der den Merkmalen des Felds entspricht und mit einem bitweisen OR kombiniert werden kann.

|Konstante|Beschreibung|
|--------------|-----------------|
|`dbFixedField`|Die Feldgröße ist Fixed (Standardwert für numerische Felder).|
|`dbVariableField`|Die Feldgröße ist variabel (nur Text Felder).|
|`dbAutoIncrField`|Der Feldwert für neue Datensätze wird automatisch zu einer eindeutigen langen Ganzzahl erhöht, die nicht geändert werden kann. Wird nur für Microsoft Jet-Datenbanktabellen unterstützt.|
|`dbUpdatableField`|Der Feldwert kann geändert werden.|
|`dbDescending`|Das Feld wird in absteigender Reihenfolge (Z-A oder 100-0) sortiert (gilt nur für ein Feld Objekt in einer Fields-Auflistung eines Index Objekts). Wenn Sie diese Konstante weglassen, wird das Feld in aufsteigender Reihenfolge (A-Z oder 0-100) sortiert (Standard).|

*fieldinfo*<br/>
Ein Verweis auf eine [cdaofieldinfo](../../mfc/reference/cdaofieldinfo-structure.md) -Struktur.

### <a name="remarks"></a>Hinweise

Ein `DAOField` (OLE)-Objekt wird erstellt und an die Fields-Auflistung des OLE-Objekts (`DAOTableDef`) angehängt. Neben der Verwendung zum Untersuchen von Objekteigenschaften können Sie auch `CDaoFieldInfo` verwenden, um einen Eingabeparameter zum Erstellen neuer Felder in einer Tabledef zu erstellen. Die erste Version von `CreateField` ist einfacher zu verwenden, aber wenn Sie eine präzisere Kontrolle wünschen, können Sie die zweite Version von `CreateField`verwenden, die einen `CDaoFieldInfo`-Parameter annimmt.

Wenn Sie die-Version von `CreateField` verwenden, die einen `CDaoFieldInfo`-Parameter annimmt, müssen Sie jedes der folgenden Member der `CDaoFieldInfo` Struktur sorgfältig festlegen:

- `m_strName`

- `m_nType`

- `m_lSize`

- `m_lAttributes`

- `m_bAllowZeroLength`

Die übrigen Member `CDaoFieldInfo` sollten für den Member auf **0**, false oder eine leere Zeichenfolge festgelegt werden, oder es kann ein `CDaoException` auftreten.

Weitere Informationen finden Sie im Thema "Methode" in der DAO-Hilfe ".

##  <a name="createindex"></a>CDaoTableDef:: kreatandex

Mit dieser Funktion können Sie einer Tabelle einen Index hinzufügen.

```
void CreateIndex(CDaoIndexInfo& indexinfo);
```

### <a name="parameters"></a>Parameter

*indexinfo*<br/>
Ein Verweis auf eine [cdaoindexinfo](../../mfc/reference/cdaoindexinfo-structure.md) -Struktur.

### <a name="remarks"></a>Hinweise

Indizes geben die Reihenfolge der Datensätze an, auf die von Datenbanktabellen zugegriffen wird, und ob doppelte Datensätze akzeptiert werden. Indizes bieten außerdem effizienten Zugriff auf Daten.

Sie müssen keine Indizes für Tabellen erstellen, aber in großen, nicht indizierten Tabellen kann der Zugriff auf einen bestimmten Datensatz oder das Erstellen eines Recordsets viel Zeit in Anspruch nehmen. Wenn Sie jedoch zu viele Indizes erstellen, werden Update-, Anfüge-und Löschvorgänge verlangsamt, da alle Indizes automatisch aktualisiert werden. Berücksichtigen Sie diese Faktoren bei der Entscheidung, welche Indizes erstellt werden sollen.

Die folgenden Member der `CDaoIndexInfo` Struktur müssen festgelegt werden:

- `m_strName` muss ein Name angegeben werden.

- `m_pFieldInfos` muss auf ein Array mit `CDaoIndexFieldInfo` Strukturen zeigen.

- `m_nFields` muss die Anzahl der Felder im Array von `CDaoFieldInfo` Strukturen angeben.

Die übrigen Elemente werden ignoriert, wenn Sie auf false festgelegt sind. Außerdem wird der `m_lDistinctCount` Member beim Erstellen des Indexes ignoriert.

##  <a name="deletefield"></a>CDaoTableDef::D eletefield

Mit dieser Member-Funktion können Sie ein Feld entfernen und darauf nicht zugreifen.

```
void DeleteField(LPCTSTR lpszName);
void DeleteField(int nIndex);
```

### <a name="parameters"></a>Parameter

*Wert*<br/>
Ein Zeiger auf einen Zeichen folgen Ausdruck, bei dem es sich um den Namen eines vorhandenen Felds handelt.

*nIndex*<br/>
Der Index des Felds in der NULL basierten Felder Auflistung der Tabelle für die Suche nach Index.

### <a name="remarks"></a>Hinweise

Sie können diese Member-Funktion für ein neues Objekt verwenden, das nicht an die Datenbank angefügt wurde, oder wenn [CanUpdate](#canupdate) einen Wert ungleich 0 (null) zurückgibt.

Verwandte Informationen finden Sie im Thema "-Methode Delete" in-DAO-Hilfe.

##  <a name="deleteindex"></a>CDaoTableDef::D eletandex

Mit dieser Member-Funktion können Sie einen Index in einer zugrunde liegenden Tabelle löschen.

```
void DeleteIndex(LPCTSTR lpszName);
void DeleteIndex(int nIndex);
```

### <a name="parameters"></a>Parameter

*Wert*<br/>
Ein Zeiger auf einen Zeichen folgen Ausdruck, der den Namen eines vorhandenen Indexes ist.

*nIndex*<br/>
Der Array Index des Index Objekts in der NULL basierten TableDefs-Auflistung der Datenbank für die Suche nach Index.

### <a name="remarks"></a>Hinweise

Sie können diese Element Funktion für ein neues Objekt verwenden, das nicht an die Datenbank angefügt wurde, oder wenn [CanUpdate](#canupdate) einen Wert ungleich 0 (null) zurückgibt.

Verwandte Informationen finden Sie im Thema "-Methode Delete" in-DAO-Hilfe.

##  <a name="getattributes"></a>CDaoTableDef:: GetAttributes

Bei einem `CDaoTableDef` Objekt gibt der Rückgabewert Merkmale der Tabelle an, die durch das `CDaoTableDef`-Objekt dargestellt wird, und kann eine Summe dieser Konstanten sein:

```
long GetAttributes();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert zurück, der eine oder mehrere Eigenschaften eines `CDaoTableDef`-Objekts angibt.

### <a name="remarks"></a>Hinweise

|Konstante|Beschreibung|
|--------------|-----------------|
|`dbAttachExclusive`|Gibt bei Datenbanken, die das Microsoft Jet-Datenbankmodul verwenden, an, dass die Tabelle eine angefügte Tabelle ist, die zur exklusiven Verwendung|
|`dbAttachSavePWD`|Gibt bei Datenbanken, die die Microsoft Jet-Datenbank-Engine verwenden, an, dass die Benutzer-ID und das Kennwort für die angefügte Tabelle mit den Verbindungsinformationen gespeichert werden.|
|`dbSystemObject`|Gibt an, dass die Tabelle eine von der Microsoft Jet-Datenbank-Engine bereitgestellte Systemtabelle ist.|
|`dbHiddenObject`|Gibt an, dass die Tabelle eine verborgene, von der Microsoft Jet-Datenbank-Engine bereitgestellte Tabelle ist.|
|`dbAttachedTable`|Gibt an, dass die Tabelle eine angefügte Tabelle aus einer nicht-ODBC-Datenbank ist, z. b. eine Paradox-Datenbank.|
|`dbAttachedODBC`|Gibt an, dass die Tabelle eine angefügte Tabelle aus einer ODBC-Datenbank ist, z. b. Microsoft SQL Server.|

Eine Systemtabelle ist eine Tabelle, die von der Microsoft Jet-Datenbank-Engine erstellt wurde und verschiedene interne Informationen enthält.

Eine verborgene Tabelle ist eine Tabelle, die für die temporäre Verwendung durch die Microsoft Jet-Datenbank-Engine erstellt wurde.

Weitere Informationen finden Sie im Thema "Attribute-Eigenschaft" in der DAO-Hilfe.

##  <a name="getconnect"></a>CDaoTableDef:: GetConnect

Rufen Sie diese Member-Funktion auf, um die Verbindungs Zeichenfolge für eine Datenquelle abzurufen.

```
CString GetConnect();
```

### <a name="return-value"></a>Rückgabewert

Ein `CString`-Objekt, das den Pfad und den Datenbanktyp für die Tabelle enthält.

### <a name="remarks"></a>Hinweise

Für ein `CDaoTableDef` Objekt, das eine angefügte Tabelle darstellt, besteht das `CString` Objekt aus einem oder zwei Teilen (einem Dateityp Spezifizierer und einem Pfad zur Datenbank).

Der Pfad, wie in der folgenden Tabelle gezeigt, ist der vollständige Pfad für das Verzeichnis, das die Datenbankdateien enthält, und dem Bezeichner "Database =" muss vorangestellt sein. In einigen Fällen (wie bei Microsoft Jet und Microsoft Excel-Datenbanken) ist ein bestimmter Dateiname im Daten Bank Pfad Argument enthalten.

Die Tabelle in [CDaoTableDef:: SetConnect](#setconnect) zeigt mögliche Datenbanktypen und ihre entsprechenden datenbankspezifizierern und Pfade an:

Bei Microsoft Jet-Datenbank-Basistabellen ist der Spezifizierer eine leere Zeichenfolge ("").

Wenn ein Kennwort erforderlich ist, aber nicht angegeben ist, zeigt der ODBC-Treiber beim ersten Zugriff auf eine Tabelle ein Anmelde Dialogfeld an, wenn die Verbindung geschlossen und erneut geöffnet wird. Wenn eine angefügte Tabelle über das `dbAttachSavePWD`-Attribut verfügt, wird die Anmeldeaufforderung beim erneuten Öffnen der Tabelle nicht angezeigt.

Weitere Informationen finden Sie im Thema "Connect Property" in der DAO-Hilfe.

##  <a name="getdatecreated"></a>CDaoTableDef:: getdatecreated

Mit dieser Funktion können Sie das Datum und die Uhrzeit der Erstellung der Tabelle ermitteln, die dem `CDaoTableDef` Objekt zugrunde liegt.

```
COleDateTime GetDateCreated();
```

### <a name="return-value"></a>Rückgabewert

Ein-Wert, der das Datum und die Uhrzeit der Erstellung der Tabelle enthält, die dem `CDaoTableDef`-Objekt zugrunde liegt.

### <a name="remarks"></a>Hinweise

Die Datums-und Uhrzeit Einstellungen werden von dem Computer abgeleitet, auf dem die Basistabelle erstellt oder zuletzt aktualisiert wurde. In einer mehr Benutzerumgebung sollten die Benutzer diese Einstellungen direkt vom Dateiserver erhalten, um Abweichungen zu vermeiden. Das heißt, dass alle Clients eine "Standard"-Zeit Quelle verwenden sollten – vielleicht von einem Server.

Weitere Informationen finden Sie im Thema "DateCreated, lastupated Properties" in der DAO-Hilfe.

##  <a name="getdatelastupdated"></a>CDaoTableDef:: getdatelastupveraltet

Mit dieser Funktion können Sie das Datum und die Uhrzeit des letzten Updates der Tabelle ermitteln, die dem `CDaoTableDef` Objekt zugrunde liegt.

```
COleDateTime GetDateLastUpdated();
```

### <a name="return-value"></a>Rückgabewert

Ein-Wert, der das Datum und die Uhrzeit der letzten Aktualisierung der Tabelle enthält, die dem `CDaoTableDef` Objekt zugrunde liegt.

### <a name="remarks"></a>Hinweise

Die Datums-und Uhrzeit Einstellungen werden von dem Computer abgeleitet, auf dem die Basistabelle erstellt oder zuletzt aktualisiert wurde. In einer mehr Benutzerumgebung sollten die Benutzer diese Einstellungen direkt vom Dateiserver erhalten, um Abweichungen zu vermeiden. Das heißt, dass alle Clients eine "Standard"-Zeit Quelle verwenden sollten – vielleicht von einem Server.

Weitere Informationen finden Sie im Thema "DateCreated, lastupated Properties" in der DAO-Hilfe.

##  <a name="getfieldcount"></a>CDaoTableDef:: GetFieldCount

Rufen Sie diese Member-Funktion auf, um die in der Tabelle definierte Anzahl von Feldern abzurufen.

```
short GetFieldCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Felder in der Tabelle.

### <a name="remarks"></a>Hinweise

Wenn der Wert 0 ist, sind keine Objekte in der Auflistung vorhanden.

Weitere Informationen finden Sie im Thema "count Property" in der DAO-Hilfe.

##  <a name="getfieldinfo"></a>CDaoTableDef:: getfieldinfo

Rufen Sie diese Member-Funktion auf, um verschiedene Arten von Informationen zu einem Feld abzurufen, das in der Tabledef definiert ist.

```
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
Der Index des Feld Objekts in der NULL basierten Feld Auflistung der Tabelle für die Suche nach Index.

*fieldinfo*<br/>
Ein Verweis auf eine [cdaofieldinfo](../../mfc/reference/cdaofieldinfo-structure.md) -Struktur.

*dwInfoOptions*<br/>
Optionen, die angeben, welche Informationen über das Feld abgerufen werden sollen. Die verfügbaren Optionen sind hier aufgeführt, zusammen mit der sie die Funktion zurückgibt verursachen:

- `AFX_DAO_PRIMARY_INFO` (Standard) Name, Typ, Größe, Attribute. Verwenden Sie diese Option für die schnellste Leistung.

- `AFX_DAO_SECONDARY_INFO` primäre Informationen Plus: Ordinalposition, erforderlich, Null Länge zulassen, Sortierreihenfolge, fremd Name, Quellfeld, Quell Tabelle

- `AFX_DAO_ALL_INFO` primäre und sekundäre Informationen, plus: Validierungs Regel, Validierungs Text, Standardwert

*Wert*<br/>
Ein Zeiger auf den Namen des Feld Objekts für die Suche nach Namen. Der Name ist eine Zeichenfolge mit bis zu 64 Zeichen, die das Feld eindeutig benennen.

### <a name="remarks"></a>Hinweise

Eine Version der-Funktion ermöglicht es Ihnen, ein Feld nach Index zu suchen. Mit der anderen Version können Sie nach einem Feld nach dem Namen suchen.

Eine Beschreibung der zurückgegebenen Informationen finden Sie in der [cdaofieldinfo](../../mfc/reference/cdaofieldinfo-structure.md) -Struktur. Diese Struktur hat Member, die die Elemente in der Beschreibung der oben aufgeführten Informationen entsprechen *DwInfoOptions*. Wenn Sie die Informationen auf einer Ebene anfordern, erhalten Sie Informationen für alle vorherigen Ebenen sowie an.

Weitere Informationen finden Sie im Thema "Attribute-Eigenschaft" in der DAO-Hilfe.

##  <a name="getindexcount"></a>CDaoTableDef:: GetIndexCount

Mit dieser Member-Funktion können Sie die Anzahl der Indizes für eine Tabelle abrufen.

```
short GetIndexCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Indizes für die Tabelle.

### <a name="remarks"></a>Hinweise

Wenn der Wert 0 ist, sind in der Auflistung keine Indizes vorhanden.

Weitere Informationen finden Sie im Thema "count Property" in der DAO-Hilfe.

##  <a name="getindexinfo"></a>CDaoTableDef:: getIndexInfo

Mit dieser Member-Funktion können Sie verschiedene Arten von Informationen über einen in der Tabledef definierten Index abrufen.

```
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
Der numerische Index des Index Objekts in der Auflistung der NULL basierten Indizes der Tabelle für die Suche nach der Position in der Auflistung.

*indexinfo*<br/>
Ein Verweis auf eine [cdaoindexinfo](../../mfc/reference/cdaoindexinfo-structure.md) -Struktur.

*dwInfoOptions*<br/>
Optionen, die angeben, welche Informationen über den Index abgerufen werden sollen. Die verfügbaren Optionen sind hier aufgeführt, zusammen mit der sie die Funktion zurückgibt verursachen:

- `AFX_DAO_PRIMARY_INFO` Name, Feld Info, Felder. Verwenden Sie diese Option für die schnellste Leistung.

- `AFX_DAO_SECONDARY_INFO` primäre Informationen Plus: Primary, Unique, Clustered, IGNORE NULLS, required, Foreign

- `AFX_DAO_ALL_INFO` primäre und sekundäre Informationen, plus: Distinct Count

*Wert*<br/>
Ein Zeiger auf den Namen des Index Objekts für die Suche nach Namen.

### <a name="remarks"></a>Hinweise

Eine Version der-Funktion ermöglicht es Ihnen, einen Index nach seiner Position in der Auflistung zu suchen. Mit der anderen Version können Sie einen Index nach Namen suchen.

Eine Beschreibung der zurückgegebenen Informationen finden Sie in der [cdaoindexinfo](../../mfc/reference/cdaoindexinfo-structure.md) -Struktur. Diese Struktur hat Member, die die Elemente in der Beschreibung der oben aufgeführten Informationen entsprechen *DwInfoOptions*. Wenn Sie die Informationen auf einer Ebene anfordern, erhalten Sie Informationen für alle vorherigen Ebenen sowie an.

Weitere Informationen finden Sie im Thema "Attribute-Eigenschaft" in der DAO-Hilfe.

##  <a name="getname"></a>CDaoTableDef:: GetName

Rufen Sie diese Member-Funktion auf, um den benutzerdefinierten Namen der zugrunde liegenden Tabelle abzurufen.

```
CString GetName();
```

### <a name="return-value"></a>Rückgabewert

Ein benutzerdefinierter Name für eine Tabelle.

### <a name="remarks"></a>Hinweise

Dieser Name beginnt mit einem Buchstaben und kann maximal 64 Zeichen enthalten. Er kann Zahlen enthalten und Unterstrich-Zeichen, aber keine Interpunktionszeichen oder Leerzeichen enthalten.

Verwandte Informationen finden Sie im Thema "Name-Eigenschaft" in-DAO-Hilfe.

##  <a name="getrecordcount"></a>CDaoTableDef:: GetRecordCount

Mit dieser Member-Funktion können Sie feststellen, wie viele Datensätze in einem `CDaoTableDef` Objekt enthalten sind.

```
long GetRecordCount();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Einträge, auf die in einem Tabledef-Objekt zugegriffen wird.

### <a name="remarks"></a>Hinweise

Das Aufrufen von `GetRecordCount` für einen Tabellentyp `CDaoTableDef` Objekts spiegelt die ungefähre Anzahl von Datensätzen in der Tabelle wider und ist sofort betroffen, wenn Tabellendaten Sätze hinzugefügt und gelöscht werden. Ein Rollback von Transaktionen wird als Teil der Daten Satz Anzahl angezeigt, bis Sie [CDaoWorkspace:: CompactDatabase](../../mfc/reference/cdaoworkspace-class.md#compactdatabase)aufgerufen haben. Ein `CDaoTableDef`-Objekt ohne Datensätze hat eine Einstellung für die Daten Satz Anzahl von 0. Beim Arbeiten mit angefügten Tabellen oder ODBC-Datenbanken gibt `GetRecordCount` immer-1 zurück.

Weitere Informationen finden Sie im Thema "RecordCount-Eigenschaft" in der DAO-Hilfe.

##  <a name="getsourcetablename"></a>CDaoTableDef:: getsourcetablename

Rufen Sie diese Member-Funktion auf, um den Namen einer angefügten Tabelle in einer Quelldatenbank abzurufen.

```
CString GetSourceTableName();
```

### <a name="return-value"></a>Rückgabewert

Ein `CString`-Objekt, das den Quellnamen einer angefügten Tabelle angibt, oder eine leere Zeichenfolge, wenn es sich um eine systemeigene Datentabelle handelt.

### <a name="remarks"></a>Hinweise

Eine angefügte Tabelle ist eine Tabelle in einer anderen Datenbank, die mit einer Microsoft Jet-Datenbank verknüpft ist. Die Daten für angefügte Tabellen verbleiben in der externen Datenbank, wo Sie von anderen Anwendungen bearbeitet werden kann.

Weitere Informationen finden Sie im Thema "SourceTableName Property" in der DAO-Hilfe.

##  <a name="getvalidationrule"></a>CDaoTableDef:: getvalidationrule

Rufen Sie diese Member-Funktion auf, um die Validierungs Regel für eine Tabledef abzurufen.

```
CString GetValidationRule();
```

### <a name="return-value"></a>Rückgabewert

Ein `CString` Objekt, das die Daten in einem Feld überprüft, wenn es geändert oder einer Tabelle hinzugefügt wird.

### <a name="remarks"></a>Hinweise

Validierungsregeln werden in Verbindung mit Update Vorgängen verwendet. Wenn eine Tabledef eine Validierungs Regel enthält, müssen die Updates an dieser Tabledef-Datei mit den vordefinierten Kriterien übereinstimmen, bevor die Daten geändert werden. Wenn die Änderung nicht mit den Kriterien übereinstimmt, wird eine Ausnahme ausgelöst, die den Wert von [getvalidationtext](#getvalidationtext) enthält. Für ein `CDaoTableDef` Objekt ist diese `CString` für eine angefügte Tabelle schreibgeschützt und für eine Basistabelle Lese-/Schreibzugriff.

Weitere Informationen finden Sie im Thema "ValidationRule Property" in der DAO-Hilfe.

##  <a name="getvalidationtext"></a>CDaoTableDef:: getvalidationtext

Mit dieser Funktion rufen Sie die Zeichenfolge ab, die angezeigt wird, wenn ein Benutzerdaten eingibt, die nicht mit der Validierungs Regel identisch sind.

```
CString GetValidationText();
```

### <a name="return-value"></a>Rückgabewert

Ein `CString`-Objekt, das den Text angibt, der angezeigt wird, wenn der Benutzerdaten eingibt, die nicht der Validierungs Regel entsprechen.

### <a name="remarks"></a>Hinweise

Für ein `CDaoTableDef` Objekt ist diese `CString` für eine angefügte Tabelle schreibgeschützt und für eine Basistabelle Lese-/Schreibzugriff.

Weitere Informationen finden Sie im Thema "ValidationText Property" in der DAO-Hilfe.

##  <a name="isopen"></a>CDaoTableDef:: IsOpen

Mit dieser Member-Funktion können Sie ermitteln, ob das `CDaoTableDef` Objekt derzeit geöffnet ist.

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das `CDaoTableDef` Objekt geöffnet ist. andernfalls 0.

### <a name="remarks"></a>Hinweise

##  <a name="m_pdatabase"></a>CDaoTableDef:: m_pDatabase

Enthält einen Zeiger auf das [CDaoDatabase](../../mfc/reference/cdaodatabase-class.md) -Objekt für diese Tabelle.

### <a name="remarks"></a>Hinweise

##  <a name="m_pdaotabledef"></a>CDaoTableDef:: m_pDAOTableDef

Enthält einen Zeiger auf die OLE-Schnittstelle für das DAO Tabledef-Objekt, das dem `CDaoTableDef`-Objekt zugrunde liegt.

### <a name="remarks"></a>Hinweise

Verwenden Sie diesen Zeiger, wenn Sie die DAO-Schnittstelle direkt zugreifen möchten.

##  <a name="open"></a>CDaoTableDef:: Open

Mit dieser Member-Funktion Öffnen Sie eine Tabledef, die zuvor in der tabledefes-Auflistung der Datenbank gespeichert wurde.

```
virtual void Open(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*Wert*<br/>
Ein Zeiger auf eine Zeichenfolge, die einen Tabellennamen angibt.

### <a name="remarks"></a>Hinweise

##  <a name="refreshlink"></a>CDaoTableDef:: erfrischendes Link

Mit dieser Member-Funktion können Sie die Verbindungsinformationen für eine angefügte Tabelle aktualisieren.

```
void RefreshLink();
```

### <a name="remarks"></a>Hinweise

Sie ändern die Verbindungsinformationen für eine angefügte Tabelle, indem Sie [SetConnect](#setconnect) für das entsprechende `CDaoTableDef` Objekt aufrufen und dann die `RefreshLink` Member-Funktion verwenden, um die Informationen zu aktualisieren. Wenn Sie `RefreshLink`aufgerufen haben, werden die Eigenschaften der angefügten Tabelle nicht geändert.

Um zu erzwingen, dass die geänderten Verbindungsinformationen wirksam werden, müssen alle geöffneten [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md) -Objekte, die auf dieser Tabledef basieren, geschlossen werden.

Weitere Informationen finden Sie in der DAO-Hilfe unter dem Thema "aktudie Methode zum auffallen verknüpfen".

##  <a name="setattributes"></a>CDaoTableDef:: antattributes

Legt einen Wert fest, der eine oder mehrere Eigenschaften eines `CDaoTableDef`-Objekts angibt.

```
void SetAttributes(long lAttributes);
```

### <a name="parameters"></a>Parameter

*lAttributes*<br/>
Merkmale der durch das `CDaoTableDef`-Objekt dargestellten Tabelle und können eine Summe dieser Konstanten sein:

|Konstante|Beschreibung|
|--------------|-----------------|
|`dbAttachExclusive`|Gibt bei Datenbanken, die das Microsoft Jet-Datenbankmodul verwenden, an, dass die Tabelle eine angefügte Tabelle ist, die zur exklusiven Verwendung|
|`dbAttachSavePWD`|Gibt bei Datenbanken, die die Microsoft Jet-Datenbank-Engine verwenden, an, dass die Benutzer-ID und das Kennwort für die angefügte Tabelle mit den Verbindungsinformationen gespeichert werden.|
|`dbSystemObject`|Gibt an, dass die Tabelle eine von der Microsoft Jet-Datenbank-Engine bereitgestellte Systemtabelle ist.|
|`dbHiddenObject`|Gibt an, dass die Tabelle eine verborgene, von der Microsoft Jet-Datenbank-Engine bereitgestellte Tabelle ist.|

### <a name="remarks"></a>Hinweise

Beim Festlegen mehrerer Attribute können Sie diese kombinieren, indem Sie die entsprechenden Konstanten mithilfe des bitweisen OR-Operators addieren. Beim Festlegen von `dbAttachExclusive` für eine nicht angefügte Tabelle wird eine Ausnahme ausgelöst. Die Kombination der folgenden Werte erzeugt außerdem eine Ausnahme:

- **dbAttachExclusive &#124; dbAttachedODBC**

- **dbAttachSavePWD &#124; dbAttachedTable**

Weitere Informationen finden Sie im Thema "Attribute-Eigenschaft" in der DAO-Hilfe.

##  <a name="setconnect"></a>CDaoTableDef:: SetConnect

Für ein `CDaoTableDef` Objekt, das eine angefügte Tabelle darstellt, besteht das Zeichen folgen Objekt aus einem oder zwei Teilen (einem Dateityp Spezifizierer und einem Pfad zur Datenbank).

```
void SetConnect(LPCTSTR lpszConnect);
```

### <a name="parameters"></a>Parameter

*lpszConnect*<br/>
Ein Zeiger auf einen Zeichen folgen Ausdruck, der zusätzliche Parameter angibt, die an ODBC-oder installierbare ISAM-Treiber übergeben werden.

### <a name="remarks"></a>Hinweise

Der Pfad, wie in der folgenden Tabelle gezeigt, ist der vollständige Pfad für das Verzeichnis, das die Datenbankdateien enthält, und dem Bezeichner "Database =" muss vorangestellt sein. In einigen Fällen (wie bei Microsoft Jet und Microsoft Excel-Datenbanken) ist ein bestimmter Dateiname im Daten Bank Pfad Argument enthalten.

> [!NOTE]
>  Fügen Sie die Anweisungen für den Gleichheits Anmelde Pfad in der Form "Database = Drive:\\\path" nicht in Leerzeichen ein. Dies führt dazu, dass eine Ausnahme ausgelöst und die Verbindung nicht hergestellt werden kann.

In der folgenden Tabelle werden mögliche Datenbanktypen und ihre entsprechenden datenbankspezifizierern und Pfade angezeigt:

|Datenbanktyp|Bezeichner|Pfad|
|-------------------|---------------|----------|
|Datenbank mithilfe der Jet-Datenbank-Engine|"[ `database`];"|"`drive`:\\\ *Pfad*\\\ *Dateiname*. Erfasst|
|dBASE III|"dBASE III;"|"`drive`:\\\ *Pfad*"|
|dBASE-IV|"dBASE IV;"|"`drive`:\\\ *Pfad*"|
|dBASE 5|"dBASE 5,0;"|"`drive`:\\\ *Pfad*"|
|Paradox 3. x|"Paradox 3. x;"|"`drive`:\\\ *Pfad*"|
|Paradox 4. x|"Paradox 4. x;"|"`drive`:\\\ *Pfad*"|
|Paradox 5. x|"Paradox 5. x;"|"`drive`:\\\ *Pfad*"|
|Excel 3,0|"Excel 3,0;"|"`drive`:\\\ *Pfad*\\\ *Dateiname*. XLS|
|Excel 4,0|"Excel 4,0;"|"`drive`:\\\ *Pfad*\\\ *Dateiname*. XLS|
|Excel 5,0 oder Excel 95|"Excel 5,0;"|"`drive`:\\\ *Pfad*\\\ *Dateiname*. XLS|
|Excel 97|"Excel 8,0;"|"`drive`:\\\ *Pfad*\ *filename*. XLS|
|HTML-Import|"HTML-Import;"|"`drive`:\\\ *Pfad*\ *Dateiname*"|
|HTML-Export|"HTML-Export;"|"`drive`:\\\ *Pfad*"|
|Text|"Text;"|"Laufwerk:\\\Pfad"|
|ODBC|ODBC Database = `database`; UID = *Benutzer*; Pwd = *Kennwort*; DSN = *DataSourceName;* LoginTimeout = *Sekunden;* " (Dies ist möglicherweise keine vollständige Verbindungs Zeichenfolge für alle Server, sondern nur ein Beispiel. Es ist sehr wichtig, dass keine Leerzeichen zwischen den Parametern vorhanden sind.)|Keine|
|Exchange|Schlag<br /><br /> Mapilevel = *folderPath*;<br /><br /> [TABLETYPE={ 0 &#124; 1 };]<br /><br /> [Profil = *Profil*;]<br /><br /> [Pwd = *Kennwort*;]<br /><br /> [DATABASE = `database`;] "|*"Laufwerk*:\\\ *Pfad*\\\ *Dateiname*. Erfasst|

> [!NOTE]
>  Btrieve wird ab DAO 3,5 nicht mehr unterstützt.

Sie müssen einen doppelten umgekehrten Schrägstrich (\\\\) in den Verbindungs Zeichenfolgen verwenden. Wenn Sie die Eigenschaften einer vorhandenen Verbindung mithilfe von `SetConnect`geändert haben, müssen Sie anschließend " [aktuaselink](#refreshlink)" aufzurufen. Wenn Sie die Verbindungs Eigenschaften mit `SetConnect`initialisieren, müssen Sie nicht `RefreshLink`anrufen, aber wenn Sie sich dafür entscheiden, müssen Sie zuerst den Tabledef anfügen.

Wenn ein Kennwort erforderlich ist, aber nicht angegeben ist, zeigt der ODBC-Treiber beim ersten Zugriff auf eine Tabelle ein Anmelde Dialogfeld an, wenn die Verbindung geschlossen und erneut geöffnet wird.

Sie können die Verbindungs Zeichenfolge für ein `CDaoTableDef` Objekt festlegen, indem Sie ein Quell Argument für die `Create` Member-Funktion bereitstellen. Sie können die Einstellung überprüfen, um den Typ, den Pfad, die Benutzer-ID, das Kennwort oder die ODBC-Datenquelle der Datenbank zu bestimmen. Weitere Informationen finden Sie in der Dokumentation des jeweiligen Treibers.

Weitere Informationen finden Sie im Thema "Connect Property" in der DAO-Hilfe.

##  <a name="setname"></a>CDaoTableDef:: SetName

Mit dieser Member-Funktion können Sie einen benutzerdefinierten Namen für eine Tabelle festlegen.

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>Parameter

*Wert*<br/>
Ein Zeiger auf einen Zeichen folgen Ausdruck, der einen Namen für eine Tabelle angibt.

### <a name="remarks"></a>Hinweise

Der Name muss mit einem Buchstaben beginnen und darf maximal 64 Zeichen enthalten. Er kann Zahlen enthalten und Unterstrich-Zeichen, aber keine Interpunktionszeichen oder Leerzeichen enthalten.

Verwandte Informationen finden Sie im Thema "Name-Eigenschaft" in-DAO-Hilfe.

##  <a name="setsourcetablename"></a>CDaoTableDef:: SetSourceTableName

Mit dieser Member-Funktion können Sie den Namen einer angefügten Tabelle oder den Namen der Basistabelle angeben, auf der das `CDaoTableDef` Objekt basiert, da es in der ursprünglichen Datenquelle vorhanden ist.

```
void SetSourceTableName(LPCTSTR lpszSrcTableName);
```

### <a name="parameters"></a>Parameter

*lpszSrcTableName*<br/>
Ein Zeiger auf einen Zeichen folgen Ausdruck, der einen Tabellennamen in der externen Datenbank angibt. Bei einer Basistabelle ist die Einstellung eine leere Zeichenfolge ("").

### <a name="remarks"></a>Hinweise

Sie müssen dann "[aktusaktuslink](#refreshlink)" anrufen. Diese Eigenschafts Einstellung ist für eine Basistabelle leer und Lese-/Schreibzugriff für eine angefügte Tabelle oder ein Objekt, das nicht an eine Auflistung angehängt ist.

Weitere Informationen finden Sie im Thema "SourceTableName Property" in der DAO-Hilfe.

##  <a name="setvalidationrule"></a>CDaoTableDef:: SetValidationRule

Mit dieser Member-Funktion können Sie eine Validierungs Regel für eine Tabledef festlegen.

```
void SetValidationRule(LPCTSTR lpszValidationRule);
```

### <a name="parameters"></a>Parameter

*lpszValidationRule*<br/>
Ein Zeiger auf einen Zeichen folgen Ausdruck, der einen Vorgang überprüft.

### <a name="remarks"></a>Hinweise

Validierungsregeln werden in Verbindung mit Update Vorgängen verwendet. Wenn eine Tabledef eine Validierungs Regel enthält, müssen die Updates an dieser Tabledef-Datei mit den vordefinierten Kriterien übereinstimmen, bevor die Daten geändert werden. Wenn die Änderung nicht mit den Kriterien übereinstimmt, wird eine Ausnahme mit dem Text von [getvalidationtext](#getvalidationtext) angezeigt.

Die Validierung wird nur für Datenbanken unterstützt, die die Microsoft Jet-Datenbank-Engine verwenden. Der Ausdruck kann nicht auf benutzerdefinierte Funktionen, Domänen Aggregatfunktionen, SQL-Aggregatfunktionen oder Abfragen verweisen. Eine Validierungs Regel für ein `CDaoTableDef` Objekt kann auf mehrere Felder in diesem Objekt verweisen.

Beispielsweise kann für Felder namens *hire_date* und *termination_date*eine Validierungs Regel wie folgt lauten:

[!code-cpp[NVC_MFCDatabase#34](../../mfc/codesnippet/cpp/cdaotabledef-class_1.cpp)]

Weitere Informationen finden Sie im Thema "ValidationRule Property" in der DAO-Hilfe.

##  <a name="setvalidationtext"></a>CDaoTableDef:: SetValidationText

Mit dieser Member-Funktion wird der Ausnahme Text einer Validierungs Regel für ein `CDaoTableDef` Objekt mit einer zugrunde liegenden Basistabelle festgelegt, die von der Microsoft Jet-Datenbank-Engine unterstützt wird.

```
void SetValidationText(LPCTSTR lpszValidationText);
```

### <a name="parameters"></a>Parameter

*lpszValidationText*<br/>
Ein Zeiger auf einen Zeichen folgen Ausdruck, der den Text angibt, der angezeigt wird, wenn die eingegebenen Daten ungültig sind.

### <a name="remarks"></a>Hinweise

Sie können den Validierungs Text einer angefügten Tabelle nicht festlegen.

Weitere Informationen finden Sie im Thema "ValidationText Property" in der DAO-Hilfe.

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase-Klasse](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset-Klasse](../../mfc/reference/cdaorecordset-class.md)

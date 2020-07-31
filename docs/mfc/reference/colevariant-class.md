---
title: COleVariant-Klasse
ms.date: 11/04/2016
f1_keywords:
- COleVariant
- AFXDISP/COleVariant
- AFXDISP/COleVariant::COleVariant
- AFXDISP/COleVariant::Attach
- AFXDISP/COleVariant::ChangeType
- AFXDISP/COleVariant::Clear
- AFXDISP/COleVariant::Detach
- AFXDISP/COleVariant::GetByteArrayFromVariantArray
- AFXDISP/COleVariant::SetString
helpviewer_keywords:
- COleVariant [MFC], COleVariant
- COleVariant [MFC], Attach
- COleVariant [MFC], ChangeType
- COleVariant [MFC], Clear
- COleVariant [MFC], Detach
- COleVariant [MFC], GetByteArrayFromVariantArray
- COleVariant [MFC], SetString
ms.assetid: e1b5cd4a-b066-4b9b-b48b-6215ed52d998
ms.openlocfilehash: 63bce4695e4e1142b797f24cfbbae71638177d04
ms.sourcegitcommit: 13f42c339fb7af935e3a93ac80e350d5e784c9f1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2020
ms.locfileid: "87470900"
---
# <a name="colevariant-class"></a>COleVariant-Klasse

Kapselt den Datentyp [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) .

## <a name="syntax"></a>Syntax

```
class COleVariant : public tagVARIANT
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleVariant:: COleVariant](#colevariant)|Erstellt ein `COleVariant`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[COleVariant:: Attach](#attach)|Fügt eine Variante an einen an `COleVariant` .|
|[COleVariant:: ChangeType](#changetype)|Ändert den Varianttyp dieses `COleVariant` Objekts.|
|[COleVariant:: Clear](#clear)|Löscht dieses `COleVariant`-Objekt.|
|[COleVariant::D Etach](#detach)|Trennt eine Variante von einem `COleVariant` und gibt die Variante zurück.|
|[COleVariant:: getbytearrayfromvariantarray](#getbytearrayfromvariantarray)|Ruft ein Bytearray aus einem vorhandenen Variant-Array ab.|
|[COleVariant:: SetString](#setstring)|Legt die Zeichenfolge auf einen bestimmten Typ fest, normalerweise ANSI.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleVariant:: Operator lpcvariant](#operator_lpcvariant)|Konvertiert einen `COleVariant` Wert in einen `LPCVARIANT` .|
|[COleVariant:: Operator lpvariant](#operator_lpvariant)|Konvertiert ein- `COleVariant` Objekt in ein-Objekt `LPVARIANT` .|
|[COleVariant:: Operator =](#operator_eq)|Kopiert einen `COleVariant` Wert.|
|[COleVariant:: Operator = =](#operator_eq_eq)|Vergleicht zwei `COleVariant` Werte.|
|[COleVariant::-Operator &lt; &lt; ,&gt;&gt;](#operator_lt_lt__gt_gt)|Gibt einen `COleVariant` Wert für `CArchive` oder `CDumpContext` aus und gibt ein- `COleVariant` Objekt aus `CArchive` .|

## <a name="remarks"></a>Hinweise

Dieser Datentyp wird in der OLE-Automatisierung verwendet. Die [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams) -Struktur enthält insbesondere einen Zeiger auf ein Array von Variant-Strukturen. Eine- `DISPPARAMS` Struktur wird verwendet, um Parameter an [IDispatch:: Aufrufen](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)zu übergeben.

> [!NOTE]
> Diese Klasse wird von der- `VARIANT` Struktur abgeleitet. Dies bedeutet, dass Sie ein `COleVariant` -Element in einem Parameter übergeben können, der einen aufruft `VARIANT` und auf die Datenmember der-Struktur zugreifen können `VARIANT` `COleVariant` .

Die beiden verwandten MFC-Klassen [COleCurrency](../../mfc/reference/colecurrency-class.md) und [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) Kapseln die Varianten Datentypen Currency ( `VT_CY` ) und Date ( `VT_DATE` ). Die- `COleVariant` Klasse wird in den DAO-Klassen ausgiebig verwendet. diese Klassen finden Sie in der typischen Verwendung dieser Klasse, z. b. [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) und [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Weitere Informationen finden Sie in den Einträgen " [Variant](/windows/win32/api/oaidl/ns-oaidl-variant)", " [Currency](/windows/win32/api/wtypes/ns-wtypes-cy-r1)", " [disppara AMS](/windows/win32/api/oaidl/ns-oaidl-dispparams)" und " [IDispatch:: Aufrufen](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) " in der Windows SDK.

Weitere Informationen zur `COleVariant` -Klasse und deren Verwendung in der OLE-Automatisierung finden Sie unter "übergeben von Parametern in der OLE-Automatisierung" im Artikel [Automation](../../mfc/automation.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="colevariantattach"></a><a name="attach"></a>COleVariant:: Attach

Diese Funktion wird aufgerufen, um das angegebene [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) -Objekt an das aktuelle-Objekt anzufügen `COleVariant` .

```cpp
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Parameter

*varSrc*<br/>
Ein vorhandenes- `VARIANT` Objekt, das dem aktuellen-Objekt angefügt werden soll `COleVariant` .

### <a name="remarks"></a>Hinweise

Diese Funktion legt den VarType von *varSrc* auf VT_EMPTY fest.

Weitere Informationen finden Sie in den [Variablen "Variant](/windows/win32/api/oaidl/ns-oaidl-variant) " und " [VarEnum](/windows/win32/api/wtypes/ne-wtypes-varenum) " in der Windows SDK.

## <a name="colevariantcolevariant"></a><a name="colevariant"></a>COleVariant:: COleVariant

Erstellt ein `COleVariant`-Objekt.

```
COleVariant();
COleVariant(const VARIANT& varSrc);
COleVariant(const COleVariant& varSrc);
COleVariant(LPCVARIANT pSrc);
COleVariant(LPCTSTR lpszSrc);
COleVariant(LPCTSTR lpszSrc, VARTYPE vtSrc);
COleVariant(CString& strSrc);
COleVariant(BYTE nSrc);
COleVariant(short nSrc, VARTYPE vtSrc = VT_I2);
COleVariant(long lSrc,VARTYPE vtSrc = VT_I4);
COleVariant(const COleCurrency& curSrc);
COleVariant(float fltSrc);
COleVariant(double dblSrc);
COleVariant(const COleDateTime& timeSrc);
COleVariant(const CByteArray& arrSrc);
COleVariant(const CLongBinary& lbSrc);
COleVariant(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>Parameter

*varSrc*<br/>
Ein vorhandenes- `COleVariant` oder- `VARIANT` Objekt, das in das neue-Objekt kopiert werden soll `COleVariant` .

*pSrc*<br/>
Ein Zeiger auf ein- `VARIANT` Objekt, das in das neue- `COleVariant` Objekt kopiert wird.

*lpszsrc*<br/>
Eine mit NULL endende Zeichenfolge, die in das neue-Objekt kopiert werden soll `COleVariant` .

*VFS*<br/>
Der `VARTYPE` für das neue- `COleVariant` Objekt.

*"Straume"*<br/>
Ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Objekt, das in das neue-Objekt kopiert werden soll `COleVariant` .

*nsrc*, *LSRC* ein numerischer Wert, der in das neue-Objekt kopiert werden soll `COleVariant` .

*VFS*<br/>
Der `VARTYPE` für das neue- `COleVariant` Objekt.

*Cursor*<br/>
Ein [COleCurrency](../../mfc/reference/colecurrency-class.md) -Objekt, das in das neue-Objekt kopiert werden soll `COleVariant` .

*flwahrheits RC*, *dblsrc*<br/>
Ein in das neue `COleVariant`-Objekt zu kopierender numerischer Wert.

*timesrc*<br/>
Ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -Objekt, das in das neue-Objekt kopiert werden soll `COleVariant` .

*arrsrc*<br/>
Ein [CByteArray](../../mfc/reference/cbytearray-class.md) -Objekt, das in das neue-Objekt kopiert werden soll `COleVariant` .

*lbsrc*<br/>
Ein [CLongBinary](../../mfc/reference/clongbinary-class.md) -Objekt, das in das neue-Objekt kopiert werden soll `COleVariant` .

*PIDL*<br/>
Ein Zeiger auf eine [itemittellist](/windows/win32/api/shtypes/ns-shtypes-itemidlist) -Struktur, die in das neue-Objekt kopiert werden soll `COleVariant` .

### <a name="remarks"></a>Hinweise

Alle diese Konstruktoren erstellen neue `COleVariant` Objekte, die mit dem angegebenen Wert initialisiert werden. Eine kurze Beschreibung der einzelnen Konstruktoren folgt.

- **COleVariant ()** Erstellt ein leeres- `COleVariant` Objekt, VT_EMPTY.

- **COleVariant (** *varSrc* **)** Kopiert ein vorhandenes- `VARIANT` Objekt oder- `COleVariant` Objekt. Der Varianttyp wird beibehalten.

- **COleVariant (** *psrc* **)** Kopiert ein vorhandenes- `VARIANT` Objekt oder- `COleVariant` Objekt. Der Varianttyp wird beibehalten.

- **COleVariant (** *lpszsrc* **)** Kopiert eine Zeichenfolge in das neue-Objekt, VT_BSTR (Unicode).

- **COleVariant (** *lpszsrc* **,** *vzrc* **)** Kopiert eine Zeichenfolge in das neue-Objekt. Der Parameter *VFS* muss VT_BSTR (Unicode) oder VT_BSTRT (ANSI) sein.

- **COleVariant (** *Strauch* **)** Kopiert eine Zeichenfolge in das neue-Objekt, VT_BSTR (Unicode).

- **COleVariant (** *nsrc* **)** Kopiert eine 8-Bit-Ganzzahl in das neue-Objekt, VT_UI1.

- **COleVariant (** *nsrc* **,** *VFS* **)** Kopiert eine 16-Bit-Ganzzahl (oder einen booleschen Wert) in das neue-Objekt. Der Parameter *VFS* muss VT_I2 oder VT_BOOL sein.

- **COleVariant (** *LSRC* **,** *VFS* **)** Kopiert eine 32-Bit-Ganzzahl (oder einen SCODE-Wert) in das neue-Objekt. Der Parameter *VFS* muss VT_I4, VT_ERROR oder VT_BOOL sein.

- **COleVariant (** *Cursor* **)** Kopiert einen `COleCurrency` Wert in das neue-Objekt, VT_CY.

- **COleVariant (** *flgsrc* **)** Kopiert einen 32-Bit-Gleit Komma Wert in das neue-Objekt, VT_R4.

- **COleVariant (** *dblsrc* **)** Kopiert einen 64-Bit-Gleit Komma Wert in das neue-Objekt, VT_R8.

- **COleVariant (** *timesrc* **)** Kopiert einen `COleDateTime` Wert in das neue-Objekt, VT_DATE.

- **COleVariant (** *arrsrc* **)** Kopiert ein- `CByteArray` Objekt in das neue-Objekt, VT_EMPTY.

- **COleVariant (** *lbsrc* **)** Kopiert ein- `CLongBinary` Objekt in das neue-Objekt, VT_EMPTY.

Weitere Informationen zu SCODE finden Sie unter [Struktur von com-Fehler Codes](/windows/win32/com/structure-of-com-error-codes) in der Windows SDK.

## <a name="colevariantchangetype"></a><a name="changetype"></a>COleVariant:: ChangeType

Konvertiert den Typ des Variant-Werts in diesem- `COleVariant` Objekt.

```cpp
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>Parameter

*VarType*<br/>
Der VarType für dieses `COleVariant` Objekt.

*pSrc*<br/>
Ein Zeiger auf das zu konvertierende [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) -Objekt. Wenn dieser Wert NULL ist, `COleVariant` wird dieses Objekt als Quelle für die Konvertierung verwendet.

### <a name="remarks"></a>Hinweise

Weitere Informationen finden Sie in den Einträgen " [Variant](/windows/win32/api/oaidl/ns-oaidl-variant)", " [VarEnum](/windows/win32/api/wtypes/ne-wtypes-varenum)" und " [VariantChangeType](/windows/win32/api/oleauto/nf-oleauto-variantchangetype) " in der Windows SDK.

## <a name="colevariantclear"></a><a name="clear"></a>COleVariant:: Clear

Löscht die `VARIANT`.

```cpp
void Clear();
```

### <a name="remarks"></a>Hinweise

Dadurch wird der VarType für dieses Objekt auf VT_EMPTY festgelegt. Der `COleVariant` Dekonstruktor ruft diese Funktion auf.

Weitere Informationen finden Sie in den `VARIANT` Einträgen, VarType und `VariantClear` in der Windows SDK.

## <a name="colevariantdetach"></a><a name="detach"></a>COleVariant::D Etach

Trennt das zugrunde liegende [Variant](/windows/win32/api/oaidl/ns-oaidl-variant) -Objekt von diesem- `COleVariant` Objekt.

```
VARIANT Detach();
```

### <a name="remarks"></a>Hinweise

Diese Funktion legt den VarType für dieses `COleVariant` Objekt auf VT_EMPTY fest.

> [!NOTE]
> Nachdem aufgerufen `Detach` wurde, ist es die Aufgabe des Aufrufers, `VariantClear` für die resultierende Struktur aufzurufen `VARIANT` .

Weitere Informationen finden Sie in den Einträgen " [Variant](/windows/win32/api/oaidl/ns-oaidl-variant)", " [VarEnum](/windows/win32/api/wtypes/ne-wtypes-varenum)" und " [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) " in der Windows SDK.

## <a name="colevariantgetbytearrayfromvariantarray"></a><a name="getbytearrayfromvariantarray"></a>COleVariant:: getbytearrayfromvariantarray

Ruft ein Bytearray aus einem vorhandenen Variant-Array ab.

```cpp
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>Parameter

*Satz*<br/>
Ein Verweis auf ein vorhandenes [CByteArray](../../mfc/reference/cbytearray-class.md) -Objekt.

## <a name="colevariantoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COleVariant:: Operator lpcvariant

Dieser Umwandlungs Operator gibt eine-Struktur zurück, `VARIANT` deren Wert aus diesem-Objekt kopiert wird `COleVariant` .

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>Hinweise

## <a name="colevariantoperator-lpvariant"></a><a name="operator_lpvariant"></a>COleVariant:: Operator lpvariant

Aufrufen dieses Umwandlungs Operators, um auf die zugrunde liegende `VARIANT` Struktur für dieses `COleVariant` Objekt zuzugreifen.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Hinweise

> [!CAUTION]
> Wenn Sie den Wert in der Struktur ändern, auf `VARIANT` die der von dieser Funktion zurückgegebene Zeiger zugreift, wird der Wert dieses `COleVariant` Objekts geändert.

## <a name="colevariantoperator-"></a><a name="operator_eq"></a>COleVariant:: Operator =

Diese überladenen Zuweisungs Operatoren kopieren den Quellwert in dieses `COleVariant` Objekt.

```
const COleVariant& operator=(const VARIANT& varSrc);
const COleVariant& operator=(LPCVARIANT pSrc);
const COleVariant& operator=(const COleVariant& varSrc);
const COleVariant& operator=(const LPCTSTR lpszSrc);
const COleVariant& operator=(const CString& strSrc);
const COleVariant& operator=(BYTE nSrc);
const COleVariant& operator=(short nSrc);
const COleVariant& operator=(long lSrc);
const COleVariant& operator=(const COleCurrency& curSrc);
const COleVariant& operator=(float fltSrc);
const COleVariant& operator=(double dblSrc);
const COleVariant& operator=(const COleDateTime& dateSrc);
const COleVariant& operator=(const CByteArray& arrSrc);
const COleVariant& operator=(const CLongBinary& lbSrc);
```

### <a name="remarks"></a>Hinweise

Eine kurze Beschreibung der einzelnen Operatoren folgt:

- **Operator = (** *varSrc* **)** Kopiert eine vorhandene Variante oder ein vorhandenes `COleVariant` Objekt in dieses-Objekt.

- **Operator = (** *psrc* **)** Kopiert das Variant-Objekt, auf das *psrc* zugreift, in dieses-Objekt.

- **Operator = (** *lpszsrc* **)** Kopiert eine NULL-terminierte Zeichenfolge in dieses-Objekt und legt den VarType auf VT_BSTR fest.

- **Operator = (** *Strauch* **)** Kopiert ein [CString](../../atl-mfc-shared/reference/cstringt-class.md) -Objekt in dieses Objekt und legt VarType auf VT_BSTR fest.

- **Operator = (** *nsrc* **)** Kopiert einen 8-oder 16-Bit-ganzzahligen Wert in dieses-Objekt. Wenn *nsrc* ein 8-Bit-Wert ist, wird der VarType dieser auf VT_UI1 festgelegt. Wenn *nsrc* ein 16-Bit-Wert ist und der VarType dieses VT_BOOL ist, wird er beibehalten. Andernfalls wird Sie auf VT_I2 festgelegt.

- **Operator = (** *LSRC* **)** Kopiert einen ganzzahligen Wert von 32 Bit in dieses-Objekt. Wenn der VarType dieses VT_ERROR ist, wird er beibehalten. Andernfalls wird Sie auf VT_I4 festgelegt.

- **Operator = (** *Cursor* **)** Kopiert ein [COleCurrency](../../mfc/reference/colecurrency-class.md) -Objekt in dieses-Objekt und legt VarType auf VT_CY fest.

- **Operator = (** *flgsrc* **)** Kopiert einen 32-Bit-Gleit Komma Wert in dieses-Objekt und legt den VarType auf VT_R4 fest.

- **Operator = (** *dblsrc* **)** Kopiert einen 64-Bit-Gleit Komma Wert in dieses-Objekt und legt den VarType auf VT_R8 fest.

- **Operator = (** *datesrc* **)** Kopiert ein [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) -Objekt in dieses Objekt und legt VarType auf VT_DATE fest.

- **Operator = (** *arrsrc* **)** Kopiert ein [CByteArray](../../mfc/reference/cbytearray-class.md) -Objekt in dieses- `COleVariant` Objekt.

- **Operator = (** *lbsrc* **)** Kopiert ein [CLongBinary](../../mfc/reference/clongbinary-class.md) -Objekt in dieses- `COleVariant` Objekt.

Weitere Informationen finden Sie in den [Variablen "Variant](/windows/win32/api/oaidl/ns-oaidl-variant) " und " [VarEnum](/windows/win32/api/wtypes/ne-wtypes-varenum) " in der Windows SDK.

## <a name="colevariantoperator-"></a><a name="operator_eq_eq"></a>COleVariant:: Operator = =

Dieser Operator vergleicht zwei Variante Werte und gibt einen Wert ungleich 0 (null) zurück, wenn Sie gleich sind. andernfalls 0.

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

## <a name="colevariantoperator-ltlt-gtgt"></a><a name="operator_lt_lt__gt_gt"></a>COleVariant::-Operator &lt; &lt; ,&gt;&gt;

Gibt einen `COleVariant` Wert für `CArchive` oder `CdumpContext` aus und gibt ein- `COleVariant` Objekt aus `CArchive` .

```
friend CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    OleVariant varSrc);

friend CArchive& AFXAPI operator<<(
    CArchive& ar,
    COleVariant varSrc);

friend CArchive& AFXAPI operator>>(
    CArchive& ar,
    COleVariant& varSrc);
```

### <a name="remarks"></a>Hinweise

Der `COleVariant` einfügeoperator ( **\<\<**) operator supports diagnostic dumping and storing to an archive. The extraction (**>>** ) unterstützt das Laden aus einem Archiv.

## <a name="colevariantsetstring"></a><a name="setstring"></a>COleVariant:: SetString

Legt die Zeichenfolge auf einen bestimmten Typ fest.

```cpp
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>Parameter

*lpszsrc*<br/>
Eine mit NULL endende Zeichenfolge, die in das neue-Objekt kopiert werden soll `COleVariant` .

*VFS*<br/>
Der VarType für das neue- `COleVariant` Objekt.

### <a name="remarks"></a>Hinweise

Der Parameter *VFS* muss VT_BSTR (Unicode) oder VT_BSTRT (ANSI) sein. `SetString`wird normalerweise verwendet, um Zeichen folgen auf ANSI festzulegen, da der Standardwert für den [COleVariant:: COleVariant](#colevariant) -Konstruktor mit einem String-oder String-Zeiger Parameter und No VarType Unicode ist.

Bei einem DAO-Recordset in einem nicht-Unicode-Build werden Zeichen folgen als ANSI erwartet. Wenn Sie also kein Unicode-Recordset erstellen, müssen Sie für DAO-Funktionen, die-Objekte verwenden, `COleVariant` die **Form COleVariant:: COleVariant (** *lpszsrc* **,** *vzrc* **)** mit *vtrc* festlegen, die auf VT_BSTRT (ANSI) festgelegt ist, oder `SetString` mit *vzrc* auf VT_BSTRT festlegen, um ANSI-Zeichen folgen zu erstellen. Beispielsweise verwenden die `CDaoRecordset` Funktionen [CDaoRecordset:: Seek](../../mfc/reference/cdaorecordset-class.md#seek) und [CDaoRecordset:: SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) - `COleVariant` Objekte als Parameter. Diese Objekte müssen ANSI sein, wenn das DAO-Recordset nicht Unicode ist.

## <a name="see-also"></a>Siehe auch

[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>

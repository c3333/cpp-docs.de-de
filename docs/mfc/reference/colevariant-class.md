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
ms.openlocfilehash: 7d8abea39a9baa3f447ca0d5f3ab1183367d531f
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753718"
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
|[COleVariant::COleVariant](#colevariant)|Erstellt ein `COleVariant`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleVariant::Anfügen](#attach)|Fügt einen VARIANT `COleVariant`an eine an.|
|[COleVariant::ChangeType](#changetype)|Ändert den Variantentyp `COleVariant` dieses Objekts.|
|[COleVariant::Löschen](#clear)|Löscht dieses `COleVariant`-Objekt.|
|[COleVariant::Detach](#detach)|Trennt einen VARIANT von `COleVariant` a und gibt den VARIANT zurück.|
|[COleVariant::GetByteArrayFromVariantArray](#getbytearrayfromvariantarray)|Ruft ein Bytearray aus einem vorhandenen Variantenarray ab.|
|[COleVariant::SetString](#setstring)|Legt die Zeichenfolge auf einen bestimmten Typ fest, in der Regel ANSI.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleVariant::operator LPCVARIANT](#operator_lpcvariant)|Konvertiert einen `COleVariant` Wert `LPCVARIANT`in eine .|
|[COleVariant::operator LPVARIANT](#operator_lpvariant)|Konvertiert ein `COleVariant` Objekt `LPVARIANT`in eine .|
|[COleVariant::operator =](#operator_eq)|Kopiert `COleVariant` einen Wert.|
|[COleVariant::operator ==](#operator_eq_eq)|Vergleicht `COleVariant` zwei Werte.|
|[COleVariant::operator &lt; &lt;,&gt;&gt;](#operator_lt_lt__gt_gt)|Gibt einen `COleVariant` Wert `CArchive` `CDumpContext` an oder `COleVariant` ein `CArchive`und gibt ein Objekt aus ein.|

## <a name="remarks"></a>Bemerkungen

Dieser Datentyp wird in der OLE-Automatisierung verwendet. Insbesondere enthält die [DISPPARAMS-Struktur](/windows/win32/api/oaidl/ns-oaidl-dispparams) einen Zeiger auf ein Array von VARIANT-Strukturen. Eine `DISPPARAMS` Struktur wird verwendet, um Parameter an [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)zu übergeben.

> [!NOTE]
> Diese Klasse wird `VARIANT` von der Struktur abgeleitet. Dies bedeutet, `COleVariant` dass Sie einen in `VARIANT` einem Parameter übergeben `VARIANT` können, der eine `COleVariant`fordert, und dass die Datenmember der Struktur auf Datenmember von zugreifen können.

Die beiden verwandten MFC-Klassen [COleCurrency](../../mfc/reference/colecurrency-class.md) und [COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md) kapseln `VT_CY`die Variantendatentypen CURRENCY ( ) und DATE ( `VT_DATE`). Die `COleVariant` Klasse wird in den DAO-Klassen ausgiebig verwendet. Siehe diese Klassen für die typische Verwendung dieser Klasse, z. B. [CDaoQueryDef](../../mfc/reference/cdaoquerydef-class.md) und [CDaoRecordset](../../mfc/reference/cdaorecordset-class.md).

Weitere Informationen finden Sie in den [Einträgen VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant), [CURRENCY](/windows/win32/api/wtypes/ns-wtypes-cy~r1), [DISPPARAMS](/windows/win32/api/oaidl/ns-oaidl-dispparams)und [IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke) entries in the Windows SDK.

Weitere Informationen zur `COleVariant` Klasse und deren Verwendung in der OLE-Automatisierung finden Sie unter "Übergeben von Parametern in DER OLE-Automatisierung" im Artikel [Automation](../../mfc/automation.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`tagVARIANT`

`COleVariant`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxdisp.h

## <a name="colevariantattach"></a><a name="attach"></a>COleVariant::Anfügen

Rufen Sie diese Funktion auf, um `COleVariant` das angegebene [VARIANT-Objekt](/windows/win32/api/oaidl/ns-oaidl-variant) an das aktuelle Objekt anzuhängen.

```cpp
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Parameter

*varSrc*<br/>
Ein `VARIANT` vorhandenes Objekt, das `COleVariant` dem aktuellen Objekt zugeordnet werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion legt den VARTYPE von *varSrc* auf VT_EMPTY.

Weitere Informationen finden Sie in den Einträgen [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) und [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum) im Windows SDK.

## <a name="colevariantcolevariant"></a><a name="colevariant"></a>COleVariant::COleVariant

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
Ein `COleVariant` vorhandenes oder `VARIANT` Objekt, `COleVariant` das in das neue Objekt kopiert werden soll.

*pSrc*<br/>
Ein Zeiger auf `VARIANT` ein Objekt, das `COleVariant` in das neue Objekt kopiert wird.

*lpszSrc*<br/>
Eine null-terminierte Zeichenfolge, die `COleVariant` in das neue Objekt kopiert werden soll.

*vtSrc*<br/>
Die `VARTYPE` für `COleVariant` das neue Objekt.

*strSrc*<br/>
Ein [CString-Objekt,](../../atl-mfc-shared/reference/cstringt-class.md) das `COleVariant` in das neue Objekt kopiert werden soll.

*nSrc*, *lSrc* Ein numerischer Wert, der in das neue `COleVariant` Objekt kopiert werden soll.

*vtSrc*<br/>
Die `VARTYPE` für `COleVariant` das neue Objekt.

*curSrc*<br/>
Ein [COleCurrency-Objekt,](../../mfc/reference/colecurrency-class.md) das `COleVariant` in das neue Objekt kopiert werden soll.

*fltSrc*, *dblSrc*<br/>
Ein in das neue `COleVariant`-Objekt zu kopierender numerischer Wert.

*timeSrc*<br/>
Ein [COleDateTime-Objekt,](../../atl-mfc-shared/reference/coledatetime-class.md) das `COleVariant` in das neue Objekt kopiert werden soll.

*arrSrc*<br/>
Ein [CByteArray-Objekt,](../../mfc/reference/cbytearray-class.md) das `COleVariant` in das neue Objekt kopiert werden soll.

*lbSrc*<br/>
Ein [CLongBinary-Objekt,](../../mfc/reference/clongbinary-class.md) das `COleVariant` in das neue Objekt kopiert werden soll.

*Pidl*<br/>
Ein Zeiger auf eine [ITEMIDLIST-Struktur,](/windows/win32/api/shtypes/ns-shtypes-itemidlist) `COleVariant` die in das neue Objekt kopiert werden soll.

### <a name="remarks"></a>Bemerkungen

Alle diese Konstruktoren `COleVariant` erstellen neue Objekte, die auf den angegebenen Wert initialisiert wurden. Es folgt eine kurze Beschreibung jedes dieser Konstruktoren.

- **COleVariant( )** Erstellt ein `COleVariant` leeres Objekt, VT_EMPTY.

- **COleVariant(** *varSrc* **)** Kopiert ein `VARIANT` `COleVariant` vorhandenes Objekt oder ein Objekt. Der Varianttyp wird beibehalten.

- **COleVariant(** *pSrc* **)** Kopiert ein `VARIANT` `COleVariant` vorhandenes Objekt oder ein Objekt. Der Varianttyp wird beibehalten.

- **COleVariant(** *lpszSrc* **)** Kopiert eine Zeichenfolge in das neue Objekt VT_BSTR (UNICODE).

- **COleVariant(** *lpszSrc* **,** *vtSrc* **)** Kopiert eine Zeichenfolge in das neue Objekt. Der Parameter *vtSrc* muss VT_BSTR (UNICODE) oder VT_BSTRT (ANSI) sein.

- **COleVariant(** *strSrc* **)** Kopiert eine Zeichenfolge in das neue Objekt VT_BSTR (UNICODE).

- **COleVariant(** *nSrc* **)** Kopiert eine 8-Bit-Ganzzahl in das neue Objekt, VT_UI1.

- **COleVariant(** *nSrc* **,** *vtSrc* **)** Kopiert eine 16-Bit-Ganzzahl (oder einen booleschen Wert) in das neue Objekt. Der Parameter *vtSrc* muss VT_I2 oder VT_BOOL sein.

- **COleVariant(** *lSrc* **,** *vtSrc* **)** Kopiert eine 32-Bit-Ganzzahl (oder einen SCODE-Wert) in das neue Objekt. Der Parameter *vtSrc* muss VT_I4, VT_ERROR oder VT_BOOL sein.

- **COleVariant(** *curSrc* **)** Kopiert `COleCurrency` einen Wert in das neue Objekt, VT_CY.

- **COleVariant(** *fltSrc* **)** Kopiert einen 32-Bit-Gleitkommawert in das neue Objekt, VT_R4.

- **COleVariant(** *dblSrc* **)** Kopiert einen 64-Bit-Gleitkommawert in das neue Objekt, VT_R8.

- **COleVariant(** *timeSrc* **)** Kopiert `COleDateTime` einen Wert in das neue Objekt, VT_DATE.

- **COleVariant(** *arrSrc* **)** Kopiert `CByteArray` ein Objekt in das neue Objekt, VT_EMPTY.

- **COleVariant(** *lbSrc* **)** Kopiert `CLongBinary` ein Objekt in das neue Objekt, VT_EMPTY.

Weitere Informationen zu SCODE finden Sie unter [Struktur von COM-Fehlercodes](/windows/win32/com/structure-of-com-error-codes) im Windows SDK.

## <a name="colevariantchangetype"></a><a name="changetype"></a>COleVariant::ChangeType

Konvertiert den Typ des Variantenwerts in diesem `COleVariant` Objekt.

```cpp
void ChangeType(VARTYPE vartype, LPVARIANT pSrc = NULL);
```

### <a name="parameters"></a>Parameter

*Vartype*<br/>
Der VARTYPE `COleVariant` für dieses Objekt.

*pSrc*<br/>
Ein Zeiger auf das [zu](/windows/win32/api/oaidl/ns-oaidl-variant) konvertierende VARIANT-Objekt. Wenn dieser Wert NULL `COleVariant` ist, wird dieses Objekt als Quelle für die Konvertierung verwendet.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie in den Einträgen [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant), [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)und [VariantChangeType](/windows/win32/api/oleauto/nf-oleauto-variantchangetype) im Windows SDK.

## <a name="colevariantclear"></a><a name="clear"></a>COleVariant::Löschen

Löscht die `VARIANT`.

```cpp
void Clear();
```

### <a name="remarks"></a>Bemerkungen

Dadurch wird der VARTYPE für dieses Objekt auf VT_EMPTY festgelegt. Der `COleVariant` Destruktor ruft diese Funktion auf.

Weitere Informationen finden `VARIANT`Sie unter , `VariantClear` VARTYPE und Einträge im Windows SDK.

## <a name="colevariantdetach"></a><a name="detach"></a>COleVariant::Detach

Trennt das zugrunde liegende [VARIANT-Objekt](/windows/win32/api/oaidl/ns-oaidl-variant) von diesem `COleVariant` Objekt.

```
VARIANT Detach();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion legt den `COleVariant` VARTYPE für dieses Objekt auf VT_EMPTY fest.

> [!NOTE]
> Nach `Detach`dem Aufruf liegt es in der `VariantClear` Verantwortung `VARIANT` des Aufrufers, die resultierende Struktur aufzurufen.

Weitere Informationen finden Sie in den [Einträgen VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant), [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum)und [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear) im Windows SDK.

## <a name="colevariantgetbytearrayfromvariantarray"></a><a name="getbytearrayfromvariantarray"></a>COleVariant::GetByteArrayFromVariantArray

Ruft ein Byte-Array aus einem vorhandenen Variantenarray ab

```cpp
void GetByteArrayFromVariantArray(CByteArray& bytes);
```

### <a name="parameters"></a>Parameter

*Bytes*<br/>
Ein Verweis auf ein vorhandenes [CByteArray-Objekt.](../../mfc/reference/cbytearray-class.md)

## <a name="colevariantoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COleVariant::operator LPCVARIANT

Dieser Umwandlungsoperator `VARIANT` gibt eine Struktur `COleVariant` zurück, deren Wert aus diesem Objekt kopiert wird.

```
operator LPCVARIANT() const;
```

### <a name="remarks"></a>Bemerkungen

## <a name="colevariantoperator-lpvariant"></a><a name="operator_lpvariant"></a>COleVariant::operator LPVARIANT

Rufen Sie diesen Umwandlungsoperator auf, um auf die zugrunde liegende `VARIANT` Struktur für dieses `COleVariant` Objekt zuzugreifen.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Bemerkungen

> [!CAUTION]
> Wenn Sie den `VARIANT` Wert in der Struktur ändern, auf die `COleVariant` der Zeiger, der von dieser Funktion zurückgegeben wird, zugegriffen wird, wird der Wert dieses Objekts geändert.

## <a name="colevariantoperator-"></a><a name="operator_eq"></a>COleVariant::operator =

Diese überladenen Zuweisungsoperatoren `COleVariant` kopieren den Quellwert in dieses Objekt.

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

### <a name="remarks"></a>Bemerkungen

Eine kurze Beschreibung der einzelnen Operatoren folgt:

- **Operator =(** *varSrc* **)** Kopiert ein vorhandenes VARIANT oder `COleVariant` Objekt in dieses Objekt.

- **Operator =(** *pSrc* **)** Kopiert das VARIANT-Objekt, auf das *pSrc* zugreift, in dieses Objekt.

- **Operator =(** *lpszsrc* **)** Kopiert eine null-terminierte Zeichenfolge in dieses Objekt und legt den VARTYPE auf VT_BSTR.

- **Operator =(** *strSrc* **)** Kopiert ein [CString-Objekt](../../atl-mfc-shared/reference/cstringt-class.md) in dieses Objekt und legt den VARTYPE auf VT_BSTR.

- **Operator =(** *nSrc* **)** Kopiert einen 8- oder 16-Bit-Ganzzahlwert in dieses Objekt. Wenn *nSrc* ein 8-Bit-Wert ist, wird der VARTYPE auf VT_UI1 festgelegt. Wenn *nSrc* ein 16-Bit-Wert ist und der VARTYPE davon VT_BOOL ist, wird er beibehalten. Andernfalls wird es auf VT_I2 eingestellt.

- **Operator =(** *lSrc* **)** Kopiert einen 32-Bit-Ganzzahlwert in dieses Objekt. Wenn der VARTYPE davon VT_ERROR ist, wird er beibehalten; Andernfalls wird es auf VT_I4 eingestellt.

- **Operator =(** *curSrc* **)** Kopiert ein [COleCurrency-Objekt](../../mfc/reference/colecurrency-class.md) in dieses Objekt und legt den VARTYPE auf VT_CY fest.

- **Operator =(** *fltSrc* **)** Kopiert einen 32-Bit-Gleitkommawert in dieses Objekt und legt varTYPE auf VT_R4 fest.

- **Operator =(** *dblSrc* **)** Kopiert einen 64-Bit-Gleitkommawert in dieses Objekt und legt den VARTYPE auf VT_R8.

- **Operator =(** *dateSrc* **)** Kopiert ein [COleDateTime-Objekt](../../atl-mfc-shared/reference/coledatetime-class.md) in dieses Objekt und legt den VARTYPE auf VT_DATE fest.

- **Operator =(** *arrSrc* **)** Kopiert ein [CByteArray-Objekt](../../mfc/reference/cbytearray-class.md) in dieses `COleVariant` Objekt.

- **Operator =(** *lbSrc* **)** Kopiert ein [CLongBinary-Objekt](../../mfc/reference/clongbinary-class.md) in dieses `COleVariant` Objekt.

Weitere Informationen finden Sie in den Einträgen [VARIANT](/windows/win32/api/oaidl/ns-oaidl-variant) und [VARENUM](/windows/win32/api/wtypes/ne-wtypes-varenum) im Windows SDK.

## <a name="colevariantoperator-"></a><a name="operator_eq_eq"></a>COleVariant::operator ==

Dieser Operator vergleicht zwei Variantenwerte und gibt einen Wert ungleich Null zurück, wenn sie gleich sind. andernfalls 0.

```
BOOL operator==(const VARIANT& varSrc) const;
BOOL operator==(LPCVARIANT pSrc) const;
```

## <a name="colevariantoperator-ltlt-gtgt"></a><a name="operator_lt_lt__gt_gt"></a>COleVariant::operator &lt; &lt;,&gt;&gt;

Gibt einen `COleVariant` Wert `CArchive` `CdumpContext` an oder `COleVariant` ein `CArchive`und gibt ein Objekt aus ein.

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

### <a name="remarks"></a>Bemerkungen

Der `COleVariant` Operator**\<** Einfügen ( ) unterstützt Diagnose-Dumping und Speicherung in einem Archiv. Der Extraktionsoperator (**>>**) unterstützt das Laden aus einem Archiv.

## <a name="colevariantsetstring"></a><a name="setstring"></a>COleVariant::SetString

Legt die Zeichenfolge auf einen bestimmten Typ fest.

```cpp
void SetString(LPCTSTR lpszSrc, VARTYPE vtSrc);
```

### <a name="parameters"></a>Parameter

*lpszSrc*<br/>
Eine null-terminierte Zeichenfolge, die `COleVariant` in das neue Objekt kopiert werden soll.

*VtSrc*<br/>
Der VARTYPE für `COleVariant` das neue Objekt.

### <a name="remarks"></a>Bemerkungen

Der Parameter *vtSrc* muss VT_BSTR (UNICODE) oder VT_BSTRT (ANSI) sein. `SetString`wird in der Regel verwendet, um Zeichenfolgen auf ANSI festzulegen, da der Standardwert für den [COleVariant::COleVariant-Konstruktor](#colevariant) mit einem Zeichenfolgen- oder Zeichenfolgenzeigerparameter und kein VARTYPE UNICODE ist.

Ein DAO-Recordset in einem Nicht-UNICODE-Build erwartet, dass Zeichenfolgen ANSI sind. Wenn Sie also kein `COleVariant` UNICODE-Recordset erstellen, müssen Sie für DAO-Funktionen, die Objekte verwenden, die Die Constructor-Form **COleVariant::COleVariant(** *lpszSrc* **,** *vtSrc* **mit** *vtSrc* auf VT_BSTRT (ANSI) festgelegt ist, oder mit `SetString` *vtSrc* verwenden, der auf VT_BSTRT festgelegt ist, um ANSI-Zeichenfolgen zu erstellen. Beispielsweise `COleVariant` verwenden `CDaoRecordset` die Funktionen [CDaoRecordset::Seek](../../mfc/reference/cdaorecordset-class.md#seek) und [CDaoRecordset::SetFieldValue](../../mfc/reference/cdaorecordset-class.md#setfieldvalue) Objekte als Parameter. Diese Objekte müssen ANSI sein, wenn das DAO-Recordset nicht UNICODE ist.

## <a name="see-also"></a>Weitere Informationen

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>

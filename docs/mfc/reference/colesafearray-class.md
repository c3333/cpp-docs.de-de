---
title: COleSafeArray-Klasse
ms.date: 08/29/2019
f1_keywords:
- COleSafeArray
- AFXDISP/COleSafeArray
- AFXDISP/COleSafeArray::COleSafeArray
- AFXDISP/COleSafeArray::AccessData
- AFXDISP/COleSafeArray::AllocData
- AFXDISP/COleSafeArray::AllocDescriptor
- AFXDISP/COleSafeArray::Attach
- AFXDISP/COleSafeArray::Clear
- AFXDISP/COleSafeArray::Copy
- AFXDISP/COleSafeArray::Create
- AFXDISP/COleSafeArray::CreateOneDim
- AFXDISP/COleSafeArray::Destroy
- AFXDISP/COleSafeArray::DestroyData
- AFXDISP/COleSafeArray::DestroyDescriptor
- AFXDISP/COleSafeArray::Detach
- AFXDISP/COleSafeArray::GetByteArray
- AFXDISP/COleSafeArray::GetDim
- AFXDISP/COleSafeArray::GetElement
- AFXDISP/COleSafeArray::GetElemSize
- AFXDISP/COleSafeArray::GetLBound
- AFXDISP/COleSafeArray::GetOneDimSize
- AFXDISP/COleSafeArray::GetUBound
- AFXDISP/COleSafeArray::Lock
- AFXDISP/COleSafeArray::PtrOfIndex
- AFXDISP/COleSafeArray::PutElement
- AFXDISP/COleSafeArray::Redim
- AFXDISP/COleSafeArray::ResizeOneDim
- AFXDISP/COleSafeArray::UnaccessData
- AFXDISP/COleSafeArray::Unlock
helpviewer_keywords:
- COleSafeArray [MFC], COleSafeArray
- COleSafeArray [MFC], AccessData
- COleSafeArray [MFC], AllocData
- COleSafeArray [MFC], AllocDescriptor
- COleSafeArray [MFC], Attach
- COleSafeArray [MFC], Clear
- COleSafeArray [MFC], Copy
- COleSafeArray [MFC], Create
- COleSafeArray [MFC], CreateOneDim
- COleSafeArray [MFC], Destroy
- COleSafeArray [MFC], DestroyData
- COleSafeArray [MFC], DestroyDescriptor
- COleSafeArray [MFC], Detach
- COleSafeArray [MFC], GetByteArray
- COleSafeArray [MFC], GetDim
- COleSafeArray [MFC], GetElement
- COleSafeArray [MFC], GetElemSize
- COleSafeArray [MFC], GetLBound
- COleSafeArray [MFC], GetOneDimSize
- COleSafeArray [MFC], GetUBound
- COleSafeArray [MFC], Lock
- COleSafeArray [MFC], PtrOfIndex
- COleSafeArray [MFC], PutElement
- COleSafeArray [MFC], Redim
- COleSafeArray [MFC], ResizeOneDim
- COleSafeArray [MFC], UnaccessData
- COleSafeArray [MFC], Unlock
ms.assetid: f45a5224-5f48-40ec-9ddd-287ef9740150
ms.openlocfilehash: a7be9910b573cb5bc430d6608e75ce6661b71bc2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374863"
---
# <a name="colesafearray-class"></a>COleSafeArray-Klasse

Eine Klasse zum Arbeiten mit Arrays beliebiger Dimension und beliebigen Typs.

## <a name="syntax"></a>Syntax

```
class COleSafeArray : public tagVARIANT
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleSafeArray::COleSafeArray](#colesafearray)|Erstellt ein `COleSafeArray`-Objekt.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleSafeArray::AccessData](#accessdata)|Ruft einen Zeiger auf die Arraydaten ab.|
|[COleSafeArray::AllocData](#allocdata)|Weist Speicher für das Array zu.|
|[COleSafeArray::AllocDescriptor](#allocdescriptor)|Weist Speicher für den sicheren Arraydeskriptor zu.|
|[COleSafeArray::Anfügen](#attach)|Gibt dem Objekt `VARIANT` die `COleSafeArray` Steuerung des vorhandenen Arrays.|
|[COleSafeArray::Löschen](#clear)|Gibt alle Daten im `VARIANT`zugrunde liegenden frei.|
|[COleSafeArray::Kopieren](#copy)|Erstellt eine Kopie eines vorhandenen Arrays.|
|[COleSafeArray::Erstellen](#create)|Erstellt ein sicheres Array.|
|[COleSafeArray::CreateOneDim](#createonedim)|Erstellt ein eindimensionales `COleSafeArray` Objekt.|
|[COleSafeArray::Destroy](#destroy)|Zerstört ein vorhandenes Array.|
|[COleSafeArray::DestroyData](#destroydata)|Zerstört Daten in einem sicheren Array.|
|[COleSafeArray::DestroyDescriptor](#destroydescriptor)|Zerstört einen Deskriptor eines sicheren Arrays.|
|[COleSafeArray::Detach](#detach)|Trennt das VARIANT-Array `COleSafeArray` vom Objekt (damit die Daten nicht freigegeben werden).|
|[COleSafeArray::GetByteArray](#getbytearray)|Kopiert den Inhalt des sicheren Arrays in ein [CByteArray](../../mfc/reference/cbytearray-class.md).|
|[COleSafeArray::GetDim](#getdim)|Gibt die Anzahl der Dimensionen des Arrays zurück.|
|[COleSafeArray::GetElement](#getelement)|Ruft ein einzelnes Element des sicheren Arrays ab.|
|[COleSafeArray::GetElemSize](#getelemsize)|Gibt die Größe eines Elements in einem sicheren Array in Bytes zurück.|
|[COleSafeArray::GetLbound](#getlbound)|Gibt die untere Grenze für jede Dimension eines sicheren Arrays zurück.|
|[COleSafeArray::GetOneDimSize](#getonedimsize)|Gibt die Anzahl der Elemente `COleSafeArray` im eindimensionalen Objekt zurück.|
|[COleSafeArray::Getubound](#getubound)|Gibt die Obergrenze für jede Dimension eines sicheren Arrays zurück.|
|[COleSafeArray::Sperre](#lock)|Erhöht die Sperranzahl eines Arrays und platziert einen Zeiger auf die Arraydaten im Arraydeskriptor.|
|[COleSafeArray::PtrOfIndex](#ptrofindex)|Gibt einen Zeiger auf das indizierte Element zurück.|
|[COleSafeArray::PutElement](#putelement)|Weist ein einzelnes Element im Array zu.|
|[COleSafeArray::Redim](#redim)|Ändert die am wenigsten signifikante (rechts) gebundene Grenze eines sicheren Arrays.|
|[COleSafeArray::ResizeOneDim](#resizeonedim)|Ändert die Anzahl der Elemente `COleSafeArray` in einem eindimensionalen Objekt.|
|[COleSafeArray::UnaccessData](#unaccessdata)|Dekrementiert die Sperranzahl eines Arrays und macht `AccessData`den von abgerufenen Zeiger ungültig.|
|[COleSafeArray::Entsperren](#unlock)|Dekrementiert die Sperranzahl eines Arrays, sodass es freigegeben oder in der Größe geändert werden kann.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[COleSafeArray::operator LPCVARIANT](#operator_lpcvariant)|Greift auf `VARIANT` die zugrunde `COleSafeArray` liegende Struktur des Objekts zu.|
|[COleSafeArray::operator LPVARIANT](#operator_lpvariant)|Greift auf `VARIANT` die zugrunde `COleSafeArray` liegende Struktur des Objekts zu.|
|[COleSafeArray::operator =](#operator_eq)|Kopiert Werte `COleSafeArray` in`SAFEARRAY`ein `VARIANT` `COleVariant`Objekt `COleSafeArray` ( , , , oder Array).|
|[COleSafeArray::operator ==](#operator_eq_eq)|Vergleicht zwei Variantenarrays `VARIANT` `COleVariant`(`SAFEARRAY` `COleSafeArray` , , , oder Arrays).|
|[COleSafeArray::Operator&lt;&lt;](#operator_lt_lt)|Gibt den Inhalt `COleSafeArray` eines Objekts an den Dumpkontext aus.|

## <a name="remarks"></a>Bemerkungen

`COleSafeArray`leitet sich von `VARIANT` der OLE-Struktur ab. Die `SAFEARRAY` OLE-Memberfunktionen `COleSafeArray`sind über verfügbar, sowie über eine Reihe von Memberfunktionen, die speziell für eindimensionale Arrays von Bytes entwickelt wurden.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`tagVARIANT`

`COleSafeArray`

## <a name="requirements"></a>Anforderungen

**Header:** afxdisp.h

## <a name="colesafearrayaccessdata"></a><a name="accessdata"></a>COleSafeArray::AccessData

Ruft einen Zeiger auf die Arraydaten ab.

```
void AccessData(void** ppvData);
```

### <a name="parameters"></a>Parameter

*ppvData*<br/>
Ein Zeiger auf einen Zeiger auf die Arraydaten.

### <a name="remarks"></a>Bemerkungen

Bei Fehler löst die Funktion eine [CMemoryException](../../mfc/reference/cmemoryexception-class.md) oder [COleException](../../mfc/reference/coleexception-class.md)aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#26](../../mfc/codesnippet/cpp/colesafearray-class_1.cpp)]

## <a name="colesafearrayallocdata"></a><a name="allocdata"></a>COleSafeArray::AllocData

Ordnet Speicher für ein sicheres Array zu.

```
void AllocData();
```

### <a name="remarks"></a>Bemerkungen

Bei Fehler löst die Funktion eine [CMemoryException](../../mfc/reference/cmemoryexception-class.md) oder [COleException](../../mfc/reference/coleexception-class.md)aus.

## <a name="colesafearrayallocdescriptor"></a><a name="allocdescriptor"></a>COleSafeArray::AllocDescriptor

Weist Speicher für die Deskriptor eines sicheren Arrays zu.

```
void AllocDescriptor(DWORD dwDims);
```

### <a name="parameters"></a>Parameter

*dwDims*<br/>
Anzahl der Dimensionen im sicheren Array.

### <a name="remarks"></a>Bemerkungen

Bei Fehler löst die Funktion eine [CMemoryException](../../mfc/reference/cmemoryexception-class.md) oder [COleException](../../mfc/reference/coleexception-class.md)aus.

## <a name="colesafearrayattach"></a><a name="attach"></a>COleSafeArray::Anfügen

Gibt dem Objekt die `VARIANT` `COleSafeArray` Kontrolle über die Daten in einem vorhandenen Array.

```
void Attach(VARIANT& varSrc);
```

### <a name="parameters"></a>Parameter

*varSrc*<br/>
Ein `VARIANT` -Objekt. Der *varSrc-Parameter* muss über die [VARTYPE-VT_ARRAY](/windows/win32/api/wtypes/ne-wtypes-varenum)verfügen.

### <a name="remarks"></a>Bemerkungen

`VARIANT`Der Quelltyp ist auf VT_EMPTY festgelegt. Diese Funktion löscht ggf. die aktuellen Arraydaten.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [COleSafeArray::AccessData](#accessdata).

## <a name="colesafearrayclear"></a><a name="clear"></a>COleSafeArray::Löschen

Löscht das sichere Array.

```
void Clear();
```

### <a name="remarks"></a>Bemerkungen

Die Funktion löscht ein sicheres `VARTYPE` Array, indem sie die des Objekts auf VT_EMPTY. Der aktuelle Inhalt wird freigegeben, und das Array wird freigegeben.

## <a name="colesafearraycolesafearray"></a><a name="colesafearray"></a>COleSafeArray::COleSafeArray

Erstellt ein `COleSafeArray`-Objekt.

```
COleSafeArray();

COleSafeArray(
    const SAFEARRAY& saSrc,
    VARTYPE vtSrc);

COleSafeArray(
    LPCSAFEARRAY pSrc,
    VARTYPE vtSrc);

COleSafeArray(const COleSafeArray& saSrc);
COleSafeArray(const VARIANT& varSrc);
COleSafeArray(LPCVARIANT pSrc);
COleSafeArray(const COleVariant& varSrc);
```

### <a name="parameters"></a>Parameter

*saSrc*<br/>
Ein `COleSafeArray` vorhandenes `SAFEARRAY` Objekt, das `COleSafeArray` in das neue Objekt kopiert werden soll.

*vtSrc*<br/>
Der VARTYPE des `COleSafeArray` neuen Objekts.

*psaSrc*<br/>
Ein Zeiger auf `SAFEARRAY` ein, das `COleSafeArray` in das neue Objekt kopiert werden soll.

*varSrc*<br/>
Ein `VARIANT` vorhandenes oder `COleVariant` Objekt, `COleSafeArray` das in das neue Objekt kopiert werden soll.

*pSrc*<br/>
Ein Zeiger auf `VARIANT` ein Objekt, das `COleSafeArray` in das neue Objekt kopiert werden soll.

### <a name="remarks"></a>Bemerkungen

Alle diese Konstruktoren `COleSafeArray` erstellen neue Objekte. Wenn kein Parameter vorhanden `COleSafeArray` ist, wird ein leeres Objekt erstellt (VT_EMPTY). Wenn `COleSafeArray` der aus einem anderen Array kopiert wird, `COleSafeArray` `COleVariant`dessen `VARIANT`VARTYPE implizit bekannt ist (a , , oder ), wird der VARTYPE des Quellarrays beibehalten und muss nicht angegeben werden. Wenn `COleSafeArray` der aus einem anderen Array kopiert`SAFEARRAY`wird, dessen VARTYPE nicht bekannt ist ( ), muss der VARTYPE im *VtSrc-Parameter* angegeben werden.

Bei Fehler löst die Funktion eine [CMemoryException](../../mfc/reference/cmemoryexception-class.md) oder [COleException](../../mfc/reference/coleexception-class.md)aus.

## <a name="colesafearraycopy"></a><a name="copy"></a>COleSafeArray::Kopieren

Erstellt eine Kopie eines vorhandenen sicheren Arrays.

```
void Copy(LPSAFEARRAY* ppsa);
```

### <a name="parameters"></a>Parameter

*ppsa*<br/>
Zeigen Sie auf einen Speicherort, an dem der neue Arraydeskriptor zurückgegeben werden soll.

### <a name="remarks"></a>Bemerkungen

Bei Fehler löst die Funktion eine [CMemoryException](../../mfc/reference/cmemoryexception-class.md) oder [COleException](../../mfc/reference/coleexception-class.md)aus.

## <a name="colesafearraycreate"></a><a name="create"></a>COleSafeArray::Erstellen

Ordnet die Daten für das Array zu und initialisiert sie.

```
void Create(
    VARTYPE vtSrc,
    DWORD dwDims,
    DWORD* rgElements);

void Create(
    VARTYPE vtSrc,
    DWORD dwDims,
    SAFEARRAYBOUND* rgsabounds);
```

### <a name="parameters"></a>Parameter

*vtSrc*<br/>
Der Basistyp des Arrays (d. h. der VARTYPE jedes Elements des Arrays). Der VARTYPE ist auf eine Teilmenge der Variantentypen beschränkt. Weder die VT_ARRAY noch das VT_BYREF-Flag können gesetzt werden. VT_EMPTY und VT_NULL sind keine gültigen Basistypen für das Array. Alle anderen Arten sind legal.

*dwDims*<br/>
Anzahl der Dimensionen im Array. Dies kann geändert werden, nachdem das Array mit [Redim](#redim)erstellt wurde.

*rgElements*<br/>
Zeiger auf ein Array der Anzahl der Elemente für jede Dimension im Array.

*rgsabounds*<br/>
Zeiger auf einen Vektor von Grenzen (einer für jede Dimension), der für das Array zugewiesen werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion löscht bei Bedarf die aktuellen Arraydaten. Bei einem Fehler löst die Funktion eine [CMemoryException](../../mfc/reference/cmemoryexception-class.md)aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

## <a name="colesafearraycreateonedim"></a><a name="createonedim"></a>COleSafeArray::CreateOneDim

Erstellt ein neues `COleSafeArray` eindimensionales Objekt.

```
void CreateOneDim(
    VARTYPE vtSrc,
    DWORD dwElements,
    const void* pvSrcData = NULL,
    long nLBound = 0);
```

### <a name="parameters"></a>Parameter

*vtSrc*<br/>
Der Basistyp des Arrays (d. h. der VARTYPE jedes Elements des Arrays).

*dwElements*<br/>
Anzahl der Elemente im Array. Dies kann geändert werden, nachdem das Array mit [ResizeOneDim](#resizeonedim)erstellt wurde.

*pvSrcData*<br/>
Zeigen Sie auf die Daten, die in das Array kopiert werden sollen.

*nLBound*<br/>
Die untere Grenze des Arrays.

### <a name="remarks"></a>Bemerkungen

Die Funktion ordnet und initialisiert die Daten für das Array, indem die angegebenen Daten kopiert werden, wenn der Zeiger *pvSrcData* nicht NULL ist.

Bei einem Fehler löst die Funktion eine [CMemoryException](../../mfc/reference/cmemoryexception-class.md)aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#28](../../mfc/codesnippet/cpp/colesafearray-class_3.cpp)]

## <a name="colesafearraydestroy"></a><a name="destroy"></a>COleSafeArray::Destroy

Zerstört einen vorhandenen Arraydeskriptor und alle Daten im Array.

```
void Destroy();
```

### <a name="remarks"></a>Bemerkungen

Wenn Objekte im Array gespeichert werden, wird jedes Objekt freigegeben. Bei Fehler löst die Funktion eine [CMemoryException](../../mfc/reference/cmemoryexception-class.md) oder [COleException](../../mfc/reference/coleexception-class.md)aus.

## <a name="colesafearraydestroydata"></a><a name="destroydata"></a>COleSafeArray::DestroyData

Zerstört alle Daten in einem sicheren Array.

```
void DestroyData();
```

### <a name="remarks"></a>Bemerkungen

Wenn Objekte im Array gespeichert werden, wird jedes Objekt freigegeben. Bei Fehler löst die Funktion eine [CMemoryException](../../mfc/reference/cmemoryexception-class.md) oder [COleException](../../mfc/reference/coleexception-class.md)aus.

## <a name="colesafearraydestroydescriptor"></a><a name="destroydescriptor"></a>COleSafeArray::DestroyDescriptor

Zerstört einen Deskriptor eines sicheren Arrays.

```
void DestroyDescriptor();
```

### <a name="remarks"></a>Bemerkungen

Bei Fehler löst die Funktion eine [CMemoryException](../../mfc/reference/cmemoryexception-class.md) oder [COleException](../../mfc/reference/coleexception-class.md)aus.

## <a name="colesafearraydetach"></a><a name="detach"></a>COleSafeArray::Detach

Trennt die `VARIANT` Daten vom `COleSafeArray` Objekt.

```
VARIANT Detach();
```

### <a name="return-value"></a>Rückgabewert

Der `VARIANT` zugrunde liegende `COleSafeArray` Wert im Objekt.

### <a name="remarks"></a>Bemerkungen

Die Funktion trennt die Daten in einem sicheren Array, indem sie den VARTYPE des Objekts auf VT_EMPTY. Es liegt in der Verantwortung des Aufrufers, das Array freizugeben, indem die Windows-Funktion [VariantClear](/windows/win32/api/oleauto/nf-oleauto-variantclear)aufgerufen wird.

Bei einem Fehler löst die Funktion eine [COleException](../../mfc/reference/coleexception-class.md)aus.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [COleSafeArray::PutElement](#putelement).

## <a name="colesafearraygetbytearray"></a><a name="getbytearray"></a>COleSafeArray::GetByteArray

Kopiert den Inhalt des sicheren `CByteArray`Arrays in eine .

```
void GetByteArray(CByteArray& bytes);
```

### <a name="parameters"></a>Parameter

*Bytes*<br/>
Ein Verweis auf ein [CByteArray-Objekt.](../../mfc/reference/cbytearray-class.md)

## <a name="colesafearraygetdim"></a><a name="getdim"></a>COleSafeArray::GetDim

Gibt die Anzahl der `COleSafeArray` Dimensionen im Objekt zurück.

```
DWORD GetDim();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Dimensionen im sicheren Array.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#27](../../mfc/codesnippet/cpp/colesafearray-class_2.cpp)]

## <a name="colesafearraygetelement"></a><a name="getelement"></a>COleSafeArray::GetElement

Ruft ein einzelnes Element des sicheren Arrays ab.

```
void GetElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Parameter

*rgIndizes*<br/>
Zeiger auf ein Array von Indizes für jede Dimension des Arrays.

*pvData*<br/>
Zeigen Sie auf die Position, an der das Element des Arrays platziert werden soll.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ruft automatisch `SafeArrayLock` `SafeArrayUnlock` die Windows-Funktionen und vor und nach dem Abrufen des Elements auf. Wenn es sich bei dem Datenelement um eine Zeichenfolge, ein Objekt oder eine Variante handelt, kopiert die Funktion das Element auf die richtige Weise. Der Parameter *pvData* sollte auf einen ausreichend großen Puffer verweisen, der das Element enthält.

Bei Fehler löst die Funktion eine [CMemoryException](../../mfc/reference/cmemoryexception-class.md) oder [COleException](../../mfc/reference/coleexception-class.md)aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#29](../../mfc/codesnippet/cpp/colesafearray-class_4.cpp)]

## <a name="colesafearraygetelemsize"></a><a name="getelemsize"></a>COleSafeArray::GetElemSize

Ruft die Größe eines Elements `COleSafeArray` in einem Objekt ab.

```
DWORD GetElemSize();
```

### <a name="return-value"></a>Rückgabewert

Die Größe der Elemente eines sicheren Arrays in Bytes.

## <a name="colesafearraygetlbound"></a><a name="getlbound"></a>COleSafeArray::GetLbound

Gibt die untere Grenze `COleSafeArray` für jede Dimension eines Objekts zurück.

```
void GetLBound(
    DWORD dwDim,
    long* pLBound);
```

### <a name="parameters"></a>Parameter

*dwDim*<br/>
Die Arraydimension, für die die untere Grenze abzurufen ist.

*pLBound*<br/>
Zeigen Sie auf die Position, um die untere Grenze zurückzugeben.

### <a name="remarks"></a>Bemerkungen

Bei einem Fehler löst die Funktion eine [COleException](../../mfc/reference/coleexception-class.md)aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#30](../../mfc/codesnippet/cpp/colesafearray-class_5.cpp)]

## <a name="colesafearraygetonedimsize"></a><a name="getonedimsize"></a>COleSafeArray::GetOneDimSize

Gibt die Anzahl der Elemente `COleSafeArray` im eindimensionalen Objekt zurück.

```
DWORD GetOneDimSize();
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im eindimensionalen sicheren Array.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [COleSafeArray::CreateOneDim](#createonedim).

## <a name="colesafearraygetubound"></a><a name="getubound"></a>COleSafeArray::Getubound

Gibt die Obergrenze für jede Dimension eines sicheren Arrays zurück.

```
void GetUBound(
    DWORD dwDim,
    long* pUBound);
```

### <a name="parameters"></a>Parameter

*dwDim*<br/>
Die Arraydimension, für die die obere Grenze abzurufen ist.

*pUBound*<br/>
Zeigen Sie auf die Position, um die obere Grenze zurückzugeben.

### <a name="remarks"></a>Bemerkungen

Bei einem Fehler löst die Funktion eine [COleException](../../mfc/reference/coleexception-class.md)aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#31](../../mfc/codesnippet/cpp/colesafearray-class_6.cpp)]

## <a name="colesafearraylock"></a><a name="lock"></a>COleSafeArray::Sperre

Erhöht die Sperranzahl eines Arrays und platziert einen Zeiger auf die Arraydaten im Arraydeskriptor.

```
void Lock();
```

### <a name="remarks"></a>Bemerkungen

Bei einem Fehler wird eine [COleException](../../mfc/reference/coleexception-class.md)ausgelöst.

Der Zeiger im Arraydeskriptor ist `Unlock` gültig, bis er aufgerufen wird. Aufrufe `Lock` zu können geschachtelt werden; eine gleiche Anzahl `Unlock` von Anrufen erforderlich sind.

Ein Array kann nicht gelöscht werden, während es gesperrt ist.

## <a name="colesafearrayoperator-lpcvariant"></a><a name="operator_lpcvariant"></a>COleSafeArray::operator LPCVARIANT

Rufen Sie diesen Umwandlungsoperator auf, um auf die zugrunde liegende `VARIANT` Struktur für dieses `COleSafeArray` Objekt zuzugreifen.

```
operator LPCVARIANT() const;
```

## <a name="colesafearrayoperator-lpvariant"></a><a name="operator_lpvariant"></a>COleSafeArray::operator LPVARIANT

Rufen Sie diesen Umwandlungsoperator auf, um auf die zugrunde liegende `VARIANT` Struktur für dieses `COleSafeArray` Objekt zuzugreifen.

```
operator LPVARIANT();
```

### <a name="remarks"></a>Bemerkungen

Beachten Sie, dass `VARIANT` das Ändern des Werts in der Struktur, `COleSafeArray` auf die der Zeiger zugriff, der von dieser Funktion zurückgegeben wird, den Wert dieses Objekts ändert.

## <a name="colesafearrayoperator-"></a><a name="operator_eq"></a>COleSafeArray::operator =

Diese überladenen Zuweisungsoperatoren `COleSafeArray` kopieren den Quellwert in dieses Objekt.

```
COleSafeArray& operator=(const COleSafeArray& saSrc);
COleSafeArray& operator=(const VARIANT& varSrc);
COleSafeArray& operator=(LPCVARIANT pSrc);
COleSafeArray& operator=(const COleVariant& varSrc);
```

### <a name="remarks"></a>Bemerkungen

Eine kurze Beschreibung der einzelnen Operatoren folgt:

- **Operator =(** *saSrc* **)** Kopiert ein `COleSafeArray` vorhandenes Objekt in dieses Objekt.

- **Operator =(** *varSrc* **)** Kopiert ein `VARIANT` `COleVariant` vorhandenes oder Array in dieses Objekt.

- **Operator =(** *pSrc* **)** Kopiert `VARIANT` das Arrayobjekt, auf das *pSrc* zugreift.

## <a name="colesafearrayoperator-"></a><a name="operator_eq_eq"></a>COleSafeArray::operator ==

Dieser Operator vergleicht zwei`SAFEARRAY` `VARIANT`Arrays ( , , `COleVariant`, oder `COleSafeArray` Arrays) und gibt einen Wert ungleich null zurück, wenn sie gleich sind. andernfalls 0.

```
BOOL operator==(const SAFEARRAY& saSrc) const;  BOOL operator==(LPCSAFEARRAY pSrc) const;

BOOL operator==(const COleSafeArray& saSrc) const;  BOOL operator==(const VARIANT& varSrc) const;

BOOL operator==(LPCVARIANT pSrc) const;  BOOL operator==(const COleVariant& varSrc) const;
```

### <a name="remarks"></a>Bemerkungen

Zwei Arrays sind gleich, wenn sie eine gleiche Anzahl von Dimensionen, gleiche Größe in jeder Dimension und gleiche Elementwerte aufweisen.

## <a name="colesafearrayoperator-ltlt"></a><a name="operator_lt_lt"></a>COleSafeArray::Operator&lt;&lt;

Der `COleSafeArray` Operator einfügen (<<) unterstützt diagnosendes Dumping und speichern eines `COleSafeArray` Objekts in einem Archiv.

```
CDumpContext& AFXAPI operator<<(
    CDumpContext& dc,
    COleSafeArray& saSrc);
```

## <a name="colesafearrayptrofindex"></a><a name="ptrofindex"></a>COleSafeArray::PtrOfIndex

Gibt einen Zeiger auf das element zurück, das durch die Indexwerte angegeben wird.

```
void PtrOfIndex(
    long* rgIndices,
    void** ppvData);
```

### <a name="parameters"></a>Parameter

*rgIndizes*<br/>
Ein Array von Indexwerten, die ein Element des Arrays identifizieren. Alle Indizes für das Element müssen angegeben werden.

*ppvData*<br/>
Zeiger auf das Element, das durch die Werte in *rgIndices*identifiziert wird.

## <a name="colesafearrayputelement"></a><a name="putelement"></a>COleSafeArray::PutElement

Weist ein einzelnes Element im Array zu.

```
void PutElement(
    long* rgIndices,
    void* pvData);
```

### <a name="parameters"></a>Parameter

*rgIndizes*<br/>
Zeiger auf ein Array von Indizes für jede Dimension des Arrays.

*pvData*<br/>
Zeiger auf die Daten, die dem Array zuzuweisen sind. VT_DISPATCH, VT_UNKNOWN und VT_BSTR Variantentypen sind Zeiger und erfordern keine weitere Indirektionsebene.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ruft automatisch die [Windows-Funktionen SafeArrayLock](/windows/win32/api/oleauto/nf-oleauto-safearraylock) und [SafeArrayUnlock](/windows/win32/api/oleauto/nf-oleauto-safearrayunlock) vor und nach dem Zuweisen des Elements auf. Ist das Datenelement eine Zeichenfolge, ein Objekt oder eine Variante, kopiert die Funktion es korrekt, und wenn das vorhandene Element eine Zeichenfolge, ein Objekt oder eine Variante ist, wird es korrekt gelöscht.

Beachten Sie, dass Sie mehrere Sperren auf einem Array verwenden können, damit Sie Elemente in einem Array platzieren können, während das Array durch andere Vorgänge gesperrt ist.

Bei Fehler löst die Funktion eine [CMemoryException](../../mfc/reference/cmemoryexception-class.md) oder [COleException](../../mfc/reference/coleexception-class.md)aus.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCOleContainer#32](../../mfc/codesnippet/cpp/colesafearray-class_7.cpp)]

## <a name="colesafearrayredim"></a><a name="redim"></a>COleSafeArray::Redim

Ändert die am wenigsten signifikante (rechts) gebundene Grenze eines sicheren Arrays.

```
void Redim(SAFEARRAYBOUND* psaboundNew);
```

### <a name="parameters"></a>Parameter

*psaboundNeu*<br/>
Zeiger auf eine neue sichere Array-gebundene Struktur, die die neue Array-Gebundene enthält. Nur die am wenigsten signifikante Dimension eines Arrays kann geändert werden.

### <a name="remarks"></a>Bemerkungen

Bei einem Fehler löst die Funktion eine [COleException](../../mfc/reference/coleexception-class.md)aus.

## <a name="colesafearrayresizeonedim"></a><a name="resizeonedim"></a>COleSafeArray::ResizeOneDim

Ändert die Anzahl der Elemente `COleSafeArray` in einem eindimensionalen Objekt.

```
void ResizeOneDim(DWORD dwElements);
```

### <a name="parameters"></a>Parameter

*dwElements*<br/>
Anzahl der Elemente im eindimensionalen sicheren Array.

### <a name="remarks"></a>Bemerkungen

Bei einem Fehler löst die Funktion eine [COleException](../../mfc/reference/coleexception-class.md)aus.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [COleSafeArray::CreateOneDim](#createonedim).

## <a name="colesafearrayunaccessdata"></a><a name="unaccessdata"></a>COleSafeArray::UnaccessData

Dekrementiert die Sperranzahl eines Arrays und macht `AccessData`den von abgerufenen Zeiger ungültig.

```
void UnaccessData();
```

### <a name="remarks"></a>Bemerkungen

Bei einem Fehler löst die Funktion eine [COleException](../../mfc/reference/coleexception-class.md)aus.

### <a name="example"></a>Beispiel

  Siehe Beispiel für [COleSafeArray::AccessData](#accessdata).

## <a name="colesafearrayunlock"></a><a name="unlock"></a>COleSafeArray::Entsperren

Dekrementiert die Sperranzahl eines Arrays, sodass es freigegeben oder in der Größe geändert werden kann.

```
void Unlock();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird aufgerufen, nachdem der Zugriff auf die Daten in einem Array abgeschlossen ist. Bei einem Fehler wird eine [COleException](../../mfc/reference/coleexception-class.md)ausgelöst.

## <a name="see-also"></a>Siehe auch

[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[COleVariant-Klasse](../../mfc/reference/colevariant-class.md)<br/>
[CRecordset-Klasse](../../mfc/reference/crecordset-class.md)<br/>
[CDatabase-Klasse](../../mfc/reference/cdatabase-class.md)<br/>

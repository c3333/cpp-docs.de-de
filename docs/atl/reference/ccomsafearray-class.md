---
title: CComSafeArray-Klasse
ms.date: 05/06/2019
f1_keywords:
- CComSafeArray
- ATLSAFE/ATL::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::Add
- ATLSAFE/ATL::CComSafeArray::Attach
- ATLSAFE/ATL::CComSafeArray::CopyFrom
- ATLSAFE/ATL::CComSafeArray::CopyTo
- ATLSAFE/ATL::CComSafeArray::Create
- ATLSAFE/ATL::CComSafeArray::Destroy
- ATLSAFE/ATL::CComSafeArray::Detach
- ATLSAFE/ATL::CComSafeArray::GetAt
- ATLSAFE/ATL::CComSafeArray::GetCount
- ATLSAFE/ATL::CComSafeArray::GetDimensions
- ATLSAFE/ATL::CComSafeArray::GetLowerBound
- ATLSAFE/ATL::CComSafeArray::GetSafeArrayPtr
- ATLSAFE/ATL::CComSafeArray::GetType
- ATLSAFE/ATL::CComSafeArray::GetUpperBound
- ATLSAFE/ATL::CComSafeArray::IsSizable
- ATLSAFE/ATL::CComSafeArray::MultiDimGetAt
- ATLSAFE/ATL::CComSafeArray::MultiDimSetAt
- ATLSAFE/ATL::CComSafeArray::Resize
- ATLSAFE/ATL::CComSafeArray::SetAt
- ATLSAFE/ATL::CComSafeArray::m_psa
helpviewer_keywords:
- CComSafeArray class
ms.assetid: ee349aef-33db-4c85-bd08-5d86a3c9d53a
ms.openlocfilehash: d1e72d364858ea31541d574ed77bdc8ccca7d748
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327392"
---
# <a name="ccomsafearray-class"></a>CComSafeArray-Klasse

Diese Klasse ist ein `SAFEARRAY` Wrapper für die Struktur.

## <a name="syntax"></a>Syntax

```
template <typename T, VARTYPE _vartype = _ATL_AutomationType<T>::type>
class CComSafeArray
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ der im Array gespeicherten Daten.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComSafeArray::CComSafeArray](#ccomsafearray)|Der Konstruktor.|
|[CComSafeArray::-CComSafeArray](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComSafeArray::Hinzufügen](#add)|Fügt einem `CComSafeArray`ein oder `SAFEARRAY` mehrere Elemente oder eine Struktur hinzu.|
|[CComSafeArray::Anfügen](#attach)|Fügt eine `SAFEARRAY` Struktur `CComSafeArray` an ein Objekt an.|
|[CComSafeArray::Kopievon](#copyfrom)|Kopiert den Inhalt `SAFEARRAY` einer `CComSafeArray` Struktur in das Objekt.|
|[CComSafeArray::CopyTo](#copyto)|Erstellt eine Kopie des `CComSafeArray`-Objekts.|
|[CComSafeArray::Create](#create)|Erstellt ein `CComSafeArray` -Objekt.|
|[CComSafeArray::Destroy](#destroy)|Zerstört ein `CComSafeArray` -Objekt.|
|[CComSafeArray::Detach](#detach)|Trennt eine `SAFEARRAY` von `CComSafeArray` einem Objekt.|
|[CComSafeArray::Getat](#getat)|Ruft ein einzelnes Element aus einem eindimensionalen Array ab.|
|[CComSafeArray::GetCount](#getcount)|Gibt die Anzahl der Elemente des Arrays zurück.|
|[CComSafeArray::GetDimensions](#getdimensions)|Gibt die Anzahl der Dimensionen des Arrays zurück.|
|[CComSafeArray::GetLowerbound](#getlowerbound)|Gibt die untere Grenze für eine bestimmte Dimension des Arrays zurück.|
|[CComSafeArray::GetSafeArrayPtr](#getsafearrayptr)|Gibt die Adresse des `m_psa` -Datenelements zurück.|
|[CComSafeArray::GetType](#gettype)|Gibt den Typ der im Array gespeicherten Daten zurück.|
|[CComSafeArray::GetUpperbound](#getupperbound)|Gibt die obere Grenze für eine bestimmte Dimension des Arrays zurück.|
|[CComSafeArray::IsSisisable](#issizable)|Testet, ob die Größe eines `CComSafeArray` -Objekts geändert werden kann.|
|[CComSafeArray::MultiDimGetAt](#multidimgetat)|Ruft ein einzelnes Element aus einem mehrdimensionalen Array ab.|
|[CComSafeArray::MultiDimSetAt](#multidimsetat)|Legt den Wert eines Elements in einem mehrdimensionalen Array fest.|
|[CComSafeArray::Größe ändern](#resize)|Ändert die Größe eines `CComSafeArray` -Objekts.|
|[CComSafeArray::Setat](#setat)|Legt den Wert eines Elements in einem eindimensionalen Array fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComSafeArray::operator LPSAFEARRAY](#operator_lpsafearray)|Gibt einen Wert `SAFEARRAY` auf einen Zeiger um.|
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|Ruft ein Element aus dem Array ab.|
|[CComSafeArray::operator =](#operator_eq)|Zuweisungsoperator.|

### <a name="public-data-members"></a>Öffentliche Datenmember

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CComSafeArray::m_psa](#m_psa)|Dieses Datenelement enthält die `SAFEARRAY` Adresse der Struktur.|

## <a name="remarks"></a>Bemerkungen

`CComSafeArray`stellt einen Wrapper für die [SAFEARRAY Data Type-Klasse](/windows/win32/api/oaidl/ns-oaidl-safearray) bereit, sodass es einfach ist, ein- und mehrdimensionale Arrays fast aller VARIANT-unterstützten Typen zu erstellen und zu verwalten.

`CComSafeArray` vereinfacht die Übergabe von Arrays zwischen Prozessen und bietet darüber hinaus zusätzliche Sicherheit durch Überprüfen der Arrayindexwerte anhand der oberen und unteren Grenzen.

Die untere Grenze eines `CComSafeArray` kann bei einem beliebigen benutzerdefinierten Wert beginnen, Arrays, auf die über C++ zugegriffen wird, sollte jedoch eine Untergrenze von 0 verwenden. Andere Sprachen wie Visual Basic können andere Begrenzungswerte (z. B. -10 bis 10) verwenden.

Verwenden Sie [CComSafeArray::Create](#create) , um ein `CComSafeArray` -Objekt zu erstellen, und [CComSafeArray::Destroy](#destroy) , um es zu löschen.

Ein `CComSafeArray` kann die folgende Teilmenge von VARIANT-Datentypen enthalten:

|VARTYPE|BESCHREIBUNG|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|INT|
|VT_I4|long|
|VT_I8|longlong|
|VT_UI1|byte|
|VT_UI2|ushort|
|VT_UI4|uint|
|VT_UI4|ulong|
|VT_UI8|ulonglong|
|VT_R4|float|
|VT_R8|double|
|VT_DECIMAL|Dezimalzeiger|
|VT_VARIANT|Variant-Zeiger|
|VT_CY|Currency-Datentyp|

## <a name="requirements"></a>Anforderungen

**Header:** atlsafe.h

## <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]

## <a name="ccomsafearrayadd"></a><a name="add"></a>CComSafeArray::Hinzufügen

Fügt einem `CComSafeArray`ein oder `SAFEARRAY` mehrere Elemente oder eine Struktur hinzu.

```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Parameter

*psaSrc*<br/>
Ein Zeiger auf ein `SAFEARRAY`-Objekt.

*ulCount*<br/>
Die Anzahl der Objekte, die dem Array hinzugefügt werden sollen.

*Pt*<br/>
Ein Zeiger auf ein oder mehrere Objekte, die dem Array hinzugefügt werden sollen.

*T*<br/>
Ein Verweis auf das Objekt, das dem Array hinzugefügt werden soll.

*bKopie*<br/>
Gibt an, ob eine Kopie der Daten erstellt werden soll. Der Standardwert ist TRUE.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Die neuen Objekte werden an das `SAFEARRAY` Ende des vorhandenen Objekts angehängt. Das Hinzufügen eines Objekts zu einem mehrdimensionalen `SAFEARRAY` Objekt wird nicht unterstützt. Beim Hinzufügen eines vorhandenen Arrays von Objekten müssen beide Arrays Elemente desselben Typs enthalten.

Das *bCopy-Flag* wird berücksichtigt, wenn Elemente vom Typ BSTR oder VARIANT zu einem Array hinzugefügt werden. Der Standardwert TRUE stellt sicher, dass eine neue Kopie der Daten erstellt wird, wenn das Element dem Array hinzugefügt wird.

## <a name="ccomsafearrayattach"></a><a name="attach"></a>CComSafeArray::Anfügen

Fügt eine `SAFEARRAY` Struktur `CComSafeArray` an ein Objekt an.

```
HRESULT Attach(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parameter

*psaSrc*<br/>
Ein Zeiger auf `SAFEARRAY` die Struktur.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Fügt einem `SAFEARRAY` `CComSafeArray` Objekt eine Struktur an, wodurch die vorhandenen `CComSafeArray` Methoden verfügbar sind.

## <a name="ccomsafearrayccomsafearray"></a><a name="ccomsafearray"></a>CComSafeArray::CComSafeArray

Der Konstruktor.

```
CComSafeArray();
CComSafeArray(const SAFEARRAYBOUND& bound);
CComSafeArray(ULONG  ulCount, LONG lLBound = 0);
CComSafeArray(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
CComSafeArray(const CComSafeArray& saSrc);
CComSafeArray(const SAFEARRAY& saSrc);
CComSafeArray(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parameter

*Gebunden*<br/>
Eine `SAFEARRAYBOUND`-Struktur.

*ulCount*<br/>
Die Anzahl der Elemente im Array.

*lLBound*<br/>
Der untere Grenzwertwert; d. h. der Index des ersten Elements im Array.

*pBound*<br/>
Ein Zeiger auf `SAFEARRAYBOUND` eine Struktur.

*uDims*<br/>
Die Anzahl der Dimensionen im Array.

*saSrc*<br/>
Ein Verweis `SAFEARRAY` auf `CComSafeArray` eine Struktur oder ein Objekt. In beiden Fällen verwendet der Konstruktor diesen Verweis, um eine Kopie des Arrays zu erstellen, sodass nach der Konstruktion nicht auf das Array verwiesen wird.

*psaSrc*<br/>
Ein Zeiger auf `SAFEARRAY` eine Struktur. Der Konstruktor verwendet diese Adresse, um eine Kopie des Arrays zu erstellen, sodass nach der Konstruktion nicht auf das Array verwiesen wird.

### <a name="remarks"></a>Bemerkungen

Erstellt ein `CComSafeArray` -Objekt.

## <a name="ccomsafearrayccomsafearray"></a><a name="dtor"></a>CComSafeArray::-CComSafeArray

Der Destruktor.

```
~CComSafeArray() throw()
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugewiesenen Ressourcen frei.

## <a name="ccomsafearraycopyfrom"></a><a name="copyfrom"></a>CComSafeArray::Kopievon

Kopiert den Inhalt `SAFEARRAY` einer `CComSafeArray` Struktur in das Objekt.

```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Parameter

*ppArray*<br/>
Zeiger auf `SAFEARRAY` den zu kopierenden.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode kopiert den `SAFEARRAY` Inhalt `CComSafeArray` eines in das aktuelle Objekt. Der vorhandene Inhalt des Arrays wird ersetzt.

## <a name="ccomsafearraycopyto"></a><a name="copyto"></a>CComSafeArray::CopyTo

Erstellt eine Kopie des `CComSafeArray`-Objekts.

```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Parameter

*ppArray*<br/>
Ein Zeiger auf eine Position, an `SAFEARRAY`der die neue erstellt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode kopiert den `CComSafeArray` Inhalt `SAFEARRAY` eines Objekts in eine Struktur.

## <a name="ccomsafearraycreate"></a><a name="create"></a>CComSafeArray::Erstellen

Erstellt ein `CComSafeArray`-Struktur hinzu.

```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```

### <a name="parameters"></a>Parameter

*pBound*<br/>
Ein Zeiger auf ein `SAFEARRAYBOUND`-Objekt.

*uDims*<br/>
Die Anzahl der Dimensionen im Array.

*ulCount*<br/>
Die Anzahl der Elemente im Array.

*lLBound*<br/>
Der untere Grenzwertwert; d. h. der Index des ersten Elements im Array.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Ein `CComSafeArray` Objekt kann aus `SAFEARRAYBOUND` einer vorhandenen Struktur und der Anzahl der Dimensionen erstellt werden, oder indem die Anzahl der Elemente im Array und die untere Grenze angegeben wird. Wenn auf das Array von C++ aus zugegriffen werden soll, sollte die untere Grenze 0 sein. Andere Sprachen können andere Werte für die Untergrenze zulassen (z. B. unterstützt Visual Basic Arrays mit Elementen mit einem Bereich wie -10 bis 10).

## <a name="ccomsafearraydestroy"></a><a name="destroy"></a>CComSafeArray::Destroy

Zerstört ein `CComSafeArray` -Objekt.

```
HRESULT Destroy();
```

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Zerstört ein `CComSafeArray` vorhandenes Objekt und alle darin enthaltenen Daten.

## <a name="ccomsafearraydetach"></a><a name="detach"></a>CComSafeArray::Detach

Trennt eine `SAFEARRAY` von `CComSafeArray` einem Objekt.

```
LPSAFEARRAY Detach();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger `SAFEARRAY` auf ein Objekt zurück.

### <a name="remarks"></a>Bemerkungen

Diese Methode trennt `SAFEARRAY` das Objekt `CComSafeArray` vom Objekt.

## <a name="ccomsafearraygetat"></a><a name="getat"></a>CComSafeArray::Getat

Ruft ein einzelnes Element aus einem eindimensionalen Array ab.

```
T& GetAt(LONG lIndex) const;
```

### <a name="parameters"></a>Parameter

*Lindex*<br/>
Die Indexnummer des zurückzugebenden Werts im Array.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf das erforderliche Arrayelement zurück.

## <a name="ccomsafearraygetcount"></a><a name="getcount"></a>CComSafeArray::GetCount

Gibt die Anzahl der Elemente des Arrays zurück.

```
ULONG GetCount(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parameter

*uDim*<br/>
Die Array-Dimension.

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Elemente des Arrays zurück.

### <a name="remarks"></a>Bemerkungen

Bei Verwendung mit einem mehrdimensionalen Array gibt diese Methode nur die Anzahl der Elemente in einer bestimmten Dimension zurück.

## <a name="ccomsafearraygetdimensions"></a><a name="getdimensions"></a>CComSafeArray::GetDimensions

Gibt die Anzahl der Dimensionen des Arrays zurück.

```
UINT GetDimensions() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Dimensionen des Arrays zurück.

## <a name="ccomsafearraygetlowerbound"></a><a name="getlowerbound"></a>CComSafeArray::GetLowerbound

Gibt die untere Grenze für eine bestimmte Dimension des Arrays zurück.

```
LONG GetLowerBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parameter

*uDim*<br/>
Die Arraydimension, für die die untere Grenze abzurufen ist. Wenn nicht angegeben, ist der Standardwert 0.

### <a name="return-value"></a>Rückgabewert

Gibt die Untergrenze zurück.

### <a name="remarks"></a>Bemerkungen

Wenn die untere Grenze 0 ist, gibt dies ein C-ähnliches Array an, dessen erstes Element elementnummer 0 ist. Im Falle eines Fehlers, z. B. eines ungültigen Dimensionsarguments, ruft diese Methode mit einem HRESULT auf, `AtlThrow` das den Fehler beschreibt.

## <a name="ccomsafearraygetsafearrayptr"></a><a name="getsafearrayptr"></a>CComSafeArray::GetSafeArrayPtr

Gibt die Adresse des `m_psa` -Datenelements zurück.

```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf das [CComSafeArray::m_psa](#m_psa) Datenmember zurück.

## <a name="ccomsafearraygettype"></a><a name="gettype"></a>CComSafeArray::GetType

Gibt den Typ der im Array gespeicherten Daten zurück.

```
VARTYPE GetType() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt den im Array gespeicherten Datentyp zurück, der einer der folgenden Typen sein kann:

|VARTYPE|BESCHREIBUNG|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|INT|
|VT_I4|long|
|VT_I8|longlong|
|VT_UI1|byte|
|VT_UI2|ushort|
|VT_UI4|uint|
|VT_UI4|ulong|
|VT_UI8|ulonglong|
|VT_R4|float|
|VT_R8|double|
|VT_DECIMAL|Dezimalzeiger|
|VT_VARIANT|Variant-Zeiger|
|VT_CY|Currency-Datentyp|

## <a name="ccomsafearraygetupperbound"></a><a name="getupperbound"></a>CComSafeArray::GetUpperbound

Gibt die obere Grenze für eine bestimmte Dimension des Arrays zurück.

```
LONG GetUpperBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parameter

*uDim*<br/>
Die Arraydimension, für die die obere Grenze abzurufen ist. Wenn nicht angegeben, ist der Standardwert 0.

### <a name="return-value"></a>Rückgabewert

Gibt die obere Grenze zurück. Dieser Wert ist inklusive, der maximal gültige Index für diese Dimension.

### <a name="remarks"></a>Bemerkungen

Im Falle eines Fehlers, z. B. eines ungültigen Dimensionsarguments, ruft diese Methode mit einem HRESULT auf, `AtlThrow` das den Fehler beschreibt.

## <a name="ccomsafearrayissizable"></a><a name="issizable"></a>CComSafeArray::IsSisisable

Testet, ob die Größe eines `CComSafeArray` -Objekts geändert werden kann.

```
bool IsSizable() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt TRUE `CComSafeArray` zurück, wenn die Größe geändert werden kann, FALSE, wenn dies nicht möglich ist.

## <a name="ccomsafearraym_psa"></a><a name="m_psa"></a>CComSafeArray::m_psa

Enthält die Adresse `SAFEARRAY` der Struktur, auf die zugegriffen wird.

```
LPSAFEARRAY m_psa;
```

## <a name="ccomsafearraymultidimgetat"></a><a name="multidimgetat"></a>CComSafeArray::MultiDimGetAt

Ruft ein einzelnes Element aus einem mehrdimensionalen Array ab.

```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```

### <a name="parameters"></a>Parameter

*alIndex*<br/>
Zeiger auf einen Vektor von Indizes für jede Dimension im Array. Die linke (bedeutendste) Dimension `alIndex[0]`ist .

*T*<br/>
Ein Verweis auf die zurückgegebenen Daten.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

## <a name="ccomsafearraymultidimsetat"></a><a name="multidimsetat"></a>CComSafeArray::MultiDimSetAt

Legt den Wert eines Elements in einem mehrdimensionalen Array fest.

```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```

### <a name="parameters"></a>Parameter

*alIndex*<br/>
Zeiger auf einen Vektor von Indizes für jede Dimension im Array. Die rechte (am wenigsten `alIndex`signifikante) Dimension ist [0].

*T*<br/>
Gibt den Wert des neuen Elements an.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Dies ist eine mehrdimensionale Version von [CComSafeArray::SetAt](#setat).

## <a name="ccomsafearrayoperator-"></a><a name="operator_at"></a>CComSafeArray::Operator\[\]

Ruft ein Element aus dem Array ab.

```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```

### <a name="parameters"></a>Parameter

*lIndex, nIndex*<br/>
Die Indexnummer des erforderlichen Elements im Array.

### <a name="return-value"></a>Rückgabewert

Gibt das entsprechende Arrayelement zurück.

### <a name="remarks"></a>Bemerkungen

Führt eine ähnliche Funktion wie [CComSafeArray::GetAt](#getat)aus, dieser Operator funktioniert jedoch nur mit eindimensionalen Arrays.

## <a name="ccomsafearrayoperator-"></a><a name="operator_eq"></a>CComSafeArray::operator =

Zuweisungsoperator.

```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parameter

*saSrc*<br/>
Ein Verweis auf ein `CComSafeArray`-Objekt.

*psaSrc*<br/>
Ein Zeiger auf ein `SAFEARRAY`-Objekt.

### <a name="return-value"></a>Rückgabewert

Gibt den Typ der im Array gespeicherten Daten zurück.

## <a name="ccomsafearrayoperator-lpsafearray"></a><a name="operator_lpsafearray"></a>CComSafeArray::operator LPSAFEARRAY

Gibt einen Wert `SAFEARRAY` auf einen Zeiger um.

```
operator LPSAFEARRAY() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert `SAFEARRAY` auf einen Zeiger um.

## <a name="ccomsafearrayresize"></a><a name="resize"></a>CComSafeArray::Größe ändern

Ändert die Größe eines `CComSafeArray` -Objekts.

```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```

### <a name="parameters"></a>Parameter

*pBound*<br/>
Ein Zeiger auf `SAFEARRAYBOUND` eine Struktur, die Informationen über die Anzahl der Elemente und die Untergrenze eines Arrays enthält.

*ulCount*<br/>
Die angeforderte Anzahl von Objekten im Array mit geänderter Größe.

*lLBound*<br/>
Die untere Grenze.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Bei dieser Methode wird nur die Größe der ganz richtigen Dimension geändert. Die Größe von Arrays, `IsResizable` die als FALSE zurückgegeben werden, wird nicht geändert.

## <a name="ccomsafearraysetat"></a><a name="setat"></a>CComSafeArray::Setat

Legt den Wert eines Elements in einem eindimensionalen Array fest.

```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Parameter

*Lindex*<br/>
Die Indexnummer des festzulegenden Arrayelements.

*T*<br/>
Der neue Wert des angegebenen Elements.

*bKopie*<br/>
Gibt an, ob eine Kopie der Daten erstellt werden soll. Der Standardwert ist TRUE.

### <a name="return-value"></a>Rückgabewert

Gibt S_OK bei Erfolg oder einen Fehler HRESULT bei einem Fehler zurück.

### <a name="remarks"></a>Bemerkungen

Das *bCopy-Flag* wird berücksichtigt, wenn Elemente vom Typ BSTR oder VARIANT zu einem Array hinzugefügt werden. Der Standardwert TRUE stellt sicher, dass eine neue Kopie der Daten erstellt wird, wenn das Element dem Array hinzugefügt wird.

## <a name="see-also"></a>Siehe auch

[SAFEARRAY Data Type](/windows/win32/api/oaidl/ns-oaidl-safearray)<br/>
[CComSafeArray::Create](#create)<br/>
[CComSafeArray::Destroy](#destroy)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)

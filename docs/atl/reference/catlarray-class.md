---
title: CAtlArray-Klasse
ms.date: 11/04/2016
f1_keywords:
- CAtlArray
- ATLCOLL/ATL::CAtlArray
- ATLCOLL/ATL::Add
- ATLCOLL/ATL::Append
- ATLCOLL/ATL::AssertValid
- ATLCOLL/ATL::Copy
- ATLCOLL/ATL::FreeExtra
- ATLCOLL/ATL::GetAt
- ATLCOLL/ATL::GetCount
- ATLCOLL/ATL::GetData
- ATLCOLL/ATL::InsertArrayAt
- ATLCOLL/ATL::InsertAt
- ATLCOLL/ATL::IsEmpty
- ATLCOLL/ATL::RemoveAll
- ATLCOLL/ATL::RemoveAt
- ATLCOLL/ATL::SetAt
- ATLCOLL/ATL::SetAtGrow
- ATLCOLL/ATL::SetCount
- ATLCOLL/ATL::INARGTYPE
- ATLCOLL/ATL::OUTARGTYPE
helpviewer_keywords:
- CAtlArray class
ms.assetid: 0b503aa8-2357-40af-a326-6654bf1da098
ms.openlocfilehash: 85168af654d3d63e06559486b464938b7fd90ad3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321574"
---
# <a name="catlarray-class"></a>CAtlArray-Klasse

Diese Klasse implementiert ein Arrayobjekt.

## <a name="syntax"></a>Syntax

```
template<typename E, class ETraits = CElementTraits<E>>
class CAtlArray
```

#### <a name="parameters"></a>Parameter

*E*<br/>
Der Typ der im Array gespeicherten Daten.

*ETraits*<br/>
Der Code, der zum Kopieren oder Verschieben von Elementen verwendet wird.

## <a name="members"></a>Member

### <a name="methods"></a>Methoden

|||
|-|-|
|[Hinzufügen](#add)|Rufen Sie diese Methode auf, um dem Arrayobjekt ein Element hinzuzufügen.|
|[Append](#append)|Rufen Sie diese Methode auf, um den Inhalt eines Arrays am Ende eines anderen Arrays hinzuzufügen.|
|[Assertvalid](#assertvalid)|Rufen Sie diese Methode auf, um zu bestätigen, dass das Arrayobjekt gültig ist.|
|[Catlarray](#catlarray)|Der Konstruktor.|
|[CAtlArray](#dtor)|Der Destruktor.|
|[Kopieren](#copy)|Rufen Sie diese Methode auf, um die Elemente eines Arrays in ein anderes zu kopieren.|
|[FreeExtra](#freeextra)|Rufen Sie diese Methode auf, um alle leeren Elemente aus dem Array zu entfernen.|
|[GetAt](#getat)|Rufen Sie diese Methode auf, um ein einzelnes Element aus dem Arrayobjekt abzurufen.|
|[GetCount](#getcount)|Rufen Sie diese Methode auf, um die Anzahl der im Array gespeicherten Elemente zurückzugeben.|
|[GetData](#getdata)|Rufen Sie diese Methode auf, um einen Zeiger auf das erste Element im Array zurückzugeben.|
|[InsertArrayAt](#insertarrayat)|Rufen Sie diese Methode auf, um ein Array in ein anderes einzufügen.|
|[Insertat](#insertat)|Rufen Sie diese Methode auf, um ein neues Element (oder mehrere Kopien eines Elements) in das Arrayobjekt einzufügen.|
|[Isempty](#isempty)|Rufen Sie diese Methode auf, um zu testen, ob das Array leer ist.|
|[Removeall](#removeall)|Rufen Sie diese Methode auf, um alle Elemente aus dem Arrayobjekt zu entfernen.|
|[RemoveAt](#removeat)|Rufen Sie diese Methode auf, um ein oder mehrere Elemente aus dem Array zu entfernen.|
|[Setat](#setat)|Rufen Sie diese Methode auf, um den Wert eines Elements im Arrayobjekt festzulegen.|
|[SetAtGrow](#setatgrow)|Rufen Sie diese Methode auf, um den Wert eines Elements im Arrayobjekt festzulegen und das Array nach Bedarf zu erweitern.|
|[SetCount](#setcount)|Rufen Sie diese Methode auf, um die Größe des Arrayobjekts festzulegen.|

### <a name="operators"></a>Operatoren

|||
|-|-|
|[Betreiber &#91;&#93;](#operator_at)|Rufen Sie diesen Operator auf, um einen Verweis auf ein Element im Array zurückzugeben.|

### <a name="typedefs"></a>TypeDefs

|||
|-|-|
|[INARGTYPE](#inargtype)|Der Datentyp, der zum Hinzufügen von Elementen zum Array verwendet werden soll.|
|[OUTARGTYPE](#outargtype)|Der Datentyp, der zum Abrufen von Elementen aus dem Array verwendet werden soll.|

## <a name="remarks"></a>Bemerkungen

`CAtlArray`bietet Methoden zum Erstellen und Verwalten eines Arrays von Elementen eines benutzerdefinierten Typs. Obwohl es den Standard-C-Arrays ähnelt, kann das `CAtlArray` Objekt bei Bedarf dynamisch verkleinert und wachsen. Der Arrayindex beginnt immer an Position 0, und die obere Grenze kann festgelegt werden oder kann erweitert werden, wenn neue Elemente hinzugefügt werden.

Für Arrays mit einer kleinen Anzahl von Elementen kann die ATL-Klasse [CSimpleArray](../../atl/reference/csimplearray-class.md) verwendet werden.

`CAtlArray`ist eng mit der `CArray` MFC-Klasse verbunden und wird in einem MFC-Projekt arbeiten, wenn auch ohne Serialisierungsunterstützung.

Weitere Informationen finden Sie unter [ATL-Auflistungsklassen](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlcoll.h

## <a name="catlarrayadd"></a><a name="add"></a>CAtlArray::Hinzufügen

Rufen Sie diese Methode auf, um dem Arrayobjekt ein Element hinzuzufügen.

```
size_t Add(INARGTYPE element);
size_t Add();
```

### <a name="parameters"></a>Parameter

*Element*<br/>
Das Element, das dem Array hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt den Index des hinzugefügten Elements zurück.

### <a name="remarks"></a>Bemerkungen

Das neue Element wird am Ende des Arrays hinzugefügt. Wenn kein Element bereitgestellt wird, wird ein leeres Element hinzugefügt. Das heißt, das Array wird vergrößert, als ob ein echtes Element hinzugefügt wurde. Wenn der Vorgang fehlschlägt, wird [AtlThrow](debugging-and-error-reporting-global-functions.md#atlthrow) mit dem Argument E_OUTOFMEMORY aufgerufen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#1](../../atl/codesnippet/cpp/catlarray-class_1.cpp)]

## <a name="catlarrayappend"></a><a name="append"></a>CAtlArray::Anfügen

Rufen Sie diese Methode auf, um den Inhalt eines Arrays am Ende eines anderen Arrays hinzuzufügen.

```
size_t Append(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parameter

*aSrc*<br/>
Das anzuhängende Array.

### <a name="return-value"></a>Rückgabewert

Gibt den Index des ersten angehängten Elements zurück.

### <a name="remarks"></a>Bemerkungen

Die Elemente im bereitgestellten Array werden am Ende des vorhandenen Arrays hinzugefügt. Bei Bedarf wird Speicher für die neuen Elemente reserviert.

Die Arrays müssen vom gleichen Typ sein, und es ist nicht möglich, ein Array an sich selbst anzuhängen.

In Debugbuilds wird ein ATLASSERT `CAtlArray` ausgelöst, wenn das Argument kein gültiges Array ist oder wenn *aSrc* auf dasselbe Objekt verweist. In Releasebuilds können ungültige Argumente zu unvorhersehbarem Verhalten führen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#2](../../atl/codesnippet/cpp/catlarray-class_2.cpp)]

## <a name="catlarrayassertvalid"></a><a name="assertvalid"></a>CAtlArray::AssertValid

Rufen Sie diese Methode auf, um zu bestätigen, dass das Arrayobjekt gültig ist.

```
void AssertValid() const;
```

### <a name="remarks"></a>Bemerkungen

Wenn das Arrayobjekt ungültig ist, wird ATLASSERT eine Assertion auslösen. Diese Methode ist nur verfügbar, wenn _DEBUG definiert ist.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#3](../../atl/codesnippet/cpp/catlarray-class_3.cpp)]

## <a name="catlarraycatlarray"></a><a name="catlarray"></a>CAtlArray::CAtlArray

Der Konstruktor.

```
CAtlArray() throw();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert das Arrayobjekt.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#4](../../atl/codesnippet/cpp/catlarray-class_4.cpp)]

## <a name="catlarraycatlarray"></a><a name="dtor"></a>CAtlArray::-CAtlArray

Der Destruktor.

```
~CAtlArray() throw();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle Ressourcen frei, die vom Arrayobjekt verwendet werden.

## <a name="catlarraycopy"></a><a name="copy"></a>CAtlArray::Kopieren

Rufen Sie diese Methode auf, um die Elemente eines Arrays in ein anderes zu kopieren.

```
void Copy(const CAtlArray<E, ETraits>& aSrc);
```

### <a name="parameters"></a>Parameter

*aSrc*<br/>
Die Quelle der Elemente, die in ein Array kopiert werden sollen.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um Elemente eines Arrays mit den Elementen eines anderen Arrays zu überschreiben. Bei Bedarf wird Speicher für die neuen Elemente reserviert. Es ist nicht möglich, Elemente eines Arrays in sich selbst zu kopieren.

Wenn der vorhandene Inhalt des Arrays beibehalten werden soll, verwenden Sie stattdessen [CAtlArray::Append.](#append)

In Debugbuilds wird ein ATLASSERT ausgelöst, wenn das vorhandene `CAtlArray` Objekt ungültig ist oder wenn *aSrc* auf dasselbe Objekt verweist. In Releasebuilds können ungültige Argumente zu unvorhersehbarem Verhalten führen.

> [!NOTE]
> `CAtlArray::Copy`unterstützt keine Arrays, die aus Elementen bestehen, die mit der [CAutoPtr-Klasse](../../atl/reference/cautoptr-class.md) erstellt wurden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#5](../../atl/codesnippet/cpp/catlarray-class_5.cpp)]

## <a name="catlarrayfreeextra"></a><a name="freeextra"></a>CAtlArray::FreeExtra

Rufen Sie diese Methode auf, um alle leeren Elemente aus dem Array zu entfernen.

```
void FreeExtra() throw();
```

### <a name="remarks"></a>Bemerkungen

Alle leeren Elemente werden entfernt, aber die Größe und die obere Grenze des Arrays bleiben unverändert.

In Debugbuilds wird ein ATLASSERT ausgelöst, wenn das CAtlArray-Objekt ungültig ist oder wenn das Array seine maximale Größe überschreitet.

## <a name="catlarraygetat"></a><a name="getat"></a>CAtlArray::GetAt

Rufen Sie diese Methode auf, um ein einzelnes Element aus dem Arrayobjekt abzurufen.

```
const E& GetAt(size_t iElement) const throw();
E& GetAt(size_t iElement) throw();
```

### <a name="parameters"></a>Parameter

*Ielement*<br/>
Der Indexwert des zurückzugebenden Arrayelements.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf das erforderliche Arrayelement zurück.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds wird ein ATLASSERT ausgelöst, wenn *iElement* die Anzahl der Elemente im Array überschreitet. In Releasebuilds kann ein ungültiges Argument zu unvorhersehbarem Verhalten führen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#6](../../atl/codesnippet/cpp/catlarray-class_6.cpp)]

## <a name="catlarraygetcount"></a><a name="getcount"></a>CAtlArray::GetCount

Rufen Sie diese Methode auf, um die Anzahl der im Array gespeicherten Elemente zurückzugeben.

```
size_t GetCount() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der im Array gespeicherten Elemente zurück.

### <a name="remarks"></a>Bemerkungen

Da sich das erste Element im Array an `GetCount` Position 0 befindet, ist der zurückgegebene Wert immer 1 größer als der größte Index.

### <a name="example"></a>Beispiel

Siehe beispiel für [CAtlArray::GetAt](#getat).

## <a name="catlarraygetdata"></a><a name="getdata"></a>CAtlArray::GetData

Rufen Sie diese Methode auf, um einen Zeiger auf das erste Element im Array zurückzugeben.

```
E* GetData() throw();
const E* GetData() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf den Speicherspeicherort zurück, in dem das erste Element im Array gespeichert wird. Wenn keine Elemente verfügbar sind, wird NULL zurückgegeben.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#7](../../atl/codesnippet/cpp/catlarray-class_7.cpp)]

## <a name="catlarrayinargtype"></a><a name="inargtype"></a>CAtlArray::INARGTYPE

Der Datentyp, der zum Hinzufügen von Elementen zum Array verwendet werden soll.

```
typedef ETraits::INARGTYPE INARGTYPE;
```

## <a name="catlarrayinsertarrayat"></a><a name="insertarrayat"></a>CAtlArray::InsertArrayAt

Rufen Sie diese Methode auf, um ein Array in ein anderes einzufügen.

```
void InsertArrayAt(size_t iStart, const CAtlArray<E, ETraits>* paNew);
```

### <a name="parameters"></a>Parameter

*iStart*<br/>
Der Index, an dem das Array eingefügt werden soll.

*paNew*<br/>
Das Array, das eingefügt werden soll.

### <a name="remarks"></a>Bemerkungen

Elemente aus dem Array *paNew* werden in das Arrayobjekt kopiert, beginnend mit dem Element *iStart*. Die vorhandenen Arrayelemente werden verschoben, um zu vermeiden, dass sie überschrieben werden.

In Debugbuilds wird ein ATLASSERT `CAtlArray` ausgelöst, wenn das Objekt ungültig ist oder wenn der *paNew-Zeiger* NULL oder ungültig ist.

> [!NOTE]
> `CAtlArray::InsertArrayAt`unterstützt keine Arrays, die aus Elementen bestehen, die mit der [CAutoPtr-Klasse](../../atl/reference/cautoptr-class.md) erstellt wurden.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#8](../../atl/codesnippet/cpp/catlarray-class_8.cpp)]

## <a name="catlarrayinsertat"></a><a name="insertat"></a>CAtlArray::InsertAt

Rufen Sie diese Methode auf, um ein neues Element (oder mehrere Kopien eines Elements) in das Arrayobjekt einzufügen.

```
void InsertAt(size_t iElement, INARGTYPE element, size_t nCount = 1);
```

### <a name="parameters"></a>Parameter

*Ielement*<br/>
Der Index, in den das Element oder die Elemente eingefügt werden sollen.

*Element*<br/>
Der Wert des elements oder der Elemente, die eingefügt werden sollen.

*nCount*<br/>
Die Anzahl der hinzuzufügenden Elemente.

### <a name="remarks"></a>Bemerkungen

Fügt ein oder mehrere Elemente in das Array ein, beginnend mit dem Index *iElement*. Vorhandene Elemente werden verschoben, um zu vermeiden, dass sie überschrieben werden.

In Debugbuilds wird ein ATLASSERT `CAtlArray` ausgelöst, wenn das Objekt ungültig ist, die Anzahl der hinzuzufügenden Elemente Null ist oder die kombinierte Anzahl von Elementen zu groß ist, als dass das Array enthalten werden kann. In Einzelhandelsbuilds kann das Übergeben ungültiger Parameter zu unvorhersehbaren Ergebnissen führen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#9](../../atl/codesnippet/cpp/catlarray-class_9.cpp)]

## <a name="catlarrayisempty"></a><a name="isempty"></a>CAtlArray::IsEmpty

Rufen Sie diese Methode auf, um zu testen, ob das Array leer ist.

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn das Array leer ist, andernfalls false.

### <a name="remarks"></a>Bemerkungen

Das Array ist angeblich leer, wenn es keine Elemente enthält. Daher ist das Array, selbst wenn es leere Elemente enthält, nicht leer.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#10](../../atl/codesnippet/cpp/catlarray-class_10.cpp)]

## <a name="catlarrayoperator-"></a><a name="operator_at"></a>CAtlArray::operator []

Rufen Sie diesen Operator auf, um einen Verweis auf ein Element im Array zurückzugeben.

```
E& operator[](size_t ielement) throw();
const E& operator[](size_t ielement) const throw();
```

### <a name="parameters"></a>Parameter

*Ielement*<br/>
Der Indexwert des zurückzugebenden Arrayelements.

### <a name="return-value"></a>Rückgabewert

Gibt einen Verweis auf das erforderliche Arrayelement zurück.

### <a name="remarks"></a>Bemerkungen

Führt eine ähnliche Funktion wie [CAtlArray::GetAt](#getat)aus. Im Gegensatz zur MFC-Klasse [CArray](../../mfc/reference/carray-class.md)kann dieser Operator nicht als Ersatz für [CAtlArray::SetAt](#setat)verwendet werden.

In Debugbuilds wird ein ATLASSERT ausgelöst, wenn *iElement* die Gesamtzahl der Elemente im Array überschreitet. In Einzelhandelsbuilds kann ein ungültiger Parameter zu unvorhersehbaren Ergebnissen führen.

## <a name="catlarrayoutargtype"></a><a name="outargtype"></a>CAtlArray::OUTARGTYPE

Der Datentyp, der zum Abrufen von Elementen aus dem Array verwendet werden soll.

```
typedef ETraits::OUTARGTYPE OUTARGTYPE;
```

## <a name="catlarrayremoveall"></a><a name="removeall"></a>CAtlArray::Alle entfernen

Rufen Sie diese Methode auf, um alle Elemente aus dem Arrayobjekt zu entfernen.

```
void RemoveAll() throw();
```

### <a name="remarks"></a>Bemerkungen

Entfernt alle Elemente aus dem Arrayobjekt.

Diese Methode ruft [CAtlArray::SetCount](#setcount) auf, um die Größe des Arrays zu ändern, und gibt anschließend den zugewiesenen Speicher frei.

### <a name="example"></a>Beispiel

Siehe beispielfür [CAtlArray::IsEmpty](#isempty).

## <a name="catlarrayremoveat"></a><a name="removeat"></a>CAtlArray::RemoveAt

Rufen Sie diese Methode auf, um ein oder mehrere Elemente aus dem Array zu entfernen.

```
void RemoveAt(size_t iElement, size_t nCount = 1);
```

### <a name="parameters"></a>Parameter

*Ielement*<br/>
Der Index des ersten zu entfernenden Elements.

*nCount*<br/>
Die Anzahl der zu entfernenden Elemente.

### <a name="remarks"></a>Bemerkungen

Entfernt ein oder mehrere Elemente aus dem Array. Alle verbleibenden Elemente werden nach unten verschoben. Die obere Grenze wird dekrementiert, aber der Speicher wird erst freigegeben, wenn ein Aufruf von [CAtlArray::FreeExtra](#freeextra) gemacht wird.

In Debugbuilds wird ein ATLASSERT `CAtlArray` ausgelöst, wenn das Objekt ungültig ist oder wenn die gesamtsumme von *iElement* und *nCount* die Gesamtzahl der Elemente im Array überschreitet. In Einzelhandelsbuilds können ungültige Parameter zu unvorhersehbaren Ergebnissen führen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#11](../../atl/codesnippet/cpp/catlarray-class_11.cpp)]

## <a name="catlarraysetat"></a><a name="setat"></a>CAtlArray::SetAt

Rufen Sie diese Methode auf, um den Wert eines Elements im Arrayobjekt festzulegen.

```
void SetAt(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parameter

*Ielement*<br/>
Der Index, der auf das festzulegende Arrayelement zeigt.

*Element*<br/>
Der neue Wert des angegebenen Elements.

### <a name="remarks"></a>Bemerkungen

In Debugbuilds wird ein ATLASSERT ausgelöst, wenn *iElement* die Anzahl der Elemente im Array überschreitet. In Einzelhandelsbuilds kann ein ungültiger Parameter zu unvorhersehbaren Ergebnissen führen.

### <a name="example"></a>Beispiel

Siehe beispiel für [CAtlArray::GetAt](#getat).

## <a name="catlarraysetcount"></a><a name="setcount"></a>CAtlArray::SetCount

Rufen Sie diese Methode auf, um die Größe des Arrayobjekts festzulegen.

```
bool SetCount(size_t nNewSize, int nGrowBy = - 1);
```

### <a name="parameters"></a>Parameter

*nNewSize*<br/>
Die erforderliche Größe des Arrays.

*nGrowBy*<br/>
Ein Wert, der verwendet wird, um zu bestimmen, wie groß der Puffer wird. Ein Wert von -1 bewirkt, dass ein intern berechneter Wert verwendet wird.

### <a name="return-value"></a>Rückgabewert

Gibt true zurück, wenn die Größe des Arrays erfolgreich geändert wurde, andernfalls false.

### <a name="remarks"></a>Bemerkungen

Das Array kann vergrößert oder verkleinert werden. Wenn erhöht, werden dem Array zusätzliche leere Elemente hinzugefügt. Wenn sie verringert werden, werden die Elemente mit den größten Indizes gelöscht und der Speicher freigegeben.

Verwenden Sie diese Methode, um die Größe des Arrays festzulegen, bevor Sie es verwenden. Wenn `SetCount` nicht verwendet wird, reduziert das Hinzufügen von Elementen – und die anschließende Speicherzuweisung – die Leistung und den Fragmentspeicher.

### <a name="example"></a>Beispiel

Siehe Beispiel für [CAtlArray::GetData](#getdata).

## <a name="catlarraysetatgrow"></a><a name="setatgrow"></a>CAtlArray::SetAtGrow

Rufen Sie diese Methode auf, um den Wert eines Elements im Arrayobjekt festzulegen und das Array nach Bedarf zu erweitern.

```
void SetAtGrow(size_t iElement, INARGTYPE element);
```

### <a name="parameters"></a>Parameter

*Ielement*<br/>
Der Index, der auf das festzulegende Arrayelement zeigt.

*Element*<br/>
Der neue Wert des angegebenen Elements.

### <a name="remarks"></a>Bemerkungen

Ersetzt den Wert des Elements, auf das der Index zeigt. Wenn *iElement* größer als die aktuelle Größe des Arrays ist, wird das Array automatisch durch einen Aufruf von [CAtlArray::SetCount](#setcount)erhöht. In Debugbuilds wird ein ATLASSERT `CAtlArray` ausgelöst, wenn das Objekt ungültig ist. In Einzelhandelsbuilds können ungültige Parameter zu unvorhersehbaren Ergebnissen führen.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#12](../../atl/codesnippet/cpp/catlarray-class_12.cpp)]

## <a name="see-also"></a>Siehe auch

[MMXSwarm-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[DynamicConsumer-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[UpdatePV-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[Marquee-Beispiel](../../overview/visual-cpp-samples.md)<br/>
[CArray-Klasse](../../mfc/reference/carray-class.md)<br/>
[Klassenübersicht](../../atl/atl-class-overview.md)

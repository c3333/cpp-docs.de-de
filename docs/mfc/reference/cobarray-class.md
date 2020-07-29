---
title: CObArray-Klasse
ms.date: 11/04/2016
f1_keywords:
- CObArray
- AFXCOLL/CObArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 27894efd-2370-4776-9ed9-24a98492af17
ms.openlocfilehash: b083bf0e82f9d9b928e613f07a71d36147240cd2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212370"
---
# <a name="cobarray-class"></a>CObArray-Klasse

Unterstützt Arrays mit `CObject` -Zeigern.

## <a name="syntax"></a>Syntax

```
class CObArray : public CObject
```

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CObArray:: CObArray](#cobarray)|Erstellt ein leeres Array für `CObject` Zeiger.|

### <a name="public-methods"></a>Öffentliche Methoden

|name|BESCHREIBUNG|
|----------|-----------------|
|[CObArray:: Add](#add)|Fügt am Ende des Arrays ein Element hinzu; vergrößert das Array bei Bedarf.|
|[CObArray:: Append](#append)|Hängt ein anderes Array an das Array an; vergrößert das Array bei Bedarf.|
|[CObArray:: Copy](#copy)|Kopiert ein anderes Array in das Array; vergrößert das Array bei Bedarf.|
|[CObArray:: ElementAt](#elementat)|Gibt einen temporären Verweis auf den Elementzeiger innerhalb des Arrays zurück.|
|[CObArray:: freextra](#freeextra)|Gibt den gesamten nicht verwendeten Arbeitsspeicher über der aktuellen Obergrenze frei.|
|[CObArray:: GetAt](#getat)|Gibt den Wert an einem bestimmten Index zurück.|
|[CObArray:: GetCount](#getcount)|Ruft die Anzahl der Elemente im Array ab.|
|[CObArray:: GetData](#getdata)|Ermöglicht den Zugriff auf Elemente im Array. Kann den Wert NULL haben.|
|[CObArray:: GetSize](#getsize)|Ruft die Anzahl der Elemente im Array ab.|
|[CObArray:: GetUpperBound](#getupperbound)|Gibt den größten gültigen Index zurück.|
|[CObArray:: InsertAt](#insertat)|Fügt ein Element (oder alle Elemente in einem anderen Array) am angegebenen Index ein.|
|[CObArray:: IsEmpty](#isempty)|Bestimmt, ob das Array leer ist.|
|[CObArray:: RemoveAll](#removeall)|Entfernt alle Elemente aus diesem Array.|
|[CObArray:: RemoveAt](#removeat)|Entfernt ein Element an einem spezifischen Index.|
|[CObArray::](#setat)|Legt den Wert für einen bestimmten Index fest; Array darf nicht vergrößert werden.|
|[CObArray:: antatgrow](#setatgrow)|Legt den Wert für einen bestimmten Index fest; vergrößert das Array bei Bedarf.|
|[CObArray:: SetSize](#setsize)|Legt die Anzahl der Elemente im Array fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CObArray::-Operator \[\]](#operator_at)|Legt das Element am angegebenen Index fest oder ruft es ab.|

## <a name="remarks"></a>Bemerkungen

Diese Objekt Arrays ähneln C-Arrays, Sie können jedoch bei Bedarf dynamisch verkleinert und vergrößert werden.

Array Indizes beginnen immer an Position 0. Sie können entscheiden, ob die obere Grenze behoben oder das Array erweitert werden soll, wenn Sie Elemente hinter der aktuellen Grenze hinzufügen. Der Arbeitsspeicher wird der oberen Grenze zusammenhängend zugewiesen, auch wenn einige Elemente NULL sind.

Unter Win32 ist die Größe eines- `CObArray` Objekts nur auf den verfügbaren Arbeitsspeicher beschränkt.

Wie bei einem C-Array ist die Zugriffszeit für ein `CObArray` indiziertes Element konstant und unabhängig von der Array Größe.

`CObArray`integriert das IMPLEMENT_SERIAL-Makro, um die Serialisierung und das Sichern der zugehörigen Elemente zu unterstützen. Wenn ein Array von `CObject` Zeigern in einem Archiv gespeichert wird, entweder mit dem überladenen einfügeoperator oder mit der `Serialize` Member-Funktion, `CObject` wird jedes Element wiederum zusammen mit dem Array Index serialisiert.

Wenn Sie ein Abbild einzelner `CObject` Elemente in einem Array benötigen, müssen Sie die Tiefe des `CDumpContext` Objekts auf 1 oder höher festlegen.

Wenn ein- `CObArray` Objekt gelöscht wird oder wenn seine Elemente entfernt werden, werden nur die `CObject` Zeiger entfernt, nicht die Objekte, auf die Sie verweisen.

> [!NOTE]
> Vor dem Verwenden eines Arrays, verwenden Sie `SetSize`, um dessen Größe festzustellen, und weisen dafür Arbeitsspeicher zu. Wenn Sie `SetSize` nicht verwenden, kann das Hinzufügen von Elementen zu Ihrem Array dazu führen, dass es häufig neu zugeordnet und kopiert wird. Häufige Neuzuordnungen und Kopiervorgänge sind ineffizient und können zu einer Fragmentierung des Arbeitsspeichers führen.

Die Ableitung der Array Klasse ähnelt der Listen Ableitung. Ausführliche Informationen zur Ableitung einer speziellen Listen Klasse finden Sie im Artikel [Sammlungen](../../mfc/collections.md).

> [!NOTE]
> Sie müssen das IMPLEMENT_SERIAL-Makro in der Implementierung der abgeleiteten Klasse verwenden, wenn Sie beabsichtigen, das Array zu serialisieren.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[CObject](../../mfc/reference/cobject-class.md)

`CObArray`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxcoll. h

## <a name="cobarrayadd"></a><a name="add"></a>CObArray:: Add

Fügt am Ende eines Arrays ein neues Element hinzu, wobei das Array um 1 vergrößert wird.

```
INT_PTR Add(CObject* newElement);
```

### <a name="parameters"></a>Parameter

*newElement*<br/>
Der `CObject` Zeiger, der diesem Array hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index des hinzugefügten Elements.

### <a name="remarks"></a>Bemerkungen

Wenn [SetSize](#setsize) mit einem *ngrowby* -Wert größer als 1 verwendet wurde, kann zusätzlicher Arbeitsspeicher zugewiesen werden. Die obere Grenze wird jedoch nur um 1 erhöht.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die ähneln `CObArray::Add` .

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR hinzufügen (Byte** `newElement` **);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR hinzufügen (DWORD** `newElement` **);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR hinzufügen (void** <strong>\*</strong> `newElement` **);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR Add (LPCTSTR** `newElement` **); throw (cmemoryexception \* );**<br /><br /> **INT_PTR hinzufügen (Konstante CString-&** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR hinzufügen (uint** `newElement` **);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR hinzufügen (Word** `newElement` **);**<br /><br /> **Throw (cmemoryexception \* );**|

### <a name="example"></a>Beispiel

  Eine Auflistung der in allen Sammlungs Beispielen verwendeten Klassen finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` .

[!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]

Die Ergebnisse dieses Programms lauten wie folgt:

```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```

## <a name="cobarrayappend"></a><a name="append"></a>CObArray:: Append

Mit dieser Member-Funktion können Sie den Inhalt eines anderen Arrays am Ende des angegebenen Arrays hinzufügen.

```
INT_PTR Append(const CObArray& src);
```

### <a name="parameters"></a>Parameter

*src*<br/>
Quelle der Elemente, die an das Array angefügt werden sollen.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten angefügten Elements.

### <a name="remarks"></a>Bemerkungen

Die Arrays müssen denselben Typ aufweisen.

Bei Bedarf `Append` kann zusätzlichen Arbeitsspeicher zuordnen, um die an das Array angefügten Elemente anzupassen.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die ähneln `CObArray::Append` .

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR anfügen (const CByteArray&** *src* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR anfügen (const cdwordarray&** *src* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR anfügen (const CPtrArray&** *src* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR anfügen (const cstringarray&** *src* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR anfügen (const cuintarray&** *src* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR anfügen (const CWordArray&** *src* **);**|

### <a name="example"></a>Beispiel

Eine Auflistung der in allen Sammlungs Beispielen verwendeten Klassen finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` .

[!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]

## <a name="cobarraycopy"></a><a name="copy"></a>CObArray:: Copy

Diese Member-Funktion wird aufgerufen, um die Elemente des angegebenen Arrays mit den Elementen eines anderen Arrays desselben Typs zu überschreiben.

```cpp
void Copy(const CObArray& src);
```

### <a name="parameters"></a>Parameter

*src*<br/>
Quelle der Elemente, die in das Array kopiert werden sollen.

### <a name="remarks"></a>Bemerkungen

`Copy`gibt keinen Arbeitsspeicher frei; bei Bedarf `Copy` kann jedoch zusätzlichen Arbeitsspeicher zuordnen, um die Elemente zu verarbeiten, die in das Array kopiert werden.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die ähneln `CObArray::Copy` .

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void Copy (const CByteArray&** *src* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void Copy (const cdwordarray&** *src* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void Copy (const CPtrArray&** *src* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void Copy (const cstringarray&** *src* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void Copy (const cuintarray&** *src* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void Copy (const CWordArray&** *src* **);**|

### <a name="example"></a>Beispiel

Eine Auflistung der in allen Sammlungs Beispielen verwendeten Klassen finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` .

[!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]

## <a name="cobarraycobarray"></a><a name="cobarray"></a>CObArray:: CObArray

Erstellt ein leeres `CObject` Zeiger Array.

```
CObArray();
```

### <a name="remarks"></a>Bemerkungen

Das Array wächst jeweils ein Element.

In der folgenden Tabelle werden andere Konstruktoren angezeigt, die ähneln `CObArray::CObArray` .

|Klasse|Konstruktor|
|-----------|-----------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**CByteArray ();**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Cdwordarray ();**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**CPtrArray ();**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Cstringarray ();**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Cuintarray ();**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**CWordArray ();**|

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]

## <a name="cobarrayelementat"></a><a name="elementat"></a>CObArray:: ElementAt

Gibt einen temporären Verweis auf den Elementzeiger innerhalb des Arrays zurück.

```
CObject*& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein ganzzahliger Index, der größer oder gleich 0 und kleiner als oder gleich dem Wert ist, der von zurückgegeben wird `GetUpperBound` .

### <a name="return-value"></a>Rückgabewert

Ein Verweis auf einen `CObject` Zeiger.

### <a name="remarks"></a>Bemerkungen

Es wird verwendet, um den linksseitigen Zuweisungs Operator für Arrays zu implementieren. Beachten Sie, dass es sich hierbei um eine erweiterte Funktion handelt, die nur zur Implementierung spezieller Array Operatoren verwendet werden sollte.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die ähneln `CObArray::ElementAt` .

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Byte& ElementAt (INT_PTR** `nIndex` **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD& ElementAt (INT_PTR** `nIndex` **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void \*& ElementAt (INT_PTR** `nIndex` **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString& ElementAt (INT_PTR** `nIndex` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Uint& ElementAt (INT_PTR** `nIndex` **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Word& ElementAt (INT_PTR** `nIndex` **);**|

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CObArray:: GetSize](#getsize).

## <a name="cobarrayfreeextra"></a><a name="freeextra"></a>CObArray:: freextra

Gibt zusätzlichen Arbeitsspeicher frei, der zugeordnet wurde, während das Array vergrößert wurde.

```cpp
void FreeExtra();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion hat keine Auswirkung auf die Größe oder die obere Grenze des Arrays.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die ähneln `CObArray::FreeExtra` .

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void freextra ();**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void freextra ();**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void freextra ();**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void freextra ();**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void freextra ();**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void freextra ();**|

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CObArray:: GetData](#getdata).

## <a name="cobarraygetat"></a><a name="getat"></a>CObArray:: GetAt

Gibt das Array Element am angegebenen Index zurück.

```
CObject* GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein ganzzahliger Index, der größer oder gleich 0 und kleiner als oder gleich dem Wert ist, der von zurückgegeben wird `GetUpperBound` .

### <a name="return-value"></a>Rückgabewert

Das `CObject` Zeiger Element, das sich derzeit an diesem Index befinden.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Wenn ein negativer Wert oder ein Wert, der größer als der von zurückgegebene Wert ist, übergeben `GetUpperBound` wird, führt dies zu einer fehlgeschlagenen

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die ähneln `CObArray::GetAt` .

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Byte GetAt (INT_PTR** `nIndex` **) Konstanten;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD GetAt (INT_PTR** `nIndex` **) Konstanten;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void \* GetAt (INT_PTR** `nIndex` **) Konstanten;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString GetAt (INT_PTR** `nIndex` **) Konstanten;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Uint GetAt (INT_PTR** `nIndex` **) Konstanten;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Wort GetAt (INT_PTR** `nIndex` **) Konstanten;**|

### <a name="example"></a>Beispiel

Eine Auflistung der in allen Sammlungs Beispielen verwendeten Klassen finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` .

[!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]

## <a name="cobarraygetcount"></a><a name="getcount"></a>CObArray:: GetCount

Gibt die Anzahl der Array Elemente zurück.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im Array.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die Anzahl der Elemente im Array abzurufen. Da Indizes NULL basiert sind, ist die Größe 1 größer als der größte Index.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die ähneln `CObArray::GetCount` .

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetCount () Konstanten;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetCount () Konstanten;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetCount () Konstanten;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetCount () Konstanten;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetCount () Konstanten;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetCount () Konstanten;**|

### <a name="example"></a>Beispiel

Eine Auflistung der in allen Sammlungs Beispielen verwendeten Klassen finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` .

[!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]

## <a name="cobarraygetdata"></a><a name="getdata"></a>CObArray:: GetData

Verwenden Sie diese Member-Funktion, um direkten Zugriff auf die Elemente im Array zu erhalten.

```
const CObject** GetData() const;

CObject** GetData();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das Array von `CObject` Zeigern.

### <a name="remarks"></a>Bemerkungen

Wenn keine Elemente verfügbar sind, wird `GetData` ein NULL-Wert zurückgegeben.

Während der direkte Zugriff auf die Elemente eines Arrays Ihnen helfen kann, schneller zu arbeiten, sollten Sie beim Aufrufen von Vorsicht walten `GetData` lassen. alle Fehler, die Sie direkt vornehmen, wirken sich direkt auf die Elemente des Arrays aus.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die ähneln `CObArray::GetData` .

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Konstanten Byte \* GetData () Konstanten; Byte \* GetData ();**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**Konstante DWORD \* GetData () Konstanten; DWORD \* GetData ();**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**Konstante void \* \* GetData () Konstanten; void \* \* GetData ();**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**Konstanten CString \* GetData ()-Konstante; CString \* GetData ();**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**konstantenuint \* GetData () Konstanten; Uint \* GetData ();**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**konstantenwort \* GetData () Konstanten; Wort \* GetData ();**|

### <a name="example"></a>Beispiel

Eine Auflistung der in allen Sammlungs Beispielen verwendeten Klassen finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` .

[!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]

## <a name="cobarraygetsize"></a><a name="getsize"></a>CObArray:: GetSize

Gibt die Größe des Arrays zurück.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Bemerkungen

Da Indizes NULL basiert sind, ist die Größe 1 größer als der größte Index.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die ähneln `CObArray::GetSize` .

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetSize () Konstanten;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetSize () Konstanten;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetSize () Konstanten;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetSize () Konstanten;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetSize () Konstanten;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetSize () Konstanten;**|

### <a name="example"></a>Beispiel

Eine Auflistung der in allen Sammlungs Beispielen verwendeten Klassen finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` .

[!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]

## <a name="cobarraygetupperbound"></a><a name="getupperbound"></a>CObArray:: GetUpperBound

Gibt die aktuelle obere Grenze dieses Arrays zurück.

```
INT_PTR GetUpperBound() const;
```

### <a name="return-value"></a>Rückgabewert

Der Index der oberen Grenze (null basiert).

### <a name="remarks"></a>Bemerkungen

Da Array Indizes NULL basiert sind, gibt diese Funktion einen Wert zurück, der kleiner als ist `GetSize` .

Die Bedingung `GetUpperBound( )` =-1 gibt an, dass das Array keine Elemente enthält.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die ähneln `CObArray::GetUpperBound` .

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetUpperBound () Konstanten;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetUpperBound () Konstanten;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetUpperBound () Konstanten;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetUpperBound () Konstanten;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetUpperBound () Konstanten;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetUpperBound () Konstanten;**|

### <a name="example"></a>Beispiel

Eine Auflistung der in allen Sammlungs Beispielen verwendeten Klassen finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` .

[!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]

## <a name="cobarrayinsertat"></a><a name="insertat"></a>CObArray:: InsertAt

Fügt ein Element (oder alle Elemente in einem anderen Array) am angegebenen Index ein.

```cpp
void InsertAt(
    INT_PTR nIndex,
    CObject* newElement,
    INT_PTR nCount = 1);

void InsertAt(
    INT_PTR nStartIndex,
    CObArray* pNewArray);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein ganzzahliger Index, der möglicherweise größer als der von zurückgegebene Wert ist `GetUpperBound` .

*newElement*<br/>
Der `CObject` Zeiger, der in dieses Array eingefügt werden soll. Ein *null* -Wert ist zulässig.

*nCount*<br/>
Gibt an, wie oft dieses Element eingefügt werden soll (Standardwert ist 1).

*nstartindex*<br/>
Ein ganzzahliger Index, der möglicherweise größer als der von zurückgegebene Wert ist `GetUpperBound` .

*pberwarray*<br/>
Ein weiteres Array, das Elemente enthält, die diesem Array hinzugefügt werden sollen.

### <a name="remarks"></a>Bemerkungen

Die erste Version von `InsertAt` Fügt ein Element (oder mehrere Kopien eines Elements) an einem angegebenen Index in einem Array ein. Beim Prozess wird das vorhandene Element an diesem Index (durch Inkrementieren des Indexes) nach oben verschoben, und alle darin liegenden Elemente werden verschoben.

In der zweiten Version werden alle Elemente aus einer anderen Auflistung eingefügt `CObArray` , beginnend an der *nstartindex* -Position.

Die `SetAt` -Funktion ersetzt dagegen ein angegebenes Array Element und verschiebt keine Elemente.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die ähneln `CObArray::InsertAt` .

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, Byte** `newElement` **, int** `nCount` **= 1);**<br /><br /> **Throw (cmemoryexception \* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CByteArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, DWORD** `newElement` **, int** `nCount` **= 1);**<br /><br /> **Throw (cmemoryexception \* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, cdwordarray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **, int** `nCount` **= 1);**<br /><br /> **Throw (cmemoryexception \* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CPtrArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **, int** `nCount` **= 1);**<br /><br /> **Throw (cmemoryexception \* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, cstringarray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, uint** `newElement` **, int** `nCount` **= 1);**<br /><br /> **Throw (cmemoryexception \* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, cuintarray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void InsertAt (INT_PTR** `nIndex` **, Word** `newElement` **, int** `nCount` **= 1);**<br /><br /> **Throw (cmemoryexception \* );**<br /><br /> **void InsertAt (INT_PTR** `nStartIndex` **, CWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **Throw (cmemoryexception \* );**|

### <a name="example"></a>Beispiel

  Eine Auflistung der in allen Sammlungs Beispielen verwendeten Klassen finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` .

[!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]

Die Ergebnisse dieses Programms lauten wie folgt:

```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```

## <a name="cobarrayisempty"></a><a name="isempty"></a>CObArray:: IsEmpty

Bestimmt, ob das Array leer ist.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Array leer ist. andernfalls 0.

## <a name="cobarrayoperator--"></a><a name="operator_at"></a>CObArray:: Operator []

Diese tief gestellten Operatoren sind eine bequeme Ersetzung für die `SetAt` -Funktion und die- `GetAt` Funktion.

```
CObject*& operator[](int_ptr nindex);
CObject* operator[](int_ptr nindex) const;
```

### <a name="remarks"></a>Bemerkungen

Der erste Operator, der für Arrays aufgerufen wird, die nicht sind **`const`** , kann entweder auf der rechten Seite (r-Wert) oder auf der linken Seite (l-Wert) einer Zuweisungsanweisung verwendet werden. Die zweite, die für **`const`** Arrays aufgerufen wird, kann nur auf der rechten Seite verwendet werden.

Die Debugversion der Bibliothek bestätigt, ob der Index (entweder auf der linken oder rechten Seite einer Zuweisungsanweisung) außerhalb des gültigen Bereichs liegt.

Die folgende Tabelle zeigt andere Operatoren, die ähneln `CObArray::operator []` .

|Klasse|Operator|
|-----------|--------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**Byte&-Operator [] (INT_PTR** `nindex` ** \) ;**<br /><br /> **Byte-Operator [] (INT_PTR** `nindex` ** \) Konstanten;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD-& Operator [] (INT_PTR** `nindex` ** \) ;**<br /><br /> **DWORD-Operator [] (INT_PTR** `nindex` ** \) Konstanten;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void \*&-Operator [] (INT_PTR** `nindex` ** \) ;**<br /><br /> **void- \* Operator [] (INT_PTR** `nindex` ** \) Konstanten;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString&-Operator [] (INT_PTR** `nindex` ** \) ;**<br /><br /> **CString-Operator [] (INT_PTR** `nindex` ** \) Konstanten;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**Uint-& Operator [] (INT_PTR** `nindex` ** \) ;**<br /><br /> **Uint-Operator [] (INT_PTR** `nindex` ** \) Konstanten;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**Word&-Operator [] (INT_PTR** `nindex` ** \) ;**<br /><br /> **Word-Operator [] (INT_PTR** `nindex` ** \) Konstanten;**|

### <a name="example"></a>Beispiel

Eine Auflistung der in allen Sammlungs Beispielen verwendeten Klassen finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` .

[!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]

## <a name="cobarrayremoveall"></a><a name="removeall"></a>CObArray:: RemoveAll

Entfernt alle Zeiger aus diesem Array, löscht die Objekte jedoch nicht `CObject` .

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Bemerkungen

Wenn das Array bereits leer ist, funktioniert die Funktion weiterhin.

Die-Funktion gibt den `RemoveAll` gesamten Arbeitsspeicher für Zeiger Speicher frei.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die ähneln `CObArray::RemoveAll` .

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAll ();**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAll ();**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAll ();**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAll ();**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAll ();**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAll ();**|

### <a name="example"></a>Beispiel

Eine Auflistung der in allen Sammlungs Beispielen verwendeten Klassen finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` .

[!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]

## <a name="cobarrayremoveat"></a><a name="removeat"></a>CObArray:: RemoveAt

Entfernt ein oder mehrere Elemente, beginnend bei einem angegebenen Index in einem Array.

```cpp
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein ganzzahliger Index, der größer oder gleich 0 und kleiner als oder gleich dem Wert ist, der von zurückgegeben wird `GetUpperBound` .

*nCount*<br/>
Die Anzahl der zu entfernenden Elemente.

### <a name="remarks"></a>Bemerkungen

Im Prozess werden alle Elemente oberhalb der entfernten Elemente nach unten verschoben. Die obere Grenze des Arrays wird verringert, aber es wird kein Arbeitsspeicher freigegeben.

Wenn Sie versuchen, mehr Elemente zu entfernen, als im Array oberhalb des Entfernungs Punkts enthalten sind, wird die Debugversion der Bibliothek bestätigt.

Die- `RemoveAt` Funktion entfernt den- `CObject` Zeiger aus dem Array, aber das Objekt selbst wird nicht gelöscht.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die ähneln `CObArray::RemoveAt` .

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAt (INT_PTR** `nIndex` **, INT_PTR** *nCount* **= 1);**|

### <a name="example"></a>Beispiel

  Eine Auflistung der in allen Sammlungs Beispielen verwendeten Klassen finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` .

[!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]

Die Ergebnisse dieses Programms lauten wie folgt:

```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```

## <a name="cobarraysetat"></a><a name="setat"></a>CObArray::

Legt das Array Element am angegebenen Index fest.

```cpp
void SetAt(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein ganzzahliger Index, der größer oder gleich 0 und kleiner als oder gleich dem Wert ist, der von zurückgegeben wird `GetUpperBound` .

*newElement*<br/>
Der Objekt Zeiger, der in dieses Array eingefügt werden soll. Ein NULL-Wert ist zulässig.

### <a name="remarks"></a>Bemerkungen

`SetAt`bewirkt nicht, dass das Array vergrößert wird. Verwenden `SetAtGrow` Sie, wenn das Array automatisch vergrößert werden soll.

Sie müssen sicherstellen, dass der Indexwert eine gültige Position im Array darstellt. Wenn Sie außerhalb des gültigen Bereichs liegt, wird die Debugversion der Bibliothek bestätigt.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die ähneln `CObArray::SetAt` .

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void-Aktivität (INT_PTR** `nIndex` **, Byte** `newElement` **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void-Aktivität (INT_PTR** `nIndex` **, DWORD** `newElement` **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void-Aktivität (INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void-Aktivität (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void-Aktivität (INT_PTR** `nIndex` **, uint** `newElement` **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void-Aktivität (INT_PTR** `nIndex` **, Word** `newElement` **);**|

### <a name="example"></a>Beispiel

  Eine Auflistung der in allen Sammlungs Beispielen verwendeten Klassen finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` .

[!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]

Die Ergebnisse dieses Programms lauten wie folgt:

```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```

## <a name="cobarraysetatgrow"></a><a name="setatgrow"></a>CObArray:: antatgrow

Legt das Array Element am angegebenen Index fest.

```cpp
void SetAtGrow(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein ganzzahliger Index, der größer oder gleich 0 (null) ist.

*newElement*<br/>
Der Objekt Zeiger, der diesem Array hinzugefügt werden soll. Ein NULL-Wert ist zulässig.

### <a name="remarks"></a>Bemerkungen

Das Array wird bei Bedarf automatisch vergrößert (d. h., die obere Grenze wird an das neue Element angepasst).

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die ähneln `CObArray::SetAtGrow` .

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void-Aktivität (INT_PTR** `nIndex` **, Byte** `newElement` **);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void-Aktivität (INT_PTR** `nIndex` **, DWORD** `newElement` **);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void-aufwachsen (INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void antatgrow (INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void-aufwachsen (INT_PTR** `nIndex` **, uint** `newElement` **);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void-aufwachsen (INT_PTR** `nIndex` **, Word** `newElement` **);**<br /><br /> **Throw (cmemoryexception \* );**|

### <a name="example"></a>Beispiel

  Eine Auflistung der in allen Sammlungs Beispielen verwendeten Klassen finden Sie unter [CObList:: CObList](../../mfc/reference/coblist-class.md#coblist) `CAge` .

[!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]

Die Ergebnisse dieses Programms lauten wie folgt:

```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```

## <a name="cobarraysetsize"></a><a name="setsize"></a>CObArray:: SetSize

Legt die Größe eines leeren oder vorhandenen Arrays fest. weist bei Bedarf Arbeitsspeicher zu.

```cpp
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Parameter

*nnewSize*<br/>
Die neue Array Größe (Anzahl der Elemente). Muss mindestens 0 sein.

*ngrowby*<br/>
Die Mindestanzahl der zuzuordnenden Element Slots, wenn eine Größen Erhöhung erforderlich ist.

### <a name="remarks"></a>Bemerkungen

Wenn die neue Größe kleiner als die alte Größe ist, wird das Array abgeschnitten, und es wird der gesamte nicht verwendete Arbeitsspeicher freigegeben. Verwenden Sie aus Gründen `SetSize` der Effizienz, um die Größe des Arrays festzulegen, bevor Sie es verwenden. Dadurch wird verhindert, dass jedes Mal, wenn ein Element hinzugefügt wird, neu zuzuordnen und kopiert werden muss.

Der *ngrowby* -Parameter wirkt sich auf die interne Speicher Belegung aus, während das Array wächst. Seine Verwendung wirkt sich nie auf die Array Größe aus, wie von `GetSize` und gemeldet `GetUpperBound` .

Wenn die Größe des Arrays zugenommen hat, werden alle neu zugeordneten **CObject** - <strong>\*</strong> Zeiger auf NULL festgelegt.

In der folgenden Tabelle werden andere Element Funktionen angezeigt, die ähneln `CObArray::SetSize` .

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**SetSize void (INT_PTR** `nNewSize` **, int** `nGrowBy` **=-1);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**SetSize void (INT_PTR** `nNewSize` **, int** `nGrowBy` **=-1);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**SetSize void (INT_PTR** `nNewSize` **, int** `nGrowBy` **=-1);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**SetSize void (INT_PTR** `nNewSize` **, int** `nGrowBy` **=-1);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**SetSize void (INT_PTR** `nNewSize` **, int** `nGrowBy` **=-1);**<br /><br /> **Throw (cmemoryexception \* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**SetSize void (INT_PTR** `nNewSize` **, int** `nGrowBy` **=-1);**<br /><br /> **Throw (cmemoryexception \* );**|

### <a name="example"></a>Beispiel

  Weitere Informationen finden Sie im Beispiel für [CObArray:: GetData](#getdata).

## <a name="see-also"></a>Weitere Informationen

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchie Diagramm](../../mfc/hierarchy-chart.md)<br/>
[Cstringarray-Klasse](../../mfc/reference/cstringarray-class.md)<br/>
[CPtrArray-Klasse](../../mfc/reference/cptrarray-class.md)<br/>
[CByteArray-Klasse](../../mfc/reference/cbytearray-class.md)<br/>
[CWordArray-Klasse](../../mfc/reference/cwordarray-class.md)<br/>
[Cdwordarray-Klasse](../../mfc/reference/cdwordarray-class.md)

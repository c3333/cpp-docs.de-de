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
ms.openlocfilehash: 7b923fd9231d3652d8d2f1750a8024d15287811e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360445"
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
|[CObArray::CObArray](#cobarray)|Erstellt ein leeres `CObject` Array für Zeiger.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CObArray::Hinzufügen](#add)|Fügt am Ende des Arrays ein Element hinzu; vergrößert das Array bei Bedarf.|
|[CObArray::Anfügen](#append)|Hängt ein anderes Array an das Array an; vergrößert das Array bei Bedarf.|
|[CObArray::Kopieren](#copy)|Kopiert ein anderes Array in das Array; vergrößert das Array bei Bedarf.|
|[CobArray::Elementat](#elementat)|Gibt einen temporären Verweis auf den Elementzeiger innerhalb des Arrays zurück.|
|[CObArray::FreeExtra](#freeextra)|Gibt den gesamten nicht verwendeten Arbeitsspeicher über der aktuellen Obergrenze frei.|
|[CobArray::Getat](#getat)|Gibt den Wert an einem bestimmten Index zurück.|
|[CObArray::GetCount](#getcount)|Ruft die Anzahl der Elemente im Array ab.|
|[CObArray::GetData](#getdata)|Ermöglicht den Zugriff auf Elemente im Array. Kann den Wert NULL haben.|
|[CObArray::GetSize](#getsize)|Ruft die Anzahl der Elemente im Array ab.|
|[CobArray::GetUpperbound](#getupperbound)|Gibt den größten gültigen Index zurück.|
|[CObArray::Insertat](#insertat)|Fügt ein Element (oder alle Elemente in einem anderen Array) am angegebenen Index ein.|
|[CobArray::IsEmpty](#isempty)|Bestimmt, ob das Array leer ist.|
|[CObArray::Alle entfernen](#removeall)|Entfernt alle Elemente aus diesem Array.|
|[CObArray::Removeat](#removeat)|Entfernt ein Element an einem spezifischen Index.|
|[CObArray::Setat](#setat)|Legt den Wert für einen bestimmten Index fest; Array darf nicht vergrößert werden.|
|[CobArray::Setatgrow](#setatgrow)|Legt den Wert für einen bestimmten Index fest; vergrößert das Array bei Bedarf.|
|[CObArray::SetSize](#setsize)|Legt die Anzahl der Elemente im Array fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CObArray::Operator \[\]](#operator_at)|Legt das Element am angegebenen Index fest oder ruft es ab.|

## <a name="remarks"></a>Bemerkungen

Diese Objektarrays ähneln C-Arrays, können jedoch bei Bedarf dynamisch verkleinert und vergrößert werden.

Arrayindizes beginnen immer an Position 0. Sie können entscheiden, ob die obere Grenze behoben werden soll oder ob das Array erweitert werden soll, wenn Sie Elemente über die aktuelle Grenze hinaus hinzufügen. Der Speicher wird der oberen Grenze zusammenhängend zugewiesen, auch wenn einige Elemente null sind.

Unter Win32 ist die `CObArray` Größe eines Objekts nur auf den verfügbaren Speicher beschränkt.

Wie bei einem C-Array ist `CObArray` die Zugriffszeit für ein indiziertes Element konstant und unabhängig von der Arraygröße.

`CObArray`enthält das IMPLEMENT_SERIAL Makro, um die Serialisierung und das Dumping seiner Elemente zu unterstützen. Wenn ein `CObject` Array von Zeigern in einem Archiv gespeichert wird, entweder `Serialize` mit dem `CObject` überladenen Einfügeoperator oder mit der Memberfunktion, wird jedes Element wiederum zusammen mit seinem Arrayindex serialisiert.

Wenn Sie ein Dump `CObject` einzelner Elemente in einem Array benötigen, müssen Sie die Tiefe des `CDumpContext` Objekts auf 1 oder höher festlegen.

Wenn `CObArray` ein Objekt gelöscht wird oder wenn seine `CObject` Elemente entfernt werden, werden nur die Zeiger entfernt, nicht die Objekte, auf die sie verweisen.

> [!NOTE]
> Vor dem Verwenden eines Arrays, verwenden Sie `SetSize`, um dessen Größe festzustellen, und weisen dafür Arbeitsspeicher zu. Wenn Sie `SetSize` nicht verwenden, kann das Hinzufügen von Elementen zu Ihrem Array dazu führen, dass es häufig neu zugeordnet und kopiert wird. Häufige Neuzuordnungen und Kopiervorgänge sind ineffizient und können zu einer Fragmentierung des Arbeitsspeichers führen.

Die Arrayklassenableitung ähnelt der Listenableitung. Weitere Informationen zur Ableitung einer speziellen Listenklasse finden Sie im Artikel [Sammlungen](../../mfc/collections.md).

> [!NOTE]
> Sie müssen das IMPLEMENT_SERIAL-Makro sinieren in der Implementierung der abgeleiteten Klasse verwenden, wenn Sie das Array serialisieren möchten.

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

[Cobject](../../mfc/reference/cobject-class.md)

`CObArray`

## <a name="requirements"></a>Anforderungen

**Kopf:** afxcoll.h

## <a name="cobarrayadd"></a><a name="add"></a>CObArray::Hinzufügen

Fügt ein neues Element am Ende eines Arrays hinzu, wodurch das Array um 1 erweitert wird.

```
INT_PTR Add(CObject* newElement);
```

### <a name="parameters"></a>Parameter

*Newelement*<br/>
Der `CObject` Zeiger, der diesem Array hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Der Index des hinzugefügten Elements.

### <a name="remarks"></a>Bemerkungen

Wenn [SetSize](#setsize) mit einem *nGrowBy-Wert* größer als 1 verwendet wurde, kann zusätzlicher Speicher zugewiesen werden. Die Obergrenze wird jedoch nur um 1 erhöht.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObArray::Add`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR Add( BYTE** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR Add( DWORD** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR Add( void** <strong>\*</strong> `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR Add( LPCTSTR** `newElement` **); throw( CMemoryException\* );**<br /><br /> **INT_PTR Add(const CString&** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR Add( UINT** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR Add( WORD** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|

### <a name="example"></a>Beispiel

  Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#75](../../mfc/codesnippet/cpp/cobarray-class_1.cpp)]

Die Ergebnisse dieses Programms sind wie folgt:

```Output
Add example: A CObArray with 2 elements
[0] = a CAge at $442A 21
[1] = a CAge at $4468 40
```

## <a name="cobarrayappend"></a><a name="append"></a>CObArray::Anfügen

Rufen Sie diese Memberfunktion auf, um den Inhalt eines anderen Arrays am Ende des angegebenen Arrays hinzuzufügen.

```
INT_PTR Append(const CObArray& src);
```

### <a name="parameters"></a>Parameter

*src*<br/>
Quelle der Elemente, die an das Array angehängt werden sollen.

### <a name="return-value"></a>Rückgabewert

Der Index des ersten angehängten Elements.

### <a name="remarks"></a>Bemerkungen

Die Arrays müssen vom gleichen Typ sein.

Falls erforderlich, kann zusätzlichem Speicher zugewiesen werden, `Append` um die an das Array angehängten Elemente unterzubringen.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObArray::Append`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR Append( const CByteArray&** *src* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR Append( const CDWordArray&** *src* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR Append( const CPtrArray&** *src* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR Append( const CStringArray&** *src* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR Append( const CUIntArray&** *src* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR Append( const CWordArray&** *src* **);**|

### <a name="example"></a>Beispiel

Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#76](../../mfc/codesnippet/cpp/cobarray-class_2.cpp)]

## <a name="cobarraycopy"></a><a name="copy"></a>CObArray::Kopieren

Rufen Sie diese Memberfunktion auf, um die Elemente des angegebenen Arrays mit den Elementen eines anderen Arrays desselben Typs zu überschreiben.

```
void Copy(const CObArray& src);
```

### <a name="parameters"></a>Parameter

*src*<br/>
Quelle der Elemente, die in das Array kopiert werden sollen.

### <a name="remarks"></a>Bemerkungen

`Copy`gibt keinen Speicher frei; Bei Bedarf kann `Copy` jedoch zusätzlicher Speicher zugewiesen werden, um die in das Array kopierten Elemente aufzunehmen.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObArray::Copy`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void Copy( const CByteArray&** *src* **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void Copy( const CDWordArray&** *src* **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void Copy( const CPtrArray&** *src* **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void Copy( const CStringArray&** *src* **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void Copy( const CUIntArray&** *src* **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void Copy( const CWordArray&** *src* **);**|

### <a name="example"></a>Beispiel

Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#77](../../mfc/codesnippet/cpp/cobarray-class_3.cpp)]

## <a name="cobarraycobarray"></a><a name="cobarray"></a>CObArray::CObArray

Erstellt ein `CObject` leeres Zeigerarray.

```
CObArray();
```

### <a name="remarks"></a>Bemerkungen

Das Array wächst jeweils um ein Element.

Die folgende Tabelle zeigt andere Konstruktoren, die `CObArray::CObArray`ähnlich wie sind.

|Klasse|Konstruktor|
|-----------|-----------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**CByteArray( );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**CDWordArray( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**CPtrArray( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CStringArray( );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**CUIntArray( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**CWordArray( );**|

### <a name="example"></a>Beispiel

[!code-cpp[NVC_MFCCollections#78](../../mfc/codesnippet/cpp/cobarray-class_4.cpp)]

## <a name="cobarrayelementat"></a><a name="elementat"></a>CobArray::Elementat

Gibt einen temporären Verweis auf den Elementzeiger innerhalb des Arrays zurück.

```
CObject*& ElementAt(INT_PTR nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein Ganzzahlindex, der größer oder gleich 0 und kleiner oder `GetUpperBound`gleich dem von zurückgegebenen Wert ist.

### <a name="return-value"></a>Rückgabewert

Ein Verweis `CObject` auf einen Zeiger.

### <a name="remarks"></a>Bemerkungen

Es wird verwendet, um den linken Zuweisungsoperator für Arrays zu implementieren. Beachten Sie, dass dies eine erweiterte Funktion ist, die nur zum Implementieren spezieller Arrayoperatoren verwendet werden sollte.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObArray::ElementAt`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE& ElementAt( INT_PTR** `nIndex` **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD& ElementAt( INT_PTR** `nIndex` **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\*& ElementAt( INT_PTR** `nIndex` **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString& ElementAt( INT_PTR** `nIndex` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT& ElementAt( INT_PTR** `nIndex` **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD& ElementAt( INT_PTR** `nIndex` **);**|

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CObArray::GetSize](#getsize).

## <a name="cobarrayfreeextra"></a><a name="freeextra"></a>CObArray::FreeExtra

Gibt zusätzlichen Speicher frei, der beim Wachsen des Arrays zugewiesen wurde.

```
void FreeExtra();
```

### <a name="remarks"></a>Bemerkungen

Diese Funktion hat keine Auswirkungen auf die Größe oder Obergrenze des Arrays.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObArray::FreeExtra`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void FreeExtra( );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void FreeExtra( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void FreeExtra( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void FreeExtra( );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void FreeExtra( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void FreeExtra( );**|

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CObArray::GetData](#getdata).

## <a name="cobarraygetat"></a><a name="getat"></a>CobArray::Getat

Gibt das Arrayelement am angegebenen Index zurück.

```
CObject* GetAt(INT_PTR nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein Ganzzahlindex, der größer oder gleich 0 und kleiner oder `GetUpperBound`gleich dem von zurückgegebenen Wert ist.

### <a name="return-value"></a>Rückgabewert

Das `CObject` Zeigerelement, das sich derzeit in diesem Index befindet.

### <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Das Übergeben eines negativen Werts oder `GetUpperBound` eines Wertes, der größer als der von zurückgegebene Wert ist, führt zu einer fehlgeschlagenen Assertion.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObArray::GetAt`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE GetAt( INT_PTR** `nIndex` **) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD GetAt( INT_PTR** `nIndex` **) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void\* GetAt( INT_PTR** `nIndex` **) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString GetAt( INT_PTR** `nIndex` **) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT GetAt( INT_PTR** `nIndex` **) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD GetAt( INT_PTR** `nIndex` **) const;**|

### <a name="example"></a>Beispiel

Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#79](../../mfc/codesnippet/cpp/cobarray-class_5.cpp)]

## <a name="cobarraygetcount"></a><a name="getcount"></a>CObArray::GetCount

Gibt die Anzahl der Arrayelemente zurück.

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Elemente im Array.

### <a name="remarks"></a>Bemerkungen

Rufen Sie diese Methode auf, um die Anzahl der Elemente im Array abzurufen. Da Indizes nullbasiert sind, ist die Größe 1 größer als der größte Index.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObArray::GetCount`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetCount( ) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetCount( ) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetCount( ) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetCount( ) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetCount( ) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetCount( ) const;**|

### <a name="example"></a>Beispiel

Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#80](../../mfc/codesnippet/cpp/cobarray-class_6.cpp)]

## <a name="cobarraygetdata"></a><a name="getdata"></a>CObArray::GetData

Verwenden Sie diese Memberfunktion, um direkten Zugriff auf die Elemente im Array zu erhalten.

```
const CObject** GetData() const;

CObject** GetData();
```

### <a name="return-value"></a>Rückgabewert

Ein Zeiger auf das `CObject` Array von Zeigern.

### <a name="remarks"></a>Bemerkungen

Wenn keine Elemente `GetData` verfügbar sind, wird ein NULL-Wert zurückgegeben.

Während der direkte Zugriff auf die Elemente eines Arrays Ihnen `GetData`helfen kann, schneller zu arbeiten, sollten Sie beim Aufrufen Vorsicht walten lassen. Alle Fehler, die Sie machen, wirken sich direkt auf die Elemente Ihres Arrays aus.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObArray::GetData`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**const BYTE\* GetData( ) const; BYTE\* GetData( );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**const DWORD\* GetData( )\* const;DWORD GetData( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**const\* \* void GetData( )\* \* const;void GetData( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**const CString\* GetData( ) const; CString\* GetData( );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**const UINT\* GetData( ) const; UINT\* GetData( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**const\* WORD GetData( ) const; WORD\* GetData( );**|

### <a name="example"></a>Beispiel

Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#81](../../mfc/codesnippet/cpp/cobarray-class_7.cpp)]

## <a name="cobarraygetsize"></a><a name="getsize"></a>CObArray::GetSize

Gibt die Größe des Arrays zurück.

```
INT_PTR GetSize() const;
```

### <a name="remarks"></a>Bemerkungen

Da Indizes nullbasiert sind, ist die Größe 1 größer als der größte Index.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObArray::GetSize`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetSize( ) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetSize( ) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetSize( ) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetSize( ) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetSize( ) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetSize( ) const;**|

### <a name="example"></a>Beispiel

Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#82](../../mfc/codesnippet/cpp/cobarray-class_8.cpp)]

## <a name="cobarraygetupperbound"></a><a name="getupperbound"></a>CobArray::GetUpperbound

Gibt die aktuelle Obergrenze dieses Arrays zurück.

```
INT_PTR GetUpperBound() const;
```

### <a name="return-value"></a>Rückgabewert

Der Index der Oberen Grenze (nullbasiert).

### <a name="remarks"></a>Bemerkungen

Da Arrayindizes nullbasiert sind, gibt diese Funktion `GetSize`einen Wert 1 kleiner als zurück.

Die `GetUpperBound( )` Bedingung = -1 gibt an, dass das Array keine Elemente enthält.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObArray::GetUpperBound`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**INT_PTR GetUpperBound( ) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**INT_PTR GetUpperBound( ) const;**|

### <a name="example"></a>Beispiel

Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#83](../../mfc/codesnippet/cpp/cobarray-class_9.cpp)]

## <a name="cobarrayinsertat"></a><a name="insertat"></a>CObArray::Insertat

Fügt ein Element (oder alle Elemente in einem anderen Array) am angegebenen Index ein.

```
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
Ein Ganzzahlindex, der größer sein kann `GetUpperBound`als der von zurückgegebene Wert.

*Newelement*<br/>
Der `CObject` Zeiger, der in diesem Array platziert werden soll. Ein *neuesElement* des Wertes NULL ist zulässig.

*nCount*<br/>
Die Häufigkeit, mit der dieses Element eingefügt werden soll (Standardwert 1).

*nStartIndex*<br/>
Ein Ganzzahlindex, der größer sein kann `GetUpperBound`als der von zurückgegebene Wert.

*pNewArray*<br/>
Ein weiteres Array, das Elemente enthält, die diesem Array hinzugefügt werden sollen.

### <a name="remarks"></a>Bemerkungen

Die erste `InsertAt` Version von fügt ein Element (oder mehrere Kopien eines Elements) an einem angegebenen Index in einem Array ein. Dabei verschiebt er das vorhandene Element an diesem Index (durch Inkrementieren des Indexes) nach oben und verschiebt alle darüber genannten Elemente nach oben.

Die zweite Version fügt alle `CObArray` Elemente aus einer anderen Auflistung ein, beginnend an der *nStartIndex-Position.*

Die `SetAt` Funktion hingegen ersetzt ein angegebenes Arrayelement und verschiebt keine Elemente.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObArray::InsertAt`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, BYTE** `newElement` **, int** `nCount` **= 1 );**<br /><br /> **throw( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CByteArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, DWORD** `newElement` **, int** `nCount` **= 1 );**<br /><br /> **throw( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CDWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **, int** `nCount` **= 1 );**<br /><br /> **throw( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CPtrArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, LPCTSTR** `newElement` , **int** `nCount` **= 1 );**<br /><br /> **throw( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CStringArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, UINT** `newElement` , **int** `nCount` **= 1 );**<br /><br /> **throw( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CUIntArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void InsertAt( INT_PTR** `nIndex` **, WORD** `newElement` **, int** `nCount` **= 1 );**<br /><br /> **throw( CMemoryException\* );**<br /><br /> **void InsertAt( INT_PTR** `nStartIndex` **, CWordArray** <strong>\*</strong> `pNewArray` **);**<br /><br /> **throw( CMemoryException\* );**|

### <a name="example"></a>Beispiel

  Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#84](../../mfc/codesnippet/cpp/cobarray-class_10.cpp)]

Die Ergebnisse dieses Programms sind wie folgt:

```Output
InsertAt example: A CObArray with 3 elements
[0] = a CAge at $45C8 21
[1] = a CAge at $4646 30
[2] = a CAge at $4606 40
```

## <a name="cobarrayisempty"></a><a name="isempty"></a>CobArray::IsEmpty

Bestimmt, ob das Array leer ist.

```
BOOL IsEmpty() const;
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Array leer ist; andernfalls 0.

## <a name="cobarrayoperator--"></a><a name="operator_at"></a>CObArray::operator [ ]

Diese Subskriptoperatoren sind ein `SetAt` `GetAt` bequemer Ersatz für die und Funktionen.

```
CObject*& operator[](int_ptr nindex);
CObject* operator[](int_ptr nindex) const;
```

### <a name="remarks"></a>Bemerkungen

Der erste Operator, der für Arrays aufgerufen wird, die nicht **const**sind, kann entweder auf der rechten (r-Wert) oder auf der linken (l-Wert) einer Zuweisungsanweisung verwendet werden. Die zweite, **const** für const-Arrays aufgerufen, darf nur auf der rechten Seite verwendet werden.

Die Debug-Version der Bibliothek bestätigt, ob das Subskript (entweder auf der linken oder rechten Seite einer Zuweisungsanweisung) a-bounds ist.

Die folgende Tabelle zeigt andere `CObArray::operator []`Operatoren, die ähnlich wie sind.

|Klasse|Operator|
|-----------|--------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**BYTE& Operator [](int_ptr** `nindex` ** \);**<br /><br /> **BYTE-Operator [](int_ptr** `nindex` ** \) const;**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**DWORD& Operator [](int_ptr** `nindex` ** \);**<br /><br /> **DWORD-Operator [](int_ptr** `nindex` ** \) const;**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**nichtig\*& Operator [](int_ptr** `nindex` ** \);**<br /><br /> **void-Operator\* [](int_ptr** `nindex` ** \) const;**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**CString& Operator [](int_ptr** `nindex` ** \);**<br /><br /> **CString-Operator [](int_ptr** `nindex` ** \) const;**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**UINT-& Operator [](int_ptr** `nindex` ** \);**<br /><br /> **UINT-Operator [](int_ptr** `nindex` ** \) const;**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**WORD& Operator [](int_ptr** `nindex` ** \);**<br /><br /> **WORD-Operator [](int_ptr** `nindex` ** \) const;**|

### <a name="example"></a>Beispiel

Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#88](../../mfc/codesnippet/cpp/cobarray-class_11.cpp)]

## <a name="cobarrayremoveall"></a><a name="removeall"></a>CObArray::Alle entfernen

Entfernt alle Zeiger aus diesem Array, löscht die `CObject` Objekte jedoch nicht.

```
void RemoveAll();
```

### <a name="remarks"></a>Bemerkungen

Wenn das Array bereits leer ist, funktioniert die Funktion weiterhin.

Die `RemoveAll` Funktion gibt den gesamten Speicher frei, der für die Zeigerspeicherung verwendet wird.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObArray::RemoveAll`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAll( );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAll( );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAll( );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAll( );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAll( );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAll( );**|

### <a name="example"></a>Beispiel

Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#85](../../mfc/codesnippet/cpp/cobarray-class_12.cpp)]

## <a name="cobarrayremoveat"></a><a name="removeat"></a>CObArray::Removeat

Entfernt ein oder mehrere Elemente, die bei einem angegebenen Index in einem Array beginnen.

```
void RemoveAt(
    INT_PTR nIndex,
    INT_PTR nCount = 1);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein Ganzzahlindex, der größer oder gleich 0 und kleiner oder `GetUpperBound`gleich dem von zurückgegebenen Wert ist.

*nCount*<br/>
Die Anzahl der zu entfernenden Elemente.

### <a name="remarks"></a>Bemerkungen

Dabei verschiebt er alle Elemente über den entfernten Elementen nach unten. Es dekrementiert die obere Grenze des Arrays, gibt jedoch keinen Speicher frei.

Wenn Sie versuchen, mehr Elemente zu entfernen, als im Array über dem Entfernungspunkt enthalten sind, wird die Debug-Version der Bibliothek bestätigt.

Die `RemoveAt` Funktion entfernt `CObject` den Zeiger aus dem Array, löscht jedoch nicht das Objekt selbst.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObArray::RemoveAt`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** `nCount` **= 1 );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void RemoveAt( INT_PTR** `nIndex` **, INT_PTR** *nCount* **= 1 );**|

### <a name="example"></a>Beispiel

  Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#112](../../mfc/codesnippet/cpp/cobarray-class_13.cpp)]

Die Ergebnisse dieses Programms sind wie folgt:

```Output
RemoveAt example: A CObArray with 1 elements
[0] = a CAge at $4606 40
```

## <a name="cobarraysetat"></a><a name="setat"></a>CObArray::Setat

Legt das Arrayelement auf den angegebenen Index fest.

```
void SetAt(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein Ganzzahlindex, der größer oder gleich 0 und kleiner oder `GetUpperBound`gleich dem von zurückgegebenen Wert ist.

*Newelement*<br/>
Der Objektzeiger, der in dieses Array eingefügt werden soll. Ein NULL-Wert ist zulässig.

### <a name="remarks"></a>Bemerkungen

`SetAt`führt nicht dazu, dass das Array wächst. Verwenden `SetAtGrow` Sie diese Option, wenn das Array automatisch vergrößert werden soll.

Sie müssen sicherstellen, dass der Indexwert eine gültige Position im Array darstellt. Wenn es aprioriert, wird die Debug-Version der Bibliothek bestätigt.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObArray::SetAt`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAt( INT_PTR** `nIndex` **, BYTE** `newElement` **);**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, DWORD** `newElement` **);**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **);**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, UINT** `newElement` **);**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAt( INT_PTR** `nIndex` **, WORD** `newElement` **);**|

### <a name="example"></a>Beispiel

  Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#86](../../mfc/codesnippet/cpp/cobarray-class_14.cpp)]

Die Ergebnisse dieses Programms sind wie folgt:

```Output
SetAt example: A CObArray with 2 elements
[0] = a CAge at $47E0 30
[1] = a CAge at $47A0 40
```

## <a name="cobarraysetatgrow"></a><a name="setatgrow"></a>CobArray::Setatgrow

Legt das Arrayelement auf den angegebenen Index fest.

```
void SetAtGrow(
    INT_PTR nIndex,
    CObject* newElement);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Ein Ganzzahlindex, der größer oder gleich 0 ist.

*Newelement*<br/>
Der Objektzeiger, der diesem Array hinzugefügt werden soll. Ein NULL-Wert ist zulässig.

### <a name="remarks"></a>Bemerkungen

Das Array wird bei Bedarf automatisch vergrößert (d. h. die obere Grenze wird angepasst, um das neue Element aufzunehmen).

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObArray::SetAtGrow`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, BYTE** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, DWORD** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, void** <strong>\*</strong> `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, LPCTSTR** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, UINT** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetAtGrow( INT_PTR** `nIndex` **, WORD** `newElement` **);**<br /><br /> **throw( CMemoryException\* );**|

### <a name="example"></a>Beispiel

  Eine Auflistung der Klasse, die `CAge` in allen Sammlungsbeispielen verwendet wird, finden Sie unter [CObList::CObList.](../../mfc/reference/coblist-class.md#coblist)

[!code-cpp[NVC_MFCCollections#87](../../mfc/codesnippet/cpp/cobarray-class_15.cpp)]

Die Ergebnisse dieses Programms sind wie folgt:

```Output
SetAtGrow example: A CObArray with 4 elements
[0] = a CAge at $47C0 21
[1] = a CAge at $4800 40
[2] = NULL
[3] = a CAge at $4840 65
```

## <a name="cobarraysetsize"></a><a name="setsize"></a>CObArray::SetSize

Legt die Größe eines leeren oder vorhandenen Arrays fest. reserviert bei Bedarf Speicher.

```
void SetSize(
    INT_PTR nNewSize,
    INT_PTR nGrowBy = -1);
```

### <a name="parameters"></a>Parameter

*nNewSize*<br/>
Die neue Arraygröße (Anzahl der Elemente). Muss größer als oder gleich 0 sein.

*nGrowBy*<br/>
Die minimale Anzahl von Elementsteckplätzen, die zugewiesen werden sollen, wenn eine Größenerhöhung erforderlich ist.

### <a name="remarks"></a>Bemerkungen

Wenn die neue Größe kleiner als die alte Größe ist, wird das Array abgeschnitten, und der gesamte nicht verwendete Speicher wird freigegeben. Rufen Sie `SetSize` aus Gründen der Effizienz an, um die Größe des Arrays festzulegen, bevor Sie es verwenden. Dadurch wird verhindert, dass das Array bei jedem Addieren eines Elements neu zugeordnet und kopiert werden muss.

Der Parameter *nGrowBy* wirkt sich auf die interne Speicherzuweisung aus, während das Array wächst. Seine Verwendung wirkt sich nie `GetSize` auf `GetUpperBound`die Arraygröße aus, wie von und berichtet.

Wenn die Größe des Arrays größer geworden ist, werden alle neu zugewiesenen **CObject-Zeiger** <strong>\*</strong> auf NULL gesetzt.

Die folgende Tabelle zeigt andere Memberfunktionen, die `CObArray::SetSize`ähnlich wie sind.

|Klasse|Memberfunktion|
|-----------|---------------------|
|[CByteArray](../../mfc/reference/cbytearray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` = **-1 );**<br /><br /> **throw( CMemoryException\* );**|
|[CDWordArray](../../mfc/reference/cdwordarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` = **-1 );**<br /><br /> **throw( CMemoryException\* );**|
|[CPtrArray](../../mfc/reference/cptrarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` = **-1 );**<br /><br /> **throw( CMemoryException\* );**|
|[CStringArray](../../mfc/reference/cstringarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` = **-1 );**<br /><br /> **throw( CMemoryException\* );**|
|[CUIntArray](../../mfc/reference/cuintarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` = **-1 );**<br /><br /> **throw( CMemoryException\* );**|
|[CWordArray](../../mfc/reference/cwordarray-class.md)|**void SetSize( INT_PTR** `nNewSize` **, int** `nGrowBy` = **-1 );**<br /><br /> **throw( CMemoryException\* );**|

### <a name="example"></a>Beispiel

  Siehe Beispiel für [CObArray::GetData](#getdata).

## <a name="see-also"></a>Siehe auch

[CObject-Klasse](../../mfc/reference/cobject-class.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CStringArray-Klasse](../../mfc/reference/cstringarray-class.md)<br/>
[CPtrArray-Klasse](../../mfc/reference/cptrarray-class.md)<br/>
[CByteArray-Klasse](../../mfc/reference/cbytearray-class.md)<br/>
[CWordArray-Klasse](../../mfc/reference/cwordarray-class.md)<br/>
[CDWordArray-Klasse](../../mfc/reference/cdwordarray-class.md)

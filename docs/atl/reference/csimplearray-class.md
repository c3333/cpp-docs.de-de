---
title: CSimpleArray-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::CSimpleArray
- ATLSIMPCOLL/ATL::CSimpleArray::Add
- ATLSIMPCOLL/ATL::CSimpleArray::Find
- ATLSIMPCOLL/ATL::CSimpleArray::GetData
- ATLSIMPCOLL/ATL::CSimpleArray::GetSize
- ATLSIMPCOLL/ATL::CSimpleArray::Remove
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleArray::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleArray::SetAtIndex
helpviewer_keywords:
- CSimpleArray class
ms.assetid: ee0c9f39-b61c-4c18-bc43-4eada21dca3a
ms.openlocfilehash: d3386687757412d09e4df29e84f691f1615c472a
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746472"
---
# <a name="csimplearray-class"></a>CSimpleArray-Klasse

Diese Klasse stellt Methoden zum Verwalten eines einfachen Arrays bereit.

## <a name="syntax"></a>Syntax

```
template <class T, class TEqual = CSimpleArrayEqualHelper<T>>
class CSimpleArray
```

#### <a name="parameters"></a>Parameter

*T*<br/>
Der Typ der Daten, die im Array gespeichert werden sollen.

*TEqual*<br/>
Ein Merkmalsobjekt, das den Gleichheitstest für Elemente des Typs *T*definiert.

## <a name="members"></a>Member

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSimpleArray::CSimpleArray](#csimplearray)|Der Konstruktor für das einfache Array.|
|[CSimpleArray::'CSimpleArray](#dtor)|Der Destruktor für das einfache Array.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSimpleArray::Hinzufügen](#add)|Fügt dem Array ein neues Element hinzu.|
|[CSimpleArray::Suchen](#find)|Sucht ein Element im Array.|
|[CSimpleArray::GetData](#getdata)|Gibt einen Zeiger auf die im Array gespeicherten Daten zurück.|
|[CSimpleArray::GetSize](#getsize)|Gibt die Anzahl der im Array gespeicherten Elemente zurück.|
|[CSimpleArray::Entfernen](#remove)|Entfernt ein bestimmtes Element aus dem Array.|
|[CSimpleArray::RemoveAll](#removeall)|Entfernt alle Elemente aus dem Array.|
|[CSimpleArray::Removeat](#removeat)|Entfernt das angegebene Element aus dem Array.|
|[CSimpleArray::SetatIndex](#setatindex)|Legt das angegebene Element im Array fest.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSimpleArray::operator\[\]](#operator_at)|Ruft ein Element aus dem Array ab.|
|[CSimpleArray::operator =](#operator_eq)|Zuweisungsoperator.|

## <a name="remarks"></a>Bemerkungen

`CSimpleArray`bietet Methoden zum Erstellen und Verwalten eines `T`einfachen Arrays eines beliebigen Typs .

Der `TEqual` Parameter bietet eine Möglichkeit, eine Gleichheitsfunktion für zwei Elemente des Typs zu `T`definieren. Durch Das Erstellen einer Klasse ähnlich [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)ist es möglich, das Verhalten des Gleichheitstests für ein bestimmtes Array zu ändern. Wenn Sie z. B. mit einem Array von Zeigern umgehen, kann es nützlich sein, die Gleichheit in Abhängigkeit von den Werten zu definieren, auf die die Zeiger verweisen. Die Standardimplementierung verwendet **operator=()**.

Sowohl `CSimpleArray` als auch [CSimpleMap](../../atl/reference/csimplemap-class.md) sind für eine kleine Anzahl von Elementen konzipiert. [CAtlArray](../../atl/reference/catlarray-class.md) und [CAtlMap](../../atl/reference/catlmap-class.md) sollten verwendet werden, wenn das Array eine große Anzahl von Elementen enthält.

## <a name="requirements"></a>Requirements (Anforderungen)

**Kopfzeile:** atlsimpcoll.h

## <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#86](../../atl/codesnippet/cpp/csimplearray-class_1.cpp)]

## <a name="csimplearrayadd"></a><a name="add"></a>CSimpleArray::Hinzufügen

Fügt dem Array ein neues Element hinzu.

```
BOOL Add(const T& t);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Das Element, das dem Array hinzugefügt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das Element erfolgreich zum Array hinzugefügt wurde, andernfalls FALSE.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#87](../../atl/codesnippet/cpp/csimplearray-class_2.cpp)]

## <a name="csimplearraycsimplearray"></a><a name="csimplearray"></a>CSimpleArray::CSimpleArray

Der Konstruktor für das Arrayobjekt.

```
CSimpleArray(const CSimpleArray<T, TEqual>& src);
CSimpleArray();
```

### <a name="parameters"></a>Parameter

*src*<br/>
Ein vorhandenes `CSimpleArray`-Objekt.

### <a name="remarks"></a>Bemerkungen

Initialisiert die Datenmember, indem `CSimpleArray` ein neues leeres Objekt `CSimpleArray` oder eine Kopie eines vorhandenen Objekts erstellt wird.

## <a name="csimplearraycsimplearray"></a><a name="dtor"></a>CSimpleArray::'CSimpleArray

Der Destruktor.

```
~CSimpleArray();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugewiesenen Ressourcen frei.

## <a name="csimplearrayfind"></a><a name="find"></a>CSimpleArray::Suchen

Sucht ein Element im Array.

```
int Find(const T& t) const;
```

### <a name="parameters"></a>Parameter

*T*<br/>
Das Element, nach dem gesucht werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt den Index des gefundenen Elements zurück, oder -1, wenn das Element nicht gefunden wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#88](../../atl/codesnippet/cpp/csimplearray-class_3.cpp)]

## <a name="csimplearraygetdata"></a><a name="getdata"></a>CSimpleArray::GetData

Gibt einen Zeiger auf die im Array gespeicherten Daten zurück.

```
T* GetData() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf die Daten im Array zurück.

## <a name="csimplearraygetsize"></a><a name="getsize"></a>CSimpleArray::GetSize

Gibt die Anzahl der im Array gespeicherten Elemente zurück.

```
int GetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der im Array gespeicherten Elemente zurück.

## <a name="csimplearrayoperator-"></a><a name="operator_at"></a>CSimpleArray::Operator\[\]

Ruft ein Element aus dem Array ab.

```
T& operator[](int nindex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der Elementindex.

### <a name="return-value"></a>Rückgabewert

Gibt das Element des Arrays zurück, auf das von *nIndex*verwiesen wird.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#89](../../atl/codesnippet/cpp/csimplearray-class_4.cpp)]

## <a name="csimplearrayoperator-"></a><a name="operator_eq"></a>CSimpleArray::operator =

Zuweisungsoperator.

```
CSimpleArray<T, TEqual>
& operator=(
    const CSimpleArray<T, TEqual>& src);
```

### <a name="parameters"></a>Parameter

*src*<br/>
Das Array, das kopiert werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt einen Zeiger auf `CSimpleArray` das aktualisierte Objekt zurück.

### <a name="remarks"></a>Bemerkungen

Kopiert alle Elemente `CSimpleArray` aus dem Objekt, auf das *src* verweist, in das aktuelle Arrayobjekt und ersetzt alle vorhandenen Daten.

### <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#90](../../atl/codesnippet/cpp/csimplearray-class_5.cpp)]

## <a name="csimplearrayremove"></a><a name="remove"></a>CSimpleArray::Entfernen

Entfernt ein bestimmtes Element aus dem Array.

```
BOOL Remove(const T& t);
```

### <a name="parameters"></a>Parameter

*T*<br/>
Das Element, das aus dem Array entfernt werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das Element gefunden und entfernt wird, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Wenn ein Element entfernt wird, werden die verbleibenden Elemente im Array neu nummeriert, um den leeren Raum zu füllen.

## <a name="csimplearrayremoveall"></a><a name="removeall"></a>CSimpleArray::RemoveAll

Entfernt alle Elemente aus dem Array.

```cpp
void RemoveAll();
```

### <a name="remarks"></a>Bemerkungen

Entfernt alle Elemente, die derzeit im Array gespeichert sind.

## <a name="csimplearrayremoveat"></a><a name="removeat"></a>CSimpleArray::Removeat

Entfernt das angegebene Element aus dem Array.

```
BOOL RemoveAtint nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Index, der auf das zu entfernende Element zeigt.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn das Element entfernt wurde, FALSE, wenn der Index ungültig war.

### <a name="remarks"></a>Bemerkungen

Wenn ein Element entfernt wird, werden die verbleibenden Elemente im Array neu nummeriert, um den leeren Raum zu füllen.

## <a name="csimplearraysetatindex"></a><a name="setatindex"></a>CSimpleArray::SetatIndex

Legen Sie das angegebene Element im Array fest.

```
BOOL SetAtIndex(
    int nIndex,
    const T& t);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der Index des zu ändernden Elements.

*T*<br/>
Der dem angegebenen Element zuzuweisende Wert.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn erfolgreich, FALSE, wenn der Index ungültig war.

## <a name="see-also"></a>Weitere Informationen

[Klassenübersicht](../../atl/atl-class-overview.md)

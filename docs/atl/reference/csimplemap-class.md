---
title: CSimpleMap-Klasse
ms.date: 11/04/2016
f1_keywords:
- CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayElementType
- ATLSIMPCOLL/ATL::CSimpleMap::_ArrayKeyType
- ATLSIMPCOLL/ATL::CSimpleMap::CSimpleMap
- ATLSIMPCOLL/ATL::CSimpleMap::Add
- ATLSIMPCOLL/ATL::CSimpleMap::FindKey
- ATLSIMPCOLL/ATL::CSimpleMap::FindVal
- ATLSIMPCOLL/ATL::CSimpleMap::GetKeyAt
- ATLSIMPCOLL/ATL::CSimpleMap::GetSize
- ATLSIMPCOLL/ATL::CSimpleMap::GetValueAt
- ATLSIMPCOLL/ATL::CSimpleMap::Lookup
- ATLSIMPCOLL/ATL::CSimpleMap::Remove
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAll
- ATLSIMPCOLL/ATL::CSimpleMap::RemoveAt
- ATLSIMPCOLL/ATL::CSimpleMap::ReverseLookup
- ATLSIMPCOLL/ATL::CSimpleMap::SetAt
- ATLSIMPCOLL/ATL::CSimpleMap::SetAtIndex
helpviewer_keywords:
- CSimpleMap class
ms.assetid: 61b06eb4-ae73-44b0-a305-0afb5a33e8b1
ms.openlocfilehash: b8650f36ac3d190207870616754dcd596cb7cc45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330800"
---
# <a name="csimplemap-class"></a>CSimpleMap-Klasse

Diese Klasse bietet Unterstützung für ein einfaches Zuordnungsarray.

## <a name="syntax"></a>Syntax

```
template <class TKey, class TVal, class TEqual = CSimpleMapEqualHelper<TKey, TVal>>
class CSimpleMap
```

#### <a name="parameters"></a>Parameter

*TKey*<br/>
Der Schlüsselelementtyp.

*TVal*<br/>
Der Wertelementtyp.

*TEqual*<br/>
Ein Merkmalsobjekt, das den Gleichheitstest für Elemente des Typs `T`definiert.

## <a name="members"></a>Member

### <a name="public-typedefs"></a>Öffentliche Typedefs

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSimpleMap::_ArrayElementType](#_arrayelementtype)|Typedef für den Werttyp.|
|[CSimpleMap::_ArrayKeyType](#_arraykeytype)|Typedef für den Schlüsseltyp.|

### <a name="public-constructors"></a>Öffentliche Konstruktoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSimpleMap::CSimpleMap](#csimplemap)|Der Konstruktor.|
|[CSimpleMap::'CSimpleMap](#dtor)|Der Destruktor.|

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CSimpleMap::Hinzufügen](#add)|Fügt dem Kartenarray einen Schlüssel und einen zugeordneten Wert hinzu.|
|[CSimpleMap::FindKey](#findkey)|Sucht einen bestimmten Schlüssel.|
|[CSimpleMap::FindVal](#findval)|Sucht einen bestimmten Wert.|
|[CSimpleMap::GetKeyAt](#getkeyat)|Ruft den angegebenen Schlüssel ab.|
|[CSimpleMap::GetSize](#getsize)|Gibt die Anzahl der Einträge im Zuordnungsarray zurück.|
|[CSimpleMap::GetValueAt](#getvalueat)|Ruft den angegebenen Wert ab.|
|[CSimpleMap::Lookup](#lookup)|Gibt den Wert zurück, der dem angegebenen Schlüssel zugeordnet ist.|
|[CSimpleMap::Entfernen](#remove)|Entfernt einen Schlüssel und einen übereinstimmenden Wert.|
|[CSimpleMap::RemoveAll](#removeall)|Entfernt alle Schlüssel und Werte.|
|[CSimpleMap::RemoveAt](#removeat)|Entfernt einen bestimmten Schlüssel und übereinstimmenden Wert.|
|[CSimpleMap::ReverseLookup](#reverselookup)|Gibt den Schlüssel zurück, der dem angegebenen Wert zugeordnet ist.|
|[CSimpleMap::SetAt](#setat)|Legt den Wert fest, der dem angegebenen Schlüssel zugeordnet ist.|
|[CSimpleMap::SetAtIndex](#setatindex)|Legt den spezifischen Schlüssel und Wert fest.|

## <a name="remarks"></a>Bemerkungen

`CSimpleMap`bietet Unterstützung für ein einfaches Zuordnungsarray eines beliebigen Typs , `T`das ein ungeordnetes Array von Schlüsselelementen und den zugehörigen Werten verwaltet.

Der `TEqual` Parameter bietet eine Möglichkeit, eine Gleichheitsfunktion für zwei Elemente des Typs zu `T`definieren. Durch Das Erstellen einer Klasse ähnlich [CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)ist es möglich, das Verhalten des Gleichheitstests für ein bestimmtes Array zu ändern. Wenn Sie z. B. mit einem Array von Zeigern umgehen, kann es nützlich sein, die Gleichheit in Abhängigkeit von den Werten zu definieren, auf die die Zeiger verweisen. Die Standardimplementierung verwendet **Operator ==()**.

Beide `CSimpleMap` und [CSimpleArray](../../atl/reference/csimplearray-class.md) werden für die Kompatibilität mit früheren ATL-Versionen bereitgestellt, und vollständigere und effizientere Auflistungsimplementierungen werden von [CAtlArray](../../atl/reference/catlarray-class.md) und [CAtlMap](../../atl/reference/catlmap-class.md)bereitgestellt.

Im Gegensatz zu anderen Kartensammlungen in ATL und MFC wird diese Klasse mit einem einfachen Array implementiert, und Suchsuchen erfordern eine lineare Suche. `CAtlMap`sollte verwendet werden, wenn das Array eine große Anzahl von Elementen enthält.

## <a name="requirements"></a>Anforderungen

**Kopfzeile:** atlsimpcoll.h

## <a name="example"></a>Beispiel

[!code-cpp[NVC_ATL_Utilities#91](../../atl/codesnippet/cpp/csimplemap-class_1.cpp)]

## <a name="csimplemapadd"></a><a name="add"></a>CSimpleMap::Hinzufügen

Fügt dem Kartenarray einen Schlüssel und einen zugeordneten Wert hinzu.

```
BOOL Add(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüssel.

*Val*<br/>
Der zugeordnete Wert.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn der Schlüssel und der Wert erfolgreich hinzugefügt wurden, andernfalls FALSE.

### <a name="remarks"></a>Bemerkungen

Jedes hinzugefügte Schlüssel- und Wertpaar bewirkt, dass der Mapping-Array-Speicher freigegeben und neu zugeordnet wird, um sicherzustellen, dass die Daten für jeden Immer zusammenhängend gespeichert werden. Das heißt, das zweite Schlüsselelement folgt immer direkt dem ersten Schlüsselelement im Speicher und so weiter.

## <a name="csimplemap_arrayelementtype"></a><a name="_arrayelementtype"></a>CSimpleMap::_ArrayElementType

Ein typedef für den Schlüsseltyp.

```
typedef TVal _ArrayElementType;
```

## <a name="csimplemap_arraykeytype"></a><a name="_arraykeytype"></a>CSimpleMap::_ArrayKeyType

Ein typedef für den Werttyp.

```
typedef TKey _ArrayKeyType;
```

## <a name="csimplemapcsimplemap"></a><a name="csimplemap"></a>CSimpleMap::CSimpleMap

Der Konstruktor.

```
CSimpleMap();
```

### <a name="remarks"></a>Bemerkungen

Initialisiert die Datenmember.

## <a name="csimplemapcsimplemap"></a><a name="dtor"></a>CSimpleMap::'CSimpleMap

Der Destruktor.

```
~CSimpleMap();
```

### <a name="remarks"></a>Bemerkungen

Gibt alle zugewiesenen Ressourcen frei.

## <a name="csimplemapfindkey"></a><a name="findkey"></a>CSimpleMap::FindKey

Sucht einen bestimmten Schlüssel.

```
int FindKey(const TKey& key) const;
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der zu suchende Schlüssel.

### <a name="return-value"></a>Rückgabewert

Gibt den Index des Schlüssels zurück, falls gefunden, andernfalls gibt er -1 zurück.

## <a name="csimplemapfindval"></a><a name="findval"></a>CSimpleMap::FindVal

Sucht einen bestimmten Wert.

```
int FindVal(const TVal& val) const;
```

### <a name="parameters"></a>Parameter

*Val*<br/>
Der zu suchende Wert.

### <a name="return-value"></a>Rückgabewert

Gibt den Index des Werts zurück, wenn er gefunden wird, andernfalls gibt er -1 zurück.

## <a name="csimplemapgetkeyat"></a><a name="getkeyat"></a>CSimpleMap::GetKeyAt

Ruft den Schlüssel am angegebenen Index ab.

```
TKey& GetKeyAt(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der Index des zurückzugebenden Schlüssels.

### <a name="return-value"></a>Rückgabewert

Gibt den Schlüssel *zurück,* auf den nIndex verweist.

### <a name="remarks"></a>Bemerkungen

Der von *nIndex* übergebene Index muss gültig sein, damit der Rückgabewert aussagekräftig ist.

## <a name="csimplemapgetsize"></a><a name="getsize"></a>CSimpleMap::GetSize

Gibt die Anzahl der Einträge im Zuordnungsarray zurück.

```
int GetSize() const;
```

### <a name="return-value"></a>Rückgabewert

Gibt die Anzahl der Einträge (ein Schlüssel und ein Wert ist ein Eintrag) im Zuordnungsarray zurück.

## <a name="csimplemapgetvalueat"></a><a name="getvalueat"></a>CSimpleMap::GetValueAt

Ruft den Wert am spezifischen Index ab.

```
TVal& GetValueAt(int nIndex) const;
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der Index des zurückzugebenden Werts.

### <a name="return-value"></a>Rückgabewert

Gibt den Wert zurück, auf den von *nIndex*verwiesen wird.

### <a name="remarks"></a>Bemerkungen

Der von *nIndex* übergebene Index muss gültig sein, damit der Rückgabewert aussagekräftig ist.

## <a name="csimplemaplookup"></a><a name="lookup"></a>CSimpleMap::Lookup

Gibt den Wert zurück, der dem angegebenen Schlüssel zugeordnet ist.

```
TVal Lookup(const TKey& key) const;
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüssel.

### <a name="return-value"></a>Rückgabewert

Gibt den zugeordneten Wert zurück. Wenn kein übereinstimmender Schlüssel gefunden wird, wird NULL zurückgegeben.

## <a name="csimplemapremove"></a><a name="remove"></a>CSimpleMap::Entfernen

Entfernt einen Schlüssel und einen übereinstimmenden Wert.

```
BOOL Remove(const TKey& key);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüssel.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn der Schlüssel und der übereinstimmende Wert erfolgreich entfernt wurden, andernfalls FALSE.

## <a name="csimplemapremoveall"></a><a name="removeall"></a>CSimpleMap::RemoveAll

Entfernt alle Schlüssel und Werte.

```
void RemoveAll();
```

### <a name="remarks"></a>Bemerkungen

Entfernt alle Schlüssel und Werte aus dem Zuordnungsarrayobjekt.

## <a name="csimplemapremoveat"></a><a name="removeat"></a>CSimpleMap::RemoveAt

Entfernt einen Schlüssel und den zugeordneten Wert am angegebenen Index.

```
BOOL RemoveAt(int nIndex);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der Index des zu entfernenden Schlüssels und des zugehörigen Werts.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE bei Erfolg, FALSE, wenn der angegebene Index ein ungültiger Index ist.

## <a name="csimplemapreverselookup"></a><a name="reverselookup"></a>CSimpleMap::ReverseLookup

Gibt den Schlüssel zurück, der dem angegebenen Wert zugeordnet ist.

```
TKey ReverseLookup(const TVal& val) const;
```

### <a name="parameters"></a>Parameter

*Val*<br/>
Der Wert.

### <a name="return-value"></a>Rückgabewert

Gibt den zugeordneten Schlüssel zurück. Wenn kein übereinstimmender Schlüssel gefunden wird, wird NULL zurückgegeben.

## <a name="csimplemapsetat"></a><a name="setat"></a>CSimpleMap::SetAt

Legt den Wert fest, der dem angegebenen Schlüssel zugeordnet ist.

```
BOOL SetAt(const TKey& key, const TVal& val);
```

### <a name="parameters"></a>Parameter

*key*<br/>
Der Schlüssel.

*Val*<br/>
Der neue Wert, der zugewiesen werden soll.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn der Schlüssel gefunden wurde und der Wert erfolgreich geändert wurde, andernfalls FALSE.

## <a name="csimplemapsetatindex"></a><a name="setatindex"></a>CSimpleMap::SetAtIndex

Legt den Schlüssel und den Wert für einen angegebenen Index fest.

```
BOOL SetAtIndex(
    int nIndex,
    const TKey& key,
    const TVal& val);
```

### <a name="parameters"></a>Parameter

*nIndex*<br/>
Der Index, der auf die Schlüssel- und Wertpaarung verweist, um sich zu ändern.

*key*<br/>
Der neue Schlüssel.

*Val*<br/>
Der neue Wert.

### <a name="return-value"></a>Rückgabewert

Gibt TRUE zurück, wenn erfolgreich, FALSE, wenn der Index ungültig war.

### <a name="remarks"></a>Bemerkungen

Aktualisiert sowohl den Schlüssel als auch den Wert, auf den *nIndex*zeigt.

## <a name="see-also"></a>Siehe auch

[Klassenübersicht](../../atl/atl-class-overview.md)

---
title: CTypedPtrMap-Klasse
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrMap
- AFXTEMPL/CTypedPtrMap
- AFXTEMPL/CTypedPtrMap::GetNextAssoc
- AFXTEMPL/CTypedPtrMap::Lookup
- AFXTEMPL/CTypedPtrMap::RemoveKey
- AFXTEMPL/CTypedPtrMap::SetAt
helpviewer_keywords:
- CTypedPtrMap [MFC], GetNextAssoc
- CTypedPtrMap [MFC], Lookup
- CTypedPtrMap [MFC], RemoveKey
- CTypedPtrMap [MFC], SetAt
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
ms.openlocfilehash: 410f0101fd0f8cda271fe0f2353b06b9e8d773b8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754363"
---
# <a name="ctypedptrmap-class"></a>CTypedPtrMap-Klasse

Stellt einen typsicheren Wrapper für Objekte der Zeigerzuordnungsklassen `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`und `CMapStringToPtr`bereit.

## <a name="syntax"></a>Syntax

```
template<class BASE_CLASS, class KEY, class VALUE>
class CTypedPtrMap : public BASE_CLASS
```

#### <a name="parameters"></a>Parameter

*BASE_CLASS*<br/>
Basisklasse der typisierten Zeigerzuordnungsklasse; muss eine Zeigerzuordnungsklasse `CMapPtrToPtr` `CMapPtrToWord`( `CMapWordToPtr`, `CMapStringToPtr`, , oder ) sein.

*Schlüssel*<br/>
Klasse des Objekts, das als Schlüssel für die Karte verwendet wird.

*Wert*<br/>
Klasse des in der Karte gespeicherten Objekts.

## <a name="members"></a>Member

### <a name="public-methods"></a>Öffentliche Methoden

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|Ruft das nächste Element zum Iterieren ab.|
|[CTypedPtrMap::Suche](#lookup)|Gibt `KEY` eine basierend `VALUE`auf einer zurück.|
|[CTypedPtrMap::RemoveKey](#removekey)|Entfernt ein Element, das durch einen Schlüssel angegeben wird.|
|[CTypedPtrMap::SetAt](#setat)|Fügt ein Element in die Karte ein. ersetzt ein vorhandenes Element, wenn ein übereinstimmender Schlüssel gefunden wird.|

### <a name="public-operators"></a>Öffentliche Operatoren

|Name|BESCHREIBUNG|
|----------|-----------------|
|[CTypedPtrMap::Operator \[\]](#operator_at)|Fügt ein Element in die Karte ein.|

## <a name="remarks"></a>Bemerkungen

Wenn Sie `CTypedPtrMap`verwenden, hilft die C++-Typüberprüfungsfunktion, Fehler zu beseitigen, die durch nicht übereinstimmende Zeigertypen verursacht werden.

Da `CTypedPtrMap` alle Funktionen inline sind, wirkt sich die Verwendung dieser Vorlage nicht wesentlich auf die Größe oder Geschwindigkeit des Codes aus.

Weitere Informationen zur `CTypedPtrMap`Verwendung finden Sie in den Artikeln [Sammlungen](../../mfc/collections.md) und [Vorlagenbasierte Klassen](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Vererbungshierarchie

`BASE_CLASS`

`CTypedPtrMap`

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:** afxtempl.h

## <a name="ctypedptrmapgetnextassoc"></a><a name="getnextassoc"></a>CTypedPtrMap::GetNextAssoc

Ruft das Kartenelement `rNextPosition`unter `rNextPosition` ab und aktualisiert dann, um auf das nächste Element in der Karte zu verweisen.

```cpp
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Parameter

*Rposition*<br/>
Gibt einen Verweis auf einen POSITION-Wert an, der von einem vorherigen `GetNextAssoc` oder `BASE_CLASS` **::GetStartPosition-Aufruf** zurückgegeben wird.

*Schlüssel*<br/>
Vorlagenparameter, der den Typ der Kartenschlüssel angibt.

*rKey*<br/>
Gibt den zurückgegebenen Schlüssel des abgerufenen Elements an.

*Wert*<br/>
Vorlagenparameter, der den Typ der Kartenwerte angibt.

*Rvalue*<br/>
Gibt den zurückgegebenen Wert des abgerufenen Elements an.

### <a name="remarks"></a>Bemerkungen

Diese Funktion ist besonders nützlich, um alle Elemente in der Karte zu durchlaufen. Beachten Sie, dass die Positionssequenz nicht unbedingt mit der Schlüsselwertsequenz identisch ist.

Wenn das abgerufene Element das letzte element in `rNextPosition` der Karte ist, wird der neue Wert von auf NULL gesetzt.

Diese Inlinefunktion `BASE_CLASS`ruft **::GetNextAssoc**auf.

## <a name="ctypedptrmaplookup"></a><a name="lookup"></a>CTypedPtrMap::Suche

`Lookup`verwendet einen Hashalgorithmus, um das Kartenelement schnell mit einem Schlüssel zu finden, der genau übereinstimmt.

```
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Parameter

*BASE_CLASS*<br/>
Vorlagenparameter, der die Basisklasse der Klasse dieser Zuordnung angibt.

*key*<br/>
Der Schlüssel des zu erkundübenden Elements.

*Wert*<br/>
Vorlagenparameter, der den Typ der in dieser Zuordnung gespeicherten Werte angibt.

*Rvalue*<br/>
Gibt den zurückgegebenen Wert des abgerufenen Elements an.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Element gefunden wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Diese Inlinefunktion `BASE_CLASS`ruft **::Lookup**auf.

## <a name="ctypedptrmapoperator--"></a><a name="operator_at"></a>CTypedPtrMap::Operator [ ]

Dieser Operator kann nur auf der linken Seite einer Zuweisungsanweisung (ein l-Wert) verwendet werden.

```
VALUE& operator[ ](base_class ::base_arg_key key);
```

### <a name="parameters"></a>Parameter

*Wert*<br/>
Vorlagenparameter, der den Typ der in dieser Zuordnung gespeicherten Werte angibt.

*BASE_CLASS*<br/>
Vorlagenparameter, der die Basisklasse der Klasse dieser Zuordnung angibt.

*key*<br/>
Der Schlüssel des Elements, das in der Karte gesucht oder erstellt werden soll.

### <a name="remarks"></a>Bemerkungen

Wenn kein Kartenelement mit dem angegebenen Schlüssel vorhanden ist, wird ein neues Element erstellt. Es gibt keine "rechte Seite" (r-Wert) äquivalent zu diesem Operator, da es eine Möglichkeit, dass ein Schlüssel nicht in der Karte gefunden werden. Verwenden `Lookup` Sie die Memberfunktion für den Elementabruf.

## <a name="ctypedptrmapremovekey"></a><a name="removekey"></a>CTypedPtrMap::RemoveKey

Diese Memberfunktion `BASE_CLASS`ruft **::RemoveKey**auf.

```
BOOL RemoveKey(KEY key);
```

### <a name="parameters"></a>Parameter

*Schlüssel*<br/>
Vorlagenparameter, der den Typ der Kartenschlüssel angibt.

*key*<br/>
Schlüssel für das zu entfernende Element.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn der Eintrag gefunden und erfolgreich entfernt wurde; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Ausführlichere Anmerkungen finden Sie unter [CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey).

## <a name="ctypedptrmapsetat"></a><a name="setat"></a>CTypedPtrMap::SetAt

Diese Memberfunktion `BASE_CLASS`ruft **::SetAt**auf.

```cpp
void SetAt(KEY key, VALUE newValue);
```

### <a name="parameters"></a>Parameter

*Schlüssel*<br/>
Vorlagenparameter, der den Typ der Kartenschlüssel angibt.

*key*<br/>
Gibt den Schlüsselwert des newValue an.

*newValue*<br/>
Gibt den Objektzeiger an, der der Wert des neuen Elements ist.

### <a name="remarks"></a>Bemerkungen

Ausführlichere Anmerkungen finden Sie unter [CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat).

## <a name="see-also"></a>Weitere Informationen

[MFC-Beispiel COLLECT](../../overview/visual-cpp-samples.md)<br/>
[Hierarchiediagramm](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr-Klasse](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord-Klasse](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapWordToPtr-Klasse](../../mfc/reference/cmapwordtoptr-class.md)<br/>
[CMapStringToPtr-Klasse](../../mfc/reference/cmapstringtoptr-class.md)

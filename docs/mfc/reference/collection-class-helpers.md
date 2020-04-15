---
title: Hilfsfunktionen für die Auflistungsklasse
ms.date: 11/04/2016
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
ms.openlocfilehash: 05fe49a4d8e6de92c584d40f3871f3efb906c7c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374815"
---
# <a name="collection-class-helpers"></a>Hilfsfunktionen für die Auflistungsklasse

Die Auflistungsklassen `CMap`, `CList`und `CArray` verwenden vorlagenbasierte globale Hilfsfunktionen für Zwecke wie vergleichen, kopieren und serialisieren Elemente. Im Rahmen der Implementierung von `CMap` `CList`Klassen, `CArray`die auf , und basieren, müssen Sie diese Funktionen bei Bedarf mit Versionen überschreiben, die auf den Inland, die Liste oder das Array zugeschnitten sind. Weitere Informationen zu übergeordneten Hilfsfunktionen wie `SerializeElements`, finden Sie im Artikel [Sammlungen: Erstellen einer typsicheren Sammlung](../../mfc/how-to-make-a-type-safe-collection.md). Beachten `ConstructElements` Sie `DestructElements` dies und sind veraltet.

Die Microsoft Foundation-Klassenbibliothek bietet die folgenden globalen Funktionen in afxtempl.h, mit denen Sie Ihre Sammlungsklassen anpassen können:

### <a name="collection-class-helpers"></a>Hilfsfunktionen für die Auflistungsklasse

|||
|-|-|
|[CompareElements](#compareelements)|Gibt an, ob die Elemente identisch sind.|
|[CopyElements](#copyelements)|Kopiert Elemente von einem Array in ein anderes.|
|[DumpElements](#dumpelements)|Bietet eine streamorientierte Diagnoseausgabe.|
|[HashKey](#hashkey)|Berechnet einen Hashschlüssel.|
|[SerializeElements](#serializeelements)|Speichert oder ruft Elemente in oder aus einem Archiv ab.|

## <a name="compareelements"></a><a name="compareelements"></a>CompareElements

Wird direkt von [CList::Find] (clist-class.md-not_found.md-clist__find und indirekt von [cmap__lookup](cmap-class.md#lookup) und [cmap__operator &#91;&#93;](cmap-class.md#operator_at)aufgerufen.

```
template<class TYPE, class ARG_TYPE>
BOOL AFXAPI
CompareElements(
    const TYPE* pElement1,
    const ARG_TYPE* pElement2);
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Der Typ des ersten zu vergleichenden Elements.

*pElement1*<br/>
Zeigen Sie auf das erste zu vergleichende Element.

*ARG_TYPE*<br/>
Der Typ des zweiten zu vergleichenden Elements.

*pElement2*<br/>
Zeiger auf das zweite zu vergleichende Element.

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null, wenn das Objekt, auf das *pElement1* zeigt, gleich dem Objekt ist, auf das *pElement2*zeigt; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die `CMap` Aufrufe `CMap` verwenden die Vorlagenparameter *KEY* und *ARG_KEY*.

Die Standardimplementierung gibt das Ergebnis des Vergleichs von * \*pElement1* und * \*pElement2*zurück. Überschreiben Sie diese Funktion, sodass sie die Elemente in einer Weise vergleicht, die für Ihre Anwendung geeignet ist.

Die C++-Sprache definiert den `==`Vergleichsoperator ( ) für einfache Typen (**char**, **int**, **float**usw.), aber keinen Vergleichsoperator für Klassen und Strukturen. Wenn Sie eine `CompareElements` der Auflistungsklassen, die sie verwenden, verwenden oder instanziieren möchten, `CompareElements` müssen Sie entweder den Vergleichsoperator definieren oder mit einer Version überladen, die entsprechende Werte zurückgibt.

### <a name="requirements"></a>Anforderungen

   **Header:** afxtempl.h

## <a name="copyelements"></a><a name="copyelements"></a>CopyElements

Diese Funktion wird direkt von [CArray::Append](carray-class.md#append) und [CArray::Copy](carray-class.md#copy)aufgerufen.

```
template<class TYPE>
void AFXAPI CopyElements(
    TYPE* pDest,
    const TYPE* pSrc,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der zu kopierenden Elemente angibt.

*pDest*<br/>
Zeigen Sie mit dem Zeiger auf das Ziel, an das die Elemente kopiert werden.

*pSrc*<br/>
Zeiger auf die Quelle der zu kopierenden Elemente.

*nCount*<br/>
Anzahl der zu kopierenden Elemente.

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung verwendet den **=** einfachen Zuweisungsoperator ( ), um den Kopiervorgang auszuführen. Wenn der kopierte Typ keinen überladenen Operator= hat, führt die Standardimplementierung eine bitweise Kopie aus.

Informationen zum Implementieren dieser und anderer Hilfsfunktionen finden Sie im Artikel [Sammlungen: Erstellen einer typsicheren Sammlung](../how-to-make-a-type-safe-collection.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxtempl.h

## <a name="dumpelements"></a><a name="dumpelements"></a>DumpElements

Stellt eine streamorientierte Diagnoseausgabe in Textform für die Elemente Ihrer Auflistung bereit, wenn sie überschrieben wird.

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parameter

*Dc*<br/>
Dump-Kontext für Dumpingelemente.

*TYP*<br/>
Vorlagenparameter, der den Typ der Elemente angibt.

*pElements*<br/>
Zeigen Sie auf die elemente, die gedumpt werden sollen.

*nCount*<br/>
Anzahl der zu dumpenden Elemente.

### <a name="remarks"></a>Bemerkungen

Die `CArray::Dump` `CList::Dump`, `CMap::Dump` und Funktionen rufen dies auf, wenn die Tiefe des Dumps größer als 0 ist.

Bei der Standardimplementierung wird keine Aktion ausgeführt. Wenn die Elemente Ihrer Auflistung `CObject`von abgeleitet sind, durchläuft Ihre Außerkraftsetzung `Dump` in der Regel die Elemente der Auflistung und ruft jedes Element nacheinander auf.

### <a name="requirements"></a>Anforderungen

  **Header** afxtempl.h

## <a name="hashkey"></a><a name="hashkey"></a>HashKey

Berechnet einen Hashwert für den angegebenen Schlüssel.

```
template<class ARG_KEY>
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key);
```

### <a name="parameters"></a>Parameter

*ARG_KEY*<br/>
Vorlagenparameter, der den Datentyp angibt, der für den Zugriff auf Kartenschlüssel verwendet wird.

*key*<br/>
Der Schlüssel, dessen Hashwert berechnet werden soll.

### <a name="return-value"></a>Rückgabewert

Der Hashwert des Schlüssels.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird direkt von [CMap::RemoveKey](cmap-class.md#removekey) und indirekt von [CMap::Lookup](cmap-class.md#lookup) und [CMap::Operator &#91;&#93;](cmap-class.md#operator_at)aufgerufen.

Die Standardimplementierung erstellt einen Hashwert, indem der *Schlüssel* um vier Positionen nach rechts verschoben wird. Überschreiben Sie diese Funktion, sodass hashwerte zurückgegeben werden, die für Ihre Anwendung geeignet sind.

### <a name="example"></a>Beispiel

```cpp
template <> UINT AFXAPI HashKey(unsigned __int64 key)
{
   // Generate the hash value by XORing the lower 32 bits of the number
   // with the upper 32 bits
   return(UINT(key) ^ UINT(key >> 32));
}
```

### <a name="requirements"></a>Anforderungen

  **Header** afxtempl.h

## <a name="serializeelements"></a><a name="serializeelements"></a>SerializeElements

[CArray](carray-class.md), [CList](clist-class.md)und [CMap](cmap-class.md) rufen diese Funktion auf, um Elemente zu serialisieren.

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>Parameter

*TYP*<br/>
Vorlagenparameter, der den Typ der Elemente angibt.

*ar*<br/>
Ein Archivobjekt, das von oder nach archiviert werden soll.

*pElements*<br/>
Zeigen Sie auf die zu archivierenden Elemente.

*nCount*<br/>
Anzahl der zu archivierenden Elemente

### <a name="remarks"></a>Bemerkungen

Die Standardimplementierung liest oder schreibt bitweise.

Informationen zum Implementieren dieser und anderer Hilfsfunktionen finden Sie im Artikel [Sammlungen: Erstellen einer typsicheren Sammlung](../how-to-make-a-type-safe-collection.md).

### <a name="example"></a>Beispiel

Siehe das Beispiel im Artikel [Sammlungen: Erstellen einer typsicheren Auflistung](../how-to-make-a-type-safe-collection.md).

### <a name="requirements"></a>Anforderungen

  **Header** afxtempl.h

## <a name="see-also"></a>Siehe auch

[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)<br/>
[CMap-Klasse](cmap-class.md)<br/>
[CList-Klasse](clist-class.md)<br/>
[CArray-Klasse](carray-class.md)

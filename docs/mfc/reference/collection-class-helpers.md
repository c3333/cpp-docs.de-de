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
ms.openlocfilehash: 04b142cde12a9795f217559f875eef7fcec3b0f2
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88841427"
---
# <a name="collection-class-helpers"></a>Hilfsfunktionen für die Auflistungsklasse

Die Auflistungs Klassen `CMap` , `CList` und `CArray` verwenden auf Vorlagen basierende globale Hilfsfunktionen, wie z. b. das vergleichen, kopieren und Serialisieren von Elementen. Als Teil der Implementierung von Klassen, die auf `CMap` , `CList` und basieren `CArray` , müssen Sie diese Funktionen bei Bedarf mit Versionen überschreiben, die auf den Datentyp zugeschnitten sind, der in der Zuordnung, Liste oder im Array gespeichert ist. Weitere Informationen zum Überschreiben von Hilfsfunktionen `SerializeElements` , wie z. b., finden Sie im Artikel [Sammlungen: Erstellen einer typsicheren](../../mfc/how-to-make-a-type-safe-collection.md)Auflistung. Beachten Sie, dass `ConstructElements` und als `DestructElements` veraltet markiert wurden.

Die Microsoft Foundation Class-Bibliothek bietet die folgenden globalen Funktionen in afxtempl. h, um Ihnen beim Anpassen der Sammlungs Klassen zu helfen:

### <a name="collection-class-helpers"></a>Hilfsfunktionen für die Auflistungsklasse

|Name|Beschreibung|
|-|-|
|[CompareElements](#compareelements)|Gibt an, ob Elemente identisch sind.|
|[CopyElements](#copyelements)|Kopiert Elemente aus einem Array in ein anderes.|
|[DumpElements](#dumpelements)|Stellt die Streamorientierte Diagnoseausgabe bereit.|
|[Hashkey](#hashkey)|Berechnet einen hashkey.|
|[SerializeElements](#serializeelements)|Speichert oder ruft Elemente in ein oder aus einem Archiv ab.|

## <a name="compareelements"></a><a name="compareelements"></a> Compareelements

Wird direkt durch [CLIST:: Find] (CLIST-Class. MD # NOT_FOUND. MD # clist__find und indirekt durch [cmap__lookup](cmap-class.md#lookup) und [cmap__operator &#91;&#93;](cmap-class.md#operator_at)aufgerufen.

```
template<class TYPE, class ARG_TYPE>
BOOL AFXAPI
CompareElements(
    const TYPE* pElement1,
    const ARG_TYPE* pElement2);
```

### <a name="parameters"></a>Parameter

*TYPE*<br/>
Der Typ des ersten zu vergleichenden Elements.

*pElement1*<br/>
Zeiger zum ersten zu vergleichenden Element.

*ARG_TYPE*<br/>
Der Typ des zweiten Elements, das verglichen werden soll.

*pElement2*<br/>
Zeiger auf das zweite zu vergleichende Element.

### <a name="return-value"></a>Rückgabewert

Ungleich 0 (null), wenn das Objekt, auf das *pElement1* verweist, gleich dem Objekt ist, auf das von *pElement2*verwiesen wird; andernfalls 0.

### <a name="remarks"></a>Bemerkungen

Die `CMap` Aufrufe verwenden die `CMap` Vorlagen Parameter *Key* und *ARG_KEY*.

Die Standard Implementierung gibt das Ergebnis des Vergleichs von * \* pElement1* und * \* pElement2*zurück. Überschreiben Sie diese Funktion, sodass Sie die Elemente auf eine Weise vergleicht, die für Ihre Anwendung geeignet ist.

Die Programmiersprache C++ definiert den Vergleichs Operator ( `==` ) für einfache Typen ( **`char`** , **`int`** , usw.), **`float`** definiert jedoch keinen Vergleichs Operator für Klassen und Strukturen. Wenn Sie oder verwenden möchten, `CompareElements` um eine der Auflistungs Klassen zu instanziieren, die Sie verwenden, müssen Sie entweder den Vergleichs Operator oder die `CompareElements` Überladung mit einer Version definieren, die die entsprechenden Werte zurückgibt.

### <a name="requirements"></a>Requirements (Anforderungen)

   **Header:** afxtempl.h

## <a name="copyelements"></a><a name="copyelements"></a> Copyelements

Diese Funktion wird direkt von " [CArray:: Append](carray-class.md#append) " und " [CArray:: Copy](carray-class.md#copy)" aufgerufen.

```
template<class TYPE>
void AFXAPI CopyElements(
    TYPE* pDest,
    const TYPE* pSrc,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parameter

*TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der zu kopierenden Elemente angibt.

*pDest*<br/>
Zeiger auf das Ziel, in das die Elemente kopiert werden.

*pSrc*<br/>
Ein Zeiger auf die Quelle der zu kopierenden Elemente.

*nCount*<br/>
Anzahl der zu kopierenden Elemente.

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung verwendet den einfachen Zuweisungs Operator ( **=** ), um den Kopiervorgang auszuführen. Wenn der kopierte Typ nicht über einen überladenen Operator = verfügt, führt die Standard Implementierung eine bitweise Kopie aus.

Weitere Informationen zur Implementierung dieser und anderer Hilfsfunktionen finden Sie im Artikel [Auflistungen: Erstellen einer typsicheren](../how-to-make-a-type-safe-collection.md)Auflistung.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxtempl. h

## <a name="dumpelements"></a><a name="dumpelements"></a> Dumpelements

Stellt beim Überschreiben die Datenstrom orientierte Diagnoseausgabe in Textform für die Elemente der Auflistung bereit.

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parameter

*DC*<br/>
Der Dumpkontext zum Sichern von Elementen.

*TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der Elemente angibt.

*pelements*<br/>
Zeiger auf die zu entsorgenden Elemente.

*nCount*<br/>
Anzahl der zu entsorgenden Elemente.

### <a name="remarks"></a>Bemerkungen

Die `CArray::Dump` `CList::Dump` Funktionen, und `CMap::Dump` bezeichnen diese, wenn die Tiefe des dumpspeichers größer als 0 ist.

Bei der Standardimplementierung wird keine Aktion ausgeführt. Wenn die Elemente der Auflistung von abgeleitet sind, durchläuft die-Überschreibung `CObject` in der Regel die Elemente der Auflistung, `Dump` wobei für jedes Element nacheinander aufgerufen wird.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxtempl. h

## <a name="hashkey"></a><a name="hashkey"></a> Hashkey

Berechnet einen Hashwert für den angegebenen Schlüssel.

```
template<class ARG_KEY>
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key);
```

### <a name="parameters"></a>Parameter

*ARG_KEY*<br/>
Vorlagen Parameter, der den Datentyp angibt, der für den Zugriff auf Kartenschlüssel verwendet wird

*key*<br/>
Der Schlüssel, dessen Hashwert berechnet werden soll.

### <a name="return-value"></a>Rückgabewert

Der Hashwert des Schlüssels.

### <a name="remarks"></a>Bemerkungen

Diese Funktion wird direkt durch [cmap:: removekey](cmap-class.md#removekey) und indirekt durch [cmap:: Lookup](cmap-class.md#lookup) -und [cmap:: Operator- &#91;&#93;](cmap-class.md#operator_at)aufgerufen.

Die Standard Implementierung erstellt einen Hashwert, indem der *Schlüssel* nach rechts um vier Positionen verschoben wird. Überschreiben Sie diese Funktion, sodass Sie für Ihre Anwendung geeignete Hashwerte zurückgibt.

### <a name="example"></a>Beispiel

```cpp
template <> UINT AFXAPI HashKey(unsigned __int64 key)
{
   // Generate the hash value by XORing the lower 32 bits of the number
   // with the upper 32 bits
   return(UINT(key) ^ UINT(key >> 32));
}
```

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxtempl. h

## <a name="serializeelements"></a><a name="serializeelements"></a> SerializeElements

[CArray](carray-class.md), [CLIST](clist-class.md)und [cmap](cmap-class.md) ruft diese Funktion auf, um Elemente zu serialisieren.

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>Parameter

*TYPE*<br/>
Ein Vorlagen Parameter, der den Typ der Elemente angibt.

*Tempel*<br/>
Ein Archiv Objekt, das in oder aus archiviert werden soll.

*pelements*<br/>
Zeiger auf die Elemente, die archiviert werden.

*nCount*<br/>
Anzahl der archivierten Elemente

### <a name="remarks"></a>Bemerkungen

Die Standard Implementierung führt einen bitweisen Lese-oder Schreibvorgang aus.

Weitere Informationen zur Implementierung dieser und anderer Hilfsfunktionen finden Sie im Artikel [Auflistungen: Erstellen einer typsicheren](../how-to-make-a-type-safe-collection.md)Auflistung.

### <a name="example"></a>Beispiel

Weitere Informationen finden Sie im Beispiel unter [Erstellen einer typsicheren](../how-to-make-a-type-safe-collection.md)Auflistung.

### <a name="requirements"></a>Requirements (Anforderungen)

  **Header** afxtempl. h

## <a name="see-also"></a>Weitere Informationen

[MFC-Makros, globale Funktionen und globale Variablen](mfc-macros-and-globals.md)<br/>
[Cmap-Klasse](cmap-class.md)<br/>
[CLIST-Klasse](clist-class.md)<br/>
[CArray-Klasse](carray-class.md)

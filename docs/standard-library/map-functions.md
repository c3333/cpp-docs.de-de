---
title: '&lt;map&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: 8cc4a82e08963902f9ba5c21ace759c47bdd0014
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228218"
---
# <a name="ltmapgt-functions"></a>&lt;map&gt;-Funktionen

## <a name="swap-map"></a><a name="swap_multimap"></a>austauschen (Map)

Tauscht die Elemente zweier Zuordnungen aus.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    map<Key, Traits, Compare, Alloctor>& left,
    map<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Die Zuordnung, in der die auszutauschenden Elemente bereitgestellt werden, oder die Zuordnung, deren Elemente mit denen der Karte *Links*ausgetauscht werden sollen.

*linken*\
Die Zuordnung, deren Elemente mit denen der Karten *rechten*ausgetauscht werden sollen.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion ist ein Algorithmus, der auf die Containerklassen Zuordnung spezialisiert ist, um die Member-Funktion auszuführen `left` .[ Swap](../standard-library/map-class.md#swap)( `right` ). Dies ist eine Instanz der partiellen Reihenfolge von Funktionsvorlagen durch den Compiler. Wenn Vorlagenfunktionen so überladen werden, dass die Übereinstimmung der Vorlage mit dem Funktionsaufruf nicht eindeutig ist, wählt der Compiler die spezialisierteste Version der Vorlagenfunktion aus. Die allgemeine Version der Vorlagen Funktion **`template`** \< **class T**> **void Swap**( **t&**, **t&**) in der Algorithmusklasse funktioniert durch Zuweisung und ist ein langsamer Vorgang. Die spezialisierte Version in jedem Container ist viel schneller, da sie mit der internen Darstellung der Containerklasse genutzt werden kann.

### <a name="example"></a>Beispiel

Im Codebeispiel für die Memberfunktion [map::swap](../standard-library/map-class.md#swap) finden Sie ein Beispiel, das die Vorlagenversion `swap` verwendet.

## <a name="swap-multimap"></a><a name="swap"></a>Swap (Multimap)

Tauscht die Elemente zweier Mehrfachzuordnungen aus.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Die mehrfach Zuordnung, die die auszutauschenden Elemente bereitstellt, oder die mehrfach Zuordnung, deren Elemente mit denen der mehrfach Zuordnung ausgetauscht werden *sollen.*

*linken*\
Die mehrfach Zuordnung, deren Elemente mit denen der mehrfach Zuordnung ausgetauscht werden *sollen.*

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion ist ein Algorithmus, der sich auf die Containerklassen Zuordnung spezialisiert hat, die für die Ausführung der Member-Funktion in der Container Klasse Multimap ausgeführt werden soll `left` .[ Swap](../standard-library/multimap-class.md#swap) ( `right` ). Dies ist eine Instanz der partiellen Reihenfolge von Funktionsvorlagen durch den Compiler. Wenn Vorlagenfunktionen so überladen werden, dass die Übereinstimmung der Vorlage mit dem Funktionsaufruf nicht eindeutig ist, wählt der Compiler die spezialisierteste Version der Vorlagenfunktion aus. Die allgemeine Version der Vorlagen Funktion **`template`** \< **class T**> **void Swap**( **t&**, **t&**) in der Algorithmusklasse funktioniert durch Zuweisung und ist ein langsamer Vorgang. Die spezialisierte Version in jedem Container ist viel schneller, da sie mit der internen Darstellung der Containerklasse genutzt werden kann.

### <a name="example"></a>Beispiel

Im Codebeispiel für die Memberfunktion [multimap::swap](../standard-library/multimap-class.md#swap) finden Sie ein Beispiel, das die Vorlagenversion `swap` verwendet.

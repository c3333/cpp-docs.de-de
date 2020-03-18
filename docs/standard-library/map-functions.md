---
title: '&lt;map&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- map/std::swap (map)
- map/std::swap (multimap)
ms.assetid: 7cb3d1a5-7add-4726-a73f-61927eafd466
ms.openlocfilehash: e7876b37bfc006eaecf2f1e36273c5ae8689dad4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425526"
---
# <a name="ltmapgt-functions"></a>&lt;map&gt;-Funktionen

## <a name="swap_multimap"></a>austauschen (Map)

Tauscht die Elemente zweier Zuordnungen aus.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    map<Key, Traits, Compare, Alloctor>& left,
    map<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parameter

*Rechte*\
Die Zuordnung, in der die auszutauschenden Elemente bereitgestellt werden, oder die Zuordnung, deren Elemente mit denen der Karte *Links*ausgetauscht werden sollen.

*Linker*\
Die Zuordnung, deren Elemente mit denen der Karten *rechten*ausgetauscht werden sollen.

### <a name="remarks"></a>Hinweise

Die Vorlagen Funktion ist ein Algorithmus, der auf die Containerklassen Zuordnung spezialisiert ist, um die Element Funktion `left`auszuführen. [Swap](../standard-library/map-class.md#swap)(`right`). Dies ist eine Instanz der partiellen Reihenfolge von Funktionsvorlagen durch den Compiler. Wenn Vorlagenfunktionen so überladen werden, dass die Übereinstimmung der Vorlage mit dem Funktionsaufruf nicht eindeutig ist, wählt der Compiler die meist spezialisierte Version der Vorlagenfunktion. Die allgemeine Version der Vorlagen Funktion, **Template** \< **Class t**> **void Swap**( **t &** , **t &** ), in der Algorithmusklasse funktioniert durch Zuweisung und ist ein langsamer Vorgang. Die spezialisierte Version in jedem Container ist viel schneller, da sie mit der internen Darstellung der Containerklasse verwendet werden kann.

### <a name="example"></a>Beispiel

Im Codebeispiel für die Memberfunktion [map::swap](../standard-library/map-class.md#swap) finden Sie ein Beispiel, das die Vorlagenversion `swap` verwendet.

## <a name="swap"></a>Swap (Multimap)

Tauscht die Elemente zweier multimap-Objekte aus.

```cpp
template <class key, class T, class _Pr, class _Alloc>
void swap(
    multimap<Key, Traits, Compare, Alloctor>& left,
    multimap<Key, Traits, Compare, Alloctor>& right);
```

### <a name="parameters"></a>Parameter

*Rechte*\
Die mehrfach Zuordnung, die die auszutauschenden Elemente bereitstellt, oder die mehrfach Zuordnung, deren Elemente mit denen der mehrfach Zuordnung ausgetauscht werden *sollen.*

*Linker*\
Die mehrfach Zuordnung, deren Elemente mit denen der mehrfach Zuordnung ausgetauscht werden *sollen.*

### <a name="remarks"></a>Hinweise

Die Vorlagen Funktion ist ein Algorithmus, der auf die Containerklassen Zuordnung spezialisiert ist, die auf der Container Klasse Multimap ausgeführt werden soll, um die Member-Funktion `left`auszuführen. [Swap](../standard-library/multimap-class.md#swap) (`right`). Dies ist eine Instanz der partiellen Reihenfolge von Funktionsvorlagen durch den Compiler. Wenn Vorlagenfunktionen so überladen werden, dass die Übereinstimmung der Vorlage mit dem Funktionsaufruf nicht eindeutig ist, wählt der Compiler die meist spezialisierte Version der Vorlagenfunktion. Die allgemeine Version der Vorlagen Funktion, **Template** \< **Class t**> **void Swap**( **t &** , **t &** ), in der Algorithmusklasse funktioniert durch Zuweisung und ist ein langsamer Vorgang. Die spezialisierte Version in jedem Container ist viel schneller, da sie mit der internen Darstellung der Containerklasse verwendet werden kann.

### <a name="example"></a>Beispiel

Im Codebeispiel für die Memberfunktion [multimap::swap](../standard-library/multimap-class.md#swap) finden Sie ein Beispiel, das die Vorlagenversion `swap` verwendet.

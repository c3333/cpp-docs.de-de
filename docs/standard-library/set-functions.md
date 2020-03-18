---
title: '&lt;set&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- set/std::swap (map)
- set/std::swap (multiset)
ms.assetid: d1277d14-8502-46c0-b820-bcda820f9406
ms.openlocfilehash: a3a63fb86caa3485b1ee14538c3eb1f1ff72923e
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79425166"
---
# <a name="ltsetgt-functions"></a>&lt;set&gt;-Funktionen

## <a name="swap"></a>austauschen (Map)

Tauscht die Elemente zweier Sätze aus.

```cpp
template <class Key, class Traits, class Allocator>
void swap(set<Key, Traits, Allocator>& left, set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Rechte*\
Die Gruppe, die die auszutauschenden Elemente bereitstellt, oder die Menge, deren Elemente mit denen des *linken*Satzes ausgetauscht werden sollen.

*Linker*\
Die Menge, deren Elemente mit denen des festgelegten *Rechts*ausgetauscht werden sollen.

### <a name="remarks"></a>Hinweise

Die Vorlagen Funktion ist ein Algorithmus, der auf die Container Klasse spezialisiert ist, die zum Ausführen der Member-Funktion `left.`[Swap](../standard-library/set-class.md#swap)(`right`) festgelegt ist. Dies ist eine Instanz der partiellen Reihenfolge von Funktionsvorlagen durch den Compiler. Wenn Vorlagenfunktionen so überladen werden, dass die Übereinstimmung der Vorlage mit dem Funktionsaufruf nicht eindeutig ist, wählt der Compiler die meist spezialisierte Version der Vorlagenfunktion. Die allgemeine Version der Vorlagenfunktion

`template` \< **classt**> **void Swap**( **t &** , **t &** )

in der Algorithmusklasse funktioniert mittels Zuweisung und ist ein langsamer Vorgang. Die spezialisierte Version in jedem Container ist viel schneller, da sie mit der internen Darstellung der Containerklasse verwendet werden kann.

### <a name="example"></a>Beispiel

Im Codebeispiel für die Memberklasse [set::swap](../standard-library/set-class.md#swap) finden Sie ein Beispiel für die Verwendung der Vorlagenversion `swap`.

## <a name="swap_multiset"></a>austauschen (Multiset)

Tauscht die Elemente zweier Multisets aus.

```cpp
template <class Key, class Traits, class Allocator>
void swap(multiset<Key, Traits, Allocator>& left, multiset<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Rechte*\
Die Multimenge, die die auszutauschenden Elemente bereitstellt, oder die Multimenge, deren Elemente mit denen des *linken*Multisets ausgetauscht werden sollen.

*Linker*\
Die Multimenge, deren Elemente mit denen des Multiset- *Rechts*ausgetauscht werden sollen.

### <a name="remarks"></a>Hinweise

Die Vorlagen Funktion ist ein Algorithmus, der auf die Container Klasse Multiset spezialisiert ist, um die Member-Funktion `left.`[Swap](../standard-library/multiset-class.md#swap)(`right`) auszuführen. Dies ist eine Instanz der partiellen Reihenfolge von Funktionsvorlagen durch den Compiler. Wenn Vorlagenfunktionen so überladen werden, dass die Übereinstimmung der Vorlage mit dem Funktionsaufruf nicht eindeutig ist, wählt der Compiler die meist spezialisierte Version der Vorlagenfunktion. Die allgemeine Version der Vorlagenfunktion

`template` \< **classt**> **void Swap**( **t &** , **t &** )

in der Algorithmusklasse funktioniert mittels Zuweisung und ist ein langsamer Vorgang. Die spezialisierte Version in jedem Container ist viel schneller, da sie mit der internen Darstellung der Containerklasse verwendet werden kann.

### <a name="example"></a>Beispiel

Im Codebeispiel für die Memberklasse [multiset::swap](../standard-library/multiset-class.md#swap) finden Sie ein Beispiel für die Verwendung der Vorlagenversion `swap`.

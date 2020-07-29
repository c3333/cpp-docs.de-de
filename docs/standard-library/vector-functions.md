---
title: '&lt;vector&gt;-Funktionen'
ms.date: 11/04/2016
f1_keywords:
- vector/std::swap
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
helpviewer_keywords:
- std::swap [vector]
ms.openlocfilehash: bf28e44b4f603b1e4d6a87f0c28b42d6cc159980
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224551"
---
# <a name="ltvectorgt-functions"></a>&lt;vector&gt;-Funktionen

## <a name="swap"></a><a name="swap"></a>Wechsel

Tauscht die Elemente zweier Vektoren aus.

```cpp
template <class Type, class Allocator>
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```

### <a name="parameters"></a>Parameter

*Richting*\
Der Vektor, der die auszutauschenden Elemente bereitstellt, oder der Vektor, dessen Elemente mit denen des Vektors ausgetauscht werden *sollen.*

*linken*\
Der Vektor, dessen Elemente mit denen des Vektor *Rechts*ausgetauscht werden sollen.

### <a name="remarks"></a>Bemerkungen

Die Vorlagen Funktion ist ein Algorithmus, der auf den Containerklassen Vektor spezialisiert ist, um die Member-Funktion auszuführen `left` . [Vector:: Swap](../standard-library/vector-class.md) *(Right*). Hierbei handelt es sich um Instanzen der partiellen Sortierung von Funktionsvorlagen durch den Compiler. Wenn Vorlagenfunktionen so überladen werden, dass die Übereinstimmung der Vorlage mit dem Funktionsaufruf nicht eindeutig ist, wählt der Compiler die spezialisierteste Version der Vorlagenfunktion aus. Die allgemeine Version der Vorlagen Funktion **`template`** \< **class T**> **void Swap**( **t&**, **t&**) in der Algorithmusklasse funktioniert durch Zuweisung und ist ein langsamer Vorgang. Die spezialisierte Version in jedem Container ist viel schneller, da sie mit der internen Darstellung der Containerklasse genutzt werden kann.

### <a name="example"></a>Beispiel

Im Codebeispiel für die Memberfunktion [vector::swap](../standard-library/vector-class.md) finden Sie ein Beispiel, in dem die Vorlagenversion `swap` verwendet wird.

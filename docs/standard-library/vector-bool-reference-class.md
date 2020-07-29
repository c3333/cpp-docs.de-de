---
title: vector&lt;bool&gt;::reference-Klasse
ms.date: 11/04/2016
f1_keywords:
- vector/vector<bool>::reference
helpviewer_keywords:
- vector<bool> reference class
ms.assetid: f27854f9-0ef0-4e7e-ad2e-cd53b6cb3334
ms.openlocfilehash: 3dde17522c05a05bda04c338682b4b3f9920a972
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228101"
---
# <a name="vectorltboolgtreference-class"></a>vector&lt;bool&gt;::reference-Klasse

Die- `vector<bool>::reference` Klasse ist eine Proxy Klasse, die von der [Vector- \<bool> Klasse](../standard-library/vector-bool-class.md) zur Simulation bereitgestellt wird `bool&` .

## <a name="remarks"></a>Bemerkungen

Ein simulierter Verweis ist erforderlich, da C++ systemintern keine direkten Verweise auf Bits zulässt. `vector<bool>` verwendet nur ein Bit pro Element, auf das anhand dieser Proxyklasse verwiesen werden kann. Allerdings ist die Verweissimulation nicht vollständig, da bestimmte Zuweisungen ungültig sind. Da die Adresse des Objekts beispielsweise nicht akzeptiert `vector<bool>::reference` werden kann, ist der folgende Code, der verwendet werden soll, `vector<bool>::operator&` nicht korrekt:

```cpp
vector<bool> vb;
// ...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="member-functions"></a>Memberfunktionen

|Memberfunktion|BESCHREIBUNG|
|-|-|
|[flip](../standard-library/vector-bool-reference-flip.md)|Kehrt den booleschen Wert eines Vektorelements um.|
|[Operator bool](../standard-library/vector-bool-reference-operator-bool.md)|Stellt eine implizite Konvertierung von `vector<bool>::reference` in bereit **`bool`** .|
|[Operator =](../standard-library/vector-bool-reference-operator-assign.md)|Weist einen booleschen Wert einem Bit zu oder weist den Wert, der in einem Element enthalten ist, auf das verwiesen wird, einem Bit zu.|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header**:\<vector>

**Namespace:** std

## <a name="see-also"></a>Siehe auch

[\<vector>](../standard-library/vector.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standard Bibliotheks Referenz](../standard-library/cpp-standard-library-reference.md)

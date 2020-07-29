---
title: vector&lt;bool&gt;::reference::operator bool
ms.date: 11/04/2016
f1_keywords:
- operatorbool
- vector<bool>::reference::operatorbool
- bool
- std::vector<bool>::reference::operatorbool
helpviewer_keywords:
- BOOL operator
- reference::operator bool
ms.assetid: b0e57869-18cc-4296-9061-da502f30120d
ms.openlocfilehash: bb757fee9d6ec824a99557c409b1c4f02f48db5d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215386"
---
# <a name="vectorltboolgtreferenceoperator-bool"></a>vector&lt;bool&gt;::reference::operator bool

Stellt eine implizite Konvertierung von `vector<bool>::reference` in bereit **`bool`** .

## <a name="syntax"></a>Syntax

```cpp
operator bool() const;
```

## <a name="return-value"></a>Rückgabewert

Der boolesche Wert des Elements des [Vektor \<bool> ](../standard-library/vector-bool-class.md) Objekts.

## <a name="remarks"></a>Bemerkungen

Das `vector<bool>`-Objekt kann von diesem Operator nicht geändert werden.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<vector>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[Vector \<bool> :: Reference-Klasse](../standard-library/vector-bool-reference-class.md)\
[C++-Standard Bibliotheks Referenz](../standard-library/cpp-standard-library-reference.md)

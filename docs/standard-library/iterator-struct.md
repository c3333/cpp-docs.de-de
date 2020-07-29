---
title: iterator-Struktur
ms.date: 11/04/2016
f1_keywords:
- xutility/std::iterator
helpviewer_keywords:
- iterator class
- iterator struct
ms.assetid: c74c8000-8b18-4829-9b71-6103c4229b74
ms.openlocfilehash: b45cdb5c3d4608296cca34ad6a0be6e25b588d28
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222302"
---
# <a name="iterator-struct"></a>iterator-Struktur

Eine leere Basis Struktur, mit der sichergestellt wird, dass eine benutzerdefinierte iteratorklasse ordnungsgemäß mit `iterator_trait` s funktioniert.

## <a name="syntax"></a>Syntax

```cpp
struct iterator {
   typedef Category iterator_category;
   typedef Type value_type;
   typedef Distance difference_type;
   typedef Distance distance_type;
   typedef Pointer pointer;
   typedef Reference reference;
   };
```

## <a name="remarks"></a>Bemerkungen

Die Vorlagenstruktur wird als Basistyp für alle Iteratoren verwendet. Definiert den Membertypen

- `iterator_category` (ein Synonym für den Vorlagenparameter `Category`).

- `value_type` (ein Synonym für den Vorlagenparameter `Type`).

- `difference_type` (ein Synonym für den Vorlagenparameter `Distance`).

- `distance_type` (ein Synonym für den Vorlagenparameter `Distance`).

- `pointer` (ein Synonym für den Vorlagenparameter `Pointer`).

- `reference` (ein Synonym für den Vorlagenparameter `Reference`).

Beachten Sie, dass `value_type` kein konstanter Typ sein sollte, auch wenn `pointer` Punkte an einem Objekt von **`const`** `Type` und Verweis ein Objekt von bezeichnen **`const`** `Type` .

## <a name="example"></a>Beispiel

Unter [iterator_traits](../standard-library/iterator-traits-struct.md) finden Sie ein Beispiel für das Deklarieren und Verwenden von Typen in der Iterator-Basisklasse.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<iterator>

**Namespace:** std

## <a name="see-also"></a>Weitere Informationen

[\<iterator>](../standard-library/iterator.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++-Standard Bibliotheks Referenz](../standard-library/cpp-standard-library-reference.md)

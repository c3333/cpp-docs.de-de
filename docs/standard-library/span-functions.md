---
title: '&lt;Spannen &gt; Funktionen'
ms.date: 05/28/2020
f1_keywords:
- span/std::span::as_bytes
- span/std::as_writable_bytes
helpviewer_keywords:
- std::span [C++], as_writable_bytes
- std::as_bytes [C++]
ms.openlocfilehash: f51c99d2f2a051a07cefcb985fdb46340fefb3ee
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217440"
---
# <a name="ltspangt-functions"></a>&lt;Spannen &gt; Funktionen

Der- \<span> Header enthält die folgenden nicht-Member-Funktionen, die für **Span** -Objekte verwendet werden.

| **Nicht-Member-Funktionen** | **Beschreibung** |
|-|-|
|[as_bytes](#as_bytes) | Erhalten Sie eine schreibgeschützte Ansicht der Objektdarstellung der Elemente in der Spanne. |
|[as_writable_bytes](#as_writable_bytes) | Erhält eine Lese-/Schreibansicht der Objektdarstellung der Elemente in der Spanne. |

## <a name="as_bytes"></a>`as_bytes`

Erhalten Sie eine schreibgeschützte Ansicht der Objektdarstellung der Elemente in der Spanne.

```cpp
template <class T, size_t Extent>
auto as_bytes(span<T, Extent> s) noexcept;
```

### <a name="parameters"></a>Parameter

*Bund*\
Der Typ der Elemente in der Spanne.

*Ausdehnung*\
Die Anzahl der Elemente in der Spanne (sofern zum Zeitpunkt der Kompilierung bekannt), andernfalls, `dynamic_extent` die angibt, dass die Anzahl der Elemente bis zur Laufzeit nicht bekannt ist.

*Hymnen*\
Die Spanne, die die unformatierte Darstellung von erhält.

### <a name="return-value"></a>Rückgabewert

Ein `span<const byte, S>` für das erste Element, das in der Spanne gespeichert ist, in der `S``{reinterpret_cast<const std::byte*>(s.data()), s.size_bytes()}`

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

void main()
{
    int a[] = { 0,1,2 };
    span <int> mySpan(a);
    auto bytes = std::as_bytes(mySpan);
}
```

## <a name="as_writable_bytes"></a>`as_writable_bytes`

Wenn `T` nicht **`const`** ist, wird eine Lese-/Schreibansicht der rohbyte Darstellung der Elemente in der Spanne abgerufen.

```cpp
template <class T, size_t Extent>
auto as_writable_bytes(span<T, Extent> s) noexcept;
```

### <a name="parameters"></a>Parameter

*Bund*\
Der Typ der Elemente in der Spanne.

*Ausdehnung*\
Die Anzahl der Elemente in der Spanne (sofern zum Zeitpunkt der Kompilierung bekannt), andernfalls, `dynamic_extent` die angibt, dass die Anzahl der Elemente bis zur Laufzeit nicht bekannt ist.

*Hymnen*\
Die Spanne, die die unformatierte Darstellung von erhält.

### <a name="return-value"></a>Rückgabewert

Ein `span<byte, S>` für das erste Element, das in der Spanne gespeichert ist, in der `S``{reinterpret_cast<std::byte*>(s.data()), s.size_bytes()}`

### <a name="example"></a>Beispiel

```cpp
#include <span>
#include <iostream>

using namespace std;

void main()
{
    int a[] = { 0,1,2 };
    span <int> mySpan(a);
    auto bytes = as_writable_bytes(mySpan);
}
```

## <a name="see-also"></a>Weitere Informationen

[\<span>](span.md)

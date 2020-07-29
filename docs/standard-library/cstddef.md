---
title: '&lt;cstddef&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstddef>
helpviewer_keywords:
- cstddef header
ms.assetid: be8d1e39-5974-41ee-b41d-eafa6c82ffce
ms.openlocfilehash: f1582a4af1c26e1ef85cf0dce8406a4046a8fe8b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222523"
---
# <a name="ltcstddefgt"></a>&lt;cstddef&gt;

Schließt den C-Standard Bibliotheks Header ein \<stddef.h> und fügt zugeordnete Namen zum- `std` Namespace hinzu. Durch einschließen dieses Headers wird sichergestellt, dass die mit externer Verknüpfung im C-Standard Bibliotheks Header deklarierten Namen im- `std` Namespace deklariert werden.

> [!NOTE]
> \<cstddef>schließt den Typ **Byte** ein und enthält nicht den Typ **`wchar_t`** .

## <a name="syntax"></a>Syntax

```cpp
#include <cstddef>
```

## <a name="namespace-and-macros"></a>Namespace und Makros

```cpp
namespace std {
    using ptrdiff_t = see definition;
    using size_t = see definition;
    using max_align_t = see definition;
    using nullptr_t = decltype(nullptr);
}

#define NULL  // an implementation-defined null pointer constant
#define offsetof(type, member-designator)
```

### <a name="parameters"></a>Parameter

*ptrdiff_t*\
Ein von der Implementierung definierter ganzzahliger Typ mit Vorzeichen, der den Unterschied zwischen zwei Indizes in einem Array Objekt enthalten kann.

*size_t*\
Ein von der Implementierung definierter ganzzahliger Typ ohne Vorzeichen, der groß genug ist, um die Größe eines beliebigen Objekts in Bytes zu enthalten.

*max_align_t*\
Ein POD-Typ, dessen Ausrichtungs Anforderung mindestens so groß wie jeder skalare Typ ist und dessen Ausrichtungs Anforderung in jedem Kontext unterstützt wird.

*nullptr_t*\
Ein Synonym für den Typ eines- **`nullptr`** Ausdrucks. Obwohl eine **`nullptr`** Adresse nicht verwendet werden kann, kann die Adresse eines anderen *nullptr_t* Objekts, das ein Lvalue ist, angenommen werden.

## <a name="byte-class"></a>Byte-Klasse

```cpp
enum class byte : unsigned char {};

template <class IntType>
    constexpr byte& operator<<=(byte& b, IntType shift) noexcept;
    constexpr byte operator<<(byte b, IntType shift) noexcept;
    constexpr byte& operator>>=(byte& b, IntType shift) noexcept;
    constexpr byte operator>>(byte b, IntType shift) noexcept;

constexpr byte& operator|=(byte& left, byte right) noexcept;
constexpr byte operator|(byte left, byte right) noexcept;
constexpr byte& operator&=(byte& left, byte right) noexcept;
constexpr byte operator&(byte left, byte right) noexcept;
constexpr byte& operator^=(byte& left, byte right) noexcept;
constexpr byte operator^(byte left, byte right) noexcept;
constexpr byte operator~(byte b) noexcept;

template <class IntType>
    IntType to_integer(byte b) noexcept;
```

## <a name="see-also"></a>Weitere Informationen

[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Übersicht über die C++-Standard Bibliothek](../standard-library/cpp-standard-library-overview.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)

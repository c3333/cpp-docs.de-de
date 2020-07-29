---
title: '&lt;cassert&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cassert>
helpviewer_keywords:
- cassert header
ms.assetid: 6ead15a3-ac45-4075-be8e-350bca995c26
ms.openlocfilehash: b28f4554610d37b881494748f75499f46cd9e8d9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230232"
---
# <a name="ltcassertgt"></a>&lt;cassert&gt;

Schließt den C-Standard Bibliotheks Header ein \<assert.h> und fügt die verknüpften Namen zum- `std` Namespace hinzu. Durch einschließen dieses Headers wird sichergestellt, dass die mit externer Verknüpfung im C-Standard Bibliotheks Header deklarierten Namen im- `std` Namespace deklariert werden.

> [!NOTE]
> \<assert.h>definiert das **`static_assert`** Makro nicht.

## <a name="syntax"></a>Syntax

```cpp
#include <cassert>
```

## <a name="macros"></a>Makros

```cpp
#define assert(E)
```

### <a name="remarks"></a>Bemerkungen

`assert(E)`ist nur konstant, wenn NDEBUG definiert ist, wo `assert` zuletzt definiert oder neu definiert wurde oder *E* in bool konvertiert wird **`true`** .

## <a name="see-also"></a>Weitere Informationen

[Assert-Makro, _ASSERT _wassert](../c-runtime-library/reference/assert-macro-assert-wassert.md)\
[Header Dateireferenz](../standard-library/cpp-standard-library-header-files.md)\
[Übersicht über die C++-Standard Bibliothek](../standard-library/cpp-standard-library-overview.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)

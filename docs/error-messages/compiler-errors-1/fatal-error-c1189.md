---
title: Schwerwiegender Fehler C1189
ms.date: 04/27/2018
f1_keywords:
- C1189
helpviewer_keywords:
- C1189
ms.assetid: 2e5c8a78-edd4-411c-b619-558a96be148a
ms.openlocfilehash: 2217b865109cc48151e4e96b2d38b88764c0c64f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203633"
---
# <a name="fatal-error-c1189"></a>Schwerwiegender Fehler C1189

> **\#Fehler:** vom *Benutzer angegebene Fehlermeldung*

## <a name="remarks"></a>Bemerkungen

C1189 wird von der `#error`-Direktive generiert. Der Entwickler, der die Direktive codiert, gibt den Text der Fehlermeldung an. Weitere Informationen finden Sie unter [#Error-Direktive (C++C/)](../../preprocessor/hash-error-directive-c-cpp.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C1189 generiert. Im Beispiel gibt der Entwickler eine benutzerdefinierte Fehlermeldung aus, da der `_WIN32` Bezeichner nicht definiert ist:

```cpp
// C1189.cpp
#undef _WIN32
#if !defined(_WIN32)
#error _WIN32 must be defined   // C1189
#endif
```

## <a name="see-also"></a>Weitere Informationen

[#define-Direktive (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)

---
title: __uuidof-Operator
ms.date: 10/10/2018
f1_keywords:
- __LIBID_cpp
- __uuidof_cpp
- __uuidof
- _uuidof
helpviewer_keywords:
- __uuidof keyword [C++]
- __LIBID_ keyword [C++]
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
ms.openlocfilehash: f7564270408d14f58d1528c1f41c0afd2dbe219c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226970"
---
# <a name="__uuidof-operator"></a>`__uuidof`-Operator

**Microsoft-spezifisch**

Ruft die GUID ab, die dem Ausdruck angefügt ist.

## <a name="syntax"></a>Syntax

> **`__uuidof (`***Ausdruck***`)`**

## <a name="remarks"></a>Bemerkungen

Der *Ausdruck* kann ein Typname, ein Zeiger, ein Verweis oder ein Array dieses Typs, eine Vorlage, die auf diese Typen spezialisiert ist, oder eine Variable dieser Typen sein. Das Argument ist gültig, solange der Compiler es verwenden kann, um das angefügte GUID zu suchen.

Ein Sonderfall dieses intrinsischen Werts ist, wenn **0** oder NULL als Argument angegeben wird. In diesem Fall **`__uuidof`** gibt eine GUID zurück, die aus Nullen besteht.

Verwenden Sie dieses Schlüsselwort, um die an folgende Elemente angefügte GUID zu extrahieren:

- Ein-Objekt durch das [`uuid`](../cpp/uuid-cpp.md) Erweiterte Attribut.

- Ein Bibliotheks Block, der mit dem-Attribut erstellt wurde [`module`](../windows/attributes/module-cpp.md) .

> [!NOTE]
> Initialisiert ein Objekt in einem Debugbuild **`__uuidof`** immer dynamisch (zur Laufzeit). In einem Releasebuild **`__uuidof`** kann ein Objekt statisch (zur Kompilierzeit) initialisieren.

Aus Gründen der Kompatibilität mit früheren Versionen ist **`_uuidof`** ein Synonym für, **`__uuidof`** es sei denn, die Compileroption [ `/Za` \( Spracherweiterungen deaktivieren)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

## <a name="example"></a>Beispiel

Mit dem folgenden Code (kompiliert mit "ole32.lib") wird das "uuid" eines Bibliotheksblocks angezeigt, der mit dem Modulattribut erstellt wird:

```cpp
// expre_uuidof.cpp
// compile with: ole32.lib
#include "stdio.h"
#include "windows.h"

[emitidl];
[module(name="MyLib")];
[export]
struct stuff {
   int i;
};

int main() {
   LPOLESTR lpolestr;
   StringFromCLSID(__uuidof(MyLib), &lpolestr);
   wprintf_s(L"%s", lpolestr);
   CoTaskMemFree(lpolestr);
}
```

## <a name="comments"></a>Kommentare

In Fällen, in denen sich der Bibliotheksname nicht mehr im Gültigkeitsbereich befindet, können Sie `__LIBID_` anstelle von verwenden **`__uuidof`** . Zum Beispiel:

```cpp
StringFromCLSID(__LIBID_, &lpolestr);
```

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Ausdrücke mit unären Operatoren](../cpp/expressions-with-unary-operators.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)

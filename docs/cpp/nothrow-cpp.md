---
title: nothrow (C++)
ms.date: 01/03/2018
f1_keywords:
- nothrow_cpp
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
ms.openlocfilehash: 8ce0e9ea6a39ef7760c7a6d0802913326433cf68
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227269"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Microsoft-spezifisch**

Ein **`__declspec`** Erweitertes Attribut, das in der Deklaration von Funktionen verwendet werden kann.

## <a name="syntax"></a>Syntax

> *Rückgabetyp* __declspec (nothrow) [*Aufrufkonvention*] *Funktionsname* ([*Argument-List*])

## <a name="remarks"></a>Bemerkungen

Es wird empfohlen, dass der gesamte neue Code den [noaußer](noexcept-cpp.md) -Operator anstelle von verwendet `__declspec(nothrow)` .

Dieses Attribut weist den Compiler an, dass die deklarierte Funktion und die Funktionen, die aufgerufen werden, nie eine Ausnahme auslösen. Die-Direktive wird jedoch nicht erzwungen. Anders ausgedrückt: Es wird nicht bewirkt, dass [Std::](../standard-library/exception-functions.md#terminate) End im Gegensatz zu **`noexcept`** oder im **Std: c++ 17** -Modus (Visual Studio 2017, Version 15,5 und höher) aufgerufen wird `throw()` .

Mit dem Modell für synchrone Ausnahmebehandlung kann der Compiler nun standardmäßig die Mechanismen der Lebensdauerverfolgung gewisser entladbarer Objekte in einer solchen Funktion eliminieren, wodurch die Codegröße erheblich reduziert wird. Bei der folgenden Präprozessordirektive sind die folgenden drei Funktions Deklarationen im **/Std: c++ 14** -Modus gleichwertig:

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

Im **/Std: c++ 17** -Modus `throw()` entspricht nicht den anderen, die verwenden, `__declspec(nothrow)` da dies bewirkt, dass `std::terminate` aufgerufen wird, wenn eine Ausnahme von der-Funktion ausgelöst wird.

Die- `void __stdcall f3() throw();` Deklaration verwendet die vom C++-Standard definierte Syntax. In c++ 17 `throw()` war das Schlüsselwort veraltet.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[__declspec](../cpp/declspec.md)<br/>
[noexcept](noexcept-cpp.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)

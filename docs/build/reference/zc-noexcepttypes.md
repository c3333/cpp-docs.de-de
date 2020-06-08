---
title: /Zc:noexceptTypes (noexcept-Regeln für C++17)
ms.date: 06/04/2020
f1_keywords:
- /Zc:noexceptTypes
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
ms.openlocfilehash: 0f833209938ccc09cbc37235788b6f719d4d12d4
ms.sourcegitcommit: fe146adb3a02872538637196bb3c45aeeeaaf5c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84506870"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes (noexcept-Regeln für C++17)

Der c++ 17-Standard erstellt `throw()` einen Alias für `noexcept` , entfernt `throw(` *`type-list`* `)` und und ermöglicht das `throw(...)` einschließen bestimmter Typen `noexcept` . Diese Änderung kann eine Reihe von Problemen mit der Quell Kompatibilität in Code verursachen, der c++ 14 oder früher entspricht. Die **`/Zc:noexceptTypes`** Option gibt die Konformität mit dem c++ 17-Standard an. **`/Zc:noexceptTypes-`** ermöglicht das Verhalten von c++ 14 und früher, wenn Code im c++ 17-Modus kompiliert wird.

## <a name="syntax"></a>Syntax

> **`/Zc:noexceptTypes`**\[**`-`**]

## <a name="remarks"></a>Bemerkungen

Wenn die- **`/Zc:noexceptTypes`** Option angegeben wird, entspricht der Compiler dem c++ 17-Standard und behandelt [**`throw()`**](../../cpp/exception-specifications-throw-cpp.md) als Alias für [**`noexcept`**](../../cpp/noexcept-cpp.md) , entfernt `throw(` *`type-list`* `)` und und ermöglicht das `throw(...)` einschließen bestimmter Typen **`noexcept`** . Die **`/Zc:noexceptTypes`** Option ist nur verfügbar, wenn [**`/std:c++17`**](std-specify-language-standard-version.md) oder [**`/std:c++latest`**](std-specify-language-standard-version.md) aktiviert ist. **`/Zc:noexceptTypes`** ist standardmäßig aktiviert, um dem ISO c++ 17-Standard zu entsprechen. Die [**`/permissive-`**](permissive-standards-conformance.md) Option wirkt sich nicht auf aus **`/Zc:noexceptTypes`** . Deaktivieren Sie diese Option, indem Sie angeben **`/Zc:noexceptTypes-`** , um zum Verhalten von c++ 14 zurückzukehren, **`noexcept`** Wenn **`/std:c++17`** oder **`/std:c++latest`** angegeben wird.

Ab Visual Studio 2017 Version 15,5 diagnostiziert der C++-Compiler eher nicht übereinstimmende Ausnahme Spezifikationen in Deklarationen im C++ 17-Modus oder wenn Sie die- [**`/permissive-`**](permissive-standards-conformance.md) Option angeben.

Dieses Beispiel zeigt, wie sich Deklarationen mit einem ausnahmespezifizierer Verhalten, wenn die **`/Zc:noexceptTypes`** Option festgelegt oder deaktiviert wird. Um das Verhalten beim Festlegen anzuzeigen, kompilieren Sie mithilfe von `cl /EHsc /W4 noexceptTypes.cpp` . Kompilieren Sie mithilfe von, um das Verhalten bei der Deaktivierung anzuzeigen `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp` .

```cpp
// noexceptTypes.cpp
// Compile by using: cl /EHsc /W4 noexceptTypes.cpp
// Compile by using: cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp

void f() throw();    // equivalent to void f() noexcept;
void f() { }         // warning C5043
void g() throw(...); // warning C5040

struct A
{
    virtual void f() throw();
};

struct B : A
{
    virtual void f() { } // error C2694
};
```

Bei der Kompilierung mit der Standardeinstellung **`/Zc:noexceptTypes`** generiert das Beispiel die aufgelisteten Warnungen. Um Ihren Code zu aktualisieren, verwenden Sie stattdessen Folgendes:

```cpp
void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A
{
    virtual void f() noexcept;
};

struct B : A
{
    virtual void f() noexcept { }
};
```

Weitere Informationen über Konformitätsprobleme in Visual C++ finden Sie unter [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Ändern Sie die Eigenschaft **zusätzliche Optionen** so, dass oder einschließt, *`/Zc:noexceptTypes`* *`/Zc:noexceptTypes-`* und wählen Sie dann **OK**aus.

## <a name="see-also"></a>Weitere Informationen:

[**`/Zc`** Konformitäts](zc-conformance.md)\
[noexcept](../../cpp/noexcept-cpp.md)\
[Ausnahmespezifikationen (throw)](../../cpp/exception-specifications-throw-cpp.md)

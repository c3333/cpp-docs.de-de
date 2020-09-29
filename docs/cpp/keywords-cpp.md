---
title: Schlüsselwörter (C++)
description: Listet die Schlüsselwörter der C++-Standardsprache, Microsoft-spezifische Schlüsselwörter und kontextspezifische Schlüsselwörter auf.
ms.custom: index-page
ms.date: 07/25/2020
helpviewer_keywords:
- keywords [C++]
ms.assetid: d7ca94a8-f785-41ce-9f73-d3c4fd508489
ms.openlocfilehash: b875b4df797985dc21f54f48ceeaa86574f31ac6
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91498762"
---
# <a name="keywords-c"></a>Schlüsselwörter (C++)

Schlüsselwörter sind vordefinierte, reservierte Bezeichner, die besondere Bedeutungen haben. Sie können nicht als Bezeichner in Ihrem Programm verwendet werden. Die folgenden Schlüsselwörter sind für Microsoft C++ reserviert. Namen mit führenden unterstrichen und Namen, die für C++/CX und C++/CLI angegeben sind, sind Microsoft-Erweiterungen.

## <a name="standard-c-keywords"></a>Standard C++ Schlüsselwörter

:::row:::
    :::column:::
        [`alignas`](align-cpp.md)\
        [`alignof`](alignof-operator.md)\
        [`and`](bitwise-and-operator-amp.md)<sup>b</sup>\
        [`and_eq`](assignment-operators.md)<sup>b</sup>\
        [`asm`](../assembler/inline/asm.md)<sup>a</sup>\
        [`auto`](./auto-cpp.md)\
        [`bitand`](bitwise-and-operator-amp.md)<sup>b</sup>\
        [`bitor`](bitwise-inclusive-or-operator-pipe.md)<sup>b</sup>\
        [`bool`](bool-cpp.md)\
        [`break`](break-statement-cpp.md)\
        [`case`](switch-statement-cpp.md)\
        [`catch`](try-throw-and-catch-statements-cpp.md)\
        [`char`](fundamental-types-cpp.md)\
        [`char8_t`](fundamental-types-cpp.md)<sup>c</sup>\
        [`char16_t`](char-wchar-t-char16-t-char32-t.md)\
        [`char32_t`](char-wchar-t-char16-t-char32-t.md)\
        [`class`](class-cpp.md)\
        [`compl`](one-s-complement-operator-tilde.md)<sup>b</sup>\
        **`concept`**<sup>c</sup>\
        [`const`](const-cpp.md)\
        [`const_cast`](const-cast-operator.md)\
        **`consteval`**<sup>c</sup>\
        [`constexpr`](constexpr-cpp.md)
    :::column-end:::
    :::column:::
        **`constinit`**<sup>c</sup>\
        [`continue`](continue-statement-cpp.md)\
        **`co_await`**<sup>c</sup>\
        **`co_return`**<sup>c</sup>\
        **`co_yield`**<sup>c</sup>\
        [`decltype`](decltype-cpp.md)\
        [`default`](switch-statement-cpp.md)\
        [`delete`](delete-operator-cpp.md)\
        [`do`](do-while-statement-cpp.md)\
        [`double`](fundamental-types-cpp.md)\
        [`dynamic_cast`](dynamic-cast-operator.md)\
        [`else`](if-else-statement-cpp.md)\
        [`enum`](enumerations-cpp.md)\
        [`explicit`](user-defined-type-conversions-cpp.md)\
        **`export`**<sup>c</sup>\
        [`extern`](./extern-cpp.md)\
        [`false`](false-cpp.md)\
        [`float`](fundamental-types-cpp.md)\
        [`for`](for-statement-cpp.md)\
        [`friend`](friend-cpp.md)\
        [`goto`](goto-statement-cpp.md)\
        [`if`](if-else-statement-cpp.md)\
        [`inline`](inline-functions-cpp.md)
    :::column-end:::
    :::column:::
        [`int`](fundamental-types-cpp.md)\
        [`long`](fundamental-types-cpp.md)\
        [`mutable`](mutable-data-members-cpp.md)\
        [`namespace`](namespaces-cpp.md)\
        [`new`](new-operator-cpp.md)\
        [`noexcept`](noexcept-cpp.md)\
        [`not`](logical-negation-operator-exclpt.md)<sup>b</sup>\
        [`not_eq`](equality-operators-equal-equal-and-exclpt-equal.md)<sup>b</sup>\
        [`nullptr`](nullptr.md)\
        [`operator`](operator-overloading.md)\
        [`or`](logical-or-operator-pipe-pipe.md)<sup>b</sup>\
        [`or_eq`](assignment-operators.md)<sup>b</sup>\
        [`private`](private-cpp.md)\
        [`protected`](protected-cpp.md)\
        [`public`](public-cpp.md)\
        [`register`](storage-classes-cpp.md#register) [`reinterpret_cast`](reinterpret-cast-operator.md)\
        **`requires`**<sup>c</sup>\
        [`return`](return-statement-cpp.md)\
        [`short`](fundamental-types-cpp.md)\
        [`signed`](fundamental-types-cpp.md)\
        [`sizeof`](sizeof-operator.md)\
        [`static`](storage-classes-cpp.md)\
        [`static_assert`](static-assert.md)
    :::column-end:::
    :::column:::
        [`static_cast`](static-cast-operator.md)\
        [`struct`](struct-cpp.md)\
        [`switch`](switch-statement-cpp.md)\
        [`template`](templates-cpp.md)\
        [`this`](this-pointer.md)\
        [`thread_local`](storage-classes-cpp.md#thread_local)\
        [`throw`](try-throw-and-catch-statements-cpp.md)\
        [`true`](true-cpp.md)\
        [`try`](try-throw-and-catch-statements-cpp.md)\
        [`typedef`](aliases-and-typedefs-cpp.md)\
        [`typeid`](typeid-operator.md)\
        [`typename`](typename.md)\
        [`union`](unions.md)\
        [`unsigned`](fundamental-types-cpp.md)\
        [`using`](using-declaration.md) Zuverlässigkeits
        [`using`](namespaces-cpp.md#using_directives) über
        [`virtual`](virtual-cpp.md)\
        [`void`](void-cpp.md)\
        [`volatile`](volatile-cpp.md)\
        [`wchar_t`](fundamental-types-cpp.md)\
        [`while`](while-statement-cpp.md)\
        [`xor`](bitwise-exclusive-or-operator-hat.md)<sup>b</sup>\
        [`xor_eq`](assignment-operators.md)<sup>b</sup>
    :::column-end:::
:::row-end:::

<sup>ein</sup> Microsoft-spezifisches **`__asm`** Schlüsselwort ersetzt die C++- **`asm`** Syntax. **`asm`** ist für die Kompatibilität mit anderen C++-Implementierungen reserviert, aber nicht implementiert. Verwenden Sie **`__asm`** für die Inlineassembly auf x86-Zielen. Microsoft C++ unterstützt keine Inlineassembly für andere Ziele.

<sup>b</sup> die Synonyme für erweiterte Operatoren sind Schlüsselwörter, wenn [`/permissive-`](../build/reference/permissive-standards-conformance.md) [ `/Za` \( Spracherweiterungen](../build/reference/za-ze-disable-language-extensions.md) angegeben werden, oder deaktivieren Sie. Sie sind keine Schlüsselwörter, wenn Microsoft-Erweiterungen aktiviert sind.

<sup>c</sup> wird unterstützt, wenn [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) angegeben wird.

## <a name="microsoft-specific-c-keywords"></a>Microsoft-spezifische C++-Schlüsselwörter

In C++ sind Bezeichner mit zwei aufeinander folgenden unterstrichen für compilerimplementierungen reserviert. Die Microsoft-Konvention liegt vor, dass Microsoft-spezifischen Schlüsselwörtern doppelte Unterstriche vorangestellt werden. Diese Wörter können nicht als Bezeichnernamen verwendet werden.

Standardmäßig sind Microsoft-Erweiterungen aktiviert. Um sicherzustellen, dass die Programme vollständig portabel sind, können Sie Microsoft-Erweiterungen deaktivieren, indem Sie [`/permissive-`](../build/reference/permissive-standards-conformance.md) während der Kompilierung die Option " [ `/Za` \( Spracherweiterungen deaktivieren](../build/reference/za-ze-disable-language-extensions.md) " angeben. Diese Optionen deaktivieren einige Microsoft-spezifische Schlüsselwörter.

Wenn Microsoft-Erweiterungen aktiviert sind, können Sie Microsoft-spezifische Schlüsselwörter in Programmen verwenden. Zur Einhaltung der ANSI-Kompatibilität wird diesen Schlüsselwörtern ein doppelter Unterstrich vorangestellt. Aus Gründen der Abwärtskompatibilität werden Versionen mit einem Unterstrich von vielen der doppelt unterstützten Schlüsselwörter unterstützt. Das **`__cdecl`** Schlüsselwort ist ohne führenden Unterstrich verfügbar.

Das **`__asm`** Schlüsselwort ersetzt die C++- **`asm`** Syntax. **`asm`** ist für die Kompatibilität mit anderen C++-Implementierungen reserviert, aber nicht implementiert. Verwenden Sie **`__asm`**.

Das **`__based`** -Schlüsselwort weist eingeschränkte Verwendungsmöglichkeiten für 32-Bit-und 64-Bit-Ziel Kompilierungen auf.

:::row:::
    :::column:::
        [`__alignof`](alignof-operator.md)<sup>e</sup>\
        [`__asm`](../assembler/inline/asm.md)<sup>e</sup>\
        [`__assume`](../intrinsics/assume.md)<sup>e</sup>\
        [`__based`](based-pointers-cpp.md)<sup>e</sup>\
        [`__cdecl`](cdecl.md)<sup>e</sup>\
        [`__declspec`](declspec.md)<sup>e</sup>\
        [`__event`](event.md)\
        [`__except`](try-except-statement.md)<sup>e</sup>\
        [`__fastcall`](fastcall.md)<sup>e</sup>\
        [`__finally`](try-finally-statement.md)<sup>e</sup>\
        [`__forceinline`](inline-functions-cpp.md)<sup>e</sup>
    :::column-end:::
    :::column:::
        [`__hook`](hook.md)<sup>d</sup>\
        [`__if_exists`](if-exists-statement.md)\
        [`__if_not_exists`](if-not-exists-statement.md)\
        [`__inline`](inline-functions-cpp.md)<sup>e</sup>\
        [`__int16`](int8-int16-int32-int64.md)<sup>e</sup>\
        [`__int32`](int8-int16-int32-int64.md)<sup>e</sup>\
        [`__int64`](int8-int16-int32-int64.md)<sup>e</sup>\
        [`__int8`](int8-int16-int32-int64.md)<sup>e</sup>\
        [`__interface`](interface.md)\
        [`__leave`](try-finally-statement.md)<sup>e</sup>\
        [`__m128`](m128.md)
    :::column-end:::
    :::column:::
        [`__m128d`](m128d.md)\
        [`__m128i`](m128i.md)\
        [`__m64`](m64.md)\
        [`__multiple_inheritance`](inheritance-keywords.md)<sup>e</sup>\
        [`__ptr32`](ptr32-ptr64.md)<sup>e</sup>\
        [`__ptr64`](ptr32-ptr64.md)<sup>Fresser</sup>\
        [`__raise`](raise.md)\
        [`__restrict`](extension-restrict.md)<sup>e</sup>\
        [`__single_inheritance`](inheritance-keywords.md)<sup>Fresser</sup>\
        [`__sptr`](sptr-uptr.md)<sup>Fresser</sup>\
        [`__stdcall`](stdcall.md)<sup>e</sup>
    :::column-end:::
    :::column:::
        [`__super`](super.md)\
        [`__thiscall`](thiscall.md)\
        [`__unaligned`](unaligned.md)<sup>e</sup>\
        [`__unhook`](unhook.md)<sup>d</sup>\
        [`__uptr`](sptr-uptr.md)<sup>e</sup>\
        [`__uuidof`](uuidof-operator.md)<sup>e</sup>\
        [`__vectorcall`](vectorcall.md)<sup>e</sup>\
        [`__virtual_inheritance`](inheritance-keywords.md)<sup>e</sup>\
        [`__w64`](w64.md)<sup>e</sup>\
        [`__wchar_t`](fundamental-types-cpp.md)
    :::column-end:::
:::row-end:::

intrinsische <sup>d-</sup> Funktion für die Ereignis Behandlung.

<sup>e</sup> aus Gründen der Abwärtskompatibilität mit früheren Versionen sind diese Schlüsselwörter sowohl mit zwei führenden unterstrichen als auch mit einem einzelnen vorangehenden unterstrich verfügbar, wenn Microsoft-Erweiterungen aktiviert sind (Standardeinstellung).

## <a name="microsoft-keywords-in-__declspec-modifiers"></a>Microsoft-Schlüsselwörter in __declspec Modifizierer

Diese Bezeichner sind erweiterte Attribute für den- **`__declspec`** Modifizierer. Sie werden als Schlüsselwörter in diesem Kontext betrachtet.

:::row:::
    :::column:::
        [`align`](align-cpp.md)\
        [`allocate`](allocate.md)\
        [`allocator`](allocator.md)\
        [`appdomain`](appdomain.md)\
        [`code_seg`](code-seg-declspec.md)\
        [`deprecated`](deprecated-cpp.md)
    :::column-end:::
    :::column:::
        [`dllexport`](dllexport-dllimport.md)\
        [`dllimport`](dllexport-dllimport.md)\
        [`jitintrinsic`](jitintrinsic.md)\
        [`naked`](naked-cpp.md)\
        [`noalias`](noalias.md)\
        [`noinline`](noinline.md)
    :::column-end:::
    :::column:::
        [`noreturn`](noreturn.md)\
        [`nothrow`](nothrow-cpp.md)\
        [`novtable`](novtable.md)\
        [`process`](process.md)\
        [`property`](property-cpp.md)\
        [`restrict`](restrict.md)
    :::column-end:::
    :::column:::
        [`safebuffers`](safebuffers.md)\
        [`selectany`](selectany.md)\
        [`spectre`](spectre.md)\
        [`thread`](thread.md)\
        [`uuid`](uuid-cpp.md)
    :::column-end:::
:::row-end:::

## <a name="ccli-and-ccx-keywords"></a>C++/CLI-und C++/CX-Schlüsselwörter

:::row:::
    :::column:::
        [`__abstract`](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<sup>f</sup>\
        [`__box`](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<sup>f</sup>\
        [`__delegate`](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<sup>f</sup>\
        [`__gc`](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<sup>f</sup>\
        [`__identifier`](../extensions/identifier-cpp-cli.md)\
        [`__nogc`](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<sup>f</sup>\
        [`__noop`](../intrinsics/noop.md)\
        **`__pin`**<sup>f</sup>\
        **`__property`**<sup>f</sup>\
        **`__sealed`**<sup>f</sup>
    :::column-end:::
    :::column:::
        [`__try_cast`](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<sup>f</sup>\
        [`__value`](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<sup>f</sup>\
        [`abstract`](../extensions/abstract-cpp-component-extensions.md)<sup>g</sup>\
        [`array`](../extensions/arrays-cpp-component-extensions.md)<sup>g</sup>\
        [`as_friend`](../preprocessor/hash-using-directive-cpp.md)\
        [`delegate`](../extensions/delegate-cpp-component-extensions.md)<sup>g</sup>\
        [`enum class`](../extensions/enum-class-cpp-component-extensions.md)\
        [`enum struct`](../extensions/enum-class-cpp-component-extensions.md)\
        [`event`](../extensions/event-cpp-component-extensions.md)<sup>g</sup>
    :::column-end:::
    :::column:::
        [`finally`](../dotnet/finally.md)\
        [`for each in`](../dotnet/for-each-in.md)\
        [`gcnew`](../extensions/ref-new-gcnew-cpp-component-extensions.md)<sup>g</sup>\
        [`generic`](../extensions/generics-cpp-component-extensions.md)<sup>g</sup>\
        [`initonly`](../dotnet/initonly-cpp-cli.md)\
        [`interface class`](../extensions/interface-class-cpp-component-extensions.md)<sup>g</sup>\
        [`interface struct`](../extensions/interface-class-cpp-component-extensions.md)<sup>g</sup>\
        [`interior_ptr`](../extensions/interior-ptr-cpp-cli.md)<sup>g</sup>\
        [`literal`](../extensions/literal-cpp-component-extensions.md)<sup>g</sup>
    :::column-end:::
    :::column:::
        [`new`](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)<sup>g</sup>\
        [`property`](../extensions/property-cpp-component-extensions.md)<sup>g</sup>\
        [`ref class`](../extensions/classes-and-structs-cpp-component-extensions.md)\
        [`ref struct`](../extensions/classes-and-structs-cpp-component-extensions.md)\
        [`safecast`](../extensions/safe-cast-cpp-component-extensions.md)\
        [`sealed`](../extensions/sealed-cpp-component-extensions.md)<sup>g</sup>\
        [`typeid`](../extensions/typeid-cpp-component-extensions.md)\
        [`value class`](../extensions/classes-and-structs-cpp-component-extensions.md)<sup>g</sup>\
        [`value struct`](../extensions/classes-and-structs-cpp-component-extensions.md)<sup>g</sup>
    :::column-end:::
:::row-end:::

<sup>f</sup> gilt nur für Managed Extensions for C++. Diese Syntax ist inzwischen veraltet. Weitere Informationen finden Sie unter [Komponentenerweiterungen für Laufzeitplattformen](../extensions/component-extensions-for-runtime-platforms.md).

<sup>g</sup> anwendbar auf C++/CLI.

## <a name="see-also"></a>Weitere Informationen

[Lexikalische Konventionen](lexical-conventions.md)<br/>
[C++ integrierte Operatoren, Rangfolge und Assoziativität](cpp-built-in-operators-precedence-and-associativity.md)

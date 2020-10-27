---
title: C-Schlüsselwörter
description: Schlüsselwörter in Standard-C- und Microsoft C-Compilererweiterungen.
ms.date: 10/15/2020
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
ms.openlocfilehash: 24981c8d70cb56b4578fd905a30ccc57eaa83d45
ms.sourcegitcommit: f19f02f217b80804ab321d463c76ce6f681abcc6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "92176220"
---
# <a name="c-keywords"></a>C-Schlüsselwörter

*Schlüsselwörter* sind Wörter, die für den C-Compiler eine besondere Bedeutung haben. In den Übersetzungsphasen 7 und 8 kann ein Bezeichner nicht dieselbe Schreibweise und Groß-/Kleinschreibung haben wie ein C-Schlüsselwort. Weitere Informationen erhalten Sie unter [Phasen der Übersetzung](../preprocessor/phases-of-translation.md) in der *Präprozessorreferenz* . Weitere Informationen zu Bezeichnern finden Sie unter [Bezeichner](../c-language/c-identifiers.md).

## <a name="standard-c-keywords"></a>Standardschlüsselwörter in C

Die Programmiersprache C verwendet die folgenden Schlüsselwörter:

:::row:::
    :::column:::
        **`auto`**\
        **`break`**\
        **`case`**\
        **`char`**\
        **`const`**\
        **`continue`**\
        **`default`**\
        **`do`**\
        **`double`**\
        **`else`**\
        **`enum`**
    :::column-end:::
    :::column:::
        **`extern`**\
        **`float`**\
        **`for`**\
        **`goto`**\
        **`if`**\
        **`inline`** <sup>1, a</sup>\
        **`int`**\
        **`long`**\
        **`register`**\
        **`restrict`** <sup>1, a</sup>\
        **`return`**
    :::column-end:::
    :::column:::
        **`short`**\
        **`signed`**\
        **`sizeof`**\
        **`static`**\
        **`struct`**\
        **`switch`**\
        **`typedef`**\
        **`union`**\
        **`unsigned`**\
        **`void`**\
        **`volatile`**
    :::column-end:::
    :::column:::
        **`while`**\
        **`_Alignas`** <sup>2, a</sup>\
        **`_Alignof`** <sup>2, a</sup>\
        **`_Atomic`** <sup>2, b</sup>\
        **`_Bool`** <sup>1, a</sup>\
        **`_Complex`** <sup>1, b</sup>\
        **`_Generic`** <sup>2, a</sup>\
        **`_Imaginary`** <sup>1, b</sup>\
        **`_Noreturn`** <sup>2, a</sup>\
        **`_Static_assert`** <sup>2, a</sup>\
        **`_Thread_local`** <sup>2, b</sup>
    :::column-end:::
:::row-end:::

<sup>1</sup>  In ISO C99 eingeführte Schlüsselwörter.

<sup>2</sup>  In ISO C11 eingeführte Schlüsselwörter.

<sup>a</sup> Ab Visual Studio 2019 Version 16.8 werden diese Schlüsselwörter in C-kompiliertem Code unterstützt, wenn die Compileroption **`/std:c11`** oder **`/std:c17`** angegeben wird.

<sup>b</sup> Ab Visual Studio 2019 Version 16.8 werden diese Schlüsselwörter in C-kompiliertem Code erkannt, aber nicht vom Compiler unterstützt, wenn die Compileroption **`/std:c11`** oder **`/std:c17`** angegeben wird.

Sie können Schlüsselwörter nicht neu definieren. Bevor Sie mit [C-Präprozessoranweisungen](../preprocessor/preprocessor-directives.md) kompilieren, können Sie jedoch Ersatztext für Schlüsselwörter angeben.

## <a name="microsoft-specific-c-keywords"></a>Microsoft-spezifische C-Schlüsselwörter

Der ANSI- und ISO-C-Standard ermöglichen, Bezeichner mit zwei vorangestellten Unterstrichen für Compilerimplementierungen zu reservieren. Daher werden gemäß Microsoft-Konvention Microsoft-spezifischen Schlüsselwortnamen doppelte Unterstriche vorangestellt. Diese Wörter können nicht als Bezeichnernamen verwendet werden. Eine Beschreibung der Regeln für die Benennung von Bezeichnern, einschließlich der Verwendung von doppelten Unterstrichen, finden Sie unter [Bezeichner](../c-language/c-identifiers.md).

Die folgenden Schlüsselwörter und speziellen Bezeichner werden vom Microsoft C-Compiler erkannt:

:::row:::
    :::column:::
        **`__asm`** <sup>5</sup>\
        **`dllimport`** <sup>4</sup>\
        **`__int8`** <sup>5</sup>\
        **`naked`** <sup>4</sup>\
        **`__based`** <sup>3, 5</sup>
    :::column-end:::
    :::column:::
        **`__except`** <sup>5</sup>\
        **`__int16`** <sup>5</sup>\
        **`__stdcall`** <sup>5</sup>\
        **`__cdecl`** <sup>5</sup>\
        **`__fastcall`**
    :::column-end:::
    :::column:::
        **`__int32`** <sup>5</sup>\
        **`thread`** <sup>4</sup>\
        **`__declspec`** <sup>5</sup>\
        **`__finally`** <sup>5</sup>\
        **`__int64`** <sup>5</sup>
    :::column-end:::
    :::column:::
        **`__try`** <sup>5</sup>\
        **`dllexport`** <sup>4</sup>\
        **`__inline`** <sup>5</sup>\
        **`__leave`** <sup>5</sup>\
        **`static_assert`** <sup>6</sup>
    :::column-end:::
:::row-end:::

<sup>3</sup> Das **`__based`** -Schlüsselwort weist eingeschränkte Verwendung für 32-Bit- und 64-Bit-Zielkompilierungen auf.

<sup>4</sup> Dies sind spezielle Bezeichner, wenn sie mit **`__declspec`** verwendet werden. Ihre Verwendung in anderen Kontexten ist nicht eingeschränkt.

<sup>5</sup> Wegen der Kompatibilität mit früheren Versionen sind diese Schlüsselwörter sowohl mit zwei führenden Unterstrichen als auch mit einem einzigen führenden Unterstrich verfügbar, wenn Microsoft-Erweiterungen aktiviert sind.

<sup>6</sup> Wenn Sie <assert.h> nicht einschließen, ordnet der Visual C-Compiler von Microsoft **`static_assert`** dem C11-Schlüsselwort **`_Static_assert`** zu.

Standardmäßig sind Microsoft-Erweiterungen aktiviert. Um das Erstellen portierbaren Codes zu unterstützen, können Sie Microsoft-Erweiterungen deaktivieren, indem Sie während der Kompilierung die Option [/Za \(Spracherweiterungen deaktivieren)](../build/reference/za-ze-disable-language-extensions.md) angeben. Mit dieser Option werden einige Microsoft-spezifische Schlüsselwörter deaktiviert.

Wenn Microsoft-Erweiterungen aktiviert sind, können Sie in den Programmen die oben aufgeführten Schlüsselwörter verwenden. Bei Einhaltung der Kompatibilität mit Standards wird den meisten dieser Schlüsselwörter ein doppelter Unterstrich vorangestellt. Die vier Ausnahmen **`dllexport`** , **`dllimport`** , **`naked`** und **`thread`** werden nur mit **`__declspec`** verwendet und erfordern deshalb keinen vorangestellten doppelten Unterstrich. Für die Abwärtskompatibilität werden die restlichen Schlüsselwörter mit Versionen mit einem Unterstrich unterstützt.

## <a name="see-also"></a>Siehe auch

[C-Elemente](../c-language/elements-of-c.md)

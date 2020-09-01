---
title: C-Schlüsselwörter
ms.date: 10/09/2018
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
ms.openlocfilehash: 1b49da349a6552022dfd9e8e66e85634f4694645
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838775"
---
# <a name="c-keywords"></a>C-Schlüsselwörter

"Schlüsselwörter" sind Wörter, die eine besondere Bedeutung für den C-Compiler haben. In den Übersetzungsphasen 7 und 8 kann ein Bezeichner nicht dieselbe Schreibweise und Groß-/Kleinschreibung haben wie ein C-Schlüsselwort. (Eine Beschreibung der [Übersetzungsphasen](../preprocessor/phases-of-translation.md) finden Sie in der *Präprozessorreferenz*. Informationen zu Bezeichnern finden Sie unter [Bezeichner](../c-language/c-identifiers.md).) Die Programmiersprache C verwendet die folgenden Schlüsselwörter:

:::row:::
    :::column:::
        **`auto`**\
        **`double`**\
        **`int`**\
        **`struct`**\
        **`break`**\
        **`else`**\
        **`long`**\
        **`switch`**
    :::column-end:::
    :::column:::
        **`case`**\
        **`enum`**\
        **`register`**\
        **`typedef`**\
        **`char`**\
        **`extern`**\
        **`return`**\
        **`union`**
    :::column-end:::
    :::column:::
        **`const`**\
        **`float`**\
        **`short`**\
        **`unsigned`**\
        **`continue`**\
        **`for`**\
        **`signed`**\
        **`void`**
    :::column-end:::
    :::column:::
        **`default`**\
        **`goto`**\
        **`sizeof`**\
        **`volatile`**\
        **`do`**\
        **`if`**\
        **`static`**\
        **`while`**
    :::column-end:::
:::row-end:::

Sie können Schlüsselwörter nicht neu definieren. Bevor Sie mit [C-Präprozessoranweisungen](../preprocessor/preprocessor-directives.md) kompilieren, können Sie jedoch Ersatztext für Schlüsselwörter angeben.

**Microsoft-spezifisch**

Der ANSI C-Standard ermöglicht, dass Bezeichner mit zwei vorangestellten Unterstrichen für Compilerimplementierungen reserviert werden können. Daher werden gemäß Microsoft-Konvention Microsoft-spezifischen Schlüsselwortnamen doppelte Unterstriche vorangestellt. Diese Wörter können nicht als Bezeichnernamen verwendet werden. Eine Beschreibung der ANSI-Regeln für die Benennung von Bezeichnern, einschließlich der Verwendung von doppelten Unterstrichen, finden Sie unter [Bezeichner](../c-language/c-identifiers.md).

Die folgenden Schlüsselwörter und speziellen Bezeichner werden vom Microsoft C-Compiler erkannt:

:::row:::
    :::column:::
        **`__asm`** <sup>3</sup>\
        **`dllimport`** <sup>2</sup>\
        **`__int8`** <sup>3</sup>\
        **`naked`** <sup>2</sup>\
        **`__based`** <sup>1, 3</sup>
    :::column-end:::
    :::column:::
        **`__except`** <sup>3</sup>\
        **`__int16`** <sup>3</sup>\
        **`__stdcall`** <sup>3</sup>\
        **`__cdecl`** <sup>3</sup>\
        **`__fastcall`**
    :::column-end:::
    :::column:::
        **`__int32`** <sup>3</sup>\
        **`thread`** <sup>2</sup>\
        **`__declspec`** <sup>3</sup>\
        **`__finally`** <sup>3</sup>\
        **`__int64`** <sup>3</sup>
    :::column-end:::
    :::column:::
        **`__try`** <sup>3</sup>\
        **`dllexport`** <sup>2</sup>\
        **`__inline`** <sup>3</sup>\
        **`__leave`** <sup>3</sup>
    :::column-end:::
:::row-end:::

<sup>1</sup> Das **`__based`** -Schlüsselwort weist eingeschränkte Verwendung für 32-Bit- und 64-Bit-Zielkompilierungen auf.

<sup>2</sup> Dies sind spezielle Bezeichner, wenn sie mit **`__declspec`** verwendet werden. Ihre Verwendung in anderen Kontexten ist nicht eingeschränkt.

<sup>3</sup> Aus Kompatibilitätsgründen mit früheren Versionen sind diese Schlüsselwörter sowohl mit zwei führenden Unterstrichen als auch mit einem einzigen führenden Unterstrich verfügbar, wenn Microsoft-Erweiterungen aktiviert sind.

Standardmäßig sind Microsoft-Erweiterungen aktiviert. Um sicherzustellen, dass Ihre Programme vollständig portabel sind, können Sie Microsoft-Erweiterungen deaktivieren, indem Sie während der Kompilierung die Option [/Za \(Spracherweiterungen deaktivieren)](../build/reference/za-ze-disable-language-extensions.md) angeben. Dabei werden einige Microsoft-spezifische Schlüsselwörter deaktiviert.

Wenn Microsoft-Erweiterungen aktiviert sind, können Sie in den Programmen die oben aufgeführten Schlüsselwörter verwenden. Bei Einhaltung der ANSI-Kompatibilität wird den meisten dieser Schlüsselwörter ein doppelter Unterstrich vorangestellt. Die vier Ausnahmen **`dllexport`** , **`dllimport`** , **`naked`** und **`thread`** werden nur mit **`__declspec`** verwendet und erfordern deshalb keinen vorangestellten doppelten Unterstrich. Für die Abwärtskompatibilität werden die restlichen Schlüsselwörter mit Versionen mit einem Unterstrich unterstützt.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[C-Elemente](../c-language/elements-of-c.md)

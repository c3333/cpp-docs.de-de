---
title: C-Schlüsselwörter
ms.date: 10/09/2018
helpviewer_keywords:
- keywords [C]
- redefining keywords
- Microsoft-specific keywords
ms.assetid: 2d932335-97bf-45cd-b367-4ae00db0ff42
ms.openlocfilehash: 081235f987d3f6f8dbfd3abb4af9d70688b7fd98
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200711"
---
# <a name="c-keywords"></a>C-Schlüsselwörter

"Schlüsselwörter" sind Wörter, die eine besondere Bedeutung für den C-Compiler haben. In den Übersetzungsphasen 7 und 8 kann ein Bezeichner nicht dieselbe Schreibweise und Groß-/Kleinschreibung haben wie ein C-Schlüsselwort. (Eine Beschreibung der [Übersetzungsphasen](../preprocessor/phases-of-translation.md) finden Sie in der *Präprozessorreferenz*. Informationen zu Bezeichnern finden Sie unter [Bezeichner](../c-language/c-identifiers.md).) Die Programmiersprache C verwendet die folgenden Schlüsselwörter:

:::row:::
    :::column:::
        **`auto`**<br/>
        **`double`**<br/>
        **`int`**<br/>
        **`struct`**<br/>
        **`break`**<br/>
        **`else`**<br/>
        **`long`**<br/>
        **`switch`**<br/>
    :::column-end:::
    :::column:::
        **`case`**<br/>
        **`enum`**<br/>
        **`register`**<br/>
        **`typedef`**<br/>
        **`char`**<br/>
        **`extern`**<br/>
        **`return`**<br/>
        **`union`**<br/>
    :::column-end:::
    :::column:::
        **`const`**<br/>
        **`float`**<br/>
        **`short`**<br/>
        **`unsigned`**<br/>
        **`continue`**<br/>
        **`for`**<br/>
        **`signed`**<br/>
        **`void`**<br/>
    :::column-end:::
    :::column:::
        **`default`**<br/>
        **`goto`**<br/>
        **`sizeof`**<br/>
        **`volatile`**<br/>
        **`do`**<br/>
        **`if`**<br/>
        **`static`**<br/>
        **`while`**<br/>
    :::column-end:::
:::row-end:::

Sie können Schlüsselwörter nicht neu definieren. Bevor Sie mit [C-Präprozessoranweisungen](../preprocessor/preprocessor-directives.md) kompilieren, können Sie jedoch Ersatztext für Schlüsselwörter angeben.

**Microsoft-spezifisch**

Der ANSI C-Standard ermöglicht, dass Bezeichner mit zwei vorangestellten Unterstrichen für Compilerimplementierungen reserviert werden können. Daher werden gemäß Microsoft-Konvention Microsoft-spezifischen Schlüsselwortnamen doppelte Unterstriche vorangestellt. Diese Wörter können nicht als Bezeichnernamen verwendet werden. Eine Beschreibung der ANSI-Regeln für die Benennung von Bezeichnern, einschließlich der Verwendung von doppelten Unterstrichen, finden Sie unter [Bezeichner](../c-language/c-identifiers.md).

Die folgenden Schlüsselwörter und speziellen Bezeichner werden vom Microsoft C-Compiler erkannt:

:::row:::
    :::column:::
        **`__asm`** <sup>3</sup><br/>
        **`dllimport`** <sup>2</sup><br/>
        **`__int8`** <sup>3</sup><br/>
        **`naked`** <sup>2</sup><br/>
        **`__based`** <sup>1, 3</sup><br/>
    :::column-end:::
    :::column:::
        **`__except`** <sup>3</sup><br/>
        **`__int16`** <sup>3</sup><br/>
        **`__stdcall`** <sup>3</sup><br/>
        **`__cdecl`** <sup>3</sup><br/>
        **`__fastcall`**<br/>
    :::column-end:::
    :::column:::
        **`__int32`** <sup>3</sup><br/>
        **`thread`** <sup>2</sup><br/>
        **`__declspec`** <sup>3</sup><br/>
        **`__finally`** <sup>3</sup><br/>
        **`__int64`** <sup>3</sup><br/>
    :::column-end:::
    :::column:::
        **`__try`** <sup>3</sup><br/>
        **`dllexport`** <sup>2</sup><br/>
        **`__inline`** <sup>3</sup><br/>
        **`__leave`** <sup>3</sup><br/>
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

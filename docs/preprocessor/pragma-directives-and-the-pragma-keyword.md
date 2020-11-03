---
title: Pragma-Anweisungen und das __pragma-Schlüsselwort
description: Beschreibt die in Microsoft Visual C und C++ (MSVC) verfügbaren pragma-Direktiven.
ms.date: 10/30/2020
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directives, C/C++'
- __pragma keyword
- pragma directives, C/C++
- pragmas, C/C++
- preprocessor
- pragmas
- preprocessor, pragmas
- pragma directives (#pragma)
ms.assetid: 9867b438-ac64-4e10-973f-c3955209873f
ms.openlocfilehash: bf4bbdcf74808edd8ef54149f8258f47bd94c600
ms.sourcegitcommit: 4abc6c4c9694f91685cfd77940987e29a51e3143
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2020
ms.locfileid: "93238407"
---
# <a name="pragma-directives-and-the-__pragma-keyword"></a>Pragma-Anweisungen und das __pragma-Schlüsselwort

Pragma-Direktiven geben Computer-oder betriebssystemspezifische Compilerfunktionen an. Das **__Pragma** -Schlüsselwort, das für den Microsoft-Compiler spezifisch ist, ermöglicht das Codieren von pragma-Direktiven innerhalb von Makro Definitionen.

## <a name="syntax"></a>Syntax

> **#`pragma`***Tokenzeichenfolge*\
> **`__pragma(`***Tokenzeichenfolge* **`)`** zwei führende Unterstriche: Microsoft-spezifische Erweiterungs **`_Pragma(`** *Zeichenfolge-Literale* **`)`** //C99

## <a name="remarks"></a>Hinweise

Jede Implementierung von C und C++ unterstützt mehrere Funktionen, die auf dem Hostcomputer oder Betriebssystem einzigartig sind. Einige Programme müssen z. b. eine genaue Kontrolle über den Speicherort der Daten im Arbeitsspeicher oder die Art und Weise steuern, wie bestimmte Funktionen Parameter erhalten. Die **#pragma** -Direktiven bieten jedem Compiler die Möglichkeit, Computer-und betriebssystemspezifische Funktionen bereitzustellen und gleichzeitig die Gesamt Kompatibilität mit den Programmiersprachen C und C++ aufrechtzuerhalten.

Pragmas sind definitionsgemäß Computer-oder betriebssystemspezifisch und unterscheiden sich in der Regel für jeden Compiler. Pragmas können in bedingten Direktiven verwendet werden, um neue präprozessorfunktionen bereitzustellen oder um Implementierungs definierte Informationen für den Compiler bereitzustellen.

Die *Tokenzeichenfolge* ist eine Reihe von Zeichen, die eine bestimmte Compileranweisung und Argumente darstellen, sofern vorhanden. Das Nummern Zeichen ( **#** ) muss das erste Zeichen, das kein Leerzeichen ist, in der Zeile sein, die das Pragma enthält. Leerzeichen können das Nummern Zeichen und das Wort "Pragma" trennen. Schreiben Sie nach **#pragma** den Text, den der Konvertierer als Vorverarbeitungs Token analysieren kann. Das Argument für **#pragma** unterliegt der Makro Erweiterung.

Die *Zeichenfolgenliterale* ist die Eingabe für `_Pragma` . Äußere Anführungszeichen und führende/nachfolgende Leerzeichen werden entfernt. `\"` wird durch ersetzt `"` und `\\` wird durch ersetzt `\` .

Der Compiler gibt eine Warnung aus, wenn ein Pragma gefunden wird, das nicht erkannt wird, und setzt die Kompilierung fort.

Die Microsoft C- und C++-Compiler erkennen die folgenden Pragmas:

:::row:::
   :::column span="":::
      [`alloc_text`](../preprocessor/alloc-text.md)\
      [`auto_inline`](../preprocessor/auto-inline.md)\
      [`bss_seg`](../preprocessor/bss-seg.md)\
      [`check_stack`](../preprocessor/check-stack.md)\
      [`code_seg`](../preprocessor/code-seg.md)\
      [`comment`](../preprocessor/comment-c-cpp.md)\
      [`component`](../preprocessor/component.md)\
      [`conform`](../preprocessor/conform.md)<sup>1</sup>\
      [`const_seg`](../preprocessor/const-seg.md)\
      [`data_seg`](../preprocessor/data-seg.md)\
      [`deprecated`](../preprocessor/deprecated-c-cpp.md)
   :::column-end:::
   :::column span="":::
      [`detect_mismatch`](../preprocessor/detect-mismatch.md)\
      [`fenv_access`](../preprocessor/fenv-access.md)\
      [`float_control`](../preprocessor/float-control.md)\
      [`fp_contract`](../preprocessor/fp-contract.md)\
      [`function`](../preprocessor/function-c-cpp.md)\
      [`hdrstop`](../preprocessor/hdrstop.md)\
      [`include_alias`](../preprocessor/include-alias.md)\
      [`init_seg`](../preprocessor/init-seg.md)<sup>1</sup>\
      [`inline_depth`](../preprocessor/inline-depth.md)\
      [`inline_recursion`](../preprocessor/inline-recursion.md)
   :::column-end:::
   :::column span="":::
      [`intrinsic`](../preprocessor/intrinsic.md)\
      [`loop`](../preprocessor/loop.md)<sup>1</sup>\
      [`make_public`](../preprocessor/make-public.md)\
      [`managed`](../preprocessor/managed-unmanaged.md)\
      [`message`](../preprocessor/message.md)\
      [`omp`](../preprocessor/omp.md)\
      [`once`](../preprocessor/once.md)\
      [`optimize`](../preprocessor/optimize.md)\
      [`pack`](../preprocessor/pack.md)\
      [`pointers_to_members`](../preprocessor/pointers-to-members.md)<sup>1</sup>
   :::column-end:::
   :::column span="":::
      [`pop_macro`](../preprocessor/pop-macro.md)\
      [`push_macro`](../preprocessor/push-macro.md)\
      [`region`, endregion](../preprocessor/region-endregion.md)\
      [`runtime_checks`](../preprocessor/runtime-checks.md)\
      [`section`](../preprocessor/section.md)\
      [`setlocale`](../preprocessor/setlocale.md)\
      [`strict_gs_check`](../preprocessor/strict-gs-check.md)\
      [`unmanaged`](../preprocessor/managed-unmanaged.md)\
      [`vtordisp`](../preprocessor/vtordisp.md)<sup>1</sup>\
      [`warning`](../preprocessor/warning.md)
   :::column-end:::
:::row-end:::

<sup>1</sup> wird nur vom C++-Compiler unterstützt.

## <a name="pragmas-and-compiler-options"></a>Pragmas und Compileroptionen

Einige Pragmas stellen die gleichen Funktionen wie Compileroptionen bereit. Wenn im Quellcode ein Pragma gefunden wird, überschreibt dieses das Verhalten, das mit der Compileroption angegeben wird. Wenn Sie z. b. [/Zp8](../build/reference/zp-struct-member-alignment.md)angegeben haben, können Sie Diese Compilereinstellung für bestimmte Abschnitte des Codes mit [Pack](../preprocessor/pack.md)überschreiben:

```cmd
cl /Zp8 some_file.cpp
```

```cpp
// some_file.cpp - packing is 8
// ...
#pragma pack(push, 1) - packing is now 1
// ...
#pragma pack(pop) - packing is 8 again
// ...
```

## <a name="the-__pragma-keyword"></a>Das __Pragma ()-Schlüsselwort

Der Compiler unterstützt auch das Microsoft-spezifische **`__pragma`** Schlüsselwort, das über die gleiche Funktionalität wie die **`#pragma`** Direktive verfügt. Der Unterschied besteht darin, dass das- **`__pragma`** Schlüsselwort Inline in einer Makro Definition verwendet werden kann. Die- **`#pragma`** Direktive kann nicht in einer Makro Definition verwendet werden, da der Compiler das Nummern Zeichen (' # ') in der Direktive als Zeichen folgen [Operator (#)](../preprocessor/stringizing-operator-hash.md)interpretiert.

Im folgenden Codebeispiel wird veranschaulicht, wie das- **`__pragma`** Schlüsselwort in einem Makro verwendet werden kann. Dieser Code wird aus dem *mfcdual. h* -Header im ACDUAL-Beispiel in "Compiler com-Support Beispiele" entnommen:

```cpp
#define CATCH_ALL_DUAL \
CATCH(COleException, e) \
{ \
_hr = e->m_sc; \
} \
AND_CATCH_ALL(e) \
{ \
__pragma(warning(push)) \
__pragma(warning(disable:6246)) /*disable _ctlState prefast warning*/ \
AFX_MANAGE_STATE(pThis->m_pModuleState); \
__pragma(warning(pop)) \
_hr = DualHandleException(_riidSource, e); \
} \
END_CATCH_ALL \
return _hr; \
```

## <a name="the-_pragma-preprocessing-operator-c99-c11"></a>Der `_Pragma` Vorverarbeitungs Operator (C99, c++ 11)

`_Pragma` ähnelt dem Microsoft-spezifischen [`__pragma`](#the-__pragma-keyword) Schlüsselwort, mit dem Unterschied, dass es Teil des Standards ist. Es wurde für C in C99 eingeführt. Für C++ wurde es in C++ 11 eingeführt.

 Sie können Pragmas in eine Makro Definition einfügen. Es verfügt über einen führenden Unterstrich `_` anstelle von zwei führenden unterstrichen, `__` dass das Microsoft-spezifische Schlüsselwort hat und der erste Buchstabe groß geschrieben ist.

Der Zeichenfolgenliteralwert sollte nach einer-Anweisung anderweitig eingefügt werden *`#pragma`* . Beispiel:

```c
#pragma message("--the #pragma way")
_Pragma ("message( \"the _Pragma way\")") 
```

Anführungszeichen und Rückstriche sollten mit Escapezeichen versehen werden, wie oben gezeigt. Eine pragma-Zeichenfolge, die nicht erkannt wird, wird ignoriert.

Im folgenden Codebeispiel wird veranschaulicht, wie das- **`_Pragma`** Schlüsselwort in einem Assert-ähnlichen Makro verwendet werden kann, wenn Sie keine Warnung erhalten möchten, wenn der Bedingungs Ausdruck konstant ist. 

Die Makro Definition verwendet die do/while (0)-Ausdrucksweise für Makros mit mehreren Anweisungen, sodass Sie so verwendet werden kann, als ob es sich um eine Anweisung handelt. Weitere Informationen finden Sie unter [C-Multiline-Makro](https://stackoverflow.com/questions/1067226/c-multi-line-macro-do-while0-vs-scope-block) auf Stack Overflow. Die _Pragma-Anweisung gilt nur für die Codezeile, die darauf folgt.

```C
// Compile with /W4

#include <stdio.h>
#include <stdlib.h>

#define MY_ASSERT(BOOL_EXPRESSION) \
    do { \
        _Pragma("warning(suppress: 4127)") /* C4127 conditional expression is constant */  \
        if (!(BOOL_EXPRESSION)) {   \
            printf("MY_ASSERT FAILED: \"" #BOOL_EXPRESSION "\" on %s(%d)", __FILE__, __LINE__); \
            exit(-1); \
        } \
    } while (0)

int main()
{
    MY_ASSERT(0 && "Note that there is no warning: C4127 conditional expression is constant");

    return 0;
}
```

## <a name="see-also"></a>Weitere Informationen:

[C/C++-präprozessorverweis](../preprocessor/c-cpp-preprocessor-reference.md)\
[C-Pragmas](../c-language/c-pragmas.md)\
[Schlüsselwörter](../cpp/keywords-cpp.md)

---
title: Pragma-Anweisungen und das __pragma-Schlüsselwort
ms.date: 08/29/2019
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
ms.openlocfilehash: 786f76d9f7fd2eee73c6b1d009186bf93ea0c667
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88842688"
---
# <a name="pragma-directives-and-the-__pragma-keyword"></a>Pragma-Anweisungen und das __pragma-Schlüsselwort

Pragma-Direktiven geben Computer-oder betriebssystemspezifische Compilerfunktionen an. Das **__Pragma** -Schlüsselwort, das für den Microsoft-Compiler spezifisch ist, ermöglicht das Codieren von pragma-Direktiven innerhalb von Makro Definitionen.

## <a name="syntax"></a>Syntax

> **#pragma** *Tokenzeichenfolge*\
> **__Pragma (** *Tokenzeichenfolge* **)**

## <a name="remarks"></a>Bemerkungen

Jede Implementierung von C und C++ unterstützt mehrere Funktionen, die auf dem Hostcomputer oder Betriebssystem einzigartig sind. Einige Programme müssen z. b. eine genaue Kontrolle über den Speicherort der Daten im Arbeitsspeicher oder die Art und Weise steuern, wie bestimmte Funktionen Parameter erhalten. Die **#pragma** -Direktiven bieten jedem Compiler die Möglichkeit, Computer-und betriebssystemspezifische Funktionen bereitzustellen und gleichzeitig die Gesamt Kompatibilität mit den Programmiersprachen C und C++ aufrechtzuerhalten.

Pragmas sind definitionsgemäß Computer-oder betriebssystemspezifisch und unterscheiden sich in der Regel für jeden Compiler. Pragmas können in bedingten Direktiven verwendet werden, um neue präprozessorfunktionen bereitzustellen oder um Implementierungs definierte Informationen für den Compiler bereitzustellen.

Die *Tokenzeichenfolge* ist eine Reihe von Zeichen, die eine bestimmte Compileranweisung und Argumente (sofern vorhanden) enthalten. Das Nummern Zeichen ( **#** ) muss das erste Zeichen, das kein Leerzeichen ist, in der Zeile sein, die das Pragma enthält. Leerzeichen können das Nummern Zeichen und das Wort "Pragma" trennen. Schreiben Sie nach **#pragma**den Text, den der Konvertierer als Vorverarbeitungs Token analysieren kann. Das Argument für **#pragma** unterliegt der Makro Erweiterung.

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

Der Compiler unterstützt auch das Microsoft-spezifische **__Pragma** -Schlüsselwort, das über die gleiche Funktionalität wie die **#pragma** -Direktive verfügt. Der Unterschied besteht darin, dass das **__Pragma** -Schlüsselwort Inline in einer Makro Definition verwendet werden kann. Die **#pragma** -Direktive kann nicht in einer Makro Definition verwendet werden, da der Compiler das Nummern Zeichen (' # ') in der Direktive als Zeichen folgen [Operator (#)](../preprocessor/stringizing-operator-hash.md)interpretiert.

Im folgenden Codebeispiel wird veranschaulicht, wie das **__Pragma** -Schlüsselwort in einem Makro verwendet werden kann. Dieser Code wurde dem mfcdual.h-Header im ACDUAL-Beispiel in den Beispielen für die COM-Unterstützung des Compilers entnommen:

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

## <a name="see-also"></a>Weitere Informationen

[C/C++-präprozessorverweis](../preprocessor/c-cpp-preprocessor-reference.md)\
[C-Pragmas](../c-language/c-pragmas.md)\
[Schlüsselwörter](../cpp/keywords-cpp.md)

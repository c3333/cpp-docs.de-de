---
title: intrinsic-Pragma
description: Mithilfe des systeminternen MSVC-Pragmas werden die unterstützten intrinsischen Funktionen angegeben, die als systeminterne Funktionen verwendet werden sollen.
ms.date: 07/08/2020
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
helpviewer_keywords:
- intrinsic pragma
- pragmas, intrinsic
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
ms.openlocfilehash: 45a5a13f3bda3657b93e1a89e7a842a4465b01d5
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041106"
---
# <a name="intrinsic-pragma"></a>`intrinsic`-Pragma

Gibt an, dass Funktionsaufrufe, die in der Argumentliste des Pragmas angegeben sind, systemintern sind.

## <a name="syntax"></a>Syntax

> **`#pragma intrinsic(`** *`function1`* [**`,`** _`function2`_ ... ] **`)`**

## <a name="remarks"></a>Bemerkungen

Das **`intrinsic`** pragma weist den Compiler an, dass eine Funktion ein bekanntes Verhalten aufweist. Der Compiler kann die Funktion aufrufen und den Funktionsaufruf nicht durch Inlineanweisungen ersetzen, wenn dies zu einer besseren Leistung führt.

Die Bibliotheksfunktionen mit systeminternen Formularen werden nachfolgend aufgeführt. Sobald ein **`intrinsic`** Pragma angezeigt wird, tritt es bei der ersten Funktionsdefinition in Kraft, die eine bestimmte intrinsische Funktion enthält. Der Effekt wird bis zum Ende der Quelldatei oder bis zum Aussehen eines Pragmas fortgesetzt, `function` das die gleiche intrinsische Funktion angibt. Das **`intrinsic`** pragma kann nur außerhalb einer Funktionsdefinition auf globaler Ebene verwendet werden.

Die folgenden Funktionen verfügen über intrinsische Formulare, und die systeminternen Formulare werden verwendet, wenn Sie Folgendes angeben [`/Oi`](../build/reference/oi-generate-intrinsic-functions.md) :

:::row:::
   :::column span="":::
      [`abs`](../c-runtime-library/reference/abs-labs-llabs-abs64.md)\
      [`_disable`](../intrinsics/disable.md)\
      [`_enable`](../intrinsics/enable.md)\
      [`fabs`](../c-runtime-library/reference/fabs-fabsf-fabsl.md)\
      [`_inp`](../c-runtime-library/inp-inpw-inpd.md)\
      [`_inpw`](../c-runtime-library/inp-inpw-inpd.md)\
   :::column-end:::
   :::column span="":::
      [`labs`](../c-runtime-library/reference/abs-labs-llabs-abs64.md)\
      [`_lrotl`](../c-runtime-library/reference/lrotl-lrotr.md)\
      [`_lrotr`](../c-runtime-library/reference/lrotl-lrotr.md)\
      [`memcmp`](../c-runtime-library/reference/memcmp-wmemcmp.md)\
      [`memcpy`](../c-runtime-library/reference/memcpy-wmemcpy.md)\
   :::column-end:::
   :::column span="":::
      [`memset`](../c-runtime-library/reference/memset-wmemset.md)\
      [`_outp`](../c-runtime-library/outp-outpw-outpd.md)\
      [`_outpw`](../c-runtime-library/outp-outpw-outpd.md)\
      [`_rotl`](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)\
      [`_rotr`](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)\
   :::column-end:::
   :::column span="":::
      [`strcat`](../c-runtime-library/reference/strcat-wcscat-mbscat.md)\
      [`strcmp`](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)\
      [`strcpy`](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)\
      [`strlen`](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)\
      [`_strset`](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)\
   :::column-end:::
:::row-end:::

Programme, die intrinsische Funktionen verwenden, sind schneller, da Sie nicht den mehr Aufwand von Funktionsaufrufen haben. Sie sind jedoch möglicherweise aufgrund des generierten zusätzlichen Codes größer.

### <a name="x86-specific-example"></a>x86-spezifisches Beispiel

Die systeminternen Funktionen `_disable` und `_enable` generieren kernelmodusanweisungen, um Interrupts zu deaktivieren oder zu aktivieren, und könnten in Kernelmodustreibern nützlich sein.

Kompilieren Sie den folgenden Code über die Befehlszeile mit, `cl -c -FAs sample.c` und *`sample.asm`* sehen Sie sich an, dass Sie sich in die x86-Anweisungen CLI und STI umwandeln:

```cpp
// pragma_directive_intrinsic.cpp
// processor: x86
#include <dos.h>   // definitions for _disable, _enable
#pragma intrinsic(_disable)
#pragma intrinsic(_enable)
void f1(void) {
   _disable();
   // do some work here that should not be interrupted
   _enable();
}
int main() {
}
```

### <a name="intrinsic-floating-point-functions"></a>Intrinsische Gleit Komma Funktionen

Diese Gleit Komma Funktionen weisen keine echten systeminternen Formen auf. Stattdessen verfügen Sie über Versionen, die Argumente direkt an den Gleit Komma Chip übergeben, anstatt Sie per Push auf den Stapel zu übertragen:

:::row:::
   :::column span="":::
      [`acos`](../c-runtime-library/reference/acos-acosf-acosl.md)\
      [`asin`](../c-runtime-library/reference/asin-asinf-asinl.md)\
   :::column-end:::
   :::column span="":::
      [`cosh`](../c-runtime-library/reference/cosh-coshf-coshl.md)\
      [`fmod`](../c-runtime-library/reference/fmod-fmodf.md)\
   :::column-end:::
   :::column span="":::
      [`pow`](../c-runtime-library/reference/pow-powf-powl.md)\
      [`sinh`](../c-runtime-library/reference/sinh-sinhf-sinhl.md)\
   :::column-end:::
   :::column span="":::
      [`tanh`](../c-runtime-library/reference/tanh-tanhf-tanhl.md)\
   :::column-end:::
:::row-end:::

Diese Gleit Komma Funktionen verfügen über echte intrinsische Formen, wenn Sie [`/Oi`](../build/reference/oi-generate-intrinsic-functions.md) und angeben [`/fp:fast`](../build/reference/fp-specify-floating-point-behavior.md) (oder eine Option, die Folgendes umfasst: **`/Oi`** [`/Ox`](../build/reference/ox-full-optimization.md) , [`/O1`](../build/reference/o1-o2-minimize-size-maximize-speed.md) und [`/O2`](../build/reference/o1-o2-minimize-size-maximize-speed.md) ):

:::row:::
   :::column span="":::
      [`atan`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)\
      [`atan2`](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)\
      [`cos`](../c-runtime-library/reference/cos-cosf-cosl.md)\
   :::column-end:::
   :::column span="":::
      [`exp`](../c-runtime-library/reference/exp-expf.md)\
      [`log`](../c-runtime-library/reference/log-logf-log10-log10f.md)\
   :::column-end:::
   :::column span="":::
      [`log10`](../c-runtime-library/reference/log-logf-log10-log10f.md)\
      [`sin`](../c-runtime-library/reference/sin-sinf-sinl.md)\
   :::column-end:::
   :::column span="":::
      [`sqrt`](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)\
      [`tan`](../c-runtime-library/reference/tan-tanf-tanl.md)\
   :::column-end:::
:::row-end:::

Sie können [`/fp:strict`](../build/reference/fp-specify-floating-point-behavior.md) oder verwenden [`/Za`](../build/reference/za-ze-disable-language-extensions.md) , um die Generierung von echten systeminternen Gleit Komma Optionen zu überschreiben. In diesem Fall werden die Funktionen als Bibliotheksroutinen erzeugt, die Argumente direkt an den Gleitkommachip übergeben, statt sie auf dem Programmstapel abzulegen.

Weitere [`#pragma function`](../preprocessor/function-c-cpp.md) Informationen und ein Beispiel zum Aktivieren und Deaktivieren von systeminternen Funktionen für einen Quell Text Block finden Sie unter.

## <a name="see-also"></a>Weitere Informationen

[Pragma-Direktiven und das `__pragma` Schlüsselwort](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[Intrinsische Compilerfunktionen](../intrinsics/compiler-intrinsics.md)

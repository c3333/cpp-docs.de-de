---
title: _controlfp_s
ms.date: 4/2/2020
api_name:
- _controlfp_s
- _o__controlfp_s
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- controlfp_s
- _controlfp_s
helpviewer_keywords:
- floating-point numbers, control word
- controlfp_s function
- floating-point functions, setting control word
- EM_AMBIGUOUS
- _controlfp_s function
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
ms.openlocfilehash: 0e734a0286ac21ed0883cc10b0cd4ee5857ba448
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917262"
---
# <a name="_controlfp_s"></a>_controlfp_s

Ruft das Gleitkommasteuerwort ab und legt es fest. Diese Version von [_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md) enthält Sicherheitsverbesserungen wie unter [Sicherheitsfunktionen in der CRT](../../c-runtime-library/security-features-in-the-crt.md) beschrieben.

## <a name="syntax"></a>Syntax

```C
errno_t _controlfp_s(
    unsigned int *currentControl,
    unsigned int newControl,
    unsigned int mask
);
```

### <a name="parameters"></a>Parameter

*CurrentControl*<br/>
Der aktuelle Bitwert des Steuerworts.

*newControl*<br/>
Neue Bitwerte des Steuerworts.

*mask*<br/>
Maske für festzulegende neue Steuerwortbits.

## <a name="return-value"></a>Rückgabewert

NULL, wenn erfolgreich, oder ein Fehlercode des **errno** -Werts.

## <a name="remarks"></a>Hinweise

Die **_controlfp_s** -Funktion ist eine plattformunabhängige und sicherere Version von **_control87**, die das Gleit Komma Steuerwort in die Adresse abruft, die in *CurrentControl* gespeichert ist, und Sie mithilfe von *newControl*festgelegt wird. Die Bits in den Werten geben den Zustand des Gleitkommasteuerelements an. Mit dem Zustand des Gleitkommasteuerelements kann das Programm die Genauigkeits-, Rundungs- und Unendlichkeitsmodi im mathematischen Gleitkommapaket je nach Plattform ändern. Sie können auch **_controlfp_s** verwenden, um Gleit Komma Ausnahmen zu maskieren bzw. die Maskierung aufzuheben.

Wenn der Wert für *Mask* gleich 0 ist, ruft **_controlfp_s** das Gleit Komma Steuerwort ab und speichert den abgerufenen Wert in *CurrentControl*.

Wenn *Mask* ungleich NULL ist, wird ein neuer Wert für das Steuerwort festgelegt: für jedes festgelegte Bit (d. h. gleich 1) in der *Maske*wird das entsprechende Bit in *New* verwendet, um das Steuerwort zu aktualisieren. Anders ausgedrückt: *fpcntrl* = ((*fpcntrl* & ~*Mask*) &#124; (*newControl* & *Mask*)), wobei *fpcntrl* das Gleit Komma Steuerwort ist. In diesem Szenario wird *CurrentControl* auf den Wert festgelegt, nachdem die Änderung abgeschlossen wurde. Es ist nicht der alte Bitwert des Steuer Worts.

> [!NOTE]
> Standardmäßig maskieren die Laufzeitbibliotheken alle Gleitkommaausnahmen.

**_controlfp_s** ist nahezu identisch mit der **_control87** -Funktion auf Intel (x86)-, x64-und Arm-Plattformen. Wenn Sie auf x86-, x64-oder arm-Plattformen abzielen, können Sie **_control87** oder **_controlfp_s**verwenden.

Der Unterschied zwischen **_control87** und **_controlfp_s** liegt darin, wie Sie DENORMAL-Werte behandeln. Bei Intel (x86)-, x64-und Arm-Plattformen können **_control87** die DENORMAL-OPERAND-Ausnahme Maske festlegen und löschen. **_controlfp_s** ändert nicht die DENORMAL-OPERAND-Ausnahme Maske. Dieses Beispiel veranschaulicht den Unterschied:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

Die möglichen Werte für die Masken Konstante (*Maske*) und die neuen Steuerelement Werte (*newControl*) werden in der folgenden hexadezimal Wertetabelle angezeigt. Verwenden Sie die unten aufgeführten portablen Konstanten (**_MCW_EM**, **_EM_INVALID**usw.) als Argumente für diese Funktionen, anstatt die hexadezimalen Werte explizit anzugeben.

Von Intel (x86) abgeleitete Plattformen unterstützen die DENORMAL-Eingabe- und -Ausgabewerte in der Hardware. Das x86-Verhalten besteht darin, die DENORMAL-Werte beizubehalten. Die ARM-Plattform und die x64-Plattformen mit SSE2-Unterstützung ermöglichen es, dass DENORMAL-Operanden und-Ergebnisse geleert oder auf 0 (null) erzwungen werden. Die Funktionen **_controlfp_s**, **_controlfp**und **_control87** stellen eine Maske zum Ändern dieses Verhaltens bereit. Das folgende Beispiel veranschaulicht die Verwendung dieser Maske:

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Auf Arm-Plattformen gilt die **_controlfp_s** -Funktion für das fpscr-Register. In x64-Architekturen ist nur das SSE2-Steuerwort, das im MXCSR-Register gespeichert ist, betroffen. Auf Intel (x86)-Plattformen wirkt sich **_controlfp_s** auf die Steuer Wörter sowohl für x87 als auch für SSE2, falls vorhanden. Es ist möglich, dass die beiden Steuer Wörter inkonsistent sind (z. b. aufgrund eines vorherigen Aufrufes [__control87_2](control87-controlfp-control87-2.md)). Wenn eine Inkonsistenz zwischen den beiden Steuer Wörtern vorliegt, legt **_controlfp_s** das **EM_AMBIGUOUS** -Flag in *CurrentControl*fest. Dies ist eine Warnung, dass das zurückgegebene Steuerwort den Zustand beider Gleitkommasteuerworte möglicherweise nicht genau dargestellt.

Auf der Arm-und x64-Architektur wird das Ändern des unendlichen Modus oder der Gleit Komma Genauigkeit nicht unterstützt. Wenn die Genauigkeits Steuer Maske auf der x64-Plattform verwendet wird, löst die Funktion eine-Assertion aus, und der Handler für ungültige Parameter wird aufgerufen, wie in [Parameter Validierung](../../c-runtime-library/parameter-validation.md)beschrieben.

Wenn die Maske nicht ordnungsgemäß festgelegt ist, generiert diese Funktion eine Ausnahme wegen eines ungültigen Parameters, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die weitere Ausführung zugelassen wird, gibt diese Funktion **EINVAL** zurück und legt **errno** auf **EINVAL**fest.

Diese Funktion wird ignoriert, wenn Sie [/CLR (Common Language Runtime-Kompilierung)](../../build/reference/clr-common-language-runtime-compilation.md) für die Kompilierung verwenden, da die Common Language Runtime (CLR) nur die standardmäßige Gleit Komma Genauigkeit unterstützt.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

### <a name="mask-constants-and-values"></a>Konstanten und Werte maskieren

Beim Löschen der **_MCW_EM** Maske wird die Ausnahme festgelegt, was die Hardware Ausnahme zulässt. durch das festlegen wird die Ausnahme ausgeblendet. Wenn ein **_EM_UNDERFLOW** oder **_EM_OVERFLOW** auftritt, wird keine Hardware Ausnahme ausgelöst, bis die nächste Gleit Komma Anweisung ausgeführt wird. Um eine Hardware Ausnahme direkt nach **_EM_UNDERFLOW** oder **_EM_OVERFLOW**zu generieren, rufen Sie die FWAIT MASM-Anweisung auf.

|Mask|Farbtonwert|Konstante|Farbtonwert|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (DENORMAL-Steuerelement)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (Unterbrechungs Ausnahme Maske)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (unendlich-Steuerelement)<br /><br /> (Wird auf Arm-oder x64-Plattformen nicht unterstützt.)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (Rundungs Steuerung)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (Genauigkeits Steuerung)<br /><br /> (Wird auf Arm-oder x64-Plattformen nicht unterstützt.)|0x00030000|**_PC_24** (24 Bits)<br /><br /> **_PC_53** (53 Bits)<br /><br /> **_PC_64** (64 Bits)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_controlfp_s**|\<float.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Beispiel

```C
// crt_contrlfp_s.c
// processor: x86
// This program uses _controlfp_s to output the FP control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word;
    int err;

    // Show original FP control word and do calculation.
    err = _controlfp_s(&control_word, 0, 0);
    if ( err ) /* handle error here */;

    printf( "Original: 0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    err = _controlfp_s(&control_word, _PC_24, MCW_PC);
    if ( err ) /* handle error here */;

    printf( "24-bit:   0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    err = _controlfp_s(&control_word, _CW_DEFAULT, MCW_PC);
    if ( err ) /* handle error here */;

    printf( "Default:  0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x9001f
0.1 * 0.1 = 1.000000000000000e-002
24-bit:   0xa001f
0.1 * 0.1 = 9.999999776482582e-003
Default:  0x9001f
0.1 * 0.1 = 1.000000000000000e-002
```

## <a name="see-also"></a>Weitere Informationen

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>

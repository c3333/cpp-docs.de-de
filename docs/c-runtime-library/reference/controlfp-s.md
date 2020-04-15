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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 4b36cc9f5ed83b68cb15c39be91165ed7aa86d7b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348534"
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

*currentControl*<br/>
Der aktuelle Bitwert des Steuerworts.

*newControl*<br/>
Neue Bitwerte des Steuerworts.

*mask*<br/>
Maske für festzulegende neue Steuerwortbits.

## <a name="return-value"></a>Rückgabewert

Null, wenn erfolgreich, oder ein Fehlercode für **einen Errno-Wert.**

## <a name="remarks"></a>Bemerkungen

Die **_controlfp_s-Funktion** ist eine plattformunabhängige und sicherere Version von **_control87**, die das Gleitkomma-Steuerwort in die in *currentControl* gespeicherte Adresse abruft und mit *newControl*festlegt. Die Bits in den Werten geben den Zustand des Gleitkommasteuerelements an. Mit dem Zustand des Gleitkommasteuerelements kann das Programm die Genauigkeits-, Rundungs- und Unendlichkeitsmodi im mathematischen Gleitkommapaket je nach Plattform ändern. Sie können **auch _controlfp_s** verwenden, um Gleitkommaausnahmen zu maskieren oder zu entlarven.

Wenn der Wert für *Maske* gleich 0 ist, ruft **_controlfp_s** das Gleitkomma-Steuerwort ab und speichert den abgerufenen Wert in *currentControl*.

Wenn *die Maske* ungleich Null ist, wird ein neuer Wert für das Steuerwort gesetzt: Für jedes Bit, das in der *Maske*festgelegt ist (d. h. gleich 1), wird das entsprechende Bit in *new* verwendet, um das Steuerwort zu aktualisieren. Mit anderen Worten, *fpcntrl* = ((*fpcntrl* & -*Maske*) &#124; (*newControl-Maske* & *mask*)), wobei *fpcntrl* das Gleitkomma-Steuerwort ist. In diesem Szenario wird *currentControl* nach Abschluss der Änderung auf den Wert festgelegt. es ist nicht der alte Steuerelement-Wort-Bitwert.

> [!NOTE]
> Standardmäßig maskieren die Laufzeitbibliotheken alle Gleitkommaausnahmen.

**_controlfp_s** ist nahezu identisch mit der **_control87-Funktion** auf Intel (x86), x64 und ARM-Plattformen. Wenn Sie auf x86-, x64- oder ARM-Plattformen abzielen, können Sie **_control87** oder **_controlfp_s**verwenden.

Der Unterschied zwischen **_control87** und **_controlfp_s** besteht darin, wie sie denormale Werte behandeln. Für Intel (x86), x64- und ARM-Plattformen können **_control87** die DENORMAL OPERAND-Ausnahmemaske festlegen und löschen. **_controlfp_s** ändert die DENORMAL OPERAND-Ausnahmemaske nicht. Dieses Beispiel veranschaulicht den Unterschied:

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

Die möglichen Werte für die Maskenkonstante (*Maske*) und neue Steuerwerte (*newControl*) werden in der folgenden Tabelle Hexadezimale Werte angezeigt. Verwenden Sie die unten aufgeführten portablen Konstanten (**_MCW_EM**, **_EM_INVALID**usw.) als Argumente für diese Funktionen, anstatt die hexadezimalen Werte explizit einzuliefern.

Von Intel (x86) abgeleitete Plattformen unterstützen die DENORMAL-Eingabe- und -Ausgabewerte in der Hardware. Das x86-Verhalten besteht darin, die DENORMAL-Werte beizubehalten. Die ARM-Plattform und die x64-Plattformen mit SSE2-Unterstützung ermöglichen es, DENORMAL-Operanden und -Ergebnisse zu spülen oder auf Null zu zwingen. Die Funktionen **_controlfp_s**, **_controlfp**und **_control87** stellen eine Maske bereit, um dieses Verhalten zu ändern. Das folgende Beispiel veranschaulicht die Verwendung dieser Maske:

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

Auf ARM-Plattformen gilt die **_controlfp_s-Funktion** für das FPSCR-Register. Bei x64-Architekturen ist nur das im MXCSR-Register gespeicherte SSE2-Steuerwort betroffen. Auf Intel (x86)-Plattformen wirkt sich **_controlfp_s** auf die Steuerwörter sowohl für x87 als auch für SSE2 aus, sofern vorhanden. Es ist möglich, dass die beiden Steuerwörter nicht miteinander übereinstimmen (z. B. aufgrund eines vorherigen Aufrufs zu [__control87_2);](control87-controlfp-control87-2.md) Wenn eine Inkonsistenz zwischen den beiden Steuerwörtern vorliegt, **legt _controlfp_s** das **EM_AMBIGUOUS-Flag** in *currentControl*fest. Dies ist eine Warnung, dass das zurückgegebene Steuerwort den Zustand beider Gleitkommasteuerworte möglicherweise nicht genau dargestellt.

Bei den ARM- und x64-Architekturen wird das Ändern des Unendlichkeitsmodus oder der Gleitkommagenauigkeit nicht unterstützt. Wenn die Präzisionssteuerungsmaske auf der x64-Plattform verwendet wird, löst die Funktion eine Assertion aus, und der ungültige Parameterhandler wird aufgerufen, wie unter [Parametervalidierung](../../c-runtime-library/parameter-validation.md)beschrieben.

Wenn die Maske nicht ordnungsgemäß festgelegt ist, generiert diese Funktion eine Ausnahme wegen eines ungültigen Parameters, wie in [Parametervalidierung](../../c-runtime-library/parameter-validation.md) beschrieben. Wenn die Ausführung fortgesetzt werden darf, gibt diese Funktion **EINVAL** zurück und setzt **errno** auf **EINVAL**.

Diese Funktion wird ignoriert, wenn Sie [/clr (Common Language Runtime Compilation)](../../build/reference/clr-common-language-runtime-compilation.md) zum Kompilieren verwenden, da die Common Language Runtime (CLR) nur die standardmäßige Gleitkommagenauigkeit unterstützt.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

### <a name="mask-constants-and-values"></a>Maskenkonstanten und -werte

Für die **_MCW_EM** Maske legt das Löschen die Ausnahme fest, die die Hardwareausnahme zulässt. Durch festlegen, wird die Ausnahme ausgeblendet. Wenn ein **_EM_UNDERFLOW** oder **_EM_OVERFLOW** auftritt, wird keine Hardwareausnahme ausgelöst, bis die nächste Gleitkommaanweisung ausgeführt wird. Um eine Hardwareausnahme unmittelbar nach **_EM_UNDERFLOW** oder **_EM_OVERFLOW**zu generieren, rufen Sie die FWAIT MASM-Anweisung auf.

|Mask|Farbtonwert|Konstante|Farbtonwert|
|----------|---------------|--------------|---------------|
|**_MCW_DN** (Denormal-Steuerung)|0x03000000|**_DN_SAVE**<br /><br /> **_DN_FLUSH**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM** (Interrupt-Ausnahmemaske)|0x0008001F|**_EM_INVALID**<br /><br /> **_EM_DENORMAL**<br /><br /> **_EM_ZERODIVIDE**<br /><br /> **_EM_OVERFLOW**<br /><br /> **_EM_UNDERFLOW**<br /><br /> **_EM_INEXACT**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC** (Infinity-Steuerung)<br /><br /> (Auf ARM- oder x64-Plattformen wird nicht unterstützt.)|0x00040000|**_IC_AFFINE**<br /><br /> **_IC_PROJECTIVE**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC** (Rundungssteuerung)|0x00000300|**_RC_CHOP**<br /><br /> **_RC_UP**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC** (Präzisionssteuerung)<br /><br /> (Auf ARM- oder x64-Plattformen wird nicht unterstützt.)|0x00030000|**_PC_24** (24 Bit)<br /><br /> **_PC_53** (53 Bit)<br /><br /> **_PC_64** (64 Bit)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

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

## <a name="see-also"></a>Siehe auch

[Gleitkommaunterstützung](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87, _clearfp](clear87-clearfp.md)<br/>
[_status87, _statusfp, _statusfp2](status87-statusfp-statusfp2.md)<br/>
[_control87, _controlfp, \__control87_2](control87-controlfp-control87-2.md)<br/>

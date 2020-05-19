---
title: C-Ganzzahlkonstanten
ms.date: 02/27/2018
helpviewer_keywords:
- integer constants
ms.assetid: fcf6b83c-2038-49ec-91ca-3d5ca1f83037
ms.openlocfilehash: 48561599896bb8a6f9ee159630ff15df6c0454be
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400513"
---
# <a name="c-integer-constants"></a>C-Ganzzahlkonstanten

Eine *Ganzzahlkonstante* ist eine dezimale (Basis 10), oktale (Basis 8) oder hexadezimale Zahl (Basis 16), die einen ganzzahligen Wert darstellt. Verwenden Sie ganzzahlige Konstanten, um ganzzahlige Werte darzustellen, die nicht geändert werden können.

## <a name="syntax"></a>Syntax

*integer-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Dezimalkonstante* *Integer-Suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Oktalkonstante* *Integer-Suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Hexadezimalkonstante* *Integer-Suffix*<sub>opt</sub>

*decimal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nonzero-digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Dezimalkonstante* *Ziffer*

*octal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Oktalkonstante* *Oktalziffer*

*hexadecimal-constant*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Hexadezimalpräfix* *Hexadezimalziffer*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Hexadezimalkonstante* *Hexadezimalziffer*

*hexadecimal-prefix*: eines der folgenden Zeichen<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0x**  **0X**

*nonzero-digit*: eines der folgenden Zeichen<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**1 2 3 4 5 6 7 8 9**

*octal-digit*: eines der folgenden Zeichen<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7**

*hexadecimal-digit*: eines der folgenden Zeichen<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**a b c d e f**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**A B C D E F**

*integer-suffix*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-Suffix* *long-Suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-Suffix* *long-long-Suffix*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unsigned-Suffix* *64-Bit-Integer-Suffix*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*long-Suffix* *unsigned-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*long-long-Suffix* *unsigned-suffix*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*64-bit-integer-suffix*

*unsigned-suffix*: eines der folgenden Zeichen<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**u U**

*long-suffix*: eines der folgenden Zeichen<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**l L**

*long-long-suffix*: eines der folgenden Zeichen<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**ll LL**

*64-bit-integer-suffix*: eines der folgenden Zeichen<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**i64 I64**

Die Suffixe **i64** und **I64** sind Microsoft-spezifisch.

Ganzzahlige Konstanten sind positiv, es sei denn, ihnen wird ein Minuszeichen ( **-** ) vorangestellt. Das Minuszeichen wird als unärer arithmetischer Negationsoperator interpretiert. (Weitere Informationen zu diesen Operator finden Sie auf der Seite [Unäre arithmetische Operatoren](../c-language/unary-arithmetic-operators.md).)

Wenn eine ganzzahlige Konstante mit **0x** oder **0X** beginnt, ist sie hexadezimal. Wenn sie mit der Ziffer **0** beginnt, ist sie oktal. Andernfalls wird davon ausgegangen, dass es sich hierbei um ein Dezimal handelt.

Die folgenden ganzzahligen Konstanten sind gleichwertig:

```C
28
0x1C   /* = Hexadecimal representation for decimal 28 */
034    /* = Octal representation for decimal 28 */
```

Die Ziffern einer ganzzahligen Konstante können nicht durch Leerzeichen getrennt werden. In diesen Beispielen werden einige gültige dezimale, oktale und hexadezimale Konstanten veranschaulicht.

```C
    /* Decimal Constants */
    int                 dec_int    = 28;
    unsigned            dec_uint   = 4000000024u;
    long                dec_long   = 2000000022l;
    unsigned long       dec_ulong  = 4000000000ul;
    long long           dec_llong  = 9000000000LL;
    unsigned long long  dec_ullong = 900000000001ull;
    __int64             dec_i64    = 9000000000002I64;
    unsigned __int64    dec_ui64   = 90000000000004ui64;

    /* Octal Constants */
    int                 oct_int    = 024;
    unsigned            oct_uint   = 04000000024u;
    long                oct_long   = 02000000022l;
    unsigned long       oct_ulong  = 04000000000UL;
    long long           oct_llong  = 044000000000000ll;
    unsigned long long  oct_ullong = 044400000000000001Ull;
    __int64             oct_i64    = 04444000000000000002i64;
    unsigned __int64    oct_ui64   = 04444000000000000004uI64;

    /* Hexadecimal Constants */
    int                 hex_int    = 0x2a;
    unsigned            hex_uint   = 0XA0000024u;
    long                hex_long   = 0x20000022l;
    unsigned long       hex_ulong  = 0XA0000021uL;
    long long           hex_llong  = 0x8a000000000000ll;
    unsigned long long  hex_ullong = 0x8A40000000000010uLL;
    __int64             hex_i64    = 0x4a44000000000020I64;
    unsigned __int64    hex_ui64   = 0x8a44000000000040Ui64;
```

## <a name="see-also"></a>Siehe auch

[C-Konstanten](../c-language/c-constants.md)<br/>

---
title: is- und isw-Routinen
ms.date: 11/04/2016
api_location:
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- isw
- is
helpviewer_keywords:
- is routines
- isw routines
ms.assetid: 1e171a57-2cde-41f6-a75f-a080fa3c12e5
ms.openlocfilehash: 8292f04fb8771b8270b6f8e2be3ca2f044f6c9b7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87189778"
---
# <a name="is-isw-routines"></a>is- und isw-Routinen

|||
|-|-|
|[isalnum, iswalnum, _isalnum_l, _iswalnum_l](../c-runtime-library/reference/isalnum-iswalnum-isalnum-l-iswalnum-l.md)|[isgraph, iswgraph, _isgraph_l, _iswgraph_l](../c-runtime-library/reference/isgraph-iswgraph-isgraph-l-iswgraph-l.md)|
|[isalpha, iswalpha, _isalpha_l, _iswalpha_l](../c-runtime-library/reference/isalpha-iswalpha-isalpha-l-iswalpha-l.md)|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|
|[isascii, __isascii, iswascii](../c-runtime-library/reference/isascii-isascii-iswascii.md)|[islower, iswlower, _islower_l, _iswlower_l](../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md)|
|[isblank, iswblank, _isblank_l, _iswblank_l](../c-runtime-library/reference/isblank-iswblank-isblank-l-iswblank-l.md)|[isprint, iswprint, _isprint_l, _iswprint_l](../c-runtime-library/reference/isprint-iswprint-isprint-l-iswprint-l.md)|
|[iscntrl, iswcntrl, _iscntrl_l, _iswcntrl_l](../c-runtime-library/reference/iscntrl-iswcntrl-iscntrl-l-iswcntrl-l.md)|[ispunct, iswpunct, _ispunct_l, _iswpunct_l](../c-runtime-library/reference/ispunct-iswpunct-ispunct-l-iswpunct-l.md)|
|[iscsym, iscsymf, __iscsym \_ _iswcsym, \_ _iscsymf, \_ _iswcsymf, _iscsym_l, _iswcsym_l, _iscsymf_l](../c-runtime-library/reference/iscsym-functions.md)|[isspace, iswspace, _isspace_l, _iswspace_l](../c-runtime-library/reference/isspace-iswspace-isspace-l-iswspace-l.md)|
|[_isctype, iswctype, _isctype_l, _iswctype_l](../c-runtime-library/reference/isctype-iswctype-isctype-l-iswctype-l.md)|[isupper, _isupper_l, iswupper, _iswupper_l](../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md)|
|[isdigit, iswdigit, _isdigit_l, _iswdigit_l](../c-runtime-library/reference/isdigit-iswdigit-isdigit-l-iswdigit-l.md)|[isxdigit, iswxdigit, _isxdigit_l, _iswxdigit_l](../c-runtime-library/reference/isxdigit-iswxdigit-isxdigit-l-iswxdigit-l.md)|

## <a name="remarks"></a>Bemerkungen

Diese Routinen überprüfen Zeichen für bestimmte Bedingungen.

Die **is**-Routinen liefern aussagekräftige Ergebnisse für alle Ganzzahlargumente von -1 (`EOF`) bis einschließlich **UCHAR_MAX** (0xFF). Der erwartete Argumenttyp ist **`int`** .

> [!CAUTION]
> Bei den **is** -Routinen kann das Übergeben eines Arguments vom Typ zu **`char`** unvorhersehbaren Ergebnissen führen. Ein SBCS-oder MBCS-Einzel Byte Zeichen vom Typ **`char`** mit einem Wert größer als 0x7F ist negativ. Wenn ein- **`char`** Wert überschritten wird, konvertiert der Compiler den Wert möglicherweise in ein **`signed int`** oder ein **`signed long`** . Wenn der Compiler diesen Wert mit einem Vorzeichen versieht, kann dies zu unerwarteten Ergebnissen führen.

Die **isw**-Routinen erzeugen aussagekräftige Ergebnisse für Ganzzahlwerte von -1 (**WEOF**) bis einschließlich 0xFFFF. Der **wint_t** -Datentyp ist in WCHAR definiert. H als **`unsigned short`** . es kann einen beliebigen breit Zeichen oder den breit Zeichenwert für das Ende der Datei (**WEOF**) enthalten.

Der Ausgabewert ist von der `LC_CTYPE`-Kategorieneinstellung des Gebietsschemas betroffen; weitere Informationen finden Sie unter [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md). Die Versionen dieser Funktionen ohne das **_l**-Suffix verwenden das aktuelle Gebietsschema für dieses vom Gebietsschema abhängige Verhalten; die Versionen mit dem **_l**-Suffix sind beinahe identisch, verwenden jedoch stattdessen den ihnen übergebenen Gebietsschemaparameter.

Im „C“-Gebietsschema sind die Testbedingungen für die **is** Routinen wie folgt:

`isalnum`<br/>
Alphanumerisch (A-Z, a-z oder 0-9)

`isalpha`<br/>
Alphabetisch (A-Z oder a-z)

`__isascii`<br/>
Ein ASCII-Zeichen (0x00-0x7F)

`isblank`<br/>
Horizontaler Tabulator oder Leerzeichen (0x09 oder 0x20).

`iscntrl`<br/>
Ein Steuerzeichen (0x00-0x1F oder 0x7F)

`__iscsym`<br/>
Buchstabe, Unterstrich oder Ziffer.

`__iscsymf`<br/>
Buchstabe oder Unterstrich.

`isdigit`<br/>
Eine Dezimalstelle (0-9)

`isgraph`<br/>
Druckbares Zeichen außer Leerzeichen ( ).

`islower`<br/>
Ein Kleinbuchstabe (a-z)

`isprint`<br/>
Ein druckbares Zeichen einschließlich Leerzeichen (0x20-0x7E)

`ispunct`<br/>
Interpunktionszeichen.

`isspace`<br/>
Ein Leerzeichen (0x09-0x0D oder 0x20)

`isupper`<br/>
Ein Großbuchstabe (A-Z)

`isxdigit`<br/>
Eine Hexadezimalziffer (A-F, a-f oder 0-9)

Bei den **isw**-Routinen ist das Ergebnis des Tests für die angegebene Bedingung vom Gebietsschema unabhängig. Die Testbedingungen für die **isw**-Funktionen sind wie folgt:

`iswalnum`<br/>
`iswalpha` oder `iswdigit`.

`iswalpha`<br/>
Beliebiges Breitzeichen, das einen von der Implementierung abhängigen Satz darstellt, für den `iswcntrl`, `iswdigit`, `iswpunct` oder `iswspace` nicht 0 sind. `iswalpha` liefert einen Rückgabewert ungleich 0 (null) nur für Breitzeichen, für die `iswupper` oder `iswlower` ungleich 0 (null) ist.

`iswascii`<br/>
Eine Breitzeichendarstellung von ASCII-Zeichen (0x0000 - 0x007F)

`iswblank`<br/>
Breitzeichen, das dem Standardleerzeichen entspricht oder ein von der Implementierung abhängiger Breitzeichensatz, für den `iswalnum` "false" ist. Standardleerzeichen sind das Leerzeichen (L' ') und der horizontale Tabulator (L'\t').

`iswcntrl`<br/>
Steuerbreitzeichen.

`__iswcsym`<br/>
Beliebiges Breitzeichen, für das `isalnum` "true" ist oder das '_'-Zeichen.

`__iswcsymf`<br/>
Beliebiges Breitzeichen, für das `iswalpha` "true" ist oder das '_'-Zeichen.

`iswctype`<br/>
Das Zeichen hat die Eigenschaft, die vom `desc`-Argument angegeben wird. Für jeden gültigen Wert des `desc`-Arguments von `iswctype` gibt es eine entsprechende Breitzeichenklassifizierungs-Routine, wie in der folgenden Tabelle dargestellt:

### <a name="equivalence-of-iswctypec-desc-to-other-isw-testing-routines"></a>Äquivalent von iswctype(c, desc) zu anderen isw-Testroutinen

|Der Wert des *desc*-Arguments|iswctype(*c, desc*)-Äquivalent|
|------------------------------|----------------------------------------|
|**_ALPHA**|**iswalpha (** `c` **)**|
|**_ALPHA** &#124; **_DIGIT**|**iswalnum (** `c` **)**|
|**_BLANK**|**iswblank (** `c` **)**|
|**_CONTROL**|**iswcntrl (** `c` **)**|
|**_DIGIT**|**iswdigit (** `c` **)**|
|**_ALPHA** &#124; **_DIGIT** &#124; **_PUNCT**|**iswgraph (** `c` **)**|
|**_LOWER**|**iswlower (** `c` **)**|
|**_ALPHA** &#124; **_BLANK** &#124; **_DIGIT** &#124; **_PUNCT**|**iswprint (** `c` **)**|
|**_PUNCT**|**iswpunct (** `c` **)**|
|**_BLANK**|**iswblank (** `c` **)**|
|**_SPACE**|**iswspace (** `c` **)**|
|**_UPPER**|**iswupper (** `c` **)**|
|**_HEX**|**iswxdigit (** `c` **)**|

`iswdigit`<br/>
Breitzeichen, das einem Dezimalstellenzeichen entspricht.

`iswgraph`<br/>
Druckbares Breitzeichen außer Leerzeichen-Breitzeichen (L' ').

`iswlower`<br/>
Kleinbuchstabe oder ein von der Implementierung abhängiger Breitzeichensatz für den `iswcntrl`, `iswdigit`, `iswpunct` oder `iswspace` nicht 0 sind. `iswlower` gibt einen Wert ungleich 0 (null) nur für Breitzeichen zurück, die den Kleinbuchstaben entsprechen.

`iswprint`<br/>
Druckbares Breitzeichen, einschließlich Leerzeichen-Breitzeichen (L' ').

`iswpunct`<br/>
Druckbares Breitzeichen, das weder ein Leerzeichen-Breitzeichen (L' ') noch ein Breitzeichen ist, für das `iswalnum` ungleich Null ist.

`iswspace`<br/>
Breitzeichen, das dem Standardleerzeichen entspricht oder ein von der Implementierung abhängiger Breitzeichensatz ist, für den `iswalnum` "false" ist. Standardleerstellenzeichen sind: Leerzeichen (L' '), Seitenvorschub (L'\f'), Zeilenumbruch (L'\n'), Wagenrücklaufzeichen (L'\r'), horizontaler Tabulator (L'\t') und vertikaler Tabulator (L'\v').

`iswupper`<br/>
Ein Breitzeichen ist ein Großbuchstabe oder ein von der Implementierung abhängiger Breitzeichensatz, für den `iswcntrl`, `iswdigit`, `iswpunct` oder `iswspace` nicht 0 sind. `iswupper` gibt einen Rückgabewert ungleich 0 (null) nur für Breitzeichen zurück, die den Großbuchstaben entsprechen.

`iswxdigit`<br/>
Breitzeichen, das einem Hexadezimalziffernzeichen entspricht.

## <a name="example"></a>Beispiel

```C
// crt_isfam.c
/* This program tests all characters between 0x0
* and 0x7F, then displays each character with abbreviations
* for the character-type codes that apply.
*/

#include <stdio.h>
#include <ctype.h>

int main( void )
{
   int ch;
   for( ch = 0; ch <= 0x7F; ch++ )
   {
      printf( "%.2x  ", ch );
      printf( " %c", isprint( ch )  ? ch   : ' ' );
      printf( "%4s", isalnum( ch )  ? "AN" : "" );
      printf( "%3s", isalpha( ch )  ? "A"  : "" );
      printf( "%3s", __isascii( ch )  ? "AS" : "" );
      printf( "%3s", iscntrl( ch )  ? "C"  : "" );
      printf( "%3s", __iscsym( ch )  ? "CS "  : "" );
      printf( "%3s", __iscsymf( ch )  ? "CSF"  : "" );
      printf( "%3s", isdigit( ch )  ? "D"  : "" );
      printf( "%3s", isgraph( ch )  ? "G"  : "" );
      printf( "%3s", islower( ch )  ? "L"  : "" );
      printf( "%3s", ispunct( ch )  ? "PU" : "" );
      printf( "%3s", isspace( ch )  ? "S"  : "" );
      printf( "%3s", isprint( ch )  ? "PR" : "" );
      printf( "%3s", isupper( ch )  ? "U"  : "" );
      printf( "%3s", isxdigit( ch ) ? "X"  : "" );
      printf( ".\n" );
   }
}
```

## <a name="output"></a>Output

```Output
00            AS  C                              .
01            AS  C                              .
02            AS  C                              .
03            AS  C                              .
04            AS  C                              .
05            AS  C                              .
06            AS  C                              .
07            AS  C                              .
08            AS  C                              .
09            AS  C                    S         .
0a            AS  C                    S         .
0b            AS  C                    S         .
0c            AS  C                    S         .
0d            AS  C                    S         .
0e            AS  C                              .
0f            AS  C                              .
10            AS  C                              .
11            AS  C                              .
12            AS  C                              .
13            AS  C                              .
14            AS  C                              .
15            AS  C                              .
16            AS  C                              .
17            AS  C                              .
18            AS  C                              .
19            AS  C                              .
1a            AS  C                              .
1b            AS  C                              .
1c            AS  C                              .
1d            AS  C                              .
1e            AS  C                              .
1f            AS  C                              .
20            AS                       S PR      .
21   !        AS              G    PU    PR      .
22   "        AS              G    PU    PR      .
23   #        AS              G    PU    PR      .
24   $        AS              G    PU    PR      .
25   %        AS              G    PU    PR      .
26   &        AS              G    PU    PR      .
27   '        AS              G    PU    PR      .
28   (        AS              G    PU    PR      .
29   )        AS              G    PU    PR      .
2a   *        AS              G    PU    PR      .
2b   +        AS              G    PU    PR      .
2c   ,        AS              G    PU    PR      .
2d   -        AS              G    PU    PR      .
2e   .        AS              G    PU    PR      .
2f   /        AS              G    PU    PR      .
30   0  AN    AS   CS      D  G          PR     X.
31   1  AN    AS   CS      D  G          PR     X.
32   2  AN    AS   CS      D  G          PR     X.
33   3  AN    AS   CS      D  G          PR     X.
34   4  AN    AS   CS      D  G          PR     X.
35   5  AN    AS   CS      D  G          PR     X.
36   6  AN    AS   CS      D  G          PR     X.
37   7  AN    AS   CS      D  G          PR     X.
38   8  AN    AS   CS      D  G          PR     X.
39   9  AN    AS   CS      D  G          PR     X.
3a   :        AS              G    PU    PR      .
3b   ;        AS              G    PU    PR      .
3c   <        AS              G    PU    PR      .
3d   =        AS              G    PU    PR      .
3e   >        AS              G    PU    PR      .
3f   ?        AS              G    PU    PR      .
40   @        AS              G    PU    PR      .
41   A  AN  A AS   CS CSF     G          PR  U  X.
42   B  AN  A AS   CS CSF     G          PR  U  X.
43   C  AN  A AS   CS CSF     G          PR  U  X.
44   D  AN  A AS   CS CSF     G          PR  U  X.
45   E  AN  A AS   CS CSF     G          PR  U  X.
46   F  AN  A AS   CS CSF     G          PR  U  X.
47   G  AN  A AS   CS CSF     G          PR  U   .
48   H  AN  A AS   CS CSF     G          PR  U   .
49   I  AN  A AS   CS CSF     G          PR  U   .
4a   J  AN  A AS   CS CSF     G          PR  U   .
4b   K  AN  A AS   CS CSF     G          PR  U   .
4c   L  AN  A AS   CS CSF     G          PR  U   .
4d   M  AN  A AS   CS CSF     G          PR  U   .
4e   N  AN  A AS   CS CSF     G          PR  U   .
4f   O  AN  A AS   CS CSF     G          PR  U   .
50   P  AN  A AS   CS CSF     G          PR  U   .
51   Q  AN  A AS   CS CSF     G          PR  U   .
52   R  AN  A AS   CS CSF     G          PR  U   .
53   S  AN  A AS   CS CSF     G          PR  U   .
54   T  AN  A AS   CS CSF     G          PR  U   .
55   U  AN  A AS   CS CSF     G          PR  U   .
56   V  AN  A AS   CS CSF     G          PR  U   .
57   W  AN  A AS   CS CSF     G          PR  U   .
58   X  AN  A AS   CS CSF     G          PR  U   .
59   Y  AN  A AS   CS CSF     G          PR  U   .
5a   Z  AN  A AS   CS CSF     G          PR  U   .
5b   [        AS              G    PU    PR      .
5c   \        AS              G    PU    PR      .
5d   ]        AS              G    PU    PR      .
5e   ^        AS              G    PU    PR      .
5f   _        AS   CS CSF     G    PU    PR      .
60   `        AS              G    PU    PR      .
61   a  AN  A AS   CS CSF     G  L       PR     X.
62   b  AN  A AS   CS CSF     G  L       PR     X.
63   c  AN  A AS   CS CSF     G  L       PR     X.
64   d  AN  A AS   CS CSF     G  L       PR     X.
65   e  AN  A AS   CS CSF     G  L       PR     X.
66   f  AN  A AS   CS CSF     G  L       PR     X.
67   g  AN  A AS   CS CSF     G  L       PR      .
68   h  AN  A AS   CS CSF     G  L       PR      .
69   i  AN  A AS   CS CSF     G  L       PR      .
6a   j  AN  A AS   CS CSF     G  L       PR      .
6b   k  AN  A AS   CS CSF     G  L       PR      .
6c   l  AN  A AS   CS CSF     G  L       PR      .
6d   m  AN  A AS   CS CSF     G  L       PR      .
6e   n  AN  A AS   CS CSF     G  L       PR      .
6f   o  AN  A AS   CS CSF     G  L       PR      .
70   p  AN  A AS   CS CSF     G  L       PR      .
71   q  AN  A AS   CS CSF     G  L       PR      .
72   r  AN  A AS   CS CSF     G  L       PR      .
73   s  AN  A AS   CS CSF     G  L       PR      .
74   t  AN  A AS   CS CSF     G  L       PR      .
75   u  AN  A AS   CS CSF     G  L       PR      .
76   v  AN  A AS   CS CSF     G  L       PR      .
77   w  AN  A AS   CS CSF     G  L       PR      .
78   x  AN  A AS   CS CSF     G  L       PR      .
79   y  AN  A AS   CS CSF     G  L       PR      .
7a   z  AN  A AS   CS CSF     G  L       PR      .
7b   {        AS              G    PU    PR      .
7c   |        AS              G    PU    PR      .
7d   }        AS              G    PU    PR      .
7e   ~        AS              G    PU    PR      .
7f            AS  C                              .
```

## <a name="see-also"></a>Siehe auch

[Zeichen Klassifizierung](../c-runtime-library/character-classification.md)<br/>
[Gebietsschema](../c-runtime-library/locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[Interpretation von Multibyte-Zeichensequenzen](../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[to-Funktionen](../c-runtime-library/to-functions.md)

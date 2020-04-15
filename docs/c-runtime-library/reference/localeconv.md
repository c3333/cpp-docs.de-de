---
title: localeconv
ms.date: 4/2/2020
api_name:
- localeconv
- _o_localeconv
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- localeconv
helpviewer_keywords:
- lconv type
- localeconv function
- locales, getting information on
ms.assetid: 7ecdb1f2-88f5-4037-a0e7-c754ab003660
ms.openlocfilehash: a617980d60b3a12c06b30aab6cd457792a1aa770
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81342147"
---
# <a name="localeconv"></a>localeconv

Ruft detaillierte Informationen über Gebietsschemaeinstellungen ab.

## <a name="syntax"></a>Syntax

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>Rückgabewert

**localeconv** gibt einen Zeiger auf ein ausgefülltes Objekt der [Typstruktur lconv](../../c-runtime-library/standard-types.md)zurück. Die im Objekt enthaltenen Werte werden aus den Gebietsschemaeinstellungen im threadlokalen Speicher kopiert und können durch nachfolgende Aufrufe von **localeconv**überschrieben werden. Änderungen an den Werten in diesem Objekt ändern die Gebietsschemaeinstellungen nicht. Aufrufe zum [festlegen von locale](setlocale-wsetlocale.md) mit *Kategoriewerten* **von LC_ALL** **, LC_MONETARY**oder **LC_NUMERIC** überschreiben den Inhalt der Struktur.

## <a name="remarks"></a>Bemerkungen

Die **localeconv-Funktion** erhält detaillierte Informationen zur numerischen Formatierung für das aktuelle Gebietsschema. Diese Informationen werden in einer Struktur des Typs **lconv** gespeichert. Die **lconv**-Struktur, die in LOCALE.H definiert ist, enthält die folgenden Member:

|Feld|Bedeutung|
|-|-|
Decimal_point<br/>_W_decimal_point|Zeiger auf Dezimalzeichen für nicht monetäre Mengen.
Thousands_sep<br/>_W_thousands_sep|Zeiger auf ein Zeichen, das Zifferngruppen links vom Dezimaltrennzeichen für nicht monetäre Mengen trennt.
Gruppierung|Zeiger auf eine **ganzzahlige Char-Größe,** die die Größe jeder Gruppe von Ziffern in nicht monetären Mengen enthält.
int_curr_symbol,<br/>_W_int_curr_symbol|Zeiger auf das internationale Währungssymbol für aktuelles Gebietsschema. Die ersten drei Zeichen geben das alphabetische internationale Währungssymbol an, wie im Standard *ISO 4217 – Codes für die Darstellung der Währung und Fonds* definiert. Das vierte Zeichen (unmittelbar vorausgehendes Zeichen NULL) trennt das internationale Währungssymbol von der monetären Menge.
Währungssymbol<br/>_W_currency_symbol|Zeiger auf das lokale Währungssymbol für das aktuelle Gebietsschema.
mon_decimal_point,<br/>_W_mon_decimal_point|Zeiger auf Dezimalzeichen für monetäre Mengen.
mon_thousands_sep,<br/>_W_mon_thousands_sep|Zeiger auf Trennzeichen für Gruppen von Ziffern links von der Dezimalstelle in monetären Mengen.
mon_grouping|Zeiger auf eine **ganzzahlige Char-Größe,** die die Größe jeder Gruppe von Ziffern in monetären Mengen enthält.
positive_sign,<br/>_W_positive_sign|Die Zeichenfolge, die das Zeichen für nicht negative monetären Mengen angibt.
negative_sign,<br/>_W_negative_sign|Die Zeichenfolge, die das Zeichen für negative monetären Mengen angibt.
int_frac_digits|Die Anzahl der Ziffern rechts vom Dezimaltrennzeichen in international formatierten monetären Mengen.
frac_digits|Die Anzahl der Ziffern rechts vom Dezimaltrennzeichen in formatierten monetären Mengen.
p_cs_precedes|Auf 1 festgelegt, wenn dem Währungssymbol ein Wert für eine nicht negative, formatierte monetäre Menge vorangeht. Auf 0 festgelegt, wenn das Symbol einem Wert folgt.
p_sep_by_space|Auf 1 festgelegt, wenn das Währungssymbol durch Leerzeichen von einem Wert für eine nicht negative, formatierte monetäre Menge getrennt ist. Auf 0 festgelegt, wenn es keine Leerzeichentrennung gibt.
n_cs_precedes|Auf 1 festgelegt, wenn dem Währungssymbol ein Wert für eine negative, formatierte monetäre Menge vorangeht. Auf 0 festgelegt, wenn das Symbol einem Wert nachfolgt.
n_sep_by_space|Auf 1 festgelegt, wenn das Währungssymbol durch Leerzeichen von einem Wert für eine negative, formatierte monetäre Menge getrennt ist. Auf 0 festgelegt, wenn es keine Leerzeichentrennung gibt.
p_sign_posn|Die Position des positiven Vorzeichens in nicht negativen, formatierten monetären Mengen.
n_sign_posn|Die Position des positiven Vorzeichens in negativen, formatierten monetären Mengen.

Außer wie angegeben, sind Member der `char *` **lconv-Struktur,** die haben, und `wchar_t *` Versionen Zeiger auf Zeichenfolgen. Alle diese, die **""** (oder **L""** für **wchar_t** <strong>\*</strong>) entspricht, ist entweder von Null länge oder wird im aktuellen Gebietsschema nicht unterstützt. Beachten Sie, dass **decimal_point** und **_W_decimal_point** immer unterstützt werden und eine Länge ungleich Null haben.

Die **Zeichenelemente** der Struktur sind kleine nicht negative Zahlen, keine Zeichen. Jeder von diesen, der gleich **CHAR_MAX** ist, wird im aktuellen Gebietsschema nicht unterstützt.

Die Werte der **Gruppierung** und **mon_grouping** werden nach den folgenden Regeln interpretiert:

- **CHAR_MAX** - Führen Sie keine weitere Gruppierung durch.

- 0 - Verwenden Sie das vorherige Element für jede der verbleibenden Ziffern.

- *n* - Anzahl der Ziffern, aus denen die aktuelle Gruppe besteht. Das nächste Element wird untersucht, um die Größe der nächsten Gruppe von Zeichen vor der aktuellen Gruppe zu bestimmen.

Die Werte für **int_curr_symbol** werden gemäß den folgenden Regeln interpretiert:

- Die ersten drei Zeichen geben das alphabetische internationale Währungssymbol an, wie im Standard *ISO 4217 – Codes für die Darstellung der Währung und Fonds* definiert.

- Das vierte Zeichen (unmittelbar vorausgehendes Zeichen NULL) trennt das internationale Währungssymbol von der monetären Menge.

Die Werte für **p_cs_precedes** und **n_cs_precedes** werden gemäß den folgenden Regeln interpretiert (die **n_cs_precedes**-Regel wird in Klammern angegeben):

- 0 - Währungssymbol folgt Wert für nicht negativen (negativen) formatierten Geldwert.

- 1 - Währungssymbol geht Wert für nicht negativen (negativen) formatierten Geldwert voraus.

Die Werte für **p_sep_by_space** und **n_sep_by_space** werden gemäß den folgenden Regeln interpretiert (die **n_sep_by_space**-Regel wird in Klammern angegeben):

- 0 - Währungssymbol wird durch Leerzeichen für nicht negativen (negativen) formatierten Geldwert getrennt.

- 1 - Es gibt keine Leerzeichentrennung zwischen Währungssymbol und Wert für nicht negativen (negativen) formatierten Geldwert.

Die Werte für **p_sign_posn** und **n_sign_posn** werden gemäß den folgenden Regeln interpretiert:

- 0 - Klammern umgeben Menge und Währungssymbol.

- 1 - Zeichenzeichenfolge geht Mengen- und Währungssymbol voraus.

- 2 - Zeichenzeichenfolge folgt Menge und Währung Symbol.

- 3 - Zeichenzeichenfolge unmittelbar vor Währungssymbol.

- 4 - Zeichenzeichenfolge folgt sofort Währungssymbol.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**localeconv**|\<locale.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Siehe auch

[Locale](../../c-runtime-library/locale.md)<br/>
[Setlocale](../../preprocessor/setlocale.md)<br/>
[strcoll-Funktionen](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>

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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: c4e1820ac412a0447c5059ecc92375275f7b2701
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218636"
---
# <a name="localeconv"></a>localeconv

Ruft detaillierte Informationen über Gebietsschemaeinstellungen ab.

## <a name="syntax"></a>Syntax

```C
struct lconv *localeconv( void );
```

## <a name="return-value"></a>Rückgabewert

**localeconv** gibt einen Zeiger auf ein ausgefülltes Objekt vom Typ [struct lkonv](../../c-runtime-library/standard-types.md)zurück. Die im-Objekt enthaltenen Werte werden aus den Gebiets Schema Einstellungen im lokalen Thread Speicher kopiert und können durch nachfolgende Aufrufe von **localeconv**überschrieben werden. Änderungen, die an den Werten in diesem-Objekt vorgenommen wurden, ändern nicht die Gebiets Schema Einstellungen. Aufrufe von [setlocale](setlocale-wsetlocale.md) mit *kategoriewerten* von **LC_ALL**, **LC_MONETARY**oder **LC_NUMERIC** überschreiben den Inhalt der-Struktur.

## <a name="remarks"></a>Bemerkungen

Die **localeconv** -Funktion ruft ausführliche Informationen zur numerischen Formatierung für das aktuelle Gebiets Schema ab. Diese Informationen werden in einer Struktur des Typs **lconv** gespeichert. Die **lconv**-Struktur, die in LOCALE.H definiert ist, enthält die folgenden Member:

|Feld|Bedeutung|
|-|-|
DECIMAL_POINT,<br/>_W_decimal_point|Zeiger auf Dezimaltrennzeichen für nicht monetäre Mengen.
thousands_sep,<br/>_W_thousands_sep|Ein Zeiger auf ein Zeichen, das Gruppen von Ziffern nach links vom Dezimaltrennzeichen für nicht monetäre Mengen trennt.
Gruppierung|Ein Zeiger auf eine ganze Zahl mit einer Größe **`char`** , die die Größe der einzelnen Ziffern in nicht monetären Mengen enthält.
Int_curr_symbol,<br/>_W_int_curr_symbol|Zeiger auf das internationale Währungssymbol für das aktuelle Gebiets Schema. Die ersten drei Zeichen geben das alphabetische internationale Währungssymbol an, wie im Standard *ISO 4217 – Codes für die Darstellung der Währung und Fonds* definiert. Das vierte Zeichen (unmittelbar vorausgehendes Zeichen NULL) trennt das internationale Währungssymbol von der monetären Menge.
CURRENCY_SYMBOL,<br/>_W_currency_symbol|Zeiger auf das lokale Währungssymbol für das aktuelle Gebiets Schema.
mon_decimal_point,<br/>_W_mon_decimal_point|Zeiger auf Dezimaltrennzeichen für monetäre Mengen.
mon_thousands_sep,<br/>_W_mon_thousands_sep|Ein Zeiger auf das Trennzeichen für Gruppen von Ziffern auf der linken Seite der Dezimalstelle in der monetären Menge.
mon_grouping|Ein Zeiger auf eine ganze Zahl mit einer Größe **`char`** , die die Größe der einzelnen Ziffern in der monetären Menge enthält.
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

Mit Ausnahme der angegebenen werden Member der **LVS v** -Struktur, die `char *` -und-Versionen aufweisen, `wchar_t *` Zeiger auf Zeichen folgen. Alle, die **""** (oder **L ""** für) gleich sind, haben **`wchar_t`** <strong>\*</strong> entweder eine Länge von 0 (null) oder werden im aktuellen Gebiets Schema nicht unterstützt. Beachten Sie, dass **DECIMAL_POINT** und **_W_decimal_point** immer unterstützt werden und von einer Länge ungleich NULL sind.

Die Elemente **`char`** der Struktur sind kleine nicht negative Zahlen, keine Zeichen. Jeder von diesen, der gleich **CHAR_MAX** ist, wird im aktuellen Gebietsschema nicht unterstützt.

Die Werte von **Gruppierung** und **Mon_grouping** werden gemäß den folgenden Regeln interpretiert:

- **CHAR_MAX** : keine weiteren Gruppierungen ausführen.

- 0-das vorherige Element wird für jede der verbleibenden Ziffern verwendet.

- *n* -Anzahl der Ziffern, die die aktuelle Gruppe bilden. Das nächste Element wird untersucht, um die Größe der nächsten Gruppe von Zeichen vor der aktuellen Gruppe zu bestimmen.

Die Werte für **int_curr_symbol** werden gemäß den folgenden Regeln interpretiert:

- Die ersten drei Zeichen geben das alphabetische internationale Währungssymbol an, wie im Standard *ISO 4217 – Codes für die Darstellung der Währung und Fonds* definiert.

- Das vierte Zeichen (unmittelbar vorausgehendes Zeichen NULL) trennt das internationale Währungssymbol von der monetären Menge.

Die Werte für **p_cs_precedes** und **n_cs_precedes** werden gemäß den folgenden Regeln interpretiert (die **n_cs_precedes**-Regel wird in Klammern angegeben):

- 0-Währungssymbol folgt dem Wert für einen nicht negativen (negativen) formatierten monetären Wert.

- 1-Währungssymbol liegt vor dem Wert für einen nicht negativen (negativen) formatierten monetären Wert.

Die Werte für **p_sep_by_space** und **n_sep_by_space** werden gemäß den folgenden Regeln interpretiert (die **n_sep_by_space**-Regel wird in Klammern angegeben):

- 0-Währungssymbol wird von Wert durch Leerzeichen für einen nicht negativen (negativen) formatierten monetären Wert getrennt.

- 1: zwischen dem Währungssymbol und dem Wert für einen nicht negativen (negativen) formatierten monetären Wert ist keine Leerzeichen Trennung vorhanden.

Die Werte für **p_sign_posn** und **n_sign_posn** werden gemäß den folgenden Regeln interpretiert:

- 0-Klammern umschließen Menge und Währungssymbol.

- 1: die Zeichenfolge wird vor der Menge und dem Währungssymbol vorangestellt.

- 2: Zeichenfolge folgt der Menge und dem Währungssymbol.

- eine Zeichenfolge mit 3 Zeichen wird unmittelbar vor dem Währungssymbol vorangestellt.

- 4: Signieren der Zeichenfolge unmittelbar nach dem Währungssymbol.

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen hierzu finden Sie unter [globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|-Routine zurückgegebener Wert|Erforderlicher Header|
|-------------|---------------------|
|**localeconv**|\<locale.h>|

Zusätzliche Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotheken

Alle Versionen [C-Laufzeitbibliotheken](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Weitere Informationen

[Gebietsschema](../../c-runtime-library/locale.md)<br/>
[setlocale](../../preprocessor/setlocale.md)<br/>
[Funktionen von "strecoll"](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>

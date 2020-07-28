---
title: Gebietsschema
ms.date: 04/11/2018
f1_keywords:
- c.international
helpviewer_keywords:
- localization, locale
- country information
- language information routines
- setlocale function
- locale routines
ms.assetid: 442f8112-9288-44d7-be3c-15d22652093a
ms.openlocfilehash: a747c60994afbf4293aca8e4a3290d20b4bc18a3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87189583"
---
# <a name="locale"></a>Gebietsschema

Das *Gebietsschema* bezieht sich auf die Einstellungen für das Land bzw. die Region und die Sprache, mit denen Sie Ihr Programm anpassen können. Einige vom Gebietsschema abhängige Kategorien umfassen die Anzeigeformate für Datums- und Währungswerte. Weitere Informationen finden Sie unter [Gebietsschemakategorien](../c-runtime-library/locale-categories.md).

Verwenden Sie die [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)-Funktion mit Funktionen ohne das **_l**-Suffix, um einige oder alle Gebietsschemainformationen des aktuellen Programms oder Threads zu ändern oder abzufragen. Die Funktionen mit dem **_l**-Suffix verwenden den Gebietsschemaparameter, der nur während der Ausführung dieser spezifischen Funktion für ihre Gebietsschemainformationen übergeben wird. Verwenden Sie [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) zum Erstellen eines Gebietsschemas, das mit einer Funktion mit einem **_l**-Suffix verwendet werden kann. Um dieses Gebietsschema freizugeben, verwenden Sie [_free_locale](../c-runtime-library/reference/free-locale.md). Rufen Sie das aktuelle Gebietsschema mithilfe von [_get_current_locale](../c-runtime-library/reference/get-current-locale.md) ab.

Steuern Sie mithilfe von [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md), ob jeder Thread über sein eigenes Gebietsschema verfügt, oder ob alle Threads in einem Programm das gleiche Gebietsschema verwenden. Weitere Informationen finden Sie unter [Gebietsschemas und Codepages](../text/locales-and-code-pages.md).

Von den Funktionen in der folgenden Tabelle sind sicherere Versionen verfügbar, die durch das Suffix **_s** („sicher“) gekennzeichnet sind. Weitere Informationen finden Sie unter [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md).

## <a name="locale-dependent-routines"></a>Gebietsschemaabhängige Routinen

|-Routine zurückgegebener Wert|Zweck|Abhängigkeit von der **setlocale**-Kategorieeinstellung|
|-------------|---------|---------------------------------------------|
|[atof, _atof_l, _wtof, _wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|Konvertieren von Zeichen in Gleitkommawert|**LC_NUMERIC**|
|[atoi, _atoi_l, _wtoi, _wtoi_l](../c-runtime-library/reference/atoi-atoi-l-wtoi-wtoi-l.md)|Konvertieren von Zeichen in ganzzahligen Wert|**LC_NUMERIC**|
|[_atoi64, _atoi64_l, _wtoi64, _wtoi64_l](../c-runtime-library/reference/atoi64-atoi64-l-wtoi64-wtoi64-l.md)|Konvertieren von Zeichen in 64-Bit-Ganzzahlwert|**LC_NUMERIC**|
|[atol, _atol_l, _wtol, _wtol_l](../c-runtime-library/reference/atol-atol-l-wtol-wtol-l.md)|Konvertieren von Zeichen in langen Wert|**LC_NUMERIC**|
|[_atodbl, _atodbl_l, _atoldbl, _atoldbl_l, _atoflt, _atoflt_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|Konvertieren von Zeichen in Wert mit doppelter Länge|**LC_NUMERIC**|
|[is-Routinen](../c-runtime-library/is-isw-routines.md)|Testganzzahl für bestimmten Zustand.|**LC_CTYPE**|
|[isleadbyte, _isleadbyte_l](../c-runtime-library/reference/isleadbyte-isleadbyte-l.md)|Test für führendes Byte|**LC_CTYPE**|
|[localeconv](../c-runtime-library/reference/localeconv.md)|Lesen von entsprechenden Werten zum Formatieren von numerischen Mengen|`LC_MONETARY, LC_NUMERIC`|
|[MB_CUR_MAX](../c-runtime-library/mb-cur-max.md)|Maximale Länge in Bytes eines beliebigen Multibytezeichens im aktuellen Gebietsschema (in STDLIB.H per Makro definiert)|**LC_CTYPE**|
|[_mbccpy, _mbccpy_l](../c-runtime-library/reference/mbccpy-mbccpy-l.md),[_mbccpy_s, _mbccpy_s_l](../c-runtime-library/reference/mbccpy-s-mbccpy-s-l.md)|Kopieren eines Multibytezeichens|**LC_CTYPE**|
|[_mbclen, mblen, _mblen_l](../c-runtime-library/reference/mbclen-mblen-mblen-l.md)|Überprüfen und Zurückgeben einer Anzahl von Bytes in Multibytezeichen|**LC_CTYPE**|
|[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|Bei Multibyte-Zeichenfolgen: Überprüfen jedes Zeichens in der Zeichenfolge; Zurückgeben der Zeichenfolgenlänge|**LC_CTYPE**|
|[mbstowcs, _mbstowcs_l](../c-runtime-library/reference/mbstowcs-mbstowcs-l.md),[mbstowcs_s, _mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)|Konvertieren von Multibytezeichensequenz in entsprechende Breitzeichensequenz|**LC_CTYPE**|
|[mbtowc, _mbtowc_l](../c-runtime-library/reference/mbtowc-mbtowc-l.md)|Konvertieren von Multibytezeichen in entsprechendes Breitzeichen|**LC_CTYPE**|
|[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)-Funktionen|Schreiben von formatierter Ausgabe|**LC_NUMERIC** (bestimmt die Basiszeichenausgabe)|
|[scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)-Funktionen|Lesen von formatierter Eingabe|**LC_NUMERIC** (bestimmt die Basiszeichenerkennung)|
|[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)|Auswählen von Gebietsschema für Programm|Nicht verfügbar|
|[strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md)|Vergleichen von Zeichen zweier Zeichenfolgen|**LC_COLLATE**|
|[_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)|Vergleichen zweier Zeichenfolgen ohne Berücksichtigung von Groß-/Kleinbuchstaben|**LC_CTYPE**|
|[_stricoll, _wcsicoll, _mbsicoll, _stricoll_l, _wcsicoll_l, _mbsicoll_l](../c-runtime-library/reference/stricoll-wcsicoll-mbsicoll-stricoll-l-wcsicoll-l-mbsicoll-l.md)|Vergleichen von Zeichen zweier Zeichenfolgen (ohne Berücksichtigung von Groß-/Kleinbuchstaben)|**LC_COLLATE**|
|[_strncoll, _wcsncoll, _mbsncoll, _strncoll_l, _wcsncoll_l, _mbsncoll_l](../c-runtime-library/reference/strncoll-wcsncoll-mbsncoll-strncoll-l-wcsncoll-l-mbsncoll-l.md)|Vergleichen der ersten **n** Zeichen von zwei Zeichenfolgen|**LC_COLLATE**|
|[_strnicmp, _wcsnicmp, _mbsnicmp, _strnicmp_l, _wcsnicmp_l, _mbsnicmp_l](../c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l.md)|Vergleichen von Zeichen zweier Zeichenfolgen ohne Berücksichtigung von Groß-/Kleinbuchstaben.|**LC_CTYPE**|
|[_strnicoll, _wcsnicoll, _mbsnicoll, _strnicoll_l, _wcsnicoll_l, _mbsnicoll_l](../c-runtime-library/reference/strnicoll-wcsnicoll-mbsnicoll-strnicoll-l-wcsnicoll-l-mbsnicoll-l.md)|Vergleichen der ersten **n** Zeichen von zwei Zeichenfolgen (ohne Berücksichtigung von Groß-/Kleinbuchstaben)|**LC_COLLATE**|
|[strftime, wcsftime, _strftime_l, _wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|Formatieren von Datums- und Uhrzeitwert nach angegebenem **format**-Argument|**LC_TIME**|
|[_strlwr, _wcslwr, _mbslwr, _strlwr_l, _wcslwr_l, _mbslwr_l](../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md), [_strlwr_s, _strlwr_s_l, _mbslwr_s, _mbslwr_s_l, _wcslwr_s, _wcslwr_s_l](../c-runtime-library/reference/strlwr-s-strlwr-s-l-mbslwr-s-mbslwr-s-l-wcslwr-s-wcslwr-s-l.md)|Konvertieren von jedem Großbuchstaben in angegebener Zeichenfolge in Kleinbuchstaben an jeweiliger Stelle|**LC_CTYPE**|
|[strtod, _strtod_l, wcstod, _wcstod_l](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|Konvertieren einer Zeichenfolge in **`double`** einen Wert|**LC_NUMERIC** (bestimmt die Basiszeichenerkennung)|
|[strtol, wcstol, _strtol_l, _wcstol_l](../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)|Konvertieren einer Zeichenfolge in **`long`** einen Wert|**LC_NUMERIC** (bestimmt die Basiszeichenerkennung)|
|[strtoul, _strtoul_l, wcstoul, _wcstoul_l](../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)|Konvertieren von Zeichenfolge in langen Wert ohne Vorzeichen|**LC_NUMERIC** (bestimmt die Basiszeichenerkennung)|
|[_strupr, _strupr_l, _mbsupr, _mbsupr_l, _wcsupr_l, _wcsupr](../c-runtime-library/reference/strupr-strupr-l-mbsupr-mbsupr-l-wcsupr-l-wcsupr.md), [_strupr_s, _strupr_s_l, _mbsupr_s, _mbsupr_s_l, _wcsupr_s, _wcsupr_s_l](../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)|Konvertieren von jedem Kleinbuchstaben in angegebener Zeichenfolge in Großbuchstaben an jeweiliger Stelle|**LC_CTYPE**|
|[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)|Transformieren von Zeichenfolge in sortierte Form gemäß Gebietsschema|**LC_COLLATE**|
|[tolower, _tolower, towlower, _tolower_l, _towlower_l](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md), [_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Konvertieren von angegebenem Zeichen zu entsprechendem Kleinbuchstaben|**LC_CTYPE**|
|[toupper, _toupper, towupper, _toupper_l, _towupper_l](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md), [_mbctolower, _mbctolower_l, _mbctoupper, _mbctoupper_l](../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)|Konvertieren von angegebenem Zeichen zu entsprechendem Großbuchstaben|**LC_CTYPE**|
|[wcstombs, _wcstombs_l](../c-runtime-library/reference/wcstombs-wcstombs-l.md), [wcstombs_s, _wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)|Konvertieren von Breitzeichensequenz in entsprechende Multibytezeichensequenz|**LC_CTYPE**|
|[wctomb, _wctomb_l](../c-runtime-library/reference/wctomb-wctomb-l.md), [wctomb_s, _wctomb_s_l](../c-runtime-library/reference/wctomb-s-wctomb-s-l.md)|Konvertieren von Breitzeichen in entsprechendes Multibytezeichen|**LC_CTYPE**|

> [!NOTE]
> Bei Multibyte-Routinen muss die Multibyte-Codepage dem mit [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) festgelegten Gebietsschema entsprechen. Wenn [_setmbcp](../c-runtime-library/reference/setmbcp.md) über ein Argument von **_MB_CP_LOCALE** verfügt, ist die Multibyte-Codepage mit der **setlocale**-Codepage identisch.

## <a name="see-also"></a>Weitere Informationen

[Internationalisierung](../c-runtime-library/internationalization.md)<br/>
[Universelle C-Laufzeitroutinen nach Kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>

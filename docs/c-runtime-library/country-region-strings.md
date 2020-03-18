---
title: Land/Region-Zeichenfolgen
ms.date: 11/04/2016
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
ms.openlocfilehash: 8556e005618a1b69c47498a07e218284dcb1164f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443435"
---
# <a name="countryregion-strings"></a>Country/Region Strings

Zeichenfolgen für Länder und Regionen können mit einer Sprachenzeichenfolge kombiniert werden, um eine Gebietsschemaspezifikation für die Funktionen `setlocale`, `_wsetlocale`, `_create_locale`und `_wcreate_locale` zu erstellen. Eine Liste der von den verschiedenen Windows-Betriebssystemversionen unterstützten Länder und Regionen finden Sie unter **Sprache**, **Ort** in der Spalte **Sprachtag** der Tabelle unter [Anhang A: Produktverhalten](https://msdn.microsoft.com/library/cc233982.aspx) in [MS-LCID]: Windows-Sprachcodebezeichner – Referenz. Ein Beispiel für Code, der verfügbare Gebietsschemanamen und zugehörige Werte aufzählt, finden Sie unter [NLS: Namenbasierte APIs – Beispiel](/windows/win32/intl/nls--name-based-apis-sample).

## <a name="additional-supported-country-and-region-strings"></a>Weitere unterstützte Zeichenfolgen für Länder und Regionen

Die Implementierung der Microsoft C-Laufzeitbibliothek unterstützt auch die folgenden zusätzlichen Land-/Regionszeichenfolgen und Abkürzungen:

|Land-/Regionszeichenfolge|Abkürzung|Entsprechender Gebietsschemaname|
|----------------------------|------------------|----------------------------|
|america|USA|de-DE|
|britain|GBR|en-GB|
|china|CHN|zh-CN|
|Tschechisch|CZE|cs-CZ|
|Großbritannien|GBR|en-GB|
|great britain|GBR|en-GB|
|Niederlande|NLD|nl-NL|
|hong-kong|HKG|zh-HK|
|new-zealand|NZL|en-NZ|
|nz|NZL|en-NZ|
|pr china|CHN|zh-CN|
|pr-china|CHN|zh-CN|
|puerto-rico|PRI|es-PR|
|Slowakisch|SVK|sk-SK|
|south africa|ZAF|af-ZA|
|south korea|KOR|ko-KR|
|south-africa|ZAF|af-ZA|
|south-korea|KOR|ko-KR|
|trinidad & tobago|TTO|en-TT|
|uk|GBR|en-GB|
|united-kingdom|GBR|en-GB|
|united-states|USA|de-DE|
|USA|USA|de-DE|

## <a name="see-also"></a>Weitere Informationen

[Gebietsschema-Namen, Sprachen und Zeichenfolgen für Länder und Regionen](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Language Strings](../c-runtime-library/language-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)

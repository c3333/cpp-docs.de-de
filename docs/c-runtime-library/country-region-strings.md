---
title: Land/Region-Zeichenfolgen
ms.date: 11/04/2016
helpviewer_keywords:
- country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
ms.openlocfilehash: d5d8c10e30886c1b34bb5dc95296bc594acda1a4
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831852"
---
# <a name="countryregion-strings"></a>Sprache/Land-Zeichenfolgen

Zeichenfolgen für Länder und Regionen können mit einer Sprachenzeichenfolge kombiniert werden, um eine Gebietsschemaspezifikation für die Funktionen `setlocale`, `_wsetlocale`, `_create_locale`und `_wcreate_locale` zu erstellen. Eine Liste der Länder-und Regions Namen, die von verschiedenen Windows-Betriebssystemversionen unterstützt werden, finden Sie in den Spalten " **Language**", " **Location**" und " **Language Tag** " der Tabelle in [Anhang A: Produktverhalten](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c) in \[ MS-LCID]: Referenz zur Windows-Sprach Code Kennung (LCID). Ein Beispiel für Code, der verfügbare Gebietsschemanamen und zugehörige Werte aufzählt, finden Sie unter [NLS: Namenbasierte APIs – Beispiel](/windows/win32/intl/nls--name-based-apis-sample).

## <a name="additional-supported-country-and-region-strings"></a>Weitere unterstützte Zeichenfolgen für Länder und Regionen

Die Implementierung der Microsoft C-Laufzeitbibliothek unterstützt auch die folgenden zusätzlichen Land-/Regionszeichenfolgen und Abkürzungen:

|Land-/Regionszeichenfolge|Abkürzung|Entsprechender Gebietsschemaname|
|----------------------------|------------------|----------------------------|
|america|USA|de-DE|
|britain|GBR|en-GB|
|china|CHN|zh-CN|
|Tschechisch|CZE|cs-CZ|
|england|GBR|en-GB|
|great britain|GBR|en-GB|
|holland|NLD|nl-NL|
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

[Gebiets Schema Namen, Sprachen und Länder-/regionszeichenfolgen](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Sprachzeichenfolgen](../c-runtime-library/language-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)

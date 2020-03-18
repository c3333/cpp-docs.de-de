---
title: Language Strings
ms.date: 11/04/2016
helpviewer_keywords:
- language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
ms.openlocfilehash: 18a94d33f9ca382bb6c7cd77a4f2b33ed800f2c6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438250"
---
# <a name="language-strings"></a>Language Strings

Die Funktionen [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) und [_create_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) können die von der Windows NLS-API unterstützten Sprachen auf Betriebssystemen verwenden, die nicht die Unicode-Codepage verwenden. Eine Liste der unterstützten Sprachen nach Betriebssystemversion finden Sie unter [Anhang A: Produktverhalten](https://msdn.microsoft.com/library/cc233982.aspx) in [MS-LCID]: Windows-Sprachcodebezeichner – Referenz. Die Sprachenzeichenfolge kann ein beliebiger Wert aus den Spalten für die **Sprache** und die **Sprachtag** der Liste der unterstützten Sprachen sein. Ein Beispiel für Code, der verfügbare Gebietsschemanamen und zugehörige Werte aufzählt, finden Sie unter [NLS: Namenbasierte APIs – Beispiel](/windows/win32/intl/nls--name-based-apis-sample).

## <a name="additional-supported-language-strings"></a>Zusätzliche unterstützte Sprachenzeichenfolgen

Die Implementierung der Microsoft C-Laufzeitbibliothek unterstützt ebenfalls diese Sprachenzeichenfolgen:

|Sprachenzeichenfolge|Entsprechender Gebietsschemaname|
|---------------------|----------------------------|
|Amerikanisch|de-DE|
|american english|de-DE|
|american-english|de-DE|
|Australisch|en-AU|
|Belgisch|nl-BE|
|Kanadisch|en-CA|
|chh|zh-HK|
|chi|zh-SG|
|Chinesisch|zh|
|chinese-hongkong|zh-HK|
|chinese-simplified|zh-CN|
|chinese-singapore|zh-SG|
|chinese-traditional|zh-TW|
|dutch-belgian|nl-BE|
|english-american|de-DE|
|english-aus|en-AU|
|english-belize|en-BZ|
|english-can|en-CA|
|english-caribbean|en-029|
|english-ire|en-IE|
|english-jamaica|en-JM|
|english-nz|en-NZ|
|english-south africa|en-ZA|
|english-trinidad y tobago|en-TT|
|english-uk|en-GB|
|english-us|de-DE|
|english-usa|de-DE|
|french-belgian|fr-BE|
|french-canadian|fr-CA|
|french-luxembourg|fr-LU|
|french-swiss|fr-CH|
|german-austrian|de-AT|
|german-lichtenstein|de-LI|
|german-luxembourg|de-LU|
|german-swiss|de-CH|
|irish-english|en-IE|
|italian-swiss|it-CH|
|Norwegisch|nein|
|norwegian-bokmal|nb-NO|
|norwegian-nynorsk|nn-NO|
|portuguese-brazilian|pt-BR|
|spanish-argentina|es-AR|
|spanish-bolivia|es-BO|
|spanish-chile|es-CL|
|spanish-colombia|es-CO|
|spanish-costa rica|es-CR|
|spanish-dominican republic|es-DO|
|spanish-ecuador|es-EC|
|spanish-el salvador|es-SV|
|spanish-guatemala|es-GT|
|spanish-honduras|es-HN|
|spanish-mexican|es-MX|
|spanish-modern|es-ES|
|spanish-nicaragua|es-NI|
|spanish-panama|es-PA|
|spanish-paraguay|es-PY|
|spanish-peru|es-PE|
|spanish-puerto rico|es-PR|
|spanish-uruguay|es-UY|
|spanish-venezuela|es-VE|
|swedish-finland|sv-FI|
|Schweizerisch|de-CH|
|uk|en-GB|
|USA|de-DE|
|usa|de-DE|

## <a name="see-also"></a>Weitere Informationen

[Gebietsschema-Namen, Sprachen und Zeichenfolgen für Länder und Regionen](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Country/Region Strings](../c-runtime-library/country-region-strings.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)

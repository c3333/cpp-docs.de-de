---
title: Gebietsschema-Namen, Sprachen und Zeichenfolgen für Länder und Regionen
description: Eine Übersicht über die Verwendung von Microsoft Universal CRT-Gebiets Schema, Sprache und Länder-und Regions Zeichenfolgen.
ms.topic: conceptual
ms.date: 12/10/2018
helpviewer_keywords:
- country/region strings
- localization, locale
- locales
- setlocale function
- language strings
ms.assetid: a0e5a0c5-5602-4da0-b65f-de3d6c8530a2
ms.openlocfilehash: fabb3cd584af6f6e19e2ac3444c76bede299dc8d
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91589925"
---
# <a name="ucrt-locale-names-languages-and-countryregion-strings"></a>UCRT: Gebietsschemanamen, Sprachen und Zeichenfolgen für Länder und Regionen

Das *locale*-Argument für die Funktionen [setlocale\_, wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md), [\_create\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) und [\_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md) kann mithilfe der Gebietsschemanamen, Sprachen, Länder-/Regionscodes und Codepages festgelegt werden, die von der Windows NLS API unterstützt werden. Das *locale*-Argument weist folgende Form auf:

> *locale* :: "*locale-Name*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\|"*Language* \[ **\_** _Country-Region_ \[ __.__ *Codepage*]] "<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\|"__.__ *Codepage*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| "C"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| ""<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| NULL

Die *locale-name*-Form ist eine kurze, von der IETF standardisierte Zeichenfolge, z.B. `en-US` für Englisch (USA) oder `bs-Cyrl-BA` für Bosnisch (Kyrillisch, Bosnien und Herzegowina). Diese Formen werden bevorzugt. Eine Liste der unterstützten Gebiets Schema Namen nach Version des Windows-Betriebssystems finden Sie in der Spalte **Sprachtag** der Tabelle in [Anhang a: Produktverhalten](/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c) in \[ MS-LCID]: Referenz zur Windows-Sprach Code Kennung (LCID). Unter dieser Ressource finden Sie die unterstützte Sprache, das Skript und die regionalen Teile der Gebietsschemanamen. Informationen zu den unterstützten Gebietsschemanamen ohne standardmäßige Sortierreihenfolge finden Sie in der Spalte des **Gebietsschemanamens** unter den [Sortierreihenfolgen-IDs](/windows/win32/Intl/sort-order-identifiers). Unter Windows 10 oder höher sind Gebiets Schema Namen zulässig, die gültigen [bcp-47-](https://tools.ietf.org/html/bcp47) sprach Tags entsprechen. `jp-US` z.B. ist ein gültiges BCP-47-Tag, für die locale-Funktion ist es jedoch effektiv nur `US`.

Die *Sprache* \[ **\_** _Country-Region_ \[ __.__ *Codepage*]] das Formular wird in den Gebiets Schema Einstellungen für eine Kategorie gespeichert, wenn eine Sprachen Zeichenfolge, eine Sprachen Zeichenfolge oder eine Zeichenfolge für ein Land oder eine Region verwendet wird Der Satz unterstützter Sprachzeichenfolgen wird in [Language Strings](../c-runtime-library/language-strings.md) beschrieben, und die Liste der unterstützten Land-/Regionszeichenfolgen wird in [Country/Region Strings](../c-runtime-library/country-region-strings.md) aufgeführt. Wenn die angegebene Sprache nicht dem angegebenen Land bzw. der angegebenen Region zugeordnet ist, wird in den Gebietsschemaeinstellungen die Standardsprache für das angegebene Land bzw. die angegebene Region gespeichert. Für Gebietsschema-Zeichenfolgen, die in Code eingebettet sind oder für den Speicher serialisiert sind, empfehlen wir diese Form nicht. Bei diesen Zeichenfolgen ist nämlich die Wahrscheinlichkeit größer, dass sie durch eine Betriebssystemaktualisierung geändert werden, als die Gebietsschema-Namensform.

Beim *code-page*-Wert handelt es sich um die dem Gebietsschema zugeordnete ANSI/OEM-Codepage. Die Codepage wird für Sie festgelegt, wenn Sie ein Gebietsschema nur nach Sprache oder nach Sprache und Land/Region angeben. Der spezielle Wert `.ACP` gibt die ANSI-Codepage für das Land bzw. die Region an. Der spezielle Wert `.OCP` gibt die OEM-Codepage für das Land bzw. die Region an. Wenn Sie beispielsweise `"Greek_Greece.ACP"` als das Gebietsschema angeben, wird das Gebietsschema als `Greek_Greece.1253` (die ANSI-Codepage für Griechisch) gespeichert, und wenn Sie `"Greek_Greece.OCP"` als das Gebietsschema angegeben, wird es als `Greek_Greece.737` (die OEM-Codepage für Griechisch) gespeichert. Weitere Informationen zu Codepages finden Sie unter [Codepages](../c-runtime-library/code-pages.md). Eine Liste der unter Windows unterstützten Codepages finden Sie unter den [Codepage-IDs](/windows/win32/Intl/code-page-identifiers).

Wenn Sie nur die Codepage zum Angeben des Gebietsschemas verwenden, werden Standardsprache und Standardland/-region des Benutzers verwendet, die von [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename) abgerufen werden. Wenn Sie beispielsweise `".1254"` (ANSI-Code für Türkisch) als Gebietsschema für einen für Englisch (USA) konfigurierten Benutzer angeben, wird `English_United States.1254` als Gebietsschema gespeichert. Die Verwendung dieser Form wird nicht empfohlen, da sie zu inkonsistentem Verhalten führen kann.

Ein *locale*-Argumentwert von `C` gibt die Umgebung mit minimaler ANSI-Konformität für die C-Übersetzung an. Das Gebiets Schema `C` geht davon aus, dass jeder **`char`** Datentyp 1 Byte und sein Wert immer kleiner als 256 ist. Wenn *locale* auf eine leere Zeichenfolge zeigt, ist das Gebietsschema die durch die Implementierung definierte native Umgebung.

Sie können für die Funktionen `setlocale` und `_wsetlocale` alle Gebietsschemakategorien gleichzeitig mithilfe der `LC_ALL` -Kategorie angeben. Die Kategorien können alle auf das gleiche Gebietsschema festgelegt werden, oder Sie können jede Kategorie einzeln festlegen, indem Sie ein Gebietsschemaargument mit dieser Form verwenden:

> *LC-ALL-specifier* :: *locale*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| \[**LC_COLLATE=**_locale_]\[**;LC_CTYPE=**_locale_]\[**;LC_MONETARY=**_locale_]\[**;LC_NUMERIC=**_locale_]\[**;LC_TIME=**_locale_]

Sie können mehrere Kategorientypen angeben, durch Semikolons getrennt. Bei nicht angegebenen Kategorientypen werden die aktuellen Gebietsschemaeinstellungen verwendet. Dieser Codeausschnitt legt beispielsweise das aktuelle Gebietsschema für alle Kategorien auf `de-DE` fest und legt dann die Kategorien `LC_MONETARY` auf `en-GB` und `LC_TIME` auf `es-ES` fest:

```C
_wsetlocale(LC_ALL, L"de-DE");
_wsetlocale(LC_ALL, L"LC_MONETARY=en-GB;LC_TIME=es-ES");
```

## <a name="utf-8-support"></a>UTF-8-Unterstützung

UTF-8-Unterstützung kann mithilfe der UTF-8-Codepage in der Gebiets Schema Zeichenfolge aktiviert werden. Weitere Informationen finden Sie im [Abschnitt UTF- `setlocale` 8-Unterstützung von](../c-runtime-library/reference/setlocale-wsetlocale.md#utf-8-support) .

## <a name="see-also"></a>Weitere Informationen

[C-Lauf Zeit Bibliotheks Referenz](../c-runtime-library/c-run-time-library-reference.md)<br/>
[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[Sprachzeichenfolgen](../c-runtime-library/language-strings.md)<br/>
[Zeichen folgen für Land/Region](../c-runtime-library/country-region-strings.md)

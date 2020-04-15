---
title: _setmbcp
ms.date: 4/2/2020
api_name:
- _setmbcp
- _o__setmbcp
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
- _setmbcp
- setmbcp
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
ms.openlocfilehash: 61086471c6194aaa8434d291647978bf891a8aea
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337595"
---
# <a name="_setmbcp"></a>_setmbcp

Legt eine neue Multibyte-Codepage fest.

## <a name="syntax"></a>Syntax

```C
int _setmbcp(
   int codepage
);
```

### <a name="parameters"></a>Parameter

*Codepage*<br/>
Neue Codepageeinstellung für gebietsschemaunabhängige Multibyte-Routinen.

## <a name="return-value"></a>Rückgabewert

Gibt 0 zurück, wenn die Codepage erfolgreich festgelegt wurde. Wenn ein ungültiger Codepagewert für *die Codepage*angegeben wird, gibt -1 zurück, und die Codepage-Einstellung bleibt unverändert. Legt **errno** auf **EINVAL** fest, wenn ein Speicherzuweisungsfehler auftritt.

## <a name="remarks"></a>Bemerkungen

Die **funktion _setmbcp** gibt eine neue Multibyte-Codepage an. Standardmäßig legt das Laufzeitsystem automatisch die Multibyte-Codepage auf die Systemstandard-ANSI-Codepage fest. Die Multibyte-Codepageeinstellung wirkt sich auf alle Multibyteroutinen auf, die nicht vom Gebietsschema abhängig sind. Es ist jedoch möglich, **_setmbcp** anzuweisen, die für das aktuelle Gebietsschema definierte Codepage zu verwenden (siehe folgende Liste der Manifestkonstanten und zugehörigen Verhaltensergebnisse). Eine Liste der Multibyteroutinen, die von der Gebietsschema-Codepage und nicht von der Multibyte-Codepage abhängig sind, finden Sie unter [Interpretation von Multybite-Zeichensequenzen](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md).

Die Multibyte-Codepage hat auch Auswirkungen auf die Multibyteverarbeitung durch die folgenden Routinen der Laufzeitbibliothek:

||||
|-|-|-|
|[_exec functions](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[_spawn-Funktionen](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

Darüber hinaus verarbeiten alle Laufzeitbibliotheksroutinen, die *argv-* oder *envp-Programmargumente* mit mehreren Byte-Zeichen als Parameter empfangen (z. B. **die _exec** und **_spawn** Familien), diese Zeichenfolgen gemäß der Multibyte-Codepage. Daher werden diese Routinen auch durch einen Aufruf an **_setmbcp** beeinflusst, der die Multibyte-Codepage ändert.

Das *Codepage-Argument* kann auf einen der folgenden Werte festgelegt werden:

- **_MB_CP_ANSI** Verwenden Sie die ANSI-Codepage, die vom Betriebssystem beim Programmstart abgerufen wurde.

- **_MB_CP_LOCALE** Verwenden Sie die Codepage des aktuellen Gebietsschemas, die sie von einem vorherigen Aufruf erhalten hat, um [setlocale](setlocale-wsetlocale.md).

- **_MB_CP_OEM** Verwenden Sie die OEM-Codepage, die vom Betriebssystem beim Programmstart abgerufen wurde.

- **_MB_CP_SBCS** Verwenden Sie die Einzelbyte-Codepage. Wenn die Codepage auf **_MB_CP_SBCS**festgelegt ist, gibt eine Routine wie [_ismbblead](ismbblead-ismbblead-l.md) immer false zurück.

- **_MB_CP_UTF8** Verwenden Sie UTF-8.  Wenn die Codepage auf **_MB_CP_UTF8**festgelegt ist, gibt eine Routine wie [_ismbblead](ismbblead-ismbblead-l.md) immer false zurück.

- Jeder andere gültige Codepagewert, unabhängig davon, ob es sich um eine ANSI-, OEM- oder eine andere vom Betriebssystem unterstützte Codepage handelt (außer UTF-7, das nicht unterstützt wird).

Standardmäßig ist der globale Status dieser Funktion auf die Anwendung beschränkt. Informationen dazu finden Sie [unter Globaler Status in der CRT](../global-state.md).

## <a name="requirements"></a>Anforderungen

|Routine|Erforderlicher Header|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

Weitere Informationen zur Kompatibilität finden Sie unter [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Siehe auch

[_getmbcp](getmbcp.md)<br/>
[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>

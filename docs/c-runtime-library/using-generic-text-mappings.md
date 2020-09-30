---
title: Verwenden von Zuordnungen für generischen Text
description: Eine Einführung in Microsoft-spezifische Zuordnungen für Datentypen, Routinen und andere Objekte in der C-Laufzeit.
ms.topic: conceptual
ms.date: 11/04/2016
f1_keywords:
- _UNICODE
helpviewer_keywords:
- _TXCHAR type
- TINT type
- _TCHAR type
- TSCHAR type
- TEXT type
- TCHAR type
- TCHAR.H data types, mappings defined in
- generic-text data types
- _TINT type
- TUCHAR type
- _UNICODE constant
- TXCHAR type
- generic-text mappings
- _TSCHAR type
- T type
- mappings, generic-text
- _TUCHAR type
- MBCS data type
- _MBCS data type
- _TEXT type
- UNICODE constant
- _T type
ms.assetid: 2848121c-e51f-4b9b-a2e6-833ece4b0cb3
ms.openlocfilehash: ea3b1eef413a0d9f52e81795c04424d533b83504
ms.sourcegitcommit: 9451db8480992017c46f9d2df23fb17b503bbe74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91590107"
---
# <a name="using-generic-text-mappings"></a>Verwenden von Zuordnungen für generischen Text

**Microsoft-spezifisch**

Um die Codeentwicklung für internationale Märkte zu vereinfachen, stellt die Microsoft-Laufzeitbibliothek für viele Datentypen, Routinen und andere Objekte Microsoft-spezifische Zuordnungen für generischen Text zur Verfügung. Diese Zuordnungen werden in TCHAR.H definiert. Sie können mithilfe dieser Namenszuordnungen generischen Code schreiben, der für die folgenden drei Arten von Zeichensätzen kompiliert werden kann: ASCII (SBCS), MBCS oder Unicode. Dies hängt von der Manifestkonstante ab, die Sie mit einer `#define`-Anweisung definieren. Generische Textzuordnungen sind Microsoft-Erweiterungen, die nicht mit ANSI kompatibel sind.

### <a name="preprocessor-directives-for-generic-text-mappings"></a>Präprozessordirektiven zum Zuordnen von generischem Text

|#define|Kompilierte Version|Beispiel|
|--------------|----------------------|-------------|
|`_UNICODE`|Unicode (Breitzeichen)|`_tcsrev` ist `_wcsrev` zugeordnet.|
|`_MBCS`|Mehrbytezeichen|`_tcsrev` ist `_mbsrev` zugeordnet.|
|Keine (bei der Standardeinstellung ist weder `_UNICODE` noch `_MBCS` definiert)|SBCS (ASCII)|`_tcsrev` ist `strrev` zugeordnet.|

Die in TCHAR.H definierte generische Textfunktion `_tcsrev` wird der `mbsrev`-Funktion zugeordnet, wenn `MBCS` in Ihrem Programm definiert wurde, oder sie wird `_wcsrev` zugeordnet, wenn `_UNICODE` definiert wurde. Andernfalls wird `_tcsrev``strrev` zugeordnet.

Der generische Text Datentyp `_TCHAR` , der auch in Tchar definiert ist. H, wird dem Typ zugeordnet, **`char`** Wenn `_MBCS` definiert ist, zum Typ, **`wchar_t`** Wenn `_UNICODE` definiert ist, und zum eingeben, **`char`** Wenn keine Konstante definiert ist. Zur Vereinfachung der Programmierung werden in TCHAR.H weitere Datentypzuordnungen zur Verfügung gestellt; `_TCHAR` ist jedoch die hilfreichste Zuordnung.

### <a name="generic-text-data-type-mappings"></a>Generische Textzuordnungen von Datentypen

|Datentypname für generischen Text|SBCS (_UNICODE & MBCS nicht definiert)|_MBCS definiert|_UNICODE definiert|
|----------------------------------|--------------------------------------------|--------------------|-----------------------|
|`_TCHAR`|**`char`**|**`char`**|**`wchar_t`**|
|`_TINT`|**`int`**|**`int`**|`wint_t`|
|`_TSCHAR`|**`signed char`**|**`signed char`**|**`wchar_t`**|
|`_TUCHAR`|**`unsigned char`**|**`unsigned char`**|**`wchar_t`**|
|`_TXCHAR`|**`char`**|**`unsigned char`**|**`wchar_t`**|
|`_T` oder `_TEXT`|Ohne Auswirkung (wird vom Präprozessor entfernt)|Ohne Auswirkung (wird vom Präprozessor entfernt)|`L` (konvertiert das nächste Zeichen oder die nächste Zeichenfolge in die Unicode-Entsprechung)|

Eine vollständige Liste mit generischen Textzuordnungen von Routinen, Variablen und anderen Objekten finden Sie unter [Generische Textzuordnungen](../c-runtime-library/generic-text-mappings.md).

Aus den folgenden Codefragmenten geht hervor, wie `_TCHAR` und `_tcsrev` für die Zuordnung zu den MBCS-, Unicode- und SBCS-Modellen verwendet werden.

```
_TCHAR *RetVal, *szString;
RetVal = _tcsrev(szString);
```

Wenn `MBCS` definiert wurde, ordnet der Präprozessor dem vorangehenden Fragment folgenden Code zu:

```
char *RetVal, *szString;
RetVal = _mbsrev(szString);
```

Wenn `_UNICODE` definiert wurde, ordnet der Präprozessor diesem Fragment folgenden Code zu:

```
wchar_t *RetVal, *szString;
RetVal = _wcsrev(szString);
```

Wenn weder `_MBCS` noch `_UNICODE` definiert wurde, ordnet der Präprozessor dem Einzelbyte-ASCII-Code das Fragment wie folgt zu:

```
char *RetVal, *szString;
RetVal = strrev(szString);
```

Daher können Sie eine einzige Quellcodedatei so schreiben, verwalten und kompilieren, dass sie mit Routinen ausgeführt wird, die jeweils speziell auf einen der drei Zeichensätze ausgerichtet sind.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[Zuordnungen für generischen Text](../c-runtime-library/generic-text-mappings.md)<br/>
[Datentyp Zuordnungen](../c-runtime-library/data-type-mappings.md)<br/>
[Zuordnungen von Konstanten und globalen Variablen](../c-runtime-library/constant-and-global-variable-mappings.md)<br/>
[Routine Zuordnungen](../c-runtime-library/routine-mappings.md)<br/>
[Ein Beispiel für ein generisches Text Programm](../c-runtime-library/a-sample-generic-text-program.md)

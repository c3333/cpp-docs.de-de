---
title: Datentypzuordnungen
ms.date: 11/04/2016
f1_keywords:
- _TXCHAR
- _TUCHAR
- _TINT
- _TSCHAR
- _TCHAR
- TCHAR::H
- TCHAR
- _T
- _TEXT
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
- TXCHAR type
- _TSCHAR type
- T type
- _TUCHAR type
- _TEXT type
- _T type
ms.assetid: 4e573c05-8800-468b-ae5f-76ff7409835e
ms.openlocfilehash: d77ac4fa9afcd5a6b8f86261c7a3ba466adc64a4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215152"
---
# <a name="data-type-mappings"></a>Datentypzuordnungen

Diese Datentypzuordnungen werden in TCHAR.H definiert und hängen davon ab, ob die Konstante `_UNICODE` oder die Konstante `_MBCS` im Programm definiert wurde.

Entsprechende Informationen finden Sie unter [Using TCHAR.H Data Types with _MBCS Code (Verwenden von TCHAR.H-Datentypen in _MBCS-Code)](../text/using-tchar-h-data-types-with-mbcs-code.md).

### <a name="generic-text-data-type-mappings"></a>Generische Textzuordnungen von Datentypen

|Generischer Textname von<br /><br /> Datentypen|SBCS (_UNICODE,<br /><br /> _MBCS nicht<br /><br /> definiert)|_MBCS<br /><br /> definiert|_UNICODE<br /><br /> definiert|
|--------------------------------------|----------------------------------------------------|------------------------|---------------------------|
|`_TCHAR`|**`char`**|**`char`**|**`wchar_t`**|
|`_tfinddata_t`|`_finddata_t`|`_finddata_t`|`_wfinddata_t`|
|`_tfinddata64_t`|`__finddata64_t`|`__finddata64_t`|`__wfinddata64_t`|
|`_tfinddatai64_t`|`_finddatai64_t`|`_finddatai64_t`|`_wfinddatai64_t`|
|`_TINT`|**`int`**|**`int`**|`wint_t`|
|`_TSCHAR`|**`signed char`**|**`signed char`**|**`wchar_t`**|
|`_TUCHAR`|**`unsigned char`**|**`unsigned char`**|**`wchar_t`**|
|`_TXCHAR`|**`char`**|**`unsigned char`**|**`wchar_t`**|
|`_T` oder `_TEXT`|Ohne Auswirkung (wird vom Präprozessor entfernt)|Ohne Auswirkung (wird vom Präprozessor entfernt)|`L` (konvertiert das nächste Zeichen oder die nächste Zeichenfolge in die Unicode-Entsprechung)|

## <a name="see-also"></a>Weitere Informationen

[Zuordnungen für generischen Text](../c-runtime-library/generic-text-mappings.md)<br/>
[Zuordnungen von Konstanten und globalen Variablen](../c-runtime-library/constant-and-global-variable-mappings.md)<br/>
[Routine Zuordnungen](../c-runtime-library/routine-mappings.md)<br/>
[Ein Beispiel für ein generisches Text Programm](../c-runtime-library/a-sample-generic-text-program.md)<br/>
[Verwenden von Zuordnungen für generischen Text](../c-runtime-library/using-generic-text-mappings.md)

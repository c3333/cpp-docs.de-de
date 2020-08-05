---
title: chars_format-Aufzählung
ms.date: 08/03/2020
f1_keywords:
- charconv/std::chars_format
helpviewer_keywords:
- std::chars_format
ms.openlocfilehash: d7f95d9bd1522fa0896ccdbac6c1dbc770f2b272
ms.sourcegitcommit: 4eda68a0b3c23d8cefa56b7ba11583412459b32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87565935"
---
# <a name="chars_format-enum"></a>chars_format-Aufzählung

Wird mit der- [\<charconv>](charconv.md) Bibliothek verwendet, um das Gleit Komma Format für primitive numerische Konvertierungen anzugeben.

## <a name="syntax"></a>Syntax

```cpp
enum class chars_format {
    scientific = unspecified,
    fixed = unspecified,
    hex = unspecified,
    general = fixed | scientific
};
```

### <a name="members"></a>Member

|Element|BESCHREIBUNG|
|-|-|
| `scientific` | Veranlasst `from_chars()` , einen Exponenten zu erwarten und zu analysieren. Dies entspricht dem Format Bezeichner `printf()` `'e'` , der für wissenschaftliche Schreibweise formatiert, wie z `"1.729e+01"` . b.. |
| `fixed` | Bewirkt `from_chars()` , dass kein Exponent erwartet oder analysiert wird. Dies entspricht dem Format Bezeichner `printf()` `'f'` , der für Gleit Komma Formate formatiert, wie z `"17.29"` . b..|
| `hex` | Bewirkt `from_chars()` , dass die Zahl im Hexadezimal Format erwartet, aber ohne einen führenden `0x` . |
| `general` | Bewirkt `from_chars()` , dass einen Exponenten annimmt (aber nicht erfordert). Für `to_chars()` ist es wie der Format Bezeichner `printf()` `'g'` , der zwischen wissenschaftlicher Schreibweise wechselt oder fest ist. Es wird berücksichtigt, was der Exponent sein wird, damit er eine relativ kompakte Ausgabe generieren kann. Beispiel: `1e-5` ergibt `"1e-05"` , führt jedoch zu `1e-4` `"0.001"` . `1e5`ergibt `100000` , während sich `1e6` ergibt `1e+06` . `1e0`erzeugt `1` .|

## <a name="remarks"></a>Bemerkungen

Für die [from_chars](charconv-functions.md#from_chars) Funktionen beschreibt diese Aufzählung, welche Art von Eingabe erwartet wird.
Für die [to_chars](charconv-functions.md#to_chars) Funktionen wird beschrieben, welche Art von Ausgabe ausgegeben werden soll.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<charconv>

**Namespace:** std

/Std: c++ 17 (oder höher) ist erforderlich.

## <a name="see-also"></a>Weitere Informationen

[\<charconv>](../standard-library/charconv.md)  
[printf ()-Formatspezifizierer](..\c-runtime-library\format-specification-syntax-printf-and-wprintf-functions.md)

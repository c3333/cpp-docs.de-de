---
title: chars_format-Aufzählung
ms.date: 07/22/2020
f1_keywords:
- charconv/std::chars_format
helpviewer_keywords:
- std::chars_format
ms.openlocfilehash: 4c1d495c943be02b66d52d1986a783b29a8009c5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230181"
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

|Element|Beschreibung|
|-|-|
| `scientific` | Veranlasst `from_chars()` , einen Exponenten zu erwarten und zu analysieren. Dies entspricht dem Format Bezeichner `'e'` `printf()` , der für die wissenschaftliche Notation formatiert, z. b.`"1.729e+01"` |
| `fixed` | Bewirkt `from_chars()` , dass kein Exponent erwartet oder analysiert wird. Dies entspricht dem Format Bezeichner `'f'` `printf()` , der für Gleit Komma Formate formatiert, z `"17.29"` . b..|
| `hex` | Bewirkt `from_chars()` , dass die Zahl im Hexadezimal Format erwartet, aber ohne eine führende "0x". |
| `general` | Bewirkt `from_chars()` , dass einen Exponenten annimmt (aber nicht erfordert). Für `to_chars()` ist es wie der `g` printf ()-Format Bezeichner, der zwischen wissenschaftlicher Schreibweise wechselt oder fest ist. Es wird berücksichtigt, was der Exponent sein wird, damit er eine relativ kompakte Ausgabe generieren kann. Beispiel: `1e-5` ergibt `"1e-05"` , führt jedoch zu `1e-4` `"0.001"` . `1e5`ergibt `100000` , während sich `1e6` ergibt `1e+06` . `1e0`erzeugt `1` .|

## <a name="remarks"></a>Bemerkungen

Für die [from_chars](charconv-functions.md#from_chars) Funktionen beschreibt diese Aufzählung, welche Art von Eingabe erwartet wird.
Für die [to_chars](charconv-functions.md#to_chars) Funktionen wird beschrieben, welche Art von Ausgabe ausgegeben werden soll.

## <a name="see-also"></a>Siehe auch

[\<charconv>](../standard-library/charconv.md)  
[printf ()-Formatspezifizierer](..\c-runtime-library\format-specification-syntax-printf-and-wprintf-functions.md)

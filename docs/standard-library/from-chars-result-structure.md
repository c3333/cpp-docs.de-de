---
title: from_chars_result-Struktur
ms.date: 7/23/2020
f1_keywords:
- std::from_chars_result
helpviewer_keywords:
- from_chars_result class
- from_chars_result structure
ms.openlocfilehash: 5a5dcfe6e5b59644e6ebf55d68ce43975e7d3c9d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215763"
---
# <a name="from_chars_result-struct"></a>from_chars_result-Struktur

## <a name="syntax"></a>Syntax

```cpp
struct from_chars_result {
    const char* ptr;
    errc ec;
};
```

|Member|Beschreibung|
|--|--|
|`ptr`| Wenn `ec` gleich ist `errc{}` , war die Konvertierung erfolgreich und `ptr` zeigt auf das erste Zeichen, das nicht Teil der erkannten Zahl ist. |
|`ec` | Der Konvertierungs Fehlercode. Bestimmte Fehlercodes finden Sie unter [`errc`](system-error-enums.md#errc) .|

### <a name="remarks"></a>Bemerkungen

Beispiel: `"1729cats"` das Auswerten als ganze Dezimalzahl ist erfolgreich, und zeigt `ptr` auf, `'c'` welches die erste nicht-Ziffer ist und auch ein- `"1729"` nach-unten-Element von ist.

Wenn keine Zeichen einem Zahlenmuster entsprechen, `from_chars_result.ptr` verweist auf `first` , und `from_chars_result.ec` ist `errc::invalid_argument` .

Wenn nur einige Zeichen mit einem Zahlenmuster übereinstimmen, `from_chars_result.ptr` zeigt auf das erste Zeichen, das nicht mit dem Muster übereinstimmt, oder hat den Wert des `last` Parameters, wenn alle Zeichen übereinstimmen.

Wenn der analysierte Wert nicht mit dem Bereich für den Konvertierungstyp, der ausgeführt wird, entspricht, `from_chars_result.ec` ist `errc::result_out_of_range` .

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<charconv>

**Namespace:** std

**Compileroption:** /Std: c++ 17 (oder höher) ist erforderlich.

## <a name="see-also"></a>Weitere Informationen

[from_chars](charconv-functions.md#from_chars)

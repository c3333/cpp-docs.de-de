---
title: to_chars_result-Struktur
ms.date: 07/22/2020
f1_keywords:
- charconv/std::to_chars_result
helpviewer_keywords:
- to_chars_result class
- to_chars_result structure
ms.openlocfilehash: 4e46d1cc9d0b6a02d731ad25c2e85c99300d7234
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509644"
---
# <a name="to_chars_result-struct"></a>to_chars_result-Struktur

## <a name="syntax"></a>Syntax

```cpp
struct to_chars_result {
    char* ptr;
    errc ec;
};
```

## <a name="members"></a>Members

|Member|Beschreibung|
|--|--|
|`ptr`| Wenn `ec` gleich ist `errc{}` , war die Konvertierung erfolgreich und `ptr` ist der 1-nach-Ende-Zeiger der geschriebenen Zeichen. Andernfalls `ptr` weist den Wert des `to_chars()` -Parameters auf `last` , und der Inhalt des Bereichs \[ First, Last) ist nicht angegeben.|
|`ec` | Der Konvertierungs Fehlercode. Bestimmte Fehlercodes finden Sie unter [`errc`](system-error-enums.md#errc) .|

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<charconv>

**Namespace:** std

**Compileroption:** /Std: c++ 17 (oder höher) ist erforderlich.

## <a name="see-also"></a>Weitere Informationen

[to_chars](charconv-functions.md#to_chars)

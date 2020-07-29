---
title: Datentypbereiche
ms.date: 05/28/2020
helpviewer_keywords:
- float keyword [C++]
- char keyword [C++]
- unsigned long
- __wchar_t keyword [C++]
- unsigned short int [C++]
- enum keyword [C++]
- unsigned char keyword [C++]
- integer data type [C++], data type ranges
- int data type
- data types [C++], ranges
- unsigned int [C++]
- short data type
- short int data
- signed types [C++], data type ranges
- long long keyword [C++]
- long double keyword [C++]
- double data type [C++], data type ranges
- signed short int [C++]
- unsigned short
- sized integer types
- signed int [C++]
- signed long int [C++]
- signed char keyword [C++]
- wchar_t keyword [C++]
- long keyword [C++]
- ranges [C++]
- unsigned types [C++], data type ranges
- floating-point numbers [C++]
- data type ranges
- ranges [C++], data types
- long int keyword [C++]
- unsigned long int [C++]
ms.assetid: 3691ceca-05fb-4b82-b1ae-5c4618cda91a
ms.openlocfilehash: f7658d0c0a61180193de268414e214595198e8fa
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228972"
---
# <a name="data-type-ranges"></a>Datentypbereiche

Die Microsoft C++ 32-Bit-und 64-Bit-Compiler erkennen die Typen in der Tabelle weiter unten in diesem Artikel.

- **`int`** (**`unsigned int`**)

- **`__int8`** (**`unsigned __int8`**)

- **`__int16`** (**`unsigned __int16`**)

- **`__int32`** (**`unsigned __int32`**)

- **`__int64`** (**`unsigned __int64`**)

- **`short`** (**`unsigned short`**)

- **`long`** (**`unsigned long`**)

- **`long long`** (**`unsigned long long`**)

Wenn der Name mit zwei Unterstrichen (`__`) beginnt, handelt es sich um einen nicht standardisierten Datentyp.

Die Bereiche, die in der folgenden Tabelle angegeben werden, sind "inclusive-inclusive".

|Typname|Byte|Andere Namen|Wertebereich|
|---------------|-----------|-----------------|---------------------|
|**`int`**|4|**`signed`**|-2,147,483,648 bis 2,147,483,647|
|**`unsigned int`**|4|**`unsigned`**|0 bis 4.294.967.295|
|**`__int8`**|1|**`char`**|–128 bis 127|
|**`unsigned __int8`**|1|**`unsigned char`**|0 bis 255|
|**`__int16`**|2|**`short`**, **`short int`**, **`signed short int`**|–32.768 bis 32.767|
|**`unsigned __int16`**|2|**`unsigned short`**, **`unsigned short int`**|0 bis 65.535|
|**`__int32`**|4|**`signed`**, **`signed int`**, **`int`**|-2,147,483,648 bis 2,147,483,647|
|**`unsigned __int32`**|4|**`unsigned`**, **`unsigned int`**|0 bis 4.294.967.295|
|**`__int64`**|8|**`long long`**, **`signed long long`**|-9,223,372,036,854,775,808 bis 9,223,372,036,854,775,807|
|**`unsigned __int64`**|8|**`unsigned long long`**|0 bis 18.446.744.073.709.551.615|
|**`bool`**|1|Keine|**`false`** oder **`true`**|
|**`char`**|1|Keine|-128 bis 127 standardmäßig<br /><br /> 0 bis 255 bei der Kompilierung mit[`/J`](../build/reference/j-default-char-type-is-unsigned.md)|
|**`signed char`**|1|Keine|–128 bis 127|
|**`unsigned char`**|1|Keine|0 bis 255|
|**`short`**|2|**`short int`**, **`signed short int`**|–32.768 bis 32.767|
|**`unsigned short`**|2|**`unsigned short int`**|0 bis 65.535|
|**`long`**|4|**`long int`**, **`signed long int`**|-2,147,483,648 bis 2,147,483,647|
|**`unsigned long`**|4|**`unsigned long int`**|0 bis 4.294.967.295|
|**`long long`**|8|None (jedoch Äquivalent zu **`__int64`** )|-9,223,372,036,854,775,808 bis 9,223,372,036,854,775,807|
|**`unsigned long long`**|8|None (jedoch Äquivalent zu **`unsigned __int64`** )|0 bis 18.446.744.073.709.551.615|
|**`enum`**|Variiert|Keine| |
|**`float`**|4|Keine|3.4E +/- 38 (7 Stellen)|
|**`double`**|8|Keine|1.7E +/- 308 (15 Stellen)|
|**`long double`**|identisch mit**`double`**|Keine|Identisch mit**`double`**|
|**`wchar_t`**|2|**`__wchar_t`**|0 bis 65.535|

Abhängig davon, wie Sie verwendet wird, kennzeichnet eine Variable von **`__wchar_t`** entweder einen breit Zeichentyp oder einen Multibyte-Zeichentyp. Verwenden Sie das Präfix `L` vor einem Zeichen oder einer Zeichenfolgenkonstante, um eine Breitzeichenkonstante festzulegen.

**`signed`** und **`unsigned`** sind modifiziererer, die Sie mit jedem ganzzahligen Typ außer verwenden können **`bool`** . Beachten Sie, dass **`char`** , **`signed char`** und **`unsigned char`** drei verschiedene Typen für Mechanismen wie überladen und Vorlagen sind.

Der **`int`** -Typ und der- **`unsigned int`** Typ haben eine Größe von vier Bytes. Portabler Code sollte jedoch nicht von der Größe von abhängen, **`int`** da der Sprachstandard dies Implementierungs spezifisch ist.

C/C++ in Visual Studio bietet Unterstützung für ganzzahlige Typen mit angegebener Größe. Weitere Informationen finden Sie unter [`__int8, __int16, __int32, __int64`](../cpp/int8-int16-int32-int64.md) und [ganzzahlige Grenzwerte](../cpp/integer-limits.md).

Weitere Informationen zu den Einschränkungen der einzelnen Typen finden Sie unter [integrierte Typen](../cpp/fundamental-types-cpp.md).

Der Bereich von Enumerationstypen variiert je nach Sprachkontext und angegebenen Compilerflags. Weitere Informationen finden Sie unter [C Enumeration Declarations (C-Enumerationsdeklarationen)](../c-language/c-enumeration-declarations.md) und [Enumerations (Enumerationen)](../cpp/enumerations-cpp.md).

## <a name="see-also"></a>Siehe auch

[Schlüsselwörter](../cpp/keywords-cpp.md)<br/>
[Integrierte Typen](../cpp/fundamental-types-cpp.md)

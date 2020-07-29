---
title: char, wchar_t, char16_t, char32_t
ms.date: 02/14/2018
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
ms.openlocfilehash: 6efbae1b8f6155410b823f1abef35c3dec90d458
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232338"
---
# <a name="char-wchar_t-char16_t-char32_t"></a>char, wchar_t, char16_t, char32_t

Die Typen **`char`** , **`wchar_t`** **`char16_t`** und **`char32_t`** sind integrierte Typen, die alphanumerische Zeichen sowie nicht alphanumerische Symbole und nicht Druck bare Zeichen darstellen.

## <a name="syntax"></a>Syntax

```cpp
char     ch1{ 'a' };  // or { u8'a' }
wchar_t  ch2{ L'a' };
char16_t ch3{ u'a' };
char32_t ch4{ U'a' };
```

## <a name="remarks"></a>Bemerkungen

Der **`char`** Typ war der ursprüngliche Zeichentyp in C und C++. Der-Typ **`unsigned char`** wird häufig zur Darstellung eines *Byte*verwendet, bei dem es sich nicht um einen integrierten Typ in C++ handelt. Der **`char`** -Typ kann verwendet werden, um Zeichen aus dem ASCII-Zeichensatz oder einem der ISO-8859-Zeichensätze sowie aus einzelnen Bytes von Multibytezeichen (z. b. Shift-JIS) oder der UTF-8-Codierung des Unicode-Zeichensatzes zu speichern. Zeichen folgen vom **`char`** Typ werden als *schmale* Zeichen folgen bezeichnet, auch wenn Sie zum Codieren von Multibytezeichen verwendet werden. Im Microsoft-Compiler **`char`** ist ein 8-Bit-Typ.

Der **`wchar_t`** Typ ist ein von der Implementierung definierter breit Zeichentyp. Im Microsoft-Compiler stellt Sie ein 16-Bit-breit Zeichen dar, das verwendet wird, um Unicode-codiert als UTF-16LE, den nativen Zeichentyp unter Windows-Betriebssystemen, zu speichern. Die breit Zeichen Versionen der ucrt-Bibliotheksfunktionen (Universal C Runtime) verwenden **`wchar_t`** und deren Zeiger-und Array Typen als Parameter und Rückgabewerte, ebenso wie die breit Zeichen Versionen der systemeigenen Windows-API.

Der **`char16_t`** -Typ und der- **`char32_t`** Typ stellen jeweils 16-Bit-und 32-Bit-breit Zeichen dar. Unicode-codiert als UTF-16 kann im **`char16_t`** -Typ gespeichert werden, und Unicode-codiert als UTF-32 kann im-Typ gespeichert werden **`char32_t`** . Zeichen folgen dieser Typen und **`wchar_t`** werden alle als *Breite* Zeichen folgen bezeichnet, obwohl der Begriff häufig speziell auf Zeichen folgen vom **`wchar_t`** Typ verweist.

In der C++-Standardbibliothek `basic_string` ist der-Typ sowohl für schmale als auch für Breite Zeichen folgen spezialisiert. Verwenden Sie, wenn die Zeichen vom Typ sind, wenn die Zeichen vom Typ sind, `std::string` **`char`** `std::u16string` **`char16_t`** `std::u32string` Wenn die Zeichen vom Typ sind **`char32_t`** und `std::wstring` die Zeichen den Typ aufweisen **`wchar_t`** . Andere Typen, die Text darstellen, einschließlich und, weisen `std::stringstream` `std::cout` Spezialisierungs-und breit Zeichenfolgen auf.

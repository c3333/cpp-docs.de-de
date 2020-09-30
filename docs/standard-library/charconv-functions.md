---
title: '&lt;chardev- &gt; Funktionen'
description: Beschreibt die <charconv> Bibliotheksfunktionen, die ganzzahlige oder Gleit Komma Werte in oder aus Zeichen konvertieren.
ms.date: 08/20/2020
f1_keywords:
- charconv/std::to_chars
- charconv/std::from_chars
helpviewer_keywords:
- std::charconv [C++], to_chars
- std::charconv [C++], from_chars
ms.openlocfilehash: cde2ae6b6275543ec74d859b9a953f8673da9c2b
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507752"
---
# <a name="ltcharconvgt-functions"></a>&lt;chardev- &gt; Funktionen

Der- \<charconv> Header enthält die folgenden nicht-Member-Funktionen:

| **Nicht-Member-Funktionen** | **Beschreibung** |
|-|-|
|[to_chars](#to_chars) | Konvertiert eine Ganzzahl oder einen Gleit Komma Wert in eine Sequenz von **`char`** . |
|[from_chars](#from_chars) | Konvertieren einer Sequenz von **`char`** in eine Ganzzahl oder einen Gleit Komma Wert. |

Diese Konvertierungs Funktionen werden auf die Leistung optimiert und unterstützen auch das kürzeste Roundtrip-Verhalten. Das kürzeste Roundtrip-Verhalten bedeutet, dass bei der Konvertierung einer Zahl in Zeichen nur ausreichend Genauigkeit ausgegeben wird, um das Wiederherstellen der ursprünglichen Anzahl bei der Wiederherstellung dieser Zeichen in einen Gleit Komma Wert zu ermöglichen.

- Beim Umrechnen von Zeichen in eine Zahl muss der numerische Wert nicht auf Null enden. Ebenso gilt, wenn eine Zahl in Zeichen umgerechnet wird, das Ergebnis nicht mit NULL endet.
- Die Konvertierungs Funktionen weisen keinen Arbeitsspeicher zu. Sie besitzen den Puffer in allen Fällen.
- Die Konvertierungs Funktionen lösen nicht aus. Es wird ein Ergebnis zurückgegeben, aus dem Sie ermitteln können, ob die Konvertierung erfolgreich abgeschlossen wurde.
- Bei den Konvertierungs Funktionen handelt es sich nicht um eine empfindliche Laufzeit.
- Die Konvertierungs Funktionen sind nicht Gebiets Schema fähig. Sie drucken und analysieren immer Dezimalstellen als und `'.'` nie als ', ' für Gebiets Schemas, die Kommas verwenden.

## `to_chars`

Konvertiert eine Ganzzahl oder einen Gleit Komma Wert in eine Sequenz von **`char`** .

Konvertiert `value` in eine Zeichenfolge, indem der Bereich ausgefüllt wird, \[ `first` `last` wobei \[ `first` , `last` ) ein gültiger Bereich sein muss.
Gibt eine [to_chars_result-Struktur](to-chars-result-structure.md)zurück. Wenn die Konvertierung erfolgreich ist, wie durch angegeben `to_char_result.ec` , ist der Member der `ptr` 1-Past-the-End-Zeiger der geschriebenen Zeichen. Andernfalls `to_char_result.ec` hat den Wert `errc::value_too_large` , `to_char_result.ptr` hat den Wert `last` , und der Inhalt des Bereichs \[ `first` ,) ist `last` nicht angegeben.

Die einzige Möglichkeit, die `to_chars` fehlschlagen kann, ist, wenn Sie einen nicht ausreichend großen Puffer für das Ergebnis bereitstellen.

```cpp
// integer to chars

to_chars_result to_chars(char* first, char* last, char value, int base = 10);
to_chars_result to_chars(char* first, char* last, signed char value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned char value, int base = 10);
to_chars_result to_chars(char* first, char* last, short value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned short value, int base = 10);
to_chars_result to_chars(char* first, char* last, int value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned int value, int base = 10);
to_chars_result to_chars(char* first, char* last, long value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned long value, int base = 10);
to_chars_result to_chars(char* first, char* last, long long value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned long long value, int base = 10);
to_chars_result to_chars(char* first, char* last, bool value, int base = 10) = delete;

// floating-point to chars

to_chars_result to_chars(char* first, char* last, float value);
to_chars_result to_chars(char* first, char* last, double value);
to_chars_result to_chars(char* first, char* last, long double value);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt, int precision);
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt, int precision);
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt, int precision);
```

### <a name="parameters"></a>Parameter

*erstes*\
Zeigt auf den Anfang des zu füllenden Puffers.

*letzten*\
Zeigt ein Zeichen hinter dem Ende des Puffers an, das ausgefüllt werden soll.

*Wert*\
Der zu konvertierende Wert. Wenn `value` negativ ist, beginnt die Darstellung mit `-` .

*sock*\
Bei ganzzahligen Konvertierungen die Basis, die beim Konvertieren in Zeichen verwendet werden soll `value` . Muss zwischen 2 und 36 (einschließlich) liegen. Es gibt keine führenden Nullen. Ziffern im Bereich 10.. 35 (einschließlich) werden als Kleinbuchstaben dargestellt. z

*fmt*\
Eine Bitmaske für Gleit Komma Konvertierungen, die das zu verwendende Konvertierungs Format angibt, z. b. Scientific, Fixed oder hexadezimal. Weitere Informationen finden Sie unter [chars_format](chars-format-class.md) .

*präziser*\
Für Gleit Komma Konvertierungen die Anzahl der Ziffern der Genauigkeit für den konvertierten Wert.

### <a name="return-value"></a>Rückgabewert

Eine [to_chars_result](to-chars-result-structure.md) , die das Ergebnis der Konvertierung enthält.

### <a name="remarks"></a>Bemerkungen

Funktionen, die einen [chars_format](chars-format-class.md) -Parameter verwenden, bestimmen den Konvertierungsspezifizierer wie `printf()` folgt: der Konvertierungsspezifizierer ist, wenn ist, `'f'` `fmt` `chars_format::fixed` `'e'` `fmt` `chars_format::scientific` `'a'` (ohne die führende `0x` im Ergebnis) `fmt` , wenn ist, `chars_format::hex` und wenn ist `'g'` `fmt` `chars_format::general` . Die Angabe der kürzesten Fixed-Notation kann zu einer längeren Ausgabe führen, da Sie möglicherweise die kürzeste Darstellung darstellt, wenn der Wert sehr groß oder sehr klein ist.

In der folgenden Tabelle wird das Konvertierungs Verhalten anhand verschiedener Kombinationen von `fmt` -und- `precision` Parametern beschrieben Der Begriff "kürzeste Roundtrip-Verhalten" bezieht sich auf das Schreiben der geringsten Anzahl von Ziffern, die erforderlich sind, damit der Wert durch die Verwendung der entsprechenden `from_chars` Funktion genau wieder hergestellt wird.

| `fmt` und- `precision` Kombination | Ausgabe |
|--|--|
|  Neither | Je nachdem, welche der Fixed-oder Scientific-Notation kürzer ist, wird als eine tief Trennung bevorzugt.</br>Dieses Verhalten kann nicht von einer Überladung simuliert werden, die den- `fmt` Parameter annimmt. |
| `fmt` | Das kürzeste Roundtrip-Verhalten für das angegebene Format, z. b. das kürzeste wissenschaftliche Format. |
| `fmt` und `precision` | Verwendet die angegebene Genauigkeit im folgenden `printf()` Stil, ohne das kürzeste Roundtrip-Verhalten. |

### <a name="example"></a>Beispiel

```cpp
#include <charconv>
#include <stdio.h>
#include <system_error>

template <typename T> void TestToChars(const T t)
{
    static_assert(std::is_floating_point_v<T>);
    constexpr bool IsFloat = std::is_same_v<T, float>;

    char buf[100]; // 100 is large enough for double and long double values because the longest possible outputs are "-1.23456735e-36" and "-1.2345678901234567e-100".
    constexpr size_t size = IsFloat ? 15 : 24;
    const std::to_chars_result res = std::to_chars(buf, buf + size, t);  // points to buffer area it can use. Must be char, not wchar_t, etc.

    if (res.ec == std::errc{}) // no error
    {
        // %.*s provides the exact number of characters to output because the output range, [buf, res.ptr), isn't null-terminated
        printf("success: %.*s\n", static_cast<int>(res.ptr - buf), buf);
    }
    else // probably std::errc::value_too_large
    {
        printf("Error: %d\n", static_cast<int>(res.ec));
    }
}

int main()
{
    TestToChars(123.34);
    return 0;
}
```

## `from_chars`

Konvertieren einer Sequenz von **`char`** in eine Ganzzahl oder einen Gleit Komma Wert.

```cpp
// char to an integer value

from_chars_result from_chars(const char* first, const char* last, char& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, signed char& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned char& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, short& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned short& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, int& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned int& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, long& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned long& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, long long& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned long long& value, int base = 10);

// char to a floating-point value

from_chars_result from_chars(const char* first, const char* last, float& value, chars_format fmt = chars_format::general);
from_chars_result from_chars(const char* first, const char* last, double& value, chars_format fmt = chars_format::general);
from_chars_result from_chars(const char* first, const char* last, long double& value, chars_format fmt = chars_format::general);
```

### <a name="parameters"></a>Parameter

*erstes*\
Zeigt auf den Anfang des Puffers der zu konvertierenden Zeichen.

*letzten*\
Verweist auf eine Stelle hinter dem Endelement des Puffers der zu konvertierenden Zeichen.

*Wert*\
Wenn die Konvertierung erfolgreich ist, enthält das Ergebnis der Konvertierung.

*sock*\
Bei ganzzahligen Konvertierungen die Basis, die während der Konvertierung verwendet werden soll. Muss zwischen 2 und 36 (einschließlich) liegen.

*fmt*\
Für Gleit Komma Konvertierungen das Format der Sequenz von Zeichen, die konvertiert wird. Weitere Informationen finden Sie unter [chars_format](chars-format-class.md) .

### <a name="remarks"></a>Bemerkungen

Die- `from_chars()` Funktionen analysieren die Zeichenfolge ( \[ `first` `last` ) für ein Zahlenmuster, bei dem \[ `first` , `last` ) ein gültiger Bereich sein muss.

Beim durch Schreiben von Zeichen werden Leerzeichen nicht ignoriert. Anders als Beispiels `strtod()` Weise muss der Puffer mit einer gültigen numerischen Darstellung beginnen.

Gibt eine [from_chars_result-Struktur](from-chars-result-structure.md)zurück.

Wenn keine Zeichen mit einem Zahlenmuster identisch sind, `value` wird nicht geändert, `from_chars_result.ptr` zeigt auf `first` , und `from_chars_result.ec` ist `errc::invalid_argument` .

Wenn nur einige Zeichen mit einem Zahlenmuster übereinstimmen, `from_chars_result.ptr` zeigt auf das erste Zeichen, das nicht mit dem Muster übereinstimmt, oder hat den Wert des `last` Parameters, wenn alle Zeichen übereinstimmen.

Wenn der analysierte Wert nicht innerhalb des Bereichs liegt, der vom Typ dargestellt `value` werden kann, `value` ist unverändert, und `from_chars_result.ec` ist `errc::result_out_of_range` .

Andernfalls `value` wird nach der Rundung auf den analysierten Wert festgelegt, und `from_chars_result.ec` ist gleich `errc{}` .

### <a name="example"></a>Beispiel

```cpp
#include <charconv>
#include <stdio.h>
#include <string_view>
#include <system_error>

double TestFromChars(const std::string_view sv)
{
    const char* const first = sv.data();
    const char* const last = first + sv.size();
    double dbl;

    const std::from_chars_result res = std::from_chars(first, last, dbl);

    if (res.ec == std::errc{}) // no error
    {
        printf("success: %g\n", dbl);
    }
    else
    {
        printf("Error: %d\n", static_cast<int>(res.ec));
    }

    return dbl;
}

int main()
{
    double dbl = TestFromChars("123.34");
    return 0;
}
```

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<charconv>

**Namespace:** std

/Std: c++ 17 (oder höher) ist erforderlich.

## <a name="see-also"></a>Weitere Informationen

[\<charconv>](charconv.md)  
[Die kürzeste Dezimal Zeichenfolge, die von Roundtrips](https://www.exploringbinary.com/the-shortest-decimal-string-that-round-trips-examples/) 
 [printf ()-Formatspezifizierer](..\c-runtime-library\format-specification-syntax-printf-and-wprintf-functions.md)

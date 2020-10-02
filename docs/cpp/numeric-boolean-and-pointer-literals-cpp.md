---
title: Numerische, boolesche und Zeiger Literale (C++)
description: Die C++-Standard sprach Formate für ganzzahlige, Gleit Komma-, boolesche und Zeiger Literale.
ms.date: 11/04/2016
helpviewer_keywords:
- literals, C++
- constants, literals
- literals [C++]
ms.assetid: 17c09fc3-3ad7-47e2-8b48-ba8ae994edc8
ms.openlocfilehash: 84fdac7010805fc4d0a429231a080ab11d5c595a
ms.sourcegitcommit: f7fbdc39d73e1fb3793c396fccf7a1602af7248b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2020
ms.locfileid: "91662255"
---
# <a name="numeric-boolean-and-pointer-literals"></a>Numerische, boolesche und Zeigerliterale

Bei einem Literal handelt es sich um ein Programmelement, das direkt einen Wert darstellt. In diesem Artikel werden Literale vom Typ Integer, Gleit Komma, boolescher Wert und Zeiger behandelt. Informationen zu Zeichen folgen-und Zeichen literalen finden Sie unter [Zeichen folgen-und Zeichen Literale (C++)](../cpp/string-and-character-literals-cpp.md). Sie können auch eigene Literale auf der Grundlage einer dieser Kategorien definieren. Weitere Informationen finden Sie unter [benutzerdefinierte Literale (C++)](../cpp/user-defined-literals-cpp.md) .

. Sie können Literale in vielen Kontexten verwenden, aber am häufigsten zum Initialisieren von benannten Variablen und zum Weitergeben der Argumente an Funktionen:

```cpp
const int answer = 42;      // integer literal
double d = sin(108.87);     // floating point literal passed to sin function
bool b = true;              // boolean literal
MyClass* mc = nullptr;      // pointer literal
```

In manchen Fällen ist es wichtig, dem Compiler darüber zu informieren, wie er ein Literal interpretieren soll oder welcher bestimmte Typ ihm erteilt werden soll. Dies erfolgt durch Anhängen von Präfixen oder Suffixen an das Literale. Beispielsweise weist das-Präfix `0x` den Compiler an, die nachfolgende Zahl als Hexadezimalwert zu interpretieren, z `0x35` . b.. Das- `ULL` Suffix weist den Compiler an, den Wert als **`unsigned long long`** Typ zu behandeln, wie in `5894345ULL` . In den folgenden Abschnitten finden Sie die vollständige Liste der Prä- und Suffixe für jeden Literaltyp.

## <a name="integer-literals"></a>Ganzzahlenliteral

Ganzzahlenliterale beginnen mit einer Ziffer und weisen weder Bruchteile noch Exponenten auf. Sie können ganzzahlige Literale im Dezimal-, binär-, Oktal-oder Hexadezimal Format angeben. Optional können Sie ein Ganzzahlliteral als unsigned und als Long-oder Long Long-Typ angeben, indem Sie ein-Suffix verwenden.

Wenn kein Präfix oder Suffix vorhanden ist, gibt der Compiler einen ganzzahligen literalwerttyp **`int`** (32 Bits) an, wenn der Wert passt, andernfalls erhält er den Typ **`long long`** (64 Bits).

Starten Sie zum Angeben eines integralen Dezimalliterals die Spezifikation mit einer Ziffer ungleich 0. Beispiel:

```cpp
int i = 157;        // Decimal literal
int j = 0198;       // Not a decimal number; erroneous octal literal
int k = 0365;       // Leading zero specifies octal literal, not decimal
int m = 36'000'000  // digit separators make large values more readable
```

Um ein oktales Integralliteral anzugeben, beginnen Sie die Angabe mit 0, gefolgt von einer Ziffernfolge im Bereich von 0 bis 7. Die Ziffern 8 und 9 sind Fehler, wenn sie ein oktales Literal angeben. Beispiel:

```cpp
int i = 0377;   // Octal literal
int j = 0397;   // Error: 9 is not an octal digit
```

Wenn Sie ein ganzzahliges Hexadezimal Format angeben möchten, beginnen Sie die Angabe mit `0x` oder `0X` (die Groß-/Kleinschreibung von "x" spielt keine Rolle), gefolgt von einer Sequenz von Ziffern im Bereich `0` bis `9` und `a` (oder `A` ) bis `f` (oder `F` ). Hexadezimalzahlen `a` (oder `A`) bis `f` (oder `F`) stellen Werte im Bereich von 10 bis 15 dar. Beispiel:

```cpp
int i = 0x3fff;   // Hexadecimal literal
int j = 0X3FFF;   // Equal to i
```

Um einen Typ ohne Vorzeichen anzugeben, verwenden Sie entweder das-oder das- `u` `U` Suffix. Um einen Long-Typ anzugeben, verwenden Sie entweder das-oder das- `l` `L` Suffix. Um einen integralen 64-Bit-Typ anzugeben, verwenden Sie das Suffix „LL“ oder „ll“. Das Suffix "I64" wird weiterhin unterstützt, wird jedoch nicht empfohlen. Es ist für Microsoft spezifisch und nicht portabel. Beispiel:

```cpp
unsigned val_1 = 328u;                  // Unsigned value
long val_2 = 0x7FFFFFL;                 // Long value specified
                                        //  as hex literal
unsigned long val_3 = 0776745ul;        // Unsigned long value
auto val_4 = 108LL;                           // signed long long
auto val_4 = 0x8000000000000000ULL << 16;     // unsigned long long
```

**Ziffern Trennzeichen**: Sie können das einfache Anführungszeichen (Apostroph) verwenden, um die Position von Werten in größeren Zahlen voneinander zu trennen, damit es den Menschen leichter lesbar ist. Trennzeichen haben keine Auswirkungen auf die Kompilierung.

```cpp
long long i = 24'847'458'121
```

## <a name="floating-point-literals"></a>Gleitkommaliterale

Gleitkommaliterale geben Werte an, die Nachkommastellen aufweisen müssen. Diese Werte enthalten Dezimalstellen ( **`.`** ) und können Exponenten enthalten.

Gleit Komma Literale verfügen über ein *signifikanand* (manchmal als *Mantisse*bezeichnet), das den Wert der Zahl angibt. Sie verfügen über einen *Exponenten*, der die Größe der Zahl angibt. Außerdem verfügen Sie über ein optionales Suffix, das den Literaltyp angibt. Der signifiund wird als Sequenz von Ziffern, gefolgt von einem-Zeitraum, gefolgt von einer optionalen Sequenz von Ziffern angegeben, die den Bruch Teil der Zahl darstellt. Beispiel:

```cpp
18.46
38.
```

Sofern vorhanden, gibt der Exponent die Größe der Zahl als Zehnerpotenz an (siehe folgendes Beispiel):

```cpp
18.46e0      // 18.46
18.46e1      // 184.6
```

Der Exponent kann mithilfe von oder angegeben werden, `e` `E` die dieselbe Bedeutung haben, gefolgt von einem optionalen Vorzeichen (+ oder-) und einer Folge von Ziffern.  Wenn ein Exponent vorhanden ist, ist das nachfolgende Dezimaltrennzeichen in ganzen Zahlen wie `18E0` nicht erforderlich.

Gleit Komma Literale werden standardmäßig auf Typ eingestellt **`double`** . Durch die Verwendung der Suffixe `f` oder oder `l` `F` `L` (bei dem Suffix wird die Groß-/Kleinschreibung nicht beachtet) kann das Literale als oder angegeben werden **`float`** **`long double`** .

Obwohl **`long double`** und **`double`** dieselbe Darstellung aufweisen, sind Sie nicht identisch. Beispielsweise können überladene Funktionen wie

```cpp
void func( double );
```

und

```cpp
void func( long double );
```

## <a name="boolean-literals"></a>Boolesche Literale

Die booleschen Literale sind **`true`** und **`false`** .

## <a name="pointer-literal-c11"></a>Zeigerliteral (C++11)

C++ führt das [`nullptr`](../cpp/nullptr.md) Literale ein, um einen von NULL initialisierten Zeiger anzugeben. In tragbarem Code **`nullptr`** sollte anstelle des ganzzahligen Typs NULL oder Makros wie z. b. verwendet werden `NULL` .

## <a name="binary-literals-c14"></a>Binäre Literale (C++14)

Ein binäres Literale kann durch die Verwendung des Präfix `0B` oder `0b`, gefolgt durch eine Sequenz von mehreren 1 und 0 angegeben werden.

```cpp
auto x = 0B001101 ; // int
auto y = 0b000001 ; // int
```

## <a name="avoid-using-literals-as-magic-constants"></a>Vermeiden der Verwendung von Literalen als „magische Konstanten“

Auch wenn Sie Literale direkt in Ausdrücken und Anweisungen verwenden können, ist es nicht immer ein guter Programmierstil:

```cpp
if (num < 100)
    return "Success";
```

Im vorherigen Beispiel empfiehlt es sich, eine benannte Konstante zu verwenden, die eine klare Bedeutung vermittelt, z. b. "MAXIMUM_ERROR_THRESHOLD". Wenn Endbenutzer den Rückgabewert "Erfolg" sehen, ist es möglicherweise besser, eine benannte Zeichen folgen Konstante zu verwenden. Sie können Zeichen folgen Konstanten an einem einzigen Speicherort in einer Datei aufbewahren, die in andere Sprachen lokalisiert werden kann. Die Verwendung benannter Konstanten hilft sowohl selbst als auch anderen, die Absicht des Codes zu verstehen.

## <a name="see-also"></a>Weitere Informationen

[Lexikalische Konventionen](../cpp/lexical-conventions.md)<br/>
[C++-Zeichen folgen Literale](../cpp/string-and-character-literals-cpp.md)<br/>
[C++ benutzerdefinierte Literale](../cpp/user-defined-literals-cpp.md)

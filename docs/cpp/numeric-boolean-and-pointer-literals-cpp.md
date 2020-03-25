---
title: Numerische, boolesche und Zeiger Literale (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- literals, C++
- constants, literals
- literals [C++]
ms.assetid: 17c09fc3-3ad7-47e2-8b48-ba8ae994edc8
ms.openlocfilehash: 21685af5fc4f2dcf042698e054430e50531163b7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177741"
---
# <a name="numeric-boolean-and-pointer-literals"></a>Numerische, boolesche und Zeiger Literale

Bei einem Literal handelt es sich um ein Programmelement, das direkt einen Wert darstellt. In diesem Artikel werden Literale der Typen Ganzzahl, Gleitkomma, Boolesch und Zeiger erläutert. Informationen zu Zeichen folgen-und Zeichen literalen finden Sie unter [Zeichen folgen-undC++Zeichen Literale ()](../cpp/string-and-character-literals-cpp.md). Sie können auch eigene Literale auf der Grundlage einer dieser Kategorien definieren. Weitere Informationen finden Sie unter [benutzerdefinierte Literale (C++)](../cpp/user-defined-literals-cpp.md) .

erforderlich. Sie können Literale in vielen Kontexten verwenden, aber am häufigsten zum Initialisieren von benannten Variablen und zum Weitergeben der Argumente an Funktionen:

```cpp
const int answer = 42; // integer literal
double d = sin(108.87);     //floating point literal passed to sin function
bool b = true;              // boolean literal
MyClass* mc = nullptr;      // pointer literal
```

In manchen Fällen ist es wichtig, dem Compiler darüber zu informieren, wie er ein Literal interpretieren soll oder welcher bestimmte Typ ihm erteilt werden soll. Dies setzen Sie um, indem Sie Prä- und Suffixe an das Literal anfügen. Beispielsweise informiert das Präfix „0x“ den Compiler darüber, die darauffolgende Zahl als einen hexadezimalen Wert, beispielsweise „0x35“, zu interpretieren. Das ull-Suffix weist den Compiler an, den Wert als **Ganzzahl ohne Vorzeichen long long** -Typ zu behandeln, wie in 5894345ull. In den folgenden Abschnitten finden Sie die vollständige Liste der Prä- und Suffixe für jeden Literaltyp.

## <a name="integer-literals"></a>Ganzzahlenliteral

Ganzzahlenliterale beginnen mit einer Ziffer und weisen weder Bruchteile noch Exponenten auf. Sie können Integerliterale im Dezimal-, Oktal- oder Hexadezimalformat angeben. Sie können Typen mit oder ohne Vorzeichen und lange oder kurze Typen angeben.

Wenn kein Präfix oder Suffix vorhanden ist, gibt der Compiler einen ganzzahligen literalwerttyp **int** (32 Bits), wenn der Wert passt, andernfalls gibt er den Typ **Long Long** (64 Bits) an.

Starten Sie zum Angeben eines integralen Dezimalliterals die Spezifikation mit einer Ziffer ungleich 0. Beispiel:

```cpp
int i = 157;   // Decimal literal
int j = 0198;       // Not a decimal number; erroneous octal literal
int k = 0365;       // Leading zero specifies octal literal, not decimal
int m = 36'000'000  // digit separators make large values more readable
int
```

Um ein oktales Integralliteral anzugeben, beginnen Sie die Angabe mit 0, gefolgt von einer Ziffernfolge im Bereich von 0 bis 7. Die Ziffern 8 und 9 sind Fehler, wenn sie ein oktales Literal angeben. Beispiel:

```cpp
int i = 0377;   // Octal literal
int j = 0397;        // Error: 9 is not an octal digit
```

Um eine integrale Hexadezimalliterale anzugeben, beginnen Sie die Angabe mit `0x` oder `0X` (die Groß-/Kleinschreibung von "x" ist nicht relevant), gefolgt von einer Ziffernfolge im Bereich `0` bis `9` und `a` (oder `A`) bis `f` (oder `F`). Hexadezimalzahlen `a` (oder `A`) bis `f` (oder `F`) stellen Werte im Bereich von 10 bis 15 dar. Beispiel:

```cpp
int i = 0x3fff;   // Hexadecimal literal
int j = 0X3FFF;        // Equal to i
```

Um einen Typ ohne Vorzeichen anzugeben, verwenden Sie entweder das `u`-oder `U`-Suffix. Um einen Long-Typ anzugeben, verwenden Sie entweder das `l`-oder `L`-Suffix. Um einen integralen 64-Bit-Typ anzugeben, verwenden Sie das Suffix „LL“ oder „ll“. Das Suffix „i64“ wird weiterhin unterstützt, sollte jedoch vermieden werden, da es für Microsoft spezifisch und nicht übertragbar ist. Beispiel:

```cpp
unsigned val_1 = 328u;             // Unsigned value
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

Gleitkommaliterale geben Werte an, die Nachkommastellen aufweisen müssen. Diese Werte enthalten Dezimalstellen ( **.** ) und können Exponenten enthalten.

Gleitkommaliterale haben eine „Mantisse“, die den Wert der Zahl angibt, einen „Exponenten“, der die Größe der Zahl angibt, und ein optionales Suffix, das den Literaltyp angibt. Die Mantisse wird wie folgt angegeben: eine Ziffernsequenz, gefolgt von einem Punkt, gefolgt von einer optionalen Ziffernsequenz, die die Nachkommastellen der Zahl darstellen. Beispiel:

```cpp
18.46
38.
```

Sofern vorhanden, gibt der Exponent die Größe der Zahl als Zehnerpotenz an (siehe folgendes Beispiel):

```cpp
18.46e0      // 18.46
18.46e1           // 184.6
```

Der Exponent kann mit `e` oder `E`angegeben werden, die die gleiche Bedeutung haben, gefolgt von einem optionalen Vorzeichen (+ oder-) und einer Folge von Ziffern.  Wenn ein Exponent vorhanden ist, ist das nachfolgende Dezimaltrennzeichen in ganzen Zahlen wie `18E0` nicht erforderlich.

Gleit Komma Literale werden standardmäßig auf den Typ **Double**eingestellt. Durch die Verwendung der Suffixe `f` oder `l` (oder `F` oder `L` – bei dem Suffix wird die Groß-/Kleinschreibung nicht beachtet), kann das Literale als **float** oder **long Double**angegeben werden.

Obwohl **long Double** und **Double** dieselbe Darstellung aufweisen, weisen Sie nicht denselben Typ auf. Sie können beispielsweise überladene Funktionen haben:

```cpp
void func( double );
```

and

```cpp
void func( long double );
```

## <a name="boolean-literals"></a>Boolesche Literale

Die booleschen Literale sind **true** und **false**.

## <a name="pointer-literal-c11"></a>Zeigerliteral (C++11)

C++führt das [nullptr](../cpp/nullptr.md) -Literale ein, um einen von NULL initialisierten Zeiger anzugeben. In tragbarem Code sollte **nullptr** anstelle des ganzzahligen Typs NULL oder Makros wie NULL verwendet werden.

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

Im vorherigen Beispiel empfiehlt sich eher die Verwendung einer benannten Konstante, die eine klare Bedeutung vermittelt, beispielsweise „MAXIMUM_ERROR_THRESHOLD“. Wenn Endbenutzer den Rückgabewert „Success“ anzeigen, empfiehlt sich eher die Verwendung einer benannten Zeichenfolgenkonstante, die an einer einzelnen Position in einer Datei gespeichert werden kann, wo sie in mehrere Sprachen lokalisiert werden kann. Die Verwendung von benannten Konstanten hilft anderen Benutzern und Ihnen, den Zweck des Codes zu verstehen.

## <a name="see-also"></a>Weitere Informationen

[Lexikalische Konventionen](../cpp/lexical-conventions.md)<br/>
[C++Zeichen folgen Literale](../cpp/string-and-character-literals-cpp.md)<br/>
[C++Benutzerdefinierte Literale](../cpp/user-defined-literals-cpp.md)

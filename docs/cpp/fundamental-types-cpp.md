---
title: Integrierte Typen (C++)
ms.date: 07/22/2020
f1_keywords:
- __int128_cpp
- __wchar_t_cpp
- char_cpp
- char8_t_cpp
- char16_t_cpp
- char32_t_cpp
- double_cpp
- float_cpp
- int_cpp
- long_cpp
- long_double_cpp
- short_cpp
- signed_cpp
- unsigned_cpp
- unsigned_int_cpp
- wchar_t_cpp
helpviewer_keywords:
- specifiers [C++], type
- float keyword [C++]
- char keyword [C++]
- __wchar_t keyword [C++]
- signed types [C++], summary of data types
- Integer data type [C++], C++ data types
- arithmetic operations [C++], types
- int data type
- unsigned types [C++], summary of data types
- short data type [C++]
- double data type [C++], summary of types
- long long keyword [C++]
- long double keyword [C++]
- unsigned types [C++]
- signed types [C++]
- void keyword [C++]
- storage [C++], basic type
- integral types, C++
- wchar_t keyword [C++]
- floating-point numbers [C++], C++ data types
- long keyword [C++]
- type specifiers [C++]
- integral types
- long keyword [C++]
- storing types [C++]
- data types [C++], void
ms.assetid: 58b0106a-0406-4b74-a430-7cbd315c0f89
ms.openlocfilehash: 73486dd4d81fc91007f078ec5c509bcb963d2706
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232273"
---
# <a name="built-in-types-c"></a>Integrierte Typen (C++)

Integrierte Typen (auch als *grundlegende Typen*bezeichnet) werden durch den C++-Sprachstandard angegeben und in den Compiler integriert. Integrierte Typen sind in keiner Header Datei definiert. Integrierte Typen sind in drei Hauptkategorien unterteilt: " *Integral*", " *Floating-Point*" und " *void*". Ganzzahlige Typen stellen ganze Zahlen dar. Gleit Komma Typen können Werte angeben, die möglicherweise Bruchteile aufweisen. Die meisten integrierten Typen werden vom Compiler als unterschiedliche Typen behandelt. Einige Typen sind jedoch *Synonyme*oder werden vom Compiler als äquivalente Typen behandelt.

## <a name="void-type"></a>void-Typ

Der [`void`](void-cpp.md) Typ beschreibt einen leeren Satz von Werten. Es kann keine Variable vom Typ **`void`** angegeben werden. Der- **`void`** Typ wird hauptsächlich verwendet, um Funktionen zu deklarieren, die keine Werte zurückgeben oder generische Zeiger auf nicht typisierte oder willkürlich typisierte Daten zu deklarieren Jeder Ausdruck kann explizit konvertiert oder in den Typ umgewandelt werden **`void`** . Allerdings werden solche Ausdrücke auf folgende Anwendungsbereiche begrenzt:

- Eine Ausdrucksanweisung. (Weitere Informationen finden Sie unter [Ausdrücke](expressions-cpp.md).)

- Der linke Operand des Komma-Operators. (Weitere Informationen finden Sie unter [Komma-Operator](comma-operator.md).)

- Der zweite oder dritte Operand des bedingten Operators (`? :`). (Weitere Informationen finden Sie unter [Ausdrücke mit dem bedingten Operator](conditional-operator-q.md).)

## <a name="stdnullptr_t"></a>Std:: nullptr_t

Das Schlüsselwort **`nullptr`** ist eine NULL-Zeiger Konstante vom Typ `std::nullptr_t` , die in einen beliebigen unformatierten Zeigertyp konvertiert werden kann. Weitere Informationen finden Sie unter [`nullptr`](nullptr.md).

## <a name="boolean-type"></a>Boolescher Typ

Der [`bool`](bool-cpp.md) -Typ kann [`true`](../cpp/true-cpp.md) -Werte und aufweisen [`false`](../cpp/false-cpp.md) . Die Größe des **`bool`** Typs ist Implementierungs spezifisch. Weitere Informationen finden Sie [Untergrößen integrierter Typen](#sizes-of-built-in-types) für Microsoft-spezifische Implementierungsdetails.

## <a name="character-types"></a>Zeichentypen

Der **`char`** Typ ist ein Zeichen Darstellungs Typ, der Elemente des grundlegenden Ausführungs Zeichensatzes effizient codiert. Der C++-Compiler behandelt Variablen des Typs **`char`** , **`signed char`** und **`unsigned char`** als mit unterschiedlichen Typen.

**Microsoft-spezifisch**: Variablen des Typs **`char`** werden in **`int`** als if vom Typ **`signed char`** standardmäßig herauf gestuft, es sei denn, die [`/J`](../build/reference/j-default-char-type-is-unsigned.md) Kompilierungs Option wird verwendet. In diesem Fall werden Sie als Typ behandelt **`unsigned char`** und auf **`int`** ohne Vorzeichen Erweiterung herauf gestuft.

Eine Variable vom Typ **`wchar_t`** ist ein breit Zeichen-oder multibytezeichentyp. Verwenden **`L`** Sie das Präfix vor einem Zeichen oder einem Zeichenfolgenliteral, um den breit Zeichentyp anzugeben.

**Microsoft-spezifisch**: ist standardmäßig **`wchar_t`** ein nativer Typ, aber Sie können verwenden, [`/Zc:wchar_t-`](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) um **`wchar_t`** eine typedef für zu erstellen **`unsigned short`** . Der **`__wchar_t`** Typ ist ein Microsoft-spezifisches Synonym für den systemeigenen **`wchar_t`** Typ.

Der **`char8_t`** Typ wird für die UTF-8-Zeichen Darstellung verwendet. Sie verfügt über die gleiche Darstellung wie **`unsigned char`** , wird vom Compiler aber als eindeutiger Typ behandelt. Der **`char8_t`** Typ ist neu in c++ 20. **Microsoft-spezifisch**: die Verwendung von **`char8_t`** erfordert die- [`/std:c++latest`](../build/reference/std-specify-language-standard-version.md) Compileroption.

Der **`char16_t`** Typ wird für die UTF-16-Zeichen Darstellung verwendet. Er muss groß genug sein, um jede beliebige UTF-16-Code Einheit darzustellen. Sie wird vom Compiler als eindeutiger Typ behandelt.

Der **`char32_t`** Typ wird für die UTF-32-Zeichen Darstellung verwendet. Er muss groß genug sein, um jede beliebige UTF-32-Code Einheit darzustellen. Sie wird vom Compiler als eindeutiger Typ behandelt.

## <a name="floating-point-types"></a>Gleitkommatypen

Gleit Komma Typen verwenden eine IEEE-754-Darstellung, um eine Näherung von Bruchzahlen über einen breiten Bereich von vergrößerwerten bereitzustellen. In der folgenden Tabelle werden die Gleit Komma Typen in C++ und die Vergleichs Einschränkungen für Gleit Komma Typen aufgeführt. Diese Einschränkungen werden vom C++-Standard vorgeschrieben und sind unabhängig von der Microsoft-Implementierung. Die absolute Größe integrierter Gleit Komma Typen wird nicht im Standardwert angegeben.

| type | Inhalte |
|--|--|
| **`float`** | Type **`float`** ist der kleinste Gleit kommatyp in C++. |
| **`double`** | **`double`** Der Typ ist ein Gleit kommatyp, der größer oder gleich dem Typ ist **`float`** , aber kürzer oder gleich der Größe des Typs ist **`long double`** . |
| **`long double`** | **`long double`** Der Typ ist ein Gleit kommatyp, der größer oder gleich dem Typ ist **`double`** . |

**Microsoft-spezifisch**: die Darstellung von **`long double`** und **`double`** ist identisch. Allerdings **`long double`** **`double`** werden und vom Compiler als unterschiedliche Typen behandelt. Der Microsoft C++-Compiler verwendet die 4-und 8-Byte-IEEE-754-Gleit Komma Darstellungen. Weitere Informationen finden Sie unter [IEEE-Gleit Komma Darstellung](../build/ieee-floating-point-representation.md).

## <a name="integer-types"></a>Ganzzahltypen

Der **`int`** Typ ist der standardmäßige Basic-ganzzahlige Typ. Sie kann alle ganzen Zahlen über einen Implementierungs spezifischen Bereich darstellen.

Eine ganzzahlige Darstellung mit Vorzeichen *ist eine,* die positive und negative Werte enthalten kann. Sie wird standardmäßig verwendet oder wenn das **`signed`** Modifiziererschlüsselwort vorhanden ist. Das **`unsigned`** Modifiziererschlüsselwort gibt eine *nicht signierte* Darstellung an, die nur nicht negative Werte enthalten kann.

Ein größenmodifizierer gibt die Breite in Bits der verwendeten ganzzahligen Darstellung an. Die-Sprache unterstützt die **`short`** **`long`** **`long long`** modifiziererer, und. Ein **`short`** Typ muss mindestens 16 Bits breit sein. Ein **`long`** Typ muss mindestens 32 Bits breit sein. Ein **`long long`** Typ muss mindestens 64 Bits breit sein. Der Standard gibt eine Größen Beziehung zwischen den ganzzahligen Typen an:

`1 == sizeof(char) <= sizeof(short) <= sizeof(int) <= sizeof(long) <= sizeof(long long)`

Eine-Implementierung muss sowohl die minimalen Größenanforderungen als auch die Größen Beziehung für jeden Typ beibehalten. Die tatsächlichen Größen können jedoch zwischen den Implementierungen variieren und variieren. Weitere Informationen finden Sie [Untergrößen integrierter Typen](#sizes-of-built-in-types) für Microsoft-spezifische Implementierungsdetails.

Das **`int`** Schlüsselwort kann weggelassen werden **`signed`** , wenn die **`unsigned`** Größen Modifizierer, oder angegeben werden. Die modifiziererer und der **`int`** Typ, sofern vorhanden, können in beliebiger Reihenfolge angezeigt werden. Beispielsweise **`short unsigned`** und **`unsigned int short`** verweisen auf denselben Typ.

### <a name="integer-type-synonyms"></a>Ganzzahlige typsynonyme

Die folgenden Typen von Typen werden vom Compiler als Synonyme angesehen:

- **`short`**, **`short int`**, **`signed short`**, **`signed short int`**

- **`unsigned short`**, **`unsigned short int`**

- **`int`**, **`signed`**, **`signed int`**

- **`unsigned`**, **`unsigned int`**

- **`long`**, **`long int`**, **`signed long`**, **`signed long int`**

- **`unsigned long`**, **`unsigned long int`**

- **`long long`**, **`long long int`**, **`signed long long`**, **`signed long long int`**

- **`unsigned long long`**, **`unsigned long long int`**

Zu den **Microsoft-spezifischen** ganzzahligen Typen zählen die Typen für die jeweilige Breite **`__int8`** ,, **`__int16`** **`__int32`** und **`__int64`** . Diese Typen können die **`signed`** **`unsigned`** modifiziererer und verwenden. Der- **`__int8`** Datentyp ist ein Synonym für den Typ **`char`** , **`__int16`** ist mit dem Typ Synonym, **`short`** **`__int32`** ist mit dem Typ Synonym **`int`** und **`__int64`** ist mit dem Typ Synonym **`long long`** .

## <a name="sizes-of-built-in-types"></a>Größen von integrierten Typen

Die meisten integrierten Typen haben Implementierungs definierte Größen. In der folgenden Tabelle wird die Menge des Speichers aufgelistet, die für integrierte Typen in Microsoft C++ erforderlich ist. Insbesondere bei **`long`** 64-Bit-Betriebssystemen ist der Wert 4 Bytes.

| type | Size |
|--|--|
| **`bool`**, **`char`**, **`char8_t`**, **`unsigned char`**, **`signed char`**, **`__int8`** | 1 Byte |
| **`char16_t`**, **`__int16`**, **`short`**, **`unsigned short`**, **`wchar_t`**, **`__wchar_t`** | 2 Bytes |
| **`char32_t`**, **`float`**, **`__int32`**, **`int`**, **`unsigned int`**, **`long`**, **`unsigned long`** | 4 Byte |
| **`double`**, **`__int64`**, **`long double`**, **`long long`**, **`unsigned long long`** | 8 Byte |

Eine Zusammenfassung des Wertebereichs der einzelnen Typen finden Sie unter [Datentyp Bereiche](data-type-ranges.md) .

Weitere Informationen zur Typkonvertierung finden Sie unter [Standard Konvertierungen](standard-conversions.md).

## <a name="see-also"></a>Weitere Informationen

[Datentypbereiche](data-type-ranges.md)

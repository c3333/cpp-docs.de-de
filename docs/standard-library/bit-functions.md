---
title: '&lt;&gt;Bitfunktionen'
description: Funktionen zum Zugreifen auf, bearbeiten und verarbeiten einzelner Bits und Sequenzen von Bits
ms.date: 08/28/2020
f1_keywords:
- bit/std::bit_cast
- bit/std::has_single_bit
- bit/std::bit_ceil
- bit/std::bit_floor
- bit/std::bit_width
- bit/std::rotl
- bit/std::rotr
- bit/std::countl_zero
- bit/std::countl_one
- bit/std::countr_zero
- bit/std::countr_one
- bit/std::popcount
helpviewer_keywords:
- std::bit [C++], bit_cast
- std::bit [C++], has_single_bit
- std::bit [C++], bit_ceil
- std::bit [C++], bit_floor
- std::bit [C++], bit_width
- std::bit [C++], rotl
- std::bit [C++], rotr
- std::bit [C++], countl_zero
- std::bit [C++], countl_one
- std::bit [C++], countr_zero
- std::bit [C++], countr_one
- std::bit [C++], popcount
ms.openlocfilehash: a2408df9aa13c6e714f615561871397be17fc4a3
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90039810"
---
# <a name="ltbitgt-functions"></a>&lt;&gt;Bitfunktionen

Der- \<bit> Header enthält die folgenden nicht-Member-Vorlagen Funktionen:

| **Nicht-Member-Funktionen** | **Beschreibung** |
|--------|---------|
|[bit_cast](#bit_cast) | Interpretiert die Objektdarstellung von einem Typ in einen anderen. |
|[bit_ceil](#bit_ceil) | Ermittelt die kleinste Potenz von zwei größer als oder gleich einem Wert. |
|[bit_floor](#bit_floor) | Ermitteln der größten Potenz von zwei nicht größeren Werten als einem Wert. |
|[bit_width](#bit_width) | Suchen Sie die kleinste Anzahl von Bits, die für die Darstellung eines Werts benötigt werden. |
|[countl_zero](#countl_zero) | Zählen Sie die Anzahl der aufeinander folgenden Bits, die auf NULL festgelegt sind, beginnend mit dem signifikantesten Bit. |
|[countl_one](#countl_one) | Zählen Sie die Anzahl der aufeinander folgenden Bits, die auf 1 festgelegt sind, beginnend mit dem signifikantesten Bit. |
|[countr_zero](#countr_zero) | Zählen Sie die Anzahl der aufeinander folgenden Bits, die auf 0 (null) festgelegt sind, beginnend mit dem geringsten Bit |
|[countr_one](#countl_one) | Zählen Sie die Anzahl aufeinander folgender Bits, die auf 1 festgelegt sind, beginnend mit dem am wenigsten bedeutenden Bit. |
|[has_single_bit](#has_single_bit) | Überprüfen Sie, ob für einen Wert nur ein einzelnes Bit auf 1 festgelegt ist. Dies entspricht dem Testen, ob ein Wert eine Potenz von zwei ist. |
|[popcount](#popcount) | Zählen Sie die Anzahl der Bits, die auf 1 festgelegt sind. |
|[rotl](#rotl) | Berechnen Sie das Ergebnis einer bitweisen linken Drehung. |
|[RotR](#rotr) | Berechnen Sie das Ergebnis einer bitweisen rechten Drehung. |

## <a name="bit_cast"></a>`bit_cast`

Kopieren Sie ein Bitmuster aus einem Objekt vom Typ `From` in ein neues Objekt vom Typ `To` .

```cpp
template <class To, class From>
[[nodiscard]] constexpr To bit_cast(const From& from) noexcept;
```

### <a name="parameters"></a>Parameter

*An*\
Der Typ der Ausgabe.

*Von*\
Der Typ des zu konvertierenden Werts.

*Von*\
Der zu konvertierende Wert.

### <a name="return-value"></a>Rückgabewert

Ein Objekt vom Typ `To`.

Jedes Bit im Ergebnis entspricht dem entsprechenden Bit in `from` , es sei denn, es sind Auffüll Teile in vorhanden `To` . in diesem Fall sind die Bits im Ergebnis nicht angegeben.

### <a name="example"></a>Beispiel

```cpp
#include <bit>
#include <iostream>

int main()
{
    float f = std::numeric_limits<float>::infinity();
    int i = std::bit_cast<int>(f);
    std::cout << "float f = " << std::hex << f
              << "\nstd::bit_cat<int>(f) = " << std::hex << i << '\n';
    return 0;
}
```

```Output
float f = inf
std::bit_cat<int>(f) = 7f800000
```

### <a name="remarks"></a>Bemerkungen

Auf Low-Level-Code muss häufig ein Objekt eines Typs als ein anderer Typ interpretiert werden. Das neu interpretierte Objekt hat die gleiche Bitdarstellung wie das ursprüngliche, aber ist ein anderer Typ.

Anstatt `reinterpret_cast` , oder zu verwenden `memcpy()` , `bit_cast()` ist eine bessere Möglichkeit, diese Konvertierungen durchführen zu können. Dies ist aus folgenden Gründen besser:
- `bit_cast()` ist gleich `constexpr`.
- `bit_cast()` erfordert, dass die Typen trivial kopiert werden können und dieselbe Größe aufweisen. Dies verhindert potenzielle Probleme, die bei Verwendung von und auftreten könnten, `reinterpret_cast` `memcpy` da Sie verwendet werden könnten, um nicht triviale kopierbare Typen versehentlich zu konvertieren. Kann auch `memcpy()` verwendet werden, um versehentlich zwischen Typen zu kopieren, die nicht die gleiche Größe aufweisen. Beispielsweise ein Double (8 Bytes) in ein unsigniertes int (4 Bytes) oder umgekehrt.

Diese Überladung ist nur an der Überladungs Auflösung beteiligt, wenn:
-  `sizeof(To) == sizeof(From)`
- `To` und `From` sind [is_trivially_copyable](is-trivially-copyable-class.md).

Diese Funktions Vorlage ist `constexpr` nur dann, wenn `To` , `From` und die Typen ihrer unter Objekte sind:
- kein Union-oder Zeigertyp
- kein Zeiger auf Member-Typ
- nicht flüchtig qualifiziert
- keinen nicht statischen Datenmember haben, bei dem es sich um einen Verweistyp handelt

## <a name="bit_ceil"></a>`bit_ceil`

Ermittelt die kleinste Potenz von zwei größer als oder gleich einem Wert. Gibt z. b. an, dass `3` zurückgibt `4` .

```cpp
template<class T>
[[nodiscard]] constexpr T bit_ceil(T value);
```

### <a name="parameters"></a>Parameter

*Wert*\
Der zu testende ganzzahlige Wert ohne Vorzeichen.

### <a name="return-value"></a>Rückgabewert

 Die kleinste Potenz von zwei größer oder gleich `value` .

### <a name="example"></a>Beispiel

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (auto i = 0u; i < 6u; ++i) // bit_ceil() takes an unsigned integer type
    {
        auto nextClosestPowerOf2 = std::bit_ceil(i);
        std::cout << "\nbit_ceil(0b" << std::bitset<4>(i) << ") = "
                  << "0b" << std::bitset<4>(nextClosestPowerOf2);
    }
    return 0;
}
```

```Output
bit_ceil(0b0000) = 0b0001
bit_ceil(0b0001) = 0b0001
bit_ceil(0b0010) = 0b0010
bit_ceil(0b0011) = 0b0100
bit_ceil(0b0100) = 0b0100
bit_ceil(0b0101) = 0b1000
```

### <a name="remarks"></a>Bemerkungen

Diese Vorlagen Funktion ist nur an der Überladungs Auflösung beteiligt, wenn `T` ein ganzzahliger Typ ohne Vorzeichen ist. Beispiel: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` usw.

## <a name="bit_floor"></a>`bit_floor`

Ermitteln der größten Potenz von zwei nicht größeren Werten als einem Wert. Gibt z. b. an, dass `5` zurückgibt `4` .

```cpp
template< class T >
[[nodiscard]] constexpr T bit_floor(T value) noexcept;
```

### <a name="parameters"></a>Parameter

*Wert*\
Der zu testende ganzzahlige Wert ohne Vorzeichen.

### <a name="return-value"></a>Rückgabewert

Die größte Potenz von zwei, die nicht größer als ist `value` . \
Wenn `value` 0 (null) ist, wird NULL zurückgegeben.

### <a name="example"></a>Beispiel

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (auto i = 0u; i < 6u; ++i) // bit_floor() takes an unsigned integer type
    {
        auto previousPowerOf2 = std::bit_floor(i);
        std::cout << "\nbit_floor(0b" << std::bitset<4>(i) << ") = 0b"
                  << std::bitset<4>(previousPowerOf2);
    }
    return 0;
}
```

```Output
bit_floor(0b0000) = 0b0000
bit_floor(0b0001) = 0b0001
bit_floor(0b0010) = 0b0010
bit_floor(0b0011) = 0b0010
bit_floor(0b0100) = 0b0100
bit_floor(0b0101) = 0b0100
```

### <a name="remarks"></a>Bemerkungen

Diese Vorlagen Funktion ist nur an der Überladungs Auflösung beteiligt, wenn `T` ein ganzzahliger Typ ohne Vorzeichen ist. Beispiel: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` usw.

## <a name="bit_width"></a>`bit_width`

Suchen Sie die kleinste Anzahl von Bits, die für die Darstellung eines Werts benötigt werden.

Wenn beispielsweise 5 (0b101) angegeben wird, wird 3 zurückgegeben, da es 3 binäre Bits zum Ausdrücken des Werts 5 benötigt.

```cpp
template<class T>
[[nodiscard]] constexpr T bit_width(T value) noexcept;
```

### <a name="parameters"></a>Parameter

*Wert*\
Der zu testende ganzzahlige Wert ohne Vorzeichen.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der Bits, die erforderlich sind, um `value` . \
Wenn `value` 0 (null) ist, wird NULL zurückgegeben.

### <a name="example"></a>Beispiel

```cpp
#include <bit>
#include <iostream>

int main()
{
    for (unsigned i=0u; i <= 8u; ++i)
    {
        std::cout << "\nbit_width(" << i << ") = "
                  << std::bit_width(i);
    }
    return 0;
}
```

```Output
bit_width(0) = 0
bit_width(1) = 1
bit_width(2) = 2
bit_width(3) = 2
bit_width(4) = 3
bit_width(5) = 3
bit_width(6) = 3
bit_width(7) = 3
bit_width(8) = 4
```

### <a name="remarks"></a>Bemerkungen

Diese Vorlagen Funktion ist nur an der Überladungs Auflösung beteiligt, wenn `T` ein ganzzahliger Typ ohne Vorzeichen ist. Beispiel: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` usw.

## <a name="countl_zero"></a>`countl_zero`

Zählen Sie die Anzahl der aufeinander folgenden Bits, die auf NULL festgelegt sind, beginnend mit dem signifikantesten Bit.

```cpp
template<class T>
[[nodiscard]] constexpr int countl_zero(T value) noexcept;
```

### <a name="parameters"></a>Parameter

*Wert*\
Der zu testende ganzzahlige Wert ohne Vorzeichen.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der aufeinanderfolgenden Bits (0), beginnend mit dem signifikantesten Bit. \
Wenn `value` 0 (null) ist, die Anzahl der Bits im Typ von `value` .

### <a name="example"></a>Beispiel

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (unsigned char result = 0, i = 0; i < 9; i++)
    {
        std::cout << "\ncountl_zero(0b" << std::bitset<8>(result) << ") = " << std::countl_zero(result);
        result = result == 0 ? 1 : result * 2;
    }
    return 0;
}
```

```Output
countl_zero(0b00000000) = 8
countl_zero(0b00000001) = 7
countl_zero(0b00000010) = 6
countl_zero(0b00000100) = 5
countl_zero(0b00001000) = 4
countl_zero(0b00010000) = 3
countl_zero(0b00100000) = 2
countl_zero(0b01000000) = 1
countl_zero(0b10000000) = 0
```

### <a name="remarks"></a>Bemerkungen

Diese Vorlagen Funktion ist nur an der Überladungs Auflösung beteiligt, wenn `T` ein ganzzahliger Typ ohne Vorzeichen ist. Beispiel: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` usw.

## <a name="countl_one"></a>`countl_one`

Zählen Sie die Anzahl der aufeinander folgenden Bits, die auf 1 festgelegt sind, beginnend mit dem signifikantesten Bit.

```cpp
template<class T>
[[nodiscard]] constexpr int countl_one(T value) noexcept;
```

### <a name="parameters"></a>Parameter

*Wert*\
Der zu testende ganzzahlige Wert ohne Vorzeichen.

### <a name="return-value"></a>Rückgabewert

Die Anzahl aufeinander folgender Bits, beginnend ab dem signifikantesten Bit.

### <a name="example"></a>Beispiel

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char value = 0;
    for (unsigned char bit = 128; bit > 0; bit /= 2)
    {
        value |= bit;
        std::cout << "\ncountl_one(0b" << std::bitset<8>(value) << ") = "
                  << std::countl_one(value);
    }
    return 0;
}
```

```Output
countl_one(0b10000000) = 1
countl_one(0b11000000) = 2
countl_one(0b11100000) = 3
countl_one(0b11110000) = 4
countl_one(0b11111000) = 5
countl_one(0b11111100) = 6
countl_one(0b11111110) = 7
countl_one(0b11111111) = 8
```

### <a name="remarks"></a>Bemerkungen

Diese Vorlagen Funktion ist nur an der Überladungs Auflösung beteiligt, wenn `T` ein ganzzahliger Typ ohne Vorzeichen ist. Beispiel: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` usw.

## <a name="countr_zero"></a>`countr_zero`

Zählen Sie die Anzahl der aufeinander folgenden Bits, die auf 0 (null) festgelegt sind, beginnend mit dem geringsten Bit

```cpp
template<class T>
[[nodiscard]] constexpr int countr_zero(T value) noexcept;
```

### <a name="parameters"></a>Parameter

*Wert*\
Der zu testende ganzzahlige Wert ohne Vorzeichen.

### <a name="return-value"></a>Rückgabewert

Die Anzahl der aufeinanderfolgenden Bits (0), beginnend mit dem am wenigsten signifikanten Bit. \
Wenn `value` 0 (null) ist, die Anzahl der Bits im Typ von `value` .

### <a name="example"></a>Beispiel

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    for (unsigned char result = 0, i = 0; i < 9; i++)
    {
        std::cout << "\ncountr_zero(0b" << std::bitset<8>(result) << ") = "
                  << std::countr_zero(result);
        result = result == 0 ? 1 : result * 2;
    }
    return 0;
}
```

```Output
countr_zero(0b00000000) = 8
countr_zero(0b00000001) = 0
countr_zero(0b00000010) = 1
countr_zero(0b00000100) = 2
countr_zero(0b00001000) = 3
countr_zero(0b00010000) = 4
countr_zero(0b00100000) = 5
countr_zero(0b01000000) = 6
countr_zero(0b10000000) = 7
```

### <a name="remarks"></a>Bemerkungen

Diese Vorlagen Funktion ist nur an der Überladungs Auflösung beteiligt, wenn `T` ein ganzzahliger Typ ohne Vorzeichen ist. Beispiel: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` usw.

## <a name="countr_one"></a>`countr_one`

Zählen Sie die Anzahl aufeinander folgender Bits, die auf 1 festgelegt sind, beginnend mit dem am wenigsten bedeutenden Bit.

```cpp
template<class T>
[[nodiscard]] constexpr int countr_one(T value) noexcept;
```

### <a name="parameters"></a>Parameter

*Wert*\
Der zu testende ganzzahlige Wert ohne Vorzeichen.

### <a name="return-value"></a>Rückgabewert

Die Anzahl aufeinander folgender Bits, beginnend ab dem unwichtigsten Bit.

### <a name="example"></a>Beispiel

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char value = 0;
    for (int bit = 1; bit <= 128; bit *= 2)
    {
        value |= bit;
        std::cout << "\ncountr_one(0b" << std::bitset<8>(value) << ") = "
                  << std::countr_one(value);
    }
    return 0;
}
```

```Output
countr_one(0b00000001) = 1
countr_one(0b00000011) = 2
countr_one(0b00000111) = 3
countr_one(0b00001111) = 4
countr_one(0b00011111) = 5
countr_one(0b00111111) = 6
countr_one(0b01111111) = 7
countr_one(0b11111111) = 8
```

### <a name="remarks"></a>Bemerkungen

Diese Vorlagen Funktion ist nur an der Überladungs Auflösung beteiligt, wenn `T` ein ganzzahliger Typ ohne Vorzeichen ist. Beispiel: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` usw.

## <a name="has_single_bit"></a>`has_single_bit`

Überprüfen Sie, ob für einen Wert nur ein Bit festgelegt ist. Dies entspricht dem Testen, ob ein Wert eine Potenz von zwei ist.
 
```cpp
template <class T>
[[nodiscard]] constexpr bool has_single_bit(T value) noexcept;
```

### <a name="parameters"></a>Parameter

*Wert*\
Der zu testende ganzzahlige Wert ohne Vorzeichen.

### <a name="return-value"></a>Rückgabewert

`true` Wenn `value` nur ein Bit festgelegt ist, bedeutet dies auch, dass `value` eine Potenz von zwei ist. Andernfalls `false`.

### <a name="example"></a>Beispiel

```cpp
#include <bit>
#include <bitset>
#include <iostream>
#include <iomanip>

int main()
{
    for (auto i = 0u; i < 10u; ++i)
    {
        std::cout << "has_single_bit(0b" << std::bitset<4>(i) << ") = "
                  << std::boolalpha << std::has_single_bit(i) << '\n';
    }
    return 0;
}
```

```Output
has_single_bit(0b0000) = false
has_single_bit(0b0001) = true
has_single_bit(0b0010) = true
has_single_bit(0b0011) = false
has_single_bit(0b0100) = true
has_single_bit(0b0101) = false
has_single_bit(0b0110) = false
has_single_bit(0b0111) = false
has_single_bit(0b1000) = true
has_single_bit(0b1001) = false
```

### <a name="remarks"></a>Bemerkungen

Diese Vorlagen Funktion ist nur an der Überladungs Auflösung beteiligt, wenn `T` ein ganzzahliger Typ ohne Vorzeichen ist. Beispiel: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` usw.

## <a name="popcount"></a>`popcount`

Zählen Sie die Anzahl der Bits, die in einem ganzzahligen Wert ohne Vorzeichen auf einen festgelegt sind.
 
```cpp
template<class T>
[[nodiscard]] constexpr int popcount(T value) noexcept;
```

### <a name="parameters"></a>Parameter

*Wert*\
Der zu testende ganzzahlige Wert ohne Vorzeichen.

### <a name="return-value"></a>Rückgabewert

Die Anzahl von Bits, die in festgelegt sind `value` .

### <a name="example"></a>Beispiel

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
   for (unsigned char value = 0; value < 16; value++)
    {
        std::cout << "\npopcount(0b" << std::bitset<4>(value) << ") = "
                  << std::popcount(value);
    }
    return 0;
}
```

```Output
popcount(0b0000) = 0
popcount(0b0001) = 1
popcount(0b0010) = 1
popcount(0b0011) = 2
popcount(0b0100) = 1
popcount(0b0101) = 2
popcount(0b0110) = 2
popcount(0b0111) = 3
popcount(0b1000) = 1
popcount(0b1001) = 2
popcount(0b1010) = 2
popcount(0b1011) = 3
popcount(0b1100) = 2
popcount(0b1101) = 3
popcount(0b1110) = 3
popcount(0b1111) = 4
```

### <a name="remarks"></a>Bemerkungen

Diese Vorlagen Funktion ist nur an der Überladungs Auflösung beteiligt, wenn `T` ein ganzzahliger Typ ohne Vorzeichen ist. Beispiel: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` usw.

## <a name="rotl"></a>`rotl`

Rotiert die Bits eines ganzzahligen Werts ohne Vorzeichen so oft wie angegeben. Bits, die "aus dem äußersten linken Bit" ausfallen, werden in das äußteste Bit gedreht.
 
```cpp
template<class T>
[[nodiscard]] constexpr T rotl(T value, int s) noexcept;
```

### <a name="parameters"></a>Parameter

*Wert*\
Der zu rolligende ganzzahlige Wert ohne Vorzeichen.

*Hymnen*\
Die Anzahl der durchzuführenden linken Rotationen.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis der Drehung von `value` left, `s` times. \
Wenn `s` 0 (null) ist, wird zurückgegeben `value` . \
Wenn `s` negativ ist, wird von verwendet `rotr(value, -s)` . Bits, die auf das äußteste Bit zurückgreifen, werden in das ganz linke Bit gedreht.

### <a name="example"></a>Beispiel

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char bits = 1;
    for (int i = 0; i < 8; ++i)
    {
        std::cout << "rotl(0b" << std::bitset<8>(bits) << ", 1) = ";
        bits = std::rotl(bits, 1);
        std::cout << "0b" << std::bitset<8>(bits) << '\n';
    }
    std::cout << "rotl(0b" << std::bitset<8>(bits) << ",-1) = ";
    bits = std::rotl(bits, -1);
    std::cout << "0b" << std::bitset<8>(bits);
    return 0;
}
```

```Output
rotl(0b00000001, 1) = 0b00000010
rotl(0b00000010, 1) = 0b00000100
rotl(0b00000100, 1) = 0b00001000
rotl(0b00001000, 1) = 0b00010000
rotl(0b00010000, 1) = 0b00100000
rotl(0b00100000, 1) = 0b01000000
rotl(0b01000000, 1) = 0b10000000
rotl(0b10000000, 1) = 0b00000001
rotl(0b00000001,-1) = 0b10000000
```

### <a name="remarks"></a>Bemerkungen

Diese Vorlagen Funktion ist nur an der Überladungs Auflösung beteiligt, wenn `T` ein ganzzahliger Typ ohne Vorzeichen ist. Beispiel: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` usw.

## <a name="rotr"></a>`rotr`

Rotiert die Bits von `value` right um die angegebene Anzahl von Uhrzeitangaben. Bits, die auf das äußteste Bit zurückgreifen, werden zurück in das äußteste Bit gedreht.
 
```cpp
template<class T>
[[nodiscard]] constexpr T rotr(T value, int s) noexcept;
```

### <a name="parameters"></a>Parameter

*Wert*\
Der zu rolligende ganzzahlige Wert ohne Vorzeichen.

*Hymnen*\
Die Anzahl der richtigen Drehungen, die durchgeführt werden sollen.

### <a name="return-value"></a>Rückgabewert

Das Ergebnis der Drehung von `value` right, `s` times. \
Wenn `s` 0 (null) ist, wird zurückgegeben `value` . \
Wenn `s` negativ ist, wird von verwendet `rotl(value, -s)` . Bits, die auf das linke Bit zurückgreifen, werden zurück in das äußteste Bit gedreht.

### <a name="example"></a>Beispiel

```cpp
#include <bit>
#include <bitset>
#include <iostream>

int main()
{
    unsigned char bits = 128;
    for (int i = 0; i < 8; ++i)
    {
        std::cout << "rotr(0b" << std::bitset<8>(bits) << ", 1) = ";
        bits = std::rotr(bits, 1);
        std::cout << "0b" << std::bitset<8>(bits) << '\n';
    }
    std::cout << "rotr(0b" << std::bitset<8>(bits) << ",-1) = ";
    bits = std::rotr(bits, -1);
    std::cout << "0b" << std::bitset<8>(bits);
    return 0;
}
```

```Output
rotr(0b10000000, 1) = 0b01000000
rotr(0b01000000, 1) = 0b00100000
rotr(0b00100000, 1) = 0b00010000
rotr(0b00010000, 1) = 0b00001000
rotr(0b00001000, 1) = 0b00000100
rotr(0b00000100, 1) = 0b00000010
rotr(0b00000010, 1) = 0b00000001
rotr(0b00000001, 1) = 0b10000000
rotr(0b10000000,-1) = 0b00000001
```

### <a name="remarks"></a>Bemerkungen

Diese Vorlagen Funktion ist nur an der Überladungs Auflösung beteiligt, wenn `T` ein ganzzahliger Typ ohne Vorzeichen ist. Beispiel: `unsigned int` , `unsigned long` , `unsigned short` , `unsigned char` usw.

## <a name="requirements"></a>Requirements (Anforderungen)

**Header:**\<bit>

**Namespace:** std

[/Std: c + + Latest](../build/reference/std-specify-language-standard-version.md) ist erforderlich.

## <a name="see-also"></a>Weitere Informationen

[\<bit>](bit.md)
---
title: Left Shift-und Right Shift-&gt; &gt; Operatoren (und &lt; &lt;)
ms.date: 08/13/2018
f1_keywords:
- <<
- '>>'
helpviewer_keywords:
- << operator [C++], with specific objects
- left shift operators [C++]
- right shift operators [C++]
- bitwise-shift operators [C++]
- '>> operator'
- shift operators [C++]
- operators [C++], shift
ms.assetid: 25fa0cbb-5fdd-4657-8745-b35f7d8f1606
ms.openlocfilehash: 2020c2dbbf8ff91ee692366f55c836be0b3dddb0
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825914"
---
# <a name="left-shift-and-right-shift-operators-gtgt-and-ltlt"></a>Left Shift-und Right Shift-&gt; &gt; Operatoren (und &lt; &lt;)

Die bitweisen Verschiebungs Operatoren sind der Right Shift-Operator**&gt;**(), der die Bits von *Shift-Expression* nach rechts verschiebt, und der Links Schiebe Operator (**&lt;**), der die Bits von *Shift-Expression* nach links verschiebt. <sup>1</sup>

## <a name="syntax"></a>Syntax

> " *Shift-Expression* `<<` *Additives-Expression* "\
> *shift-expression* `>>` *additive-expression*

## <a name="remarks"></a>Bemerkungen

> [!IMPORTANT]
> Die folgenden Beschreibungen und Beispiele sind unter Windows für x86-und x64-Architekturen gültig. Die Implementierung der Operatoren Left Shift und Right Shift unterscheidet sich deutlich von Windows für ARM-Geräte. Weitere Informationen finden Sie im Abschnitt "Shift-Operatoren" des Blogbeitrags [Hello Arm](https://blogs.msdn.com/b/vcblog/archive/2012/10/25/hello-arm-exploring-undefined-unspecified-and-implementation-defined-behavior-in-c.aspx) .

## <a name="left-shifts"></a>Verschiebungen nach links

Der Left Shift-Operator bewirkt, dass die Bits in *Shift-Expression* um die durch *Additiven Ausdruck*angegebene Anzahl von Positionen nach links verschoben werden. Die durch den Verschiebevorgang frei gewordenen Bitpositionen werden mit Nullen angefüllt. Eine Verschiebung nach links ist eine logische Verschiebung (die Bits, die über das Ende hinaus verschoben werden, werden verworfen, einschließlich des Vorzeichenbits). Weitere Informationen zu den Arten von bitweisen Verschiebungen finden Sie unter [bitweise Verschiebungen](https://en.wikipedia.org/wiki/Bitwise_shift).

Im folgenden Codebeispiel wird veranschaulicht, wie Verschiebevorgänge nach links nicht signierte Zahlen verwenden. Das folgende Beispiel veranschaulicht, was mit den Bits geschieht, indem der Wert als ein Bitset dargestellt wird. Weitere Informationen finden Sie unter [Bitset-Klasse](../standard-library/bitset-class.md).

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned short short1 = 4;
    bitset<16> bitset1{short1};   // the bitset representation of 4
    cout << bitset1 << endl;  // 0b00000000'00000100

    unsigned short short2 = short1 << 1;     // 4 left-shifted by 1 = 8
    bitset<16> bitset2{short2};
    cout << bitset2 << endl;  // 0b00000000'00001000

    unsigned short short3 = short1 << 2;     // 4 left-shifted by 2 = 16
    bitset<16> bitset3{short3};
    cout << bitset3 << endl;  // 0b00000000'00010000
}
```

Wenn Sie eine signierte Zahl nach links verschieben, sodass das Vorzeichenbit davon betroffen ist, ist das Ergebnis nicht definiert. Im folgenden Beispiel wird gezeigt, was geschieht, wenn ein 1-Bit in die zeichenbitposition verschoben wird.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short short1 = 16384;
    bitset<16> bitset1(short1);
    cout << bitset1 << endl;  // 0b01000000'00000000

    short short3 = short1 << 1;
    bitset<16> bitset3(short3);  // 16384 left-shifted by 1 = -32768
    cout << bitset3 << endl;  // 0b10000000'00000000

    short short4 = short1 << 14;
    bitset<16> bitset4(short4);  // 4 left-shifted by 14 = 0
    cout << bitset4 << endl;  // 0b00000000'00000000
}
```

## <a name="right-shifts"></a>Verschiebungen nach rechts

Der Right Shift-Operator bewirkt, dass das Bitmuster in *Shift-Expression* um die durch *Additiven Ausdruck*angegebene Anzahl von Positionen nach rechts verschoben wird. Für unsignierte Zahlen werden die durch den Verschiebevorgang frei gewordenen Bitpositionen mit Nullen angefüllt. Für signierte Zahlen wird das Vorzeichenbit verwendet, um die frei gewordenen Bitpositionen zu füllen. In anderen Worten, wenn die Zahl positiv ist, wird 0 verwendet, und wenn die Zahl negativ ist, wird 1 verwendet.

> [!IMPORTANT]
> Das Ergebnis der Verschiebung einer signierten negativen Zahl nach rechts ist implementierungsabhängig. Obwohl der Microsoft C++-Compiler das Signier Bit zum Auffüllen von frei gewordenen Bitpositionen verwendet, gibt es keine Garantie dafür, dass auch andere Implementierungen dies tun.

Dieses Beispiel veranschaulicht, wie Verschiebevorgänge nach rechts nicht signierte Zahlen verwenden:

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned short short11 = 1024;
    bitset<16> bitset11{short11};
    cout << bitset11 << endl;     // 0b00000100'00000000

    unsigned short short12 = short11 >> 1;  // 512
    bitset<16> bitset12{short12};
    cout << bitset12 << endl;     // 0b00000010'00000000

    unsigned short short13 = short11 >> 10;  // 1
    bitset<16> bitset13{short13};
    cout << bitset13 << endl;     // 0b00000000'00000001

    unsigned short short14 = short11 >> 11;  // 0
    bitset<16> bitset14{short14};
    cout << bitset14 << endl;     // 0b00000000'00000000
}
```

Das nächste Beispiel zeigt Verschiebevorgänge nach rechts mit positiven, signierten Zahlen.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short short1 = 1024;
    bitset<16> bitset1(short1);
    cout << bitset1 << endl;     // 0b00000100'00000000

    short short2 = short1 >> 1;  // 512
    bitset<16> bitset2(short2);
    cout << bitset2 << endl;     // 0b00000010'00000000

    short short3 = short1 >> 11;  // 0
    bitset<16> bitset3(short3);
    cout << bitset3 << endl;     // 0b00000000'00000000
}
```

Das nächste Beispiel zeigt Verschiebevorgänge nach rechts mit negativen, signierten Ganzzahlen.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    short neg1 = -16;
    bitset<16> bn1(neg1);
    cout << bn1 << endl;  // 0b11111111'11110000

    short neg2 = neg1 >> 1; // -8
    bitset<16> bn2(neg2);
    cout << bn2 << endl;  // 0b11111111'11111000

    short neg3 = neg1 >> 2; // -4
    bitset<16> bn3(neg3);
    cout << bn3 << endl;  // 0b11111111'11111100

    short neg4 = neg1 >> 4; // -1
    bitset<16> bn4(neg4);
    cout << bn4 << endl;  // 0b11111111'11111111

    short neg5 = neg1 >> 5; // -1
    bitset<16> bn5(neg5);
    cout << bn5 << endl;  // 0b11111111'11111111
}
```

## <a name="shifts-and-promotions"></a>Verschiebungen und Heraufstufungen

Die Ausdrücke auf beiden Seiten eines Schiebeoperators müssen vom Typ „Ganzzahl“ sein. Ganzzahlige Erweiterungen werden gemäß den in [Standard Konvertierungen](standard-conversions.md)beschriebenen Regeln ausgeführt. Der Ergebnistyp ist mit dem Typ des höher *gestuften Shift-Ausdrucks*identisch.

Im folgenden Beispiel wird eine Variable vom Typ **char** zu **int**herauf gestuft.

```cpp
#include <iostream>
#include <typeinfo>

using namespace std;

int main() {
    char char1 = 'a';

    auto promoted1 = char1 << 1;   // 194
    cout << typeid(promoted1).name() << endl;  // int

    auto promoted2 = char1 << 10;  // 99328
    cout << typeid(promoted2).name() << endl;  // int
}
```

## <a name="additional-details"></a>Weitere Details

Das Ergebnis einer Verschiebungs Operation ist nicht definiert, wenn *Additives Ausdruck* negativ ist oder wenn *Additives Ausdruck* größer oder gleich der Anzahl der Bits im (höher gestuften) *Shift-Ausdruck*ist. Wenn *Additives Ausdruck* 0 ist, wird kein Verschiebungs Vorgang ausgeführt.

```cpp
#include <iostream>
#include <bitset>

using namespace std;

int main() {
    unsigned int int1 = 4;
    bitset<32> b1{int1};
    cout << b1 << endl;    // 0b00000000'00000000'00000000'00000100

    unsigned int int2 = int1 << -3;  // C4293: '<<' : shift count negative or too big, undefined behavior
    unsigned int int3 = int1 >> -3;  // C4293: '>>' : shift count negative or too big, undefined behavior
    unsigned int int4 = int1 << 32;  // C4293: '<<' : shift count negative or too big, undefined behavior
    unsigned int int5 = int1 >> 32;  // C4293: '>>' : shift count negative or too big, undefined behavior
    unsigned int int6 = int1 << 0;
    bitset<32> b6{int6};
    cout << b6 << endl;    // 0b00000000'00000000'00000000'00000100 (no change)
}
```

## <a name="footnotes"></a>Fußnoten

<sup>1</sup> im folgenden finden Sie die Beschreibung der Shift-Operatoren in der ISO-Spezifikation c++ 11 (INCITS/ISO/IEC 14882-2011 [2012]), Abschnitte 5.8.2 und 5.8.3.

Der Wert von `E1 << E2` ist `E1` nach links verschobene `E2`-Bitpositionen; frei gewordene Bitpositionen werden mit Nullen angefüllt. Wenn `E1` einen nicht signierten Typ hat, ist der Wert des Ergebnisses **E1 × 2**<sup>**E2**</sup>, wobei das reduzierte Modulo eins mehr als der maximale Wert ist, der im Ergebnistyp dargestellt werden kann. Wenn `E1` andernfalls über einen signierten Typ und einen nicht negativen Wert verfügt und **E1 × 2**<sup>**E2**</sup> im entsprechenden nicht signierten Typ des Ergebnis Typs dargestellt werden kann, ist dieser Wert, der in den Ergebnistyp konvertiert wird, der resultierende Wert. Andernfalls ist das Verhalten nicht definiert.

Der Wert von `E1 >> E2` ist `E1` nach rechts verschobene `E2`-Bitpositionen. Wenn `E1` einen nicht signierten Typ hat oder `E1` wenn einen signierten Typ und einen nicht negativen Wert hat, ist der Wert des Ergebnisses der integrale Teil des quotients von **E1/2**<sup>**E2**</sup>. Wenn `E1` einen signierten Typ und einen negativen Wert hat, ist der Ergebniswert durch die Implementierung definiert.

## <a name="see-also"></a>Weitere Informationen

[Ausdrücke mit binären Operatoren](../cpp/expressions-with-binary-operators.md)<br/>
[Integrierte C++-Operatoren, Rangfolge und Assoziativität](../cpp/cpp-built-in-operators-precedence-and-associativity.md)

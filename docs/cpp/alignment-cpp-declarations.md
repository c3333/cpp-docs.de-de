---
title: Ausrichtung
description: Gibt an, wie die Daten Ausrichtung in modernem C++ angegeben wird.
ms.date: 12/11/2019
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
ms.openlocfilehash: 7f6bef061fee41389bad644d9ac5244f5644da76
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227646"
---
# <a name="alignment"></a>Ausrichtung

Eines der Features von C++ auf niedriger Ebene ist die Möglichkeit zum Angeben der präzisen Ausrichtung von Objekten im Speiche, um eine bestimmte Hardwarearchitektur optimal zu nutzen. Standardmäßig richtet der Compiler Klassen-und Strukturmember auf ihren Größen Wert aus: **`bool`** und **`char`** an 1-Byte-Begrenzungen, **`short`** an 2-Byte-Begrenzungen,, **`int`** **`long`** und **`float`** an 4-Byte-Begrenzungen und **`long long`** , **`double`** und **`long double`** auf 8-Byte-Begrenzungen.

In den meisten Szenarien müssen Sie sich nicht mit der Ausrichtung beschäftigen, da die Standardausrichtung bereits optimal ist. In einigen Fällen können Sie jedoch bedeutende Leistungsverbesserungen oder Speicher Einsparungen erzielen, indem Sie eine benutzerdefinierte Ausrichtung für Ihre Datenstrukturen angeben. Vor Visual Studio 2015 konnten Sie die Microsoft-spezifischen Schlüsselwörter verwenden **`__alignof`** und **`__declspec(align)`** eine Ausrichtung angeben, die größer als die Standardeinstellung ist. Ab Visual Studio 2015 sollten Sie die c++ 11-Standard Schlüsselwörter **`alignof`** und **`alignas`** für die maximale Code Portabilität verwenden. Die neuen Schlüsselwörter Verhalten sich auf die gleiche Weise wie die Microsoft-spezifischen Erweiterungen. Die Dokumentation für diese Erweiterungen gilt auch für die neuen Schlüsselwörter. Weitere Informationen finden Sie unter [ `alignof` Operator](../cpp/alignof-operator.md) und [align](../cpp/align-cpp.md). Der C++-Standard gibt kein Verpackungs Verhalten für die Ausrichtung an Grenzen an, die kleiner als der Compilerstandard für die Zielplattform sind, sodass Sie in diesem Fall weiterhin Microsoft verwenden müssen [`#pragma pack`](../preprocessor/pack.md) .

Verwenden Sie die [aligned_storage-Klasse](../standard-library/aligned-storage-class.md) für die Speicher Belegung von Datenstrukturen mit benutzerdefinierten Ausrichtungen. Die [aligned_union-Klasse](../standard-library/aligned-union-class.md) dient zum Angeben der Ausrichtung für Unions mit nicht trivialen Konstruktoren oder Dekonstruktoren.

## <a name="alignment-and-memory-addresses"></a>Ausrichtung und Speicheradressen

Die Ausrichtung ist eine Eigenschaft einer Speicheradresse, ausgedrückt als numerisches Adressmodulo der Potenz 2. Beispielsweise ist die Adresse 0x0001103f modulo 4 3. Diese Adresse wird als "4N + 3" ausgerichtet, wobei "4" die gewählte Potenz von 2 angibt. Die Ausrichtung einer Adresse hängt von der gewählten Potenz von 2 ab. Das gleiche Adressmodulo 8 ist 7. Eine Adresse wird als an X ausgerichtet betrachtet, wenn die Ausrichtung Xn+ 0 ist.

CPUs führen Anweisungen aus, die für im Arbeitsspeicher gespeicherte Daten verwendet werden. Die Daten werden durch Ihre Adressen im Arbeitsspeicher identifiziert. Ein einzelnes Datum weist auch eine Größe auf. Wir nennen ein Datum, das *natürlich ausgerichtet* ist, wenn seine Adresse auf seine Größe abgestimmt ist. Andernfalls wird Sie als *falsch ausgerichtet* bezeichnet. Beispielsweise ist ein 8-Byte-Gleit Komma Datum natürlich ausgerichtet, wenn die Adresse, die zur Identifizierung verwendet wird, eine 8-Byte-Ausrichtung hat.

## <a name="compiler-handling-of-data-alignment"></a>Compilerbehandlung der Daten Ausrichtung

Compiler versuchen, Daten Zuordnungen auf eine Weise zu erstellen, die eine Fehlausrichtung der Daten verhindert.

Der Compiler weist für einfache Datentypen Adressen zu, die ein Vielfaches der Größe in Bytes des Datentyps entsprechen. Der Compiler weist z. b. Adressen Variablen vom Typ zu, die ein **`long`** Vielfaches von 4 sind, wobei die untersten Bits der Adresse auf 0 (null) festgelegt werden.

Der Compiler füllt auch Strukturen auf eine Weise auf, die jedes Element der Struktur auf natürliche Weise anpasst. Sehen Sie sich die Struktur `struct x_` im folgenden Codebeispiel an:

```cpp
struct x_
{
   char a;     // 1 byte
   int b;      // 4 bytes
   short c;    // 2 bytes
   char d;     // 1 byte
} bar[3];
```

Der Compiler füllt die Struktur, um die natürliche Ausrichtung zu erzwingen.

Im folgenden Codebeispiel wird gezeigt, wie der Compiler die aufgefüllte Struktur in den Arbeitsspeicher platziert:

```cpp
// Shows the actual memory layout
struct x_
{
   char a;            // 1 byte
   char _pad0[3];     // padding to put 'b' on 4-byte boundary
   int b;            // 4 bytes
   short c;          // 2 bytes
   char d;           // 1 byte
   char _pad1[1];    // padding to make sizeof(x_) multiple of 4
} bar[3];
```

Beide Deklarationen geben `sizeof(struct x_)` als 12 Bytes zurück.

Die zweite Deklaration enthält zwei Auffüllelemente:

1. `char _pad0[3]`, wenn der `int b` Member an einer 4-Byte-Grenze ausgerichtet werden soll.

1. `char _pad1[1]`, wenn die Array Elemente der-Struktur `struct _x bar[3];` an einer vier-Byte-Grenze ausgerichtet werden sollen.

Der Abstand richtet die Elemente von `bar[3]` auf eine Weise aus, die natürlichen Zugriff zulässt.

Das folgende Codebeispiel zeigt das `bar[3]` Array Layout:

```Output
adr offset   element
------   -------
0x0000   char a;         // bar[0]
0x0001   char pad0[3];
0x0004   int b;
0x0008   short c;
0x000a   char d;
0x000b   char _pad1[1];

0x000c   char a;         // bar[1]
0x000d   char _pad0[3];
0x0010   int b;
0x0014   short c;
0x0016   char d;
0x0017   char _pad1[1];

0x0018   char a;         // bar[2]
0x0019   char _pad0[3];
0x001c   int b;
0x0020   short c;
0x0022   char d;
0x0023   char _pad1[1];
```

## <a name="alignof-and-alignas"></a>`alignof` und `alignas`

Der **`alignas`** Typspezifizierer ist eine Portable, C++-Standardmethode zum Angeben der benutzerdefinierten Ausrichtung von Variablen und benutzerdefinierten Typen. Der **`alignof`** Operator ist ebenso eine standardmäßige, Portable Methode zum Abrufen der Ausrichtung eines bestimmten Typs oder einer Variablen.

## <a name="example"></a>Beispiel

Sie können **`alignas`** für eine Klasse, Struktur oder Union oder für einzelne Member verwenden. Wenn mehrere **`alignas`** spezifier gefunden wird, wählt der Compiler den strengsten Wert aus (der mit dem größten Wert).

```cpp
// alignas_alignof.cpp
// compile with: cl /EHsc alignas_alignof.cpp
#include <iostream>

struct alignas(16) Bar
{
    int i;       // 4 bytes
    int n;      // 4 bytes
    alignas(4) char arr[3];
    short s;          // 2 bytes
};

int main()
{
    std::cout << alignof(Bar) << std::endl; // output: 16
}
```

## <a name="see-also"></a>Siehe auch

[Ausrichtung der Datenstruktur](https://en.wikipedia.org/wiki/Data_structure_alignment)

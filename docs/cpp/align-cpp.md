---
title: align (C++)
ms.date: 12/17/2018
f1_keywords:
- align_cpp
helpviewer_keywords:
- align __declspec keyword
- __declspec keyword [C++], align
ms.assetid: 9cb63f58-658b-4425-ac47-af8eabfc5878
ms.openlocfilehash: 227053fbfa4190dc6227ba7096a7c76aef30bb54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181550"
---
# <a name="align-c"></a>align (C++)

Verwenden Sie in Visual Studio 2015 und höher den c++ 11-Standar`alignas` dspezifizierer, um die Ausrichtung zu steuern. Weitere Informationen finden Sie unter [Alignment](../cpp/alignment-cpp-declarations.md).

**Microsoft-spezifisch**

Verwenden Sie `__declspec(align(#))`, um die Ausrichtung von benutzerdefinierten Daten genau zu steuern (z. B. statische Speicherbelegungen oder automatische Daten in einer Funktion.)

## <a name="syntax"></a>Syntax

> **__declspec (** *#* **))** *Deklarator*

## <a name="remarks"></a>Bemerkungen

Das Schreiben von Anwendungen, die die neuesten Prozessoranweisungen verwenden, bringt mehrere neue Einschränkungen und Probleme mit sich. Insbesondere machen viele neue Anweisungen die Ausrichtung von Daten an 16-Byte-Grenzen erforderlich. Darüber hinaus verbessern Sie durch die Ausrichtung häufig verwendeter Daten an der Cachezeilengröße eines bestimmten Prozessors die Cacheleistung. Wenn Sie beispielsweise eine Struktur definieren, deren Größe kleiner ist als 32 Bytes, sollten Sie sie an 32 Bytes ausrichten, um sicherzustellen, dass Objekte dieses Strukturtyps effizient zwischengespeichert werden.

\# ist der Ausrichtungs Wert. Gültige Einträge sind ganzzahlige Potenzen von zwei von 1 bis 8192 (Bytes), z. B. 2, 4, 8, 16, 32 oder 64. `declarator` sind die Daten, die Sie als ausgerichtet deklarieren.

Weitere Informationen zum Zurückgeben eines Werts vom Typ `size_t`, der die Ausrichtungs Anforderung des Typs ist, finden Sie unter [__alignof](../cpp/alignof-operator.md). Informationen zum Deklarieren von nicht ausgerichteten Zeigern beim Ausrichten von 64-Bit-Prozessoren finden Sie unter [__unaligned](../cpp/unaligned.md).

Sie können `__declspec(align(#))` verwenden, wenn Sie eine **Struktur**, **Union**oder **Klasse**definieren, oder wenn Sie eine Variable deklarieren.

Der Compiler gewährleistet oder versucht nicht, das Ausrichtungsattribut der Daten während des Kopierens oder Transformierens von Daten beizubehalten. [Memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) kann z. b. eine mit `__declspec(align(#))` deklarierte Struktur an einen beliebigen Speicherort kopieren. Beachten Sie, dass normale Zuweisungen – z. b. [malloc](../c-runtime-library/reference/malloc.md), C++ [Operator new](new-operator-cpp.md)und Win32-Zuweisungen – Arbeitsspeicher zurückgeben, der in der Regel nicht ausreichend für `__declspec(align(#))` Strukturen oder Struktur Arrays ausgerichtet ist. Um sicherzustellen, dass das Ziel eines Kopier-oder Daten Transformations Vorgangs ordnungsgemäß ausgerichtet ist, verwenden Sie [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md), oder schreiben Sie eine eigene Zuweisung.

Die Ausrichtung für Funktionsparameter können Sie nicht angeben. Wenn die Daten, die über ein Ausrichtungsattribut verfügen, als Wert auf dem Stapel übergeben werden, wird die Ausrichtung durch die Aufrufkonvention gesteuert. Falls die Datenausrichtung in der aufgerufenen Funktion wichtig ist, kopieren Sie vor der Verwendung den Parameter in den korrekt ausgerichteten Speicher.

Ohne `__declspec(align(#))`richtet der Compiler im allgemeinen Daten auf natürlichen Begrenzungen basierend auf dem Zielprozessor und der Größe der Daten, bis zu 4-Byte-Begrenzungen auf 32-Bit-Prozessoren und 8-Byte-Begrenzungen auf 64-Bit-Prozessoren aus. Daten in Klassen oder Strukturen werden in der Klasse oder Struktur am Minimum ihrer natürlichen Ausrichtung und der aktuellen Verpackungseinstellung ausgerichtet (von #Pragma `pack` oder der `/Zp`-Compileroption).

In diesem Beispiel wird die Verwendung von `__declspec(align(#))` veranschaulicht:

```cpp
__declspec(align(32)) struct Str1{
   int a, b, c, d, e;
};
```

Dieser Typ verfügt nun über ein 32-Byte-Ausrichtungsattribut. Dies bedeutet, dass alle statischen und automatischen Instanzen auf einer 32-Byte-Begrenzung beginnen. Zusätzliche Strukturtypen, die mit diesem Typ als Member deklariert sind, behalten das Ausrichtungs Attribut dieses Typs bei, d. h. jede Struktur, die `Str1` als Element hat, verfügt über ein Ausrichtungs Attribut von mindestens 32.

Beachten Sie, dass `sizeof(struct Str1)` gleich 32 ist. Wenn ein Array von Str1-Objekten erstellt wird und die Basis des Arrays mit 32 Bytes ausgerichtet ist, ist demnach jeder Member des Arrays auch mit 32 Bytes ausgerichtet. Um ein Array zu erstellen, dessen Basis ordnungsgemäß im dynamischen Arbeitsspeicher ausgerichtet ist, verwenden Sie [_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md), oder schreiben Sie eine eigene Zuweisung.

Der `sizeof`-Wert für jede Struktur ist der Offset des letzten Members plus die Größe dieses Members, aufgerundet auf das nächste Vielfache des größten Memberausrichtungswerts oder den Ausrichtungswert der gesamten Struktur, je nachdem, welcher Wert größer ist.

Für die Strukturausrichtung verwendet der Compiler diese Regeln:

- Sofern sie nicht mit `__declspec(align(#))` überschrieben wird, ist die Ausrichtung eines skalaren Strukturmembers das Minimum seiner Größe und der aktuellen Verpackung.

- Sofern sie nicht mit `__declspec(align(#))` überschrieben wird, ist die Ausrichtung einer Struktur das Maximum der einzelnen Ausrichtungen ihrer Member.

- Ein Strukturmember wird bei einem Offset vom Anfang seiner übergeordneten Struktur platziert, die das kleinste Vielfache seiner Ausrichtung größer oder gleich dem Offset des Endes des vorhergehenden Members ist.

- Die Größe einer Struktur ist das kleinste Vielfache seiner Ausrichtung größer oder gleich dem Offset des Endes des letzten Members.

`__declspec(align(#))` kann lediglich Ausrichtungseinschränkungen erhöhen.

Weitere Informationen finden Sie unter

- [Beispiele ausrichten](#vclrfalignexamples)

- [Definieren neuer Typen mit __declspec (ausrichten (#))](#vclrf_declspecaligntypedef)

- [Ausrichten von Daten im lokalen Thread Speicher](#vclrfthreadlocalstorageallocation)

- [Funktionsweise von "ausrichten" mit Daten Verpackung](#vclrfhowalignworkswithdatapacking)

- [Beispiele für die Struktur Ausrichtung](../build/x64-software-conventions.md#examples-of-structure-alignment) (x64-spezifisch)

## <a name="align-examples"></a><a name="vclrfalignexamples"></a>Beispiele ausrichten

Die folgenden Beispiele zeigen, wie sich `__declspec(align(#))` auf die Größe und die Ausrichtung der Datenstrukturen auswirkt. Die Beispiele gehen von folgenden Definitionen aus:

```cpp
#define CACHE_LINE  32
#define CACHE_ALIGN __declspec(align(CACHE_LINE))
```

In diesem Beispiel wird die `S1`-Struktur mit `__declspec(align(32))` definiert. Alle Verwendungen von `S1` für eine Variablendefinition oder andere Typdeklarationen sind mit 32 Bytes ausgerichtet. `sizeof(struct S1)` gibt 32 zurück, und `S1` weist 16 Auffüll-Bytes auf, die den 16 Bytes folgen, die für die Aufnahme der vier ganzen Zahlen erforderlich sind. Jedes **int** -Element erfordert eine 4-Byte-Ausrichtung, aber die Ausrichtung der Struktur selbst wird als 32 deklariert. Daher ist die Gesamtausrichtung 32.

```cpp
struct CACHE_ALIGN S1 { // cache align all instances of S1
   int a, b, c, d;
};
struct S1 s1;   // s1 is 32-byte cache aligned
```

In diesem Beispiel gibt `sizeof(struct S2)` 16 zurück, was genau der Summe der Membergrößen entspricht, da es ein Vielfaches der größten Ausrichtungsanforderung (ein Vielfaches von 8) ist.

```cpp
__declspec(align(8)) struct S2 {
   int a, b, c, d;
};
```

Im folgenden Beispiel gibt `sizeof(struct S3)` 64 zurück.

```cpp
struct S3 {
   struct S1 s1;   // S3 inherits cache alignment requirement
                  // from S1 declaration
   int a;         // a is now cache aligned because of s1
                  // 28 bytes of trailing padding
};
```

Beachten Sie in diesem Beispiel, dass `a` die Ausrichtung des natürlichen Typs, in diesem Fall 4 Bytes, aufweist. Allerdings muss `S1` mit 32 Bytes ausgerichtet sein. 28 Auffüll-Bytes folgen `a`, sodass `s1` am Offset 32 beginnt. `S4` erbt dann die Ausrichtungsanforderung von `S1`, da es die größte Anforderungsausrichtung in der Struktur ist. `sizeof(struct S4)` gibt 64 zurück.

```cpp
struct S4 {
   int a;
   // 28 bytes padding
    struct S1 s1;      // S4 inherits cache alignment requirement of S1
};
```

Die folgenden drei Variablendeklarationen verwenden auch `__declspec(align(#))`. In jedem Fall muss die Variable mit 32 Bytes ausgerichtet sein. Im Fall des Arrays ist die Basisadresse des Arrays, nicht jeder Arraymember, mit 32 Bytes ausgerichtet. Der `sizeof`-Wert für jeden Arraymember wird nicht von der Verwendung von `__declspec(align(#))` beeinflusst.

```cpp
CACHE_ALIGN int i;
CACHE_ALIGN int array[128];
CACHE_ALIGN struct s2 s;
```

Um jeden Member eines Arrays auszurichten, sollte Code wie dieser verwendet werden:

```cpp
typedef CACHE_ALIGN struct { int a; } S5;
S5 array[10];
```

In diesem Beispiel sehen Sie, dass die Ausrichtung der Struktur selbst und die Ausrichtung des ersten Elements identisch sind:

```cpp
CACHE_ALIGN struct S6 {
   int a;
   int b;
};

struct S7 {
   CACHE_ALIGN int a;
               int b;
};
```

`S6` und `S7` weisen identische Ausrichtungs-, Speicherbelegungs- und Größeneigenschaften auf.

In diesem Beispiel ist die Ausrichtung der Startadressen von a, b, c und d jeweils 4, 1, 4 und 1.

```cpp
void fn() {
   int a;
   char b;
   long c;
   char d[10]
}
```

Wenn der Speicher für Heaps zugewiesen wird, hängt die Ausrichtung davon ab, welche Speicherbelegungsfunktion aufgerufen wird.  Wenn Sie beispielsweise `malloc` verwenden, hängt das Ergebnis von der Größe des Operanden ab. Wenn *arg* > = 8, wird der zurückgegebene Arbeitsspeicher auf 8 Byte ausgerichtet. Wenn *arg* < 8 ist, ist die Ausrichtung des zurückgegebenen Arbeitsspeichers die erste Potenz von 2 weniger als *arg*. Wenn Sie beispielsweise "malloc(7)" verwenden, ist die Ausrichtung 4 Bytes.

## <a name="defining-new-types-with-__declspecalign"></a><a name="vclrf_declspecaligntypedef"></a>Definieren neuer Typen mit __declspec (ausrichten (#))

Sie können einen Typ mit einem Ausrichtungsmerkmal definieren.

Beispielsweise können Sie eine `struct` wie folgt mit einem Ausrichtungs Wert definieren:

```cpp
struct aType {int a; int b;};
typedef __declspec(align(32)) struct aType bType;
```

Jetzt sind `aType` und `bType` die gleiche Größe (8 Bytes), aber Variablen vom Typ `bType` sind 32-Byte-ausgerichtet.

## <a name="aligning-data-in-thread-local-storage"></a><a name="vclrfthreadlocalstorageallocation"></a>Ausrichten von Daten im lokalen Thread Speicher

Statische lokale Threadspeicher (TLS), die mit dem `__declspec(thread)`-Attribut erstellt und im TLS-Abschnitt des Images platziert wurden, verhalten sich bei der Ausrichtung wie normale statische Daten. Zum Erstellen von TLS-Daten ordnet das Betriebssystem die Größe des TLS-Abschnitts zu und berücksichtigt das Ausrichtungsattribut für TLS-Abschnitte.

Dieses Beispiel zeigt verschiedene Möglichkeiten, ausgerichtete Daten in den threadlokalen Speicher zu platzieren.

```cpp
// put an aligned integer in TLS
__declspec(thread) __declspec(align(32)) int a;

// define an aligned structure and put a variable of the struct type
// into TLS
__declspec(thread) __declspec(align(32)) struct F1 { int a; int b; } a;

// create an aligned structure
struct CACHE_ALIGN S9 {
   int a;
   int b;
};
// put a variable of the structure type into TLS
__declspec(thread) struct S9 a;
```

## <a name="how-align-works-with-data-packing"></a><a name="vclrfhowalignworkswithdatapacking"></a>Funktionsweise von "ausrichten" mit Daten Verpackung

Die `/Zp`-Compileroption und das `pack`-Pragma haben den Effekt, dass Daten für Struktur-und Union-Member verpackt werden. Dieses Beispiel zeigt, wie `/Zp` und `__declspec(align(#))` zusammenarbeiten:

```cpp
struct S {
   char a;
   short b;
   double c;
   CACHE_ALIGN double d;
   char e;
   double f;
};
```

Die folgende Tabelle zeigt den Offset eines jeden Members mit einer Vielzahl von `/Zp` (oder #pragma `pack`)-Werten, wobei gezeigt wird, wie die beiden interagieren.

|Variable|/Zp1|/Zp2|/Zp4|/Zp8|
|--------------|-----------|-----------|-----------|-----------|
|a|0|0|0|0|
|b|1|2|2|2|
|c|3|4|4|8|
|d|32|32|32|32|
|e|40|40|40|40|
|f|41|42|44|48|
|sizeof(S)|64|64|64|64|

Weitere Informationen finden Sie unter [/Zp (Ausrichten des Strukturmembers)](../build/reference/zp-struct-member-alignment.md).

Der Offset eines Objekts basiert auf dem Offset des vorherigen Objekts und der aktuellen Verpackungseinstellung, es sei denn, das Objekt weist ein `__declspec(align(#))`-Attribut auf. In diesem Fall basiert die Ausrichtung auf dem Offset des vorherigen Objekts und dem `__declspec(align(#))`-Wert für das Objekt.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Weitere Informationen

[__declspec](../cpp/declspec.md)<br/>
[Übersicht über ARM-ABI-Konventionen](../build/overview-of-arm-abi-conventions.md)<br/>
[Softwarekonventionen bei x64-Systemen](../build/x64-software-conventions.md)

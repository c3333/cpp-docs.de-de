---
title: align (C++)
ms.date: 12/17/2018
f1_keywords:
- align_cpp
helpviewer_keywords:
- align __declspec keyword
- __declspec keyword [C++], align
ms.assetid: 9cb63f58-658b-4425-ac47-af8eabfc5878
ms.openlocfilehash: 0a1212f1c78f49029f82be5a2f5d82ea1788b6e0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227659"
---
# <a name="align-c"></a>align (C++)

Verwenden Sie in Visual Studio 2015 und höher den c++ 11- **`alignas`** standardspezifizierer, um die Ausrichtung zu steuern. Weitere Informationen finden Sie unter [Alignment](../cpp/alignment-cpp-declarations.md).

**Microsoft-spezifisch**

Verwenden Sie `__declspec(align(#))`, um die Ausrichtung von benutzerdefinierten Daten genau zu steuern (z. B. statische Speicherbelegungen oder automatische Daten in einer Funktion.)

## <a name="syntax"></a>Syntax

> **__declspec (** *#* )- *Deklarator* (align ( **))**

## <a name="remarks"></a>Bemerkungen

Das Schreiben von Anwendungen, die die neuesten Prozessoranweisungen verwenden, bringt mehrere neue Einschränkungen und Probleme mit sich. Viele neue Anweisungen erfordern Daten, die auf 16-Byte-Grenzen ausgerichtet sind. Außerdem verbessern Sie durch die Ausrichtung häufig verwendeter Daten an der Cache Zeilengröße des Prozessors die Cache Leistung. Wenn Sie z. b. eine Struktur definieren, deren Größe kleiner als 32 Bytes ist, sollten Sie eine 32-Byte-Ausrichtung wünschen, um sicherzustellen, dass Objekte dieses Struktur Typs effizient zwischengespeichert werden.

\#der Ausrichtungs Wert. Gültige Einträge sind ganzzahlige Potenzen von zwei von 1 bis 8192 (Bytes), z. B. 2, 4, 8, 16, 32 oder 64. `declarator`die Daten, die Sie als ausgerichtet deklarieren.

Informationen dazu, wie Sie einen Wert vom Typ zurückgeben, der `size_t` die Ausrichtungs Anforderung des Typs ist, finden Sie unter [`alignof`](../cpp/alignof-operator.md) . Informationen zum Deklarieren von nicht ausgerichteten Zeigern beim Ausrichten von 64-Bit-Prozessoren finden Sie unter [`__unaligned`](../cpp/unaligned.md) .

Sie können verwenden, `__declspec(align(#))` Wenn Sie **`struct`** , oder definieren **`union`** **`class`** , oder wenn Sie eine Variable deklarieren.

Der Compiler garantiert oder versucht nicht, das Ausrichtungs Attribut von Daten während eines Kopier-oder Daten Transformations Vorgangs beizubehalten. Beispielsweise [`memcpy`](../c-runtime-library/reference/memcpy-wmemcpy.md) kann eine mit deklarierte Struktur `__declspec(align(#))` an einen beliebigen Speicherort kopieren. Normale Zuweisungen (z. b. [`malloc`](../c-runtime-library/reference/malloc.md) , C++ [`operator new`](new-operator-cpp.md) und die Win32-Zuweisungen) geben normalerweise Arbeitsspeicher zurück, der nicht ausreichend für `__declspec(align(#))` Strukturen oder Struktur Arrays ausgerichtet ist. Um sicherzustellen, dass das Ziel eines Kopier-oder Daten Transformations Vorgangs ordnungsgemäß ausgerichtet ist, verwenden Sie [`_aligned_malloc`](../c-runtime-library/reference/aligned-malloc.md) . Oder schreiben Sie Ihre eigene Zuweisung.

Sie können keine Ausrichtung für Funktionsparameter angeben. Wenn Sie Daten, die über ein Ausrichtungs Attribut verfügen, nach Wert auf dem Stapel übergeben, wird die Ausrichtung durch die Aufruf Konvention gesteuert. Falls die Datenausrichtung in der aufgerufenen Funktion wichtig ist, kopieren Sie vor der Verwendung den Parameter in den korrekt ausgerichteten Speicher.

Ohne `__declspec(align(#))` richtet der Compiler Daten auf natürlichen Grenzen basierend auf dem Zielprozessor und der Größe der Daten, bis zu 4-Byte-Begrenzungen auf 32-Bit-Prozessoren und 8-Byte-Begrenzungen auf 64-Bit-Prozessoren aus. Daten in Klassen oder Strukturen werden in der Klasse oder Struktur am Minimalwert ihrer natürlichen Ausrichtung und der aktuellen Verpackungs Einstellung (von `#pragma pack` oder der- `/Zp` Compileroption) ausgerichtet.

In diesem Beispiel wird die Verwendung von `__declspec(align(#))` veranschaulicht:

```cpp
__declspec(align(32)) struct Str1{
   int a, b, c, d, e;
};
```

Dieser Typ verfügt nun über ein 32-Byte-Ausrichtungsattribut. Dies bedeutet, dass alle statischen und automatischen Instanzen an einer 32-Byte-Grenze beginnen. Zusätzliche Strukturtypen, die mit diesem Typ als Member deklariert sind, behalten das Ausrichtungs Attribut dieses Typs bei, d. h. jede Struktur mit `Str1` als Element hat ein Ausrichtungs Attribut von mindestens 32.

Hier `sizeof(struct Str1)` ist gleich 32. Wenn ein Array von- `Str1` Objekten erstellt wird und die Basis des Arrays 32-Byte-ausgerichtet ist, ist dies impliziert, dass jedes Element des-Arrays ebenfalls 32-Byte-ausgerichtet ist. Verwenden Sie, um ein Array zu erstellen, dessen Basis ordnungsgemäß im dynamischen Arbeitsspeicher ausgerichtet ist [`_aligned_malloc`](../c-runtime-library/reference/aligned-malloc.md) . Oder schreiben Sie Ihre eigene Zuweisung.

Der **`sizeof`** Wert für jede Struktur ist der Offset des letzten Elements, zuzüglich der Größe dieses Elements, aufgerundet auf das nächste Vielfache des größten Members-Ausrichtungs Werts oder auf den gesamten Struktur Ausrichtungs Wert, je nachdem, welcher Wert größer ist.

Für die Strukturausrichtung verwendet der Compiler diese Regeln:

- Sofern sie nicht mit `__declspec(align(#))` überschrieben wird, ist die Ausrichtung eines skalaren Strukturmembers das Minimum seiner Größe und der aktuellen Verpackung.

- Sofern sie nicht mit `__declspec(align(#))` überschrieben wird, ist die Ausrichtung einer Struktur das Maximum der einzelnen Ausrichtungen ihrer Member.

- Ein Strukturmember wird bei einem Offset vom Anfang seiner übergeordneten Struktur platziert, die das kleinste Vielfache seiner Ausrichtung größer oder gleich dem Offset des Endes des vorherigen Members ist.

- Die Größe einer Struktur ist das kleinste Vielfache seiner Ausrichtung größer oder gleich dem Offset des Endes des letzten Members.

`__declspec(align(#))` kann lediglich Ausrichtungseinschränkungen erhöhen.

Weitere Informationen finden Sie unter

- [`align`Beispiele](#vclrfalignexamples)

- [Definieren neuer Typen mit`__declspec(align(#))`](#vclrf_declspecaligntypedef)

- [Ausrichten von Daten im lokalen Threadspeicher](#vclrfthreadlocalstorageallocation)

- [Wie `align` funktioniert mit Daten Verpackung?](#vclrfhowalignworkswithdatapacking)

- [Beispiele für die Struktur Ausrichtung](../build/x64-software-conventions.md#examples-of-structure-alignment) (x64-spezifisch)

## <a name="align-examples"></a><a name="vclrfalignexamples"></a>Beispiele ausrichten

Die folgenden Beispiele zeigen, wie sich `__declspec(align(#))` auf die Größe und die Ausrichtung der Datenstrukturen auswirkt. Die Beispiele gehen von folgenden Definitionen aus:

```cpp
#define CACHE_LINE  32
#define CACHE_ALIGN __declspec(align(CACHE_LINE))
```

In diesem Beispiel wird die `S1`-Struktur mit `__declspec(align(32))` definiert. Alle Verwendungen von `S1` für eine Variablendefinition oder andere Typdeklarationen sind mit 32 Bytes ausgerichtet. `sizeof(struct S1)` gibt 32 zurück, und `S1` weist 16 Auffüll-Bytes auf, die den 16 Bytes folgen, die für die Aufnahme der vier ganzen Zahlen erforderlich sind. Jeder **`int`** Member erfordert eine 4-Byte-Ausrichtung, aber die Ausrichtung der Struktur selbst wird als 32 deklariert. Dann ist die Gesamtausrichtung 32.

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

Beachten Sie in diesem Beispiel, dass `a` die Ausrichtung des natürlichen Typs, in diesem Fall 4 Bytes, aufweist. Allerdings muss `S1` mit 32 Bytes ausgerichtet sein. 28 Bytes an Auffüll Zeichen folgen `a` , sodass `s1` bei Offset 32 beginnt. `S4`erbt dann die Ausrichtungs Anforderung von `S1` , da es sich dabei um die größte Ausrichtungs Anforderung in der Struktur handelt. `sizeof(struct S4)` gibt 64 zurück.

```cpp
struct S4 {
   int a;
   // 28 bytes padding
   struct S1 s1;      // S4 inherits cache alignment requirement of S1
};
```

Die folgenden drei Variablendeklarationen verwenden auch `__declspec(align(#))`. In jedem Fall muss die Variable mit 32 Bytes ausgerichtet sein. Im-Array ist die Basisadresse des Arrays, nicht jedes Arraymember, 32-Byte-ausgerichtet. Der **`sizeof`** Wert für jeden Arraymember ist nicht betroffen, wenn Sie verwenden `__declspec(align(#))` .

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

Wenn der Speicher für Heaps zugewiesen wird, hängt die Ausrichtung davon ab, welche Speicherbelegungsfunktion aufgerufen wird.  Wenn Sie beispielsweise `malloc` verwenden, hängt das Ergebnis von der Größe des Operanden ab. Wenn *arg* >= 8, wird der zurückgegebene Arbeitsspeicher auf 8 Byte ausgerichtet. Wenn *arg* < 8 ist, ist die Ausrichtung des zurückgegebenen Arbeitsspeichers die erste Potenz von 2 weniger als *arg*. Wenn Sie z `malloc(7)` . b. verwenden, ist die Ausrichtung 4 Bytes.

## <a name="defining-new-types-with-__declspecalign"></a><a name="vclrf_declspecaligntypedef"></a>Definieren neuer Typen mit`__declspec(align(#))`

Sie können einen Typ mit einem Ausrichtungsmerkmal definieren.

Beispielsweise können Sie eine **`struct`** mit einem Ausrichtungs Wert auf diese Weise definieren:

```cpp
struct aType {int a; int b;};
typedef __declspec(align(32)) struct aType bType;
```

Nun `aType` sind und `bType` die gleiche Größe (8 Bytes), aber Variablen vom Typ `bType` sind 32-Byte-ausgerichtet.

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

## <a name="how-align-works-with-data-packing"></a><a name="vclrfhowalignworkswithdatapacking"></a>Wie `align` funktioniert mit Daten Verpackung?

Die `/Zp` -Compileroption und das- `pack` pragma haben den Effekt, dass Daten für Struktur-und Union-Member verpackt werden. Dieses Beispiel zeigt, wie `/Zp` und `__declspec(align(#))` zusammenarbeiten:

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

In der folgenden Tabelle wird der Offset der einzelnen Member unter verschiedenen `/Zp` Werten (oder `#pragma pack` ) aufgelistet, die zeigen, wie die beiden interagieren.

|Variable|/Zp1|/Zp2|/Zp4|/Zp8|
|--------------|-----------|-----------|-----------|-----------|
|a|0|0|0|0|
|b|1|2|2|2|
|c|3|4|4|8|
|d|32|32|32|32|
|e|40|40|40|40|
|f|41|42|44|48|
|sizeof(S)|64|64|64|64|

Weitere Informationen finden Sie unter [ `/Zp` (Ausrichtung auf Strukturmember)](../build/reference/zp-struct-member-alignment.md).

Der Offset eines Objekts basiert auf dem Offset des vorherigen Objekts und der aktuellen Verpackungseinstellung, es sei denn, das Objekt weist ein `__declspec(align(#))`-Attribut auf. In diesem Fall basiert die Ausrichtung auf dem Offset des vorherigen Objekts und dem `__declspec(align(#))`-Wert für das Objekt.

**Ende Microsoft-spezifisch**

## <a name="see-also"></a>Siehe auch

[`__declspec`](../cpp/declspec.md)<br/>
[Übersicht über ARM-ABI-Konventionen](../build/overview-of-arm-abi-conventions.md)<br/>
[Softwarekonventionen bei x64-Systemen](../build/x64-software-conventions.md)

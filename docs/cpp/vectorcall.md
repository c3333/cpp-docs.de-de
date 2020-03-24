---
title: __vectorcall
ms.date: 12/17/2018
f1_keywords:
- __vectorcall_cpp
- __vectorcall
- _vectorcall
helpviewer_keywords:
- __vectorcall keyword
- __vectorcall
ms.assetid: 1c95ed59-86c6-4857-b4ed-10519193f851
ms.openlocfilehash: c933f995c57094b28e477e439c7b9ff5a13c2063
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187517"
---
# <a name="__vectorcall"></a>__vectorcall

**Microsoft-spezifisch**

Die **__vectorcall** -Aufruf Konvention gibt an, dass Argumente für Funktionen, sofern möglich, in Registern übermittelt werden sollen. **__vectorcall** verwendet mehr Register für Argumente als [__fastcall](../cpp/fastcall.md) oder die standardmäßige [x64-Aufruf Konvention](../build/x64-calling-convention.md) verwenden. Die **__vectorcall** -Aufruf Konvention wird nur in nativem Code auf x86-und x64-Prozessoren unterstützt, die Streaming SIMD Extensions 2 (SSE2) und höher enthalten. Verwenden Sie **__vectorcall** , um Funktionen zu beschleunigen, die mehrere Gleit Komma-oder SIMD-Vektor Argumente übergeben und Vorgänge ausführen, die die in Registern geladenen Argumente nutzen. In der folgenden Liste sind die Funktionen aufgeführt, die von den x86-und x64-Implementierungen von **__vectorcall**gemeinsam sind. Die Unterschiede werden später in diesem Artikel erklärt.

|Element|Implementierung|
|-------------|--------------------|
|C-Namensergänzungskonvention|Funktionsnamen werden mit zwei "at"-Zeichen (\@\@) versehen, gefolgt von der Anzahl der Bytes (in dezimal) in der Parameterliste.|
|Konvention zur Umwandlung von Groß- in Kleinbuchstaben und umgekehrt|Groß-/Kleinbuchstaben werden nicht umgewandelt.|

Die Verwendung der [/GV](../build/reference/gd-gr-gv-gz-calling-convention.md) -Compileroption bewirkt, dass jede Funktion im Modul als **__vectorcall** kompiliert wird, es sei denn, die Funktion ist eine Member-Funktion, wird mit einem in Konflikt stehenden Aufruf Konvention-Attribut deklariert, verwendet eine `vararg` Variable Argumentliste oder hat den Namen `main`.

Sie können drei Arten von Argumenten übergeben, indem Sie in **__vectorcall** Funktionen registrieren: *ganzzahlige Typwerte* , *Vektortyp* Werte und *homogene Vektor Aggregat* Werte (HVA).

Ein ganzzahliger Typ erfüllt zwei Anforderungen: er stimmt mit der systemeigenen Registergröße des Prozessors überein – z. B. 4 Bytes auf einem x86- oder 8 Bytes auf einem x64-Computer - und kann in eine Ganzzahl einer Registerlänge und wieder zurück konvertiert werden, ohne die Bitdarstellung zu ändern. Beispielsweise kann jeder Typ, der in x86 (**Long Long** on x64) zu **int** herauf gestuft werden kann – z. b. ein **char** -oder **Short**-– oder, der in **int** (**Long Long** on x64) und zurück in seinen ursprünglichen Typ umgewandelt werden kann, ein ganzzahliger Typ sein. Ganzzahlige Typen umfassen Zeiger-, Verweis-und **Struktur** -oder **Union** -Typen von 4 Bytes (8 Bytes auf x64) oder weniger. Auf x64-Plattformen werden größere **Struktur** -und **Union** -Typen als Verweis an den vom Aufrufer zugeordneten Arbeitsspeicher übergeben. auf x86-Plattformen werden Sie als Wert auf dem Stapel übermittelt.

Ein Vektortyp ist entweder ein Gleit kommatyp – beispielsweise ein **float** -oder **Double**-–-Typ oder ein SIMD-Vektortyp – z. b. **__m128** oder **__m256**.

Ein HVA-Typ ist ein zusammengesetzter Typ aus maximal vier Datenmembern, die über identische Vektortypen verfügen. Ein HVA-Typ hat dieselbe Ausrichtungsanforderung wie der Vektortyp seiner Member. Dies ist ein Beispiel für eine HVA- **Struktur** Definition, die drei identische Vektor Typen enthält und eine 32-Byte-Ausrichtung hat:

```cpp
typedef struct {
   __m256 x;
   __m256 y;
   __m256 z;
} hva3;    // 3 element HVA type on __m256
```

Deklarieren Sie Ihre Funktionen explizit mit dem **__vectorcall** -Schlüsselwort in Header Dateien, damit separat kompilierter Code ohne Fehler verknüpft werden kann. Für Funktionen muss ein prototyptypisiert werden, um **__vectorcall**zu verwenden, und es kann keine Argumentliste `vararg` variabler Länge verwendet werden.

Eine Member-Funktion kann mit dem **__vectorcall** -Spezifizierer deklariert werden. Der ausgeblendete **this** -Zeiger wird von Register als erstes ganzzahliges Typargument übermittelt

Auf Arm-Computern wird **__vectorcall** vom Compiler akzeptiert und ignoriert.

Wenn die Funktion bei nicht statischen Memberfunktionen von Klassen abweichend definiert ist, muss der Aufrufkonventionsmodifizierer nicht in der abweichenden Definition angegeben werden. Das bedeutet, dass für nicht statische Member der Klasse zum Zeitpunkt der Definition die während der Deklaration angegebene Aufrufkonvention angenommen wird. Bei dieser Klassendefinition:

```cpp
struct MyClass {
   void __vectorcall mymethod();
};
```

entspricht:

```cpp
void MyClass::mymethod() { return; }
```

entspricht:

```cpp
void __vectorcall MyClass::mymethod() { return; }
```

Der **__vectorcall** Aufruf Konvention-Modifizierer muss angegeben werden, wenn ein Zeiger auf eine **__vectorcall** -Funktion erstellt wird. Im nächsten Beispiel wird eine **typedef** für einen Zeiger auf eine **__vectorcall** Funktion erstellt, die vier **doppelte** Argumente annimmt und einen **__m256** Wert zurückgibt:

```cpp
typedef __m256 (__vectorcall * vcfnptr)(double, double, double, double);
```

Aus Gründen der Kompatibilität mit früheren Versionen ist **_vectorcall** ein Synonym für **__vectorcall** , es sei denn, die Compileroption [/Za \(Deaktivieren von Spracherweiterungen)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

## <a name="__vectorcall-convention-on-x64"></a>__vectorcall-Konvention auf x64

Die **__vectorcall** Aufruf Konvention auf x64 erweitert die standardmäßige x64-Aufruf Konvention, um zusätzliche Register zu nutzen. Sowohl Typargumente als auch Vektortypargumente werden Registern auf Grundlage der Position in der Argumentliste zugeordnet. HVA-Argumente werden nicht verwendeten Vektorregistern zugeordnet.

Wenn eines der ersten vier Argumente in der Reihenfolge von links nach rechts ein ganzzahliges Typargument ist, werden sie in dem Register übergeben, das dieser Position entspricht – RCX, RDX, R8 oder R9. Ein verborgener **this** -Zeiger wird als erstes ganzzahliges Typargument behandelt. Wenn ein HVA-Argument in einem der ersten vier Argumente nicht in den verfügbaren Registern übergeben werden kann, wird stattdessen ein Verweis auf vom Aufrufer reservierten Speicher im entsprechenden ganzzahligen Typregister übergeben. Ganzzahlige Typargumente nach der vierten Parameterposition werden auf dem Stapel übergeben sind.

Wenn eines der ersten sechs Argumente in der Reihenfolge von links nach rechts ein Vektortypargument ist, werden sie als Wert in den SSE-Vektorregistern 0 bis 5 entsprechend der Argumentposition übergeben. Gleit Komma-und **__m128** Typen werden in XMM-Registern und **__m256** Typen in ymm-Registern übermittelt. Dies weicht von der Standard-x64-Aufrufkonvention ab, da die Vektortypen als Wert statt als Verweis übergeben und zusätzliche Register verwendet werden. Der für Vector-Typargumente zugeordnete Schatten Stapelraum ist auf 8 Bytes gesetzt, und die [/homeparams](../build/reference/homeparams-copy-register-parameters-to-stack.md) -Option wird nicht angewendet. Vektortypargumente in der siebten oder in höheren Parameterpositionen werden auf dem Stapel als Verweis auf vom Aufrufer zugeordneten Speicher übergeben.

Nachdem Register für Vektor Argumente zugeordnet wurden, werden die Datenmember von HVA-Argumenten in aufsteigender Reihenfolge zu nicht verwendeten Vektor Registern XMM0 zu xmm5 (oder YMM0 bis YMM5, für **__m256** Typen) zugeordnet, solange genügend Register für das gesamte HVA verfügbar sind. Wenn nicht genügend Register verfügbar sind, wird das HVA-Argument als Verweis an Speicher übergeben, der vom Aufrufer zugeordnet wird. Das Stapelschattenleerzeichen für ein HVA-Argument wird mit nicht definiertem Inhalt auf 8 Bytes festgelegt. HVA-Argumente werden Registern in der Reihenfolge von links nach rechts in der Parameterliste zugewiesen und können sich in einer beliebigen Position befinden. HVA-Argumente in einer der vier ersten Argumentpositionen, die keinen Vektorregistern zugewiesen sind, werden als Verweis im ganzzahligen Register übergeben, das dieser Position entspricht. HVA-Argumente, die nach der vierten Parameterposition als Verweis übergeben werden, werden auf dem Stapel abgelegt.

Die Ergebnisse **__vectorcall** Funktionen werden nach Möglichkeit in Registern als Wert zurückgegeben. Ergebnisse des ganzzahligen Typs, einschließlich Strukturen oder Unions von 8 Bytes oder weniger, werden als Wert in RAX zurückgegeben. Vektortypergebnisse werden je nach Größe als Wert in XMM0 oder YMM0 zurückgegeben. In HVA-Ergebnissen wird jedes Datenelement je nach Elementgröße als Wert in den Registern XMM0:XMM3 oder YMM0:YMM3 zurückgegeben. Ergebnistypen, die nicht in die entsprechenden Register passen, werden als Verweis auf vom Aufrufer zugeordneten Speicher zurückgegeben.

Der Stapel wird vom Aufrufer in der x64-Implementierung von **__vectorcall**verwaltet. Der Aufruferprolog- und -Epilogcode ordnet den Stapel für die aufgerufene Funktion zu und löscht ihn. Argumente werden von rechts nach links auf dem Stapel abgelegt, und Schattenstapelspeicher wird für Argumente zugeordnet, die in Registern übergeben werden.

Beispiele:

```cpp
// crt_vc64.c
// Build for amd64 with: cl /arch:AVX /W3 /FAs crt_vc64.c
// This example creates an annotated assembly listing in
// crt_vc64.asm.

#include <intrin.h>
#include <xmmintrin.h>

typedef struct {
   __m128 array[2];
} hva2;    // 2 element HVA type on __m128

typedef struct {
   __m256 array[4];
} hva4;    // 4 element HVA type on __m256

// Example 1: All vectors
// Passes a in XMM0, b in XMM1, c in YMM2, d in XMM3, e in YMM4.
// Return value in XMM0.
__m128 __vectorcall
example1(__m128 a, __m128 b, __m256 c, __m128 d, __m256 e) {
   return d;
}

// Example 2: Mixed int, float and vector parameters
// Passes a in RCX, b in XMM1, c in R8, d in XMM3, e in YMM4,
// f in XMM5, g pushed on stack.
// Return value in YMM0.
__m256 __vectorcall
example2(int a, __m128 b, int c, __m128 d, __m256 e, float f, int g) {
   return e;
}

// Example 3: Mixed int and HVA parameters
// Passes a in RCX, c in R8, d in R9, and e pushed on stack.
// Passes b by element in [XMM0:XMM1];
// b's stack shadow area is 8-bytes of undefined value.
// Return value in XMM0.
__m128 __vectorcall example3(int a, hva2 b, int c, int d, int e) {
   return b.array[0];
}

// Example 4: Discontiguous HVA
// Passes a in RCX, b in XMM1, d in XMM3, and e is pushed on stack.
// Passes c by element in [YMM0,YMM2,YMM4,YMM5], discontiguous because
// vector arguments b and d were allocated first.
// Shadow area for c is an 8-byte undefined value.
// Return value in XMM0.
float __vectorcall example4(int a, float b, hva4 c, __m128 d, int e) {
   return b;
}

// Example 5: Multiple HVA arguments
// Passes a in RCX, c in R8, e pushed on stack.
// Passes b in [XMM0:XMM1], d in [YMM2:YMM5], each with
// stack shadow areas of an 8-byte undefined value.
// Return value in RAX.
int __vectorcall example5(int a, hva2 b, int c, hva4 d, int e) {
   return c + e;
}

// Example 6: HVA argument passed by reference, returned by register
// Passes a in [XMM0:XMM1], b passed by reference in RDX, c in YMM2,
// d in [XMM3:XMM4].
// Register space was insufficient for b, but not for d.
// Return value in [YMM0:YMM3].
hva4 __vectorcall example6(hva2 a, hva4 b, __m256 c, hva2 d) {
   return b;
}

int __cdecl main( void )
{
   hva4 h4;
   hva2 h2;
   int i;
   float f;
   __m128 a, b, d;
   __m256 c, e;

   a = b = d = _mm_set1_ps(3.0f);
   c = e = _mm256_set1_ps(5.0f);
   h2.array[0] = _mm_set1_ps(6.0f);
   h4.array[0] = _mm256_set1_ps(7.0f);

   b = example1(a, b, c, d, e);
   e = example2(1, b, 3, d, e, 6.0f, 7);
   d = example3(1, h2, 3, 4, 5);
   f = example4(1, 2.0f, h4, d, 5);
   i = example5(1, h2, 3, h4, 5);
   h4 = example6(h2, h4, c, h2);
}
```

## <a name="__vectorcall-convention-on-x86"></a>__vectorcall-Konvention auf x86

Die **__vectorcall** -Aufruf Konvention folgt der **__fastcall** Konvention für ganzzahlige 32-Bit-Typargumente und nutzt die SSE-Vektor Register für Vector Type und HVA-Argumente.

Die ersten beiden ganzzahligen Typargumente, die in der Parameterliste von links nach rechts gefunden werden, werden in ECX bzw. EDX eingefügt. Ein verborgener **this** -Zeiger wird als erstes ganzzahliges Typargument behandelt und in ECX übermittelt. Die ersten sechs Vektortypargumente werden je nach Argumentgröße als Wert in den SSE-Vektorregistern 0 bis 5, in den XMM- oder YMM-Registern, übergeben.

Die ersten sechs Vektortypargumente in der Reihenfolge von links nach rechts werden als Wert in den SSE-Vektorregistern 0 bis 5 übergeben. Gleit Komma-und **__m128** Typen werden in XMM-Registern und **__m256** Typen in ymm-Registern übermittelt. Für Vektortypargumente, die von Registern übergeben werden, wird kein Schattenstapelspeicher zugeordnet. Das siebte und die folgenden Vektortypargumente werden als Verweis auf vom Aufrufer zugeordneten Speicher auf dem Stapel übergeben. Die Einschränkung des Compilerfehlers [C2719](../error-messages/compiler-errors-2/compiler-error-c2719.md) gilt nicht für diese Argumente.

Nachdem Register für Vektor Argumente zugeordnet wurden, werden die Datenmember von HVA-Argumenten in aufsteigender Reihenfolge den nicht verwendeten Vektor Registern XMM0 bis xmm5 (oder YMM0 bis YMM5, für **__m256** Typen) zugeordnet, solange genügend Register für das gesamte HVA verfügbar sind. Wenn nicht genügend Register verfügbar sind, wird das HVA-Argument auf dem Stapel als Verweis an Speicher übergeben, der vom Aufrufer zugeordnet wird. Es wird kein Stapelschattenleerzeichen für ein HVA-Argument zugeordnet. HVA-Argumente werden Registern in der Reihenfolge von links nach rechts in der Parameterliste zugewiesen und können sich in einer beliebigen Position befinden.

Die Ergebnisse **__vectorcall** Funktionen werden nach Möglichkeit in Registern als Wert zurückgegeben. Ergebnisse des ganzzahligen Typs, einschließlich Strukturen oder Unions von 4 Bytes oder weniger, werden als Wert in EAX zurückgegeben. Ganzzahlige Typstrukturen oder Unions von 8 Bytes oder weniger werden als Wert in EDX:EAX zurückgegeben. Vektortypergebnisse werden je nach Größe als Wert in XMM0 oder YMM0 zurückgegeben. In HVA-Ergebnissen wird jedes Datenelement je nach Elementgröße als Wert in den Registern XMM0:XMM3 oder YMM0:YMM3 zurückgegeben. Andere Ergebnistypen werden als Hinweis auf den vom Aufrufer zugeordneten Speicher zurückgegeben.

Die x86-Implementierung von **__vectorcall** folgt der Konvention von Argumenten, die von rechts nach links vom Aufrufer auf dem Stapel abgelegt werden, und die aufgerufene Funktion löscht den Stapel direkt vor der Rückgabe. Nur Argumente, die nicht in Registern platziert werden, werden auf dem Stapel abgelegt.

Beispiele:

```cpp
// crt_vc86.c
// Build for x86 with: cl /arch:AVX /W3 /FAs crt_vc86.c
// This example creates an annotated assembly listing in
// crt_vc86.asm.

#include <intrin.h>
#include <xmmintrin.h>

typedef struct {
   __m128 array[2];
} hva2;    // 2 element HVA type on __m128

typedef struct {
   __m256 array[4];
} hva4;    // 4 element HVA type on __m256

// Example 1: All vectors
// Passes a in XMM0, b in XMM1, c in YMM2, d in XMM3, e in YMM4.
// Return value in XMM0.
__m128 __vectorcall
example1(__m128 a, __m128 b, __m256 c, __m128 d, __m256 e) {
   return d;
}

// Example 2: Mixed int, float and vector parameters
// Passes a in ECX, b in XMM0, c in EDX, d in XMM1, e in YMM2,
// f in XMM3, g pushed on stack.
// Return value in YMM0.
__m256 __vectorcall
example2(int a, __m128 b, int c, __m128 d, __m256 e, float f, int g) {
   return e;
}

// Example 3: Mixed int and HVA parameters
// Passes a in ECX, c in EDX, d and e pushed on stack.
// Passes b by element in [XMM0:XMM1].
// Return value in XMM0.
__m128 __vectorcall example3(int a, hva2 b, int c, int d, int e) {
   return b.array[0];
}

// Example 4: HVA assigned after vector types
// Passes a in ECX, b in XMM0, d in XMM1, and e in EDX.
// Passes c by element in [YMM2:YMM5].
// Return value in XMM0.
float __vectorcall example4(int a, float b, hva4 c, __m128 d, int e) {
   return b;
}

// Example 5: Multiple HVA arguments
// Passes a in ECX, c in EDX, e pushed on stack.
// Passes b in [XMM0:XMM1], d in [YMM2:YMM5].
// Return value in EAX.
int __vectorcall example5(int a, hva2 b, int c, hva4 d, int e) {
   return c + e;
}

// Example 6: HVA argument passed by reference, returned by register
// Passes a in [XMM1:XMM2], b passed by reference in ECX, c in YMM0,
// d in [XMM3:XMM4].
// Register space was insufficient for b, but not for d.
// Return value in [YMM0:YMM3].
hva4 __vectorcall example6(hva2 a, hva4 b, __m256 c, hva2 d) {
   return b;
}

int __cdecl main( void )
{
   hva4 h4;
   hva2 h2;
   int i;
   float f;
   __m128 a, b, d;
   __m256 c, e;

   a = b = d = _mm_set1_ps(3.0f);
   c = e = _mm256_set1_ps(5.0f);
   h2.array[0] = _mm_set1_ps(6.0f);
   h4.array[0] = _mm256_set1_ps(7.0f);

   b = example1(a, b, c, d, e);
   e = example2(1, b, 3, d, e, 6.0f, 7);
   d = example3(1, h2, 3, 4, 5);
   f = example4(1, 2.0f, h4, d, 5);
   i = example5(1, h2, 3, h4, 5);
   h4 = example6(h2, h4, c, h2);
}
```

**End Microsoft Specific**

## <a name="see-also"></a>Weitere Informationen

[Argumentübergabe und Benennungskonventionen](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Schlüsselwörter](../cpp/keywords-cpp.md)

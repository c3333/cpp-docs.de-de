---
title: Aufrufkonvention bei x64-Systemen
description: Dieser Artikel enthält Details zu den Standardaufrufkonventionen bei x64-Systemen.
ms.date: 07/06/2020
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: 9bfecd0fb154658a299d3dac7d9e45398ebe450b
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058632"
---
# <a name="x64-calling-convention"></a>Aufrufkonvention bei x64-Systemen

In diesem Abschnitt werden die Standardprozesse und -konventionen beschrieben, die eine Funktion (Aufrufer) für Aufrufe in eine andere Funktion (Aufgerufener) in x64-Code verwendet.

## <a name="calling-convention-defaults"></a>Standardaufrufkonventionen

Die x64-ABI (Application Binary Interface, Binärschnittstelle) verwendet standardmäßig eine Schnellaufrufkonvention mit vier Registern. Der Speicherplatz wird in der Aufrufliste als Schattenspeicher für Aufgerufene zum Speichern dieser Register zugeordnet.

Es gibt eine strikte 1:1-Entsprechung zwischen den Argumenten eines Funktionsaufrufs und den für diese Argumente verwendeten Registern. Jedes Argument, das nicht in acht Bytes passt oder einer Größe von einem, zwei, vier oder acht Bytes entspricht, muss als Verweis übergeben werden. Ein einzelnes Argument wird nie auf mehrere Register verteilt.

Der x87-Registerstapel wird nicht verwendet. Er kann vom Aufgerufenen verwendet werden, muss jedoch bei Funktionsaufrufen als flüchtig angesehen werden. Alle Gleitkommavorgänge werden mithilfe der 16 XMM-Register ausgeführt.

Ganzzahlige Argumente werden in die Register RCX, RDX, R8 und R9 übergeben. Gleitkommaargumente werden in XMM0L, XMM1L, XMM2L und XMM3L übergeben. Argumente mit einer Größe von 16 Bytes werden als Verweis übergeben. Die Parameterübergabe wird im Abschnitt [Parameterübergabe](#parameter-passing) ausführlich beschrieben. Diese Register sowie RAX, R10, R11, XMM4 und XMM5 werden als flüchtig eingestuft. Die Registerverwendung wird ausführlich im Artikel [Registerverwendung](../build/x64-software-conventions.md#register-usage) und im Abschnitt [Gespeicherte Register des Aufrufers und des Aufgerufenen](#callercallee-saved-registers) dieses Artikels beschrieben.

Bei Prototypfunktionen werden alle Argumente vor dem Übergeben in die erwarteten Typen für Aufgerufene konvertiert. Der Aufrufer ist für die Zuweisung von Speicherplatz für die Parameter des Aufgerufenen verantwortlich. Der Aufrufer muss immer ausreichend Speicherplatz für vier Registerparameter zuweisen, auch wenn der Aufgerufene nicht so viele Parameter verwendet. Diese Konvention vereinfacht die Unterstützung für C-Sprachfunktionen und Vararg-C- oder -C++-Funktionen ohne Prototyp. Für Vararg-Funktionen oder Funktionen ohne Prototyp müssen alle Gleitkommawerte im entsprechenden allgemeinen Register dupliziert werden. Alle auf die ersten vier Parameter folgenden Parameter müssen vor dem Aufruf im Stapel nach dem Schattenspeicher gespeichert werden. Details zu Vararg-Funktionen finden Sie im Abschnitt [Varargs](#varargs). Informationen zu Funktionen ohne Prototyp finden Sie unter [Funktionen ohne Prototyp](#unprototyped-functions).

## <a name="alignment"></a>Ausrichtung

Die meisten Strukturen weisen ihre natürliche Ausrichtung auf. Die primären Ausnahmen sind der Stapelzeiger und der `malloc`- oder `alloca`-Arbeitsspeicher, die auf 16 Bytes ausgerichtet sind, um die Leistung zu unterstützen. Eine Ausrichtung auf über 16 Bytes muss manuell erfolgen. Da 16 Bytes jedoch einer gängigen Ausrichtungsgröße für XMM-Vorgänge entsprechen, sollte dieser Wert für die meisten Codes funktionieren. Weitere Informationen zum Strukturlayout und zur Ausrichtung finden Sie unter [Typen und Speicher](../build/x64-software-conventions.md#types-and-storage). Weitere Informationen zum Stapellayout finden Sie unter [Verwendung von Stapeln bei x64-Systemen](../build/stack-usage.md).

## <a name="unwindability"></a>Unentladbarkeit

Leaf-Funktionen sind Funktionen, die nicht flüchtige Register nicht ändern. Eine Nicht-Leaf-Funktion ändert möglicherweise das nicht flüchtige Register RSP, indem sie beispielsweise eine Funktion aufruft. Sie könnte das Register RSP auch ändern, indem sie zusätzlichen Stapelspeicher für lokale Variablen zuweist. Zum Wiederherstellen nicht flüchtiger Register beim Verarbeiten einer Ausnahme werden Nicht-Leaf-Funktionen mit statischen Daten versehen. Die Daten beschreiben, wie die Funktion in einer beliebigen Anweisung ordnungsgemäß entladen wird. Diese Daten werden als *pdata*- oder Prozedurdaten gespeichert, die sich wiederum auf *xdata*-Daten und somit die Ausnahme beziehen, mit der Daten verarbeitet werden. Die xdata-Daten enthalten die Entladungsinformationen und können auf zusätzliche pdata-Daten oder eine Ausnahmehandlerfunktion verweisen.

Prologe und Epiloge sind stark eingeschränkt, sodass sie in xdata-Daten angemessen beschrieben werden können. Der Stapelzeiger muss (abgesehen von Leaf-Funktionen) in jedem Codebereich, der nicht Teil eines Epilogs oder Prologs ist, auf 16 Bytes ausgerichtet bleiben. Leaf-Funktionen können einfach durch Simulieren einer Rückgabe entladen werden, sodass pdata- und xdata-Daten nicht erforderlich sind. Ausführliche Informationen zur ordnungsgemäßen Struktur von Funktionsprologen und -epilogen finden Sie unter [Prolog und Epilog bei x64-Systemen](../build/prolog-and-epilog.md). Weitere Informationen zur Ausnahmebehandlung und dem Entladen von pdata- und xdata-Daten finden Sie unter [Ausnahmebehandlung bei x64-Systemen](../build/exception-handling-x64.md).

## <a name="parameter-passing"></a>Parameterübergabe

Die x64-Aufrufkonvention übergibt standardmäßig die ersten vier Argumente an eine Funktion in Registern. Die für diese Argumente verwendeten Register sind abhängig von der Position und vom Typ des Arguments. Verbleibende Argumente werden in der Reihenfolge von rechts nach links auf den Stapel verschoben.

Integerargumente an den vier ersten Positionen von links werden entsprechend von links nach rechts in RCX, RDX, R8 und R9 verschoben. Das fünfte Argument und alle nachfolgenden werden wie zuvor beschrieben an den Stapel übergeben. Alle Integerargumente werden in Registern rechtsbündig ausgerichtet, sodass der Aufgerufene die oberen Bits des Registers ignorieren und nur auf den notwendigen Teil des Registers zugreifen kann.

Alle Gleitkommaargumente und Gleitkommaargumente mit doppelter Genauigkeit in den ersten vier Parametern werden abhängig von der Position in XMM0 bis XMM3 übergeben. Gleitkommawerte werden nur in den Integerregistern RCX, RDX, R8 und R9 platziert, wenn VarArgs-Argumente vorhanden sind. Weitere Informationen finden Sie unter [Varargs](#varargs). Ebenso werden die Register XMM0 bis XMM3 ignoriert, wenn das entsprechende Argument ein Integer oder ein Zeigertyp ist.

[`__m128`](../cpp/m128.md)-Typen, -Arrays und -Zeichenfolgen werden nie als unmittelbarer Wert übergeben. Stattdessen wird ein Zeiger an den vom Aufrufer zugeordneten Arbeitsspeicher übergeben. Strukturen und Unions mit einer Größe von 8, 16, 32 oder 64 Bits sowie `__m64`-Typen werden wie Integer der gleichen Größe übergeben. Strukturen oder Unions anderer Größen werden als Zeiger auf den vom Aufrufer zugeordneten Arbeitsspeicher übergeben. Für diese als Zeiger übergebenen Aggregattypen, einschließlich `__m128`, muss der vom Aufrufer zugewiesene temporäre Speicher auf 16 Byte ausgerichtet sein.

Intrinsische Funktionen, die keinen Stapelbereich zuordnen und keine anderen Funktionen aufrufen, verwenden manchmal andere flüchtige Register, um zusätzliche Registerargumente zu übergeben. Diese Optimierung wird durch die enge Bindung zwischen dem Compiler und der Implementierung der intrinsischen Funktion ermöglicht.

Der Aufgerufene ist dafür verantwortlich, die Registerparameter bei Bedarf im Schattenspeicher zu sichern.

Die folgende Tabelle gibt Aufschluss darüber, wie Parameter übergeben werden, nach Typ und Position von links:

| Parametertyp | Fünfter und nachfolgende | Vierter | Dritter | second | Äußerster links |
|-|-|-|-|-|-|
| Gleitkomma | Stapel | XMM3 | XMM2 | XMM1 | XMM0 |
| Ganze Zahl | Stapel | R9 | R8 | RDX | RCX |
| Aggregate (8, 16, 32 oder 64 Bits) und `__m64` | Stapel | R9 | R8 | RDX | RCX |
| Andere Aggregate, als Zeiger | Stapel | R9 | R8 | RDX | RCX |
| `__m128`, als Zeiger | Stapel | R9 | R8 | RDX | RCX |

### <a name="example-of-argument-passing-1---all-integers"></a>Beispiel 1 für Argumentübergabe: Alle Integerwerte

```cpp
func1(int a, int b, int c, int d, int e, int f);
// a in RCX, b in RDX, c in R8, d in R9, f then e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>Beispiel 2 für Argumentübergabe: Alle Gleitkommawerte

```cpp
func2(float a, double b, float c, double d, float e, float f);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, f then e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Beispiel 3 für Argumentübergabe: Kombination aus Integer- und Gleitkommawerten

```cpp
func3(int a, double b, int c, float d, int e, float f);
// a in RCX, b in XMM1, c in R8, d in XMM3, f then e pushed on stack
```

### <a name="example-of-argument-passing-4---__m64-__m128-and-aggregates"></a>Beispiel 4 für Argumentübergabe: `__m64`, `__m128` und Aggregate

```cpp
func4(__m64 a, __m128 b, struct c, float d, __m128 e, __m128 f);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3,
// ptr to f pushed on stack, then ptr to e pushed on stack
```

## <a name="varargs"></a>VarArgs

Wenn Parameter über VarArgs übergeben werden (z. B. Ellipsenargumente), wird die übliche Konvention für die Übertragung von Registerparametern angewendet. Diese beinhaltet das Übertragen des fünften und der nachfolgenden Argumente an den Stapel. Es ist Aufgabe des Aufgerufenen, Argumente zu sichern, deren Adresse verwendet wird. Nur im Falle von Gleitkommawerten müssen sowohl das Integerregister als auch das Gleitkommaregister den Wert enthalten, falls der Aufgerufene den Wert in den Integerregistern erwartet.

## <a name="unprototyped-functions"></a>Funktionen ohne Prototyp

Bei Funktionen ohne Prototyp übergibt der Aufrufer ganzzahlige Werte als Integer und Gleitkommawerte als Werte mit doppelter Genauigkeit. Nur im Falle von Gleitkommawerten enthalten sowohl das Integerregister als auch das Gleitkommaregister den Gleitkommawert, falls der Aufgerufene den Wert in den Integerregistern erwartet.

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>Rückgabewerte

Ein skalarer Rückgabewert, der in 64 Bits passt, einschließlich des `__m64`-Typs, wird durch RAX zurückgegeben. Nicht skalare Typen, darunter Gleitkommazahlen, Doubles und Vektortypen, wie z. B. [`__m128`](../cpp/m128.md), [`__m128i`](../cpp/m128i.md) und [`__m128d`](../cpp/m128d.md) werden in XMM0 zurückgegeben. Der Status von nicht verwendeten Bits in dem in RAX oder XMM0 zurückgegebenen Wert ist nicht definiert.

Benutzerdefinierte Typen können als Wert von globalen Funktionen und statische Memberfunktionen zurückgegeben werden. Die Länge muss 1, 2, 4, 8, 16, 32 oder 64 Bits entsprechen, um einen benutzerdefinierten Typ als Wert in RAX zurückzugeben. Er darf außerdem keinen benutzerdefinierten Konstruktor, Destruktor oder Kopierzuweisungsoperator aufweisen. Er darf keine privaten oder geschützten nicht statischen Datenmember sowie keine nicht statischen Datenmember des Verweistyps aufweisen. Er darf keine Basisklassen oder virtuellen Funktionen aufweisen. Außerdem darf er nur Datenmember enthalten, die diese Anforderungen ebenfalls erfüllen. (Diese Definition entspricht im Grunde der eines C++03 POD-Typs. Da die Definition im Standard C++11 geändert wurde, sollte `std::is_pod` nicht für diesen Test verwendet werden.) Andernfalls muss der Aufrufer Speicher für den Rückgabewert zuweisen und einen Zeiger darauf als erstes Argument übergeben. Die verbleibenden Argumente werden dann um ein Argument nach rechts verschoben. Derselbe Zeiger muss vom Aufgerufenen in RAX zurückgegeben werden.

Diese Beispiele zeigen, wie Parameter und Rückgabewerte für Funktionen mit den angegebenen Deklarationen übergeben werden:

### <a name="example-of-return-value-1---64-bit-result"></a>Beispiel für Rückgabewert 1: Ergebnis 64 Bit

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>Beispiel für Rückgabewert 2: Ergebnis 128 Bit

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Beispiel für Rückgabewert 3: Ergebnis Benutzertyp als Zeiger

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>Beispiel für Rückgabewert 4: Ergebnis Benutzertyp als Wert

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>Gespeicherte Register des Aufrufers und des Aufgerufenen

Die x64-ABI sieht die Register RAX, RCX, RDX, R8, R9, R10, R11 und XMM0–XMM5 als flüchtig an. Falls vorhanden, sind die oberen Teile von YMM0–YMM15 und ZMM0–ZMM15 ebenfalls flüchtig. Bei AVX512VL sind die ZMM-, YMM- und XMM-Register 16–31 ebenfalls flüchtig. Sehen Sie flüchtige Register bei Funktionsaufrufen als zerstört an, es sei denn, die Sicherheit ist durch eine Analyse wie z. B. eine Optimierung des gesamten Programms gewährleistet.

Die x64-ABI sieht die Register RBX, RBP, RDI, RSI, RSP, R12, R13, R14, R15 und XMM6–XMM15 als nicht flüchtig an. Sie müssen von einer Funktion, die sie verwendet, gespeichert und wiederhergestellt werden.

## <a name="function-pointers"></a>Funktionszeiger

Funktionszeiger sind einfach nur Zeiger auf die Bezeichnung der jeweiligen Funktion. Es gibt keine Anforderung für das Inhaltsverzeichnis für Funktionszeiger.

## <a name="floating-point-support-for-older-code"></a>Gleitkommaunterstützung für älteren Code

Die MMX- und Gleitkommastapelregister (MM0 bis MM7 und ST0 bis ST7) werden auch bei Kontextwechseln beibehalten. Es gibt keine explizite Aufrufkonvention für diese Register. Die Verwendung dieser Register ist im Kernelmoduscode strengstens untersagt.

## <a name="fpcsr"></a>FPCSR

Der Registerzustand umfasst auch das x87-FPU-Steuerwort. Die Aufrufkonvention legt dieses Register als nicht flüchtig an.

Das x87-FPU-Steuerwortregister wird zu Beginn der Programmausführung mithilfe der folgenden Standardwerte festgelegt:

| Register\[bits] | Einstellung |
|-|-|
| FPCSR\[0:6] | Ausnahme maskiert alle Einsen (1) (alle Ausnahmen maskiert) |
| FPCSR\[7] | Reserviert: 0 |
| FPCSR\[8:9] | Genauigkeitssteuerung: 10B (doppelte Genauigkeit) |
| FPCSR\[10:11] | Rundungssteuerung: 0 (Runden auf nächste Zahl) |
| FPCSR\[12] | Unendlichkeitssteuerung: 0 (nicht verwendet) |

Ein Aufgerufener, der alle Felder in FpCsr ändert, muss diese vor der Rückgabe an den Aufrufer wiederherstellen. Darüber hinaus muss ein Aufrufer, der eines dieser Felder geändert hat, die Standardwerte wiederherstellen, bevor er einen Aufgerufenen aufruft, es sei denn, der Aufgerufene erwartet nach Vereinbarung die geänderten Werte.

Es gibt zwei Ausnahmen für die Regeln bezüglich der Nichtflüchtigkeit der Steuerungsflags:

- Dies ist bei Funktionen der Fall, bei denen der dokumentierte Zweck der angegebenen Funktion darin besteht, die nicht flüchtigen FPCSR-Flags zu ändern.

- Dies liegt vor, wenn dieser Verstoß gegen die Regeln tatsächlich dazu führt, dass sich ein Programm wie ein Programm verhält, das die Regeln nicht verletzt (z. B. durch eine vollständige Programmanalyse).

## <a name="mxcsr"></a>MXCSR

Der Registerstatus umfasst auch MXCSR. Die Aufrufkonvention dividiert dieses Register in einen flüchtigen und einen nicht flüchtigen Teil. Der flüchtige Teil besteht aus den sechs Statusflags in MXCSR\[0:5], während der Rest des Registers (MXCSR\[6:15]) als nicht flüchtig eingestuft wird.

Der nicht flüchtige Teil wird zu Beginn der Programmausführung auf die folgenden Standardwerte festgelegt:

| Register\[bits] | Einstellung |
|-|-|
| MXCSR\[6] | Denormalisiert alle Nullen: 0 |
| MXCSR\[7:12] | Ausnahme maskiert alle Einsen (1) (alle Ausnahmen maskiert) |
| MXCSR\[13:14] | Rundungssteuerung: 0 (Runden auf nächste Zahl) |
| MXCSR\[15] | Zurücksetzung auf Null bei Unterlauf maskierter Werte: 0 (Aus) |

Ein Aufgerufener, der alle nicht flüchtigen Felder in MxCsr ändert, muss diese vor der Rückgabe an den Aufrufer wiederherstellen. Darüber hinaus muss ein Aufrufer, der eines dieser Felder geändert hat, die Standardwerte wiederherstellen, bevor er einen Aufgerufenen aufruft, es sei denn, der Aufgerufene erwartet nach Vereinbarung die geänderten Werte.

Es gibt zwei Ausnahmen für die Regeln bezüglich der Nichtflüchtigkeit der Steuerungsflags:

- Dies ist bei Funktionen der Fall, bei denen der dokumentierte Zweck der angegebenen Funktion darin besteht, die nicht flüchtigen MXCSR-Flags zu ändern.

- Dies liegt vor, wenn dieser Verstoß gegen die Regeln tatsächlich dazu führt, dass sich ein Programm wie ein Programm verhält, das die Regeln nicht verletzt (z. B. durch eine vollständige Programmanalyse).

Machen Sie keine Annahmen über den Status des flüchtigen Teils des MXCSR-Registers über eine Funktionsgrenze hinweg, es sei denn, dies wird ausdrücklich in der Dokumentation einer Funktion beschrieben.

## <a name="setjmplongjmp"></a>setjmp/longjmp

Wenn Sie „setjmpex.h“ oder „setjmp.h“ einschließen, führen alle Aufrufe von [`setjmp`](../c-runtime-library/reference/setjmp.md) oder [`longjmp`](../c-runtime-library/reference/longjmp.md) zu einer Entladung, die Destruktoren und `__finally` aufruft.  Dieses Verhalten unterscheidet sich von x86, da das Einschließen von „setjmp.h“ hier dazu führt, dass `__finally`-Klauseln und Destruktoren nicht aufgerufen werden.

Durch einen `setjmp`-Aufruf werden der aktuelle Stapelzeiger, nicht flüchtige Register und MXCSR-Register beibehalten.  Durch einen `longjmp`-Aufruf kehren Sie zur neuesten `setjmp`-Aufrufseite zurück, und der Stapelzeiger, nicht flüchtige Register und MXCSR-Register werden wieder in den Zustand zurückgesetzt, der vom neuesten `setjmp`-Aufruf beibehalten wurde.

## <a name="see-also"></a>Siehe auch

[Softwarekonventionen bei x64-Systemen](../build/x64-software-conventions.md)

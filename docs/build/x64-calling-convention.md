---
title: Aufrufkonvention bei x64-Systemen
description: Details der standardmäßigen x64 ABI-Aufrufkonvention.
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: caf22172ea5e9c20280bce8e508d72fd30c00c5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335133"
---
# <a name="x64-calling-convention"></a>Aufrufkonvention bei x64-Systemen

In diesem Abschnitt werden die Standardprozesse und -konventionen beschrieben, die eine Funktion (der Aufrufer) verwendet, um Aufrufe in eine andere Funktion (den Angerufenen) im x64-Code zu tätigen.

## <a name="calling-convention-defaults"></a>Aufrufkonventionsstandards

Die x64 Application Binary Interface (ABI) verwendet standardmäßig eine Vier-Register-Fast-Call-Aufrufkonvention. In der Aufrufliste wird Speicherplatz als Schattenspeicher für Angerufene zum Speichern dieser Register reserviert. Es gibt eine strikte 1:1-Entsprechung zwischen den Argumenten zu einem Funktionsaufruf und den Registern, die für diese Argumente verwendet werden. Jedes Argument, das nicht in 8 Bytes passt oder nicht 1, 2, 4 oder 8 Bytes ist, muss als Verweis übergeben werden. Ein einzelnes Argument wird nie auf mehrere Register verteilt. Der x87-Registerstapel ist nicht verwendet und kann vom Angerufenen verwendet werden, muss jedoch über Funktionsaufrufe hinweg als flüchtig betrachtet werden. Alle Gleitkommaoperationen werden mit den 16 XMM-Registern durchgeführt. Ganzzahl-Argumente werden in den Registern RCX, RDX, R8 und R9 übergeben. Gleitkommaargumente werden in XMM0L, XMM1L, XMM2L und XMM3L übergeben. 16-Byte-Argumente werden als Verweis übergeben. Die Parameterübergabe wird ausführlich in [Parameter Passing](#parameter-passing)beschrieben. Zusätzlich zu diesen Registern gelten RAX, R10, R11, XMM4 und XMM5 als flüchtig. Alle anderen Register sind nicht flüchtig. Die Registernutzung wird in [Register usage](../build/x64-software-conventions.md#register-usage) und [Caller/Callee Saved Registers](#callercallee-saved-registers)detailliert dokumentiert.

Bei Prototypfunktionen werden alle Argumente vor dem Übergeben in die erwarteten Angerufenentypen konvertiert. Der Aufrufer ist für die Zuweisung von Platz für Parameter an den Angerufenen verantwortlich und muss immer genügend Platz zuweisen, um vier Registerparameter zu speichern, auch wenn der Angerufene nicht so viele Parameter verwendet. Diese Konvention vereinfacht die Unterstützung für nicht prototypisierte C-Sprachfunktionen und vararg C/C++-Funktionen. Bei vararg- oder nicht prototypierten Funktionen müssen alle Gleitkommawerte im entsprechenden Allgemeinen Register dupliziert werden. Alle Parameter, die über die ersten vier hinausgehen, müssen nach dem Schattenspeicher vor dem Aufruf auf dem Stapel gespeichert werden. Vararg Funktionsdetails finden Sie in [Varargs](#varargs). Unprototypisierte Funktionsinformationen sind in [Unprototyped Functions](#unprototyped-functions)detailliert.

## <a name="alignment"></a>Ausrichtung

Die meisten Strukturen sind an ihrer natürlichen Ausrichtung ausgerichtet. Die primären Ausnahmen sind der `malloc` Stapelzeiger und oder `alloca` Der Speicher, die an 16 Bytes ausgerichtet sind, um die Leistung zu verbessern. Die Ausrichtung über 16 Bytes muss manuell erfolgen, aber da 16 Bytes eine gemeinsame Ausrichtungsgröße für XMM-Vorgänge ist, sollte dieser Wert für den meisten Code funktionieren. Weitere Informationen zum Strukturlayout und zur Ausrichtung finden Sie unter [Typen und Speicher](../build/x64-software-conventions.md#types-and-storage). Informationen zum Stapellayout finden Sie unter [x64-Stack-Nutzung](../build/stack-usage.md).

## <a name="unwindability"></a>Entwindbarkeit

Blattfunktionen sind Funktionen, die keine nichtflüchtigen Register ändern. Eine Nicht-Blattfunktion kann nichtflüchtige RSP ändern, z. B. durch Aufrufen einer Funktion oder Zuweisung von zusätzlichem Stapelspeicher für lokale Variablen. Um nichtflüchtige Register wiederherzustellen, wenn eine Ausnahme behandelt wird, müssen Nicht-Blattfunktionen mit statischen Daten mit Anmerkungen beauft werden, die beschreiben, wie die Funktion ordnungsgemäß bei einer beliebigen Anweisung entwickelt wird. Diese Daten werden als *pdata*oder Prozedurdaten gespeichert, was wiederum auf *xdata*, die Ausnahmebehandlungsdaten, verweist. Die xdata enthält die Entladungsinformationen und kann auf zusätzliche pdata oder eine Ausnahmehandlerfunktion verweisen. Prologs und Epilogs sind stark eingeschränkt, so dass sie in xdata korrekt beschrieben werden können. Der Stapelzeiger muss in jedem Codebereich, der nicht Teil eines Epilogs oder Prologs ist, außer innerhalb von Blattfunktionen, an 16 Bytes ausgerichtet sein. Blattfunktionen können einfach durch Simulieren einer Rückgabe aufgelöst werden, sodass pdata und xdata nicht erforderlich sind. Einzelheiten zur richtigen Struktur von Funktionsprologs und Epilogs finden Sie unter [x64 prolog und epilog](../build/prolog-and-epilog.md). Weitere Informationen zur Ausnahmebehandlung sowie zur Ausnahmebehandlung und -entladung von pdata und xdata finden Sie unter [x64-Ausnahmebehandlung](../build/exception-handling-x64.md).

## <a name="parameter-passing"></a>Parameterübergabe

Die ersten vier Ganzzahlargumente werden in Registern übergeben. Ganzzahlwerte werden in der Reihenfolge von links nach rechts in RCX, RDX, R8 und R9 übergeben. Argumente fünf und höher werden auf dem Stapel übergeben. Alle Argumente sind in Registern rechtsberechtigt, so dass der Angerufene die oberen Teile des Registers ignorieren und nur auf den erforderlichen Teil des Registers zugreifen kann.

Alle Gleitkomma- und Doppelpräzisionsargumente in den ersten vier Parametern werden je nach Position in XMM0 - XMM3 übergeben. Die ganzzahligen Register RCX, RDX, R8 und R9, die normalerweise für diese Positionen verwendet würden, werden ignoriert, außer im Fall von varargs-Argumenten. Weitere Informationen finden Sie unter [Varargs](#varargs). Ebenso werden die XMM0 - XMM3-Register ignoriert, wenn das entsprechende Argument ein Ganzzahl- oder Zeigertyp ist.

[__m128](../cpp/m128.md) Typen, Arrays und Zeichenfolgen werden nie vom unmittelbaren Wert übergeben. Stattdessen wird ein Zeiger an den vom Aufrufer zugewiesenen Speicher übergeben. Strukturen und Unions der Größe 8, 16, 32 oder 64 Bits und __m64 Typen werden übergeben, als wären sie ganze Zahlen gleicher Größe. Strukturen oder Unions anderer Größen werden als Zeiger auf den vom Aufrufer zugewiesenen Speicher übergeben. Für diese Aggregattypen, die als \_Zeiger übergeben werden, einschließlich _m128, muss der vom Aufrufer zugewiesene temporäre Speicher 16-Byte ausgerichtet sein.

Intrinsische Funktionen, die keinen Stapelspeicher zuweisen und keine anderen Funktionen aufrufen, verwenden manchmal andere flüchtige Register, um zusätzliche Registerargumente zu übergeben. Diese Optimierung wird durch die enge Bindung zwischen dem Compiler und der intrinsischen Funktionsimplementierung ermöglicht.

Der Angerufene ist dafür verantwortlich, die Registerparameter bei Bedarf in ihren Schattenraum zu werfen.

Die folgende Tabelle fasst zusammen, wie Parameter übergeben werden:

|Parametertyp|Wie bestanden|
|--------------------|----------------|
|Gleitkomma|Erste 4 Parameter - XMM0 bis XMM3. Andere gaben den Stapel weiter.|
|Integer|Erste 4 Parameter - RCX, RDX, R8, R9. Andere gaben den Stapel weiter.|
|Aggregate (8, 16, 32 oder 64 Bit) und __m64|Erste 4 Parameter - RCX, RDX, R8, R9. Andere gaben den Stapel weiter.|
|Aggregate (sonstige)|Durch Zeiger. Erste 4 Parameter als Zeiger in RCX, RDX, R8 und R9 übergeben|
|__m128|Durch Zeiger. Erste 4 Parameter als Zeiger in RCX, RDX, R8 und R9 übergeben|

### <a name="example-of-argument-passing-1---all-integers"></a>Beispiel für Argument, das 1 - alle ganzen Zahlen übergibt

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>Beispiel für Argument, das 2 - alle Floats

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Beispiel für Argument, das 3 - gemischte Ints und Floats passiert

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--__m64-__m128-and-aggregates"></a>Beispiel für Argument, das \_4 -__m64, _m128 und Aggregate übergibt

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>VarArgs

Wenn Parameter über varargs übergeben werden (z. B. Auslassungsargumente), gilt die Regelkonvention für die Übergabe von Registerparametern, einschließlich des Verschüttens des fünften und des nachfolgenden Arguments in den Stapel. Es liegt in der Verantwortung des Angerufenen, Argumente zu verwerfen, deren Adresse übernommen wurde. Nur für Gleitkommawerte müssen sowohl das Ganzzahlregister als auch das Gleitkommaregister den Wert enthalten, falls der Angerufene den Wert in den Ganzzahlregistern erwartet.

## <a name="unprototyped-functions"></a>Nicht prototypisierte Funktionen

Bei Funktionen, die nicht vollständig prototypiert sind, übergibt der Aufrufer Ganzzahlwerte als Ganzzahlen und Gleitkommawerte als doppelte Genauigkeit. Nur bei Gleitkommawerten enthalten sowohl das Ganzzahlregister als auch das Gleitkommaregister den Gleitkommawert, falls der Angerufene den Wert in den Ganzzahlregistern erwartet.

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>Rückgabewerte

Ein skalarer Rückgabewert, der in 64 Bit passen kann, wird über RAX zurückgegeben. Dies umfasst __m64 Typen. Nicht skalare Typen wie Floats, Doubles und Vektortypen wie [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md) [__m128d](../cpp/m128d.md) werden in XMM0 zurückgegeben. Der Status von nicht verwendeten Bits in dem in RAX oder XMM0 zurückgegebenen Wert ist nicht definiert.

Benutzerdefinierte Typen können als Wert von globalen Funktionen und statische Memberfunktionen zurückgegeben werden. Um einen benutzerdefinierten Typ nach Wert in RAX zurückzugeben, muss er eine Länge von 1, 2, 4, 8, 16, 32 oder 64 Bit haben. Es darf auch keinen benutzerdefinierten Konstruktor-, Destruktor- oder Kopierzuweisungsoperator haben. keine privaten oder geschützten nicht statischen Datenmember; keine nicht statischen Datenmember des Referenztyps; keine Basisklassen; keine virtuellen Funktionen; und keine Datenmember, die diese Anforderungen nicht auch erfüllen. (Dies ist im Grunde die Definition eines C++03 POD-Typs. Da sich die Definition im C++11-Standard geändert `std::is_pod` hat, wird die Verwendung für diesen Test nicht empfohlen.) Andernfalls übernimmt der Aufrufer die Verantwortung für die Zuweisung von Speicher und das Übergeben eines Zeigers für den Rückgabewert als erstes Argument. Nachfolgende Argumente werden dann um ein Argument nach rechts verschoben. Derselbe Zeiger muss vom Aufgerufenen in RAX zurückgegeben werden.

Diese Beispiele zeigen, wie Parameter und Rückgabewerte für Funktionen mit den angegebenen Deklarationen übergeben werden:

### <a name="example-of-return-value-1---64-bit-result"></a>Beispiel für Rückgabewert 1 - 64-Bit-Ergebnis

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>Beispiel für Rückgabewert 2 - 128-Bit-Ergebnis

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Beispiel für Rückgabewert 3 - Benutzertypergebnis nach Zeiger

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>Beispiel für Rückgabewert 4 - Benutzertypergebnis nach Wert

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>Anrufer/Anrufer gespeicherte Register

Die Register RAX, RCX, RDX, R8, R9, R10, R11, XMM0-5 und die oberen Teile von YMM0-15 und ZMM0-15 gelten als flüchtig und müssen bei Funktionsaufrufen als zerstört betrachtet werden (sofern nicht anders durch Analysen wie die gesamte Programmoptimierung sicherheitsbedenzierbar). Bei AVX512VL sind die Register ZMM, YMM und XMM 16-31 flüchtig.

Die Register RBX, RBP, RDI, RSI, RSP, R12, R13, R14, R15 und XMM6-15 gelten als nichtflüchtig und müssen von einer Funktion, die sie verwendet, gespeichert und wiederhergestellt werden.

## <a name="function-pointers"></a>Funktionszeiger

Funktionszeiger sind einfach Zeiger auf die Beschriftung der jeweiligen Funktion. Es gibt keine Inhaltsverzeichnisanforderungen (TOC) für Funktionszeiger.

## <a name="floating-point-support-for-older-code"></a>Gleitkommaunterstützung für älteren Code

Die MMX- und Gleitkomma-Stack-Register (MM0-MM7/ST0-ST7) bleiben über Kontextwechsel hinweg erhalten. Es gibt keine ausdrückliche Aufrufkonvention für diese Register. Die Verwendung dieser Register ist im Kernelmodus-Code strengstens untersagt.

## <a name="fpcsr"></a>FpCsr

Der Registerstatus enthält auch das Steuerwort x87 FPU. Die Berufungskonvention schreibt vor, dass dieses Register nicht flüchtig ist.

Das X87 FPU-Steuerwortregister wird zu Beginn der Programmausführung auf die folgenden Standardwerte gesetzt:

| Bits\[registrieren] | Einstellung |
|-|-|
| FPCSR\[0:6] | Ausnahme masken alle 1 (alle Ausnahmen maskiert) |
| FPCSR\[7] | Reserviert - 0 |
| FPCSR\[8:9] | Präzisionssteuerung - 10B (doppelte Präzision) |
| FPCSR\[10:11] | Rundungssteuerung - 0 (rund zum nächsten) |
| FPCSR\[12] | Infinity-Steuerung - 0 (nicht verwendet) |

Ein Angerufener, der eines der Felder in FPCSR ändert, muss sie wiederherstellen, bevor er zu seinem Aufrufer zurückkehrt. Darüber hinaus muss ein Aufrufer, der eines dieser Felder geändert hat, sie auf ihre Standardwerte zurücksetzen, bevor er einen Angerufenen aufruft, es sei denn, der Aufrufer erwartet die geänderten Werte durch Vereinbarung.

Es gibt zwei Ausnahmen von den Regeln über die Nicht-Volatilität der Kontrollflags:

1. In Funktionen, bei denen der dokumentierte Zweck der angegebenen Funktion darin besteht, die nichtflüchtigen FpCsr-Flags zu ändern.

1. Wenn es nachweislich richtig ist, dass die Verletzung dieser Regeln zu einem Programm führt, das sich wie ein Programm verhält, bei dem diese Regeln nicht verletzt werden, z. B. durch eine Ganzprogrammanalyse.

## <a name="mxcsr"></a>MxCsr

Der Registerstatus enthält auch MxCsr. Die aufrufende Konvention unterteilt dieses Register in einen flüchtigen und einen nichtflüchtigen Teil. Der flüchtige Teil besteht aus den sechs\[Statusflags in MXCSR 0:5],\[während der Rest des Registers, MXCSR 6:15], als nichtflüchtig gilt.

Der nichtflüchtige Teil wird zu Beginn der Programmausführung auf die folgenden Standardwerte festgelegt:

| Bits\[registrieren] | Einstellung |
|-|-|
| MXCSR\[6] | Denormals sind Nullen - 0 |
| MXCSR\[7:12] | Ausnahme masken alle 1 (alle Ausnahmen maskiert) |
| MXCSR\[13:14] | Rundungssteuerung - 0 (rund zum nächsten) |
| MXCSR\[15] | Flush auf Null für maskierten Unterlauf - 0 (aus) |

Ein Angerufener, der eines der nichtflüchtigen Felder in MXCSR ändert, muss sie wiederherstellen, bevor er zu seinem Aufrufer zurückkehrt. Darüber hinaus muss ein Aufrufer, der eines dieser Felder geändert hat, sie auf ihre Standardwerte zurücksetzen, bevor er einen Angerufenen aufruft, es sei denn, der Aufrufer erwartet die geänderten Werte durch Vereinbarung.

Es gibt zwei Ausnahmen von den Regeln über die Nicht-Volatilität der Kontrollflags:

- In Funktionen, bei denen der dokumentierte Zweck der angegebenen Funktion darin besteht, die nichtflüchtigen MxCsr-Flags zu ändern.

- Wenn es nachweislich richtig ist, dass die Verletzung dieser Regeln zu einem Programm führt, das sich wie ein Programm verhält, bei dem diese Regeln nicht verletzt werden, z. B. durch eine Ganzprogrammanalyse.

Über den Zustand des flüchtigen Teils von MXCSR über eine Funktionsgrenze hinweg können keine Annahmen getroffen werden, es sei denn, dies wird in der Dokumentation einer Funktion ausdrücklich beschrieben.

## <a name="setjmplongjmp"></a>setjmp/longjmp

Wenn Sie setjmpex.h oder setjmp.h einschließen, führen alle Aufrufe von [setjmp](../c-runtime-library/reference/setjmp.md) oder [longjmp](../c-runtime-library/reference/longjmp.md) zu einer Entladung, die Destruktoren und `__finally` Aufrufe aufruft.  Dies unterscheidet sich von x86, wobei die `__finally` Einbeziehung von setjmp.h dazu führt, dass Klauseln und Destruktoren nicht aufgerufen werden.

Ein Aufruf `setjmp` zum Beibehalten des aktuellen Stapelzeigers, nicht flüchtiger Register und MxCsr-Register.  Ruft `longjmp` auf, um `setjmp` zur letzten Aufrufsite zurückzukehren, und setzt den Stapelzeiger, nicht flüchtige Register und MxCsr-Register `setjmp` in den Zustand zurück, der vom letzten Aufruf beibehalten wurde.

## <a name="see-also"></a>Siehe auch

[Softwarekonventionen bei x64-Systemen](../build/x64-software-conventions.md)

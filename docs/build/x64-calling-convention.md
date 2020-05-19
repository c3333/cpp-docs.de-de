---
title: Aufrufkonvention bei x64-Systemen
description: Dieser Artikel enthält Details zu den ABI-Standardaufrufkonventionen bei x64-Systemen.
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: caf22172ea5e9c20280bce8e508d72fd30c00c5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335133"
---
# <a name="x64-calling-convention"></a>Aufrufkonvention bei x64-Systemen

In diesem Abschnitt werden die Standardprozesse und -konventionen beschrieben, die eine Funktion (Aufrufer) für Aufrufe in eine andere Funktion (Aufgerufener) in x64-Code verwendet.

## <a name="calling-convention-defaults"></a>Standardaufrufkonventionen

Die x64-ABI (Application Binary Interface, Binärschnittstelle) verwendet standardmäßig eine Schnellaufrufkonvention mit vier Registern. Der Speicherplatz wird in der Aufrufliste als Schattenspeicher für Aufgerufene zum Speichern dieser Register zugeordnet. Es gibt eine strikte 1:1-Entsprechung zwischen den Argumenten eines Funktionsaufrufs und den für diese Argumente verwendeten Registern. Jedes Argument, das nicht in acht Bytes passt oder einer Größe von einem, zwei, vier oder acht Bytes entspricht, muss als Verweis übergeben werden. Ein einzelnes Argument wird nie auf mehrere Register verteilt. Der x87-Registerstapel wird nicht verwendet und kann vom Aufgerufenen verwendet werden, muss jedoch bei Funktionsaufrufen als flüchtig angesehen werden. Alle Gleitkommavorgänge werden mithilfe der 16 XMM-Register ausgeführt. Ganzzahlige Argumente werden in die Register RCX, RDX, R8 und R9 übergeben. Gleitkommaargumente werden in XMM0L, XMM1L, XMM2L und XMM3L übergeben. Argumente mit einer Größe von 16 Bytes werden als Verweis übergeben. Die Parameterübergabe wird im Abschnitt [Parameterübergabe](#parameter-passing) ausführlich beschrieben. Zusätzlich zu diesen Registern werden RAX, R10, R11, XMM4 und XMM5 als flüchtig eingestuft. Alle anderen Register sind nicht flüchtig. Die Registerverwendung wird ausführlich im Artikel [Registerverwendung](../build/x64-software-conventions.md#register-usage) und im Abschnitt [Gespeicherte Register des Aufrufers und des Aufgerufenen](#callercallee-saved-registers) dieses Artikels beschrieben.

Bei Prototypfunktionen werden alle Argumente vor dem Übergeben in die erwarteten Typen für Aufgerufene konvertiert. Der Aufrufer ist dafür verantwortlich, dem Aufgerufenen Speicherplatz für Parameter und immer ausreichend Speicherplatz für vier Registerparameter zuzuweisen, auch wenn der Aufgerufene nicht so viele Parameter verwendet. Diese Konvention vereinfacht die Unterstützung für C-Sprachfunktionen und Vararg-C- oder -C++-Funktionen ohne Prototyp. Für Vararg-Funktionen oder Funktionen ohne Prototyp müssen alle Gleitkommawerte im entsprechenden allgemeinen Register dupliziert werden. Alle Parameter außerhalb der ersten vier müssen im Stapel nach dem Schattenspeicher und vor dem Aufruf gespeichert werden. Details zu Vararg-Funktionen finden Sie im Abschnitt [Varargs](#varargs). Informationen zu Funktionen ohne Prototyp finden Sie unter [Funktionen ohne Prototyp](#unprototyped-functions).

## <a name="alignment"></a>Ausrichtung

Die meisten Strukturen weisen ihre natürliche Ausrichtung auf. Die primären Ausnahmen sind der Stapelzeiger und der `malloc`- oder `alloca`-Arbeitsspeicher, die auf 16 Bytes ausgerichtet sind, um die Leistung zu unterstützen. Eine Ausrichtung auf über 16 Bytes muss manuell erfolgen. Da 16 Bytes jedoch einer gängigen Ausrichtungsgröße für XMM-Vorgänge entsprechen, sollte dieser Wert für einen Großteil des Codes funktionieren. Weitere Informationen zum Strukturlayout und zur Ausrichtung finden Sie unter [Typen und Speicher](../build/x64-software-conventions.md#types-and-storage). Weitere Informationen zum Stapellayout finden Sie unter [Verwendung von Stapeln bei x64-Systemen](../build/stack-usage.md).

## <a name="unwindability"></a>Unentladbarkeit

Leaf-Funktionen sind Funktionen, die nicht flüchtige Register nicht ändern. Eine Non-Leaf-Funktion kann nicht flüchtige RSP-Dateien möglicherweise durch Aufrufen einer Funktion oder Zuweisen von zusätzlichem Stapelspeicher für lokale Variablen ändern. Non-Leaf-Funktionen müssen mit statischen Daten versehen sein, die beschreiben, wie die Funktion in einer beliebigen Anweisung ordnungsgemäß entladen wird, um beim Behandeln einer Ausnahme nicht flüchtige Register wiederherzustellen. Diese Daten werden als *pdata*- oder Prozedurdaten gespeichert, die sich wiederum auf *xdata*-Daten und somit die Ausnahme beziehen, mit der Daten verarbeitet werden. Die xdata-Daten enthalten die Entladungsinformationen und können auf zusätzliche pdata-Daten oder eine Ausnahmehandlerfunktion verweisen. Prologe und Epiloge sind stark eingeschränkt, sodass sie in xdata-Daten angemessen beschrieben werden können. Der Stapelzeiger muss (abgesehen von Leaf-Funktionen) in jedem Codebereich, der nicht Teil eines Epilogs oder Prologs ist, auf 16 Bytes ausgerichtet werden. Leaf-Funktionen können einfach durch Simulieren einer Rückgabe entladen werden, sodass pdata- und xdata-Daten nicht erforderlich sind. Ausführliche Informationen zur ordnungsgemäßen Struktur von Funktionsprologen und -epilogen finden Sie unter [Prolog und Epilog bei x64-Systemen](../build/prolog-and-epilog.md). Weitere Informationen zur Ausnahmebehandlung und dem Entladen von pdata- und xdata-Daten finden Sie unter [Ausnahmebehandlung bei x64-Systemen](../build/exception-handling-x64.md).

## <a name="parameter-passing"></a>Parameterübergabe

Die ersten vier ganzzahligen Argumente werden in Register übergeben. Ganzzahlige Werte werden der Reihenfolge nach von links nach rechts in RCX, RDX, R8 und R9 übergeben. Das fünfte Argument und alle darauf folgenden werden an den Stapel übergeben. Alle Argumente werden in Registern rechtsbündig ausgerichtet, sodass der Aufgerufene die oberen Bits des Registers ignorieren und nur auf den notwendigen Teil des Registers zugreifen kann.

Alle Gleitkommaargumente und Gleitkommaargumente mit doppelter Genauigkeit in den ersten vier Parametern werden abhängig von der Position in XMM0 bis XMM3 übergeben. Die ganzzahligen Register RCX, RDX, R8 und R9, die normalerweise für diese Positionen verwendet werden, werden mit der Ausnahme von Varargs-Argumenten ignoriert. Weitere Informationen finden Sie unter [Varargs](#varargs). Ebenso werden die Register XMM0 bis XMM3 ignoriert, wenn das entsprechende Argument ein Integer oder ein Zeigertyp ist.

Typen, Arrays und Zeichenfolgen vom [__m128](../cpp/m128.md)-Datentyp werden nie als unmittelbarer Wert übergeben. Stattdessen wird ein Zeiger an den vom Aufrufer zugeordneten Arbeitsspeicher übergeben. Strukturen und Unions mit einer Größe von 8, 16, 32 oder 64 Bits sowie __m64-Typen werden wie Integer der gleichen Größe übergeben. Strukturen oder Unions anderer Größen werden als Zeiger auf den vom Aufrufer zugeordneten Arbeitsspeicher übergeben. Für diese als Zeiger übergebenen Aggregattypen muss einschließlich des \__m128-Datentyps der vom Aufrufer zugewiesene temporäre Speicher auf 16 Byte ausgerichtet sein.

Intrinsische Funktionen, die keinen Stapelbereich zuordnen und keine anderen Funktionen aufrufen, verwenden manchmal andere flüchtige Register, um zusätzliche Registerargumente zu übergeben. Diese Optimierung wird durch die enge Bindung zwischen dem Compiler und der Implementierung der intrinsischen Funktion ermöglicht.

Der Aufgerufene ist dafür verantwortlich, die Registerparameter bei Bedarf im Schattenspeicher zu sichern.

Die folgende Tabelle gibt Aufschluss über die Übergabeformen von Parametern:

|Parametertyp|Übergabe|
|--------------------|----------------|
|Gleitkomma|Die ersten vier Parameter: XMM0 bis XMM3. Andere werden an den Stapel weitergegeben.|
|Ganze Zahl|Die ersten vier Parameter: RCX, RDX, R8 und R9. Andere werden an den Stapel weitergegeben.|
|Aggregate (8, 16, 32 oder 64 Bits) und __m64|Die ersten vier Parameter: RCX, RDX, R8 und R9. Andere werden an den Stapel weitergegeben.|
|(Andere) Aggregate|Nach Zeiger. Die ersten vier Parameter werden als Zeiger in RCX, RDX, R8 und R9 übergeben.|
|__m128|Nach Zeiger. Die ersten vier Parameter werden als Zeiger in RCX, RDX, R8 und R9 übergeben.|

### <a name="example-of-argument-passing-1---all-integers"></a>Beispiel 1 für Argumentübergabe: Alle Integerwerte

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>Beispiel 2 für Argumentübergabe: Alle Gleitkommawerte

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Beispiel 3 für Argumentübergabe: Kombination aus Integer- und Gleitkommawerten

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--__m64-__m128-and-aggregates"></a>Beispiel 4 für Argumentübergabe: __m64, \___m128 und Aggregate

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>VarArgs

Wenn Parameter über Varargs übergeben werden (z. B. Ellipsenargumente), wird die normale Übergabekonvention für Registrierungsparameter angewendet, einschließlich der Übertragung des fünften und der nachfolgenden Argumente an den Stapel. Es ist Aufgabe des Aufgerufenen, Argumente zu sichern, deren Adresse verwendet wird. Nur im Falle von Gleitkommawerten müssen sowohl das Integerregister als auch das Gleitkommaregister den Wert enthalten, falls der Aufgerufene den Wert in den Integerregistern erwartet.

## <a name="unprototyped-functions"></a>Funktionen ohne Prototyp

Bei Funktionen ohne Prototyp übergibt der Aufrufer ganzzahlige Werte als Integer und Gleitkommawerte als Werte mit doppelter Genauigkeit. Nur im Falle von Gleitkommawerten enthalten sowohl das Integerregister als auch das Gleitkommaregister den Gleitkommawert, falls der Aufgerufene den Wert in den Integerregistern erwartet.

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>Rückgabewerte

Ein skalarer Rückgabewert, der in 64 Bits passt, wird durch RAX zurückgegeben. Dazu gehören auch __m64-Typen. Nicht skalare Typen einschließlich Gleitkommazahlen, Werte mit doppelter Genauigkeit und Vektortypen (z. B. [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md) und [__m128d](../cpp/m128d.md)) werden in XMM0 zurückgegeben. Der Status von nicht verwendeten Bits in dem in RAX oder XMM0 zurückgegebenen Wert ist nicht definiert.

Benutzerdefinierte Typen können als Wert von globalen Funktionen und statische Memberfunktionen zurückgegeben werden. Die Länge muss 1, 2, 4, 8, 16, 32 oder 64 Bits entsprechen, um einen benutzerdefinierten Typ als Wert in RAX zurückzugeben. Außerdem darf kein benutzerdefinierter Konstruktor, Destruktor oder Kopierzuweisungsoperator enthalten sein. Ebenfalls verboten sind private bzw. geschützte, nicht statische Datenmember, nicht statische Datenmember von Verweistypen, Basisklassen, virtuelle Funktionen und Datenmember, die diese Anforderungen nicht erfüllen. (Dies ist im Grunde die Definition eines C++03 POD-Typs. Da die Definition im Standard C++11 geändert wurde, sollte `std::is_pod` nicht für diesen Test verwendet werden.) Andernfalls übernimmt der Aufrufer die Verantwortung für die Speicherbelegung und die Übergabe eines Zeigers für den Rückgabewert als erstes Argument. Nachfolgende Argumente werden dann um ein Argument nach rechts verschoben. Derselbe Zeiger muss vom Aufgerufenen in RAX zurückgegeben werden.

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

Die Register RAX, RCX, RDX, R8, R9, R10, R11, XMM0-5 und die oberen Teile von YMM0-15 und ZMM0-15 gelten als flüchtig und müssen bei Funktionsaufrufen als zerstört angesehen werden (es sei denn, die Sicherheit ist durch eine Analyse wie z. B. eine Optimierung des gesamten Programms gewährleistet). Bei AVX512VL, ZMM, YMM und XMM sind die Register 16 bis 31 flüchtig.

Die Register RBX, RBP, RDI, RSI, RSP, R12, R13, R14, R15 und XMM6-15 gelten als nicht flüchtig und müssen von einer Funktion gespeichert und wieder hergestellt werden, die sie verwendet.

## <a name="function-pointers"></a>Funktionszeiger

Funktionszeiger sind einfach nur Zeiger auf die Bezeichnung der jeweiligen Funktion. Es gibt keine Anforderungen für das Inhaltsverzeichnis für Funktionszeiger.

## <a name="floating-point-support-for-older-code"></a>Gleitkommaunterstützung für älteren Code

Die MMX- und Gleitkommastapelregister (MM0 bis MM7 und ST0 bis ST7) werden auch bei Kontextwechseln beibehalten. Es gibt keine explizite Aufrufkonvention für diese Register. Die Verwendung dieser Register ist im Kernelmoduscode strengstens untersagt.

## <a name="fpcsr"></a>FpCsr

Der Registerzustand umfasst auch das x87-FPU-Steuerwort. Die Aufrufkonvention legt dieses Register als nicht flüchtig an.

Das x87-FPU-Steuerwortregister wird zu Beginn der Programmausführung auf die folgenden Standardwerte festgelegt:

| Register\[bits] | Einstellung |
|-|-|
| FPCSR\[0:6] | Ausnahme maskiert alle Einsen (1) (alle Ausnahmen maskiert) |
| FPCSR\[7] | Reserviert: 0 |
| FPCSR\[8:9] | Genauigkeitssteuerung: 10B (doppelte Genauigkeit) |
| FPCSR\[10:11] | Rundungssteuerung: 0 (Runden auf nächste Zahl) |
| FPCSR\[12] | Unendlichkeitssteuerung: 0 (nicht verwendet) |

Ein Aufgerufener, der alle Felder in FpCsr ändert, muss diese vor der Rückgabe an den Aufrufer wiederherstellen. Darüber hinaus muss ein Aufrufer, der eines dieser Felder geändert hat, die Standardwerte wiederherstellen, bevor er einen Aufgerufenen aufruft, es sei denn, der Aufrufer erwartet die geänderten Werte.

Es gibt zwei Ausnahmen für die Regeln bezüglich der Nichtflüchtigkeit der Steuerungsflags:

1. Dies ist bei Funktionen der Fall, bei denen der dokumentierte Zweck der angegebenen Funktion darin besteht, die nicht flüchtigen FpCsr-Flags zu ändern.

1. Dies liegt vor, wenn dieser Verstoß gegen die Regeln tatsächlich dazu führt, dass sich ein Programm wie ein Programm verhält, bei dem die Regeln nicht verletzt werden (z. B. durch eine vollständige Programmanalyse).

## <a name="mxcsr"></a>MxCsr

Der Registrierungsstatus umfasst auch MxCsr. Die Aufrufkonvention dividiert dieses Register in einen flüchtigen und einen nicht flüchtigen Teil. Der flüchtige Teil besteht aus den sechs Statusflags in MXCSR\[0:5], während der Rest des Registers (MXCSR\[6:15]) als nicht flüchtig eingestuft wird.

Der nicht flüchtige Teil wird zu Beginn der Programmausführung auf die folgenden Standardwerte festgelegt:

| Register\[bits] | Einstellung |
|-|-|
| MXCSR\[6] | Denormalisiert alle Nullen: 0 |
| MXCSR\[7:12] | Ausnahme maskiert alle Einsen (1) (alle Ausnahmen maskiert) |
| MXCSR\[13:14] | Rundungssteuerung: 0 (Runden auf nächste Zahl) |
| MXCSR\[15] | Zurücksetzung auf Null bei Unterlauf maskierter Werte: 0 (Aus) |

Ein Aufgerufener, der alle nicht flüchtigen Felder in MxCsr ändert, muss diese vor der Rückgabe an den Aufrufer wiederherstellen. Darüber hinaus muss ein Aufrufer, der eines dieser Felder geändert hat, die Standardwerte wiederherstellen, bevor er einen Aufgerufenen aufruft, es sei denn, der Aufrufer erwartet die geänderten Werte.

Es gibt zwei Ausnahmen für die Regeln bezüglich der Nichtflüchtigkeit der Steuerungsflags:

- Dies ist bei Funktionen der Fall, bei denen der dokumentierte Zweck der angegebenen Funktion darin besteht, die nicht flüchtigen MxCsr-Flags zu ändern.

- Dies liegt vor, wenn dieser Verstoß gegen die Regeln tatsächlich dazu führt, dass sich ein Programm wie ein Programm verhält, bei dem die Regeln nicht verletzt werden (z. B. durch eine vollständige Programmanalyse).

Es können keine Annahmen über den Status des flüchtigen Teils von MxCsr über eine Funktionsgrenze hinweg vorgenommen werden, es sei denn, dies wird ausdrücklich in der Dokumentation einer Funktion beschrieben.

## <a name="setjmplongjmp"></a>setjmp/longjmp

Wenn Sie „setjmpex.h“ oder „setjmp.h“ einschließen, führen alle Aufrufe von [setjmp](../c-runtime-library/reference/setjmp.md) oder [longjmp](../c-runtime-library/reference/longjmp.md) zu einer Entladung, die Destruktoren und `__finally` aufruft.  Dies unterscheidet sich von x86, da das Einschließen von „setjmp.h“ hier dazu führt, dass `__finally`-Klauseln und Destruktoren nicht aufgerufen werden.

Durch einen `setjmp`-Aufruf werden der aktuelle Stapelzeiger, nicht flüchtige Register und MxCsr-Register beibehalten.  Durch einen `longjmp`-Aufruf kehren Sie zur neuesten `setjmp`-Aufrufseite zurück, und der Stapelzeiger, nicht flüchtige Register und MxCsr-Register werden wieder in den Zustand zurückgesetzt, der vom neuesten `setjmp`-Aufruf beibehalten wurde.

## <a name="see-also"></a>Siehe auch

[Softwarekonventionen bei x64-Systemen](../build/x64-software-conventions.md)

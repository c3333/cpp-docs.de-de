---
title: Aufrufkonvention bei x64-Systemen
description: Details der standardmäßigen x64 ABI-Aufruf Konvention.
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: 2cad00ac7f2cb5fe086fa262a0f512330997391f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856884"
---
# <a name="x64-calling-convention"></a>Aufrufkonvention bei x64-Systemen

In diesem Abschnitt werden die Standardprozesse und Konventionen beschrieben, die von einer Funktion (dem Aufrufer) verwendet werden, um Aufrufe an eine andere Funktion (den aufgerufenen) in x64-Code vorzunehmen.

## <a name="calling-convention-defaults"></a>Standardwerte für Aufruf Konvention

Die x64-Anwendungs Binärdatei Schnittstelle (ABI) verwendet standardmäßig eine fast-Call-Aufruf Konvention mit vier Register. Der Speicherplatz wird in der aufrufsstapel als Schatten Speicher für aufgerufenen zugeordnet, um diese Register zu speichern. Es gibt eine strikte 1:1-Entsprechung zwischen den Argumenten eines Funktions Aufrufes und den Registern, die für diese Argumente verwendet werden. Jedes Argument, das nicht in 8 Bytes passt oder keine 1, 2, 4 oder 8 Bytes ist, muss als Verweis übermittelt werden. Ein einzelnes Argument wird nie auf mehrere Register verteilt. Der x87-Register Stapel wird nicht verwendet und kann vom aufgerufenen verwendet werden, er muss jedoch über Funktionsaufrufe hinweg als flüchtig angesehen werden. Alle Gleit Komma Operationen werden mithilfe der 16 XMM-Register ausgeführt. Ganzzahlige Argumente werden in den Registern RCX, RDX, R8 und R9 übermittelt. Gleit Komma Argumente werden in XMM0L, XMM1L, XMM2L und XMM3L übermittelt. 16-Byte-Argumente werden als Verweis übermittelt. Die Übergabe von Parametern wird in der [Parameter Übergabe](#parameter-passing)ausführlich beschrieben. Zusätzlich zu diesen Registern werden Rax, R10, R11, XMM4 und XMM5 als flüchtig eingestuft. Alle anderen Register sind nicht flüchtig. Die Register Verwendung ist im Detail unter [Register Usage](../build/x64-software-conventions.md#register-usage) und Aufrufer/Aufgerufener [gespeicherter Register](#callercallee-saved-registers)dokumentiert.

Für prototyptypisierte Funktionen werden alle Argumente vor dem übergeben in die erwarteten aufgerufenen Typen konvertiert. Der Aufrufer ist dafür verantwortlich, dem aufgerufenen Platz für Parameter zuzuweisen, und muss immer ausreichend Speicherplatz zum Speichern von vier Register Parametern zuweisen, auch wenn der aufgerufene nicht viele Parameter annimmt. Diese Konvention vereinfacht die Unterstützung für nicht prototyptypisierte c-Sprachfunktionen undC++ vararg c/Functions. Für vararg-oder unprototypisierte Funktionen müssen alle Gleit Komma Werte im entsprechenden allgemeinen Register dupliziert werden. Alle Parameter außerhalb der ersten vier müssen nach dem Schatten Speicher vor dem-Befehl auf dem Stapel gespeichert werden. Die Details der vararg-Funktion finden Sie in [varargs](#varargs). Nicht prototyptypisierte Funktions Informationen werden in [Funktionen mit unprototyptypisierung](#unprototyped-functions)ausführlich erläutert.

## <a name="alignment"></a>Ausrichtung

Die meisten Strukturen sind an ihrer natürlichen Ausrichtung ausgerichtet. Die primären Ausnahmen sind der Stapelzeiger und `malloc` oder `alloca` Arbeitsspeicher, die auf 16 Bytes ausgerichtet sind, um die Leistung zu unterstützen. Die Ausrichtung oberhalb von 16 Bytes muss manuell erfolgen, aber da 16 Bytes eine gemeinsame Ausrichtungs Größe für XMM-Vorgänge ist, sollte dieser Wert für den meisten Code funktionieren. Weitere Informationen zum Struktur Layout und zur Ausrichtung finden Sie unter [Typen und Speicher](../build/x64-software-conventions.md#types-and-storage). Weitere Informationen zum Stapel Layout finden Sie unter [x64-Stapel Verwendung](../build/stack-usage.md).

## <a name="unwindability"></a>Nicht windability

Blatt Funktionen sind Funktionen, die keine nicht flüchtigen Register ändern. Eine nicht Blatt Funktion kann eine nicht flüchtige RSP ändern, z. b. durch Aufrufen einer Funktion oder Zuweisen von zusätzlichem Stapel Speicher für lokale Variablen. Zum Wiederherstellen nicht flüchtiger Register, wenn eine Ausnahme behandelt wird, müssen nicht Blatt Funktionen mit statischen Daten versehen werden, die beschreiben, wie die Funktion in einer beliebigen Anweisung ordnungsgemäß entladen wird. Diese Daten werden als *pData*-oder-Prozedur Daten gespeichert, die wiederum auf *XData*verweisen, die Ausnahme Behandlungsdaten. Die XData-Daten enthalten die Entwicklungsinformationen und können auf zusätzliche pData oder eine ausnahmehandlerfunktion verweisen. Prologs und Epilogs sind stark eingeschränkt, sodass Sie in XData ordnungsgemäß beschrieben werden können. Der Stapelzeiger muss in jedem Code Bereich, der nicht Teil eines Epilogcode oder Prologs ist, auf 16 Bytes ausgerichtet werden, außer in Blatt Funktionen. Blatt Funktionen können einfach durch Simulieren einer Rückgabe entzittert werden, daher sind pData und XData nicht erforderlich. Ausführliche Informationen zur ordnungsgemäßen Struktur von Funktions-Prologe und Epilogs finden Sie unter [x64 Prolog und Epilogcode](../build/prolog-and-epilog.md). Weitere Informationen zur Ausnahmebehandlung und zum behandeln und entwickeln von pData-und XData-Ausnahmen finden Sie unter [x64-Ausnahmebehandlung](../build/exception-handling-x64.md).

## <a name="parameter-passing"></a>Parameterübergabe

Die ersten vier ganzzahligen Argumente werden in Registern übermittelt. Ganzzahlige Werte werden in RCX, RDX, R8 und R9 in der Reihenfolge von links nach rechts übermittelt. Die Argumente fünf und höher werden im Stapel übermittelt. Alle Argumente werden in Registern rechtsbündig ausgerichtet, sodass der aufgerufene die oberen Bits des Registers ignorieren und nur auf den Teil des notwendigen Registers zugreifen kann.

Alle Gleit Komma-und doppelten Genauigkeits Argumente in den ersten vier Parametern werden in XMM0-XMM3, abhängig von der Position, weitergegeben. Die ganze Zahl registriert RCX, RDX, R8 und R9, die normalerweise für diese Positionen verwendet werden, außer im Fall von varargs-Argumenten. Weitere Informationen finden Sie unter [varargs](#varargs). Ebenso werden die XMM0-XMM3-Register ignoriert, wenn das entsprechende Argument eine Ganzzahl oder ein Zeigertyp ist.

[__m128](../cpp/m128.md) Typen, Arrays und Zeichen folgen werden nie von einem unmittelbaren Wert übermittelt. Stattdessen wird ein Zeiger an den vom Aufrufer zugeordneten Arbeitsspeicher übergeben. Strukturen und Unions der Größe 8, 16, 32 oder 64 Bits und __m64 Typen werden so wie bei ganzen Zahlen der gleichen Größe an Sie übermittelt. Strukturen oder Unions anderer Größen werden als Zeiger auf den vom Aufrufer zugeordneten Arbeitsspeicher übergeben. Für diese Aggregat Typen, die als Zeiger übergeben werden, einschließlich \__m128, muss der vom Aufrufer zugewiesene temporäre Speicher 16 Byte ausgerichtet sein.

Intrinsische Funktionen, die keinen Stapelbereich zuordnen und keine anderen Funktionen aufzurufen, verwenden manchmal andere flüchtige Register, um zusätzliche Register Argumente zu übergeben. Diese Optimierung wird durch die enge Bindung zwischen dem Compiler und der Implementierung der intrinsischen Funktion ermöglicht.

Der aufgerufene ist dafür verantwortlich, die Register Parameter bei Bedarf in ihren Schattenbereich zu sichern.

In der folgenden Tabelle wird zusammengefasst, wie Parameter übermittelt werden:

|Parametertyp|Bestandene Vorgehensweise|
|--------------------|----------------|
|Gleitkomma|Die ersten vier Parameter: XMM0 bis XMM3. Andere wurden auf dem Stapel weitergegeben.|
|Integer|Die ersten vier Parameter: RCX, RDX, R8, R9. Andere wurden auf dem Stapel weitergegeben.|
|Aggregate (8, 16, 32 oder 64 Bits) und __m64|Die ersten vier Parameter: RCX, RDX, R8, R9. Andere wurden auf dem Stapel weitergegeben.|
|Aggregate (sonstige)|Nach Zeiger. Die ersten vier Parameter, die als Zeiger in RCX, RDX, R8 und R9 als Zeiger gegeben wurden.|
|__m128|Nach Zeiger. Die ersten vier Parameter, die als Zeiger in RCX, RDX, R8 und R9 als Zeiger gegeben wurden.|

### <a name="example-of-argument-passing-1---all-integers"></a>Beispiel für Argument Übergabe 1-alle ganzen Zahlen

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>Beispiel für Argument Übergabe 2-alle Gleit Komma Zahlen

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Beispiel für übergebene Argument 3-gemischte int-und Gleit Komma Zahlen

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--__m64-__m128-and-aggregates"></a>Beispiel für das Übergeben des Arguments 4-__m64, \__m128 und Aggregaten

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>VarArgs

Wenn Parameter über varargs übergeben werden (z. b. Ellipsen Argumente), wird die normale Registrierungs Konvention für den Registrierungs Parameter angewendet, einschließlich der Übertragung der fünften und nachfolgenden Argumente auf den Stapel. Es ist Aufgabe des aufgerufenen, Argumente zu sichern, deren Adresse angenommen wird. Nur für Gleit Komma Werte müssen sowohl das ganzzahlige Register als auch das Gleit Komma Register den Wert enthalten, falls der aufgerufene den Wert in den ganzzahligen Registern erwartet.

## <a name="unprototyped-functions"></a>Nicht prototyptypisierte Funktionen

Für Funktionen, die nicht vollständig prototyptypisiert sind, übergibt der Aufrufer ganzzahlige Werte als ganze Zahlen und Gleit Komma Werte als doppelte Genauigkeit. Nur für Gleit Komma Werte enthalten sowohl das ganzzahlige Register als auch das Gleit Komma Register den float-Wert für den Fall, dass der aufgerufene den Wert in den ganzzahligen Registern erwartet.

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>Rückgabewerte

Ein skalarer Rückgabewert, der in 64 Bits passen kann, wird durch RAX zurückgegeben. Dies schließt __m64 Typen ein. Nicht skalare Typen, wie z. b. Gleit Komma Zahlen, Doubles und Vektor Typen wie [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md) [__m128d](../cpp/m128d.md) , werden in XMM0 zurückgegeben. Der Status von nicht verwendeten Bits in dem in RAX oder XMM0 zurückgegebenen Wert ist nicht definiert.

Benutzerdefinierte Typen können als Wert von globalen Funktionen und statische Memberfunktionen zurückgegeben werden. Wenn ein benutzerdefinierter Typ als Wert in RAX zurückgegeben werden soll, muss er eine Länge von 1, 2, 4, 8, 16, 32 oder 64 Bits aufweisen. Es muss auch keinen benutzerdefinierten Konstruktor, Dekonstruktor oder Kopier Zuweisungs Operator aufweisen. keine privaten oder geschützten nicht statischen Datenmember. keine nicht statischen Datenmember des Verweis Typs. keine Basisklassen; keine virtuellen Funktionen; und keine Datenmember, die diese Anforderungen nicht erfüllen. (Dies ist im Grunde die Definition eines C++03 POD-Typs. Da sich die Definition im Standard c++ 11 geändert hat, wird empfohlen, `std::is_pod` für diesen Test nicht zu verwenden.) Andernfalls übernimmt der Aufrufer die Verantwortung für das belegen von Speicher und das Übergeben eines Zeigers für den Rückgabewert als erstes Argument. Nachfolgende Argumente werden dann um ein Argument nach rechts verschoben. Derselbe Zeiger muss vom Aufgerufenen in RAX zurückgegeben werden.

Diese Beispiele zeigen, wie Parameter und Rückgabewerte für Funktionen mit den angegebenen Deklarationen übergeben werden:

### <a name="example-of-return-value-1---64-bit-result"></a>Beispiel für Rückgabewert 1-64-Bit-Ergebnis

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>Beispiel für Rückgabewert 2-128-Bit-Ergebnis

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Beispiel für Rückgabewert 3-Benutzertyp Ergebnis durch Zeiger

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>Beispiel für Rückgabewert 4-Benutzertyp Ergebnis nach Wert

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>Gespeicherte Register des Aufrufers/aufgerufenen

Die Register Rax, RCX, RDX, R8, R9, R10, R11, XMM0-5 und die oberen Teile von YMM0-15 und ZMM0-15 gelten als flüchtig und müssen bei Funktionsaufrufen als zerstört angesehen werden (es sei denn, die Sicherheit ist durch Analyse wie z. b. die Optimierung des gesamten Programms gewährleistet). Auf AVX512VL sind die ZMM-, ymm-und XMM-Register 16-31 flüchtig.

Die Register RBX, RBP, RDI, RSI, RSP, R12, R13, R14, R15 und XMM6-15 gelten als nicht flüchtig und müssen von einer Funktion gespeichert und wieder hergestellt werden, die Sie verwendet.

## <a name="function-pointers"></a>Funktionszeiger
 
Funktionszeiger sind einfach Zeiger auf die Bezeichnung der jeweiligen Funktion. Es gibt keine Inhaltsverzeichnis Anforderungen (TOC) für Funktionszeiger.

## <a name="floating-point-support-for-older-code"></a>Gleit Komma Unterstützung für älteren Code

Die MMX-und Gleit Komma Stapel Register (MM0-MM7/st0-ST7) werden über Kontextwechsel hinweg beibehalten. Es gibt keine explizite Aufruf Konvention für diese Register. Die Verwendung dieser Register ist im Kernelmoduscode streng unzulässig.

## <a name="fpcsr"></a>FpCsr

Der Registrierungsstatus enthält auch das x87-Steuerelement Wort. Die Aufruf Konvention legt diese Register als nicht flüchtig an.

Das x87 FPU-Steuerelement Wort Register wird zu Beginn der Programmausführung auf die folgenden Standardwerte festgelegt:

| \[Bits Registrieren] | Einstellung |
|-|-|
| FpCsr\[0:6] | Ausnahme Maske alle 1 (alle Ausnahmen maskiert) |
| FpCsr\[7] | Reserviert-0 |
| FpCsr\[8:9] | Genauigkeits Steuerung-10B (doppelte Genauigkeit) |
| FpCsr\[10:11] | Rundungs Steuerung-0 (Runden auf nächstgelegene) |
| FpCsr\[12] | Unendlich-Steuerelement-0 (nicht verwendet) |

Ein aufgerufener, der alle Felder in FPCSR ändert, muss diese vor der Rückgabe an den Aufrufer wiederherstellen. Darüber hinaus muss ein Aufrufer, der eines dieser Felder geändert hat, die Standardwerte wiederherstellen, bevor er einen aufgerufenen aufruft, es sei denn, der Aufrufer erwartet die geänderten Werte.

Es gibt zwei Ausnahmen zu den Regeln bezüglich der nicht-Volatilität der Steuerungsflags:

1. In Funktionen, bei denen der dokumentierte Zweck der angegebenen Funktion darin besteht, die nicht flüchtigen FpCsr-Flags zu ändern.

1. Wenn dies der Fall ist, ist der Verstoß gegen diese Regeln ein Programm, das sich wie ein Programm verhält, bei dem diese Regeln nicht verletzt werden, z. b. durch die gesamte Programmanalyse.

## <a name="mxcsr"></a>MxCsr

Der Registrierungsstatus umfasst auch MXCSR. Die Aufruf Konvention dividiert dieses Register in einen flüchtigen Teil und einen nicht flüchtigen Teil. Der flüchtige Teil besteht aus den sechs Statusflags in MXCSR\[0:5], während der Rest von Register, MXCSR\[6:15] als nicht flüchtig eingestuft wird.

Der nicht flüchtige Teil wird zu Beginn der Programmausführung auf die folgenden Standardwerte festgelegt:

| \[Bits Registrieren] | Einstellung |
|-|-|
| MXCSR\[6] | Denormals sind Nullen-0 |
| MXCSR\[7:12] | Ausnahme Maske alle 1 (alle Ausnahmen maskiert) |
| MXCSR\[13:14] | Rundungs Steuerung-0 (Runden auf nächstgelegene) |
| MXCSR\[15] | Bei maskiertem Unterlauf zu NULL leeren-0 (aus) |

Ein aufgerufener, der alle nicht flüchtigen Felder in MXCSR ändert, muss diese vor der Rückgabe an den Aufrufer wiederherstellen. Darüber hinaus muss ein Aufrufer, der eines dieser Felder geändert hat, die Standardwerte wiederherstellen, bevor er einen aufgerufenen aufruft, es sei denn, der Aufrufer erwartet die geänderten Werte.

Es gibt zwei Ausnahmen zu den Regeln bezüglich der nicht-Volatilität der Steuerungsflags:

- In Funktionen, bei denen der dokumentierte Zweck der angegebenen Funktion darin besteht, die nicht flüchtigen MxCsr-Flags zu ändern.

- Wenn dies der Fall ist, ist der Verstoß gegen diese Regeln ein Programm, das sich wie ein Programm verhält, bei dem diese Regeln nicht verletzt werden, z. b. durch die gesamte Programmanalyse.

Es können keine Annahmen über den Status des flüchtigen Teils von MXCSR über eine Funktions Grenze hinweg vorgenommen werden, es sei denn, dies wird ausdrücklich in der-Dokumentation einer-Funktion beschrieben.

## <a name="setjmplongjmp"></a>setjmp/longjmp

Wenn Sie "setjmpex. h" oder "setjmp. h" einschließen, führen alle Aufrufe von " [setjmp](../c-runtime-library/reference/setjmp.md) " oder " [longjmp](../c-runtime-library/reference/longjmp.md) " zu einer Entladung, die debugtoren und `__finally` Aufrufe aufruft.  Dies unterscheidet sich von x86, wobei das Einschließen von setjmp. h dazu führt, dass `__finally` Klauseln und debugktoren nicht aufgerufen werden.

Ein-`setjmp`, der den aktuellen Stapelzeiger, nicht flüchtige Register und MXCSR-Register beibehält.  Aufrufe von `longjmp` zur aktuellen `setjmp` Aufruf Site zurückkehren und den Stapelzeiger, nicht flüchtige Register und MXCSR-Register wieder in den Zustand zurücksetzen, der durch den letzten `setjmp` Aufruf beibehalten wird.

## <a name="see-also"></a>Weitere Informationen

[Softwarekonventionen bei x64-Systemen](../build/x64-software-conventions.md)

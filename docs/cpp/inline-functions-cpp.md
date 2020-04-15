---
title: Inlinefunktionen [C++]
ms.date: 10/09/2018
f1_keywords:
- __forceinline_cpp
- __inline_cpp
- inline_cpp
- __inline
- _inline
- __forceinline
- _forceinline
helpviewer_keywords:
- inline functions [C++], class members
ms.assetid: 355f120c-2847-4608-ac04-8dda18ffe10c
ms.openlocfilehash: 703c04873a733d068da025b595909ecc681ff147
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374090"
---
# <a name="inline-functions-c"></a>Inlinefunktionen [C++]

Eine Funktion, die im Text einer Klassendeklaration definiert ist, ist eine Inlinefunktion.

## <a name="example"></a>Beispiel

In der folgenden Klassendeklaration ist der `Account`-Konstruktor eine Inlinefunktion. Die `GetBalance`Memberfunktionen `Deposit`, `Withdraw` und werden nicht als **Inline** angegeben, können aber als Inlinefunktionen implementiert werden.

```cpp
// Inline_Member_Functions.cpp
class Account
{
public:
    Account(double initial_balance) { balance = initial_balance; }
    double GetBalance();
    double Deposit( double Amount );
    double Withdraw( double Amount );
private:
    double balance;
};

inline double Account::GetBalance()
{
    return balance;
}

inline double Account::Deposit( double Amount )
{
    return ( balance += Amount );
}

inline double Account::Withdraw( double Amount )
{
    return ( balance -= Amount );
}
int main()
{
}
```

> [!NOTE]
> In der Klassendeklaration wurden die Funktionen ohne das **Inline-Schlüsselwort** deklariert. Das **Inline-Schlüsselwort** kann in der Klassendeklaration angegeben werden. das Ergebnis ist das gleiche.

Eine angegebene Inlinememberfunktion muss in jeder Kompilierungseinheit auf die gleiche Weise deklariert werden. Diese Einschränkung bewirkt, dass sich Inlinefunktionen wie instanziierte Funktionen verhalten. Außerdem muss es genau eine Definition einer Inlinefunktion geben.

Eine Klassenmemberfunktion ist standardmäßig eine externe Verknüpfung, es **inline** sei denn, eine Definition für diese Funktion enthält den Inlinebezeichner. Das obige Beispiel zeigt, dass diese Funktionen nicht explizit mit dem **Inlinebezeichner** deklariert werden müssen. Die Verwendung von **Inline** in der Funktionsdefinition bewirkt, dass es sich um eine Inline-Funktion handelt. Es ist jedoch illegal, eine Funktion nach einem Aufruf dieser Funktion als **Inline-Funktion** zu deklarieren.

## <a name="inline-__inline-and-__forceinline"></a>Inline, __inline \_und _forceinline

Die **Inline-** und __inline-Bezeichner weisen den Compiler an, eine Kopie des Funktionstexts an jedem Ort einzufügen, an dem die Funktion aufgerufen wird. **__inline**

Die Einfügung (bezeichnet als Inlineerweiterung oder Inlinekonstrukt) wird nur ausgeführt, wenn die Kosten-Nutzen-Analyse des Compilers dies als sinnvoll bewertet. Eine Inlineerweiterung verringert den Funktionsaufruf-Mehraufwand, möglicherweise auf Kosten der größeren Codegröße.

Das **Schlüsselwort __forceinline** überschreibt die Kosten-Nutzen-Analyse und stützt sich stattdessen auf das Urteil des Programmierers. Seien Sie vorsichtig, wenn Sie **__forceinline verwenden.** Die unterschiedslose Verwendung von **__forceinline** kann zu größerem Code mit nur marginalen Leistungssteigerungen oder in einigen Fällen sogar leistungsverlusten führen (z. B. aufgrund eines erhöhten Pagings einer größeren ausführbaren Datei).

Die Verwendung von Inlinefunktionen kann das Programm schneller machen, da so der Mehraufwand vermieden wird, der Funktionsaufrufen zugeordnet ist. Inline erweiterte Funktionen unterliegen Codeoptimierungen, die für normale Funktionen nicht verfügbar sind.

Der Compiler behandelt die Inlineerweiterungsoptionen und -Schlüsselwörter als Vorschläge. Es gibt keine Garantie, dass Funktionen inline gestellt werden. Sie können den Compiler nicht zwingen, eine bestimmte Funktion inzuline, auch nicht mit dem **Schlüsselwort __forceinline.** Beim Kompilieren mit **/clr**führt der Compiler keine Funktion ein, wenn Sicherheitsattribute auf die Funktion angewendet werden.

Das **Inline-Schlüsselwort** ist nur in C++ verfügbar. Die **__inline-** und **__forceinline** Schlüsselwörter sind sowohl in C als auch in C++ verfügbar. Aus Kompatibilität mit früheren Versionen sind **_inline** und **_forceinline** Synonyme für **__inline**und **__forceinline,** es sei denn, die Compileroption [/Za \(Deaktivieren von Spracherweiterungen)](../build/reference/za-ze-disable-language-extensions.md) wird angegeben.

Das **Inline-Schlüsselwort** teilt dem Compiler mit, dass die Inlineerweiterung bevorzugt wird. Jedoch kann der Compiler eine separate Instanz der Funktion erstellen (instanziieren) und Standardaufrufbindungen erstellen, anstatt den Code inline einzufügen. Zwei Fälle, in denen dies auftreten kann, sind:

- Rekursive Funktionen.

- Funktionen, auf die durch einen Zeiger an anderer Stelle in der Übersetzungseinheit verwiesen wird.

Diese Gründe können, *wie andere,* nach Ermessen des Compilers die Inlining beeinträchtigen; Sie sollten nicht vom **Inlinebezeichner** abhängig sein, um eine Funktion inline zu machen.

Wie bei normalen Funktionen so ist auch bei den Argumenten einer Inlinefunktion die Reihenfolge der Auswertung nicht festgelegt. Tatsächlich kann sie sich von der Reihenfolge unterscheiden, in der die Argumente ausgewertet werden, wenn sie mithilfe des normalen Funktionsaufrufprotokolls übergeben werden.

Mit der Optimierungsoption [/Ob-Compiler](../build/reference/ob-inline-function-expansion.md) können Sie ermitteln, ob die Inline-Funktionserweiterung tatsächlich stattfindet.

[/LTCG](../build/reference/ltcg-link-time-code-generation.md) führt modulübergreifendes Inlining durch, unabhängig davon, ob es im Quellcode angefordert wurde.

### <a name="example-1"></a>Beispiel 1

```cpp
// inline_keyword1.cpp
// compile with: /c
inline int max( int a , int b ) {
   if( a > b )
      return a;
   return b;
}
```

Die Memberfunktionen einer Klasse können entweder mithilfe **inline** des Inline-Schlüsselworts oder durch Platzieren der Funktionsdefinition innerhalb der Klassendefinition inline deklariert werden.

### <a name="example-2"></a>Beispiel 2

```cpp
// inline_keyword2.cpp
// compile with: /EHsc /c
#include <iostream>
using namespace std;

class MyClass {
public:
   void print() { cout << i << ' '; }   // Implicitly inline
private:
   int i;
};
```

**Microsoft Specific**

Das **Schlüsselwort __inline** entspricht **inline**.

Selbst bei **__forceinline**kann der Compiler nicht unter allen Umständen Code inline. Der Compiler kann keine Funktion inline setzen, wenn Folgendes der Fall ist:

- Die Funktion oder ihr Aufrufer werden mit /Ob0 kompiliert (die Standardoption für Debugbuilds).

- Die Funktion und der Aufrufer verwenden unterschiedliche Typen der Ausnahmebehandlung (C++-Ausnahmebehandlung zum einen, strukturierte Ausnahmebehandlung zum anderen).

- Die Funktion weist eine variable Argumentliste auf.

- Die Funktion verwendet eine Inlineassembly, es sei denn, sie wird mit /Og, /Ox, /O1, oder /O2 kompiliert.

- Die Funktion ist rekursiv und wird nicht von **#pragma inline_recursion(on)** begleitet. Mit dem Pragma werden rekursive Funktionen mit einer Standardtiefe von 16 Aufrufen inline gesetzt. Um die Inlining-Tiefe zu reduzieren, verwenden Sie [inline_depth](../preprocessor/inline-depth.md) Pragma.

- Die Funktion ist virtuell und wird virtuell aufgerufen. Direkte Aufrufe virtueller Funktionen können inline gesetzt werden.

- Das Programm akzeptiert die Adresse der Funktion, und der Aufruf erfolgt über den Zeiger auf die Funktion. Direkte Aufrufe von Funktionen, deren Adresse akzeptiert wurden, können inline gesetzt werden.

- Die Funktion ist auch mit dem [nackten](../cpp/naked-cpp.md) [__declspec](../cpp/declspec.md) Modifikator gekennzeichnet.

Wenn der Compiler eine mit **__forceinline**deklarierte Funktion nicht inlinen kann, generiert er eine Warnung der Ebene 1, außer wenn:

- Die Funktion wird mit /Od oder /Ob0 kompiliert. In diesen Fällen ist keine Inlining zu erwarten.

- Die Funktion ist extern definiert, in einer eingeschlossenen Bibliothek oder einer anderen Übersetzungseinheit oder ist ein virtuelles Aufrufziel oder indirektes Aufrufziel. Der Compiler kann nicht inlineierten Code identifizieren, den er in der aktuellen Übersetzungseinheit nicht finden kann.

Rekursive Funktionen können inline bis zu einer [inline_depth](../preprocessor/inline-depth.md) vom inline_depth-Pragma angegebenen Tiefe bis zu maximal 16 Aufrufen ersetzt werden. Nach dieser Tiefe werden rekursive Funktionsaufrufe als Aufrufe einer Instanz der Funktion behandelt.  Die Tiefe, bis zu der rekursive Funktionen durch die Inlineheuristik geprüft werden, kann 16 nicht überschreiten. Das [inline_recursion](../preprocessor/inline-recursion.md) Pragma steuert die Inline-Erweiterung einer Funktion, die derzeit erweitert wird. Informationen finden Sie in der Compileroption [Inline-Function Expansion](../build/reference/ob-inline-function-expansion.md) (/Ob).

**END Microsoft Spezifisch**

Weitere Informationen zur **inline** Verwendung des Inline-Bezeichners finden Sie unter:

- [Inline-Klassenmemberfunktionen](../cpp/inline-functions-cpp.md)

- [Definieren von Inline-C++-Funktionen mit dllexport und dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

## <a name="when-to-use-inline-functions"></a>Verwendungsmöglichkeiten von Inlinefunktionen

Inlinefunktionen werden am besten für kleine Funktionen verwendet, z. B. Zugriff auf private Datenmember. Ein- oder zweispurige „Zugriffsmethoden“-Funktionen geben in erster Linie Zustandsinformationen über Objekte ab. Kurze Funktionen werden von der Restkapazität des Funktionsaufrufs beeinflusst. Längere Funktionen benötigen proportional weniger Zeit in der Aufruf-/Rückgabesequenz und profitieren weniger vom Inlining.

Eine `Point` Klasse kann wie folgt definiert werden:

```cpp
// when_to_use_inline_functions.cpp
class Point
{
public:
    // Define "accessor" functions as
    //  reference types.
    unsigned& x();
    unsigned& y();
private:
    unsigned _x;
    unsigned _y;
};

inline unsigned& Point::x()
{
    return _x;
}
inline unsigned& Point::y()
{
    return _y;
}
int main()
{
}
```

Angenommen, die Koordinatenmanipulation ist ein relativ häufiger Vorgang in einem Client`x` `y` einer solchen Klasse, wobei die beiden Accessorfunktionen (und im vorherigen Beispiel) angegeben werden, da **inline** in der Regel den Overhead für:

- Funktionsaufrufen (einschließlich der Parameterübergabe und -ablage der Adresse des Objekts auf dem Stapel)

- Beibehaltung des Stapelrahmens des Aufrufers

- Neuem Stapelrahmensetup

- Rückgabewertkommunikation

- Wiederherstellung des alten Stapelrahmens

- Rückgabewert

## <a name="inline-functions-vs-macros"></a>Inlinefunktionen im Vergleich zu Makros

Obwohl Inlinefunktionen Makros ähneln (da der Funktionscode zum Zeitpunkt des Aufrufs zur Kompilierzeit erweitert wird), werden Inlinefunktionen vom Compiler analysiert, während Makros vom Präprozessor erweitert werden. Folglich gibt es einige wichtige Unterschiede:

- Inlinefunktionen folgen allen Protokollen des Typs mit erzwungener Sicherheit auf normalen Funktionen.

- Inlinefunktionen werden mit der gleichen Syntax wie jede andere Funktion angegeben, mit der Ausnahme, dass sie das **Inline-Schlüsselwort** in die Funktionsdeklaration aufnehmen.

- Die Ausdrücke, die als Argumente an Inlinefunktionen übergeben werden, werden einmal ausgewertet. In einigen Fällen können die Ausdrücke, die als Argumente an Makros übergeben werden, mehrmals ausgewertet werden.

Das folgende Beispiel zeigt ein Makro, das Kleinbuchstaben in Großbuchstaben konvertiert:

```cpp
// inline_functions_macro.c
#include <stdio.h>
#include <conio.h>

#define toupper(a) ((a) >= 'a' && ((a) <= 'z') ? ((a)-('a'-'A')):(a))

int main() {
   char ch;
   printf_s("Enter a character: ");
   ch = toupper( getc(stdin) );
   printf_s( "%c", ch );
}
//  Sample Input:  xyz
// Sample Output:  Z
```

Der Ausdruck `toupper(getc(stdin))` hat die Absicht, ein Zeichen vom`stdin`Konsolengerät ( ) zu lesen und ggf. in Großbuchstaben zu konvertieren.

Aufgrund der Implementierung des Makros wird `getc` einmal ausgeführt, um zu bestimmen, ob das Zeichen größer oder gleich "a" ist, und einmal, um zu bestimmen, ob es ist kleiner oder gleich "z" ist. Wenn es sich in diesem Bereich befindet, wird `getc` erneut ausgeführt, um das Zeichen in einen Großbuchstaben zu konvertieren. Dies bedeutet, dass das Programm auf zwei oder drei Zeichen wartet, obwohl es idealerweise nur auf eines warten sollte.

Inlinefunktionen beheben das zuvor beschriebene Problem:

```cpp
// inline_functions_inline.cpp
#include <stdio.h>
#include <conio.h>

inline char toupper( char a ) {
   return ((a >= 'a' && a <= 'z') ? a-('a'-'A') : a );
}

int main() {
   printf_s("Enter a character: ");
   char ch = toupper( getc(stdin) );
   printf_s( "%c", ch );
}
```

```Output
Sample Input: a
Sample Output: A
```

## <a name="see-also"></a>Siehe auch

[noinline](../cpp/noinline.md)<br/>
[auto_inline](../preprocessor/auto-inline.md)

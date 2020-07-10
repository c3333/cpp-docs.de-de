---
title: Inlinefunktionen [C++]
description: Das C++-Inline Schlüsselwort kann verwendet werden, um dem Compiler Inline Funktionen vorzuschlagen.
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
ms.openlocfilehash: 454a727f0c002dc476e5fdab217efc3dea716e14
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180708"
---
# <a name="inline-functions-c"></a>Inlinefunktionen [C++]

Eine Funktion, die im Text einer Klassendeklaration definiert ist, ist eine Inlinefunktion.

## <a name="example"></a>Beispiel

In der folgenden Klassendeklaration ist der `Account`-Konstruktor eine Inlinefunktion. Die Member-Funktionen, `GetBalance` `Deposit` und `Withdraw` werden nicht als angegeben, **`inline`** sondern können als Inline Funktionen implementiert werden.

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
> In der Klassen Deklaration wurden die Funktionen ohne das- **`inline`** Schlüsselwort deklariert. Das- **`inline`** Schlüsselwort kann in der Klassen Deklaration angegeben werden. das Ergebnis ist identisch.

Eine angegebene Inlinememberfunktion muss in jeder Kompilierungseinheit auf die gleiche Weise deklariert werden. Diese Einschränkung bewirkt, dass sich Inlinefunktionen wie instanziierte Funktionen verhalten. Außerdem muss es genau eine Definition einer Inlinefunktion geben.

Eine Klassenmember-Funktion verwendet standardmäßig die externe Verknüpfung, es sei denn, eine Definition für diese Funktion enthält den **`inline`** Spezifizierer Das vorherige Beispiel zeigt, dass Sie diese Funktionen nicht explizit mit dem- **`inline`** Spezifizierer deklarieren müssen. **`inline`** Die Verwendung von in der Funktionsdefinition bewirkt, dass es sich um eine Inline Funktion handelt. Es ist jedoch nicht zulässig, eine Funktion als **`inline`** nach einem Aufrufe dieser Funktion erneut zu deklarieren.

## <a name="inline-__inline-and-__forceinline"></a>`inline`, `__inline` und `__forceinline`

Die **`inline`** **`__inline`** Bearbeiter und weisen den Compiler an, eine Kopie des Funktions Texts an jeder Stelle einzufügen, an der die Funktion aufgerufen wird.

Die Einfügung, die als *Inline Erweiterung* oder *Inlining*bezeichnet wird, tritt nur auf, wenn die kostengünstige Analyse des Compilers anzeigt, dass Sie sich lohnt. Die Inline Erweiterung minimiert den Funktions aufrufaufwand, um die potenziellen Kosten größerer Codegröße zu erhöhen.

Das **`__forceinline`** Schlüsselwort überschreibt die Kostenvorteils Analyse und basiert stattdessen auf der Einschätzung des Programmierers. Seien Sie vorsichtig, wenn Sie verwenden **`__forceinline`** . Die willkürliche Verwendung von **`__forceinline`** kann zu größerem Code mit nur marginalen Leistungssteigerungen oder in einigen Fällen sogar zu Leistungseinbußen führen (z. b. aufgrund der zunehmenden Auslagerung einer größeren ausführbaren Datei).

Die Verwendung von Inlinefunktionen kann das Programm schneller machen, da so der Mehraufwand vermieden wird, der Funktionsaufrufen zugeordnet ist. Inline erweiterte Funktionen unterliegen Codeoptimierungen, die für normale Funktionen nicht verfügbar sind.

Der Compiler behandelt die Inlineerweiterungsoptionen und -Schlüsselwörter als Vorschläge. Es gibt keine Garantie, dass Funktionen Inline geschaltet werden. Sie können den Compiler nicht zwingen, eine bestimmte Funktion Inline aufzusetzen, auch nicht mit dem- **`__forceinline`** Schlüsselwort. Beim Kompilieren mit führt **`/clr`** der Compiler eine Funktion nicht Inline aus, wenn auf die Funktion Sicherheits Attribute angewendet werden.

Das **`inline`** Schlüsselwort ist nur in C++ verfügbar. Die **`__inline`** **`__forceinline`** Schlüsselwörter und sind sowohl in C als auch in C++ verfügbar. Aus Gründen der Kompatibilität mit früheren **`_inline`** Versionen **`_forceinline`** sind und Synonyme für **`__inline`** , und **`__forceinline`** es sei denn, die Compileroption [ `/Za` \( Spracherweiterungen deaktivieren)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

Das- **`inline`** Schlüsselwort teilt dem Compiler mit, dass die Inline Erweiterung bevorzugt wird. Jedoch kann der Compiler eine separate Instanz der Funktion erstellen (instanziieren) und Standardaufrufbindungen erstellen, anstatt den Code inline einzufügen. Es gibt zwei Fälle, in denen dieses Verhalten auftreten kann:

- Rekursive Funktionen.

- Funktionen, auf die durch einen Zeiger an anderer Stelle in der Übersetzungseinheit verwiesen wird.

Diese Gründe können das Inlining beeinträchtigen, *wie es auch andere*nach dem Ermessen des Compilers ist. Sie sollten nicht von dem **`inline`** Spezifizierer abhängig sein, damit eine Funktion Inline ist.

Wie bei normalen Funktionen gibt es keine definierte Reihenfolge für die Argument Auswertung in einer Inline Funktion. Tatsächlich kann Sie sich von der Argument Auswertungs Reihenfolge unterscheiden, wenn Sie mit dem normalen Funktions aufrufsprotokoll übermittelt wird.

Die [`/Ob`](../build/reference/ob-inline-function-expansion.md) compileroptimierungs-Option hilft bei der Bestimmung, ob die Inline Funktionserweiterung tatsächlich auftritt.

[`/LTCG`](../build/reference/ltcg-link-time-code-generation.md)führt Modul übergreifende Inlining aus, unabhängig davon, ob es im Quellcode angefordert wird oder nicht.

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

Die Member-Funktionen einer Klasse können Inline deklariert werden, entweder mithilfe des- **`inline`** Schlüssel Worts oder durch Platzieren der Funktionsdefinition innerhalb der Klassendefinition.

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

**Microsoft-spezifisch**

Das- **`__inline`** Schlüsselwort entspricht **`inline`** .

Auch mit **`__forceinline`** kann der Compiler nicht in allen Fällen Inline Code Inline codieren. Der Compiler kann eine Funktion nicht Inline Inline ausführen, wenn:

- Die-Funktion oder ihr Aufrufer wird mit kompiliert **`/Ob0`** (die Standardoption für Debugbuilds).

- Die Funktion und der Aufrufer verwenden unterschiedliche Typen der Ausnahmebehandlung (C++-Ausnahmebehandlung zum einen, strukturierte Ausnahmebehandlung zum anderen).

- Die Funktion weist eine variable Argumentliste auf.

- Die Funktion verwendet eine Inlineassembly, es sei denn **`/Ox`** , Sie wird mit, **`/O1`** oder kompiliert **`/O2`** .

- Die Funktion ist rekursiv und hat nicht **`#pragma inline_recursion(on)`** festgelegt. Mit dem Pragma werden rekursive Funktionen mit einer Standardtiefe von 16 Aufrufen inline gesetzt. Verwenden Sie pragma, um die Inlining-Tiefe zu verringern [`inline_depth`](../preprocessor/inline-depth.md) .

- Die Funktion ist virtuell und wird virtuell aufgerufen. Direkte Aufrufe virtueller Funktionen können inline gesetzt werden.

- Das Programm akzeptiert die Adresse der Funktion, und der Aufruf erfolgt über den Zeiger auf die Funktion. Direkte Aufrufe von Funktionen, deren Adresse akzeptiert wurden, können inline gesetzt werden.

- Die-Funktion wird auch mit dem- [`naked`](../cpp/naked-cpp.md) [`__declspec`](../cpp/declspec.md) Modifizierer markiert.

Wenn der Compiler eine mit deklarierte Funktion nicht Inline ausführen kann **`__forceinline`** , generiert er eine Warnung der Stufe 1, ausgenommen:

- Die Funktion wird mit/od oder/Ob0. kompiliert. In diesen Fällen wird kein Inlining erwartet.

- Die-Funktion wird extern, in einer enthaltenen Bibliothek oder einer anderen Übersetzungseinheit definiert, oder ist ein virtuelles oder indirektes aufrufsziel. Der Compiler kann keinen nicht Inline Code identifizieren, der in der aktuellen Übersetzungseinheit nicht gefunden werden kann.

Rekursive Funktionen können durch Inline Code zu einer durch das Pragma angegebenen Tiefe ersetzt werden [`inline_depth`](../preprocessor/inline-depth.md) , bis zu einem Maximum von 16 aufrufen. Nach dieser Tiefe werden rekursive Funktionsaufrufe als Aufrufe einer Instanz der Funktion behandelt.  Die Tiefe, in der rekursive Funktionen von der Inline-Heuristik überprüft werden, kann 16 nicht überschreiten. Das- [`inline_recursion`](../preprocessor/inline-recursion.md) pragma steuert die Inline Erweiterung einer Funktion, die zurzeit in der Erweiterung ist. Weitere Informationen finden Sie unter der/ob [-Compileroption (Inline Funktionserweiterung](../build/reference/ob-inline-function-expansion.md) ).

**Ende Microsoft-spezifisch**

Weitere Informationen zur Verwendung des **Inline** Spezifizierers finden Sie unter:

- [Inline-Klassenmemberfunktionen](../cpp/inline-functions-cpp.md)

- [Definieren von C++-Inline Funktionen mit dllexport und DllImport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

## <a name="when-to-use-inline-functions"></a>Verwendungsmöglichkeiten von Inlinefunktionen

Inlinefunktionen werden am besten für kleine Funktionen verwendet, z. B. Zugriff auf private Datenmember. Der Hauptzweck dieser ein-oder zweizeiligen "Accessor"-Funktionen besteht darin, Zustandsinformationen zu Objekten zurückzugeben. Kurze Funktionen sind sensibel für den Aufwand von Funktionsaufrufen. Längere Funktionen verbringen proportional weniger Zeit in der aufrufenden und der Rückgabe Sequenz und profitieren weniger von Inlining.

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

Vorausgesetzt, die Koordinaten Manipulation ist ein relativ allgemeiner Vorgang in einem Client einer solchen Klasse, indem die beiden Accessorfunktionen ( `x` und `y` im vorangehenden Beispiel) angegeben werden, was in der **`inline`** Regel den mehr Aufwand für Folgendes spart:

- Funktionsaufrufen (einschließlich der Parameterübergabe und -ablage der Adresse des Objekts auf dem Stapel)

- Beibehaltung des Stapelrahmens des Aufrufers

- Neue Stapel Rahmen Einrichtung

- Rückgabewertkommunikation

- Wiederherstellen des alten Stapel Rahmens

- Rückgabewert

## <a name="inline-functions-vs-macros"></a>Inline Funktionen im Vergleich zu Makros

Inline Funktionen sind Makros ähnlich, da der Funktionscode zum Zeitpunkt des Aufrufes zur Kompilierzeit erweitert wird. Inline Funktionen werden jedoch vom Compiler analysiert, und Makros werden durch den Präprozessor erweitert. Folglich gibt es einige wichtige Unterschiede:

- Inlinefunktionen folgen allen Protokollen des Typs mit erzwungener Sicherheit auf normalen Funktionen.

- Inline Funktionen werden mit der gleichen Syntax wie jede andere Funktion angegeben, mit dem Unterschied, dass Sie das- **`inline`** Schlüsselwort in die Funktionsdeklaration einschließen.

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

Die Absicht des Ausdrucks `toupper(getc(stdin))` besteht darin, dass ein Zeichen aus dem Konsolen Gerät () gelesen `stdin` und ggf. in Großbuchstaben konvertiert werden soll.

Aufgrund der Implementierung des-Makros `getc` wird einmal ausgeführt, um zu bestimmen, ob das Zeichen größer oder gleich "a" ist, und einmal, um zu bestimmen, ob es kleiner oder gleich "z" ist. Wenn es sich in diesem Bereich befindet, wird `getc` erneut ausgeführt, um das Zeichen in einen Großbuchstaben zu konvertieren. Dies bedeutet, dass das Programm auf zwei oder drei Zeichen wartet, wenn im Idealfall nur auf eins gewartet werden soll.

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

## <a name="see-also"></a>Weitere Informationen

[`noinline`](../cpp/noinline.md)<br/>
[`auto_inline`](../preprocessor/auto-inline.md)

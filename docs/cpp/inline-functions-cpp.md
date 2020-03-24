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
ms.openlocfilehash: b13007211857d84e4f3b33c80ed6b5beaf6f0bcf
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178236"
---
# <a name="inline-functions-c"></a>Inlinefunktionen [C++]

Eine Funktion, die im Text einer Klassendeklaration definiert ist, ist eine Inlinefunktion.

## <a name="example"></a>Beispiel

In der folgenden Klassendeklaration ist der `Account`-Konstruktor eine Inlinefunktion. Die Member-Funktionen `GetBalance`, `Deposit`und `Withdraw` sind nicht als **Inline** angegeben, können aber als Inline Funktionen implementiert werden.

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
>  In der Klassen Deklaration wurden die Funktionen ohne das **Inline** Schlüsselwort deklariert. Das **Inline** Schlüsselwort kann in der Klassen Deklaration angegeben werden. Das Ergebnis ist identisch.

Eine angegebene Inlinememberfunktion muss in jeder Kompilierungseinheit auf die gleiche Weise deklariert werden. Diese Einschränkung bewirkt, dass sich Inlinefunktionen wie instanziierte Funktionen verhalten. Außerdem muss es genau eine Definition einer Inlinefunktion geben.

Eine Klassenmember-Funktion verwendet standardmäßig die externe Verknüpfung, es sei denn, eine Definition für diese Funktion enthält den **Inline** Bezeichner. Das vorangehende Beispiel zeigt, dass diese Funktionen nicht explizit mit dem **Inline** -Spezifizierer deklariert werden müssen. die Verwendung von **Inline** in der Funktionsdefinition bewirkt, dass es sich um eine Inline Funktion handelt. Es ist jedoch nicht zulässig, eine Funktion nach einem Rückruf dieser Funktion als **Inline** neu zu deklarieren.

## <a name="inline-__inline-and-__forceinline"></a>Inline-, __inline-und \__forceinline

Die **Inline** -und **__inline** Spezifizierer weisen den Compiler an, eine Kopie des Funktions Texts an jeder Stelle einzufügen, an der die Funktion aufgerufen wird.

Die Einfügung (bezeichnet als Inlineerweiterung oder Inlinekonstrukt) wird nur ausgeführt, wenn die Kosten-Nutzen-Analyse des Compilers dies als sinnvoll bewertet. Eine Inlineerweiterung verringert den Funktionsaufruf-Mehraufwand, möglicherweise auf Kosten der größeren Codegröße.

Das Schlüsselwort " **__forceinline** " überschreibt die Kosten-/Nutzungsanalyse und basiert stattdessen auf der Einschätzung des Programmierers. Seien Sie vorsichtig, wenn Sie **__forceinline**verwenden. Die willkürliche Verwendung von **__forceinline** kann zu größerem Code führen, bei dem nur marginale Leistungssteigerungen erzielt werden, oder in einigen Fällen sogar Leistungseinbußen (z. b. aufgrund erhöhter Auslagerung einer größeren ausführbaren Datei).

Die Verwendung von Inlinefunktionen kann das Programm schneller machen, da so der Mehraufwand vermieden wird, der Funktionsaufrufen zugeordnet ist. Inline erweiterte Funktionen unterliegen Codeoptimierungen, die für normale Funktionen nicht verfügbar sind.

Der Compiler behandelt die Inlineerweiterungsoptionen und -Schlüsselwörter als Vorschläge. Es gibt keine Garantie, dass Funktionen inline gestellt werden. Sie können den Compiler nicht zwingen, eine bestimmte Funktion Inline Inline zu erzwingen, selbst mit dem **__forceinline** -Schlüsselwort. Beim Kompilieren mit **/CLR**führt der Compiler eine Funktion nicht Inline aus, wenn auf die Funktion Sicherheits Attribute angewendet werden.

Das **Inline** -Schlüsselwort ist nur C++in verfügbar. Die Schlüsselwörter **__inline** und **__forceinline** sind sowohl in C als C++auch in verfügbar. Aus Gründen der Kompatibilität mit früheren Versionen sind **_inline** und **_forceinline** Synonyme für **__inline**und **__forceinline** , es sei denn, die Compileroption [/Za \(Spracherweiterungen deaktivieren)](../build/reference/za-ze-disable-language-extensions.md) ist angegeben.

Das **Inline** Schlüsselwort weist den Compiler an, dass die Inline Erweiterung bevorzugt wird. Jedoch kann der Compiler eine separate Instanz der Funktion erstellen (instanziieren) und Standardaufrufbindungen erstellen, anstatt den Code inline einzufügen. Zwei Fälle, in denen dies auftreten kann, sind:

- Rekursive Funktionen.

- Funktionen, auf die durch einen Zeiger an anderer Stelle in der Übersetzungseinheit verwiesen wird.

Diese Gründe können das Inlining beeinträchtigen, *wie es auch andere*nach dem Ermessen des Compilers ist. Sie sollten nicht vom **Inline** -Spezifizierer abhängen, damit eine Funktion Inline ist.

Wie bei normalen Funktionen so ist auch bei den Argumenten einer Inlinefunktion die Reihenfolge der Auswertung nicht festgelegt. Tatsächlich kann sie sich von der Reihenfolge unterscheiden, in der die Argumente ausgewertet werden, wenn sie mithilfe des normalen Funktionsaufrufprotokolls übergeben werden.

Mit der [/ob](../build/reference/ob-inline-function-expansion.md) -compileroptimierungs-Option kann bestimmt werden, ob die Inline Funktionserweiterung tatsächlich auftritt.

[/LTCG](../build/reference/ltcg-link-time-code-generation.md) führt Modul übergreifende Inlining unabhängig davon aus, ob es im Quellcode angefordert wurde.

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

Die Member-Funktionen einer Klasse können Inline deklariert werden, entweder mithilfe des **Inline** Schlüsselworts oder durch Platzieren der Funktionsdefinition innerhalb der Klassendefinition.

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

Das **__inline** -Schlüsselwort entspricht **Inline**.

Selbst bei **__forceinline**kann der Compiler nicht in allen Situationen Inline Code Inline durch. Der Compiler kann keine Funktion inline setzen, wenn Folgendes der Fall ist:

- Die Funktion oder ihr Aufrufer werden mit /Ob0 kompiliert (die Standardoption für Debugbuilds).

- Die Funktion und der Aufrufer verwenden unterschiedliche Typen der Ausnahmebehandlung (C++-Ausnahmebehandlung zum einen, strukturierte Ausnahmebehandlung zum anderen).

- Die Funktion weist eine variable Argumentliste auf.

- Die Funktion verwendet eine Inlineassembly, es sei denn, sie wird mit /Og, /Ox, /O1, oder /O2 kompiliert.

- Die Funktion ist rekursiv und wird nicht von **#Pragma inline_recursion (on)** begleitet. Mit dem Pragma werden rekursive Funktionen mit einer Standardtiefe von 16 Aufrufen inline gesetzt. Verwenden Sie [inline_depth](../preprocessor/inline-depth.md) -Pragma, um die Inlining-Tiefe zu verringern.

- Die Funktion ist virtuell und wird virtuell aufgerufen. Direkte Aufrufe virtueller Funktionen können inline gesetzt werden.

- Das Programm akzeptiert die Adresse der Funktion, und der Aufruf erfolgt über den Zeiger auf die Funktion. Direkte Aufrufe von Funktionen, deren Adresse akzeptiert wurden, können inline gesetzt werden.

- Die-Funktion wird auch mit dem [Naked](../cpp/naked-cpp.md) - [__declspec](../cpp/declspec.md) Modifizierer markiert.

Wenn der Compiler eine mit **__forceinline**deklarierte Funktion nicht Inline ausführen kann, generiert er eine Warnung der Stufe 1, ausgenommen:

- Die Funktion wird mit/od oder/Ob0. kompiliert. In diesen Fällen wird kein Inlining erwartet.

- Die-Funktion wird extern, in einer enthaltenen Bibliothek oder einer anderen Übersetzungseinheit definiert, oder ist ein virtuelles oder indirektes aufrufsziel. Der Compiler kann keinen nicht Inline Code identifizieren, der in der aktuellen Übersetzungseinheit nicht gefunden werden kann.

Rekursive Funktionen können Inline zu einer vom [inline_depth](../preprocessor/inline-depth.md) -Pragma angegebenen Tiefe, bis zu einem Maximum von 16 aufrufen, ersetzt werden. Nach dieser Tiefe werden rekursive Funktionsaufrufe als Aufrufe einer Instanz der Funktion behandelt.  Die Tiefe, bis zu der rekursive Funktionen durch die Inlineheuristik geprüft werden, kann 16 nicht überschreiten. Das [inline_recursion](../preprocessor/inline-recursion.md) -Pragma steuert die Inline Erweiterung einer Funktion, die zurzeit in der Erweiterung ist. Weitere Informationen finden Sie unter der/ob [-Compileroption (Inline Funktionserweiterung](../build/reference/ob-inline-function-expansion.md) ).

**Ende Microsoft-spezifisch**

Weitere Informationen zur Verwendung des **Inline** Spezifizierers finden Sie unter:

- [Inline-Klassenmember-Funktionen](../cpp/inline-functions-cpp.md)

- [Definieren von C++-Inlinefunktionen mit dllexport und dllimport](../cpp/defining-inline-cpp-functions-with-dllexport-and-dllimport.md)

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

Wenn die Koordinaten Manipulation ein relativ allgemeiner Vorgang in einem Client einer solchen Klasse ist, spart die Angabe der beiden Accessorfunktionen (`x` und `y` im vorangehenden Beispiel) in **der Regel den** mehr Aufwand in:

- Funktionsaufrufen (einschließlich der Parameterübergabe und -ablage der Adresse des Objekts auf dem Stapel)

- Beibehaltung des Stapelrahmens des Aufrufers

- Neuem Stapelrahmensetup

- Rückgabewertkommunikation

- Wiederherstellung des alten Stapelrahmens

- Rückgabewert

## <a name="inline-functions-vs-macros"></a>Inline Funktionen im Vergleich zu Makros

Obwohl Inlinefunktionen Makros ähneln (da der Funktionscode zum Zeitpunkt des Aufrufs zur Kompilierzeit erweitert wird), werden Inlinefunktionen vom Compiler analysiert, während Makros vom Präprozessor erweitert werden. Folglich gibt es einige wichtige Unterschiede:

- Inlinefunktionen folgen allen Protokollen des Typs mit erzwungener Sicherheit auf normalen Funktionen.

- Inline Funktionen werden mit der gleichen Syntax wie jede andere Funktion angegeben, mit dem Unterschied, dass Sie das **Inline** Schlüsselwort in der Funktionsdeklaration enthalten.

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

Die Absicht des Ausdrucks `toupper(getc(stdin))` ist, dass ein Zeichen vom Konsolen Gerät (`stdin`) gelesen und bei Bedarf in Großbuchstaben konvertiert werden soll.

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

## <a name="see-also"></a>Weitere Informationen

[noinline](../cpp/noinline.md)<br/>
[auto_inline](../preprocessor/auto-inline.md)

---
title: Postfixausdrücke
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], postfix
- postfix expressions
- expressions [C++], postfix
ms.assetid: 7ac62a57-06df-422f-b012-a75b37d7cb9b
ms.openlocfilehash: 9a5c99c78623f2192b59a73f270f3ad5d2a34516
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231168"
---
# <a name="postfix-expressions"></a>Postfixausdrücke

Postfixausdrücke bestehen aus primären Ausdrücken bzw. Ausdrücken, in denen Postfixoperatoren einem primären Ausdruck folgen. Die Postfix-Operatoren sind in der folgenden Tabelle aufgeführt.

### <a name="postfix-operators"></a>Postfix-Operatoren

|Name des Operators|Operator-Notation|
|-------------------|-----------------------|
|[Index Operator](../cpp/subscript-operator.md)|**[ ]**|
|[Funktionsaufrufoperator](../cpp/function-call-operator-parens.md)|**( )**|
|[Operator für die explizite Typkonvertierung](../cpp/explicit-type-conversion-operator-parens.md)|*Typname* **()**|
|[Member Access-Operator](../cpp/member-access-operators-dot-and.md)|**.** noch**->**|
|[Postfix-Operator für Inkrement](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**++**|
|[Postfix-Operator für Dekrement](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|**--**|

Die folgende Syntax beschreibt mögliche Postfixausdrücke:

```
primary-expression
postfix-expression[expression]postfix-expression(expression-list)simple-type-name(expression-list)postfix-expression.namepostfix-expression->namepostfix-expression++postfix-expression--cast-keyword < typename > (expression )typeid ( typename )
```

Der obige *Postfix-Ausdruck* kann ein [primärer Ausdruck](primary-expressions.md) oder ein anderer Postfix-Ausdruck sein. Postfixausdrücke gruppieren sich von links nach rechts und ermöglichen so das Verketten der Ausdrücke wie folgt:

```cpp
func(1)->GetValue()++
```

Im obigen Ausdruck `func` ist ein primärer Ausdruck, `func(1)` ein funktionspostfix-Ausdruck, `func(1)->GetValue` ein Postfix-Ausdruck, der einen Member der-Klasse angibt, ein `func(1)->GetValue()` weiterer funktionspostfix-Ausdruck und der gesamte Ausdruck ein Postfix Ausdruck, der den Rückgabewert von GetValue erhöht.  Die Bedeutung des Ausdrucks als Ganzes ist „Funktion aufrufen, dabei 1 als Argument übergeben und einen Zeiger für eine Klasse als Rückgabewert erhalten.  Anschließend `GetValue()` können Sie für diese Klasse aufzurufen und dann den zurückgegebenen Wert erhöhen.

Die oben aufgeführten Ausdrücke sind Zuweisungsausdrücke, was bedeutet, dass das Ergebnis dieser Ausdrücke ein "r-value" sein muss.

Die Form des Postfixausdrucks

```cpp
simple-type-name ( expression-list )
```

gibt den Aufruf des Konstruktors an.  Wenn "simple-type-name" ein grundlegender Typ ist, muss die Ausdrucksliste ein einzelner Ausdruck sein, und dieser Ausdruck gibt eine Umwandlung des Werts des Ausdrucks in den einfachen Typ an.  Dieser Typ von Umwandlungsausdruck imitiert einen Konstruktor.  Da diese Form die Konstruktion grundlegender Klassen und Typen mit derselben Syntax ermöglicht, ist sie bei der Definition von Vorlagenklassen besonders nützlich.

Das *Cast-Schlüsselwort* ist einer von **`dynamic_cast`** , **`static_cast`** oder **`reinterpret_cast`** .  Weitere Informationen finden Sie unter [`dynamic_cast`](dynamic-cast-operator.md) , [`static_cast`](static-cast-operator.md) und [`reinterpet_cast`](reinterpret-cast-operator.md) .

Der **`typeid`** Operator wird als Postfix Ausdruck angesehen.  Siehe **typeid-Operator**.

## <a name="formal-and-actual-arguments"></a>Formale und tatsächliche Argumente

Aufrufende Programme übergeben Informationen an die aufgerufenen Funktionen in „tatsächlichen Argumenten“. Die aufgerufenen Funktionen greifen mithilfe der entsprechenden „formalen Argumente“ auf die Informationen zu.

Wenn eine Funktion aufgerufen wird, werden die folgenden Aufgaben ausgeführt:

- Alle tatsächlichen Argumente (die vom Aufrufer angegebenen) werden ausgewertet. Es gibt keine implizite Reihenfolge, in der diese Argumente ausgewertet werden. Alle Argumente werden jedoch ausgewertet, und alle Nebeneffekte werden vor dem Eintritt in die Funktion abgeschlossen.

- Jedes formale Argument wird mit dem entsprechenden tatsächlichen Argument in der Ausdrucksliste initialisiert. (Ein formales Argument ist ein Argument, das im Funktions Header deklariert und im Text einer Funktion verwendet wird.) Konvertierungen erfolgen wie bei der Initialisierung – sowohl standardmäßige als auch benutzerdefinierte Konvertierungen werden bei der Konvertierung eines tatsächlichen Arguments in den richtigen Typ durchgeführt. Die ausgeführte Initialisierung wird durch den folgenden Code konzeptionell veranschaulicht:

    ```cpp
    void Func( int i ); // Function prototype
    ...
    Func( 7 );          // Execute function call
    ```

   Die konzeptionellen Initialisierungen vor dem Aufruf sind:

    ```cpp
    int Temp_i = 7;
    Func( Temp_i );
    ```

   Beachten Sie, dass die Initialisierung ausgeführt wird, als würde die Gleichheitszeichensyntax anstelle der Klammersyntax verwendet werden. Eine Kopie von `i` wird vor dem Übergeben des Werts an die Funktion erstellt. (Weitere Informationen finden Sie unter [Initialisierer](../cpp/initializers.md) und [Konvertierungen](../cpp/user-defined-type-conversions-cpp.md)).

   Wenn also der Funktionsprototyp (Deklaration) ein Argument vom Typ aufruft **`long`** und das aufrufende Programm ein tatsächliches Argument vom Typ bereitstellt **`int`** , wird das tatsächliche Argument mithilfe einer Standardtyp Konvertierung in den Typ herauf gestuft **`long`** (siehe [Standard Konvertierungen](../cpp/standard-conversions.md)).

   Es ist ein Fehler, ein tatsächliches Argument anzugeben, für das es keine Standard- oder benutzerdefinierte Konvertierung in den Typ des formalen Arguments gibt.

   Für die tatsächlichen Argumente des Klassentyps wird das formale Argument initialisiert, indem der Konstruktor der Klasse aufgerufen wird. (Weitere Informationen zu diesen speziellen Klassenmember-Funktionen finden Sie unter [Konstruktoren](../cpp/constructors-cpp.md) .)

- Der Funktionsaufruf wird ausgeführt.

Das folgende Programmfragment zeigt einen Funktionsaufruf:

```cpp
// expre_Formal_and_Actual_Arguments.cpp
void func( long param1, double param2 );

int main()
{
    long i = 1;
    double j = 2;

    // Call func with actual arguments i and j.
    func( i, j );
}

// Define func with formal parameters param1 and param2.
void func( long param1, double param2 )
{
}
```

Wenn `func` von Main aufgerufen wird, wird der formale Parameter `param1` mit dem Wert initialisiert `i` (wird in `i` den Typ konvertiert, **`long`** um mithilfe einer Standard Konvertierung dem richtigen Typ zu entsprechen), und der formale Parameter `param2` wird mit dem Wert initialisiert `j` ( `j` wird **`double`** mit einer Standard Konvertierung in den Typ konvertiert).

## <a name="treatment-of-argument-types"></a>Behandlung von Argumenttypen

Formale Argumente, die als-Typen deklariert sind, **`const`** können im Text einer Funktion nicht geändert werden. Funktionen können jedes Argument ändern, das nicht vom Typ ist **`const`** . Allerdings ist die Änderung für die Funktion lokal und wirkt sich nicht auf den Wert des tatsächlichen Arguments aus, es sei denn, das eigentliche Argument war ein Verweis auf ein Objekt, das nicht vom Typ ist **`const`** .

Die folgenden Funktionen veranschaulichen einige dieser Konzepte:

```cpp
// expre_Treatment_of_Argument_Types.cpp
int func1( const int i, int j, char *c ) {
   i = 7;   // C3892 i is const.
   j = i;   // value of j is lost at return
   *c = 'a' + j;   // changes value of c in calling function
   return i;
}

double& func2( double& d, const char *c ) {
   d = 14.387;   // changes value of d in calling function.
   *c = 'a';   // C3892 c is a pointer to a const object.
    return d;
}
```

## <a name="ellipsis-and-default-arguments"></a>Ellipsen und Standardargumente

Funktionen können deklariert werden, um weniger Argumente als in der Funktionsdefinition angegeben mit einer der folgenden beiden Methoden zu akzeptieren: Auslassungspunkte (`...`) oder Standardargumente.

Das Auslassungs Zeichen gibt an, dass möglicherweise Argumente erforderlich sind, die Anzahl und Typen jedoch nicht in der Deklaration angegeben sind. Dies ist normalerweise ein schlechtes Beispiel für C++-Programmierung, da es einen der Vorteile von C++ unterlaufen kann: Typsicherheit. Verschiedene Konvertierungen werden auf Funktionen angewendet, die mit Auslassungs Zeichen deklariert sind, als auf die Funktionen, für die die formalen und tatsächlichen Argument Typen bekannt sind:

- Wenn das tatsächliche Argument vom Typ ist **`float`** , wird es **`double`** vor dem Funktions aufrufin den Typ herauf gestuft.

- Alle-oder-,-oder- **`signed char`** **`unsigned char`** **`signed short`** **`unsigned short`** , enumerierten Typen oder Bitfelder werden mithilfe der ganzzahligen herauf Stufung in eine **`signed int`** oder eine konvertiert **`unsigned int`** .

- Jedes Argument des Klassentyps wird durch einen Wert als Datenstruktur übergeben; die Kopie wird durch Kopieren der Binärdatei statt durch Aufrufen des Kopierkonstruktors der Klasse erstellt (falls vorhanden).

Auslassungs Zeichen (sofern verwendet) müssen als letztes in der Argumentliste deklariert werden. Weitere Informationen zum Übergeben einer Variablen Anzahl von Argumenten finden Sie in der Referenz zu [va_arg, va_start und va_list](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) in der *Lauf Zeit Bibliotheks Referenz*.

Informationen zu Standardargumenten in der CLR-Programmierung finden Sie unter [Variablen Argument Listen (...) (C++/CLI)](../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md).

Mit Standardargumenten können Sie den Wert festlegen, den ein Argument annehmen soll, wenn keiner im Funktionsaufruf angegeben wird. Das folgende Codefragment zeigt, wie Standardargumente funktionieren. Weitere Informationen zu Einschränkungen beim Angeben von Standardargumenten finden Sie unter [Standardargumente](../cpp/default-arguments.md).

```cpp
// expre_Ellipsis_and_Default_Arguments.cpp
// compile with: /EHsc
#include <iostream>

// Declare the function print that prints a string,
// then a terminator.
void print( const char *string,
            const char *terminator = "\n" );

int main()
{
    print( "hello," );
    print( "world!" );

    print( "good morning", ", " );
    print( "sunshine." );
}

using namespace std;
// Define print.
void print( const char *string, const char *terminator )
{
    if( string != NULL )
        cout << string;

    if( terminator != NULL )
        cout << terminator;
}
```

Das vorangehende Programm deklariert eine Funktion, `print`, die zwei Argumente akzeptiert. Das zweite Argument, *Terminator*, hat jedoch den Standardwert `"\n"` . In `main` ermöglichen die ersten beiden Aufrufe von `print` dem standardmäßigen zweiten Argument, eine neue Zeile bereitzustellen, um die gedruckte Zeichenfolge zu beenden. Der dritte Aufruf gibt einen expliziten Wert für das zweite Argument zurück. Die Ausgabe des Programms lautet

```Output
hello,
world!
good morning, sunshine.
```

## <a name="see-also"></a>Siehe auch

[Ausdrucks Typen](../cpp/types-of-expressions.md)

---
title: Funktionsüberladung
ms.date: 03/27/2019
helpviewer_keywords:
- function overloading [C++], about function overloading
- function overloading
- declaring functions [C++], overloading
ms.assetid: 3c9884cb-1d5e-42e8-9a49-6f46141f929e
ms.openlocfilehash: a59c0e27a4500cb20ef42e9a55b4eb0004e07f65
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368907"
---
# <a name="function-overloading"></a>Funktionsüberladung

C++ lässt die Angabe mehrerer Funktionen mit dem gleichen Namen im gleichen Gültigkeitsbereich zu. Diese Funktionen werden als *überladene* Funktionen bezeichnet. Überladene Funktionen ermöglichen es Ihnen, je nach Typ und Anzahl der Argumente unterschiedliche Semantik für eine Funktion zu liefern.

Beispielsweise kann `print` eine Funktion, `std::string` die ein Argument verwendet, ganz andere Aufgaben ausführen als eine, die ein Argument vom Typ **double**verwendet. Durch das Überladen können Sie `print_string` Namen `print_double`wie z. B. oder verwenden. Zum Zeitpunkt der Kompilierung wählt der Compiler basierend auf dem Vom Aufrufer übergebenen Argumenttyp aus, welche Überladung verwendet werden soll.  Wenn Sie `print(42.0)`aufrufen, `void print(double d)` wird die Funktion aufgerufen. Wenn Sie `print("hello world")`aufrufen, `void print(std::string)` wird die Überladung aufgerufen.

Sie können sowohl Memberfunktionen als auch Nicht-Memberfunktionen überlasten. Die folgende Tabelle zeigt, welche Teile einer Funktionsdeklaration von C++ verwendet werden, um zwischen Gruppen von Funktionen mit dem gleichen Namen und dem gleichen Gültigkeitsbereich zu differenzieren.

### <a name="overloading-considerations"></a>Überlegungen zur Überladung

|Funktionsdeklarationselement|Wird zum Überladen verwendet?|
|----------------------------------|---------------------------|
|Funktionsrückgabetyp|Nein|
|Anzahl der Argumente|Ja|
|Typ der Argumente|Ja|
|Vorhandensein oder Abwesenheit von Auslassungszeichen|Ja|
|Verwendung von **typedef-Namen**|Nein|
|Nicht angegebene Arraygrenzen|Nein|
|**const** oder **flüchtig**|Ja, wenn sie auf die gesamte Funktion angewendet wird|
|[Ref-Qualifizierer](#ref-qualifiers)|Ja|

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht, wie das Überladen verwendet werden kann.

```cpp
// function_overloading.cpp
// compile with: /EHsc
#include <iostream>
#include <math.h>
#include <string>

// Prototype three print functions.
int print(std::string s);             // Print a string.
int print(double dvalue);            // Print a double.
int print(double dvalue, int prec);  // Print a double with a
                                     //  given precision.
using namespace std;
int main(int argc, char *argv[])
{
    const double d = 893094.2987;
    if (argc < 2)
    {
        // These calls to print invoke print( char *s ).
        print("This program requires one argument.");
        print("The argument specifies the number of");
        print("digits precision for the second number");
        print("printed.");
        exit(0);
    }

    // Invoke print( double dvalue ).
    print(d);

    // Invoke print( double dvalue, int prec ).
    print(d, atoi(argv[1]));
}

// Print a string.
int print(string s)
{
    cout << s << endl;
    return cout.good();
}

// Print a double in default precision.
int print(double dvalue)
{
    cout << dvalue << endl;
    return cout.good();
}

//  Print a double in specified precision.
//  Positive numbers for precision indicate how many digits
//  precision after the decimal point to show. Negative
//  numbers for precision indicate where to round the number
//  to the left of the decimal point.
int print(double dvalue, int prec)
{
    // Use table-lookup for rounding/truncation.
    static const double rgPow10[] = {
        10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1,
        10E0, 10E1,  10E2,  10E3,  10E4, 10E5,  10E6 };
    const int iPowZero = 6;

    // If precision out of range, just print the number.
    if (prec < -6 || prec > 7)
    {
        return print(dvalue);
    }
    // Scale, truncate, then rescale.
    dvalue = floor(dvalue / rgPow10[iPowZero - prec]) *
        rgPow10[iPowZero - prec];
    cout << dvalue << endl;
    return cout.good();
}
```

Der vorhergehende Code zeigt das Überladen der `print`-Funktion im Dateigültigkeitsbereich an.

Das Standardargument wird nicht als Teil des Funktionstyps betrachtet. Daher wird es nicht bei der Auswahl überladener Funktionen verwendet. Zwei Funktionen, die sich nur bei den Standardargumenten unterscheiden, werden als mehrfache Definitionen und nicht als überladene Funktionen betrachtet.

Standardargumente können für überladene Operatoren nicht bereitgestellt werden.

## <a name="argument-matching"></a>Argumentübereinstimmung

Überladene Funktionen werden für die beste Übereinstimmung von Funktionsdeklarationen im aktuellen Bereich für Argumente ausgewählt, die im Funktionsaufruf angegeben werden. Wenn eine passende Funktion gefunden wird, wird diese Funktion aufgerufen. "Geeignet" bedeutet in diesem Zusammenhang entweder:

- Ein exakte Übereinstimmung wurde gefunden.

- Eine triviale Konvertierung wurde ausgeführt.

- Eine ganzzahlige Heraufstufung wurde ausgeführt.

- Eine Standardkonvertierung zum gewünschten Argumenttyp ist vorhanden.

- Eine benutzerdefinierte Konvertierung (entweder Konvertierungsoperator oder Konstruktor) auf den gewünschten Argumenttyp ist vorhanden.

- Es wurden durch Ellipsen dargestellte Argumente gefunden.

Der Compiler erstellt einen Satz Kandidatenfunktionen für jedes Argument. Kandidatenfunktionen sind Funktionen, in denen das tatsächliche Argument an dieser Position in den Typ des formalen Arguments konvertiert werden kann.

Ein Satz von „am besten passenden Funktionen“ wird für jedes Argument erstellt, und die ausgewählte Funktion ist die Schnittmenge aller Sätze. Wenn die Schnittmenge mehr als eine Funktion enthält, ist das Überladen mehrdeutig und generiert einen Fehler. Die letztendlich ausgewählte Funktion stimmt stets besser überein als jede andere Funktion in der Gruppe für mindestens ein Argument. Wenn es keinen eindeutigen Gewinner gibt, generiert der Funktionsaufruf einen Fehler.

Berücksichtigen Sie die folgenden Deklarationen (Funktionen sind zur Identifikation der folgenden Erläuterung als `Variant 1`, `Variant 2` und `Variant 3` gekennzeichnet):

```cpp
Fraction &Add( Fraction &f, long l );       // Variant 1
Fraction &Add( long l, Fraction &f );       // Variant 2
Fraction &Add( Fraction &f, Fraction &f );  // Variant 3

Fraction F1, F2;
```

Betrachten Sie folgende Anweisung:

```cpp
F1 = Add( F2, 23 );
```

Die vorhergehende Anweisung erstellt zwei Sätze:

|Satz 1: Kandidatenfunktionen, deren erstes Argument vom Typ „fraction“ ist|Set 2: Kandidatenfunktionen, deren zweites Argument in Type **int** konvertiert werden kann|
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
|Variant 1|Variante 1 (**int** kann mit einer Standardkonvertierung in **long** konvertiert werden)|
|Variant 3||

Funktionen in Satz 2 sind Funktionen, für die es implizite Konvertierungen vom tatsächlichen Parametertyp in den formalen Parametertyp gibt, und unter diesen Funktionen gibt es eine Funktion, für die die "Kosten" der Konvertierung des tatsächlichen Parametertyps in seinen formalen Parametertyp der kleinste ist.

Die Schnittmenge dieser beiden Sätze ist "Variant 1". Ein Beispiel für einen mehrdeutigen Funktionsaufruf ist:

```cpp
F1 = Add( 3, 6 );
```

Der vorhergehende Funktionsaufruf erstellt die folgenden Sätze:

|Set 1: Kandidatenfunktionen, die das erste Argument des **Typs int** haben|Set 2: Kandidatenfunktionen, die zweites Argument des **Typs int** haben|
|---------------------------------------------------------------------|----------------------------------------------------------------------|
|Variante 2 (**int** kann mit einer Standardkonvertierung in **long** konvertiert werden)|Variante 1 (**int** kann mit einer Standardkonvertierung in **long** konvertiert werden)|

Da der Schnittpunkt dieser beiden Sätze leer ist, generiert der Compiler eine Fehlermeldung.

Bei der Argumentübereinstimmung wird eine Funktion mit *n* Standardargumenten als *n*+1 separate Funktionen mit jeweils einer anderen Anzahl von Argumenten behandelt.

Die Ellipse (...) dient als Platzhalter; sie stimmt mit jedem tatsächlichen Argument überein. Es kann zu vielen mehrdeutigen Sätzen führen, wenn Sie Ihre überladenen Funktionssätze nicht mit äußerster Sorgfalt entwerfen.

> [!NOTE]
> Die Mehrdeutigkeit überladener Funktionen kann erst festgestellt werden, wenn ein Funktionsaufruf gefunden wurde. An diesem Punkt werden die Sätze für jedes Argument im Funktionsaufruf erstellt, und Sie können bestimmen, ob eine eindeutige Überladung vorhanden ist. Dies bedeutet, dass Mehrdeutigkeiten im Code vorhanden sein dürfen, bis sie durch einen bestimmten Funktionsaufruf eindeutig deklariert werden.

## <a name="argument-type-differences"></a>Unterschiede bei Argumenttypen

Überladene Funktionen unterscheiden zwischen Argumenttypen, die verschiedene Initialisierer erfordern. Daher gelten ein Argument eines angegebenen Typs und ein Verweis auf diesen Typ für den Zweck des Überladens als identisch. Sie gelten als identisch, weil sie die gleichen Initialisierer erfordern. `max( double, double )` wird beispielsweise identisch mit `max( double &, double & )` betrachtet. Das Deklarieren von zwei solcher Funktionen verursacht einen Fehler.

Aus dem gleichen Grund werden Funktionsargumente eines Typs, der von **const** oder **volatile** geändert wurde, zum Zwecke der Überladung nicht anders behandelt als der Basistyp.

Der Funktionsüberlademechanismus kann jedoch zwischen Referenzen unterscheiden, die durch **const** und volatile qualifiziert **sind,** und Verweisen auf den Basistyp. Es ermöglicht Code wie den folgenden:

```cpp
// argument_type_differences.cpp
// compile with: /EHsc /W3
// C4521 expected
#include <iostream>

using namespace std;
class Over {
public:
   Over() { cout << "Over default constructor\n"; }
   Over( Over &o ) { cout << "Over&\n"; }
   Over( const Over &co ) { cout << "const Over&\n"; }
   Over( volatile Over &vo ) { cout << "volatile Over&\n"; }
};

int main() {
   Over o1;            // Calls default constructor.
   Over o2( o1 );      // Calls Over( Over& ).
   const Over o3;      // Calls default constructor.
   Over o4( o3 );      // Calls Over( const Over& ).
   volatile Over o5;   // Calls default constructor.
   Over o6( o5 );      // Calls Over( volatile Over& ).
}
```

### <a name="output"></a>Output

```Output
Over default constructor
Over&
Over default constructor
const Over&
Over default constructor
volatile Over&
```

Zeiger auf **const-** und **flüchtige** Objekte werden auch als unterschiedlich betrachtet als Zeiger zum Basistyp zum Zwecke der Überladung.

## <a name="argument-matching-and-conversions"></a>Argumentübereinstimmung und Konvertierungen

Wenn der Compiler versucht, die tatsächlichen Argumente mit den Argumenten in Funktionsdeklarationen abzugleichen, kann er Standardkonvertierungen oder benutzerdefinierte Konvertierungen bereitstellen, um den korrekten Typ zu erhalten, wenn keine genaue Übereinstimmung gefunden wird. Die Anwendung von Konvertierungen unterliegt diesen Regeln:

- Sequenzen von Konvertierungen, die mehr als eine benutzerdefinierte Konvertierung enthalten, werden nicht berücksichtigt.

- Sequenzen von Konvertierungen, die gekürzt werden können, indem Konvertierungen im Zwischenformat entfernt werden, werden nicht berücksichtigt.

Das Ergebnis der Konvertierungssequenz, falls vorhanden, ist die am besten passende Sequenz. Es gibt mehrere Möglichkeiten, ein Objekt vom Typ **int** mithilfe von Standardkonvertierungen in Typ **unsigniert long** zu konvertieren (siehe [Standardkonvertierungen):](../cpp/standard-conversions.md)

- Konvertieren Sie von **int** zu **lang** und dann von **lang** nach **unsigniert lang**.

- Konvertieren Sie von **int** in **unsigned long**.

Die erste Sequenz, obwohl sie das gewünschte Ziel erreicht, ist nicht die beste Matching-Sequenz – eine kürzere Sequenz existiert.

Die folgende Tabelle zeigt eine Gruppe von Konvertierungen, die als triviale Konvertierungen bezeichnet werden, die eine begrenzte Auswirkung auf die Bestimmung haben, welche Sequenz die größte Übereinstimmung hat. Die Instanzen, in denen triviale Konvertierungen sich auf die Sequenzwahl auswirken, werden in der Liste nach der Tabelle behandelt.

### <a name="trivial-conversions"></a>Triviale Konvertierungen

|Konvertieren von Typ|Konvertiert in Typ|
|-----------------------|---------------------|
|*Typname*|*Typname***&**|
|*Typname***&**|*Typname*|
|*Typname* **[ ]**|*Typname*__\*__|
|*Typname* **(** *Argumentliste* **)**|**(** __\*__ *Typname* **) (** *Argumentliste* **)**|
|*Typname*|**const** *const-Typname*|
|*Typname*|**flüchtiger** *Typname*|
|*Typname*__\*__|**const** *const-Typname*__\*__|
|*Typname*__\*__|**flüchtiger** *Typname*__\*__|

Die Reihenfolge für Konvertierungen lautet wie folgt:

1. Genaue Übereinstimmung. Ein genaue Übereinstimmung zwischen den Typen, mit denen die Funktion aufgerufen wird und den Typen, die im Funktionsprototyp deklariert werden, ist immer die beste Übereinstimmung. Sequenzen von trivialen Konvertierungen werden als exakte Übereinstimmungen klassifiziert. Sequenzen, die keine dieser Konvertierungen vornehmen, werden jedoch als besser angesehen als Sequenzen, die konvertiert werden:

   - Vom Zeiger, zum Zeiger **const** nach`type` <strong>\*</strong> const ( zu **const** `type` <strong>\*</strong>).

   - Vom Zeiger zum Zeiger **volatile** auf`type` <strong>\*</strong> flüchtig ( zu **flüchtig** `type` <strong>\*</strong>).

   - Von Verweis, auf Verweis`type` **&** auf **const** ( bis **const** `type` **&**).

   - Von Verweis auf Verweis`type` **&** auf **flüchtige** ( zu **flüchtige** `type` **&**).

1. Übereinstimmung mithilfe von Erweiterungen. Jede Sequenz, die nicht als exakte Übereinstimmung klassifiziert ist, die nur integrale Promotions, Konvertierungen von **float** in **double**und triviale Konvertierungen enthält, wird als Übereinstimmung mithilfe von Werbeaktionen klassifiziert. Obwohl eine Übereinstimmung mit Erweiterungen besser ist als eine Übereinstimmung, die Standardkonvertierungen verwendet, ist sie nicht so gut wie eine genaue Übereinstimmung.

1. Übereinstimmung mithilfe von Standardkonvertierungen. Jede beliebige Sequenz, die nicht als genaue Übereinstimmung klassifiziert wird, oder eine Übereinstimmung mithilfe von Erweiterungen, die nur Standardkonvertierungen und triviale Konvertierungen enthält, wird als Übereinstimmung mithilfe von Standardkonvertierungen klassifiziert. In dieser Kategorie gelten die folgenden Regeln:

   - Die Konvertierung von einem Zeiger in eine abgeleitete Klasse in einen Zeiger in eine `void *` direkte `const void *`oder indirekte Basisklasse ist der Konvertierung in oder vorzuziehen.

   - Die Konvertierung von einem Zeiger auf eine abgeleitete Klasse in einen Zeiger auf eine Basisklasse erzeugt eine bessere Übereinstimmung, je näher die Basisklasse der direkten Basisklasse ist. Angenommen, die Klassenhierarchie folgt der in der folgenden Abbildung dargestellten Klassenhierarchie.

![Diagramm der bevorzugten Konvertierungen](../cpp/media/vc391t1.gif "Diagramm der bevorzugten Konvertierungen") <br/>
Diagramm mit bevorzugten Konvertierungen

Die Konvertierung von Typ `D*` in Typ `C*` ist der Konvertierung von Typ `D*` in Typ `B*` vorzuziehen. Entsprechend ist die Konvertierung von Typ `D*` in Typ `B*` der Konvertierung von Typ `D*` in Typ `A*` vorzuziehen.

Die gleiche Regel gilt für Verweiskonvertierungen. Die Konvertierung von Typ `D&` in Typ `C&` ist der Konvertierung von Typ `D&` in Typ `B&` usw. vorzuziehen.

Die gleiche Regel gilt für pointer-to-member-Konvertierungen. Die Konvertierung von Typ `T D::*` in Typ `T C::*` ist der Konvertierung von Typ `T D::*` in Typ `T B::*` und so weiter vorzuziehen (wobei `T` der Typ des Members ist).

Die vorhergehende Regel gilt nur für einen bestimmten Ableitungspfad. Betrachten Sie das Diagramm, das in der folgenden Abbildung dargestellt wird.

![Mehrere&#45;Vererbung, die bevorzugte Conversions anzeigt](../cpp/media/vc391t2.gif "Mehrere&#45;Vererbung, die bevorzugte Conversions anzeigt") <br/>
Diagramm mit mehrfacher Vererbung, das bevorzugte Konvertierungen anzeigt

Die Konvertierung von Typ `C*` in Typ `B*` ist der Konvertierung von Typ `C*` in Typ `A*` vorzuziehen. Der Grund liegt darin, dass sie sich auf dem gleichen Pfad befinden, und `B*` näher liegt. Die Konvertierung von `C*` Typ `D*` zu Typ ist jedoch nicht `A*`vorzuziehen als die Konvertierung in Typ ; Es gibt keine Präferenz, da die Konvertierungen unterschiedlichen Pfaden folgen.

1. Übereinstimmung mit benutzerdefinierten Konvertierungen. Diese Sequenz kann nicht als exakte Übereinstimmung, Übereinstimmung mit Promotions oder eine Übereinstimmung mit Standardkonvertierungen klassifiziert werden. Die Reihenfolge darf nur benutzerdefinierte Konvertierungen, Standardkonvertierungen oder triviale Konvertierungen enthalten, um die Übereinstimmung mit benutzerdefinierten Konvertierungen zu erreichen. Eine Übereinstimmung mit benutzerdefinierten Konvertierungen gilt als eine bessere Übereinstimmung als eine Übereinstimmung mit einem Auslassungszeichen, jedoch als nicht so gut wie eine Übereinstimmung mit Standardkonvertierungen.

1. Übereinstimmung mit einem Auslassungszeichen. Jede beliebige Sequenz, die Auslassungszeichen in der Deklaration entspricht, wird als Übereinstimmung mit einem Auslassungszeichen klassifiziert. Es gilt als das schwächste Match.

Benutzerdefinierte Konvertierungen werden angewendet, wenn keine integrierte Erweiterung oder Konvertierung vorhanden ist. Diese Konvertierungen werden auf der Grundlage des Typs des Arguments ausgewählt, das abgeglichen wird. Betrachten Sie folgenden Code:

```cpp
// argument_matching1.cpp
class UDC
{
public:
   operator int()
   {
      return 0;
   }
   operator long();
};

void Print( int i )
{
};

UDC udc;

int main()
{
   Print( udc );
}
```

Die verfügbaren benutzerdefinierten Konvertierungen `UDC` für die Klasse stammen vom Typ **int** und type **long**. Deshalb berücksichtigt der Compiler Konvertierungen für den Typ des Objekts, das abgeglichen wird: `UDC`. Eine Konvertierung **in int** ist vorhanden und wird ausgewählt.

Während des Prozesseses zum Zuordnen von Argumenten können Standardkonvertierungen sowohl auf das Argument als auch auf das Ergebnis einer benutzerdefinierten Konvertierung angewendet werden. Daher funktioniert der folgende Code:

```cpp
void LogToFile( long l );
...
UDC udc;
LogToFile( udc );
```

Im vorherigen Beispiel wird der benutzerdefinierte Konvertierungsoperator **,operator long**, aufgerufen, um in type `udc` **long**zu konvertieren. Wenn keine benutzerdefinierte Konvertierung in Typ **long** definiert worden wäre, wäre `UDC` die Konvertierung wie folgt verlaufen: Typ wäre mit der benutzerdefinierten Konvertierung in Type **int** konvertiert worden. Dann wäre die Standardkonvertierung von type **int** in type **long** angewendet worden, um dem Argument in der Deklaration zu entsprechen.

Wenn benutzerdefinierte Konvertierungen erforderlich sind, um einem Argument zu entsprechen, werden die Standardkonvertierungen bei der Bewertung der besten Übereinstimmung nicht verwendet. Auch wenn mehr als eine Kandidatenfunktion eine benutzerdefinierte Konvertierung erfordert, werden die Funktionen als gleich betrachtet. Beispiel:

```cpp
// argument_matching2.cpp
// C2668 expected
class UDC1
{
public:
   UDC1( int );  // User-defined conversion from int.
};

class UDC2
{
public:
   UDC2( long ); // User-defined conversion from long.
};

void Func( UDC1 );
void Func( UDC2 );

int main()
{
   Func( 1 );
}
```

Beide Versionen `Func` von erfordern eine benutzerdefinierte Konvertierung, um typ **int** in das Klassentypargument zu konvertieren. Mögliche Konversionen sind:

- Konvertieren Sie vom Typ `UDC1` **int** in type (eine benutzerdefinierte Konvertierung).

- Konvertieren von Typ **int** in Typ **long**; konvertieren Sie `UDC2` dann in Typ (eine zweistufige Konvertierung).

Obwohl die zweite Konvertierung sowohl eine Standardkonvertierung als auch die benutzerdefinierte Konvertierung erfordert, werden die beiden Konvertierungen weiterhin als gleich betrachtet.

> [!NOTE]
> Benutzerdefinierte Konvertierungen gelten als Konvertierung durch Konstruktion oder als Konvertierung durch Initialisierung (Konvertierungsfunktion). Beide Methoden werden als gleich betrachtet, wenn die beste Übereinstimmung berücksichtigt wird.

## <a name="argument-matching-and-the-this-pointer"></a>Argumentübereinstimmung und der this-Zeiger

Klassenmemberfunktionen werden unterschiedlich behandelt, je nachdem, ob sie als **statisch**deklariert werden. Da nicht statische Funktionen über ein implizites Argument verfügen, das den **zeigerums** bereitstellt, werden nichtstatische Funktionen als ein Argument mehr als statische Funktionen betrachtet. andernfalls werden sie für identisch erklärt.

Diese nicht statischen Memberfunktionen erfordern, dass der implizite **zeiger dieser** Zeiger mit dem Objekttyp übereinstimmt, über den die Funktion aufgerufen wird, oder für überladene Operatoren erfordern, dass das erste Argument mit dem Objekt übereinstimmt, auf das der Operator angewendet wird. (Weitere Informationen zu überlasteten Operatoren finden Sie unter [Überladene Operatoren](../cpp/operator-overloading.md).)

Im Gegensatz zu anderen Argumenten in überladenen Funktionen werden keine temporären Objekte eingeführt, und es werden keine Konvertierungen versucht, wenn versucht wird, dem **Argument dieses** Zeigers zu entsprechen.

Wenn `->` der Memberauswahloperator für den Zugriff auf `class_name`eine Memberfunktion der Klasse `class_name * const`verwendet wird, hat das **dieses** Zeigerargument den Typ . Wenn die Member als **const** oder **volatile**deklariert werden, sind `const class_name * const` die Typen bzw. `volatile class_name * const`.

Der Memberauswahloperator `.` funktioniert genau auf die gleiche Weise, außer dass ein impliziter `&`-Operator (address-of) dem Objektnamen vorangestellt ist. Im folgenden Beispiel wird gezeigt, wie dies funktioniert:

```cpp
// Expression encountered in code
obj.name

// How the compiler treats it
(&obj)->name
```

Der linke Operand der Operatoren `->*` und `.*` (Zeiger auf Member) wird hinsichtlich der Argumentübereinstimmung genauso wie der `.`-Operator und der `->`-Operator (Memberauswahl) behandelt.

## <a name="ref-qualifiers-on-member-functions"></a><a name="ref-qualifiers"></a>Ref-Qualifizierer für Memberfunktionen

Ref-Qualifizierer ermöglichen es, eine Memberfunktion zu überlasten, je nach, ob es sich bei dem **dadurch** darauf zeigenden Objekt um einen rvalue oder einen lvalue handelt.  Diese Funktion kann verwendet werden, um unnötige Kopiervorgänge in Szenarien zu vermeiden, in denen Sie keinen Zeigerzugriff auf die Daten gewähren möchten. Angenommen, die `C` Klasse initialisiert einige Daten in ihrem Konstruktor und gibt `get_data()`eine Kopie dieser Daten in der Memberfunktion zurück. Wenn es sich `C` bei einem Objekt des Typs um einen rvalue handelt, der zerstört werden soll, wählt der Compiler die `get_data() &&` Überladung aus, die die Daten verschiebt, anstatt sie zu kopieren.

```cpp
#include <iostream>
#include <vector>

using namespace std;

class C
{

public:
    C() {/*expensive initialization*/}
    vector<unsigned> get_data() &
    {
        cout << "lvalue\n";
        return _data;
    }
    vector<unsigned> get_data() &&
    {
        cout << "rvalue\n";
        return std::move(_data);
    }

private:
    vector<unsigned> _data;
};

int main()
{
    C c;
    auto v = c.get_data(); // get a copy. prints "lvalue".
    auto v2 = C().get_data(); // get the original. prints "rvalue"
    return 0;
}
```

## <a name="restrictions-on-overloading"></a>Beschränkungen der Überlastung

Mehrere Einschränkungen steuern eine akzeptable Gruppe von überladenen Funktionen:

- Zwei beliebige Funktionen in einer Gruppe von überladenen Funktionen müssen unterschiedliche Argumentlisten haben.

- Das Überladen von Funktionen mit Argumentlisten der gleichen Typen auf alleiniger Grundlage des Rückgabetyps ist ein Fehler.

     **Microsoft Specific**

Sie können **den Operator neu** nur auf der Grundlage des Rückgabetyps überlasten, insbesondere auf der Grundlage des angegebenen Speichermodellmodifizierers.

**END Microsoft Spezifisch**

- Memberfunktionen können nicht nur auf der Grundlage von statisch und nicht statisch überladen werden.

- **typedef** typdef-Deklarationen definieren keine neuen Typen; sie führen Synonyme für bestehende Typen ein. Sie wirken sich nicht auf den Überlademechanismus aus. Betrachten Sie folgenden Code:

    ```cpp
    typedef char * PSTR;

    void Print( char *szToPrint );
    void Print( PSTR szToPrint );
    ```

   Die vorhergehenden zwei Funktionen verfügen über identische Argumentlisten. `PSTR`ist ein Synonym `char *`für typ . Im Memberbereich generiert dieser Code einen Fehler.

- Aufgelistete Typen sind verschiedene Typen und können verwendet werden, um zwischen überladenen Funktionen zu unterscheiden.

- Die Typen "array of " und "pointer to" gelten als identisch, um zwischen überladenen Funktionen zu unterscheiden, jedoch nur für singly dimensionierte Arrays. Aus diesem Grund stehen diese überlasteten Funktionen in Konflikt und generieren eine Fehlermeldung:

    ```cpp
    void Print( char *szToPrint );
    void Print( char szToPrint[] );
    ```

   Für mehrdimensionale Arrays gelten die zweite und alle nachfolgenden Dimensionen als Teil des Typs. Deshalb werden sie beim Unterscheiden zwischen überladenen Funktionen verwendet:

    ```cpp
    void Print( char szToPrint[] );
    void Print( char szToPrint[][7] );
    void Print( char szToPrint[][9][42] );
    ```

## <a name="overloading-overriding-and-hiding"></a>Überladen, Überschreiben und Ausblenden

Zwei beliebige Funktionsdeklarationen des gleichen Namens im gleichen Bereich können auf die gleiche Funktion oder zwei einzelne Funktionen, die überladen werden, verweisen. Wenn die Argumentlisten der Deklarationen Argumente äquivalenter Typen enthalten (wie im vorherigen Abschnitt beschrieben), beziehen sich die Funktionsdeklarationen auf die gleiche Funktion. Andernfalls beziehen sie sich auf zwei separate Funktionen, die mithilfe des Überladens ausgewählt werden.

Der Klassenumfang wird strikt eingehalten; Daher befindet sich eine in einer Basisklasse deklarierte Funktion nicht im gleichen Bereich wie eine Funktion, die in einer abgeleiteten Klasse deklariert ist. Wenn eine Funktion in einer abgeleiteten Klasse mit demselben Namen wie eine virtuelle Funktion in der Basisklasse deklariert wird, *überschreibt* die Funktion der abgeleiteten Klasse die Basisklassenfunktion. Weitere Informationen finden Sie unter [Virtuelle Funktionen](../cpp/virtual-functions.md).

Wenn die Basisklassenfunktion nicht als "virtuell" deklariert wird, wird die abgeleitete Klassenfunktion als *ausgeblendet.* Sowohl das Überschreiben als auch das Ausblenden unterscheiden sich von Überladungen.

Der Blockumfang wird strikt eingehalten; Daher befindet sich eine im Dateibereich deklarierte Funktion nicht im gleichen Bereich wie eine lokal deklarierte Funktion. Wenn eine lokal deklarierte Funktion den gleichen Namen wie eine Funktion besitzt, die im Dateibereich deklariert wird, blendet die lokal deklarierte Funktion die Funktion im Dateibereich aus, und es erfolgt keine Überladung. Beispiel:

```cpp
// declaration_matching1.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
void func( int i )
{
    cout << "Called file-scoped func : " << i << endl;
}

void func( char *sz )
{
   cout << "Called locally declared func : " << sz << endl;
}

int main()
{
   // Declare func local to main.
   extern void func( char *sz );

   func( 3 );   // C2664 Error. func( int ) is hidden.
   func( "s" );
}
```

Der vorhergehende Code zeigt zwei Definitionen der Funktion `func`. Die Definition, die ein `char *` Argument `main` vom Typ verwendet, ist lokal, da die **externe** Anweisung angezeigt wird. Daher ist die Definition, die ein Argument vom Typ **int** verwendet, ausgeblendet, und der erste Aufruf `func` ist fehlerhaft.

Für überladene Memberfunktionen können verschiedenen Versionen der Funktion unterschiedliche Zugriffsrechte zugewiesen werden. Sie werden weiterhin als im Gültigkeitsbereich der einschließenden Klasse betrachtet und sind somit überladene Funktionen. Betrachten Sie den folgenden Code, in dem die Memberfunktion `Deposit` überladen wird. Eine Version ist öffentlich, die andere privat.

Der Zweck dieses Beispiels ist es, eine `Account`-Klasse bereitzustellen, in der ein korrektes Kennwort erforderlich ist, um Eingaben vorzunehmen. Dies geschieht durch Überladung.

Der Aufruf `Deposit` `Account::Deposit` von in ruft die private Memberfunktion auf. Dieser Aufruf ist `Account::Deposit` korrekt, da er eine Memberfunktion ist und Zugriff auf die privaten Member der Klasse hat.

```cpp
// declaration_matching2.cpp
class Account
{
public:
   Account()
   {
   }
   double Deposit( double dAmount, char *szPassword );

private:
   double Deposit( double dAmount )
   {
      return 0.0;
   }
   int Validate( char *szPassword )
   {
      return 0;
   }

};

int main()
{
    // Allocate a new object of type Account.
    Account *pAcct = new Account;

    // Deposit $57.22. Error: calls a private function.
    // pAcct->Deposit( 57.22 );

    // Deposit $57.22 and supply a password. OK: calls a
    //  public function.
    pAcct->Deposit( 52.77, "pswd" );
}

double Account::Deposit( double dAmount, char *szPassword )
{
   if ( Validate( szPassword ) )
      return Deposit( dAmount );
   else
      return 0.0;
}
```

## <a name="see-also"></a>Siehe auch

[Funktionen (C++)](../cpp/functions-cpp.md)

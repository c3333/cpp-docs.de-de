---
title: Initialisierer
ms.date: 07/29/2019
description: Initialisieren von Klassen, Strukturen, Arrays und grundlegenden Typen in C++.
helpviewer_keywords:
- arrays [C++], array-element initializers
- aggregate initializers [C++]
ms.assetid: ce301ed8-aa1c-47b2-bb39-9f0541b4af85
ms.openlocfilehash: 98b0c07db8eb10aa47830c9926c6ebcdc3f12dcb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227438"
---
# <a name="initializers"></a>Initialisierer

Ein Initialisierer gibt den Anfangswert einer Variablen an. Sie können Variablen in diesen Kontexten initialisieren:

- In der Definition einer Variablen:

    ```cpp
    int i = 3;
    Point p1{ 1, 2 };
    ```

- Als einer der Parameter einer Funktion:

    ```cpp
    set_point(Point{ 5, 6 });
    ```

- Als Rückgabewert einer Funktion:

    ```cpp
    Point get_new_point(int x, int y) { return { x, y }; }
    Point get_new_point(int x, int y) { return Point{ x, y }; }
    ```

Initialisierer können diese Formate annehmen:

- Ein Ausdruck (oder eine durch Komma getrennte Liste von Ausdrücken) in Klammern:

    ```cpp
    Point p1(1, 2);
    ```

- Ein Gleichheitszeichen gefolgt von einem Ausdruck:

    ```cpp
    string s = "hello";
    ```

- Eine Initialisiererliste in Klammern. Die Liste kann leer sein oder aus einer Gruppe von Listen bestehen, siehe folgendes Beispiel:

    ```cpp
    struct Point{
        int x;
        int y;
    };
    class PointConsumer{
    public:
        void set_point(Point p){};
        void set_points(initializer_list<Point> my_list){};
    };
    int main() {
        PointConsumer pc{};
        pc.set_point({});
        pc.set_point({ 3, 4 });
        pc.set_points({ { 3, 4 }, { 5, 6 } });
    }
    ```

## <a name="kinds-of-initialization"></a>Arten von Initialisierung

Es gibt mehrere Arten von Initialisierung, die an unterschiedlichen Stellen in der Programmausführung auftreten können. Die verschiedenen Arten von Initialisierung schließen sich nicht gegenseitig aus. So kann z. B. eine Listeninitialisierung eine Wertinitialisierung auslösen, und in anderen Fällen kann sie eine Aggregatinitialisierung auslösen.

### <a name="zero-initialization"></a>Initialisierung mit 0 (NULL)

Die Initialisierung mit 0 (NULL) ist die Festlegung einer Variablen auf einen NULL-Wert, der implizit in den Typ konvertiert wird:

- Numerische Variablen werden mit 0 initialisiert (oder 0,0 oder 0,0000000000 usw.).

- Char-Variablen werden mit initialisiert `'\0'` .

- Zeiger werden mit initialisiert **`nullptr`** .

- Arrays, [Pod](../standard-library/is-pod-class.md) -Klassen, Strukturen und Unions werden mit einem Wert von 0 (null) initialisiert.

Die Initialisierung mit 0 (NULL) wird zu unterschiedlichen Zeiten ausgeführt:

- Bei Programmstart für alle benannten Variablen, die eine statische Dauer haben. Diese Variablen können später erneut initialisiert werden.

- Während der Wertinitialisierung für skalare Typen und POD-Klassentypen, die mit leeren geschweiften Klammern initialisiert werden.

- Für Arrays, die nur eine Teilmenge ihrer initialisierten Member haben.

Im Folgenden einige Beispiele für die Initialisierung mit 0 (NULL):

```cpp
struct my_struct{
    int i;
    char c;
};

int i0;              // zero-initialized to 0
int main() {
    static float f1;  // zero-initialized to 0.000000000
    double d{};     // zero-initialized to 0.00000000000000000
    int* ptr{};     // initialized to nullptr
    char s_array[3]{'a', 'b'};  // the third char is initialized to '\0'
    int int_array[5] = { 8, 9, 10 };  // the fourth and fifth ints are initialized to 0
    my_struct a_struct{};   // i = 0, c = '\0'
}
```

### <a name="default-initialization"></a><a name="default_initialization"></a>Standard Initialisierung

Die Standardinitialisierung für Klassen, Strukturen und Unions ist die Initialisierung mit einem Standardkonstruktor. Der Standardkonstruktor kann ohne Initialisierungs Ausdruck oder mit dem- **`new`** Schlüsselwort aufgerufen werden:

```cpp
MyClass mc1;
MyClass* mc3 = new MyClass;
```

Wenn die Klasse, Struktur oder Union über keinen Standardkonstruktor verfügt, gibt der Compiler einen Fehler aus.

Skalare Variablen werden standardmäßig initialisiert, wenn sie ohne einen Initialisierungsausdruck definiert werden. Sie haben unbestimmte Werte.

```cpp
int i1;
float f;
char c;
```

Arrays werden standardmäßig initialisiert, wenn sie ohne einen Initialisierungsausdruck definiert werden. Wenn ein Array standardmäßig initialisiert wird, werden dessen Member standardmäßig initialisiert und haben unbestimmte Werte, siehe folgendes Beispiel:

```cpp
int int_arr[3];
```

Wenn die Arraymember keinen Standardkonstruktor besitzen, gibt der Compiler einen Fehler aus.

#### <a name="default-initialization-of-constant-variables"></a>Standardinitialisierung konstanter Variablen

Konstante Variablen müssen zusammen mit einem Initialisierer deklariert werden. Wenn sie skalare Typen sind, lösen sie einen Compilerfehler aus, und wenn sie Klassentypen sind, die über einen Standardkonstruktor verfügen, lösen sie eine Warnung aus:

```cpp
class MyClass{};
int main() {
    //const int i2;   // compiler error C2734: const object must be initialized if not extern
    //const char c2;  // same error
    const MyClass mc1; // compiler error C4269: 'const automatic data initialized with compiler generated default constructor produces unreliable results
}
```

#### <a name="default-initialization-of-static-variables"></a>Standardinitialisierung statischer Variablen

Statische Variablen, die ohne einen Initialisierer deklariert werden, werden mit 0 (NULL) initialisiert (implizit in den Typ konvertiert).

```cpp
class MyClass {
private:
    int m_int;
    char m_char;
};

int main() {
    static int int1;       // 0
    static char char1;     // '\0'
    static bool bool1;   // false
    static MyClass mc1;     // {0, '\0'}
}
```

Weitere Informationen zur Initialisierung von globalen statischen Objekten finden Sie unter [Hauptfunktion und Befehlszeilenargumente](main-function-command-line-args.md).

### <a name="value-initialization"></a>Wertinitialisierung

Wertinitialisierung findet in den folgenden Fällen statt:

- Ein benannter Wert wird mit leeren geschweiften Klammern initialisiert.

- Ein anonymes temporäres Objekt wird mithilfe von leeren runden oder geschweiften Klammern initialisiert.

- ein Objekt wird mit dem- **`new`** Schlüsselwort und leeren Klammern oder geschweiften Klammern initialisiert.

Eine Wertinitialisierung führt Folgendes aus:

- Bei Klassen, die mindestens einen öffentlichen Konstruktor haben, wird der Standardkonstruktor aufgerufen.

- Bei Klassen außer Union, die keine deklarierten Konstruktoren haben, wird das Objekt mit 0 (NULL) initialisiert, und der Standardkonstruktor wird aufgerufen.

- Bei Arrays wird jedes Element wertinitialisiert.

- In allen anderen Fällen wird die Variable mit 0 (NULL) initialisiert.

```cpp
class BaseClass {
private:
    int m_int;
};

int main() {
    BaseClass bc{};     // class is initialized
    BaseClass*  bc2 = new BaseClass();  // class is initialized, m_int value is 0
    int int_arr[3]{};  // value of all members is 0
    int a{};     // value of a is 0
    double b{};  // value of b is 0.00000000000000000
}
```

### <a name="copy-initialization"></a>Kopierinitialisierung

Die Kopierinitialisierung ist die Initialisierung eines Objekts mithilfe eines anderen Objekts. Sie findet in den folgenden Fällen statt:

- Eine Variable wird mithilfe eines Gleichheitszeichens initialisiert.

- Ein Argument wird an eine Funktion übergeben.

- Ein Objekt wird von einer Funktion zurückgegeben.

- Eine Ausnahme wird ausgelöst oder abgefangen.

- Ein nicht statisches Datenmember wird mithilfe eines Gleichheitszeichens initialisiert.

- Klassen-, Struktur- und Union-Member werden anhand der Kopierinitialisierung während der Aggregatinitialisierung initialisiert. Beispiele finden Sie unter [Aggregat Initialisierung](#agginit) .

Der folgende Code zeigt mehrere Beispiele für die Kopierinitialisierung:

```cpp
#include <iostream>
using namespace std;

class MyClass{
public:
    MyClass(int myInt) {}
    void set_int(int myInt) { m_int = myInt; }
    int get_int() const { return m_int; }
private:
    int m_int = 7; // copy initialization of m_int

};
class MyException : public exception{};
int main() {
    int i = 5;              // copy initialization of i
    MyClass mc1{ i };
    MyClass mc2 = mc1;      // copy initialization of mc2 from mc1
    MyClass mc1.set_int(i);    // copy initialization of parameter from i
    int i2 = mc2.get_int(); // copy initialization of i2 from return value of get_int()

    try{
        throw MyException();
    }
    catch (MyException ex){ // copy initialization of ex
        cout << ex.what();
    }
}
```

Mit der Kopierinitialisierung können explizite Konstruktoren nicht aufgerufen werden:

```cpp
vector<int> v = 10; // the constructor is explicit; compiler error C2440: cannot convert from 'int' to 'std::vector<int,std::allocator<_Ty>>'
regex r = "a.*b"; // the constructor is explicit; same error
shared_ptr<int> sp = new int(1729); // the constructor is explicit; same error
```

In einigen Fällen, wenn auf den Kopierkonstruktor der Klasse nicht zugegriffen werden kann oder dieser gelöscht wird, verursacht die Kopierinitialisierung einen Compilerfehler.

### <a name="direct-initialization"></a>Direkte Initialisierung

Die direkte Initialisierung verwendet (nicht leere) geschweifte oder runde Klammern. Im Gegensatz zur Kopierinitialisierung können hier explizite Konstruktoren aufgerufen werden. Sie findet in den folgenden Fällen statt:

- Eine Variable wird mithilfe von nicht leeren geschweiften oder runden Klammern initialisiert.

- eine Variable wird mit dem- **`new`** Schlüsselwort und nicht leeren geschweiften Klammern oder Klammern initialisiert.

- eine Variable wird mit initialisiert.**`static_cast`**

- In einem Konstruktor werden Basisklassen und nicht statische Member mithilfe einer Initialisierungsliste initialisiert.

- In der Kopie einer erfassten Variable in einem Lambdaausdruck.

Der folgende Code zeigt einige Beispiele für die direkte Initialisierung.

```cpp
class BaseClass{
public:
    BaseClass(int n) :m_int(n){} // m_int is direct initialized
private:
    int m_int;
};

class DerivedClass : public BaseClass{
public:
    // BaseClass and m_char are direct initialized
    DerivedClass(int n, char c) : BaseClass(n), m_char(c) {}
private:
    char m_char;
};
int main(){
    BaseClass bc1(5);
    DerivedClass dc1{ 1, 'c' };
    BaseClass* bc2 = new BaseClass(7);
    BaseClass bc3 = static_cast<BaseClass>(dc1);

    int a = 1;
    function<int()> func = [a](){  return a + 1; }; // a is direct initialized
    int n = func();
}
```

### <a name="list-initialization"></a>Listeninitialisierung

Listeninitialisierung findet statt, wenn eine Variable mithilfe einer Initialisiererliste in geschweiften Klammern initialisiert wird. In geschweifte Klammern gesetzte Initialisiererlisten können in den folgenden Fällen verwendet werden:

- Eine Variable wird initialisiert.

- eine Klasse wird mit dem-Schlüsselwort initialisiert. **`new`**

- Ein Objekt wird von einer Funktion zurückgegeben.

- Ein Argument wird an eine Funktion übergeben.

- Eines der Argumente in einer direkten Initialisierung.

- In einem nicht statischen Datenmemberinitialisierer.

- In einer Konstruktorinitialisiererliste.

Der folgende Code zeigt einige Beispiele für die Listeninitialisierung:

```cpp
class MyClass {
public:
    MyClass(int myInt, char myChar) {}
private:
    int m_int[]{ 3 };
    char m_char;
};
class MyClassConsumer{
public:
    void set_class(MyClass c) {}
    MyClass get_class() { return MyClass{ 0, '\0' }; }
};
struct MyStruct{
    int my_int;
    char my_char;
    MyClass my_class;
};
int main() {
    MyClass mc1{ 1, 'a' };
    MyClass* mc2 = new MyClass{ 2, 'b' };
    MyClass mc3 = { 3, 'c' };

    MyClassConsumer mcc;
    mcc.set_class(MyClass{ 3, 'c' });
    mcc.set_class({ 4, 'd' });

    MyStruct ms1{ 1, 'a', { 2, 'b' } };
}
```

### <a name="aggregate-initialization"></a><a name="agginit"></a>Aggregat Initialisierung

Die Aggregatinitialisierung ist eine Form der Listeninitialisierung für Arrays oder Klassentypen (häufig Strukturen oder Unions), die Folgendes aufweisen:

- Keine private- oder protected-Member

- Keine von Benutzern bereitgestellten Konstruktoren, mit Ausnahme der explizit auf den Standardwert festgelegten oder gelöschten Konstruktoren

- Keine Basisklassen

- Keine virtuellen Memberfunktionen

> [!NOTE]
> <!--conformance note-->In Visual Studio 2015 und früheren Versionen ist es für ein Aggregat nicht zulässig, für nicht statische Member geschweifter Klammern oder gleichmäßige Initialisierer zu haben. Diese Einschränkung wurde im c++ 14-Standard entfernt und in Visual Studio 2017 implementiert.

Aggregatinitialisierer bestehen wie im folgenden Beispiel aus einer Initialisierungsliste in geschweiften Klammern mit oder ohne Gleichheitszeichen:

```cpp
#include <iostream>
using namespace std;

struct MyAggregate{
    int myInt;
    char myChar;
};

struct MyAggregate2{
    int myInt;
    char myChar = 'Z'; // member-initializer OK in C++14
};

int main() {
    MyAggregate agg1{ 1, 'c' };
    MyAggregate2 agg2{2};
    cout << "agg1: " << agg1.myChar << ": " << agg1.myInt << endl;
    cout << "agg2: " << agg2.myChar << ": " << agg2.myInt << endl;

    int myArr1[]{ 1, 2, 3, 4 };
    int myArr2[3] = { 5, 6, 7 };
    int myArr3[5] = { 8, 9, 10 };

    cout << "myArr1: ";
    for (int i : myArr1){
        cout << i << " ";
    }
    cout << endl;

    cout << "myArr3: ";
    for (auto const &i : myArr3) {
        cout << i << " ";
    }
    cout << endl;
}
```

Die folgende Ausgabe wird angezeigt:

```Output
agg1: c: 1
agg2: Z: 2
myArr1: 1 2 3 4
myArr3: 8 9 10 0 0
```

> [!IMPORTANT]
> Arraymember, die deklariert, aber während der Aggregat Initialisierung nicht explizit initialisiert werden, werden mit 0 (null) initialisiert, wie `myArr3` oben beschrieben.

#### <a name="initializing-unions-and-structs"></a>Initialisieren von Unions und Strukturen

Wenn eine Union über keinen Konstruktor verfügt, können Sie sie mithilfe eines einzelnen Werts initialisieren (oder mithilfe einer anderen Instanz einer Union). Der Wert wird verwendet, um das erste nicht statische Feld zu initialisieren. Dies unterscheidet sich von der Strukturinitialisierung, in der mithilfe des ersten Werts im Initialisierer das erste Feld initialisiert wird, mithilfe des zweiten Werts das zweite Feld initialisiert wird usw. Vergleichen Sie die Initialisierung von Unions und Strukturen im folgenden Beispiel:

```cpp
struct MyStruct {
    int myInt;
    char myChar;
};
union MyUnion {
    int my_int;
    char my_char;
    bool my_bool;
    MyStruct my_struct;
};

int main() {
    MyUnion mu1{ 'a' };  // my_int = 97, my_char = 'a', my_bool = true, {myInt = 97, myChar = '\0'}
    MyUnion mu2{ 1 };   // my_int = 1, my_char = 'x1', my_bool = true, {myInt = 1, myChar = '\0'}
    MyUnion mu3{};      // my_int = 0, my_char = '\0', my_bool = false, {myInt = 0, myChar = '\0'}
    MyUnion mu4 = mu3;  // my_int = 0, my_char = '\0', my_bool = false, {myInt = 0, myChar = '\0'}
    //MyUnion mu5{ 1, 'a', true };  // compiler error: C2078: too many initializers
    //MyUnion mu6 = 'a';            // compiler error: C2440: cannot convert from 'char' to 'MyUnion'
    //MyUnion mu7 = 1;              // compiler error: C2440: cannot convert from 'int' to 'MyUnion'

    MyStruct ms1{ 'a' };            // myInt = 97, myChar = '\0'
    MyStruct ms2{ 1 };              // myInt = 1, myChar = '\0'
    MyStruct ms3{};                 // myInt = 0, myChar = '\0'
    MyStruct ms4{1, 'a'};           // myInt = 1, myChar = 'a'
    MyStruct ms5 = { 2, 'b' };      // myInt = 2, myChar = 'b'
}
```

#### <a name="initializing-aggregates-that-contain-aggregates"></a>Initialisierung von Aggregaten, die Aggregate enthalten

Aggregattypen können andere Aggregattypen enthalten, z. B. Arrays von Arrays, Arrays von Strukturen usw. Diese Typen werden initialisiert, indem geschachtelte Gruppen von geschweiften Klammern verwendet werden, z. B.:

```cpp
struct MyStruct {
    int myInt;
    char myChar;
};
int main() {
    int intArr1[2][2]{{ 1, 2 }, { 3, 4 }};
    int intArr3[2][2] = {1, 2, 3, 4};
    MyStruct structArr[]{ { 1, 'a' }, { 2, 'b' }, {3, 'c'} };
}
```

### <a name="reference-initialization"></a>Verweisinitialisierung

Variablen des Referenztyps müssen mit einem Objekt des Typs, von dem der Referenztyp abgeleitet wird, oder mit einem Objekt eines Typs initialisiert werden, der in den Typ konvertiert werden kann, von dem der Referenztyp abgeleitet wird. Beispiel:

```cpp
// initializing_references.cpp
int iVar;
long lVar;
int main()
{
    long& LongRef1 = lVar;        // No conversion required.
    long& LongRef2 = iVar;        // Error C2440
    const long& LongRef3 = iVar;  // OK
    LongRef1 = 23L;               // Change lVar through a reference.
    LongRef2 = 11L;               // Change iVar through a reference.
    LongRef3 = 11L;               // Error C3892
}
```

Die einzige Möglichkeit, einen Verweis mit einem temporären Objekt zu initialisieren, besteht darin, ein konstantes temporäres Objekt zu initialisieren. Nach der Initialisierung zeigt eine Referenztypvariable immer auf das gleiche Objekt. Sie kann nicht geändert werden und auf ein anderes Objekt zeigen.

Obwohl die Syntax identisch sein kann, sind die Initialisierung von Referenztypvariablen und die Zuweisung zu Referenztypvariablen semantisch unterschiedlich. Im vorherigen Beispiel ähneln die Zuweisungen, die `iVar` und `lVar` ändern, den Initialisierungen zwar, haben jedoch unterschiedliche Auswirkungen. Die Initialisierung gibt das Objekt an, auf das die Referenztypvariable zeigt. Die Zuweisung weist über die Referenz auf das verwiesene Objekt hin.

Da beide ein Argument des Referenztyps an eine Funktion übergeben und einen Wert des Referenztyps einer Funktion zurückgeben und daher Initialisierungen sind, werden die formalen Argumente einer Funktion ebenso korrekt initialisiert wie die zurückgegebenen Verweise.

Referenztypvariablen können ohne Initialisierer nur in folgenden Objekten deklariert werden:

- Funktionsdeklarationen (Prototypen). Beispiel:

    ```cpp
    int func( int& );
    ```

- Funktionsrückgabetyp-Deklarationen. Beispiel:

    ```cpp
    int& func( int& );
    ```

- Deklaration eines Referenztypklassenmembers. Beispiel:

    ```cpp
    class c {public:   int& i;};
    ```

- Deklaration einer Variablen, die explizit als angegeben wird **`extern`** . Beispiel:

    ```cpp
    extern int& iVal;
    ```

Bei der Initialisierung einer Referenztypvariable verwendet der Compiler das Entscheidungsdiagramm, wie in der folgenden Abbildung gezeigt, um zwischen dem Erstellen eines Verweises auf ein Objekt und dem Erstellen eines temporären Objekts auszuwählen, auf das der Verweis zeigt.

![Entscheidungs Diagramm für die Initialisierung von Verweis Typen](../cpp/media/vc38s71.gif "Entscheidungs Diagramm für die Initialisierung von Verweis Typen") <br/>
Entscheidungs Diagramm für die Initialisierung von Verweis Typen

Verweise auf **`volatile`** Typen (deklariert als **`volatile`** *Typname* - <strong>&</strong> *Bezeichner*) können mit **`volatile`** Objekten desselben Typs oder mit Objekten initialisiert werden, die nicht als deklariert wurden **`volatile`** . Sie können jedoch nicht mit **`const`** Objekten dieses Typs initialisiert werden. Ebenso können Verweise auf **`const`** Typen (die als **`const`** *Typname* - <strong>&</strong> *Bezeichner*deklariert sind) mit **`const`** Objekten desselben Typs (oder mit Objekten, die eine Konvertierung in diesen Typ aufweisen, oder mit Objekten, die nicht als deklariert wurden) initialisiert werden **`const`** . Sie können jedoch nicht mit **`volatile`** Objekten dieses Typs initialisiert werden.

Verweise, die weder mit dem-Schlüsselwort noch mit dem-Schlüsselwort qualifiziert sind, **`const`** **`volatile`** können nur mit Objekten initialisiert werden, die weder als **`const`** auch **`volatile`**

### <a name="initialization-of-external-variables"></a>Initialisierung von externen Variablen

Deklarationen von automatischen, statischen und externen Variablen können Initialisierer enthalten. Deklarationen externer Variablen können jedoch nur Initialisierer enthalten, wenn die Variablen nicht als deklariert werden **`extern`** .

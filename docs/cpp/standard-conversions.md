---
title: Standardkonvertierungen
ms.date: 10/02/2019
helpviewer_keywords:
- standard conversions, categories of
- L-values [C++]
- conversions, standard
ms.assetid: ce7ac8d3-5c99-4674-8229-0672de05528d
ms.openlocfilehash: cb4960c2f981b99fbc798098357a0ac65e8ddaa6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232221"
---
# <a name="standard-conversions"></a>Standardkonvertierungen

Die Programmiersprache C++ definiert Konvertierungen zwischen ihren grundlegenden Typen. Sie definiert auch Konvertierungen für Zeiger- und Verweistypen sowie und für abgeleitete "pointer-to-member"-Typen. Diese Konvertierungen werden als *Standard Konvertierungen*bezeichnet.

In diesem Abschnitt werden die folgenden Standardkonvertierungen erläutert:

- Ganzzahlige Erweiterungen

- Integrale Konvertierungen

- Unverankerte Konvertierungen

- Unverankerte und integrale Konvertierungen

- Arithmetische Konvertierungen

- Zeigerkonvertierungen

- Verweiskonvertierungen

- Konvertierungen von Zeiger in Member

  > [!NOTE]
  > Benutzerdefinierte Typen können eigene Konvertierungen festlegen. Die Konvertierung von benutzerdefinierten Typen wird in [Konstruktoren](../cpp/constructors-cpp.md) und [Konvertierungen](../cpp/user-defined-type-conversions-cpp.md)behandelt.

Der folgende Code bewirkt Konvertierungen (in diesen Beispiel ganzzahlige Erweiterungen):

```cpp
long  long_num1, long_num2;
int   int_num;

// int_num promoted to type long prior to assignment.
long_num1 = int_num;

// int_num promoted to type long prior to multiplication.
long_num2 = int_num * long_num2;
```

Das Ergebnis einer Konvertierung ist nur dann ein l-Wert, wenn hierdurch ein Verweistyp erstellt wird. Eine benutzerdefinierte Konvertierung, die als deklariert wurde, `operator int&()` gibt z. b. einen Verweis zurück und ist ein l-Wert. Eine Konvertierung, die als deklariert wurde, `operator int()` gibt jedoch ein-Objekt zurück, und es ist kein l-Wert.

## <a name="integral-promotions"></a>Ganzzahlige Erweiterungen

Objekte eines ganzzahligen Typs können in einen anderen umfassenderen ganzzahligen Typ, d. h. einen Typ, der einen größeren Satz von Werten darstellen kann, konvertiert werden. Diese erweiternde Art der Konvertierung wird *als*ganzzahlige herauf Stufung bezeichnet. Mit der ganzzahligen herauf Stufung können Sie die folgenden Typen in einem Ausdruck verwenden, wenn ein anderer ganzzahliger Typ verwendet werden kann:

- Objekte, Literale und Konstanten des Typs **`char`** und**`short int`**

- Enumerationstypen

- **`int`** Bitfelder

- Enumeratoren

C++-Erweiterungen sind "Wert Beibehaltung", da der Wert nach der herauf Stufung garantiert mit dem Wert vor der herauf Stufung übereinstimmt. Bei Wert Beibehaltungs Aktionen werden Objekte von kürzeren ganzzahligen Typen (z. b. Bitfelder oder Objekte des Typs **`char`** ) zum Typ herauf gestuft, **`int`** Wenn **`int`** den vollständigen Bereich des ursprünglichen Typs darstellen kann. Wenn **`int`** nicht den vollständigen Bereich von Werten darstellen kann, wird das Objekt zum Typ herauf gestuft **`unsigned int`** .  Obwohl diese Strategie mit der von Standard C verwendeten Strategie identisch ist, behalten Werte erhaltende Konvertierungen die "Signatur" des Objekts nicht bei.

Wertneutrale Erweiterungen und vorzeichenneutrale Erweiterungen erzeugen normalerweise dieselben Ergebnisse. Sie können jedoch unterschiedliche Ergebnisse erzielen, wenn das herauf gestufte Objekt wie folgt aussieht:

- Ein Operand von `/` , `%` , `/=` , `%=` , `<` , `<=` , `>` oder`>=`

   Diese Operatoren benötigen Vorzeichen zum Bestimmen des Ergebnisses. Bei der Anwendung auf diese Operanden ergeben sich Werterhaltende und Signier enden Aktionen.

- Der linke Operand von `>>` oder.`>>=`

   Diese Operatoren behandeln die Mengen mit und ohne Vorzeichen bei einem Verschiebungs Vorgang unterschiedlich. Bei signierten Mengen gibt ein Right Shift-Vorgang das Signier Bit an die frei gewordenen Bitpositionen weiter, während die frei gewordenen Bitpositionen in einer nicht signierten Menge mit 0 gefüllt sind.

- Ein Argument für eine überladene Funktion oder der Operand eines überladenen Operators, der von der Signatur des Operanden Typs für die Argument Übereinstimmung abhängig ist. Weitere Informationen zum Definieren überladener Operatoren finden Sie unter [überladene Operatoren](../cpp/operator-overloading.md).

## <a name="integral-conversions"></a>Integrale Konvertierungen

*Integral Konvertierungen* sind Konvertierungen zwischen ganzzahligen Typen. Die ganzzahligen Typen sind **`char`** , **`short`** (oder **`short int`** ), **`int`** , **`long`** und **`long long`** . Diese Typen können mit oder qualifiziert **`signed`** werden **`unsigned`** und **`unsigned`** können als Kurzform für verwendet werden **`unsigned int`** .

### <a name="signed-to-unsigned"></a>Mit Vorzeichen zu ohne Vorzeichen

Objekte aus Ganzzahltypen mit Vorzeichen können in entsprechende Typen ohne Vorzeichen konvertiert werden. Wenn diese Konvertierungen auftreten, ändert sich das tatsächliche Bitmuster nicht. Die Interpretation der Daten wird jedoch geändert. Codebeispiel:

```cpp
#include <iostream>

using namespace std;
int main()
{
    short  i = -3;
    unsigned short u;

    cout << (u = i) << "\n";
}
// Output: 65533
```

Im vorherigen Beispiel **`signed short`** wird ein, `i` , definiert und mit einer negativen Zahl initialisiert. Der Ausdruck `(u = i)` bewirkt `i` , dass vor der Zuweisung zu in eine konvertiert wird **`unsigned short`** `u` .

### <a name="unsigned-to-signed"></a>Ohne Vorzeichen zu mit Vorzeichen

Objekte aus Ganzzahltypen ohne Vorzeichen können in entsprechende Typen mit Vorzeichen konvertiert werden. Liegt der Wert ohne Vorzeichen jedoch außerhalb des darstellbaren Bereichs des signierten Typs, weist das Ergebnis nicht den richtigen Wert auf, wie im folgenden Beispiel gezeigt:

```cpp
#include <iostream>

using namespace std;
int main()
{
short  i;
unsigned short u = 65533;

cout << (i = u) << "\n";
}
//Output: -3
```

Im vorherigen Beispiel ist ein ganzzahliges `u` **`unsigned short`** Objekt, das in eine signierte Menge konvertiert werden muss, um den Ausdruck auszuwerten `(i = u)` . Da der Wert nicht ordnungsgemäß in einem dargestellt werden kann **`signed short`** , werden die Daten wie gezeigt falsch interpretiert.

## <a name="floating-point-conversions"></a>Gleitkommakonvertierungen

Ein Objekt vom Gleitkommatyp kann gefahrlos in einen genaueren Gleitkommatyp konvertiert werden, d. h. die Konvertierung verursacht keinen Signifikanzverlust. Beispielsweise sind Konvertierungen von **`float`** in **`double`** oder von **`double`** in **`long double`** sicher, und der Wert ist unverändert.

Ein Objekt eines Gleit Komma Typs kann auch in einen weniger präzisen Typ konvertiert werden, wenn es sich in einem Bereich befindet, der durch diesen Typ dargestellt werden kann. (Weitere Informationen finden Sie unter [Floating Limits](../cpp/floating-limits.md) für die Bereiche von Gleit Komma Typen.) Wenn der ursprüngliche Wert nicht exakt darstellbar ist, kann er in den nächsthöheren oder den nächst niedrigeren darstellbaren Wert konvertiert werden. Das Ergebnis ist nicht definiert, wenn kein solcher Wert vorhanden ist. Betrachten Sie das folgenden Beispiel:

```cpp
cout << (float)1E300 << endl;
```

Der maximale Wert, der vom Typ dargestellt werden kann, **`float`** ist 3.402823466 E38 – eine wesentlich geringere Zahl als 1e300. Daher wird die Zahl in unendlich konvertiert, und das Ergebnis ist "inf".

## <a name="conversions-between-integral-and-floating-point-types"></a>Konvertierungen zwischen ganzzahligem Typ und Gleitkommatyp

Bestimmte Ausdrücke können bewirken, dass Objekte vom Typ "float" in Ganzzahltypen konvertiert werden oder umgekehrt. Wenn ein Objekt des ganzzahligen Typs in einen Gleit kommatyp konvertiert wird und der ursprüngliche Wert nicht exakt darstellbar ist, ist das Ergebnis entweder der nächste höhere oder der nächste niedrigere darstellbare Wert.

Wenn ein Objekt vom Gleit kommatyp in einen ganzzahligen Typ konvertiert wird, wird der Teil Bruchteil *abgeschnitten*oder in Richtung NULL gerundet. Eine Zahl wie 1,3 wird in 1 konvertiert, und-1,3 wird in-1 konvertiert. Wenn der abgeschnittene Wert höher als der höchste darstellbare Wert oder kleiner als der niedrigste darstellbare Wert ist, ist das Ergebnis nicht definiert.

## <a name="arithmetic-conversions"></a>Arithmetische Konvertierungen

Viele binäre Operatoren (unter [Ausdrücke mit binären Operatoren](../cpp/expressions-with-binary-operators.md)erläutert) verursachen Konvertierungen von Operanden und erzielen die Ergebnisse auf die gleiche Weise. Die Konvertierungen dieser Operatoren werden als *übliche arithmetische Konvertierungen*bezeichnet. Arithmetische Konvertierungen von Operanden, die unterschiedliche systemeigene Typen aufweisen, werden wie in der folgenden Tabelle dargestellt. Typedef-Typen verhalten sich entsprechend ihren zugrunde liegenden systemeigenen Typen.

### <a name="conditions-for-type-conversion"></a>Bedingungen für die Typkonvertierung

|Bedingungen erfüllt|Konvertierung|
|--------------------|----------------|
|Beide Operanden sind vom Typ **`long double`** .|Ein anderer Operand wird in den-Typ konvertiert **`long double`** .|
|Vorangehende Bedingung nicht erfüllt, und der Operand ist vom Typ **`double`** .|Ein anderer Operand wird in den-Typ konvertiert **`double`** .|
|Vorangehende Bedingungen nicht erfüllt, und der Operand ist vom Typ **`float`** .|Ein anderer Operand wird in den-Typ konvertiert **`float`** .|
|Vorausgehende Bedingungen nicht erfüllt (keiner der Operanden ist vom Typ „floating“).|Operanden erhalten ganzzahlige herauf stufungen wie folgt:<br /><br />-Wenn einer der beiden Operanden vom Typ ist **`unsigned long`** , wird der andere Operand in den Typ konvertiert **`unsigned long`** .<br />-Wenn die vorangehende Bedingung nicht erfüllt ist und einer der beiden **`long`** Operanden vom Typ und der andere vom Typ ist **`unsigned int`** , werden beide Operanden in den Typ konvertiert **`unsigned long`** .<br />: Wenn die beiden vorangehenden Bedingungen nicht erfüllt werden und ein Operand vom Typ ist **`long`** , wird der andere Operand in den Typ konvertiert **`long`** .<br />-Wenn die vorangehenden drei Bedingungen nicht erfüllt werden und ein Operand vom Typ ist **`unsigned int`** , wird der andere Operand in den Typ konvertiert **`unsigned int`** .<br />Wenn keine der vorangehenden Bedingungen erfüllt ist, werden beide Operanden in den Typ konvertiert **`int`** .|

Das folgende Codebeispiel veranschaulicht die Konvertierungsregeln, die in der Tabelle beschrieben werden:

```cpp
double dVal;
float fVal;
int iVal;
unsigned long ulVal;

int main() {
   // iVal converted to unsigned long
   // result of multiplication converted to double
   dVal = iVal * ulVal;

   // ulVal converted to float
   // result of addition converted to double
   dVal = ulVal + fVal;
}
```

Die erste Anweisung im vorangehenden Beispiel zeigt die Multiplikation von zwei ganzzahligen Typen, nämlich `iVal` und `ulVal`. Die Bedingung erfüllt ist, dass keiner der Operanden vom Typ "Floating" und ein Operand vom Typ ist **`unsigned int`** . Daher wird der andere Operand `iVal` in den Typ konvertiert **`unsigned int`** . Das Ergebnis wird dann zugewiesen `dVal` . Die hier erfüllte Bedingung besteht darin, dass ein Operand vom Typ ist **`double`** , sodass das **`unsigned int`** Ergebnis der Multiplikation in den Typ konvertiert wird **`double`** .

Die zweite Anweisung im vorangehenden Beispiel zeigt das Hinzufügen eines und eines ganzzahligen **`float`** Typs: `fVal` und `ulVal` . Die `ulVal` Variable wird **`float`** in den Typ konvertiert (dritte Bedingung in der Tabelle). Das Ergebnis der Addition wird in **`double`** den-Typ (zweite Bedingung in der Tabelle) konvertiert und zugewiesen `dVal` .

## <a name="pointer-conversions"></a>Zeigerkonvertierungen

Zeiger können bei der Zuweisung, Initialisierung, beim Vergleich und bei anderen Ausdrücken konvertiert werden.

### <a name="pointer-to-classes"></a>Zeiger auf Klassen

Es gibt zwei Fälle, in denen ein Zeiger auf eine Klasse in einen Zeiger auf eine Basisklasse konvertiert werden kann.

Der erste Fall tritt auf, wenn auf die bezeichnete Basisklasse zugegriffen werden kann und die Konvertierung eindeutig ist. Weitere Informationen zu mehrdeutigen Basisklassen verweisen finden Sie unter [mehrere Basisklassen](../cpp/multiple-base-classes.md).

Ob auf eine Basisklasse zugegriffen werden kann, hängt von der Art der Vererbung bei der Ableitung ab. Betrachten Sie die Vererbung, wie in der folgenden Abbildung veranschaulicht.

![Vererbungs Diagramm mit Basis&#45;-Klassen Barrierefreiheit](../cpp/media/vc38xa1.gif "Vererbungs Diagramm mit Basis&#45;-Klassen Barrierefreiheit") <br/>
Vererbungsdiagramm für Abbildung der Basisklasse-Barrierefreiheit

Die folgende Tabelle zeigt die Zugriffsmöglichkeiten auf die Basisklassen bei der Situation, die in der Abbildung veranschaulicht wird.

|Typ der Funktion|Ableitung|Konvertierung von<br /><br /> B * zu einem \* Recht?|
|----------------------|----------------|-------------------------------------------|
|Externe (nicht im Klassenumfang enthaltene) Funktion|Privat|Nein|
||Protected|Nein|
||Öffentlich|Ja|
|B-Memberfunktion (im B-Bereich)|Privat|Ja|
||Protected|Ja|
||Öffentlich|Ja|
|C-Memberfunktion (im C-Bereich)|Privat|Nein|
||Protected|Ja|
||Öffentlich|Ja|

Im zweiten Fall, in dem ein Zeiger auf eine Klasse in einen Zeiger auf eine Basisklasse konvertiert werden kann, wird eine explizite Typkonvertierung verwendet. Weitere Informationen zu expliziten Typkonvertierungen finden Sie unter [Operator für explizite Typkonvertierung](explicit-type-conversion-operator-parens.md).

Das Ergebnis einer solchen Konvertierung ist ein Zeiger auf das unter *geordnete*Objekt, der Teil des Objekts, der von der Basisklasse vollständig beschrieben wird.

Der folgende Code definiert zwei Klassen, `A` und `B`, wobei `B` von `A` abgeleitet ist. (Weitere Informationen zur Vererbung finden Sie unter [abgeleitete Klassen](../cpp/inheritance-cpp.md).) Anschließend definiert es `bObject` , ein Objekt vom Typ `B` und zwei Zeiger ( `pA` und `pB` ), die auf das Objekt zeigen.

```cpp
// C2039 expected
class A
{
public:
    int AComponent;
    int AMemberFunc();
};

class B : public A
{
public:
    int BComponent;
    int BMemberFunc();
};
int main()
{
   B bObject;
   A *pA = &bObject;
   B *pB = &bObject;

   pA->AMemberFunc();   // OK in class A
   pB->AMemberFunc();   // OK: inherited from class A
   pA->BMemberFunc();   // Error: not in class A
}
```

Der Zeiger `pA` ist vom Typ `A *`, der als "Zeiger auf ein Objekt vom Typ `A`" interpretiert werden kann. Member von `bObject` (z. b. `BComponent` und `BMemberFunc` ) sind für den Typ eindeutig `B` und daher über nicht zugänglich `pA` . Der `pA`-Zeiger erlaubt nur Zugriff auf die Eigenschaften (Memberfunktionen und Daten) des Objekts, die in der Klasse `A` definiert sind.

### <a name="pointer-to-function"></a>Zeiger auf Funktion

Ein Zeiger auf eine Funktion kann in den Typ konvertiert werden `void *` , wenn `void *` der Typ groß genug ist, um diesen Zeiger zu speichern.

### <a name="pointer-to-void"></a>Zeiger auf void

Zeiger auf den Typ **`void`** können in Zeiger auf einen beliebigen anderen Typ konvertiert werden, jedoch nur mit einer expliziten Typumwandlung (im Gegensatz zu C). Ein Zeiger auf einen beliebigen Typ kann implizit in einen Zeiger auf den Typ konvertiert werden **`void`** . Ein Zeiger auf ein unvollständiges Objekt eines Typs kann in einen Zeiger auf **`void`** (implizit) und zurück (explizit) konvertiert werden. Das Ergebnis einer solchen Konvertierung entspricht dem Wert des ursprünglichen Zeigers. Ein Objekt wird als unvollständig betrachtet, wenn es deklariert ist, aber es sind nicht genügend Informationen verfügbar, um seine Größe oder Basisklasse zu bestimmen.

Ein Zeiger auf ein Objekt, das nicht ist **`const`** oder **`volatile`** implizit in einen Zeiger vom Typ konvertiert werden kann `void *` .

### <a name="const-and-volatile-pointers"></a>const- und volatile-Zeiger

C++ stellt keine Standard Konvertierung von einem **`const`** **`volatile`** -Typ oder-Typ in einen Typ bereit, der nicht **`const`** oder ist **`volatile`** . Allerdings kann jede Art der Konvertierung mithilfe expliziter Typumwandlungen festgelegt werden (einschließlich unsicherer Konvertierungen).

> [!NOTE]
> C++ Zeiger auf Member, außer Zeiger auf statische Member, unterscheiden sich von normalen Zeigern und weisen nicht die gleichen Standard Konvertierungen auf. Zeiger auf statische Member sind normale Zeiger und haben die gleichen Konvertierungen wie normale Zeiger.

### <a name="null-pointer-conversions"></a>NULL-Zeigerkonvertierungen

Ein ganzzahliger konstanter Ausdruck, der NULL ergibt, oder ein solcher Ausdruck, der in einen Zeigertyp umgewandelt wird, wird in einen Zeiger konvertiert, der als *null-Zeiger*bezeichnet wird. Dieser Zeiger vergleicht immer ungleich mit einem Zeiger auf ein beliebiges gültiges Objekt oder eine gültige Funktion. Eine Ausnahme sind Zeiger auf-basierte-Objekte, die den gleichen Offset aufweisen können und weiterhin auf andere Objekte verweisen können.

In c++ 11 sollte der [nullptr](../cpp/nullptr.md) -Typ dem NULL-Zeiger im C-Stil bevorzugt werden.

### <a name="pointer-expression-conversions"></a>Zeiger-Ausdruck-Konvertierungen

Jeder Ausdruck mit einem Arraytyp kann in einen Zeiger des gleichen Typs konvertiert werden. Das Ergebnis der Konvertierung ist ein Zeiger auf das erste Arrayelement. Im folgenden Beispiel wird eine solche Konvertierung veranschaulicht:

```cpp
char szPath[_MAX_PATH]; // Array of type char.
char *pszPath = szPath; // Equals &szPath[0].
```

Ein Ausdruck, der eine Funktion ergibt, die einen bestimmten Typ zurückgibt, wird in einen Zeiger auf eine Funktion konvertiert, die diesen Typ zurückgibt, ausgenommen unter folgenden Bedingungen:

- Der Ausdruck wird als Operand für den Address-of-Operator ( **&** ) verwendet.

- Der Ausdruck wird als Operand des Funktionsaufrufoperators verwendet.

## <a name="reference-conversions"></a>Verweiskonvertierungen

In diesen Fällen kann ein Verweis auf eine Klasse in einen Verweis auf eine Basisklasse konvertiert werden:

- Auf die angegebene Basisklasse kann zugegriffen werden.

- Die Konvertierung ist eindeutig. (Weitere Informationen zu mehrdeutigen Basisklassen verweisen finden Sie unter [mehrere Basisklassen](../cpp/multiple-base-classes.md).)

Das Ergebnis der Konvertierung ist ein Zeiger auf das Unterobjekt, das die Basisklasse darstellt.

## <a name="pointer-to-member"></a>Zeiger auf Member

Zeiger auf Klassenmember können bei der Zuweisung, Initialisierung, beim Vergleich und bei anderen Ausdrücken konvertiert werden. In diesem Abschnitt werden die folgenden Konvertierungen von Zeigern in Elemente beschrieben:

### <a name="pointer-to-base-class-member"></a>Zeiger auf Basisklassenmember

Ein Zeiger auf den Member einer Basisklasse kann in einen Zeiger auf den Member einer Klasse konvertiert werden, die davon abgeleitet ist, wenn die folgenden Bedingungen erfüllt sind:

- Auf die entgegengesetzte Konvertierung von Zeigern auf eine abgeleitete Klasse in Zeiger auf eine Basisklasse kann zugegriffen werden.

- Die abgeleitete Klasse erbt nicht virtuell von der Basisklasse.

Wenn der linke Operand ein Zeiger auf einen Member ist, muss der rechte Operand vom Typ „pointer-to-member“ oder ein konstanter Ausdruck sein, der als 0 ausgewertet wird. Diese Zuweisung ist nur in den folgenden Fällen gültig:

- Der rechte Operand ist ein Zeiger auf einen Member derselben Klasse wie der linke Operand.

- Der linke Operand ist ein Zeiger auf den Member einer Klasse, die öffentlich und eindeutig von der Klasse des rechten Operanden abgeleitet wird.

### <a name="null-pointer-to-member-conversions"></a>NULL-Zeiger auf Element Konvertierungen

Ein ganzzahliger konstanter Ausdruck, der NULL ergibt, wird in einen NULL-Zeiger konvertiert. Dieser Zeiger vergleicht immer ungleich mit einem Zeiger auf ein beliebiges gültiges Objekt oder eine gültige Funktion. Eine Ausnahme sind Zeiger auf-basierte-Objekte, die den gleichen Offset aufweisen können und weiterhin auf andere Objekte verweisen können.

Der folgende Code veranschaulicht die Definition eines Zeigers auf einen Member `i` in Klasse `A`. Der Zeiger `pai` wird mit 0 initialisiert. Das ist der NULL-Zeiger.

```cpp
class A
{
public:
int i;
};

int A::*pai = 0;

int main()
{
}
```

## <a name="see-also"></a>Weitere Informationen

[C++-Sprachreferenz](../cpp/cpp-language-reference.md)

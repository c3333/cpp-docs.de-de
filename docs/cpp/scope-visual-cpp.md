---
title: Gültigkeitsbereich (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- classes [C++], scope
- scope [C++]
- function prototypes [C++], scope
- class scope
- prototype scope
- functions [C++], scope
- scope, C++ names
ms.assetid: 81fecbb0-338b-4325-8332-49f33e716352
ms.openlocfilehash: a5b5601c89991fbe1a148ebaf781fe2ad6a9dfc4
ms.sourcegitcommit: c4cf8976939dd0e13e25b82930221323ba6f15d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/12/2020
ms.locfileid: "83204135"
---
# <a name="scope-c"></a>Gültigkeitsbereich (C++)

Wenn Sie ein Programmelement deklarieren, wie z. b. eine Klasse, eine Funktion oder eine Variable, kann Ihr Name nur "sichtbar" sein und in bestimmten Teilen des Programms verwendet werden. Der Kontext, in dem ein Name sichtbar ist, wird als Gültigkeits *Bereich*bezeichnet. Wenn Sie z. b. eine Variable `x` innerhalb einer Funktion deklarieren, `x` ist nur innerhalb des Funktions Texts sichtbar. Er verfügt über einen *lokalen Bereich*. Möglicherweise haben Sie im Programm andere Variablen mit demselben Namen. solange Sie sich in unterschiedlichen Bereichen befinden, verstoßen Sie nicht gegen eine Definitions Regel, und es wird kein Fehler ausgelöst.

Für automatische nicht statische Variablen bestimmt der Bereich auch, wann Sie im Programmspeicher erstellt und zerstört werden.

Es gibt sechs Arten von Bereichen:

- **Globaler** Gültigkeitsbereich Ein globaler Name ist ein Wert, der außerhalb einer Klasse, einer Funktion oder eines Namespace deklariert wird. In C++ sind diese Namen jedoch auch mit einem impliziten globalen Namespace vorhanden. Der Bereich der globalen Namen erstreckt sich vom Zeitpunkt der Deklaration bis zum Ende der Datei, in der Sie deklariert werden. Bei globalen Namen unterliegt die Sichtbarkeit auch den Regeln der [Verknüpfung](program-and-linkage-cpp.md) , die bestimmen, ob der Name in anderen Dateien im Programm sichtbar ist.

- **Namespace Bereich** Ein Name, der innerhalb eines [Namespace](namespaces-cpp.md)außerhalb von Klassen-oder Enumerationsdefinitionen oder Funktionsblöcken deklariert wird, ist ab dem Zeitpunkt der Deklaration bis zum Ende des Namespace sichtbar. Ein Namespace kann in mehreren Blöcken über verschiedene Dateien hinweg definiert werden.

- **Lokaler Bereich** Ein in einer Funktion oder einem Lambda deklarierter Name, einschließlich der Parameternamen, verfügt über einen lokalen Gültigkeitsbereich. Sie werden häufig als "Locals" bezeichnet. Sie sind nur ab dem Zeitpunkt der Deklaration bis zum Ende der Funktion oder des Lambda-Texts sichtbar. Der lokale Gültigkeitsbereich ist eine Art von Block Bereich, der weiter unten in diesem Artikel erläutert wird.

- **Klassen Bereich** Namen von Klassenmembern verfügen über einen Klassen Bereich, der unabhängig vom Zeitpunkt der Deklaration in der Klassendefinition erweitert wird. Der Zugriff auf Klassenmember wird weiter durch die **öffentlichen**, **privaten**und **geschützten** Schlüsselwörter gesteuert. Auf öffentliche oder geschützte Member kann nur mithilfe der Member-Selection-Operatoren (zugegriffen werden **.** oder **->** ) oder Zeiger-auf-Member-Operatoren (**.** <strong>\*</strong> oder **->** <strong>\*</strong> ).

- **Anweisungs Bereich** Namen, die in einer **for**-, **if**-, **while**-oder **Switch** -Anweisung deklariert sind, sind bis zum Ende des Anweisungsblocks sichtbar.

- **Funktionsbereich** Eine [Bezeichnung](labeled-statements.md) weist einen Funktionsbereich auf, was bedeutet, dass Sie in einem Funktions Rumpf auch vor dem Zeitpunkt der Deklaration sichtbar ist. Der Funktionsbereich ermöglicht das Schreiben von-Anweisungen, wie `goto cleanup` vor dem `cleanup` Deklarieren der Bezeichnung.

## <a name="hiding-names"></a>Ausblenden von Namen

Sie können einen Namen verbergen, indem Sie ihn in einem eingeschlossenen Block deklarieren. In der folgenden Abbildung wird `i` innerhalb des inneren Blocks neu deklariert. Dadurch wird die Variable ausgeblendet, die `i` im äußeren Blockbereich zugeordnet ist.

![Ausblenden&#45;Bereichs namens ausblenden](../cpp/media/vc38sf1.png "Ausblenden&#45;Bereichs namens ausblenden") <br/>
Block Bereich und namens ausblenden

Die in der Abbildung dargestellte Ausgabe des Programms lautet wie folgt:

```cpp
i = 0
i = 7
j = 9
i = 0
```

> [!NOTE]
> Es wird angenommen, dass das `szWhat`-Argument im Funktionsbereich liegt. Daher wird es so behandelt, als wäre es im äußersten Block der Funktion deklariert worden.

## <a name="hiding-class-names"></a>Ausblenden von Klassennamen

Sie können Klassennamen ausblenden, indem Sie eine Funktion, ein Objekt, eine Variable oder einen Enumerator im gleichen Bereich deklarieren. Der Klassenname kann jedoch weiterhin aufgerufen werden, wenn die Schlüsselwort **Klasse**vorangestellt ist.

```cpp
// hiding_class_names.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

// Declare class Account at global scope.
class Account
{
public:
    Account( double InitialBalance )
        { balance = InitialBalance; }
    double GetBalance()
        { return balance; }
private:
    double balance;
};

double Account = 15.37;            // Hides class name Account

int main()
{
    class Account Checking( Account ); // Qualifies Account as
                                       //  class name

    cout << "Opening account with a balance of: "
         << Checking.GetBalance() << "\n";
}
//Output: Opening account with a balance of: 15.37
```

> [!NOTE]
> An jeder Stelle, für die der Klassenname ( `Account` ) aufgerufen wird, muss die schlüsselwortklasse verwendet werden, um Sie von dem globalen Variablen Konto unterscheiden zu können. Diese Regel gilt nicht, wenn der Klassenname auf der linken Seite des Bereichsauflösungsoperators (::) auftritt. Namen auf der linken Seite des Bereichsauflösungsoperators gelten immer als Klassennamen.

Im folgenden Beispiel wird veranschaulicht, wie ein Zeiger auf ein Objekt vom Typ `Account` mithilfe des **Class** -Schlüssel Worts deklariert wird:

```cpp
class Account *Checking = new class Account( Account );
```

Der `Account` im Initialisierer (in Klammern) in der vorangehenden Anweisung verfügt über einen globalen Gültigkeitsbereich. er ist vom Typ " **Double**".

> [!NOTE]
> Die in diesem Beispiel dargestellte Wiederverwendung von Bezeichnernamen gilt als schlechter Programmierstil.

Informationen zur Deklaration und Initialisierung von Klassen Objekten finden Sie unter [Klassen, Strukturen und Unions](../cpp/classes-and-structs-cpp.md). Weitere Informationen zum Verwenden der **New** -und **Delete** -Operatoren für freie Speicher finden Sie unter [New-und DELETE-Operatoren](new-and-delete-operators.md).

## <a name="hiding-names-with-global-scope"></a>Ausblenden von Namen mit globalem Bereich

Sie können Namen mit globalem Gültigkeitsbereich ausblenden, indem Sie den gleichen Namen explizit im Block Bereich deklarieren. Auf Namen des globalen Bereichs kann jedoch mit dem Bereichs Auflösungs Operator () zugegriffen werden `::` .

```cpp
#include <iostream>

int i = 7;   // i has global scope, outside all blocks
using namespace std;

int main( int argc, char *argv[] ) {
   int i = 5;   // i has block scope, hides i at global scope
   cout << "Block-scoped i has the value: " << i << "\n";
   cout << "Global-scoped i has the value: " << ::i << "\n";
}
```

```Output
Block-scoped i has the value: 5
Global-scoped i has the value: 7
```

## <a name="see-also"></a>Siehe auch

[Grundlegende Konzepte](../cpp/basic-concepts-cpp.md)

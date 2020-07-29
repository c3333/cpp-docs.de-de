---
title: Ausnahmen und Stapelentladung in C++
ms.date: 11/19/2019
ms.assetid: a1a57eae-5fc5-4c49-824f-3ce2eb8129ed
ms.openlocfilehash: e0dadc90f85caeea359fca4ed0b45868ea77177e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221561"
---
# <a name="exceptions-and-stack-unwinding-in-c"></a>Ausnahmen und Stapelentladung in C++

Im C++-Ausnahmemechanismus geht die Steuerung von der throw-Anweisung zur ersten catch-Anweisung, die den ausgelösten Typ behandeln kann. Wenn die Catch-Anweisung erreicht wird, werden alle automatischen Variablen im Bereich zwischen den Throw-und Catch-Anweisungen in einem Prozess zerstört, der als *Stapel Auflösung*bezeichnet wird. Bei der Stapelentladung wird die Ausführung wie folgt fortgesetzt:

1. Das Steuerelement erreicht die **`try`** Anweisung durch normale sequenzielle Ausführung. Der geschützte Abschnitt im- **`try`** Block wird ausgeführt.

1. Wenn während der Ausführung des geschützten Abschnitts keine Ausnahme ausgelöst wird, werden die Klauseln, die **`catch`** dem-Block folgen, **`try`** nicht ausgeführt. Die Ausführung wird bei der Anweisung nach der letzten Klausel fortgesetzt, die auf **`catch`** den zugeordneten- **`try`** Block folgt.

1. Wenn während der Ausführung des geschützten Abschnitts oder in einer Routine, die der geschützte Abschnitt direkt oder indirekt aufruft, eine Ausnahme ausgelöst wird, wird ein Exception-Objekt aus dem-Objekt erstellt, das vom **`throw`** -Operanden erstellt wird. (Dies impliziert, dass möglicherweise ein Kopierkonstruktor beteiligt ist.) An diesem Punkt sucht der Compiler nach einer **`catch`** Klausel in einem höheren Ausführungs Kontext, der eine Ausnahme des Typs behandeln kann, der ausgelöst wird, oder für einen **`catch`** Handler, der einen beliebigen Ausnahmetyp behandeln kann. Die **`catch`** Handler werden in der Reihenfolge ihrer Darstellung nach dem- **`try`** Block untersucht. Wenn kein entsprechender Handler gefunden wird, wird der nächste dynamisch einschließende- **`try`** Block untersucht. Dieser Prozess wird fortgesetzt, bis der äußerste einschließende **`try`** Block untersucht wird.

1. Wenn ein entsprechender Handler weiterhin nicht gefunden wird oder wenn während des Entladungsprozesses eine Ausnahme auftritt, bevor der Handler die Steuerung übernimmt, wird die vordefinierte Laufzeitfunktion `terminate` aufgerufen. Wenn eine Ausnahme auftritt, nachdem die Ausnahme ausgelöst wurde, aber bevor die Abwicklung beginnt, wird `terminate` aufgerufen.

1. Wenn ein übereinstimmender **`catch`** Handler gefunden wird und ihn als Wert abfängt, wird der formale Parameter initialisiert, indem das Ausnahme Objekt kopiert wird. Wenn er als Verweis abfängt, wird der Parameter so initialisiert, dass er auf das Ausnahmeobjekt verweist. Nachdem der formale Parameter initialisiert wurde, beginnt der Prozess der Stapelentladung. Dies umfasst die Zerstörung aller automatischen Objekte, die vollständig erstellt – aber noch nicht zerstört wurden – zwischen dem Anfang des **`try`** Blocks, der dem Handler zugeordnet ist, **`catch`** und der Throw-Site der Ausnahme. Beschädigung tritt in umgekehrter Reihenfolge der Konstruktion auf. Der **`catch`** Handler wird ausgeführt, und das Programm setzt die Ausführung nach dem letzten Handler Fort – d. h. bei der ersten Anweisung oder dem Konstrukt, bei der es sich nicht um einen **`catch`** Handler handelt. Das Steuerelement kann nur einen **`catch`** Handler über eine ausgelöste Ausnahme, nie über eine- **`goto`** Anweisung oder eine- **`case`** Bezeichnung in einer- **`switch`** Anweisung eingeben.

## <a name="stack-unwinding-example"></a>Beispiel für Stapel entwickeln

Das folgende Beispiel zeigt, wie der Stapel entladen wird, wenn eine Ausnahme ausgelöst wird. Die Ausführung auf dem Thread springt von der throw-Anweisung in `C` auf die catch-Anweisung in `main` und entlädt währenddessen jede Funktionen. Beachten Sie die Reihenfolge, in der die `Dummy`-Objekte erstellt und dann zerstört werden, wenn sie den Gültigkeitsbereich verlassen. Beachten Sie außerdem, dass keine Funktion außer `main` abgeschlossen wird, die die catch-Anweisung enthält. Funktion `A` kehrt nie von ihrem Aufruf von `B()` zurück und `B` nie von seinem Aufruf von `C()`. Wenn Sie die Definition des `Dummy`-Zeigers und die zugehörige Löschanweisung auskommentieren und das Programm dann ausführen, sehen Sie, dass der Zeiger nie gelöscht wird. Dies zeigt, was geschehen kann, wenn Funktionen keine Ausnahmegarantie bieten. Weitere Informationen finden Sie unter "How to: Design for Exceptions". Wenn Sie die catch-Anweisung auskommentieren, können Sie nachvollziehen, was geschieht, wenn ein Programm aufgrund eines Ausnahmefehlers beendet wird.

```cpp
#include <string>
#include <iostream>
using namespace std;

class MyException{};
class Dummy
{
    public:
    Dummy(string s) : MyName(s) { PrintMsg("Created Dummy:"); }
    Dummy(const Dummy& other) : MyName(other.MyName){ PrintMsg("Copy created Dummy:"); }
    ~Dummy(){ PrintMsg("Destroyed Dummy:"); }
    void PrintMsg(string s) { cout << s  << MyName <<  endl; }
    string MyName;
    int level;
};

void C(Dummy d, int i)
{
    cout << "Entering FunctionC" << endl;
    d.MyName = " C";
    throw MyException();

    cout << "Exiting FunctionC" << endl;
}

void B(Dummy d, int i)
{
    cout << "Entering FunctionB" << endl;
    d.MyName = "B";
    C(d, i + 1);
    cout << "Exiting FunctionB" << endl;
}

void A(Dummy d, int i)
{
    cout << "Entering FunctionA" << endl;
    d.MyName = " A" ;
  //  Dummy* pd = new Dummy("new Dummy"); //Not exception safe!!!
    B(d, i + 1);
 //   delete pd;
    cout << "Exiting FunctionA" << endl;
}

int main()
{
    cout << "Entering main" << endl;
    try
    {
        Dummy d(" M");
        A(d,1);
    }
    catch (MyException& e)
    {
        cout << "Caught an exception of type: " << typeid(e).name() << endl;
    }

    cout << "Exiting main." << endl;
    char c;
    cin >> c;
}

/* Output:
    Entering main
    Created Dummy: M
    Copy created Dummy: M
    Entering FunctionA
    Copy created Dummy: A
    Entering FunctionB
    Copy created Dummy: B
    Entering FunctionC
    Destroyed Dummy: C
    Destroyed Dummy: B
    Destroyed Dummy: A
    Destroyed Dummy: M
    Caught an exception of type: class MyException
    Exiting main.

*/
```

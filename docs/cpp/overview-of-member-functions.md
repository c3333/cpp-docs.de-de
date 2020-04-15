---
title: Übersicht über Memberfunktionen
ms.date: 11/04/2016
helpviewer_keywords:
- this pointer, and nonstatic member functions
- nonstatic member functions [C++]
- inline functions [C++], treating member functions as
- member functions [C++], definition in class declaration
ms.assetid: 9f77a438-500e-40bb-a6c6-544678f3f4c8
ms.openlocfilehash: 6dec4ee53cd840c47d76ac0579daca710b0eeb68
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358411"
---
# <a name="overview-of-member-functions"></a>Übersicht über Memberfunktionen

Memberfunktionen sind entweder statisch oder nicht statisch. Das Verhalten statischer Memberfunktionen unterscheidet sich von anderen Memberfunktionen, da statische Memberfunktionen **dieses** Argument nicht implizit haben. Nicht statische Memberfunktionen verfügen über einen **diesen** Zeiger. Memberfunktionen können, ob statisch oder nicht statisch, entweder inner- oder außerhalb der Klassendeklaration definiert werden.

Wenn eine Memberfunktion innerhalb einer Klassendeklaration definiert ist, wird sie als Inlinefunktion behandelt, und es ist nicht erforderlich, den Funktionsnamen mit dem Klassennamen zu qualifizieren. Obwohl Funktionen, die innerhalb von Klassendeklarationen definiert sind, bereits als Inlinefunktionen behandelt werden, können Sie das **Schlüsselwort inline** für Dokumentcode verwenden.

Ein Beispiel des Deklarierens einer Funktion innerhalb einer Klassendeklaration folgt:

```cpp
// overview_of_member_functions1.cpp
class Account
{
public:
    // Declare the member function Deposit within the declaration
    //  of class Account.
    double Deposit( double HowMuch )
    {
        balance += HowMuch;
        return balance;
    }
private:
    double balance;
};

int main()
{
}
```

Wenn sich die Definition einer Memberfunktion außerhalb der Klassendeklaration befindet, wird sie nur dann als Inlinefunktion behandelt, wenn sie explizit als **Inline**deklariert wird. Darüber hinaus muss der Funktionsname in der Definition mit dem Klassennamen mithilfe des Bereichsauflösungsoperators (`::`) qualifiziert sein.

Das folgende Beispiel ist mit der vorherigen Deklaration der Klasse `Account` identisch, mit der Ausnahme, dass die Funktion `Deposit` außerhalb der Klassendeklaration definiert ist:

```cpp
// overview_of_member_functions2.cpp
class Account
{
public:
    // Declare the member function Deposit but do not define it.
    double Deposit( double HowMuch );
private:
    double balance;
};

inline double Account::Deposit( double HowMuch )
{
    balance += HowMuch;
    return balance;
}

int main()
{
}
```

> [!NOTE]
> Obwohl Memberfunktionen entweder innerhalb einer Klassendeklaration definiert werden können oder getrennt, können keine Memberfunktionen einer Klasse hinzugefügt werden, nachdem die Klasse definiert ist.

Die Klassen, die Memberfunktionen enthalten, können viele Deklarationen haben, aber die Memberfunktionen selbst dürfen nur eine Definition in einem Programm haben. Mehrfache Definitionen verursachen zur Verknüpfungszeit eine Fehlermeldung. Wenn eine Klasse Inlinefunktionsdefinitionen enthält, müssen die Funktionsdefinitionen identisch sein, um dieser ODR (one definition rule) zu entsprechen.

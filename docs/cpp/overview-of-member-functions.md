---
title: Übersicht über Memberfunktionen
ms.date: 11/04/2016
helpviewer_keywords:
- this pointer, and nonstatic member functions
- nonstatic member functions [C++]
- inline functions [C++], treating member functions as
- member functions [C++], definition in class declaration
ms.assetid: 9f77a438-500e-40bb-a6c6-544678f3f4c8
ms.openlocfilehash: 81fc3ae7a732171c6bddff9f584976dd747372b4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233664"
---
# <a name="overview-of-member-functions"></a>Übersicht über Memberfunktionen

Memberfunktionen sind entweder statisch oder nicht statisch. Das Verhalten statischer Element Funktionen unterscheidet sich von anderen Element Funktionen, da statische Member-Funktionen kein implizites **`this`** Argument aufweisen. Nicht statische Member-Funktionen verfügen über einen- **`this`** Zeiger. Memberfunktionen können, ob statisch oder nicht statisch, entweder inner- oder außerhalb der Klassendeklaration definiert werden.

Wenn eine Memberfunktion innerhalb einer Klassendeklaration definiert ist, wird sie als Inlinefunktion behandelt, und es ist nicht erforderlich, den Funktionsnamen mit dem Klassennamen zu qualifizieren. Obwohl innerhalb von Klassen Deklarationen definierte Funktionen bereits als Inline Funktionen behandelt werden, können Sie das- **`inline`** Schlüsselwort verwenden, um Code zu dokumentieren.

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

Wenn die Definition einer Element Funktion außerhalb der Klassen Deklaration liegt, wird Sie nur dann als Inline Funktion behandelt, wenn Sie explizit als deklariert wird **`inline`** . Darüber hinaus muss der Funktionsname in der Definition mit dem Klassennamen mithilfe des Bereichsauflösungsoperators (`::`) qualifiziert sein.

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

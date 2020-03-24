---
title: Abstrakte Klassen (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- classes [C++], abstract
- base classes [C++], abstract classes [C++]
- abstract classes [C++]
- derived classes [C++], abstract classes [C++]
ms.assetid: f0c5975b-39de-4d68-9640-6ce57f4632e6
ms.openlocfilehash: 2ea9d3765f65434cb738c2b7c53f9499bba24545
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181693"
---
# <a name="abstract-classes-c"></a>Abstrakte Klassen (C++)

Abstrakte Klassen fungieren als Ausdrücke allgemeiner Konzepte, von denen spezifischere Klassen abgeleitet werden können. Sie können kein Objekt vom Typ einer abstrakten Klasse erstellen. Sie können jedoch Zeiger und Verweise auf Typen einer abstrakten Klasse verwenden.

Eine Klasse, die mindestens eine rein virtuelle Funktion enthält, wird als abstrakte Klasse angesehen. Klassen, die von der abstrakten Klasse abgeleitet sind, müssen die rein virtuelle Funktion implementieren, um nicht selbst als abstrakte Klasse angesehen zu werden.

Sehen Sie sich das in [Virtual Functions](../cpp/virtual-functions.md)gezeigte Beispiel an. Mit der `Account`-Klasse soll eine allgemeine Funktionalität gewährleistet werden, aber Objekte vom Typ `Account` sind zu allgemein, um von Nutzen zu sein. Daher ist `Account` ein guter Kandidat für eine abstrakte Klasse:

```cpp
// deriv_AbstractClasses.cpp
// compile with: /LD
class Account {
public:
   Account( double d );   // Constructor.
   virtual double GetBalance();   // Obtain balance.
   virtual void PrintBalance() = 0;   // Pure virtual function.
private:
    double _balance;
};
```

Diese Deklaration unterscheidet sich von der vorherigen einzig darin, dass `PrintBalance` mit dem reinen Bezeichner (`= 0`) deklariert wird.

## <a name="restrictions-on-abstract-classes"></a>Einschränkungen für abstrakte Klassen

Abstrakte Klassen können nicht verwendet werden für:

- Variablen oder Memberdaten

- Argumenttypen

- Funktionsrückgabetypen

- Typen expliziter Konvertierungen

Eine weitere Einschränkung ist, dass, wenn der Konstruktor für eine abstrakte Klasse eine rein virtuelle Funktion entweder direkt oder indirekt aufruft, das Ergebnis nicht definiert ist. Allerdings können Konstruktoren und Destruktoren für abstrakte Klassen andere Memberfunktionen aufrufen.

Rein virtuelle Funktionen können für abstrakte Klassen definiert werden, sie können aber nur mithilfe folgender Syntax direkt aufgerufen werden:

*abstract-class-Name*::*Function-Name*()

Dies ist hilfreich beim Entwerfen von Klassenhierarchien, deren Basisklasse()n rein virtuelle Destruktoren enthält/enthalten, da Basisklassendestruktoren immer beim Zerstören eines Objekts aufgerufen werden. Betrachten Sie das folgenden Beispiel:

```cpp
// Declare an abstract base class with a pure virtual destructor.
// deriv_RestrictionsonUsingAbstractClasses.cpp
class base {
public:
    base() {}
    virtual ~base()=0;
};

// Provide a definition for destructor.
base::~base() {}

class derived:public base {
public:
    derived() {}
    ~derived(){}
};

int main() {
    derived *pDerived = new derived;
    delete pDerived;
}
```

Wenn das Objekt, auf das `pDerived` zeigt, gelöscht wird, wird der Destruktor für die `derived`-Klasse aufgerufen, und dann wird der Destruktor für die `base`-Klasse aufgerufen. Die leere Implementierung für die rein virtuelle Funktion gewährleistet, dass zumindest eine gewisse Implementierung für die Funktion vorhanden ist.

> [!NOTE]
> Im vorherigen Beispiel wird die rein virtuelle Funktion `base::~base` implizit von `derived::~derived` aufgerufen. Es ist auch möglich, rein virtuelle Funktionen explizit mithilfe eines vollqualifizierten Memberfunktionsnamens aufzurufen.

## <a name="see-also"></a>Weitere Informationen

[Vererbung](../cpp/inheritance-cpp.md)

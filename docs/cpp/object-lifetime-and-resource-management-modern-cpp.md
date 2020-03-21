---
title: Objektlebenszeit und Ressourcenverwaltung (RAII)
description: Befolgen Sie das Prinzip von RAII in C++ modern, um Ressourcen Lecks zu vermeiden.
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 8aa0e1a1-e04d-46b1-acca-1d548490700f
ms.openlocfilehash: d30b5296b35bec7f8949057becfaeeea61ef09a0
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078031"
---
# <a name="object-lifetime-and-resource-management-raii"></a>Objektlebenszeit und Ressourcenverwaltung (RAII)

Im Gegensatz zu verwalteten C++ Sprachen hat keine automatischen *Garbage Collection*. Dabei handelt es sich um einen internen Prozess, der Heap Speicher und andere Ressourcen beim Ausführen eines Programms freigibt. Ein C++ Programm ist dafür verantwortlich, alle erworbenen Ressourcen an das Betriebssystem zurückzugeben. Eine nicht verwendete Ressource kann nicht freigegeben werden *.* Kompromittierte Ressourcen sind für andere Programme erst verfügbar, wenn der Prozess beendet wird. Insbesondere Speicher Verluste sind eine häufige Ursache für Fehler bei der Programmierung im C-Stil.

Modern C++ vermeidet das Verwenden von Heap Arbeitsspeicher so weit wie möglich, indem Objekte im Stapel deklariert werden. Wenn eine Ressource zu groß für den Stapel ist, sollte Sie einem Objekt *gehören* . Wenn das Objekt initialisiert wird, erhält es die Ressource, die es besitzt. Das Objekt ist dann dafür verantwortlich, die Ressource im Dekonstruktor freizugeben. Das besitzende Objekt selbst wird auf dem Stapel deklariert. Das Prinzip, dass *Objektressourcen Ressourcen* auch als "Ressourcen Erwerb ist Initialisierung" oder RAII bezeichnet werden.

Wenn ein Ressourcen Besitz Endes Stapel Objekt den Gültigkeitsbereich verlässt, wird sein Dekonstruktor automatisch aufgerufen. Auf diese Weise ist Garbage Collection in C++ eng mit der Objekt Lebensdauer verknüpft und ist deterministisch. Eine Ressource wird immer an einem bekannten Punkt im Programm freigegeben, den Sie steuern können. Nur deterministische deformen wie solche in C++ können Arbeitsspeicher-und nicht-Arbeitsspeicher Ressourcen gleichermaßen verarbeiten.

Das folgende Beispiel zeigt ein einfaches-Objekt `w`. Sie wird auf dem Stapel im Funktionsbereich deklariert und am Ende des Funktions Blocks zerstört. Das Objekt `w` das keine *Ressourcen* besitzt (z. b. von Heap zugewiesener Arbeitsspeicher). Der einzige Element `g` ist selbst auf dem Stapel deklariert und verlässt den Gültigkeitsbereich einfach mit `w`. Im `widget` Dekonstruktor ist kein spezieller Code erforderlich.

```cpp
class widget {
private:
    gadget g;   // lifetime automatically tied to enclosing object
public:
    void draw();
};

void functionUsingWidget () {
    widget w;   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.g gadget member
    // ...
    w.draw();
    // ...
} // automatic destruction and deallocation for w and w.g
  // automatic exception safety,
  // as if "finally { w.dispose(); w.g.dispose(); }"
```

Im folgenden Beispiel besitzt `w` eine Speicher Ressource und muss daher über Code in seinem Dekonstruktor verfügen, um den Arbeitsspeicher zu löschen.

```cpp
class widget
{
private:
    int* data;
public:
    widget(const int size) { data = new int[size]; } // acquire
    ~widget() { delete[] data; } // release
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                        // constructs w, including the w.data member
    w.do_something();

} // automatic destruction and deallocation for w and w.data

```

Seit c++ 11 gibt es eine bessere Möglichkeit, das vorherige Beispiel zu schreiben: mithilfe eines intelligenten Zeigers aus der Standardbibliothek. Der intelligente Zeiger übernimmt die Zuordnung und Löschung des Arbeitsspeichers, den er besitzt. Durch die Verwendung eines intelligenten Zeigers entfällt die Notwendigkeit eines expliziten Dekonstruktors in der `widget`-Klasse.

```cpp
#include <memory>
class widget
{
private:
    std::unique_ptr<int> data;
public:
    widget(const int size) { data = std::make_unique<int>(size); }
    void do_something() {}
};

void functionUsingWidget() {
    widget w(1000000);   // lifetime automatically tied to enclosing scope
                // constructs w, including the w.data gadget member
    // ...
    w.do_something();
    // ...
} // automatic destruction and deallocation for w and w.data

```

Durch die Verwendung intelligenter Zeiger für die Speicher Belegung können Sie das Potenzial von Speicher Verlusten vermeiden. Dieses Modell funktioniert für andere Ressourcen, z. b. Datei Handles oder Sockets. Sie können Ihre eigenen Ressourcen auf ähnliche Weise in ihren-Klassen verwalten. Weitere Informationen finden Sie unter [intelligente Zeiger](smart-pointers-modern-cpp.md).

Der Entwurf von C++ stellt sicher, dass Objekte zerstört werden, wenn Sie den Gültigkeitsbereich verlassen. Das heißt, Sie werden zerstört, da Blöcke in umgekehrter Reihenfolge der Konstruktion beendet werden. Wenn ein Objekt zerstört wird, werden seine Basen und Member in einer bestimmten Reihenfolge zerstört. Objekte, die außerhalb eines Blocks im globalen Gültigkeitsbereich deklariert werden, können zu Problemen führen. Es kann schwierig sein, zu debuggen, wenn der Konstruktor eines globalen Objekts eine Ausnahme auslöst.

## <a name="see-also"></a>Weitere Informationen

[Willkommen zurück beiC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++-Programmiersprachenreferenz](../cpp/cpp-language-reference.md)<br/>
[C++-Standardbibliothek](../standard-library/cpp-standard-library-reference.md)

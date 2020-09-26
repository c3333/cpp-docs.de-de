---
title: Willkommen zurück bei C++ (Modern C++)
description: Hier werden die neuen Programmierausdrücke in modernem C++ und deren Zweck erläutert.
ms.date: 05/17/2020
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 05c1fe80086e5b98d3f8a9c66c6759fddab39fa0
ms.sourcegitcommit: d9c94dcabd94537e304be0261b3263c2071b437b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "91353050"
---
# <a name="welcome-back-to-c---modern-c"></a>Willkommen zurück bei C++ (Modern C++)

C++ ist zu einer der am häufigsten verwendeten Programmiersprachen der Welt geworden. Gut geschriebene C++-Programme sind schnell und effizient. Die Sprache ist flexibler als andere Sprachen: Sie kann auf den höchsten Abstraktionsebenen und auf Chipebene verwendet werden. C++ bietet hochgradig optimierte Standardbibliotheken. Die Sprache ermöglicht den Zugriff auf spezifische Hardwarefeatures, sodass die Geschwindigkeit maximiert und die Arbeitsspeicheranforderung minimiert werden kann. Mithilfe von C++ können Sie verschiedenste Apps entwickeln: Spiele, Gerätetreiber leistungsstarke wissenschaftliche Software, eingebettete Programme, Windows-Client-Apps und sogar Bibliotheken und Compiler für andere Programmiersprachen.

Eine der ursprünglichen Anforderungen für C++ war Abwärtskompatibilität mit der Programmiersprache C. Deshalb hat C++ schon immer die C-Programmierkonventionen mit unformatierten Zeigern, Arrays, auf NULL endende Zeichenfolgen und andere Features zugelassen. Diese können zwar eine herausragende Leistung ermöglichen, aber auch zu Fehlern und Komplexität führen. Bei der Weiterentwicklung von C++ standen Features im Vordergrund, durch die erheblich weniger C-Ausdrücke verwendet werden mussten. Die altbekannten C-Features sind nach Bedarf verfügbar, doch in modernem C++-Code sind diese immer weniger erforderlich. Moderner C++-Code ist einfacher, sicherer, eleganter und immer noch so schnell wie gewohnt.

In den folgenden Abschnitte finden Sie eine Übersicht über die Features in modernem C++. Sofern nicht anders angegeben, sind die hier aufgeführten Features in C++ 11 und höher verfügbar. Im Microsoft-C++-Compiler können Sie in der Compileroption [`/std`](../build/reference/std-specify-language-standard-version.md) festlegen, welche Version des Standards für Ihr Projekt verwendet werden soll.

## <a name="resources-and-smart-pointers"></a>Ressourcen und intelligente Zeiger

Eine der häufigsten Fehlerkategorien bei der C-Programmierung ist der *Arbeitsspeicherverlust*. Diese Verluste werden häufig verursacht, weil **`delete`** nicht für Arbeitsspeicher aufgerufen werden kann, der mit **`new`** zugewiesen wurde. Beim modernen C++ rückt das Prinzip *Ressourcenbelegung ist Initialisierung (Resource Acquisition is Initialization, RAII)* in den Vordergrund. Die Idee ist einfach: Der *Ressourcenbesitz* (Heaparbeitsspeicher, Dateihandles, Sockets usw.) sollte bei einem Objekt liegen. Dieses Objekt erstellt bzw. empfängt die neu zugeordnete Ressource im Konstruktor und löscht sie in ihrem Dekonstruktor. Das RAII-Prinzip garantiert, dass alle Ressourcen ordnungsgemäß zum Betriebssystem zurückgegeben werden, wenn das Besitzerobjekt den Gültigkeitsbereich verlässt.

Die C++-Standardbibliothek enthält drei intelligente Zeigertypen, um die Anwendung des RAII-Prinzips zu erleichtern: [`std::unique_ptr`](../standard-library/unique-ptr-class.md), [`std::shared_ptr`](../standard-library/shared-ptr-class.md) und [`std::weak_ptr`](../standard-library/weak-ptr-class.md). Ein intelligenter Zeiger übernimmt die Zuordnung und Löschung des Arbeitsspeichers, den er besitzt. Im folgenden Beispiel sehen Sie eine Klasse mit einem Arrayelement, die dem Heap im Aufruf von `make_unique()` zugeordnet wird. Die Aufrufe von **`new`** und **`delete`** werden von der `unique_ptr`-Klasse gekapselt. Wenn ein `widget`-Objekt den Gültigkeitsbereich verlässt, wird der unique_ptr-Dekonstruktor aufgerufen. Dieser gibt den Arbeitsspeicher frei, der für das Array reserviert wurde.  

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

Verwenden Sie nach Möglichkeit einen intelligenten Zeiger, wenn Sie Heaparbeitsspeicher zuordnen. Wenn Sie die Operatoren new und delete explizit verwenden müssen, befolgen Sie das RAII-Prinzip. Weitere Informationen finden Sie unter [Objektlebenszeit und Ressourcenverwaltung (RAII)](object-lifetime-and-resource-management-modern-cpp.md).

## <a name="stdstring-and-stdstring_view"></a>`std::string` und `std::string_view`

C-Zeichenfolgen sind eine weitere häufige Fehlerquelle. Mithilfe von [`std::string` und `std::wstring`](../standard-library/basic-string-class.md) können Sie praktisch alle Fehler beseitigen, die mit C-Zeichenfolgen in Zusammenhang stehen. Außerdem können Sie die Vorteile von Memberfunktionen für Such-, Anfüge-, Voranstellvorgänge und weitere Vorgänge nutzen. Beide sind für die Geschwindigkeit optimiert. Wenn Sie eine Zeichenfolge an eine Funktion übergeben, die nur schreibgeschützten Zugriff zulässt, können Sie in C++ 17 [`std::string_view`](../standard-library/basic-string-view-class.md) verwenden, um die Leistung weiter zu verbessern.

## <a name="stdvector-and-other-standard-library-containers"></a>`std::vector` und andere Container der C++-Standardbibliothek

Sämtliche Container der Standardbibliothek befolgen das RAII-Prinzip. Sie stellen Iteratoren für den sicheren Durchlauf von Elementen bereit. Zudem sind sie für Leistung optimiert und wurden gründlich auf Richtigkeit getestet. Wenn Sie diese Container verwenden, reduzieren Sie die Wahrscheinlichkeit, dass Fehler oder Ineffizienzen in benutzerdefinierten Datenstrukturen eingeführt werden. Verwenden Sie [`vector`](../standard-library/vector-class.md) anstelle von unformatierten Arrays als sequenziellen Container in C++.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Verwenden Sie [`map`](../standard-library/map-class.md) (nicht `unordered_map`) als assoziativen Standardcontainer. Verwenden Sie [`set`](../standard-library/set-class.md), [`multimap`](../standard-library/multimap-class.md) und [`multiset`](../standard-library/multiset-class.md) für degenerierte Fälle und Mehrfachfälle.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Wenn eine Leistungsoptimierung erforderlich ist, erwägen Sie folgende Verwendungen:

- Den Typ [`array`](../standard-library/array-class-stl.md), wenn das Einbetten wichtig ist – beispielsweise als Klassenmember

- Unsortierte assoziative Container wie [`unordered_map`](../standard-library/unordered-map-class.md) – diese erzeugen weniger Aufwand pro Element und führen stetig Lookupvorgänge durch, aber es ist schwieriger, sie korrekt und effizient zu verwenden.

- Ein sortiertes `vector`-Element – Weitere Informationen finden Sie unter [Algorithmen](../standard-library/algorithms.md).

Verwenden Sie keine C-Arrays. Verwenden Sie für ältere APIs, die direkten Zugriff auf die Daten benötigen, stattdessen Zugriffsmethoden wie `f(vec.data(), vec.size());`. Weitere Informationen zu Containern finden Sie unter [C++-Standardbibliothekcontainer](../standard-library/stl-containers.md).

## <a name="standard-library-algorithms"></a>Algorithmen der Standardbibliothek

Sie sollten sich die [Algorithmen](../standard-library/algorithm.md) in der C++-Standardbibliothek ansehen, bevor Sie einen benutzerdefinierten Algorithmus für Ihr Programm schreiben. Die Standardbibliothek enthält einen stetig wachsenden Bestand an Algorithmen für viele gängige Vorgänge wie das Suchen, Sortieren, Filtern und Randomisieren. Die mathematische Bibliothek ist umfangreich. Ab C++ 17 werden parallele Versionen von vielen Algorithmen bereitgestellt.

Im Folgenden sind einige wichtige Beispiele aufgeführt:

- `for_each`, der Standarddurchlaufalgorithmus (zusammen mit bereichsbasierten `for`-Schleifen)

- `transform` für indirekte Änderungen von Containerelementen

- `find_if`, der Standardsuchalgorithmus

- `sort`, `lower_bound` und weitere Standardsortier- und -suchalgorithmen

Verwenden Sie zum Schreiben eines Vergleichsoperators den strikten **`<`** -Operator und nach Möglichkeit *benannte Lambdaausdrücke*.

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>`auto` anstelle von expliziten Typnamen

In C++ 11 wurde das [`auto`](auto-cpp.md)-Schlüsselwort für die Verwendung in Variablen-, Funktions- und Vorlagendeklarationen eingeführt. **`auto`** weist den Compiler an, den Typ des Objekts abzuleiten, damit Sie ihn nicht explizit eingeben müssen. **`auto`** ist besonders nützlich, wenn der abgeleitete Typ eine geschachtelte Vorlage ist:

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>Bereichsbasierte `for`-Schleifen

C-Iterationen für Arrays und Container sind für Indizierungsfehler anfällig und mühsam einzugeben. Sie können bereichsbasierte **`for`** -Schleifen mit Containern der Standardbibliothek und unformatierten Arrays verwenden, um diese Fehler zu vermeiden und Ihren Code lesbarer zu gestalten. Weitere Informationen finden Sie unter [Bereichsbasierte `for`-Anweisung](../cpp/range-based-for-statement-cpp.md).

```cpp
#include <iostream>
#include <vector>

int main()
{
    std::vector<int> v {1,2,3};

    // C-style
    for(int i = 0; i < v.size(); ++i)
    {
        std::cout << v[i];
    }

    // Modern C++:
    for(auto& num : v)
    {
        std::cout << num;
    }
}
```

## <a name="constexpr-expressions-instead-of-macros"></a>`constexpr`-Ausdrücke anstelle von Makros

Makros entsprechen in C und C++ Tokens, die vom Präprozessor vor der Kompilierung verarbeitet werden. Jede Instanz eines Makrotokens wird durch den definierten Wert oder Ausdruck ersetzt, bevor die Datei kompiliert wird. Makros werden bei der C-Programmierung häufig verwendet, um konstante Werte für die Kompilierzeit zu definieren. Makros sind jedoch fehleranfällig und schwer zu debuggen. In modernem C++ sollten Sie [`constexpr`](constexpr-cpp.md)-Variablen für Kompilierzeitkonstanten bevorzugen:

```cpp
#define SIZE 10 // C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>Einheitliche Initialisierung

In modernem C++ können Sie die Initialisierung mit geschweiften Klammern für jeden Typ verwenden. Diese Form der Initialisierung ist besonders praktisch, wenn Arrays, Vektoren oder andere Container initialisiert werden. Im folgenden Beispiel wird `v2` mit drei Instanzen von `S` initialisiert. `v3` wird mit drei Instanzen von `S` initialisiert, die selbst mit geschweiften Klammern initialisiert werden. Der Compiler leitet den Typ jedes Elements auf Grundlage des deklarierten Typs von `v3` ab.

```cpp
#include <vector>

struct S
{
    std::string name;
    float num;
    S(std::string s, float f) : name(s), num(f) {}
};

int main()
{
    // C-style initialization
    std::vector<S> v;
    S s1("Norah", 2.7);
    S s2("Frank", 3.5);
    S s3("Jeri", 85.9);

    v.push_back(s1);
    v.push_back(s2);
    v.push_back(s3);

    // Modern C++:
    std::vector<S> v2 {s1, s2, s3};

    // or...
    std::vector<S> v3{ {"Norah", 2.7}, {"Frank", 3.5}, {"Jeri", 85.9} };

}
```

Weitere Informationen finden Sie unter [Initialisierung mit geschweiften Klammern](initializing-classes-and-structs-without-constructors-cpp.md).

## <a name="move-semantics"></a>Verschiebesemantik

Modernes C++ enthält eine *Verschiebesemantik*, sodass unnötige Arbeitsspeicherkopien vermieden werden können. In früheren Versionen der Sprache waren Kopien in bestimmten Situationen unvermeidlich. Ein *Verschiebevorgang* überträgt den Besitz einer Ressource von einem Objekt zum nächsten, ohne eine Kopie zu erstellen. Einige Klassen besitzen Ressourcen wie Heaparbeitsspeicher oder Dateihandles. Wenn Sie eine ressourcenbesitzende Klasse implementieren, können Sie einen *Verschiebungskonstruktor* und einen *Verschiebungszuweisungsoperator* definieren. Der Compiler wählt diese speziellen Member bei der Überladungsauflösung in Situationen aus, in denen keine Kopie benötigt wird. Die Containertypen der Standardbibliothek rufen den Verschiebungskonstruktor für Objekte auf, wenn dieser definiert ist. Weitere Informationen finden Sie unter [Verschiebungskonstruktoren und Verschiebungszuweisungsoperatoren (C++)](move-constructors-and-move-assignment-operators-cpp.md).

## <a name="lambda-expressions"></a>Lambdaausdrücke

Bei der C-Programmierung kann eine Funktion mithilfe eines *Funktionszeigers* an eine andere Funktion übergeben werden. Funktionszeiger sind unpraktisch zu verwalten und nachzuvollziehen. Die Funktion, auf die sie verweisen, kann an anderer Stelle im Quellcode definiert werden – weit entfernt von der Stelle, an der sie aufgerufen wird. Außerdem sind sie nicht typsicher. Modernes C++ bietet *Funktionsobjekte*, bei denen es sich um Klassen handelt, die den [`operator()`](function-call-operator-parens.md)-Operator überschreiben, sodass sie wie eine Funktion aufgerufen werden können. Funktionsobjekte können am einfachsten mithilfe von [Inline-Lambdaausdrücken](../cpp/lambda-expressions-in-cpp.md) erstellt werden. Im folgenden Beispiel wird veranschaulicht, wie ein Lambdaausdruck verwendet wird, um ein Funktionsobjekt zu übergeben, das die `for_each`-Funktion für jedes Element im Vektor aufruft:

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

Der Lambdaausdruck `[=](int i) { return i > x && i < y; }` kann als Funktion verstanden werden, die ein einzelnes Argument vom Typ **`int`** annimmt und einen booleschen Wert zurückgibt, der angibt, ob das Argument größer als `x` und kleiner als `y` ist. Beachten Sie, dass die Variablen `x` und `y` aus dem umgebenden Kontext im Lambdaausdruck verwendet werden können. Dabei gibt `[=]` an, dass diese Variablen *nach Wert erfasst* werden. Der Lambdaausdruck enthält also eigene Kopien dieser Variablen.

## <a name="exceptions"></a>Ausnahmen

Bei modernem C++ werden verstärkt Ausnahmen anstelle von Fehlercodes verwendet, um Fehlerzustände zu melden und zu behandeln. Weitere Informationen finden Sie unter [Modernes C++: Best Practices für Ausnahmen und Fehlerbehandlung](errors-and-exception-handling-modern-cpp.md).

## `std::atomic`

Verwenden Sie die Struktur [`std::atomic`](../standard-library/atomic-structure.md) der C++-Standardbibliothek und ähnliche Typen für die Kommunikation zwischen Threads.

## <a name="stdvariant-c17"></a>`std::variant` (C++ 17)

Unions werden häufig bei der C-Programmierung verwendet, um Arbeitsspeicher zu sparen, indem die Member verschiedener Typen die gleiche Arbeitsspeicheradresse belegen können. Allerdings sind Unions nicht typsicher und anfällig für Programmierfehler. In C++ 17 werden [`std::variant`](../standard-library/variant-class.md)-Klassen als stabilere und sicherere Alternative zu Unions eingeführt. Die [`std::visit`](../standard-library/variant-functions.md#visit)-Funktion kann verwendet werden, um typsicher auf die Member eines `variant`-Typs zuzugreifen.

## <a name="see-also"></a>Siehe auch

[C++ Language Reference (C++-Programmiersprachenreferenz)](../cpp/cpp-language-reference.md)\
[Lambda-Ausdrücke](../cpp/lambda-expressions-in-cpp.md)\
[C++-Standardbibliothek](../standard-library/cpp-standard-library-reference.md)\
[Microsoft C++-Sprachkonformität: Tabelle](../overview/visual-cpp-language-conformance.md)

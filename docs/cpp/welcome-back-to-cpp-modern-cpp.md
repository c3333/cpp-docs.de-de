---
title: Willkommen zurück bei C++ - Modern C++
description: Beschreibt die neuen Programmieridiome in Modern C++ und deren Begründung.
ms.date: 01/10/2020
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 7d0fcb623162713b845107bbf00669af7ae5ca98
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369496"
---
# <a name="welcome-back-to-c---modern-c"></a>Willkommen zurück bei C++ - Modern C++

Seit seiner Gründung hat sich C++ zu einer der am häufigsten verwendeten Programmiersprachen der Welt entwickelt. Gut geschriebene C++-Programme sind schnell und effizient. Die Sprache ist flexibler als andere Sprachen: Sie kann auf den höchsten Abstraktionsebenen und auf der Ebene des Siliziums funktionieren. C++ bietet hochoptimierte Standardbibliotheken. Es ermöglicht den Zugriff auf Low-Level-Hardware-Funktionen, um die Geschwindigkeit zu maximieren und den Speicherbedarf zu minimieren. Mit C++ können Sie eine Vielzahl von Apps erstellen. Spiele, Gerätetreiber und leistungsstarke wissenschaftliche Software. Eingebettete Programme. Windows-Client-Apps. Sogar Bibliotheken und Compiler für andere Programmiersprachen werden in C++ geschrieben.

Eine der ursprünglichen Anforderungen für C++ war Abwärtskompatibilität mit der Programmiersprache C. Daher hat C++ immer die Programmierung im C-Stil mit unformatierten Zeigern, Arrays, null-terminierten Zeichenfolgen und anderen Features zugelassen. Sie können eine großartige Leistung ermöglichen, aber auch Fehler und Komplexität hervorbringen. Die Entwicklung von C++ hat Features hervorgehoben, die die Notwendigkeit, Idiome im C-Stil zu verwenden, erheblich reduzieren. Die alten C-Programmierfunktionen sind vorhanden, wenn Sie sie brauchen, aber mit modernem C++-Code sollten Sie sie immer weniger benötigen. Moderner C++-Code ist einfacher, sicherer, eleganter und immer noch so schnell wie eh und je.

Die folgenden Abschnitte geben einen Überblick über die Hauptmerkmale des modernen C++. Sofern nicht anders angegeben, sind die hier aufgeführten Funktionen in C++11 und höher verfügbar. Im Microsoft C++-Compiler können Sie die Compileroption [/std](../build/reference/std-specify-language-standard-version.md) festlegen, um anzugeben, welche Version des Standards für Ihr Projekt verwendet werden soll.

## <a name="resources-and-smart-pointers"></a>Ressourcen und intelligente Zeiger

Eine der wichtigsten Klassen von Fehlern in der C-Stil-Programmierung ist das *Speicherleck*. Lecks werden häufig durch einen Fehler beim Aufrufen von **Löschvorgängen** für Speicher verursacht, der mit **neuen**zugewiesen wurde. Moderne C++ betont das Prinzip der *Ressourcenerfassung ist Initialisierung* (RAII). Die Idee ist einfach. Ressourcen (Heapspeicher, Dateihandles, Sockets usw.) sollten *im Besitz* eines Objekts sein. Dieses Objekt erstellt oder empfängt die neu zugewiesene Ressource in seinem Konstruktor und löscht sie in ihrem Destruktor. Das RAII-Prinzip garantiert, dass alle Ressourcen ordnungsgemäß an das Betriebssystem zurückgegeben werden, wenn das besitzende Objekt den Gültigkeitsbereich verlässt.

Um die einfache Übernahme der RAII-Prinzipien zu unterstützen, bietet die C++-Standardbibliothek drei intelligente Zeigertypen: [std::unique_ptr](../standard-library/unique-ptr-class.md), [std::shared_ptr](../standard-library/shared-ptr-class.md)und [std::weak_ptr](../standard-library/weak-ptr-class.md). Ein intelligenter Zeiger verarbeitet die Zuweisung und Löschung des Speichers, den er besitzt. Das folgende Beispiel zeigt eine Klasse mit einem Arraymember, `make_unique()`der auf dem Heap im Aufruf von zugeordnet ist. Die Aufrufe zu **new** und **delete** werden `unique_ptr` von der Klasse gekapselt. Wenn `widget` ein Objekt den Gültigkeitsbereich verlässt, wird der unique_ptr Destruktor aufgerufen, und es gibt den Speicher frei, der für das Array reserviert wurde.  

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

Verwenden Sie nach Möglichkeit einen intelligenten Zeiger, wenn Heapspeicher zugewiesen wird. Wenn Sie die neuen und löschen Operatoren explizit verwenden müssen, folgen Sie dem Prinzip von RAII. Weitere Informationen finden Sie unter [Objektlebensdauer und Ressourcenverwaltung (RAII)](object-lifetime-and-resource-management-modern-cpp.md).

## <a name="stdstring-and-stdstring_view"></a>std::string und std::string_view

Zeichenfolgen im C-Stil sind eine weitere Wichtige Quelle für Fehler. Mit [std::string und std::wstring](../standard-library/basic-string-class.md)können Sie praktisch alle Fehler beseitigen, die mit Zeichenfolgen im C-Stil verbunden sind. Sie profitieren auch von Memberfunktionen zum Suchen, Anfügen, Vorstehen usw. Beide sind hochgradig auf Geschwindigkeit optimiert. Wenn Sie eine Zeichenfolge an eine Funktion übergeben, die nur schreibgeschützten Zugriff erfordert, können Sie in C++17 [std::string_view](../standard-library/basic-string-view-class.md) verwenden, um einen noch größeren Leistungsvorteil zu erzielen.

## <a name="stdvector-and-other-standard-library-containers"></a>std::vector und andere Standardbibliothekscontainer

Die Standard Library Container folgen alle dem Prinzip von RAII. Sie bieten Iteratoren für die sichere Durchquerung von Elementen. Und sie sind stark leistungsoptimiert und wurden gründlich auf Korrektheit getestet. Durch die Verwendung dieser Container eliminieren Sie das Potenzial für Fehler oder Ineffizienzen, die in benutzerdefinierten Datenstrukturen eingeführt werden können. Anstelle von Raw-Arrays verwenden Sie [vector](../standard-library/vector-class.md) als sequenzieller Container in C++.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Verwenden [map](../standard-library/map-class.md) Sie `unordered_map`Map (nicht ) als standardmäßigen assoziativen Container. Verwenden Sie [set](../standard-library/set-class.md), [multimap](../standard-library/multimap-class.md)und [multiset](../standard-library/multiset-class.md) für degenerierte und mehrfache Fälle.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Wenn eine Leistungsoptimierung erforderlich ist, erwägen Sie folgende Verwendungen:

- Der [Arraytyp](../standard-library/array-class-stl.md) beim Einbetten ist wichtig, z. B. als Klassenmember.

- Ungeordnete assoziative Container wie [unordered_map](../standard-library/unordered-map-class.md). Diese haben einen geringeren Overhead pro Element und eine konstante Suche, können jedoch schwieriger und effizient verwendet werden.

- Sortiert `vector`. Weitere Informationen finden Sie unter [Algorithmen](../cpp/algorithms-modern-cpp.md).

Verwenden Sie keine Arrays im C-Stil. Verwenden Sie für ältere APIs, die direkten Zugriff `f(vec.data(), vec.size());` auf die Daten benötigen, stattdessen Accessormethoden. Weitere Informationen zu Containern finden Sie unter [C++ StandardBibliothekscontainer](../standard-library/stl-containers.md).

## <a name="standard-library-algorithms"></a>Standardbibliotheksalgorithmen

Bevor Sie davon ausgehen, dass Sie einen benutzerdefinierten Algorithmus für Ihr Programm schreiben müssen, überprüfen Sie zuerst die C++ [Standardlibrary-Algorithmen](../standard-library/algorithm.md). Die Standardbibliothek enthält eine ständig wachsende Auswahl an Algorithmen für viele gängige Vorgänge wie Suchen, Sortieren, Filtern und Randomisieren. Die Mathebibliothek ist umfangreich. Ab C++17 werden parallele Versionen vieler Algorithmen bereitgestellt.

Im Folgenden sind einige wichtige Beispiele aufgeführt:

- **for_each**der Standard-Traversalalgorithmus (zusammen mit bereichsbasierten Schleifen).

- **transform**, für die nicht-in-Ort-Änderung von Containerelementen

- **find_if**der Standardsuchalgorithmus.

- **sort**, **lower_bound**und die anderen Standard-Sortier- und Suchalgorithmen.

Um einen Komparator zu **<** schreiben, verwenden Sie streng und verwenden Sie, wenn Sie können, *den Namen Lambdas.*

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>Auto statt expliziter Typnamen

C++11 hat das [Schlüsselwort auto](auto-cpp.md) für die Verwendung in Variablen-, Funktions- und Vorlagendeklarationen eingeführt. **auto** weist den Compiler an, den Typ des Objekts abzuleiten, damit Sie es nicht explizit eingeben müssen. **auto** ist besonders nützlich, wenn es sich bei dem abgeleiteten Typ um eine geschachtelte Vorlage handelt:

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>Bereichsbasierte For-Schleifen

Die Iteration im C-Stil über Arrays und Container ist anfällig für Indizierungsfehler und auch mühsam typisiert. Um diese Fehler zu beseitigen und den Code lesbarer zu machen, verwenden Sie bereichsbasierte Schleifen mit Standardbibliothekscontainern und Raw-Arrays. Weitere Informationen finden Sie unter [Bereichsbasiert für Anweisung](../cpp/range-based-for-statement-cpp.md).

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

## <a name="constexpr-expressions-instead-of-macros"></a>constexpr-Ausdrücke statt Makros

Makros in C und C++ sind Token, die vom Präprozessor vor der Kompilierung verarbeitet werden. Jede Instanz eines Makrotokens wird durch ihren definierten Wert oder Ausdruck ersetzt, bevor die Datei kompiliert wird. Makros werden häufig in der Programmierung im C-Stil verwendet, um konstante Werte für die Kompilierungszeit zu definieren. Makros sind jedoch fehleranfällig und schwer zu debuggen. In modernen C++ sollten Sie [constexpr-Variablen](constexpr-cpp.md) für Kompilierungszeitkonstanten bevorzugen:

```cpp
#define SIZE 10 // C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>Einheitliche Initialisierung

In modernen C++ können Sie die Geschweifkontoinitialisierung für jeden Typ verwenden. Diese Form der Initialisierung ist besonders praktisch beim Initialisieren von Arrays, Vektoren oder anderen Containern. Im folgenden Beispiel `v2` wird mit drei `S`Instanzen von initialisiert. `v3`wird mit drei Instanzen initialisiert, von `S` denen sie selbst mithilfe von geschweiften Klammern initialisiert werden. Der Compiler leitet den Typ jedes Elements basierend `v3`auf dem deklarierten Typ von ab.

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

Weitere Informationen finden Sie unter [Brace Initialisierung](initializing-classes-and-structs-without-constructors-cpp.md).

## <a name="move-semantics"></a>Verschieben der Semantik

Moderne C++ bietet *Bewegungssemantik*, die es ermöglicht, unnötige Speicherkopien zu vermeiden. In früheren Versionen der Sprache waren Kopien in bestimmten Situationen unvermeidbar. Ein *Verschiebungsvorgang* überträgt den Besitz einer Ressource von einem Objekt auf das nächste, ohne eine Kopie zu erstellen. Beim Implementieren einer Klasse, die eine Ressource besitzt (z. B. Heapspeicher, Dateihandles usw.), können Sie einen *Verschiebungskonstruktor* und einen *Verschiebungszuweisungsoperator* dafür definieren. Der Compiler wählt diese speziellen Member während der Überlastauflösung in Situationen aus, in denen keine Kopie benötigt wird. Die Containertypen der Standardbibliothek rufen den Verschiebungskonstruktor für Objekte auf, sofern einer definiert ist. Weitere Informationen finden Sie unter Verschieben von [Konstruktoren und Verschieben von Zuweisungsoperatoren (C++)](move-constructors-and-move-assignment-operators-cpp.md).

## <a name="lambda-expressions"></a>Lambdaausdrücke

In der Programmierung im C-Stil kann eine Funktion mithilfe eines *Funktionszeigers*an eine andere Funktion übergeben werden. Funktionszeiger sind unbequem zu pflegen und zu verstehen. Die Funktion, auf die sie sich beziehen, kann an anderer Stelle im Quellcode definiert werden, weit entfernt von dem Punkt, an dem sie aufgerufen wird. Außerdem sind sie nicht typsicher. Modernes C++ stellt *Funktionsobjekte*bereit, Klassen, die den [Operator ()](function-call-operator-parens.md) überschreiben, wodurch sie wie eine Funktion aufgerufen werden können. Die bequemste Möglichkeit zum Erstellen von Funktionsobjekten ist mit [Inline-Lambdaausdrücken](../cpp/lambda-expressions-in-cpp.md). Das folgende Beispiel zeigt, wie ein Lambda-Ausdruck verwendet `for_each` wird, um ein Funktionsobjekt zu übergeben, dass die Funktion für jedes Element im Vektor aufgerufen wird:

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

Der `[=](int i) { return i > x && i < y; }` Lambda-Ausdruck kann als "Funktion gelesen werden, die ein einzelnes Argument des Typs `int` annimmt und ein boolesches Argument zurückgibt, das angibt, ob das Argument größer als `x` und kleiner als `y`ist." Beachten Sie, `x` `y` dass die Variablen und aus dem umgebenden Kontext im Lambda verwendet werden können. Der `[=]` gibt an, dass diese Variablen nach Wert *erfasst* werden. Mit anderen Worten, der Lambda-Ausdruck hat seine eigenen Kopien dieser Werte.

## <a name="exceptions"></a>Ausnahmen

Moderne S++ betont Ausnahmen anstelle von Fehlercodes als die beste Möglichkeit, Fehlerbedingungen zu melden und zu behandeln. Weitere Informationen finden Sie unter [Bewährte Methoden für moderne C++-Methoden für Ausnahmen und Fehlerbehandlung](errors-and-exception-handling-modern-cpp.md).

## <a name="stdatomic"></a>std::atomare

Verwenden Sie die C++-Standardbibliothek [std::atomic](../standard-library/atomic-structure.md) struct und verwandte Typen für Interthread-Kommunikationsmechanismen.

## <a name="stdvariant-c17"></a>std::Variante (C++17)

Unions werden häufig in der Programmierung im C-Stil verwendet, um Speicher zu sparen, indem Member verschiedener Typen den gleichen Speicherort belegen können. Unions sind jedoch nicht typsicher und anfällig für Programmierfehler. C++17 führt die [std::variant-Klasse](../standard-library/variant-class.md) als robustere und sicherere Alternative zu Gewerkschaften ein. Die [Funktion std::visit](../standard-library/variant-functions.md#visit) kann verwendet werden, `variant` um auf typsichere Weise auf die Member eines Typs zuzugreifen.

## <a name="see-also"></a>Siehe auch

[C++-Sprachreferenz](../cpp/cpp-language-reference.md)\
[Lambda-Ausdrücke](../cpp/lambda-expressions-in-cpp.md)\
[C++-Standardbibliothek](../standard-library/cpp-standard-library-reference.md)\
[Microsoft C++-Sprachkonformität: Tabelle](../overview/visual-cpp-language-conformance.md)

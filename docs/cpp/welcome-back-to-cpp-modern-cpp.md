---
title: Willkommen zurück bei C++-modern C++
description: Beschreibt die neuen Programmier Ausdrücke in modernen C++ und deren Begründung.
ms.date: 05/17/2020
ms.topic: conceptual
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
ms.openlocfilehash: 76ac17e71368cdeee669b98505778838ef0dfee7
ms.sourcegitcommit: d4da3693f83a24f840e320e35c24a4a07cae68e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/18/2020
ms.locfileid: "83550796"
---
# <a name="welcome-back-to-c---modern-c"></a>Willkommen zurück bei C++-modern C++

Seit seiner Erstellung ist C++ zu einer der am häufigsten verwendeten Programmiersprachen in der Welt geworden. Gut geschriebene C++-Programme sind schnell und effizient. Die Sprache ist flexibler als andere Sprachen: Sie kann auf der höchsten Abstraktions Ebene und auf der Ebene des Silicon verwendet werden. C++ bietet hochgradig optimierte Standardbibliotheken. Sie ermöglicht den Zugriff auf Low-Level-Hardware Features, um die Geschwindigkeit zu maximieren und Arbeitsspeicher Anforderungen zu minimieren Mit C++ können Sie eine große Bandbreite von apps erstellen. Spiele, Gerätetreiber und leistungsstarke wissenschaftliche Software. Eingebettete Programme. Windows-Client-apps. Auch Bibliotheken und Compiler für andere Programmiersprachen werden in C++ geschrieben.

Eine der ursprünglichen Anforderungen für C++ war Abwärtskompatibilität mit der Programmiersprache C. Daher hat C++ stets die Programmierung im C-Stil mit unformatierten Zeigern, Arrays, auf NULL endenden Zeichen folgen und anderen Features gestattet. Sie können eine hohe Leistung ermöglichen, aber auch Fehler und Komplexität erzeugen. Die Entwicklung von C++ hat hervorgehobene Funktionen hervorgehoben, die die Notwendigkeit der Verwendung von Idioms im C-Stil erheblich verringern. Die alten Funktionen für die C-Programmierung sind vorhanden, wenn Sie Sie benötigen, aber mit modernem C++-Code sollten Sie diese weniger und weniger benötigen. Moderner C++-Code ist einfacher, sicherer, eleganter und immer noch so schnell wie je zuvor.

Die folgenden Abschnitte bieten einen Überblick über die wichtigsten Features von modern C++. Sofern nicht anders angegeben, sind die hier aufgeführten Funktionen in c++ 11 und höher verfügbar. Im Microsoft C++-Compiler können Sie die- [`/std`](../build/reference/std-specify-language-standard-version.md) Compileroption festlegen, um anzugeben, welche Version des Standards für das Projekt verwendet werden soll.

## <a name="resources-and-smart-pointers"></a>Ressourcen und intelligente Zeiger

Eine der Hauptklassen von Fehlern bei der Programmierung im C-Stil ist der *Speicher*Fehler. Verluste werden häufig durch einen Fehler beim Abrufen von Arbeits **`delete`** Speicher verursacht, der mit zugeordnet wurde **`new`** . Modern C++ betont das Prinzip der *Ressourcenbeschaffung ist Initialisierung* (RAII). Die Idee ist einfach. Ressourcen (Heap Speicher, Datei Handles, Sockets usw.) sollten *im Besitz* eines Objekts sein. Dieses Objekt erstellt bzw. empfängt die neu zugeordnete Ressource im Konstruktor und löscht sie in Ihrem Dekonstruktor. Das Prinzip von RAII stellt sicher, dass alle Ressourcen ordnungsgemäß an das Betriebssystem zurückgegeben werden, wenn das besitzende Objekt den Gültigkeitsbereich verlässt.

Zur Unterstützung der einfachen Übernahme von RAII-Prinzipien bietet die C++-Standard Bibliothek drei Typen von intelligenten Zeigern: [`std::unique_ptr`](../standard-library/unique-ptr-class.md) , [`std::shared_ptr`](../standard-library/shared-ptr-class.md) und [`std::weak_ptr`](../standard-library/weak-ptr-class.md) . Ein intelligenter Zeiger übernimmt die Zuordnung und Löschung des Arbeitsspeichers, den er besitzt. Das folgende Beispiel zeigt eine-Klasse mit einem Array Element, das im-aufrufswert auf dem Heap zugeordnet wird `make_unique()` . Die Aufrufe **`new`** von und **`delete`** werden von der-Klasse gekapselt `unique_ptr` . Wenn ein- `widget` Objekt den Gültigkeitsbereich verlässt, wird der unique_ptr Dekonstruktor aufgerufen und gibt den Arbeitsspeicher frei, der für das Array reserviert wurde.  

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

Verwenden Sie nach Möglichkeit einen intelligenten Zeiger, wenn Sie Heap Speicher zuordnen. Wenn Sie die Operatoren "New" und "Delete" explizit verwenden müssen, befolgen Sie das Prinzip von RAII. Weitere Informationen finden Sie unter [Objekt Lebensdauer und Ressourcenverwaltung (RAII)](object-lifetime-and-resource-management-modern-cpp.md).

## <a name="stdstring-and-stdstring_view"></a>`std::string` und `std::string_view`

Zeichen folgen im C-Stil sind eine weitere wichtige Quelle für Fehler. Mithilfe von [ `std::string` und `std::wstring` ](../standard-library/basic-string-class.md)können Sie praktisch alle Fehler vermeiden, die mit Zeichen folgen im C-Stil verknüpft sind. Außerdem profitieren Sie von den Vorteilen der Element Funktionen zum Suchen, anfügen, voranstellen usw. Beide sind für die Geschwindigkeit stark optimiert. Wenn Sie eine Zeichenfolge an eine Funktion übergeben, die nur schreibgeschützten Zugriff erfordert, können Sie in c++ 17 einen [`std::string_view`](../standard-library/basic-string-view-class.md) noch größeren Leistungsvorteil nutzen.

## <a name="stdvector-and-other-standard-library-containers"></a>`std::vector`und andere Standard Bibliotheks Container

Die Standard Bibliotheks Container befolgen alle das Prinzip von RAII. Sie stellen Iteratoren für den sicheren Durchlauf von Elementen bereit. Und Sie sind stark für die Leistung optimiert und wurden gründlich auf Richtigkeit getestet. Wenn Sie diese Container verwenden, vermeiden Sie das Potenzial von Fehlern oder Ineffizienzen, die in benutzerdefinierten Datenstrukturen eingeführt werden könnten. Verwenden Sie anstelle von unformatierten Arrays [`vector`](../standard-library/vector-class.md) als sequenziellen Container in C++.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Verwenden Sie [`map`](../standard-library/map-class.md) (nicht `unordered_map` ) als standardmäßigen assoziativen Container. Verwenden Sie [`set`](../standard-library/set-class.md) , [`multimap`](../standard-library/multimap-class.md) und [`multiset`](../standard-library/multiset-class.md) für degenerierte und mehrere Fälle.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Wenn eine Leistungsoptimierung erforderlich ist, erwägen Sie folgende Verwendungen:

- Der [`array`](../standard-library/array-class-stl.md) Typ beim Einbetten ist wichtig, z. b. als Klassenmember.

- Ungeordnete assoziative Container, z [`unordered_map`](../standard-library/unordered-map-class.md) . b.. Diese verfügen über einen niedrigeren pro-Element-Aufwand und eine Konstante Zeit Suche, Sie können jedoch schwieriger und effizient verwendet werden.

- Sortiert `vector` . Weitere Informationen finden Sie unter [Algorithmen](../cpp/algorithms-modern-cpp.md).

Verwenden Sie keine Arrays im C-Stil. Für ältere APIs, die direkten Zugriff auf die Daten benötigen, verwenden Sie stattdessen Accessormethoden wie z `f(vec.data(), vec.size());` . b.. Weitere Informationen zu Containern finden Sie unter [C++-Standard Bibliotheks Container](../standard-library/stl-containers.md).

## <a name="standard-library-algorithms"></a>Algorithmen der Standard Bibliothek

Bevor Sie davon ausgehen, dass Sie einen benutzerdefinierten Algorithmus für Ihr Programm schreiben müssen, überprüfen Sie zunächst die [Algorithmen](../standard-library/algorithm.md)der C++-Standard Bibliothek. Die Standard Bibliothek enthält ein ständig wachsendes Spektrum an Algorithmen für viele gängige Vorgänge wie das suchen, sortieren, Filtern und randomialisieren. Die mathematische Bibliothek ist umfangreich. Ab c++ 17 werden parallele Versionen von vielen Algorithmen bereitgestellt.

Im Folgenden sind einige wichtige Beispiele aufgeführt:

- `for_each`, der standardmäßige Traversale-Algorithmus (zusammen mit Bereichs basierten `for` Schleifen).

- `transform`, für nicht direkte Änderungen von Container Elementen

- `find_if`, der Standard Suchalgorithmus.

- `sort`, `lower_bound` und die anderen standardmäßigen Sortier-und Suchalgorithmen.

Verwenden Sie zum Schreiben eines Comparators Strict, **`<`** und verwenden Sie *benannte Lambdas* , wenn dies möglich ist.

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="auto-instead-of-explicit-type-names"></a>`auto`anstelle von expliziten Typnamen

C++ 11 hat das [`auto`](auto-cpp.md) Schlüsselwort für die Verwendung in Variablen-, Funktions-und Vorlagen Deklarationen eingeführt. **`auto`** weist den Compiler an, den Typ des Objekts abzuleiten, damit Sie ihn nicht explizit eingeben müssen. **`auto`** ist besonders nützlich, wenn der dedulierte Typ eine in einer Vorlage vorgenommene Vorlage ist:

```cpp
map<int,list<string>>::iterator i = m.begin(); // C-style
auto i = m.begin(); // modern C++
```

## <a name="range-based-for-loops"></a>Bereichs basierte `for` Schleifen

Die Iterationen im C-Stil für Arrays und Container sind anfällig für das Indizieren von Fehlern und auch mühsam. Um diese Fehler zu vermeiden und den Code lesbarer zu machen, verwenden Sie Bereichs basierte `for` Schleifen mit Standard Bibliotheks Containern und unformatierten Arrays. Weitere Informationen finden Sie unter [Bereichs basierte `for` Anweisung](../cpp/range-based-for-statement-cpp.md).

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

## <a name="constexpr-expressions-instead-of-macros"></a>`constexpr`Ausdrücke anstelle von Makros

Makros in C und C++ sind Token, die vom Präprozessor vor der Kompilierung verarbeitet werden. Jede Instanz eines Makro Tokens wird durch den definierten Wert oder Ausdruck ersetzt, bevor die Datei kompiliert wird. Makros werden häufig bei der Programmierung im C-Stil verwendet, um konstante Werte für die Kompilierzeit zu definieren. Makros sind jedoch fehleranfällig und schwer zu debuggen. In modernen C++ sollten Sie [`constexpr`](constexpr-cpp.md) Variablen für Kompilierzeit Konstanten bevorzugen:

```cpp
#define SIZE 10 // C-style
constexpr int size = 10; // modern C++
```

### <a name="uniform-initialization"></a>Einheitliche Initialisierung

In modern C++ können Sie die Initialisierung von Klammern für beliebige Typen verwenden. Diese Form der Initialisierung ist besonders praktisch, wenn Arrays, Vektoren oder andere Container initialisiert werden. Im folgenden Beispiel `v2` wird mit drei Instanzen von initialisiert `S` . `v3`wird mit drei Instanzen von initialisiert `S` , die selbst mit geschweiften Klammern initialisiert werden. Der Compiler leitet den Typ jedes Elements auf der Grundlage des deklarierten Typs von ab `v3` .

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

Weitere Informationen finden Sie unter geschweifter [Klammer Initialisierung](initializing-classes-and-structs-without-constructors-cpp.md).

## <a name="move-semantics"></a>Verschieben der Semantik

Modern C++ bietet Verschiebungs *Semantik*, sodass unnötige Speicher Kopien vermieden werden können. In früheren Versionen der Sprache waren Kopien in bestimmten Situationen unvermeidlich. Ein *Verschiebungs Vorgang überträgt* den Besitz einer Ressource von einem Objekt zum nächsten, ohne eine Kopie zu erstellen. Einige Klassen besitzen Ressourcen wie Heap Speicher, Datei Handles usw. Wenn Sie eine Ressourcen besitzende Klasse implementieren, können Sie einen *bewegungskonstruktor* und Verschiebungs *Zuweisungs Operator* dafür definieren. Der Compiler wählt diese speziellen Member bei der Überladungs Auflösung in Situationen aus, in denen eine Kopie nicht benötigt wird. Die Containertypen der Standard Bibliothek rufen den bewegungskonstruktor für Objekte auf, wenn eine definiert ist. Weitere Informationen finden Sie unter [bewegungskonstruktoren und Bewegungs Zuweisungs Operatoren (C++)](move-constructors-and-move-assignment-operators-cpp.md).

## <a name="lambda-expressions"></a>Lambdaausdrücke

Bei der Programmierung im C-Stil kann eine Funktion mithilfe eines *Funktions Zeigers*an eine andere Funktion übermittelt werden. Funktionszeiger sind unpraktisch für die Wartung und das Verständnis. Die Funktion, auf die Sie verweisen, kann an anderer Stelle im Quellcode definiert werden, und zwar weit entfernt von dem Zeitpunkt, an dem Sie aufgerufen wird. Außerdem sind Sie nicht typsicher. Modern C++ bietet *Funktions Objekte*, Klassen, die den- [`operator()`](function-call-operator-parens.md) Operator überschreiben, sodass Sie wie eine Funktion aufgerufen werden können. Die einfachste Möglichkeit zum Erstellen von Funktions Objekten ist die Verwendung von Inline- [Lambda-Ausdrücken](../cpp/lambda-expressions-in-cpp.md). Im folgenden Beispiel wird gezeigt, wie ein Lambda-Ausdruck verwendet wird, um ein Funktions Objekt zu übergeben, das die `for_each` Funktion für jedes Element im Vektor aufruft:

```cpp
    std::vector<int> v {1,2,3,4,5};
    int x = 2;
    int y = 4;
    auto result = find_if(begin(v), end(v), [=](int i) { return i > x && i < y; });
```

Der Lambda `[=](int i) { return i > x && i < y; }` -Ausdruck kann als "Funktion gelesen werden, die ein einzelnes Argument vom Typ annimmt `int` und einen booleschen Wert zurückgibt, der angibt, ob das Argument größer als `x` und kleiner als ist `y` ." Beachten Sie, dass die Variablen `x` und `y` aus dem umgebenden Kontext im Lambda-Ausdruck verwendet werden können. Der `[=]` gibt an, dass diese Variablen nach Wert *aufgezeichnet* werden, d. h., der Lambda Ausdruck hat seine eigenen Kopien dieser Werte.

## <a name="exceptions"></a>Ausnahmen

Modern C++ unterstreicht Ausnahmen anstelle von Fehlercodes als beste Methode zum melden und behandeln von Fehlerbedingungen. Weitere Informationen finden Sie unter [modern C++ bewährte Methoden für Ausnahmen und Fehlerbehandlung](errors-and-exception-handling-modern-cpp.md).

## `std::atomic`

Verwenden Sie die Struktur der C++-Standard Bibliothek [`std::atomic`](../standard-library/atomic-structure.md) und verwandte Typen für Kommunikationsmechanismen zwischen Threads.

## <a name="stdvariant-c17"></a>`std::variant`(C++ 17)

Unions werden häufig bei der Programmierung im C-Stil verwendet, um Speicherplatz zu sparen, indem die Mitglieder verschiedener Typen die gleiche Speicheradresse belegen können. Allerdings sind Unions nicht typsicher und anfällig für Programmierfehler. C++ 17 stellt die [`std::variant`](../standard-library/variant-class.md) -Klasse als stabilere und sicherere Alternative zu Unions dar. Die- [`std::visit`](../standard-library/variant-functions.md#visit) Funktion kann verwendet werden, um auf typsichere Weise auf die Member eines `variant` Typs zuzugreifen.

## <a name="see-also"></a>Weitere Informationen

[C++-Sprachreferenz](../cpp/cpp-language-reference.md)\
[Lambda-Ausdrücke](../cpp/lambda-expressions-in-cpp.md)\
[C++-Standard Bibliothek](../standard-library/cpp-standard-library-reference.md)\
[Microsoft C++-Sprachkonformität: Tabelle](../overview/visual-cpp-language-conformance.md)

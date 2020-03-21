---
title: Deklarationen und DefinitionenC++()
ms.date: 12/12/2019
ms.assetid: 678f1424-e12f-45e0-a957-8169e5fef6cb
ms.openlocfilehash: 7aa9e07a471ed5a32ecc8f13690f1a1bf08b655f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077208"
---
# <a name="declarations-and-definitions-c"></a>Deklarationen und DefinitionenC++()

Ein C++ Programm besteht aus verschiedenen Entitäten, z. b. Variablen, Funktionen, Typen und Namespaces. Jede dieser Entitäten muss *deklariert* werden, bevor Sie verwendet werden können. Eine-Deklaration gibt einen eindeutigen Namen für die Entität an, zusammen mit Informationen über ihren Typ und andere Merkmale. An C++ dem Punkt, an dem ein Name deklariert wird, ist der Punkt, an dem er für den Compiler sichtbar wird. Sie können nicht auf eine Funktion oder Klasse verweisen, die zu einem späteren Zeitpunkt in der Kompilierungseinheit deklariert wird. Variablen sollten vor dem Zeitpunkt, an dem Sie verwendet werden, so nah wie möglich sein.

Das folgende Beispiel zeigt einige Deklarationen:

```cpp
#include <string>

void f(); // forward declaration

int main()
{
    const double pi = 3.14; //OK
    int i = f(2); //OK. f is forward-declared
    std::string str; // OK std::string is declared in <string> header
    C obj; // error! C not yet declared.
    j = 0; // error! No type specified.
    auto k = 0; // OK. type inferred as int by compiler.
}

int f(int i)
{
    return i + 42;
}

namespace N {
   class C{/*...*/};
}
```

In Zeile 5 wird die `main`-Funktion deklariert. In Zeile 7 **wird eine Konstante** Variable mit dem Namen `pi` deklariert und *Initialisiert*. In Zeile 8 wird ein Integer-`i` deklariert und mit dem Wert initialisiert, der von der Funktion `f`erzeugt wird. Der Name `f` der für den Compiler aufgrund der *Vorwärts Deklaration* in Zeile 3 sichtbar ist.

In Zeile 9 wird eine Variable mit dem Namen `obj` vom Typ `C` deklariert. Diese Deklaration löst jedoch einen Fehler aus, da `C` bis zu einem späteren Zeitpunkt im Programm nicht deklariert wird und nicht vorwärts deklariert ist. Um den Fehler zu beheben, können Sie entweder die gesamte *Definition* des `C` vor `main` verschieben oder eine vorwärts Deklaration dafür hinzufügen. Dieses Verhalten unterscheidet sich von anderen Sprachen wie C#z. b., in denen Funktionen und Klassen vor dem Zeitpunkt der Deklaration in einer Quelldatei verwendet werden können.

In Zeile 10 wird eine Variable mit dem Namen `str` vom Typ `std::string` deklariert. Der Name `std::string` ist sichtbar, da er in der `string` [Header Datei](header-files-cpp.md) eingeführt wird, die in Zeile 1 in der Quelldatei zusammengeführt wird. `std` ist der Namespace, in dem die `string` Klasse deklariert wird.

In Zeile 11 wird ein Fehler ausgelöst, da der Name `j` nicht deklariert wurde. Eine Deklaration muss einen Typ bereitstellen, im Gegensatz zu anderen Sprachen wie javaScript. In Zeile 12 wird das `auto`-Schlüsselwort verwendet, das den Compiler anweist, den Typ der `k` basierend auf dem Wert abzuleiten, mit dem Sie initialisiert wird. Der Compiler wählt in diesem Fall `int` für den Typ aus.  

## <a name="declaration-scope"></a>Gültigkeitsbereich der Deklaration

Der von einer Deklaration eingeführte Name ist innerhalb des *Bereichs* gültig, in dem die Deklaration auftritt. Im vorherigen Beispiel sind die Variablen, die innerhalb der `main` Funktion deklariert werden, *lokale Variablen*. Sie können eine andere Variable mit dem Namen `i` außerhalb von Main im globalen Gültigkeits *Bereich*deklarieren, und es wäre eine vollständig getrennte Entität. Eine solche Duplizierung von Namen kann jedoch zu Verwirrung und Fehlern im Programmierer führen und sollte vermieden werden. In Zeile 21 wird die Klasse `C` im Gültigkeitsbereich des Namespace `N`deklariert. Durch die Verwendung von Namespaces können *Namenskollisionen*vermieden werden. Die C++ meisten Standard Bibliotheksnamen werden innerhalb des `std`-Namespace deklariert. Weitere Informationen darüber, wie Bereichs Regeln mit Deklarationen interagieren, finden Sie unter [Scope](../cpp/scope-visual-cpp.md).

## <a name="definitions"></a>Definitionen

Einige Entitäten, einschließlich Funktionen, Klassen, enumerationseinheiten und Konstanten Variablen, müssen zusätzlich zu den deklarierten definiert werden. Eine *Definition* stellt dem Compiler alle Informationen zur Verfügung, die er benötigt, um Computercode zu generieren, wenn die Entität später im Programm verwendet wird. Im vorherigen Beispiel enthält Zeile 3 eine Deklaration für die-Funktion `f` aber die *Definition* für die-Funktion wird in den Zeilen 15 bis 18 bereitgestellt. In Zeile 21 ist die Klasse `C` deklariert und definiert (obwohl die Klasse so definiert ist, dass Sie nichts tut). Eine Konstante Variable muss in derselben Anweisung, in der Sie deklariert ist, mit anderen Worten einem Wert zugewiesen werden. Eine Deklaration eines integrierten Typs, wie z. b. `int`, ist automatisch eine Definition, da der Compiler weiß, wie viel Speicherplatz dafür belegt werden soll.

Das folgende Beispiel zeigt Deklarationen, die auch Definitionen sind:

```cpp
// Declare and define int variables i and j.
int i;
int j = 10;

// Declare enumeration suits.
enum suits { Spades = 1, Clubs, Hearts, Diamonds };

// Declare class CheckBox.
class CheckBox : public Control
{
public:
    Boolean IsChecked();
    virtual int     ChangeState() = 0;
};
```

Es folgen einige Deklarationen, die keine Definitionen sind:

```cpp
extern int i;
char *strchr( const char *Str, const char Target );
```

## <a name="typedefs-and-using-statements"></a>Typedefs und using-Anweisungen

In älteren Versionen von C++wird das [typedef](aliases-and-typedefs-cpp.md) -Schlüsselwort verwendet, um einen neuen Namen zu deklarieren, der ein *Alias* für einen anderen Namen ist. Beispielsweise ist der Typ `std::string` ein anderer Name für `std::basic_string<char>`. Es sollte offensichtlich sein, warum Programmierer den Typedef-Namen und nicht den tatsächlichen Namen verwenden. In modernen C++ist das [using](aliases-and-typedefs-cpp.md) -Schlüsselwort als typedef vorzuziehen, aber die Idee ist identisch: ein neuer Name wird für eine Entität deklariert, die bereits deklariert und definiert ist.

## <a name="static-class-members"></a>Statische Klassenmember

Da statische Klassendatenmember diskrete Variablen sind, die von allen Objekten der Klasse gemeinsam genutzt werden, müssen Sie außerhalb der Klassendefinition definiert und initialisiert werden. (Weitere Informationen finden Sie unter [Klassen](../cpp/classes-and-structs-cpp.md).)

## <a name="extern-declarations"></a>externe Deklarationen

Ein C++ Programm kann mehr als eine [Kompilierungseinheit](header-files-cpp.md)enthalten. Verwenden Sie zum Deklarieren einer Entität, die in einer separaten Kompilierungseinheit definiert ist, das [extern](extern-cpp.md) -Schlüsselwort. Die Informationen in der Deklaration sind für den Compiler ausreichend, aber wenn die Definition der Entität im Verknüpfungs Schritt nicht gefunden werden kann, gibt der Linker einen Fehler aus.

## <a name="in-this-section"></a>In diesem Abschnitt

[Speicherklassen](storage-classes-cpp.md)<br/>
[const](const-cpp.md)<br/>
[constexpr](constexpr-cpp.md)<br/>
[extern](extern-cpp.md)<br/>
[Initialisierer](initializers.md)<br/>
[Aliasse und Typdefinitionen](aliases-and-typedefs-cpp.md)<br/>
[using-Deklaration](using-declaration.md)<br/>
[volatile](volatile-cpp.md)<br/>
[decltype](decltype-cpp.md)<br/>
[Attribute inC++](attributes.md)<br/>

## <a name="see-also"></a>Weitere Informationen

[Grundlegende Konzepte](../cpp/basic-concepts-cpp.md)<br/>

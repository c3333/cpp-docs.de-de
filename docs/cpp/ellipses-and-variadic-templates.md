---
title: Auslassungs Zeichen-und Variadic-Vorlagen
ms.date: 11/04/2016
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
ms.openlocfilehash: e916dac40355f4397ef4846c0edf568c60b7d3dd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221626"
---
# <a name="ellipsis-and-variadic-templates"></a>Auslassungs Zeichen-und Variadic-Vorlagen

In diesem Artikel wird gezeigt, wie die Auslassungspunkte (`...`) mit variadic Vorlagen von C++ verwendet werden. Das Auslassungszeichen hatte viele Verwendungszwecke in C und C++. Hierzu gehören Variablenargumentlisten für Funktionen. Die `printf()`-Funktion der C-Laufzeitbibliothek ist eines der bekanntesten Beispiele.

Eine *Variadic-Vorlage* ist eine Klassen-oder Funktions Vorlage, die eine beliebige Anzahl von Argumenten unterstützt. Dieser Mechanismus ist für C++-Bibliotheksentwickler besonders nützlich, da Sie ihn auf Klassen- und Funktionsvorlagen anwenden können, und dadurch eine große Bandbreite typsicherer und nicht trivialer Funktionalität und Flexibilität bereitstellen können.

## <a name="syntax"></a>Syntax

Ein Auslassungszeichen wird auf zwei Arten von variadic-Vorlagen verwendet. Auf der linken Seite des Parameter namens gibt er ein *Parameter Paket*an, und rechts neben dem Parameternamen werden die Parameter Pakete in separate Namen erweitert.

Im folgenden finden Sie ein einfaches Beispiel für die Syntax Syntax der *Variadic-Vorlagen Klasse* :

```cpp
template<typename... Arguments> class classname;
```

Sie können für Parameterpakete und Erweiterungen Leerstellen um die Auslassungszeichen entsprechend den jeweiligen Anforderungen, wie in den folgenden Beispielen dargestellt, hinzufügen:

```cpp
template<typename ...Arguments> class classname;
```

Oder so:

```cpp
template<typename ... Arguments> class classname;
```

Beachten Sie, dass in diesem Artikel die Konvention verwendet wird, die im ersten Beispiel (das Ellipsen ist an angefügt) verwendet wird **`typename`** .

In den vorangehenden Beispielen ist das *Argument* ein Parameter Paket. Die `classname`-Klasse kann eine variable Anzahl von Argumenten akzeptieren, wie in den folgenden Beispielen gezeigt.

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
vtclass<long, std::vector<int>, std::string> vtinstance4;
```

Mit einer variadic-Vorlagenklassendefinition können Sie auch mindestens einen Parameter anfordern:

```cpp
template <typename First, typename... Rest> class classname;
```

Im folgenden finden Sie ein einfaches Beispiel für die Syntax der *Variadic-Vorlagen Funktion* :

```cpp
template <typename... Arguments> returntype functionname(Arguments... args);
```

Das *Argument* Parameter Pack wird dann zur Verwendung erweitert, wie im nächsten Abschnitt "Grundlegendes zu **Variadic-Vorlagen**" gezeigt.

Andere Formen der variadic-Vorlagenfunktionssyntax sind möglich, darunter diese Beispiele:

```cpp
template <typename... Arguments> returntype functionname(Arguments&... args);
template <typename... Arguments> returntype functionname(Arguments&&... args);
template <typename... Arguments> returntype functionname(Arguments*... args);
```

Spezifiken wie **`const`** sind ebenfalls zulässig:

```cpp
template <typename... Arguments> returntype functionname(const Arguments&... args);
```

Wie bei variadic-Vorlagenklassendefinitionen können Sie Funktionen ausführen, die mindestens einen Parameter erfordern:

```cpp
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);
```

Variadic-Vorlagen verwenden den Operator `sizeof...()` (nicht verknüpft mit dem älteren `sizeof()`-Operator):

```cpp
template<typename... Arguments>
void tfunc(const Arguments&... args)
{
    constexpr auto numargs{ sizeof...(Arguments) };

    X xobj[numargs]; // array of some previously defined type X

    helper_func(xobj, args...);
}
```

## <a name="more-about-ellipsis-placement"></a>Weitere Informationen zur Platzierung von Auslassungszeichen

In diesem Artikel wurde bereits die Platzierung des Auslassungszeichens, mit der Parameterpakete und Erweiterungen definiert werden, wie folgt beschrieben: "Auf der linken Seite des Parameternamens zeigt es ein Parameterpaket an, und auf der rechten Seite des Parameternamens erweitert es die Parameterpakete in separaten Namen". Dies ist technisch gesehen richtig, kann jedoch bei der Übersetzung in Code verwirrend sein. Zu berücksichtigen:

- In einer Template-Parameter-List ( `template <parameter-list>` ) `typename...` führt ein Vorlagen Parameter Paket ein.

- In einer Parameter-Declaration-Klausel ( `func(parameter-list)` ) führt die Ellipse auf oberster Ebene ein Funktionsparameter Paket ein, und die Auslassungs Zeichen Positionierung ist wichtig:

    ```cpp
    // v1 is NOT a function parameter pack:
    template <typename... Types> void func1(std::vector<Types...> v1);

    // v2 IS a function parameter pack:
    template <typename... Types> void func2(std::vector<Types>... v2);
    ```

- Wenn das Auslassungszeichen direkt nach dem Parameternamen angezeigt wird, haben Sie eine Parameterpaketerweiterung.

## <a name="example"></a>Beispiel

Eine gute Möglichkeit, den Funktionsmechanismus von variadic-Vorlagen zu veranschaulichen, ist dessen Verwendung in der Neuschreibung einiger Funktionen von `printf`:

```cpp
#include <iostream>

using namespace std;

void print() {
    cout << endl;
}

template <typename T> void print(const T& t) {
    cout << t << endl;
}

template <typename First, typename... Rest> void print(const First& first, const Rest&... rest) {
    cout << first << ", ";
    print(rest...); // recursive call using pack expansion syntax
}

int main()
{
    print(); // calls first overload, outputting only a newline
    print(1); // calls second overload

    // these call the third overload, the variadic template,
    // which uses recursion as needed.
    print(10, 20);
    print(100, 200, 300);
    print("first", 2, "third", 3.14159);
}
```

## <a name="output"></a>Output

```Output
1
10, 20
100, 200, 300
first, 2, third, 3.14159
```

> [!NOTE]
> Die meisten Implementierungen, die Variadic-Vorlagen Funktionen enthalten, verwenden die Rekursion einiger Formen, Sie unterscheiden sich jedoch geringfügig von der herkömmlichen Rekursion.  Bei der herkömmlichen Rekursion wird eine Funktion mit derselben Signatur aufgerufen. (Es kann überladen oder Vorlagen basiert sein, aber die gleiche Signatur wird jedes Mal ausgewählt.) Bei der Variadic-Rekursion wird eine Variadic-Funktions Vorlage mit abweichender (fast immer absteigender) Anzahl von Argumenten aufgerufen, sodass jedes Mal eine andere Signatur gestempelt wird. Eine "Basisfall" ist dennoch erforderlich, aber die Art der Rekursion ist anders.

---
title: Compilerfehler C2672
ms.date: 10/24/2017
f1_keywords:
- C2672
helpviewer_keywords:
- C2672
ms.assetid: 7e86338a-2d4b-40fe-9dd2-ac6886f3f31a
ms.openlocfilehash: 9f844b54285a7df69bfb4387a7afcc82dfef9252
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177130"
---
# <a name="compiler-error-c2672"></a>Compilerfehler C2672

> "*Function*": keine übereinstimmende überladene Funktion gefunden

Der Compiler konnte keine überladene Funktion finden, die mit der angegebenen Funktion übereinstimmt. Es wurde keine Funktion gefunden, die übereinstimmende Parameter annimmt, oder keine übereinstimmende Funktion hat die erforderliche Barrierefreiheit im Kontext.

Wenn Sie von bestimmten Container oder Algorithmen der Standardbibliothek verwendet werden, müssen die Typen barrierefreie Member oder Friend-Funktionen bereitstellen, die die Anforderungen des Containers oder Algorithmus erfüllen. Die iteratortypen sollten z. b. von `std::iterator<>`abgeleitet werden. Bei Vergleichs Vorgängen oder der Verwendung anderer Operatoren für Containerelement Typen ist es möglicherweise erforderlich, dass der Typ sowohl als Linker als auch als rechter Operand angesehen wird. Die Verwendung des-Typs als rechter Operand kann die Implementierung des-Operators als nicht-Member-Funktion des Typs erfordern.

## <a name="example"></a>Beispiel

Compilerversionen vor Visual Studio 2017 führten in einigen Vorlagen Kontexten keine Zugriffs Überprüfung für qualifizierte Namen durch. Das erwartete SFINAE-Verhalten kann behindert werden, in dem die Ersetzung aufgrund der Nichterreichbarkeit des Namens erwartungsgemäß fehlschlägt. Dies kann potenziell einen Absturz oder unerwartetes Verhalten zur Laufzeit auslösen, da der Compiler fälschlicherweise die falsche Überladung des Operators aufgerufen hat. In Visual Studio 2017 wird ein Compilerfehler ausgelöst.

Dieses Beispiel wird in Visual Studio 2015 kompiliert, es wird jedoch ein Fehler in Visual Studio 2017 ausgelöst. Um dieses Problem zu beheben, machen Sie den Vorlagen Parameter Member zugänglich, wo er ausgewertet wird.

```cpp
#include <type_traits>

template <class T> class S {
// public:    // Uncomment this line to fix
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x)
{
    return (x == 0);
}

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```

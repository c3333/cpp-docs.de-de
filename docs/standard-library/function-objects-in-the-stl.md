---
title: Funktionsobjekte in der C++-Standardbibliothek
ms.date: 03/15/2019
helpviewer_keywords:
- functors
- C++ Standard Library, functors
- C++ Standard Library, function objects
- function objects
ms.assetid: 85f8a735-2c7b-4f10-9c4d-95c666ec4192
ms.openlocfilehash: ed413b2bcdcda8f65794b10c792b10358564420a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215737"
---
# <a name="function-objects-in-the-c-standard-library"></a>Funktionsobjekte in der C++-Standardbibliothek

Ein *Funktionsobjekt*oder *Funktionselement*ist ein beliebiger Typ, der „operator()“ implementiert. Dieser Operator wird als *Aufrufoperator* oder manchmal als *Anwendungsoperator*bezeichnet. Die C++-Standardbibliothek verwendet Funktionsobjekte hauptsächlich als Sortierungskriterien für Container und in Algorithmen.

„Funktionsobjekte“ bieten gegenüber einem konventionellen Funktionsaufruf zwei wesentliche Vorteile. Der erste Vorteil ist, dass ein Funktionsobjekt einen Zustand enthalten kann. Der zweite Vorteil ist, dass ein Funktionsobjekt ein Typ ist und daher nicht als Vorlagenparameter verwendet werden kann.

## <a name="creating-a-function-object"></a>Erstellen eines Funktionsobjekts

Um ein Funktionsobjekt zu erstellen, erstellen Sie einen Typ, und implementieren Sie „operator()“, z. B.:

```cpp
class Functor
{
public:
    int operator()(int a, int b)
    {
        return a < b;
    }
};

int main()
{
    Functor f;
    int a = 5;
    int b = 7;
    int ans = f(a, b);
}
```

Die letzte Zeile der `main` -Funktion zeigt, wie Sie das Funktionsobjekt aufrufen. Dieser Aufruf ähnelt einem Aufruf einer Funktion, ruft aber tatsächlich den Operator () des Funktions Typs auf. Diese Ähnlichkeit zwischen dem Aufruf eines Funktionsobjekts und einer Funktion hat zum Begriff „Funktionsobjekt“ geführt.

## <a name="function-objects-and-containers"></a>Funktionsobjekte und Container

Die C++-Standard Bibliothek enthält mehrere Funktions Objekte in der [\<functional>](../standard-library/functional.md) Header Datei. Eine Verwendung dieser Funktionsobjekte ist als Sortierungskriterium für Container. Beispielsweise wird der `set` -Container wie folgt deklariert:

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

Das zweite Vorlagenargument ist das Funktionsobjekt „ `less`“. Dieses Funktions Objekt gibt zurück, **`true`** Wenn der erste Parameter kleiner als der zweite Parameter ist. Da einige Container ihre Elemente sortieren, benötigt der Container eine Möglichkeit zum Vergleichen von zwei Elementen. Der Vergleich erfolgt mithilfe des Funktions Objekts. Sie können eigene Sortierungskriterien für Container definieren, indem Sie ein Funktionsobjekt erstellen und es in der Vorlagenliste für den Container angeben.

## <a name="function-objects-and-algorithms"></a>Funktionsobjekte und Algorithmen

Eine weitere Verwendungsmöglichkeit von Funktionsobjekten ist in Algorithmen. Beispielsweise wird der `remove_if` -Algorithmus wie folgt deklariert:

```cpp
template <class ForwardIterator, class Predicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    Predicate pred);
```

Das letzte Argument für `remove_if` ist ein Funktionsobjekt, das einen booleschen Wert zurückgibt (ein *Prädikat*). Wenn das Ergebnis des Funktions Objekts ist **`true`** , wird das Element aus dem Container entfernt, auf den die Iteratoren und zugreifen `first` `last` . Sie können eines der Funktions Objekte verwenden, die im- [\<functional>](../standard-library/functional.md) Header für das Argument deklariert sind, `pred` oder Sie können ein eigenes erstellen.

## <a name="see-also"></a>Weitere Informationen

[C++-Standard Bibliotheks Referenz](../standard-library/cpp-standard-library-reference.md)

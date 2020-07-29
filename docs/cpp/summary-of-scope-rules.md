---
title: Zusammenfassung der Bereichsregeln
ms.date: 11/04/2016
helpviewer_keywords:
- class scope [C++], rules
- classes [C++], scope
- class names [C++], scope rules
- names [C++], class
- scope [C++], class names
ms.assetid: 47e26482-0111-466f-b857-598c15d05105
ms.openlocfilehash: 024a61419129f669485944a427379dd41c385404
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231064"
---
# <a name="summary-of-scope-rules"></a>Zusammenfassung der Bereichsregeln

Die Verwendung eines Name muss innerhalb seines Bereichs eindeutig sein (bis zu dem Punkt, an dem das Überladen bestimmt wird). Wenn der Name eine Funktion kennzeichnet, muss die Funktion im Hinblick auf Anzahl und Typ der Parameter eindeutig sein. Wenn der Name weiterhin eindeutig ist, werden [Member-Access-](../cpp/member-access-control-cpp.md) Regeln angewendet.

## <a name="constructor-initializers"></a>Konstruktorinitialisierer

[Konstruktorinitialisierer](constructors-cpp.md#member_init_list) werden im Gültigkeitsbereich des äußersten Blocks des Konstruktors ausgewertet, für den Sie angegeben werden. Daher können sie die Parameternamen des Konstruktors verwenden.

## <a name="global-names"></a>Globale Namen

Ein Name eines Objekts, einer Funktion oder eines Enumerators ist global, wenn er außerhalb einer Funktion oder Klasse eingefügt oder ihm der globale unäre Bereichsoperator (`::`) vorangestellt wird und er nicht in Verbindung mit einem dieser binären Operatoren verwendet wird:

- Bereichsauflösung (`::`)

- Elementauswahl für Objekte und Verweise (**.**)

- Elementauswahl für Zeiger ( **->** )

## <a name="qualified-names"></a>Qualifizierte Namen

Namen, die mit dem binären Bereichsauflösungsoperator (`::`) verwendet werden, werden als „qualifizierte Namen“ bezeichnet. Der Name, der nach dem binären Bereichsauflösungsoperator angegeben wird, muss einem Member der Klasse entsprechen, der auf der linken Seite des Operators angegeben oder ein Member der Basisklasse(n) ist.

Namen, die nach dem Member-Selection-Operator () angegeben werden **.** oder **->** ) müssen Member des Klassen Typs des Objekts sein, das auf der linken Seite des Operators oder der zugehörigen Basisklassen angegeben wird. Namen, die auf der rechten Seite des Member-Selection-Operators ( **->** ) angegeben sind, können auch Objekte eines anderen Klassen Typs sein, vorausgesetzt, dass die linke Seite von **->** ein Klassenobjekt ist und dass die Klasse einen überladenen Member-Selection-Operator () definiert, der **->** zu einem Zeiger auf einen anderen Klassentyp ausgewertet wird. (Diese Bereitstellung wird ausführlicher unter Zugriff auf [Klassenmember](../cpp/member-access.md)erläutert.)

Der Compiler sucht nach Namen in der folgenden Reihenfolge und hört auf, wenn der Name gefunden wird:

1. Aktueller Blockbereich, wenn der Name innerhalb einer Funktion verwendet wird; andernfalls globaler Gültigkeitsbereich.

1. Nach außen durch jeden einschließenden Blockbereich, einschließlich des äußersten Gültigkeitsbereichs der Funktion (der Funktionsparameter enthält).

1. Wenn der Name innerhalb einer Memberfunktion verwendet wird, wird der Gültigkeitsbereich der Klasse nach dem Namen durchsucht.

1. Die Basisklassen der Klasse werden nach dem Namen durchsucht.

1. Der einschließende, verschachtelte Klassenbereich (sofern vorhanden) und seine Basen werden durchsucht. Die Suche wird fortgesetzt, bis der äußerste einschließende Klassenbereich durchsucht wurde.

1. Globaler Gültigkeitsbereich wird durchsucht.

Sie können jedoch wie folgt Änderungen an dieser Suchreihenfolge vornehmen:

1. Namen, denen `::` vorangestellt wird, zwingen die Suche, im globalen Gültigkeitsbereich zu starten.

1. Namen, denen die **`class`** Schlüsselwörter, und vorangestellt sind, **`struct`** **`union`** erzwingen, dass der Compiler nur nach-,- **`class`** oder-Namen sucht **`struct`** **`union`** .

1. Namen auf der linken Seite des Bereichs Auflösungs Operators ( `::` ) können nur-,-,- **`class`** oder-Namen sein **`struct`** **`namespace`** **`union`** .

Wenn der Name auf einen nicht statischen Member verweist, aber in einer statischen Memberfunktion verwendet wird, wird eine Fehlermeldung generiert. Wenn der Name auf einen nicht statischen Member in einer einschließenden Klasse verweist, wird auch eine Fehlermeldung generiert, da eingeschlossene Klassen keine Zeiger der einschließenden Klasse aufweisen **`this`** .

## <a name="function-parameter-names"></a>Funktionsparameternamen

Funktionsparameternamen in Funktionsdefinitionen werden als Bestandteil des Gültigkeitsbereichs des äußersten Blocks der Funktion angesehen. Daher sind sie lokale Namen und verlassen den Gültigkeitsbereich, wenn die Funktion beendet wird.

Funktionsparameternamen in Funktionsdeklarationen (Prototypen) befinden sich im lokalen Gültigkeitsbereich der Deklaration und verlassen den Gültigkeitsbereich am Ende der Deklaration.

Standardparameter befinden sich im Gültigkeitsbereich des Parameters, für das sie die Standardeinstellung sind, wie in den beiden vorherigen Absätzen beschrieben. Sie können jedoch nicht auf lokale Variablen oder nicht statische Klassenmember zugreifen. Standardparameter werden zum Zeitpunkt des Funktionsaufrufs, aber im ursprünglichen Gültigkeitsbereich der Funktionsdeklaration ausgewertet. Deshalb werden die Standardparameter für Memberfunktionen immer im Klassengültigkeitsbereich ausgewertet.

## <a name="see-also"></a>Siehe auch

[Vererbung](../cpp/inheritance-cpp.md)

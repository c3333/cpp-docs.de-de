---
title: Umwandlung
ms.date: 11/19/2018
helpviewer_keywords:
- casting [C++]
- coercion [C++]
- virtual functions [C++], in derived classes [C++]
- static cast operator
- dynamic cast operator
- polymorphic classes [C++]
- classes [C++], polymorphism
ms.assetid: 3dbeb06e-2f4b-4693-832d-624bc8ec95de
ms.openlocfilehash: bb06db3af6aee031b6cb2d69b38a9404304420fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190129"
---
# <a name="casting"></a>Umwandlung

Die Programmiersprache C++ setzt voraus, dass, wenn eine Klasse von einer Basisklasse abgeleitet ist, die virtuelle Funktionen enthält, ein Zeiger auf diesen Basisklassentyp verwendet werden kann, um Implementierungen der virtuellen Funktionen, die sich im abgeleiteten Klasseobjekt befinden, aufzurufen. Eine Klasse, die virtuelle Funktionen enthält, wird manchmal als "eine polymorphe Klasse" bezeichnet.

Da eine abgeleitete Klasse die Definitionen aller Basisklassen enthält, von der sie abgeleitet ist, kann ein Zeiger oben in der Klassenhierarchie in jede dieser Basisklassen umgewandelt werden. Bei einem Zeiger auf eine Basisklasse, kann es sicherer sein, den Zeiger die Hierarchie herunter umzuwandeln. Es ist sicher, wenn das Objekt, auf das gezeigt wird, tatsächlich einen Typ aufweist, der aus der Basisklasse abgeleitet ist. In diesem Fall wird das eigentliche Objekt als "vollständiges Objekt" angesehen. Der Zeiger auf die Basisklasse zeigt auf ein "Unterobjekt" des vollständigen Objekts. Betrachten Sie z. B. die Klassenhierarchie, die in der folgenden Abbildung gezeigt wird.

![Klassenhierarchie](../cpp/media/vc38zz1.gif "Klassenhierarchie") <br/>
Klassenhierarchie

Ein Objekt vom Typ `C` könnte visualisiert werden, wie in der folgenden Abbildung zu sehen ist.

![Klasse C mit unter&#45;geordneten Objekten B und A](../cpp/media/vc38zz2.gif "Klasse C mit unter&#45;geordneten Objekten B und A") <br/>
Klasse C mit Unterobjekten B und A

Bei einer Instanz der Klasse `C`, gibt es die Unterobjekte `B` und `A`. Die Instanz von `C`, einschließlich der Unterobjekte `A` und `B`, ist das "vollständige Objekt".

Mit Laufzeit-Typeninformation können Sie prüfen, ob ein Zeiger tatsächlich auf ein vollständiges Objekt zeigt und auch sicher umgewandelt werden kann, um auf ein anderes Objekt in seiner Hierarchie zu zeigen. Der [dynamic_cast](../cpp/dynamic-cast-operator.md) -Operator kann verwendet werden, um diese Typen von Umwandlungen zu erstellen. Außerdem wird die Laufzeitüberprüfung ausgeführt, die erforderlich ist, um den Vorgang sicher zu gestalten.

Für die Konvertierung von nicht polymorphen Typen können Sie den [static_cast](../cpp/static-cast-operator.md) -Operator verwenden (in diesem Thema wird der Unterschied zwischen statischen und dynamischen Umwandlungs Konvertierungen erläutert, und wann diese verwendet werden kann).

In diesem Abschnitt werden folgende Themen behandelt:

- [Umwandlungs Operatoren](../cpp/casting-operators.md)

- [Lauf Zeittyp Informationen](../cpp/run-time-type-information.md)

## <a name="see-also"></a>Siehe auch

[Ausdrücke](../cpp/expressions-cpp.md)

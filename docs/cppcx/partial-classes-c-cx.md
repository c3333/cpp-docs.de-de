---
title: Partielle Klassen (C++/CX)
description: Deklarieren und Verwenden von partiellen Klassen in C++/CX.
ms.date: 12/30/2016
ms.assetid: 69d93575-636c-4564-8cca-6dfba0c7e328
ms.openlocfilehash: 70225069c948a50b38ac3642113cf940c86cf8da
ms.sourcegitcommit: 0df2b7ab4e81284c5248e4584767591dcc1950c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/09/2020
ms.locfileid: "89609062"
---
# <a name="partial-classes-ccx"></a>Partielle Klassen (C++/CX)

Eine partielle Klasse ist ein Konstrukt, das Szenarien unterstützt, in denen Sie einen Teil einer Klassendefinition ändern. Software, die automatisch Code generiert – beispielsweise der XAML Designer – ändert ebenfalls Code in der gleichen Klasse. Durch die Verwendung einer partiellen Klasse können Sie verhindern, dass der Designer Ihren Code überschreibt. In einem Visual Studio-Projekt wird der- **`partial`** Modifizierer automatisch auf die generierte Datei angewendet.

## <a name="syntax"></a>Syntax

Um eine partielle Klasse zu definieren, verwenden Sie das **`partial`** Schlüsselwort direkt vor dem Klassen Schlüssel von, was andernfalls eine normale Klassendefinition wäre. Ein Schlüsselwort wie **`partial ref class`** ist ein kontextbezogenes Schlüsselwort, das Leerzeichen enthält. Partielle Definitionen werden in den folgenden Konstrukten unterstützt.

- **`class`** oder **`struct`**

- **`ref class`** oder **`ref struct`**

- **`value class`** oder **`value struct`**

- **`enum`** oder **`enum class`**

- **`ref interface`**, **`interface class`** , **`interface struct`** oder **`__interface`**

- **`union`**

Dieses Beispiel veranschaulicht eine partielle **`ref class`** :

[!code-cpp[cx_partial#01](../cppcx/codesnippet/CPP/partialclassexample/class1.h#01)]

## <a name="contents"></a>Inhalte

Eine partielle Klassendefinition kann alles enthalten, was die vollständige Klassendefinition enthalten kann, wenn das **`partial`** Schlüsselwort ausgelassen wurde. Mit einer Ausnahme schließt dies jedes gültige Konstrukt ein, z. B. Basisklassen, Datenmember, Memberfunktionen, Enumerationen, Friend-Deklarationen und Attribute. Inlinedefinitionen statischer Datenmember sind zulässig.

Die eine Ausnahme ist die Klassen-Barrierefreiheit. Beispielsweise ist die Anweisung `public partial class MyInvalidClass {/* ... */};` fehlerhaft. Zugriffsspezifizierer, die in einer partiellen Klassendefinition für MyInvalidClass verwendet werden, wirken sich nicht auf die Standard-Barrierefreiheit in einer nachfolgenden partiellen oder vollständigen Klassendefinition für MyInvalidClass aus.

Das folgende Codefragment zeigt die Barrierefreiheit. In der ersten partiellen Klasse ist `Method1` öffentlich, weil die Barrierefreiheit öffentlich ist. In der zweiten partiellen Klasse ist `Method2` privat, weil die standardmäßige Klassenbarrierefreiheit privat ist.

[!code-cpp[cx_partial#02](../cppcx/codesnippet/CPP/partialclassexample/class1.h#02)]

## <a name="declaration"></a>Deklaration

Eine partielle Definition einer Klasse, wie z `MyClass` . b., ist nur eine Deklaration von MyClass. Das heißt, es wird nur der Name eingeführt `MyClass` . `MyClass` kann nicht auf eine Weise verwendet werden, für die eine Klassendefinition erforderlich ist, z. b. das Wissen der Größe von `MyClass` oder der Verwendung einer Basis oder eines Members von `MyClass` . `MyClass` gilt nur dann als definiert, wenn der Compiler auf eine nicht partielle Definition von trifft `MyClass` .

Im folgenden Beispiel wird das Deklarationsverhalten einer partiellen Klasse demonstriert. Nach der Deklaration #1 `MyClass` kann so verwendet werden, als ob Sie als vorwärts Deklaration geschrieben wäre `ref class MyClass;` . Deklaration Nr. 2 ist mit Deklaration Nr. 1 äquivalent. Deklaration Nr. 3 ist gültig, da sie eine Vorwärtsdeklaration für eine Klasse ist. Deklaration Nr. 4 ist jedoch ungültig, da

`MyClass` nicht vollständig definiert ist.

Deklarations #5 verwendet nicht das **`partial`** Schlüsselwort, und die Deklaration definiert vollständig `MyClass` . Daher ist Deklaration Nr. 6 gültig.

[!code-cpp[Cx_partial#03](../cppcx/codesnippet/CPP/partialclassexample/class1.h#03)]

## <a name="number-and-ordering"></a>Anzahl und Reihenfolge

Es kann null oder mehr partielle Klassendefinitionen für jede vollständige Definition einer Klasse geben.

Jede partielle Klassendefinition einer Klasse muss lexikalisch der vollständigen Definition dieser Klasse vorangestellt sein, aber es müssen keine vorwärts Deklarationen der Klasse vorangestellt werden. Wenn es keine vollständige Definition der Klasse gibt, können die partiellen Klassendeklarationen nur Vorwärtsdeklarationen sein.

Alle Klassen Schlüssel, z **`class`** . b. und, müssen mit identisch sein **`struct`** . Beispielsweise ist der Code `partial class X {}; struct X {};`ein.

Das folgende Beispiel zeigt Anzahl und Reihenfolge. Bei der letzten partiellen Deklaration tritt ein Fehler auf, da die Klasse bereits definiert ist.

[!code-cpp[cx_partial#04](../cppcx/codesnippet/CPP/partialclassexample/class1.h#04)]

## <a name="full-definition"></a>Vollständige Definition

Zum Zeitpunkt der vollständigen Definition der Klasse ist X ist das Verhalten das Gleiche, als ob die Definition von X alle Basisklassen, Member usw. in der Reihenfolge deklariert hätte, in der sie in der partiellen Klasse gefunden und definiert wurden. Das bedeutet, dass der Inhalt der partiellen Klassen so behandelt wird, als ob er zum Zeitpunkt der vollständigen Definition der Klasse geschrieben wäre. Namenssuche und andere Sprachregeln werden zum Zeitpunkt der vollständigen Definition der Klasse angewendet, als ob der Inhalt der partiellen Klassen an dieser Stelle geschrieben wäre.

Die folgenden zwei Codebeispiele haben identische Bedeutung und Auswirkungen. Im ersten Beispiel wird eine partielle Klasse verwendet, im zweiten jedoch nicht.

[!code-cpp[cx_partial#05](../cppcx/codesnippet/CPP/partialclassexample/class1.h#05)]

[!code-cpp[cx_partial#06](../cppcx/codesnippet/CPP/partialclassexample/class1.h#06)]

## <a name="templates"></a>Vorlagen

Eine partielle Klasse kann keine Vorlage sein.

## <a name="restrictions"></a>Beschränkungen

Eine partielle Klasse kann nicht über eine Übersetzungseinheit hinausgehen.

Das **`partial`** Schlüsselwort wird nur in Kombination mit dem- **`ref class`** Schlüsselwort oder dem **`value class`** Schlüsselwort unterstützt.

### <a name="examples"></a>Beispiele

Im folgenden Beispiel wird die Klasse `Address` für zwei Codedateien definiert. Der Designer ändert `Address.details.h` , und Sie ändern `Address.h`. Nur die Klassendefinition in der ersten Datei verwendet das **`partial`** Schlüsselwort.

[!code-cpp[cx_partial#07](../cppcx/codesnippet/CPP/partialclassexample/address.details.h#07)]

[!code-cpp[cx_partial#09](../cppcx/codesnippet/CPP/partialclassexample/address.h#09)]

## <a name="see-also"></a>Weitere Informationen

[Typensystem](../cppcx/type-system-c-cx.md)<br/>
[C++/CX-Sprachreferenz](../cppcx/visual-c-language-reference-c-cx.md)<br/>
[Namespaces-Referenz](../cppcx/namespaces-reference-c-cx.md)

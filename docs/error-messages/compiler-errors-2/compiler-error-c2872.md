---
title: Compilerfehler C2872
ms.date: 11/04/2016
f1_keywords:
- C2872
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
ms.openlocfilehash: f57b250f87bd7f2c5808b5a681ddfe49dfa5e876
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228894"
---
# <a name="compiler-error-c2872"></a>Compilerfehler C2872

'*Symbol*': Mehrdeutiges Symbol

Der Compiler kann nicht feststellen, auf welches Symbol verwiesen wird. Es liegt mehr als ein Symbol mit dem angegebenen Namen im Gültigkeitsbereich vor. Weitere Informationen finden Sie in den Hinweisen in der Fehlermeldung für die Dateispeicher Orte und-Deklarationen, die der Compiler für das mehrdeutige Symbol Um dieses Problem zu beheben, können Sie das mehrdeutige Symbol vollständig qualifizieren, indem Sie den Namespace verwenden, z `std::byte` `::byte` . b. oder. Sie können auch einen [Namespace-alias](../../cpp/namespaces-cpp.md#namespace_aliases) verwenden, um einem enthaltenen Namespace einen bequemen Kurznamen für die Verwendung bei der Eindeutigkeit von Symbolen im Quellcode zu geben.

C2872 kann auftreten, wenn eine Header Datei eine [using-Direktive](../../cpp/namespaces-cpp.md#using_directives)enthält und eine nachfolgende Header Datei enthalten ist, die einen Typ enthält, der sich auch in dem Namespace befindet, der in der **`using`** Direktive angegeben ist. Geben Sie eine- **`using`** Direktive erst an, nachdem alle Header Dateien mit angegeben wurden `#include` .

C2872 kann in Visual Studio 2013 auftreten, weil ein Konflikt zwischen dem `Windows::Foundation::Metadata::Platform` Aufzählungstyp und dem C++/CX-defined- `Platform` Namespace vorliegt. Führen Sie zur Umgehung dieses Problems die folgenden Schritte aus:

- Entfernen Sie die Klausel "using namespace Windows:: Foundation:: Metadata" aus den Projektdateien.

- Geben Sie den voll qualifizierten Namen für jeden Typ an, der in diesem Namespace enthalten ist.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird C2872 generiert, da ein mehrdeutiger Verweis auf eine Variable mit dem Namen erstellt wird `i` . zwei Variablen mit demselben Namen befinden sich im Gültigkeitsbereich:

```cpp
// C2872.cpp
// compile with: cl /EHsc C2872.cpp
namespace A {
   int i;
}

using namespace A;
int i;
int main() {
   ::i++;   // ok, uses i from global namespace
   A::i++;   // ok, uses i from namespace A
   i++;   // C2872 ambiguous: ::i or A::i?
   // To fix this issue, use the fully qualified name
   // for the intended variable.
}
```

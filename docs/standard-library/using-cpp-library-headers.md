---
title: Verwenden von C++-Bibliotheksheadern
ms.date: 11/04/2016
helpviewer_keywords:
- headers, naming in C++ include directive
- standard header in C++
- headers
- INCLUDE directive
- headers, C++ Standard Library
- library headers
- C++ Standard Library, headers
ms.assetid: a36e889e-1af2-4cd9-a211-bfc7a3fd8e85
ms.openlocfilehash: a73ebebb4fdde5dd72f148390d004c32b9f4dff7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215477"
---
# <a name="using-c-library-headers"></a>Verwenden von C++-Bibliotheksheadern

Der Inhalt eines Standardheaders kann durch Benennen in einer include-Direktive eingebunden werden.

```cpp
#include <iostream>// include I/O facilities
```

Die Standardheader können in beliebiger Reihenfolge eingebunden werden. Ein Standardheader kann mehrmals eingebunden werden. Und es können mehrere Standardheader eingebunden werden, die dasselbe Makro oder denselben Typ definieren. Ein Standardheader darf jedoch nicht in eine Deklaration eingebunden werden. Definieren Sie keine Makros, die dieselben Namen wie Schlüsselwörter haben, bevor Sie einen Standardheader einschließen.

Ein C++-Bibliotheksheader enthält alle anderen C++-Bibliotheksheader, die zum Definieren der erforderlichen Typen benötigt werden. (Fügen Sie immer explizit alle C++-Bibliotheks Header ein, die in einer Übersetzungseinheit erforderlich sind, aber nicht, wenn Sie die eigentlichen Abhängigkeiten erraten.) Ein Standard-C-Header enthält nie einen anderen Standard Header. Mit einem Standardheader werden lediglich die in diesem Dokument hierfür beschriebenen Entitäten deklariert bzw. definiert.

Alle Funktionen in der Bibliothek werden in einem Standardheader deklariert. Im Gegensatz zu Standard C wird vom Standardheader kein Maskierungsmakro mit demselben Namen wie die Funktion bereitgestellt, das die Funktionsdeklaration maskiert und denselben Effekt erzielt. Weitere Informationen zu Maskierungsmakros finden Sie unter [C++ Library Conventions (C++-Bibliothekskonventionen)](../standard-library/cpp-library-conventions.md).

Alle Namen außer **Operator Delete** und **Operator new** in den C++-Bibliotheks Headern werden im- `std` Namespace oder in einem Namespace definiert, der im- `std` Namespace geschachtelt ist. Auf den Namen `cin` wird beispielsweise mit `std::cin` verwiesen. Makronamen unterliegen nicht der Namespacequalifikation. Daher wird `__STD_COMPLEX` ohne Namespacequalifizierer geschrieben.

In einigen Übersetzungs Umgebungen kann das Einschließen eines C++-Bibliotheks Headers externe Namen, die im `std` Namespace deklariert sind, ebenfalls in den globalen Namespace einbinden, wobei individuelle **`using`** Deklarationen für die einzelnen Namen angegeben werden. Ist dies nicht der Fall, werden vom Header *keine* Bibliotheksnamen in den aktuellen Namespace eingeführt.

Für den C++-Standard ist es erforderlich, dass die C-Standard Header alle externen Namen im Namespace deklarieren `std` und Sie dann in den globalen Namespace mit einzelnen **`using`** Deklarationen für die einzelnen Namen anheben. In einigen Übersetzungsumgebungen enthalten die C-Standardheader jedoch keine Namespacedeklarationen. Stattdessen werden alle Namen direkt im globalen Namespace deklariert. Somit wird das Ergebnis am besten portierbar, wenn im Umgang mit Namespaces zwei Regeln befolgt werden:

- Um einen externen Namen, der normalerweise in deklariert ist, im Namespace zu deklarieren, fügen Sie Beispiels `std` \<stdlib.h> Weise den-Header ein \<cstdlib> . Beachten Sie, dass der Name möglicherweise auch im globalen Namespace deklariert wird.

- Um den globalen Namespace zu deklarieren, müssen Sie \<stdlib.h> den-Header \<stdlib.h> direkt einschließen. Beachten Sie, dass der Name möglicherweise auch im Namespace `std` deklariert wird.

Wenn Sie also aufzurufen, `std::abort` um eine ungewöhnliche Beendigung zu bewirken, sollten Sie einschließen \<cstdlib> . Wenn Sie anrufen möchten `abort` , sollten Sie einschließen \<stdlib.h> .

Alternativ können Sie folgende Deklaration schreiben:

```cpp
using namespace std;
```

Damit werden alle Bibliotheksnamen in den aktuellen Namespace eingebunden. Wenn Sie diese Deklaration direkt nach den include-Direktiven einfügen, werden die Namen in den globalen Namespace gehoben. Danach müssen Sie sich in der restlichen Übersetzungseinheit um Namespaces keine Gedanken mehr zu machen. Außerdem umgehen Sie damit die meisten Differenzen zwischen unterschiedlichen Übersetzungsumgebungen.

Sofern nicht ausdrücklich anders angegeben, sollten Sie Namen nicht im Namespace `std` oder in einem Namespace angeben, der im Namespace `std` in Ihrem Programm geschachtelt ist.

## <a name="see-also"></a>Weitere Informationen

[Übersicht über die C++-Standard Bibliothek](../standard-library/cpp-standard-library-overview.md)\
[Thread Sicherheit in der C++-Standard Bibliothek](../standard-library/thread-safety-in-the-cpp-standard-library.md)

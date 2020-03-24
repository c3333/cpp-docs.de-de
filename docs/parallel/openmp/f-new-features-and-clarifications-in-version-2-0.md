---
title: F. Neue Funktionen und Erläuterungen in Version 2.0
ms.date: 01/22/2019
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: 8cd82000992ab957bf2c41f11deccd65e2e6ea8f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215032"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. Neue Funktionen und Erläuterungen in Version 2.0

In diesem Anhang werden die wichtigsten Änderungen an OpenMP C/C++ Specification bei der Umstellung von Version 1,0 auf Version 2,0 zusammengefasst. Die folgenden Elemente sind neue Features, die der Spezifikation hinzugefügt werden:

- Kommas sind in OpenMP- [Direktiven](2-directives.md#21-directive-format)zulässig.

- Hinzufügen der `num_threads`-Klausel. Diese Klausel ermöglicht es Benutzern, eine bestimmte Anzahl von Threads für ein [paralleles Konstrukt](2-directives.md#23-parallel-construct)anzufordern.

- Die [Thread private](2-directives.md#271-threadprivate-directive) -Direktive wurde erweitert, um statische Block Bereichs Variablen zu akzeptieren.

- C99-Arrays mit variabler Länge sind umfassende Typen und können überall dort angegeben werden, wo alle Typen zulässig sind, z. b. in den Listen der Klauseln `private`, `firstprivate`und `lastprivate` (siehe [Abschnitt 2.7.2](2-directives.md#272-data-sharing-attribute-clauses)).

- Eine private Variable in einem parallelen Bereich kann in einer nsted-Direktive erneut als [Privat](2-directives.md#2721-private) gekennzeichnet werden.

- Die `copyprivate`-Klausel wurde hinzugefügt. Es stellt einen Mechanismus bereit, mit dem eine private Variable verwendet werden kann, um einen Wert von einem Teammitglied an die anderen Elemente zu übertragen. Es ist eine Alternative zur Verwendung einer freigegebenen Variablen für den Wert, wenn eine solche freigegebene Variable schwierig wäre (z. b. in einer Rekursion, die eine andere Variable auf jeder Ebene erfordert). Die [copyprivate](2-directives.md#2728-copyprivate) -Klausel kann nur in der `single`-Direktive angezeigt werden.

- Das Hinzufügen von Zeit Steuerungs Routinen [omp_get_wtick](3-run-time-library-functions.md#332-omp_get_wtick-function) und [omp_get_wtime](3-run-time-library-functions.md#331-omp_get_wtime-function) ähnlich wie die MPI-Routinen. Diese Funktionen sind für die zeitliche zeitliche Steuerung von Wall-Stunden erforderlich.

- Es wurde ein Anhang mit einer Liste von [Implementierungs definiertem Verhalten](e-implementation-defined-behaviors-in-openmp-c-cpp.md) in OpenMPC++ C/hinzugefügt. Eine-Implementierung ist erforderlich, um das Verhalten in diesen Fällen zu definieren und zu dokumentieren.

- Die folgenden Änderungen dienen zum verdeutlichen oder korrigieren von Features in der vorherigen OpenMP-API-SpezifikationC++für C/:

  - Erläutert, dass das Verhalten von [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) und [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) bei Rückgabe von `omp_in_parallel` ungleich NULL nicht definiert ist.

  - Erläuterte [directive nesting](2-directives.md#29-directive-nesting) Anweisungs Schachtelung, wenn geschachtelte parallele verwendet wird.

  - Die Funktionen der [Sperr Initialisierung](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions) und sperrenzerstörung können in einem parallelen Bereich aufgerufen werden. [lock destruction](3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)

  - [Anhang A](a-examples.md)wurden neue Beispiele hinzugefügt.

---
title: Hinzufügen einer Anmerkung zum Sperrverhalten
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Releases_nonreentrant_lock_
- _Lock_kind_mutex_
- _Lock_kind_critical_section_
- _Acquires_lock_
- _Releases_lock_
- _Has_lock_kind_
- _Releases_exclusive_lock_
- _Post_same_lock_
- _Requires_exclusive_lock_held_
- _Requires_shared_lock_held_
- _Lock_kind_semaphore_
- _Requires_lock_held_
- _Acquires_exclusive_lock_
- _Create_lock_level_
- _Acquires_nonreentrant_lock_
- _Releases_shared_lock_
- _Has_lock_level_
- _Lock_kind_spin_lock_
- _Requires_lock_not_held_
- _Acquires_shared_lock_
- _Requires_no_locks_held_
- _Lock_level_order_
- _Lock_kind_event_
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
ms.openlocfilehash: 8966d982b7bcbe9844a7bf1ec3088c2a9424b23a
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "79467054"
---
# <a name="annotating-locking-behavior"></a>Hinzufügen einer Anmerkung zum Sperrverhalten

Um Parallelitäts Fehler in Ihrem Multithread-Programm zu vermeiden, befolgen Sie immer eine angemessene Sperr Disziplin, und verwenden Sie SAL-Anmerkungen.

Parallelitäts Fehler sind bekanntermaßen schwer zu reproduzieren, zu diagnostizieren und zu debuggen, da Sie nicht deterministisch sind. Die Argumentation der Thread Interaktion ist am besten schwierig und ist nicht mehr praktikabel, wenn Sie einen Code Körper entwerfen, der mehr als einige Threads enthält. Daher empfiehlt es sich, eine Sperr Disziplin in ihren Multithreadprogrammen zu befolgen. Wenn Sie z. b. eine Sperr Reihenfolge während des Erstellens mehrerer Sperren einhalten, können Deadlocks vermieden werden, und das Abrufen der richtigen Schutzsperre, bevor Sie auf eine freigegebene Ressource zugreifen, hilft

Leider können scheinbar einfache Sperr Regeln in der Praxis erstaunlich schwer befolgt werden. Eine grundlegende Einschränkung in den heutigen Programmiersprachen und Compilern besteht darin, dass Sie die Spezifikation und die Analyse der Parallelitäts Anforderungen nicht direkt unterstützen. Programmierer müssen sich auf informelle Code Kommentare verlassen, um Ihre Absichten in Bezug auf die Verwendung von Sperren auszudrücken.

Parallelitäts SAL-Anmerkungen sind so konzipiert, dass Sie das Sperren von Nebeneffekten, die Sperr Verantwortung, die Daten Überwachungen, die Hierarchie der Sperr Reihenfolge und ein anderes erwartetes Sperr Verhalten angeben können. Durch die explizite Durchführung impliziter Regeln bieten SAL-Parallelitäts Anmerkungen eine konsistente Möglichkeit, zu dokumentieren, wie der Code Sperr Regeln verwendet. Neben läufigkeits Anmerkungen verbessern auch die Fähigkeit von Code Analysetools, Racebedingungen, Deadlocks, nicht übereinstimmende Synchronisierungs Vorgänge und andere feine Parallelitäts Fehler zu finden.

## <a name="general-guidelines"></a>Allgemeine Richtlinien

Mithilfe von Anmerkungen können Sie die Verträge, die durch Funktionsdefinitionen zwischen Implementierungen (Callees) und Clients (Aufrufer) impliziert werden, sowie Express invarianten und andere Eigenschaften des Programms angeben, die die Analyse weiter verbessern können.

SAL unterstützt viele verschiedene Arten von Sperr primitiven – z. b. kritische Abschnitte, Mutexen, Spin-Sperren und andere Ressourcen Objekte. Viele Parallelitäts Anmerkungen nehmen einen Sperr Ausdruck als Parameter an. Gemäß der Konvention wird eine Sperre durch den Pfad Ausdruck des zugrunde liegenden Sperr Objekts bezeichnet.

Einige Thread Besitz Regeln, die berücksichtigt werden sollten:

- Dreh Sperren sind nicht gezählte sperren, die den Thread Besitz löschen.

- Mutexen und wichtige Abschnitte sind gezählte Sperren mit einem eindeutigen Thread Besitz.

- Semaphore und Ereignisse sind gezählte sperren, die keinen eindeutigen Thread Besitz aufweisen.

## <a name="locking-annotations"></a>Sperren von Anmerkungen

In der folgenden Tabelle sind die Sperr Anmerkungen aufgeführt.

|Anmerkung|BESCHREIBUNG|
|----------------|-----------------|
|`_Acquires_exclusive_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass die Funktion im Post-Zustand um eine exklusive Sperrenanzahl des Sperr Objekts erhöht wird, das durch `expr`benannt wird.|
|`_Acquires_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass die Funktion im Post-Zustand um einen Schritt um die Sperrenanzahl des Sperr Objekts erhöht wird, das durch `expr`benannt wird.|
|`_Acquires_nonreentrant_lock_(expr)`|Die von `expr` benannte Sperre wird abgerufen.  Wenn die Sperre bereits besteht, wird ein Fehler gemeldet.|
|`_Acquires_shared_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass die Funktion im Post-Zustand um eine Anzahl der freigegebenen Sperren des Sperr Objekts, das von `expr`benannt wird, inkreliert wird.|
|`_Create_lock_level_(name)`|Eine Anweisung, die das Symbol deklariert, `name` eine Sperr Ebene sein kann, damit Sie in den Anmerkungen `_Has_Lock_level_` und `_Lock_level_order_`verwendet werden kann.|
|`_Has_lock_kind_(kind)`|Kommentiert alle-Objekte, um die Typinformationen eines Ressourcen Objekts zu verfeinern. Manchmal wird ein gemeinsamer Typ für verschiedene Arten von Ressourcen verwendet, und der überladene Typ reicht nicht aus, um die semantischen Anforderungen zwischen verschiedenen Ressourcen zu unterscheiden. Im folgenden finden Sie eine Liste vordefinierter `kind` Parameter:<br /><br /> `_Lock_kind_mutex_`<br /> Sperrenkind-ID für Mutexes.<br /><br /> `_Lock_kind_event_`<br /> Sperrenkind-ID für Ereignisse.<br /><br /> `_Lock_kind_semaphore_`<br /> Sperrenkind-ID für Semaphore.<br /><br /> `_Lock_kind_spin_lock_`<br /> Sperrenkind-ID für Spin-sperren.<br /><br /> `_Lock_kind_critical_section_`<br /> Sperrenkind-ID für kritische Abschnitte.|
|`_Has_lock_level_(name)`|Kommentiert ein Lock-Objekt und übergibt ihm die Sperr Ebene `name`.|
|`_Lock_level_order_(name1, name2)`|Eine-Anweisung, die die Sperr Anordnung zwischen `name1` und `name2`ermöglicht.  Sperren, die über eine Ebene `name1` verfügen, müssen vor Sperren mit der Ebene `name2`abgerufen werden.|
|`_Post_same_lock_(expr1, expr2)`|Kommentiert eine Funktion und gibt an, dass die beiden sperren, `expr1` und `expr2`im Post-Zustand so behandelt werden, als wären Sie das gleiche Sperr Objekt.|
|`_Releases_exclusive_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass die Funktion im Post-Zustand um eine exklusive Sperrenanzahl des Sperr Objekts, das von `expr`benannt wird, dekreliert.|
|`_Releases_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass die Funktion im Post-Zustand um eine Sperrenanzahl des Sperr Objekts, das von `expr`benannt wird, dekreliert.|
|`_Releases_nonreentrant_lock_(expr)`|Die Sperre, die von `expr` benannt wird, wird freigegeben. Wenn die Sperre derzeit nicht aufrechterhalten wird, wird ein Fehler gemeldet.|
|`_Releases_shared_lock_(expr)`|Kommentiert eine Funktion und gibt an, dass die Funktion im Post-Zustand um einen Wert für die Anzahl der freigegebenen Sperren des Sperr Objekts, das von `expr`benannt wird, verringert.|
|`_Requires_lock_held_(expr)`|Kommentiert eine Funktion und gibt an, dass die Sperrenanzahl des Objekts, das von `expr` benannt ist, mindestens eins ist.|
|`_Requires_lock_not_held_(expr)`|Kommentiert eine Funktion und gibt an, dass die Sperrenanzahl des Objekts, das von `expr` benannt ist, in der vorab Zustand 0 (null) ist.|
|`_Requires_no_locks_held_`|Kommentiert eine Funktion und gibt an, dass die Sperr Anzahl aller Sperren, die der Prüfung bekannt sind, 0 (null) ist.|
|`_Requires_shared_lock_held_(expr)`|Kommentiert eine Funktion und gibt an, dass die freigegebene Sperrenanzahl des Objekts, das von `expr` benannt ist, mindestens eins ist.|
|`_Requires_exclusive_lock_held_(expr)`|Kommentiert eine Funktion und gibt an, dass im Voraus die exklusive Sperr Anzahl des Objekts, das von `expr` benannt ist, mindestens eins ist.|

## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>Systeminterne SAL-Funktionen für nicht verfügbare Sperrobjekte

Bestimmte Sperrobjekte werden von der Implementierung der zugehörigen Sperr Funktionen nicht verfügbar gemacht.  In der folgenden Tabelle werden die systeminternen SAL-Variablen aufgelistet, die Anmerkungen für Funktionen ermöglichen, die für diese nicht verfügbar gemachten Sperrobjekte verwendet werden.

|Anmerkung|BESCHREIBUNG|
|----------------|-----------------|
|`_Global_cancel_spin_lock_`|Beschreibt die Abbruch Drehsperre.|
|`_Global_critical_region_`|Beschreibt den kritischen Bereich.|
|`_Global_interlock_`|Beschreibt Interlocked-Vorgänge.|
|`_Global_priority_region_`|Beschreibt den Prioritäts Bereich.|

## <a name="shared-data-access-annotations"></a>Anmerkungen zum freigegebenen Datenzugriff

In der folgenden Tabelle sind die Anmerkungen für den Zugriff auf freigegebene Daten aufgeführt.

|Anmerkung|BESCHREIBUNG|
|----------------|-----------------|
|`_Guarded_by_(expr)`|Kommentiert eine Variable und gibt an, dass bei jedem Zugriff auf die Variable die Sperrenanzahl des Sperr Objekts, das von `expr` benannt wird, mindestens eins ist.|
|`_Interlocked_`|Kommentiert eine Variable und entspricht `_Guarded_by_(_Global_interlock_)`.|
|`_Interlocked_operand_`|Der mit Anmerkungen versehene Funktionsparameter ist der Ziel Operand einer der verschiedenen Interlocked-Funktionen.  Diese Operanden müssen über bestimmte zusätzliche Eigenschaften verfügen.|
|`_Write_guarded_by_(expr)`|Kommentiert eine Variable und gibt an, dass bei jeder Änderung der Variablen die Sperrenanzahl des Sperr Objekts, das von `expr` benannt ist, mindestens eins ist.|

## <a name="smart-lock-and-raii-annotations"></a>Smart Lock-und RAII-Anmerkungen

Smart Locks wrappen in der Regel Native Sperren und verwalten ihre Lebensdauer. In der folgenden Tabelle werden Anmerkungen aufgelistet, die mit intelligenten Sperren und RAII-Codierungs Mustern mit Unterstützung für `move` Semantik verwendet werden können.

|Anmerkung|BESCHREIBUNG|
|----------------|-----------------|
|`_Analysis_assume_smart_lock_acquired_`|Weist den Analyzer an, zu übernehmen, dass eine Smart Lock abgerufen wurde. Diese Anmerkung erwartet einen verweissperrentyp als Parameter.|
|`_Analysis_assume_smart_lock_released_`|Weist den Analyzer an, zu übernehmen, dass eine Smart Lock freigegeben wurde. Diese Anmerkung erwartet einen verweissperrentyp als Parameter.|
|`_Moves_lock_(target, source)`|Beschreibt `move constructor` Vorgang, der den Sperr Zustand vom `source`-Objekt an den `target`überträgt. Der `target` wird als neu konstruiertes Objekt betrachtet, sodass jeder Zustand, der zuvor aufgetreten ist, verloren geht und durch den `source` Status ersetzt wird. Die `source` wird auch auf einen sauberen Zustand zurückgesetzt, der keine Sperr Anzahl oder kein Alias Ziel aufweist, aber Aliase, die darauf zeigen, bleiben unverändert.|
|`_Replaces_lock_(target, source)`|Beschreibt `move assignment operator` Semantik, bei der die Ziel Sperre freigegeben wird, bevor der Status aus der Quelle übertragen wird. Dies kann als eine Kombination von `_Moves_lock_(target, source)` angesehen werden, denen ein `_Releases_lock_(target)`vorangestellt ist.|
|`_Swaps_locks_(left, right)`|Beschreibt das Standard `swap` Verhalten, bei dem davon ausgegangen wird, dass-Objekte `left` und `right` ihren Zustand austauschen. Der ausgetauschte Status umfasst ggf. Sperr Anzahl und Aliasing-Ziel. Aliase, die auf die `left` und `right` Objekte zeigen, bleiben unverändert.|
|`_Detaches_lock_(detached, lock)`|Beschreibt ein Szenario, in dem ein Lock Wrapper Type die Trennung der enthaltenen Ressource zulässt. Dies ähnelt der Funktionsweise von `std::unique_ptr` mit dem internen Zeiger: Sie ermöglicht es Programmierern, den Zeiger zu extrahieren und den intelligenten Zeiger Container in einem sauberen Zustand zu belassen. Eine ähnliche Logik wird von `std::unique_lock` unterstützt und kann in benutzerdefinierten sperrwrappern implementiert werden. Die getrennte Sperre behält ihren Zustand (sofern vorhanden) bei, während der Wrapper zurückgesetzt wird, sodass er keine Sperr Anzahl und kein Alias Ziel enthält, während seine eigenen Aliase beibehalten werden. Es gibt keinen Vorgang für Sperr Zählungen (freigeben und erwerben). Diese Anmerkung verhält sich genau wie `_Moves_lock_`, mit der Ausnahme, dass das getrennte Argument `return` und nicht `this`sein sollte.|

## <a name="see-also"></a>Weitere Informationen

- [Verwenden von SAL-Anmerkungen zum Reduzieren von C/C++-Codefehlern](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Einführung in SAL](../code-quality/understanding-sal.md)
- [Hinzufügen einer Anmerkung zu Funktionsparametern und Rückgabewerten](../code-quality/annotating-function-parameters-and-return-values.md)
- [Hinzufügen einer Anmerkung zum Funktionsverhalten](../code-quality/annotating-function-behavior.md)
- [Hinzufügen einer Anmerkung zu Strukturen und Klassen](../code-quality/annotating-structs-and-classes.md)
- [Angeben, wann und wo eine Anmerkung gültig ist](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Systeminterne Funktionen](../code-quality/intrinsic-functions.md)
- [Empfohlene Vorgehensweisen und Beispiele](../code-quality/best-practices-and-examples-sal.md)
- [Blog des Code Analyseteams](https://blogs.msdn.microsoft.com/codeanalysis/)

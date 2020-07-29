---
title: 1. Einführung
ms.date: 01/16/2019
ms.assetid: c42e72bc-0e31-4b1c-b670-cd82673c0c5a
ms.openlocfilehash: 60a5090814b722cc0d9f6e51ab9038e697a4ed2a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231649"
---
# <a name="1-introduction"></a>1. Einführung

Dieses Dokument gibt eine Auflistung von Compilerdirektiven, Bibliotheksfunktionen und Umgebungsvariablen an, die Sie verwenden können, um Parallelität für freigegebenen Arbeitsspeicher in C-und C++-Programmen anzugeben. Die in diesem Dokument beschriebene Funktionalität wird zusammen als " *OpenMP C/C++ Application Program Interface (API)*" bezeichnet. Das Ziel dieser Spezifikation besteht darin, ein Modell für die parallele Programmierung bereitzustellen, mit dem ein Programm über freigegebene Arbeitsspeicher Architekturen von unterschiedlichen Anbietern portierbar sein kann. Compiler von vielen Anbietern unterstützen die OpenMP-C/C++-API. Weitere Informationen zu OpenMP, einschließlich der *OpenMP Fortran-Anwendungsprogramm Schnittstelle*, finden Sie auf der folgenden Website:

[https://www.openmp.org](https://www.openmp.org)

Die in diesem Dokument definierten Anweisungen, Bibliotheksfunktionen und Umgebungsvariablen ermöglichen es Ihnen, parallele Programme zu erstellen und zu verwalten, während Sie Portabilität zulassen. Durch die-Direktiven wird das C-und C++-Programmiermodell mit einem einzelnen Programm mit mehreren Daten (SPMD), Arbeits Freigabe-Konstrukten und Synchronisierungskonstrukten erweitert. Außerdem unterstützen Sie die Freigabe und die Privatisierung von Daten. Compiler, die die OpenMP C-und C++-API unterstützen, enthalten eine Befehlszeilenoption für den Compiler, die aktiviert und die Interpretation aller OpenMP-Compilerdirektiven zulässt.

## <a name="11-scope"></a>1.1 Bereich

Diese Spezifikation behandelt nur die benutzergesteuerte Parallelisierung, bei der Sie explizit definieren, welche Aktionen der Compiler und das Laufzeitsystem ausführen, um das Programm parallel auszuführen. OpenMP C-und C++-Implementierungen sind nicht erforderlich, um auf Abhängigkeiten, Konflikte, Deadlocks, Racebedingungen oder andere Probleme zu überprüfen, die zu einer falschen Programmausführung führen. Sie müssen sicherstellen, dass die Anwendung, die die API-Konstrukte von OpenMP C und C++ verwendet, ordnungsgemäß ausgeführt wird. Vom Compiler generierte automatische Parallelisierung und Anweisungen an den Compiler, um diese Parallelisierung zu unterstützen, wird in diesem Dokument nicht behandelt.

## <a name="12-definition-of-terms"></a>1,2 Definition von Begriffen

In diesem Dokument werden die folgenden Begriffe verwendet:

- barrier

  Ein Synchronisierungs Punkt, der von allen Threads in einem Team erreicht werden muss.  Jeder Thread wartet, bis alle Threads im Team an diesem Punkt eintreffen. Es gibt explizite Barrieren, die durch Anweisungen und implizite Barrieren identifiziert werden, die von der-Implementierung erstellt werden.

- Konstrukt

  Ein Konstrukt ist eine-Anweisung. Sie besteht aus einer-Direktive, gefolgt von einem strukturierten-Block. Einige-Anweisungen sind nicht Teil eines-Konstrukts. (Siehe " *OpenMP-Directive* " in [Anhang C](c-openmp-c-and-cpp-grammar.md)).

- Anweisung

  Ein C-oder C++ `#pragma` -Wert, gefolgt von dem `omp` Bezeichner, dem anderen Text und einer neuen Zeile. Die-Direktive gibt das Programmverhalten an.

- dynamischer Block

  Alle Anweisungen im *lexikalischen*Block sowie jede Anweisung innerhalb einer Funktion, die als Ergebnis der Ausführung von Anweisungen innerhalb des lexikalischen Wertebereichs ausgeführt wird. Ein dynamischer Block wird auch als *Region*bezeichnet.

- lexikalischer Block

  -Anweisungen, die lexikalisch in einem *strukturierten Block*gespeichert sind.

- Master Thread

  Der Thread, der ein Team erstellt, wenn ein *paralleler Bereich* eingegeben wird.

- paralleler Bereich

  Anweisungen, die an ein paralleles OpenMP-Konstrukt gebunden werden und von vielen Threads ausgeführt werden können.

- private

  Eine private Variable benennt einen Speicherblock, der für den Thread eindeutig ist, der den Verweis durchführen soll. Es gibt mehrere Möglichkeiten, anzugeben, dass eine Variable privat ist: eine Definition innerhalb eines parallelen Bereichs, eine-Direktive, eine-,-,- `threadprivate` `private` oder- `firstprivate` `lastprivate` `reduction` Klausel oder die Verwendung der Variablen als **`for`** Schleifen Steuerungs Variable in einer **`for`** Schleife direkt nach einer- `for` oder- `parallel for` Direktive.

- region

  Ein dynamischer Block.

- serielle Region

  Anweisungen, die nur vom *Master Thread* außerhalb des dynamischen Umfangs eines beliebigen *parallelen Bereichs*ausgeführt werden.

- serialize

  So führen Sie ein paralleles Konstrukt mit aus:

  - ein Team von Threads, das nur aus einem einzigen Thread besteht (der Haupt Thread für das parallele Konstrukt),

  - serielle Reihenfolge der Ausführung für die Anweisungen innerhalb des strukturierten Blocks (dieselbe Reihenfolge, als wäre der Block nicht Teil eines parallelen Konstrukts), und

  - keine Auswirkung auf den Wert, der von zurückgegeben wird `omp_in_parallel()` (abgesehen von den Auswirkungen der schachtelten parallelen Konstrukte).

- Freigegeben

  Eine freigegebene Variable benennt einen einzelnen Speicherblock. Alle Threads in einem Team, die auf diese Variable zugreifen, greifen auch auf diesen einzelnen Speicherblock zu.

- strukturierter Block

  Ein strukturierter Block ist eine-Anweisung (Single oder Verbund), die über einen einzelnen Eintrag und einen einzelnen Exit verfügt. Wenn ein Sprung in eine oder aus einer-Anweisung erfolgt, ist diese Anweisung ein strukturierter Block. (Diese Regel enthält einen `longjmp` -Befehl. (3C) oder die Verwendung von `throw` , obwohl ein-Rückruf `exit` zulässig ist.) Wenn die Ausführung immer beim Öffnen beginnt `{` und immer am schließenden endet `}` , ist eine Verbund Anweisung ein strukturierter Block. Eine Ausdrucks Anweisung, eine Auswahl Anweisung, eine Iterations Anweisung oder **`try`** ein Block ist ein strukturierter Block, wenn die entsprechende Verbund Anweisung, die durch das einschließen in `{` und abgerufen wird, `}` ein strukturierter Block wäre. Eine Jump-Anweisung, eine Anweisung mit der Bezeichnung oder eine Deklarations Anweisung ist kein strukturierter Block.

- Team

  Ein oder mehrere Threads, die bei der Ausführung eines-Konstrukts zusammenarbeiten.

- Thread

  Eine Ausführungs Entität mit einem seriellen Ablauf Steuerungs Fluss, einem Satz privater Variablen und dem Zugriff auf freigegebene Variablen.

- Variable

  Ein Bezeichner, der optional von Namespace Namen qualifiziert wird und ein Objekt benennt.

## <a name="13-execution-model"></a>1,3-Ausführungs Modell

OpenMP verwendet das Fork-Join-Modell der parallelen Ausführung. Obwohl dieses Fork-Join-Modell nützlich sein kann, um verschiedene Probleme zu lösen, ist es auf große Array basierte Anwendungen zugeschnitten. OpenMP soll Programme unterstützen, die sowohl als parallele Programme (viele Ausführungs Threads als auch als vollständige OpenMP-Unterstützungs Bibliothek) ordnungsgemäß ausgeführt werden. Es handelt sich auch um Programme, die ordnungsgemäß als sequenzielle Programme ausgeführt werden (Direktiven werden ignoriert und eine einfache OpenMP-stubbibliothek). Es ist jedoch möglich und zulässig, ein Programm zu entwickeln, das sich bei der sequenziellen Ausführung nicht ordnungsgemäß verhält. Außerdem können unterschiedliche Grad an Parallelität aufgrund von Änderungen bei der Zuordnung numerischer Vorgänge zu unterschiedlichen numerischen Ergebnissen führen. Beispielsweise kann die Verringerung der seriellen Addition ein anderes Muster für Additions Zuordnungen aufweisen als eine parallele Reduzierung. Diese unterschiedlichen Zuordnungen können die Ergebnisse der Gleit Komma Addition ändern.

Ein mit der OpenMP-C/C++-API geschriebenes Programm beginnt mit der Ausführung als einzelner Ausführungs Thread, der als *Haupt Thread*bezeichnet wird. Der Master Thread wird in einem seriellen Bereich ausgeführt, bis das erste parallele Konstrukt gefunden wird. In der OpenMP-C/C++-API `parallel` stellt die-Direktive ein paralleles Konstrukt dar. Wenn ein paralleles Konstrukt gefunden wird, erstellt der Master Thread ein Thread Team, und der Master wird der Master des Teams. Jeder Thread im Team führt die Anweisungen im dynamischen Bereich eines parallelen Bereichs aus, mit Ausnahme der Arbeits Freigabe-Konstrukte. Alle Threads im Team müssen Arbeits Freigabe Konstrukte in derselben Reihenfolge erkennen, und mindestens ein Thread führt die Anweisungen im zugeordneten strukturierten Block aus. Die Grenze, die am Ende eines Arbeits Freigabe Aufbaus ohne eine- `nowait` Klausel impliziert ist, wird von allen Threads im Team ausgeführt.

Wenn ein Thread ein frei gegebenes Objekt ändert, wirkt sich dies nicht nur auf seine eigene Ausführungsumgebung aus, sondern auch auf die anderen Threads im Programm. Die Änderung wird garantiert von der Sicht eines anderen Threads bis zum nächsten Sequenz Punkt (wie in der Basis Sprache definiert) vervollständigt, wenn das Objekt als flüchtig deklariert wird. Andernfalls wird die Änderung nach dem ersten Ändern des Threads garantiert fertiggestellt. Die anderen Threads (oder gleichzeitig) sehen eine `flush` Direktive, die das Objekt angibt (entweder implizit oder explizit). Wenn die `flush` Direktiven, die von anderen OpenMP-Direktiven impliziert werden, nicht die richtige Reihenfolge von Nebeneffekten gewährleisten, ist es für den Programmierer zuständig, zusätzliche explizite `flush` Direktiven bereitzustellen.

Nach Abschluss des parallelen Konstrukts werden die Threads im Team an einer impliziten Barriere synchronisiert, und nur der Master Thread setzt die Ausführung fort. Eine beliebige Anzahl paralleler Konstrukte kann in einem einzelnen Programm angegeben werden. Folglich kann ein Programm während der Ausführung mehrmals verzweigen und beitreten.

Die OpenMP C/C++-API ermöglicht Programmierern die Verwendung von-Direktiven in Funktionen, die aus parallelen Konstrukten aufgerufen werden. Direktiven, die nicht im lexikalischen Bereich eines parallelen Konstrukts angezeigt werden, aber möglicherweise im dynamischen Block liegen, werden als *verwaiste* Direktiven bezeichnet. Mit verwaisten Direktiven können Programmierer wichtige Teile des Programms parallel ausführen, wobei nur minimale Änderungen am sequenziellen Programm vorgenommen werden. Mit dieser Funktion können Sie parallele Konstrukte auf den obersten Ebenen der Programmaufruf Struktur codieren und Direktiven verwenden, um die Ausführung in einer der aufgerufenen Funktionen zu steuern.

Nicht synchronisierte Aufrufe von C-und C++-Ausgabefunktionen, die in die gleiche Datei schreiben, können zu einer Ausgabe führen, in der von verschiedenen Threads geschriebene Daten in nicht deterministischer Reihenfolge angezeigt werden. Ebenso können nicht synchronisierte Aufrufe von Eingabefunktionen, die aus derselben Datei lesen, Daten in nicht deterministischer Reihenfolge lesen. Nicht synchronisierte Verwendung von e/a-Vorgängen, sodass jeder Thread auf eine andere Datei zugreift, erzeugt dieselben Ergebnisse wie die serielle Ausführung der e/a-Funktionen.

## <a name="14-compliance"></a>1.4 Kompatibilität

Eine Implementierung der OpenMP-C/C++-API ist *OpenMP-kompatibel* , wenn Sie die Semantik aller Elemente dieser Spezifikation erkennt und beibehält, wie in den Kapiteln 1, 2, 3, 4 und Anhang C dargelegt. Appendices A, B, D, E und F dienen nur zu Informationszwecken und sind nicht Teil der Spezifikation. Implementierungen, die nur eine Teilmenge der API einschließen, sind nicht mit OpenMP kompatibel.

Die OpenMP C-und C++-API ist eine Erweiterung der Basis Sprache, die von einer-Implementierung unterstützt wird. Wenn die Basis Sprache kein Sprachkonstrukt oder eine Erweiterung unterstützt, die in diesem Dokument angezeigt wird, ist die OpenMP-Implementierung nicht erforderlich, um Sie zu unterstützen.

Alle standardmäßigen C-und C++-Bibliotheksfunktionen und integrierten Funktionen (d. h. Funktionen, von denen der Compiler über bestimmte Kenntnisse verfügt) müssen Thread sicher sein. Die nicht synchronisierte Verwendung Thread sicherer Funktionen durch verschiedene Threads in einem parallelen Bereich führt nicht zu undefiniertem Verhalten. Das Verhalten ist jedoch möglicherweise nicht identisch mit dem in einem seriellen Bereich. (Eine Funktion der Zufallszahlengenerierung ist ein Beispiel.)

Die OpenMP C/C++-API gibt an, dass ein bestimmtes Verhalten von der *Implementierung definiert ist.* Eine konforme OpenMP-Implementierung ist erforderlich, um das Verhalten in diesen Fällen zu definieren und zu dokumentieren. Eine Liste der durch die Implementierung definierten Verhalten finden Sie in [Anhang E](e-implementation-defined-behaviors-in-openmp-c-cpp.md).

## <a name="15-normative-references"></a>1,5 normative Verweise

- ISO/IEC 9899:1999, *Informationstechnologie-Programmiersprachen-C*. Diese OpenMP-API-Spezifikation bezieht sich auf ISO/IEC 9899:1999 als C99.

- ISO/IEC 9899:1990, *Informationstechnologie-Programmiersprachen-C*. Diese OpenMP-API-Spezifikation bezieht sich auf ISO/IEC 9899:1990 als C90.

- ISO/IEC 14882:1998, *Informationstechnologie-Programmiersprachen-C++*. Diese OpenMP-API-Spezifikation bezieht sich auf ISO/IEC 14882:1998 als C++.

Wenn diese OpenMP-API-Spezifikation auf C verweist, wird auf die Basis Sprache verwiesen, die von der-Implementierung unterstützt wird.

## <a name="16-organization"></a>1.6 Organization

- [Funktionen der Runtimebibliothek](3-run-time-library-functions.md)
- [Umgebungsvariablen](4-environment-variables.md)
- [Durch die Implementierung definiertes Verhalten in OpenMP (C/C++)](e-implementation-defined-behaviors-in-openmp-c-cpp.md)
- [Neue Features in OpenMP C/C++ Version 2,0](f-new-features-and-clarifications-in-version-2-0.md)

---
title: Übersicht über Module in C++
ms.date: 12/13/2019
helpviewer_keywords:
- modules [C++]
- modules [C++], overview
description: Module in c++ 20 stellen eine moderne Alternative zu Header Dateien dar.
ms.openlocfilehash: 286d2ec8a26dbd0a85e8f8721ad6fd7f12f45a31
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078039"
---
# <a name="overview-of-modules-in-c"></a>Übersicht über Module in C++

C++ 20 führt *Module*ein, eine moderne Lösung für die Komponentisierung C++ von Bibliotheken und Programmen. Ein Modul ist ein Satz von Quell Code Dateien, die unabhängig von den [Übersetzungseinheiten](https://wikipedia.org/wiki/Translation_unit_(programming)) kompiliert werden, die Sie importieren. Module eliminieren viele der Probleme, die mit der Verwendung von Header Dateien verbunden sind, oder reduzieren Sie erheblich und können auch die Kompilierungszeiten reduzieren. Makros, Präprozessordirektiven und nicht exportierte Namen, die in einem Modul deklariert sind, sind nicht sichtbar und haben daher keine Auswirkungen auf die Kompilierung der Übersetzungseinheit, die das Modul importiert. Sie können Module in beliebiger Reihenfolge importieren, ohne dass Makro Neudefinitionen berücksichtigt werden. Deklarationen in der importierten Übersetzungseinheit nehmen nicht an der Überladungs Auflösung oder Namenssuche im importierten Modul Teil. Nachdem ein Modul einmal kompiliert wurde, werden die Ergebnisse in einer Binärdatei gespeichert, in der alle exportierten Typen, Funktionen und Vorlagen beschrieben werden. Diese Datei kann viel schneller verarbeitet werden als eine Header Datei und kann vom Compiler an jedem Ort wieder verwendet werden, an dem das Modul in ein Projekt importiert wird.

Module können nebeneinander mit Header Dateien verwendet werden. Eine C++ Quelldatei kann Module und auch #include Header Dateien importieren. In einigen Fällen kann eine Header Datei als Modul importiert werden, anstatt textuell #included durch den Präprozessor. Es wird empfohlen, dass neue Projekte Module anstelle von Header Dateien so weit wie möglich verwenden. Für größere vorhandene Projekte, die sich in der aktiven Entwicklung befinden, empfiehlt es sich, mit der Umstellung von Legacy Headern in Module zu experimentieren, um festzustellen, ob die Kompilierungszeiten eine sinnvolle Reduzierung

## <a name="enable-modules-in-the-microsoft-c-compiler"></a>Aktivieren von Modulen im Microsoft C++ -Compiler

Ab Visual Studio 2019 Version 16,2 sind Module im Microsoft C++ -Compiler nicht vollständig implementiert. Sie können die Module-Funktion verwenden, um einzelne Partitions Module zu erstellen und die von Microsoft bereitgestellten Standard Bibliotheks Module zu importieren. Kompilieren Sie mit [/experimental: Module](../build/reference/experimental-module.md) und [/Std: c + + Latest](../build/reference/std-specify-language-standard-version.md), um die Unterstützung für Module zu aktivieren. Klicken Sie in einem Visual Studio-Projekt in **Projektmappen-Explorer** mit der rechten Maustaste auf den Projekt Knoten, und wählen Sie **Eigenschaften**aus. Legen Sie die Dropdown- **Konfiguration** auf **alle Konfigurationen**fest, und wählen Sie dann **Konfigurations Eigenschaften** > **C++ C/**  > **Sprache** >  **C++ Module aktivieren (experimentell)** .

Ein Modul und der Code, in dem es verwendet wird, müssen mit denselben Compileroptionen kompiliert werden.

## <a name="consume-the-c-standard-library-as-modules"></a>Verwenden der C++ Standard Bibliothek als Module

Obwohl es nicht durch den c++ 20-Standard angegeben ist, ermöglicht Microsoft seine C++ Implementierung der Standardbibliothek als Module. Wenn Sie die C++ Standard Bibliothek als Module importieren, anstatt Sie über Header Dateien #including, können Sie die Kompilierungszeiten abhängig von der Größe Ihres Projekts möglicherweise beschleunigen. Die Bibliothek ist in die folgenden Module integriert:

- Std. Regex stellt den Inhalt der Regex-Header \<>
- Std. File System stellt den Inhalt von Header \<File System >
- Std. Memory stellt den Inhalt von Header \<Arbeitsspeicher bereit >
- Std. Threading bietet den Inhalt von Headern \<Atomic >, \<CONDITION_VARIABLE >, \<zukünftige >, \<Mutex >, \<shared_mutex > und \<Thread >
- Std. Core bietet alles andere in der C++ Standard Bibliothek.

Um diese Module zu verwenden, fügen Sie einfach eine Import Deklaration am Anfang der Quell Code Datei hinzu. Beispiel:

```cpp
import std.core;
import std.regex;
```

Kompilieren Sie das Programm mit den Optionen [/EHsc](../build/reference/eh-exception-handling-model.md) und [/MD](../build/reference/md-mt-ld-use-run-time-library.md) , um das Microsoft-Standard Bibliotheks Modul zu nutzen.

## <a name="basic-example"></a>Einfaches Beispiel

Das folgende Beispiel zeigt eine einfache Modul Definition in einer Quelldatei namens " **foo. IXX**". Die Erweiterung **. IXX** ist für Modulschnittstellen Dateien in Visual Studio erforderlich. In diesem Beispiel enthält die Schnittstellen Datei sowohl die Funktionsdefinition als auch die-Deklaration. Die Definitionen können jedoch auch in eine oder mehrere separate Dateien eingefügt werden (wie in einem späteren Beispiel gezeigt). Die " **Export Module foo** "-Anweisung gibt an, dass diese Datei die primäre Schnittstelle für ein Modul namens "`Foo`" ist. Der **Export** -Modifizierer auf `f()` gibt an, dass diese Funktion sichtbar ist, wenn `Foo` von einem anderen Programm oder Modul importiert wird. Beachten Sie, dass das Modul auf einen Namespace verweist `Bar`.

```cpp
export module Foo;

#define ANSWER 42

namespace Bar
{
   int f_internal() {
        return ANSWER;
      }

   export int f() {
      return f_internal();
   }
}
```

Die Datei **MyProgram. cpp** verwendet die **Import** Deklaration, um auf den Namen zuzugreifen, der von `Foo`exportiert wird. Beachten Sie, dass der Name `Bar` hier sichtbar ist, aber nicht alle Member. Beachten Sie auch, dass das Makro `ANSWER` nicht sichtbar ist.

```cpp

import Foo;
import std.core;

using namespace std;

int main()
{
   cout << "The result of f() is " << Bar::f() << endl; // 42
   // int i = Bar::f_internal(); // C2039
   // int j = ANSWER; //C2065
}

```

Die Import Deklaration kann nur im globalen Gültigkeitsbereich angezeigt werden.

## <a name="implementing-modules"></a>Implementieren von Modulen

Sie können ein Modul mit einer einzelnen Schnittstellen Datei (. IXX) erstellen, die Namen exportiert und Implementierungen aller Funktionen und Typen enthält. Sie können die Implementierungen auch in eine oder mehrere separate Implementierungs Dateien einfügen, ähnlich wie. h-und. cpp-Dateien verwendet werden. Das **Export** Schlüsselwort wird nur in der Schnittstellen Datei verwendet. Eine Implementierungs Datei kann ein anderes Modul **importieren** , aber keine Namen **exportieren** . Implementierungs Dateien können mit einer beliebigen Erweiterung benannt werden. Eine Schnittstellen Datei und der Satz von Implementierungs Dateien, die Sie zurückgibt, werden als eine spezielle Art von Übersetzungseinheit behandelt, die als *Modul Einheit*bezeichnet wird. Ein Name, der in einer beliebigen Implementierungs Datei deklariert wird, wird in allen anderen Dateien in der gleichen Modul Einheit automatisch angezeigt.

Bei größeren Modulen können Sie das Modul in mehrere Modul Einheiten aufteilen, die als *Partitionen*bezeichnet werden. Jede Partition besteht aus einer Schnittstellen Datei, die von einer oder mehreren Implementierungs Dateien unterstützt wird. (Ab Visual Studio 2019 Version 16,2 sind Partitionen noch nicht vollständig implementiert.)

## <a name="modules-namespaces-and-argument-dependent-lookup"></a>Module, Namespaces und Argument abhängige Suche

Die Regeln für Namespaces in Modulen sind identisch mit denen in anderen Code. Wenn eine Deklaration innerhalb eines Namespace exportiert wird, wird der einschließende Namespace (ausgenommen nicht exportierte Member) ebenfalls implizit exportiert. Wenn ein Namespace explizit exportiert wird, werden alle Deklarationen in dieser Namespace Definition exportiert.

Beim Durchführen einer Argument abhängigen Suche für Überladungs Auflösungen in der importierten Übersetzungseinheit berücksichtigt der Compiler Funktionen, die in derselben Übersetzungseinheit (einschließlich Modulschnittstellen) deklariert sind, wie der Typ der Argumente der Funktion. definiert sind.

### <a name="module-partitions"></a>Modul Partitionen

> [!NOTE]
> Dieser Abschnitt wird aus Gründen der Vollständigkeit bereitgestellt. Partitionen sind im Microsoft C++ -Compiler noch nicht implementiert.

Ein Modul kann in *Partitionen*unterteilt werden, die jeweils aus einer Schnittstellen Datei und NULL oder mehr Implementierungs Dateien bestehen. Eine Modul Partition ähnelt einem Modul, mit der Ausnahme, dass Sie den Besitz aller Deklarationen im gesamten Modul freigibt. Alle Namen, die von Partitions Schnittstellen Dateien exportiert werden, werden importiert und von der primären Schnittstellen Datei erneut exportiert. Der Name einer Partition muss mit dem Modulnamen gefolgt von einem Doppelpunkt beginnen. Deklarationen in einer der Partitionen sind innerhalb des gesamten Moduls sichtbar. Zum Vermeiden von ODR-Fehlern (One-Definition-Rule) sind keine besonderen Vorsichtsmaßnahmen erforderlich. Sie können einen Namen (Funktion, Klasse usw.) in einer Partition deklarieren und in einer anderen Partition definieren. Eine Partitions Implementierungs Datei beginnt wie folgt:

```cpp
module Foo:part1
```

die Partitions Schnittstellen Datei beginnt wie folgt:

```cpp
export module Foo:part1
```

Um auf Deklarationen in einer anderen Partition zuzugreifen, muss Sie von einer Partition importiert werden, aber es kann nur der Partitions Name und nicht der Modulname verwendet werden:

```cpp
module Foo:part2;
import :part1;
```

Die primäre Schnittstellen Einheit muss alle Schnittstellen Partitions Dateien des Moduls wie folgt importieren und erneut exportieren:

```cpp
export import :part1
export import :part2
...
```

Die primäre Schnittstellen Einheit kann Partitions Implementierungs Dateien importieren, Sie kann Sie jedoch nicht exportieren, da diese Dateien keine Namen exportieren dürfen. Dies ermöglicht es einem Modul, Implementierungsdetails für das Modul intern beizubehalten.

## <a name="modules-and-header-files"></a>Module und Header Dateien

Sie können Header Dateien in eine Modul Quelldatei einschließen, indem Sie die `#include`-Direktive vor der Modul Deklaration platzieren. Diese Dateien werden als im *globalen Modul Fragment*angesehen. Ein Modul kann nur die Namen im *globalen Modul Fragment* sehen, die sich in den Überschriften befinden, die es explizit einschließt. Das globale Modul Fragment enthält nur Symbole, die tatsächlich verwendet werden.

```cpp
// MyModuleA.cpp

#include "customlib.h"
#include "anotherlib.h"

import std.core;
import MyModuleB;

//... rest of file
```

Sie können eine herkömmliche Header Datei verwenden, um zu steuern, welche Module importiert werden:

```cpp
// MyProgram.h
import std.core;
#ifdef DEBUG_LOGGING
import std.filesystem;
#endif
```

### <a name="imported-header-files"></a>Importierte Header Dateien

> [!NOTE]
> Dieser Abschnitt dient nur zu Informationszwecken. Legacy Importe sind im Microsoft C++ -Compiler noch nicht implementiert.

Einige Header sind ausreichend eigenständig, sodass Sie mit dem **Import** -Schlüsselwort eingefügt werden können. Der Hauptunterschied zwischen einem importierten Header und einem importierten Modul besteht darin, dass alle Präprozessordefinitionen in der Kopfzeile im importierten Programm direkt nach der Import-Anweisung sichtbar sind. (Präprozessordefinitionen in allen Dateien, die in diesem Header enthalten sind, sind *nicht* sichtbar.)

```cpp
import <vector>
import "myheader.h"
```

## <a name="see-also"></a>Weitere Informationen

[Module, Import, Export](import-export-module.md)

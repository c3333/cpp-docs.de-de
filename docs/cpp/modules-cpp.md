---
title: Übersicht über Module in C++
ms.date: 12/13/2019
helpviewer_keywords:
- modules [C++]
- modules [C++], overview
description: Module in C++20 bieten eine moderne Alternative zu Headerdateien.
ms.openlocfilehash: cd45be1dee888c8caeb65b7ff002ac8fee1ecbe1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370759"
---
# <a name="overview-of-modules-in-c"></a>Übersicht über Module in C++

C++20 stellt *Module*vor, eine moderne Lösung für die Komponentenisierung von C++-Bibliotheken und -Programmen. Ein Modul ist ein Satz von Quellcodedateien, die unabhängig von den [Übersetzungseinheiten](https://wikipedia.org/wiki/Translation_unit_(programming)) kompiliert werden, die sie importieren. Module eliminieren oder reduzieren viele der Probleme im Zusammenhang mit der Verwendung von Headerdateien und reduzieren möglicherweise die Kompilierungszeiten. Makros, Präprozessordirektiven und nicht exportierte Namen, die in einem Modul deklariert sind, sind nicht sichtbar und haben daher keine Auswirkungen auf die Kompilierung der Übersetzungseinheit, die das Modul importiert. Sie können Module in beliebiger Reihenfolge importieren, ohne sich um Makroneudefinitionen zu kümmern. Deklarationen in der importierenden Übersetzungseinheit nehmen nicht an der Überladungsauflösung oder der Namenssuche im importierten Modul teil. Nachdem ein Modul einmal kompiliert wurde, werden die Ergebnisse in einer Binärdatei gespeichert, die alle exportierten Typen, Funktionen und Vorlagen beschreibt. Diese Datei kann viel schneller als eine Headerdatei verarbeitet werden und kann vom Compiler an jeder Stelle wiederverwendet werden, an der das Modul in ein Projekt importiert wird.

Module können neben Header-Dateien verwendet werden. Eine C++-Quelldatei kann Module importieren und auch Headerdateien #include. In einigen Fällen kann eine Headerdatei als Modul importiert werden, anstatt vom Präprozessor textlich #included. Es wird empfohlen, dass neue Projekte so viele Module anstelle von Headerdateien wie möglich verwenden. Für größere bestehende Projekte, die sich in aktiver Entwicklung befinden, empfehlen wir Ihnen, mit der Konvertierung von Legacy-Headern in Module zu experimentieren, um zu sehen, ob Sie eine sinnvolle Reduzierung der Kompilierungszeiten erhalten.

## <a name="enable-modules-in-the-microsoft-c-compiler"></a>Aktivieren von Modulen im Microsoft C++-Compiler

Ab Visual Studio 2019 Version 16.2 sind Module im Microsoft C++-Compiler nicht vollständig implementiert. Sie können die Modulfunktion verwenden, um Module mit einer Partition zu erstellen und die von Microsoft bereitgestellten Standardbibliotheksmodule zu importieren. Um die Unterstützung für Module zu aktivieren, kompilieren Sie mit [/experimental:module](../build/reference/experimental-module.md) und [/std:c++latest](../build/reference/std-specify-language-standard-version.md). Klicken Sie in einem Visual Studio-Projekt mit der rechten Maustaste auf den Projektknoten im **Projektmappen-Explorer,** und wählen Sie **Eigenschaften**aus. Legen Sie die **Dropdown-Liste Konfiguration** auf **Alle Konfigurationen**fest, und wählen Sie dann **Konfigurationseigenschaften** > **C/C++** > **Language** > **Enable C++ Modules (experimentell)** aus.

Ein Modul und der Code, der es verwendet, müssen mit denselben Compileroptionen kompiliert werden.

## <a name="consume-the-c-standard-library-as-modules"></a>Verwenden der C++-Standardbibliothek als Module

Obwohl nicht durch den C++20-Standard angegeben, ermöglicht Microsoft das Importieren der Implementierung der C++-Standardbibliothek als Module. Durch importieren Sie die C++-Standardbibliothek als Module, anstatt sie durch Headerdateien #including, und Sie können die Kompilierungszeiten je nach Größe des Projekts möglicherweise beschleunigen. Die Bibliothek ist in die folgenden Module unterteilt:

- std.regex stellt den \<Inhalt von Headerregex>
- std.filesystem stellt den \<Inhalt des Header-Dateisystems>
- std.memory stellt den \<Inhalt des Headerspeichers bereit,>
- std.threading bietet den Inhalt \<von \<Headern, \<die \<>, condition_variable \<>, \<zukünftige>, mutex>, shared_mutex> und Thread->
- std.core bietet alles andere in der C++-Standardbibliothek

Um diese Module zu verwenden, fügen Sie einfach eine Importdeklaration am oberen Rand der Quellcodedatei hinzu. Beispiel:

```cpp
import std.core;
import std.regex;
```

Um das Microsoft Standard Library-Modul zu nutzen, kompilieren Sie Ihr Programm mit den Optionen [/EHsc](../build/reference/eh-exception-handling-model.md) und [/MD.](../build/reference/md-mt-ld-use-run-time-library.md)

## <a name="basic-example"></a>Einfaches Beispiel

Das folgende Beispiel zeigt eine einfache Moduldefinition in einer Quelldatei namens **Foo.ixx**. Die **Erweiterung .ixx** ist für Modulschnittstellendateien in Visual Studio erforderlich. In diesem Beispiel enthält die Schnittstellendatei sowohl die Funktionsdefinition als auch die Deklaration. Die Definitionen können jedoch auch in einer oder mehreren separaten Dateien platziert werden (wie in einem späteren Beispiel gezeigt). Die **Foo-Anweisung des Exportmoduls** gibt an, `Foo`dass diese Datei die primäre Schnittstelle für ein Modul namens ist. Der Exportmodifizierer auf **export** `f()` gibt an, `Foo` dass diese Funktion sichtbar ist, wenn sie von einem anderen Programm oder Modul importiert wird. Beachten Sie, dass das `Bar`Modul auf einen Namespace verweist.

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

Die Datei **MyProgram.cpp** verwendet die Importdeklaration, `Foo`um auf den Namen zuzugreifen, der von exportiert wird. **import** Beachten Sie, `Bar` dass der Name hier sichtbar ist, aber nicht alle mitglieder. Beachten Sie auch, dass das Makro `ANSWER` nicht sichtbar ist.

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

Die Importdeklaration kann nur im globalen Gültigkeitsbereich angezeigt werden.

## <a name="implementing-modules"></a>Implementieren von Modulen

Sie können ein Modul mit einer einzelnen Schnittstellendatei (.ixx) erstellen, die Namen exportiert und Implementierungen aller Funktionen und Typen enthält. Sie können die Implementierungen auch in eine oder mehrere separate Implementierungsdateien eintragen, ähnlich wie .h- und .cpp-Dateien verwendet werden. Das **Exportschlüsselwort** wird nur in der Schnittstellendatei verwendet. Eine Implementierungsdatei kann ein anderes Modul **importieren,** aber keine Namen **exportieren.** Implementierungsdateien können mit einer beliebigen Erweiterung benannt werden. Eine Schnittstellendatei und der Satz von Implementierungsdateien, die sie zurücksetzen, werden als eine spezielle Art von Übersetzungseinheit behandelt, die als *Moduleinheit*bezeichnet wird. Ein Name, der in einer Implementierungsdatei deklariert wird, wird automatisch in allen anderen Dateien innerhalb derselben Moduleinheit angezeigt.

Bei größeren Modulen können Sie das Modul in mehrere Moduleinheiten aufteilen, die *als Partitionen*bezeichnet werden. Jede Partition besteht aus einer Schnittstellendatei, die von einer oder mehreren Implementierungsdateien unterstützt wird. (Ab Visual Studio 2019 Version 16.2 sind Partitionen noch nicht vollständig implementiert.)

## <a name="modules-namespaces-and-argument-dependent-lookup"></a>Module, Namespaces und argumentabhängige Suche

Die Regeln für Namespaces in Modulen sind die gleichen wie in jedem anderen Code. Wenn eine Deklaration innerhalb eines Namespace exportiert wird, wird der einschließende Namespace (ohne nicht exportierte Elemente) ebenfalls implizit exportiert. Wenn ein Namespace explizit exportiert wird, werden alle Deklarationen innerhalb dieser Namespacedefinition exportiert.

Bei der argumentabhängigen Suche nach Überladungsauflösungen in der importierenden Übersetzungseinheit berücksichtigt der Compiler Funktionen, die in derselben Übersetzungseinheit deklariert werden (einschließlich Modulschnittstellen), als den Ort, an dem der Typ der Argumente der Funktion definiert ist.

### <a name="module-partitions"></a>Modulpartitionen

> [!NOTE]
> Dieser Abschnitt ist der Vollständigkeit geraubjahre zur Verfügung gestellt. Partitionen sind im Microsoft C++-Compiler noch nicht implementiert.

Ein Modul kann in Partitionen komponentenisiert werden, die jeweils aus einer Schnittstellendatei und null oder mehr *Implementierungsdateien*bestehen. Eine Modulpartition ähnelt einem Modul, mit der Ausnahme, dass sie den Besitz aller Deklarationen im gesamten Modul teilt. Alle Namen, die von Partitionsschnittstellendateien exportiert werden, werden von der primären Schnittstellendatei importiert und erneut exportiert. Der Name einer Partition muss mit dem Modulnamen gefolgt von einem Doppelpunkt beginnen. Deklarationen in einer der Partitionen sind innerhalb des gesamten Moduls sichtbar. Es sind keine besonderen Vorsichtsmaßnahmen erforderlich, um Fehler in der Ein-Definition-Regel (ODR) zu vermeiden. Sie können einen Namen (Funktion, Klasse usw.) in einer Partition deklarieren und in einer anderen Partition definieren. Eine Partitionsimplementierungsdatei beginnt wie folgt:

```cpp
module Foo:part1
```

und die Partitionsschnittstellendatei beginnt wie folgt:

```cpp
export module Foo:part1
```

Um auf Deklarationen in einer anderen Partition zuzugreifen, muss eine Partition sie importieren, kann jedoch nur den Partitionsnamen und nicht den Modulnamen verwenden:

```cpp
module Foo:part2;
import :part1;
```

Die primäre Schnittstelleneinheit muss alle Schnittstellenpartitionsdateien des Moduls wie folgt importieren und erneut exportieren:

```cpp
export import :part1
export import :part2
...
```

Die primäre Schnittstelleneinheit kann Partitionsimplementierungsdateien importieren, aber nicht exportieren, da diese Dateien keine Namen exportieren dürfen. Dadurch kann ein Modul Implementierungsdetails intern im Modul aufbewahren.

## <a name="modules-and-header-files"></a>Module und Headerdateien

Sie können Headerdateien in eine Modulquelldatei einschließen, indem Sie die `#include` Direktive vor die Moduldeklaration setzen. Diese Dateien werden als im *globalen Modulfragment*betrachtet. Ein Modul kann nur die Namen im *globalen Modulfragment* sehen, die sich in Headern befinden, die es explizit enthält. Das globale Modulfragment enthält nur Symbole, die tatsächlich verwendet werden.

```cpp
// MyModuleA.cpp

#include "customlib.h"
#include "anotherlib.h"

import std.core;
import MyModuleB;

//... rest of file
```

Sie können eine herkömmliche Headerdatei verwenden, um zu steuern, welche Module importiert werden:

```cpp
// MyProgram.h
import std.core;
#ifdef DEBUG_LOGGING
import std.filesystem;
#endif
```

### <a name="imported-header-files"></a>Importierte Headerdateien

> [!NOTE]
> Dieser Abschnitt ist nur informational. Legacyimporte sind im Microsoft C++-Compiler noch nicht implementiert.

Einige Header sind so in sich geschlossen, dass sie mithilfe des **Schlüsselworts import** eingebracht werden dürfen. Der Hauptunterschied zwischen einem importierten Header und einem importierten Modul besteht darin, dass alle Präprozessordefinitionen im Header unmittelbar nach der Importanweisung im Importprogramm sichtbar sind. (Präprozessordefinitionen in allen Dateien, die von diesem Header enthalten *sind,* sind nicht sichtbar.)

```cpp
import <vector>
import "myheader.h"
```

## <a name="see-also"></a>Siehe auch

[module, import, export](import-export-module.md)

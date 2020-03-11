---
title: 4. Umgebungsvariablen
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: b41829fd9cf2f90312f669ef991f56dda02947f7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882857"
---
# <a name="4-environment-variables"></a>4. Umgebungsvariablen

In diesem Kapitel werden die OpenMP- C++ C-und API-Umgebungsvariablen (oder ähnliche plattformspezifische Mechanismen) beschrieben, die die Ausführung von parallelem Code steuern.  Die Namen der Umgebungsvariablen müssen in Großbuchstaben angegeben werden. Bei den Ihnen zugewiesenen Werten wird die Groß-/Kleinschreibung beachtet, und möglicherweise sind führende und nachfolgende Leerzeichen  Änderungen an den Werten nach dem Start des Programms werden ignoriert.

Die Umgebungsvariablen lauten wie folgt:

- [OMP_SCHEDULE](#41-omp_schedule) legt den Zeit Plantyp für die Laufzeit und die Segmentgröße fest.
- [OMP_NUM_THREADS](#42-omp_num_threads) legt die Anzahl von Threads fest, die während der Ausführung verwendet werden sollen.
- [OMP_DYNAMIC](#43-omp_dynamic) aktiviert oder deaktiviert die dynamische Anpassung der Anzahl von Threads.
- [OMP_NESTED](#44-omp_nested) aktiviert oder deaktiviert die zusammengeführte Parallelität.

Die Beispiele in diesem Kapitel veranschaulichen, wie diese Variablen in UNIX C Shell-Umgebungen (csh) festgelegt werden können. In der Korn-Shell und in den DOS-Umgebungen sind die Aktionen ähnlich:

csh:  
`setenv OMP_SCHEDULE "dynamic"`

ksh:  
`export OMP_SCHEDULE="dynamic"`

Aussprechen  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-omp_schedule"></a>4,1 OMP_SCHEDULE

`OMP_SCHEDULE` gilt nur für `for`-und `parallel for`-Direktiven, die den Zeit Plantyp `runtime`haben. Der Zeit Plantyp und die Blockgröße für all diese Schleifen können zur Laufzeit festgelegt werden. Legen Sie diese Umgebungsvariable auf jeden erkannten Zeit Plantyp und auf eine optionale *chunk_size*fest.

Für `for` und `parallel for` Direktiven, die einen anderen Zeit Plantyp als `runtime`aufweisen, wird `OMP_SCHEDULE` ignoriert. Der Standardwert für diese Umgebungsvariable ist von der Implementierung definiert. Wenn die optionale *chunk_size* festgelegt ist, muss der Wert positiv sein. Wenn *chunk_size* nicht festgelegt ist, wird der Wert 1 angenommen, es sei denn, der Zeitplan ist `static`. Bei einem `static` Zeitplan wird die Standard Segmentgröße auf den Schleifen Iterations Bereich dividiert durch die Anzahl der auf die Schleife angewendeten Threads festgelegt.

Beispiel:

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>Querverweise

- [for](2-directives.md#241-for-construct) -Direktive
- [parallel for](2-directives.md#251-parallel-for-construct) -Direktive

## <a name="42-omp_num_threads"></a>4,2 OMP_NUM_THREADS

Die `OMP_NUM_THREADS`-Umgebungsvariable legt die Standard Anzahl von Threads fest, die während der Ausführung verwendet werden sollen. `OMP_NUM_THREADS` wird ignoriert, wenn diese Zahl explizit durch Aufrufen der `omp_set_num_threads` Bibliotheks Routine geändert wird. Sie wird auch ignoriert, wenn eine explizite `num_threads`-Klausel für eine `parallel` Direktive vorliegt.

Der Wert der `OMP_NUM_THREADS`-Umgebungsvariablen muss eine positive ganze Zahl sein. Seine Auswirkung hängt davon ab, ob die dynamische Anpassung der Thread Anzahl aktiviert ist. Eine umfassende Reihe von Regeln zur Interaktion zwischen der `OMP_NUM_THREADS`-Umgebungsvariablen und der dynamischen Anpassung von Threads finden Sie im [Abschnitt 2,3](2-directives.md#23-parallel-construct).

Die Anzahl der zu verwendenden Threads ist von der Implementierung definiert, wenn Folgendes gilt:

- die `OMP_NUM_THREADS`-Umgebungsvariable ist nicht angegeben.
- der angegebene Wert ist keine positive ganze Zahl, oder
- der Wert ist größer als die maximale Anzahl von Threads, die das System unterstützen kann.

Beispiel:

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>Querverweise

- [num_threads](2-directives.md#23-parallel-construct) -Klausel
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function) -Funktion
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) -Funktion

## <a name="43-omp_dynamic"></a>4,3 OMP_DYNAMIC

Die Umgebungsvariable `OMP_DYNAMIC` aktiviert oder deaktiviert die dynamische Anpassung der Anzahl von Threads, die für die Ausführung paralleler Regionen verfügbar sind. `OMP_DYNAMIC` wird ignoriert, wenn die dynamische Anpassung explizit aktiviert oder deaktiviert wird, indem die `omp_set_dynamic` Bibliotheks Routine aufgerufen wird. Der Wert muss `TRUE` oder `FALSE`sein.

Wenn `OMP_DYNAMIC` auf `TRUE`festgelegt ist, kann die Anzahl der Threads, die für die Ausführung paralleler Regionen verwendet werden, von der Laufzeitumgebung angepasst werden, um die Systemressourcen optimal zu nutzen.  Wenn `OMP_DYNAMIC` auf `FALSE`festgelegt ist, ist die dynamische Anpassung deaktiviert. Die Standard Bedingung ist von der Implementierung definiert.

Beispiel:

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>Querverweise

- [Parallele Bereiche](2-directives.md#23-parallel-construct)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) -Funktion

## <a name="44-omp_nested"></a>4,4 OMP_NESTED

Die `OMP_NESTED`-Umgebungsvariable aktiviert oder deaktiviert die gemutete Parallelität, es sei denn, die gemusterte Parallelität wird durch Aufrufen der `omp_set_nested` Bibliotheks Routine aktiviert oder deaktiviert. Wenn `OMP_NESTED` auf `TRUE`festgelegt ist, wird die unter Aktivierung der Parallelität aktiviert. Wenn `OMP_NESTED` auf `FALSE`festgelegt ist, wird die nicht aktivierte Parallelität deaktiviert. Standardwert: `FALSE`.

Beispiel:

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>Querverweise

- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) -Funktion

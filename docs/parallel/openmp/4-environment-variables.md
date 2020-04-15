---
title: 4. Umgebungsvariablen
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: e93c59654c17ed6dbfb7483ac2dce716ce24b52a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370269"
---
# <a name="4-environment-variables"></a>4. Umgebungsvariablen

In diesem Kapitel werden die OpenMP C- und C++-API-Umgebungsvariablen (oder ähnliche plattformspezifische Mechanismen) beschrieben, die die Ausführung von parallelem Code steuern.  Die Namen von Umgebungsvariablen müssen großbuchstaben sein. Die ihnen zugewiesenen Werte sind nicht berücksichtigt und können einen führenden und nachfolgenden Leerraum aufweisen.  Änderungen an den Werten nach dem Programmstart werden ignoriert.

Die Umgebungsvariablen lauten wie folgt:

- [OMP_SCHEDULE](#41-omp_schedule) legt den Laufzeitzeitplantyp und die Chunkgröße fest.
- [OMP_NUM_THREADS](#42-omp_num_threads) legt die Anzahl der Threads fest, die während der Ausführung verwendet werden sollen.
- [OMP_DYNAMIC](#43-omp_dynamic) aktiviert oder deaktiviert die dynamische Anpassung der Anzahl der Threads.
- [OMP_NESTED](#44-omp_nested) aktiviert oder deaktiviert verschachtelte Parallelität.

Die Beispiele in diesem Kapitel veranschaulichen nur, wie diese Variablen in Unix C-Shell-Umgebungen (csh) festgelegt werden können. In den Korn-Shell- und DOS-Umgebungen sind die Aktionen ähnlich:

Csh:  
`setenv OMP_SCHEDULE "dynamic"`

Ksh:  
`export OMP_SCHEDULE="dynamic"`

Dos:  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-omp_schedule"></a><a name="41-omp_schedule"></a>4.1 OMP_SCHEDULE

`OMP_SCHEDULE`gilt nur `for` `parallel for` für Und-Direktiven mit dem Zeitplantyp `runtime`. Der Zeitplantyp und die Chunk-Größe für alle diese Schleifen können zur Laufzeit festgelegt werden. Legen Sie diese Umgebungsvariable auf einen beliebigen erkannten Zeitplantyp und auf einen optionalen *chunk_size*fest.

Für `for` `parallel for` und Direktiven, die `runtime` `OMP_SCHEDULE` einen anderen Zeitplantyp als haben, werden ignoriert. Der Standardwert für diese Umgebungsvariable ist implementierungsdefiniert. Wenn die optionale *chunk_size* festgelegt ist, muss der Wert positiv sein. Wenn *chunk_size* nicht festgelegt ist, wird ein Wert von 1 `static`angenommen, es sei denn, der Zeitplan ist . Für `static` einen Zeitplan wird die Standardblockgröße auf den Schleifeniterationsraum dividiert durch die Anzahl der Threads festgelegt, die auf die Schleife angewendet werden.

Beispiel:

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>Querverweise

- [für](2-directives.md#241-for-construct) Richtlinie
- [parallel für](2-directives.md#251-parallel-for-construct) die Richtlinie

## <a name="42-omp_num_threads"></a><a name="42-omp_num_threads"></a>4.2 OMP_NUM_THREADS

Die `OMP_NUM_THREADS` Umgebungsvariable legt die Standardanzahl der Threads fest, die während der Ausführung verwendet werden sollen. `OMP_NUM_THREADS`wird ignoriert, wenn diese Nummer `omp_set_num_threads` explizit durch Aufrufen der Bibliotheksroutine geändert wird. Es wird auch ignoriert, wenn `num_threads` es eine `parallel` explizite Klausel für eine Direktive gibt.

Der Wert `OMP_NUM_THREADS` der Umgebungsvariablen muss eine positive ganze Zahl sein. Seine Wirkung hängt davon ab, ob die dynamische Anpassung der Anzahl der Threads aktiviert ist. Einen umfassenden Satz von Regeln über `OMP_NUM_THREADS` die Interaktion zwischen der Umgebungsvariablen und der dynamischen Anpassung von Threads finden Sie in [Abschnitt 2.3](2-directives.md#23-parallel-construct).

Die Anzahl der zu verwendenden Threads ist implementierungsdefiniert, wenn:

- Die `OMP_NUM_THREADS` Umgebungsvariable wird nicht angegeben,
- Der angegebene Wert ist keine positive Ganze Zahl oder
- Der Wert ist größer als die maximale Anzahl von Threads, die das System unterstützen kann.

Beispiel:

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>Querverweise

- [num_threads-Klausel](2-directives.md#23-parallel-construct)
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function) Funktion
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) Funktion

## <a name="43-omp_dynamic"></a><a name="43-omp_dynamic"></a>4.3 OMP_DYNAMIC

Die `OMP_DYNAMIC` Umgebungsvariable aktiviert oder deaktiviert die dynamische Anpassung der Anzahl der Threads, die für die Ausführung paralleler Regionen verfügbar sind. `OMP_DYNAMIC`wird ignoriert, wenn die dynamische Anpassung `omp_set_dynamic` explizit aktiviert oder deaktiviert wird, indem die Bibliotheksroutine aufgerufen wird. Sein Wert `TRUE` muss `FALSE`oder sein.

Wenn `OMP_DYNAMIC` auf `TRUE`festgelegt ist, kann die Anzahl der Threads, die zum Ausführen paralleler Regionen verwendet werden, von der Laufzeitumgebung angepasst werden, um Die Systemressourcen am besten zu nutzen.  Wenn `OMP_DYNAMIC` auf `FALSE`gesetzt ist, ist die dynamische Anpassung deaktiviert. Die Standardbedingung ist implementierungsdefiniert.

Beispiel:

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>Querverweise

- [Parallelregionen](2-directives.md#23-parallel-construct)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) Funktion

## <a name="44-omp_nested"></a><a name="44-omp_nested"></a>4.4 OMP_NESTED

Die `OMP_NESTED` Umgebungsvariable aktiviert oder deaktiviert geschachtelte Parallelität, es sei denn, die geschachtelte Parallelität wird durch Aufrufen der `omp_set_nested` Bibliotheksroutine aktiviert oder deaktiviert. Wenn `OMP_NESTED` auf `TRUE`gesetzt ist, ist die verschachtelte Parallelität aktiviert. Wenn `OMP_NESTED` auf `FALSE`gesetzt ist, ist die verschachtelte Parallelität deaktiviert. Der Standardwert ist `FALSE`.

Beispiel:

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>Querverweis

- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) Funktion

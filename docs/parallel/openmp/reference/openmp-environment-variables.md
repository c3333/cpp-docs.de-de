---
title: OpenMP-Umgebungsvariablen
ms.date: 03/20/2019
f1_keywords:
- OpenMP environment variables
- OMP_DYNAMIC
- OMP_NESTED
- OMP_NUM_THREADS
- OMP_SCHEDULE
helpviewer_keywords:
- OpenMP environment variables
- OMP_DYNAMIC OpenMP environment variable
- OMP_NESTED OpenMP environment variable
- OMP_NUM_THREADS OpenMP environment variable
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
ms.openlocfilehash: 838427320fcb68cedb97b36156fc18002ed962d8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882900"
---
# <a name="openmp-environment-variables"></a>OpenMP-Umgebungsvariablen

Enthält Links zu Umgebungsvariablen, die in der OpenMP-API verwendet werden.

Die visuelle C++ Implementierung von OpenMP Standard umfasst die folgenden Umgebungsvariablen: Diese Umgebungsvariablen werden beim Programmstart gelesen, und Änderungen an ihren Werten werden zur Laufzeit ignoriert (z. b. mit [_putenv _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).

|Umgebungsvariable|BESCHREIBUNG|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|Ändert das Verhalten der [Schedule](openmp-clauses.md#schedule) -Klausel, wenn `schedule(runtime)` in einer `for`-oder `parallel for`-Direktive angegeben wird.|
|[OMP_NUM_THREADS](#omp-num-threads)|Legt die maximale Anzahl von Threads im parallelen Bereich fest, es sei denn, Sie wird von [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) oder [num_threads](openmp-clauses.md#num-threads)überschrieben.|
|[OMP_DYNAMIC](#omp-dynamic)|Gibt an, ob die OpenMP-Laufzeit die Anzahl der Threads in einem parallelen Bereich anpassen kann.|
|[OMP_NESTED](#omp-nested)|Gibt an, ob die unter Verwendung von naktivierung aktiviert ist, es sei denn, die nicht aktivierte Parallelität ist mit `omp_set_nested`aktiviert oder deaktiviert|

## <a name="omp-dynamic"></a>OMP_DYNAMIC

Gibt an, ob die OpenMP-Laufzeit die Anzahl der Threads in einem parallelen Bereich anpassen kann.

```cmd
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>Bemerkungen

Die `OMP_DYNAMIC`-Umgebungsvariable kann von der [omp_set_dynamic](openmp-functions.md#omp-set-dynamic) -Funktion überschrieben werden.

Der Standardwert in der visuellen C++ Implementierung von OpenMP Standard ist `OMP_DYNAMIC=FALSE`.

Weitere Informationen finden Sie unter [4,3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md).

### <a name="example"></a>Beispiel

Mit dem folgenden Befehl wird die `OMP_DYNAMIC`-Umgebungsvariable auf true festgelegt:

```cmd
set OMP_DYNAMIC=TRUE
```

Der folgende Befehl zeigt die aktuelle Einstellung der Umgebungsvariablen `OMP_DYNAMIC` an:

```cmd
set OMP_DYNAMIC
```

## <a name="omp-nested"></a>OMP_NESTED

Gibt an, ob die unter Verwendung von naktivierung aktiviert ist, es sei denn, die nicht aktivierte Parallelität ist mit `omp_set_nested`aktiviert oder deaktiviert

```cmd
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>Bemerkungen

Die `OMP_NESTED`-Umgebungsvariable kann von der [omp_set_nested](openmp-functions.md#omp-set-nested) -Funktion überschrieben werden.

Der Standardwert in der visuellen C++ Implementierung von OpenMP Standard ist `OMP_DYNAMIC=FALSE`.

Weitere Informationen finden Sie unter [4,4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md).

### <a name="example"></a>Beispiel

Mit dem folgenden Befehl wird die `OMP_NESTED`-Umgebungsvariable auf true festgelegt:

```cmd
set OMP_NESTED=TRUE
```

Der folgende Befehl zeigt die aktuelle Einstellung der Umgebungsvariablen `OMP_NESTED` an:

```cmd
set OMP_NESTED
```

## <a name="omp-num-threads"></a>OMP_NUM_THREADS

Legt die maximale Anzahl von Threads im parallelen Bereich fest, es sei denn, Sie wird von [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) oder [num_threads](openmp-clauses.md#num-threads)überschrieben.

```cmd
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>Parameter

*num*<br/>
Die maximale Anzahl von Threads, die im parallelen Bereich angezeigt werden sollen, bis zu 64 in C++ der visuellen Implementierung.

### <a name="remarks"></a>Bemerkungen

Die `OMP_NUM_THREADS`-Umgebungsvariable kann durch die [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) -Funktion oder durch [num_threads](openmp-clauses.md#num-threads)überschrieben werden.

Der Standardwert `num` in der visuellen C++ Implementierung von OpenMP Standard ist die Anzahl der virtuellen Prozessoren, einschließlich der Hyperthreading-CPUs.

Weitere Informationen finden Sie unter [4,2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).

### <a name="example"></a>Beispiel

Mit dem folgenden Befehl wird die `OMP_NUM_THREADS`-Umgebungsvariable auf `16`festgelegt:

```cmd
set OMP_NUM_THREADS=16
```

Der folgende Befehl zeigt die aktuelle Einstellung der Umgebungsvariablen `OMP_NUM_THREADS` an:

```cmd
set OMP_NUM_THREADS
```

## <a name="omp-schedule"></a>OMP_SCHEDULE

Ändert das Verhalten der [Schedule](openmp-clauses.md#schedule) -Klausel, wenn `schedule(runtime)` in einer `for`-oder `parallel for`-Direktive angegeben wird.

```cmd
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>Parameter

*size*<br/>
Optionale Gibt die Größe der Iterationen an. die *Größe* muss eine positive ganze Zahl sein. Der Standardwert ist `1`, es sei denn, der *Typ* ist statisch. Ungültig, wenn der *Typ* `runtime`ist.

*type*<br/>
Die Art der Planung, entweder `dynamic`, `guided`, `runtime`oder `static`.

### <a name="remarks"></a>Bemerkungen

Der Standardwert in der visuellen C++ Implementierung von OpenMP Standard ist `OMP_SCHEDULE=static,0`.

Weitere Informationen finden Sie unter [4,1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md).

### <a name="example"></a>Beispiel

Mit dem folgenden Befehl wird die `OMP_SCHEDULE`-Umgebungsvariable festgelegt:

```cmd
set OMP_SCHEDULE="guided,2"
```

Der folgende Befehl zeigt die aktuelle Einstellung der Umgebungsvariablen `OMP_SCHEDULE` an:

```cmd
set OMP_SCHEDULE
```

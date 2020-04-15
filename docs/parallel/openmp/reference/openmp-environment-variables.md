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
ms.openlocfilehash: bee9b0fbdf147ee962ff92d0b3b9ff57d4209f84
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363887"
---
# <a name="openmp-environment-variables"></a>OpenMP-Umgebungsvariablen

Stellt Links zu Umgebungsvariablen bereit, die in der OpenMP-API verwendet werden.

Die Visual C++-Implementierung des OpenMP-Standards enthält die folgenden Umgebungsvariablen. Diese Umgebungsvariablen werden beim Programmstart gelesen, und Änderungen an ihren Werten werden zur Laufzeit ignoriert (z. B. mit [_putenv, _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).

|Umgebungsvariable|BESCHREIBUNG|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|Ändert das Verhalten der [Schedule-Klausel,](openmp-clauses.md#schedule) `schedule(runtime)` wenn `for` `parallel for` sie in einer oder einer Direktive angegeben ist.|
|[OMP_NUM_THREADS](#omp-num-threads)|Legt die maximale Anzahl von Threads im parallelen Bereich fest, es sei denn, sie werden von [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) oder [num_threads](openmp-clauses.md#num-threads)überschrieben.|
|[OMP_DYNAMIC](#omp-dynamic)|Gibt an, ob die OpenMP-Laufzeit die Anzahl der Threads in einem parallelen Bereich anpassen kann.|
|[OMP_NESTED](#omp-nested)|Gibt an, ob geschachtelte Parallelität aktiviert ist, es sei `omp_set_nested`denn, die geschachtelte Parallelität ist mit aktiviert oder deaktiviert.|

## <a name="omp_dynamic"></a><a name="omp-dynamic"></a>OMP_DYNAMIC

Gibt an, ob die OpenMP-Laufzeit die Anzahl der Threads in einem parallelen Bereich anpassen kann.

```cmd
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>Bemerkungen

Die `OMP_DYNAMIC` Umgebungsvariable kann von der [omp_set_dynamic-Funktion](openmp-functions.md#omp-set-dynamic) überschrieben werden.

Der Standardwert in der Visual C++-Implementierung `OMP_DYNAMIC=FALSE`des OpenMP-Standards ist .

Weitere Informationen finden Sie unter [4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md).

### <a name="example"></a>Beispiel

Mit dem folgenden `OMP_DYNAMIC` Befehl wird die Umgebungsvariable auf TRUE festgelegt:

```cmd
set OMP_DYNAMIC=TRUE
```

Der folgende Befehl zeigt die `OMP_DYNAMIC` aktuelle Einstellung der Umgebungsvariablen an:

```cmd
set OMP_DYNAMIC
```

## <a name="omp_nested"></a><a name="omp-nested"></a>OMP_NESTED

Gibt an, ob geschachtelte Parallelität aktiviert ist, es sei `omp_set_nested`denn, die geschachtelte Parallelität ist mit aktiviert oder deaktiviert.

```cmd
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>Bemerkungen

Die `OMP_NESTED` Umgebungsvariable kann von der [omp_set_nested-Funktion](openmp-functions.md#omp-set-nested) überschrieben werden.

Der Standardwert in der Visual C++-Implementierung `OMP_DYNAMIC=FALSE`des OpenMP-Standards ist .

Weitere Informationen finden Sie unter [4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md).

### <a name="example"></a>Beispiel

Mit dem folgenden `OMP_NESTED` Befehl wird die Umgebungsvariable auf TRUE festgelegt:

```cmd
set OMP_NESTED=TRUE
```

Der folgende Befehl zeigt die `OMP_NESTED` aktuelle Einstellung der Umgebungsvariablen an:

```cmd
set OMP_NESTED
```

## <a name="omp_num_threads"></a><a name="omp-num-threads"></a>OMP_NUM_THREADS

Legt die maximale Anzahl von Threads im parallelen Bereich fest, es sei denn, sie werden von [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) oder [num_threads](openmp-clauses.md#num-threads)überschrieben.

```cmd
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>Parameter

*num*<br/>
Die maximale Anzahl von Threads, die im parallelen Bereich angezeigt werden sollen, bis zu 64 in der Visual C++-Implementierung.

### <a name="remarks"></a>Bemerkungen

Die `OMP_NUM_THREADS` Umgebungsvariable kann von der [omp_set_num_threads-Funktion](openmp-functions.md#omp-set-num-threads) oder von [num_threads](openmp-clauses.md#num-threads)überschrieben werden.

Der Standardwert `num` in der Visual C++-Implementierung des OpenMP-Standards ist die Anzahl der virtuellen Prozessoren, einschließlich Hyperthreading-CPUs.

Weitere Informationen finden Sie unter [4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).

### <a name="example"></a>Beispiel

Mit dem folgenden `OMP_NUM_THREADS` Befehl `16`wird die Umgebungsvariable auf :

```cmd
set OMP_NUM_THREADS=16
```

Der folgende Befehl zeigt die `OMP_NUM_THREADS` aktuelle Einstellung der Umgebungsvariablen an:

```cmd
set OMP_NUM_THREADS
```

## <a name="omp_schedule"></a><a name="omp-schedule"></a>OMP_SCHEDULE

Ändert das Verhalten der [Schedule-Klausel,](openmp-clauses.md#schedule) `schedule(runtime)` wenn `for` `parallel for` sie in einer oder einer Direktive angegeben ist.

```cmd
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>Parameter

*Größe*<br/>
(Optional) Gibt die Größe von Iterationen an. *Größe* muss eine positive ganze Zahl sein. Der Standardwert ist `1`, außer wenn der *Typ* statisch ist. Nicht gültig, `runtime`wenn der *Typ* ist.

*type*<br/>
Die Art der `dynamic`Planung, `runtime`entweder `static`, `guided`, oder .

### <a name="remarks"></a>Bemerkungen

Der Standardwert in der Visual C++-Implementierung `OMP_SCHEDULE=static,0`des OpenMP-Standards ist .

Weitere Informationen finden Sie unter [4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md).

### <a name="example"></a>Beispiel

Mit dem folgenden `OMP_SCHEDULE` Befehl wird die Umgebungsvariable festgelegt:

```cmd
set OMP_SCHEDULE="guided,2"
```

Der folgende Befehl zeigt die `OMP_SCHEDULE` aktuelle Einstellung der Umgebungsvariablen an:

```cmd
set OMP_SCHEDULE
```

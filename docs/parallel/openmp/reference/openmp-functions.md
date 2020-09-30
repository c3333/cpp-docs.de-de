---
title: OpenMP-Funktionen
ms.date: 03/20/2019
f1_keywords:
- OpenMP functions
- omp_destroy_lock
- omp_destroy_nest_lock
- omp_get_dynamic
- omp_get_max_threads
- omp_get_nested
- omp_get_num_procs
- omp_get_num_threads
- omp_get_thread_num
- omp_get_wtick
- omp_get_wtime
- omp_in_parallel
- omp_init_lock
- omp_init_nest_lock
- omp_set_dynamic
- omp_set_lock
- omp_set_nest_lock
- omp_set_nested
- omp_set_num_threads
- omp_test_lock
- omp_test_nest_lock
- omp_unset_lock
- omp_unset_nest_lock
helpviewer_keywords:
- OpenMP functions
- omp_destroy_lock OpenMP function
- omp_destroy_nest_lock OpenMP function
- omp_get_dynamic OpenMP function
- omp_get_max_threads OpenMP function
- omp_get_nested OpenMP function
- omp_get_num_procs OpenMP function
- omp_get_num_threads OpenMP function
- omp_get_thread_num OpenMP function
- omp_get_wtick OpenMP function
- omp_get_wtime OpenMP function
- omp_in_parallel OpenMP function
- omp_init_lock OpenMP function
- omp_init_nest_lock OpenMP function
- omp_set_dynamic OpenMP function
- omp_set_lock OpenMP function
- omp_set_nest_lock OpenMP function
- omp_set_nested OpenMP function
- omp_set_num_threads OpenMP function
- omp_test_lock OpenMP function
- omp_test_nest_lock OpenMP function
- omp_unset_lock OpenMP function
- omp_unset_nest_lock OpenMP function
ms.assetid: a55a2e5c-a260-44ee-bbd6-de7e2351b384
ms.openlocfilehash: 660d786148738c8ce998ad5d78645efdb444ea47
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503695"
---
# <a name="openmp-functions"></a>OpenMP-Funktionen

Enthält Links zu Funktionen, die in der OpenMP-API verwendet werden.

Die Visual C++-Implementierung von OpenMP Standard umfasst die folgenden Funktionen und Datentypen.

Für die Ausführung der Umgebung:

|Funktion|Beschreibung|
|--------|-----------|
|[omp_set_num_threads](#omp-set-num-threads)|Legt die Anzahl der Threads in zukünftigen parallelen Regionen fest, es sei denn, Sie wird von einer [num_threads](openmp-clauses.md#num-threads) -Klausel überschrieben.|
|[omp_get_num_threads](#omp-get-num-threads)|Gibt die Anzahl der Threads im parallelen Bereich zurück.|
|[omp_get_max_threads](#omp-get-max-threads)|Gibt eine ganze Zahl zurück, die gleich oder größer als die Anzahl der Threads ist, die verfügbar sind, wenn ein paralleler Bereich ohne [num_threads](openmp-clauses.md#num-threads) an diesem Punkt im Code definiert wäre.|
|[omp_get_thread_num](#omp-get-thread-num)|Gibt die Thread Nummer des Threads zurück, der innerhalb des Thread Teams ausgeführt wird.|
|[omp_get_num_procs](#omp-get-num-procs)|Gibt die Anzahl der Prozessoren zurück, die verfügbar sind, wenn die-Funktion aufgerufen wird.|
|[omp_in_parallel](#omp-in-parallel)|Gibt einen Wert ungleich 0 (null) zurück, wenn er aus einem parallelen Bereich|
|[omp_set_dynamic](#omp-set-dynamic)|Gibt an, dass die Anzahl der Threads, die in zukünftigen parallelen Regionen verfügbar sind, von der Laufzeit angepasst werden kann.|
|[omp_get_dynamic](#omp-get-dynamic)|Gibt einen Wert zurück, der angibt, ob die Anzahl der Threads, die in zukünftigen parallelen Regionen verfügbar sind, von der Laufzeit angepasst werden kann.|
|[omp_set_nested](#omp-set-nested)|Aktiviert die durch die Aktivierung von Parallelität.|
|[omp_get_nested](#omp-get-nested)|Gibt einen Wert zurück, der angibt, ob die unter Aktivierung der Parallelität aktiviert ist.|

Für Sperre:

|Funktion|Beschreibung|
|--------|-----------|
|[omp_init_lock](#omp-init-lock)|Initialisiert eine einfache Sperre.|
|[omp_init_nest_lock](#omp-init-nest-lock)|Initialisiert eine Sperre.|
|[omp_destroy_lock](#omp-destroy-lock)|Hebt die Initialisierung einer Sperre auf.|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|Hebt die Initialisierung einer nicht stabilen Sperre auf.|
|[omp_set_lock](#omp-set-lock)|Blockiert die Thread Ausführung, bis eine Sperre verfügbar ist.|
|[omp_set_nest_lock](#omp-set-nest-lock)|Blockiert die Thread Ausführung, bis eine Sperre verfügbar ist.|
|[omp_unset_lock](#omp-unset-lock)|Gibt eine Sperre frei.|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|Gibt eine nicht stabile Sperre frei.|
|[omp_test_lock](#omp-test-lock)|Versucht, eine Sperre festzulegen, blockiert jedoch nicht die Thread Ausführung.|
|[omp_test_nest_lock](#omp-test-nest-lock)|Versucht, eine Sperre für eine Sperre festzulegen, blockiert jedoch nicht die Thread Ausführung.|

|Datentyp|Beschreibung|
|---------|-----------|
|`omp_lock_t`|Ein Typ, der den Status einer Sperre enthält, ob die Sperre verfügbar ist oder ob ein Thread eine Sperre besitzt.|
|`omp_nest_lock_t`|Ein Typ, der eines der folgenden Informationen über eine Sperre enthält: gibt an, ob die Sperre verfügbar ist, und die Identität des Threads, der die Sperre besitzt, und eine Schachtelungs Anzahl.|

Für Zeit Steuerungs Routinen:

|Funktion|Beschreibung|
|--------|-----------|
|[omp_get_wtime](#omp-get-wtime)|Gibt einen Wert in Sekunden zurück, der von einem bestimmten Zeitpunkt verstrichen ist.|
|[omp_get_wtick](#omp-get-wtick)|Gibt die Anzahl der Sekunden zwischen Prozessor Takt Einheiten zurück.|

## <a name="omp_destroy_lock"></a><a name="omp-destroy-lock"></a> omp_destroy_lock

Hebt die Initialisierung einer Sperre auf.

```cpp
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*lock*<br/>
Eine Variable vom Typ `omp_lock_t` , die mit [omp_init_lock](#omp-init-lock)initialisiert wurde.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.2.2 omp_destroy_lock und omp_destroy_nest_lock Functions](../3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions).

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von finden Sie unter [omp_init_lock](#omp-init-lock) `omp_destroy_lock` .

## <a name="omp_destroy_nest_lock"></a><a name="omp-destroy-nest-lock"></a> omp_destroy_nest_lock

Hebt die Initialisierung einer nicht stabilen Sperre auf.

```cpp
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*lock*<br/>
Eine Variable vom Typ `omp_nest_lock_t` , die mit [omp_init_nest_lock](#omp-init-nest-lock)initialisiert wurde.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.2.2 omp_destroy_lock und omp_destroy_nest_lock Functions](../3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions).

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von finden Sie unter [omp_init_nest_lock](#omp-init-nest-lock) `omp_destroy_nest_lock` .

## <a name="omp_get_dynamic"></a><a name="omp-get-dynamic"></a> omp_get_dynamic

Gibt einen Wert zurück, der angibt, ob die Anzahl der Threads, die in zukünftigen parallelen Regionen verfügbar sind, von der Laufzeit angepasst werden kann.

```cpp
int omp_get_dynamic();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 bedeutet, dass Threads dynamisch angepasst werden.

### <a name="remarks"></a>Bemerkungen

Die dynamische Anpassung von Threads wird mit [omp_set_dynamic](#omp-set-dynamic) und [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic)angegeben.

Weitere Informationen finden Sie unter [3.1.7 omp_set_dynamic Function](../3-run-time-library-functions.md#317-omp_set_dynamic-function).

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von finden Sie unter [omp_set_dynamic](#omp-set-dynamic) `omp_get_dynamic` .

## <a name="omp_get_max_threads"></a><a name="omp-get-max-threads"></a> omp_get_max_threads

Gibt eine ganze Zahl zurück, die gleich oder größer als die Anzahl der Threads ist, die verfügbar sind, wenn ein paralleler Bereich ohne [num_threads](openmp-clauses.md#num-threads) an diesem Punkt im Code definiert wäre.

```cpp
int omp_get_max_threads( )
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [Funktion "3.1.3 omp_get_max_threads](../3-run-time-library-functions.md#313-omp_get_max_threads-function)".

### <a name="example"></a>Beispiel

```cpp
// omp_get_max_threads.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_num_threads(8);
    printf_s("%d\n", omp_get_max_threads( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_max_threads( ));
        }

    printf_s("%d\n", omp_get_max_threads( ));

    #pragma omp parallel num_threads(3)
        #pragma omp master
        {
            printf_s("%d\n", omp_get_max_threads( ));
        }

    printf_s("%d\n", omp_get_max_threads( ));
}
```

```Output
8
8
8
8
8
```

## <a name="omp_get_nested"></a><a name="omp-get-nested"></a> omp_get_nested

Gibt einen Wert zurück, der angibt, ob die unter Aktivierung der Parallelität aktiviert ist.

```cpp
int omp_get_nested( );
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich 0 (null) bedeutet, dass die Option für die gruppierte Parallelität

### <a name="remarks"></a>Bemerkungen

Die gemusterte Parallelität wird mit [omp_set_nested](#omp-set-nested) und [OMP_NESTED](openmp-environment-variables.md#omp-nested)angegeben.

Weitere Informationen finden Sie unter [3.1.10 omp_get_nested Function](../3-run-time-library-functions.md#3110-omp_get_nested-function).

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von finden Sie unter [omp_set_nested](#omp-set-nested) `omp_get_nested` .

## <a name="omp_get_num_procs"></a><a name="omp-get-num-procs"></a> omp_get_num_procs

Gibt die Anzahl der Prozessoren zurück, die verfügbar sind, wenn die-Funktion aufgerufen wird.

```cpp
int omp_get_num_procs();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.1.5 omp_get_num_procs Function](../3-run-time-library-functions.md#315-omp_get_num_procs-function).

### <a name="example"></a>Beispiel

```cpp
// omp_get_num_procs.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    printf_s("%d\n", omp_get_num_procs( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_procs( ));
        }
}
```

```Output
// Expect the following output when the example is run on a two-processor machine:
2
2
```

## <a name="omp_get_num_threads"></a><a name="omp-get-num-threads"></a> omp_get_num_threads

Gibt die Anzahl der Threads im parallelen Bereich zurück.

```cpp
int omp_get_num_threads( );
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter " [3.1.2 omp_get_num_threads](../3-run-time-library-functions.md#312-omp_get_num_threads-function)"-Funktion.

### <a name="example"></a>Beispiel

```cpp
// omp_get_num_threads.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_num_threads( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_threads( ));
        }

    printf_s("%d\n", omp_get_num_threads( ));

    #pragma omp parallel num_threads(3)
        #pragma omp master
        {
            printf_s("%d\n", omp_get_num_threads( ));
        }

    printf_s("%d\n", omp_get_num_threads( ));
}
```

```Output
1
4
1
3
1
```

## <a name="omp_get_thread_num"></a><a name="omp-get-thread-num"></a> omp_get_thread_num

Gibt die Thread Nummer des Threads zurück, der innerhalb des Thread Teams ausgeführt wird.

```cpp
int omp_get_thread_num( );
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.1.4 omp_get_thread_num Function](../3-run-time-library-functions.md#314-omp_get_thread_num-function).

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von finden Sie unter [parallel](openmp-directives.md#parallel) `omp_get_thread_num` .

## <a name="omp_get_wtick"></a><a name="omp-get-wtick"></a> omp_get_wtick

Gibt die Anzahl der Sekunden zwischen Prozessor Takt Einheiten zurück.

```cpp
double omp_get_wtick( );
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.3.2 omp_get_wtick Funktion](../3-run-time-library-functions.md#332-omp_get_wtick-function).

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von finden Sie unter [omp_get_wtime](#omp-get-wtime) `omp_get_wtick` .

## <a name="omp_get_wtime"></a><a name="omp-get-wtime"></a> omp_get_wtime

Gibt einen Wert in Sekunden zurück, der von einem bestimmten Zeitpunkt verstrichen ist.

```cpp
double omp_get_wtime( );
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert in Sekunden der verstrichenen Zeit von einem beliebigen, aber konsistenten Punkt zurück.

### <a name="remarks"></a>Bemerkungen

Dieser Punkt bleibt während der Programmausführung konsistent, sodass bevorstehende Vergleiche möglich sind.

Weitere Informationen finden Sie unter " [3.3.1 omp_get_wtime](../3-run-time-library-functions.md#331-omp_get_wtime-function)"-Funktion.

### <a name="example"></a>Beispiel

```cpp
// omp_get_wtime.cpp
// compile with: /openmp
#include "omp.h"
#include <stdio.h>
#include <windows.h>

int main() {
    double start = omp_get_wtime( );
    Sleep(1000);
    double end = omp_get_wtime( );
    double wtick = omp_get_wtick( );

    printf_s("start = %.16g\nend = %.16g\ndiff = %.16g\n",
             start, end, end - start);

    printf_s("wtick = %.16g\n1/wtick = %.16g\n",
             wtick, 1.0 / wtick);
}
```

```Output
start = 594255.3671159324
end = 594256.3664474116
diff = 0.9993314791936427
wtick = 2.793651148400146e-007
1/wtick = 3579545
```

## <a name="omp_in_parallel"></a><a name="omp-in-parallel"></a> omp_in_parallel

Gibt einen Wert ungleich 0 (null) zurück, wenn er aus einem parallelen Bereich

```cpp
int omp_in_parallel( );
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.1.6 omp_in_parallel Function](../3-run-time-library-functions.md#316-omp_in_parallel-function).

### <a name="example"></a>Beispiel

```cpp
// omp_in_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_num_threads(4);
    printf_s("%d\n", omp_in_parallel( ));

    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_in_parallel( ));
        }
}
```

```Output
0
1
```

## <a name="omp_init_lock"></a><a name="omp-init-lock"></a> omp_init_lock

Initialisiert eine einfache Sperre.

```cpp
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*lock*<br/>
Eine Variable des Typs `omp_lock_t`.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.2.1 omp_init_lock und omp_init_nest_lock Functions](../3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions).

### <a name="example"></a>Beispiel

```cpp
// omp_init_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_lock_t my_lock;

int main() {
   omp_init_lock(&my_lock);

   #pragma omp parallel num_threads(4)
   {
      int tid = omp_get_thread_num( );
      int i, j;

      for (i = 0; i < 5; ++i) {
         omp_set_lock(&my_lock);
         printf_s("Thread %d - starting locked region\n", tid);
         printf_s("Thread %d - ending locked region\n", tid);
         omp_unset_lock(&my_lock);
      }
   }

   omp_destroy_lock(&my_lock);
}
```

```Output
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 0 - starting locked region
Thread 0 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 1 - starting locked region
Thread 1 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 2 - starting locked region
Thread 2 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
Thread 3 - starting locked region
Thread 3 - ending locked region
```

## <a name="omp_init_nest_lock"></a><a name="omp-init-nest-lock"></a> omp_init_nest_lock

Initialisiert eine Sperre.

```cpp
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*lock*<br/>
Eine Variable des Typs `omp_nest_lock_t`.

### <a name="remarks"></a>Bemerkungen

Die anfängliche Schachtelungs Anzahl ist 0 (null).

Weitere Informationen finden Sie unter [3.2.1 omp_init_lock und omp_init_nest_lock Functions](../3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions).

### <a name="example"></a>Beispiel

```cpp
// omp_init_nest_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_nest_lock_t my_lock;

void Test() {
   int tid = omp_get_thread_num( );
   omp_set_nest_lock(&my_lock);
   printf_s("Thread %d - starting nested locked region\n", tid);
   printf_s("Thread %d - ending nested locked region\n", tid);
   omp_unset_nest_lock(&my_lock);
}

int main() {
   omp_init_nest_lock(&my_lock);

   #pragma omp parallel num_threads(4)
   {
      int i, j;

      for (i = 0; i < 5; ++i) {
         omp_set_nest_lock(&my_lock);
            if (i % 3)
               Test();
            omp_unset_nest_lock(&my_lock);
        }
    }

    omp_destroy_nest_lock(&my_lock);
}
```

```Output
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 3 - starting nested locked region
Thread 3 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 2 - starting nested locked region
Thread 2 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 1 - starting nested locked region
Thread 1 - ending nested locked region
Thread 0 - starting nested locked region
Thread 0 - ending nested locked region
```

## <a name="omp_set_dynamic"></a><a name="omp-set-dynamic"></a> omp_set_dynamic

Gibt an, dass die Anzahl der Threads, die in zukünftigen parallelen Regionen verfügbar sind, von der Laufzeit angepasst werden kann.

```cpp
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>Parameter

*ster*<br/>
Ein Wert, der angibt, ob die Anzahl der in zukünftigen parallelen Regionen verfügbaren Threads von der Laufzeit angepasst werden kann. Wenn der Wert ungleich 0 (null) ist, kann die Laufzeit die Anzahl der Threads anpassen. Wenn NULL, wird die Anzahl der Threads von der Laufzeit nicht dynamisch angepasst.

### <a name="remarks"></a>Bemerkungen

Die Anzahl der Threads überschreitet niemals den Wert, der von [omp_set_num_threads](#omp-set-num-threads) oder [OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads)festgelegt wird.

Verwenden Sie [omp_get_dynamic](#omp-get-dynamic) , um die aktuelle Einstellung von anzuzeigen `omp_set_dynamic` .

Durch die Einstellung für `omp_set_dynamic` wird die Einstellung der Umgebungsvariablen [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic) überschrieben.

Weitere Informationen finden Sie unter [3.1.7 omp_set_dynamic Function](../3-run-time-library-functions.md#317-omp_set_dynamic-function).

### <a name="example"></a>Beispiel

```cpp
// omp_set_dynamic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main()
{
    omp_set_dynamic(9);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_dynamic( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_dynamic( ));
        }
}
```

```Output
1
1
```

## <a name="omp_set_lock"></a><a name="omp-set-lock"></a> omp_set_lock

Blockiert die Thread Ausführung, bis eine Sperre verfügbar ist.

```cpp
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*lock*<br/>
Eine Variable vom Typ `omp_lock_t` , die mit [omp_init_lock](#omp-init-lock)initialisiert wurde.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.2.3 omp_set_lock und omp_set_nest_lock Functions](../3-run-time-library-functions.md#323-omp_set_lock-and-omp_set_nest_lock-functions).

### <a name="examples"></a>Beispiele

Ein Beispiel für die Verwendung von finden Sie unter [omp_init_lock](#omp-init-lock) `omp_set_lock` .

## <a name="omp_set_nest_lock"></a><a name="omp-set-nest-lock"></a> omp_set_nest_lock

Blockiert die Thread Ausführung, bis eine Sperre verfügbar ist.

```cpp
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*lock*<br/>
Eine Variable vom Typ `omp_nest_lock_t` , die mit [omp_init_nest_lock](#omp-init-nest-lock)initialisiert wurde.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.2.3 omp_set_lock und omp_set_nest_lock Functions](../3-run-time-library-functions.md#323-omp_set_lock-and-omp_set_nest_lock-functions).

### <a name="examples"></a>Beispiele

Ein Beispiel für die Verwendung von finden Sie unter [omp_init_nest_lock](#omp-init-nest-lock) `omp_set_nest_lock` .

## <a name="omp_set_nested"></a><a name="omp-set-nested"></a> omp_set_nested

Aktiviert die durch die Aktivierung von Parallelität.

```cpp
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>Parameter

*ster*<br/>
Ein Wert ungleich 0 (null) aktiviert eine nicht-NULL-Parallelität, während NULL die gruppierten Parallelität deaktiviert.

### <a name="remarks"></a>Bemerkungen

Die OMP-Parallelität kann mit `omp_set_nested` oder durch Festlegen der [OMP_NESTED](openmp-environment-variables.md#omp-nested) -Umgebungsvariablen aktiviert werden.

Durch die Einstellung für `omp_set_nested` wird die Einstellung der `OMP_NESTED` Umgebungsvariablen überschrieben.

Durch das Aktivieren der Umgebungsvariablen kann ein anderweitig betriebsfähiges Programm unterbrechen, da sich die Anzahl der Threads bei der Schachtelung paralleler Bereiche exponentiell vergrößert. Beispielsweise erfordert eine Funktion, die mit der Anzahl der auf 4 festgelegten OMP-Threads sechs Mal wiederholt wird, 4.096 (4 bis 6) Threads. Mit Ausnahme von e/a-gebundenen Anwendungen verschlechtert sich die Leistung einer Anwendung im Allgemeinen, wenn mehr Threads als Prozessoren vorhanden sind.

Verwenden Sie [omp_get_nested](#omp-get-nested) , um die aktuelle Einstellung von anzuzeigen `omp_set_nested` .

Weitere Informationen finden Sie unter [3.1.9 omp_set_nested Function](../3-run-time-library-functions.md#319-omp_set_nested-function).

### <a name="example"></a>Beispiel

```cpp
// omp_set_nested.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main( )
{
    omp_set_nested(1);
    omp_set_num_threads(4);
    printf_s("%d\n", omp_get_nested( ));
    #pragma omp parallel
        #pragma omp master
        {
            printf_s("%d\n", omp_get_nested( ));
        }
}
```

```Output
1
1
```

## <a name="omp_set_num_threads"></a><a name="omp-set-num-threads"></a> omp_set_num_threads

Legt die Anzahl der Threads in zukünftigen parallelen Regionen fest, es sei denn, Sie wird von einer [num_threads](openmp-clauses.md#num-threads) -Klausel überschrieben.

```cpp
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>Parameter

*num_threads*<br/>
Die Anzahl der Threads im parallelen Bereich.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [omp_set_num_threads Funktion "3.1.1](../3-run-time-library-functions.md#311-omp_set_num_threads-function)".

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von finden Sie unter [omp_get_num_threads](#omp-get-num-threads) `omp_set_num_threads` .

## <a name="omp_test_lock"></a><a name="omp-test-lock"></a> omp_test_lock

Versucht, eine Sperre festzulegen, blockiert jedoch nicht die Thread Ausführung.

```cpp
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*lock*<br/>
Eine Variable vom Typ `omp_lock_t` , die mit [omp_init_lock](#omp-init-lock)initialisiert wurde.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.2.5 omp_test_lock und omp_test_nest_lock Functions](../3-run-time-library-functions.md#325-omp_test_lock-and-omp_test_nest_lock-functions).

### <a name="example"></a>Beispiel

```cpp
// omp_test_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_lock_t simple_lock;

int main() {
    omp_init_lock(&simple_lock);

    #pragma omp parallel num_threads(4)
    {
        int tid = omp_get_thread_num();

        while (!omp_test_lock(&simple_lock))
            printf_s("Thread %d - failed to acquire simple_lock\n",
                     tid);

        printf_s("Thread %d - acquired simple_lock\n", tid);

        printf_s("Thread %d - released simple_lock\n", tid);
        omp_unset_lock(&simple_lock);
    }

    omp_destroy_lock(&simple_lock);
}
```

```Output
Thread 1 - acquired simple_lock
Thread 1 - released simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 2 - acquired simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 2 - released simple_lock
Thread 0 - failed to acquire simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - acquired simple_lock
Thread 3 - failed to acquire simple_lock
Thread 0 - released simple_lock
Thread 3 - failed to acquire simple_lock
Thread 3 - acquired simple_lock
Thread 3 - released simple_lock
```

## <a name="omp_test_nest_lock"></a><a name="omp-test-nest-lock"></a> omp_test_nest_lock

Versucht, eine Sperre für eine Sperre festzulegen, blockiert jedoch nicht die Thread Ausführung.

```cpp
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*lock*<br/>
Eine Variable vom Typ `omp_nest_lock_t` , die mit [omp_init_nest_lock](#omp-init-nest-lock)initialisiert wurde.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.2.5 omp_test_lock und omp_test_nest_lock Functions](../3-run-time-library-functions.md#325-omp_test_lock-and-omp_test_nest_lock-functions).

### <a name="example"></a>Beispiel

```cpp
// omp_test_nest_lock.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

omp_nest_lock_t nestable_lock;

int main() {
   omp_init_nest_lock(&nestable_lock);

   #pragma omp parallel num_threads(4)
   {
      int tid = omp_get_thread_num();
      while (!omp_test_nest_lock(&nestable_lock))
         printf_s("Thread %d - failed to acquire nestable_lock\n",
                tid);

      printf_s("Thread %d - acquired nestable_lock\n", tid);

      if (omp_test_nest_lock(&nestable_lock)) {
         printf_s("Thread %d - acquired nestable_lock again\n",
                tid);
         printf_s("Thread %d - released nestable_lock\n",
                tid);
         omp_unset_nest_lock(&nestable_lock);
      }

      printf_s("Thread %d - released nestable_lock\n", tid);
      omp_unset_nest_lock(&nestable_lock);
   }

   omp_destroy_nest_lock(&nestable_lock);
}
```

```Output
Thread 1 - acquired nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 1 - acquired nestable_lock again
Thread 0 - failed to acquire nestable_lock
Thread 1 - released nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 1 - released nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 3 - acquired nestable_lock
Thread 0 - failed to acquire nestable_lock
Thread 3 - acquired nestable_lock again
Thread 0 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 3 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 3 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - acquired nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - acquired nestable_lock again
Thread 2 - failed to acquire nestable_lock
Thread 0 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 0 - released nestable_lock
Thread 2 - failed to acquire nestable_lock
Thread 2 - acquired nestable_lock
Thread 2 - acquired nestable_lock again
Thread 2 - released nestable_lock
Thread 2 - released nestable_lock
```

## <a name="omp_unset_lock"></a><a name="omp-unset-lock"></a> omp_unset_lock

Gibt eine Sperre frei.

```cpp
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*lock*<br/>
Eine Variable vom Typ `omp_lock_t` , die mit [omp_init_lock](#omp-init-lock)initialisiert wurde, dem der Thread gehört und in der Funktion ausgeführt wird.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.2.4 omp_unset_lock und omp_unset_nest_lock Functions](../3-run-time-library-functions.md#324-omp_unset_lock-and-omp_unset_nest_lock-functions).

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von finden Sie unter [omp_init_lock](#omp-init-lock) `omp_unset_lock` .

## <a name="omp_unset_nest_lock"></a><a name="omp-unset-nest-lock"></a> omp_unset_nest_lock

Gibt eine nicht stabile Sperre frei.

```cpp
void omp_unset_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*lock*<br/>
Eine Variable vom Typ `omp_nest_lock_t` , die mit [omp_init_nest_lock](#omp-init-nest-lock)initialisiert wurde, dem der Thread gehört und in der Funktion ausgeführt wird.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.2.4 omp_unset_lock und omp_unset_nest_lock Functions](../3-run-time-library-functions.md#324-omp_unset_lock-and-omp_unset_nest_lock-functions).

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von finden Sie unter [omp_init_nest_lock](#omp-init-nest-lock) `omp_unset_nest_lock` .

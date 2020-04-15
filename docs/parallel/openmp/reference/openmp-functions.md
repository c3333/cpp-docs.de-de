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
ms.openlocfilehash: 0475a83ba259ed00bbcb9ddaba99a1556b35f613
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317144"
---
# <a name="openmp-functions"></a>OpenMP-Funktionen

Stellt Links zu Funktionen bereit, die in der OpenMP-API verwendet werden.

Die Visual C++-Implementierung des OpenMP-Standards umfasst die folgenden Funktionen und Datentypen.

Für die Umgebungsausführung:

|Funktion|BESCHREIBUNG|
|--------|-----------|
|[omp_set_num_threads](#omp-set-num-threads)|Legt die Anzahl der Threads in kommenden parallelen Regionen fest, es sei denn, sie werden durch eine [num_threads-Klausel](openmp-clauses.md#num-threads) überschrieben.|
|[omp_get_num_threads](#omp-get-num-threads)|Gibt die Anzahl der Threads im parallelen Bereich zurück.|
|[omp_get_max_threads](#omp-get-max-threads)|Gibt eine ganze Zahl zurück, die gleich oder größer ist als die Anzahl der Threads, die verfügbar wären, wenn an diesem Punkt im Code ein paralleler Bereich ohne [num_threads](openmp-clauses.md#num-threads) definiert wurde.|
|[omp_get_thread_num](#omp-get-thread-num)|Gibt die Threadnummer des Threads zurück, der innerhalb des Threadteams ausgeführt wird.|
|[omp_get_num_procs](#omp-get-num-procs)|Gibt die Anzahl der Prozessoren zurück, die verfügbar sind, wenn die Funktion aufgerufen wird.|
|[omp_in_parallel](#omp-in-parallel)|Gibt einen Wert ungleich Null zurück, wenn er innerhalb eines parallelen Bereichs aufgerufen wird.|
|[omp_set_dynamic](#omp-set-dynamic)|Gibt an, dass die Anzahl der Threads, die in kommenden parallelen Regionen verfügbar sind, durch die Laufzeit angepasst werden kann.|
|[omp_get_dynamic](#omp-get-dynamic)|Gibt einen Wert zurück, der angibt, ob die Anzahl der Threads, die in kommenden parallelen Regionen verfügbar sind, durch die Laufzeit angepasst werden kann.|
|[omp_set_nested](#omp-set-nested)|Aktiviert verschachtelte Parallelität.|
|[omp_get_nested](#omp-get-nested)|Gibt einen Wert zurück, der angibt, ob die geschachtelte Parallelität aktiviert ist.|

Für Sperre:

|Funktion|BESCHREIBUNG|
|--------|-----------|
|[omp_init_lock](#omp-init-lock)|Initialisiert eine einfache Sperre.|
|[omp_init_nest_lock](#omp-init-nest-lock)|Initialisiert eine Sperre.|
|[omp_destroy_lock](#omp-destroy-lock)|Entinitialisiert eine Sperre.|
|[omp_destroy_nest_lock](#omp-destroy-nest-lock)|Wenn eine verschachtelbare Sperre nicht initialisiert wird.|
|[omp_set_lock](#omp-set-lock)|Blockiert die Threadausführung, bis eine Sperre verfügbar ist.|
|[omp_set_nest_lock](#omp-set-nest-lock)|Blockiert die Threadausführung, bis eine Sperre verfügbar ist.|
|[omp_unset_lock](#omp-unset-lock)|Gibt eine Sperre frei.|
|[omp_unset_nest_lock](#omp-unset-nest-lock)|Gibt eine verschachtelbare Sperre frei.|
|[omp_test_lock](#omp-test-lock)|Versucht, eine Sperre festzulegen, blockiert jedoch nicht die Threadausführung.|
|[omp_test_nest_lock](#omp-test-nest-lock)|Versucht, eine verschachtelbare Sperre festzulegen, blockiert jedoch nicht die Threadausführung.|

|Datentyp|BESCHREIBUNG|
|---------|-----------|
|`omp_lock_t`|Ein Typ, der den Status einer Sperre enthält, unabhängig davon, ob die Sperre verfügbar ist oder ob ein Thread eine Sperre besitzt.|
|`omp_nest_lock_t`|Ein Typ, der eine der folgenden Informationen zu einer Sperre enthält: ob die Sperre verfügbar ist, und die Identität des Threads, der die Sperre besitzt, und eine Verschachtelungsanzahl.|

Für Timing-Routinen:

|Funktion|BESCHREIBUNG|
|--------|-----------|
|[omp_get_wtime](#omp-get-wtime)|Gibt einen Wert in Sekunden der von einem bestimmten Punkt verstrichenen Zeit zurück.|
|[omp_get_wtick](#omp-get-wtick)|Gibt die Anzahl der Sekunden zwischen den Ticks der Prozessoruhr zurück.|

## <a name="omp_destroy_lock"></a><a name="omp-destroy-lock"></a>omp_destroy_lock

Entinitialisiert eine Sperre.

```cpp
void omp_destroy_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*Sperren*<br/>
Eine Variable `omp_lock_t` des Typs, die mit [omp_init_lock](#omp-init-lock)initialisiert wurde.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.2.2 omp_destroy_lock und omp_destroy_nest_lock Funktionen](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Beispiel

Ein [Beispiel](#omp-init-lock) für die `omp_destroy_lock`Verwendung finden Sie in omp_init_lock .

## <a name="omp_destroy_nest_lock"></a><a name="omp-destroy-nest-lock"></a>omp_destroy_nest_lock

Wenn eine verschachtelbare Sperre nicht initialisiert wird.

```cpp
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*Sperren*<br/>
Eine Variable `omp_nest_lock_t` des Typs, die mit [omp_init_nest_lock](#omp-init-nest-lock)initialisiert wurde.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.2.2 omp_destroy_lock und omp_destroy_nest_lock Funktionen](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md).

### <a name="example"></a>Beispiel

Ein [Beispiel](#omp-init-nest-lock) für die `omp_destroy_nest_lock`Verwendung finden Sie unter omp_init_nest_lock .

## <a name="omp_get_dynamic"></a><a name="omp-get-dynamic"></a>omp_get_dynamic

Gibt einen Wert zurück, der angibt, ob die Anzahl der Threads, die in kommenden parallelen Regionen verfügbar sind, durch die Laufzeit angepasst werden kann.

```cpp
int omp_get_dynamic();
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null bedeutet, dass Threads dynamisch angepasst werden.

### <a name="remarks"></a>Bemerkungen

Die dynamische Anpassung von Gewinden wird mit [omp_set_dynamic](#omp-set-dynamic) und [OMP_DYNAMIC](openmp-environment-variables.md#omp-dynamic)angegeben.

Weitere Informationen finden Sie unter [3.1.7 omp_set_dynamic Funktion](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

### <a name="example"></a>Beispiel

Ein [Beispiel](#omp-set-dynamic) für die `omp_get_dynamic`Verwendung finden Sie in omp_set_dynamic .

## <a name="omp_get_max_threads"></a><a name="omp-get-max-threads"></a>omp_get_max_threads

Gibt eine ganze Zahl zurück, die gleich oder größer ist als die Anzahl der Threads, die verfügbar wären, wenn an diesem Punkt im Code ein paralleler Bereich ohne [num_threads](openmp-clauses.md#num-threads) definiert wurde.

```cpp
int omp_get_max_threads( )
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.1.3 omp_get_max_threads Funktion](../../../parallel/openmp/3-1-3-omp-get-max-threads-function.md).

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

## <a name="omp_get_nested"></a><a name="omp-get-nested"></a>omp_get_nested

Gibt einen Wert zurück, der angibt, ob die geschachtelte Parallelität aktiviert ist.

```cpp
int omp_get_nested( );
```

### <a name="return-value"></a>Rückgabewert

Ein Wert ungleich Null bedeutet, dass geschachtelte Parallelität aktiviert ist.

### <a name="remarks"></a>Bemerkungen

Die verschachtelte Parallelität wird mit [omp_set_nested](#omp-set-nested) und [OMP_NESTED](openmp-environment-variables.md#omp-nested)angegeben.

Weitere Informationen finden Sie unter [3.1.10 omp_get_nested Funktion](../../../parallel/openmp/3-1-10-omp-get-nested-function.md).

### <a name="example"></a>Beispiel

Ein [Beispiel](#omp-set-nested) für die `omp_get_nested`Verwendung finden Sie in omp_set_nested .

## <a name="omp_get_num_procs"></a><a name="omp-get-num-procs"></a>omp_get_num_procs

Gibt die Anzahl der Prozessoren zurück, die verfügbar sind, wenn die Funktion aufgerufen wird.

```cpp
int omp_get_num_procs();
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.1.5 omp_get_num_procs Funktion](../../../parallel/openmp/3-1-5-omp-get-num-procs-function.md).

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

## <a name="omp_get_num_threads"></a><a name="omp-get-num-threads"></a>omp_get_num_threads

Gibt die Anzahl der Threads im parallelen Bereich zurück.

```cpp
int omp_get_num_threads( );
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.1.2 omp_get_num_threads Funktion](../../../parallel/openmp/3-1-2-omp-get-num-threads-function.md).

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

## <a name="omp_get_thread_num"></a><a name="omp-get-thread-num"></a>omp_get_thread_num

Gibt die Threadnummer des Threads zurück, der innerhalb des Threadteams ausgeführt wird.

```cpp
int omp_get_thread_num( );
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.1.4 omp_get_thread_num Funktion](../../../parallel/openmp/3-1-4-omp-get-thread-num-function.md).

### <a name="example"></a>Beispiel

Siehe [parallel](openmp-directives.md#parallel) für ein `omp_get_thread_num`Beispiel für die Verwendung von .

## <a name="omp_get_wtick"></a><a name="omp-get-wtick"></a>omp_get_wtick

Gibt die Anzahl der Sekunden zwischen den Ticks der Prozessoruhr zurück.

```cpp
double omp_get_wtick( );
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.3.2 omp_get_wtick Funktion](../../../parallel/openmp/3-3-2-omp-get-wtick-function.md).

### <a name="example"></a>Beispiel

Ein [Beispiel](#omp-get-wtime) für die `omp_get_wtick`Verwendung finden Sie in omp_get_wtime .

## <a name="omp_get_wtime"></a><a name="omp-get-wtime"></a>omp_get_wtime

Gibt einen Wert in Sekunden der von einem bestimmten Punkt verstrichenen Zeit zurück.

```cpp
double omp_get_wtime( );
```

### <a name="return-value"></a>Rückgabewert

Gibt einen Wert in Sekunden der Zeit zurück, die von einem beliebigen, aber konsistenten Punkt verstrichen ist.

### <a name="remarks"></a>Bemerkungen

Dieser Punkt bleibt während der Programmausführung konsistent, was anstehende Vergleiche ermöglicht.

Weitere Informationen finden Sie unter [3.3.1 omp_get_wtime Funktion](../../../parallel/openmp/3-3-1-omp-get-wtime-function.md).

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

## <a name="omp_in_parallel"></a><a name="omp-in-parallel"></a>omp_in_parallel

Gibt einen Wert ungleich Null zurück, wenn er innerhalb eines parallelen Bereichs aufgerufen wird.

```cpp
int omp_in_parallel( );
```

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.1.6 omp_in_parallel Funktion](../../../parallel/openmp/3-1-6-omp-in-parallel-function.md).

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

## <a name="omp_init_lock"></a><a name="omp-init-lock"></a>omp_init_lock

Initialisiert eine einfache Sperre.

```cpp
void omp_init_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*Sperren*<br/>
Eine Variable des Typs `omp_lock_t`.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.2.1 omp_init_lock und omp_init_nest_lock Funktionen](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

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

## <a name="omp_init_nest_lock"></a><a name="omp-init-nest-lock"></a>omp_init_nest_lock

Initialisiert eine Sperre.

```cpp
void omp_init_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*Sperren*<br/>
Eine Variable des Typs `omp_nest_lock_t`.

### <a name="remarks"></a>Bemerkungen

Die anfängliche Verschachtelungsanzahl ist Null.

Weitere Informationen finden Sie unter [3.2.1 omp_init_lock und omp_init_nest_lock Funktionen](../../../parallel/openmp/3-2-1-omp-init-lock-and-omp-init-nest-lock-functions.md).

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

## <a name="omp_set_dynamic"></a><a name="omp-set-dynamic"></a>omp_set_dynamic

Gibt an, dass die Anzahl der Threads, die in kommenden parallelen Regionen verfügbar sind, durch die Laufzeit angepasst werden kann.

```cpp
void omp_set_dynamic(
   int val
);
```

### <a name="parameters"></a>Parameter

*Val*<br/>
Ein Wert, der angibt, ob die Anzahl der Threads, die in kommenden parallelen Regionen verfügbar sind, durch die Laufzeit angepasst werden kann. Bei einem Wert ungleich Null kann die Laufzeit die Anzahl der Threads anpassen, bei Null wird die Anzahl der Threads nicht dynamisch angepasst.

### <a name="remarks"></a>Bemerkungen

Die Anzahl der Threads wird niemals den von [omp_set_num_threads](#omp-set-num-threads) oder [OMP_NUM_THREADS](openmp-environment-variables.md#omp-num-threads)festgelegten Wert überschreiten.

Verwenden Sie [omp_get_dynamic,](#omp-get-dynamic) um `omp_set_dynamic`die aktuelle Einstellung von anzuzeigen.

Die Einstellung `omp_set_dynamic` für überschreibt die Einstellung der [Umgebungsvariablen OMP_DYNAMIC.](openmp-environment-variables.md#omp-dynamic)

Weitere Informationen finden Sie unter [3.1.7 omp_set_dynamic Funktion](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md).

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

## <a name="omp_set_lock"></a><a name="omp-set-lock"></a>omp_set_lock

Blockiert die Threadausführung, bis eine Sperre verfügbar ist.

```cpp
void omp_set_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*Sperren*<br/>
Eine Variable `omp_lock_t` des Typs, die mit [omp_init_lock](#omp-init-lock)initialisiert wurde.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.2.3 omp_set_lock und omp_set_nest_lock Funktionen](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Beispiele

Ein [Beispiel](#omp-init-lock) für die `omp_set_lock`Verwendung finden Sie in omp_init_lock .

## <a name="omp_set_nest_lock"></a><a name="omp-set-nest-lock"></a>omp_set_nest_lock

Blockiert die Threadausführung, bis eine Sperre verfügbar ist.

```cpp
void omp_set_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*Sperren*<br/>
Eine Variable `omp_nest_lock_t` des Typs, die mit [omp_init_nest_lock](#omp-init-nest-lock)initialisiert wurde.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.2.3 omp_set_lock und omp_set_nest_lock Funktionen](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md).

### <a name="examples"></a>Beispiele

Ein [Beispiel](#omp-init-nest-lock) für die `omp_set_nest_lock`Verwendung finden Sie unter omp_init_nest_lock .

## <a name="omp_set_nested"></a><a name="omp-set-nested"></a>omp_set_nested

Aktiviert verschachtelte Parallelität.

```cpp
void omp_set_nested(
   int val
);
```

### <a name="parameters"></a>Parameter

*Val*<br/>
Ein Wert ungleich Null aktiviert verschachtelte Parallelität, während Null die geschachtelte Parallelität deaktiviert.

### <a name="remarks"></a>Bemerkungen

OMP verschachtelte Parallelität kann `omp_set_nested`mit aktiviert werden, oder indem die [OMP_NESTED](openmp-environment-variables.md#omp-nested) Umgebungsvariable gesetzt wird.

Die Einstellung `omp_set_nested` für überschreibt die `OMP_NESTED` Einstellung der Umgebungsvariablen.

Das Aktivieren der Umgebungsvariablen kann ein ansonsten operationelles Programm unterbrechen, da die Anzahl der Threads beim Verschachteln paralleler Regionen exponentiell zunimmt. Beispielsweise erfordert eine Funktion, die sechsmal mit der Anzahl der OMP-Threads auf 4 zurückgeht, 4.096 (4 bis zur Leistung von 6) Threads. Mit Ausnahme von E/A-gebundenen Anwendungen verschlechtert sich die Leistung einer Anwendung im Allgemeinen, wenn mehr Threads als Prozessoren vorhanden sind.

Verwenden Sie [omp_get_nested,](#omp-get-nested) um `omp_set_nested`die aktuelle Einstellung von anzuzeigen.

Weitere Informationen finden Sie unter [3.1.9 omp_set_nested Funktion](../../../parallel/openmp/3-1-9-omp-set-nested-function.md).

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

## <a name="omp_set_num_threads"></a><a name="omp-set-num-threads"></a>omp_set_num_threads

Legt die Anzahl der Threads in kommenden parallelen Regionen fest, es sei denn, sie werden durch eine [num_threads-Klausel](openmp-clauses.md#num-threads) überschrieben.

```cpp
void omp_set_num_threads(
   int num_threads
);
```

### <a name="parameters"></a>Parameter

*num_threads*<br/>
Die Anzahl der Threads im parallelen Bereich.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.1.1 omp_set_num_threads Funktion](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md).

### <a name="example"></a>Beispiel

Ein [Beispiel](#omp-get-num-threads) für die `omp_set_num_threads`Verwendung finden Sie in omp_get_num_threads .

## <a name="omp_test_lock"></a><a name="omp-test-lock"></a>omp_test_lock

Versucht, eine Sperre festzulegen, blockiert jedoch nicht die Threadausführung.

```cpp
int omp_test_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*Sperren*<br/>
Eine Variable `omp_lock_t` des Typs, die mit [omp_init_lock](#omp-init-lock)initialisiert wurde.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.2.5 omp_test_lock und omp_test_nest_lock Funktionen](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

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

## <a name="omp_test_nest_lock"></a><a name="omp-test-nest-lock"></a>omp_test_nest_lock

Versucht, eine verschachtelbare Sperre festzulegen, blockiert jedoch nicht die Threadausführung.

```cpp
int omp_test_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*Sperren*<br/>
Eine Variable `omp_nest_lock_t` des Typs, die mit [omp_init_nest_lock](#omp-init-nest-lock)initialisiert wurde.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.2.5 omp_test_lock und omp_test_nest_lock Funktionen](../../../parallel/openmp/3-2-5-omp-test-lock-and-omp-test-nest-lock-functions.md).

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

## <a name="omp_unset_lock"></a><a name="omp-unset-lock"></a>omp_unset_lock

Gibt eine Sperre frei.

```cpp
void omp_unset_lock(
   omp_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*Sperren*<br/>
Eine Variable `omp_lock_t` des Typs, die mit [omp_init_lock](#omp-init-lock)initialisiert wurde, die dem Thread gehören und in der Funktion ausgeführt werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.2.4 omp_unset_lock und omp_unset_nest_lock Funktionen](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Beispiel

Ein [Beispiel](#omp-init-lock) für die `omp_unset_lock`Verwendung finden Sie in omp_init_lock .

## <a name="omp_unset_nest_lock"></a><a name="omp-unset-nest-lock"></a>omp_unset_nest_lock

Gibt eine verschachtelbare Sperre frei.

```cpp
void omp_unset_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>Parameter

*Sperren*<br/>
Eine Variable `omp_nest_lock_t` des Typs, die mit [omp_init_nest_lock](#omp-init-nest-lock)initialisiert wurde, die dem Thread gehören und in der Funktion ausgeführt werden.

### <a name="remarks"></a>Bemerkungen

Weitere Informationen finden Sie unter [3.2.4 omp_unset_lock und omp_unset_nest_lock Funktionen](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md).

### <a name="example"></a>Beispiel

Ein [Beispiel](#omp-init-nest-lock) für die `omp_unset_nest_lock`Verwendung finden Sie unter omp_init_nest_lock .

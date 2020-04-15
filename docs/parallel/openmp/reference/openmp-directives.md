---
title: OpenMP-Direktiven
ms.date: 03/20/2019
f1_keywords:
- OpenMP directives
- atomic
- barrier
- critical
- flush
- for
- master
- parallel
- section
- single
- threadprivate
helpviewer_keywords:
- OpenMP directives
- atomic OpenMP directive
- barrier OpenMP directive
- critical OpenMP directive
- flush OpenMP directive
- for OpenMP directive
- master OpenMP directive
- ordered OpenMP directive
- parallel OpenMP directive
- sections OpenMP directive
- single OpenMP directive
- threadprivate OpenMP directive
ms.assetid: 0562c263-344c-466d-843e-de830d918940
ms.openlocfilehash: 569419b3422b155afc6e9692efaecd4e5a06f188
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366447"
---
# <a name="openmp-directives"></a>OpenMP-Direktiven

Stellt Links zu Direktiven bereit, die in der OpenMP-API verwendet werden.

Visual C++ unterstützt die folgenden OpenMP-Direktiven.

Für parallele Arbeitsteilung:

|Direktive|BESCHREIBUNG|
|---------|-----------|
|[parallel](#parallel)|Definiert einen parallelen Bereich, d. h. Code, der von mehreren Threads parallel ausgeführt wird.|
|[for](#for-openmp)|Bewirkt, dass `for` die arbeit in einer Schleife innerhalb eines parallelen Bereichs auf Threads aufgeteilt wird.|
|[Bereichen](#sections-openmp)|Identifiziert Codeabschnitte, die auf alle Threads aufgeteilt werden sollen.|
|[single](#single)|Hier können Sie angeben, dass ein Codeabschnitt für einen einzelnen Thread ausgeführt werden soll, nicht unbedingt für den Masterthread.|

Für Master und Synchronisation:

|Direktive|BESCHREIBUNG|
|---------|-----------|
|[master](#master)|Gibt an, dass nur der Masterthread einen Abschnitt des Programms ausführen soll.|
|[Kritisch](#critical)|Gibt an, dass Code jeweils nur für einen Thread ausgeführt wird.|
|[Barriere](#barrier)|Synchronisiert alle Threads in einem Team; alle Gewinde halten an der Barriere, bis alle Threads die Barriere ausführen.|
|[Unteilbar](#atomic)|Gibt an, dass ein Speicherspeicherort, der atomar aktualisiert wird.|
|[Flush](#flush-openmp)|Gibt an, dass alle Threads dieselbe Speicheransicht für alle freigegebenen Objekte haben.|
|[Bestellt](#ordered-openmp-directives)|Gibt an, dass Code `for` unter einer parallelisierten Schleife wie eine sequenzielle Schleife ausgeführt werden soll.|

Für Datenumgebung:

|Direktive|BESCHREIBUNG|
|---------|-----------|
|[threadprivate](#threadprivate)|Gibt an, dass eine Variable für einen Thread privat ist.|

## <a name="atomic"></a><a name="atomic"></a>Atomic

Gibt an, dass ein Speicherspeicherort, der atomar aktualisiert wird.

```cpp
#pragma omp atomic
   expression
```

### <a name="parameters"></a>Parameter

*Ausdruck*<br/>
Die Anweisung mit dem *lvalue*, dessen Speicherspeicherort Sie vor mehr als einem Schreibvorgang schützen möchten.

### <a name="remarks"></a>Bemerkungen

Die `atomic` Richtlinie unterstützt keine Klauseln.

Weitere Informationen finden Sie unter [2.6.4 Atomkonstrukt](../../../parallel/openmp/2-6-4-atomic-construct.md).

### <a name="example"></a>Beispiel

```cpp
// omp_atomic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

#define MAX 10

int main() {
   int count = 0;
   #pragma omp parallel num_threads(MAX)
   {
      #pragma omp atomic
      count++;
   }
   printf_s("Number of threads: %d\n", count);
}
```

```Output
Number of threads: 10
```

## <a name="barrier"></a><a name="barrier"></a>Barriere

Synchronisiert alle Threads in einem Team; alle Gewinde halten an der Barriere, bis alle Threads die Barriere ausführen.

```cpp
#pragma omp barrier
```

### <a name="remarks"></a>Bemerkungen

Die `barrier` Richtlinie unterstützt keine Klauseln.

Weitere Informationen finden Sie unter [2.6.3 Barriererichtlinie](../../../parallel/openmp/2-6-3-barrier-directive.md).

### <a name="example"></a>Beispiel

Eine Beispielverwendung finden `barrier`Sie unter [Master](#master).

## <a name="critical"></a><a name="critical"></a>Kritisch

Gibt an, dass Code jeweils nur für einen Thread ausgeführt wird.

```cpp
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>Parameter

*name*<br/>
(Optional) Ein Name zum Identifizieren des kritischen Codes. Der Name muss in Klammern eingeschlossen werden.

### <a name="remarks"></a>Bemerkungen

Die `critical` Richtlinie unterstützt keine Klauseln.

Weitere Informationen finden Sie unter [2.6.2 kritisches Konstrukt](../../../parallel/openmp/2-6-2-critical-construct.md).

### <a name="example"></a>Beispiel

```cpp
// omp_critical.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>
#include <stdlib.h>

#define SIZE 10

int main()
{
    int i;
    int max;
    int a[SIZE];

    for (i = 0; i < SIZE; i++)
    {
        a[i] = rand();
        printf_s("%d\n", a[i]);
    }

    max = a[0];
    #pragma omp parallel for num_threads(4)
        for (i = 1; i < SIZE; i++)
        {
            if (a[i] > max)
            {
                #pragma omp critical
                {
                    // compare a[i] and max again because max
                    // could have been changed by another thread after
                    // the comparison outside the critical section
                    if (a[i] > max)
                        max = a[i];
                }
            }
        }

    printf_s("max = %d\n", max);
}
```

```Output
41
18467
6334
26500
19169
15724
11478
29358
26962
24464
max = 29358
```

## <a name="flush"></a><a name="flush-openmp"></a>Flush

Gibt an, dass alle Threads dieselbe Speicheransicht für alle freigegebenen Objekte haben.

```cpp
#pragma omp flush [(var)]
```

### <a name="parameters"></a>Parameter

*var*<br/>
(Optional) Eine durch Kommas getrennte Liste von Variablen, die Objekte darstellen, die Sie synchronisieren möchten. Wenn *var* nicht angegeben ist, wird der gesamte Speicher geleert.

### <a name="remarks"></a>Bemerkungen

Die `flush` Richtlinie unterstützt keine Klauseln.

Weitere Informationen finden Sie unter [2.6.5 Flush Directive](../../../parallel/openmp/2-6-5-flush-directive.md).

### <a name="example"></a>Beispiel

```cpp
// omp_flush.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void read(int *data) {
   printf_s("read data\n");
   *data = 1;
}

void process(int *data) {
   printf_s("process data\n");
   (*data)++;
}

int main() {
   int data;
   int flag;

   flag = 0;

   #pragma omp parallel sections num_threads(2)
   {
      #pragma omp section
      {
         printf_s("Thread %d: ", omp_get_thread_num( ));
         read(&data);
         #pragma omp flush(data)
         flag = 1;
         #pragma omp flush(flag)
         // Do more work.
      }

      #pragma omp section
      {
         while (!flag) {
            #pragma omp flush(flag)
         }
         #pragma omp flush(data)

         printf_s("Thread %d: ", omp_get_thread_num( ));
         process(&data);
         printf_s("data = %d\n", data);
      }
   }
}
```

```Output
Thread 0: read data
Thread 1: process data
data = 2
```

## <a name="for"></a><a name="for-openmp"></a> für

Bewirkt, dass `for` die arbeit in einer Schleife innerhalb eines parallelen Bereichs auf Threads aufgeteilt wird.

```cpp
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>Parameter

*Klauseln*<br/>
(Optional) Null oder mehr Klauseln, siehe Abschnitt **"Bemerkungen".**

*for_statement*<br/>
Eine `for` Schleife. Undefiniertes Verhalten entsteht, `for` wenn Benutzercode in der Schleife die Indexvariable ändert.

### <a name="remarks"></a>Bemerkungen

Die `for` Richtlinie unterstützt die folgenden Klauseln:

- [privat](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [Bestellt](openmp-clauses.md#ordered-openmp-clauses)
- [schedule](openmp-clauses.md#schedule)
- [Nowait](openmp-clauses.md#nowait)

Wenn `parallel` auch `clauses` angegeben, kann eine Klausel `parallel` `for` von der `nowait`oder Richtlinien akzeptiert werden, außer .

Weitere Informationen finden Sie unter [2.4.1 für construct](../../../parallel/openmp/2-4-1-for-construct.md).

### <a name="example"></a>Beispiel

```cpp
// omp_for.cpp
// compile with: /openmp
#include <stdio.h>
#include <math.h>
#include <omp.h>

#define NUM_THREADS 4
#define NUM_START 1
#define NUM_END 10

int main() {
   int i, nRet = 0, nSum = 0, nStart = NUM_START, nEnd = NUM_END;
   int nThreads = 0, nTmp = nStart + nEnd;
   unsigned uTmp = (unsigned((abs(nStart - nEnd) + 1)) *
                               unsigned(abs(nTmp))) / 2;
   int nSumCalc = uTmp;

   if (nTmp < 0)
      nSumCalc = -nSumCalc;

   omp_set_num_threads(NUM_THREADS);

   #pragma omp parallel default(none) private(i) shared(nSum, nThreads, nStart, nEnd)
   {
      #pragma omp master
      nThreads = omp_get_num_threads();

      #pragma omp for
      for (i=nStart; i<=nEnd; ++i) {
            #pragma omp atomic
            nSum += i;
      }
   }

   if  (nThreads == NUM_THREADS) {
      printf_s("%d OpenMP threads were used.\n", NUM_THREADS);
      nRet = 0;
   }
   else {
      printf_s("Expected %d OpenMP threads, but %d were used.\n",
               NUM_THREADS, nThreads);
      nRet = 1;
   }

   if (nSum != nSumCalc) {
      printf_s("The sum of %d through %d should be %d, "
               "but %d was reported!\n",
               NUM_START, NUM_END, nSumCalc, nSum);
      nRet = 1;
   }
   else
      printf_s("The sum of %d through %d is %d\n",
               NUM_START, NUM_END, nSum);
}
```

```Output
4 OpenMP threads were used.
The sum of 1 through 10 is 55
```

## <a name="master"></a><a name="master"></a>Master

Gibt an, dass nur der Masterthread einen Abschnitt des Programms ausführen soll.

```cpp
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>Bemerkungen

Die `master` Richtlinie unterstützt keine Klauseln.

Mit der [einzelnen](#single) Direktive können Sie angeben, dass ein Codeabschnitt für einen einzelnen Thread ausgeführt werden soll, nicht unbedingt für den Masterthread.

Weitere Informationen finden Sie unter [2.6.1 Masterkonstrukt](../../../parallel/openmp/2-6-1-master-construct.md).

### <a name="example"></a>Beispiel

```cpp
// omp_master.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>

int main( )
{
    int a[5], i;

    #pragma omp parallel
    {
        // Perform some computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] = i * i;

        // Print intermediate results.
        #pragma omp master
            for (i = 0; i < 5; i++)
                printf_s("a[%d] = %d\n", i, a[i]);

        // Wait.
        #pragma omp barrier

        // Continue with the computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] += i;
    }
}
```

```Output
a[0] = 0
a[1] = 1
a[2] = 4
a[3] = 9
a[4] = 16
```

## <a name="ordered"></a><a name="ordered-openmp-directives"></a>Bestellt

Gibt an, dass Code `for` unter einer parallelisierten Schleife wie eine sequenzielle Schleife ausgeführt werden soll.

```cpp
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>Bemerkungen

Die `ordered` Richtlinie muss innerhalb des dynamischen `parallel for` Umfangs `ordered` eines [for](#for-openmp) oder konstrukt mit einer Klausel liegen.

Die `ordered` Richtlinie unterstützt keine Klauseln.

Weitere Informationen finden Sie unter [2.6.6 geordnetes Konstrukt](../../../parallel/openmp/2-6-6-ordered-construct.md).

### <a name="example"></a>Beispiel

```cpp
// omp_ordered.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

static float a[1000], b[1000], c[1000];

void test(int first, int last)
{
    #pragma omp for schedule(static) ordered
    for (int i = first; i <= last; ++i) {
        // Do something here.
        if (i % 2)
        {
            #pragma omp ordered
            printf_s("test() iteration %d\n", i);
        }
    }
}

void test2(int iter)
{
    #pragma omp ordered
    printf_s("test2() iteration %d\n", iter);
}

int main( )
{
    int i;
    #pragma omp parallel
    {
        test(1, 8);
        #pragma omp for ordered
        for (i = 0 ; i < 5 ; i++)
            test2(i);
    }
}
```

```Output
test() iteration 1
test() iteration 3
test() iteration 5
test() iteration 7
test2() iteration 0
test2() iteration 1
test2() iteration 2
test2() iteration 3
test2() iteration 4
```

## <a name="parallel"></a><a name="parallel"></a>Parallel

Definiert einen parallelen Bereich, d. h. Code, der von mehreren Threads parallel ausgeführt wird.

```cpp
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parameter

*Klauseln*<br/>
(Optional) Null oder mehr Klauseln, siehe Abschnitt **"Bemerkungen".**

### <a name="remarks"></a>Bemerkungen

Die `parallel` Richtlinie unterstützt die folgenden Klauseln:

- [if](openmp-clauses.md#if-openmp)
- [privat](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [Standard](openmp-clauses.md#default-openmp)
- [geteilt](openmp-clauses.md#shared-openmp)
- [copyin](openmp-clauses.md#copyin)
- [reduction](openmp-clauses.md#reduction)
- [num_threads](openmp-clauses.md#num-threads)

`parallel`kann auch mit den [Richtlinien für](#for-openmp) und [Abschnitte](#sections-openmp) verwendet werden.

Weitere Informationen finden Sie unter [2.3 paralleles Konstrukt](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Beispiel

Das folgende Beispiel zeigt, wie Sie die Anzahl der Threads festlegen und einen parallelen Bereich definieren. Die Anzahl der Threads ist standardmäßig gleich der Anzahl der logischen Prozessoren auf dem Computer. Wenn Sie z. B. über einen Computer mit einem physischen Prozessor verfügen, für den Hyperthreading aktiviert ist, verfügt er über zwei logische Prozessoren und zwei Threads. Die Reihenfolge der Ausgabe kann auf verschiedenen Maschinen variieren.

```cpp
// omp_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(4)
   {
      int i = omp_get_thread_num();
      printf_s("Hello from thread %d\n", i);
   }
}
```

```Output
Hello from thread 0
Hello from thread 1
Hello from thread 2
Hello from thread 3
```

## <a name="sections"></a><a name="sections-openmp"></a>Bereichen

Identifiziert Codeabschnitte, die auf alle Threads aufgeteilt werden sollen.

```cpp
#pragma omp [parallel] sections [clauses]
{
   #pragma omp section
   {
      code_block
   }
}
```

### <a name="parameters"></a>Parameter

*Klauseln*<br/>
(Optional) Null oder mehr Klauseln, siehe Abschnitt **"Bemerkungen".**

### <a name="remarks"></a>Bemerkungen

Die `sections` Direktive kann `section` null oder mehr Richtlinien enthalten.

Die `sections` Richtlinie unterstützt die folgenden Klauseln:

- [privat](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [Nowait](openmp-clauses.md#nowait)

Wenn `parallel` auch `clauses` angegeben, kann eine Klausel `parallel` `sections` von der `nowait`oder Richtlinien akzeptiert werden, außer .

Weitere Informationen finden Sie unter [2.4.2 Abschnitte erstellen](../../../parallel/openmp/2-4-2-sections-construct.md).

### <a name="example"></a>Beispiel

```cpp
// omp_sections.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
    #pragma omp parallel sections num_threads(4)
    {
        printf_s("Hello from thread %d\n", omp_get_thread_num());
        #pragma omp section
        printf_s("Hello from thread %d\n", omp_get_thread_num());
    }
}
```

```Output
Hello from thread 0
Hello from thread 0
```

## <a name="single"></a><a name="single"></a>Einzelnen

Hier können Sie angeben, dass ein Codeabschnitt für einen einzelnen Thread ausgeführt werden soll, nicht unbedingt für den Masterthread.

```cpp
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parameter

*Klauseln*<br/>
(Optional) Null oder mehr Klauseln, siehe Abschnitt **"Bemerkungen".**

### <a name="remarks"></a>Bemerkungen

Die `single` Richtlinie unterstützt die folgenden Klauseln:

- [privat](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [copyprivate](openmp-clauses.md#copyprivate)
- [Nowait](openmp-clauses.md#nowait)

Mit der [Masterdirektive](#master) können Sie angeben, dass ein Codeabschnitt nur für den Masterthread ausgeführt werden soll.

Weitere Informationen finden Sie unter [2.4.3 Single Construct](../../../parallel/openmp/2-4-3-single-construct.md).

### <a name="example"></a>Beispiel

```cpp
// omp_single.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(2)
   {
      #pragma omp single
      // Only a single thread can read the input.
      printf_s("read input\n");

      // Multiple threads in the team compute the results.
      printf_s("compute results\n");

      #pragma omp single
      // Only a single thread can write the output.
      printf_s("write output\n");
    }
}
```

```Output
read input
compute results
compute results
write output
```

## <a name="threadprivate"></a><a name="threadprivate"></a>Threadprivate

Gibt an, dass eine Variable für einen Thread privat ist.

```cpp
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>Parameter

*var*<br/>
Eine durch Kommas getrennte Liste von Variablen, die für einen Thread privat werden sollen. *var* muss entweder eine Variable mit globalem oder Namespace-Bereich oder eine lokale statische Variable sein.

### <a name="remarks"></a>Bemerkungen

Die `threadprivate` Richtlinie unterstützt keine Klauseln.

Die `threadprivate` Direktive basiert auf dem [thread-Attribut,](../../../cpp/thread.md) das das [Schlüsselwort __declspec](../../../cpp/declspec.md) verwendet. Grenzwerte `__declspec(thread)` für `threadprivate`die Anwendung auf . Beispielsweise ist `threadprivate` eine Variable in jedem Thread vorhanden, der im Prozess gestartet wurde, nicht nur in den Threads, die Teil eines Threadteams sind, das von einem parallelen Bereich erstellt wurde. Beachten Sie dieses Implementierungsdetail; Sie können feststellen, dass `threadprivate` Konstruktoren für einen benutzerdefinierten Typ häufiger als erwartet aufgerufen werden.

Sie können `threadprivate` in einer DLL verwenden, die beim Prozessstart statisch `threadprivate` geladen wird, Sie können jedoch keine DLL verwenden, die über [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) geladen wird, `LoadLibrary`z. B. DLLs, die mit [/DELAYLOAD (Delay Load Import)](../../../build/reference/delayload-delay-load-import.md)geladen werden, das auch verwendet.

Eine `threadprivate` Variable eines *zerstörbaren* Typs hat nicht garantiert, dass ihr Destruktor aufgerufen wird. Beispiel:

```cpp
struct MyType
{
    ~MyType();
};

MyType threaded_var;
#pragma omp threadprivate(threaded_var)
int main()
{
    #pragma omp parallel
    {}
}
```

Benutzer haben keine Kontrolle darüber, wann die Threads, die den parallelen Bereich bilden, beendet werden. Wenn diese Threads beim Beenden des Prozesses vorhanden sind, werden die Threads nicht über den Prozessausgang `threaded_var` benachrichtigt, und der Destruktor wird für keinen Thread außer dem, der beendet wird (hier der primäre Thread), aufgerufen. Code sollte also nicht mit `threadprivate` der ordnungsgemäßen Zerstörung von Variablen rechnen.

Weitere Informationen finden Sie unter [2.7.1 threadprivate direkt](../../../parallel/openmp/2-7-1-threadprivate-directive.md).

### <a name="example"></a>Beispiel

Eine Verwendungsprobe `threadprivate`finden Sie unter [privat](openmp-clauses.md#private-openmp).

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
ms.openlocfilehash: bfd2cec32acdd6431a571916f1c80e1700ef3af7
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441775"
---
# <a name="openmp-directives"></a>OpenMP-Direktiven

Stellt Links zu Anweisungen bereit, die in der OpenMP-API verwendet werden.

Visual C++ unterstützt die folgenden OpenMP-Direktiven.

Für parallele Arbeits Freigabe:

|Direktive|BESCHREIBUNG|
|---------|-----------|
|[parallel](#parallel)|Definiert einen parallelen Bereich, bei dem es sich um Code handelt, der von mehreren Threads parallel ausgeführt wird.|
|[for](#for-openmp)|Bewirkt, dass die Arbeit in einer `for`-Schleife innerhalb eines parallelen Bereichs in Threads aufgeteilt wird.|
|[sections](#sections-openmp)|Identifiziert Code Abschnitte, die in alle Threads aufgeteilt werden sollen.|
|[single](#single)|Ermöglicht Ihnen, anzugeben, dass ein Code Abschnitt für einen einzelnen Thread, nicht notwendigerweise für den Master Thread, ausgeführt werden soll.|

Für Master und Synchronisierung:

|Direktive|BESCHREIBUNG|
|---------|-----------|
|[master](#master)|Gibt an, dass nur der Master Thread einen Abschnitt des Programms ausführen soll.|
|[Kritisch](#critical)|Gibt an, dass der Code nur auf einem Thread gleichzeitig ausgeführt wird.|
|[barrier](#barrier)|Synchronisiert alle Threads in einem Team. alle Threads werden an der Barriere angehalten, bis alle Threads die Barriere ausführen.|
|[atomic](#atomic)|Gibt an, dass eine Speicheradresse atomarisch aktualisiert wird.|
|[flush](#flush-openmp)|Gibt an, dass alle Threads dieselbe Ansicht des Arbeitsspeichers für alle freigegebenen Objekte haben.|
|[bestellen](#ordered-openmp-directives)|Gibt an, dass der Code in einer parallelisierten `for` Schleife wie eine sequenzielle Schleife ausgeführt werden soll.|

Für Daten Umgebung:

|Direktive|BESCHREIBUNG|
|---------|-----------|
|[threadprivate](#threadprivate)|Gibt an, dass eine Variable für einen Thread privat ist.|

## <a name="atomic"></a>Atomic

Gibt an, dass eine Speicheradresse atomarisch aktualisiert wird.

```cpp
#pragma omp atomic
   expression
```

### <a name="parameters"></a>Parameter

*expression*<br/>
Die Anweisung mit dem *Lvalue-Wert*, dessen Speicherort Sie vor mehr als einem Schreibvorgang schützen möchten.

### <a name="remarks"></a>Bemerkungen

Die `atomic`-Anweisung unterstützt keine Klauseln.

Weitere Informationen finden Sie unter [2.6.4 Atomic Construct](../../../parallel/openmp/2-6-4-atomic-construct.md).

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

## <a name="barrier"></a>Barriere

Synchronisiert alle Threads in einem Team. alle Threads werden an der Barriere angehalten, bis alle Threads die Barriere ausführen.

```cpp
#pragma omp barrier
```

### <a name="remarks"></a>Bemerkungen

Die `barrier`-Anweisung unterstützt keine Klauseln.

Weitere Informationen finden Sie unter [2.6.3 Barrier Directive](../../../parallel/openmp/2-6-3-barrier-directive.md).

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `barrier`finden Sie unter [Master](#master).

## <a name="critical"></a>kritisch

Gibt an, dass der Code nur auf einem Thread gleichzeitig ausgeführt wird.

```cpp
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>Parameter

*name*<br/>
Optionale Ein Name, der den kritischen Code identifiziert. Der Name muss in Klammern eingeschlossen werden.

### <a name="remarks"></a>Bemerkungen

Die `critical`-Anweisung unterstützt keine Klauseln.

Weitere Informationen finden Sie unter " [2.6.2 Critical Construct](../../../parallel/openmp/2-6-2-critical-construct.md)".

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

## <a name="flush-openmp"></a>Flächen

Gibt an, dass alle Threads dieselbe Ansicht des Arbeitsspeichers für alle freigegebenen Objekte haben.

```cpp
#pragma omp flush [(var)]
```

### <a name="parameters"></a>Parameter

*var*<br/>
Optionale Eine durch Trennzeichen getrennte Liste von Variablen, die Objekte darstellen, die Sie synchronisieren möchten. Wenn *var* nicht angegeben wird, wird der gesamte Arbeitsspeicher geleert.

### <a name="remarks"></a>Bemerkungen

Die `flush`-Anweisung unterstützt keine Klauseln.

Weitere Informationen finden Sie unter [2.6.5 Flush-Direktive](../../../parallel/openmp/2-6-5-flush-directive.md).

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

## <a name="for-openmp"></a>damit

Bewirkt, dass die Arbeit in einer `for`-Schleife innerhalb eines parallelen Bereichs in Threads aufgeteilt wird.

```cpp
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>Parameter

*bezogene*<br/>
Optionale NULL oder mehr Klauseln finden Sie im Abschnitt " **Hinweise** ".

*for_statement*<br/>
Eine `for`-Schleife. Nicht definiertes Verhalten führt dazu, dass der Benutzercode in der `for`-Schleife die Index Variable ändert.

### <a name="remarks"></a>Bemerkungen

Die `for`-Direktive unterstützt die folgenden Klauseln:

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [bestellen](openmp-clauses.md#ordered-openmp-clauses)
- [schedule](openmp-clauses.md#schedule)
- [nowait](openmp-clauses.md#nowait)

Wenn `parallel` ebenfalls angegeben ist, kann `clauses` jede von der `parallel`-oder `for` Direktive akzeptierte Klausel sein, ausgenommen `nowait`.

Weitere Informationen finden Sie unter [2.4.1 für Konstrukt](../../../parallel/openmp/2-4-1-for-construct.md).

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

## <a name="master"></a>Herrn

Gibt an, dass nur der Master Thread einen Abschnitt des Programms ausführen soll.

```cpp
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>Bemerkungen

Die `master`-Anweisung unterstützt keine Klauseln.

Mit der [einzelnen](#single) -Direktive können Sie angeben, dass ein Code Abschnitt für einen einzelnen Thread, nicht notwendigerweise für den Master Thread, ausgeführt werden soll.

Weitere Informationen finden Sie unter [2.6.1 Master Construct](../../../parallel/openmp/2-6-1-master-construct.md).

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

## <a name="ordered-openmp-directives"></a>bestellen

Gibt an, dass der Code in einer parallelisierten `for` Schleife wie eine sequenzielle Schleife ausgeführt werden soll.

```cpp
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>Bemerkungen

Die `ordered`-Direktive muss innerhalb des dynamischen Wertebereichs eines [for](#for-openmp) -oder `parallel for`-Konstrukts mit einer `ordered`-Klausel liegen.

Die `ordered`-Anweisung unterstützt keine Klauseln.

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

## <a name="parallel"></a>zeitige

Definiert einen parallelen Bereich, bei dem es sich um Code handelt, der von mehreren Threads parallel ausgeführt wird.

```cpp
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parameter

*bezogene*<br/>
Optionale NULL oder mehr Klauseln finden Sie im Abschnitt " **Hinweise** ".

### <a name="remarks"></a>Bemerkungen

Die `parallel`-Direktive unterstützt die folgenden Klauseln:

- [if](openmp-clauses.md#if-openmp)
- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [Standardwert](openmp-clauses.md#default-openmp)
- [Genu](openmp-clauses.md#shared-openmp)
- [copyin](openmp-clauses.md#copyin)
- [reduction](openmp-clauses.md#reduction)
- [num_threads](openmp-clauses.md#num-threads)

`parallel` können auch mit den Anweisungen [for](#for-openmp) und [Abschnitts](#sections-openmp) verwendet werden.

Weitere Informationen finden Sie unter [2,3 parallel Construct](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie die Anzahl von Threads festgelegt und ein paralleler Bereich definiert wird. Die Anzahl der Threads ist standardmäßig gleich der Anzahl der logischen Prozessoren auf dem Computer. Wenn Sie z. b. über einen Computer mit einem physischen Prozessor verfügen, für den Hyperthreading aktiviert ist, verfügt er über zwei logische Prozessoren und zwei Threads. Die Reihenfolge der Ausgabe kann sich auf verschiedenen Computern unterscheiden.

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

## <a name="sections-openmp"></a>Strecken

Identifiziert Code Abschnitte, die in alle Threads aufgeteilt werden sollen.

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

*bezogene*<br/>
Optionale NULL oder mehr Klauseln finden Sie im Abschnitt " **Hinweise** ".

### <a name="remarks"></a>Bemerkungen

Die `sections`-Direktive kann NULL oder mehr `section` Direktiven enthalten.

Die `sections`-Direktive unterstützt die folgenden Klauseln:

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [nowait](openmp-clauses.md#nowait)

Wenn `parallel` ebenfalls angegeben ist, kann `clauses` jede von der `parallel`-oder `sections` Direktive akzeptierte Klausel sein, ausgenommen `nowait`.

Weitere Informationen finden Sie unter [2.4.2 Abschnitts Construct](../../../parallel/openmp/2-4-2-sections-construct.md).

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

## <a name="single"></a>Gänger

Ermöglicht Ihnen, anzugeben, dass ein Code Abschnitt für einen einzelnen Thread, nicht notwendigerweise für den Master Thread, ausgeführt werden soll.

```cpp
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parameter

*bezogene*<br/>
Optionale NULL oder mehr Klauseln finden Sie im Abschnitt " **Hinweise** ".

### <a name="remarks"></a>Bemerkungen

Die `single`-Direktive unterstützt die folgenden Klauseln:

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [copyprivate](openmp-clauses.md#copyprivate)
- [nowait](openmp-clauses.md#nowait)

Mithilfe der [Master](#master) -Direktive können Sie angeben, dass ein Code Abschnitt nur für den Master Thread ausgeführt werden soll.

Weitere Informationen finden Sie unter " [2.4.3 Single Construct](../../../parallel/openmp/2-4-3-single-construct.md)".

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

## <a name="threadprivate"></a>Thread private

Gibt an, dass eine Variable für einen Thread privat ist.

```cpp
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>Parameter

*var*<br/>
Eine durch Trennzeichen getrennte Liste von Variablen, die Sie als privat in einem Thread einrichten möchten. *var* muss entweder eine globale oder eine Namespace bezogene Variable oder eine lokale statische Variable sein.

### <a name="remarks"></a>Bemerkungen

Die `threadprivate`-Anweisung unterstützt keine Klauseln.

Die `threadprivate`-Direktive basiert auf dem [Thread](../../../cpp/thread.md) -Attribut, das das [__declspec](../../../cpp/declspec.md) -Schlüsselwort verwendet. Grenzwerte für `__declspec(thread)` gelten für `threadprivate`. Beispielsweise ist eine `threadprivate` Variable in jedem Thread vorhanden, der während des Prozesses gestartet wird, nicht nur die Threads, die Teil eines Thread Teams sind, das von einem parallelen Bereich erzeugt wurde. Beachten Sie diese Implementierungsdetails. Sie werden feststellen, dass Konstruktoren für einen `threadprivate` benutzerdefinierten Typs häufiger als erwartet aufgerufen werden.

Sie können `threadprivate` in einer DLL verwenden, die beim Prozessstart statisch geladen wird. Sie können jedoch `threadprivate` nicht in einer DLL verwenden, die über [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) geladen wird, z. b. DLLs, die mit/DELAYLOAD geladen werden [(verzögertes Laden importieren)](../../../build/reference/delayload-delay-load-import.md), wodurch auch `LoadLibrary`verwendet wird.

Bei einer `threadprivate` *Variablen eines debugierbaren Typs ist* gewährleistet, dass der Debuggertyp nicht mit dem Namen Beispiel:

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

Benutzer haben keine Kontrolle darüber, wann die Threads, die den parallelen Bereich bilden, beendet werden. Wenn diese Threads vorhanden sind, wenn der Prozess beendet wird, werden die Threads über den Prozess Vorgang nicht benachrichtigt, und der debugtor wird nicht für `threaded_var` in einem Thread aufgerufen, außer dem, der beendet wird (hier der primäre Thread). Code sollte also nicht bei der ordnungsgemäßen Zerstörung `threadprivate` Variablen gezählt werden.

Weitere Informationen finden Sie unter [2.7.1 Thread private-Direktive](../../../parallel/openmp/2-7-1-threadprivate-directive.md).

### <a name="example"></a>Beispiel

Ein Beispiel für die Verwendung von `threadprivate`finden Sie unter [private](openmp-clauses.md#private-openmp).

---
title: Übersicht über C++ AMP
ms.date: 11/19/2018
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, requirements
- C++ Accelerated Massive Parallelism, architecture
- C++ AMP
- C++ Accelerated Massive Parallelism, overview
- C++ Accelerated Massive Parallelism
ms.assetid: 9e593b06-6e3c-43e9-8bae-6d89efdd39fc
ms.openlocfilehash: 5c9819c1d9167bea9a9bedeef2ac44798d5a121f
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404846"
---
# <a name="c-amp-overview"></a>Übersicht über C++ AMP

C++ Accelerated Massive Parallelism (C++ AMP) beschleunigt die Ausführung von C++-Code, indem die Vorteile Daten parallel verarbeitender Hardware, beispielsweise ein Grafikprozessor (Graphics Processing Unit, GPU) auf einer separaten Grafikkarte, genutzt werden. Sie können mithilfe von C++ AMP mehrdimensionale Datenalgorithmen programmieren, sodass die Ausführung durch die parallele Verarbeitung auf heterogener Hardware beschleunigt werden kann. Das C++ AMP-Programmiermodell umfasst mehrdimensionale Arrays, Indizierung, Arbeitsspeicherübertragung, Kacheln und eine Bibliothek mathematischer Funktionen. Sie können C++ AMP-Spracherweiterungen verwenden, um zu steuern, wie Daten von der CPU zur GPU und umgekehrt verschoben werden, sodass Sie die Leistung verbessern können.

## <a name="system-requirements"></a>Systemanforderungen

- Windows 7 oder höher

- Windows Server 2008 R2 oder höher

- DirectX 11-Funktionsebene 11.0 oder aktuellere Hardware

- Für das Debuggen im Software Emulator ist Windows 8 oder Windows Server 2012 erforderlich. Für das Debuggen auf der Hardware müssen Sie die Treiber für Ihre Grafikkarte installieren. Weitere Informationen finden Sie unter [Debuggen von GPU-Code](/visualstudio/debugger/debugging-gpu-code).

- Hinweis: amp wird derzeit auf ARM64 nicht unterstützt.

## <a name="introduction"></a>Einführung

Die folgenden beiden Beispielen veranschaulichen die primären Komponenten von C++ AMP. Angenommen, Sie möchten die entsprechenden Elemente zweier eindimensionaler Arrays addieren. Beispielsweise können Sie `{1, 2, 3, 4, 5}` und zum Abrufen von hinzufügen `{6, 7, 8, 9, 10}` `{7, 9, 11, 13, 15}` . Ohne C++ AMP zu verwenden, schreiben Sie den folgenden Code, um die Zahlen zu addieren und die Ergebnisse anzuzeigen.

```cpp
#include <iostream>

void StandardMethod() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    for (int idx = 0; idx < 5; idx++)
    {
        sumCPP[idx] = aCPP[idx] + bCPP[idx];
    }

    for (int idx = 0; idx < 5; idx++)
    {
        std::cout << sumCPP[idx] << "\n";
    }
}
```

Die wichtigen Teile des Codes lauten wie folgt:

- Daten: Die Daten bestehen aus drei Arrays. Alle haben den gleichen Rang (Eins) und die gleiche Länge (Fünf).

- Iteration: Die erste `for`-Schleife stellt einen Mechanismus für das Durchlaufen der Elemente in den Arrays bereit. Der Code, der zur Berechnung der Summen ausgeführt werden soll, befindet sich im ersten `for`-Block.

- Index: Über die Variable `idx` wird auf die einzelnen Elemente der Arrays zugegriffen.

Bei Verwendung von C++ AMP können Sie stattdessen den folgenden Code schreiben.

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

const int size = 5;

void CppAmpMethod() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[size];

    // Create C++ AMP objects.
    array_view<const int, 1> a(size, aCPP);
    array_view<const int, 1> b(size, bCPP);
    array_view<int, 1> sum(size, sumCPP);
    sum.discard_data();

    parallel_for_each(
        // Define the compute domain, which is the set of threads that are created.
        sum.extent,
        // Define the code to run on each thread on the accelerator.
        [=](index<1> idx) restrict(amp) {
            sum[idx] = a[idx] + b[idx];
        }
    );

    // Print the results. The expected output is "7, 9, 11, 13, 15".
    for (int i = 0; i < size; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

Es sind zwar die gleichen grundlegenden Elemente vorhanden, es werden jedoch C++ AMP-Konstrukte verwendet:

- Daten: Sie verwenden C++ Arrays, um drei C++ amp [array_view](../../parallel/amp/reference/array-view-class.md) -Objekten zu erstellen. Sie stellen vier Werte zur Verfügung, um ein `array_view`-Objekt zu erstellen: die Datenwerte, den Rang, den Elementtyp und die Länge des `array_view`-Objekts in jeder Dimension. Der Rang und der Typ werden als Typparameter übergeben. Die Daten und die Länge werden als Konstruktorparameter übergeben. In diesem Beispiel ist das an den Konstruktor übergebene C++-Array eindimensional. Der Rang und die Länge werden verwendet, um die rechteckige Form der Daten im `array_view`-Objekt zu erstellen, und die Datenwerte werden verwendet, um das Array zu füllen. Die Lauf Zeit Bibliothek enthält auch die [Array-Klasse](../../parallel/amp/reference/array-class.md), die über eine Schnittstelle verfügt, die der-Klasse ähnelt, und wird weiter unten `array_view` in diesem Artikel erläutert.

- Iteration: die [Parallel_for_each-Funktion (C++ amp)](reference/concurrency-namespace-functions-amp.md#parallel_for_each) stellt einen Mechanismus zum Durchlaufen der Datenelemente oder der *Compute-Domäne*bereit. In diesem Beispiel wird die Compute-Domäne durch `sum.extent` angegeben. Der Code, den Sie ausführen möchten, ist in einem Lambda-Ausdruck oder einer *Kernel Funktion*enthalten. Die Anweisung `restrict(amp)` gibt an, dass nur die Teilmenge der Programmiersprache C++ verwendet wird, die mit C++ AMP beschleunigt werden kann.

- Index: die [Index Klassen](../../parallel/amp/reference/index-class.md) Variable, `idx` , wird mit dem Rang eins deklariert, um dem Rang des Objekts zu entsprechen `array_view` . Mithilfe des Index kann auf die einzelnen Elemente der `array_view`-Objekte zugegriffen werden.

## <a name="shaping-and-indexing-data-index-and-extent"></a>Strukturieren und Indizieren von Daten: Index und Umfang

Sie müssen die Datenwerte definieren und die Form der Daten deklarieren, bevor Sie den Kernelcode ausführen können. Alle Daten werden als Array (rechteckig) definiert, und Sie können das Array mit einem die oft ausgegebene Befehlszeilen  Rang (Anzahl der Dimensionen) definieren. Die Daten können in jeder Dimension von beliebiger Größe sein.

### <a name="index-class"></a>index-Klasse

Die [Index Klasse](../../parallel/amp/reference/index-class.md) gibt eine Position im- `array` oder-Objekt an, `array_view` indem der Offset vom Ursprung in jeder Dimension in ein Objekt eingeschlossen wird. Wenn Sie auf eine Position im Array zugreifen, übergeben Sie ein `index`-Objekt an den Indizierungsoperator `[]` statt einer Liste mit ganzzahligen Indizes. Sie können auf die Elemente in jeder Dimension zugreifen, indem Sie den [Array:: Operator ()-Operator](reference/array-class.md#operator_call) oder den [array_view:: Operator ()](reference/array-view-class.md#operator_call)-Operator verwenden.

Im folgenden Beispiel wird ein eindimensionaler Index erstellt, der das dritte Element in einem eindimensionalen `array_view`-Objekt angibt. Der Index wird verwendet, um das dritte Element im `array_view`-Objekt auszugeben. Die Ausgabe lautet 3.

```cpp
int aCPP[] = {1, 2, 3, 4, 5};
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout << a[idx] << "\n";
// Output: 3
```

Im folgenden Beispiel wird ein zweidimensionaler Index erstellt, der das Element angibt, bei dem die Zeile = 1 und die Spalte = 2 in einem zweidimensionalen `array_view`-Objekt ist. Der erste Parameter im `index`-Konstruktor ist die Zeilenkomponente, und der zweite Parameter ist die Spaltenkomponente. Die Ausgabe ist 6.

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6};
array_view<int, 2> a(2, 3, aCPP);

index<2> idx(1, 2);

std::cout <<a[idx] << "\n";
// Output: 6
```

Im folgenden Beispiel wird ein dreidimensionaler Index erstellt, der das-Element angibt, bei dem die Tiefe = 0, die Zeile = 1 und die Spalte = 3 in einem dreidimensionalen `array_view` Objekt ist. Beachten Sie, dass der erste Parameter die Tiefenkomponente, der zweite Parameter die Zeilenkomponente und der dritte Parameter die Spaltenkomponente ist. Die Ausgabe lautet 8.

```cpp
int aCPP[] = {
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};

array_view<int, 3> a(2, 3, 4, aCPP);

// Specifies the element at 3, 1, 0.
index<3> idx(0, 1, 3);

std::cout << a[idx] << "\n";
// Output: 8
```

### <a name="extent-class"></a>extent-Klasse

Die Block [Klasse](../../parallel/amp/reference/extent-class.md) gibt die Länge der Daten in jeder Dimension des- `array` Objekts oder des-Objekts an `array_view` . Sie können einen Wertebereich erstellen und diesen verwenden, um ein `array`- oder `array_view`-Objekt zu erstellen. Sie können den Wertebereich eines vorhandenen `array`- oder `array_view`-Objekts auch abrufen. Im folgenden Beispiel wird die Länge des Wertebereichs in jeder Dimension eines `array_view`-Objekts ausgegeben.

```cpp
int aCPP[] = {
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};
// There are 3 rows and 4 columns, and the depth is two.
array_view<int, 3> a(2, 3, 4, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
std::cout << "Length in most significant dimension is " << a.extent[0] << "\n";
```

Im folgenden Beispiel wird ein `array_view`-Objekt erstellt, das die gleichen Dimensionen wie das Objekt im vorherigen Beispiel hat, aber in diesem Beispiel wird ein `extent`-Objekt statt expliziter Parameter im `array_view`-Konstruktor verwendet.

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
```

## <a name="moving-data-to-the-accelerator-array-and-array_view"></a>Verschieben von Daten in die Beschleunigung: array und array_view

In der Laufzeitbibliothek sind zwei Datencontainer definiert, die verwendet werden, um Daten in den Beschleuniger zu verschieben. Dabei handelt es sich um die [Array-Klasse](../../parallel/amp/reference/array-class.md) und die [array_view-Klasse](../../parallel/amp/reference/array-view-class.md). Die `array`-Klasse ist eine Containerklasse, die eine tiefe Kopie der Daten erstellt, wenn das Objekt erstellt wird. Die `array_view`-Klasse ist eine Wrapperklasse, die die Daten kopiert, wenn die Kernelfunktion auf die Daten zugreift. Wenn die Daten auf dem Quellgerät benötigt werden, werden sie zurückkopiert.

### <a name="array-class"></a>array-Klasse

Wenn ein `array`-Objekt erstellt wird und Sie einen Konstruktor verwenden, der einen Zeiger auf das Dataset enthält, wird im Beschleuniger eine tiefe Kopie der Daten erstellt. Die Kernelfunktion ändert die Kopie im Beschleuniger. Wenn die Ausführung der Kernelfunktion beendet ist, müssen Sie die Daten zurück in die Quelldatenstruktur kopieren. Im folgenden Beispiel wird jedes Element in einem Vektor mit 10 multipliziert. Nachdem die Kernel Funktion abgeschlossen wurde, `vector conversion operator` wird der verwendet, um die Daten zurück in das Vektor Objekt zu kopieren.

```cpp
std::vector<int> data(5);

for (int count = 0; count <5; count++)
{
    data[count] = count;
}

array<int, 1> a(5, data.begin(), data.end());

parallel_for_each(
    a.extent,
    [=, &a](index<1> idx) restrict(amp) {
        a[idx] = a[idx]* 10;
    });

data = a;
for (int i = 0; i < 5; i++)
{
    std::cout << data[i] << "\n";
}
```

### <a name="array_view-class"></a>array_view-Klasse

Die `array_view`-Klasse verfügt über fast dieselben Member wie die `array`-Klasse, aber das zugrunde liegende Verhalten ist unterschiedlich. Die Daten, die dem `array_view`-Konstruktor übergeben werden, werden nicht wie beim `array`-Konstruktor im Grafikprozessor repliziert. Stattdessen werden die Daten in den Beschleuniger kopiert, wenn die Kernelfunktion ausgeführt wird. Wenn Sie zwei `array_view`-Objekte erstellen, die dieselben Daten verwenden, verweisen daher beide `array_view`-Objekte auf denselben Arbeitsspeicherbereich. In diesem Fall müssen Sie jeden Multithreaded-Zugriff synchronisieren. Der Hauptvorteil bei der Verwendung der `array_view`-Klasse besteht darin, dass Daten nur verschoben werden, wenn es erforderlich ist.

### <a name="comparison-of-array-and-array_view"></a>Vergleich von "array" und "array_view"

In der folgenden Tabelle werden die Übereinstimmungen und Unterschiede zwischen der `array`- und der `array_view`-Klasse zusammengefasst.

|BESCHREIBUNG|array-Klasse|array_view-Klasse|
|-----------------|-----------------|-----------------------|
|Zeitpunkt der Bestimmung des Rangs|Beim Kompilieren|Beim Kompilieren|
|Zeitpunkt der Bestimmung des Wertebereichs|Zur Laufzeit|Zur Laufzeit|
|Form|Rechteckig|Rechteckig|
|Datenspeicher|Ist ein Datencontainer|Ist ein Datenwrapper|
|Kopieren|Explizit und tiefe Kopie während der Definition|Implizite Kopie, wenn von der Kernelfunktion darauf zugegriffen wird|
|Abrufen von Daten|Durch Kopieren der Arraydaten zurück in ein Objekt im CPU-Thread|Durch direkten Zugriff auf das `array_view` Objekt oder durch Aufrufen der [Methode array_view:: Synchronisieren](reference/array-view-class.md#synchronize) , um weiterhin auf die Daten im ursprünglichen Container zuzugreifen.|

### <a name="shared-memory-with-array-and-array_view"></a>Freigegebener Speicher mit array und array_view

Freigegebener Arbeitsspeicher ist der Arbeitsspeicher, auf den sowohl die CPU als auch die Zugriffstaste zugreifen kann. Durch die Verwendung von freigegebenem Arbeitsspeicher entfällt bzw. reduziert sich der Mehraufwand zum Kopieren von Daten zwischen CPU und der Zugriffstaste erheblich. Obwohl der Arbeitsspeicher freigegeben wird, kann darauf nicht von CPU und der Zugriffstaste gleichzeitig zugegriffen werden. In diesem Fall kommt es zu einem nicht definierten Verhalten.

Mithilfe von `array`-Objekten kann die Verwendung von freigegebenem Arbeitsspeicher präzise gesteuert werden, sofern die zugeordnete Zugriffstaste dies unterstützt. Ob eine Zugriffstaste freigegebenen Speicher unterstützt, wird durch die [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) -Eigenschaft der Zugriffstaste bestimmt, die **true** zurückgibt, wenn Shared Memory unterstützt wird. Wenn Shared Memory unterstützt wird, wird die standardmäßige [access_type Enumeration](reference/concurrency-namespace-enums-amp.md#access_type) für Speicher Belegungen auf der Zugriffstaste durch die- `default_cpu_access_type` Eigenschaft bestimmt. Standardmäßig wird für `array`- und `array_view`-Objekte der gleiche `access_type` wie für das primäre zugeordnete `accelerator`-Objekt verwendet.

Indem Sie die [Array:: cpu_access_type-Datenmember](reference/array-class.md#cpu_access_type) -Eigenschaft eines `array` explizit festlegen, können Sie die Verwendung von frei gegebenem Arbeitsspeicher präzise steuern, damit Sie die App basierend auf den Speicherzugriffs Mustern der berechnungskerne für die Leistungsmerkmale der Hardware optimieren können. Ein `array_view`-Objekt verfügt über das gleiche `cpu_access_type`-Objekt wie das `array`, dem es zugeordnet ist; oder wenn das array_view-Objekt ohne eine Datenquelle erstellt wird, spiegelt sein `access_type`-Objekt die Umgebung, in der die erste Speicherbelegung erfolgte. Das bedeutet, dass es sich bei einem Erstzugriff durch den Host (CPU) so verhält, als ob es über eine CPU-Datenquelle erstellt wurde und es gibt das `access_type`-Objekt des  `accelerator_view`-Objekts frei, das durch die Erfassung zugeordnet wird. Wenn jedoch auf sie zunächst von einem `accelerator_view`-Objekt zugegriffen wird, dann verhält es sich, als ob es über ein `array`-Objekt erstellt wurde, das auf diesem `accelerator_view`-Objekt erstellt wurde. Es wird das `array`-Objekt des `access_type`-Objekts freigegeben.

Das folgende Codebeispiel zeigt, wie Sie bestimmen, ob die Standardzugriffstaste freigegebenen Arbeitsspeicher unterstützt, und erstellt anschließend mehrere Arrays mit verschiedenen cpu_access_type-Konfigurationen.

```cpp
#include <amp.h>
#include <iostream>

using namespace Concurrency;

int main()
{
    accelerator acc = accelerator(accelerator::default_accelerator);

    // Early out if the default accelerator doesn’t support shared memory.
    if (!acc.supports_cpu_shared_memory)
    {
        std::cout << "The default accelerator does not support shared memory" << std::endl;
        return 1;
    }

    // Override the default CPU access type.
    acc.default_cpu_access_type = access_type_read_write

    // Create an accelerator_view from the default accelerator. The
    // accelerator_view inherits its default_cpu_access_type from acc.
    accelerator_view acc_v = acc.default_view;

    // Create an extent object to size the arrays.
    extent<1> ex(10);

    // Input array that can be written on the CPU.
    array<int, 1> arr_w(ex, acc_v, access_type_write);

    // Output array that can be read on the CPU.
    array<int, 1> arr_r(ex, acc_v, access_type_read);

    // Read-write array that can be both written to and read from on the CPU.
    array<int, 1> arr_rw(ex, acc_v, access_type_read_write);
}
```

## <a name="executing-code-over-data-parallel_for_each"></a>Ausführen von Code zu Daten: parallel_for_each

Die [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) -Funktion definiert den Code, den Sie auf der Zugriffstaste für die Daten im- `array` Objekt oder-Objekt ausführen möchten `array_view` . Betrachten Sie den folgenden Code aus der Einführung dieses Themas.

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

void AddArrays() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5] = {0, 0, 0, 0, 0};

    array_view<int, 1> a(5, aCPP);
    array_view<int, 1> b(5, bCPP);
    array_view<int, 1> sum(5, sumCPP);

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp)
        {
            sum[idx] = a[idx] + b[idx];
        }
    );

    for (int i = 0; i < 5; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

Die `parallel_for_each`-Methode akzeptiert zwei Argumente, eine Compute-Domäne und einen Lambda-Ausdruck.

Die *Compute-Domäne* ist ein `extent` Objekt oder ein- `tiled_extent` Objekt, das den Satz von Threads definiert, die für die parallele Ausführung erstellt werden sollen. Für jedes Element in der Compute-Domäne wird ein Thread generiert. In diesem Fall ist das `extent`-Objekt eindimensional und hat fünf Elemente. Daher werden fünf Threads gestartet.

Der *Lambda-Ausdruck* definiert den Code, der in jedem Thread ausgeführt werden soll. Die `[=]` Erfassungs Klausel gibt an, dass der Text des Lambda-Ausdrucks auf alle erfassten Variablen nach Wert zugreift, in diesem Fall, `a` `b` und `sum` . In diesem Beispiel wird in der Parameterliste eine eindimensionale `index`-Variable mit dem Namen `idx` erstellt. Der Wert von `idx[0]` beträgt im ersten Thread null und wird in jedem nachfolgenden Thread um eins erhöht. Die Anweisung `restrict(amp)` gibt an, dass nur die Teilmenge der Programmiersprache C++ verwendet wird, die mit C++ AMP beschleunigt werden kann.  Die Einschränkungen für Funktionen, die den einschränkungsmodifizierer aufweisen, werden unter [einschränken (C++ amp)](../../cpp/restrict-cpp-amp.md)beschrieben. Weitere Informationen finden Sie unter [Lambda-Ausdrucks Syntax](../../cpp/lambda-expression-syntax.md).

Der Lambdaausdruck kann den auszuführenden Code enthalten oder eine separate Kernelfunktion aufrufen. Die Kernelfunktion muss den `restrict(amp)`-Modifizierer enthalten. Das folgende Beispiel entspricht dem vorherigen Beispiel, jedoch wird eine separate Kernelfunktion aufgerufen.

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

void AddElements(
    index<1> idx,
    array_view<int, 1> sum,
    array_view<int, 1> a,
    array_view<int, 1> b) restrict(amp) {
    sum[idx] = a[idx] + b[idx];
}

void AddArraysWithFunction() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5] = {0, 0, 0, 0, 0};

    array_view<int, 1> a(5, aCPP);
    array_view<int, 1> b(5, bCPP);
    array_view<int, 1> sum(5, sumCPP);

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp) {
            AddElements(idx, sum, a, b);
        }
    );

    for (int i = 0; i < 5; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

## <a name="accelerating-code-tiles-and-barriers"></a>Beschleunigen von Code: Kacheln und Barrieren

Sie können eine zusätzliche Beschleunigung erreichen, indem Sie Kacheln verwenden. Beim ticken werden die Threads in gleiche rechteckige Teilmengen oder *Kacheln*aufgeteilt. Sie bestimmen die geeignete Kachelgröße auf der Basis des Datasets und des Algorithmus, den Sie programmieren. Für jeden Thread haben Sie Zugriff auf den *globalen* Speicherort eines Datenelements relativ zum ganzen `array` oder `array_view` und auf den *lokalen* Speicherort relativ zur Kachel. Die Verwendung des lokalen Indexwerts vereinfacht den Code, da Sie keinen Code schreiben müssen, um globale Indexwerte in lokale zu übersetzen. Um das Ticken zu verwenden, rufen Sie die Block [:: Tile-Methode](reference/extent-class.md#tile) für die Compute-Domäne in der `parallel_for_each` -Methode auf, und verwenden Sie ein [tiled_index](../../parallel/amp/reference/tiled-index-class.md) -Objekt im Lambda-Ausdruck.

In typischen Anwendungen sind die Elemente in einer Kachel auf irgendeine Weise verknüpft, und der Code muss in der gesamten Kachel auf Werte zugreifen und diese verfolgen. Verwenden Sie das Schlüsselwort Schlüsselwort [tile_static](../../cpp/tile-static-keyword.md) und die [tile_barrier:: Wait-Methode](reference/tile-barrier-class.md#wait) , um dies zu erreichen. Eine Variable mit dem **tile_static** -Schlüsselwort verfügt über einen Bereich über eine gesamte Kachel, und für jede Kachel wird eine Instanz der Variablen erstellt. Sie müssen sich um die Synchronisierung des Kachel-Threadzugriffs auf die Variable kümmern. Die [tile_barrier:: Wait-Methode](reference/tile-barrier-class.md#wait) beendet die Ausführung des aktuellen Threads, bis alle Threads in der Kachel den-Aufrufvorgang erreicht haben `tile_barrier::wait` . Sie können also Werte auf der Kachel sammeln, indem Sie **tile_static** Variablen verwenden. Anschließend können Sie alle Berechnungen beenden, für die der Zugriff auf alle Werte erforderlich ist.

Im folgenden Diagramm wird ein zweidimensionales Array mit Samplingdaten dargestellt, das in Kacheln angeordnet ist.

![Indexwerte in einer gekachelten Erweiterung](../../parallel/amp/media/camptiledgridexample.png "Indexwerte in einer gekachelten Erweiterung")

Im folgenden Codebeispiel werden die Samplingdaten aus dem vorherigen Diagramm verwendet. Im Code wird jeder Wert in der Kachel durch den Durchschnitt der Werte in der Kachel ersetzt.

```cpp
// Sample data:
int sampledata[] = {
    2, 2, 9, 7, 1, 4,
    4, 4, 8, 8, 3, 4,
    1, 5, 1, 2, 5, 2,
    6, 8, 3, 2, 7, 2};

// The tiles:
// 2 2    9 7    1 4
// 4 4    8 8    3 4
//
// 1 5    1 2    5 2
// 6 8    3 2    7 2

// Averages:
int averagedata[] = {
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
};

array_view<int, 2> sample(4, 6, sampledata);

array_view<int, 2> average(4, 6, averagedata);

parallel_for_each(
    // Create threads for sample.extent and divide the extent into 2 x 2 tiles.
    sample.extent.tile<2,2>(),
        [=](tiled_index<2,2> idx) restrict(amp) {
        // Create a 2 x 2 array to hold the values in this tile.
        tile_static int nums[2][2];

        // Copy the values for the tile into the 2 x 2 array.
        nums[idx.local[1]][idx.local[0]] = sample[idx.global];

        // When all the threads have executed and the 2 x 2 array is complete, find the average.
        idx.barrier.wait();
        int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1];

        // Copy the average into the array_view.
        average[idx.global] = sum / 4;
    });

for (int i = 0; i <4; i++) {
    for (int j = 0; j <6; j++) {
        std::cout << average(i,j) << " ";
    }
    std::cout << "\n";
}

// Output:
// 3 3 8 8 3 3
// 3 3 8 8 3 3
// 5 5 2 2 4 4
// 5 5 2 2 4 4
```

## <a name="math-libraries"></a>Mathematische Bibliotheken

C++ AMP enthält zwei mathematische Bibliotheken. Die Bibliothek mit doppelter Genauigkeit im Namespace "Parallelität [::p recise_math](../../parallel/amp/reference/concurrency-precise-math-namespace.md) bietet Unterstützung für Funktionen mit doppelter Genauigkeit. Sie unterstützt auch Funktionen mit einfacher Genauigkeit, obwohl die Unterstützung doppelter Genauigkeit auf der Hardware noch benötigt wird. Sie entspricht der [C99-Spezifikation (ISO/IEC 9899)](https://go.microsoft.com/fwlink/p/?linkid=225887). Der Beschleuniger muss doppelte Genauigkeit vollständig unterstützen. Sie können bestimmen, ob dies geschieht, indem Sie den Wert des [Datenmembers Accelerator:: supports_double_precision](reference/accelerator-class.md#supports_double_precision)überprüfen. Die fast Math Library im [Namespace "parallelcurrency:: fast_math](../../parallel/amp/reference/concurrency-fast-math-namespace.md)" enthält einen weiteren Satz mathematischer Funktionen. Diese Funktionen, die nur `float`-Operanden unterstützen, werden schneller ausgeführt, sind jedoch nicht so präzise wie die Funktionen in der mathematischen Bibliothek mit doppelter Genauigkeit. Die Funktionen sind in der \<amp_math.h> Header Datei enthalten, und alle werden mit deklariert `restrict(amp)` . Die Funktionen in der \<cmath> Header Datei werden in die `fast_math` -und- `precise_math` Namespaces importiert. Das Schlüsselwort " **einschränken** " wird verwendet, um die \<cmath> Version und die C++ amp Version zu unterscheiden. Der folgende Code berechnet mithilfe der schnellen Methode den Logarithmus zur Basis 10 jedes Werts, der in der Berechnungsdomäne enthalten ist.

```cpp
#include <amp.h>
#include <amp_math.h>
#include <iostream>
using namespace concurrency;

void MathExample() {

    double numbers[] = { 1.0, 10.0, 60.0, 100.0, 600.0, 1000.0 };
    array_view<double, 1> logs(6, numbers);

    parallel_for_each(
        logs.extent,
        [=] (index<1> idx) restrict(amp) {
            logs[idx] = concurrency::fast_math::log10(numbers[idx]);
        }
    );

    for (int i = 0; i < 6; i++) {
        std::cout << logs[i] << "\n";
    }
}
```

## <a name="graphics-library"></a>Grafikbibliothek

C++ AMP enthält eine Grafikbibliothek, die für die Programmierung beschleunigter Grafikfunktionen entwickelt wurde. Diese Bibliothek wird nur auf Geräten verwendet, die systemeigene Grafikfunktionen unterstützen. Die Methoden befinden sich im [Namespace "parallelcurrency:: graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md) " und sind in der \<amp_graphics.h> Header Datei enthalten. Die Grafikbibliothek enthält die folgenden Hauptkomponenten:

- [Texture-Klasse](../../parallel/amp/reference/texture-class.md): Sie können die Textur Klasse verwenden, um Texturen aus dem Arbeitsspeicher oder aus einer Datei zu erstellen. Texturen ähneln Arrays, da Sie Daten enthalten, und Sie ähneln Containern in der C++-Standard Bibliothek in Bezug auf Zuweisungs-und Kopier Erstellung. Weitere Informationen finden Sie unter [C++-Standardbibliothekscontainer](../../standard-library/stl-containers.md). Die Vorlagenparameter für die `texture`-Klasse sind der Elementtyp und der Rang. Der Rang kann 1, 2 oder 3 lauten. Der Elementtyp kann einer der Typen kurzer Vektoren sein, die später in diesem Artikel beschrieben werden.

- [writeonly_texture_view-Klasse](../../parallel/amp/reference/writeonly-texture-view-class.md): bietet schreibgeschützten Zugriff auf eine beliebige Textur.

- Short Vector Library: definiert einen Satz von kurzen Vektor Typen der Länge 2, 3 und 4, die auf **int**, `uint` , **float**, **Double**, [Norm](../../parallel/amp/reference/norm-class.md)oder [unorm](../../parallel/amp/reference/unorm-class.md)basieren.

## <a name="universal-windows-platform-uwp-apps"></a>Universelle Windows-Plattform-Apps (UWP)

Wie andere C++-Bibliotheken können Sie C++ amp in ihren UWP-Apps verwenden. In diesen Artikeln wird beschrieben, wie C++ AMP-Code in Apps verwendet wird, die mit C++, C#, Visual Basic oder JavaScript erstellt werden:

- [Verwenden von C++ amp in UWP-apps](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)

- [Exemplarische Vorgehensweise: Erstellen einer grundlegenden Windows-Runtime Komponente in C++ und Aufrufen dieser Komponente über JavaScript](https://go.microsoft.com/fwlink/p/?linkid=249077)

- [Reise-Optimierer für den Reise-Optimierer von Reisekarten, Windows Store-Apps in JavaScript](https://go.microsoft.com/fwlink/p/?linkid=249078)

- [Verwenden von C++ amp aus c# mithilfe des Windows-Runtime](https://devblogs.microsoft.com/pfxteam/how-to-use-c-amp-from-c-using-winrt/)

- [Verwenden von C++ amp aus C #](https://devblogs.microsoft.com/pfxteam/how-to-use-c-amp-from-c/)

- [Aufrufen von systemeigenen Funktionen aus verwaltetem Code](../../dotnet/calling-native-functions-from-managed-code.md)

## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP und Parallelitätsschnellansicht

Die Nebenläufigkeitsschnellansicht unterstützt u. a. das Analysieren der Leistung des C++ AMP-Codes. Diese Artikel beschreiben diese Funktionen:

- [GPU-Aktivitätsdiagramm](/visualstudio/profiling/gpu-activity-graph)

- [GPU-Aktivität (Paging)](/visualstudio/profiling/gpu-activity-paging)

- [GPU-Aktivität (dieser Prozess)](/visualstudio/profiling/gpu-activity-this-process)

- [GPU-Aktivität (andere Prozesse)](/visualstudio/profiling/gpu-activity-other-processes)

- [Kanäle (Thread Ansicht)](/visualstudio/profiling/channels-threads-view)

- [Analysieren von C++ amp-Code mit der neben läufigkeits Schnellansicht](/archive/blogs/nativeconcurrency/analyzing-c-amp-code-with-the-concurrency-visualizer)

## <a name="performance-recommendations"></a>Leistungsempfehlungen

Modulo und Division ganzer Zahlen ohne Vorzeichen weisen eine erheblich bessere Leistung als Modulo und Division ganzer Zahlen mit Vorzeichen auf. Es wird empfohlen, ganze Zahlen ohne Vorzeichen zu verwenden, sofern möglich.

## <a name="see-also"></a>Weitere Informationen

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Syntax von Lambda Ausdrücken](../../cpp/lambda-expression-syntax.md)<br/>
[Referenz (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[Parallele Programmierung in nativem Code (Blog)](https://go.microsoft.com/fwlink/p/?linkid=238472)

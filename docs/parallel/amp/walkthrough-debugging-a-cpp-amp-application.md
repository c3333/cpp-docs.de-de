---
title: 'Exemplarische Vorgehensweise: Debuggen einer C++ AMP-Anwendung'
ms.date: 04/23/2019
helpviewer_keywords:
- debugging, C++ Accelerated Massive Parallelism
- C++ AMP, debugging
- C++ Accelerated Massive Parallelism, debugging
- debugging, C++ AMP
ms.assetid: 40e92ecc-f6ba-411c-960c-b3047b854fb5
ms.openlocfilehash: 6eb93d617ac9909a67719b144a44ed461701225e
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404716"
---
# <a name="walkthrough-debugging-a-c-amp-application"></a>Exemplarische Vorgehensweise: Debuggen einer C++ AMP-Anwendung

In diesem Thema wird veranschaulicht, wie Sie eine Anwendung debuggen, die C++ Accelerated massive parallelism (C++ amp) verwendet, um die-GPU (Graphics Processing Unit) zu nutzen. Dabei wird ein paralleles Reduzierungs Programm verwendet, das eine große Anzahl von Ganzzahlen zusammenfasst. In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Der GPU-Debugger wird gestartet.

- Überprüfen von GPU-Threads im Fenster "GPU-Threads".

- Verwenden des Fensters **parallele Stapel** , um die Aufruf Listen mehrerer GPU-Threads gleichzeitig zu beobachten.

- Verwenden des Fensters **parallele Überwachung** zum Überprüfen der Werte eines einzelnen Ausdrucks über mehrere Threads gleichzeitig.

- Kennzeichnen, Einfrieren, reaktivieren und Gruppieren von GPU-Threads.

- Ausführen aller Threads einer Kachel an einem bestimmten Speicherort im Code.

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie mit dieser exemplarischen Vorgehensweise beginnen:

- Lesen Sie [C++ amp Übersicht](../../parallel/amp/cpp-amp-overview.md).

- Stellen Sie sicher, dass die Zeilennummern im Text-Editor angezeigt werden. Weitere Informationen finden Sie unter Gewusst [wie: Anzeigen von Zeilennummern im Editor](/visualstudio/ide/reference/how-to-display-line-numbers-in-the-editor).

- Stellen Sie sicher, dass Sie mindestens Windows 8 oder Windows Server 2012 ausführen, um das Debuggen im Software Emulator zu unterstützen.

[!INCLUDE[note_settings_general](../../mfc/includes/note_settings_general_md.md)]

### <a name="to-create-the-sample-project"></a>So erstellen Sie das Beispielprojekt

Die Anweisungen zum Erstellen eines Projekts variieren abhängig von der verwendeten Version von Visual Studio. Stellen Sie sicher, dass die richtige Version in der oberen linken Ecke dieser Seite ausgewählt ist.

::: moniker range="vs-2019"

### <a name="to-create-the-sample-project-in-visual-studio-2019"></a>So erstellen Sie das Beispiel Projekt in Visual Studio 2019

1. Klicken Sie in der Menüleiste auf **Datei** > **Neu** > **Projekt**, um das Dialogfeld **Neues Projekt erstellen** zu öffnen.

1. Legen Sie oben im Dialogfeld die **Sprache** auf **C++** , die **Plattform** auf **Windows** und den **Projekttyp** auf **Konsole** fest.

1. Wählen Sie aus der gefilterten Projekttypliste **Konsolen-App** aus, und klicken Sie auf **Weiter**. Geben Sie auf der nächsten Seite `AMPMapReduce` als Projektnamen in das Feld **Name** ein, und geben Sie den Projektspeicherort an, falls gewünscht.

   ![Benennen Sie das Projekt.](../../build/media/mathclient-project-name-2019.png "Benennen Sie das Projekt.")

1. Klicken Sie auf die Schaltfläche **Erstellen**, um das Clientprojekt zu erstellen.

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-the-sample-project-in-visual-studio-2017-or-visual-studio-2015"></a>So erstellen Sie das Beispiel Projekt in Visual Studio 2017 oder Visual Studio 2015

1. Starten Sie Visual Studio.

1. Wählen Sie in der Menüleiste **Datei** > **Neu** > **Projekt** aus.

1. Wählen Sie unter **installiert** im Bereich Vorlagen die Option **Visual C++** aus.

1. Wählen Sie **Win32-Konsolenanwendung**aus, geben Sie `AMPMapReduce` im Feld **Name** ein, und klicken Sie dann auf die Schaltfläche **OK** .

1. Klicken Sie auf **Weiter**.

1. Deaktivieren Sie das Kontrollkästchen **vorkompilierter Header** , und wählen Sie dann die Schaltfläche **Fertig** stellen aus.

1. Löschen Sie in **Projektmappen-Explorer**" *stdafx. h*", " *targetver. h*" und " *stdafx. cpp* " aus dem Projekt.

::: moniker-end

Nächste Schritte:

1. Öffnen Sie "ampmapreduce. cpp", und ersetzen Sie den Inhalt durch den folgenden Code.

```cpp
    // AMPMapReduce.cpp defines the entry point for the program.
    // The program performs a parallel-sum reduction that computes the sum of an array of integers.

    #include <stdio.h>
    #include <tchar.h>
    #include <amp.h>

    const int BLOCK_DIM = 32;

    using namespace concurrency;

    void sum_kernel_tiled(tiled_index<BLOCK_DIM> t_idx, array<int, 1> &A, int stride_size) restrict(amp)
    {
        tile_static int localA[BLOCK_DIM];

        index<1> globalIdx = t_idx.global * stride_size;
        index<1> localIdx = t_idx.local;

        localA[localIdx[0]] =  A[globalIdx];

        t_idx.barrier.wait();

        // Aggregate all elements in one tile into the first element.
        for (int i = BLOCK_DIM / 2; i > 0; i /= 2)
        {
            if (localIdx[0] < i)
            {

                localA[localIdx[0]] += localA[localIdx[0] + i];
            }

            t_idx.barrier.wait();
        }

        if (localIdx[0] == 0)
        {
            A[globalIdx] = localA[0];
        }
    }

    int size_after_padding(int n)
    {
        // The extent might have to be slightly bigger than num_stride to
        // be evenly divisible by BLOCK_DIM. You can do this by padding with zeros.
        // The calculation to do this is BLOCK_DIM * ceil(n / BLOCK_DIM)
        return ((n - 1) / BLOCK_DIM + 1) * BLOCK_DIM;
    }

    int reduction_sum_gpu_kernel(array<int, 1> input)
    {
        int len = input.extent[0];

        //Tree-based reduction control that uses the CPU.
        for (int stride_size = 1; stride_size < len; stride_size *= BLOCK_DIM)
        {
            // Number of useful values in the array, given the current
            // stride size.
            int num_strides = len / stride_size;

            extent<1> e(size_after_padding(num_strides));

            // The sum kernel that uses the GPU.
            parallel_for_each(extent<1>(e).tile<BLOCK_DIM>(), [&input, stride_size] (tiled_index<BLOCK_DIM> idx) restrict(amp)
            {
                sum_kernel_tiled(idx, input, stride_size);
            });
        }

        array_view<int, 1> output = input.section(extent<1>(1));
        return output[0];
    }

    int cpu_sum(const std::vector<int> &arr) {
        int sum = 0;
        for (size_t i = 0; i < arr.size(); i++) {
            sum += arr[i];
        }
        return sum;
    }

    std::vector<int> rand_vector(unsigned int size) {
        srand(2011);

        std::vector<int> vec(size);
        for (size_t i = 0; i < size; i++) {
            vec[i] = rand();
        }
        return vec;
    }

    array<int, 1> vector_to_array(const std::vector<int> &vec) {
        array<int, 1> arr(vec.size());
        copy(vec.begin(), vec.end(), arr);
        return arr;
    }

    int _tmain(int argc, _TCHAR* argv[])
    {
        std::vector<int> vec = rand_vector(10000);
        array<int, 1> arr = vector_to_array(vec);

        int expected = cpu_sum(vec);
        int actual = reduction_sum_gpu_kernel(arr);

        bool passed = (expected == actual);
        if (!passed) {
            printf("Actual (GPU): %d, Expected (CPU): %d", actual, expected);
        }
        printf("sum: %s\n", passed  "Passed!" : "Failed!");

        getchar();

        return 0;
    }
```

1. Klicken Sie in der Menüleiste auf **Datei**  >  **Alle speichern**.

1. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für **ampmapreduce**, und wählen Sie dann **Eigenschaften**aus.

1. Wählen Sie im Dialogfeld Eigenschaften **Seiten** unter **Konfigurations Eigenschaften**die Option **C/C++**  >  **Vorkompilierte Header**aus.

1. Wählen Sie für die Eigenschaft **Vorkompilierte Header** die Option **nicht vorkompilierte Header verwenden**aus, und klicken Sie dann auf die Schaltfläche **OK** .

1. Wählen Sie auf der Menüleiste **Erstellen** > **Projektmappe erstellen** aus.

## <a name="debugging-the-cpu-code"></a>Debuggen des CPU-Codes

In diesem Verfahren verwenden Sie den lokalen Windows-Debugger, um sicherzustellen, dass der CPU-Code in dieser Anwendung korrekt ist. Das Segment des CPU-Codes in dieser Anwendung, das besonders interessant ist, ist die `for` Schleife in der `reduction_sum_gpu_kernel` Funktion. Er steuert die Struktur basierte parallele Reduzierung, die auf der GPU ausgeführt wird.

### <a name="to-debug-the-cpu-code"></a>Zum Debuggen des CPU-Codes

1. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für **ampmapreduce**, und wählen Sie dann **Eigenschaften**aus.

2. Wählen Sie im Dialogfeld Eigenschaften **Seiten** unter **Konfigurations Eigenschaften**die Option **Debugging**aus. Vergewissern Sie sich, dass in der Liste **zu startender Debugger** der **lokale Windows-Debugger** ausgewählt ist.

3. Kehren Sie zum **Code-Editor**zurück.

4. Legen Sie in den Codezeilen, die in der folgenden Abbildung dargestellt werden, Breakpoints fest (ungefähr Zeilen 67 Zeile 70).

   ![CPU-Haltepunkte](../../parallel/amp/media/campcpubreakpoints.png "CPU-Haltepunkte") <br/>
   CPU-Haltepunkte

5. Klicken Sie in der Menüleiste **Debug**auf  >  **Debuggen Debuggen starten**.

6. Beobachten Sie **im Fenster Lokal den Wert** für, `stride_size` bis der Breakpoint in Zeile 70 erreicht ist.

7. Klicken Sie in der Menüleiste **Debug**auf  >  **Debuggen Debuggen**.

## <a name="debugging-the-gpu-code"></a>Debuggen des GPU-Codes

In diesem Abschnitt wird gezeigt, wie Sie den GPU-Code Debuggen, d. h. den in der Funktion enthaltenen Code `sum_kernel_tiled` . Der GPU-Code berechnet die Summe von ganzen Zahlen für jeden "Block" parallel.

### <a name="to-debug-the-gpu-code"></a>Zum Debuggen des GPU-Codes

1. Öffnen Sie in **Projektmappen-Explorer**das Kontextmenü für **ampmapreduce**, und wählen Sie dann **Eigenschaften**aus.

2. Wählen Sie im Dialogfeld Eigenschaften **Seiten** unter **Konfigurations Eigenschaften**die Option **Debugging**aus.

3. Wählen Sie in der Liste **Zu startender Debugger** die Option **Lokaler Windows-Debugger** aus.

4. Überprüfen Sie in der Liste **Debuggertyp** , ob **automatisch** ausgewählt ist.

    Der Standardwert ist **Auto** . Vor Windows 10 ist **GPU nur** der erforderliche Wert anstelle von " **Auto**".

5. Klicken Sie auf die Schaltfläche **OK** .

6. Legen Sie in Zeile 30 einen Haltepunkt fest, wie in der folgenden Abbildung dargestellt.

   ![GPU-Haltepunkte](../../parallel/amp/media/campgpubreakpoints.png "GPU-Haltepunkte") <br/>
   GPU-Haltepunkt

7. Klicken Sie in der Menüleiste **Debug**auf  >  **Debuggen Debuggen starten**. Die Breakpoints im CPU-Code in den Zeilen 67 und 70 werden während des GPU-Debuggens nicht ausgeführt, da diese Codezeilen auf der CPU ausgeführt werden.

### <a name="to-use-the-gpu-threads-window"></a>So verwenden Sie das Fenster "GPU-Threads"

1. Wählen Sie zum Öffnen des Fensters **GPU-Threads** in der Menüleiste die Option Windows-GPU-Threads **Debuggen**aus  >  **Windows**  >  **GPU Threads**.

   Sie können den Status der GPU-Threads im angezeigten Fenster **GPU-Threads** überprüfen.

2. Docken Sie das **GPU-Thread** Fenster am unteren Rand von Visual Studio an. Wählen Sie die Schaltfläche **Thread Umschaltung erweitern** aus, um die Kachel-und Thread Textfelder anzuzeigen. Im Fenster **GPU-Threads** wird die Gesamtzahl aktiver und blockierter GPU-Threads angezeigt, wie in der folgenden Abbildung dargestellt.

   ![GPU-Threadfenster mit vier aktiven Threads](../../parallel/amp/media/campc.png "GPU-Threadfenster mit vier aktiven Threads") <br/>
   GPU-Threadfenster

   Für diese Berechnung sind 313 Kacheln zugeordnet. Jede Kachel enthält 32 Threads. Da das lokale GPU-Debuggen in einem Software Emulator erfolgt, gibt es vier aktive GPU-Threads. Die vier Threads führen die Anweisungen gleichzeitig aus und fahren dann mit der nächsten Anweisung fort.

   Im Fenster " **GPU-Threads** " sind vier GPU-Threads aktiv, und 28 GPU-Threads werden bei der Anweisung " [tile_barrier:: Wait](reference/tile-barrier-class.md#wait) ", die in etwa Zeile 21 () definiert ist, blockiert `t_idx.barrier.wait();` . Alle 32-GPU-Threads gehören zur ersten Kachel,, `tile[0]` . Ein Pfeil zeigt auf die Zeile, die den aktuellen Thread enthält. Verwenden Sie eine der folgenden Methoden, um zu einem anderen Thread zu wechseln:

    - Öffnen Sie in der Zeile, zu der der Thread im Fenster **GPU-Threads** wechseln soll, das Kontextmenü, und wählen Sie **zu Thread wechseln**. Wenn die Zeile mehr als einen Thread darstellt, wechseln Sie entsprechend den Thread Koordinaten zum ersten Thread.

    - Geben Sie die Kachel-und Thread Werte des Threads in die entsprechenden Textfelder ein, und wählen Sie dann die Schaltfläche **Thread wechseln** aus.

   Das Fenster " **aufrufsstapel** " zeigt die Aufrufe des aktuellen GPU-Threads an.

### <a name="to-use-the-parallel-stacks-window"></a>So verwenden Sie das Fenster "parallele Stapel"

1. Um das Fenster **parallele Stapel** zu öffnen, wählen Sie in der Menüleiste **Debug**  >  **Windows**  >  **Parallel Stacks**Debuggen aus.

   Sie können das Fenster **parallele Stapel** verwenden, um die Stapel Rahmen mehrerer GPU-Threads gleichzeitig zu überprüfen.

2. Docken Sie das **parallele Stapel** Fenster am unteren Rand von Visual Studio an.

3. Stellen Sie sicher, dass in der Liste in der oberen linken Ecke **Threads** ausgewählt ist. In der folgenden Abbildung zeigt das Fenster **parallele Stapel** eine Aufruf Stapel zentrierte Ansicht der GPU-Threads an, die Sie im Fenster **GPU-Threads** gesehen haben.

   ![Fenster für parallele Stapel mit vier aktiven Threads](../../parallel/amp/media/campd.png "Fenster für parallele Stapel mit vier aktiven Threads") <br/>
   Fenster für parallele Stapel

   32 Threads wurden von `_kernel_stub` zur Lambda-Anweisung im `parallel_for_each` Funktions-und dann zur- `sum_kernel_tiled` Funktion gewechselt, bei der die parallele Reduzierung erfolgt. 28 aus den 32 Threads haben sich zur [tile_barrier:: Wait](reference/tile-barrier-class.md#wait) -Anweisung entwickelt und bleiben in Zeile 22 blockiert, während die anderen 4 Threads in der Funktion in `sum_kernel_tiled` Zeile 30 aktiv bleiben.

   Sie können die Eigenschaften eines GPU-Threads überprüfen, die im Fenster " **GPU-Threads** " in der Rich DataTip des Fensters " **parallele Stapel** " verfügbar sind. Um dies zu erreichen, bewegen Sie den Mauszeiger auf den Stapel Rahmen **sum_kernel_tiled**. Die folgende Abbildung zeigt DataTip.

   ![DataTip für Fenster für parallele Stapel](../../parallel/amp/media/campe.png "DataTip für Fenster für parallele Stapel") <br/>
   GPU-Thread DataTip

   Weitere Informationen zum Fenster **parallele Stapel** finden [Sie unter Verwenden des Fensters "parallele Stapel](/visualstudio/debugger/using-the-parallel-stacks-window)".

### <a name="to-use-the-parallel-watch-window"></a>So verwenden Sie die parallele Überwachungsfenster

1. Um das Fenster **parallele Überwachung** zu öffnen, wählen Sie in der Menüleiste **Debuggen**  >  **Windows**  >  **parallel**Watch  >  **parallel Watch 1**aus.

   Sie können das Fenster **parallele Überwachung** verwenden, um die Werte eines Ausdrucks über mehrere Threads hinweg zu untersuchen.

2. Docken Sie das parallele Fenster "über **Wachen 1** " am unteren Rand von Visual Studio an. In der Tabelle des Fensters " **parallele Überwachung** " sind 32 Zeilen vorhanden. Jeder entspricht einem GPU-Thread, der sowohl im Fenster GPU-Threads als auch im Fenster **parallele Stapel** angezeigt wird. Nun können Sie Ausdrücke eingeben, deren Werte Sie über alle 32 GPU-Threads hinweg überprüfen möchten.

3. Wählen Sie die Kopfzeile **Überwachungs Spalte hinzufügen** aus, geben Sie ein `localIdx` , und drücken Sie dann die **Eingabe** Taste.

4. Klicken Sie erneut auf den Spaltenheader " **Überwachung hinzufügen** ", geben Sie ein `globalIdx` , und **drücken** Sie die EINGABETASTE.

5. Klicken Sie erneut auf den Spaltenheader " **Überwachung hinzufügen** ", geben Sie ein `localA[localIdx[0]]` , und **drücken** Sie die EINGABETASTE.

   Sie können nach einem angegebenen Ausdruck sortieren, indem Sie die entsprechende Spaltenüberschrift auswählen.

   Wählen Sie den Spaltenheader **Locala [localidx [0]]** aus, um die Spalte zu sortieren. Die folgende Abbildung zeigt die Ergebnisse der Sortierung nach **Locala [localidx [0]]**.

   ![Fenster für parallele Stapel mit sortierten Ergebnissen](../../parallel/amp/media/campf.png "Fenster für parallele Stapel mit sortierten Ergebnissen") <br/>
   Sortierergebnisse

   Sie können den Inhalt im Fenster **parallele Überwachung** in Excel exportieren, indem Sie auf die Schaltfläche **Excel** und dann **auf in Excel öffnen**klicken. Wenn Sie Excel auf dem Entwicklungs Computer installiert haben, wird ein Excel-Arbeitsblatt geöffnet, das den Inhalt enthält.

6. In der oberen rechten Ecke des Fensters **parallele Überwachung** gibt es ein Filter Steuerelement, das Sie verwenden können, um den Inhalt mithilfe von booleschen Ausdrücken zu filtern. Geben Sie `localA[localIdx[0]] > 20000` im Textfeld Filter Steuerelement ein, und drücken Sie dann die **Eingabe** Taste.

   Das Fenster enthält jetzt nur Threads, bei denen der `localA[localIdx[0]]` Wert größer als 20000 ist. Der Inhalt ist nach wie vor nach der `localA[localIdx[0]]` Spalte sortiert. Dies ist die Sortier Aktion, die Sie zuvor ausgeführt haben.

## <a name="flagging-gpu-threads"></a>Kennzeichnen von GPU-Threads

Sie können bestimmte GPU-Threads markieren, indem Sie Sie im Fenster " **GPU-Threads** ", im Fenster " **parallele Überwachung** " oder im Fenster " **parallele Stapel** " kennzeichnen. Wenn eine Zeile im Fenster GPU-Threads mehr als einen Thread enthält, werden durch das Kennzeichnen dieser Zeile alle in der Zeile enthaltenen Threads gekennzeichnet.

### <a name="to-flag-gpu-threads"></a>So markieren Sie GPU-Threads

1. Wählen Sie im Fenster **parallele Überwachung 1** die Spaltenüberschrift **[Thread]** aus, um nach Kachel Index und Thread Index zu sortieren.

2. Wählen Sie in der Menüleiste die Option **Debuggen**  >  **fortsetzen**aus. Dadurch werden die vier aktiven Threads in der nächsten Barriere (definiert in Zeile 32 von ampmapreduce. cpp) fortgesetzt.

3. Wählen Sie auf der linken Seite der Zeile das Flag-Symbol aus, das die vier zurzeit aktiven Threads enthält.

   Die folgende Abbildung zeigt die vier aktiven markierten Threads im Fenster **GPU-Threads** .

   ![GPU-Threadfenster mit gekennzeichneten Threads](../../parallel/amp/media/campg.png "GPU-Threadfenster mit gekennzeichneten Threads") <br/>
   Aktive Threads im GPU-Threadfenster

   Sowohl das Fenster **parallele Überwachung** als auch das DataTip des Fensters **parallele Stapel** geben die gekennzeichneten Threads an.

4. Wenn Sie sich auf die vier Threads konzentrieren möchten, die Sie gekennzeichnet haben, können Sie auswählen, dass in den Fenstern **GPU-Threads**, **parallele Überwachung**und **parallele Stapel** nur die markierten Threads angezeigt werden.

   Wählen Sie in einem der Fenster oder auf der Symbolleiste **Debugspeicherort** die Schaltfläche nur gekennzeichnete **anzeigen** aus. In der folgenden Abbildung wird die Schaltfläche nur gekennzeichnete anzeigen auf der Symbolleiste **Debugspeicherort** **angezeigt** .

   ![Symbolleiste „Debugspeicherort“ mit Symbol für „Nur gekennzeichnete anzeigen“](../../parallel/amp/media/camph.png "Symbolleiste „Debugspeicherort“ mit Symbol für „Nur gekennzeichnete anzeigen“") <br/>
   Schaltfläche "nur gekennzeichnete **anzeigen** "

   Nun zeigen die Fenster **GPU-Threads**, **parallele Überwachung**und **parallele Stapel** nur die markierten Threads an.

## <a name="freezing-and-thawing-gpu-threads"></a>Einfrieren und Reaktivieren von GPU-Threads

Sie können GPU-Threads entweder über das **GPU-Thread** Fenster oder das **parallele Überwachungs** Fenster Einfrieren (aussetzen) und (fortsetzen). Sie können CPU-Threads auf die gleiche Weise Einfrieren und durchlaufen. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden des Fensters "Threads](/visualstudio/debugger/how-to-use-the-threads-window)".

### <a name="to-freeze-and-thaw-gpu-threads"></a>So fixieren Sie GPU-Threads und aktivieren diese

1. Wählen Sie die Schaltfläche **nur** gekennzeichnete anzeigen aus, um alle Threads anzuzeigen.

2. Klicken Sie in der Menüleiste auf **Debuggen**  >  **fortsetzen**.

3. Öffnen Sie das Kontextmenü für die aktive Zeile, und wählen Sie dann **Einfrieren**aus.

   Die folgende Abbildung des Fensters **GPU-Threads** zeigt, dass alle vier Threads eingefroren sind.

   ![GPU-Threadfenster mit fixierten Threads](../../parallel/amp/media/campk.png "GPU-Threadfenster mit fixierten Threads") <br/>
   Fixierte Threads im Fenster " **GPU-Threads** "

   Ebenso zeigt das Fenster **parallele Überwachung** , dass alle vier Threads eingefroren sind.

4. Wählen Sie in der Menüleiste die Option **Debuggen**  >  **fortsetzen** aus, um zuzulassen, dass die nächsten vier GPU-Threads in Zeile 22 über der Grenze fortfahren und den Breakpoint in Zeile 30 erreichen. Das Fenster " **GPU-Threads** " zeigt an, dass die vier zuvor fixierten Threads fixiert bleiben und sich im aktiven Zustand befinden.

5. Wählen Sie in der Menüleiste **Debuggen**, **weiter**aus.

6. Im Fenster **parallele Überwachung** können Sie auch einzelne oder mehrere GPU-Threads überwachen.

### <a name="to-group-gpu-threads"></a>So gruppieren Sie GPU-Threads

1. Wählen Sie im Kontextmenü für einen der Threads im Fenster **GPU-Threads** die Option **Gruppieren nach**, **Adresse**aus.

   Die Threads im Fenster **GPU-Threads** sind nach Adresse gruppiert. Die Adresse entspricht der Anweisung in Disassembly, in der sich die jeweilige Thread Gruppe befindet. 24 Threads befinden sich in Zeile 22, in der die [tile_barrier:: Wait-Methode](reference/tile-barrier-class.md#wait) ausgeführt wird. 12 Threads befinden sich in der Anweisung für die Barriere in Zeile 32. Vier dieser Threads werden gekennzeichnet. Acht Threads befinden sich am Haltepunkt in Zeile 30. Vier dieser Threads sind fixiert. Die folgende Abbildung zeigt die gruppierten Threads im Fenster **GPU-Threads** .

   ![GPU-Threadfenster mit nach Adresse angeordneten Threads](../../parallel/amp/media/campl.png "GPU-Threadfenster mit nach Adresse angeordneten Threads") <br/>
   Gruppierte Threads im Fenster " **GPU-Threads** "

2. Sie können den Vorgang **Gruppieren nach** auch durchführen, indem Sie das Kontextmenü für das Datenraster im Fenster **parallele Überwachung** öffnen, **Gruppieren nach**auswählen und dann das Menü Element auswählen, das der Gruppierung der Threads entspricht.

## <a name="running-all-threads-to-a-specific-location-in-code"></a>Ausführen aller Threads an einem bestimmten Speicherort im Code

Sie führen alle Threads in einer gegebenen Kachel in der Zeile aus, die den Cursor enthält, indem Sie die **aktuelle Kachel zum Cursor ausführen**verwenden.

### <a name="to-run-all-threads-to-the-location-marked-by-the-cursor"></a>So führen Sie alle Threads an dem durch den Cursor markierten Speicherort aus

1. Wählen Sie im Kontextmenü für die fixierten Threads die Option **Thaw**aus.

2. Platzieren Sie den Cursor im **Code-Editor**in Zeile 30.

3. Wählen Sie im Kontextmenü für den **Code-Editor**die Option **aktuelle Kachel bis Cursor ausführen**aus.

   Die 24 Threads, die zuvor an der Barriere in Zeile 21 blockiert waren, wurden in Zeile 32 weiterentwickelt. Dies wird im Fenster **GPU-Threads** angezeigt.

## <a name="see-also"></a>Weitere Informationen

[Übersicht über C++ amp](../../parallel/amp/cpp-amp-overview.md)<br/>
[Debuggen von GPU-Code](/visualstudio/debugger/debugging-gpu-code)<br/>
[How to: Verwenden des Fensters „GPU-Threads“](/visualstudio/debugger/how-to-use-the-gpu-threads-window)<br/>
[How to: Verwenden des Fensters „Parallele Überwachung“](/visualstudio/debugger/how-to-use-the-parallel-watch-window)<br/>
[Analysieren von C++ amp-Code mit der neben läufigkeits Schnellansicht](/archive/blogs/nativeconcurrency/analyzing-c-amp-code-with-the-concurrency-visualizer)

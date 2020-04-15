---
title: 'Exemplarische Vorgehensweise: Entfernen von Arbeit aus einem Benutzeroberflächenthread'
ms.date: 08/19/2019
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 52bc98ef339a19c6ec2a53697f532a9a94b6c9a6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377446"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>Exemplarische Vorgehensweise: Entfernen von Arbeit aus einem Benutzeroberflächenthread

In diesem Dokument wird veranschaulicht, wie die Concurrency Runtime verwendet wird, um die Arbeit, die vom Benutzeroberflächenthread (UI) in einer MFC-Anwendung (Microsoft Foundation Classes) ausgeführt wird, in einen Arbeitsthread zu verschieben. In diesem Dokument wird auch veranschaulicht, wie Die Leistung eines langwierigen Zeichnungsvorgangs verbessert werden kann.

Das Entfernen von Arbeit aus dem UI-Thread durch Auslagern von Blockierungsvorgängen, z. B. Zeichnen, in Arbeitsthreads kann die Reaktionsfähigkeit Ihrer Anwendung verbessern. In dieser exemplarischen Vorgehensweise wird eine Zeichnungsroutine verwendet, die das Mandelbrot-Fraktal generiert, um einen langwierigen Blockierungsvorgang zu demonstrieren. Die Generierung des Mandelbrot-Fraktoals ist auch ein guter Kandidat für die Parallelisierung, da die Berechnung jedes Pixels unabhängig von allen anderen Berechnungen ist.

## <a name="prerequisites"></a>Voraussetzungen

Lesen Sie sich folgende Themen durch, bevor Sie mit dieser exemplarischen Vorgehensweise beginnen:

- [Aufgabe Parallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [Asynchrone Nachrichtenblöcke](../../parallel/concrt/asynchronous-message-blocks.md)

- [Message Passing-Funktionen](../../parallel/concrt/message-passing-functions.md)

- [Parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md)

- [Abbruch in der PPL](cancellation-in-the-ppl.md)

Es wird außerdem empfohlen, die Grundlagen der MFC-Anwendungsentwicklung und GDI+ zu verstehen, bevor Sie mit dieser exemplarischen Vorgehensweise beginnen. Weitere Informationen zu MFC finden Sie unter [MFC Desktop Applications](../../mfc/mfc-desktop-applications.md). Weitere Informationen zu GDI+ finden Sie unter [GDI+](/windows/win32/gdiplus/-gdiplus-gdi-start).

## <a name="sections"></a><a name="top"></a>Bereichen

Diese exemplarische Vorgehensweise enthält folgende Abschnitte:

- [Erstellen der MFC-Anwendung](#application)

- [Implementieren der seriellen Version der Mandelbrot-Anwendung](#serial)

- [Entfernen von Arbeit aus dem Benutzeroberflächenthread](#removing-work)

- [Verbesserung der Zeichnungsleistung](#performance)

- [Hinzufügen von Support für Dies nach dem Absagen](#cancellation)

## <a name="creating-the-mfc-application"></a><a name="application"></a>Erstellen der MFC-Anwendung

In diesem Abschnitt wird beschrieben, wie Sie die grundlegende MFC-Anwendung erstellen.

### <a name="to-create-a-visual-c-mfc-application"></a>So erstellen Sie eine Visual C++ MFC-Anwendung

1. Verwenden Sie den **MFC-Anwendungs-Assistenten,** um eine MFC-Anwendung mit allen Standardeinstellungen zu erstellen. Weitere Informationen zum Öffnen des Assistenten für Ihre Version von Visual Studio finden Sie in [der exemplarischen Vorgehensweise: Verwenden der neuen MFC-Shell-Steuerelemente.](../../mfc/walkthrough-using-the-new-mfc-shell-controls.md)

1. Geben Sie einen Namen für `Mandelbrot`das Projekt ein, z. B. , und klicken Sie dann auf **OK,** um den **MFC-Anwendungs-Assistenten**anzuzeigen.

1. Wählen Sie im Bereich **Anwendungstyp** die Option **Einzeldokument**aus. Stellen Sie sicher, dass das Kontrollkästchen **Dokument-/Ansichtsarchitekturunterstützung** deaktiviert ist.

1. Klicken Sie auf **Fertig stellen,** um das Projekt zu erstellen und den **MFC-Anwendungs-Assistenten zu**schließen.

   Überprüfen Sie, ob die Anwendung erfolgreich erstellt wurde, indem Sie sie erstellen und ausführen. Um die Anwendung zu erstellen, klicken Sie im Menü **Build** auf **Lösung erstellen**. Wenn die Anwendung erfolgreich erstellt wird, führen Sie die Anwendung aus, indem Sie **im** Menü Debuggen starten im **Menü Debuggen** klicken.

## <a name="implementing-the-serial-version-of-the-mandelbrot-application"></a><a name="serial"></a>Implementieren der seriellen Version der Mandelbrot-Anwendung

In diesem Abschnitt wird beschrieben, wie das Mandelbrot-Fraktal gezeichnet wird. Diese Version zeichnet das Mandelbrot-Fraktal in ein [GDI+-Bitmap-Objekt](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap) und kopiert dann den Inhalt dieser Bitmap in das Clientfenster.

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>So implementieren Sie die serielle Version der Mandelbrot-Anwendung

1. Fügen Sie in *pch.h* (*stdafx.h* in Visual Studio `#include` 2017 und früher) die folgende Direktive hinzu:

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. Definieren Sie in ChildView.h nach der `pragma` Direktive den `BitmapPtr` Typ. Der `BitmapPtr` Typ ermöglicht es, `Bitmap` einen Zeiger auf ein Objekt von mehreren Komponenten gemeinsam zu verwenden. Das `Bitmap` Objekt wird gelöscht, wenn es von keiner Komponente mehr referenziert wird.

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. Fügen Sie in ChildView.h den `protected` folgenden `CChildView` Code zum Abschnitt der Klasse hinzu:

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. Kommentieren oder entfernen Sie in ChildView.cpp die folgenden Zeilen.

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   In Debugbuilds verhindert dieser Schritt, `DEBUG_NEW` dass die Anwendung den Zuweisungsdienst verwendet, der mit GDI+ nicht kompatibel ist.

1. Fügen Sie in `using` `Gdiplus` ChildView.cpp dem Namespace eine Direktive hinzu.

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. Fügen Sie dem Konstruktor und Destruktor der `CChildView` Klasse den folgenden Code hinzu, um GDI+ zu initialisieren und herunterzufahren.

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. Implementieren Sie die `CChildView::DrawMandelbrot`-Methode. Diese Methode zeichnet das Mandelbrot-Fraktal auf das angegebene `Bitmap` Objekt.

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. Implementieren Sie die `CChildView::OnPaint`-Methode. Diese Methode `CChildView::DrawMandelbrot` ruft den Inhalt `Bitmap` des Objekts auf und kopiert ihn dann in das Fenster.

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. Stellen Sie sicher, dass die Anwendung erfolgreich aktualisiert wurde, indem Sie sie erstellen und ausführen.

Die folgende Abbildung zeigt die Ergebnisse der Mandelbrot-Anwendung.

![Mandelbrot-Anwendung](../../parallel/concrt/media/mandelbrot.png "Mandelbrot-Anwendung")

Da die Berechnung für jedes Pixel rechnerisch teuer ist, kann der UI-Thread keine zusätzlichen Nachrichten verarbeiten, bis die Gesamtberechnung abgeschlossen ist. Dies kann die Reaktionsfähigkeit in der Anwendung verringern. Sie können dieses Problem jedoch beheben, indem Sie Arbeit aus dem UI-Thread entfernen.

[[Oben](#top)]

## <a name="removing-work-from-the-ui-thread"></a><a name="removing-work"></a>Entfernen von Arbeit aus dem UI-Thread

In diesem Abschnitt wird gezeigt, wie Sie die Zeichnungsarbeit aus dem UI-Thread in der Mandelbrot-Anwendung entfernen. Durch Verschieben von Zeichnungsarbeiten aus dem UI-Thread in einen Arbeitsthread kann der UI-Thread Nachrichten verarbeiten, während der Arbeitsthread das Bild im Hintergrund generiert.

Die Parallelitätslaufzeit bietet drei Möglichkeiten zum Ausführen von Aufgaben: [Taskgruppen](../../parallel/concrt/task-parallelism-concurrency-runtime.md), [asynchrone Agenten](../../parallel/concrt/asynchronous-agents.md)und [einfache Aufgaben](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Obwohl Sie einen dieser Mechanismen verwenden können, um Arbeit aus dem UI-Thread zu entfernen, verwendet dieses Beispiel ein [concurrency::task_group-Objekt,](reference/task-group-class.md) da Aufgabengruppen den Abbruch unterstützen. In dieser exemplarischen Vorgehensweise wird später der Abbruch verwendet, um die Menge an Arbeit zu reduzieren, die ausgeführt wird, wenn die Größe des Clientfensters geändert wird, und um eine Bereinigung durchzuführen, wenn das Fenster zerstört wird.

In diesem Beispiel wird auch ein [concurrency::unbounded_buffer-Objekt](reference/unbounded-buffer-class.md) verwendet, um die Kommunikation zwischen dem UI-Thread und dem Arbeitsthread zu ermöglichen. Nachdem der Arbeitsthread das Bild erstellt hat, `Bitmap` sendet `unbounded_buffer` er einen Zeiger auf das Objekt an das Objekt und sendet dann eine Paint-Nachricht an den UI-Thread. Der UI-Thread empfängt `unbounded_buffer` dann `Bitmap` vom Objekt das Objekt und zeichnet es in das Clientfenster.

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>So entfernen Sie die Zeichnungsarbeit aus dem UI-Thread

1. Fügen Sie in *pch.h* (*stdafx.h* in Visual Studio `#include` 2017 und früher) die folgenden Direktiven hinzu:

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. Fügen Sie in ChildView.h `task_group` dem `unbounded_buffer` `protected` Abschnitt `CChildView` der Klasse und Membervariablen hinzu. Das `task_group` Objekt enthält die Aufgaben, die das Zeichnen ausführen. Das `unbounded_buffer` Objekt enthält das fertige Mandelbrot-Bild.

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. Fügen Sie in `using` `concurrency` ChildView.cpp dem Namespace eine Direktive hinzu.

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. In `CChildView::DrawMandelbrot` der Methode ruft `Bitmap::UnlockBits`nach dem Aufruf von die [concurrency::send-Funktion](reference/concurrency-namespace-functions.md#send) auf, um das `Bitmap` Objekt an den UI-Thread zu übergeben. Anschließend eine Paint-Nachricht an den UI-Thread senden und den Clientbereich ungültig machen.

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. Aktualisieren `CChildView::OnPaint` Sie die Methode, um das aktualisierte `Bitmap` Objekt zu empfangen, und zeichnen Sie das Bild in das Clientfenster.

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   Die `CChildView::OnPaint` Methode erstellt eine Aufgabe zum Generieren des Mandelbrot-Abbilds, wenn kein S-Platz im Nachrichtenpuffer vorhanden ist. Der Nachrichtenpuffer enthält `Bitmap` kein Objekt in Fällen wie der ursprünglichen Paint-Nachricht und wenn ein anderes Fenster vor das Clientfenster verschoben wird.

1. Stellen Sie sicher, dass die Anwendung erfolgreich aktualisiert wurde, indem Sie sie erstellen und ausführen.

Die Benutzeroberfläche reagiert jetzt reaktionsschneller, da die Zeichnungsarbeit im Hintergrund ausgeführt wird.

[[Oben](#top)]

## <a name="improving-drawing-performance"></a><a name="performance"></a>Verbesserung der Zeichnungsleistung

Die Generierung des Mandelbrot-Fraktoals ist ein guter Kandidat für die Parallelisierung, da die Berechnung jedes Pixels unabhängig von allen anderen Berechnungen ist. Um die Zeichnungsprozedur zu `for` parallelisieren, `CChildView::DrawMandelbrot` konvertieren Sie die äußere Schleife in der Methode wie folgt in einen Aufruf des [concurrency::parallel_for-Algorithmus.](reference/concurrency-namespace-functions.md#parallel_for)

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

Da die Berechnung jedes Bitmapelements unabhängig ist, müssen Sie die Zeichnungsvorgänge, die auf den Bitmapspeicher zugreifen, nicht synchronisieren. Dadurch kann die Leistung skaliert werden, wenn die Anzahl der verfügbaren Prozessoren zunimmt.

[[Oben](#top)]

## <a name="adding-support-for-cancellation"></a><a name="cancellation"></a>Hinzufügen von Support für Dies nach dem Absagen

In diesem Abschnitt wird beschrieben, wie die Größe des Fensters behandelt wird und wie aktive Zeichnungsaufgaben abgebrochen werden, wenn das Fenster zerstört wird.

Das Dokument [Cancellation in der PPL](cancellation-in-the-ppl.md) erklärt, wie der Abbruch in der Laufzeit funktioniert. Die Kündigung ist kooperativ; daher tritt es nicht sofort auf. Um eine abgebrochene Aufgabe zu beenden, löst die Laufzeit während eines nachfolgenden Aufrufs von der Aufgabe in die Laufzeit eine interne Ausnahme aus. Im vorherigen Abschnitt wird `parallel_for` gezeigt, wie der Algorithmus verwendet wird, um die Leistung der Zeichnungsaufgabe zu verbessern. Der Aufruf `parallel_for` von ermöglicht der Laufzeit, die Aufgabe zu beenden, und ermöglicht daher das Abbrechen.

### <a name="cancelling-active-tasks"></a>Abbrechen aktiver Aufgaben

Die Mandelbrot-Anwendung erstellt `Bitmap` Objekte, deren Dimensionen der Größe des Clientfensters entsprechen. Jedes Mal, wenn die Größe des Clientfensters geändert wird, erstellt die Anwendung eine zusätzliche Hintergrundaufgabe, um ein Bild für die neue Fenstergröße zu generieren. Die Anwendung erfordert diese Zwischenbilder nicht; Es wird nur das Bild für die endgültige Fenstergröße benötigt. Um zu verhindern, dass die Anwendung diese zusätzliche Arbeit ausführt, können `WM_SIZE` `WM_SIZING` Sie alle aktiven Zeichnungsaufgaben in den Nachrichtenhandlern für die und Nachrichten abbrechen und dann die Zeichnungsarbeit neu planen, nachdem die Größe des Fensters geändert wurde.

Um aktive Zeichnungsaufgaben abzubrechen, wenn die Größe des Fensters geändert wird, ruft die `WM_SIZING` `WM_SIZE` Anwendung die [parallel::task_group::cancel-Methode](reference/task-group-class.md#cancel) in den Handlern für die und Nachrichten auf. Der Handler `WM_SIZE` für die Nachricht ruft auch die [parallelität::task_group::wait-Methode](reference/task-group-class.md#wait) auf, um zu warten, bis alle aktiven Aufgaben abgeschlossen sind, und plant dann die Zeichnungsaufgabe für die aktualisierte Fenstergröße neu.

Wenn das Clientfenster zerstört wird, ist es sinnvoll, alle aktiven Zeichnungsaufgaben abzubrechen. Durch das Abbrechen aktiver Zeichnungsaufgaben wird sichergestellt, dass Arbeitsthreads keine Nachrichten an den UI-Thread senden, nachdem das Clientfenster zerstört wurde. Die Anwendung bricht alle aktiven Zeichnungsaufgaben `WM_DESTROY` im Handler für die Nachricht ab.

### <a name="responding-to-cancellation"></a>Reagieren auf Stornierung

Die `CChildView::DrawMandelbrot` Methode, die die Zeichnungsaufgabe ausführt, muss auf Abbruch reagieren. Da die Laufzeit die Ausnahmebehandlung verwendet, um Aufgaben abzubrechen, muss die `CChildView::DrawMandelbrot` Methode einen ausnahmesicheren Mechanismus verwenden, um sicherzustellen, dass alle Ressourcen ordnungsgemäß bereinigt werden. In diesem Beispiel wird das *RAII-Muster (Resource Acquisition Is Initialization)* verwendet, um sicherzustellen, dass die Bitmapbits entsperrt werden, wenn der Vorgang abgebrochen wird.

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>So fügen Sie Unterstützung für die Löschung in der Mandelbrot-Anwendung hinzu

1. Fügen `protected` Sie in ChildView.h `CChildView` im Abschnitt der Klasse `OnSize` `OnSizing`Deklarationen für die Funktionen , und `OnDestroy` message map hinzu.

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. Ändern Sie in ChildView.cpp die Nachrichtenzuordnung `WM_SIZE`so, dass sie Handler für die , `WM_SIZING`und `WM_DESTROY` Nachrichten enthält.

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. Implementieren Sie die `CChildView::OnSizing`-Methode. Diese Methode bricht alle vorhandenen Zeichnungsaufgaben ab.

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. Implementieren Sie die `CChildView::OnSize`-Methode. Diese Methode bricht alle vorhandenen Zeichnungsaufgaben ab und erstellt eine neue Zeichnungsaufgabe für die aktualisierte Clientfenstergröße.

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. Implementieren Sie die `CChildView::OnDestroy`-Methode. Diese Methode bricht alle vorhandenen Zeichnungsaufgaben ab.

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. Definieren Sie in ChildView.cpp die `scope_guard` Klasse, die das RAII-Muster implementiert.

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. Fügen Sie der `CChildView::DrawMandelbrot` Methode nach dem `Bitmap::LockBits`Aufruf folgenden Codes hinzu:

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   Dieser Code verarbeitet den `scope_guard` Abbruch, indem er ein Objekt erstellt. Wenn das Objekt den Bereich verlässt, werden die Bitmapbits entsperrt.

1. Ändern Sie das `CChildView::DrawMandelbrot` Ende der `scope_guard` Methode, um das Objekt zu beenden, nachdem die Bitmapbits entsperrt wurden, aber bevor Nachrichten an den UI-Thread gesendet werden. Dadurch wird sichergestellt, dass der UI-Thread nicht aktualisiert wird, bevor die Bitmapbits entsperrt werden.

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

1. Stellen Sie sicher, dass die Anwendung erfolgreich aktualisiert wurde, indem Sie sie erstellen und ausführen.

Wenn Sie die Größe des Fensters ändern, wird die Zeichnungsarbeit nur für die endgültige Fenstergröße ausgeführt. Alle aktiven Zeichnungsaufgaben werden auch abgebrochen, wenn das Fenster zerstört wird.

[[Oben](#top)]

## <a name="see-also"></a>Siehe auch

[Parallelitätslaufzeit-Walkthroughs](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Aufgabe Parallelität](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[Asynchrone Nachrichtenblöcke](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Message Passing-Funktionen](../../parallel/concrt/message-passing-functions.md)<br/>
[Parallele Algorithmen](../../parallel/concrt/parallel-algorithms.md)<br/>
[Abbruch in der PPL](cancellation-in-the-ppl.md)<br/>
[MFC-Desktopanwendungen](../../mfc/mfc-desktop-applications.md)

---
title: Erstellen von asynchronen Vorgängen in C++ für UWP-apps
ms.date: 11/19/2018
helpviewer_keywords:
- Windows 8.x apps, creating C++ async operations
- Creating C++ async operations
ms.assetid: a57cecf4-394a-4391-a957-1d52ed2e5494
ms.openlocfilehash: a12900f3145f0dde797fe56c893442e1632cc01c
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404511"
---
# <a name="creating-asynchronous-operations-in-c-for-uwp-apps"></a>Erstellen von asynchronen Vorgängen in C++ für UWP-apps

In diesem Dokument werden einige der wichtigsten Punkte beschrieben, die Sie beachten sollten, wenn Sie mit der Task-Klasse Windows-Thread Pool-basierte asynchrone Vorgänge in einer UWP-app (Universal Windows-Runtime) entwickeln.

Die Verwendung der asynchronen Programmierung ist eine Schlüsselkomponente im Windows-Runtime App-Modell, da apps auf diese Weise auf Benutzereingaben reaktionsfähig bleiben. Sie können eine lang dauernde Aufgabe starten, ohne den Benutzeroberflächenthread zu blockieren, und die Ergebnisse der Aufgabe später empfangen. Sie können Aufgaben auch abbrechen und Statusbenachrichtigungen beim Ausführen von Aufgaben im Hintergrund erhalten. Das Dokument [asynchrone Programmierung in C++](/windows/uwp/threading-async/asynchronous-programming-in-cpp-universal-windows-platform-apps) bietet eine Übersicht über das asynchrone Muster, das in Visual C++ zum Erstellen von UWP-apps verfügbar ist. In diesem Dokument erfahren Sie, wie Sie Ketten von asynchronen Windows-Runtime Vorgängen nutzen und erstellen können. In diesem Abschnitt wird beschrieben, wie Sie die Typen in "ppltasks. h" verwenden, um asynchrone Vorgänge zu generieren, die von einer anderen Windows-Runtime Komponente genutzt werden können, und wie Sie steuern, wie asynchrone Arbeit ausgeführt wird. Lesen Sie auch die Muster und Tipps für die asynchrone [Programmierung in Hilo (Windows Store-Apps mit C++ und XAML)](/previous-versions/windows/apps/jj160321(v=win.10)) , um zu erfahren, wie wir mit der Task-Klasse asynchrone Vorgänge in Hilo implementiert haben, einer Windows-Runtime-APP, die C++ und XAML verwendet.

> [!NOTE]
> Sie können die [Parallel Patterns Library](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL) und die [Asynchronous Agents Library](../../parallel/concrt/asynchronous-agents-library.md) in einer UWP-App verwenden. Aufgabenplaner oder Ressourcen-Manager können jedoch nicht verwendet werden. In diesem Dokument werden zusätzliche von der ppl bereitgestellte Funktionen beschrieben, die nur für eine UWP-APP und nicht für eine Desktop-App verfügbar sind.

## <a name="key-points"></a>Wesentliche Punkte

- Erstellen Sie mithilfe von [concurrency::create_async](reference/concurrency-namespace-functions.md#create_async) asynchrone Vorgänge, die von anderen Komponenten genutzt werden können (die möglicherweise in einer anderen Sprache als C++ geschrieben sind).

- Verwenden Sie [concurrency::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) zum Übermitteln von Statusbenachrichtigungen an Komponenten, von denen die asynchronen Vorgänge aufgerufen werden.

- Mithilfe von Abbruchtoken können interne asynchrone Vorgänge abgebrochen werden.

- Das Verhalten der `create_async` -Funktion hängt vom Rückgabetyp der daran übergebenen Arbeitsfunktion ab. Eine Arbeitsfunktion, die eine Aufgabe zurückgibt (entweder `task<T>` oder `task<void>`) oder synchron in dem Kontext ausgeführt wird, in dem `create_async`aufgerufen wurde. Eine Arbeitsfunktion, die `T` oder `void` zurückgibt, wird in einem die oft ausgegebene Befehlszeilen  Kontext ausgeführt.

- Mithilfe der [concurrency::task::then](reference/task-class.md#then) -Methode können Sie eine Kette von Aufgaben erstellen, die nacheinander ausgeführt werden. In einer UWP-App hängt der Standardkontext für die Fortsetzungen einer Aufgabe davon ab, wie diese Aufgabe erstellt wurde. Wenn die Aufgabe durch Übergabe einer asynchronen Aktion an den Aufgabenkonstruktor oder durch Übergabe eines Lambda-Ausdrucks erstellt wurde, der eine asynchrone Aktion zurückgibt, handelt es sich beim Standardkontext für alle Fortsetzungen dieser Aufgabe um den aktuellen Kontext. Wenn die Aufgabe nicht aus einer asynchronen Aktion erstellt wird, wird für die Fortsetzungen der Aufgabe standardmäßig ein beliebiger Kontext verwendet. Sie können den Standardkontext mit der [concurrency::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) -Klasse überschreiben.

## <a name="in-this-document"></a>Inhalt dieses Dokuments

- [Erstellen von asynchronen Operationen](#create-async)

- [Beispiel: Erstellen einer C++-Komponente für Windows-Runtime](#example-component)

- [Steuern des Ausführungs-Threads](#exethread)

- [Beispiel: Steuern der Ausführung in einer Windows-Runtime-App mit C++ und XAML](#example-app)

## <a name="creating-asynchronous-operations"></a><a name="create-async"></a>Erstellen von asynchronen Vorgängen

Sie können das Aufgaben- und Fortsetzungsmodell in der Parallel Patterns Library (PPL) verwenden, um Hintergrundaufgaben sowie zusätzliche Aufgaben zu definieren, die nach Abschluss der vorherigen Aufgabe ausgeführt werden sollen. Diese Funktionalität wird von der [concurrency::task](../../parallel/concrt/reference/task-class.md) -Klasse bereitgestellt. Weitere Informationen zu diesem Modell und der `task` -Klasse finden Sie unter [Task Parallelism](../../parallel/concrt/task-parallelism-concurrency-runtime.md)aufgerufen wurde.

Der Windows-Runtime ist eine Programmierschnittstelle, mit der Sie UWP-Apps erstellen können, die nur in einer speziellen Betriebssystemumgebung ausgeführt werden. Solche Apps verwenden autorisierte Funktionen, Datentypen und Geräte und werden aus dem Microsoft Store verteilt. Die Windows-Runtime wird durch die *Anwendungs Binärdatei Schnittstelle* (ABI) dargestellt. Die ABI ist ein zugrunde liegender binärer Vertrag, der Windows-Runtime-APIs für Programmiersprachen wie Visual C++ verfügbar macht.

Mithilfe des Windows-Runtime können Sie die besten Funktionen verschiedener Programmiersprachen verwenden und in einer APP kombinieren. Beispielsweise können Sie die Benutzeroberfläche in JavaScript erstellen und die rechenintensive App-Logik in einer C++-Komponente ausführen. Die Fähigkeit, diese rechenintensiven Vorgänge im Hintergrund auszuführen, ist ein Schlüsselfaktor dafür, die Benutzeroberfläche reaktionsfähig zu halten. Da die- `task` Klasse für C++ spezifisch ist, müssen Sie eine Windows-Runtime-Schnittstelle verwenden, um asynchrone Vorgänge an andere Komponenten zu übermitteln (die möglicherweise in anderen Sprachen als C++ geschrieben sind). Der Windows-Runtime stellt vier Schnittstellen bereit, mit denen Sie asynchrone Vorgänge darstellen können:

[Windows::Foundation::IAsyncAction](/uwp/api/windows.foundation.iasyncaction)<br/>
Stellt eine asynchrone Aktion dar.

[Windows:: Foundation:: iasyncactionwithprogress\<TProgress>](/uwp/api/windows.foundation.iasyncactionwithprogress-1)<br/>
Stellt eine asynchrone Aktion für Statusbenachrichtigungen dar.

[Windows:: Foundation:: iasyncoperation\<TResult>](/uwp/api/windows.foundation.iasyncoperation-1)<br/>
Stellt einen asynchronen Vorgang dar, der ein Ergebnis zurückgibt.

[Windows:: Foundation:: iasyncoperationwithprogress\<TResult, TProgress>](/uwp/api/windows.foundation.iasyncoperationwithprogress-2)<br/>
Stellt einen asynchronen Vorgang dar, der ein Ergebnis zurückgibt und den Status meldet.

Der Begriff *Aktion* bedeutet, dass die asynchrone Aufgabe keinen Wert generiert (denken Sie an eine Funktion, die `void`zurückgibt). Der Begriff *Vorgang* bedeutet, dass die asynchrone Aufgabe einen Wert generiert. Der Begriff *Status* bedeutet, dass die Aufgabe Statusbenachrichtigungen an den Aufrufer übermitteln kann. JavaScript, .NET Framework und Visual C++ bieten jeweils eine eigene Möglichkeit zum Erstellen von Instanzen dieser Schnittstellen zur ABI-übergreifenden Verwendung. Für Visual C++ stellt die PPL die [concurrency::create_async](reference/concurrency-namespace-functions.md#create_async) -Funktion bereit. Diese Funktion erstellt eine Windows-Runtime asynchrone Aktion oder einen Vorgang, der den Abschluss einer Aufgabe darstellt. Die `create_async` Funktion verwendet eine Arbeitsfunktion (in der Regel einen Lambda-Ausdruck), erstellt intern ein `task` -Objekt und umschließt diese Aufgabe in einer der vier asynchronen Windows-Runtime-Schnittstellen.

> [!NOTE]
> Verwenden `create_async` Sie nur, wenn Sie Funktionalität erstellen müssen, auf die von einer anderen Sprache oder einer anderen Windows-Runtime-Komponente zugegriffen werden kann. Verwenden Sie die `task` -Klasse direkt, wenn Sie wissen, dass der Vorgang von C++-Code in der gleichen Komponente sowohl erstellt als auch genutzt wird.

Der Rückgabetyp von `create_async` wird durch den Typ der Argumente bestimmt. Wenn z. B. die Arbeitsfunktion weder einen Wert zurückgibt und noch den Status meldet, wird von `create_async` eine `IAsyncAction`zurückgegeben. Wenn die Arbeitsfunktion keinen Wert zurückgibt, jedoch den Status meldet, wird von `create_async` eine `IAsyncActionWithProgress`zurückgegeben. Stellen Sie für Statusmeldungen ein [concurrency::progress_reporter](../../parallel/concrt/reference/progress-reporter-class.md) -Objekt als Parameter der Arbeitsfunktion bereit. Durch Statusbenachrichtigungen kann gemeldet werden, wie viel Arbeit bereits erledigt wurde und wie viel noch verbleibt (beispielsweise als Prozentsatz). Zudem können Ergebnisse gemeldet werden, sobald sie verfügbar sind.

Die `IAsyncAction`-, `IAsyncActionWithProgress<TProgress>`-, `IAsyncOperation<TResult>`- und `IAsyncActionOperationWithProgress<TProgress, TProgress>` -Schnittstellen bieten jeweils eine `Cancel` -Methode, die das Abbrechen des asynchronen Vorgangs ermöglicht. Die `task` -Klasse verwendet Abbruchtoken. Wenn Sie Arbeit mithilfe eines Abbruchtokens abbrechen, wird von der Runtime keine neue Verarbeitung gestartet, die dieses Token abonniert. Für eine bereits aktive Verarbeitung kann das entsprechende Abbruchtoken überwacht und die Verarbeitung zum angegebenen Zeitpunkt beendet werden. Im Dokument [Cancellation in the PPL](cancellation-in-the-ppl.md)wird dieser Mechanismus ausführlich beschrieben. Es gibt zwei Möglichkeiten, um den Task Abbruch mit den Windows-Runtime-Methoden zu verbinden `Cancel` . Die erste Möglichkeit besteht darin, die an `create_async` zu übergebende Arbeitsfunktion so zu definieren, dass diese ein [concurrency::cancellation_token](../../parallel/concrt/reference/cancellation-token-class.md) -Objekt akzeptiert. Wenn die- `Cancel` Methode aufgerufen wird, wird dieses Abbruch Token abgebrochen, und die normalen Abbruch Regeln gelten für das zugrunde liegende- `task` Objekt, das den-Aufruf unterstützt `create_async` . Wenn Sie kein `cancellation_token` -Objekt bereitstellen, wird dieses vom zugrunde liegenden `task` -Objekt implizit definiert. Definieren Sie ein `cancellation_token` -Objekt, wenn auf Abbrüche in der Arbeitsfunktion kooperativ reagiert werden muss. Im Abschnitt [Beispiel: Steuern der Ausführung in einer Windows-Runtime-App mit C++ und XAML](#example-app) finden Sie ein Beispiel für das Ausführen von Abbrüchen in einer universelle Windows-Plattform-app (UWP) mit c# und XAML, die eine benutzerdefinierte Windows-Runtime C++-Komponente verwendet.

> [!WARNING]
> In einer Kette von Aufgaben Fortsetzungen sollten Sie den Status immer bereinigen und dann " [parallelcurrency:: cancel_current_task](reference/concurrency-namespace-functions.md#cancel_current_task) " aufzurufen, wenn das Abbruch Token abgebrochen wird. Wenn Sie frühzeitig zurückkehren, anstatt `cancel_current_task`aufzurufen, geht der Vorgang in den Zustand "Abgeschlossen" anstelle von "Abgebrochen" über.

In der folgenden Tabelle werden die Kombinationen zusammengefasst, die Sie zum Definieren asynchroner Vorgänge in Ihrer App verwenden können.

|So erstellen Sie diese Windows-Runtime-Schnittstelle|Rückgabe dieses `create_async`-Typs|Übergabe dieser Parametertypen an die Arbeitsfunktion zur Verwendung als implizites Abbruchtoken|Übergabe dieser Parametertypen an die Arbeitsfunktion zur Verwendung als explizites Abbruchtoken|
|----------------------------------------------------------------------------------|------------------------------------------|--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
|`IAsyncAction`|`void` oder `task<void>`|(none)|(`cancellation_token`)|
|`IAsyncActionWithProgress<TProgress>`|`void` oder `task<void>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|
|`IAsyncOperation<TResult>`|`T` oder `task<T>`|(none)|(`cancellation_token`)|
|`IAsyncActionOperationWithProgress<TProgress, TProgress>`|`T` oder `task<T>`|(`progress_reporter`)|(`progress_reporter`, `cancellation_token`)|

Bei der Rückgabe kann es sich um einen Wert oder ein `task` -Objekt handeln, dass von der an die `create_async` -Funktion übergebenen Arbeitsfunktion zurückgeben wird. Diese Unterschiede führen zu verschiedenen Verhalten. Bei Rückgabe eines Werts wird die Arbeitsfunktion zur Ausführung auf einem Hintergrundthread mit `task` umschlossen. Zudem wird von der zugrunde liegenden `task` ein implizites Abbruchtoken verwendet. Umgekehrt wird die Arbeitsfunktion bei Rückgabe eines `task` -Objekts synchron ausgeführt. Stellen Sie daher beim Zurückgeben eines `task` -Objekts sicher, dass alle längeren Vorgänge in der Arbeitsfunktion auch als Aufgaben ausgeführt werden, damit die App reaktionsfähig bleiben kann. Zudem wird von der zugrunde liegenden `task` kein implizites Abbruchtoken verwendet. Daher müssen Sie die Arbeitsfunktion so definieren, dass diese ein `cancellation_token` -Objekt akzeptiert, falls bei der Rückgabe eines `task` -Objekts durch `create_async`Abbruchunterstützung erforderlich ist.

Das folgende Beispiel zeigt die verschiedenen Möglichkeiten zum Erstellen eines `IAsyncAction` Objekts, das von einer anderen Windows-Runtime Komponente genutzt werden kann.

[!code-cpp[concrt-windowsstore-primes#100](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_1.cpp)]

## <a name="example-creating-a-c-windows-runtime-component-and-consuming-it-from-c"></a><a name="example-component"></a>Beispiel: Erstellen einer C++-Windows-Runtime Komponente und deren Nutzung aus C\#

Eine APP, die XAML und c# verwendet, um die Benutzeroberfläche zu definieren, und eine C++-Windows-Runtime Komponente, um rechenintensive Vorgänge auszuführen. In diesem Beispiel wird von der C++-Komponente berechnet, bei welchen Zahlen in einem angegebenen Bereich es sich um Primzahlen handelt. Um die Unterschiede zwischen den vier Windows-Runtime asynchronen Aufgaben Schnittstellen zu veranschaulichen, starten Sie in Visual Studio, indem Sie eine **leere** Projekt Mappe erstellen und benennen `Primes` . Fügen Sie der Projektmappe dann ein Projekt für **Windows-Runtime-Komponente** hinzu, und nennen Sie es `PrimesLibrary`. Fügen Sie der generierten C++-Headerdatei folgenden Code hinzu (in diesem Beispiel wird "Class1.h" in "Primes.h" umbenannt). Jede `public` -Methode definiert eine der vier asynchronen Schnittstellen. Die Methoden, die einen Wert zurückgeben, geben ein [Windows:: Foundation:: Collections: \<int> : IVector](/uwp/api/windows.foundation.collections.ivector-1) -Objekt zurück. Die den Status meldenden Methoden generieren `double` -Werte, die den Prozentsatz der abgeschlossenen Gesamtarbeit definieren.

[!code-cpp[concrt-windowsstore-primes#1](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_2.h)]

> [!NOTE]
> Gemäß der Konvention enden die asynchronen Methodennamen im Windows-Runtime in der Regel mit "Async".

Fügen Sie der generierten C++-Quelldatei folgenden Code hinzu (in diesem Beispiel wird "Class1.cpp" in "Primes.cpp" umbenannt). Mit der `is_prime` -Funktion wird ermittelt, ob es sich bei der Eingabe um eine Primzahl handelt. Mit den verbleibenden Methoden wird die `Primes` -Klasse implementiert. Für jeden Aufruf von `create_async` wird eine mit der aufrufenden Methode kompatible Signatur verwendet. Da von `Primes::ComputePrimesAsync` beispielsweise `IAsyncAction`zurückgegeben wird, gibt die für `create_async` bereitgestellte Arbeitsfunktion keinen Wert zurück und akzeptiert kein `progress_reporter` -Objekt als Parameter.

[!code-cpp[concrt-windowsstore-primes#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_3.cpp)]

Jede Methode führt zuerst eine Überprüfung durch, um sicherzustellen, dass die Eingabeparameter nicht negativ sind. Im Fall eines negativen Eingabewerts wird von der Methode [Platform::InvalidArgumentException](../../cppcx/platform-invalidargumentexception-class.md)ausgelöst. Die Fehlerbehandlung wird weiter unten in diesem Abschnitt erläutert.

Um diese Methoden aus einer UWP-APP zu nutzen, verwenden Sie die Vorlage Visual c# **blank app (XAML)** , um der Visual Studio-Projekt Mappe ein zweites Projekt hinzuzufügen. In diesem Beispiel wird das Projekt `Primes`genannt. Fügen Sie anschließend im Projekt `Primes` einen Verweis auf das Projekt `PrimesLibrary` hinzu.

Fügen Sie "MainPage.xaml" den folgenden Code hinzu. Durch diesen Code wird die Benutzeroberfläche definiert, damit Sie die C++-Komponente aufrufen und Ergebnisse anzeigen können.

[!code-xml[concrt-windowsstore-primes#3](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_4.xaml)]

Fügen Sie der `MainPage` -Klasse in "MainPage.xaml" den folgenden Code hinzu. Durch diesen Code werden ein `Primes` -Objekt und die Ereignishandler für Schaltflächen definiert.

[!code-cs[concrt-windowsstore-primes#4](../../parallel/concrt/codesnippet/csharp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_5.cs)]

Von diesen Methoden wird mithilfe des `async` -Schlüsselworts und des `await` -Schlüsselworts die Benutzeroberfläche aktualisiert, nachdem die asynchronen Vorgänge abgeschlossen wurden. Informationen zum asynchronen Programmieren in UWP-apps finden Sie unter [Threading und Async-Programmierung](/windows/uwp/threading-async).

Die `getPrimesCancellation` -Methode und die `cancelGetPrimes` -Methode werden zusammen verwendet, damit der Benutzer den Vorgang abbrechen kann. Wenn der Benutzer die Schaltfläche **Abbrechen** auswählt, ruft die- `cancelGetPrimes` Methode [iasyncoperationwithprogress \<TResult, TProgress> :: Cancel](/uwp/api/windows.foundation.iasyncinfo.cancel) auf, um den Vorgang abzubrechen. Der Concurrency Runtime, der den zugrunde liegenden asynchronen Vorgang verwaltet, löst einen internen Ausnahmetyp aus, der vom Windows-Runtime abgefangen wird, um zu kommunizieren, dass der Abbruch abgeschlossen wurde. Weitere Informationen zum Abbruch Modell finden Sie unter [Abbruch](../../parallel/concrt/cancellation-in-the-ppl.md).

> [!IMPORTANT]
> Damit die ppl ordnungsgemäß an den Windows-Runtime Berichten kann, dass der Vorgang abgebrochen wurde, fangen Sie diesen internen Ausnahmetyp nicht ab. Dies bedeutet auch, dass nicht alle Ausnahmen abgefangen werden sollten(`catch (...)`). Wenn Sie alle Ausnahmen abfangen müssen, lösen Sie die Ausnahme erneut aus, um sicherzustellen, dass der Windows-Runtime den Abbruch Vorgang beenden kann.

In der folgenden Abbildung wird die `Primes` -App nach Auswahl aller Optionen dargestellt.

![Windows-Runtime PRIMES-App](../../parallel/concrt/media/concrt_windows_primes.png "Windows-Runtime PRIMES-App")

Ein Beispiel, in dem verwendet wird, `create_async` um asynchrone Aufgaben zu erstellen, die von anderen Sprachen genutzt werden können, finden [Sie unter Using C++ im Beispiel für den Reise-Optimierer von Beispiel](/previous-versions/windows/apps/hh699891(v=vs.140))Code.

## <a name="controlling-the-execution-thread"></a><a name="exethread"></a>Steuern des Ausführungs Threads

Der Windows-Runtime verwendet das COM-Threading Modell. In diesem Modell werden Objekte in unterschiedlichen Apartments gehostet, abhängig von der jeweiligen Synchronisierungsmethode. Threadsichere Objekte werden im Multithread-Apartment (MTA) gehostet. Objekte, auf die von einem einzelnen Thread zugegriffen werden muss, werden in einem Singlethread-Apartment (STA) gehostet.

In einer App mit Benutzeroberfläche ist der ASTA (Application STA)-Thread für das Verschieben von Fenstermeldungen zuständig und ist der einzige Thread im Prozess, von dem die STA-gehosteten UI-Steuerelemente aktualisiert werden können. Dies hat zwei Auswirkungen. Erstens sollten alle CPU-intensiven und E/A-Vorgänge nicht im ASTA-Thread ausgeführt werden, damit die App reaktionsfähig bleibt. Zweitens müssen von Hintergrundthreads stammende Ergebnisse zurück in das ASTA gemarshallt werden, um die Benutzeroberfläche zu aktualisieren. In einer C++-UWP `MainPage` -App und anderen XAML-Seiten werden alle auf dem ATSA ausgeführt. Daher werden im ASTA deklarierte Aufgabenfortsetzungen standardmäßig dort ausgeführt, sodass Steuerelemente direkt im Fortsetzungstext aktualisiert werden können. Wenn Sie jedoch eine Aufgabe in einer anderen Aufgabe schachteln, werden alle Fortsetzungen dieser geschachtelten Aufgabe im MTA ausgeführt. Daher sollten Sie berücksichtigen, ob der Ausführungskontext dieser Fortsetzungen explizit angegeben werden muss.

Dank einer besonderen Semantik können die Threaddetails bei durch einen asynchronen Vorgang wie `IAsyncOperation<TResult>`erstellten Aufgaben ignoriert werden. Obwohl ein Vorgang möglicherweise in einem Hintergrundthread ausgeführt wird (oder überhaupt nicht von einem Thread unterstützt wird), erfolgen dessen Fortsetzungen in jedem Fall standardmäßig in dem Apartment, von dem die Fortsetzungsvorgänge gestartet wurden (d. h. im Apartment, von dem `task::then`aufgerufen wurde). Mithilfe der [concurrency::task_continuation_context](../../parallel/concrt/reference/task-continuation-context-class.md) -Klasse kann der Ausführungskontext einer Fortsetzung gesteuert werden. Verwenden Sie zum Erstellen von `task_continuation_context` -Objekten die folgenden statischen Hilfsmethoden:

- Mithilfe von [concurrency::task_continuation_context::use_arbitrary](reference/task-continuation-context-class.md#use_arbitrary) geben Sie an, dass die Fortsetzung in einem Hintergrundthread ausgeführt wird.

- Mithilfe von [concurrency::task_continuation_context::use_current](reference/task-continuation-context-class.md#use_current) geben Sie an, dass die Fortsetzung in dem Thread ausgeführt wird, von dem `task::then`aufgerufen wurde.

Sie können der `task_continuation_context` task::then [-Methode ein](reference/task-class.md#then) -Objekt übergeben, um den Ausführungskontext der Fortsetzung explizit zu steuern. Alternativ können Sie die Aufgabe an ein anderes Apartment übergeben und dann die `task::then` -Methode aufrufen, um den Ausführungskontext implizit zu steuern.

> [!IMPORTANT]
> Da der Hauptbenutzer Oberflächen-Thread von UWP-apps unter STA ausgeführt wird, werden Fortsetzungen, die Sie auf diesem STA erstellen, standardmäßig auf dem STA ausgeführt. Entsprechend werden im MTA erstellte Fortsetzungen auch im MTA ausgeführt.

Im folgenden Abschnitt wird eine App dargestellt, die eine Datei auf dem Datenträger liest, die häufigsten Wörter in dieser Datei sucht und die Ergebnisse anschließend auf der Benutzeroberfläche anzeigt. Der letzte Vorgang (die Aktualisierung der Benutzeroberfläche) erfolgt im UI-Thread.

> [!IMPORTANT]
> Dieses Verhalten gilt speziell für UWP-apps. Bei Desktop-Apps wird die Ausführung von Fortsetzungen nicht von Ihnen gesteuert. Stattdessen wird vom Planer ein Arbeitsthread zur Ausführung der einzelnen Fortsetzungen ausgewählt.

> [!IMPORTANT]
> Rufen Sie nicht [concurrency::task::wait](reference/task-class.md#wait) im Text einer Fortsetzung auf, die im STA ausgeführt wird. Andernfalls löst die Laufzeit [concurrency::invalid_operation](../../parallel/concrt/reference/invalid-operation-class.md) aus, da diese Methode den aktuellen Thread blockiert und die App dadurch möglicherweise nicht mehr reagiert. Sie können jedoch die [concurrency::task::get](reference/task-class.md#get) -Methode aufrufen, um das Ergebnis der Vorgängeraufgabe in einer aufgabenbasierten Fortsetzung zu erhalten.

## <a name="example-controlling-execution-in-a-windows-runtime-app-with-c-and-xaml"></a><a name="example-app"></a>Beispiel: Steuern der Ausführung in einer Windows-Runtime-App mit C++ und XAML

Betrachten Sie eine App mit C++ und XAML, die eine Datei auf dem Datenträger liest, die häufigsten Wörter in dieser Datei sucht und die Ergebnisse anschließend auf der Benutzeroberfläche anzeigt. Um diese APP zu erstellen, starten Sie in Visual Studio, indem Sie ein **leeres App-Projekt (Universal Windows)** erstellen und benennen `CommonWords` . Geben Sie im App-Manifest die **Dokumentbibliothek** -Funktion an, damit die App auf den Ordner "Dokumente" zugreifen kann. Fügen Sie im Deklarationsabschnitt des App-Manifests außerdem den Textdateityp (.txt) hinzu. Weitere Informationen zu App-Funktionen und-Deklarationen finden Sie unter [Verpacken, Bereitstellung und Abfrage von Windows-apps](/windows/win32/appxpkg/appx-portal).

Aktualisieren Sie in "MainPage.xaml" das `Grid` -Element mit einem `ProgressRing` -Element und einem `TextBlock` -Element. `ProgressRing` gibt an, dass der Vorgang ausgeführt wird, und `TextBlock` zeigt die Ergebnisse der Berechnung an.

[!code-xml[concrt-windowsstore-commonwords#1](../../parallel/concrt/codesnippet/xaml/creating-asynchronous-operations-in-cpp-for-windows-store-apps_6.xaml)]

Fügen Sie " `#include` *PCH. h*" die folgenden-Anweisungen hinzu.

[!code-cpp[concrt-windowsstore-commonwords#2](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_7.h)]

Fügen Sie der `MainPage` -Klasse ("MainPage.h") die folgenden Methodendeklarationen hinzu.

[!code-cpp[concrt-windowsstore-commonwords#3](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_8.h)]

Fügen Sie "MainPage.cpp" die folgenden `using` -Anweisungen hinzu.

[!code-cpp[concrt-windowsstore-commonwords#4](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_9.cpp)]

Implementieren Sie in "MainPage.cpp" die Methoden `MainPage::MakeWordList`, `MainPage::FindCommonWords`und `MainPage::ShowResults` . Von `MainPage::MakeWordList` und `MainPage::FindCommonWords` werden rechenintensive Vorgänge ausgeführt. Von der `MainPage::ShowResults` -Methode wird das Ergebnis der Berechnung auf der Benutzeroberfläche angezeigt.

[!code-cpp[concrt-windowsstore-commonwords#5](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_10.cpp)]

Ändern Sie den `MainPage` -Konstruktor, um eine Kette von Fortsetzungsaufgaben zu erstellen, von denen häufige Wörter im Buch *Die Ilias* von Homer auf der Benutzeroberfläche angezeigt werden. Die ersten beiden Fortsetzungsaufgaben, von denen der Text in einzelne Wörter unterteilt und nach häufigen Wörtern durchsucht wird, können zeitaufwändig sein. Daher wird für diese Aufgaben explizit die Ausführung im Hintergrund festgelegt. Für die letzte Fortsetzungsaufgabe zur Aktualisierung der Benutzeroberfläche wird kein Fortsetzungskontext angegeben, weshalb hierbei die Apartmentthreadregeln befolgt werden.

[!code-cpp[concrt-windowsstore-commonwords#6](../../parallel/concrt/codesnippet/cpp/creating-asynchronous-operations-in-cpp-for-windows-store-apps_11.cpp)]

> [!NOTE]
> In diesem Beispiel wird das Angeben eines Ausführungskontexts und Zusammenstellen einer Kette von Fortsetzungen veranschaulicht. Denken Sie daran, dass die Fortsetzungen einer durch einen asynchronen Vorgang erstellten Aufgabe standardmäßig in dem Apartment ausgeführt werden, von dem `task::then`aufgerufen wurde. In diesem Beispiel wird daher durch `task_continuation_context::use_arbitrary` angegeben, dass Vorgänge, die nicht die Benutzeroberfläche betreffen, in einem Hintergrundthread ausgeführt werden.

In der folgenden Abbildung werden die Ergebnisse der `CommonWords` -App dargestellt.

![Windows-Runtime commonwords-App](../../parallel/concrt/media/concrt_windows_common_words.png "Windows-Runtime commonwords-App")

In diesem Beispiel kann der Abbruch unterstützt werden, da von den `task` Objekten, die unterstützt werden, `create_async` ein implizites Abbruch Token verwendet wird. Wenn die Aufgaben kooperativ auf Abbruchvorgänge reagieren sollen, definieren Sie die Arbeitsfunktion so, dass diese ein `cancellation_token` -Objekt akzeptiert. Weitere Informationen zum Abbrechen in der PPL finden Sie unter [Cancellation in the PPL](cancellation-in-the-ppl.md).

## <a name="see-also"></a>Weitere Informationen

[Concurrency Runtime](../../parallel/concrt/concurrency-runtime.md)

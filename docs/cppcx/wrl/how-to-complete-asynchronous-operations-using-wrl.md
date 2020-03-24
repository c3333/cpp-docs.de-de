---
title: 'Gewusst wie: Abschließen asynchroner Vorgänge mit WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
ms.openlocfilehash: 8e7e52342cf73a56c6c33d4d1f998f446d632ddd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213940"
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>Gewusst wie: Abschließen asynchroner Vorgänge mit WRL

In diesem Dokument wird gezeigt, wie Sie C++ die Windows-Runtime Template Library (WRL) verwenden, um asynchrone Vorgänge zu starten und Aufgaben auszuführen, wenn die Vorgänge beendet sind.

Dieses Dokument enthält zwei Beispiele. Im ersten Beispiel wird ein asynchroner Timer gestartet und gewartet, bis der Timer abläuft. In diesem Beispiel geben Sie die asynchrone Aktion an, wenn Sie das Timer-Objekt erstellen. Im zweiten Beispiel wird ein Hintergrundarbeitsthread ausgeführt. In diesem Beispiel wird gezeigt, wie mit einer Windows-Runtime Methode gearbeitet wird, die eine `IAsyncInfo`-Schnittstelle zurückgibt. Die [Rückruf](callback-function-wrl.md) Funktion ist ein wichtiger Bestandteil beider Beispiele, da Sie Ihnen ermöglicht, einen Ereignishandler für die Verarbeitung der Ergebnisse der asynchronen Vorgänge anzugeben.

Ein grundlegendes Beispiel, das eine Instanz einer Komponente erstellt und einen Eigenschafts Wert abruft, finden [Sie unter Gewusst wie: Aktivieren und Verwenden einer Windows-Runtime Komponente](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).

> [!TIP]
> In diesem Beispiele werden die Rückrufe mithilfe von Lambdaausdrücken definiert. Sie können auch Funktions Objekte (functors), Funktionszeiger oder [Std:: function](../../standard-library/function-class.md) -Objekte verwenden. Weitere Informationen zu C++ Lambda-Ausdrücken finden Sie unter [Lambda-Ausdrücke](../../cpp/lambda-expressions-in-cpp.md).

## <a name="example-working-with-a-timer"></a>Beispiel: Arbeiten mit einem Timer

Mit den folgenden Schritten wird ein asynchroner Timer und gestartet und gewartet, bis der Timer abläuft. Im Folgenden finden Sie das vollständige Beispiel.

> [!WARNING]
> Obwohl Sie in der Regel die C++ Windows-Runtime Vorlagen Bibliothek in einer universelle Windows-Plattform-app (UWP) verwenden, wird in diesem Beispiel eine Konsolen-App zur Veranschaulichung verwendet. Funktionen wie `wprintf_s` sind in einer UWP-APP nicht verfügbar. Weitere Informationen zu den Typen und Funktionen, die Sie in einer UWP-App verwenden können, finden Sie unter CRT-Funktionen, die in universelle Windows-Plattform-apps und [Win32 und com für UWP-apps](/uwp/win32-and-com/win32-and-com-for-uwp-apps) [nicht unterstützt](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) werden.

1. Fügen Sie (`#include`) alle erforderlichen Windows-Runtime, C++ Windows-Runtime Vorlagen Bibliothek oder C++ Standard Bibliotheks Header ein.

   [!code-cpp[wrl-consume-async#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]

   `Windows.System.Threading.h` deklariert die Typen, die für die Verwendung eines asynchronen Timers erforderlich sind.

   Es wird empfohlen, den Code mithilfe der `using namespace`-Direktive in der CPP-Datei verständlicher zu gestalten.

2. Initialisieren Sie die Windows-Runtime.

   [!code-cpp[wrl-consume-async#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]

3. Erstellen Sie eine Aktivierungsfactory für die `ABI::Windows::System::Threading::IThreadPoolTimer`-Schnittstelle.

   [!code-cpp[wrl-consume-async#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]

   Der Windows-Runtime verwendet voll qualifizierte Namen, um Typen zu identifizieren. Der `RuntimeClass_Windows_System_Threading_ThreadPoolTimer`-Parameter ist eine Zeichenfolge, die vom Windows-Runtime bereitgestellt wird und den erforderlichen Lauf Zeit Klassennamen enthält.

4. Erstellen Sie ein [Ereignis](event-class-wrl.md) Objekt, das den Timer-Rückruf mit der Haupt-App synchronisiert.

   [!code-cpp[wrl-consume-async#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]

   > [!NOTE]
   > Dieses Ereignis dient lediglich zur Veranschaulichung im Rahmen der Konsolen-App. In diesem Beispiel sorgt das Ereignis dafür, dass ein asynchroner Vorgang abgeschlossen wird, bevor die App beendet wird. In den meisten Apps warten Sie in der Regel nicht auf den Abschluss asynchroner Vorgänge.

5. Erstellen Sie ein `IThreadPoolTimer`-Objekt, das nach zwei Sekunden abläuft. Erstellen Sie mit der `Callback`-Funktion den Ereignishandler (ein `ABI::Windows::System::Threading::ITimerElapsedHandler`-Objekt).

   [!code-cpp[wrl-consume-async#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]

6. Drucken Sie eine Meldung an die Konsole, und warten Sie, bis der Timerrückruf abgeschlossen ist. Alle `ComPtr`- und RAII-Objekte verlassen den Bereich und werden automatisch freigegeben.

   [!code-cpp[wrl-consume-async#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]

Im Folgenden sehen Sie das vollständige Beispiel:

[!code-cpp[wrl-consume-async#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]

### <a name="compiling-the-code"></a>Kompilieren des Codes

Um den Code zu kompilieren, kopieren Sie ihn, und fügen Sie ihn in ein Visual Studio-Projekt ein, oder fügen Sie ihn in eine Datei mit dem Namen `wrl-consume-async.cpp` ein, und führen Sie dann den folgenden Befehl in einem Visual Studio-Eingabe Aufforderungs Fenster aus.

`cl.exe wrl-consume-async.cpp runtimeobject.lib`

## <a name="example-working-with-a-background-thread"></a>Beispiel: Arbeiten mit einem Hintergrundthread

Mit den folgenden Schritten starten Sie einen Arbeitsthread und definieren die Aktion, die von diesem Thread ausgeführt wird. Im Folgenden finden Sie das vollständige Beispiel.

> [!TIP]
> In diesem Beispiel wird gezeigt, wie Sie mit der `ABI::Windows::Foundation::IAsyncAction`-Schnittstelle arbeiten. Sie können dieses Muster für jede Schnittstelle anwenden, die `IAsyncInfo` implementiert: `IAsyncAction`, `IAsyncActionWithProgress`, `IAsyncOperation` und `IAsyncOperationWithProgress`.

1. Fügen Sie (`#include`) alle erforderlichen Windows-Runtime, C++ Windows-Runtime Vorlagen Bibliothek oder C++ Standard Bibliotheks Header ein.

   [!code-cpp[wrl-consume-asyncOp#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]

   Windows.System.Threading.h deklariert die Typen, die zur Verwendung eines Arbeitsthreads benötigt werden.

   Es wird empfohlen, den Code mithilfe der `using namespace`-Anweisung in der CPP-Datei verständlicher zu gestalten.

2. Initialisieren Sie die Windows-Runtime.

   [!code-cpp[wrl-consume-asyncOp#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]

3. Erstellen Sie eine Aktivierungsfactory für die `ABI::Windows::System::Threading::IThreadPoolStatics`-Schnittstelle.

   [!code-cpp[wrl-consume-asyncOp#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]

4. Erstellen Sie ein [Ereignis](event-class-wrl.md) Objekt, das den Abschluss des Arbeitsthreads mit der Haupt-App synchronisiert.

   [!code-cpp[wrl-consume-asyncOp#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]

   > [!NOTE]
   > Dieses Ereignis dient lediglich zur Veranschaulichung im Rahmen der Konsolen-App. In diesem Beispiel sorgt das Ereignis dafür, dass ein asynchroner Vorgang abgeschlossen wird, bevor die App beendet wird. In den meisten Apps warten Sie in der Regel nicht auf den Abschluss asynchroner Vorgänge.

5. Rufen Sie die `IThreadPoolStatics::RunAsync`-Methode auf, um einen Arbeitsthread zu erstellen. Definieren Sie mit der `Callback`-Funktion die Aktion.

   [!code-cpp[wrl-consume-asyncOp#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]

   Die `IsPrime`-Funktion wird im folgenden vollständigen Beispiel definiert.

6. Drucken Sie eine Meldung an die Konsole, und warten Sie, bis der Thread abgeschlossen ist. Alle `ComPtr`- und RAII-Objekte verlassen den Bereich und werden automatisch freigegeben.

   [!code-cpp[wrl-consume-asyncOp#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]

Im Folgenden sehen Sie das vollständige Beispiel:

[!code-cpp[wrl-consume-asyncOp#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]

### <a name="compiling-the-code"></a>Kompilieren des Codes

Um den Code zu kompilieren, kopieren Sie ihn, und fügen Sie ihn in ein Visual Studio-Projekt ein, oder fügen Sie ihn in eine Datei mit dem Namen `wrl-consume-asyncOp.cpp` ein, und führen Sie dann den folgenden Befehl in einem **Visual Studio-Eingabe** Aufforderungs Fenster aus.

`cl.exe wrl-consume-asyncOp.cpp runtimeobject.lib`

## <a name="see-also"></a>Weitere Informationen

[C++-Vorlagenbibliothek für Windows-Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)

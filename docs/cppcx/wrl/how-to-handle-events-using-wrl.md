---
title: 'Gewusst wie: Behandeln von Ereignissen mit WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
ms.openlocfilehash: 0e13212d7cb481bc72a903a31fb170fd1ff8b7ec
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213927"
---
# <a name="how-to-handle-events-using-wrl"></a>Gewusst wie: Behandeln von Ereignissen mit WRL

In diesem Dokument wird gezeigt, wie Sie C++ die Windows-Runtime Vorlagen Bibliothek (WRL) verwenden, um die Ereignisse eines Windows-Runtime Objekts zu abonnieren und zu behandeln.

Ein grundlegendes Beispiel, das eine Instanz dieser Komponente erstellt und einen Eigenschafts Wert abruft, finden [Sie unter Gewusst wie: Aktivieren und Verwenden einer Windows-Runtime Komponente](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md).

## <a name="subscribing-to-and-handling-events"></a>Abonnieren und Behandeln von Ereignissen

Mit den folgenden Schritten starten Sie ein `ABI::Windows::System::Threading::IDeviceWatcher`-Objekt und überwachen den Fortschritt mit Ereignishandlern. Die `IDeviceWatcher`-Schnittstelle ermöglicht es Ihnen, Geräte asynchron oder im Hintergrund aufzulisten und benachrichtigt zu werden, wenn Geräte hinzugefügt, entfernt oder geändert werden. Die [Rückruf](callback-function-wrl.md) Funktion ist ein wichtiger Bestandteil dieses Beispiels, da Sie Sie ermöglicht, Ereignishandler anzugeben, die die Ergebnisse des Hintergrund Vorgangs verarbeiten. Im Folgenden finden Sie das vollständige Beispiel.

> [!WARNING]
> Obwohl Sie in der Regel die C++ Windows-Runtime Vorlagen Bibliothek in einer universelle Windows-Plattform-App verwenden, wird in diesem Beispiel eine Konsolen-App zur Veranschaulichung verwendet. Funktionen wie `wprintf_s` sind in einer universelle Windows-Plattform-APP nicht verfügbar. Weitere Informationen zu den Typen und Funktionen, die Sie in einer universelle Windows-Plattform-App verwenden können, finden Sie unter CRT-Funktionen, die [in universelle Windows-Plattform-apps nicht unterstützt](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) werden, und [Win32 und com für UWP-apps](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

1. Fügen Sie (`#include`) alle erforderlichen Windows-Runtime, C++ Windows-Runtime Vorlagen Bibliothek oder C++ Standard Bibliotheks Header ein.

   [!code-cpp[wrl-consume-event#2](../codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]

   `Windows.Devices.Enumeration.h` deklariert die Typen, die zum Aufzählen von Geräten erforderlich sind.

   Es wird empfohlen, den Code mithilfe der `using namespace`-Direktive in der CPP-Datei verständlicher zu gestalten.

2. Deklarieren Sie die lokalen Variablen für die App. In diesem Beispiel wird die Anzahl der aufgelisteten Geräte und Registrierungstoken abgelegt; dadurch kann später das Abonnement von Ereignissen gekündigt werden.

   [!code-cpp[wrl-consume-event#7](../codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]

3. Initialisieren Sie die Windows-Runtime.

   [!code-cpp[wrl-consume-event#3](../codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]

4. Erstellen Sie ein [Ereignis](event-class-wrl.md) Objekt, das den Abschluss des Enumerationsprozesses mit der Haupt-App synchronisiert.

   [!code-cpp[wrl-consume-event#4](../codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]

   > [!NOTE]
   > Dieses Ereignis dient lediglich zur Veranschaulichung im Rahmen der Konsolen-App. In diesem Beispiel sorgt das Ereignis dafür, dass ein asynchroner Vorgang abgeschlossen wird, bevor die App beendet wird. In den meisten Apps warten Sie in der Regel nicht auf den Abschluss asynchroner Vorgänge.

5. Erstellen Sie eine Aktivierungsfactory für die `IDeviceWatcher`-Schnittstelle.

   [!code-cpp[wrl-consume-event#5](../codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]

   Der Windows-Runtime verwendet voll qualifizierte Namen, um Typen zu identifizieren. Der `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation`-Parameter ist eine Zeichenfolge, die vom Windows-Runtime bereitgestellt wird und den erforderlichen Lauf Zeit Klassennamen enthält.

6. Erstellen Sie das Objekt `IDeviceWatcher`.

   [!code-cpp[wrl-consume-event#6](../codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]

7. Abonnieren Sie mit der `Callback`-Funktion die Ereignisse `Added`, `EnumerationCompleted` und `Stopped`.

   [!code-cpp[wrl-consume-event#8](../codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]

   Der Ereignishandler `Added` erhöht die Anzahl der aufgelisteten Geräte. Er beendet den Enumerationsprozess, nachdem zehn Geräte gefunden wurden.

   Der Ereignishandler `Stopped` entfernt die Ereignishandler und legt das Abschlussereignis fest.

   Der Ereignishandler `EnumerationCompleted` beendet den Enumerationsprozess. Dieses Ereignis wird behandelt, falls es einmal weniger als zehn Geräte gibt.

   > [!TIP]
   > Dieses Beispiel definiert die Rückrufe mithilfe eines Lambdaausdrucks. Sie können auch Funktions Objekte (functors), Funktionszeiger oder [Std:: function](../../standard-library/function-class.md) -Objekte verwenden. Weitere Informationen zu Lambdaausdrücken finden Sie unter [Lambda Expressions (Lambdaausdrücke)](../../cpp/lambda-expressions-in-cpp.md).

8. Starten Sie den Enumerationsprozess.

   [!code-cpp[wrl-consume-event#9](../codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]

9. Warten Sie, bis der Enumerationsprozess abgeschlossen ist, und drucken Sie dann eine Meldung aus. Alle `ComPtr`- und RAII-Objekte verlassen den Bereich und werden automatisch freigegeben.

   [!code-cpp[wrl-consume-event#10](../codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]

Im Folgenden sehen Sie das vollständige Beispiel:

[!code-cpp[wrl-consume-event#1](../codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]

## <a name="compiling-the-code"></a>Kompilieren des Codes

Um den Code zu kompilieren, kopieren Sie ihn, und fügen Sie ihn in ein Visual Studio-Projekt ein, oder fügen Sie ihn in eine Datei mit dem Namen `wrl-consume-events.cpp` ein, und führen Sie dann den folgenden Befehl in einem **Visual Studio-Eingabe** Aufforderungs Fenster aus.

`cl.exe wrl-consume-events.cpp runtimeobject.lib`

## <a name="see-also"></a>Weitere Informationen

[C++-Vorlagenbibliothek für Windows-Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)

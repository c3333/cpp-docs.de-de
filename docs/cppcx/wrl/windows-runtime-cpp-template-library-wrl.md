---
title: Windows Runtime C++ Template Library (WRL)
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: b915afce-553b-44a7-b8dc-0ab601758eb0
ms.openlocfilehash: 10e2303fa5498079fc1f9bb6f82aa909c9a6c3ee
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840534"
---
# <a name="windows-runtime-c-template-library-wrl"></a>Windows Runtime C++ Template Library (WRL)

Die C++-Vorlagenbibliothek für Windows-Runtime(WRL) ist eine Vorlagenbibliothek, die eine niederschwelligen Zugang zur Erstellung und Verwendung von Windows-Runtime-Komponenten bietet.

> [!NOTE]
> WRL ist nun durch C++/WinRT abgelöst, eine standardmäßige C++ 17-sprach Projektion für Windows-Runtime-APIs. C++/WinRT ist im Windows 10 SDK ab Version 1803 erhältlich. C++/WinRT wird vollständig in Header Dateien implementiert und wurde entwickelt, um Ihnen erstklassigen Zugriff auf die moderne Windows-API zu ermöglichen.
>
> Mit C++/WinRT können Sie mithilfe eines beliebigen Standard kompatiblen C++ 17-Compilers Windows-Runtime-APIs verwenden und erstellen. C++/WinRT führt in der Regel zu einer besseren Leistung und erzeugt kleinere Binärdateien als jede andere Sprachoption für die Windows-Runtime. Wir unterstützen C++/CX und WRL weiterhin, empfehlen jedoch dringend die Verwendung von C++/WinRT für neue Anwendungen. Weitere Informationen finden Sie unter [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/index).

## <a name="benefits"></a>Vorteile

Die Windows-Runtime C++-Vorlagen Bibliothek ermöglicht es Ihnen, Component Object Model (com)-Komponenten leichter zu implementieren und zu nutzen. Er bietet Techniken zum Verwalten von Daten wie Verweis Zählung, um die Lebensdauer von Objekten zu verwalten und HRESULT-Werte zu testen, um zu bestimmen, ob ein Vorgang erfolgreich war Um die Windows-Runtime C++-Vorlagen Bibliothek erfolgreich verwenden zu können, müssen Sie diese Regeln und Verfahren sorgfältig befolgen.

C++/CX ist eine sprachbasierte Methode auf hoher Ebene, um Windows-Runtime Komponenten zu verwenden. Sowohl die Windows-Runtime C++-Vorlagen Bibliothek als auch die C++-/CX vereinfachen das Schreiben von Code für die Windows-Runtime, indem automatisch Aufgaben für die Verwaltung in Ihrem Namen ausgeführt werden.

Die Windows-Runtime C++-Vorlagen Bibliothek und C++/CX bieten unterschiedliche Vorteile. Hier sind einige Gründe, warum Sie möglicherweise die Windows-Runtime C++ Template Library anstelle von C++/CX verwenden möchten:

- Windows-Runtime C++-Vorlagen Bibliothek fügt der Windows-Runtime Application Binary Interface (ABI) wenig Abstraktion hinzu, sodass Sie den zugrunde liegenden Code steuern können, um Windows-Runtime APIs besser erstellen oder nutzen zu können.

- C++/CX stellt com HRESULT-Werte als Ausnahmen dar. Wenn Sie eine CodeBase geerbt haben, die com verwendet, oder eine CodeBase, die keine Ausnahmen verwendet, stellen Sie möglicherweise fest, dass die Windows-Runtime C++-Vorlagen Bibliothek eine natürlichere Möglichkeit zum Arbeiten mit der Windows-Runtime ist, da keine Ausnahmen verwendet werden müssen.

   > [!NOTE]
   > Die Windows-Runtime C++-Vorlagen Bibliothek verwendet HRESULT-Werte und löst keine Ausnahmen aus. Außerdem verwendet die Windows-Runtime C++-Vorlagen Bibliothek intelligente Zeiger und das RAII-Muster, um sicherzustellen, dass Objekte ordnungsgemäß zerstört werden, wenn der Anwendungscode eine Ausnahme auslöst. Weitere Informationen zu intelligenten Zeigern und RAII finden Sie unter [intelligente Zeiger](../../cpp/smart-pointers-modern-cpp.md) und [Objekt eigene Ressourcen (RAII)](../../cpp/objects-own-resources-raii.md).

- Der Zweck und das Design der Windows-Runtime C++-Vorlagen Bibliothek sind von der Active Template Library (ATL) inspiriert, bei der es sich um einen Satz von Vorlagen basierten C++-Klassen handelt, die die Programmierung von COM-Objekten vereinfachen. Da Windows-Runtime C++-Vorlagen Bibliothek Standard-C++ verwendet, um die Windows-Runtime zu umschließen, können Sie viele vorhandene COM-Komponenten, die in ATL geschrieben sind, leichter in den Windows-Runtime portieren und damit interagieren. Wenn Sie ATL bereits kennen, werden Sie möglicherweise feststellen, dass die Programmierung von Windows-Runtime C++-Vorlagen Bibliothek einfacher ist.

## <a name="getting-started"></a>Erste Schritte

Hier finden Sie einige Ressourcen, mit denen Sie sofort mit der Windows-Runtime C++-Vorlagen Bibliothek arbeiten können.

[Video zur Windows Runtime-Bibliothek (WRL)](https://channel9.msdn.com/Events/Windows-Camp/Developing-Windows-8-Metro-style-apps-in-Cpp/The-Windows-Runtime-Library-WRL-)<br/>
In diesem Channel 9-Video erfahren Sie mehr darüber, wie die Windows-Runtime C++-Vorlagen Bibliothek Sie beim Schreiben von universelle Windows-Plattform (UWP)-apps und beim Erstellen und Nutzen von Windows-Runtime Komponenten unterstützt.

[Gewusst wie: Aktivieren und Verwenden einer Windows-Runtime-Komponente](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)<br/>
Zeigt, wie die Windows-Runtime C++-Vorlagen Bibliothek verwendet wird, um die Windows-Runtime zu initialisieren und eine Windows-Runtime Komponente zu aktivieren und zu verwenden.

[Gewusst wie: Abschließen asynchroner Vorgänge](how-to-complete-asynchronous-operations-using-wrl.md)<br/>
Zeigt, wie die Windows-Runtime C++-Vorlagen Bibliothek verwendet wird, um asynchrone Vorgänge zu starten und Aufgaben auszuführen, wenn der Vorgang beendet wird.

[Gewusst wie: Behandeln von Ereignissen](how-to-handle-events-using-wrl.md)<br/>
Zeigt, wie die Windows-Runtime C++-Vorlagen Bibliothek verwendet wird, um die Ereignisse eines Windows-Runtime Objekts zu abonnieren und zu verarbeiten.

[Exemplarische Vorgehensweise: Erstellen einer UWP-App mithilfe von WRL und Media Foundation](walkthrough-creating-a-windows-store-app-using-wrl-and-media-foundation.md)<br/>
Erfahren Sie, wie Sie eine UWP-app erstellen, die [Microsoft Media Foundation](/windows/win32/medfound/microsoft-media-foundation-sdk)verwendet.

[Gewusst wie: Erstellen einer klassischen COM-Komponente](how-to-create-a-classic-com-component-using-wrl.md)<br/>
Zeigt, wie die Windows-Runtime C++-Vorlagen Bibliothek zum Erstellen einer grundlegenden COM-Komponente und eine einfache Methode zum Registrieren und Verwenden der COM-Komponente aus einer Desktop-App verwendet wird.

[Gewusst wie: direktes Instanziieren von WRL-Komponenten](how-to-instantiate-wrl-components-directly.md)<br/>
Erfahren Sie, wie Sie mit den Funktionen [Microsoft::WRL::Make](make-function.md) und [Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md) eine Komponente aus dem Modul instanziieren, das sie definiert.

[Vorgehensweise: Verwenden von „winmdidl.exe“ und „midlrt.exe“ zum Erstellen von H-Dateien aus Windows-Metadaten](use-winmdidl-and-midlrt-to-create-h-files-from-windows-metadata.md)<br/>
Zeigt, wie benutzerdefinierte Komponenten für Windows-Runtime von WRL durch Erstellen einer IDL-Datei von den WINMD-Metadaten verarbeitet werden.

[Exemplarische Vorgehensweise: Herstellen einer Verbindung mithilfe von Aufgaben und XML-http](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md)<br/>
Zeigt, wie die [IXMLHTTPRequest2](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2) -und [IXMLHTTPRequest2Callback](/windows/win32/api/msxml6/nn-msxml6-ixmlhttprequest2callback) -Schnittstellen in Verbindung mit Aufgaben verwendet werden, um HTTP Get-und Post-Anforderungen an einen Webdienst in einer UWP-APP zu senden.

[Beispiel zu Bing Maps Trip Optimizer](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples)<br/>
Verwendet die `HttpRequest` -Klasse, die in Exemplarische Vorgehensweise [: Herstellen einer Verbindung mithilfe von Aufgaben und XML-HTTP-Anforderungen](../../parallel/concrt/walkthrough-connecting-using-tasks-and-xml-http-requests.md) im Kontext einer kompletten UWP-App definiert ist.

[Beispiel zum Erstellen einer Windows Runtime DLL-Komponente mit C++](https://github.com/Microsoft/VCSamples/tree/master/VC2012Samples/Windows%208%20samples/C%2B%2B/Windows%208%20app%20samples)<br/>
Zeigt, wie die Windows-Runtime C++-Vorlagen Bibliothek verwendet wird, um eine Prozess interne dll-Komponente zu erstellen und Sie aus C++/CX, JavaScript und c# zu nutzen.

[DirectX-Beispiel eines Murmellabyrinthspiels](/samples/microsoft/windows-appsample-marble-maze/directx-marble-maze-game-sample/)<br/>
Veranschaulicht, wie die Windows-Runtime C++-Vorlagen Bibliothek verwendet wird, um die Lebensdauer von COM-Komponenten wie DirectX und Media Foundation im Kontext eines kompletten 3D-Spiels zu verwalten.

[Popup Benachrichtigungen aus Desktop-Apps](/windows/uwp/design/shell/tiles-and-notifications/toast-desktop-apps)<br/>
Veranschaulicht, wie Popup Benachrichtigungen von einer Desktop-App gesendet werden.

## <a name="windows-runtime-c-template-library-compared-to-atl"></a>Windows-Runtime C++-Vorlagen Bibliothek im Vergleich zu ATL

Windows-Runtime C++-Vorlagen Bibliothek ähnelt der Active Template Library (ATL), da Sie Sie zum Erstellen kleiner, schneller COM-Objekte verwenden können. Windows-Runtime C++ Template Library und ATL teilen auch Konzepte wie die Definition von Objekten in Modulen, die explizite Registrierung von Schnittstellen und die offene Erstellung von Objekten mithilfe von Factorys. Wenn Sie mit ATL vertraut sind, können Sie mit Windows-Runtime C++ Template Library vertraut sein.

Windows-Runtime C++-Vorlagen Bibliothek unterstützt die für UWP-apps erforderliche com-Funktionalität. Daher unterscheidet sie sich von ATL, da die direkte Unterstützung für COM-Funktionen wie Folgende fehlt:

- aggregation

- vordefinierte Implementierungen

- duale Schnittstellen (`IDispatch`)

- Standardenumeratorschnittstellen

- Verbindungspunkte

- abtrennbare Schnittstellen

- OLE-Einbettung

- ActiveX-Steuerelemente

- COM+

## <a name="concepts"></a>Konzepte

Windows-Runtime C++-Vorlagen Bibliothek stellt Typen bereit, die einige grundlegende Konzepte darstellen. Im folgenden Abschnitt werden diese Typen beschrieben.

### <a name="comptr"></a>ComPtr

[ComPtr](comptr-class.md) ist ein Typ des *intelligenten Zeigermechanismus* , der die Schnittstelle darstellt, die vom Vorlagenparameter angegeben wird. Mit `ComPtr` deklarieren Sie eine Variable, die auf die Member eines Objekts zugreifen kann, das von der Schnittstelle abgeleitet wird. `ComPtr` verwaltet automatisch einen Verweiszähler für den zugrunde liegenden Schnittstellenzeiger und gibt die Schnittstelle frei, wenn der Verweiszähler auf null geht.

### <a name="runtimeclass"></a>RuntimeClass

[RuntimeClass](runtimeclass-class.md) stellt eine instanziierte Klasse dar, die einen Satz angegebener Schnittstellen erbt. Ein- `RuntimeClass` Objekt kann eine Kombination der Unterstützung für eine oder mehrere Windows-Runtime com-Schnittstellen oder einen schwachen Verweis auf eine Komponente bereitstellen.

### <a name="module"></a>Modul

[Module](module-class.md) stellt eine Auflistung von zugehörigen Objekten dar. Ein `Module` -Objekt verwaltet Klassenfactorys, die Objekte erstellen, und die Registrierung, die anderen Anwendungen die Verwendung eines Objekts ermöglicht.

### <a name="callback"></a>Rückruf

Die [Rückruf](callback-function-wrl.md) -Funktion erstellt ein Objekt, dessen Memberfunktion ein Ereignishandler ist (eine Rückrufmethode). Mit der `Callback` -Funktion schreiben Sie asynchrone Operationen.

### <a name="eventsource"></a>EventSource

Mit[EventSource](eventsource-class.md) verwalten Sie *Delegat* -Ereignishandler. Verwenden Sie Windows-Runtime C++-Vorlagen Bibliothek zum Implementieren eines Delegaten, und verwenden Sie, um Delegaten `EventSource` hinzuzufügen, zu entfernen und aufzurufen.

### <a name="asyncbase"></a>AsyncBase

[Asyncbase](asyncbase-class.md) stellt virtuelle Methoden bereit, die das Windows-Runtime asynchrone Programmiermodell darstellen. Überschreiben Sie die Member in dieser Klasse, um eine benutzerdefinierte Klasse zu erstellen, die einen asynchronen Vorgang starten, beenden oder seinen Fortschritt überprüfen kann.

### <a name="ftmbase"></a>FtmBase

[FtmBase](ftmbase-class.md) stellt ein Freethread-Marshaller-Objekt dar. `FtmBase` erstellt eine globale Schnittstellentabelle (GIT) und hilft bei der Verwaltung von Marshalling- und Proxyobjekten.

### <a name="weakref"></a>WeakRef

[WeakRef](weakref-class.md) ist ein Typ des intelligenten Zeigermechanismus, der einen *schwachen Verweis*auf ein Objekt darstellt, das möglicherweise zugänglich ist. Ein `WeakRef` -Objekt kann nur von der Windows-Runtime und nicht vom klassischen com verwendet werden.

Ein `WeakRef` -Objekt stellt in der Regel ein Objekt dar, dessen Vorhandensein von einem externen Thread oder einer externen Anwendung gesteuert wird. Beispielsweise kann ein `WeakRef` -Objekt auf ein Dateiobjekt verweisen. Wenn die Datei geöffnet ist, so ist `WeakRef` gültig, und die referenzierte Datei ist zugänglich. Wenn die Datei hingegen geschlossen ist, so ist `WeakRef` ungültig, und die Datei ist nicht zugänglich.

## <a name="related-topics"></a>Verwandte Themen

[Schlüssel-APIs nach Kategorie](key-wrl-apis-by-category.md)\
Hebt die primären Windows-Runtime C++-Vorlagen Bibliothekstypen,-Funktionen und-Makros hervor.

[Angabe](wrl-reference.md)\
Enthält Referenzinformationen für die Windows-Runtime C++-Vorlagen Bibliothek.

[Kurz Referenz (C++/CX)](../../cppcx/quick-reference-c-cx.md)\
Beschreibt kurz die C++/CX-Funktionen, die die Windows-Runtime unterstützen.

[Verwenden von Windows-Runtime Komponenten in Visual C++](/windows/uwp/winrt-components/walkthrough-creating-a-basic-windows-runtime-component-in-cpp-and-calling-it-from-javascript-or-csharp)\
Zeigt, wie Sie mit C++/CX eine grundlegende Windows-Runtime Komponente erstellen.

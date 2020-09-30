---
title: 'Vorgehensweise: Verwenden von vorhandenem C++-Code in einer UWP-App (Universelle Windows-Plattform)'
description: Möglichkeiten, vorhandene Code-apps und-Bibliotheken in universelle Windows-Plattform-apps zu verwenden.
ms.date: 09/04/2020
ms.assetid: 87e5818c-3081-42f3-a30d-3dca2cf0645c
ms.openlocfilehash: fd23c875d67654e96a828f4dba412dd74652912a
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503673"
---
# <a name="how-to-use-existing-c-code-in-a-universal-windows-platform-app"></a>Vorgehensweise: Verwenden von vorhandenem C++-Code in einer UWP-App (Universelle Windows-Plattform)

Es gibt verschiedene Möglichkeiten, wie vorhandener C++-Code in universelle Windows-Plattform (UWP)-Projekten verwendet werden kann. Einige Möglichkeiten erfordern nicht, dass Code neu kompiliert wird, wenn die Komponenten Erweiterungen (C++/CX) aktiviert sind (d. h. mit der `/ZW` -Option). Möglicherweise müssen Sie Code in Standard-C++ beibehalten oder eine klassische Win32-Kompilierungs Umgebung für Code beibehalten. Dies ist auch mit den entsprechenden Architektur Optionen möglich. Beachten Sie den gesamten Code, der UWP-Benutzeroberfläche und Typen enthält, die für c#, Visual Basic und JavaScript-Aufrufer verfügbar gemacht werden. Dieser Code sollte in Windows-App-Projekten und Windows-Runtime Komponenten Projekten vorliegen. Code, den Sie nur von C++ (einschließlich C++/CX) aus aufzurufen, kann sich in einem Projekt befinden, das mit der- `/ZW` Option oder einem standardmäßigen C++-Projekt kompiliert wird. Nur Binär Code, der keine unzulässigen APIs verwendet, kann verwendet werden, indem er in als statische Bibliothek verknüpft wird. Oder Sie können Sie mit der App als Inhalt Verpacken und in eine DLL laden.

Die vielleicht einfachste Möglichkeit, für die Ausführung Ihres Desktop-Programms in der UWP-Umgebung zu sorgen, ist der Einsatz von Desktop Bridge-Technologien. Dazu gehört der Desktop App Converter, der Ihre vorhandene Anwendung als UWP-App paketieren wird, ohne dass Codeänderungen erforderlich sind. Weitere Informationen finden Sie unter [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

Im weiteren Verlauf dieses Artikels wird erläutert, wie Sie C++-Bibliotheken (DLLs und statische Bibliotheken) auf die universelle Windows-Plattform portieren. Möglicherweise möchten Sie Ihren Code portieren, damit Ihre C++-Kern Logik mit mehreren UWP-Apps verwendet werden kann.

UWP-apps werden in einer geschützten Umgebung ausgeführt. Infolgedessen sind viele Win32-, com-und CRT-API-Aufrufe, die die Plattformsicherheit gefährden können, nicht zulässig. Mit der `/ZW` -Compileroption können solche Aufrufe erkannt und ein Fehler generiert werden. Sie können das zertifizierungskit für apps in Ihrer Anwendung verwenden, um Code zu erkennen, der unzulässige APIs aufruft. Weitere Informationen finden Sie unter [Zertifizierungskit für Windows-Apps](/windows/uwp/debug-test-perf/windows-app-certification-kit).

Wenn Quellcode für die Bibliothek verfügbar ist, können Sie versuchen, die unzulässigen API-Aufrufe auszuschließen. Eine Liste der nicht zulässigen APIs finden Sie unter [Win32-und com-APIs für UWP-apps](/uwp/win32-and-com/win32-and-com-for-uwp-apps) und CRT-Funktionen, die [in universelle Windows-Plattform-apps nicht unterstützt](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)werden. Einige Alternativen finden Sie unter [Alternatives to Windows APIs in UWP apps (Alternativen zu Windows-APIs in UWP-Apps)](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Wenn Sie nur versuchen, einen Verweis von einem universellen Windows-Projekt auf eine klassische Desktop Bibliothek hinzuzufügen, erhalten Sie eine Fehlermeldung, die besagt, dass die Bibliothek nicht kompatibel ist. Wenn es sich um eine statische Bibliothek handelt, können Sie eine Verknüpfung mit Ihrer Bibliothek herstellen, indem Sie die Bibliothek ( *`.lib`* Datei) Ihrer Linker-Eingabe auf die gleiche Weise wie in einer klassischen Win32-Anwendung hinzufügen. Wenn nur eine binäre Bibliothek verfügbar ist, ist dies die einzige Option. Eine statische Bibliothek wird mit der ausführbaren Datei Ihrer APP verknüpft. Eine Win32-DLL, die Sie in einer UWP-App verwenden, muss jedoch in der APP verpackt werden, indem Sie in das Projekt eingeschlossen und als Inhalt markiert wird. Wenn Sie eine Win32-DLL in eine UWP-App laden möchten, müssen Sie auch [`LoadPackagedLibrary`](/windows/win32/api/winbase/nf-winbase-loadpackagedlibrary) anstelle von `LoadLibrary` oder aufruft `LoadLibraryEx` .

Wenn Sie über Quellcode für die dll oder statische Bibliothek verfügen, können Sie Sie mithilfe der-Compileroption als UWP-Projekt neu kompilieren `/ZW` . Anschließend können Sie mithilfe des **Projektmappen-Explorer**einen Verweis darauf hinzufügen und in C++-UWP-Apps verwenden. Verknüpfen Sie die DLL mithilfe der Export Bibliothek.

Um Funktionalität für Aufrufer in anderen Sprachen verfügbar zu machen, können Sie die Bibliothek in eine Komponente für Windows-Runtime konvertieren. Windows-Runtime Komponenten unterscheiden sich von normalen DLLs insofern, als Sie Metadaten in Form von Dateien enthalten, die *`.winmd`* den Inhalt auf eine Weise beschreiben, die von .net-und JavaScript-Consumern benötigt wird.  Um API-Elemente für andere Sprachen verfügbar zu machen, können Sie C++/CX-Konstrukte hinzufügen, z. b. Verweis Klassen, und Sie als öffentlich festlegen. In Windows 10 und höher wird die [C++/WinRT-Bibliothek](https://github.com/microsoft/cppwinrt) anstelle von C++/CX. empfohlen.

Die vorherige Erörterung gilt nicht für COM-Komponenten, die anders behandelt werden müssen. Wenn Sie über einen com-Server in einer exe-oder DLL-Datei verfügen, können Sie ihn in einem universellen Windows-Projekt verwenden. Verpacken Sie diese als [com-Komponente ohne Registrierung](/windows/win32/sbscs/creating-registration-free-com-objects), fügen Sie Sie Ihrem Projekt als Inhalts Datei hinzu, und instanziieren Sie Sie mit [`CoCreateInstanceFromApp`](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstancefromapp) . Weitere Informationen finden Sie im Blogbeitrag [Using Free-COM DLL in Windows Store C++ Project (Verwenden von Free-COM-DLLs in Windows Store-C++-Projekten)](/archive/blogs/win8devsupport/using-free-com-dll-in-windows-store-c-project).

Wenn Sie eine vorhandene COM-Bibliothek auf die UWP portieren möchten, können Sie Sie auch in eine Windows-Runtime Komponente konvertieren. Wir empfehlen die C++/WinRT-Bibliothek für solche Ports, aber es ist auch möglich, die [Windows-Runtime C++ Template Library (WRL)](../cppcx/wrl/windows-runtime-cpp-template-library-wrl.md)zu verwenden. Die WRL ist veraltet und unterstützt nicht alle Funktionen von ATL und OLE. Ob ein solcher Port möglich ist, hängt von den Features von com, ATL und OLE ab, die für die Komponente erforderlich sind.

Unabhängig davon, welche Entwicklungsszenarien Sie auswählen, sollten Sie eine Reihe von Makro Definitionen beachten. Sie können diese Makros in Ihrem Code verwenden, um Code bedingt in den klassischen Desktop-Win32-und UWP-Code zu kompilieren.

```cpp
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
```

Diese Anweisungen gelten jeweils für UWP-Apps, Windows Phone Store-Apps, beide oder keines von beiden (nur klassische Win32-Desktop-Apps). Diese Makros sind nur in Windows SDK 8,1 und höher verfügbar.

Dieser Artikel enthält die folgenden Prozeduren:

- [Verwenden einer Win32-DLL in einer UWP-App](#BK_Win32DLL)

- [Verwenden einer nativen statischen C++-Bibliothek in einer UWP-App](#BK_StaticLib)

- [Portieren einer C++-Bibliothek auf eine Windows-Runtime Komponente](#BK_WinRTComponent)

## <a name="using-a-win32-dll-in-a-uwp-app"></a><a name="BK_Win32DLL"></a> Verwenden einer Win32-DLL in einer UWP-App

Zur Verbesserung der Sicherheit und Zuverlässigkeit werden universelle Windows-apps in einer eingeschränkten Laufzeitumgebung ausgeführt. Sie können eine native dll nicht so verwenden, wie Sie es in einer klassischen Windows-Desktop Anwendung tun würden. Wenn Sie über Quellcode für eine DLL verfügen, können Sie den Code so portieren, dass er unter UWP ausgeführt werden kann. Als Erstes ändern Sie einige Projekteinstellungen und Projektdatei-Metadaten, um das Projekt als UWP-Projekt zu identifizieren. Sie kompilieren den Bibliotheks Code mithilfe der Option neu `/ZW` , wodurch C++/CX. Bestimmte API-Aufrufe sind in UWP-apps aufgrund von strengeren Steuerelementen, die dieser Umgebung zugeordnet sind, nicht zulässig. Weitere Informationen finden Sie unter [Win32-und com-APIs für UWP-apps](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

Bei einer nativen DLL, die Funktionen mithilfe von `__declspec(dllexport)` exportiert, können Sie diese Funktionen aus einer UWP-App aufrufen, indem Sie die DLL als UWP-Projekt neu kompilieren. Angenommen, wir haben ein Win32-DLL-Projekt mit dem Namen *Giraffen* , das eine Reihe von Klassen und deren Methoden mit Code wie der folgenden Header Datei exportiert:

```cpp
// giraffe.h
// Define GIRAFFE_EXPORTS when building this DLL
#pragma once

#ifdef GIRAFFE_EXPORTS
#define GIRAFFE_API __declspec(dllexport)
#else
#define GIRAFFE_API
#endif

GIRAFFE_API int giraffeFunction();

class Giraffe
{
    int id;
        Giraffe(int id_in);
    friend class GiraffeFactory;

public:
    GIRAFFE_API int GetID();
};

class GiraffeFactory
{
    static int nextID;

public:
    GIRAFFE_API GiraffeFactory();
    GIRAFFE_API static int GetNextID();
    GIRAFFE_API static Giraffe* Create();
};
```

Und folgende Codedatei:

```cpp
// giraffe.cpp
#include "pch.h"
#include "giraffe.h"

Giraffe::Giraffe(int id_in) : id(id_in)
{
}

int Giraffe::GetID()
{
    return id;
}

int GiraffeFactory::nextID = 0;

GiraffeFactory::GiraffeFactory()
{
    nextID = 0;
}

int GiraffeFactory::GetNextID()
{
    return nextID;
}

Giraffe* GiraffeFactory::Create()
{
    return new Giraffe(nextID++);
}

int giraffeFunction();
```

Alles andere im Projekt ( *`pch.h`* , *`dllmain.cpp`* ) ist Teil der standardmäßigen Win32-Projektvorlage. Der Code definiert das Makro `GIRAFFE_API` , das in aufgelöst `__declspec(dllexport)` wird, wenn `GIRAFFE_EXPORTS` definiert ist. Das heißt, es wird definiert, wenn das Projekt als DLL erstellt wird, jedoch nicht, wenn ein Client den- *`giraffe.h`* Header verwendet. Diese DLL kann in einem UWP-Projekt verwendet werden, ohne den Quellcode zu ändern. Es müssen nur einige Projekteinstellungen und Eigenschaften geändert werden.

Das folgende Verfahren gilt, wenn Sie über eine native dll verfügen, die Funktionen mithilfe von verfügbar macht `__declspec(dllexport)` .

### <a name="to-port-a-native-dll-to-the-uwp-without-creating-a-new-project"></a>So portieren Sie eine systemeigene DLL auf UWP, ohne ein neues Projekt zu erstellen

1. Öffnen Sie das DLL-Projekt in Visual Studio.

1. Öffnen Sie die **Projekteigenschaften** für das DLL-Projekt, und legen Sie die **Konfiguration** auf **alle Konfigurationen**fest.

1. Legen Sie in den **Projekteigenschaften** unter **C/C++** > **Allgemein** (Registerkarte) die Option **Windows-Runtime-Erweiterung verwenden** auf **Yes (/ZW)** (Ja (/ZW)) fest. Diese Eigenschaft ermöglicht Komponenten Erweiterungen (C++/CX).

1. Wählen Sie in **Projektmappen-Explorer**den Projekt Knoten aus, öffnen Sie das Kontextmenü, und wählen Sie **Projekt entladen**aus. Öffnen Sie anschließend das Kontextmenü des entladenen Projektknotens, und klicken Sie dann auf die Option zum Bearbeiten der Projektdatei. Suchen Sie das Element `WindowsTargetPlatformVersion`, und ersetzen Sie es durch die folgenden Elemente.

    ```xml
    <AppContainerApplication>true</AppContainerApplication>
    <ApplicationType>Windows Store</ApplicationType>
    <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
    <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
    <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
    ```

   Schließen *`.vcxproj`* Sie die Datei, öffnen Sie das Kontextmenü erneut, und wählen Sie **Projekt erneut laden**aus.

   **Projektmappen-Explorer** identifiziert nun das Projekt als universelles Windows-Projekt.

1. Stellen Sie sicher, dass der Name der vorkompilierten Headerdatei richtig ist. Im Abschnitt **Vorkompilierte Header** müssen Sie möglicherweise die **Vorkompilierte Header Datei** von *`pch.h`* in oder umgekehrt ändern, *`stdafx.h`* Wenn ein Fehler wie der folgende angezeigt wird:

   > Fehler C2857: die mit der Befehlszeilenoption angegebene ' #include '-Anweisung **`/Ycpch.h`** wurde in der Quelldatei nicht gefunden.

   Das Problem besteht darin, dass für ältere Projektvorlagen eine andere Benennungs Konvention für die vorkompilierte Header Datei verwendet wird. Visual Studio 2019 und spätere Projekte verwenden *`pch.h`* .

1. Erstellen Sie das Projekt. Möglicherweise erhalten Sie Fehlermeldungen zu nicht kompatiblen Befehlszeilenoptionen. Die nun veraltete, aber häufig verwendete Option **Minimale Neuerstellung aktivieren** (/Gm) ist beispielsweise standardmäßig in vielen älteren C++-Projekten festgelegt und nicht mit `/ZW` kompatibel.

   Einige Funktionen sind nicht verfügbar, wenn Sie für die universelle Windows-Plattform kompilieren. Es werden Compilerfehler zu Problemen angezeigt. Beheben Sie diese Fehler, bis Sie über einen sauberen Build verfügen.

1. Wenn Sie die dll in einer UWP-app in der gleichen Projekt Mappe verwenden möchten, öffnen Sie das Kontextmenü für den UWP-Projekt Knoten, und wählen Sie Verweis **Hinzufügen**aus  >  **Reference**.

   Aktivieren Sie unter **Projekt**Mappe  >  **Solution**das Kontrollkästchen neben dem DLL-Projekt, und klicken Sie auf die Schaltfläche **OK** .

1. Schließen Sie die Header Datei (en) der Bibliothek in die Datei der UWP-App ein *`pch.h`* .

    ```cpp
    #include "..\Giraffe\giraffe.h"
    ```

1. Fügen Sie im UWP-Projekt wie gewohnt Code zum Aufrufen von Funktionen und Erstellen von Typen aus der DLL hinzu.

    ```cpp
    MainPage::MainPage()
    {
        InitializeComponent();
        GiraffeFactory gf;
        Giraffe* g = gf.Create();
        int id = g->GetID();
    }
    ```

## <a name="using-a-native-c-static-library-in-a-uwp-app"></a><a name="BK_StaticLib"></a> Verwenden einer nativen, statischen C++-Bibliothek in einer UWP-App

Sie können eine native statische C++-Bibliothek in einem UWP-Projekt verwenden, aber es gibt einige Einschränkungen zu beachten. Lesen Sie zunächst mehr zu [statischen Bibliotheken in C++/CX](../cppcx/static-libraries-c-cx.md). Sie können auf den nativen Code in Ihrer statischen Bibliothek aus Ihrer UWP-App zugreifen, aber es wird nicht empfohlen, öffentliche Verweistypen in einer solchen statischen Bibliothek zu erstellen. Wenn Sie eine statische Bibliothek mit der Option `/ZW` kompilieren, gibt der Bibliothekar (eigentlich der Linker) folgende Warnung aus:

> LNK4264: archiving object file compiled with /ZW into a static library; note that when authoring Windows Runtime types it is not recommended to link with a static library that contains Windows Runtime metadata (LNK4264: Mit /ZW kompilierte Objektdatei wird in einer statischen Bibliothek archiviert. Beachten Sie, dass beim Erstellen von Windows-Runtime-Typen das Verknüpfen mit einer statischen Bibliothek, die Windows-Runtime-Metadaten enthält, nicht empfohlen wird.)

Sie können jedoch eine statische Bibliothek in einer UWP-App verwenden, ohne Sie mit neu kompilieren zu müssen `/ZW` . Ihre Bibliothek kann keine Verweis Typen deklarieren oder C++/CX-Konstrukte verwenden. Wenn Sie jedoch nur eine Bibliothek mit System eigenem Code verwenden möchten, können Sie dies durchführen, indem Sie die folgenden Schritte ausführen.

### <a name="to-use-a-native-c-static-library-in-a-uwp-project"></a>So verwenden Sie eine systemeigene, statische C++-Bibliothek in einem UWP-Projekt

1. Wählen Sie in den Projekteigenschaften für das UWP-Projekt im linken Bereich **Konfigurations Eigenschaften**  >  **Linker**-  >  **Eingabe** aus. Fügen Sie im rechten Bereich der Eigenschaft **Zusätzliche Abhängigkeiten** den Pfad zur Bibliothek hinzu. Fügen Sie z. b. für eine Bibliothek im Projekt, die die Ausgabe in platziert *`<SolutionFolder>\Debug\MyNativeLibrary\MyNativeLibrary.lib`* , den relativen Pfad hinzu *`Debug\MyNativeLibrary\MyNativeLibrary.lib`* .

1. Fügen Sie eine include-Anweisung hinzu, um auf die Header Datei *`pch.h`* (falls vorhanden) oder in einer beliebigen Datei zu verweisen *`.cpp`* , und beginnen Sie mit dem Hinzufügen von Code, der die Bibliothek verwendet.

   ```cpp
   #include "..\MyNativeLibrary\MyNativeLibrary.h"
   ```

   Fügen Sie im Knoten **Verweise** in **Projektmappen-Explorer**keinen Verweis hinzu. Dieser Mechanismus funktioniert nur für Komponenten für Windows-Runtime.

## <a name="porting-a-c-library-to-a-windows-runtime-component"></a><a name="BK_WinRTComponent"></a> Portieren einer C++-Bibliothek in eine Komponente für Windows-Runtime

Angenommen, Sie möchten Native APIs in einer statischen Bibliothek aus einer UWP-App verwenden. Wenn Sie über den Quellcode für die systemeigene Bibliothek verfügen, können Sie den Code in eine Windows-Runtime Komponente portieren. Es handelt sich nicht mehr um eine statische Bibliothek. Sie werden Sie in eine DLL umwandeln, die Sie in jeder beliebigen C++ UWP-App verwenden können. In diesem Verfahren wird beschrieben, wie eine neue Windows-Runtime Komponente erstellt wird, die C++/CX-Erweiterungen verwendet. Weitere Informationen zum Erstellen einer Komponente, die C++/WinRT verwendet, finden Sie unter [Windows-Runtime Komponenten mit C++/WinRT](/windows/uwp/winrt-components/create-a-windows-runtime-component-in-cppwinrt).

Wenn Sie C++/CX verwenden, können Sie Verweis Typen und andere C++/CX-Konstrukte hinzufügen, die für Clients in beliebigen UWP-App-Codes verfügbar sind. Sie können auf diese Typen aus c#, Visual Basic oder JavaScript zugreifen. Die grundlegende Prozedur lautet wie folgt:

- Erstellen Sie ein Windows-Runtime Component-Projekt (Universal Windows).
- Kopieren Sie den Code für die statische Bibliothek hinein, und
- beheben Sie alle Fehler des Compilers, die von der-Option verursacht werden `/ZW` .

### <a name="to-port-a-c-library-to-a-windows-runtime-component"></a>So portieren Sie eine C++-Bibliothek in eine Komponente für Windows-Runtime

1. Erstellen Sie ein Windows-Runtime Component-Projekt (Universal Windows).

1. Schließen Sie das Projekt.

1. Suchen Sie im **Windows-Datei-Explorer**das neue Projekt. Suchen Sie dann das C++-Bibliotheksprojekt, das den Code enthält, den Sie portieren möchten. Kopieren Sie die Quelldateien (Header Dateien, Code Dateien und andere Ressourcen, einschließlich in Unterverzeichnissen) aus dem C++-Bibliotheksprojekt. Fügen Sie Sie in den neuen Projektordner ein, und stellen Sie sicher, dass die gleiche Ordnerstruktur beibehalten wird.

1. Öffnen Sie das Windows-Runtime Komponenten Projekt erneut. Öffnen Sie das Kontextmenü für den Projekt Knoten in **Projektmappen-Explorer**, und wählen Sie **Add**  >  **Vorhandenes Element**hinzufügen aus.

1. Wählen Sie alle Dateien aus, die Sie aus dem ursprünglichen Projekt hinzufügen möchten, und klicken Sie auf **OK**. Wiederholen Sie dies ggf. für Unterordner.

1. Möglicherweise ist der Code jetzt teilweise doppelt. Wenn mehr als ein vorkompilierter Header vorhanden ist (z.b. sowohl *`stdafx.h`* als auch *`pch.h`* ), wählen Sie einen aus, der beibehalten werden soll. Kopieren Sie allen erforderlichen Code, wie z. B. include-Anweisungen, in den beibehaltenen Header. Löschen Sie dann den anderen, und stellen Sie in den Projekteigenschaften unter **Vorkompilierte Header**sicher, dass der Name der Header Datei richtig ist.

   Wenn Sie die als vorkompilierten Header zu verwendende Datei geändert haben, überprüfen Sie, ob die Optionen für vorkompilierte Header für jede Datei korrekt sind. Wählen Sie nacheinander *`.cpp`* die einzelnen Dateien aus, öffnen Sie das Fenster Eigenschaften, und stellen Sie sicher, dass alle auf **verwenden (/Yu)** festgelegt sind, mit Ausnahme des vorkompilierten Headers, der auf **Create (/YC)** festgelegt werden sollte.

1. Erstellen Sie das Projekt, und beheben Sie alle Fehler. Diese Fehler können dadurch verursacht werden, dass `/ZW` Sie die Option verwenden, oder Sie können durch eine neue Version der Windows SDK verursacht werden. Oder Sie reflektieren möglicherweise Abhängigkeiten wie z. b. Header Dateien, von denen Ihre Bibliothek abhängt, oder Unterschiede in den Projekteinstellungen zwischen dem alten und dem neuen Projekt.

1. Fügen Sie Ihrem Projekt öffentliche Verweis Typen hinzu, oder konvertieren Sie normale Typen in Verweis Typen. Verwenden Sie diese Typen, um Einstiegspunkte in die Funktionalität verfügbar zu machen, die Sie von UWP-Apps aus abrufen möchten.

1. Testen Sie die Komponente, indem Sie in einem UWP-App-Projekt einen Verweis darauf erstellen, und fügen Sie Code zum Aufrufen der öffentlichen APIs hinzu, die Sie erstellt haben.

## <a name="see-also"></a>Weitere Informationen

[Portieren auf die universelle Windows-Plattform](../porting/porting-to-the-universal-windows-platform-cpp.md)

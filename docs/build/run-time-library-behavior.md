---
title: DLLs und Verhalten C++ der visuellen Lauf Zeit Bibliothek
ms.date: 08/19/2019
f1_keywords:
- _DllMainCRTStartup
- CRT_INIT
helpviewer_keywords:
- DLLs [C++], entry point function
- process detach [C++]
- process attach [C++]
- DLLs [C++], run-time library behavior
- DllMain function
- _CRT_INIT macro
- _DllMainCRTStartup method
- run-time [C++], DLL startup sequence
- DLLs [C++], startup sequence
ms.assetid: e06f24ab-6ca5-44ef-9857-aed0c6f049f2
ms.openlocfilehash: 572a0ba70c1ba2d46d2d9fd6d8ac543a77bbbc01
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422793"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>DLLs und Verhalten C++ der visuellen Lauf Zeit Bibliothek

Wenn Sie eine Dynamic Link Library (dll) mithilfe von Visual Studio erstellen, enthält der Linker standardmäßig die visuelle C++ Lauf Zeit Bibliothek (vcruntime). Die vcruntime enthält den Code, der zum Initialisieren und Beenden einerC++ C/ausführbaren Datei erforderlich ist. Beim Verknüpfen mit einer dll stellt der vcruntime-Code eine interne DLL-Einstiegspunkt Funktion mit dem Namen `_DllMainCRTStartup` bereit, die Windows-Betriebssystem Meldungen an die dll verarbeitet, die an einen Prozess oder Thread angefügt oder von diesem getrennt werden sollen. Die `_DllMainCRTStartup`-Funktion führt wichtige Aufgaben aus, z. b. das Einrichten von Stapelpuffer Sicherheit, die Initialisierung und Beendigung der C-Lauf Zeit Bibliothek (CRT) und Aufrufe von Konstruktoren und Debuggern für statische und globale Objekte. `_DllMainCRTStartup` ruft auch Hook-Funktionen für andere Bibliotheken wie WinRT, MFC und ATL auf, um eine eigene Initialisierung und Beendigung auszuführen. Ohne diese Initialisierung würden die CRT und andere Bibliotheken sowie die statischen Variablen in einem nicht initialisierten Zustand verbleiben. Die gleichen vcruntime-internen Initialisierungs-und Beendigungs Routinen werden aufgerufen, unabhängig davon, ob Ihre DLL eine statisch verknüpfte CRT oder eine dynamisch verknüpfte CRT-DLL verwendet.

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>Standard-DLL-Einstiegspunkt _DllMainCRTStartup

In Windows können alle DLLs eine optionale Einstiegspunkt Funktion enthalten, die in der Regel als `DllMain`bezeichnet wird, die für Initialisierung und Beendigung aufgerufen wird. Dadurch haben Sie die Möglichkeit, zusätzliche Ressourcen je nach Bedarf zu reservieren oder freizugeben. Windows ruft die Einstiegspunktfunktion in den folgenden vier Situationen auf: Anfügen an bzw. Trennen von einem Prozess und Anfügen an einen bzw. Trennen von einem Thread. Wenn eine DLL in einen Prozess Adressraum geladen wird, entweder wenn eine Anwendung, die Sie verwendet, geladen wird, oder wenn die Anwendung die dll zur Laufzeit anfordert, erstellt das Betriebssystem eine separate Kopie der DLL-Daten. Dies wird als *Prozess anfügen*bezeichnet. *Thread anfügen* tritt auf, wenn der Prozess, in den die dll geladen wird, einen neuen Thread erstellt. *Thread* Trennung tritt auf, wenn der Thread beendet wird, und der *Prozess trennt* , wenn die dll nicht mehr benötigt wird und von einer Anwendung freigegeben wird. Das Betriebssystem führt einen separaten Rückruf für den DLL-Einstiegspunkt für jedes dieser Ereignisse aus und übergibt *ein Argument für* jeden Ereignistyp. Beispielsweise sendet das Betriebssystem `DLL_PROCESS_ATTACH` *als Argument Argument* , um das Anfügen von Prozessen zu signalisieren.

Die vcruntime-Bibliothek stellt eine Einstiegspunkt Funktion mit dem Namen `_DllMainCRTStartup` bereit, um standardmäßige Initialisierungs-und Beendigungs Vorgänge zu verarbeiten. Bei der Prozess Anfügung richtet die `_DllMainCRTStartup`-Funktion Puffer Sicherheitsüberprüfungen ein, initialisiert die CRT und andere Bibliotheken, initialisiert Lauf Zeittyp Informationen, initialisiert und ruft Konstruktoren für statische und nicht lokale Daten auf, initialisiert den Thread lokalen Speicher, erhöht einen internen statischen Counter für jede Anfügung und ruft dann eine vom Benutzer oder Bibliothek bereitgestellte `DllMain`auf. Beim Prozess trennen durchläuft die Funktion diese Schritte in umgekehrter Reihenfolge. Er ruft `DllMain`auf, Dekremente den internen Wert, ruft Debuggerfunktionen auf, ruft CRT-Beendigungs Funktionen und registrierte `atexit` Funktionen auf und benachrichtigt alle anderen Bibliotheken der Beendigung. Wenn der Anlage Indikator null wechselt, gibt die Funktion `FALSE` zurück, um Windows anzuzeigen, dass die DLL entladen werden kann. Die `_DllMainCRTStartup`-Funktion wird auch beim Anfügen und trennen von Threads aufgerufen. In diesen Fällen führt der vcruntime-Code keine zusätzliche Initialisierung oder Beendigung aus und ruft nur `DllMain` auf, um die Nachricht zu übergeben. Wenn `DllMain` `FALSE` von der Prozess Anfügung zurückgibt, das Signal fehlschlägt `_DllMainCRTStartup`, werden `DllMain` erneut aufgerufen und `DLL_PROCESS_DETACH` als *Grund* Argument weitergegeben. Anschließend wird der restliche Beendigungs Prozess durchlaufen.

Beim Entwickeln von DLLs in Visual Studio wird der von vcruntime angegebene Standard Einstiegspunkt `_DllMainCRTStartup` automatisch verknüpft. Sie müssen keine Einstiegspunkt Funktion für die DLL angeben, indem Sie die Linkeroption [/Entry (Einstiegspunkt Symbol)](reference/entry-entry-point-symbol.md) verwenden.

> [!NOTE]
> Obwohl es möglich ist, mithilfe der/Entry: Linker-Option eine andere Einstiegspunkt Funktion für eine DLL anzugeben, wird Sie nicht empfohlen, da die Einstiegspunkt Funktion alles duplizieren muss, das `_DllMainCRTStartup` in derselben Reihenfolge tut. Die vcruntime stellt Funktionen bereit, die es Ihnen ermöglichen, das Verhalten zu duplizieren. Beispielsweise können Sie [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) sofort beim Anfügen von Prozessen aufzurufen, um die Puffer Überprüfungs Option [/GS (Buffer Security Check)](reference/gs-buffer-security-check.md) zu unterstützen. Sie können die `_CRT_INIT`-Funktion aufzurufen, indem Sie die gleichen Parameter wie die Einstiegspunkt Funktion übergeben, um die restlichen Funktionen der DLL-Initialisierung oder-Beendigung auszuführen.

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>Initialisieren einer DLL

Die dll verfügt möglicherweise über Initialisierungs Code, der beim Laden der DLL ausgeführt werden muss. Damit Sie Ihre eigenen dll-Initialisierungs-und Beendigungs Funktionen ausführen können, ruft `_DllMainCRTStartup` eine Funktion mit dem Namen `DllMain` auf, die Sie bereitstellen können. Für Ihre `DllMain` muss die erforderliche Signatur für einen DLL-Einstiegspunkt vorhanden sein. Die Standard-Einstiegspunkt Funktion `_DllMainCRTStartup` `DllMain` mit denselben von Windows über gebenden Parametern aufruft. Wenn Sie keine `DllMain` Funktion bereitstellen, stellt Visual Studio eine für Sie bereit und verknüpft Sie, sodass `_DllMainCRTStartup` immer etwas aufzurufen hat. Dies bedeutet Folgendes: Wenn Sie die dll nicht initialisieren müssen, müssen Sie bei der Erstellung der dll nichts Besonderes tun.

Dies ist die Signatur, die für `DllMain`verwendet wird:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

Einige Bibliotheken wrappen die `DllMain` Funktion. Implementieren Sie z. b. in einer regulären MFC-DLL die `InitInstance`-und `ExitInstance` Member-Funktionen des `CWinApp` Objekts, um die für die dll erforderliche Initialisierung und Beendigung auszuführen. Weitere Informationen finden Sie im Abschnitt [Initialisieren regulärer MFC-DLLs](#initializing-regular-dlls) .

> [!WARNING]
> Es gibt erhebliche Beschränkungen hinsichtlich der Sicherheit eines dll-Einstiegs Punkts. Weitere Informationen finden Sie unter [allgemeine bewährte Methoden](/windows/win32/Dlls/dynamic-link-library-best-practices) für bestimmte Windows-APIs, die in `DllMain`unsicher aufgerufen werden können. Wenn Sie etwas außer der einfachsten Initialisierung benötigen, führen Sie dies in einer Initialisierungsfunktion für die dll aus. Sie können erfordern, dass Anwendungen die Initialisierungsfunktion aufruft, nachdem `DllMain` ausgeführt wurde und bevor Sie andere Funktionen in der DLL aufruft.

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>Initialisieren von normalen DLLs (nicht-MFC)

Um Ihre eigene Initialisierung in normalen (nicht-MFC-DLLs) auszuführen, die die `_DllMainCRTStartup` Einstiegspunkt angegebene vcruntime-Angabe verwenden, muss der DLL-Quellcode eine Funktion mit dem Namen `DllMain`enthalten. Der folgende Code zeigt ein einfaches Gerüst, das zeigt, wie die Definition von `DllMain` aussehen könnte:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved)  // reserved
{
    // Perform actions based on the reason for calling.
    switch (reason)
    {
    case DLL_PROCESS_ATTACH:
        // Initialize once for each new process.
        // Return FALSE to fail DLL load.
        break;

    case DLL_THREAD_ATTACH:
        // Do thread-specific initialization.
        break;

    case DLL_THREAD_DETACH:
        // Do thread-specific cleanup.
        break;

    case DLL_PROCESS_DETACH:
        // Perform any necessary cleanup.
        break;
    }
    return TRUE;  // Successful DLL_PROCESS_ATTACH.
}
```

> [!NOTE]
> Ältere Windows SDK Dokumentation besagt, dass der tatsächliche Name der DLL-Einstiegspunkt Funktion in der Linker-Befehlszeile mit der/Entry-Option angegeben werden muss. In Visual Studio müssen Sie die Option/Entry nicht verwenden, wenn der Name der Einstiegspunkt Funktion `DllMain`ist. Wenn Sie die/Entry-Option verwenden und die Einstiegspunkt Funktion als `DllMain`benennen, wird die CRT nicht ordnungsgemäß initialisiert, es sei denn, die Einstiegspunkt Funktion führt dieselben Initialisierungs Aufrufe aus, die `_DllMainCRTStartup` vornimmt.

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>Reguläre MFC-DLLs initialisieren

Da reguläre MFC-DLLs über ein `CWinApp` Objekt verfügen, sollten Sie die Initialisierungs-und Beendigungs Aufgaben am gleichen Speicherort wie eine MFC-Anwendung ausführen: in den `InitInstance`-und `ExitInstance` Member-Funktionen der `CWinApp`von-abgeleiteten Klasse der dll. Da MFC eine `DllMain` Funktion bereitstellt, die von `_DllMainCRTStartup` für `DLL_PROCESS_ATTACH` und `DLL_PROCESS_DETACH`aufgerufen wird, sollten Sie keine eigene `DllMain` Funktion schreiben. Die von MFC bereitgestellte `DllMain` Funktion ruft `InitInstance` auf, wenn die dll geladen wird, und ruft `ExitInstance` vor dem Entladen der dll auf.

Eine reguläre MFC-DLL kann mehrere Threads nachverfolgen, indem Sie [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) und [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) in der `InitInstance`-Funktion aufrufen. Diese Funktionen ermöglichen es der dll, Thread spezifische Daten zu verfolgen.

In ihrer regulären MFC-DLL, die dynamisch mit MFC verknüpft ist, wenn Sie eine MFC-OLE-, MFC-Daten Bank (oder DAO) oder MFC-Socketunterstützung verwenden, werden die Debug-MFC-Erweiterungs-DLLs mfco*Version*d. dll, MFCD*Version*d. dll und mfcn*Version*d. dll (wobei *Version* die Versionsnummer ist) automatisch verknüpft. Sie müssen eine der folgenden vordefinierten Initialisierungs Funktionen für jede dieser DLLs, die Sie in ihrer regulären MFC-DLL-`CWinApp::InitInstance`verwenden, abrufen.

|MFC-Unterstützung|Aufzurufende Initialisierungsfunktion|
|-------------------------|-------------------------------------|
|MFC-OLE (mfco*Version*D. dll)|`AfxOleInitModule`|
|MFC-Datenbank (MFCD*Version*D. dll)|`AfxDbInitModule`|
|MFC-Sockets (mfcn*Version*D. dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>MFC-Erweiterungs-DLLs initialisieren

Da MFC-Erweiterungs-DLLs nicht über ein `CWinApp`von abgeleitetes Objekt verfügen (wie reguläre MFC-DLLs), sollten Sie den Initialisierungs-und Beendigungs Code der `DllMain`-Funktion hinzufügen, die der MFC-DLL-Assistent generiert.

Der Assistent stellt den folgenden Code für MFC-Erweiterungs-DLLs bereit. Im Code ist `PROJNAME` ein Platzhalter für den Namen des Projekts.

```cpp
#include "pch.h" // For Visual Studio 2017 and earlier, use "stdafx.h"
#include <afxdllx.h>

#ifdef _DEBUG
#define new DEBUG_NEW
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif
static AFX_EXTENSION_MODULE PROJNAMEDLL = { NULL, NULL };

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
   if (dwReason == DLL_PROCESS_ATTACH)
   {
      TRACE0("PROJNAME.DLL Initializing!\n");

      // MFC extension DLL one-time initialization
      AfxInitExtensionModule(PROJNAMEDLL,
                                 hInstance);

      // Insert this DLL into the resource chain
      new CDynLinkLibrary(Dll3DLL);
   }
   else if (dwReason == DLL_PROCESS_DETACH)
   {
      TRACE0("PROJNAME.DLL Terminating!\n");
   }
   return 1;   // ok
}
```

Beim Erstellen eines neuen `CDynLinkLibrary` Objekts während der Initialisierung kann die MFC-Erweiterungs-DLL `CRuntimeClass` Objekte oder Ressourcen in die Client Anwendung exportieren.

Wenn Sie die MFC-Erweiterungs-DLL aus einer oder mehreren regulären MFC-DLLs verwenden möchten, müssen Sie eine Initialisierungsfunktion exportieren, die ein `CDynLinkLibrary`-Objekt erstellt. Diese Funktion muss von allen regulären MFC-DLLs aufgerufen werden, die die MFC-Erweiterungs-DLL verwenden. Ein geeigneter Speicherort für diese Initialisierungsfunktion ist die `InitInstance` Member-Funktion des `CWinApp`abgeleiteten Objekts der regulären MFC-DLL, bevor die exportierten Klassen oder Funktionen der MFC-Erweiterungs-DLL verwendet werden.

In der `DllMain`, die vom MFC-DLL-Assistenten generiert wird, erfasst der Aufruf von `AfxInitExtensionModule` die Lauf Zeit Klassen des Moduls (`CRuntimeClass` Strukturen) sowie die zugehörigen objektfactorys (`COleObjectFactory` Objekte), die beim Erstellen des `CDynLinkLibrary` Objekts verwendet werden. Sie sollten den Rückgabewert von `AfxInitExtensionModule`überprüfen. Wenn ein Nullwert von `AfxInitExtensionModule`zurückgegeben wird, wird von der `DllMain`-Funktion NULL zurückgegeben.

Wenn Ihre MFC-Erweiterungs-DLL explizit mit einer ausführbaren Datei verknüpft wird (was bedeutet, dass die ausführbare Datei `AfxLoadLibrary`, um eine Verknüpfung mit der dll zu erhalten), sollten Sie einen Aufruf von `AfxTermExtensionModule` auf `DLL_PROCESS_DETACH`hinzufügen Diese Funktion ermöglicht MFC das Bereinigen der MFC-Erweiterungs-DLL, wenn jeder Prozess von der MFC-Erweiterungs-DLL trennt (was geschieht, wenn der Prozess beendet wird oder wenn die dll aufgrund eines `AfxFreeLibrary`-Aufrufes entladen wird). Wenn Ihre MFC-Erweiterungs-DLL implizit mit der Anwendung verknüpft wird, ist der `AfxTermExtensionModule`-Aufrufe nicht erforderlich.

Anwendungen, die explizit mit MFC-Erweiterungs-DLLs verknüpfen, müssen `AfxTermExtensionModule` beim Freigeben der DLL-Datei aufzurufen. Sie sollten auch `AfxLoadLibrary` und `AfxFreeLibrary` verwenden (anstelle der Win32-Funktionen `LoadLibrary` und `FreeLibrary`), wenn die Anwendung mehrere Threads verwendet. Die Verwendung von `AfxLoadLibrary` und `AfxFreeLibrary` stellt sicher, dass der Code zum Starten und Herunterfahren, der beim Laden und Entladen der MFC-Erweiterungs-DLL ausgeführt wird, den globalen MFC-Zustand nicht beschädigt.

Da die Datei MFCx0. dll vollständig initialisiert ist, wenn `DllMain` aufgerufen wird, können Sie Arbeitsspeicher zuweisen und MFC-Funktionen in `DllMain` aufrufen (im Gegensatz zur 16-Bit-Version von MFC).

Erweiterungs-DLLs können das Multithreading durchführen, indem Sie die `DLL_THREAD_ATTACH` und `DLL_THREAD_DETACH` Fälle in der `DllMain`-Funktion verarbeiten. Diese Fälle werden an `DllMain` übermittelt, wenn Threads die dll anfügen und trennen. Wenn Sie [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) aufrufen, wenn eine DLL angefügt wird, kann die dll lokale TLS-Indizes (Thread Local Storage) für jeden an die dll angefügten Thread verwalten.

Beachten Sie, dass die Header Datei Afxdllx. h spezielle Definitionen für Strukturen enthält, die in MFC-Erweiterungs-DLLs verwendet werden, wie z. b. die Definition für `AFX_EXTENSION_MODULE` und `CDynLinkLibrary`. Sie sollten diese Header Datei in der MFC-Erweiterungs-DLL einschließen.

> [!NOTE]
>  Es ist wichtig, dass Sie keines der `_AFX_NO_XXX` Makros in " *PCH. h* " ("*stdafx. h* " in Visual Studio 2017 und früher) definieren und nicht definieren. Diese Makros sind nur zum Zweck der Überprüfung vorhanden, ob eine bestimmte Zielplattform diese Funktion unterstützt. Sie können Ihr Programm schreiben, um diese Makros zu überprüfen (z. b. `#ifndef _AFX_NO_OLE_SUPPORT`), aber Ihr Programm sollte diese Makros nie definieren bzw. nicht definieren.

Eine Beispiel Initialisierungsfunktion, die Multithreading behandelt, ist in die [Verwendung von lokalem Thread Speicher in einer Dynamic Link Library](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library) im Windows SDK eingeschlossen. Beachten Sie, dass das Beispiel eine Einstiegspunkt Funktion mit dem Namen `LibMain`enthält. Sie sollten diese Funktion jedoch `DllMain`, damit Sie mit den MFC-und C-Laufzeitbibliotheken funktioniert.

## <a name="see-also"></a>Siehe auch

[Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)<br/>
[DllMain-Einstiegspunkt](/windows/win32/Dlls/dllmain)<br/>
[Bewährte Methoden für die Dynamic Link Library](/windows/win32/Dlls/dynamic-link-library-best-practices)

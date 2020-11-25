---
title: Verhalten der Laufzeitbibliothek für DLLs und Visual C++
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
ms.openlocfilehash: 5af3efd733a5d682e33863b330b6a558e824c9b3
ms.sourcegitcommit: 6284bca6549e7b4f199d4560c30df6c1278bd4a0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95782978"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Verhalten der Laufzeitbibliothek für DLLs und Visual C++

Wenn Sie eine DLL (Dynamic Link Library) mithilfe von Visual Studio erstellen, enthält der Linker standardmäßig die Visual C++-Laufzeitbibliothek (VCRuntime). Die VCRuntime-Bibliothek enthält Code, der zum Initialisieren und Beenden einer ausführbaren C-/C++-Datei benötigt wird. Wenn eine Verknüpfung mit einer DLL besteht, stellt der VCRuntime-Code eine interne DLL-Einstiegspunktfunktion namens `_DllMainCRTStartup` bereit, die Windows-Betriebssystemnachrichten an die DLL verarbeitet, um einen Prozess oder Thread anzufügen oder zu trennen. Die `_DllMainCRTStartup`-Funktion führt wichtige Aufgaben aus, z. B. das Einrichten der Stapelpuffersicherheit, das Initialisieren und Beenden der C-Laufzeitbibliothek (CRT) und das Aufrufen von Konstruktoren und Destruktoren für statische und globale Objekte. `_DllMainCRTStartup` ruft auch Hookfunktionen für andere Bibliotheken wie WinRT, MFC und ATL auf, um eine eigene Initialisierung und Beendigung durchzuführen. Ohne diese Initialisierung verbleiben die C-Laufzeitbibliothek und andere Bibliotheken sowie Ihre statischen Variablen in einem nicht initialisierten Zustand. Unabhängig davon, ob Ihre DLL eine statisch verknüpfte C-Laufzeitbibliothek oder eine dynamisch verknüpfte C-Laufzeitbibliothek-DLL verwendet, werden die gleichen internen Initialisierungs- und Beendigungsroutinen der VCRuntime-Bibliothek verwendet.

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>DLL-Standardeinstiegspunkt „_DllMainCRTStartup“

In Windows können alle DLLs eine optionale Einstiegspunktfunktion (in der Regel `DllMain`) enthalten, die sowohl für die Initialisierung als auch für die Beendigung aufgerufen wird. Dadurch haben Sie die Möglichkeit, zusätzliche Ressourcen je nach Bedarf zu reservieren oder freizugeben. Windows ruft die Einstiegspunktfunktion in den folgenden vier Situationen auf: Anfügen an bzw. Trennen von einem Prozess und Anfügen an einen bzw. Trennen von einem Thread. Sobald eine DLL in einen Prozessadressbereich geladen wird, entweder wenn eine Anwendung geladen wird, die sie verwendet, oder wenn die Anwendung die DLL zur Laufzeit anfordert, erstellt das Betriebssystem eine separate Kopie der DLL-Daten. Dies wird als *Prozessanfügung* bezeichnet. Die *Threadanfügung* erfolgt, wenn der Prozess, in den die DLL geladen wird, einen neuen Thread erstellt. Die *Threadtrennung* tritt auf, wenn der Thread beendet wird. Die *Prozesstrennung* tritt auf, wenn die DLL nicht mehr benötigt wird und von einer Anwendung freigegeben wird. Das Betriebssystem führt einen separaten Aufruf des DLL-Einstiegspunkts für jedes dieser Ereignisse durch und übergibt ein *reason*-Argument für jeden Ereignistyp. Das Betriebssystem sendet beispielsweise `DLL_PROCESS_ATTACH` als *reason*-Argument, um die Prozessanfügung zu signalisieren.

Die VCRuntime-Bibliothek stellt eine Einstiegspunktfunktion namens `_DllMainCRTStartup` bereit, um Standardinitialisierungsvorgänge und -beendigungsvorgänge zu verarbeiten. Bei der Prozessanfügung richtet die `_DllMainCRTStartup`-Funktion Puffersicherheitsüberprüfungen ein, initialisiert die C-Laufzeitbibliothek und andere Bibliotheken, initialisiert die Laufzeittypinformationen, initialisiert die Aufrufkonstruktoren für statische und nicht lokale Daten, initialisiert den lokalen Threadspeicher, inkrementiert einen internen statischen Zähler für jede Anfügung und ruft dann eine von einem Benutzer oder einer Bibliothek bereitgestellte `DllMain`-Funktion auf. Bei Prozesstrennung, durchläuft die Funktion diese Schritte in umgekehrter Reihenfolge. `DllMain` wird aufgerufen, der interne Zähler wird reduziert, Destruktoren werden aufgerufen, Beendigungsfunktionen werden für die C-Laufzeitbibliothek aufgerufen, registrierte `atexit`-Funktionen werden aufgerufen und alle anderen Bibliotheken werden über die Beendigung informiert. Wenn der Anfügungszähler auf null (0) fällt, gibt die Funktion `FALSE` zurück, um Windows darüber zu informieren, dass die DLL entladen werden kann. Die `_DllMainCRTStartup`-Funktion wird ebenfalls während der Threadanfügung und -trennung aufgerufen. In diesen Fällen führt der VCRuntime-Code keine zusätzliche Initialisierung oder Beendigung eigenständig durch und ruft lediglich `DllMain` auf, um die Nachricht weiterzuleiten. Wenn `DllMain` den Wert `FALSE` von der Prozessanfügung zurückgibt, um einen Fehler anzugeben, ruft `_DllMainCRTStartup` wieder `DllMain` auf, übergibt `DLL_PROCESS_DETACH` als *reason*-Argument und durchläuft dann den Rest des Beendigungsprozesses.

Beim Erstellen von DLLs in Visual Studio wird der Standardeinstiegspunkt `_DllMainCRTStartup` automatisch verknüpft, der von der VCRuntime-Bibliothek bereitgestellt wird. Sie müssen keine Einstiegspunktfunktion für Ihre DLL mit der Linkeroption [/ENTRY (Einstiegspunktsymbol)](reference/entry-entry-point-symbol.md) festlegen.

> [!NOTE]
> Es ist zwar möglich, eine andere Einstiegspunktfunktion für eine DLL mit der Linkeroption „/ENTRY“ festzulegen, aber davon wird abgeraten, da Ihre Einstiegspunktfunktion alle Aktionen von `_DllMainCRTStartup` duplizieren in derselben Reihenfolge müsste. Die VCRuntime-Bibliothek stellt Funktionen bereit, mit denen Sie das Verhalten duplizieren können. Beispielsweise können Sie [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) direkt bei der Prozessanfügung aufrufen, um die Pufferüberprüfungsoption [/GS (Puffersicherheitsüberprüfung)](reference/gs-buffer-security-check.md) zu unterstützen. Sie können die `_CRT_INIT`-Funktion aufrufen und dieselben Parameter als Einstiegspunktfunktion übergeben, um die restlichen DLL-Initialisierungs- oder -Beendigungsfunktionen auszuführen.

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>Initialisieren einer DLL

Ihre DLL verfügt möglicherweise über Initialisierungscode, der beim Laden der DLL ausgeführt werden muss. Damit Sie Ihre eigenen DLL-Initialisierungs- und -Beendigungsfunktionen ausführen können, ruft `_DllMainCRTStartup` eine Funktion namens `DllMain` auf, die Sie bereitstellen können. Ihre `DllMain`-Funktion muss über die für einen DLL-Einstiegspunkt erforderliche Signatur verfügen. Die Standard-Einstiegspunktfunktion `_DllMainCRTStartup` ruft `DllMain` mit denselben Parametern auf, die von Windows übergeben werden. Wenn Sie keine `DllMain`-Funktion angeben, stellt Visual Studio standardmäßig eine bereit und verknüpft diese, sodass `_DllMainCRTStartup` immer eine Funktion aufrufen kann. Das bedeutet, dass Sie beim Erstellen Ihrer DLL keine weiteren Schritte ausführen müssen, wenn Sie Ihre DLL nicht initialisieren müssen.

Die folgende Signatur wird für `DllMain` verwendet:

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

Einige Bibliotheken umschließen die `DllMain`-Funktion für Sie. Implementieren Sie in einer regulärer MFC-DLL beispielsweise die Memberfunktionen `InitInstance` und `ExitInstance` des `CWinApp`-Objekts, um die für Ihre DLL erforderliche Initialisierung und Beendigung durchzuführen. Weitere Informationen finden Sie im Abschnitt [Initialisieren regulärer MFC-DLLs](#initializing-regular-dlls).

> [!WARNING]
> Es gibt erhebliche Einschränkungen bei den Aktionen, die Sie sicher in einem DLL-Einstiegspunkt durchführen können. Informationen über spezifische Windows-APIs, die nicht sicher in `DllMain` aufgerufen werden können, finden Sie unter [Allgemeine bewährte Methoden](/windows/win32/Dlls/dynamic-link-library-best-practices). Wenn Sie mehr als nur die einfachste Initialisierung durchführen müssen, führen Sie dies in einer Initialisierungsfunktion für die DLL durch. Sie können erfordern, dass Anwendungen die Initialisierungsfunktion aufrufen, nachdem `DllMain` ausgeführt wurde und bevor sie andere Funktionen in der DLL aufrufen.

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>Initialisieren herkömmlicher DLLs (nicht MFC)

Ihr DLL-Quellcode muss eine Funktion namens `DllMain` enthalten, damit Sie Ihre eigene Initialisierung in herkömmlichen DLLs (nicht MFC) durchführen können, die den von der VCRuntime-Bibliothek bereitgestellten `_DllMainCRTStartup`-Einstiegspunkt verwenden. Der folgende Code stellt ein Grundgerüst dar, das veranschaulicht, wie die Definition von `DllMain` aussehen könnte:

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
> Laut älterer Dokumentation zum Windows SDK muss der tatsächliche Name der DLL-Einstiegspunktfunktion für die Linkerbefehlszeile mit der Option „/ENTRY“ festgelegt werden. In Visual Studio müssen Sie die Option „/ENTRY“ nicht verwenden, wenn der Name Ihrer Einstiegspunktfunktion `DllMain` ist. Tatsächlich wird die C-Laufzeitbibliothek nicht ordnungsgemäß initialisiert, wenn Sie die Option „/ENTRY“ verwenden und Ihrer Einstiegspunktfunktion einen anderen Namen als `DllMain` geben, es sei denn, Ihre Einstiegspunktfunktion führt die selben Initialisierungsaufrufe aus, die `_DllMainCRTStartup` ausführt.

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>Initialisieren regulärer MFC-DLLs

Da reguläre MFC-DLLs ein `CWinApp`-Objekt enthalten, sollten sie ihre Initialisierungs- und Beendigungsaufgaben am selben Ort wie eine MFC-Anwendung durchführen: in den Memberfunktionen `InitInstance` und `ExitInstance` der von `CWinApp` abgeleiteten Klasse der DLL. Da MFC eine `DllMain`-Funktion bereitstellt, die von `_DllMainCRTStartup` für `DLL_PROCESS_ATTACH` und `DLL_PROCESS_DETACH` aufgerufen wird, sollten Sie nicht Ihre eigene `DllMain`-Funktion schreiben. Die von MFC bereitgestellte `DllMain`-Funktion ruft `InitInstance` auf, wenn Ihre DLL geladen wird, und ruft `ExitInstance` auf, bevor die DLL entladen wird.

Eine reguläre MFC-DLL kann mehrere Threads nachverfolgen, indem [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) und [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) in der `InitInstance`-Funktion aufgerufen werden. Diese Funktionen ermöglichen der DLL die Nachverfolgung von threadspezifischen Daten.

In Ihrer regulären MFC-DLL, die dynamisch mit MFC verknüpft wird, wenn Sie MFC-Unterstützung für OLE, Datenbanken (oder DAO) oder Sockets verwenden, werden die MFC-Erweiterungs-DLLs „MFCO *version* D.dll“, „MFCD *version* D.dll“ und „MFCN *version* D.dll“ (wobei *version* der Versionsnummer entspricht) automatisch verknüpft. Sie müssen eine der folgenden vordefinierten Initialisierungsfunktionen für jede dieser DLLs aufrufen, die Sie in der `CWinApp::InitInstance`-Methode Ihrer regulären MFC-DLL verwenden.

|Typ der MFC-Unterstützung|Aufzurufende Initialisierungsfunktion|
|-------------------------|-------------------------------------|
|MFC-OLE (MFCO *version* D.dll)|`AfxOleInitModule`|
|MFC-Datenbank (MFCD *version* D.dll)|`AfxDbInitModule`|
|MFC-Sockets (MFCN *version* D.dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>Initialisieren von MFC-Erweiterungs-DLLs

Da MFC-Erweiterungs-DLLs über kein von `CWinApp` abgeleitetes Objekt verfügen (wie reguläre MFC-DLLs), sollten Sie Ihren Initialisierungs- und Beendigungscode zur `DllMain`-Funktion hinzufügen, die der MFC-DLL-Assistent generiert.

Der Assistent stellt den folgenden Code für MFC-Erweiterungs-DLLs bereit. Im Code ist `PROJNAME` ein Platzhalter für den Namen Ihres Projekts.

```cpp
#include "pch.h" // For Visual Studio 2017 and earlier, use "stdafx.h"
#include <afxdllx.h>

#ifdef _DEBUG
#define new DEBUG_NEW
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif
static AFX_EXTENSION_MODULE PROJNAMEDLL;

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

Durch die Erstellung eines neuen `CDynLinkLibrary`-Objekts während der Initialisierung kann die MFC-Erweiterungs-DLL `CRuntimeClass`-Objekte oder Ressourcen in die Clientanwendung exportieren.

Wenn Sie Ihre MFC-Erweiterungs-DLL über mindestens eine reguläre MFC-DLL verwenden, müssen Sie eine Initialisierungsfunktion exportieren, die ein `CDynLinkLibrary`-Objekt erstellt. Die Funktion muss von allen regulären MFC-DLLs aufgerufen werden, die die MFC-Erweiterungs-DLL verwenden. Die `InitInstance`-Memberfunktion des von `CWinApp` abgeleiteten Objekts der regulären MFC-DLL bietet sich dafür an, diese Initialisierungsfunktion aufzurufen, bevor andere exportierte Klassen oder Funktionen der MFC-Erweiterungs-DLL verwendet werden.

In der `DllMain`-Funktion, die der MFC-DLL-Assistent generiert, erfasst der Aufruf von `AfxInitExtensionModule` die Laufzeitklassen des Moduls (`CRuntimeClass`-Strukturen) sowie die Objektfactorys (`COleObjectFactory`-Objekte), die beim Erstellen des `CDynLinkLibrary`-Objekts verwendet werden. Sie sollten den Rückgabewert von `AfxInitExtensionModule` überprüfen. Wenn `AfxInitExtensionModule` den Wert null (0) zurückgibt, geben Sie null in Ihrer `DllMain`-Funktion zurück.

Wenn Ihre MFC-Erweiterungs-DLL explizit mit einer ausführbaren Datei verknüpft wird (d. h. die ausführbare Datei ruft `AfxLoadLibrary` für die Verknüpfung mit der DLL auf), sollten Sie einen Aufruf von `AfxTermExtensionModule` bei `DLL_PROCESS_DETACH` hinzufügen. Mithilfe dieser Funktion kann MFC die MFC-Erweiterungs-DLL bereinigen, wenn einzelne Prozesse von der MFC-Erweiterungs-DLL getrennt werden (dies geschieht, wenn der Prozess beendet wird oder die DLL aufgrund eines `AfxFreeLibrary`-Aufrufs entladen wird). Wenn Ihre MFC-Erweiterungs-DLL implizit mit der Anwendung verknüpft wird, ist der Aufruf von `AfxTermExtensionModule` nicht erforderlich.

Anwendungen, die explizit mit MFC-Erweiterungs-DLLs verknüpft werden, müssen `AfxTermExtensionModule` beim Freigeben der DLL aufrufen. Außerdem sollten sie `AfxLoadLibrary` und `AfxFreeLibrary` (anstelle der Win32-Funktionen `LoadLibrary` und `FreeLibrary`) verwenden, wenn die Anwendung mehrere Threads nutzt. Mit `AfxLoadLibrary` und `AfxFreeLibrary` wird sichergestellt, dass der Start- und Beendigungscode nicht den globalen MFC-Zustand beschädigt, wenn die MFC-Erweiterungs-DLL geladen und entladen wird.

Da die „MFCx0.dll“ bereits vollständig initialisiert ist, wenn `DllMain` aufgerufen wird, können Sie Speicher zuweisen und MFC-Funktionen in `DllMain` aufrufen (im Gegensatz zur 16-Bit-Version von MFC).

Erweiterungs-DLLs können das Multithreading durchführen, indem sie die Fälle `DLL_THREAD_ATTACH` und `DLL_THREAD_DETACH` in der `DllMain`-Funktion verarbeiten. Diese Fälle werden an `DllMain` übergeben, wenn Threads angefügt oder von der DLL getrennt werden. Durch Aufrufen von [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) beim Anfügen einer DLL, kann die DLL TLS-Indizes (Thread Local Storage, threadlokaler Speicher) für jeden Thread verwalten, der an die DLL angefügt ist.

Beachten Sie, dass die Headerdatei „Afxdllx.h“ besondere Definitionen für Strukturen enthält, die in MFC-Erweiterungs-DLLs verwendet werden, z. B. die Definition für `AFX_EXTENSION_MODULE` und `CDynLinkLibrary`. Sie sollten diese Headerdatei in Ihre MFC-Erweiterungs-DLL einschließen.

> [!NOTE]
> Es ist wichtig, dass Sie die `_AFX_NO_XXX`-Makros in *pch.h* (*stdafx.h* in Visual Studio 2017 und früher) weder definieren noch ihre Definition aufgeben. Diese Makros sind lediglich dafür vorgesehen, zu überprüfen, ob eine bestimmte Zielplattform das Feature unterstützt oder nicht. Sie können Ihr Programm so schreiben, dass es diese Makros überprüft (z. B. `#ifndef _AFX_NO_OLE_SUPPORT`), jedoch sollte Ihr Programm diese Makros nie definieren und ihre Definition nie aufgeben.

Eine Beispielinitialisierungsfunktion, die Multithreading verarbeitet, finden Sie unter [Verwenden des threadlokalen Speichers in einer Dynamic Link Library](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library) im Windows SDK. Beachten Sie, dass das Beispiel eine Einstiegspunktfunktion namens `LibMain` enthält, jedoch sollten Sie diese Funktion `DllMain` nennen, damit sie im Zusammenhang mit den MFC- und C-Laufzeitbibliotheken funktioniert.

## <a name="see-also"></a>Siehe auch

[Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)<br/>
[DllMain-Einstiegspunkt](/windows/win32/Dlls/dllmain)<br/>
[Bewährte Methoden zur Verwendung von Dynamic Link Librarys](/windows/win32/Dlls/dynamic-link-library-best-practices)

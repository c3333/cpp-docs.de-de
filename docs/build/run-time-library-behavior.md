---
title: DLLs and Visual C++ run-time library behavior (Verhalten der Laufzeitbibliothek für DLLs und Visual C++)
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
ms.openlocfilehash: 2f2ffb13e6a80b144298bbf8cd76b5666a10b4dd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335664"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>DLLs and Visual C++ run-time library behavior (Verhalten der Laufzeitbibliothek für DLLs und Visual C++)

Wenn Sie eine Dynamic-Link-Bibliothek (DLL) mithilfe von Visual Studio erstellen, enthält der Linker standardmäßig die Visual C++-Laufzeitbibliothek (VCRuntime). Die VCRuntime enthält Code, der zum Initialisieren und Beenden einer ausführbaren C/C++-Datei erforderlich ist. Wenn der VCRuntime-Code mit einer DLL verknüpft ist, `_DllMainCRTStartup` stellt er eine interne DLL-Einstiegspunktfunktion bereit, die Windows-Betriebssystemnachrichten an die DLL verarbeitet, um sie an einen Prozess oder Thread anzuhängen oder von ihm zu trennen. Die `_DllMainCRTStartup` Funktion führt wichtige Aufgaben wie die Einrichtung der Stapelpuffersicherheit, die Initialisierung und Beendigung der C-Laufzeitbibliothek (CRT) sowie Aufrufe von Konstruktoren und Destruktoren für statische und globale Objekte aus. `_DllMainCRTStartup`ruft auch Hook-Funktionen für andere Bibliotheken wie WinRT, MFC und ATL auf, um ihre eigene Initialisierung und Beendigung durchzuführen. Ohne diese Initialisierung würden die CRT und andere Bibliotheken sowie Ihre statischen Variablen in einem nicht initialisierten Zustand belassen. Dieselben internen VCRuntime-Initialisierungs- und Beendigungsroutinen werden aufgerufen, unabhängig davon, ob Ihre DLL eine statisch verknüpfte CRT oder eine dynamisch verknüpfte CRT-DLL verwendet.

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>Standard-DLL-Einstiegspunkt _DllMainCRTStartup

In Windows können alle DLLs eine optionale Einstiegsfunktion enthalten, die normalerweise als , bezeichnet `DllMain`wird und sowohl zur Initialisierung als auch zur Beendigung aufgerufen wird. Dadurch haben Sie die Möglichkeit, zusätzliche Ressourcen je nach Bedarf zu reservieren oder freizugeben. Windows ruft die Einstiegspunktfunktion in den folgenden vier Situationen auf: Anfügen an bzw. Trennen von einem Prozess und Anfügen an einen bzw. Trennen von einem Thread. Wenn eine DLL in einen Prozessadressraum geladen wird, entweder wenn eine Anwendung, die sie verwendet, geladen wird oder wenn die Anwendung die DLL zur Laufzeit anfordert, erstellt das Betriebssystem eine separate Kopie der DLL-Daten. Dies wird als *Prozessanhang*bezeichnet. *Thread-Anfügen* tritt auf, wenn der Prozess, in den die DLL geladen wird, einen neuen Thread erstellt. *Threadablösung* tritt auf, wenn der Thread beendet wird, und *die Prozesstrennung* erfolgt, wenn die DLL nicht mehr erforderlich ist und von einer Anwendung freigegeben wird. Das Betriebssystem führt für jedes dieser Ereignisse einen separaten Aufruf des DLL-Einstiegspunkts durch und übergibt ein *Ursachenargument* für jeden Ereignistyp. Beispielsweise sendet `DLL_PROCESS_ATTACH` das Betriebssystem als *Grundargument* zum Signalprozessanfügen.

Die VCRuntime-Bibliothek stellt eine `_DllMainCRTStartup` Einstiegsfunktion bereit, die aufgerufen wird, um standardmäßige Initialisierungs- und Beendigungsvorgänge zu verarbeiten. Beim Prozessanfügen `_DllMainCRTStartup` richtet die Funktion Puffersicherheitsprüfungen ein, initialisiert die CRT und andere Bibliotheken, initialisiert Laufzeittypinformationen, initialisiert und ruft Konstruktoren für statische und nicht lokale Daten auf, initialisiert threadlokalen Speicher, erhöht einen internen statischen Zähler für jeden Anhang und ruft dann eine von Benutzern oder Bibliothek bereitgestellte `DllMain`. Beim Prozesslösen durchläuft die Funktion diese Schritte umgekehrt. Es `DllMain`ruft auf , dekrementiert den internen Zähler, ruft Destruktoren auf, ruft CRT-Beendigungsfunktionen und registrierte `atexit` Funktionen auf und benachrichtigt alle anderen Bibliotheken über die Beendigung. Wenn der Anlagenzähler auf Null `FALSE` geht, kehrt die Funktion zurück, um Windows anzuzeigen, dass die DLL entladen werden kann. Die `_DllMainCRTStartup` Funktion wird auch beim Anfügen des Gewindes und beim Trennen des Gewindes aufgerufen. In diesen Fällen führt der VCRuntime-Code keine zusätzliche Initialisierung `DllMain` oder Beendigung aus eigener Kraft durch und ruft nur auf, die Nachricht weiterzugeben. Wenn `DllMain` `FALSE` das Zurückkehren vom Prozess `_DllMainCRTStartup` `DllMain` anfügt, `DLL_PROCESS_DETACH` ein Signalfehler, ein erneuter Anruf und das *Grundargument,* dann den Rest des Beendigungsprozesses durchläuft.

Beim Erstellen von DLLs in Visual `_DllMainCRTStartup` Studio wird der von VCRuntime bereitgestellte Standardeinstiegspunkt automatisch verknüpft. Sie müssen keine Einstiegspunktfunktion für Ihre DLL angeben, indem Sie die Linkeroption [/ENTRY (Entry Point Symbol)](reference/entry-entry-point-symbol.md) verwenden.

> [!NOTE]
> Es ist zwar möglich, eine andere Einstiegspunktfunktion für eine DLL mithilfe der Linkeroption /ENTRY: anzugeben, wir empfehlen `_DllMainCRTStartup` dies jedoch nicht, da Ihre Einstiegspunktfunktion alles, was dies tut, in der gleichen Reihenfolge duplizieren müsste. DIE VCRuntime bietet Funktionen, mit denen Sie ihr Verhalten duplizieren können. Sie können z. B. [__security_init_cookie](../c-runtime-library/reference/security-init-cookie.md) sofort beim Prozessanfügen aufrufen, um die [Pufferüberprüfungsoption /GS (Buffer Security Check)](reference/gs-buffer-security-check.md) zu unterstützen. Sie können `_CRT_INIT` die Funktion aufrufen und dieselben Parameter wie die Einstiegspunktfunktion übergeben, um die restlichen DLL-Initialisierungs- oder Beendigungsfunktionen auszuführen.

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>Initialisieren einer DLL

Ihre DLL hat möglicherweise Initialisierungscode, der ausgeführt werden muss, wenn die DLL geladen wird. Damit Sie Ihre eigenen DLL-Initialisierungs- `_DllMainCRTStartup` und Beendigungsfunktionen ausführen können, ruft eine Funktion namens `DllMain` "You" auf. Sie `DllMain` müssen über die Fürsatonie für einen DLL-Einstiegspunkt verfügen. Die Standard-Einstiegspunktfunktion `_DllMainCRTStartup` ruft `DllMain` die gleichen Parameter an, die von Windows übergeben werden. Wenn Sie keine `DllMain` Funktion bereitstellen, stellt Visual Studio standardmäßig eine Funktion `_DllMainCRTStartup` bereit und verknüpft sie, sodass immer etwas zum Aufrufen verwendet wird. Dies bedeutet, dass, wenn Sie Ihre DLL nicht initialisieren müssen, nichts Besonderes beim Erstellen Ihrer DLL zu tun ist.

Dies ist die `DllMain`Signatur, die für :

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

Einige Bibliotheken `DllMain` umschließen die Funktion für Sie. Implementieren Sie beispielsweise in einer regulären `CWinApp` MFC-DLL die Funktionen des Objekts und `InitInstance` `ExitInstance` des Members, um die Initialisierung und Beendigung auszuführen, die für Ihre DLL erforderlich sind. Weitere Informationen finden Sie im Abschnitt [Initialisieren regelmäßiger MFC-DLLs.For](#initializing-regular-dlls) more details, see the Initialize regular MFC DLLs section.

> [!WARNING]
> Es gibt erhebliche Einschränkungen für das, was Sie in einem DLL-Einstiegspunkt sicher tun können. Weitere Informationen finden Sie unter [Allgemeine bewährte Methoden](/windows/win32/Dlls/dynamic-link-library-best-practices) `DllMain`für bestimmte Windows-APIs, die nicht sicher aufzurufen sind. Wenn Sie etwas anderes als die einfachste Initialisierung benötigen, dann tun Sie dies in einer Initialisierungsfunktion für die DLL. Sie können verlangen, dass Anwendungen `DllMain` die Initialisierungsfunktion aufrufen, nachdem sie ausgeführt wurden und bevor sie andere Funktionen in der DLL aufrufen.

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>Initialisieren gewöhnlicher (nicht-MFC) DLLs

Um eine eigene Initialisierung in normalen (nicht-MFC)-DLLs durchzuführen, die den von VCRuntime bereitgestellten `_DllMainCRTStartup` Einstiegspunkt verwenden, muss Ihr DLL-Quellcode eine Funktion namens `DllMain`enthalten. Der folgende Code zeigt ein grundlegendes `DllMain` Skelett, das zeigt, wie die Definition aussehen könnte:

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
> Ältere Windows SDK-Dokumentation besagt, dass der tatsächliche Name der DLL-Einstiegspunktfunktion in der Linker-Befehlszeile mit der Option /ENTRY angegeben werden muss. Mit Visual Studio müssen Sie die Option /ENTRY nicht verwenden, wenn `DllMain`der Name Ihrer Einstiegspunktfunktion lautet. Wenn Sie die Option /ENTRY verwenden und Ihre Einstiegspunktfunktion anders benennen als `DllMain`, wird die CRT nicht ordnungsgemäß initialisiert, es sei denn, Ihre Einstiegspunktfunktion führt dieselben Initialisierungsaufrufe aus, die `_DllMainCRTStartup` sie ausführt.

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>Initialisieren regulärer MFC-DLLs

Da normale MFC-DLLs über `CWinApp` ein Objekt verfügen, sollten sie ihre Initialisierungs- und `InitInstance` `ExitInstance` Beendigungsaufgaben am gleichen `CWinApp`Speicherort wie eine MFC-Anwendung ausführen: in den und Memberfunktionen der dLL-abgeleiteten Klasse. Da MFC `DllMain` eine Funktion bereitstellt, `DLL_PROCESS_ATTACH` `DLL_PROCESS_DETACH`die von `_DllMainCRTStartup` for und `DllMain` aufgerufen wird, sollten Sie keine eigene Funktion schreiben. Die von MFC `DllMain` `InitInstance` bereitgestellte Funktion ruft auf, `ExitInstance` wenn Ihre DLL geladen wird und sie aufruft, bevor die DLL entladen wird.

Eine reguläre MFC-DLL kann mehrere Threads verfolgen, indem [tlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) und [TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue) in ihrer `InitInstance` Funktion aufgerufen werden. Mit diesen Funktionen kann die DLL threadspezifische Daten nachverfolgen.

Wenn Sie in Ihrer regulären MFC-DLL, die dynamisch mit MFC verknüpft ist, MFC OLE, MFC Database (oder DAO) oder MFC Sockets unterstützen, werden die Debug-MFC-Erweiterungs-DLLs MFCO-Version D.dll, MFCD-Version D.dll und MFCN-Version D.dll (wobei *Version* die Versionsnummer ist) automatisch verknüpft.*version**version**version* Sie müssen eine der folgenden vordefinierten Initialisierungsfunktionen für jede dieser DLLs aufrufen, die `CWinApp::InitInstance`Sie in Ihrer regulären MFC-DLL verwenden.

|Typ der MFC-Unterstützung|Initialisierungsfunktion zum Aufrufen|
|-------------------------|-------------------------------------|
|MFC OLE (MFCO*version*D.dll)|`AfxOleInitModule`|
|MFC-Datenbank *(MFCD-Version*D.dll)|`AfxDbInitModule`|
|MFC-Sockel *(MFCN-Version*D.dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>Initialisieren von MFC-Erweiterungs-DLLs

Da MFC-Erweiterungs-DLLs `CWinApp`nicht über ein -derived-Objekt verfügen (wie normale MFC-DLLs), sollten Sie der `DllMain` Funktion, die der MFC-DLL-Assistent generiert, Initialisierungs- und Beendigungscode hinzufügen.

Der Assistent stellt den folgenden Code für MFC-Erweiterungs-DLLs bereit. Im Code `PROJNAME` ist ein Platzhalter für den Namen Ihres Projekts.

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

Durch das `CDynLinkLibrary` Erstellen eines neuen Objekts während der `CRuntimeClass` Initialisierung kann die MFC-Erweiterungs-DLL Objekte oder Ressourcen in die Clientanwendung exportieren.

Wenn Sie Ihre MFC-Erweiterungs-DLL aus einer oder mehreren regulären MFC-DLLs `CDynLinkLibrary` verwenden möchten, müssen Sie eine Initialisierungsfunktion exportieren, die ein Objekt erstellt. Diese Funktion muss von jeder der regulären MFC-DLLs aufgerufen werden, die die MFC-Erweiterungs-DLL verwenden. Ein geeigneter Ort zum Aufrufen dieser `InitInstance` Initialisierungsfunktion ist die Memberfunktion `CWinApp`des regulären MFC-DLL-abgeleiteten Objekts, bevor eine der exportierten Klassen oder Funktionen der MFC-Erweiterungs-DLL verwendet wird.

In `DllMain` dem, das der MFC-DLL-Assistent generiert, wird der `AfxInitExtensionModule` Aufruf`CRuntimeClass` zum Erfassen der Laufzeitklassen`COleObjectFactory` (Strukturen) des `CDynLinkLibrary` Moduls sowie seiner Objektfabriken (Objekte) für die Verwendung beim Erstellen des Objekts verwendet. Sie sollten den Rückgabewert von überprüfen; `AfxInitExtensionModule` Wenn ein Nullwert `AfxInitExtensionModule`von zurückgegeben wird, geben Sie Null von Ihrer `DllMain` Funktion zurück.

Wenn Ihre MFC-Erweiterungs-DLL explizit mit einer ausführbaren Datei verknüpft wird (d. h. die ausführbaren Aufrufe `AfxLoadLibrary` zum Verknüpfen mit der DLL), sollten Sie einen Aufruf von `AfxTermExtensionModule` auf hinzufügen. `DLL_PROCESS_DETACH` Diese Funktion ermöglicht mFC das Bereinigen der MFC-Erweiterungs-DLL, wenn sich jeder Prozess von der MFC-Erweiterungs-DLL löst `AfxFreeLibrary` (was geschieht, wenn der Prozess beendet wird oder wenn die DLL als Ergebnis eines Aufrufs entladen wird). Wenn Ihre MFC-Erweiterungs-DLL implizit mit der `AfxTermExtensionModule` Anwendung verknüpft wird, ist der Aufruf nicht erforderlich.

Anwendungen, die explizit eine Verknüpfung mit `AfxTermExtensionModule` MFC-Erweiterungs-DLLs herstellen, müssen beim Freilassen der DLL aufrufen. Sie sollten `AfxLoadLibrary` auch `AfxFreeLibrary` verwenden und (anstelle `LoadLibrary` der `FreeLibrary`Win32-Funktionen und ) wenn die Anwendung mehrere Threads verwendet. Verwenden `AfxLoadLibrary` `AfxFreeLibrary` und stellt sicher, dass der Start- und Herunterfahrcode, der ausgeführt wird, wenn die MFC-Erweiterungs-DLL geladen und entladen wird, den globalen MFC-Status nicht beschädigt.

Da MFCx0.dll vollständig initialisiert ist, wenn der Zeitpunkt `DllMain` aufgerufen wird, `DllMain` können Sie Speicher zuweisen und MFC-Funktionen innerhalb aufrufen (im Gegensatz zur 16-Bit-Version von MFC).

Erweiterungs-DLLs können sich um Multithreading kümmern, indem sie die `DLL_THREAD_ATTACH` und `DLL_THREAD_DETACH` die Fälle in der `DllMain` Funktion bearbeiten. Diese Fälle werden `DllMain` an den Zeitpunkt übergeben, an den Threads anfügen und von der DLL trennen. Wenn [TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc) aufgerufen wird, wenn eine DLL angefügt wird, kann die DLL TLS-Indizes (Thread Local Storage) für jeden Thread verwalten, der an die DLL angefügt ist.

Beachten Sie, dass die Headerdatei Afxdllx.h spezielle Definitionen für Strukturen enthält, `AFX_EXTENSION_MODULE` `CDynLinkLibrary`die in MFC-Erweiterungs-DLLs verwendet werden, z. B. die Definition für und . Sie sollten diese Headerdatei in Ihre MFC-Erweiterungs-DLL aufnehmen.

> [!NOTE]
> Es ist wichtig, dass Sie keines `_AFX_NO_XXX` der Makros in *pch.h* (*stdafx.h* in Visual Studio 2017 und früher) definieren oder undefinieren. Diese Makros existieren nur zum Zweck der Überprüfung, ob eine bestimmte Zielplattform diese Funktion unterstützt oder nicht. Sie können Ihr Programm schreiben, um diese `#ifndef _AFX_NO_OLE_SUPPORT`Makros zu überprüfen (z. B. ), aber Ihr Programm sollte diese Makros niemals definieren oder aufdefinieren.

Eine Beispielinitialisierungsfunktion, die Multithreading verarbeitet, ist in der Verwendung des [lokalen Threadspeichers in einer Dynamic-Link-Bibliothek](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library) im Windows SDK enthalten. Beachten Sie, dass das Beispiel `LibMain`eine Einstiegspunktfunktion `DllMain` namens enthält, Sie sollten diese Funktion jedoch benennen, damit sie mit den MFC- und C-Laufzeitbibliotheken funktioniert.

## <a name="see-also"></a>Siehe auch

[Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)<br/>
[DllMain-Einstiegspunkt](/windows/win32/Dlls/dllmain)<br/>
[Best Practices für Dynamic-Link-Bibliotheken](/windows/win32/Dlls/dynamic-link-library-best-practices)

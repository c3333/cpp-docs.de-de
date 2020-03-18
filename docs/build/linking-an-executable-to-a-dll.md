---
title: Eine ausführbare Datei mit einer DLL verknüpfen
ms.date: 08/22/2019
helpviewer_keywords:
- run time [C++], linking
- dynamic load linking [C++]
- linking [C++], DLLs
- DLLs [C++], linking
- implicit linking [C++]
- explicit linking [C++]
- executable files [C++], linking to DLLs
- loading DLLs [C++]
ms.assetid: 7592e276-dd6e-4a74-90c8-e1ee35598ea3
ms.openlocfilehash: 2f907fedcaaf9897749ee0eb6a7ea5a33e1af679
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422835"
---
# <a name="link-an-executable-to-a-dll"></a>Eine ausführbare Datei mit einer DLL verknüpfen

Eine ausführbare Datei kann mit einer DLL durch eine der folgenden Methoden verknüpft werden (bzw. diese laden):

- *Implizites verknüpfen*, bei dem das Betriebssystem die dll zur gleichen Zeit lädt wie die ausführbare Datei, die Sie verwendet. Die ausführbare Client Datei ruft die exportierten Funktionen der dll auf dieselbe Weise auf wie die Funktionen, die statisch verknüpft sind und in der ausführbaren Datei enthalten sind. Implizites verknüpfen wird manchmal als *statisches Laden* oder *dynamisches Verknüpfen der Ladezeit*bezeichnet.

- *Explizites verknüpfen*, bei dem das Betriebssystem die dll bei Bedarf zur Laufzeit lädt. Eine ausführbare Datei, die eine DLL durch explizites verknüpfen verwendet, muss die dll explizit laden und entladen. Außerdem muss ein Funktionszeiger für den Zugriff auf jede Funktion eingerichtet werden, die er aus der dll verwendet. Anders als Aufrufe von Funktionen in einer statisch verknüpften Bibliothek oder einer implizit verknüpften DLL muss die ausführbare Client Datei die exportierten Funktionen in einer explizit verknüpften DLL über Funktionszeiger aufrufen. Explizites verknüpfen wird manchmal als *dynamische Auslastung* oder *Lauf Zeit dynamische Verknüpfung*bezeichnet.

Eine ausführbare Datei kann eine der beiden Verknüpfungs Methoden verwenden, um eine Verknüpfung mit der gleichen dll Außerdem schließen sich diese Methoden nicht gegenseitig aus. eine ausführbare Datei kann implizit mit einer DLL verknüpft werden, und eine andere kann explizit an Sie angehängt werden.

<a name="determining-which-linking-method-to-use"></a>

## <a name="determine-which-linking-method-to-use"></a>Ermitteln, welche Verknüpfungsmethode verwendet werden soll

Ob implizites verknüpfen oder explizite Verknüpfungen verwendet werden müssen, ist eine architektonische Entscheidung, die Sie für Ihre Anwendung treffen müssen. Jede Methode weist Vor- und Nachteile auf.

### <a name="implicit-linking"></a>Implizite Verknüpfung

Implizites verknüpfen tritt auf, wenn der Code einer Anwendung eine exportierte DLL-Funktion aufruft. Beim Kompilieren oder Assemblieren des Quellcodes für die aufrufende ausführbare Datei wird durch den DLL-Funktionsaufruf ein Verweis auf eine externe Funktion im Objektcode generiert. Um diesen externen Verweis aufzulösen, muss die Anwendung mit der Importbibliothek (LIB-Datei) verknüpft werden, die vom Ersteller der DLL bereitgestellt wird.

Die Importbibliothek enthält nur Code zum Laden der DLL sowie zum Implementieren von Funktionsaufrufen in der DLL. Wenn in einer Importbibliothek eine externe Funktion gefunden wird, wird der Linker informiert, dass der Code für diese Funktion in einer DLL enthalten ist. Um externe Verweise auf DLLs aufzulösen, fügt der Linker der ausführbaren Datei einfach Informationen hinzu. Dadurch wird dem System mitgeteilt, wo der DLL-Code zu finden ist, wenn der Prozess startet.

Wenn vom System ein Programm gestartet wird, das dynamisch verknüpfte Verweise enthält, verwendet es die Informationen in der ausführbaren Programmdatei, um die benötigten DLLs zu finden. Wenn die dll nicht gefunden werden kann, beendet das System den Prozess und zeigt ein Dialogfeld an, das den Fehler meldet. Andernfalls ordnet das System die dll-Module dem Prozess Adressraum zu.

Wenn eine der DLLs über eine Einstiegspunkt Funktion für Initialisierungs-und Beendigungs Code verfügt, z. b. `DllMain`, ruft das Betriebssystem die Funktion auf. Über einen der Parameter, die an die Einstiegspunktfunktion übergeben werden, wird Code definiert, der angibt, dass die DLL an den Prozess angefügt wird. Wenn die Einstiegspunkt Funktion nicht "true" zurückgibt, beendet das System den Prozess und meldet den Fehler.

Schließlich ändert das System den ausführbaren Code des Prozesses, um Startadressen für die DLL-Funktionen bereitzustellen.

Wie der Rest des Programmcodes ordnet das Lade Programm den DLL-Code dem Adressraum des Prozesses zu, wenn der Prozess gestartet wird. Das Betriebssystem lädt es nur bei Bedarf in den Arbeitsspeicher. Folglich haben die `PRELOAD`-und `LOADONCALL` Code Attribute, die von DEF-Dateien zum Steuern des Ladens in früheren Windows-Versionen verwendet werden, keine Bedeutung mehr.

### <a name="explicit-linking"></a>Explizite Verknüpfung

Die meisten Anwendungen verwenden implizites verknüpfen, da es sich hierbei um die einfachste Verknüpfungs Methode handelt. Es gibt jedoch Situationen, in denen die explizite Verknüpfung erforderlich ist. Die folgenden Gründe sprechen häufig für die explizite Verknüpfung:

- Die Anwendung kennt den Namen einer DLL, die Sie zum Zeitpunkt der Laufzeit lädt. Die Anwendung kann z. b. den Namen der dll und der exportierten Funktionen beim Start aus einer Konfigurationsdatei abrufen.

- Ein Prozess, der implizites verknüpfen verwendet, wird vom Betriebssystem beendet, wenn die dll beim Prozessstart nicht gefunden wird. Ein Prozess, bei dem explizite Verknüpfungen verwendet werden, wird in dieser Situation nicht beendet, und es kann versucht werden, den Fehler zu beheben. So könnte der Prozess z. B. dem Benutzer den Fehler melden und ihn veranlassen, einen anderen Pfad für die DLL anzugeben.

- Ein Prozess, der implizites verknüpfen verwendet, wird auch beendet, wenn eine der DLLs, mit denen er verknüpft ist, eine `DllMain` Funktion hat, die fehlschlägt. Ein Prozess, bei dem explizite Verknüpfungen verwendet werden, wird in dieser Situation nicht beendet.

- Eine Anwendung, die implizit mit zahlreichen DLLs verknüpft ist, wird u. U. langsam gestartet, da von Windows neben der Anwendung auch alle DLLs geladen werden. Um die Startleistung zu verbessern, verwendet eine Anwendung möglicherweise nur implizite Verknüpfungen für DLLs, die unmittelbar nach dem Laden erforderlich sind Die explizite Verknüpfung kann verwendet werden, um andere DLLs nur dann zu laden, wenn Sie benötigt werden.

- Bei der expliziten Verknüpfung entfällt die Notwendigkeit, die Anwendung mit einer Import Bibliothek zu verknüpfen. Wenn Änderungen in der dll bewirken, dass die Export Ordinalzahlen geändert werden, müssen Anwendungen nicht erneut verknüpft werden, wenn Sie `GetProcAddress` mit dem Namen einer Funktion und nicht mit einem Ordinalwert aufruft. Anwendungen, die implizites verknüpfen verwenden, müssen weiterhin mit der geänderten Import Bibliothek verknüpft werden.

Beachten Sie die beiden folgenden Schwachstellen im Zusammenhang mit der expliziten Verknüpfung:

- Wenn die dll über eine `DllMain` Einstiegspunkt Funktion verfügt, ruft das Betriebssystem die Funktion im Kontext des Threads auf, der `LoadLibrary`aufgerufen hat. Die Einstiegspunkt Funktion wird nicht aufgerufen, wenn die DLL bereits an den Prozess angefügt wurde, weil ein vorheriger Aufruf von `LoadLibrary`, der über keinen entsprechenden Aufruf der `FreeLibrary`-Funktion verfügt. Explizites verknüpfen kann Probleme verursachen, wenn die DLL eine `DllMain` Funktion verwendet, um jeden Thread eines Prozesses zu initialisieren, da alle Threads, die bereits vorhanden sind, wenn `LoadLibrary` (oder `AfxLoadLibrary`) aufgerufen wird, nicht initialisiert werden.

- Wenn eine DLL statische Blockdaten als `__declspec(thread)`deklariert, kann dies zu einem Schutz Fehler führen, wenn diese explizit verknüpft ist. Nachdem die dll durch einen Aufruf von `LoadLibrary`geladen wurde, verursacht Sie einen Schutz Fehler, wenn der Code auf diese Daten verweist. (Statische Blockdaten umfassen sowohl globale als auch lokale statische Elemente.) Daher sollten Sie beim Erstellen einer DLL die Verwendung des lokalen Thread Speichers vermeiden. Wenn dies nicht möglich ist, informieren Sie Ihre DLL-Benutzer über die möglichen Fehler beim dynamischen Laden der dll. Weitere Informationen finden Sie unter [Verwenden von lokalem Thread Speicher in einer Dynamic Link Library (Windows SDK)](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library).

<a name="linking-implicitly"></a>

## <a name="how-to-use-implicit-linking"></a>Verwenden impliziter Verknüpfungen

Um eine DLL durch implizites verknüpfen verwenden zu können, müssen ausführbare Client Dateien diese Dateien vom Anbieter der dll abrufen:

- Eine oder mehrere Header Dateien (. h-Dateien), die die Deklarationen der exportierten Daten, Funktionen C++ und Klassen in der dll enthalten. Die von der DLL exportierten Klassen, Funktionen und Daten müssen in der Header Datei als `__declspec(dllimport)` gekennzeichnet werden. Weitere Informationen finden Sie unter [dllexport, dllimport](../cpp/dllexport-dllimport.md).

- Eine Import Bibliothek, die mit Ihrer ausführbaren Datei verknüpft werden soll. Der Linker erstellt die Import Bibliothek, wenn die dll erstellt wird. Weitere Informationen finden Sie unter [lib-Dateien als Eingabe](reference/dot-lib-files-as-linker-input.md)für den Linker.

- Die tatsächliche dll-Datei.

Um die Daten, Funktionen und Klassen in einer DLL durch implizites verknüpfen zu verwenden, muss jede Client Quelldatei die Header Dateien enthalten, die Sie deklarieren. Aus Codierungs Sicht entsprechen Aufrufe der exportierten Funktionen wie jeder andere Funktionsaufruf.

Um die ausführbare Client Datei zu erstellen, müssen Sie eine Verknüpfung mit der Import Bibliothek der dll herstellen. Wenn Sie ein externes Makefile-oder Buildsystem verwenden, geben Sie die Import Bibliothek zusammen mit den anderen Objektdateien oder Bibliotheken an, die Sie verknüpfen.

Das Betriebssystem muss in der Lage sein, die DLL-Datei beim Laden der aufrufenden ausführbaren Datei zu lokalisieren. Dies bedeutet, dass Sie bei der Installation der Anwendung entweder das vorhanden sein der DLL bereitstellen oder überprüfen müssen.

<a name="linking-explicitly"></a>

## <a name="how-to-link-explicitly-to-a-dll"></a>Explizites verknüpfen mit einer dll

Um eine DLL durch explizites verknüpfen verwenden zu können, müssen Anwendungen einen Funktionsaufruf durchführen, um die dll zur Laufzeit explizit zu laden. Für die explizite Verknüpfung mit einer DLL muss eine Anwendung folgende Schritte ausführen:

- Rufen Sie [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) oder eine ähnliche Funktion zum Laden der dll und zum Abrufen eines Modul Handles auf.

- Rufen Sie [GetProcAddress](getprocaddress.md) auf, um einen Funktionszeiger auf jede exportierte Funktion zu erhalten, die die Anwendung aufruft. Da Anwendungen die DLL-Funktionen über einen Zeiger aufzurufen, generiert der Compiler keine externen Verweise, sodass keine Verknüpfung mit einer Import Bibliothek erforderlich ist. Sie müssen jedoch über eine `typedef`-oder `using`-Anweisung verfügen, die die von Ihnen aufzurufende Rückruf Signatur der exportierten Funktionen definiert.

- Rufen Sie [FreeLibrary](freelibrary-and-afxfreelibrary.md) auf, wenn Sie mit der dll abgeschlossen sind.

Diese Beispiel Funktion ruft beispielsweise `LoadLibrary` auf, um eine DLL mit dem Namen "myDll" zu laden, ruft `GetProcAddress` auf, um einen Zeiger auf eine Funktion mit dem Namen "DLLFunc1" zu erhalten, ruft die Funktion auf und speichert das Ergebnis und ruft dann `FreeLibrary` auf, um die dll zu entladen.

```C
#include "windows.h"

typedef HRESULT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT*);

HRESULT LoadAndCallSomeFunction(DWORD dwParam1, UINT * puParam2)
{
    HINSTANCE hDLL;               // Handle to DLL
    LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer
    HRESULT hrReturnVal;

    hDLL = LoadLibrary("MyDLL");
    if (NULL != hDLL)
    {
        lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL, "DLLFunc1");
        if (NULL != lpfnDllFunc1)
        {
            // call the function
            hrReturnVal = lpfnDllFunc1(dwParam1, puParam2);
        }
        else
        {
            // report the error
            hrReturnVal = ERROR_DELAY_LOAD_FAILED;
        }
        FreeLibrary(hDLL);
    }
    else
    {
        hrReturnVal = ERROR_DELAY_LOAD_FAILED;
    }
    return hrReturnVal;
}
```

Im Gegensatz zu diesem Beispiel sollten Sie in den meisten Fällen `LoadLibrary` und nur einmal in der Anwendung für eine bestimmte dll `FreeLibrary`. Dies trifft vor allem dann zu, wenn Sie mehrere Funktionen in der DLL aufrufen oder DLL-Funktionen wiederholt aufrufen.

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Arbeiten mit Importbibliotheken und Exportdateien](reference/working-with-import-libraries-and-export-files.md)

- [Such Reihenfolge der Dynamic Link Library](/windows/win32/Dlls/dynamic-link-library-search-order)

## <a name="see-also"></a>Siehe auch

[Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)

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
ms.openlocfilehash: 0cd9cfa32e6f87479dfcd9926b1735671ff6690f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223940"
---
# <a name="link-an-executable-to-a-dll"></a>Eine ausführbare Datei mit einer DLL verknüpfen

Eine ausführbare Datei kann mit einer DLL durch eine der folgenden Methoden verknüpft werden (bzw. diese laden):

- *Implizite Verknüpfung*. Dabei lädt das Betriebssystem die DLL zur selben Zeit wie die ausführbare Datei, die sie verwendet. Die ausführbare Clientdatei ruft die exportierten Funktionen der DLL auf dieselbe Weise auf, wie wenn die Funktionen statisch verknüpft und in der ausführbaren Datei enthalten wären. Das implizite Verknüpfen wird gelegentlich auch als *statisches Laden* oder *dynamisches Verknüpfen zur Ladezeit* bezeichnet.

- *Explizite Verknüpfung*. Hierbei lädt das Betriebssystem die DLL bei Bedarf zur Laufzeit. Eine ausführbare Datei, die eine DLL verwendet, indem eine explizite Verknüpfung hergestellt wird, muss die DLL explizit laden und entladen. Außerdem muss ein Funktionszeiger eingerichtet werden, um auf die einzelnen Funktionen zuzugreifen, die in der DLL verwendet werden. Im Gegensatz zu Funktionsaufrufen in einer statisch verknüpften Bibliothek oder implizit verknüpften DLL muss die ausführbare Clientdatei die exportierten Funktionen in einer explizit verknüpften DLL über Funktionszeiger aufrufen. Die explizite Verknüpfung wird gelegentlich auch als *dynamisches Laden* oder *dynamisches Verknüpfen zur Laufzeit* bezeichnet.

Eine ausführbare Datei kann jede dieser beiden Verknüpfungsmethoden verwenden, um eine Verknüpfung zur selben DLL herzustellen. Außerdem schließen sich diese Methoden gegenseitig aus. Eine ausführbare Datei kann eine implizite Verknüpfung zu einer DLL herstellen, und eine andere könnten explizit mit ihr verknüpft sein.

<a name="determining-which-linking-method-to-use"></a>

## <a name="determine-which-linking-method-to-use"></a>Ermitteln, welche Verknüpfungsmethode verwendet werden soll

Ob implizite oder explizite Verknüpfung verwendet wird, ist eine architektonische Entscheidung, die Sie für Ihre Anwendung treffen müssen. Jede Methode weist Vor- und Nachteile auf.

### <a name="implicit-linking"></a>Implizite Verknüpfung

Die implizite Verknüpfung findet statt, wenn der Code einer Anwendung eine exportierte DLL-Funktion aufruft. Beim Kompilieren oder Assemblieren des Quellcodes für die aufrufende ausführbare Datei wird durch den DLL-Funktionsaufruf ein Verweis auf eine externe Funktion im Objektcode generiert. Um diesen externen Verweis aufzulösen, muss die Anwendung mit der Importbibliothek (LIB-Datei) verknüpft werden, die vom Ersteller der DLL bereitgestellt wird.

Die Importbibliothek enthält nur Code zum Laden der DLL sowie zum Implementieren von Funktionsaufrufen in der DLL. Wenn in einer Importbibliothek eine externe Funktion gefunden wird, wird der Linker informiert, dass der Code für diese Funktion in einer DLL enthalten ist. Um externe Verweise auf DLLs aufzulösen, fügt der Linker der ausführbaren Datei einfach Informationen hinzu. Dadurch wird dem System mitgeteilt, wo der DLL-Code zu finden ist, wenn der Prozess startet.

Wenn vom System ein Programm gestartet wird, das dynamisch verknüpfte Verweise enthält, verwendet es die Informationen in der ausführbaren Programmdatei, um die benötigten DLLs zu finden. Wird die DLL nicht gefunden, beendet das System den Prozess und zeigt ein Dialogfeld mit einer entsprechenden Fehlermeldung an. Andernfalls ordnet das System die DLL-Module im Adressbereich des Prozesses zu.

Wenn eine der DLLs über eine Einstiegspunktfunktion für Initialisierungs- und Terminierungscode wie `DllMain` verfügt, ruft das Betriebssystem die Funktion auf. Über einen der Parameter, die an die Einstiegspunktfunktion übergeben werden, wird Code definiert, der angibt, dass die DLL an den Prozess angefügt wird. Wenn die Einstiegspunktfunktion nicht den Wert TRUE zurückgibt, beendet das System den Prozess mit einer entsprechenden Fehlermeldung.

Schließlich ändert das System den ausführbaren Code des Prozesses, um Startadressen für die DLL-Funktionen bereitzustellen.

Wie der Rest des Codes eines Programms ordnet das Ladeprogramm DLL-Code in den Adressraum des Prozesses zu, wenn der Prozess gestartet wird. Das Betriebssystem lädt ihn nur bei Bedarf in den Arbeitsspeicher. Somit haben die von DEF-Dateien früherer Windows-Versionen verwendeten Codeattribute `PRELOAD` und `LOADONCALL`, durch die das Laden gesteuert wurde, ihre Bedeutung verloren.

### <a name="explicit-linking"></a>Explizite Verknüpfung

Die meisten Anwendungen verwenden die implizite Verknüpfung, da diese Verknüpfungsmethode am einfachsten anzuwenden ist. Es gibt jedoch Situationen, in denen die explizite Verknüpfung erforderlich ist. Die folgenden Gründe sprechen häufig für die explizite Verknüpfung:

- Die Anwendung kennt den Namen einer DLL, die sie lädt, bis zur Laufzeit nicht. Es ist z. B. möglich, dass die Anwendung den Namen der DLL und der exportierten Funktionen beim Start aus einer Konfigurationsdatei abrufen muss.

- Ein Prozess, der die implizite Verknüpfung verwendet, wird vom Betriebssystem beendet, wenn die DLL beim Starten des Prozesses nicht gefunden wird. Verwendet ein Prozess die explizite Verknüpfung, wird er in dieser Situation nicht beendet und kann versuchen, die Verarbeitung fortzusetzen. So könnte der Prozess z. B. dem Benutzer den Fehler melden und ihn veranlassen, einen anderen Pfad für die DLL anzugeben.

- Ein Prozess, der die implizite Verknüpfung verwendet, wird auch beendet, wenn eine der DLLs, mit denen er verknüpft ist, eine fehlgeschlagene `DllMain`-Funktion enthält. Ein Prozess, der eine explizite Verknüpfung verwendet, wird in dieser Situation nicht beendet.

- Eine Anwendung, die implizit mit zahlreichen DLLs verknüpft ist, wird u. U. langsam gestartet, da von Windows neben der Anwendung auch alle DLLs geladen werden. Zur Verbesserung der Startleistung kann eine Anwendung auch nur eine implizite Verknüpfung für DLLs verwenden, die unmittelbar nach dem Laden erforderlich ist. Es könnte auch eine explizite Verknüpfung verwendet werden, um weitere DLLs nur bei Bedarf zu laden.

- Durch die explizite Verknüpfung entfällt die Notwendigkeit, die Anwendung mit einer Importbibliothek zu verknüpfen. Wenn Änderungen in der DLL dazu führen, dass sich die Exportordinalzahlen ändern, müssen Anwendungen keine neue Verknüpfung herstellen, wenn sie `GetProcAddress` mithilfe des Namens einer Funktion und nicht mit einem Ordinalwert aufrufen. Anwendungen, die die implizite Verknüpfung verwenden, müssen dennoch eine neue Verknüpfung mit der geänderten Importbibliothek herstellen.

Beachten Sie die beiden folgenden Schwachstellen im Zusammenhang mit der expliziten Verknüpfung:

- Wenn die DLL über eine `DllMain`-Einstiegspunktfunktion verfügt, ruft das Betriebssystem die Funktion im Kontext des Threads auf, durch den `LoadLibrary` aufgerufen wurde. Die Einstiegspunktfunktion wird nicht aufgerufen, wenn die DLL bereits an den Prozess angefügt ist, da es einen früheren Aufruf von `LoadLibrary` ohne entsprechenden Aufruf der `FreeLibrary`-Funktion gegeben hat. Explizites Verknüpfen kann Probleme verursachen, wenn die DLL eine `DllMain`-Funktion verwendet, um die einzelnen Threads eines Prozesses zu initialisieren, da jeder Thread, der bereits vorhanden war, als `LoadLibrary` (oder `AfxLoadLibrary`) aufgerufen wurde, nicht initialisiert wird.

- Wenn eine DLL statische Daten als `__declspec(thread)` deklariert, kann dies zu einer Schutzverletzung führen, sobald explizit verknüpft wird. Nachdem die DLL durch einen Aufruf von `LoadLibrary` geladen wurde, verursacht sie eine Schutzverletzung, sobald vom Code auf diese Daten verwiesen wird. (Statische Daten umfassen sowohl globale als auch lokale statische Elemente.) Deshalb sollten Sie bei der Erstellung einer DLL auf die Verwendung von threadlokalem Speicher verzichten. Ist dies nicht möglich, informieren Sie Ihre DLL-Benutzer über mögliche Probleme beim dynamischen Laden Ihrer DLL. Weitere Informationen finden Sie unter [Verwenden von threadlokalem Speicher in einer DLL](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library).

<a name="linking-implicitly"></a>

## <a name="how-to-use-implicit-linking"></a>Verwenden impliziter Verknüpfung

Wenn Sie eine DLL durch implizite Verknüpfung verwenden möchten, müssen ausführbare Clientdateien die folgenden Dateien vom Anbieter der DLL erhalten:

- Mindestens eine der Headerdateien (H-Dateien), die die Deklarationen der exportierten Daten, Funktionen und C++-Klassen in der DLL enthalten. Die Klassen, Funktionen und Daten, die von der DLL exportiert wurden, müssen in der Headerdatei mit `__declspec(dllimport)` markiert werden. Weitere Informationen finden Sie unter [dllexport, dllimport](../cpp/dllexport-dllimport.md).

- Eine Importbibliothek zur Verknüpfung in Ihrer ausführbaren Datei. (Die Importbibliothek wird vom Linker erstellt, nachdem die DLL erstellt wurde.) Weitere Informationen finden Sie unter [LIB-Dateien als Linkereingabe](reference/dot-lib-files-as-linker-input.md).

- Die DLL-Datei selbst.

Damit die Daten, Funktionen und Klassen in einer DLL durch implizites Verknüpfen verwendet werden können, müssen alle Clientquelldateien die Headerdateien enthalten und sie deklarieren. Hinsichtlich der Codierung unterscheiden sich die Aufrufe für exportierte Funktionen nicht von anderen Funktionsaufrufen.

Sie müssen eine Verknüpfung mit der Importbibliothek der DLL herstellen, um die aufrufende ausführbare Datei zu erstellen. Wenn Sie eine externe Makefile oder ein Buildsystem verwenden, geben Sie die Importbibliothek zusammen mit den anderen Objektdateien oder Bibliotheken an, die Sie verknüpfen.

Das Betriebssystem muss in der Lage sein, die DLL-Datei beim Laden der aufrufenden ausführbaren Datei zu lokalisieren. Das bedeutet, Sie müssen die DLL entweder bereitstellen oder ihre Existenz bestätigen, wenn Sie Ihre Anwendung installieren.

<a name="linking-explicitly"></a>

## <a name="how-to-link-explicitly-to-a-dll"></a>Explizites Verknüpfen mit einer DLL

Wenn eine DLL durch explizite Verknüpfung verwendet werden soll, müssen Anwendungen einen Funktionsaufruf durchführen, um die DLL zur Laufzeit explizit zu laden. Für die explizite Verknüpfung mit einer DLL muss eine Anwendung folgende Schritte ausführen:

- [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) (oder eine ähnliche Funktion) aufrufen, um die DLL zu laden und ein Modulhandle zu erhalten.

- [GetProcAddress](getprocaddress.md) aufrufen, um einen Funktionszeiger auf jede exportierte Funktion zu erhalten, die durch die Anwendung aufgerufen wird. Da Anwendungen die DLL-Funktionen über einen Zeiger aufrufen, muss der Compiler keine externen Verweise generieren. Folglich ist es auch nicht erforderlich, eine Importbibliothek zu verknüpfen. Sie müssen jedoch über eine **`typedef`** - oder **`using`** -Anweisung verfügen, die die Aufrufsignatur der von Ihnen aufgerufenen exportierten Funktionen definiert.

- [FreeLibrary](freelibrary-and-afxfreelibrary.md) aufrufen, wenn die DLL nicht mehr benötigt wird.

Diese Beispielfunktion ruft beispielsweise `LoadLibrary` auf, um eine DLL namens „MyDLL“ zu laden, sie ruft `GetProcAddress` auf, um einen Zeiger auf eine Funktion namens „DLLFunc1“ zu erhalten, sie ruft die Funktion auf und speichert das Ergebnis und ruft dann `FreeLibrary` auf, um die DLL zu entladen.

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

Im Gegensatz zu diesem Beispiel sollten Sie in den meisten Fällen `LoadLibrary` und `FreeLibrary` für eine bestimmte DLL nur einmal in Ihrer Anwendung aufrufen. Dies gilt insbesondere, wenn Sie mehrere Funktionen in der DLL aufrufen möchten oder DLL-Funktionen wiederholt aufrufen möchten.

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Arbeiten mit Importbibliotheken und Exportdateien](reference/working-with-import-libraries-and-export-files.md)

- [Dynamic Link Library-Suchreihenfolge](/windows/win32/Dlls/dynamic-link-library-search-order)

## <a name="see-also"></a>Siehe auch

[Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)

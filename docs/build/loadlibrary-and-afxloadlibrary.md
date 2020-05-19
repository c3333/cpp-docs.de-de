---
title: "\"LoadLibrary\" und \"AfxLoadLibrary\""
description: Verwenden von "LoadLibrary" und "AfxLoadLibrary" für das explizite Laden von DLLs in MSVC
ms.date: 01/28/2020
f1_keywords:
- LoadLibrary
helpviewer_keywords:
- DLLs [C++], AfxLoadLibrary
- DLLs [C++], LoadLibrary
- AfxLoadLibrary method
- LoadLibrary method
- explicit linking [C++]
ms.assetid: b4535d19-6243-4146-a31a-a5cca4c7c9e3
ms.openlocfilehash: f803212c4485f7517dc42802f1ff581ffa4e609d
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821537"
---
# <a name="loadlibrary-and-afxloadlibrary"></a>"LoadLibrary" und "AfxLoadLibrary"

Prozesse rufen [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) oder [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexw) auf, um explizit eine Verknüpfung mit einer DLL herzustellen. (MFC-Apps verwenden [AfxLoadLibrary](../mfc/reference/application-information-and-management.md#afxloadlibrary) oder [AfxLoadLibraryEx](../mfc/reference/application-information-and-management.md#afxloadlibraryex).) Wenn die Funktion erfolgreich ausgeführt wird, ordnet sie die angegebene DLL dem Adressraum des aufrufenden Prozesses zu und gibt ein Handle für die DLL zurück. Das Handle ist in anderen Funktionen erforderlich, die für die explizite Verknüpfung verwendet werden – z. B. `GetProcAddress` und `FreeLibrary`. Weitere Informationen finden Sie unter [Explizite Verknüpfung](linking-an-executable-to-a-dll.md#linking-explicitly).

`LoadLibrary` versucht, die DLL mithilfe derselben Suchfolge aufzufinden, die für die implizite Verknüpfung verwendet wird. `LoadLibraryEx` bietet Ihnen eine bessere Kontrolle über die Reihenfolge der Suchpfade. Weitere Informationen finden Sie unter [Dynamic Link Library-Suchreihenfolge](/windows/win32/dlls/dynamic-link-library-search-order). Wenn das System die DLL nicht finden kann oder die Einstiegspunktfunktion FALSE zurückgibt, wird von `LoadLibrary` NULL zurückgegeben. Wenn im Aufruf von `LoadLibrary` ein DLL-Modul angegeben ist, das bereits im Adressraum des aufrufenden Prozesses zugeordnet ist, gibt die Funktion einfach ein Handle für die DLL zurück und erhöht den Referenzzähler des Moduls.

Wenn die DLL über eine Einstiegspunktfunktion verfügt, ruft das Betriebssystem die Funktion im Kontext des Threads auf, durch den `LoadLibrary` oder `LoadLibraryEx` aufgerufen wurde. Die Einstiegspunktfunktion wird nicht aufgerufen, wenn die DLL bereits an den Prozess angefügt ist. Dies ist der Fall, wenn ein vorheriger `LoadLibrary`- oder `LoadLibraryEx`-Aufruf für die DLL keinen entsprechenden Aufruf der `FreeLibrary`-Funktion enthielt.

Für MFC-Anwendungen, die MFC-Erweiterungs-DLLs laden, wird empfohlen, `AfxLoadLibrary` bzw. `AfxLoadLibraryEx` anstelle von `LoadLibrary` bzw. `LoadLibraryEx` zu verwenden. Die MFC-Funktionen behandeln die Threadsynchronisierung vor dem expliziten Laden der DLL. Die Schnittstellen (Funktionsprototypen) zu `AfxLoadLibrary` und `AfxLoadLibraryEx` sind identisch mit `LoadLibrary` und `LoadLibraryEx`.

Wenn die DLL nicht von Windows geladen werden kann, versucht der Prozess, nach dem Fehler eine Wiederherstellung durchzuführen. Beispielsweise könnte er den Benutzer über den Fehler informieren und dann nach einem anderen Pfad zur DLL fragen.

> [!IMPORTANT]
> Stellen Sie sicher, dass Sie den vollständigen Pfad aller DLLs angeben. Das aktuelle Verzeichnis wird möglicherweise zuerst durchsucht, wenn Dateien von `LoadLibrary` geladen werden. Wenn Sie den Pfad für die Datei nicht vollständig qualifizieren, wird unter Umständen eine falsche Datei geladen. Wenn Sie eine DLL erstellen, verwenden Sie die Linkeroption [/DEPENDENTLOADFLAG](reference/dependentloadflag.md), um eine Suchreihenfolge für statisch verknüpfte DLL-Abhängigkeiten anzugeben. Verwenden Sie in Ihren DLLs sowohl vollständige Pfade für das explizite Laden von Abhängigkeiten als auch `LoadLibraryEx`- oder `AfxLoadLibraryEx`-Aufrufparameter, um die Suchreihenfolge der Module anzugeben. Weitere Informationen finden Sie unter [Dynamic Link Library-Sicherheit](/windows/win32/dlls/dynamic-link-library-security) und [Dynamic Link Library-Suchreihenfolge](/windows/win32/dlls/dynamic-link-library-search-order).

## <a name="what-do-you-want-to-do"></a>Wie möchten Sie vorgehen?

- [Link an executable to a DLL (Eine ausführbare Datei mit einer DLL verknüpfen)](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Link an executable to a DLL (Eine ausführbare Datei mit einer DLL verknüpfen)](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

- [Dynamic Link Library-Suchreihenfolge](/windows/win32/Dlls/dynamic-link-library-search-order)

- [FreeLibrary und AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)

- [GetProcAddress](getprocaddress.md)

## <a name="see-also"></a>Siehe auch

- [Erstellen von C/C++-DLLs in Visual Studio](dlls-in-visual-cpp.md)

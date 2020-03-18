---
title: Erstellen von CC++ /DLLs in Visual Studio
description: Eine Übersicht darüber, warum und wie DLLs mit C++ in Visual Studio erstellt und verwendet werden.
ms.date: 01/27/2020
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
ms.openlocfilehash: 7083924f137fa9283da40404c7d15183e59c0b1c
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422829"
---
# <a name="create-cc-dlls-in-visual-studio"></a>Erstellen von CC++ /DLLs in Visual Studio

In Windows ist eine Dynamic Link Library (dll) eine Art ausführbare Datei, die als freigegebene Bibliothek von Funktionen und Ressourcen fungiert. Dynamisches Verknüpfen ist eine Funktion des Betriebssystems. Dadurch kann eine ausführbare Dateifunktionen aufzurufen oder Ressourcen verwenden, die in einer separaten Datei gespeichert sind. Diese Funktionen und Ressourcen können getrennt von den ausführbaren Dateien, von denen sie verwendet werden, kompiliert und bereitgestellt werden.

Eine dll ist keine eigenständige ausführbare Datei. DLLs werden im Kontext der Anwendungen ausgeführt, von denen Sie aufgerufen werden. Das Betriebssystem lädt die dll in den Speicherbereich einer Anwendung. Dies erfolgt entweder beim Laden der Anwendung (*implizites verknüpfen*) oder bei Bedarf zur Laufzeit (*explizites verknüpfen*). DLLs machen es außerdem einfach, Funktionen und Ressourcen in ausführbaren Dateien gemeinsam zu nutzen. Mehrere Anwendungen können gleichzeitig auf den Inhalt einer einzigen Kopie einer im Arbeitsspeicher enthaltenen DLL zugreifen.

## <a name="differences-between-dynamic-linking-and-static-linking"></a>Unterschiede zwischen dynamischem verknüpfen und statischem verknüpfen

Statisches verknüpfen kopiert den gesamten Objektcode in einer statischen Bibliothek in die ausführbaren Dateien, die diese verwenden, wenn Sie erstellt werden. Die dynamische Verknüpfung umfasst nur die Informationen, die von Windows zur Laufzeit benötigt werden, um die dll zu suchen und zu laden, die ein Datenelement oder eine Funktion enthält. Wenn Sie eine DLL erstellen, erstellen Sie auch eine Import Bibliothek, die diese Informationen enthält. Wenn Sie eine ausführbare Datei erstellen, die die DLL aufruft, verwendet der Linker die exportierten Symbole in der Import Bibliothek, um diese Informationen für das Windows-Lade Programm zu speichern. Wenn das Lade Modul eine DLL lädt, wird die dll im Speicherbereich der Anwendung zugeordnet. Falls vorhanden, wird eine spezielle Funktion in der dll (`DllMain`) aufgerufen, um eine beliebige Initialisierung durchzuführen, die die dll benötigt.

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>Unterschiede zwischen Anwendungen und DLLs

Obwohl es sich bei DLLs und Anwendungen um ausführbare Module handelt, unterscheiden Sie sich auf verschiedene Weise. Der offensichtlichste Unterschied besteht darin, dass Sie eine DLL nicht ausführen können. Im Hinblick auf das System gibt es zwei grundsätzliche Unterschiede zwischen Anwendungen und DLLs:

- Eine Anwendung kann mehrere Instanzen von sich selbst gleichzeitig im System ausführen. Eine DLL kann nur über eine Instanz verfügen.

- Eine Anwendung kann als Prozess geladen werden. Sie kann z. b. einen Stapel, Ausführungs Threads, globalen Speicher, Datei Handles und eine Nachrichten Warteschlange besitzen. Eine DLL kann diese Dinge nicht besitzen.

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>Vorteile der Verwendung von DLLs

Dynamisches Verknüpfen mit Code und Ressourcen bietet im Vergleich zur statischen Verknüpfung mehrere Vorteile:

- Die dynamische Verknüpfung spart Arbeitsspeicher und verringert den Austausch. Viele Prozesse können eine DLL gleichzeitig verwenden und eine einzelne Kopie der schreibgeschützten Teile einer DLL im Arbeitsspeicher freigeben. Im Gegensatz dazu verfügt jede Anwendung, die mit einer statisch verknüpften Bibliothek erstellt wird, über eine komplette Kopie des Bibliothekscodes, den Windows in den Arbeitsspeicher laden muss.

- Die dynamische Verknüpfung spart Speicherplatz und Bandbreite. Viele Anwendungen können eine einzelne, auf der Festplatte gespeicherte Kopie der DLL gemeinsam nutzen. Im Gegensatz dazu ist für jede Anwendung, die mit einer statischen Link Bibliothek erstellt wurde, der Bibliotheks Code mit dem ausführbaren Image verknüpft. , Der mehr Speicherplatz beansprucht und mehr Bandbreite für die Übertragung benötigt.

- Wartung, Sicherheitskorrekturen und Upgrades können einfacher sein. Wenn Ihre Anwendungen allgemeine Funktionen in einer DLL verwenden, können Sie Fehlerbehebungen implementieren und Updates für die DLL bereitstellen. Wenn DLLs aktualisiert werden, müssen die Anwendungen, die Sie verwenden, nicht erneut kompiliert oder neu verknüpft werden. Sie können die neue dll verwenden, sobald Sie bereitgestellt ist. Wenn Sie im Gegensatz dazu Fehlerbehebungen in statisch verknüpftem Objektcode vornehmen, müssen Sie jede Anwendung, die diese verwendet, neu verknüpfen und erneut bereitstellen.

- Sie können DLLs zum Bereitstellen von nach Marktunterstützung verwenden. Beispielsweise kann eine Anzeigetreiber-DLL geändert werden, um eine Anzeige zu unterstützen, die beim Versand der Anwendung nicht verfügbar war.

- Mithilfe der expliziten Verknüpfung können Sie DLLs zur Laufzeit ermitteln und laden. Beispielsweise Anwendungs Erweiterungen, die Ihrer APP neue Funktionen hinzufügen, ohne Sie erneut zu erstellen oder bereitzustellen.

- Durch dynamisches Verknüpfen wird die Unterstützung von Anwendungen vereinfacht, die in verschiedenen Programmiersprachen geschrieben wurden. Programme, die in verschiedenen Programmiersprachen erstellt wurden, können dieselbe DLL-Funktion aufrufen, solange sie die Aufrufkonvention der Funktion einhalten. Die Programme und die DLL-Funktion müssen wie folgt kompatibel sein: die Reihenfolge, in der die Funktion erwartet, dass ihre Argumente auf den Stapel verschoben werden. Gibt an, ob die Funktion oder die Anwendung für das Bereinigen des Stapels verantwortlich ist. Und, ob Argumente in Registern übermittelt werden.

- Dynamic Linking bietet einen Mechanismus zum Erweitern der MFC-Klassen (Microsoft Foundation Class Library). Sie können Klassen von bestehenden MFC-Klassen ableiten und diese in einer MFC-Erweiterungs-DLL speichern, die dann von MFC-Anwendungen genutzt werden kann.

- Durch dynamisches Verknüpfen wird die Erstellung internationaler Versionen der Anwendung vereinfacht. DLLs sind eine bequeme Möglichkeit zum Bereitstellen von Gebiets Schema spezifischen Ressourcen, die das Erstellen internationaler Versionen einer Anwendung erheblich vereinfachen. Anstatt viele lokalisierte Versionen der Anwendung zu versenden, können Sie die Zeichen folgen und Bilder für jede Sprache in einer separaten Ressourcen-DLL platzieren. Die Anwendung kann dann die entsprechenden Ressourcen für dieses Gebiets Schema zur Laufzeit laden.

Ein potenzieller Nachteil bei der Verwendung von DLLs besteht darin, dass die Anwendung nicht eigenständig ist. Dies hängt davon ab, ob ein separates dll-Modul vorhanden ist, das Sie im Rahmen der Installation bereitstellen oder selbst überprüfen müssen.

## <a name="more-information-on-how-to-create-and-use-dlls"></a>Weitere Informationen zum Erstellen und Verwenden von DLLs

Die folgenden Artikel enthalten ausführliche Informationen zum Erstellen von C/C++ DLLs in Visual Studio.

Exemplarische Vorgehensweise [: Erstellen und Verwenden einer Dynamic LinkC++Library ()-](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)\
Beschreibt, wie Sie mit Visual Studio eine DLL erstellen und verwenden.

[Arten von DLLs](kinds-of-dlls.md)\
Bietet Informationen zu den verschiedenen Arten von DLLs, die erstellt werden können.

[Häufig gestellte Fragen zu dll](dll-frequently-asked-questions.md) -\
Bietet Antworten auf häufig gestellte Fragen zu DLLs.

[Eine ausführbare Datei mit einer DLL verknüpfen](linking-an-executable-to-a-dll.md)\
Beschreibt das explizite und implizite Verknüpfen mit einer DLL.

[Initialisieren einer DLL](run-time-library-behavior.md#initializing-a-dll) -\
Erläutert den dll-Initialisierungs Code, der beim Laden der DLL ausgeführt werden muss.

[DLLs und Verhalten C++ der visuellen Lauf Zeit Bibliothek](run-time-library-behavior.md)\
Beschreibt die Startsequenz der Lauf Zeit Bibliotheks-DLL.

[LoadLibrary-und AfxLoadLibrary-](loadlibrary-and-afxloadlibrary.md)\
Erläutert die Verwendung von `LoadLibrary` und `AfxLoadLibrary` zur expliziten Verknüpfung mit einer DLL zur Laufzeit.

[GetProcAddress](getprocaddress.md) -\
Erläutert die Verwendung von `GetProcAddress`, um die Adresse einer exportierten Funktion in der dll abzurufen.

" [FreeLibrary" und "AfxFreeLibrary](freelibrary-and-afxfreelibrary.md) "\
Erläutert die Verwendung von `FreeLibrary` und `AfxFreeLibrary`, wenn das dll-Modul nicht mehr benötigt wird.

[Such Reihenfolge der Dynamic Link Library](/windows/win32/Dlls/dynamic-link-library-search-order)\
Beschreibt den Suchpfad, der von Windows verwendet wird, um eine DLL im System zu finden.

[Modul Zustände einer regulären MFC-DLL, die dynamisch mit MFC verknüpft](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md) ist\
Beschreibt die Modul Zustände einer regulären MFC-DLL, die dynamisch mit MFC verknüpft ist.

[MFC-Erweiterungs-DLLs](extension-dlls-overview.md)\
Erläutert DLLs, die in der Regel wiederverwendbare, von den vorhandenen MFC-Klassen abgeleitete Klassen implementieren

[Erstellen einer reinen Ressourcen-DLL-](creating-a-resource-only-dll.md)\
Erörtert eine reine Ressourcen-DLL, die ausschließlich Ressourcen enthält, z. B. Symbole, Bitmaps, Zeichenfolgen und Dialogfelder.

[Lokalisierte Ressourcen in MFC-Anwendungen: Satelliten-DLLs](localized-resources-in-mfc-applications-satellite-dlls.md)\
Bietet erweiterte Unterstützung für Satelliten-DLLs, eine Funktion, die den Entwickler bei der Erstellung von Anwendungen unterstützt, die für mehrere Sprachen lokalisiert sind.

[Importieren und exportieren](importing-and-exporting.md) von\
Beschreibt das Importieren öffentlicher Symbole in eine Anwendung bzw. das Exportieren von Funktionen aus einer DLL.

[Aktive Technologie und DLLs](active-technology-and-dlls.md)\
Bietet die Möglichkeit, Objektserver innerhalb einer DLL zu implementieren.

[Automation in einer DLL](automation-in-a-dll.md) -\
Beschreibt, welche Features die Automatisierungsoption im MFC-DLL-Assistenten bereitstellt.

[Benennungs Konventionen für MFC-DLLs](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)\
Erörtert, nach welcher strukturierten Namenskonvention die in MFC enthaltenen DLLs und Bibliotheken benannt sind.

[Aufrufen von DLL-Funktionen aus Visual Basic Anwendungen](calling-dll-functions-from-visual-basic-applications.md)\
Beschreibt den Aufruf von DLL-Funktionen aus Visual Basic-Anwendungen.

## <a name="related-sections"></a>Verwandte Abschnitte

[Verwenden von MFC als Teil einer DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md) -\
Beschreibt reguläre MFC-DLLs, mit denen Sie die MFC-Bibliothek als Bestandteil einer Windows Dynamic Link Library verwenden können.

[Dll-Version des MFC](../mfc/tn033-dll-version-of-mfc.md) -\
Beschreibt, wie Sie MFCxx. dll und MFCxxD. dll (wobei x die MFC-Versionsnummer ist) freigegebene Dynamic-Link-Bibliotheken mit MFC-Anwendungen und MFC-Erweiterungs-DLLs verwenden können.

---
title: Erstellen von C-/C++-DLLs in Visual Studio
description: Dieser Artikel bietet eine Übersicht darüber, warum und wie DLLs mit C++ in Visual Studio erstellt und verwendet werden.
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
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422829"
---
# <a name="create-cc-dlls-in-visual-studio"></a>Erstellen von C-/C++-DLLs in Visual Studio

Bei Windows ist eine Dynamic Link Library (DLL) eine Art ausführbare Datei, die als eine gemeinsam genutzte Bibliothek von Funktionen und Ressourcen fungiert. Das dynamische Verknüpfen ist eine Betriebssystemfunktion. Es ermöglicht einer ausführbaren Datei das Aufrufen von Funktionen oder Verwenden von Ressourcen, die in einer separaten Datei gespeichert sind. Diese Funktionen und Ressourcen können getrennt von den ausführbaren Dateien, von denen sie verwendet werden, kompiliert und bereitgestellt werden.

Eine DLL ist keine eigenständige ausführbare Datei. DLLs werden im Kontext der Anwendungen ausgeführt, von denen sie aufgerufen werden. Das Betriebssystem lädt die DLL in den Speicherplatz einer Anwendung. Dies erfolgt entweder beim Laden der Anwendung (*implizites Verknüpfen*) oder bei Bedarf zur Laufzeit (*explizites Verknüpfen*). DLLs machen es außerdem einfach, Funktionen und Ressourcen in ausführbaren Dateien gemeinsam zu nutzen. Mehrere Anwendungen können gleichzeitig auf den Inhalt einer einzigen Kopie einer im Arbeitsspeicher enthaltenen DLL zugreifen.

## <a name="differences-between-dynamic-linking-and-static-linking"></a>Unterschiede zwischen dynamischem Verknüpfen und statischem Verknüpfen

Beim statischen Verknüpfen wird der gesamte Objektcode in einer statischen Bibliothek in die ausführbaren Dateien kopiert, die diesen verwenden, wenn sie erstellt werden. Beim dynamischen Verknüpfen werden nur die Informationen eingebunden, die von Windows zur Laufzeit benötigt werden, um die DLL zu suchen und zu laden, in der ein Datenelement oder eine Funktion enthalten ist. Wenn Sie eine DLL erstellen, erstellen Sie auch eine Importbibliothek, die diese Informationen enthält. Wenn Sie eine ausführbare Datei erstellen, die die DLL aufruft, verwendet der Linker die exportierten Symbole in der Importbibliothek, um diese Informationen für das Windows-Ladeprogramm zu speichern. Wenn das Ladeprogramm eine DLL lädt, wird die DLL in den Speicherplatz Ihrer Anwendung eingebunden. Falls vorhanden, wird eine spezielle Funktion in der DLL, `DllMain`, aufgerufen, um die von der DLL benötigte Initialisierung durchzuführen.

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>Unterschiede zwischen Anwendungen und DLLs

Obwohl sowohl DLLs als auch Anwendungen ausführbare Module sind, unterscheiden sie sich in verschiedener Hinsicht. Der offensichtlichste Unterschied besteht darin, dass Sie eine DLL nicht ausführen können. Im Hinblick auf das System gibt es zwei grundsätzliche Unterschiede zwischen Anwendungen und DLLs:

- Von einer Anwendung können mehrere Instanzen gleichzeitig im System ausgeführt werden. Eine DLL kann nur über eine Instanz verfügen.

- Eine Anwendung kann als Prozess geladen werden. Sie kann über einen Stapel, Ausführungsthreads, globalen Arbeitsspeicher, Dateihandles und eine Nachrichtenwarteschlange verfügen. Eine DLL kann diese Dinge nicht besitzen.

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>Vorteile der Verwendung von DLLs

Dynamisches Verknüpfen mit Code und Ressourcen bietet im Vergleich zum statischen Verknüpfen mehrere Vorteile:

- Beim dynamischen Verknüpfen wird Arbeitsspeicher gespart und der Austausch reduziert. Eine DLL kann von vielen Prozessen gleichzeitig verwendet werden. Dabei wird eine einzelne, in den Arbeitsspeicher geladene Kopie der schreibgeschützten Teile einer DLL gemeinsam genutzt. Im Gegensatz dazu verfügt jede Anwendung, die mithilfe einer statisch verknüpften Bibliothek erstellt wird, über eine vollständige Kopie des Bibliothekscodes, den Windows in den Arbeitsspeicher laden muss.

- Beim dynamischen Verknüpfen werden Speicherplatz und Bandbreite eingespart. Viele Anwendungen können eine einzelne, auf der Festplatte gespeicherte Kopie der DLL gemeinsam nutzen. Im Gegensatz dazu wird für jede Anwendung, die mit einer statischen Verknüpfungsbibliothek erstellt wurde, der Bibliothekscode in deren ausführbares Image eingebunden. Dabei werden mehr Speicherplatz und mehr Bandbreite für die Übertragung verwendet.

- Die Verwaltung, Sicherheitskorrekturen und Upgrades können einfacher durchzuführen sein. Wenn Ihre Anwendungen allgemeine Funktionen in einer DLL verwenden, können Sie für die DLL Fehlerbehebungen durchführen und Updates bereitstellen. Wenn DLLs aktualisiert werden, müssen die Anwendungen, die sie verwenden, nicht neu kompiliert oder neu verknüpft werden. Sie können die neue DLL verwenden, sobald diese bereitgestellt wurde. Wenn Sie im Gegensatz dazu Fehlerbehebungen in statisch verknüpftem Objektcode vornehmen, müssen Sie jede Anwendung, die diesen verwendet, neu verknüpfen und erneut bereitstellen.

- Sie können DLLs zum Bereitstellen von Unterstützung nach der Vermarktung verwenden. Eine Treiber-DLL für eine Anzeige kann z. B. so geändert werden, dass eine Anzeige unterstützt wird, die zum Zeitpunkt der Auslieferung der Anwendung noch gar nicht verfügbar war.

- Mithilfe der expliziten Verknüpfung können Sie DLLs zur Laufzeit ermitteln und laden. Dazu zählen beispielsweise Anwendungserweiterungen, die neue Funktionen zu Ihrer App hinzufügen, ohne diese neu zu erstellen oder bereitzustellen.

- Durch das dynamische Verknüpfen wird die Unterstützung von Anwendungen vereinfacht, die in verschiedenen Programmiersprachen geschrieben sind. Programme, die in verschiedenen Programmiersprachen erstellt wurden, können dieselbe DLL-Funktion aufrufen, solange sie die Aufrufkonvention der Funktion einhalten. Die Programme und die DLL-Funktion müssen in den folgenden Punkten kompatibel sein: der Reihenfolge, in der die Funktion erwartet, dass ihre Argumente per Push auf den Stapel übertragen werden, ob die Funktion oder die Anwendung für das Bereinigen des Stapels verantwortlich ist, und ob Argumente in Registern übermittelt werden.

- Die dynamische Verknüpfung stellt einen Mechanismus zum Erweitern der MFC-Bibliotheksklassen (Microsoft Foundation Class) bereit. Sie können Klassen von bestehenden MFC-Klassen ableiten und diese in einer MFC-Erweiterungs-DLL speichern, die dann von MFC-Anwendungen genutzt werden kann.

- Durch das dynamische Verknüpfen wird die Erstellung internationaler Versionen Ihrer Anwendung vereinfacht. DLLs sind eine praktische Methode zum Bereitstellen gebietsschemaspezifischer Ressourcen, durch die das Erstellen internationaler Versionen einer Anwendung deutlich vereinfacht wird. Anstatt viele lokalisierte Versionen Ihrer Anwendung zu versenden, können Sie die Zeichenfolgen und Images für jede Sprache in einer separaten Ressourcen-DLL ablegen. Die Anwendung kann dann die entsprechenden Ressourcen für dieses Gebietsschema zur Laufzeit laden.

Ein potenzieller Nachteil bei der Verwendung von DLLs besteht darin, dass die Anwendung nicht eigenständig ist. Dies hängt davon ab, ob ein separates DLL-Modul vorhanden ist, das Sie im Rahmen der Installation bereitstellen oder selbst überprüfen müssen.

## <a name="more-information-on-how-to-create-and-use-dlls"></a>Weitere Informationen zum Erstellen und Verwenden von DLLs

Die folgenden Artikel enthalten ausführliche Informationen zum Erstellen von C-/C++-DLLs in Visual Studio.

[Exemplarische Vorgehensweise: Erstellen und Verwenden einer Dynamic Link Library (C++)](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)\
Beschreibt, wie Sie mit Visual Studio eine DLL erstellen und verwenden.

[Arten von DLLs](kinds-of-dlls.md)\
Bietet Informationen zu den verschiedenen Arten von DLLs, die erstellt werden können.

[Häufig gestellte Fragen (FAQs) zu DLLs](dll-frequently-asked-questions.md)\
Bietet Antworten auf häufig gestellte Fragen zu DLLs.

[Verknüpfen einer ausführbaren Datei mit einer DLL](linking-an-executable-to-a-dll.md)\
Beschreibt das explizite und implizite Verknüpfen mit einer DLL.

[Initialisieren einer DLL](run-time-library-behavior.md#initializing-a-dll)\
In diesem Artikel wird der Initialisierungscode einer DLL beschrieben, der beim Laden der DLL ausgeführt werden muss.

[Verhalten der Laufzeitbibliothek für DLLs und Visual C++](run-time-library-behavior.md)\
Dieser Artikel beschreibt die DLL-Startsequenz der Laufzeitbibliothek.

[„LoadLibrary“ und „AfxLoadLibrary“](loadlibrary-and-afxloadlibrary.md)\
In diesem Artikel wird die Verwendung von `LoadLibrary` und `AfxLoadLibrary` zum expliziten Verknüpfen einer DLL zur Laufzeit beschrieben.

[GetProcAddress](getprocaddress.md)\
In diesem Artikel wird die Verwendung von `GetProcAddress` zum Abrufen der Adresse einer exportierten Funktion in der DLL beschrieben.

[FreeLibrary und AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)\
In diesem Artikel wird die Verwendung von `FreeLibrary` und `AfxFreeLibrary` in Situationen beschrieben, in denen das DLL-Modul nicht länger benötigt wird.

[Dynamic Link Library-Suchreihenfolge](/windows/win32/Dlls/dynamic-link-library-search-order)\
Beschreibt den Suchpfad, der von Windows verwendet wird, um eine DLL im System zu finden.

[Modulzustände einer regulären, dynamisch mit MFC verknüpften MFC-DLL](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)\
In diesem Artikel werden die Modulzustände einer regulären, dynamisch mit MFC verknüpften MFC-DLL beschrieben.

[MFC-Erweiterungs-DLLs](extension-dlls-overview.md)\
In diesem Artikel werden DLLs erläutert, die in der Regel wiederverwendbare Klassen implementieren, die von den bestehenden MFC-Klassen abgeleitet wurden.

[Erstellen einer DLL als reine Ressource](creating-a-resource-only-dll.md)\
Erörtert eine reine Ressourcen-DLL, die ausschließlich Ressourcen enthält, z. B. Symbole, Bitmaps, Zeichenfolgen und Dialogfelder.

[Lokalisierte Ressourcen in MFC-Anwendungen: Satelliten-DLLs](localized-resources-in-mfc-applications-satellite-dlls.md)\
Bietet erweiterte Unterstützung für Satelliten-DLLs, eine Funktion, die den Entwickler bei der Erstellung von Anwendungen unterstützt, die für mehrere Sprachen lokalisiert sind.

[Importieren und Exportieren](importing-and-exporting.md)\
Beschreibt das Importieren öffentlicher Symbole in eine Anwendung bzw. das Exportieren von Funktionen aus einer DLL.

[Active Technology und DLLs](active-technology-and-dlls.md)\
Bietet die Möglichkeit, Objektserver innerhalb einer DLL zu implementieren.

[Automatisierung in einer DLL](automation-in-a-dll.md)\
Beschreibt, welche Features die Automatisierungsoption im MFC-DLL-Assistenten bereitstellt.

[Namenskonventionen für MFC-DLLs](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)\
Erörtert, nach welcher strukturierten Namenskonvention die in MFC enthaltenen DLLs und Bibliotheken benannt sind.

[Aufrufen von DLL-Funktionen in Visual Basic-Anwendungen](calling-dll-functions-from-visual-basic-applications.md)\
Beschreibt den Aufruf von DLL-Funktionen aus Visual Basic-Anwendungen.

## <a name="related-sections"></a>Verwandte Abschnitte

[Verwenden von MFC als Teil einer DLL](../mfc/tn011-using-mfc-as-part-of-a-dll.md)\
In diesem Artikel werden reguläre MFC-DLLs beschrieben, über die Sie die MFC-Bibliothek als Bestandteil einer Windows-DLL (Dynamic Link Library) verwenden können.

[DLL-Version von MFC](../mfc/tn033-dll-version-of-mfc.md)\
In diesem Artikel wird beschrieben, wie die gemeinsam genutzten Dynamic Link Librarys „MFCxx.dll“ und „MFCxxD.dll“ (wobei x für die MFC-Versionsnummer steht) mit MFC-Anwendungen und MFC-Erweiterungs-DLLs verwendet werden können.

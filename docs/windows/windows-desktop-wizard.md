---
title: Windows-Desktop-Assistenten
ms.date: 03/29/2019
f1_keywords:
- vc.appwiz.win32.overview
- vc.appwiz.win32.appset
helpviewer_keywords:
- Windows Desktop Wizard
- Win32 Project Wizard
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
ms.openlocfilehash: 3ba53be8e412a39d938198cbd7f2587496ea38eb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165950"
---
# <a name="windows-desktop-wizard"></a>Windows-Desktop-Assistenten

Der Windows-Desktop-Assistent ersetzt den Win32-Anwendungs-Assistenten in Visual Studio 2017 und höher. Mit dem Assistenten können Sie einen von vier C++ Projekttypen erstellen (siehe die Überschrift in der Tabelle unten). Sie können zusätzliche Optionen festlegen, die für den jeweils geöffneten Projekttyp geeignet sind.

   ![Windows-Desktop-Assistenten](media/windows-desktop-wizard.png)

Der folgenden Tabelle können Sie entnehmen, welche Optionen für die einzelnen Anwendungstypen verfügbar sind.

|Art der Unterstützung|Konsolenanwendung|Ausführbare (Windows-)Anwendung|Dynamic Link Library|Statische Bibliothek|
|---------------------|-------------------------|----------------------------------------|---------------------------|--------------------|
|**Leeres Projekt**|Ja|Ja|Ja|Nein|
|**Symbole exportieren**|Nein|Nein|Ja|Nein|
|**Vorkompilierter Header**|Nein|Nein|Nein|Ja|
|**ATL-Unterstützung**|Ja|Nein|Nein|Nein|
|**MFC-Unterstützung**|Ja|Nein|Nein|Ja|

## <a name="overview"></a>Übersicht

Auf der Seite für diesen Assistenten werden die aktuellen Projekteinstellungen für die von Ihnen erstellte Win32-Anwendung beschrieben. Die folgenden Optionen sind standardmäßig aktiviert:

- Das Projekt ist eine Windows-Anwendung.

- Das Projekt ist nicht leer.

- Das Projekt enthält keine Exportsymbole.

- Das Projekt verwendet keine vorkompilierte Headerdatei (diese Option ist nur für statische Bibliotheksprojekte verfügbar).

- Das Projekt unterstützt weder MFC noch ATL.

## <a name="application-type"></a>Anwendungstyp

Erstellt den angegebenen Anwendungstyp.

|Option|BESCHREIBUNG|
|------------|-----------------|
|**Konsolenanwendung**|Erstellt eine Konsolenanwendung. Die visuellen C++ [Laufzeitbibliotheken](../c-runtime-library/c-run-time-library-reference.md) stellen außerdem Ausgaben und Eingaben aus Konsolen Fenstern mit Standard-e/a-Funktionen bereit, wie z. b. `printf_s()` und `scanf_s()`. Eine Konsolenanwendung hat keine grafische Benutzeroberfläche. Sie kompiliert Code in einer EXE-Datei und kann als eigenständige Anwendung von der Befehlszeile ausgeführt werden.<br /><br /> Sie können einer Konsolenanwendung MFC- und ATL-Unterstützung hinzufügen.|
|**Windows-Anwendung**|Erstellt ein Win32-Programm. Ein Win32-Programm ist eine ausführbare Anwendung (EXE), die in C oder C++ geschrieben ist und über Aufrufe der Win32-API eine grafische Benutzeroberfläche erstellt.<br /><br /> Sie können einer Windows-Anwendung keine MFC- oder ATL-Unterstützung hinzufügen.|
|**Dynamic Link Library**|Erstellt eine Win32-Dynamic Link Library (DLL). Eine Win32-DLL ist eine in C oder C++ geschriebene Binärdatei, die anstelle von MFC-Klassenaufrufen Win32-API-Aufrufe verwendet. Sie fungiert als gemeinsam genutzte Funktionsbibliothek, die von mehreren Anwendungen gleichzeitig eingesetzt werden kann.<br /><br /> Sie können einer mit diesem Assistenten erstellten DLL-Anwendung keine MFC-oder ATL-Unterstützung hinzufügen. Sie können jedoch eine MFC-DLL erstellen, indem Sie auf **Neu > Projekt > MFC-DLL**klicken.|
|**Statische Bibliothek**|Erstellt eine statische Bibliothek. Eine statische Bibliothek ist eine Datei, die Objekte sowie zugehörige Funktionen und Daten enthält, die bei der Erstellung der ausführbaren Datei mit dem Programm verknüpft werden. In diesem Thema wird erläutert, wie die Startdateien und [Projekteigenschaften](../build/reference/property-pages-visual-cpp.md) für eine statische Bibliothek erstellt werden. Eine statische Bibliothek bietet die folgenden Vorteile:<br /><br />-Eine statische Win32-Bibliothek ist nützlich, wenn die Anwendung, an der Sie arbeiten, anstelle von MFC-Klassen Aufrufe an die Win32-API durchführt.<br />-Der Verknüpfungs Prozess ist identisch, unabhängig davon, ob der Rest der Windows-Anwendung in C C++oder in geschrieben ist.<br />-Sie können eine statische Bibliothek mit einem MFC-basierten Programm oder einem nicht-MFC-Programm verknüpfen.|

## <a name="additional-options"></a>Weitere Optionen

Definiert abhängig vom Anwendungstyp die Unterstützung sowie Optionen für die Anwendung.

|Option|BESCHREIBUNG|
|------------|-----------------|
|**Leeres Projekt**|Legt fest, dass die Projektdateien leer sind. Wenn Sie über eine Gruppe von Quellcodedateien (z. B. CPP-Dateien, Headerdateien, Symbole, Symbolleisten, Dialogfelder usw.) verfügen und in der Visual C++-Entwicklungsumgebung ein Projekt erstellen möchten, müssen Sie zunächst ein leeres Projekt anlegen und die Dateien dem Projekt dann hinzufügen.<br /><br /> Diese Option ist für statische Bibliotheksprojekte nicht verfügbar.|
|**Symbole exportieren**|Legt fest, dass vom DLL-Projekt Symbole exportiert werden.|
|**Vorkompilierter Header**|Legt fest, dass das statische Bibliotheksprojekt einen vorkompilierten Header verwendet.|
|**Security Development Lifecycle (SDL)-Prüfungen**|Weitere Informationen zu SDL finden Sie unter [Microsoft Security Development Lifecycle (SDL) Prozess Leit Faden](../build/reference/sdl-enable-additional-security-checks.md) .|

## <a name="add-common-headers-for"></a>Allgemeine Header hinzufügen für:

Fügen Sie Unterstützung für eine der in Visual C++ enthaltenen Bibliotheken hinzu.

|Option|BESCHREIBUNG|
|------------|-----------------|
|**ATL**|Wird in die Projektunterstützung für Klassen in ATL (Active Template Library) integriert. Nur für Win32-Konsolenanwendungen.<br /><br /> **Hinweis** Diese Option gibt keine Unterstützung für das Hinzufügen von ATL-Objekten mithilfe der ATL-Code-Assistenten an. Sie können ATL-Objekte nur zu ATL- oder MFC-Projekten mit ATL-Unterstützung hinzufügen.|
|**MFC**|Wird in die Projektunterstützung für die MFC (Microsoft Foundation Class)-Bibliothek integriert. Nur für Win32-Konsolenanwendungen und statische Bibliotheken.|

## <a name="remarks"></a>Bemerkungen

Nach Erstellung einer Windows-Desktopanwendung können Sie mit dem Assistenten für [generischen](../ide/generic-cpp-class-wizard.md) Code generische C++-Klassen hinzufügen. Sie können weitere Elemente, wie HTML-Dateien, Headerdateien, Ressourcen oder Textdateien, hinzufügen.

> [!NOTE]
> Es können keine ATL-Klassen hinzugefügt werden. MFC-Klassen können nur solchen Windows-Desktopanwendungstypen hinzugefügt werden, die MFC unterstützen (siehe vorangehende Tabelle).

Die vom Assistenten erstellten Projektdateien können im **Projektmappen-Explorer**angezeigt werden. Weitere Informationen zu den Dateien, die der Assistent für das Projekt erstellt, finden Sie in der vom Projekt generierten Datei `ReadMe.txt`. Weitere Informationen zu den Dateitypen finden Sie unter [Dateitypen, die für C++ Visual Studio-Projekte erstellt](../build/reference/file-types-created-for-visual-cpp-projects.md)wurden.

## <a name="see-also"></a>Weitere Informationen

[C++-Projektvorlagen](../build/reference/visual-cpp-project-types.md)

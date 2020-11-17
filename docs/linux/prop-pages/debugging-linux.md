---
title: Debuggereigenschaften (Linux C++) | Microsoft Docs
description: Hier werden die Eigenschaften des Microsoft Visual Studio-Debuggers für Linux C++ beschrieben.
ms.date: 06/07/2019
ms.assetid: 0c1c0fcc-a49b-451c-a5cb-ce9711fac064
ms.openlocfilehash: 0d43877df817f40cfd97a03c4f66730ab17138d8
ms.sourcegitcommit: 12eb6a824dd7187a065d44fceca4c410f58e121e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "94334220"
---
# <a name="c-debugging-properties-linux-c"></a>C++-Debugeigenschaften (Linux C++)

::: moniker range="msvc-140"

Die Unterstützung für Linux ist in Visual Studio 2017 und höher verfügbar.

::: moniker-end

::: moniker range=">=msvc-150"

| Eigenschaft | BESCHREIBUNG | Auswahlmöglichkeiten |
|--|--|--|
| Remotedebugcomputer | **Visual Studio 2019 Version 16.1:** Gibt den Computer an, auf dem das Programm gedebuggt werden soll. Kann sich vom Remotebuildcomputer unterscheiden, der auf der Seite [Allgemein](general-linux.md) angegeben wurde. Sie können eine Zielcomputerverbindung hinzufügen oder bearbeiten, indem Sie **Tools** > **Optionen** > **Plattformübergreifend** > **Verbindungs-Manager** auswählen. |
| Befehl vor dem Start | Ein Befehl, der für die Shell ausgeführt wird, bevor der Debugger startet. Er kann verwendet werden, um die Debugumgebung zu beeinflussen. |
| Program | Der vollständige Pfad zu dem auf dem Remotesystem zu debuggenden Programm. Wenn die Angabe leer oder unverändert gelassen wird, wird standardmäßig die aktuelle Projektausgabe verwendet. |
| Programmargumente | Die Befehlszeilenargumente, die an das zu debuggende Programm übergeben werden sollen. |
| Arbeitsverzeichnis | Das Arbeitsverzeichnis der Remoteanwendung. Standardmäßig ist dies das Basisverzeichnis des Benutzers. |
| Zusätzliche Debuggerbefehle | Zusätzliche `gdb`-Befehle, die der Debugger vor dem Starten des Debuggens ausführt. |
| Debuggerportnummer | Die Portnummer für die Debuggerkommunikation mit dem Remotedebugger. Der Port darf nicht lokal in Gebrauch sein. Dieser Wert muss eine positive Zahl zwischen 1 und 65535 sein. Wenn keine Angabe erfolgt, wird eine freie Portnummer verwendet. |
| Portnummer des Remotedebuggers | Die Portnummer, an der der Remotedebuggerserver (`gdbserver`) auf dem Remotesystem lauscht. Der Port darf auf dem Remotesystem nicht in Gebrauch sein. Dieser Wert muss eine positive Zahl zwischen 1 und 65535 sein. Wenn keine Angabe erfolgt, wird eine freie Portnummer ab 4444 verwendet. |
| Debugmodus | Gibt an, wie der Debugger mit `gdb` kommuniziert. Im *gdb-Modus* steuert der Debugger `gdb` über die Shell auf dem Remotesystem. Im *gdbserver-Modus* wird `gdb` lokal ausgeführt und stellt eine Remoteverbindung zu `gdbserver` her. | **gdbserver**<br/>**gdb** |
| Zusätzliche Symbolsuchpfaden | Zusätzlicher Suchpfad für Debugsymbole (solib-search-path). |
| Untergeordnete Prozesse debuggen | Gibt an, ob Debuggen für untergeordnete Prozesse aktiviert werden soll. |
| Python Pretty Printing aktivieren | Aktiviert Pretty Printing von Ausdruckswerten. Wird nur im GDB-Debugmodus unterstützt. |
| Visualisierungsdatei | Systemeigene Visualisierungsstandarddatei (NATVIS-Datei), die die Visualisierungsdirektiven für SLT-Typen enthält. Andere NATVIS-Dateien, die zur aktuellen Projektmappe gehören, werden automatisch geladen. |
| Zusätzliche Dateipfadzuordnung für Quellen | Zusätzliche Pfadäquivalenzen für den Debugger, um Windows-Quelldateinamen Linux-Quelldateinamen zuzuordnen. Das Format lautet: \<windows-path>=\<linux-path>;.... Auf einen Quelldateinamen, der unter dem Windows-Pfad gefunden wird, wird so verwiesen, als ob er an der gleichen relativen Position unter dem Linux-Pfad gefunden wurde. Dateien, die im lokalen Projekt gefunden werden, benötigen keine zusätzliche Zuordnung. |
| GDB-Pfad | **Visual Studio 2019, Version 16.9**: Gibt den Pfad zur ausführbaren GDB-Datei an, die von Visual Studio verwendet werden soll. |

::: moniker-end

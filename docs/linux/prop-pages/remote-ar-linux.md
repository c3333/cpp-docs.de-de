---
title: Remotearchiveigenschaften (C++ Linux)
ms.date: 06/07/2019
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
f1_keywords: []
ms.openlocfilehash: 9e35c9cc0b8a99e87654f1052e8666c52e35a071
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924448"
---
# <a name="remote-archive-properties-c-linux"></a>Remotearchiveigenschaften (C++ Linux)

::: moniker range="msvc-140"

Die Unterstützung für Linux ist in Visual Studio 2017 und höher verfügbar.

::: moniker-end

::: moniker range=">=msvc-150"

| Eigenschaft | Beschreibung |
|--|--|
| Erstellen eines Archivindex | Einen Archivindex erstellen (vgl. ranlib). Diese Option kann das Verknüpfen beschleunigen und die Abhängigkeit innerhalb der eigenen Bibliothek verringern. |
| Schlankes Archiv erstellen | Erstellt ein schlankes Archiv.  Ein schlankes Archiv enthält relative Pfade zu den Objekten, anstatt die Objekte einzubetten.  Um zwischen schlank und normal zu wechseln, muss die vorhandene Bibliothek gelöscht werden. |
| Keine Warnung beim Erstellen | Gibt keine Warnung aus, falls oder wenn die Bibliothek erstellt wird. |
| Zeitstempel abschneiden | Verwendet NULL für Zeitstempel und UIDs/GIDs. |
| Startbanner unterdrücken | Versionsnummer nicht anzeigen. |
| Ausführlich | Ausführlich |
| Zusätzliche Optionen | Zusätzliche Optionen. |
| Ausgabedatei | Die Option /OUT überschreibt den Standardnamen und den Speicherort des Programms, das die Bibliothek erstellt. |
| Archivierungsprogramm | Gibt das Programm an, das beim Linken statischer Objekte aufgerufen werden soll, oder den Pfad zum Archivierungsprogramm auf dem Remotesystem. |
| Archivierungsprogrammtimeout | Remote-Archivierungsprogrammtimeout in Millisekunden. |
| Ausgabe kopieren | Gibt an, ob die Buildausgabedatei vom Remotesystem auf den lokalen Computer kopiert werden soll. |

::: moniker-end

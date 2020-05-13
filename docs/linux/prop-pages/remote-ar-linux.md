---
title: Remotearchiveigenschaften (C++ Linux)
ms.date: 06/07/2019
ms.assetid: 5ee1e44c-8337-4c3a-b2f3-35e4be954f9f
f1_keywords: []
ms.openlocfilehash: 3b6f71d9cceccf0b0221be46bacb1294d84533cd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364303"
---
# <a name="remote-archive-properties-c-linux"></a>Remotearchiveigenschaften (C++ Linux)

::: moniker range="vs-2015"

Die Unterstützung für Linux ist in Visual Studio 2017 und höher verfügbar.

::: moniker-end

::: moniker range=">=vs-2017"

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

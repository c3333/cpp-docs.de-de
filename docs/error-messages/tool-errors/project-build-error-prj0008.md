---
title: Projektbuildfehler PRJ0008
ms.date: 11/04/2016
f1_keywords:
- PRJ0008
helpviewer_keywords:
- PRJ0008
ms.assetid: 6bf7f17a-d2a8-4826-99c7-d600d846952f
ms.openlocfilehash: 7d1c11ab7539f25d371c0bfbd2853b6155c9661c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192953"
---
# <a name="project-build-error-prj0008"></a>Projektbuildfehler PRJ0008

Die Datei "file" konnte nicht gelöscht werden.

**Stellen Sie sicher, dass die Datei nicht von einem anderen Prozess geöffnet ist und nicht schreibgeschützt ist.**

Beim erneuten Erstellen oder bereinigen löscht C++ Visual alle bekannten zwischen-und Ausgabedateien für den Build sowie alle Dateien, die die Platzhalter Spezifikationen in der Eigenschaft **Erweiterungen zum Löschen bei Clean auf** der Eigenschaften [Seite Allgemeine Konfigurationseinstellungen](../../build/reference/general-property-page-project.md)erfüllen.

Dieser Fehler wird angezeigt, wenn eine C++ Datei von Visual nicht gelöscht werden kann. Um den Fehler zu beheben, machen Sie die Datei und das zugehörige Verzeichnis für den Benutzer, der den Build erstellt, beschreibbar.

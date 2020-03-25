---
title: Projektbuildwarnung PRJ0041
ms.date: 11/04/2016
f1_keywords:
- PRJ0041
helpviewer_keywords:
- PRJ0041
ms.assetid: dc9f4cf9-6bd5-4222-89e8-7802a59bb96b
ms.openlocfilehash: bb6469b1daf193223a9b3361cc3e4bfb96d0c751
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80191930"
---
# <a name="project-build-warning-prj0041"></a>Projektbuildwarnung PRJ0041

Fehlende Abhängigkeit ' Abhängigkeit ' für Datei ' Datei ' wurde nicht gefunden. Das Projekt wird möglicherweise weiterhin erstellt, wird jedoch möglicherweise nicht mehr aktuell angezeigt, bis diese Datei gefunden wird.

Eine Datei (Ressourcen Datei oder IDL/ODL-Datei) enthielt beispielsweise eine include-Anweisung, die vom Projekt System nicht aufgelöst werden konnte.

Da das Projekt System keine Präprozessoranweisungen verarbeitet (z. b. #if), ist die angreifende Anweisung möglicherweise nicht Teil des Builds.

Um diese Warnung zu beheben, löschen Sie den gesamten unnötigen Code in RC-Dateien, oder fügen Sie Platzhalter Dateien mit dem entsprechenden Namen hinzu.

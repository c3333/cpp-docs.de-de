---
title: Projektbuildfehler PRJ0006
ms.date: 11/04/2016
f1_keywords:
- PRJ0006
helpviewer_keywords:
- PRJ0006
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
ms.openlocfilehash: 816355276a203adba1401841ce02eb94a18085b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192782"
---
# <a name="project-build-error-prj0006"></a>Projektbuildfehler PRJ0006

Die temporäre Datei "file" konnte nicht geöffnet werden. Stellen Sie sicher, dass die Datei vorhanden ist und dass das Verzeichnis nicht schreibgeschützt ist.

Visual C++ konnte während des Buildprozesses keine temporäre Datei erstellen. Gründe hierfür sind:

- Kein Temp-Verzeichnis.

- Schreib geschütztes Temp-Verzeichnis.

- Nicht genügend Speicherplatz.

- Der $ (IntDir)-Ordner ist entweder schreibgeschützt oder enthält temporäre Dateien, die schreibgeschützt sind.

Dieser Fehler tritt auch nach dem Fehler Projektbuildfehler PRJ0007 auf: das Ausgabeverzeichnis "Verzeichnis" konnte nicht erstellt werden. Fehler Projektbuildfehler PRJ0007 bedeutet, dass das Verzeichnis "$ (IntDir)" nicht erstellt werden konnte. Dies impliziert, dass die Erstellung temporär Dateien auch fehlschlägt.

Temporäre Dateien werden immer dann erstellt, wenn Sie Folgendes angeben:

- Eine Antwortdatei.

- Ein benutzerdefinierter Buildschritt.

- Ein Buildereignis.

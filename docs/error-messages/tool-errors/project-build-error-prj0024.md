---
title: Projektbuildfehler PRJ0024
ms.date: 08/27/2018
f1_keywords:
- PRJ0024
helpviewer_keywords:
- PRJ0024
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
ms.openlocfilehash: bcfdcce54618acca0e22daa54e95083cf3ee9d50
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192613"
---
# <a name="project-build-error-prj0024"></a>Projektbuildfehler PRJ0024

> Der Unicode-Pfad "*path*" konnte nicht in die ANSI-Codepage des Benutzers übersetzt werden.

*path* ist die ursprüngliche Unicode-Version der Pfad Zeichenfolge. Dieser Fehler kann auftreten, wenn ein Unicode-Pfad vorhanden ist, der für die aktuelle System Codepage nicht direkt in ANSI übersetzt werden kann.

Dieser Fehler kann auftreten, wenn Sie mit einem Projekt arbeiten, das auf einem System mithilfe einer Codepage entwickelt wurde, die sich nicht auf Ihrem Computer befindet.

Die Lösung für diesen Fehler besteht darin, den Pfad für die Verwendung von ANSI-Text zu aktualisieren oder die Codepage auf dem Computer zu installieren und als System Standardwert festzulegen.

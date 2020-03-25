---
title: Projektbuildfehler PRJ0032
ms.date: 11/04/2016
f1_keywords:
- PRJ0032
helpviewer_keywords:
- PRJ0032
ms.assetid: bc6acbea-4041-4237-8b5a-f0434705d89f
ms.openlocfilehash: 62efa0e72c6fbe4bd38983ff0507923392427c04
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192483"
---
# <a name="project-build-error-prj0032"></a>Projektbuildfehler PRJ0032

Die ' Outputs '-Eigenschaft für den benutzerdefinierten Buildschritt auf Projektebene enthielt ' Macro ', das als ' macro_expansion ' ausgewertet wird.

Ein benutzerdefinierter Buildschritt in einem Projekt hatte aufgrund eines Makro Auswertungs Problems wahrscheinlich eine ungültige Ausgabe. Dieser Fehler kann auch bedeuten, dass der Pfad falsch formatiert ist und Zeichen oder Zeichenkombinationen enthält, die in einem Dateipfad unzulässig sind.

Um diesen Fehler zu beheben, korrigieren Sie das Makro, oder korrigieren Sie die Pfadspezifikation. Der ausgewertete Pfad ist ein absoluter Pfad aus dem Projektverzeichnis.

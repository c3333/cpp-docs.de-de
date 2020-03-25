---
title: Projektbuildfehler PRJ0031
ms.date: 11/04/2016
f1_keywords:
- PRJ0031
helpviewer_keywords:
- PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
ms.openlocfilehash: e13236f65aaca778a297cdd2942c07b75dd701d0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192496"
---
# <a name="project-build-error-prj0031"></a>Projektbuildfehler PRJ0031

Die Outputs-Eigenschaft für den benutzerdefinierten Buildschritt für die Datei ' file ' enthielt ' Macro ', das als ' macro_expansion ' ausgewertet wird.

Ein benutzerdefinierter Buildschritt in einer Datei hat wahrscheinlich aufgrund eines Makro Auswertungs Problems eine schlechte Ausgabe verursacht. Dieser Fehler kann auch bedeuten, dass der Pfad falsch formatiert ist und Zeichen oder Zeichenkombinationen enthält, die in einem Dateipfad unzulässig sind.

Um diesen Fehler zu beheben, korrigieren Sie das Makro, oder korrigieren Sie die Pfadspezifikation. Der ausgewertete Pfad ist ein absoluter Pfad aus dem Projektverzeichnis.

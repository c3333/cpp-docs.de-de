---
title: Projektbuildfehler PRJ0033
ms.date: 11/04/2016
f1_keywords:
- PRJ0033
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
ms.openlocfilehash: 141355ac49ec4722e85b5d4c25240e8048a72c9a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192191"
---
# <a name="project-build-error-prj0033"></a>Projektbuildfehler PRJ0033

Die ' zusätzliche Abhängigkeiten '-Eigenschaft für den benutzerdefinierten Buildschritt für die Datei ' file ' enthielt ' Macro ', das als ' macro_expansion ' ausgewertet wird.

Ein benutzerdefinierter Buildschritt in einer Datei enthielt einen Fehler in seiner zusätzlichen Abhängigkeit, wahrscheinlich aufgrund eines Makro Evaluierungs Problems. Dieser Fehler kann auch bedeuten, dass der Pfad falsch formatiert ist und Zeichen oder Zeichenkombinationen enthält, die in einem Dateipfad unzulässig sind.

Um diesen Fehler zu beheben, korrigieren Sie das Makro, oder korrigieren Sie die Pfadspezifikation. Der ausgewertete Pfad ist ein absoluter Pfad aus dem Projektverzeichnis.

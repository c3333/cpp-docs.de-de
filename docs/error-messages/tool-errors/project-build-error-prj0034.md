---
title: Projektbuildfehler PRJ0034
ms.date: 11/04/2016
f1_keywords:
- PRJ0034
helpviewer_keywords:
- PRJ0034
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
ms.openlocfilehash: bcb7e22d6a09e3435eb2236532101a1836c08a03
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192187"
---
# <a name="project-build-error-prj0034"></a>Projektbuildfehler PRJ0034

Die Eigenschaft "zusätzliche Abhängigkeiten" für den benutzerdefinierten Buildschritt auf Projektebene enthielt "Makro", das in "macro_expansion" ausgewertet wird.

Ein benutzerdefinierter Buildschritt in einem Projekt enthielt einen Fehler in seiner zusätzlichen Abhängigkeit, wahrscheinlich aufgrund eines Makro Evaluierungs Problems. Dieser Fehler kann auch bedeuten, dass der Pfad falsch formatiert ist und Zeichen oder Zeichenkombinationen enthält, die in einem Dateipfad unzulässig sind.

Um diesen Fehler zu beheben, korrigieren Sie das Makro, oder korrigieren Sie die Pfadspezifikation. Der ausgewertete Pfad ist ein absoluter Pfad aus dem Projektverzeichnis.

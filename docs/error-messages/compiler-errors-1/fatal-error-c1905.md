---
title: Schwerwiegender Fehler C1905
ms.date: 11/04/2016
f1_keywords:
- C1905
helpviewer_keywords:
- C1905
ms.assetid: fefc6769-477f-45a2-9878-6f0a5f42472c
ms.openlocfilehash: 106dfe8a078047225097686d185a1ba43987ce33
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202625"
---
# <a name="fatal-error-c1905"></a>Schwerwiegender Fehler C1905

Front-End und Back-End sind nicht kompatibel (müssen auf denselben Prozessor ausgerichtet sein).

Dieser Fehler tritt auf, wenn eine OBJ-Datei von einem Compiler-Front-End (C1. dll) generiert wird, das auf einen Prozessor (z. b. x86, Arm oder x64) abzielt, aber von einem Back-End (C2. dll) gelesen wird, das auf einen anderen Prozessor abzielt.

Stellen Sie zur Behebung dieses Problems sicher, dass Front-End und Back-End kompatibel sind. Dies ist die Standardeinstellung für Projekte, die in Visual Studio erstellt wurden. Dieser Fehler kann auftreten, wenn Sie die Projektdatei bearbeitet und dabei verschiedene Pfade zu den Compilertools verwendet haben. Wenn Sie den Pfad für die Compilertools nicht ausdrücklich festgelegt haben, kann dieser Fehler auftreten, wenn die Visual Studio-Installation beschädigt ist. Beispielsweise können Sie Compiler-DLL-Dateien von einem Speicherort zu einem anderen kopiert haben. Verwenden Sie **Programme und Funktionen** in der Windows-Systemsteuerung, um Visual Studio zu reparieren oder neu zu installieren.

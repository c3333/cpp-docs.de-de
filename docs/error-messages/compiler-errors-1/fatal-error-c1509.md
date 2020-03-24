---
title: Schwerwiegender Fehler C1509
ms.date: 11/04/2016
f1_keywords:
- C1509
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
ms.openlocfilehash: 0d1d7255dd64239a6a76bb15a1f309b43eac0d4b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202955"
---
# <a name="fatal-error-c1509"></a>Schwerwiegender Fehler C1509

Compilerlimit: zu viele Ausnahme handlerzustände in der Funktion "Function". Funktion vereinfachen

Der Code überschreitet eine interne Beschränkung für Ausnahmehandlerzustände (32.768 Zustände).

Die häufigste Ursache ist, dass die Funktion einen komplexen Ausdruck von benutzerdefinierten Klassen Variablen und arithmetischen Operatoren enthält.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>So beheben Sie den Fehler (unterschiedliche Lösungsmöglichkeiten)

1. Vereinfachen Sie Ausdrücke, indem Sie temporären Variablen allgemeine Teil Ausdrücke zuweisen.

1. Teilen Sie die Funktion in kleinere Funktionen auf.

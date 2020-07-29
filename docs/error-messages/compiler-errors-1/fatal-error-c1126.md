---
title: Schwerwiegender Fehler C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: 110fbfe984ee7714e0c8ee2e2cb4deec4f43905a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87207926"
---
# <a name="fatal-error-c1126"></a>Schwerwiegender Fehler C1126

"Bezeichner": automatische Zuordnung überschreitet Größe

Der für lokale Variablen einer Funktion zugewiesene Speicherplatz (zuzüglich eines begrenzten Speicherplatzes, wie etwa 20 Bytes für austauschbare Funktionen), überschreitet den Grenzwert.

Um diesen Fehler zu beheben, `malloc` verwenden **`new`** Sie oder, um große Datenmengen zuzuordnen.

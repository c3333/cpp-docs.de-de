---
title: Schwerwiegender Fehler C1126
ms.date: 11/04/2016
f1_keywords:
- C1126
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
ms.openlocfilehash: a6c9d06cd087eb4462ae475cc1f6d64ba451887f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203635"
---
# <a name="fatal-error-c1126"></a>Schwerwiegender Fehler C1126

"Bezeichner": automatische Zuordnung überschreitet Größe

Der für lokale Variablen einer Funktion zugewiesene Speicherplatz (zuzüglich eines begrenzten Speicherplatzes, wie etwa 20 Bytes für austauschbare Funktionen), überschreitet den Grenzwert.

Um diesen Fehler zu beheben, verwenden Sie `malloc` oder `new`, um große Datenmengen zuzuordnen.

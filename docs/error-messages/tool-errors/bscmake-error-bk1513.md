---
title: BSCMAKE-Fehler BK1513
ms.date: 11/04/2016
f1_keywords:
- BK1513
helpviewer_keywords:
- BK1513
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
ms.openlocfilehash: 3a16163f33814be18a67833995362ee9b13d8118
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197638"
---
# <a name="bscmake-error-bk1513"></a>BSCMAKE-Fehler BK1513

nicht inkrementelle Aktualisierung erfordert alle.SBR-Dateien

BSCMAKE kann keine neue Browserinformationsdatei (.bsc) erstellen, weil eine oder mehrere .sbr-Dateien abgeschnitten werden. Um die Namen der abgeschnittene SBR-Dateien zu finden, lesen Sie die [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) -Warnungen, die diesen Fehler begleiten.

BSCMAKE kann eine .bsc-Datei mit einer verkürzten .sbr-Datei aktualisieren, aber eine neue kann nicht erstellt werden. BSCMAKE kann eine neue .bsc-Datei aus den folgenden Gründen erstellen:

- Fehlende .bsc-Datei.

- Falscher Dateiname für .bsc-Datei angegeben.

- Beschädigte .bsc-Datei.

Um dieses Problem zu beheben, löschen Sie die verkürzten .sbr-Dateien und erstellen sie neu oder löschen Sie die Lösung und erstellen sie neu. (Wählen Sie in der IDE **Erstellen**, Projekt Mappe **Bereinigen**aus, und wählen Sie dann **Erstellen**, Projekt Mappe **neu**erstellen aus.)

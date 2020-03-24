---
title: Linkertoolwarnung LNK4020
ms.date: 05/29/2018
f1_keywords:
- LNK4020
helpviewer_keywords:
- LNK4020
ms.openlocfilehash: e818909cc0b590b0f7727846cfd7b469e8bc0e3f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194225"
---
# <a name="linker-tools-warning-lnk4020"></a>Linkertoolwarnung LNK4020

> ein typdatensatz in '*filename*' ist beschädigt. auf einige Symbole und Typen kann vom Debugger möglicherweise nicht zugegriffen werden.

Der *Dateiname* der PDB-Datei weist einen beschädigten typdatensatz auf.

Dieses Problem ist häufig bei anderen Buildproblemen sekundär. Wenn dies das erste gemeldete Buildproblem ist, behandeln Sie zunächst die anderen Fehler und Warnungen. Wenn dies das erste gemeldete Problem ist, müssen Sie möglicherweise Ihre Buildverzeichnisse bereinigen und das Projekt neu erstellen. Wenn Sie parallele Buildprozesse verwenden, prüfen Sie, ob der Fehler weiterhin auftritt, wenn Sie den Build serialisieren.

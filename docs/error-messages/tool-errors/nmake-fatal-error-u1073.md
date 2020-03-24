---
title: 'NMAKE: Schwerwiegender Fehler U1073'
ms.date: 11/04/2016
f1_keywords:
- U1073
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
ms.openlocfilehash: 97d44594540d18bf008757506a9e36e6d16d2cd7
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80182694"
---
# <a name="nmake-fatal-error-u1073"></a>NMAKE: Schwerwiegender Fehler U1073

Sie wissen nicht, wie Sie "TargetName" erstellen

Das angegebene Ziel ist nicht vorhanden, und es ist kein Befehl zum Ausführen oder Ableiten der Regel vorhanden.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>So beheben Sie den Fehler (unterschiedliche Lösungsmöglichkeiten)

1. Überprüfen Sie die Schreibweise des Zielnamens.

1. Wenn *TargetName* ein pseudotarget ist, geben Sie es als Ziel in einem anderen Beschreibungsblock an.

1. Wenn es sich bei *TargetName* um einen Makro Aufruf handelt, stellen Sie sicher, dass es nicht zu einer NULL-Zeichenfolge erweitert wird.

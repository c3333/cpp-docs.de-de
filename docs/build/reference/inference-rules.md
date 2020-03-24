---
title: Rückschlussregeln
ms.date: 11/04/2016
helpviewer_keywords:
- inference rules in NMAKE
- rules, inference
- NMAKE program, inference rules
ms.assetid: caff320f-fb07-4eea-80c3-a6a2133a8492
ms.openlocfilehash: d3d7ca41d96d3845237b445edefff05044dacdc2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170513"
---
# <a name="inference-rules"></a>Rückschlussregeln

Rückschluss Regeln stellen Befehle zum Aktualisieren von Zielen und zum Ableiten von abhängigen Elementen für Ziele bereit. Erweiterungen in einer Rückschluss Regel stimmen mit einem einzelnen Ziel und abhängigen überein, die den gleichen Basis Namen aufweisen. Rückschluss Regeln sind Benutzer definiert oder vordefiniert. Vordefinierte Regeln können neu definiert werden.

, Wenn eine veraltete Abhängigkeit keine Befehle aufweist und wenn [. Suffixe](dot-directives.md) enthält die Erweiterung der abhängigen, NMAKE verwendet eine Regel, deren Erweiterungen dem Ziel und einer vorhandenen Datei im aktuellen oder angegebenen Verzeichnis entsprechen. Wenn mehr als eine Regel mit vorhandenen Dateien übereinstimmt, ist der **. Suffixe** -Liste bestimmt, welche verwendet werden soll. die Listen Priorität wird von links nach rechts herabgelassen. Wenn eine abhängige Datei nicht vorhanden ist und nicht als Ziel in einem anderen Beschreibungsblock aufgeführt ist, kann eine Rückschluss Regel die fehlende Abhängigkeit von einer anderen Datei mit demselben Basisnamen erstellen. Wenn das Ziel eines Beschreibungs Blocks keine abhängigen Elemente oder Befehle aufweist, kann eine Rückschluss Regel das Ziel aktualisieren. Mit Inferenz Regeln kann ein Befehlszeilen Ziel erstellt werden, auch wenn kein Beschreibungsblock vorhanden ist. NMAKE kann eine Regel für eine abgerufene abhängige Abhängigkeit aufrufen, auch wenn eine explizite abhängige Angabe angegeben ist.

## <a name="what-do-you-want-to-know-more-about"></a>Worüber möchten Sie mehr erfahren?

[Definieren einer Regel](defining-a-rule.md)

[Regeln im Batch Modus](batch-mode-rules.md)

[Vordefinierte Regeln](predefined-rules.md)

[Abhergestellte abhängige Elemente und Regeln](inferred-dependents-and-rules.md)

[Rangfolge in Rückschluss Regeln](precedence-in-inference-rules.md)

## <a name="see-also"></a>Weitere Informationen

[NMAKE-Referenz](nmake-reference.md)

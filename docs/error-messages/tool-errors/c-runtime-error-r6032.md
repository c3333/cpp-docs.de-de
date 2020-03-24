---
title: C-Laufzeitfehler R6032
ms.date: 11/04/2016
f1_keywords:
- R6032
helpviewer_keywords:
- R6032
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
ms.openlocfilehash: b29b946d08cff903cf0ca398ba0d7589cb5d54ea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197092"
---
# <a name="c-runtime-error-r6032"></a>C-Laufzeitfehler R6032

Nicht genügend Speicherplatz für Gebiets Schema Informationen.

> [!NOTE]
> Wenn diese Fehlermeldung beim Ausführen einer App angezeigt wird, wurde die APP heruntergefahren, weil Sie über ein internes Speicherproblem verfügt. Es gibt mehrere mögliche Ursachen für diesen Fehler, aber häufig wird er durch einen extrem wenig Arbeitsspeicher oder durch einen Programmfehler verursacht.
>
> Sie können versuchen, diesen Fehler zu beheben, indem Sie folgende Schritte ausführen:
>
> - Schließen Sie andere laufende Anwendungen, oder starten Sie den Computer neu, um Arbeitsspeicher freizugeben.
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um das Programm zu reparieren oder neu zu installieren.
> - Überprüfen Sie **Windows Update** in der **Systemsteuerung** auf Software Updates.
> - Überprüfen Sie, ob eine aktualisierte Version der App angezeigt wird. Wenn das Problem weiterhin besteht, wenden Sie sich an den Anbieter der APP

**Informationen für Programmierer**

Die Laufzeit verwaltet Informationen über das Gebiets Schema auf jedem Thread, sodass Aufrufe an Gebiets Schema bezogene Funktionen verarbeitet werden können. Wenn die Speicher Belegung für diese Informationen fehlschlägt, kann die Laufzeit nicht fortgesetzt werden, da zu viele ihrer grundlegenden Funktionen von ihr abhängig sind.

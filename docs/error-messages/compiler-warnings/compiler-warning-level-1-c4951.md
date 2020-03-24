---
title: Compilerwarnung (Stufe 1) C4951
ms.date: 08/27/2018
f1_keywords:
- C4951
helpviewer_keywords:
- C4951
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
ms.openlocfilehash: d94347df17bac01334cfd85c2bd9f6c8a98b5fc0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174595"
---
# <a name="compiler-warning-level-1-c4951"></a>Compilerwarnung (Stufe 1) C4951

> "*Funktion*" wurde bearbeitet, seit die Profildaten erfasst wurden. die Funktions Profildaten werden nicht verwendet.

Eine Funktion wurde in einem Eingabemodul für [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)bearbeitet, sodass die Profildaten jetzt ungültig sind. Das Eingabemodul wurde nach **/LTCG:PGINSTRUMENT** neu kompiliert und verfügt über eine Funktion (*Funktion*) mit einer anderen Ablaufsteuerung als der, die zum Zeitpunkt des **/LTCG:PGINSTRUMENT** -Vorgangs im Modul enthalten war.

Diese Warnung dient nur zu Informationszwecken. Um diese Warnung zu beheben, führen Sie **/LTCG:PGINSTRUMENT**aus, wiederholen alle Testläufe und führen **/LTCG:PGOPTIMIZE**aus.

Bei Verwendung von **/LTCG:PGOPTIMIZE** würde diese Warnung durch einen Fehler ersetzt.

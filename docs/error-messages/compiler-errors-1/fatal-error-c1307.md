---
title: Schwerwiegender Fehler C1307
ms.date: 11/04/2016
f1_keywords:
- C1307
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
ms.openlocfilehash: c7eb90c8e17408f6898ef7ff1a9d9e5efcafb4fa
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203345"
---
# <a name="fatal-error-c1307"></a>Schwerwiegender Fehler C1307

Das Programm wurde seit dem Erfassen der Profildaten bearbeitet.

Bei Verwendung von [/LTCG: pgoptimiert](../../build/reference/ltcg-link-time-code-generation.md)hat der Linker ein Eingabe Modul erkannt, das nach/LTCG: PGINSTRUMENT neu kompiliert wurde, und das Modul wurde an den Punkt geändert, an dem vorhandene Profildaten nicht mehr relevant sind. Wenn sich das Aufruf Diagramm z. b. im neu kompilierten Modul geändert hat, generiert der Compiler C1307.

Um diesen Fehler zu beheben, führen Sie/LTCG: PGINSTRUMENT aus, wiederholen alle Testläufe und führen/LTCG: pgoptimiert aus. Wenn Sie/LTCG: PGINSTRUMENT nicht ausführen und alle Testläufe wiederholen können, verwenden Sie/LTCG: PGUPDATE anstelle von/LTCG: pgoptimiert, um das optimierte Image zu erstellen.

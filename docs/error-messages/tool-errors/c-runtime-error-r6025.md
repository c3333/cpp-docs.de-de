---
title: C-Laufzeitfehler R6025
ms.date: 11/04/2016
f1_keywords:
- R6025
helpviewer_keywords:
- R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
ms.openlocfilehash: 6e184ba24ad535697a727276a980fd082625e082
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218051"
---
# <a name="c-runtime-error-r6025"></a>C-Laufzeitfehler R6025

reiner virtueller Funktionsaufrufe

> [!NOTE]
> Wenn diese Fehlermeldung beim Ausführen einer App angezeigt wird, wurde die APP aufgrund eines internen Problems heruntergefahren. Der häufigste Grund für diesen Fehler ist ein Fehler in der APP oder eine beschädigte Installation.
>
> Sie können versuchen, diesen Fehler zu beheben, indem Sie folgende Schritte ausführen:
>
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um das Programm zu reparieren oder neu zu installieren.
> - Überprüfen Sie **Windows Update** in der **Systemsteuerung** auf Software Updates.
> - Überprüfen Sie, ob eine aktualisierte Version der App angezeigt wird. Wenn das Problem weiterhin besteht, wenden Sie sich an den Anbieter der APP

**Informationen für Programmierer**

Es wurde kein Objekt zum Verarbeiten des reinen virtuellen Funktions Aufrufes instanziiert.

Dieser Fehler wird ausgelöst, wenn eine virtuelle Funktion in einer abstrakten Basisklasse durch einen Zeiger aufgerufen wird, der durch eine Umwandlung in den Typ der abgeleiteten Klasse erstellt wird, aber tatsächlich ein Zeiger auf die Basisklasse ist. Dies kann bei der Umwandlung von einem **`void`** <strong>\*</strong> in einen Zeiger auf eine Klasse vorkommen, wenn **`void`** <strong>\*</strong> während der Erstellung der Basisklasse erstellt wurde.

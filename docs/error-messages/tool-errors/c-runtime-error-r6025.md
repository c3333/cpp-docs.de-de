---
title: C-Laufzeitfehler R6025
ms.date: 11/04/2016
f1_keywords:
- R6025
helpviewer_keywords:
- R6025
ms.assetid: afa06d98-9c36-445b-b3e7-b6409bc8e779
ms.openlocfilehash: d5edb08278b7b6b9b3eb62e92fc04410f96a8f09
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075125"
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

Dieser Fehler wird ausgelöst, wenn eine virtuelle Funktion in einer abstrakten Basisklasse durch einen Zeiger aufgerufen wird, der durch eine Umwandlung in den Typ der abgeleiteten Klasse erstellt wird, aber tatsächlich ein Zeiger auf die Basisklasse ist. Dies kann vorkommen, wenn die Umwandlung von einem **void**  <strong>-\*</strong> in einen Zeiger auf eine Klasse erfolgt, wenn der **void** -<strong>\*</strong> während der Erstellung der Basisklasse erstellt wurde.

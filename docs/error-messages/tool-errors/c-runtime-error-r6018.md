---
title: C-Laufzeitfehler R6018
ms.date: 11/04/2016
f1_keywords:
- R6018
helpviewer_keywords:
- R6018
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
ms.openlocfilehash: 83ad191fe1518e5e6bab0798840415ef392db71e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197287"
---
# <a name="c-runtime-error-r6018"></a>C-Laufzeitfehler R6018

Unerwarteter Heap Fehler

> [!NOTE]
> Wenn diese Fehlermeldung beim Ausführen einer App angezeigt wird, wurde die APP aufgrund eines internen Problems heruntergefahren. Es gibt mehrere mögliche Ursachen für diesen Fehler, aber häufig wird er durch einen Fehler im App-Code verursacht.
>
> Sie können versuchen, diesen Fehler zu beheben, indem Sie folgende Schritte ausführen:
>
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um das Programm zu reparieren oder neu zu installieren.
> - Überprüfen Sie **Windows Update** in der **Systemsteuerung** auf Software Updates.
> - Überprüfen Sie, ob eine aktualisierte Version der App angezeigt wird. Wenn das Problem weiterhin besteht, wenden Sie sich an den Anbieter der APP

**Informationen für Programmierer**

Unerwarteter Fehler beim Ausführen eines Speicher Verwaltungs Vorgangs durch das Programm.

Dieser Fehler tritt normalerweise auf, wenn das Programm versehentlich die Lauf Zeit Heap Daten ändert. Dies kann jedoch auch durch einen internen Fehler im Lauf Zeit-oder Betriebssystem Code verursacht werden.

Um dieses Problem zu beheben, überprüfen Sie, ob Fehler im Code auf Heap Beschädigung auftreten. Weitere Informationen und Beispiele finden Sie unter [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Überprüfen Sie als nächstes, ob Sie die neuesten verteilbaren Komponenten für Ihre APP-Bereitstellung verwenden. Weitere Informationen finden Sie unter [Bereitstellung C++in Visual ](../../windows/deployment-in-visual-cpp.md).

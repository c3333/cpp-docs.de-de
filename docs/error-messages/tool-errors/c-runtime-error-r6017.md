---
title: C-Laufzeitfehler R6017
ms.date: 11/04/2016
f1_keywords:
- R6017
helpviewer_keywords:
- R6017
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
ms.openlocfilehash: 2d868939425c11f13dffd84e28c1afee45e3b11a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197301"
---
# <a name="c-runtime-error-r6017"></a>C-Laufzeitfehler R6017

unerwarteter Multithread-Sperr Fehler.

> [!NOTE]
> Wenn diese Fehlermeldung beim Ausführen einer App angezeigt wird, wurde die APP aufgrund eines internen Problems heruntergefahren. Es gibt mehrere mögliche Ursachen für diesen Fehler, aber häufig wird er durch einen Fehler im App-Code verursacht.
>
> Sie können versuchen, diesen Fehler zu beheben, indem Sie folgende Schritte ausführen:
>
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um das Programm zu reparieren oder neu zu installieren.
> - Überprüfen Sie **Windows Update** in der **Systemsteuerung** auf Software Updates.
> - Überprüfen Sie, ob eine aktualisierte Version der App angezeigt wird. Wenn das Problem weiterhin besteht, wenden Sie sich an den Anbieter der APP

**Informationen für Programmierer**

Der Prozess hat einen unerwarteten Fehler beim Zugreifen auf eine C-Laufzeit-multithreadsperre für eine System Ressource erhalten. Dieser Fehler tritt normalerweise auf, wenn der Prozess die Laufzeitheap-Daten versehentlich ändert. Sie kann jedoch auch durch einen internen Fehler in der Lauf Zeit Bibliothek oder im Betriebssystem Code verursacht werden.

Um dieses Problem zu beheben, überprüfen Sie, ob Fehler im Code auf Heap Beschädigung auftreten. Weitere Informationen und Beispiele finden Sie unter [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details). Überprüfen Sie als nächstes, ob Sie die neuesten verteilbaren Komponenten für Ihre APP-Bereitstellung verwenden. Weitere Informationen finden Sie unter [Bereitstellung C++in Visual ](../../windows/deployment-in-visual-cpp.md).

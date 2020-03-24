---
title: C-Laufzeitfehler R6019
ms.date: 11/04/2016
f1_keywords:
- R6019
helpviewer_keywords:
- R6019
ms.assetid: 8129923e-7db2-40ee-9602-def9365f8d28
ms.openlocfilehash: b647825b7e856be9dc51a5a652be87a4cc6d0e23
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197261"
---
# <a name="c-runtime-error-r6019"></a>C-Laufzeitfehler R6019

das Konsolen Gerät kann nicht geöffnet werden.

> [!NOTE]
> Wenn diese Fehlermeldung beim Ausführen einer App angezeigt wird, wurde die APP heruntergefahren, weil versucht wurde, auf die Konsole zuzugreifen, aber Sie verfügte nicht über ausreichende Berechtigungen. Es gibt mehrere mögliche Ursachen für diesen Fehler. Dies liegt jedoch in der Regel daran, dass das Programm als Administrator ausgeführt werden muss oder ein Fehler im Programm vorliegt.
>
> Sie können versuchen, diesen Fehler zu beheben, indem Sie folgende Schritte ausführen:
>
> - Führen Sie das Programm als Administrator aus.
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um das Programm zu reparieren oder neu zu installieren.
> - Überprüfen Sie **Windows Update** in der **Systemsteuerung** auf Software Updates.
> - Überprüfen Sie, ob eine aktualisierte Version der App angezeigt wird. Wenn das Problem weiterhin besteht, wenden Sie sich an den Anbieter der APP

**Informationen für Programmierer**

Dieser Fehler tritt auf, weil die APP als Konsolen Funktion bezeichnet wird, das Betriebssystem jedoch keinen Zugriff auf die Konsole gewährt hat. Außer im Debugmodus sind Konsolenfunktionen in Microsoft Store-Apps in der Regel nicht zulässig. Wenn Ihre APP Administratorrechte zum Ausführen erfordert, stellen Sie sicher, dass Sie standardmäßig als Administrator ausgeführt wird.

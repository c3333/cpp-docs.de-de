---
title: C-Laufzeitfehler R6028
ms.date: 11/04/2016
f1_keywords:
- R6028
helpviewer_keywords:
- R6028
ms.assetid: 81e99079-4388-4244-a4f7-4641c508871c
ms.openlocfilehash: 1c165b7c9351e34ef6316962cd90663f2b6152ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197131"
---
# <a name="c-runtime-error-r6028"></a>C-Laufzeitfehler R6028

Heap kann nicht initialisiert werden.

> [!NOTE]
> Wenn diese Fehlermeldung beim Ausführen einer App angezeigt wird, wurde die APP heruntergefahren, weil Sie über ein internes Speicherproblem verfügt. Es gibt viele mögliche Ursachen für diesen Fehler, aber häufig wird er durch einen extrem wenig Arbeitsspeicher, einen Programmfehler oder durch fehlerhafte Hardwaretreiber verursacht.
>
> Sie können versuchen, diesen Fehler zu beheben, indem Sie folgende Schritte ausführen:
>
> - Schließen Sie andere laufende Anwendungen, oder starten Sie den Computer neu, um Arbeitsspeicher freizugeben.
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um das Programm zu reparieren oder neu zu installieren.
> - Wenn die APP vor einer neuen Installation einer anderen APP oder eines Treibers funktioniert, verwenden Sie die Seite **apps und Features** bzw. **Programme und Funktionen** in der **Systemsteuerung** , um die neue APP oder den Treiber zu entfernen, und wiederholen Sie dann die app.
> - Überprüfen Sie die Website des Hardware Anbieters, oder **Windows Update** Sie in der **Systemsteuerung** Software-und Treiber Updates.
> - Überprüfen Sie, ob eine aktualisierte Version der App angezeigt wird. Wenn das Problem weiterhin besteht, wenden Sie sich an den Anbieter der APP

**Informationen für Programmierer**

Dieser Fehler tritt auf, wenn das Betriebssystem den Speicherpool für die Anwendung nicht erstellen konnte. Das heißt, CRT (C Runtime) hat die Win32-Funktion `HeapCreate` aufgerufen, die NULL zurückgibt und auf einen Fehler hinweist.

Wenn dieser Fehler während des Starts der App auftritt, kann das System die Heapanforderungen möglicherweise nicht erfüllen, da fehlerhafte Treiber geladen werden. Aktualisierte Treiber finden Sie unter Windows Update oder auf der Website des Hardwareherstellers.

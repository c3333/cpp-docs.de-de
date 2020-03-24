---
title: C-Laufzeitfehler R6026
ms.date: 11/04/2016
f1_keywords:
- R6026
helpviewer_keywords:
- R6026
ms.assetid: 7ea751f8-fc20-46ab-99ef-84c95ca0b6b4
ms.openlocfilehash: c0f2f6371933d118bf52328726fb2c68907c2666
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197183"
---
# <a name="c-runtime-error-r6026"></a>C-Laufzeitfehler R6026

nicht genügend Speicherplatz für die Stdio-Initialisierung.

> [!NOTE]
> Wenn diese Fehlermeldung beim Ausführen einer App angezeigt wird, wurde die APP heruntergefahren, weil Sie über ein internes Speicherproblem verfügt. Es gibt mehrere mögliche Ursachen für diesen Fehler, aber in der Regel wird er durch einen extrem wenig Arbeitsspeicher verursacht. Dies kann auch durch einen Fehler in der APP verursacht werden, durch Beschädigung der visuellen C++ Bibliotheken, die es verwendet, oder durch einen Treiber.
>
> Sie können versuchen, diesen Fehler zu beheben, indem Sie folgende Schritte ausführen:
>
> - Schließen Sie andere laufende Anwendungen, oder starten Sie den Computer neu, um Arbeitsspeicher freizugeben.
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um das Programm zu reparieren oder neu zu installieren.
> - Wenn die APP vor einer neuen Installation einer anderen APP oder eines Treibers funktioniert, verwenden Sie die Seite **apps und Features** bzw. **Programme und Funktionen** in der **Systemsteuerung** , um die neue APP oder den Treiber zu entfernen, und wiederholen Sie dann die app.
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um alle Kopien von Microsoft Visual C++ Redistributable zu reparieren oder neu zu installieren.
> - Überprüfen Sie **Windows Update** in der **Systemsteuerung** auf Software Updates.
> - Überprüfen Sie, ob eine aktualisierte Version der App angezeigt wird. Wenn das Problem weiterhin besteht, wenden Sie sich an den Anbieter der APP

**Informationen für Programmierer**

Dieser Fehler tritt auf, wenn nicht genügend freier Arbeitsspeicher verfügbar ist, um die Standard-e/a-Unterstützung in der C-Laufzeit zu initialisieren. Dieser Fehler tritt normalerweise beim Starten der APP auf. Vergewissern Sie sich, dass Ihre APP und die von ihr Auslastungs Treiber und DLLs den Heap beim Start nicht beschädigen.

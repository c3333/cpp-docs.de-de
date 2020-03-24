---
title: C-Laufzeitfehler R6027
ms.date: 11/04/2016
f1_keywords:
- R6027
helpviewer_keywords:
- R6027
ms.assetid: c06a62b3-08d9-4bf5-bcad-8340ec552f69
ms.openlocfilehash: 8c2aab7b090dbfa4553b8d1622f13aef13f58aa3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197170"
---
# <a name="c-runtime-error-r6027"></a>C-Laufzeitfehler R6027

nicht genügend Speicherplatz für die Lowio-Initialisierung.

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

Dieser Fehler tritt auf, wenn nicht genügend freier Arbeitsspeicher verfügbar ist, um die e/a-Unterstützung auf niedriger Ebene in der C-Laufzeit zu initialisieren. Dieser Fehler tritt normalerweise beim Starten der APP auf. Vergewissern Sie sich, dass Ihre APP und die von ihr Auslastungs Treiber und DLLs den Heap beim Start nicht beschädigen.

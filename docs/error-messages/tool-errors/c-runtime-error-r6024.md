---
title: C-Laufzeitfehler R6024
ms.date: 11/04/2016
f1_keywords:
- R6024
helpviewer_keywords:
- R6024
ms.assetid: 0fb11c0f-9b81-4cab-81bd-4785742946a5
ms.openlocfilehash: de89d2e9e2b34f40b906a5dacca4179eade23f7e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197196"
---
# <a name="c-runtime-error-r6024"></a>C-Laufzeitfehler R6024

nicht genügend Speicherplatz für _onexit/atexit-Tabelle.

> [!NOTE]
> Wenn diese Fehlermeldung beim Ausführen einer App angezeigt wird, wurde die APP heruntergefahren, weil Sie über ein internes Speicherproblem verfügt. Dieser Fehler wird normalerweise durch einen extrem wenig Arbeitsspeicher oder nur selten durch einen Programmfehler oder durch Beschädigungen der von ihm verwendeten visuellen C++ Bibliotheken verursacht.
>
> Sie können versuchen, diesen Fehler zu beheben, indem Sie folgende Schritte ausführen:
>
> - Schließen Sie andere laufende Anwendungen, oder starten Sie den Computer neu, um Arbeitsspeicher freizugeben.
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um das Programm zu reparieren oder neu zu installieren.
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um alle Kopien von Microsoft Visual C++ Redistributable zu reparieren oder neu zu installieren.
> - Überprüfen Sie **Windows Update** in der **Systemsteuerung** auf Software Updates.
> - Überprüfen Sie, ob eine aktualisierte Version der App angezeigt wird. Wenn das Problem weiterhin besteht, wenden Sie sich an den Anbieter der APP

**Informationen für Programmierer**

Dieser Fehler tritt auf, weil für die `_onexit`-oder `atexit`-Funktion kein Arbeitsspeicher verfügbar war. Dieser Fehler wird durch einen Mangel an Arbeitsspeicher verursacht. Möglicherweise sollten Sie Puffer beim Starten der APP vorab zuordnen, um das Speichern von Benutzerdaten und das Ausführen einer sauberen App-Beendigung in Bedingungen mit geringem Arbeitsspeicher zu unterstützen.

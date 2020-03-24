---
title: C-Laufzeitfehler R6008
ms.date: 11/04/2016
f1_keywords:
- R6008
helpviewer_keywords:
- R6008
ms.assetid: f0f304fc-709a-4843-bc7e-bad1ae0d1649
ms.openlocfilehash: 214b6548cc7a3b880223503c2f3e9222d64212ca
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197392"
---
# <a name="c-runtime-error-r6008"></a>C-Laufzeitfehler R6008

nicht genügend Speicherplatz für Argumente.

> [!NOTE]
> Wenn diese Fehlermeldung beim Ausführen einer App angezeigt wird, wurde die APP heruntergefahren, weil Sie über ein internes Speicherproblem verfügt. Es gibt mehrere mögliche Ursachen für diesen Fehler, aber häufig wird er durch einen extrem wenig Arbeitsspeicher oder durch Umgebungsvariablen oder durch einen Programmfehler verursacht.
>
> Sie können versuchen, diesen Fehler zu beheben, indem Sie folgende Schritte ausführen:
>
> - Schließen Sie andere laufende Anwendungen, oder starten Sie den Computer neu, um Arbeitsspeicher freizugeben.
> - Reduzieren Sie die Anzahl und Größe der Befehlszeilenargumente für die app.
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um das Programm zu reparieren oder neu zu installieren.
> - Überprüfen Sie **Windows Update** in der **Systemsteuerung** auf Software Updates.
> - Überprüfen Sie, ob eine aktualisierte Version der App angezeigt wird. Wenn das Problem weiterhin besteht, wenden Sie sich an den Anbieter der APP

**Informationen für Programmierer**

Genügend Arbeitsspeicher zum Laden des Programms, aber nicht genügend Arbeitsspeicher, um das **argv** -Array zu erstellen. Dies kann durch extrem wenig Arbeitsspeicher oder durch ungewöhnlich große Befehlszeilen oder die Verwendung von Umgebungsvariablen verursacht werden. Sehen Sie sich eine der folgenden Lösungen an:

- Erhöhen Sie die Menge an Arbeitsspeicher, die dem Programm zur Verfügung steht.

- Reduzieren Sie die Anzahl und Größe der Befehlszeilenargumente.

- Reduzieren Sie die Umgebungs Größe, indem Sie unnötige Variablen entfernen.

---
title: C-Laufzeitfehler R6009
ms.date: 11/04/2016
f1_keywords:
- R6009
helpviewer_keywords:
- R6009
ms.assetid: edfb1f8b-3807-48f4-a994-318923b747ae
ms.openlocfilehash: 64391f8ec05a99bb85a9d6cd00d6488a945fdb62
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197352"
---
# <a name="c-runtime-error-r6009"></a>C-Laufzeitfehler R6009

nicht genügend Speicherplatz für die Umgebung.

> [!NOTE]
> Wenn diese Fehlermeldung beim Ausführen einer App angezeigt wird, wurde die APP heruntergefahren, weil Sie über ein internes Speicherproblem verfügt. Es gibt mehrere mögliche Ursachen für diesen Fehler, aber häufig wird er durch einen extrem wenig Arbeitsspeicher oder durch Umgebungsvariablen oder durch einen Programmfehler verursacht.
>
> Sie können versuchen, diesen Fehler zu beheben, indem Sie folgende Schritte ausführen:
>
> - Schließen Sie andere laufende Anwendungen, oder starten Sie den Computer neu, um Arbeitsspeicher freizugeben.
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um das Programm zu reparieren oder neu zu installieren.
> - Überprüfen Sie **Windows Update** in der **Systemsteuerung** auf Software Updates.
> - Überprüfen Sie, ob eine aktualisierte Version der App angezeigt wird. Wenn das Problem weiterhin besteht, wenden Sie sich an den Anbieter der APP

**Informationen für Programmierer**

Zum Laden des Programms war ausreichend Arbeitsspeicher verfügbar, aber nicht genügend Arbeitsspeicher, um das **arvp** -Array zu erstellen.  Dies kann durch extrem wenig Arbeitsspeicher oder durch ungewöhnlich große Umgebungsvariablen verursacht werden. Sehen Sie sich eine der folgenden Lösungen an:

- Erhöhen Sie die Menge an Arbeitsspeicher, die dem Programm zur Verfügung steht.

- Reduzieren Sie die Anzahl und Größe der Befehlszeilenargumente.

- Reduzieren Sie die Umgebungs Größe, indem Sie unnötige Variablen entfernen.

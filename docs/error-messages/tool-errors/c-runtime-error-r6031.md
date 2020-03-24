---
title: C-Laufzeitfehler R6031
ms.date: 11/04/2016
f1_keywords:
- R6031
helpviewer_keywords:
- R6031
ms.assetid: 805d4cd1-cb2f-43fe-87e6-e7bd5b7329c5
ms.openlocfilehash: 4b75b0855f0f0d60304cfe8b7a00b4ce27a8daab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197105"
---
# <a name="c-runtime-error-r6031"></a>C-Laufzeitfehler R6031

Versuchen Sie, die CRT mehrmals zu initialisieren. Dies weist auf einen Fehler in der Anwendung hin.

> [!NOTE]
> Wenn diese Fehlermeldung beim Ausführen einer App angezeigt wird, wurde die APP aufgrund eines internen Problems heruntergefahren. Dies kann auf einen Fehler in der APP oder auf einen Fehler in einem Add-on oder einer Erweiterung zurückzuführen sein, das von der APP verwendet wird.
>
> Sie können versuchen, diesen Fehler zu beheben, indem Sie folgende Schritte ausführen:
>
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um das Programm zu reparieren oder neu zu installieren.
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um alle von der APP verwendeten Add-on-oder Erweiterungsprogramme zu entfernen, zu reparieren oder neu zu installieren.
> - Überprüfen Sie **Windows Update** in der **Systemsteuerung** auf Software Updates.
> - Überprüfen Sie, ob eine aktualisierte Version der App angezeigt wird. Wenn das Problem weiterhin besteht, wenden Sie sich an den Anbieter der APP

**Informationen für Programmierer**

Diese Diagnose gibt an, dass MSIL-Anweisungen während der Loadersperre ausgeführt wurden. Weitere Informationen finden Sie unter [Initialisierung gemischter](../../dotnet/initialization-of-mixed-assemblies.md)Assemblys.

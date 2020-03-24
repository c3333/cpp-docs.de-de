---
title: C-Laufzeitfehler R6033
ms.date: 11/04/2016
f1_keywords:
- R6033
helpviewer_keywords:
- R6033
ms.assetid: f9cffdc9-81bd-4a64-a698-02762cbd82c9
ms.openlocfilehash: 86ac98a2635975b811c7b50020e4d4782675ae4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197016"
---
# <a name="c-runtime-error-r6033"></a>C-Laufzeitfehler R6033

Versuch der Verwendung von MSIL-Code aus dieser Assembly während der Initialisierung von System eigenem Code. Dies weist auf einen Fehler in der Anwendung hin. Dies ist wahrscheinlich das Ergebnis des Aufrufs einer MSIL-kompilierten (/CLR)-Funktion aus einem systemeigenen Konstruktor oder aus DllMain.

> [!NOTE]
> Wenn diese Fehlermeldung beim Ausführen einer App angezeigt wird, wurde die APP aufgrund eines internen Problems heruntergefahren. Dieser Fehler kann durch einen Fehler in der APP oder durch einen Fehler in einem Add-in oder einer Erweiterung verursacht werden, der verwendet wird.
>
> Sie können versuchen, diesen Fehler zu beheben, indem Sie folgende Schritte ausführen:
>
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um das Programm zu reparieren oder neu zu installieren.
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um Erweiterungen oder Add-Ins zu entfernen, zu reparieren oder neu zu installieren.
> - Überprüfen Sie **Windows Update** in der **Systemsteuerung** auf Software Updates.
> - Überprüfen Sie, ob eine aktualisierte Version der App angezeigt wird. Wenn das Problem weiterhin besteht, wenden Sie sich an den Anbieter der APP

**Informationen für Programmierer**

Diese Diagnose gibt an, dass MSIL-Anweisungen während der Loadersperre ausgeführt wurden. Dies kann vorkommen, wenn Sie Native C++ mithilfe des/CLR-Flags kompiliert haben. Verwenden Sie nur das/CLR-Flag für Module, die verwalteten Code enthalten. Weitere Informationen finden Sie unter [Initialisierung gemischter](../../dotnet/initialization-of-mixed-assemblies.md)Assemblys.

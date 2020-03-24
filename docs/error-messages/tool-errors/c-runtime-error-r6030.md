---
title: C-Laufzeitfehler R6030
ms.date: 11/04/2016
f1_keywords:
- R6030
helpviewer_keywords:
- R6030
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
ms.openlocfilehash: 5d7160623d4e1eb83240c09e637c780fefc0d43d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/24/2020
ms.locfileid: "80197118"
---
# <a name="c-runtime-error-r6030"></a>C-Laufzeitfehler R6030

CRT nicht initialisiert

> [!NOTE]
> Wenn diese Fehlermeldung beim Ausführen einer App angezeigt wird, wurde die APP aufgrund eines internen Problems heruntergefahren. Dieses Problem wird häufig durch bestimmte Sicherheitssoftware Programme oder selten durch einen Programmfehler verursacht.
>
> Sie können versuchen, diesen Fehler zu beheben, indem Sie folgende Schritte ausführen:
>
> - Die Sicherheitssoftware kann bestimmte Anweisungen zum Beheben dieses Problems enthalten. Weitere Informationen finden Sie auf der Website Ihres Security Software Vendor. Alternativ dazu können Sie auch nach aktualisierten Versionen Ihrer Sicherheitssoftware suchen oder verschiedene Sicherheitssoftware ausprobieren.
> - Verwenden Sie die Seite **apps und Features** oder **Programme und Features** in der **Systemsteuerung** , um das Programm zu reparieren oder neu zu installieren.
> - Überprüfen Sie **Windows Update** in der **Systemsteuerung** auf Software Updates.
> - Überprüfen Sie, ob eine aktualisierte Version der App angezeigt wird. Wenn das Problem weiterhin besteht, wenden Sie sich an den Anbieter der APP

**Informationen für Programmierer**

Dieser Fehler tritt auf, wenn Sie die C-Laufzeit (CRT) verwenden, der CRT-Startcode jedoch nicht ausgeführt wurde. Dieser Fehler kann auftreten, wenn der Linkerschalter [/Entry](../../build/reference/entry-entry-point-symbol.md) verwendet wird, um die Standard Startadresse außer Kraft zu setzen, normalerweise **mainCRTStartup**, **wmainCRTStartup** für eine Konsolen-exe, **WinMainCRTStartup** oder **wWinMainCRTStartup** für eine Windows-exe-Datei oder **_DllMainCRTStartup** für eine DLL. Die C-Laufzeit wird nicht initialisiert, es sei denn, eine der oben genannten Funktionen wird beim Start aufgerufen. Diese Startfunktionen werden normalerweise standardmäßig aufgerufen, wenn Sie eine Verknüpfung mit der C-Lauf Zeit Bibliothek herstellen und die normalen **Haupt**-, **wmain**-, **WinMain**-oder **DllMain** -Einstiegspunkte verwenden.

Dieser Fehler kann auch auftreten, wenn ein anderes Programmcode einschleusungs Techniken verwendet, um bestimmte dll-Bibliotheks Aufrufe zu übernehmen. Für einige eindringliche Sicherheitsprogramme wird dieses Verfahren verwendet. In Visual C++ Studio-Versionen vor Visual Studio 2015 ist es möglich, eine statisch verknüpfte CRT-Bibliothek zu verwenden, um das Problem zu beheben. Dies wird jedoch aus Gründen der Sicherheits-und Anwendungs Updates nicht empfohlen. Um dieses Problem zu beheben, ist möglicherweise eine Benutzeraktion erforderlich.

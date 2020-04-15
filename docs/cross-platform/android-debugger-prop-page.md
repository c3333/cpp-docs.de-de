---
title: Android-Debuggereigenschaften (C++)
ms.date: 10/23/2017
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: 23fd871f030593607cf374870b96e09d8bc2da7a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374204"
---
# <a name="android-debugger-properties"></a>Android-Debuggereigenschaften

| Eigenschaft | BESCHREIBUNG | Auswahl |
|--|--|--|
| Debuggertyp | Gibt den Codetyp an, der debuggt werden soll. | **Nur Native**<br /><br />**Nur Java** |
| Debugziel | Gibt den Emulator oder das Gerät an, das zum Debuggen verwendet werden soll. Wenn keine Emulatoren ausgeführt werden, verwenden Sie "Android Virtual Device (AVD) Manager", um ein Gerät zu starten. |
| Zu startendes Paket | Gibt den Speicherort der *.apk* an, die gedebuggen wird. Diese Option startet das Paket (APK), wenn die Anwendung gedebuggt wird. |
| Starten der Aktivität | Die Android-Aktivität, die zum Start der Anwendung verwendet wird, muss mit der im Anwendungsmanifest verwendeten Aktivität übereinstimmen. Drücken Sie Anwenden, um die Liste von *AndroidManifest.xml* abzurufen und dynamisch aufzufüllen. |
| Zusätzliche Symbolsuchpfaden | Zusätzlicher Suchpfad für Debugsymbole |
| Zusätzliche Suchpfade für Java-Quellen | Zusätzliche Suchpfade für Java-Quelldateien. (Gilt nur, wenn Debuggertyp „nur Java“ ist.) |

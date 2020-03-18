---
title: Android-Debugger-C++Eigenschaften ()
ms.date: 10/23/2017
ms.assetid: 789f7a1c-38b4-41d0-809b-14f4d96c8116
f1_keywords:
- VC.Project.AndroidDebugger.DebuggerType
- VC.Project.AndroidDebugger.AndroidDeviceID
- VC.Project.AndroidDebugger.PackagePath
- VC.Project.AndroidDebugger.LaunchActivity
ms.openlocfilehash: 3ac896b384181e4e2b436368f39a343d35fe321a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79470274"
---
# <a name="android-debugger-properties"></a>Android-Debuggereigenschaften

| Eigenschaft | BESCHREIBUNG | Auswahl |
|--|--|--|
| Debuggertyp | Gibt den Codetyp an, der debuggt werden soll. | **Nur systemeigen**<br /><br />**Nur Java** |
| Debugziel | Gibt den Emulator oder das Gerät an, das zum Debuggen verwendet werden soll. Wenn keine Emulatoren ausgeführt werden, verwenden Sie "Android Virtual Device (AVD) Manager", um ein Gerät zu starten. |
| Zu startendes Paket | Gibt den Speicherort der *APK*-Datei an, für die das Debugging ausgeführt wird. Mit dieser Option wird das Paket (APK) beim debuggten der Anwendung gestartet. |
| Starten der Aktivität | Die Android-Aktivität, die zum Start der Anwendung verwendet wird, muss mit der im Anwendungsmanifest verwendeten Aktivität übereinstimmen. Drücken Sie auf „Apply“ (Anwenden), um die Liste aus *AndroidManifest.xml* abzurufen und dynamisch aufzufüllen. |
| Zusätzliche Symbolsuchpfade | Zusätzlicher Suchpfad für Debugsymbole |
| Zusätzliche Suchpfade für Java-Quellen | Zusätzliche Suchpfade für Java-Quelldateien. (Gilt nur, wenn Debuggertyp „nur Java“ ist.) |

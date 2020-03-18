---
title: Allgemeine Projekteigenschaften (Android C++)
ms.date: 10/23/2017
ms.assetid: 65f4868b-b864-4989-a275-1e51869ef599
f1_keywords:
- VC.Project.VCConfiguration.Android.OutputDirectory
- VC.Project.VCConfiguration.Android.IntermediateDirectory
- VC.Project.VCConfiguration.Android.TargetName
- VC.Project.VCConfiguration.Android.TargetExt
- VC.Project.VCConfiguration.Android.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.Android.BuildLogFile
- VC.Project.VCConfiguration.Android.PlatformToolset
- VC.Project.VCConfiguration.Android.ConfigurationType
- VC.Project.VCConfiguration.UseOfSTL
- VC.Project.VCConfiguration.ThumbMode
ms.openlocfilehash: 78f6df8286151b61ed026cc6b5170ff3508295d4
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2020
ms.locfileid: "79470268"
---
# <a name="general-project-properties-android-c"></a>Allgemeine Projekteigenschaften (Android C++)

| Eigenschaft | BESCHREIBUNG | Auswahl |
|--|--|--|
| Ausgabeverzeichnis | Gibt einen relativen Pfad zum Ausgabedateiverzeichnis an. Kann Umgebungsvariablen enthalten. |
| Zwischenverzeichnis | Gibt einen relativen Pfad zum Zwischendateiverzeichnis an. Kann Umgebungsvariablen enthalten. |
| Zielname | Gibt einen Dateinamen an, den dieses Projekt generiert. |
| Zielerweiterung | Gibt eine Dateierweiterung an, die von diesem Projekt generiert wird. (Beispiel: *.exe* oder *.dll*) |
| Bei der Bereinigung zu löschende Erweiterungen | Durch Semikolons getrennte Platzhalterspezifikation, die angibt, welche Dateien im Zwischenverzeichnis beim Bereinigen oder erneuten Erstellen gelöscht werden sollen. |
| Buildprotokolldatei | Gibt die zu schreibende Buildprotokolldatei an, wenn die Buildprotokollierung aktiviert ist. |
| Plattformtoolset | Gibt das Toolset zum Erstellen der aktuellen Konfiguration an. Wenn keine Angabe erfolgt, wird das Standardtoolset verwendet. |
| Konfigurationstyp | Gibt den Typ der Ausgabe an, die diese Konfiguration generiert. | **Dynamische Bibliothek (.so)** : Dynamische Bibliothek ( *.so*)<br>**Statische Bibliothek (.a)** : Statische Bibliothek ( *.a*)<br>**Hilfsprogramm**: Hilfsprogramm<br>**Makefile**: Makefile<br> |
| API-Zielebene | API-Ebene des Android NDK, die diese Konfiguration als Ziel hat. |
| Verwendung von STL | Gibt an, welche C++-Standardbibliothek für diese Konfiguration verwendet werden soll. | **Minimale C++-Laufzeitbibliothek (system)**<br>**C++-Laufzeit statische Bibliothek (gabi++_static)**<br>**C++-Laufzeit freigegebene Bibliothek (gabi++_shared)**<br>**STLport-Laufzeit statische Bibliothek (stlport_static)**<br>**STLport-Laufzeit freigegebene Bibliothek (stlport_shared)**<br>**GNU STL statische Bibliothek (gnustl_static)**<br>**GNU STL freigegebene Bibliothek (gnustl_shared)**<br>**LLVM libc++ statische Bibliothek (c++_static)**<br>**LLVM libc++ freigegebene Bibliothek (c++_shared)**<br> |
| Thumb-Modus | Generieren Sie Code, der für die Thumb-Mikroarchitektur ausgeführt wird. Dies gilt nur für die ARM-Architektur. | **Thumb**<br>**Arm**<br>**Disabled**<br> |

---
title: 'Eigenschaftenseite für benutzerdefinierten Buildschritt: Allgemein'
description: In diesem Artikel werden die Eigenschaften beschrieben, die im Dialogfeld Eigenschaften Seiten auf der Seite benutzerdefinierter Buildschritt verfügbar sind.
ms.date: 10/27/2020
f1_keywords:
- VC.Project.VCCustomBuildStep.AdditionalInputs
- VC.Project.VCCustomBuildStep.CustomBuildAfterTargets
- VC.Project.VCCustomBuildStep.CustomBuildBeforeTargets
- VC.Project.VCCustomBuildStep.Outputs
- VC.Project.VCCustomBuildStep.Message
- VC.Project.VCCustomBuildStep.Command
helpviewer_keywords:
- project properties, custom build step
- custom build step (general)
ms.assetid: bd319741-0491-46c4-a428-7c61b4b46a02
ms.openlocfilehash: 53f2deef931821981b3301f44ba37660975fb811
ms.sourcegitcommit: 9c801a43ee0d4d84956b03fd387716c818705e0d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2020
ms.locfileid: "92907583"
---
# <a name="custom-build-step-property-page-general"></a>Eigenschaftenseite für benutzerdefinierten Buildschritt: Allgemein

Für jede Projekt Konfiguration und Ziel Platt Form Kombination in Ihrem Projekt können Sie einen benutzerdefinierten Schritt angeben, der beim Erstellen des Projekts ausgeführt werden soll.

Die Linux-Version dieser Seite finden Sie unter [Benutzerdefinierte Buildschritteigenschaften (Linux C++)](../../linux/prop-pages/custom-build-step-linux.md).

## <a name="general-page"></a>Seite „Allgemein“

- **Befehlszeile**

   Der vom benutzerdefinierten Buildschritt auszuführende Befehl.

- **Beschreibung**

   Eine Meldung, die anzeigt, wann der benutzerdefinierte Buildschritt läuft.

- **Ausgaben**

   Die Ausgabedatei, die der benutzerdefinierte Buildschritt generiert. Diese Einstellung ist erforderlich, damit inkrementelle Builds ordnungsgemäß funktionieren.

- **Zusätzliche Abhängigkeiten**

   Eine durch Semikolons getrennte Liste von zusätzlichen Eingabedateien, die für den benutzerdefinierten Buildschritt verwendet werden soll.

- **Im Anschluss ausführen und vorher ausführen**

   Diese Optionen definieren, wann ein benutzerdefinierter Buildschritt im Buildprozess relativ zu den aufgelisteten Zielen ausgeführt wird. Die am häufigsten aufgelisteten Ziele sind `BuildGenerateSources` , `BuildCompile` und `BuildLink` , da Sie die Hauptschritte im Buildprozess darstellen. Andere häufig aufgelistete Ziele sind `Midl` , `CLCompile` und `Link` .

- **Ausgabe als Inhalt behandeln**

   Diese Option ist nur für universelle Windows-Plattform-oder Windows Phone-apps von Bedeutung, die alle Inhalts Dateien im *`.appx`* Paket enthalten.

### <a name="to-specify-a-custom-build-step"></a>So legen Sie einen benutzerdefinierten Buildschritt fest

1. Klicken Sie in der Menüleiste auf **Projekt** > **Eigenschaften** . Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Navigieren Sie im Dialogfeld Eigenschaften **Seiten** zur Seite **Konfigurations Eigenschaften**  >  **benutzerdefinierter Buildschritt**  >  **Allgemein** .

1. Ändern Sie die Einstellungen.

## <a name="see-also"></a>Siehe auch

[Windows C++-Projekteigenschaftenseitenverweis](property-pages-visual-cpp.md)

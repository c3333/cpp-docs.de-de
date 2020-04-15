---
title: 'Vererbung von Eigenschaften in Visual Studio-Projekten: C++'
description: Funktionsweise der Eigenschaftsvererbung in systemeigenen Visual Studio C++-Projekten (MSBuild).
ms.date: 02/21/2020
helpviewer_keywords:
- C++ projects, property inheritance
ms.openlocfilehash: 4740c479c6cc7c877fd72b7828a8e4811826de6c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328479"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Vererbung von Eigenschaften in Visual Studio-Projekten

Das native Visual Studio-Projektsystem basiert auf MSBuild. MSBuild definiert Dateiformate und Regeln für das Erstellen von Projekten jeglicher Art. Es verwaltet den größten Teil der Komplexität des Erstellens für mehrere Konfigurationen und Plattformen. Sie werden es nützlich finden, um zu verstehen, wie es funktioniert. Dies ist besonders wichtig, wenn Sie benutzerdefinierte Konfigurationen definieren möchten. Oder um wiederverwendbare Eigenschaftensätze zu erstellen, die Sie freigeben und in mehrere Projekte importieren können.

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>Die VCXPROJ-Datei, PROPS- und TARGETS-Dateien

Projekteigenschaften werden entweder direkt in*`.vcxproj`* der Projektdatei *`.targets`* *`.props`* ( ) oder in anderen Dateien gespeichert, die die Projektdatei importiert und die Standardwerte bereitstellen. Für Visual Studio 2015 befinden *`\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140`* sich diese Dateien in . Für Visual Studio 2017 befinden *`\Program Files (x86)\Microsoft Visual Studio\2017\<edition>\Common7\IDE\VC\VCTargets`* sich *`<edition>`* diese Dateien in , in dem die Visual Studio-Edition installiert ist. In Visual Studio 2019 befinden *`\Program Files (x86)\Microsoft Visual Studio\2019\<edition>\MSBuild\Microsoft\VC\v160`* sich diese Dateien in . Eigenschaften werden auch in *`.props`* allen benutzerdefinierten Dateien gespeichert, die Sie Ihrem eigenen Projekt hinzufügen können. Es wird dringend empfohlen, diese Dateien NICHT manuell zu bearbeiten. Verwenden Sie stattdessen die Eigenschaftenseiten in der IDE, um alle Eigenschaften zu ändern, insbesondere diejenigen, die an der Vererbung beteiligt sind, es sei denn, Sie haben ein tiefes Verständnis von MSBuild.

Wie zuvor beschrieben kann der gleichen Eigenschaft für die gleiche Konfiguration in verschiedenen Dateien ein anderer Wert zugewiesen werden. Wenn Sie ein Projekt erstellen, wertet die MSBuild-Engine die Projektdatei und alle importierten Dateien in einer klar definierten Reihenfolge (siehe unten) aus. Während die Dateien ausgewertet werden, überschreiben alle Eigenschaftswerte, die in den Dateien definiert sind, die vorhandenen Werte. Alle Werte, die nicht angegeben sind, werden von Dateien geerbt, die zuvor ausgewertet wurden. Wenn Sie eine Eigenschaft mit Eigenschaftenseiten festlegen, ist es auch wichtig, darauf zu achten, wo Sie sie festlegen. Wenn Sie eine Eigenschaft in einer *`.props`* Datei auf "X" festlegen, die Eigenschaft jedoch in der Projektdatei auf "Y" festgelegt ist, wird das Projekt mit der Eigenschaft "Y" erstellt. Wenn dieselbe Eigenschaft für ein Projektelement, z. B. eine *`.cpp`* Datei, auf "Z" festgelegt ist, verwendet das MSBuild-Modul den Wert "Z".

So sieht die grundlegende Vererbungsstruktur aus:

1. Standardeinstellungen aus dem MSBuild CPP Toolset (.. "Programmdateien" und "MSBuild" und "Microsoft.Cpp" und "Microsoft.Cpp.Default.props", das von der *`.vcxproj`* Datei importiert wird.)

1. Eigenschaftenblätter

1. *`.vcxproj`* Datei. (Kann Standard- und die Eigenschaftenblatteinstellungen überschreiben.)

1. Elementmetadaten

> [!TIP]
> Auf einer Eigenschaftenseite wird eine Eigenschaft in **Fettschrift** im aktuellen Kontext definiert. Eine Eigenschaft in normaler Schriftart ist geerbt.

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>Anzeigen einer erweiterten Projektdatei mit allen importierten Werten

Manchmal ist es hilfreich, die erweiterte Datei anzuzeigen, um zu bestimmen, wie ein bestimmter Eigenschaftswert vererbt wird. Um die erweiterte Version anzuzeigen, geben Sie folgenden Befehl an einer Visual Studio-Eingabeaufforderung ein. (Ändern Sie die Platzhalterdateinamen in die Namen der Dateien, die Sie verwenden möchten.)

> **msbuild /pp:**_temp_**.txt** _myapp_**.vcxproj**

Erweiterte Projektdateien können groß und schwer verständlich sein, es sei denn, Sie sind mit MSBuild vertraut. So sieht die grundlegende Struktur einer Projektdatei aus:

1. Grundlegende Projekteigenschaften, die in der IDE nicht verfügbar gemacht werden.

1. Import *`Microsoft.cpp.default.props`* von , der einige grundlegende, werkzeugsatzunabhängige Eigenschaften definiert.

1. Globale Konfigurationseigenschaften (verfügbar als **PlatformToolset-** und **Project-Standardeigenschaften** auf der Seite **"Konfiguration Allgemein".** Diese Eigenschaften bestimmen, in *`Microsoft.cpp.props`* welche Toolset- und intrinsischen Eigenschaftenblätter im nächsten Schritt importiert werden.

1. Import *`Microsoft.cpp.props`* von , der die meisten Projektstandards festlegt.

1. Import aller Eigenschaftenblätter, *`.user`* einschließlich Dateien. Diese Eigenschaftenblätter können alles außer den **Standardeigenschaften PlatformToolset** und **Project** überschreiben.

1. Die restlichen Projektkonfigurationseigenschaften. Diese Werte können das überschreiben, was in den Eigenschaftenblättern festgelegt wurde.

1. Elemente (Dateien) zusammen mit ihren Metadaten. Diese Elemente sind immer das letzte Wort in MSBuild-Auswertungsregeln, auch wenn sie vor anderen Eigenschaften und Importen auftreten.

Weitere Informationen finden Sie unter [MSBuild-Eigenschaften](/visualstudio/msbuild/msbuild-properties).

## <a name="build-configurations"></a>Buildkonfigurationen

Eine Konfiguration ist nur eine beliebige Gruppe von Eigenschaften, denen ein Name zugewiesen wird. Visual Studio bietet Debug- und Releasekonfigurationen. Jede legt verschiedene Eigenschaften entsprechend für einen Debugbuild oder Releasebuild fest. Sie können den **Configuration Manager** verwenden, um benutzerdefinierte Konfigurationen zu definieren. Sie sind eine bequeme Möglichkeit, Eigenschaften für einen bestimmten Geschmack von Build zu gruppieren.

Um sich ein besseres Bild von Buildkonfigurationen zu machen, öffnen Sie **Property Manager**. Sie können es öffnen, indem Sie je nach Ihren Einstellungen **> Eigenschaften-Manager** anzeigen oder **> andere Windows->-Eigenschaften-Manager anzeigen**auswählen. **Property Manager** verfügt über Knoten für jede Konfiguration und jedes Plattformpaar im Projekt. Unter jedem dieser Knoten befinden sich Knoten*`.props`* für Eigenschaftenblätter (Dateien), die bestimmte Eigenschaften für diese Konfiguration festlegen.

![Eigenschaften-Manager](media/property-manager.png "Eigenschaften-Manager")

Sie können z. B. zum Bereich Allgemein in den Eigenschaftenseiten wechseln. Ändern Sie die Character Set-Eigenschaft in "Nicht festlegen" anstelle von "Unicode verwenden", und klicken Sie dann auf **OK**. Der Property Manager zeigt jetzt kein **Unicode** Support-Eigenschaftenblatt an. Es wird für die aktuelle Konfiguration entfernt, ist aber immer noch für andere Konfigurationen da.

Weitere Informationen zum Eigenschaften-Manager und zu Eigenschaftenblättern finden Sie unter [Teilen oder Wiederverwenden von Visual Studio C++-Projekteinstellungen](create-reusable-property-configurations.md).

> [!TIP]
> Die *`.user`* Datei ist ein Legacy-Feature. Es wird empfohlen, sie zu löschen, um Eigenschaften korrekt nach Konfiguration und Plattform gruppiert zu halten.

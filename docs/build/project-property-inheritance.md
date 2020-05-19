---
title: 'Vererbung von Eigenschaften in Visual Studio-Projekten: C++'
description: Hier wird die Funktionsweise der Eigenschaftenvererbung in nativen Visual Studio C++-Projekten (MSBuild) erläutert.
ms.date: 02/21/2020
helpviewer_keywords:
- C++ projects, property inheritance
ms.openlocfilehash: 4740c479c6cc7c877fd72b7828a8e4811826de6c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328479"
---
# <a name="property-inheritance-in-visual-studio-projects"></a>Vererbung von Eigenschaften in Visual Studio-Projekten

Das native Visual Studio-Projektsystem beruht auf MSBuild. MSBuild definiert Dateiformate und Regeln zum Erstellen von Projekten aller Art. Diese Engine übernimmt einen Großteil der komplexen Vorgänge beim Erstellen mehrerer Konfigurationen und Plattformen. Es ist hilfreich, die Funktionsweise zu verstehen. Dies ist besonders wichtig, wenn Sie benutzerdefinierte Konfigurationen definieren möchten. Eine weitere Möglichkeit ist das Erstellen wiederverwendbarer Eigenschaften, die Sie freigeben und in mehrere Projekte importieren können.

## <a name="the-vcxproj-file-props-files-and-targets-files"></a>Die VCXPROJ-Datei, PROPS- und TARGETS-Dateien

Projekteigenschaften werden entweder direkt in der Projektdatei ( *`.vcxproj`* ) oder in anderen *`.targets`* - oder *`.props`* -Dateien gespeichert, die Standardwerte angeben und von der Projektdatei importiert werden. Für Visual Studio 2015 befinden sich diese Dateien unter *`\Program Files (x86)\MSBuild\Microsoft.Cpp\v4.0\V140`* . Für Visual Studio 2017 befinden sich diese Dateien unter *`\Program Files (x86)\Microsoft Visual Studio\2017\<edition>\Common7\IDE\VC\VCTargets`* , wobei *`<edition>`* die installierte Visual Studio-Version ist. In Visual Studio 2019 befinden sich diese Dateien unter *`\Program Files (x86)\Microsoft Visual Studio\2019\<edition>\MSBuild\Microsoft\VC\v160`* . Eigenschaften werden ebenfalls in einer benutzerdefinierten *`.props`* -Datei gespeichert, die Sie zu Ihrem Projekt hinzufügen können. Es wird dringend empfohlen, diese Dateien NICHT manuell zu bearbeiten. Verwenden Sie zum Ändern aller Eigenschaften stattdessen die Eigenschaftenseiten in der IDE. Dies gilt insbesondere für die Dateien, die in die Vererbung mit einbezogen werden, sofern Sie nicht über umfassende MSBuild-Kenntnisse verfügen.

Wie zuvor beschrieben kann der gleichen Eigenschaft für die gleiche Konfiguration in verschiedenen Dateien ein anderer Wert zugewiesen werden. Wenn Sie ein Projekt erstellen, wertet die MSBuild-Engine die Projektdatei und alle importierten Dateien in einer klar definierten Reihenfolge (siehe unten) aus. Während die Dateien ausgewertet werden, überschreiben alle Eigenschaftswerte, die in den Dateien definiert sind, die vorhandenen Werte. Alle nicht angegebenen Werte werden von Dateien geerbt, die zuvor ausgewertet wurden. Beim Festlegen einer Eigenschaft mit Eigenschaftenseiten ist ebenfalls wichtig, darauf zu achten, wo Sie diese festlegen. Wenn Sie eine Eigenschaft in einer *`.props`* -Datei auf „X“ festlegen, diese aber in der Projektdatei auf „Y“ festgelegt ist, wird das Projekt mit der auf „Y“ festgelegten Eigenschaft erstellt. Wenn die gleiche Eigenschaft in einem Projektelement (z. B. in einer *`.cpp`* -Datei) auf „Z“ festgelegt ist, verwendet die MSBuild-Engine den Wert „Z“.

So sieht die grundlegende Vererbungsstruktur aus:

1. Standardeinstellungen von MSBuild CPP Toolset („..\Programme\MSBuild\Microsoft.Cpp\v4.0\Microsoft.Cpp.Default.props“, die durch die *`.vcxproj`* -Datei importiert werden)

1. Eigenschaftenblätter

1. *`.vcxproj`* -Datei (Kann Standard- und die Eigenschaftenblatteinstellungen überschreiben.)

1. Elementmetadaten

> [!TIP]
> Auf einer Eigenschaftenseite wird eine Eigenschaft in **Fettdruck** im aktuellen Kontext definiert. Eine Eigenschaft in normaler Schriftart ist geerbt.

## <a name="view-an-expanded-project-file-with-all-imported-values"></a>Anzeigen einer erweiterten Projektdatei mit allen importierten Werten

Manchmal ist es hilfreich, die erweiterte Datei anzuzeigen, um zu bestimmen, wie ein bestimmter Eigenschaftswert vererbt wird. Um die erweiterte Version anzuzeigen, geben Sie folgenden Befehl an einer Visual Studio-Eingabeaufforderung ein. (Ändern Sie die Platzhalterdateinamen in die Namen der Dateien, die Sie verwenden möchten.)

> **msbuild /pp:** _temp_ **.txt** _myapp_ **.vcxproj**

Erweiterte Projektdateien können sehr groß und schwierig zu verstehen sein, wenn Sie nicht mit MSBuild vertraut sind. So sieht die grundlegende Struktur einer Projektdatei aus:

1. Grundlegende Projekteigenschaften, die in der IDE nicht verfügbar gemacht werden

1. Import von *`Microsoft.cpp.default.props`* , womit einige einfache, vom Toolset unabhängige Eigenschaften definiert werden

1. Globale Konfigurationseigenschaften (verfügbar als Standardeigenschaften **PlatformToolset** und **Project** auf der Seite **Konfiguration > Allgemein**). Diese Eigenschaften bestimmen, welche Toolset- und systeminternen Eigenschaftenblätter im nächsten Schritt in *`Microsoft.cpp.props`* importiert werden.

1. Import von *`Microsoft.cpp.props`* , womit die meisten Projektstandardwerte festlegt werden

1. Import aller Eigenschaftenblätter einschließlich *`.user`* -Dateien. Diese Eigenschaftenblätter können alle Eigenschaften außer die Standardeigenschaften **PlatformToolset** und **Project** überschreiben.

1. Restliche Projektkonfigurationseigenschaften. Diese Werte können das überschreiben, was in den Eigenschaftenblättern festgelegt wurde.

1. Elemente (Dateien) zusammen mit ihren Metadaten. Diese Elemente stellen immer das letzte Wort in den MSBuild-Auswertungsregeln dar, selbst wenn sie vor anderen Eigenschaften und Importen auftreten.

Weitere Informationen finden Sie unter [MSBuild Properties](/visualstudio/msbuild/msbuild-properties) (MSBuild-Eigenschaften).

## <a name="build-configurations"></a>Buildkonfigurationen

Eine Konfiguration ist nur eine beliebige Gruppe von Eigenschaften, denen ein Name zugewiesen wird. Visual Studio stellt Debug- und Releasekonfigurationen bereit. Jede Konfiguration legt verschiedene Eigenschaften für einen Debug- oder Releasebuild entsprechend fest. Sie können den **Konfigurations-Manager** verwenden, um benutzerdefinierte Konfigurationen zu definieren. Diese sind eine bequeme Methode zum Gruppieren von Eigenschaften für eine bestimmte Art von Build.

Öffnen Sie den **Eigenschaften-Manager**, um eine bessere Vorstellung von Buildkonfigurationen zu erhalten. Öffnen Sie diesen, indem Sie in Abhängigkeit Ihrer Einstellungen entweder auf **Ansicht > Eigenschaften-Manager** oder auf **Ansicht > Weitere Fenster > Eigenschaften-Manager** klicken. Der **Eigenschaften-Manager** weist Knoten für jedes Konfigurations- und Plattformpaar im Projekt auf. Unter jedem dieser Knoten befinden sich Knoten für Eigenschaftenblätter ( *`.props`* -Dateien), die spezifische Eigenschaften für diese Konfiguration festlegen.

![Eigenschaften-Manager](media/property-manager.png "Eigenschaften-Manager")

Sie können beispielsweise auf der Seite „Eigenschaften“ zum Bereich „Allgemein“ wechseln. Ändern Sie die Eigenschaft für „Zeichensatz“ in „Nicht festgelegt“ anstelle von „Unicode-Zeichensatz verwenden“, und klicken Sie dann auf **OK**. Der Eigenschaften-Manager zeigt jetzt kein Eigenschaftenblatt für die **Unicode-Unterstützung** an. Es wird für die aktuelle Konfiguration entfernt, ist für andere Konfigurationen aber noch vorhanden.

Weitere Informationen zum Eigenschaften-Manager und zu Eigenschaftenblättern finden Sie unter [Teilen oder Wiederverwenden von Visual Studio C++-Projekteinstellungen](create-reusable-property-configurations.md).

> [!TIP]
> Die *`.user`* -Eigenschaft ist ein veraltetes Feature. Es wird empfohlen, diese zu löschen, damit die Eigenschaften entsprechend der Konfiguration und Plattform richtig gruppiert werden.

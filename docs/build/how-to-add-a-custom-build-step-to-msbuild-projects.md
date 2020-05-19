---
title: 'Vorgehensweise: Hinzufügen eines benutzerdefinierten Buildschritts zu MSBuild-Projekten'
ms.date: 10/16/2019
helpviewer_keywords:
- 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
ms.openlocfilehash: 78d40a5b4a02fe9b065bbbdde33afc6180d75381
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444917"
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>Vorgehensweise: Hinzufügen eines benutzerdefinierten Buildschritts zu MSBuild-Projekten

Ein benutzerdefinierter Buildschritt ist ein benutzerdefinierter Schritt in einem Build. Ein benutzerdefinierter Buildschritt verhält sich wie jeder andere *Befehlstoolschritt*, wie zum Beispiel der Standardkompilier- oder Linktoolschritt.

Geben Sie einen benutzerdefinierten Buildschritt in der Projektdatei (.vcxproj) an. Der Schritt kann eine auszuführende Befehlszeile, alle zusätzlichen Eingabe- oder Ausgabedateien und eine anzuzeigende Meldung angeben. Wenn **MSBuild** feststellt, dass Ihre Ausgabedateien in Bezug auf Ihre Eingabedateien veraltet sind, zeigt es die Meldung an, und der Befehl wird ausgeführt.

Verwenden Sie eines oder beide der XML-Elemente `CustomBuildAfterTargets` und `CustomBuildBeforeTargets` in der Projektdatei, um den Speicherort des benutzerdefinierten Buildschritts in der Sequenz von Buildzielen anzugeben. Sie können beispielsweise angeben, dass der benutzerdefinierte Buildschritt nach dem Linktoolziel und noch vor dem Manifesttoolziel ausgeführt werden soll. Die tatsächlich verfügbaren Ziele hängen von Ihrem speziellen Build ab.

Geben Sie das `CustomBuildBeforeTargets`-Element an, um den benutzerdefinierten Buildschritt auszuführen, bevor ein bestimmtes Ziel ausgeführt wird. Geben Sie das `CustomBuildAfterTargets`-Element an, um den Schritt nach einem bestimmten Ziel auszuführen. Geben Sie beide Elemente an, um den Schritt zwischen zwei angrenzenden Ziele auszuführen. Wenn keines der Elemente angegeben ist, wird das benutzerdefinierte Buildtool an seinem Standardspeicherort ausgeführt, d. h. nach dem **Linkziel**.

Benutzerdefinierte Buildschritte und benutzerdefinierte Buildtools nutzen die in den XML-Elementen `CustomBuildBeforeTargets` und `CustomBuildAfterTargets` angegebenen Informationen gemeinsam. Geben Sie daher diese Ziele nur einmal in der Projektdatei an.

### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>Definieren, was durch den benutzerdefinierten Buildschritt ausgeführt wird

1. Fügen Sie eine Eigenschaftengruppe zu der Projektdatei hinzu. Geben Sie in dieser Eigenschaftengruppe den Befehl, seine Eingaben und Ausgaben sowie eine Nachricht an, wie im folgenden Beispiel gezeigt. Dieses Beispiel erstellt eine CAB-Datei aus der „main.cpp“-Datei, die Sie unter [Exemplarische Vorgehensweise: Verwenden von MSBuild zum Erstellen eines C++-Projekts](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md) erstellt haben.

    ```
    <ItemDefinitionGroup>
      <CustomBuildStep>
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>
        <Outputs>$(TargetName).cab</Outputs>
        <Inputs>$(ProjectDir)main.cpp</Inputs>
      </CustomBuildStep>
    </ItemDefinitionGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>Definieren, an welcher Stelle im Build der benutzerdefinierte Buildschritt ausgeführt wird

1. Fügen Sie die folgende Eigenschaftengruppe zu der Projektdatei hinzu. Sie können beide Ziele angeben oder eines weglassen, wenn Sie vor oder nach einem bestimmten Ziel nur den benutzerdefinierten Schritt ausführen möchten. In diesem Beispiel erhält **MSBuild** die Anweisung, den benutzerdefinierten Schritt nach dem Kompilierungsschritt aber noch vor dem Linkschritt auszuführen.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>Siehe auch

[Exemplarische Vorgehensweise: Verwenden von MSBuild zum Erstellen eines C++-Projekts](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[How to: Verwenden von Buildereignissen in MSBuild-Projekten](how-to-use-build-events-in-msbuild-projects.md)<br/>
[How to: Hinzufügen von benutzerdefinierten Buildtools zu MSBuild-Projekten](how-to-add-custom-build-tools-to-msbuild-projects.md)

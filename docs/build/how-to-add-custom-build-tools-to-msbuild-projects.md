---
title: 'Vorgehensweise: Hinzufügen von benutzerdefinierten Buildtools zu MSBuild-Projekten'
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: add custom build tools'
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
ms.openlocfilehash: 812932d9e668ab5ee0eb75eadbf75be3d791cddb
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220718"
---
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>Vorgehensweise: Hinzufügen von benutzerdefinierten Buildtools zu MSBuild-Projekten

Ein benutzerdefiniertes Buildtool ist ein benutzerdefiniertes Befehlszeilentool, das mit einer bestimmten Datei verknüpft ist.

Geben Sie für eine bestimmte Datei in der Projektdatei (.vcxproj) die auszuführende Befehlszeile, alle zusätzlichen Eingabe- oder Ausgabedateien sowie eine anzuzeigende Meldung an. Wenn **MSBuild** feststellt, dass Ihre Ausgabedateien in Bezug auf Ihre Eingabedateien veraltet sind, zeigt es die Meldung an, und das Befehlszeilentool wird ausgeführt.

Um anzugeben, wann das benutzerdefinierte Buildtool ausgeführt wird, verwenden Sie eines oder beide der XML-Elemente `CustomBuildBeforeTargets` und `CustomBuildAfterTargets` in der Projektdatei. Sie könnten beispielsweise angeben, dass Ihr benutzerdefiniertes Buildtool nach dem MIDL-Compiler und vor dem C/C++-Compiler ausgeführt werden soll. Geben Sie das `CustomBuildBeforeTargets`-Element an, um das Tool auszuführen, bevor ein bestimmtes Ziel ausgeführt wird. Geben Sie das `CustomBuildAfterTargets`-Element an, um das Tool nach einem bestimmten Ziel auszuführen. Geben Sie beide Elemente an, um das Tool zwischen der Ausführung zweier Ziele auszuführen. Wenn keines der Elemente angegeben ist, wird das benutzerdefinierte Buildtool an seinem Standardspeicherort ausgeführt, d. h. vor dem **MIDL**-Ziel.

Benutzerdefinierte Buildschritte und benutzerdefinierte Buildtools nutzen die in den XML-Elementen `CustomBuildBeforeTargets` und `CustomBuildAfterTargets` angegebenen Informationen gemeinsam. Geben Sie diese Ziele einmal in der Projektdatei an.

### <a name="to-add-a-custom-build-tool"></a>Hinzufügen eines benutzerdefinierten Buildtools

1. Fügen Sie der Projektdatei eine Elementgruppe hinzu, und fügen Sie für jede Eingabedatei ein Element hinzu. Geben Sie, wie hier gezeigt, den Befehl, zusätzliche Eingaben und Ausgaben sowie eine Meldung als Elementmetadaten an. In diesem Beispiel wird davon ausgegangen, dass eine Datei „faq.txt“ im selben Verzeichnis wie Ihr Projekt vorhanden ist.

    ```
    <ItemGroup>
      <CustomBuild Include="faq.txt">
        <Message>Copying readme...</Message>
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>
        <Outputs>$(OutDir)%(Identity)</Outputs>
      </CustomBuild>
    </ItemGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>So definieren Sie, an welcher Stelle im Build die benutzerdefinierten Buildtools ausgeführt werden

1. Fügen Sie die folgende Eigenschaftengruppe zu der Projektdatei hinzu. Sie müssen mindestens eines der Ziele angeben. Sie können das andere Ziel weglassen, wenn es Ihnen nur darum geht, dass der Buildschritt vor (oder nach) einem bestimmten Ziel ausgeführt wird. In diesem Beispiel wird der benutzerdefinierte Schritt nach dem Kompilieren, aber vor dem Verknüpfen durchführt.

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>Siehe auch

[Exemplarische Vorgehensweise: Verwenden von MSBuild zum Erstellen eines C++-Projekts](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[How to: Verwenden von Buildereignissen in MSBuild-Projekten](how-to-use-build-events-in-msbuild-projects.md)<br/>
[How to: Hinzufügen eines benutzerdefinierten Buildschritts zu MSBuild-Projekten](how-to-add-a-custom-build-step-to-msbuild-projects.md)

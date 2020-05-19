---
title: 'C++: MSBuild in der Befehlszeile'
ms.date: 12/12/2018
helpviewer_keywords:
- MSBuild
ms.assetid: 7a1be7ff-0312-4669-adf2-5f5bf507d560
ms.openlocfilehash: e95d99cf5c63c824bb9bade8e76bc3ca99079669
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220576"
---
# <a name="msbuild-on-the-command-line---c"></a>C++: MSBuild in der Befehlszeile

Allgemein sollten Sie Visual Studio verwenden, um Projekteigenschaften festzulegen und das MSBuild-System aufzurufen. Sie können jedoch auch das **MSBuild**-Tool direkt in der Befehlszeile verwenden. Der Buildprozess wird von den Informationen in einer Projektdatei (VCXPROJ) gesteuert, die Sie erstellen und bearbeiten können. Die Projektdatei gibt die Buildoptionen basierend auf den Buildstufen, -bedingungen und -ereignissen an. Zusätzlich können Sie null oder mehr Befehlszeilen*options*argumente angeben.

> **msbuild.exe** [ *Projektdatei* ] [ *Optionen* ]

Verwenden Sie die **/target**- (oder **/t**) und **/property**- (oder **/p**) Befehlszeilenoptionen, um bestimmte Eigenschaften und Ziele zu überschreiben, die in der Projektdatei angegeben sind.

Eine wesentliche Funktion der Projektdatei ist die Angabe eines *Ziels*, das eine bestimmte Operation im Projekt darstellt, und der zum Ausführen der Operation erforderlichen Ein- und Ausgaben. Eine Projektdatei kann ein oder mehrere Ziele angeben, zu denen auch ein Standardziel gehören kann.

Jedes Ziel besteht aus einer Sequenz aus einer oder mehreren *Aufgaben*. Jede Aufgabe wird durch eine .NET Framework-Klasse dargestellt, die einen ausführbaren Befehl enthält. Die [CL-Aufgabe](/visualstudio/msbuild/cl-task) enthält z. B. den Befehl [cl.exe](reference/compiling-a-c-cpp-program.md).

Ein *Aufgabenparameter* ist eine Eigenschaft der Klassenaufgabe und stellt in der Regel eine Befehlszeilenoption des ausführbaren Befehls dar. Der `FavorSizeOrSpeed`-Parameter der `CL`-Aufgabe entspricht z. B. den Compileroptionen **/Os** und **/Ot**.

Zusätzliche Aufgabenparameter unterstützen die MSBuild-Infrastruktur. Der `Sources`-Aufgabenparameter gibt z. B. einen Satz von Aufgaben an, die von anderen Aufgaben genutzt werden können. Weitere Informationen zur Verwendung von MSBuild-Aufgaben finden Sie unter [Referenz zu MSBuild-Tasks](/visualstudio/msbuild/msbuild-task-reference).

Die meisten Aufgaben erfordern Eingaben und Ausgaben, z. B. Dateinamen, Pfade und Zeichenfolgenparameter bzw. numerische oder boolesche Parameter. Eine allgemeine Eingabe ist z. B. der Name einer zu kompilierenden CPP-Quelldatei. Ein wichtiger Eingabeparameter ist eine Zeichenfolge, die die Buildkonfiguration und die Plattform angibt, z. B. „Debug\|Win32“. Eingaben und Ausgaben werden von einem oder mehreren benutzerdefinierten XML-`Item`-Elementen angegeben, die in einem `ItemGroup`-Element enthalten sind.

Eine Projektdatei kann auch benutzerdefinierte *Eigenschaften* und `ItemDefinitionGroup`-*Elemente* angeben. Eigenschaften und Elemente bilden Name-Wert-Paare, die als Variablen im Build verwendet werden können. Die Namenskomponente eines Paars definiert ein *Makro*, und die Wertkomponente deklariert den *Makrowert*. Auf ein Eigenschaftenmakro wird mithilfe der $(*Name*)-Notation zugegriffen, und auf ein Elementmakro wird mithilfe der %(*Name*)-Notation zugegriffen.

Andere XML-Elemente in einer Projektdatei können Makros testen und anschließend den Wert eines Makros bedingt festlegen oder die Ausführung des Builds steuern. Makronamen und Literalzeichenfolgen können verkettet werden, um Konstrukte, wie z. B. einen Pfad oder einen Dateinamen, zu generieren. In der Befehlszeile legt die **/property**-Option die Projekteigenschaft fest oder überschreibt sie. Auf Elemente kann in der Befehlszeile nicht verwiesen werden.

Das MSBuild-System kann vor bzw. nach einem anderen Ziel ein Ziel bedingt ausführen. Das System kann außerdem ein Ziel aufgrund dessen erstellen, ob die Dateien, die das Ziel nutzt, neuer als die vom Ziel ausgegebenen Dateien sind.

Weitere Informationen zur MSBuild finden Sie unter:

- [MSBuild](/visualstudio/msbuild/msbuild) Übersicht über MSBuild-Konzepte

- [MSBuild-Referenz](/visualstudio/msbuild/msbuild-reference) Referenzinformationen zum MSBuild-System

- [Referenz zum MSBuild-Projektdateischema](/visualstudio/msbuild/msbuild-project-file-schema-reference) Führt die MSBuild-XML-Schemaelemente, ihre Attribute sowie die übergeordneten und untergeordneten Elemente auf. Achten Sie insbesondere auf die Elemente [ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild), [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild), [Target](/visualstudio/msbuild/target-element-msbuild) und [Task](/visualstudio/msbuild/task-element-msbuild).

- [MSBuild-Befehlszeilenreferenz](/visualstudio/msbuild/msbuild-command-line-reference) Beschreibt die Befehlszeilenargumente und die Optionen, die Sie mit „msbuild.exe“ verwenden können.

- [Referenz zu MSBuild-Tasks](/visualstudio/msbuild/msbuild-task-reference) Beschreibt die MSBuild-Aufgaben. Achten Sie insbesondere auf diese Aufgaben, die für Visual C++ spezifisch sind: [BscMake Task](/visualstudio/msbuild/bscmake-task), [CL Task](/visualstudio/msbuild/cl-task), [CPPClean Task](/visualstudio/msbuild/cppclean-task), [LIB Task](/visualstudio/msbuild/lib-task), [Link Task](/visualstudio/msbuild/link-task), [MIDL Task](/visualstudio/msbuild/midl-task), [MT Task](/visualstudio/msbuild/mt-task), [RC Task](/visualstudio/msbuild/rc-task), [SetEnv Task](/visualstudio/msbuild/setenv-task), [VCMessage Task](/visualstudio/msbuild/vcmessage-task).

## <a name="in-this-section"></a>In diesem Abschnitt

|Begriff|Definition|
|----------|----------------|
|[Exemplarische Vorgehensweise: Verwenden von MSBuild zum Erstellen eines C++-Projekts](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)|Zeigt, wie ein C++-Projekt in Visual Studio mithilfe von **MSBuild** erstellt wird|
|[How to: Verwenden von Buildereignissen in MSBuild-Projekten](how-to-use-build-events-in-msbuild-projects.md)|Zeigt, wie eine Aktion angegeben wird, die zu einer bestimmten Stufe des Buildprozesses auftritt: vor dem Beginn des Builds; vor dem Beginn des Verknüpfungsschritts oder nach Ende des Builds.|
|[How to: Hinzufügen eines benutzerdefinierten Buildschritts zu MSBuild-Projekten](how-to-add-a-custom-build-step-to-msbuild-projects.md)|Zeigt, wie eine benutzerdefinierte Stufe der Buildsequenz hinzugefügt wird|
|[How to: Hinzufügen von benutzerdefinierten Buildtools zu MSBuild-Projekten](how-to-add-custom-build-tools-to-msbuild-projects.md)|Zeigt, wie ein Buildtool einer bestimmten Datei zugeordnet wird|
|[How to: Integrieren von benutzerdefinierte Tools in die Projekteigenschaften](how-to-integrate-custom-tools-into-the-project-properties.md)|Zeigt, wie Optionen für ein benutzerdefiniertes Tool den Projekteigenschaften zugeordnet werden|
|[How to: Ändern des Zielframeworks und des Plattformtoolsets](how-to-modify-the-target-framework-and-platform-toolset.md)|Zeigt, wie ein Projekt für mehrere Frameworks oder Toolsets kompiliert wird|

## <a name="see-also"></a>Siehe auch

[Verwenden des MSVC-Toolsets über die Befehlszeile](building-on-the-command-line.md)

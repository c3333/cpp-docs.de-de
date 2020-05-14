---
title: 'Vorgehensweise: Verwenden von Buildereignissen in MSBuild-Projekten'
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: use build events in projects'
ms.assetid: 2a58dc9d-3d50-4e49-97c1-86c5a05ce218
ms.openlocfilehash: 3fe205223b6cf381bbf3e2872b1a84f9d81a3cb7
ms.sourcegitcommit: 2da5c42928739ca8cd683a9002598f28d8ec5f8e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70060069"
---
# <a name="how-to-use-build-events-in-msbuild-projects"></a>Vorgehensweise: Verwenden von Buildereignissen in MSBuild-Projekten

Ein Buildereignis ist ein Befehl, der MSBuild in einer bestimmten Phase im Buildprozess ausführt. Das *Präbuildereignis* tritt auf, bevor das Buildereignis gestartet wird. Das *Prälinkereignis* tritt auf, bevor der Verknüpfungsschritt gestartet wird, und das *Postbuildereignis* tritt auf, nachdem das Buildereignis erfolgreich abgeschlossen wurde. Ein Buildereignis tritt nur auf, wenn der zugeordnete Buildschritt auftritt. Das Prälinkereignis tritt beispielsweise nicht auf, wenn der Verknüpfungsschritt nicht ausgeführt wird.

Jedes der drei Buildereignisse wird in einer Elementdefinitionsgruppe durch ein Command-Element (`<Command>`) dargestellt, das ausgeführt wird, und ein Message-Element (`<Message>`), das angezeigt wird, wenn **MSBuild** das Buildereignis ausführt. Jedes Element ist optional, und Sie können dasselbe Element mehrmals ausführen, wobei das letzte Vorkommen Vorrang hat.

Ein optionales *use-in-build*-Element (`<`*build-event*`UseInBuild>`) kann in einer Eigenschaftengruppe angegeben werden, um anzugeben, dass das Buildereignis ausgeführt wird. Der Wert des Inhalts eines *use-in-build*-Elements lautet entweder **true** oder **false**. Ein Buildereignis wird standardmäßig ausgeführt, es sei denn, das zugehörige *use-in-build*-Element ist auf `false` festgelegt.

In der folgenden Tabelle ist jedes XML-Element des Buildereignisses aufgelistet:

|XML-Element|Beschreibung|
|-----------------|-----------------|
|`PreBuildEvent`|Dieses Ereignis wird vor Beginn des Builds ausgeführt.|
|`PreLinkEvent`|Dieses Ereignis wird vor dem Verknüpfungsschritt ausgeführt.|
|`PostBuildEvent`|Diese Ereignis wird nach Beendigung des Builds ausgeführt.|

In der folgenden Tabelle sind alle *use-in-build*-Elemente aufgeführt:

|XML-Element|Beschreibung|
|-----------------|-----------------|
|`PreBuildEventUseInBuild`|Gibt an, ob das *Präbuildereignis* ausgeführt werden soll|
|`PreLinkEventUseInBuild`|Gibt an, ob das *Prälinkereignis* ausgeführt werden soll|
|`PostBuildEventUseInBuild`|Gibt an, ob das *Postbuildereignis* ausgeführt werden soll|

## <a name="example"></a>Beispiel

Das folgende Beispiel kann innerhalb des Project-Elements der Datei „myproject.vcxproj“ ausgeführt werden, die unter [ Verwenden von MSBuild zum Erstellen eines C++-Projekts](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md) erstellt wird. Ein *Präbuildereignis* erstellt eine Kopie von „main.cpp“. Ein *Prälinkereignis* erstellt eine Kopie von „main.obj“, und ein *Postbuildereignis* erstellt eine Kopie von „myproject.exe“. Wenn das Projekt mithilfe einer Releasekonfiguration erstellt wird, werden die Buildereignisse ausgeführt. Wenn das Projekt mit einer Debugkonfiguration erstellt wird, werden die Buildereignisse nicht ausgeführt.

``` xml
<ItemDefinitionGroup>
  <PreBuildEvent>
    <Command>copy $(ProjectDir)main.cpp $(ProjectDir)copyOfMain.cpp</Command>
    <Message>Making a copy of main.cpp </Message>
  </PreBuildEvent>
  <PreLinkEvent>
    <Command>copy $(ProjectDir)$(Configuration)\main.obj $(ProjectDir)$(Configuration)\copyOfMain.obj</Command>
    <Message>Making a copy of main.obj</Message>
  </PreLinkEvent>
  <PostBuildEvent>
    <Command>copy $(ProjectDir)$(Configuration)\$(TargetFileName) $(ProjectDir)$(Configuration)\copyOfMyproject.exe</Command>
    <Message>Making a copy of myproject.exe</Message>
  </PostBuildEvent>
</ItemDefinitionGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
  <PreBuildEventUseInBuild>true</PreBuildEventUseInBuild>
  <PreLinkEventUseInBuild>true</PreLinkEventUseInBuild>
  <PostBuildEventUseInBuild>true</PostBuildEventUseInBuild>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
  <PreBuildEventUseInBuild>false</PreBuildEventUseInBuild>
  <PreLinkEventUseInBuild>false</PreLinkEventUseInBuild>
  <PostBuildEventUseInBuild>false</PostBuildEventUseInBuild>
</PropertyGroup>
```

## <a name="see-also"></a>Siehe auch

[MSBuild on the Command Line – C++ (C++: MSBuild in der Befehlszeile)](msbuild-visual-cpp.md)<br/>
[Exemplarische Vorgehensweise: Verwenden von MSBuild zum Erstellen eines C++-Projekts](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)

---
title: 'Exemplarische Vorgehensweise: Verwenden von MSBuild zum Erstellen eines Visual Studio-C++-Projekts'
description: In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie ein MSBuild-C++-VCXPROJ-Befehlszeilenprojekt von Grund auf erstellen.
ms.date: 10/08/2020
helpviewer_keywords:
- 'MSBuild (C++), walkthrough: create a project'
ms.openlocfilehash: b3d4e8881f926e80e95832a27f7a5106ce876265
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924337"
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>Exemplarische Vorgehensweise: Verwenden von MSBuild zum Erstellen eines Visual C++-Projekts

Diese exemplarische Vorgehensweise zeigt, wie Sie mit MSBuild in einer Eingabeaufforderung ein Visual Studio-C++-Projekt erstellen. Sie erfahren, wie Sie eine XML-basierte *`.vcxproj`* -Projektdatei für eine Visual C++-Konsolenanwendung erstellen. Nach der Erstellung des Projekts erfahren Sie, wie der Buildprozess angepasst wird.

> [!IMPORTANT]
> Verwenden Sie diesen Ansatz nicht, wenn Sie die Projektdatei später mithilfe der Visual Studio-IDE bearbeiten möchten. Wenn Sie eine *`.vcxproj`* -Datei manuell erstellen, kann die Visual Studio-IDE diese möglicherweise nicht bearbeiten oder laden, insbesondere wenn das Projekt Platzhalter in Projektelementen verwendet. Weitere Informationen finden Sie unter [`.vcxproj`- und `.props`-Dateistruktur](./reference/vcxproj-file-structure.md) sowie [`.vcxproj`-Dateien und Platzhalter](./reference/vcxproj-files-and-wildcards.md).

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben beschrieben:

- Erstellen der C++-Quelldateien für das Projekt

- Erstellen der XML-MSBuild-Projektdatei

- Verwenden von MSBuild für die Projekterstellung

- Verwenden von MSBuild für die Anpassung des Projekts

## <a name="prerequisites"></a>Voraussetzungen

Für diese exemplarische Vorgehensweise benötigen Sie Folgendes:

- Eine Kopie von Visual Studio mit installierter Workload **Desktopentwicklung mit C++**

- Allgemeine Kenntnisse des MSBuild-Systems

::: moniker range="msvc-140"

> [!NOTE]
> Die meisten der spezifischen Buildanweisungen sind in den *`.targets`* - und *`.props`* -Dateien enthalten, die im Standardzieleordner definiert sind, der in der Eigenschaft `$(VCTargetsPath)` gespeichert ist. Dort finden Sie Dateien wie *`Microsoft.Cpp.Common.props`* . In Visual Studio 2015 und früheren Versionen ist der Standardpfad für diese Dateien *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\`* .

::: moniker-end

::: moniker range="msvc-150"

> [!NOTE]
> Die meisten der spezifischen Buildanweisungen sind in den *`.targets`* - und *`.props`* -Dateien enthalten, die im Standardzieleordner definiert sind, der in der Eigenschaft `$(VCTargetsPath)` gespeichert ist. Dort finden Sie Dateien wie *`Microsoft.Cpp.Common.props`* . In Visual Studio 2017 ist der Standardpfad für diese Dateien *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\`* . In Visual Studio 2015 und früheren Versionen wurden sie unter *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\`* gespeichert.

::: moniker-end

::: moniker range=">=msvc-160"

> [!NOTE]
> Die meisten der spezifischen Buildanweisungen sind in den *`.targets`* - und *`.props`* -Dateien enthalten, die im Standardzieleordner definiert sind, der in der Eigenschaft `$(VCTargetsPath)` gespeichert ist. Dort finden Sie Dateien wie *`Microsoft.Cpp.Common.props`* . Der Standardpfad für diese Dateien ist *`%VSINSTALLDIR%MSBuild\Microsoft\VC\<version>\`* . Der Wert des Pfadelements `<version>` hängt von der Visual Studio-Version ab. Für Visual Studio 2019 ist er *`v160`* . In Visual Studio 2017 wurden diese Dateien unter *`%VSINSTALLDIR%Common7\IDE\VC\VCTargets\`* gespeichert. In Visual Studio 2015 und früheren Versionen wurden sie unter *`%ProgramFiles(x86)%\MSBuild\Microsoft.Cpp\v4.0\<version>\`* gespeichert.

::: moniker-end

## <a name="create-the-c-source-files"></a>Erstellen der C++-Quelldateien

In dieser exemplarischen Vorgehensweise erstellen Sie ein Projekt, das eine Quell- und eine Headerdatei besitzt. Die Quelldatei *`main.cpp`* enthält die `main`-Funktion für die Konsolenanwendung. Die Headerdatei *`main.h`* enthält Code zum Einbeziehen der *`<iostream>`* -Headerdatei. Sie können diese C++-Dateien mithilfe von Visual Studio oder einem Text-Editor wie Visual Studio Code erstellen.

### <a name="to-create-the-c-source-files-for-your-project"></a>So erstellen Sie die C++-Quelldateien für das Projekt

1. Erstellen Sie einen Ordner für Ihr Projekt.

1. Erstellen Sie eine Datei namens *`main.cpp`* , und fügen Sie dort den folgenden Code hinzu:

    ```cpp
    // main.cpp : the application source code.
    #include <iostream>
    #include "main.h"
    int main()
    {
       std::cout << "Hello, from MSBuild!\n";
       return 0;
    }
    ```

1. Erstellen Sie eine Datei namens *`main.h`* , und fügen Sie dort den folgenden Code hinzu:

    ```cpp
    // main.h: the application header code.
    /* Additional source code to include. */
    ```

## <a name="creating-the-xml-msbuild-project-file"></a>Erstellen der XML-MSBuild-Projektdatei

Eine MSBuild-Projektdatei ist eine XML-Datei, die ein Projektstammelement (`<Project>`) enthält. In dem Beispielprojekt, das Sie erstellen werden, enthält das `<Project>`-Element sieben untergeordnete Elemente:

- Drei Elementgruppentags (`<ItemGroup>`), die Projektkonfiguration und Plattform sowie Quelldateiname und Headerdateiname angeben.

- Drei Importtags (`<Import>`), die den Speicherort von Microsoft Visual C++-Einstellungen angeben.

- Ein Eigenschaftsgruppentag (`<PropertyGroup>`), das Projekteinstellungen angibt.

### <a name="to-create-the-msbuild-project-file"></a>So erstellen Sie die MSBuild-Projektdatei

1. Erstellen Sie mithilfe eines Text-Editors eine Projektdatei mit dem Namen *`myproject.vcxproj`* , und fügen Sie anschließend das hier gezeigte `<Project>`-Stammelement hinzu. (Verwenden Sie `ToolsVersion="14.0"`, wenn Sie Visual Studio 2015 verwenden, `ToolsVersion="15.0"` bei Visual Studio 2017 und `ToolsVersion="16.0"` bei Visual Studio 2019.)

    ```xml
    <Project DefaultTargets="Build" ToolsVersion="16.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

   Fügen Sie die Elemente in den folgenden Verfahrensschritten zwischen den `<Project>`-Stammtags ein.

1. Fügen Sie diese beiden untergeordneten `<ProjectConfiguration>`-Elemente in einem `<ItemGroup>`-Element hinzu. Das untergeordnete Element gibt Debug- und Releasekonfigurationen für ein 32-Bit-Windows-Betriebssystem an:

    ```xml
    <ItemGroup>
      <ProjectConfiguration Include="Debug|Win32">
        <Configuration>Debug</Configuration>
        <Platform>Win32</Platform>
      </ProjectConfiguration>
      <ProjectConfiguration Include="Release|Win32">
        <Configuration>Release</Configuration>
        <Platform>Win32</Platform>
      </ProjectConfiguration>
    </ItemGroup>
    ```

1. Fügen Sie ein `<Import>`-Element hinzu, das den Pfad der C++-Standardeinstellungen für dieses Projekt angibt:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
    ```

1. Fügen Sie ein Eigenschaftsgruppenelement (`<PropertyGroup>`) hinzu, das zwei Projekteigenschaften angibt, `<ConfigurationType>` und `<PlatformToolset>`. (Verwenden Sie `v140` als Wert für `<PlatformToolset>`, wenn Sie Visual Studio 2015 verwenden, `v141` bei Visual Studio 2017 und `v142` bei Visual Studio 2019.)

    ```xml
    <PropertyGroup>
      <ConfigurationType>Application</ConfigurationType>
      <PlatformToolset>v142</PlatformToolset>
    </PropertyGroup>
    ```

1. Fügen Sie ein `<Import>`-Element hinzu, das den Pfad der aktuellen C++-Einstellungen für dieses Projekt angibt:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
    ```

1. Fügen Sie ein untergeordnetes `<ClCompile>`-Element in einem `<ItemGroup>`-Element hinzu. Das untergeordnete Element gibt den Namen der zu kompilierenden C/C++-Quelldatei an:

    ```xml
    <ItemGroup>
      <ClCompile Include="main.cpp" />
    </ItemGroup>
    ```

   > [!NOTE]
   > `<ClCompile>` ist ein *Buildziel* und im Standardzieleordner definiert.

1. Fügen Sie ein untergeordnetes `<ClInclude>`-Element in einem `<ItemGroup>`-Element hinzu. Das untergeordnete Element gibt den Namen der Headerdatei für die C/C++-Quelldatei an:

    ```xml
    <ItemGroup>
      <ClInclude Include="main.h" />
    </ItemGroup>
    ```

1. Fügen Sie ein `<Import>`-Element hinzu, das den Pfad der Datei angibt, in der das Ziel für dieses Projekt definiert wird:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
    ```

### <a name="complete-project-file"></a>Vollständige Projektdatei

Der folgende Code zeigt die im vorherigen Abschnitt erstellte vollständige Projektdatei. (Verwenden Sie `ToolsVersion="15.0"` für Visual Studio 2017 und `ToolsVersion="14.0"` für Visual Studio 2015.)

```xml
<Project DefaultTargets="Build" ToolsVersion="16.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <ProjectConfiguration Include="Debug|Win32">
      <Configuration>Debug</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
    <ProjectConfiguration Include="Release|Win32">
      <Configuration>Release</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
  </ItemGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
  <PropertyGroup>
    <ConfigurationType>Application</ConfigurationType>
    <PlatformToolset>v142</PlatformToolset>
  </PropertyGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ItemGroup>
    <ClCompile Include="main.cpp" />
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="main.h" />
  </ItemGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
</Project>
```

## <a name="using-msbuild-to-build-your-project"></a>Verwenden von MSBuild für die Projekterstellung

Geben Sie den folgenden Befehl in die Eingabeaufforderung ein, um die Konsolenanwendung zu erstellen:

> `msbuild myproject.vcxproj /p:configuration=debug`

MSBuild erstellt einen Ordner für die Ausgabedateien und kompiliert und verknüpft anschließend Ihr Projekt, um das Programm *`Myproject.exe`* zu generieren. Verwenden Sie nach dem Abschluss des Buildprozesses den folgenden Befehl, um die Anwendung aus dem Debugordner auszuführen:

> `myproject`

Die Anwendung sollte „Hello, from MSBuild!“ im Konsolenfenster anzuzeigen.

## <a name="customizing-your-project"></a>Anpassen des Projekts

MSBuild ermöglicht die Ausführung von vordefinierten Buildzielen, das Übernehmen von benutzerdefinierten Eigenschaften und das Verwenden benutzerdefinierter Tools, Ereignisse und Buildschritte. In diesem Abschnitt werden die folgenden Aufgaben behandelt:

- Verwenden von MSBuild mit Buildzielen

- Verwenden von MSBuild mit Buildeigenschaften

- Verwenden von MSBuild mit dem 64-Bit-Compiler und Tools

- Verwenden von MSBuild mit anderen Toolsets

- Hinzufügen von MSBuild-Anpassungen

### <a name="using-msbuild-with-build-targets"></a>Verwenden von MSBuild mit Buildzielen

Ein *Buildziel* ist ein benannter Satz vordefinierter oder benutzerdefinierter Befehle, die während der Builderstellung ausgeführt werden können. Verwenden Sie die Ziel-Befehlszeilenoption ( **`/t`** ), um ein Buildziel anzugeben. Für das `myproject`-Beispielprojekt löscht das vordefinierte **`clean`** -Ziel alle Dateien im Debugordner und erstellt eine neue Protokolldatei.

Geben Sie zum Bereinigen von `myproject` den folgenden Befehl in die Eingabeaufforderung ein:

> `msbuild myproject.vcxproj /t:clean`

### <a name="using-msbuild-with-build-properties"></a>Verwenden von MSBuild mit Buildeigenschaften

Die Eigenschaften-Befehlszeilenoption (`/p`) ermöglicht es Ihnen, eine Eigenschaft in der Projektbuilddatei zu überschreiben. Im `myproject`- Beispielprojekt wird die Release- oder Debugbuildkonfiguration durch die `Configuration`-Eigenschaft angegeben. Das für die Ausführung der erstellten Anwendung verwendete Betriebssystem wird mit der `Platform`-Eigenschaft angegeben.

Geben Sie den folgenden Befehl in die Eingabeaufforderung ein, um einen Debugbuild der `myproject`-Anwendung für die Ausführung unter 32-Bit-Versionen von Windows zu erstellen:

> `msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`

Angenommen, durch das `myproject`-Beispielprojekt wird auch eine Konfiguration für Windows (64 Bit) und eine andere Konfiguration für ein benutzerdefiniertes Betriebssystem mit dem Namen `myplatform` definiert.

Geben Sie den folgenden Befehl in die Eingabeaufforderung ein, um einen Releasebuild zu erstellen, der unter 64-Bit-Versionen von Windows ausgeführt wird:

> `msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`

Geben Sie den folgenden Befehl in die Eingabeaufforderung ein, um einen Releasebuild für `myplatform` zu erstellen:

> `msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`

### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>Verwenden von MSBuild mit dem 64-Bit-Compiler und Tools

Wenn Visual Studio unter einer 64-Bit-Version von Windows installiert ist, sind die x64-nativen 64-Bit-Tools und die Cross Tools standardmäßig installiert. Sie können MSBuild konfigurieren, um den 64-Bit-Compiler und die Tools zur Erstellung Ihrer Anwendung zu verwenden, indem Sie die `PreferredToolArchitecture`-Eigenschaft festlegen. Diese Eigenschaft beeinflusst nicht die Projektkonfigurations- oder Plattformeigenschaften. Standardmäßig wird die 32-Bit-Version des Tools verwendet. Fügen Sie zum Angeben der 64-Bit-Version des Compilers und der Tools in der Projektdatei *`Myproject.vcxproj`* das folgende Eigenschaftsgruppenelement nach dem `<Import />`-Element für die Datei *`Microsoft.Cpp.default.props`* hinzu:

```xml
<PropertyGroup>
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>
</PropertyGroup>
```

Geben Sie den folgenden Befehl in die Eingabeaufforderung ein, um die 64-Bit-Tools zum Erstellen Ihrer Anwendung zu verwenden:

> `msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="using-msbuild-with-a-different-toolset"></a>Verwenden von MSBuild mit einem anderen Toolset

Wenn Sie die Toolsets und Bibliotheken für andere Versionen von Visual C++ installiert haben, kann MSBuild entweder Anwendungen für die aktuelle Visual C++-Version oder für die anderen installierten Versionen erstellen. Wenn Sie beispielsweise Visual Studio 2012 installiert haben, fügen Sie in der Projektdatei *`Myproject.vcxproj`* das folgende Eigenschaftsgruppenelement nach dem `<Import />`-Element für die Datei *`Microsoft.Cpp.props`* hinzu, um das Visual C++ 11.0-Toolset für Windows XP anzugeben:

```xml
<PropertyGroup>
    <PlatformToolset>v110_xp</PlatformToolset>
</PropertyGroup>
```

Geben Sie den folgenden Befehl ein, um das Projekt mit dem Visual C++ 11.0-Toolset für Windows XP erneut zu erstellen:

> `msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`

### <a name="adding-msbuild-customizations"></a>Hinzufügen von MSBuild-Anpassungen

MSBuild bietet verschiedene Möglichkeiten zur Anpassung des Buildprozesses. In den folgenden Artikeln wird gezeigt, wie Sie dem MSBuild-Projekt benutzerdefinierte Buildschritte, Tools und Ereignisse hinzufügen:

- [How to: Hinzufügen eines benutzerdefinierten Buildschritts zu MSBuild-Projekten](how-to-add-a-custom-build-step-to-msbuild-projects.md)

- [How to: Hinzufügen von benutzerdefinierten Buildtools zu MSBuild-Projekten](how-to-add-custom-build-tools-to-msbuild-projects.md)

- [How to: Verwenden von Buildereignissen in MSBuild-Projekten](how-to-use-build-events-in-msbuild-projects.md)

---
title: 'Exemplarische Vorgehensweise: Verwenden von MSBuild zum Erstellen eines Visual C++-Projekts'
ms.date: 05/16/2019
helpviewer_keywords:
- 'msbuild (c++), walkthrough: create a project'
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
ms.openlocfilehash: c93867f3be3b17f703c549aa5c05f3d327934c26
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422715"
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>Exemplarische Vorgehensweise: Verwenden von MSBuild zum Erstellen eines Visual C++-Projekts

Diese exemplarische Vorgehensweise veranschaulicht, wie mit MSBuild ein Visual Studio C++-Projekt an einer Eingabeaufforderung erstellt wird. Sie erfahren, wie die C++-Quelldateien und eine XML-basierte Projektdatei für eine Visual C++-Konsolenanwendung erstellt werden. Nach der Erstellung des Projekts erfahren Sie, wie der Buildprozess angepasst wird.

In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben veranschaulicht:

- Erstellen der C++-Quelldateien für das Projekt

- Erstellen der XML-MSBuild-Projektdatei

- Verwenden von MSBuild für die Projekterstellung

- Verwenden von MSBuild für die Anpassung des Projekts

## <a name="prerequisites"></a>Erforderliche Komponenten

Für diese exemplarische Vorgehensweise wird Folgendes benötigt:

- Eine Kopie von Visual Studio mit installierter Workload **Desktopentwicklung mit C++**

- Allgemeine Kenntnisse des MSBuild-Systems

> [!NOTE]
> Verwenden Sie diesen Ansatz nicht, wenn Sie die Projektdatei später mithilfe der Visual Studio-IDE bearbeiten möchten. Wenn Sie eine VCXPROJ-Datei manuell erstellen, ist die Visual Studio-IDE möglicherweise nicht imstande, sie zu bearbeiten oder zu laden, insbesondere, wenn das Projekt Platzhalterzeichen in Projektelementen verwendet.

> [!NOTE]
> Die meisten der spezifischen Buildanweisungen sind in den **.targets**- und **.props**-Dateien enthalten, die im Verzeichnis „VCTargets“ definiert sind, das in der Eigenschaft `$(VCTargetsPath)` gespeichert ist. Der Standardpfad für diese Dateien in Visual Studio 2019 Enterprise Edition ist „C:\Programme (x86) \Microsoft Visual Studio\2019\Enterprise\MSBuild\Microsoft\VC\v160\Microsoft.Cpp.Common.props“.

## <a name="creating-the-c-source-files"></a>Erstellen der C++-Quelldateien

In dieser exemplarischen Vorgehensweise erstellen Sie ein Projekt, das eine Quell- und eine Headerdatei besitzt. Die Quelldatei "main.cpp" enthält die Hauptfunktion für die Konsolenanwendung. Die Headerdatei "main.h" enthält Code zum Einschließen der iostream-Headerdatei. Sie können diese C++-Dateien mithilfe von Visual Studio oder einem Text-Editor wie Visual Studio Code erstellen.

### <a name="to-create-the-c-source-files-for-your-project"></a>So erstellen Sie die C++-Quelldateien für das Projekt

1. Erstellen Sie ein Verzeichnis für das Projekt.

1. Erstellen Sie eine Datei mit dem Namen "main.cpp", und fügen Sie der Datei den folgenden Code hinzu:

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

1. Erstellen Sie eine Datei mit dem Namen "main.h", und fügen Sie der Datei den folgenden Code hinzu:

    ```cpp
    // main.h: the application header code.
    /* Additional source code to include. */
    ```

## <a name="creating-the-xml-msbuild-project-file"></a>Erstellen der XML-MSBuild-Projektdatei

Eine MSBuild-Projektdatei ist eine XML-Datei, die ein Projektstammelement (`<Project>`) enthält. Im folgenden Beispielprojekt enthält das `<Project>`-Element sieben untergeordnete Elemente:

- Drei Elementgruppentags (`<ItemGroup>`), die Projektkonfiguration und Plattform sowie Quelldateiname und Headerdateiname angeben.

- Drei Importtags (`<Import>`), die den Speicherort von Microsoft Visual C++-Einstellungen angeben.

- Ein Eigenschaftsgruppentag (`<PropertyGroup>`), das Projekteinstellungen angibt.

### <a name="to-create-the-msbuild-project-file"></a>So erstellen Sie die MSBuild-Projektdatei

1. Erstellen Sie mithilfe eines Text-Editors eine Projektdatei mit dem Namen `myproject.vcxproj`, und fügen Sie anschließend das folgende `<Project>`-Stammelement hinzu. Fügen Sie die Elemente in den folgenden Verfahrensschritten zwischen den `<Project>`-Stammtags ein. (Verwenden Sie ToolsVersion="15.0", wenn Sie mit Visual Studio 2017 oder ToolsVersion="16.0", wenn Sie mit Visual Studio 2019 arbeiten.)

    ```xml
    <Project DefaultTargets="Build" ToolsVersion="16.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

1. Fügen Sie die zwei folgenden untergeordneten `<ProjectConfiguration>`-Elemente in einem `<ItemGroup>`-Element hinzu. Das untergeordnete Element gibt Debug- und Releasekonfigurationen für ein 32-Bit-Windows-Betriebssystem an:

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

1. Fügen Sie das folgende `<Import>`-Element hinzu, das den Pfad der C++-Standardeinstellungen für dieses Projekt angibt:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
    ```

1. Fügen Sie das folgende Eigenschaftsgruppenelement (`<PropertyGroup>`) hinzu, das zwei Projekteigenschaften angibt. (Verwenden Sie v141, wenn Sie mit Visual Studio 2017 oder v142, wenn Sie mit Visual Studio 2019 arbeiten.)

    ```xml
    <PropertyGroup>
      <ConfigurationType>Application</ConfigurationType>
      <PlatformToolset>v142</PlatformToolset>
    </PropertyGroup>
    ```

1. Fügen Sie das folgende `<Import>`-Element hinzu, das den Pfad der aktuellen C++-Einstellungen für dieses Projekt angibt:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
    ```

1. Fügen Sie das folgende untergeordnete `<ClCompile>`-Element in einem `<ItemGroup>`-Element hinzu. Das untergeordnete Element gibt den Namen der zu kompilierenden C/C++-Quelldatei an:

    ```xml
    <ItemGroup>
      <ClCompile Include="main.cpp" />
    </ItemGroup>
    ```

   > [!NOTE]
   > `<ClCompile>` ist ein *Buildziel* und im Verzeichnis **VCTargets** definiert.

1. Fügen Sie das folgende untergeordnete `<ClInclude>`-Element in einem `<ItemGroup>`-Element hinzu. Das untergeordnete Element gibt den Namen der Headerdatei für die C/C++-Quelldatei an:

    ```xml
    <ItemGroup>
      <ClInclude Include="main.h" />
    </ItemGroup>
    ```

1. Fügen Sie das folgende `<Import>`-Element hinzu, das den Pfad der Datei angibt, durch die das Ziel für dieses Projekt definiert wird:

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
    ```

### <a name="complete-project-file"></a>Vollständige Projektdatei

Im folgenden Code wird die zuvor erstellte vollständige Projektdatei dargestellt. (Verwenden Sie ToolsVersion="15.0" für Visual Studio 2017.)

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

Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um die Konsolenanwendung zu erstellen:

`msbuild myproject.vcxproj /p:configuration=debug`

Von MSBuild wird ein Verzeichnis für die Ausgabedateien erstellt, und anschließend wird das Projekt kompiliert und verknüpft, um das Programm „Myproject.exe“ zu generieren. Nachdem der Buildprozess beendet wurde, verwenden Sie den folgenden Befehl, um die Anwendung aus dem Debugordner auszuführen:

`myproject`

Die Anwendung sollte „Hello, from MSBuild!“ im Konsolenfenster anzuzeigen.

## <a name="customizing-your-project"></a>Anpassen des Projekts

MSBuild ermöglicht die Ausführung von vordefinierten Buildzielen, das Übernehmen von benutzerdefinierten Eigenschaften und das Verwenden benutzerdefinierter Tools, Ereignisse und Buildschritte. In diesem Abschnitt werden die folgenden Aufgaben veranschaulicht:

- Verwenden von MSBuild mit Buildzielen

- Verwenden von MSBuild mit Buildeigenschaften

- Verwenden von MSBuild mit dem 64-Bit-Compiler und Tools

- Verwenden von MSBuild mit anderen Toolsets

- Hinzufügen von MSBuild-Anpassungen

### <a name="using-msbuild-with-build-targets"></a>Verwenden von MSBuild mit Buildzielen

Ein *Buildziel* ist ein benannter Satz vordefinierter oder benutzerdefinierter Befehle, die während der Builderstellung ausgeführt werden können. Verwenden Sie die Zielbefehlszeilenoption (`/t`), um ein Buildziel anzugeben. Für das `myproject`-Beispielprojekt werden vom vordefinierten **Bereinigungsziel** alle Dateien im Debugordner gelöscht, und eine neue Protokolldatei wird erstellt.

Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um `myproject` zu bereinigen.

`msbuild myproject.vcxproj /t:clean`

### <a name="using-msbuild-with-build-properties"></a>Verwenden von MSBuild mit Buildeigenschaften

Die Eigenschaften-Befehlszeilenoption (`/p`) ermöglicht es Ihnen, eine Eigenschaft in der Projektbuilddatei zu überschreiben. Im `myproject`- Beispielprojekt wird die Release- oder Debugbuildkonfiguration durch die `Configuration`-Eigenschaft angegeben. Das Betriebssystem, das für die Ausführung der erstellten Anwendung vorgesehen ist, wird durch die `Platform`-Eigenschaft angegeben.

Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um einen Debugbuild der `myproject`-Anwendung zu erstellen, die für die Ausführung unter Windows (32 Bit) vorgesehen ist.

`msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`

Angenommen, durch das `myproject`-Beispielprojekt wird auch eine Konfiguration für Windows (64 Bit) und eine andere Konfiguration für ein benutzerdefiniertes Betriebssystem mit dem Namen `myplatform` definiert.

Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um einen Releasebuild zu erstellen, der unter Windows (64 Bit) ausgeführt wird.

`msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`

Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um einen Releasebuild für `myplatform` anzuzeigen:

`msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`

### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>Verwenden von MSBuild mit dem 64-Bit-Compiler und Tools

Wenn Sie Visual Studio auf einer 64-Bit-Windows-Version installiert haben, werden standardmäßig die systemeigenen Tools sowie Cross Tools für 64-Bit x64 installiert. Sie können MSBuild konfigurieren, um den 64-Bit-Compiler und die Tools zur Erstellung Ihrer Anwendung zu verwenden, indem Sie die `PreferredToolArchitecture`-Eigenschaft festlegen. Diese Eigenschaft beeinflusst nicht die Projektkonfigurations- oder Plattformeigenschaften. Standardmäßig wird die 32-Bit-Version des Tools verwendet. Fügen Sie das folgende Eigenschaften Gruppenelement der Projektdatei "MyProject. vcxproj" nach dem `Microsoft.Cpp.default.props` \<Import/>-Element hinzu, um die 64-Bit-Version des Compilers und der Tools anzugeben:

```xml
<PropertyGroup>
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>
</PropertyGroup>
```

Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um die 64-Bit-Tools zur Erstellung Ihrer Anwendung zu verwenden.

`msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="using-msbuild-with-a-different-toolset"></a>Verwenden von MSBuild mit einem anderen Toolset

Wenn Sie die Toolsets und Bibliotheken für andere Versionen von Visual C++ installiert haben, kann MSBuild entweder Anwendungen für die aktuelle Visual C++-Version oder für die anderen installierten Versionen erstellen. Wenn Sie z. b. Visual Studio 2012 installiert haben, um das Visual C++ 11,0-Toolset für Windows XP anzugeben, fügen Sie das folgende Eigenschaften Gruppenelement der Projektdatei "MyProject. vcxproj" nach dem `Microsoft.Cpp.props` \<Import/>-Element hinzu:

```xml
<PropertyGroup>
    <PlatformToolset>v110_xp</PlatformToolset>
</PropertyGroup>
```

Geben Sie einen der folgenden Befehle ein, um das Projekt mit dem Visual C++ 11.0-Toolset für Windows XP erneut zu erstellen:

`msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`

### <a name="adding-msbuild-customizations"></a>Hinzufügen von MSBuild-Anpassungen

MSBuild bietet verschiedene Möglichkeiten zur Anpassung des Buildprozesses. Die folgenden Themen zeigen, wie dem MSBuild-Projekt benutzerdefinierte Buildschritte, Tools und Ereignisse hinzugefügt werden:

- [Vorgehensweise: Hinzufügen eines benutzerdefinierten Buildschritts zu MSBuild-Projekten](how-to-add-a-custom-build-step-to-msbuild-projects.md)

- [Vorgehensweise: Hinzufügen von benutzerdefinierten Buildtools zu MSBuild-Projekten](how-to-add-custom-build-tools-to-msbuild-projects.md)

- [Vorgehensweise: Verwenden von Buildereignissen in MSBuild-Projekten](how-to-use-build-events-in-msbuild-projects.md)

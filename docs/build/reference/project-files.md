---
title: Beispielprojektdatei
ms.date: 08/19/2019
helpviewer_keywords:
- .vcxproj files
- C++ projects, project file format
ms.assetid: 5261cf45-3136-40a6-899e-dc1339551401
ms.openlocfilehash: eef28961ab8c4d3a34a74999c7e0c69a4fc3fced
ms.sourcegitcommit: 9c2b3df9b837879cd17932ae9f61cdd142078260
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "92924013"
---
# <a name="project-files"></a>Projektdateien

Eine C++-Projektdatei in Visual Studio ist eine XML-basierte Datei mit der Dateinamenerweiterung. vcxproj und enthält Informationen, die zum Erstellen eines C++-Projekts erforderlich sind. Beachten Sie, dass die Projektdatei verschiedene Projektdateien importiert, die über die Erweiterung ".-Eigenschaften" oder ". targets" verfügen. Diese Dateien enthalten zusätzliche Buildinformationen und können selbst auf andere ".-Eigenschaften" oder ". targets"-Dateien verweisen. Die Makros im Dateipfad (z. B. `$(VCTargetsPath)`) hängen von Ihrer Visual Studio-Installation ab. Weitere Informationen zu diesen Makros und ". Properties"-und Targets-Dateien finden Sie auf der [Eigenschaften Seite "VC + +-Verzeichnisse](vcpp-directories-property-page.md)", " [Set C++ Compiler" und "Build Properties" in Visual Studio](../working-with-project-properties.md) und [Allgemeine Makros für Buildbefehle und-Eigenschaften](common-macros-for-build-commands-and-properties.md).

## <a name="example"></a>Beispiel

::: moniker range=">=msvc-160"

Die folgende vcxproj-Beispieldatei wurde erstellt, indem Sie im Dialogfeld **Neues Projekt** die Option **Windows-Desktop-Assistent** ausgewählt haben. Verwenden Sie entweder das Tool „msbuild.exe“ in der Befehlszeile oder den Befehl **Build** in der IDE. (Dieses Beispiel kann nicht verarbeitet werden, da die erforderlichen Quell-und Header Dateien nicht bereitgestellt werden.) Weitere Informationen zu den XML-Elementen in einer Projektdatei finden Sie unter [Project File Schema Reference](/visualstudio/msbuild/msbuild-project-file-schema-reference).

::: moniker-end

::: moniker range="<=msvc-150"

Die folgende VCXPROJ-Beispieldatei wurde erstellt, indem eine **Win32-Konsolenanwendung** im Dialogfeld **Neues Projekt** angegeben wurde. Verwenden Sie entweder das Tool „msbuild.exe“ in der Befehlszeile oder den Befehl **Build** in der IDE. (Dieses Beispiel kann nicht verarbeitet werden, da die erforderlichen Quell-und Header Dateien nicht bereitgestellt werden.) Weitere Informationen zu den XML-Elementen in einer Projektdatei finden Sie unter [Project File Schema Reference](/visualstudio/msbuild/msbuild-project-file-schema-reference).

::: moniker-end

>[!NOTE]
> Ändern Sie für Projekte in Visual Studio 2017 und früher `pch.h` in `stdafx.h` und `pch.cpp` in `stdafx.cpp` .

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project DefaultTargets="Build" ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup Label="ProjectConfigurations">
    <ProjectConfiguration Include="Debug|Win32">
      <Configuration>Debug</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
    <ProjectConfiguration Include="Release|Win32">
      <Configuration>Release</Configuration>
      <Platform>Win32</Platform>
    </ProjectConfiguration>
  </ItemGroup>
  <PropertyGroup Label="Globals">
    <ProjectGuid>{96F21549-A7BF-4695-A1B1-B43625B91A14}</ProjectGuid>
    <Keyword>Win32Proj</Keyword>
    <RootNamespace>SomeProjName</RootNamespace>
  </PropertyGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Default.props" />
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'" Label="Configuration">
    <ConfigurationType>Application</ConfigurationType>
    <CharacterSet>Unicode</CharacterSet>
  </PropertyGroup>
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
    <ConfigurationType>Application</ConfigurationType>
    <WholeProgramOptimization>true</WholeProgramOptimization>
    <CharacterSet>Unicode</CharacterSet>
  </PropertyGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
  <ImportGroup Label="ExtensionSettings">
  </ImportGroup>
  <ImportGroup Label="PropertySheets" Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
    <Import Project="$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props" Condition="exists('$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props')" Label="LocalAppDataPlatform" />
  </ImportGroup>
  <ImportGroup Label="PropertySheets" Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
    <Import Project="$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props" Condition="exists('$(UserRootDir)\Microsoft.Cpp.$(Platform).user.props')" Label="LocalAppDataPlatform" />
  </ImportGroup>
  <PropertyGroup Label="UserMacros" />
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
    <LinkIncremental>true</LinkIncremental>
  </PropertyGroup>
  <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
    <LinkIncremental>false</LinkIncremental>
  </PropertyGroup>
  <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
    <ClCompile>
      <PrecompiledHeader>Use</PrecompiledHeader>
      <WarningLevel>Level3</WarningLevel>
      <MinimalRebuild>true</MinimalRebuild>
      <DebugInformationFormat>EditAndContinue</DebugInformationFormat>
      <Optimization>Disabled</Optimization>
      <BasicRuntimeChecks>EnableFastChecks</BasicRuntimeChecks>
      <RuntimeLibrary>MultiThreadedDebugDLL</RuntimeLibrary>
      <PreprocessorDefinitions>WIN32;_DEBUG;_CONSOLE;%(PreprocessorDefinitions)</PreprocessorDefinitions>
    </ClCompile>
    <Link>
      <SubSystem>Console</SubSystem>
      <GenerateDebugInformation>true</GenerateDebugInformation>
    </Link>
  </ItemDefinitionGroup>
  <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
    <ClCompile>
      <WarningLevel>Level3</WarningLevel>
      <PrecompiledHeader>Use</PrecompiledHeader>
      <DebugInformationFormat>ProgramDatabase</DebugInformationFormat>
      <Optimization>MaxSpeed</Optimization>
      <RuntimeLibrary>MultiThreadedDLL</RuntimeLibrary>
      <FunctionLevelLinking>true</FunctionLevelLinking>
      <IntrinsicFunctions>true</IntrinsicFunctions>
      <PreprocessorDefinitions>WIN32;NDEBUG;_CONSOLE;%(PreprocessorDefinitions)</PreprocessorDefinitions>
    </ClCompile>
    <Link>
      <SubSystem>Console</SubSystem>
      <GenerateDebugInformation>true</GenerateDebugInformation>
      <EnableCOMDATFolding>true</EnableCOMDATFolding>
      <OptimizeReferences>true</OptimizeReferences>
    </Link>
  </ItemDefinitionGroup>
  <ItemGroup>
    <None Include="ReadMe.txt" />
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="pch.h" />
    <ClInclude Include="targetver.h" />
  </ItemGroup>
  <ItemGroup>
    <ClCompile Include="SomeProjName.cpp" />
    <ClCompile Include="pch.cpp">
      <PrecompiledHeader Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">Create</PrecompiledHeader>
      <PrecompiledHeader Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">Create</PrecompiledHeader>
    </ClCompile>
  </ItemGroup>
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
  <ImportGroup Label="ExtensionTargets">
  </ImportGroup>
</Project>
```

## <a name="see-also"></a>Siehe auch

[Visual Studio-Projekte: C++](../creating-and-managing-visual-cpp-projects.md)<br>
[Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio](../working-with-project-properties.md)

---
title: Vcxproj.filters Dateien
ms.date: 09/25/2019
description: Verwenden von Filtern von Dateien in Visual Studio C++-Projekten zum Definieren benutzerdefinierter logischer Ordner für Dateien im Projektmappen-Explorer
helpviewer_keywords:
- vcxproj.filters
- filters file [C++]
ms.openlocfilehash: 57735246b543680243994b99b8c05c9ad1211f38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335934"
---
# <a name="vcxprojfilters-files"></a>vcxproj.filters Dateien

Die *Filterdatei* (\*.vcxproj.filters) ist eine XML-Datei im MSBuild-Format, die sich im Stammprojektordner befindet. Es gibt an, welche Dateitypen in welchen logischen Ordner im **Projektmappen-Explorer**gehen. In der folgenden Abbildung befinden sich die *CPP-Dateien* unter dem Knoten **Quelldateien.** Die *.h-Dateien* befinden sich unter dem **Header Files-Knoten** und *.ico-* und *.rc-Dateien* unter **Ressourcendateien**. Diese Platzierung wird durch die Filterdatei gesteuert.

![Logische Ordner im Projektmappen-Explorer](media/solution-explorer-filters.png)

## <a name="creating-a-custom-filters-file"></a>Erstellen einer benutzerdefinierten Filterdatei

Visual Studio erstellt diese Datei automatisch. Für Desktopanwendungen sind die vordefinierten logischen Ordner (Filter): **Quelldateien**, **Headerdateien** und **Ressourcendateien**. Andere Projekttypen wie UWP verfügen möglicherweise über einen anderen Satz von Standardordnern. Visual Studio weist jedem Ordner automatisch bekannte Dateitypen zu. Wenn Sie einen Filter mit einem benutzerdefinierten Namen oder einen Filter mit benutzerdefinierten Dateitypen erstellen möchten, können Sie eine eigene Filterdatei im Stammordner des Projekts oder unter einem vorhandenen Filter erstellen. (**Verweise** und **externe Abhängigkeiten** sind spezielle Ordner, die nicht am Filtern beteiligt sind.)

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die Filterdatei für die Beispielanzeige zuvor. Es hat eine flache Hierarchie; Mit anderen Worten, es gibt keine verschachtelten logischen Ordner. Der `UniqueIdentifier` -Knoten ist optional. Es ermöglicht Visual Studio-Automatisierungsschnittstellen, den Filter zu finden. `Extensions`ist ebenfalls optional. Wenn eine neue Datei zu einem Projekt hinzugefügt wird, wird sie dem obersten Filter mit einer übereinstimmenden Dateierweiterung hinzugefügt. Um eine Datei zu einem bestimmten Filter hinzuzufügen, klicken Sie mit der rechten Maustaste auf den Filter, und wählen **Sie Neues Element hinzufügen**aus.

Der, `ItemGroup` der `ClInclude` die Knoten enthält, wird beim ersten Start des Projekts erstellt. Wenn Sie eigene vcxproj-Dateien generieren, stellen Sie sicher, dass alle Projektelemente auch einen Eintrag in der Filterdatei haben. Werte in `ClInclude` einem Knoten überschreiben die Standardfilterung basierend auf Dateierweiterungen. Wenn Sie Visual Studio verwenden, um dem Projekt ein neues Element hinzuzufügen, fügt die IDE einen einzelnen Dateieintrag in der Filterdatei hinzu. Der Filter wird nicht automatisch neu zugewiesen, wenn Sie die Dateierweiterung ändern.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <ItemGroup>
    <Filter Include="Source Files">
      <UniqueIdentifier>{4FC737F1-C7A5-4376-A066-2A32D752A2FF}</UniqueIdentifier>
      <Extensions>cpp;c;cc;cxx;def;odl;idl;hpj;bat;asm;asmx</Extensions>
    </Filter>
    <Filter Include="Header Files">
      <UniqueIdentifier>{93995380-89BD-4b04-88EB-625FBE52EBFB}</UniqueIdentifier>
      <Extensions>h;hh;hpp;hxx;hm;inl;inc;ipp;xsd</Extensions>
    </Filter>
    <Filter Include="Resource Files">
      <UniqueIdentifier>{67DA6AB6-F800-4c08-8B7A-83BB121AAD01}</UniqueIdentifier>
      <Extensions>rc;ico;cur;bmp;dlg;rc2;rct;bin;rgs;gif;jpg;jpeg;jpe;resx;tiff;tif;png;wav;mfcribbon-ms</Extensions>
    </Filter>
  </ItemGroup>
  <ItemGroup>
    <ClInclude Include="MFCApplication1.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="MFCApplication1Dlg.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="stdafx.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="targetver.h">
      <Filter>Header Files</Filter>
    </ClInclude>
    <ClInclude Include="Resource.h">
      <Filter>Header Files</Filter>
    </ClInclude>
  </ItemGroup>
  <ItemGroup>
    <ClCompile Include="MFCApplication1.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
    <ClCompile Include="MFCApplication1Dlg.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
    <ClCompile Include="stdafx.cpp">
      <Filter>Source Files</Filter>
    </ClCompile>
  </ItemGroup>
  <ItemGroup>
    <ResourceCompile Include="MFCApplication1.rc">
      <Filter>Resource Files</Filter>
    </ResourceCompile>
  </ItemGroup>
  <ItemGroup>
    <None Include="res\MFCApplication1.rc2">
      <Filter>Resource Files</Filter>
    </None>
  </ItemGroup>
  <ItemGroup>
    <Image Include="res\MFCApplication1.ico">
      <Filter>Resource Files</Filter>
    </Image>
  </ItemGroup>
</Project>
```

Um verschachtelte logische Ordner zu erstellen, deklarieren Sie alle Knoten in Filtern, `ItemGroup` wie unten gezeigt. Jeder untergeordnete Knoten muss den vollständigen logischen Pfad für das oberste übergeordnete Element deklarieren. Im folgenden Beispiel muss `ParentFilter` ein leerer deklariert werden, da in späteren Knoten darauf verwiesen wird.

```xml
  <ItemGroup>
    <Filter Include="ParentFilter">
    </Filter>
    <Filter Include="ParentFilter\Source Files"> <!-- Full path to topmost parent.-->  
      <UniqueIdentifier>{4FC737F1-C7A5-4376-A066-2A32D752A2FF}</UniqueIdentifier> <!--  Optional-->
      <Extensions>cpp;c;cc;cxx;def;odl;idl;hpj;bat;asm;asmx</Extensions> <!-- Optional -->
    </Filter>
    <Filter Include="Header Files">
      <UniqueIdentifier>{93995380-89BD-4b04-88EB-625FBE52EBFB}</UniqueIdentifier>
      <Extensions>h;hh;hpp;hxx;hm;inl;inc;ipp;xsd</Extensions>
    </Filter>
  </ItemGroup>
```

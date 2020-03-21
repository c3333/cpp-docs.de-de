---
title: Vcxproj. Filters-Dateien
ms.date: 09/25/2019
description: Verwenden von Filter Dateien in Visual C++ Studio-Projekten zum Definieren von benutzerdefinierten logischen Ordnern für Dateien in Projektmappen-Explorer
helpviewer_keywords:
- vcxproj.filters
- filters file [C++]
ms.openlocfilehash: bdf40708a70d841cb3d3144fa8fa73a71e9e9ef2
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078276"
---
# <a name="vcxprojfilters-files"></a>Vcxproj. Filters-Dateien

Die *Filter* Datei (\*. vcxproj. Filters) ist eine XML-Datei im MSBuild-Format, die sich im Stamm Projektordner befindet. Gibt an, welche Dateitypen in welchem logischen Ordner in **Projektmappen-Explorer**werden. In der folgenden Abbildung befinden sich die *cpp* -Dateien unter dem Knoten **Quelldateien** . die *h* -Dateien befinden sich unter dem Knoten **Header Dateien** , und *ICO* -und *RC* -Dateien befinden sich unter **Ressourcen Dateien**. Diese Platzierung wird von der Filterdatei gesteuert.

![Logische Ordner in Projektmappen-Explorer](media/solution-explorer-filters.png)

## <a name="creating-a-custom-filters-file"></a>Erstellen einer benutzerdefinierten Filterdatei

Diese Datei wird von Visual Studio automatisch erstellt. Bei Desktop Anwendungen lauten die vordefinierten logischen Ordner (Filter): **Quelldateien**, **Header Dateien** und **Ressourcen Dateien**. Andere Projekttypen, z. b. UWP, haben möglicherweise einen anderen Satz von Standardordnern. Visual Studio weist jedem Ordner automatisch bekannte Dateitypen zu. Wenn Sie einen Filter mit einem benutzerdefinierten Namen oder einem Filter erstellen möchten, der benutzerdefinierte Dateitypen enthält, können Sie im Stamm Ordner des Projekts oder unter einem vorhandenen Filter eine eigene Filterdatei erstellen. (**Verweise** und **externe Abhängigkeiten** sind spezielle Ordner, die nicht an der Filterung beteiligt sind.)

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die Filterdatei für das Beispiel, das zuvor gezeigt wurde. Sie verfügt über eine flache Hierarchie. Das heißt, es gibt keine logischen logischen Ordner. Der `UniqueIdentifier` -Knoten ist optional. Es ermöglicht Visual Studio-Automatisierungs Schnittstellen, den Filter zu suchen. `Extensions` ist ebenfalls optional. Wenn einem Projekt eine neue Datei hinzugefügt wird, wird Sie dem obersten Filter mit einer übereinstimmenden Dateierweiterung hinzugefügt. Um einem bestimmten Filter eine Datei hinzuzufügen, klicken Sie mit der rechten Maustaste auf den Filter, und wählen Sie **Neues Element hinzufügen**aus.

Der `ItemGroup`, der die `ClInclude` Knoten enthält, wird beim ersten Start des Projekts erstellt. Wenn Sie Ihre eigenen vcxproj-Dateien erstellen, stellen Sie sicher, dass alle Projekt Elemente auch über einen Eintrag in der Filterdatei verfügen. Werte in einem `ClInclude` Knoten überschreiben die Standard Filterung auf der Grundlage von Dateierweiterungen. Wenn Sie Visual Studio verwenden, um dem Projekt ein neues Element hinzuzufügen, fügt die IDE einen einzelnen Datei Eintrag in der Filterdatei hinzu. Der Filter wird nicht automatisch neu zugewiesen, wenn Sie die Dateierweiterung ändern.

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

Um geclusterte logische Ordner zu erstellen, deklarieren Sie alle Knoten in Filter `ItemGroup` wie unten gezeigt. Jeder untergeordnete Knoten muss den vollständigen logischen Pfad für das oberste übergeordnete Element deklarieren. Im folgenden Beispiel muss eine leere `ParentFilter` deklariert werden, da in späteren Knoten auf Sie verwiesen wird.

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

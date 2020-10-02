---
title: vcxproj-Dateien und Platzhalter
description: Gibt an, wie die System. vcxproj-Dateien von C++ Native MSBuild-Projekte Platzhalter verarbeiten.
ms.date: 09/30/2020
helpviewer_keywords:
- .vcxproj file structure
ms.assetid: 14d0c552-29db-480e-80c1-7ea89d6d8e9c
ms.openlocfilehash: 23d36a63f328e14cca59d1d57838173b4dcb0954
ms.sourcegitcommit: f7fbdc39d73e1fb3793c396fccf7a1602af7248b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/02/2020
ms.locfileid: "91663095"
---
# <a name="vcxproj-files-and-wildcards"></a>`.vcxproj` Dateien und Platzhalter

Die Visual Studio-IDE unterstützt bestimmte Konstrukte in Projekt Elementen in *`.vcxproj`* Dateien nicht. Diese nicht unterstützten Konstrukte enthalten Platzhalter, durch Semikolons getrennte Listen oder MSBuild-Makros, die zu mehreren Dateien erweitert werden. Das `.vcxproj` Projekt System für C++-Builds ist restriktiver als MSBuild. Jedes Projekt Element muss über ein eigenes MSBuild-Element verfügen. Weitere Informationen zum `.vcxproj` Dateiformat finden Sie unter [ `.vcxproj` und `.props` Dateistruktur](vcxproj-file-structure.md).

Diese Konstruktionsbeispiele werden von der IDE nicht unterstützt:

```xml
<ItemGroup>
  <None Include="*.txt">
  <ClCompile Include="a.cpp;b.cpp"/>
  <ClCompile Include="@(SomeItems)" />
</ItemGroup>
```

Wenn eine `.vcxproj` Projektdatei, die diese Konstrukte enthält, in die IDE geladen wird, scheint das Projekt möglicherweise zuerst zu funktionieren. Allerdings sind Probleme wahrscheinlich, sobald das Projekt von Visual Studio geändert und dann auf der Festplatte gespeichert wird. Möglicherweise treten zufällige Abstürze und undefiniertes Verhalten auf.

Wenn Visual Studio in Visual Studio 2019 Version 16,7 eine `.vcxproj` Projektdatei lädt, erkennt es automatisch nicht unterstützte Einträge in Projekt Elementen. Beim Laden der Projekt Mappe werden Warnungen im Fenster Ausgabe angezeigt.

Visual Studio 2019 Version 16,7 bietet auch Unterstützung für schreibgeschützte Projekte. Die schreibgeschützte Unterstützung ermöglicht der IDE das verwenden manuell erstellter Projekte, die nicht über die zusätzlichen Einschränkungen von IDE-editierbaren Projekten verfügen.

Wenn Sie über eine Datei verfügen, in der mindestens `.vcxproj` ein nicht unterstütztes-Konstrukte verwendet wird, können Sie Sie mithilfe einer der folgenden Optionen in der IDE ohne Warnungen laden:

- Alle Elemente explizit auflisten
- Markieren Sie das Projekt als schreibgeschützt.
- Platzhalter Elemente in einen Zieltext verschieben

## <a name="list-all-items-explicitly"></a>Alle Elemente explizit auflisten

Derzeit gibt es keine Möglichkeit, Platzhalter Erweiterungs Elemente im Projektmappen-Explorer Fenster in einem nicht schreibgeschützten Projekt sichtbar zu machen. Projektmappen-Explorer erwartet, dass Projekte alle Elemente explizit auflisten.

Legen Sie `.vcxproj` die-Eigenschaft auf fest, um zu ermöglichen, dass Projekte in Visual Studio 2019, Version 16,7 oder höher, automatisch erweitert werden `ReplaceWildcardsInProjectItems` `true` . Es wird empfohlen, eine *`Directory.Build.props`* Datei in einem Stammverzeichnis zu erstellen und diesen Inhalt zu verwenden:

```xml
<Project>
  <PropertyGroup>
    <ReplaceWildcardsInProjectItems>true</ReplaceWildcardsInProjectItems>
  </PropertyGroup>
</Project>
```

## <a name="mark-your-project-as-read-only"></a>Markieren Sie das Projekt als schreibgeschützt.

In Visual Studio 2019, Version 16,7 und höher, können Sie *Projekte als Schreib*geschützt markieren. Um das Projekt als schreibgeschützt zu markieren, fügen Sie der Datei die folgende Eigenschaft *`.vcxproj`* oder einer der importierten Dateien hinzu:

```xml
<PropertyGroup>
    <ReadOnlyProject>true</ReadOnlyProject>
</PropertyGroup>
```

`<ReadOnlyProject>`Durch die Einstellung wird verhindert, dass Visual Studio das Projekt bearbeitet und speichert, sodass Sie beliebige MSBuild-Konstrukte darin verwenden können, einschließlich Platzhaltern.

Es ist wichtig zu wissen, dass der Projekt Cache nicht verfügbar ist, wenn Visual Studio Platzhalter in Projekt Elementen in der *`.vcxproj`* Datei oder einem seiner Importe erkennt. Ladezeiten von Projektmappen in der IDE sind viel länger, wenn Sie über viele Projekte verfügen, die Platzhalter verwenden.

## <a name="move-wildcard-items-to-a-target-body"></a>Platzhalter Elemente in einen Zieltext verschieben

Sie können Platzhalter verwenden, um Ressourcen zu erfassen, generierte Quellen hinzuzufügen usw. Wenn Sie diese im Fenster Projektmappen-Explorer nicht benötigen, können Sie stattdessen dieses Verfahren verwenden:

1. Ändern Sie den Namen der Element Gruppe, um Platzhalter hinzuzufügen. Beispielsweise anstelle von:

   ```xml
   <Image Include="*.bmp" />
   <ClCompile Include="*.cpp" />
   ```

   Ändern Sie ihn in:

   ```xml
   <_WildCardImage Include="*.bmp" />
   <_WildCardClCompile Include="*.cpp" />
   ```

1. Fügen Sie den Inhalt der  *`.vcxproj`* Datei hinzu.Sie können es auch einer *`Directory.Build.targets`* Datei in einem Stammverzeichnis hinzufügen, um alle Projekte unter diesem Stammverzeichnis zu beeinflussen:

   ```xml
   <Target Name="AddWildCardItems"
       AfterTargets="BuildGenerateSources">
     <ItemGroup>
       <Image Include="@(_WildCardImage)" />
       <ClCompile Include="@(_WildCardClCompile)" />
     </ItemGroup>
   </Target>
   ```

   Diese Änderung bewirkt, dass der Build die Elemente enthält, die in der  *`.vcxproj`* Datei definiert sind. Sie werden jedoch im Projektmappen-Explorer Fenster nicht angezeigt, und Sie verursachen keine Probleme in der IDE.

1.  `_WildCardClCompile`   Fügen Sie den folgenden Inhalt hinzu, um den korrekten IntelliSense für Elemente anzuzeigen, wenn Sie diese Dateien im Editor öffnen:

   ```xml
   <PropertyGroup>
     <ComputeCompileInputsTargets>
       AddWildCardItems
       $(ComputeCompileInputsTargets)
     </ComputeCompileInputsTargets>
   </PropertyGroup>
   ```

In der Tat können Sie Platzhalter für alle Elemente in einem Zieltext verwenden. Sie können auch Platzhalter in einem verwenden  `ItemGroup`   , der nicht als Projekt Element durch ein-Objekt definiert ist [`ProjectSchemaDefinition`](https://devblogs.microsoft.com/cppblog/vc-MSBuild-extensibility-example/) .

> [!NOTE]
> Wenn Sie Platzhalter aus einer *`.vcxproj`* Datei in eine importierte Datei verschieben, werden Sie im Projektmappen-Explorer Fenster nicht angezeigt. Durch diese Änderung kann Ihr Projekt auch ohne Änderungen in der IDE geladen werden. Diese Vorgehensweise wird jedoch nicht empfohlen, da der Projekt Cache deaktiviert wird.

## <a name="see-also"></a>Weitere Informationen

[Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio](../working-with-project-properties.md)<br/>
[XML-Dateien der Eigenschaften Seite](property-page-xml-files.md)

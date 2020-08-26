---
title: 'Vorgehensweise: Ändern von C++-Projekteigenschaften und Zielen ohne Änderungen an der Projektdatei'
ms.date: 11/28/2018
helpviewer_keywords:
- project properties [C++], modifying outside project file
ms.openlocfilehash: a1ba5647542f69cfc7748986e512e74401bfc404
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "88833360"
---
# <a name="how-to-modify-c-project-properties-and-targets-without-changing-the-project-file"></a>Vorgehensweise: Ändern von C++-Projekteigenschaften und Zielen ohne Änderungen an der Projektdatei

Sie können Projekteigenschaften und -ziele über die MSBuild-Eingabeaufforderung überschreiben, ohne die Projektdatei zu ändern. Dies ist nützlich, wenn Sie einige Eigenschaften vorübergehend oder gelegentlich anwenden möchten. MSBuild-Kenntnisse sind hierbei von Vorteil. Weitere Informationen finden Sie unter [MSBuild](/visualstudio/msbuild/msbuild).

> [!IMPORTANT]
> Sie können den XML-Editor in Visual Studio oder einen beliebigen Text-Editor verwenden, um die PROPS- oder TARGETS-Datei zu erstellen. Verwenden Sie in diesem Szenario nicht den **Eigenschaften-Manager**, da dieser die Eigenschaften zur Projektdatei hinzufügt.

*So überschreiben Sie Projekteigenschaften:*

1. Erstellen Sie eine PROPS-Datei, die die Eigenschaften angibt, die Sie überschreiben möchten.

1. Geben Sie über die Eingabeaufforderung Folgendes ein: set ForceImportBeforeCppTargets="C:\sources\my_props.props"

*So überschreiben Sie Projektziele:*

1. Erstellen Sie eine TARGETS-Datei mit ihrer Implementierung oder einem bestimmten Ziel.

2. Geben Sie über die Eingabeaufforderung Folgendes ein: set ForceImportAfterCppTargets ="C:\sources\my_target.targets"

Sie können diese Optionen auch über die MSBuild-Befehlszeile festlegen, indem Sie die Option „/p:“ verwenden:

```cmd
> msbuild myproject.sln /p:ForceImportBeforeCppTargets="C:\sources\my_props.props"
> msbuild myproject.sln /p:ForceImportAfterCppTargets="C:\sources\my_target.targets"
```

Das Überschreiben von Eigenschaften und Zielen auf diese Weise entspricht dem Hinzufügen folgender Importe zu allen VCXPROJ-Dateien in der Projektmappe:

```cmd
<Import Project=="C:\sources\my_props.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
<Import Project==" C:\sources\my_target.targets"" />
```

---
title: Eigenschaftenseite "Allgemein" (Datei)
ms.date: 08/30/2019
f1_keywords:
- VC.Project.VCFileConfiguration.ExcludedFromBuild
- VC.Project.VCFileConfiguration.Tool
ms.assetid: 26e3711e-9e7d-4e8d-bc4c-2474538efdad
ms.openlocfilehash: 7626e161e6f59de32d426b558827c423a0bb050d
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90041379"
---
# <a name="general-property-page-file"></a>Eigenschaftenseite "Allgemein" (Datei)

Dieses Thema bezieht sich auf Windows-Projekte. Informationen zu Projekten unter anderen Betriebssystemen als Windows finden Sie unter [Referenz zur Linux C++-Eigenschaftenseite](../../linux/prop-pages-linux.md).

Wenn Sie mit der rechten Maustaste auf einen Datei Knoten **Projektmappen-Explorer**klicken, wird die Eigenschaften Seite **Allgemein** unter dem Knoten **Konfigurations Eigenschaften** geöffnet. Sie enthält die folgenden Eigenschaften:

- **Vom Build ausgeschlossen**

   Gibt an, ob die Datei im Build für die aktuelle Konfiguration enthalten sein soll.

   Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.ExcludedFromBuild%2A>.

- **Inhalt** (gilt nur für UWP-apps.) Gibt an, ob die Dateiinhalte enthält, die in das App-Paket eingeschlossen werden sollen.

- **Elementtyp**

   Der **Elementtyp** gibt das Tool an, das zum Verarbeiten der Datei während des Buildprozesses verwendet wird. [Dateien, deren Erweiterung Visual Studio bekannt ist,](/visualstudio/extensibility/visual-cpp-project-extensibility#project-items) haben in dieser Eigenschaft einen Standardwert. Sie können hier ein benutzerdefiniertes Tool angeben, wenn Sie einen benutzerdefinierten Dateityp haben oder das Standard Tool für einen bekannten Dateityp überschreiben möchten. Weitere Informationen finden Sie unter [Specifying Custom Build Tools (Angeben von benutzerdefinierten Buildtools)](../specifying-custom-build-tools.md). Sie können diese Eigenschaften Seite auch verwenden, um anzugeben, dass eine Datei nicht Teil des Buildprozesses ist.

   Die folgende Abbildung zeigt die Eigenschaften Seite für eine *cpp* -Datei. Der Standard **Elementtyp** für diese Art von Datei ist der **C/C++-Compiler** (*cl.exe*), und die Eigenschaften Seite macht verschiedene Compilereinstellungen verfügbar, die nur auf diese Datei angewendet werden können.

   ![Eigenschaften Seite "Allgemein" für ein Projekt Element](media/file-general-item-type.png "Elementtyp Auswahl")

    In der folgenden Tabelle sind die Standardelement Typen aufgeführt:

    |Dateierweiterung|Elementtyp|Standard Tool|
    |-|-|-|
    |APPX|XAML-Anwendungs Definition|[App-Packager](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |. HLSL,. CSO|HLSL-Compiler|[fxc.exe](/windows/win32/direct3dtools/fxc)|
    |.h|C/C++-Header|[C/C++-Präprozessor](../../preprocessor/c-cpp-preprocessor-reference.md)|
    |–|Ist nicht Teil des Builds|–|
    |. XML,. XSLT,. Xsl|Xml|[XML-Editor](/visualstudio/xml-tools/xml-editor)|
    |. resw,. resjson|PRI-Ressource (UWP-Apps)|[MakePri.exe](/windows/uwp/app-resources/compile-resources-manually-with-makepri)|
    ||Medien (UWP)|[App-Packager](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |.xsd|XML-Daten Generator (Tool)|Das [XML-Schema Definitions Tool (Xsd.exe)](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe) (erfordert .NET-Arbeitsauslastung. Nicht in MSVC enthalten.)|
    ||Manifesttool|[mt.exe](/windows/win32/sbscs/mt-exe)|
    |.rc|Resource|[Windows-Ressourcen Compiler (rc.exe)](/windows/win32/menurc/resource-compiler)|
    |. appxmanifest|App-Paket Manifest|[App-Packager](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |OBJ|Object|[C/C++-Linker (link.exe)](cl-invokes-the-linker.md)|
    |.ttf|Schriftart|–|
    |.txt|Text|–|
    |–|Custom Build-Tool|Benutzerdefiniert|
    |–|Datei kopieren|–|
    |. packagelayout|Layout des App-Pakets|[App-Packager](/windows/win32/appxpkg/make-appx-package--makeappx-exe-)|
    |RESX-Datei|Vom Compiler verwaltete Ressource|[Resgen.exe (Resource File Generator)](/dotnet/framework/tools/resgen-exe-resource-file-generator)|
    |natvis|C++-Debugger-Visualisierungs Datei|[Natvis-Framework](/visualstudio/debugger/create-custom-views-of-native-objects)|
    |JPG, BMP, ICO usw.|Image|Ressourcen Compiler basierend auf dem Anwendungstyp.|
    |.cpp|C/C++-Compiler|cl.exe|

   Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCFileConfiguration.Tool%2A>.

Informationen zum Zugreifen auf die Eigenschaften Seite " **Allgemein** " unter dem Knoten " **Konfigurations Eigenschaften** " finden Sie unter [Set C++ Compiler and Build Properties in Visual Studio](../working-with-project-properties.md).

## <a name="see-also"></a>Siehe auch

[Windows C++-Projekteigenschaftenseitenverweis](property-pages-visual-cpp.md)

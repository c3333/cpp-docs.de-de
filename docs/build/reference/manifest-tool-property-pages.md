---
title: Eigenschaftenseiten des Manifesttools
ms.date: 07/24/2019
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
- VC.Project.VCManifestTool.AdditionalManifestFiles
- VC.Project.VCManifestTool.InputResourceManifests
- VC.Project.VCManifestTool.EmbedManifest
- VC.Project.VCManifestTool.OutputManifestFile
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.GenerateCatalogFiles
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.ReplacementsFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- vc.project.AdditionalOptionsPage
ms.assetid: f33499c4-7733-42d9-80e3-8a5018786965
ms.openlocfilehash: 20ca118b3aacb02333d49b67d13de30f11dc5d8d
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079500"
---
# <a name="manifest-tool-property-pages"></a>Eigenschaftenseiten des Manifesttools

Verwenden Sie diese Seiten, um allgemeine Optionen für " [Mt. exe](/windows/win32/sbscs/mt-exe)" anzugeben. Diese Seiten finden Sie unter **Project** > **Properties** > **Configuration Properties** > **Manifest Tool**.

## <a name="general-property-page"></a>Eigenschaften Seite "Allgemein"

### <a name="suppress-startup-banner"></a>Startbanner unterdrücken

   **Ja (/nologo)** gibt an, dass standardmäßige Copyrightinformationen von Microsoft beim Starten des Manifesttools ausgeblendet werden. Verwenden Sie diese Option, um unerwünschte Ausgabe in Protokolldateien zu unterdrücken, wenn Sie die „mt.exe“ als Teil eines Buildprozesses oder in einer Buildumgebung ausführen.

### <a name="verbose-output"></a>Ausführliche Ausgabe

   **Ja (/verbose)** gibt an, dass zusätzliche Buildinformationen während der Manifestgenerierung angezeigt werden.

### <a name="assembly-identity"></a>Assemblyidentität * *

Verwendet die Option „/identity“, um eine Identitätszeichenfolge anzugeben, die aus den Attributen für das [\<assemblyIdentity>-Element](/visualstudio/deployment/assemblyidentity-element-clickonce-application) besteht. Eine Identitätszeichenfolge beginnt mit dem Wert für das `name`-Attribut gefolgt von *Attribut* = *Wert*-Paaren. Die Attribute in einer Identitätszeichenfolge werden durch Kommas getrennt.

Dies ist ein Beispiel für eine Identitäts Zeichenfolge: `Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`

## <a name="input-and-output-property-page"></a>Eingabe-und Ausgabe Eigenschaften Seite

###  <a name="additional-manifest-files"></a>Zusätzliche Manifest-Dateien

Verwendet die Option **/manifest**, um die vollständigen Pfade von zusätzlichen Manifestdateien anzugeben, die das Manifesttool verarbeitet oder zusammenführt. Vollständige Pfade werden durch Semikolons getrennt. (-Manifest [manifest1] [manifest2]...)

###  <a name="input-resource-manifests"></a>Eingabe Ressourcen Manifeste

Verwendet die Option **/inputresource**, um den vollständigen Pfad einer Ressource vom Typ RT_MANIFEST anzugeben, die in das Manifesttool eingegeben wird. Dem Pfad kann die angegebene Ressourcen-ID folgen. Beispiel:

`dll_with_manifest.dll;#1`

###  <a name="embed-manifest"></a>Manifest einbetten

- **Ja** gibt an, dass das Projektsystem die Anwendungsmanifestdatei in die Assembly einbettet.

- **Nein** gibt an, dass das Projektsystem die Anwendungsmanifestdatei als eigenständige Datei erstellt.

###  <a name="output-manifest-file"></a>Ausgabe Manifest-Datei

Gibt den Namen der Ausgabemanifestdatei an. Diese Eigenschaft ist optional, wenn nur eine Manifestdatei mit dem Manifesttool bearbeitet wird. (-out: [Datei]; # [Ressourcen-ID])

###  <a name="manifest-resource-file"></a>Manifestressourcendatei

Gibt die Ausgaberessourcen-Datei an, die verwendet wird, um das Manifest in die Projektausgabe einzubetten.

###  <a name="generate-catalog-files"></a>Katalogdateien generieren

Verwendet die Option **/makecdfs**, um anzugeben, dass das Manifesttool die Katalogdefinitionsdateien (CDF-Dateien) generiert, die zum Erstellen von Katalogen verwendet werden. /makecdfs

###  <a name="generate-manifest-from-managedassembly"></a>Manifest aus ManagedAssembly generieren

Generiert ein Manifest aus einer verwalteten Assembly. (-managedassemblyname: [Datei])

###  <a name="suppress-dependency-element"></a>Abhängigkeits Element unterdrücken

Wird mit-Managedassembly verwendet. unterdrückt die Generierung von Abhängigkeits Elementen im endgültigen Manifest. (-noabhängigkeit)

###  <a name="generate-category-tags"></a>Kategorietags generieren

Wird mit-Managedassembly verwendet. -Category bewirkt, dass die kategorietags generiert werden. (-Category)

###  <a name="dpi-awareness"></a>DPI-Informationen

Gibt an, ob die Anwendung DPI-fähig ist. Für MFC-Projekte ist diese Einstellung standardmäßig auf **Ja** festgelegt, andernfalls ist **Nein** festgelegt, da nur MFC-Projekte über integrierte DPI-Unterstützung verfügen. Sie können die Einstellung auf **Ja** festlegen, indem Sie Code hinzufügen, um verschiedene DPI-Einstellungen zu verarbeiten. Wenn Sie Ihre Anwendung auf DPI-fähig einstellen und sie nicht DPI-fähig ist, wird sie möglicherweise verschwommen oder klein angezeigt.

**choices**

- **None**
- **Hohe dpi-Werten**
- **Hohe dpi-Werten pro Monitor**

## <a name="isolated-com-property-page"></a>Isolierte COM-Eigenschaften Seite

Weitere Informationen zu isolierten com finden Sie unter [isolierte Anwendungen](/windows/win32/SbsCs/isolated-applications) und Gewusst [wie: Erstellen isolierter Anwendungen für die Nutzung von COM-Komponenten](../how-to-build-isolated-applications-to-consume-com-components.md).

###  <a name="type-library-file"></a>Typbibliotheks Datei

Gibt die Typbibliothek an, die für die Unterstützung des unterstützten com-Manifests verwendet wird (-TLB: [Datei])

###  <a name="registrar-script-file"></a>Registrierungs Skriptdatei

Gibt die Registrierungs Skriptdatei an, die für die Unterstützung des unterstützten com-Manifests verwendet wird (-RGS: [Datei])

###  <a name="component-file-name"></a>Komponenten Dateiname

Gibt den Dateinamen der Komponente an, die aus der. tlb-oder RGS-Datei erstellt wird. (-dll: [Datei])

###  <a name="replacements-file"></a>Ersetzungs Datei

Gibt die Datei an, die Werte für ersetzbare Zeichen folgen in der RGS-Datei enthält. (Ersetzungen: [Datei])

## <a name="advanced-property-page"></a>Erweiterte Eigenschaften Seite

###  <a name="update-file-hashes"></a>Dateihashes aktualisieren

Berechnet den Hash der in den Datei Elementen angegebenen Dateien und aktualisiert das Hash Attribut mit diesem Wert. (hashupdate: [Pfad])

###  <a name="update-file-hashes-search-path"></a>Suchpfad für Dateihashes aktualisieren

Gibt den Suchpfad an, der beim Aktualisieren der Dateihashes verwendet werden soll.

###  <a name="additional-options"></a>Zusätzliche Optionen

Zusätzliche Optionen

## <a name="see-also"></a>Weitere Informationen

[C++Referenz zur Projekteigenschaften Seite](property-pages-visual-cpp.md)

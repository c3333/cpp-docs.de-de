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
ms.openlocfilehash: e1d0f1ac889cb915216ceb70d48e36efe4ad21bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336301"
---
# <a name="manifest-tool-property-pages"></a>Eigenschaftenseiten des Manifesttools

Verwenden Sie diese Seiten, um allgemeine Optionen für [Mt.exe](/windows/win32/sbscs/mt-exe)anzugeben. Diese Seiten finden Sie unter **Project** > **Properties** > **Configuration Properties** > **Manifest Tool**.

## <a name="general-property-page"></a>Eigenschaftenseite „Allgemein“

### <a name="suppress-startup-banner"></a>Startbanner unterdrücken

   **Ja (/nologo)** gibt an, dass standardmäßige Copyrightinformationen von Microsoft beim Starten des Manifesttools ausgeblendet werden. Verwenden Sie diese Option, um unerwünschte Ausgabe in Protokolldateien zu unterdrücken, wenn Sie die „mt.exe“ als Teil eines Buildprozesses oder in einer Buildumgebung ausführen.

### <a name="verbose-output"></a>Verbose Ausgabe

   **Ja (/verbose)** gibt an, dass zusätzliche Buildinformationen während der Manifestgenerierung angezeigt werden.

### <a name="assembly-identity"></a>Assemblyidentität

Verwendet die Option /identity, um eine Identitätszeichenfolge anzugeben, die die Attribute für die [ \<assemblyIdentity> Element](/visualstudio/deployment/assemblyidentity-element-clickonce-application)umfasst. Eine Identitätszeichenfolge beginnt mit `name` dem Wert für das Attribut und wird von*Attributwertpaaren* *attribute* = gefolgt. Die Attribute in einer Identitätszeichenfolge werden durch Kommas getrennt.

Dies ist eine Beispiel-Identitätszeichenfolge:`Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`

## <a name="input-and-output-property-page"></a>Eingabe- und Ausgabeeigenschaftsseite

### <a name="additional-manifest-files"></a>Zusätzliche Manifestdateien

Verwendet die Option **/manifest**, um die vollständigen Pfade von zusätzlichen Manifestdateien anzugeben, die das Manifesttool verarbeitet oder zusammenführt. Vollständige Pfade werden durch Semikolons getrennt. (-manifest [manifest1] [manifest2] ...)

### <a name="input-resource-manifests"></a>Ressourcenmanifeste eingeben

Verwendet die Option **/inputresource**, um den vollständigen Pfad einer Ressource vom Typ RT_MANIFEST anzugeben, die in das Manifesttool eingegeben wird. Dem Pfad kann die angegebene Ressourcen-ID folgen. Beispiel:

`dll_with_manifest.dll;#1`

### <a name="embed-manifest"></a>Manifest einbetten

- **Ja** gibt an, dass das Projektsystem die Anwendungsmanifestdatei in die Assembly einbettet.

- **Nein** gibt an, dass das Projektsystem die Anwendungsmanifestdatei als eigenständige Datei erstellt.

### <a name="output-manifest-file"></a>Manifestdatei ausgeben

Gibt den Namen der Ausgabemanifestdatei an. Diese Eigenschaft ist optional, wenn nur eine Manifestdatei mit dem Manifesttool bearbeitet wird. (-out:[datei];[Ressourcen-ID])

### <a name="manifest-resource-file"></a>Manifestressourcendatei

Gibt die Ausgaberessourcen-Datei an, die verwendet wird, um das Manifest in die Projektausgabe einzubetten.

### <a name="generate-catalog-files"></a>Katalogdateien generieren

Verwendet die Option **/makecdfs**, um anzugeben, dass das Manifesttool die Katalogdefinitionsdateien (CDF-Dateien) generiert, die zum Erstellen von Katalogen verwendet werden. (/makecdfs)

### <a name="generate-manifest-from-managedassembly"></a>Manifest aus einer verwalteten Assembly generieren

Generiert ein Manifest aus einer verwalteten Assembly. (-verwalteter Assemblyname:\[Datei])

### <a name="suppress-dependency-element"></a>Abhängigkeitselement unterdrücken

Wird mit -managedassembly verwendet. unterdrückt die Generierung von Abhängigkeitselementen im endgültigen Manifest. (-keine Abhängigkeit)

### <a name="generate-category-tags"></a>Kategorietags generieren

Wird mit -managedassembly verwendet. -Kategorie bewirkt, dass die Kategorie-Tags generiert werden. (-Kategorie)

### <a name="dpi-awareness"></a>DPI-Bewusstsein

Gibt an, ob die Anwendung DPI-fähig ist. Für MFC-Projekte ist diese Einstellung standardmäßig auf **Ja** festgelegt, andernfalls ist **Nein** festgelegt, da nur MFC-Projekte über integrierte DPI-Unterstützung verfügen. Sie können die Einstellung auf **Ja** festlegen, indem Sie Code hinzufügen, um verschiedene DPI-Einstellungen zu verarbeiten. Wenn Sie Ihre Anwendung auf DPI-fähig einstellen und sie nicht DPI-fähig ist, wird sie möglicherweise verschwommen oder klein angezeigt.

**Entscheidungen**

- **None**
- **Hoher DPI-Bekannt**
- **Pro Monitor High DPI Aware**

## <a name="isolated-com-property-page"></a>Isolierte COM-Eigenschaftsseite

Weitere Informationen zu isoliertem COM finden Sie unter [Isolierte Anwendungen](/windows/win32/SbsCs/isolated-applications) und [Wie Sie: Erstellen isolierter Anwendungen zur Nutzung von COM-Komponenten](../how-to-build-isolated-applications-to-consume-com-components.md).

### <a name="type-library-file"></a>Typbibliotheksdatei

Gibt die Typbibliothek an, die für die regfree COM-Manifestunterstützung verwendet werden soll. (-tlb:[Datei])

### <a name="registrar-script-file"></a>Registrierungsskriptdatei

Gibt die Registrierungsskriptdatei an, die für die regullose COM-Manifestunterstützung verwendet werden soll. (-rgs:[Datei])

### <a name="component-file-name"></a>Komponentendateiname

Gibt den Dateinamen der Komponente an, die aus den angegebenen .tlb- oder .rgs-Komponenten erstellt wird. (-dll:[Datei])

### <a name="replacements-file"></a>Ersetzungsdatei

Gibt die Datei an, die Werte für ersetzbare Zeichenfolgen in der RGS-Datei enthält. (Ersatz:[Datei])

## <a name="advanced-property-page"></a>Erweiterte Eigenschaftenseite

### <a name="update-file-hashes"></a>Dateihashes aktualisieren

Berechnet den Hash der in den Dateielementen angegebenen Dateien und aktualisiert das Hashattribut mit diesem Wert. (hashupdate:[pfad])

### <a name="update-file-hashes-search-path"></a>Suchpfad für Dateihashes aktualisieren

Gibt den Suchpfad an, der beim Aktualisieren der Dateihashes verwendet werden soll.

### <a name="additional-options"></a>Zusätzliche Optionen

Zusätzliche Optionen

## <a name="see-also"></a>Siehe auch

[C++-Projekteigenschaftsseitenverweis](property-pages-visual-cpp.md)

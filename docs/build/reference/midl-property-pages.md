---
title: MIDL-Compilereigenschaftenseiten
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 57498a01-fccc-4a0e-a036-6ff702f83126
f1_keywords:
- VC.Project.VCMidlTool.PreprocessorDefinitions
- VC.Project.VCMidlTool.AdditionalIncludeDirectories
- VC.Project.VCMidlTool.AdditionalMetadataDirectories
- VC.Project.VCMidlTool.IgnoreStandardIncludePath
- VC.Project.VCMidlTool.IgnoreStandardIncludePath
- VC.Project.VCMidlTool.MkTypLibCompatible
- VC.Project.VCMidlTool.WarningLevel
- VC.Project.VCMidlTool.WarnAsError
- VC.Project.VCMidlTool.SuppressStartupBanner
- VC.Project.VCMidlTool.DefaultCharType
- VC.Project.VCMidlTool.TargetEnvironment
- VC.Project.VCMidlTool.GenerateStublessProxies
- VC.Project.VCMidlTool.SuppressCompilerWarnings
- VC.Project.VCMidlTool.ApplicationConfigurationMode
- VC.Project.VCMidlTool.LocaleID
- VC.Project.VCMidlTool.MultiProcMIDL
- VC.Project.VCMidlTool.OutputDirectory
- VC.Project.VCMidlTool.WinmdFileName
- VC.Project.VCMidlTool.HeaderFileName
- VC.Project.VCMidlTool.DLLDataFileName
- VC.Project.VCMidlTool.InterfaceIdentifierFileName
- VC.Project.VCMidlTool.ProxyFileName
- VC.Project.VCMidlTool.GenerateTypeLibrary
- VC.Project.VCMidlTool.TypeLibraryName
- VC.Project.VCMidlTool.GenerateClientFiles
- VC.Project.VCMidlTool.GenerateServerFiles
- VC.Project.VCMidlTool.ClientStubFile
- VC.Project.VCMidlTool.ServerStubFile
- VC.Project.VCMidlTool.TypeLibFormat
- VC.Project.VCMidlTool.CPreprocessOptions
- VC.Project.VCMidlTool.UndefinePreprocessorDefinitions
- VC.Project.VCMidlTool.EnableErrorChecks
- VC.Project.VCMidlTool.ErrorCheckAllocations
- VC.Project.VCMidlTool.ErrorCheckBounds
- VC.Project.VCMidlTool.ErrorCheckEnumRange
- VC.Project.VCMidlTool.ErrorCheckRefPointers
- VC.Project.VCMidlTool.ErrorCheckStubData
- VC.Project.VCMidlTool.PreendWithABINamepsace
- VC.Project.VCMidlTool.ValidateParameters
- VC.Project.VCMidlTool.StructMemberAlignment
- VC.Project.VCMidlTool.RedirectOutputAndErrors
- VC.Project.VCMidlTool.MinimumTargetSystem
- vc.project.AdditionalOptionsPage
ms.openlocfilehash: d6833230baca892836c187799df7f0658aa16772
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336253"
---
# <a name="midl-property-pages"></a>Eigenschaftenseiten "MIDL"

Die MIDL-Eigenschaftenseiten sind als Elementeigenschaft auf einer verfügbar. IDL-Datei in einem C++-Projekt, das COM verwendet. Verwenden Sie sie, um den [MIDL-Compiler](/windows/win32/midl/using-the-midl-compiler-2)zu konfigurieren. Informationen zum programmgesteuerten Zugriff auf die MIDL-Optionen für C++-Projekte finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>. Siehe auch [Allgemeine MIDL-Befehlszeilensyntax](/windows/win32/midl/general-midl-command-line-syntax).

## <a name="general-property-page"></a>Eigenschaftenseite „Allgemein“

### <a name="preprocessor-definitions"></a>Präprozessordefinitionen

Gibt eine oder mehrere Definitionen an, einschließlich MIDL-Makros ([/D](/windows/win32/midl/-d))\[Makros\]).

### <a name="additional-include-directories"></a>Zusätzliche Includeverzeichnisse

Gibt ein oder mehrere Verzeichnisse an, die dem\]Includepfad ([/I-Pfad](/windows/win32/midl/-i)\[) hinzugefügt werden sollen.

### <a name="additional-metadata-directories"></a>Zusätzliche Metadatenverzeichnisse

Geben Sie das Verzeichnis an, das die Datei\]Windows.Foundation.WinMD ([/metadata_dir](/windows/win32/midl/-metadata-dir) \[Pfad ) enthält.

### <a name="enable-windows-runtime"></a>Aktivieren der Windows-Runtime

Aktivieren Sie die Windows-Runtime-Semantik, um die Windows-Metadatendatei ([/winrt](/windows/win32/midl/-winrt)) zu erstellen.

### <a name="ignore-standard-include-path"></a>Standard-Include-Pfad ignorieren

Ignorieren Sie das aktuelle und das INCLUDE-Verzeichnisse ([/no_def_idir](/windows/win32/midl/-no-def-idir)).

### <a name="mktyplib-compatible"></a>MktypLib kompatibel

Erzwingt die Kompatibilität mit mktyplib.exe Version 2.03 ([/mktyplib203](/windows/win32/midl/-mktyplib203)).

### <a name="warning-level"></a>Warnstufe

Wählt die Strenge der MIDL-Codefehler ([/W](/windows/win32/midl/-w)) aus.

**Entscheidungen**

- **1**
- **1**
- **2**
- **3**
- **4**

### <a name="treat-warnings-as-errors"></a>Warnungen als Fehler behandeln

Aktiviert MIDL, um alle Warnungen als Fehler zu behandeln ([/WX](/windows/win32/midl/-wx)).

### <a name="suppress-startup-banner"></a>Startbanner unterdrücken

Unterdrücken Sie die Anzeige des Startbanners und der Informationsmeldung ([/nologo](/windows/win32/midl/-nologo)).

### <a name="c-compiler-char-type"></a>C-Compiler-Char-Typ

Gibt den Standardzeichentyp des C-Compilers an, der zum Kompilieren des generierten Codes verwendet wird. ([/char](/windows/win32/midl/-char) signed|unsigned|ascii7).

**Entscheidungen**

- **Signiert** - Signiert
- **Nicht signiert** - Nicht signiert
- **Ascii** - Ascii

### <a name="target-environment"></a>Zielumgebung

Gibt an, welche Umgebung als Ziel gilt ([/env](/windows/win32/midl/-env) arm32|win32|ia64|x64).

**Entscheidungen**

- **Nicht eingestellt** - Win32
- **Microsoft Windows 32-Bit** - Win32
- **Microsoft Windows 64-Bit auf Itanium** - IA64
- **Microsoft Windows ARM** - ARM
- **Microsoft Windows ARM64** - ARM64
- **Microsoft Windows 64-Bit auf x64** - X64

### <a name="generate-stubless-proxies"></a>Generieren von stubless Proxies

Generieren Sie vollständig interpretierte Stubs mit Erweiterungen und stubless-Proxys für Objektschnittstellen ([/Oicf](/windows/win32/midl/-oi), [/Oif](/windows/win32/midl/-oi) ).

### <a name="suppress-compiler-warnings"></a>Unterdrücken von Compilerwarnungen

Unterdrücken von Compilerwarnungen ([/no_warn](/windows/win32/midl/-no-warn)).

### <a name="application-configuration-mode"></a>Anwendungskonfigurationsmodus

Ausgewählte ACF-Attribute in der IDL-Datei zulassen ([/app_config](/windows/win32/midl/-app-config)).

### <a name="locale-id"></a>Gebietsschemakennung

Gibt die LCID für Eingabedateien, Dateinamen und Verzeichnispfade ([/lcid](/windows/win32/midl/-lcid) DECIMAL) an.

### <a name="multi-processor-compilation"></a>Multiprozessor-Kompilierung

Führen Sie mehrere Instanzen gleichzeitig aus.

## <a name="output-property-page"></a>Ausgabeeigenschaftsseite

### <a name="output-directory"></a>Ausgabeverzeichnis

Gibt das Ausgabeverzeichnis ([/out](/windows/win32/midl/-out) [verzeichnis]) an.

### <a name="metadata-file"></a>Metadatendatei

Gibt den Namen der generierten Metadatendatei ([/winmd](/windows/win32/midl/-winmd) filename) an.

### <a name="header-file"></a>Headerdatei

Gibt den Namen der generierten[/h](/windows/win32/midl/-h) Headerdatei ( /h-Dateiname) an.

### <a name="dlldata-file"></a>DllData-Datei

Gibt den Namen der Datei DLLDATA ([/dlldata](/windows/win32/midl/-dlldata) filename) an.

### <a name="iid-file"></a>IID-Datei

Gibt den Namen für die Datei Interface Identifier ([/iid](/windows/win32/midl/-iid) filename) an.

### <a name="proxy-file"></a>Proxy-Datei

Gibt den Namen der Proxydatei ([/proxy](/windows/win32/midl/-proxy) filename) an.

### <a name="generate-type-library"></a>Generieren der Typbibliothek

Geben Sie an, dass keine Typbibliothek generiert werden soll ([/notlb] für nein).

### <a name="type-library"></a>Typbibliothek

Gibt den Namen der Typbibliotheksdatei ([/tlb-Dateiname)](/windows/win32/midl/-tlb) an.

### <a name="generate-client-stub-files"></a>Generieren von Client-Stub-Dateien

Nur Client-Stubdatei generieren ([/client](/windows/win32/midl/-client) [stub|none]).

**Entscheidungen**

- **Stub** - Stub
- **Keine** - Keine

### <a name="generate-server-stub-files"></a>Generieren von Server-Stub-Dateien

Nur Server-Stubdatei generieren ([/server](/windows/win32/midl/-server) [stub|none]).

**Entscheidungen**

- **Stub** - Stub
- **Keine** - Keine

### <a name="client-stub-file"></a>Client-Stub-Datei

Geben Sie die Client-Stub-Datei ([/cstub](/windows/win32/midl/-cstub) [datei]) an.

### <a name="server-stub-file"></a>Server-Stub-Datei

Geben Sie die Server-Stubdatei ([/sstub](/windows/win32/midl/-sstub) [datei]) an.

### <a name="type-library-format"></a>Typbibliotheksformat

Gibt das Dateiformat der Typbibliothek an ([/oldtlb|/newtlb]).

**Entscheidungen**

- **NewFormat** - Neues Format
- **OldFormat** - Altes Format

## <a name="advanced-property-page"></a>Erweiterte Eigenschaftenseite

### <a name="c-preprocess-options"></a>C Vorprozessoptionen

Gibt Die Switches werden an den C-Compilerpräprozessor ([/cpp_opt-Switches](/windows/win32/midl/-cpp-opt) übergeben).

### <a name="undefine-preprocessor-definitions"></a>Präprozessordefinitionen aufheben

Gibt eine oder mehrere unerlegt an, einschließlich MIDL-Makros ([/U](/windows/win32/midl/-U) [macros]).

### <a name="enable-error-checking"></a>Fehlerprüfung aktivieren

Fehlerüberprüfungsoption auswählen ([/error all|none]).

**Entscheidungen**

- **EnableCustom** - Alle
- **Alle** - Alle
- **Keine** - Keine

### <a name="check-allocations"></a>Überprüfen der Zuordnungen

Überprüfen Sie, ob Speicherfehler ([/error](/windows/win32/midl/-error) allocation) ausdemadien sind.

### <a name="check-bounds"></a>Prüfgrenzen

Prüfgröße im Vergleich zur Transmissionslängenspezifikation ([/error](/windows/win32/midl/-error) bounds_check).

### <a name="check-enum-range"></a>Überprüfen des Enum-Bereichs

Überprüfen Sie Enumerumwerte im zulässigen Bereich ([/error](/windows/win32/midl/-error) enum).

### <a name="check-reference-pointers"></a>Referenzzeiger überprüfen

Überprüfen Sie, ob Verweiszeiger nicht NULL sind ([/error](/windows/win32/midl/-error) ref).

### <a name="check-stub-data"></a>Stubdaten überprüfen

Zusätzliche Überprüfung auf serverseitige Stubdatengültigkeit ([/error](/windows/win32/midl/-error) stub_data).

### <a name="prepend-with-abi-namespace"></a>Präparat mit 'ABI'-Namespace

Setzen Sie den Namespace "ABI" allen Typen vor.  ([/ns_prefix](/windows/win32/midl/-ns-prefix)).

### <a name="validate-parameters"></a>Überprüfen von Parametern

Generieren Sie zusätzliche Informationen, um Parameter zu validieren ([/robust](/windows/win32/midl/-robust) | [/no_robust](/windows/win32/midl/-no-robust)).

### <a name="struct-member-alignment"></a>Struktur-Memberausrichtung

Gibt die Verpackungsebene von Strukturen im Zielsystem (/ZpN) an.

**Entscheidungen**

- **Nicht gesetzt** - nicht gesetzt
- **1 Byte** - Zp1
- **2 Byte** - Zp2
- **4 Byte** - Zp4
- **8 Byte** - Zp8

### <a name="redirect-output"></a>Umleitungsausgabe

Leitet die Ausgabe vom Bildschirm zu einer Datei ([/o-Datei)](/windows/win32/midl/-o) um.

### <a name="minimum-target-system"></a>Mindestzielsystem

Legen Sie das minimale Zielsystem ([/target STRING)](/windows/win32/midl/-target) fest.

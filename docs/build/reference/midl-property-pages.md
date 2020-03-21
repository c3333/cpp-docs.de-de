---
title: Eigenschaften Seiten für den Mittelpunkt Compiler
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
ms.openlocfilehash: 260936d01a611f061b0b4fa9a5c087ff38cc66a3
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076128"
---
# <a name="midl-property-pages"></a>Eigenschaftenseiten "MIDL"

Die Eigenschaften Seiten in der Mitte sind als Element Eigenschaft in verfügbar. Die IDL-Datei C++ in einem Projekt, das com verwendet. Verwenden Sie diese, um den [Mittel l-Compiler](/windows/win32/midl/using-the-midl-compiler-2)zu konfigurieren. Informationen zum programmgesteuerten Zugriff auf die MIDL-Optionen für C++-Projekte finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>. Siehe auch [allgemeine Syntax der Mittell-Befehlszeile](/windows/win32/midl/general-midl-command-line-syntax).

## <a name="general-property-page"></a>Eigenschaften Seite "Allgemein"

### <a name="preprocessor-definitions"></a>Präprozessordefinitionen

Gibt eine oder mehrere Definitionen an, einschließlich der/D-Makros ([/D](/windows/win32/midl/-d)), die\[Makros\])).

### <a name="additional-include-directories"></a>Zusätzliche Includeverzeichnisse

Gibt mindestens ein Verzeichnis an, das dem Include-Pfad hinzugefügt werden soll ([/I](/windows/win32/midl/-i)\[Pfad\]).

### <a name="additional-metadata-directories"></a>Weitere Metadatenverzeichnisse

Geben Sie das Verzeichnis an, das die Datei "Windows. Foundation. winmd" ([/metadata_dir](/windows/win32/midl/-metadata-dir) \[Pfad\]) enthält.

### <a name="enable-windows-runtime"></a>Aktivieren von Windows-Runtime

Aktivieren Sie Windows-Runtime Semantik zum Erstellen einer Windows-Metadatendatei ([/WinRT](/windows/win32/midl/-winrt)).

### <a name="ignore-standard-include-path"></a>Standardincludepfad ignorieren

Die aktuellen und include-Verzeichnisse ([/no_def_idir](/windows/win32/midl/-no-def-idir)) werden ignoriert.

### <a name="mktyplib-compatible"></a>MkTypLib-kompatibel

Erzwingt Kompatibilität mit MkTypLib. exe, Version 2,03 ([/mktyplib203](/windows/win32/midl/-mktyplib203)).

### <a name="warning-level"></a>Warnstufe

Wählt die strenge der Mittell-Code Fehler ([/W](/windows/win32/midl/-w)) aus.

**choices**

- **1**
- **1**
- **2**
- **3**
- **4**

### <a name="treat-warnings-as-errors"></a>Warnungen als Fehler behandeln

Ermöglicht es mittlerer l, alle Warnungen als Fehler zu behandeln ([/WX](/windows/win32/midl/-wx)).

### <a name="suppress-startup-banner"></a>Startbanner unterdrücken

Unterdrückt die Anzeige des Start Banners und der Informations Meldung ([/nologo](/windows/win32/midl/-nologo)).

### <a name="c-compiler-char-type"></a>C-Compiler char-Typ

Gibt den Standard Zeichentyp des C-Compilers an, der zum Kompilieren des generierten Codes verwendet wird. ([/char](/windows/win32/midl/-char) signiert | unsigned | ASCII7).

**choices**

- **Signiert** -signiert
- **Unsigned** -unsigned
- **ASCII** -ASCII

### <a name="target-environment"></a>Zielumgebung

Gibt an, welche Umgebung als Ziel festgelegt werden soll ([/env](/windows/win32/midl/-env) arm32 | Win32 | ia64 | x64).

**choices**

- **Nicht festgelegt** -Win32
- **Microsoft Windows 32-Bit** -Win32
- **Microsoft Windows 64-Bit auf Itanium** -ia64
- **Microsoft Windows Arm** -Arm
- **Microsoft Windows ARM64** -ARM64
- **Microsoft Windows 64-Bit auf x64** -x64

### <a name="generate-stubless-proxies"></a>Erstellen von stublosen Proxys

Generieren vollständig interpretierter stubys mit Erweiterungen und stubproxys für Objekt Schnittstellen ([/Oicf](/windows/win32/midl/-oi), [/OIF](/windows/win32/midl/-oi) ).

### <a name="suppress-compiler-warnings"></a>Unterdrücken von Compilerwarnungen

Unterdrücken von compilerwarnungs Meldungen ([/no_warn](/windows/win32/midl/-no-warn)).

### <a name="application-configuration-mode"></a>Anwendungs Konfigurations Modus

Ermöglicht die Auswahl ausgewählter ACF-Attribute in der IDL-Datei ([/app_config](/windows/win32/midl/-app-config)).

### <a name="locale-id"></a>Gebiets Schema-ID

Gibt die LCID für Eingabedateien, Dateinamen und Verzeichnispfade an ([/LCID](/windows/win32/midl/-lcid) Decimal).

### <a name="multi-processor-compilation"></a>Kompilierung mit mehreren Prozessoren

Führen Sie mehrere Instanzen gleichzeitig aus.

## <a name="output-property-page"></a>Ausgabe (Eigenschaften Seite)

### <a name="output-directory"></a>Ausgabeverzeichnis

Gibt das Ausgabeverzeichnis an ([/out](/windows/win32/midl/-out) [Verzeichnis]).

### <a name="metadata-file"></a>Metadatendatei

Gibt den Namen der generierten Metadatendatei an ([/winmd](/windows/win32/midl/-winmd) filename).

### <a name="header-file"></a>Headerdatei

Gibt den Namen der generierten Header Datei an ([/h](/windows/win32/midl/-h) filename).

### <a name="dlldata-file"></a>Dlldata-Datei

Gibt den Namen der dlldata-Datei an ([/dlldata](/windows/win32/midl/-dlldata) filename).

### <a name="iid-file"></a>IID-Datei

Gibt den Namen für die schnittstellenbezeichnerdatei an ([/IID](/windows/win32/midl/-iid) filename).

### <a name="proxy-file"></a>Proxy Datei

Gibt den Namen der Proxy Datei an ([/Proxy](/windows/win32/midl/-proxy) filename).

### <a name="generate-type-library"></a>Typbibliothek generieren

Geben Sie an, dass keine Typbibliothek generiert werden soll ([/notlb] für No).

### <a name="type-library"></a>Typbibliothek

Gibt den Namen der Typbibliotheks Datei an ([/tlb](/windows/win32/midl/-tlb) filename).

### <a name="generate-client-stub-files"></a>Client-Stub-Dateien generieren

Nur Client-Stub-Datei generieren ([/Client](/windows/win32/midl/-client) [Stub | none]).

**choices**

- **Stub** -Stub
- **None** -None

### <a name="generate-server-stub-files"></a>Server-Stub-Dateien generieren

Nur Server-Stub-Datei generieren ([/Server](/windows/win32/midl/-server) [Stub | none]).

**choices**

- **Stub** -Stub
- **None** -None

### <a name="client-stub-file"></a>Client-Stub-Datei

Geben Sie die Client-Stub-Datei an ([/cstub](/windows/win32/midl/-cstub) [File]).

### <a name="server-stub-file"></a>Server-Stub-Datei

Geben Sie die Server-Stub-Datei an ([/sstub](/windows/win32/midl/-sstub) [File]).

### <a name="type-library-format"></a>Format der Typbibliothek

Gibt das Format der Typbibliotheks Datei an ([/oldtlb |/newtlb]).

**choices**

- **Newformat** -neues Format
- **OldFormat** -altes Format

## <a name="advanced-property-page"></a>Erweiterte Eigenschaften Seite

### <a name="c-preprocess-options"></a>C-Vorverarbeitungs Optionen

Gibt Switches an, die an den C-compilerpräprozessor ([/Cpp_opt](/windows/win32/midl/-cpp-opt) Switches) übergeben werden.

### <a name="undefine-preprocessor-definitions"></a>Präprozessordefinitionen aufheben

Gibt eine oder mehrere nicht Definitionen an, einschließlich der Mittel l-Makros ([/U](/windows/win32/midl/-U) [Makros]).

### <a name="enable-error-checking"></a>Fehlerüberprüfung aktivieren

Wählen Sie die Option Fehlerüberprüfung ([/Error all | none]) aus.

**choices**

- **Enablecustom** -alle
- **Alle**
- **None** -None

### <a name="check-allocations"></a>Zuordnungen überprüfen

Überprüfen auf Fehler aufgrund von nicht genügend Arbeitsspeicher ([/Error](/windows/win32/midl/-error) -Zuordnung).

### <a name="check-bounds"></a>Grenzen überprüfen

Überprüfen Sie die Größe im Vergleich zur Übertragungs längenspezifikation ([/Error](/windows/win32/midl/-error) bounds_check).

### <a name="check-enum-range"></a>Aufzählungs Bereich überprüfen

Überprüfen Sie, ob die Enumerationswerte zulässig sind ([/Error](/windows/win32/midl/-error) Enumeration).

### <a name="check-reference-pointers"></a>Verweis Zeiger überprüfen

Überprüfen Sie, ob Verweis Zeiger nicht NULL sind ([/Error](/windows/win32/midl/-error) Ref).

### <a name="check-stub-data"></a>Stub-Daten überprüfen

Geben Sie eine zusätzliche Überprüfung auf die Gültigkeit der serverseitigen Stub-Daten ([/Error](/windows/win32/midl/-error) stub_data) aus.

### <a name="prepend-with-abi-namespace"></a>"Abi"-Namespace voransetzen

Fügen Sie allen Typen den "abi"-Namespace voran.  ([/ns_prefix](/windows/win32/midl/-ns-prefix)).

### <a name="validate-parameters"></a>Parameter überprüfen

Generieren Sie zusätzliche Informationen zum Überprüfen von Parametern ([/robust](/windows/win32/midl/-robust) | [/no_robust](/windows/win32/midl/-no-robust)).

### <a name="struct-member-alignment"></a>Ausrichtung von Strukturmembern

Gibt die Verpackungs Ebene von Strukturen im Zielsystem an (/ZpN).

**choices**

- **Nicht festgelegt** -nicht festgelegt
- **1 Byte** -Zp1
- **2 Byte** -Zp2
- **4 Byte** -zp4
- **8 Byte** -Zp8

### <a name="redirect-output"></a>Ausgabe umleiten

Leitet die Ausgabe vom Bildschirm an eine Datei ([/o](/windows/win32/midl/-o) -Datei) um.

### <a name="minimum-target-system"></a>Minimalziel System

Legen Sie das minimale Zielsystem fest ([/target](/windows/win32/midl/-target) String).

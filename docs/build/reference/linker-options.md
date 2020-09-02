---
title: MSVC (Linkeroptionen)
description: Eine Liste der Optionen, die vom Microsoft Link Linker unterstützt werden.
ms.date: 09/01/2020
f1_keywords:
- link
helpviewer_keywords:
- linker [C++]
- linker [C++], options listed
- libraries [C++], linking to COFF
- LINK tool [C++], linker options
ms.assetid: c1d51b8a-bd23-416d-81e4-900e02b2c129
ms.openlocfilehash: 0d85361b8d4b5896d9ed7beae0d310fe28dc98e9
ms.sourcegitcommit: e58918c45316d799c1952ca7797a85adbcd0c472
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/01/2020
ms.locfileid: "89281795"
---
# <a name="linker-options"></a>Linkeroptionen

"LINK.exe" ist ein Tool, das Objektdateien und Bibliotheken im COFF-Format (Common Object File Format) miteinander verbindet, um eine ausführbare Datei (EXE-Datei) oder eine DLL (Dynamic Link Library) zu erstellen.

In der folgenden Tabelle sind die Optionen für "LINK.exe" aufgelistet. Weitere Informationen zu LINK finden Sie unter:

- [Compilergesteuerte Link Optionen](compiler-controlled-link-options.md)

- [Verknüpfen von Eingabedateien](link-input-files.md)

- [Link Ausgabe](link-output.md)

- [Reservierte Wörter](reserved-words.md)

In der Befehlszeile wird die Groß-/Kleinschreibung bei Linkeroptionen nicht beachtet. Dies bedeutet beispielsweise, dass `/base` `/BASE` das gleiche ist. Anweisungen zum Angeben der einzelnen Optionen in der Befehlszeile oder in Visual Studio finden Sie in der Dokumentation zur entsprechenden Option.

Einige Linkeroptionen können Sie auch mit dem [comment](../../preprocessor/comment-c-cpp.md) -Pragma festlegen.

## <a name="linker-options-listed-alphabetically"></a>Linkeroptionen alphabetisch aufgelistet

|Option|Zweck|
|------------|-------------|
|[@](at-specify-a-linker-response-file.md)|Legt eine Antwortdatei fest.|
|[/ALIGN](align-section-alignment.md)|Legt die Ausrichtung eines Abschnitts fest.|
|[/ALLOWBIND](allowbind-prevent-dll-binding.md)|Gibt an, dass eine DLL nicht gebunden werden kann.|
|[/ALLOWISOLATION](allowisolation-manifest-lookup.md)|Gibt das Verhalten bei der Manifestsuche an.|
|[/APPCONTAINER](appcontainer-windows-store-app.md)|Gibt an, ob die App in einer appcontainer-Prozessumgebung ausgeführt werden muss.|
|[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md)|Fügt einem verwalteten Image das <xref:System.Diagnostics.DebuggableAttribute> hinzu.|
|[/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md)|Erstellt einen Link zu einer verwalteten Ressource.|
|[/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md)|Legt fest, dass ein MSIL-Modul (Microsoft Intermediate Language) in den Assembler importiert werden soll.|
|[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md)|Bettet eine verwaltete Ressourcendatei in eine Assembly ein.|
|[/Base](base-base-address.md)|Legt eine Basisadresse für das Programm fest.|
|[/CETCOMPAT](cetcompat.md)|Markiert die Binärdatei als "mit Stapel Schatten Stapel kompatibel".|
|[/CGTHREADS](cgthreads-compiler-threads.md)|Legt die Anzahl von cl.exe-Threads zur Verwendung für die Optimierung und Codegenerierung fest, wenn die Link-Zeitcodegenerierung angegeben ist.|
|[/CLRIMAGETYPE](clrimagetype-specify-type-of-clr-image.md)|Legt den Typ (IJW, rein oder sicher) eines CLR-Images fest.|
|[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md)|Behält den letzten Fehlercode von Funktionen bei, die vom P/Invoke-Mechanismus aufgerufen werden.|
|[/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md)|Gibt das Threadingattribut an, das auf den Einstiegspunkt des CLR-Programms angewendet wird.|
|[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md)|Gibt an, ob der Linker das SuppressUnmanagedCodeSecurity-Attribute auf vom Linker generierte PInvoke-Stub, die von verwaltetem Code aus systemeigene DLLs Aufrufen, anwendet.|
|[/Debug](debug-generate-debug-info.md)|Erstellt Debuginformationen.|
|[/DebugType](debugtype-debug-info-options.md)|Gibt an, welche Daten in Debuginformationen eingeschlossen werden sollen.|
|[/DEF](def-specify-module-definition-file.md)|Übergibt eine Moduldefinitionsdatei (DEF-Datei) an den Linker.|
|[/DEFAULTLIB](defaultlib-specify-default-library.md)|Durchsucht die angegebene Bibliothek beim Auflösen externer Verweise.|
|[/Delay](delay-delay-load-import-settings.md)|Steuert das verzögerte Laden von DLLs.|
|[/DELAYLOAD](delayload-delay-load-import.md)|Löst das verzögerte Laden der angegebenen DLL aus.|
|[/DELAYSIGN](delaysign-partially-sign-an-assembly.md)|Eine Assembly wird teilweise signiert.|
|[/DEPENDENTLOADFLAG](dependentloadflag.md)|Legt Standardflags für abhängige DLL-Ladungen fest.|
|[/DLL](dll-build-a-dll.md)|Erstellt eine DLL.|
|[/Driver](driver-windows-nt-kernel-mode-driver.md)|Erstellt einen Kernelmodustreiber.|
|[/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)|Gibt an, ob ein ausführbares Image generiert werden soll, das zur Ladezeit mithilfe der ASLR-Funktion (Address Space Layout Anordnung) neu erstellt wird.|
|[/Entry](entry-entry-point-symbol.md)|Legt die Startadresse fest.|
|[/ERRORREPORT](errorreport-report-internal-linker-errors.md)| Veraltet. Die Fehlerberichterstattung wird durch [Windows-Fehlerberichterstattung (wer)](/windows/win32/wer/windows-error-reporting) -Einstellungen gesteuert. |
|[/Export](export-exports-a-function.md)|Exportiert eine Funktion.|
|[/FILEALIGN](filealign.md)|Richtet Abschnitte in der Ausgabedatei an Vielfachen eines angegebenen Werts aus.|
|[/Fixed](fixed-fixed-base-address.md)|Erstellt ein Programm, das nur an seiner bevorzugten Basisadresse geladen werden kann.|
|[/Force](force-force-file-output.md)|Erzwingt die Fertigstellung des Links, auch wenn nicht aufgelöste oder mehrfach definierte Symbole vorliegen.|
|[/FUNCTIONPADMIN](functionpadmin-create-hotpatchable-image.md)|Erstellt ein Hotpatch-fähiges Image.|
|[/GENPROFILE, /FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)|Beide Optionen geben die Generierung einer *`.pgd`* Datei durch den Linker an, um die Profil gesteuerte Optimierung (PGO) zu unterstützen. /GENPROFILE und /FASTGENPROFILE verwenden unterschiedliche Standardparameter.|
|[/Guard](guard-enable-guard-checks.md)|Aktiviert den Ablaufsteuerungsschutz.|
|[/Heap](heap-set-heap-size.md)|Legt die Größe des Heap in Bytes fest.|
|[/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md)|Gibt die Unterstützung für 64-Bit-ASLR (Address Space Layout Randomization) mit hoher Entropie an.|
|[/IDLOUT](idlout-name-midl-output-files.md)|Gibt den Namen der *`.idl`* Datei und andere mittlere Ausgabedateien an.|
|[/Ignore](ignore-ignore-specific-warnings.md)|Unterdrückt die Ausgabe der angegebenen Linkerwarnungen.|
|[/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md)|Verhindert die Verarbeitung von Attributinformationen in eine *`.idl`* Datei.|
|[/IMPLIB](implib-name-import-library.md)|Überschreibt den Standardnamen für die Importbibliothek.|
|[/INCLUDE](include-force-symbol-references.md)|Erzwingt Symbolverweise.|
|[/Incremental](incremental-link-incrementally.md)|Steuert inkrementelles Verknüpfen.|
|[/INTEGRITYCHECK](integritycheck-require-signature-check.md)|Gibt an, dass für das Modul eine Signaturüberprüfung zur Ladezeit erforderlich ist.|
|[/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)|Gibt einen Schlüsselcontainer zum Signieren einer Assembly an.|
|[/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)|Gibt einen Schlüssel oder ein Schlüsselpaar zum Signieren einer Assembly an.|
|[/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md)|Teilt dem Compiler mit, dass die Anwendung Adressen unterstützt, die mehr als zwei Gigabytes umfassen|
|[/LIBPATH](libpath-additional-libpath.md)|Gibt einen Suchpfad vor dem Umgebungsbibliothekspfads an.|
|[/LINKREPRO](linkrepro.md)|Gibt einen Pfad zum Generieren von Link Reproduktions Artefakten in an.|
|[/LINKREPROTARGET](linkreprotarget.md)|Generiert eine Link Reproduktion nur, wenn das angegebene Ziel erstellt wird. <sup>16,1</sup>|
|[/LTCG](ltcg-link-time-code-generation.md)|Gibt Link-Zeitcodegenerierung an.|
|[/Machine](machine-specify-target-platform.md)|Legt die Zielplattform fest.|
|[/Manifest](manifest-create-side-by-side-assembly-manifest.md)|Erstellt eine parallele Manifestdatei und bettet sie optional in der Binärdatei ein.|
|[/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md)|Gibt einen \<dependentAssembly> Abschnitt in der Manifest-Datei an.|
|[/MANIFESTFILE](manifestfile-name-manifest-file.md)|Ändert den Standardnamen der Manifestdatei.|
|[/MANIFESTINPUT](manifestinput-specify-manifest-input.md)|Gibt eine Manifesteingabedatei an, die der Linker verarbeitet und in der Binärdatei einbettet. Sie können diese Option mehrmals verwenden, um mehr als eine Manifesteingabedatei anzugeben.|
|[/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md)|Gibt an, ob Informationen zur Benutzerkontensteuerung (UAC) in das Programmmanifest eingebettet werden.|
|[/Map](map-generate-mapfile.md)|Erstellt eine Zuordnungsdatei.|
|[/MAPINFO](mapinfo-include-information-in-mapfile.md)|Fügt die angegebenen Informationen in die Zuordnungsdatei ein.|
|[/Merge](merge-combine-sections.md)|Kombiniert Abschnitte miteinander.|
|[/MIDL](midl-specify-midl-command-line-options.md)|Gibt die MIDL-Befehlszeilenoptionen an.|
|[/NATVIS](natvis-add-natvis-to-pdb.md)|Fügt Debugger-Visualisierungen aus einer natvis-Datei zur Programmdatenbank (PDB) hinzu.|
|[/NoAssembly](noassembly-create-a-msil-module.md)|Unterdrückt die Erstellung einer .NET Framework-Assembly.|
|[/NODEFAULTLIB](nodefaultlib-ignore-libraries.md)|Ignoriert alle (angegebenen) Standardbibliotheken bei der Auflösung von externen Verweisen.|
|[/NOENTRY](noentry-no-entry-point.md)|Erstellt eine DLL, die nur als Ressource dient.|
|[/NOLOGO](nologo-suppress-startup-banner-linker.md)|Unterdrückt den Startbanner.|
|[/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)|Kennzeichnet eine ausführbare Datei als mit der Windows-Funktion zur Datenausführungsverhinderung kompatibel.|
|[/Opt](opt-optimizations.md)|Steuert die LINK-Optimierungen.|
|[/Order](order-put-functions-in-order.md)|Fügt COMDATs in einer vordefinierten Reihenfolge in das Image ein.|
|[/Out](out-output-file-name.md)|Gibt den Ausgabedateinamen an.|
|[/PDB](pdb-use-program-database.md)|Erstellt eine PDB-Datei.|
|[/PDBALTPATH](pdbaltpath-use-alternate-pdb-path.md)|Verwendet einen alternativen Speicherort zum Speichern einer PDB-Datei.|
|[/PDBSTRIPPED](pdbstripped-strip-private-symbols.md)|Erstellt eine PDB-Datei ohne Private Symbole.|
|[/PGD](pgd-specify-database-for-profile-guided-optimizations.md)|Gibt eine *`.pgd`* Datei für Profil gesteuerte Optimierungen an.|
|[/POGOSAFEMODE](pogosafemode-linker-option.md)|**Veraltet** Erstellt einen Thread sicheren, instrumentierten PGO-Build.|
|[/PROFILE](profile-performance-tools-profiler.md)|Erstellt eine Ausgabedatei, die mit dem Leistungstoolprofiler verwendet werden kann.|
|[/Release](release-set-the-checksum.md)|Legt die Prüfsumme im *`.exe`* Header fest.|
|[/SAFESEH](safeseh-image-has-safe-exception-handlers.md)|Legt fest, dass das Image eine Tabelle mit sicheren Ausnahmehandlern enthält.|
|[/SECTION](section-specify-section-attributes.md)|Überschreibt die Attribute eines Abschnitts.|
|["/Sourcelink"](sourcelink.md)|Gibt eine sourcelink-Datei an, die der PDB hinzugefügt werden soll.|
|[/Stack](stack-stack-allocations.md)|Legt die Stapelgröße in Bytes fest.|
|[/Stub](stub-ms-dos-stub-file-name.md)|Fügt ein MS-DOS-Stubprogramm an ein Win32-Programm an.|
|[/SUBSYSTEM](subsystem-specify-subsystem.md)|Weist das Betriebssystem an, wie die Datei ausgeführt werden soll *`.exe`* .|
|[/SWAPRUN](swaprun-load-linker-output-to-swap-file.md)|Weist das Betriebssystem an, die Linkerausgabe vor dem Ausführen in eine Auslagerungs Datei zu kopieren.|
|[/TLBID](tlbid-specify-resource-id-for-typelib.md)|Gibt Ressourcen-ID der vom Linker generierten Typbibliothek an.|
|[/TLBOUT](tlbout-name-dot-tlb-file.md)|Gibt den Namen der *`.tlb`* Datei und andere mittlere Ausgabedateien an.|
|[/TSAWARE](tsaware-create-terminal-server-aware-application.md)|Erstellt eine Anwendung, die auf dem Terminalserver ausgeführt werden soll.|
|[/USEPROFILE](useprofile.md)|Verwendet die Trainingsdaten für die Profil gesteuerte Optimierung, um ein optimiertes Image zu erstellen.|
|[/Verbose](verbose-print-progress-messages.md)|Druckt Linkerstatusmeldungen aus.|
|[/Version](version-version-information.md)|Weist eine Versionsnummer zu.|
|[/WHOLEARCHIVE](wholearchive-include-all-library-object-files.md)|Schließt jede Objektdatei aus angegebenen statischen Bibliotheken ein.|
|[/WINMD](winmd-generate-windows-metadata.md)|Aktiviert die Generierung einer Windows-Runtime-Metadatendatei.|
|[/WINMDFILE](winmdfile-specify-winmd-file.md)|Gibt den Dateinamen für die Ausgabedatei der Windows-Runtime-Metadaten (winmd) an, die von der [/WINMD](winmd-generate-windows-metadata.md) - Linkeroption generiert wird.|
|[/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md)|Gibt einen Schlüssel oder ein Schlüsselpaar an, um eine Windows-Runtime-Metadatendatei zu signieren.|
|[/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md)|Gibt einen Schlüsselcontainer zum Signieren einer Windows-Metadatendatei an.|
|[/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md)|Signiert teilweise eine Windows-Runtime-Metadatendatei (.winmd), indem der öffentliche Schlüssels in die winmd-Datei eingefügt wird.|
|[/WX](wx-treat-linker-warnings-as-errors.md)|Behandelt Linkerwarnungen als Fehler.|

<sup>16,1</sup> diese Option ist ab Visual Studio 2019 Version 16,1 verfügbar.

## <a name="see-also"></a>Weitere Informationen

[Referenz zur C/C++-Referenz](c-cpp-building-reference.md)\
[MSVC-Linkerreferenz](linking.md)

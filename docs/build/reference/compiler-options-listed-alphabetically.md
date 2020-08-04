---
title: Compileroptionen (alphabetisch sortiert)
description: Verweis Auflistung in alphabetischer Reihenfolge der Microsoft C/C++-Compilerbefehlszeilenoptionen.
ms.date: 07/29/2020
helpviewer_keywords:
- compiler options, C++
ms.openlocfilehash: 81f2fbfe385e8655193c5862455e6ffca3719c96
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520861"
---
# <a name="compiler-options-listed-alphabetically"></a>Compileroptionen (alphabetisch sortiert)

Diese Tabelle enthält eine alphabetische Liste der Compileroptionen. Eine Liste der Compileroptionen nach Kategorie finden Sie im Artikel zu den in der [Kategorie aufgeführten Compileroptionen](compiler-options-listed-by-category.md) .

## <a name="compiler-options"></a>Compileroptionen

| Option | Zweck |
|--|--|
| [`@`](at-specify-a-compiler-response-file.md) | Legt eine Antwortdatei fest. |
| [`/?`](help-compiler-command-line-help.md) | Listet die Compileroptionen auf. |
| [`/AI`](ai-specify-metadata-directories.md) | Gibt ein Verzeichnis an, das durchsucht werden soll, um Datei Verweise aufzulösen, die an die [`#using`](../../preprocessor/hash-using-directive-cpp.md) Anweisung |
| [`/analyze`](analyze-code-analysis.md) | Aktiviert die Codeanalyse. |
| [`/arch`](arch-minimum-cpu-architecture.md) | Gibt die Architektur für die Codegenerierung an. |
| [`/await`](await-enable-coroutine-support.md) | Aktivieren von Coroutinen-Erweiterungen (fort Setz Bare Funktionen). |
| [`/bigobj`](bigobj-increase-number-of-sections-in-dot-obj-file.md) | Erhöht die Anzahl von adressierbaren Abschnitten in einer OBJ-Datei. |
| [`/C`](c-preserve-comments-during-preprocessing.md) | Behält Kommentare beim Präprozessorlauf bei |
| [`/c`](c-compile-without-linking.md) | Kompiliert ohne Verknüpfen. |
| [`/cgthreads`](cgthreads-code-generation-threads.md) | Gibt die Anzahl der cl.exe-Threads an, die für Optimierung und Codegenerierung verwendet werden. |
| [`/clr`](clr-common-language-runtime-compilation.md) | Erzeugt eine Ausgabedatei, die auf der Common Language Runtime ausgeführt werden kann. |
| [`/constexpr`](constexpr-control-constexpr-evaluation.md) | Steuern Sie die **`constexpr`** Auswertung zum Zeitpunkt der Kompilierung. |
| [`/D`](d-preprocessor-definitions.md) | Definiert Konstanten und Makros. |
| [`/diagnostics`](diagnostics-compiler-diagnostic-options.md) | Steuert das Format von Diagnosemeldungen. |
| [`/doc`](doc-process-documentation-comments-c-cpp.md) | Verarbeitet Dokumentationskommentare zu einer XML-Datei. |
| [`/E`](e-preprocess-to-stdout.md) | Kopiert die Präprozessorausgabe in die Standardausgabe. |
| [`/EH`](eh-exception-handling-model.md) | Gibt das Modell der Ausnahmebehandlung an. |
| [`/EP`](ep-preprocess-to-stdout-without-hash-line-directives.md) | Kopiert die Präprozessorausgabe in die Standardausgabe. |
| [`/errorReport`](errorreport-report-internal-compiler-errors.md) | Veraltet. Die Fehlerberichterstattung wird durch [Windows-Fehlerberichterstattung (wer)](/windows/win32/wer/windows-error-reporting) -Einstellungen gesteuert. |
| [`/execution-charset`](execution-charset-set-execution-character-set.md) | Legen Sie den Ausführungs Zeichensatz fest. |
| [`/experimental:module`](experimental-module.md) | Ermöglicht die Unterstützung von experimentellen Modulen. |
| [`/experimental:preprocessor`](experimental-preprocessor.md) | Aktiviert die experimentelle Unterstützung für den Präprozessor. |
| [`/F`](f-set-stack-size.md) | Legt die Stapelgröße fest. |
| [`/favor`](favor-optimize-for-architecture-specifics.md) | Erzeugt Code, der für eine bestimmte x64-Architektur optimiert ist. Oder für die speziellen Mikro Architekturen in den amd64-und EM64T-Architekturen. |
| [`/FA`](fa-fa-listing-file.md) | Erstellt eine Listendatei. |
| [`/Fa`](fa-fa-listing-file.md) | Legt den Namen der Listendatei fest. |
| [`/FC`](fc-full-path-of-source-code-file-in-diagnostics.md) | Anzeige des vollständigen Pfads der Quellcodedateien im Diagnosetext in "cl.exe". |
| [`/Fd`](fd-program-database-file-name.md) | Benennt die Programmdatenbankdatei um. |
| [`/Fe`](fe-name-exe-file.md) | Benennt die ausführbare Datei um. |
| [`/FI`](fi-name-forced-include-file.md) | Führt eine Vorverarbeitung der angegebenen Includedatei durch. |
| [`/Fi`](fi-preprocess-output-file-name.md) | Legt den vorverarbeiteten Ausgabedateinamen fest. |
| [`/Fm`](fm-name-mapfile.md) | Erstellt eine Zuordnungs Datei. |
| [`/Fo`](fo-object-file-name.md) | Erstellt eine Objektdatei. |
| [`/fp`](fp-specify-floating-point-behavior.md) | Gibt das Gleitkommaverhalten an. |
| [`/Fp`](fp-name-dot-pch-file.md) | Gibt den Namen einer vorkompilierten Headerdatei an. |
| [`/FR`](fr-fr-create-dot-sbr-file.md)<br /><br /> [`/Fr`](fr-fr-create-dot-sbr-file.md) | Erstellt Browserdateien. **`/Fr`** ist veraltet. |
| [`/FS`](fs-force-synchronous-pdb-writes.md) | Erzwingt die Serialisierung aller Schreibvorgänge in die Programm Datenbankdatei (PDB-Datei) über MSPDBSRV.EXE. |
| [`/FU`](fu-name-forced-hash-using-file.md) | Erzwingt die Verwendung eines Datei namens, als ob er an die-Direktive übermittelt worden wäre [`#using`](../../preprocessor/hash-using-directive-cpp.md) . |
| [`/Fx`](fx-merge-injected-code.md) | Führt eingefügten Code mit der Quelldatei zusammen. |
| [`/GA`](ga-optimize-for-windows-application.md) | Codeoptimierung für Windows-Anwendung. |
| [`/Gd`](gd-gr-gv-gz-calling-convention.md) | Verwendet die- **`__cdecl`** Aufruf Konvention (nur x86). |
| [`/Ge`](ge-enable-stack-probes.md) | Veraltet. Aktiviert Stapelüberprüfungen. |
| [`/GF`](gf-eliminate-duplicate-strings.md) | Aktiviert Stringpooling. |
| [`/GH`](gh-enable-pexit-hook-function.md) | Ruft die Hookfunktion `_pexit`auf. |
| [`/Gh`](gh-enable-penter-hook-function.md) | Ruft die Hookfunktion `_penter`auf. |
| [`/GL`](gl-whole-program-optimization.md) | Aktiviert die Optimierung des gesamten Programms. |
| [`/Gm`](gm-enable-minimal-rebuild.md) | Veraltet. Aktiviert minimale Neuerstellung. |
| [`/GR`](gr-enable-run-time-type-information.md) | Aktiviert Laufzeit-Typeninformation (RTTI). |
| [`/Gr`](gd-gr-gv-gz-calling-convention.md) | Verwendet die- **`__fastcall`** Aufruf Konvention (nur x86). |
| [`/GS`](gs-buffer-security-check.md) | Führt eine Puffer-Sicherheitsüberprüfung durch. |
| [`/Gs`](gs-control-stack-checking-calls.md) | Steuert Stapelüberprüfungen |
| [`/GT`](gt-support-fiber-safe-thread-local-storage.md) | Unterstützt die Fiber-Sicherheit für Daten, die mit statischem lokalen Thread-Speicher zugewiesen werden. |
| [`/guard:cf`](guard-enable-control-flow-guard.md) | Fügt Sicherheitsüberprüfungen zum Ablaufsteuerungsschutz hinzu. |
| [`/guard:ehcont`](guard-enable-eh-continuation-metadata.md) | Aktiviert die eh-Fortsetzungs Metadaten. |
| [`/Gv`](gd-gr-gv-gz-calling-convention.md) | Verwendet die- **`__vectorcall`** Aufruf Konvention. (nur x86 und x64) |
| [`/Gw`](gw-optimize-global-data.md) | Ermöglicht programmübergreifende globale Datenoptimierung. |
| [`/GX`](gx-enable-exception-handling.md) | Veraltet. Aktiviert synchrone Ausnahmebehandlung. Verwenden Sie [`/EH`](eh-exception-handling-model.md) stattdessen. |
| [`/Gy`](gy-enable-function-level-linking.md) | Aktiviert Funktionslevel-Linking. |
| [`/GZ`](gz-enable-stack-frame-run-time-error-checking.md) | Veraltet. Identisch mit [`/RTC1`](rtc-run-time-error-checks.md) . |
| [`/Gz`](gd-gr-gv-gz-calling-convention.md) | Verwendet die- **`__stdcall`** Aufruf Konvention (nur x86). |
| [`/H`](h-restrict-length-of-external-names.md) | Veraltet. Beschränkt die Länge externer (öffentlicher) Namen. |
| [`/HELP`](help-compiler-command-line-help.md) | Listet die Compileroptionen auf. |
| [`/homeparams`](homeparams-copy-register-parameters-to-stack.md) | Erzwingt, dass in Registern übergebene Parameter beim Funktionseinstieg in ihre Speicherorte auf dem Stapel geschrieben werden. Diese Compileroption gilt nur für die x64-Compiler (systemeigene und Cross-Kompilierung). |
| [`/hotpatch`](hotpatch-create-hotpatchable-image.md) | Erstellt ein Abbild, das heiß patchfähig ist. |
| [`/I`](i-additional-include-directories.md) | Sucht in einem Verzeichnis nach Includedateien. |
| [`/J`](j-default-char-type-is-unsigned.md) | Ändert den **`char`** Standardtyp. |
| [`/JMC`](jmc.md) | Unterstützt natives C++-nur eigenen Code Debugging. |
| [`/kernel`](kernel-create-kernel-mode-binary.md) | Der Compiler und der Linker erstellen eine Binärdatei, die im Kernel von Windows ausgeführt werden kann. |
| [`/LD`](md-mt-ld-use-run-time-library.md) | Erstellt eine Dynamic Link Library (DLL). |
| [`/LDd`](md-mt-ld-use-run-time-library.md) | Erstellt eine Debug-Dynamic Link Library. |
| [`/link`](link-pass-options-to-linker.md) | Übergibt die angegebene Option an LINK. |
| [`/LN`](ln-create-msil-module.md) | Generiert ein MSIL-Modul. |
| [`/MD`](md-mt-ld-use-run-time-library.md) | Erstellt mit MSVCRT.lib eine Multithread-DLL. |
| [`/MDd`](md-mt-ld-use-run-time-library.md) | Erstellt mit MSVCRTD.lib eine Multithread-DLL für den Debugger. |
| [`/MP`](mp-build-with-multiple-processes.md) | Kompiliert mehrere Quelldateien unter Verwendung mehrerer Prozesse. |
| [`/MT`](md-mt-ld-use-run-time-library.md) | Erstellt mit LIBCMT.lib eine ausführbare Multithread-Datei. |
| [`/MTd`](md-mt-ld-use-run-time-library.md) | Erstellt mit LIBCMTD.lib eine ausführbare Multithread-Datei für den Debugger. |
| [`/nologo`](nologo-suppress-startup-banner-c-cpp.md) | Unterdrückt die Anzeige von Startinformationen. |
| [`/O1`](o1-o2-minimize-size-maximize-speed.md) | Erstellt kompakten Code. |
| [`/O2`](o1-o2-minimize-size-maximize-speed.md) | Erstellt schnellen Code. |
| [`/Ob`](ob-inline-function-expansion.md) | Steuert Inline-Erweiterung. |
| [`/Od`](od-disable-debug.md) | Deaktiviert Optimierung. |
| [`/Og`](og-global-optimizations.md) | Veraltet. Verwendet globale Optimierung. |
| [`/Oi`](oi-generate-intrinsic-functions.md) | Erstellt systeminterne Funktionen. |
| [`/openmp`](openmp-enable-openmp-2-0-support.md) | Aktiviert die- [`#pragma omp`](../../preprocessor/omp.md) Direktive im Quellcode. |
| [`/Os`](os-ot-favor-small-code-favor-fast-code.md) | Bevorzugt kompakten Code. |
| [`/Ot`](os-ot-favor-small-code-favor-fast-code.md) | Bevorzugt schnellen Code. |
| [`/Ox`](ox-full-optimization.md) | Eine Teilmenge von/O2, die/GF oder/Gy. nicht enthält. |
| [`/Oy`](oy-frame-pointer-omission.md) | Unterdrückt Framezeiger (nur x86). |
| [`/P`](p-preprocess-to-a-file.md) | Schreibt Präprozessorausgaben in eine Datei. |
| [`/permissive-`](permissive-standards-conformance.md) | Legen Sie den Standard Konformitäts Modus fest. |
| [`/Qfast_transcendentals`](qfast-transcendentals-force-fast-transcendentals.md) | Generiert schnelle Transzendente. |
| [`/QIfist`](qifist-suppress-ftol.md) | Veraltet. Unterdrückt `_ftol` , wenn eine Konvertierung von einem Gleitkommatyp zu einem ganzzahligen Typ erforderlich ist (nur x86). |
| [`/Qimprecise_fwaits`](qimprecise-fwaits-remove-fwaits-inside-try-blocks.md) | Entfernt- `fwait` Befehle in- **`try`** Blöcken. |
| [`/QIntel-jcc-erratum`](qintel-jcc-erratum.md) | Verringert die Auswirkungen der Intel JCC Erratum-mikrocodeaktualisierung auf die Leistung. |
| [/QPAR (Auto-parallelizer)](qpar-auto-parallelizer.md) | Ermöglicht automatische Parallelisierung von Schleifen, die mit der [#pragma loop()](../../preprocessor/loop.md) -Direktive gekennzeichnet sind. |
| [`/Qsafe_fp_loads`](qsafe-fp-loads.md) | Verwendet ganzzahlige Verschiebungsanweisungen für Gleitkommawerte und deaktiviert bestimmte Gleitkomma-Ladeoptimierungen. |
| [`/Qspectre`](qspectre.md) | Gibt die Compilergenerierung von Anweisungen an, um bestimmte mit Spectre-Variante 1 zusammenhängende Sicherheitsrisiken abzumildern. |
| [`/Qspectre-load`](qspectre-load.md) | Gibt die Compilergenerierung von serialisierungsanweisungen zum mindern von Spectre-Sicherheitsrisiken basierend auf Ladeanweisungen an. |
| [`/Qspectre-load-cf`](qspectre-load-cf.md) | Gibt die Compilergenerierung von serialisierungsanweisungen zum mindern von Spectre-Sicherheitsrisiken basierend auf Ablauf Steuerungs Anweisungen an, die Speicher laden. |
| [`/Qvec-report`(Bericht Ebene für die automatische Vektorisierung)](qvec-report-auto-vectorizer-reporting-level.md) | Aktiviert die Berichterstellungsebenen für die automatische Vektorisierung. |
| [`/RTC`](rtc-run-time-error-checks.md) | Aktiviert Laufzeitfehlerüberprüfung. |
| [`/sdl`](sdl-enable-additional-security-checks.md) | Aktiviert zusätzliche Sicherheitsfunktionen und Warnungen. |
| [`/showIncludes`](showincludes-list-include-files.md) | Zeigt während der Kompilierung eine Liste der Includedateien an. |
| [`/source-charset`](source-charset-set-source-character-set.md) | Quell Zeichensatz festlegen. |
| [`/sourceDependencies`](sourcedependencies.md) | Listen Header, Module und andere Quell Abhängigkeiten. |
| [`/std`](std-specify-language-standard-version.md) | C++ Standard Versions Kompatibilitäts Auswahl. |
| [`/Tc`](tc-tp-tc-tp-specify-source-file-type.md) | Gibt eine C-Quelldatei an. |
| [`/TC`](tc-tp-tc-tp-specify-source-file-type.md) | Gibt an, dass alle Quelldateien C sind. |
| [`/Tp`](tc-tp-tc-tp-specify-source-file-type.md) | Gibt eine C++-Quelldatei an. |
| [`/TP`](tc-tp-tc-tp-specify-source-file-type.md) | Gibt an, dass alle Quelldateien C++ sind. |
| [`/U`](u-u-undefine-symbols.md) | Entfernt ein vorkompiliertes Makro. |
| [`/u`](u-u-undefine-symbols.md) | Entfernt alle vorkompilierten Makros. |
| [`/utf-8`](utf-8-set-source-and-executable-character-sets-to-utf-8.md) | Legen Sie die Quell-und Ausführungs Zeichensätze auf UTF-8 fest. |
| [`/V`](v-version-number.md) | Veraltet. Legt die Versionszeichenfolge der OBJ-Datei fest. |
| [`/validate-charset`](validate-charset-validate-for-compatible-characters.md) | Überprüfen Sie die UTF-8-Dateien nur für kompatible Zeichen. |
| [`/vd`](vd-disable-construction-displacements.md) | Unterdrückt oder aktiviert ausgeblendete vtordisp-Klassenmember. |
| [`/vmb`](vmb-vmg-representation-method.md) | Verwendet bestmögliche Basis für Zeiger auf Member. |
| [`/vmg`](vmb-vmg-representation-method.md) | Verwendet volle Allgemeingültigkeit für Zeiger auf Member. |
| [`/vmm`](vmm-vms-vmv-general-purpose-representation.md) | Deklariert mehrfache Vererbung. |
| [`/vms`](vmm-vms-vmv-general-purpose-representation.md) | Deklariert einfache Vererbung. |
| [`/vmv`](vmm-vms-vmv-general-purpose-representation.md) | Deklariert virtuelle Vererbung. |
| [`/volatile`](volatile-volatile-keyword-interpretation.md) | Wählt aus, wie das volatile-Schlüsselwort interpretiert wird. |
| [`/w`](compiler-option-warning-level.md) | Deaktiviert alle Warnungen. |
| [`/W0`, `/W1`, `/W2`, `/W3`, `/W4`](compiler-option-warning-level.md) | Legt die auszugebende Warnstufe fest. |
| [`/w1`, `/w2`, `/w3`, `/w4`](compiler-option-warning-level.md) | Legt die Warnstufe für die angegebene Warnung fest. |
| [`/Wall`](compiler-option-warning-level.md) | Aktiviert alle Warnungen, einschließlich standardmäßig deaktivierter Warnmeldungen. |
| [`/wd`](compiler-option-warning-level.md) | Deaktiviert die angegebene Warnung. |
| [`/we`](compiler-option-warning-level.md) | Behandelt die angegebene Warnung als einen Fehler. |
| [`/WL`](wl-enable-one-line-diagnostics.md) | Aktiviert einzeilige Diagnose für Fehler- und Warnmeldungen beim Kompilieren von C++-Quellcode aus der Befehlszeile. |
| [`/wo`](compiler-option-warning-level.md) | Zeigt die angegebene Warnung nur einmal an. |
| [`/Wp64`](wp64-detect-64-bit-portability-issues.md) | Veraltet. Erkennt 64-Bit-Portabilitätsprobleme. |
| [`/Wv`](compiler-option-warning-level.md) | Zeigt keine Warnungen an, die nach der angegebenen Version des Compilers eingeführt wurden. |
| [`/WX`](compiler-option-warning-level.md) | Behandelt alle Warnungen als Fehler. |
| [`/X`](x-ignore-standard-include-paths.md) | Ignoriert das standardmäßige Includeverzeichnis. |
| [`/Y-`](y-ignore-precompiled-header-options.md) | Ignoriert alle anderen Optionen für vorkompilierte Header im aktuellen Erstellungsprozess. |
| [`/Yc`](yc-create-precompiled-header-file.md) | Erstellt eine vorkompilierte Headerdatei. |
| [`/Yd`](yd-place-debug-information-in-object-file.md) | Veraltet. Legt vollständige Debuginformationen in allen Objektdateien ab. Verwenden Sie [`/Zi`](z7-zi-zi-debug-information-format.md) stattdessen. |
| [`/Yl`](yl-inject-pch-reference-for-debug-library.md) | Fügt beim Erstellen einer Debugbibliothek einen PCH-Verweis ein |
| [`/Yu`](yu-use-precompiled-header-file.md) | Verwendet eine vorkompilierte Headerdatei beim Erstellungsvorgang. |
| [`/Z7`](z7-zi-zi-debug-information-format.md) | Generiert C 7,0-kompatible Debuginformationen. |
| [`/Za`](za-ze-disable-language-extensions.md) | Deaktiviert Spracherweiterungen. |
| [`/Zc`](zc-conformance.md) | Gibt Standardverhalten an. |
| [`/Ze`](za-ze-disable-language-extensions.md) | Veraltet. Aktiviert Spracherweiterungen. |
| [`/Zf`](zf.md) | Verbessert die PDB-Generierungs Zeit in parallelen Builds. |
| [`/Zg`](zg-generate-function-prototypes.md) | In Visual Studio 2015 entfernt. Erzeugt Funktionsprototypen. |
| [`/ZH`](zh.md) | Gibt MD5, SHA-1 oder SHA-256 für Prüfsummen in Debuginformationen an. |
| [`/ZI`](z7-zi-zi-debug-information-format.md) | Fügt Debuginformationen in eine Programmdatenbank ein, die mit Bearbeiten und Fortfahren kompatibel ist. |
| [`/Zi`](z7-zi-zi-debug-information-format.md) | Erzeugt vollständige Debuginformationen. |
| [`/Zl`](zl-omit-default-library-name.md) | Entfernt Standard-Bibliotheksnamen aus der OBJ-Datei (nur x86). |
| [`/Zm`](zm-specify-precompiled-header-memory-allocation-limit.md) | Legt die maximale Speicherbelegung für den vorkompilierten Header fest. |
| [`/Zo`](zo-enhance-optimized-debugging.md) | Generiert erweiterte Debuginformationen für optimierten Code. |
| [`/Zp`](zp-struct-member-alignment.md) | Komprimiert Strukturmember. |
| [`/Zs`](zs-syntax-check-only.md) | Prüft nur die Syntax. |
| [`/ZW`](zw-windows-runtime-compilation.md) | Erzeugt eine Ausgabedatei, die auf dem Windows-Runtime ausgeführt wird. |

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)\
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)

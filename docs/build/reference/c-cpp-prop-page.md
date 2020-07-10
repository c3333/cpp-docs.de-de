---
title: C/C++-Projekteigenschaften (Visual Studio)
description: Referenzhandbuch zu den Eigenschaften Seiteneigenschaften von Visual Studio Microsoft C/C++-Projekt.
ms.date: 07/08/2020
ms.topic: article
ms.assetid: 16375038-4917-4bd0-9a2a-26343c1708b7
ms.openlocfilehash: 3366f6677bf976b6211dd27a8abb114765fb2abc
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180889"
---
# <a name="cc-property-pages"></a>C/C++-Eigenschaften Seiten

Die folgenden Eigenschaften Seiten finden Sie unter **Projekt**  >  **Eigenschaften**  >  **Konfigurations Eigenschaften**  >  **C/C++**:

## <a name="cc-general-properties"></a>Allgemeine C/C++-Eigenschaften

### <a name="additional-include-directories"></a>Zusätzliche Includeverzeichnisse

Gibt mindestens ein Verzeichnis an, das dem include-Pfad hinzugefügt werden soll. Verwenden Sie Semikolons als Trennzeichen, wenn mehrere Verzeichnisse vorhanden sind. Sets [ `/I` (Zusätzliche Includeverzeichnisse)](i-additional-include-directories.md).

### <a name="additional-using-directories"></a>Zusätzliche #using Verzeichnisse

Gibt ein oder mehrere Verzeichnisse an (getrennte Verzeichnisnamen mit einem Semikolon), die durchsucht werden sollen, um Namen aufzulösen, die an eine #using Direktive weitergegeben Legt fest [`/AI`](ai-specify-metadata-directories.md) .

### <a name="debug-information-format"></a>Debuginformationsformat

Gibt den Typ der Debuginformationen an, die vom Compiler generiert werden.  Diese Eigenschaft erfordert kompatible Linker-Einstellungen. Legt [ `/Z7` , `/Zi` , `/ZI` (Debuginformationsformat)](z7-zi-zi-debug-information-format.md).

#### <a name="choices"></a>Auswahl

- **Keine**: Generiert keine Debuginformationen, sodass die Kompilierung ggf. schneller erfolgt.
- **C7-kompatibel** : Wählen Sie den Typ der Debuginformationen aus, der für Ihr Programm erstellt wurde, und ob diese Informationen in Objektdateien (obj) oder in einer Programmdatenbank (PDB) gespeichert werden.
- **Programmdatenbank** : erstellt eine Programmdatenbank (PDB), die Typinformationen und symbolische Debuginformationen für die Verwendung mit dem Debugger enthält. Zu den symbolischen Debuginformationen gehören die Namen und Typen von Variablen, Funktionen und Zeilennummern.
- **Programmdatenbank zum Bearbeiten und Fortfahren** : erstellt eine Programmdatenbank, wie oben beschrieben, in einem Format, das die Funktion " [Bearbeiten und Fortfahren](/visualstudio/debugger/edit-and-continue) " unterstützt.

### <a name="support-just-my-code-debugging"></a>Unterstützung nur eigenen Code Debugging

Fügt unterstützenden Code zum Aktivieren [nur eigenen Code](/visualstudio/debugger/just-my-code) Debuggens in dieser Kompilierungseinheit hinzu. Legt fest [`/JMC`](jmc.md) .

### <a name="common-language-runtime-support"></a>Common Language Runtime-Unterstützung

Verwenden Sie den .net-Lauf Zeit Dienst.  Dieser Switch ist mit anderen Switches nicht kompatibel. Ausführliche Informationen finden Sie in der Dokumentation zur Gruppe " [`/clr`](clr-common-language-runtime-compilation.md) Switches".

#### <a name="choices"></a>Auswahl

- **Keine Common Language Runtime-Unterstützung** -keine Common Language Runtime-Unterstützung
- **Common Language Runtime-Unterstützung** : erstellt Metadaten für Ihre Anwendung, die von anderen CLR-Anwendungen genutzt werden können. Ermöglicht es der Anwendung auch, Typen und Daten in den Metadaten anderer CLR-Komponenten zu verwenden.
- **Pure MSIL Common Language Runtime-Unterstützung** : erzeugt eine nur- [MSIL](/dotnet/standard/managed-code)-Ausgabedatei ohne nativen ausführbaren Code, obwohl Sie Native Typen enthalten kann, die in MSIL kompiliert werden.
- **Sichere MSIL Common Language Runtime-Unterstützung** : erzeugt einen reinen MSIL-Code (kein System eigener ausführbarer Code) und eine überprüfbare Ausgabedatei.

### <a name="consume-windows-runtime-extension"></a>Windows-Runtime Erweiterung verbrauchen

Verwendet die Windows-Lauf Zeit Sprachen-Erweiterungen. Legt fest [`/ZW`](zw-windows-runtime-compilation.md) .

### <a name="suppress-startup-banner"></a>Startbanner unterdrücken

Unterdrückt die Anzeige des Anmelde Banners, wenn der Compiler startet und während der Kompilierung Informationsmeldungen anzeigt.

### <a name="warning-level"></a>Warnstufe

Wählen Sie aus, wie streng der Compiler bei Codefehlern sein soll. Legt fest [`/W0` - `/W4`](compiler-option-warning-level.md) .

#### <a name="choices"></a>Auswahl

- **Alle Warnungen** deaktivieren: auf Ebene 0 werden alle Warnungen deaktiviert.
- **Level1** -Level 1 zeigt schwerwiegende Warnungen an. Ebene 1 ist die Standard Warnstufe in der Befehlszeile.
- **Level2** -Level 2 zeigt alle Warnungen der Stufe 1 an, die weniger schwerwiegend sind als Ebene 1.
- **Level3** -Level 3 zeigt alle Warnungen der Stufe 2 sowie alle anderen für Produktionszwecke empfohlenen Warnungen an.
- In **Level4** -Level 4 werden alle Warnungen der Stufe 3 sowie Informations Warnungen angezeigt, die in den meisten Fällen problemlos ignoriert werden können.
- **Enableallwarning** : aktiviert alle Warnungen, einschließlich derjenigen, die standardmäßig deaktiviert sind.

### <a name="treat-warnings-as-errors"></a>Warnungen als Fehler behandeln

Behandelt Compilerwarnungen als Fehler. Bei einem neuen Projekt ist es möglicherweise am besten, [`/WX`](wx-treat-linker-warnings-as-errors.md) bei jeder Kompilierung zu verwenden. Lösen Sie alle Warnungen auf, um schwer zu suchende Code Fehler zu minimieren.

### <a name="warning-version"></a>Warnungs Version

Blenden Sie Warnungen aus, die nach einer bestimmten Version des Compilers eingeführt wurden. Legt fest [`/Wv:xx`\[`.yy`\[`.zzzzz`\]\]](wx-treat-linker-warnings-as-errors.md) .

### <a name="diagnostics-format"></a>Diagnose Format

Ermöglicht die umfassende Diagnose mit Spalten Informationen und Quell Kontext in Diagnosemeldungen.

#### <a name="choices"></a>Auswahl

- **Caretzeichen** : stellt Spalten Informationen in der Diagnose Meldung bereit. Und gibt die relevante Zeile des Quellcodes mit einem Caretzeichen aus, das die problematische Spalte angibt.
- **Spalten Info** : gibt ggf. die Spaltennummer in der Zeile an, in der die Diagnose ausgegeben wird.
- **Klassisch** : gibt nur die vorherigen, präzisen Diagnosemeldungen mit der Zeilennummer aus.

### <a name="sdl-checks"></a>SDL-Prüfungen

Weitere empfohlene Überprüfungen für Security Development Lifecycle (SDL) umfasst das Aktivieren zusätzlicher Funktionen zur sicheren Codegenerierung und ermöglicht zusätzliche sicherheitsrelevante Warnungen als Fehler. Legt [ `/sdl` , `/sdl-` ](sdl-enable-additional-security-checks.md)fest.

### <a name="multi-processor-compilation"></a>Kompilierung mit mehreren Prozessoren

Kompilierung mit mehreren Prozessoren

## <a name="cc-optimization-properties"></a>C/C++-Optimierungs Eigenschaften

### <a name="optimization"></a>Optimization

Wählen Sie die Option für die Codeoptimierung aus. Wählen Sie Benutzer definiert, um bestimmte Optimierungs Optionen zu verwenden. Legt [/od](od-disable-debug.md), [/O1,/O2](o-options-optimize-code.md)fest.

#### <a name="choices"></a>Auswahl

- **Benutzerdefiniert**: Benutzerdefinierte Optimierung
- **Deaktiviert**: Deaktivieren der Optimierung.
- **Maximale Optimierung (Größe bevorzugen)** : äquivalent zu**`/Os /Oy /Ob2 /Gs /GF /Gy`**
- **Maximale Optimierung (Geschwindigkeit bevorzugen)** : äquivalent zu**`/Oi /Ot /Oy /Ob2 /Gs /GF /Gy`**
- **Optimierungen (Geschwindigkeit bevorzugen)** : äquivalent zu**`/Oi /Ot /Oy /Ob2`**

### <a name="inline-function-expansion"></a>Inline Funktionserweiterung

Wählen Sie die Ebene der [Inline Funktions](../../cpp/inline-functions-cpp.md) Erweiterung für den Build aus. Legt fest [`/Ob`](ob-inline-function-expansion.md) .

#### <a name="choices"></a>Auswahl

- **Standard**
- **Deaktiviert** : deaktiviert die Inline Erweiterung, die standardmäßig aktiviert ist.
- **Nur __inline** : erweitert nur Funktionen, die als **`inline`** , oder markiert sind `__forceinline` `__inline` . Oder in einer C++ Member-Funktion, die innerhalb einer Klassen Deklaration definiert ist.
- **Alle geeigneten** -erweitert Funktionen **`inline`** , die als oder gekennzeichnet sind `__inline` , und jede andere Funktion, die der Compiler auswählt. (Die Erweiterung erfolgt nach dem Ermessen des Compilers, häufig als *Automatisches inlining*bezeichnet.)

### <a name="enable-intrinsic-functions"></a>Intrinsische Funktionen aktivieren

Aktiviert intrinsische Funktionen.  Die Verwendung von intrinsischen Funktionen erzeugt schnelleren, aber möglicherweise größeren Code. Legt fest [`/Oi`](oi-generate-intrinsic-functions.md) .

### <a name="favor-size-or-speed"></a>Größe oder Geschwindigkeit bevorzugen

Gibt an, ob Codegröße oder Code Geschwindigkeit bevorzugt werden soll. "Globale Optimierung" muss aktiviert sein. Legt [ `/Ot` , `/Os` ](os-ot-favor-small-code-favor-fast-code.md)fest.

#### <a name="choices"></a>Auswahl

- Bevorzugen Sie kleinen Code zugunsten von **geringem Code** . Minimiert die Größe von exe-und DLLs, indem der Compiler angewiesen wird, die Größe gegenüber der Geschwindigkeit zu bevorzugen.
- **Schnellen Code** bevorzugen, schnellen Code bevorzugen. Maximiert die Geschwindigkeit von EXEs und DLLs, indem der Compiler angewiesen wird, die Geschwindigkeit der Größe zu bevorzugen. (Dieser Wert ist die Standardeinstellung.)
- **Weder** keine Größen-und Geschwindigkeits Optimierung.

### <a name="omit-frame-pointers"></a>Frame Zeiger weglassen

Unterdrückt die Erstellung von Framezeigern im Anrufstapel.

### <a name="enable-fiber-safe-optimizations"></a>Fiber-sichere Optimierungen aktivieren

Aktiviert die Speicherplatz Optimierung bei Verwendung von Fibers und Thread lokalem Speicherzugriff. Legt fest [`/GT`](gt-support-fiber-safe-thread-local-storage.md) .

### <a name="whole-program-optimization"></a>Optimierung des gesamten Programms

Ermöglicht Modul übergreifende Optimierungen durch verzögern der Codegenerierung bis zur Verknüpfungs Zeit. Erfordert die Linkeroption "Link-Zeit Code Generierung". Legt fest [`/GL`](gl-whole-program-optimization.md) .

## <a name="cc-preprocessor-properties"></a>C/C++-präprozessoreigenschaften

### <a name="preprocessor-definitions"></a>Präprozessordefinitionen

Definiert Vorverarbeitungssymbole für Ihre Quelldatei.

### <a name="undefine-preprocessor-definitions"></a>Präprozessordefinitionen aufheben

Gibt mindestens eine aufgehobene Präprozessordefinition an. Legt fest [`/U`](u-u-undefine-symbols.md) .

### <a name="undefine-all-preprocessor-definitions"></a>Alle Präprozessordefinitionen aufheben

Hebt die Definition aller zuvor definierten Präprozessorwerte auf. Legt fest [`/u`](u-u-undefine-symbols.md) .

### <a name="ignore-standard-include-paths"></a>Standardincludepfade ignorieren

Verhindert, dass der Compiler in Verzeichnissen, die in den INCLUDE-Umgebungsvariablen angegeben sind, nach Includedateien sucht.

### <a name="preprocess-to-a-file"></a>In einer Datei Vorverarbeiten

Vorverarbeitet C-und C++-Quelldateien und schreibt die vorverarbeitete Ausgabe in eine Datei. Mit dieser Option wird die Kompilierung unterdrückt, und es wird keine *`.obj`* Datei erzeugt.

### <a name="preprocess-suppress-line-numbers"></a>Vorverarbeitung unterdrücken von Zeilennummern

Preprocess ohne #line Direktiven.

### <a name="keep-comments"></a>Kommentare beibehalten

Unterdrückt die kommentarleiste aus dem Quellcode. erfordert, dass eine der Vorverarbeitungs Optionen festgelegt wird. Legt fest [`/C`](c-preserve-comments-during-preprocessing.md) .

## <a name="cc-code-generation-properties"></a>Eigenschaften der C/C++-Code Generierung

### <a name="enable-string-pooling"></a>Zeichen folgen Pooling aktivieren

Der Compiler erstellt nur eine schreibgeschützte Kopie identischer Zeichen folgen im Programm Image. Dies führt zu kleineren Programmen, einer Optimierung, die als *Zeichen folgen Pooling*bezeichnet wird. die Option [ `/O1` `/O2` , ](o-options-optimize-code.md)und wird [`/ZI`](z7-zi-zi-debug-information-format.md) automatisch festgelegt [`/GF`](gf-eliminate-duplicate-strings.md) .

### <a name="enable-minimal-rebuild"></a>Minimale Neuerstellung aktivieren

Aktiviert die minimale Neuerstellung, die bestimmt, ob C++-Quelldateien, die geänderte C++-Klassendefinitionen enthalten, in Header Dateien gespeichert werden sollen *`.h`* .

### <a name="enable-c-exceptions"></a>C++-Ausnahmen aktivieren

Gibt das Ausnahmebehandlungsmodell an, das vom Compiler verwendet wird.

#### <a name="choices"></a>Auswahl

- **Ja bei SEH-Ausnahmen** : das Ausnahme Behandlungsmodell, das asynchrone (strukturierte) und synchrone (C++) Ausnahmen abfängt. Legt fest [`/EHa`](eh-exception-handling-model.md) .
- **Ja** , das Ausnahme Behandlungsmodell, das nur C++-Ausnahmen abfängt und den Compiler anweist, dass externe C-Funktionen nie eine C++-Ausnahme auslösen. Legt fest [`/EHsc`](eh-exception-handling-model.md) .
- **Ja bei extern c-Funktionen** : das Ausnahme Behandlungsmodell, das nur C++-Ausnahmen abfängt und den Compiler anweist, zu übernehmen, dass externe c-Funktionen eine Ausnahme auslösen. Legt fest [`/EHs`](eh-exception-handling-model.md) .
- **No** -keine Ausnahmebehandlung.

### <a name="smaller-type-check"></a>Kleinere Typüberprüfung

Aktivieren Sie die Überprüfung der Konvertierung in kleinere Typen, nicht kompatibel mit einem anderen Optimierungstyp als "Debug". Legt fest [`/RTCc`](rtc-run-time-error-checks.md) .

### <a name="basic-runtime-checks"></a>Grundlegende Lauf Zeit Prüfungen

Grundlegende Lauf Zeit Fehlerüberprüfungen aktivieren, nicht kompatibel mit allen anderen Optimierungen als Debuggen. Legt [ `/RTCs` , `/RTCu` , `/RTC1` ](rtc-run-time-error-checks.md)fest.

#### <a name="choices"></a>Auswahl

- **Stapel Rahmen** : aktiviert die Lauf Zeit Fehlerüberprüfung für Stapel Rahmen.
- **Nicht initialisierte Variablen** : meldet, wenn eine Variable verwendet wird, ohne initialisiert worden zu sein.
- **Both (/RTC1, equiv. to/RTCsu)** -Äquivalent von/RTCsu.
- **Standard** -standardmäßige Laufzeitüberprüfungen.

### <a name="runtime-library"></a>Laufzeitbibliothek

Dient zum Angeben der zu verknüpfenden Laufzeitbibliothek. Legt [ `/MT` , `/MTd` , `/MD` , `/MDd` ](md-mt-ld-use-run-time-library.md)fest.

#### <a name="choices"></a>Auswahl

- **Multithread** : bewirkt, dass die Anwendung die statische Multithread-Version der Lauf Zeit Bibliothek verwendet.
- **Multithread-Debug** : Definiert _DEBUG und _MT. Diese Option bewirkt auch, dass der Compiler den Bibliotheksnamen " *LIBCMTD. lib* " in der *`.obj`* Datei platziert, sodass der Linker " *LIBCMTD. lib* " zum Auflösen externer Symbole verwendet.
- **Multithread-DLL** : bewirkt, dass Ihre Anwendung die Multithread-und dll-spezifische Version der Lauf Zeit Bibliothek verwendet. Definiert _MT und _DLL und bewirkt, dass der Compiler den Bibliotheksnamen " *msvcrt. lib* " in der *`.obj`* Datei platziert.
- **Multithreaded-Debug-DLL** : Definiert _DEBUG, _MT und _DLL und bewirkt, dass Ihre Anwendung die Multithread-und dll-spezifische Version der Lauf Zeit Bibliothek verwendet. Außerdem bewirkt dies, dass der Compiler den Bibliotheksnamen " *msvcrtd. lib* " in der *`.obj`* Datei platziert.

### <a name="struct-member-alignment"></a>Ausrichtung von Strukturmembern

Gibt 1-, 2-, 4-oder 8-Byte-Begrenzungen für die Ausrichtung der Strukturmember an. Legt fest [`/Zp`](zp-struct-member-alignment.md) .

#### <a name="choices"></a>Auswahl

- **1 Byte** packt Strukturen an 1-Byte-Begrenzungen. Identisch mit **`/Zp`** .
- **2** Byte packt Strukturen an 2-Byte-Begrenzungen.
- **4 Byte** -Pack-Strukturen an 4-Byte-Begrenzungen.
- **8 Byte** -Pack-Strukturen an 8-Byte-Begrenzungen (Standard).
- **16 Byte** -Pack-Strukturen an 16-Byte-Begrenzungen.
- **Standard** -Standard-Ausrichtungs Einstellungen.

### <a name="security-check"></a>Sicherheitsüberprüfung

Die Sicherheitsprüfung hilft bei der Erkennung von Überläufen des Stapelpuffers. Hierbei handelt es sich um gängige Versuche, die Sicherheit eines Programms zu gefährden.

#### <a name="choices"></a>Auswahl

- **Sicherheitsüberprüfung deaktivieren**: Sicherheitsüberprüfung deaktivieren. Legt fest [`/GS-`](gs-buffer-security-check.md) .
- **Sicherheitsüberprüfung aktivieren**: Sicherheitsüberprüfung aktivieren. Legt fest [`/GS`](gs-buffer-security-check.md) .

### <a name="control-flow-guard"></a>Ablaufsteuerungsschutz

Guard-Sicherheitsüberprüfung hilft bei der Erkennung von versuchen, eine Verteilung an einen ungültigen Codeblock durch

#### <a name="choices"></a>Auswahl

- **Ja** , Sicherheitsüberprüfung mit Schutzgruppen aktivieren [`/guard:cf`](guard-enable-control-flow-guard.md) .
- **Nein**

### <a name="enable-function-level-linking"></a>Funktionslevel-Linking aktivieren

Ermöglicht dem Compiler, einzelne Funktionen in Form von kompilierten Funktionen (COMDATs) zu kompilieren. Zur Bearbeitung erforderlich, funktionieren weiterhin. Legt [/Gy](gy-enable-function-level-linking.md)fest.

### <a name="enable-parallel-code-generation"></a>Parallele Code Generierung aktivieren

Ermöglicht dem Compiler, parallelen Code für Schleifen zu generieren, die mithilfe von identifiziert werden, `#pragma loop(hint_parallel[(n)])` Wenn die Optimierung aktiviert ist.

### <a name="enable-enhanced-instruction-set"></a>Erweiterten Anweisungs Satz aktivieren

Ermöglicht die Verwendung von Anweisungen, die auf Prozessoren mit erweiterten Anweisungs Sätzen gefunden werden. Zum Beispiel die Erweiterungen SSE, SSE2, AVX und AVX2 für IA-32. Und, die AVX-und AVX2-Erweiterungen für x64. Derzeit **`/arch:SSE`** **`/arch:SSE2`** sind und nur verfügbar, wenn Sie für die x86-Architektur entwickeln. Wenn keine Option angegeben ist, verwendet der Compiler Anweisungen, die auf Prozessoren gefunden werden, die SSE2 unterstützen. Die Verwendung erweiterter Anweisungen kann mit deaktiviert werden **`/arch:IA32`** . Weitere Informationen finden Sie unter [`/arch (x86)`](arch-x86.md) [`/arch (x64)`](arch-x64.md) und [`/arch (ARM)`](arch-arm.md) .

#### <a name="choices"></a>Auswahl

- **Streaming SIMD Extensions** Streaming SIMD Extensions. Sationen**`/arch:SSE`**
- **Streaming SIMD Extensions 2** -Streaming SIMD Extensions 2. Sationen**`/arch:SSE2`**
- **Erweiterte Vektor Erweiterungen** -Erweiterte Vektor Erweiterungen. Sationen**`/arch:AVX`**
- **Erweiterte Vektor Erweiterungen 2** -Erweiterte Vektor Erweiterungen 2. Sationen**`/arch:AVX2`**
- **Keine erweiterten Anweisungen** -keine erweiterten Anweisungen. Sationen**`/arch:IA32`**
- **Nicht festgelegt** -nicht festgelegt.

### <a name="floating-point-model"></a>Gleit Komma Modell

Legt das Gleitkommamodell fest. Legt [ `/fp:precise` , `/fp:strict` , `/fp:fast` ](fp-specify-floating-point-behavior.md)fest.

#### <a name="choices"></a>Auswahl

- **Genau** : Standardwert. Verbessert die Konsistenz von Gleit Komma Tests auf Gleichheit und Ungleichheit.
- **Strict** -das strengste Gleit Komma Modell. **`/fp:strict`** bewirkt **`fp_contract`** , dass deaktiviert ist und **`fenv_access`** auf on gesetzt ist. **`/fp:except`** ist impliziert und kann durch explizites angeben von deaktiviert werden **`/fp:except-`** . Bei Verwendung mit **`/fp:except-`** **`/fp:strict`** erzwingt eine strikte Gleit Komma Semantik, aber ohne Berücksichtigung von Ausnahme Ereignissen.
- **Schneller** : erstellt den schnellsten Code in den meisten Fällen.

### <a name="enable-floating-point-exceptions"></a>Gleit Komma Ausnahmen aktivieren

Verlässliches Modell für Gleitkommaausnahmen. Ausnahmen werden sofort ausgelöst, nachdem Sie ausgelöst wurden. Legt [/fp: außer](fp-specify-floating-point-behavior.md)fest.

### <a name="create-hotpatchable-image"></a>Hotpatchfähiges Image erstellen

Wenn Hotpatching vor auf ON fest steht, stellt der Compiler sicher, dass die erste Anweisung jeder Funktion zwei Bytes beträgt, wie für das Hotpatching vor erforderlich. Legt [/hotpatch](hotpatch-create-hotpatchable-image.md)fest.

### <a name="spectre-mitigation"></a>Spectre-Entschärfung

Spectre-entschärfungen für CVE 2017-5753. Legt fest [`/Qspectre`](qspectre.md) .

#### <a name="choices"></a>Auswahl

- **Aktiviert** : enable Spectre Entschärfungs Feature für CVE 2017-5753
- **Deaktiviert** -nicht festgelegt.

## <a name="cc-language-properties"></a>C/C++-Spracheigenschaften

### <a name="disable-language-extensions"></a>Spracherweiterungen deaktivieren

Unterdrückt oder aktiviert Spracherweiterungen. Legt fest [`/Za`](za-ze-disable-language-extensions.md) .

### <a name="conformance-mode"></a>Konformitäts Modus

Aktiviert oder unterdrückt den Konformitäts Modus. Legt fest [`/permissive-`](permissive-standards-conformance.md) .

### <a name="treat-wchar_t-as-built-in-type"></a>Wchar_t als integrierten Typ behandeln

Wenn angegeben, wird der Typ zu einem systemeigenen Typ, der auf **`wchar_t`** `__wchar_t` die gleiche Weise wie **`short`** zugeordnet wird `__int16` . [`/Zc:wchar_t`](zc-wchar-t-wchar-t-is-native-type.md)ist standardmäßig aktiviert.

### <a name="force-conformance-in-for-loop-scope"></a>Konformität in for-Schleifen Bereich erzwingen

Wird zum Implementieren des standardmäßigen C++-Verhaltens für die for-Anweisung-Schleifen mit Microsoft-Erweiterungen verwendet. Legt fest [ `/Za` `/Ze` (Spracherweiterungen deaktivieren](za-ze-disable-language-extensions.md)). [`/Zc:forScope`](zc-forscope-force-conformance-in-for-loop-scope.md)ist standardmäßig aktiviert.

### <a name="remove-unreferenced-code-and-data"></a>Entfernen von nicht referenzierten Code und Daten

Wenn angegeben, generiert der Compiler keine Symbol Informationen für nicht referenzierten Code und Daten mehr.

### <a name="enforce-type-conversion-rules"></a>Typkonvertierungsregeln erzwingen

Wird verwendet, um einen Rvalue-Verweistyp als Ergebnis eines Umwandlungs Vorgangs pro c++ 11-Standard zu identifizieren.

### <a name="enable-run-time-type-information"></a>Laufzeit-Typeninformation aktivieren

Fügt Code für die Überprüfung der C++-Objekttypen während der Laufzeit hinzu (Laufzeit-Typinformationen). Legt [ `/GR` , `/GR-` ](gr-enable-run-time-type-information.md)fest.

### <a name="open-mp-support"></a>Open MP-Unterstützung

Aktiviert OpenMP 2,0-Spracherweiterungen. Legt fest [`/openmp`](openmp-enable-openmp-2-0-support.md) .

### <a name="c-language-standard"></a>C++-Sprachstandard

Bestimmt den C++-Sprachstandard, den der Compiler ermöglicht. Verwenden Sie nach Möglichkeit die neueste Version. Legt [ `/std:c++14` , `/std:c++17` , `/std:c++latest` ](std-specify-language-standard-version.md)fest.

#### <a name="choices"></a>Auswahl

- **Standard**
- **ISO c++ 14 Standard**
- **ISO c++ 17 Standard**
- **Vorschau: Features aus dem neuesten C++ Working Draft**

### <a name="enable-c-modules-experimental"></a>C++-Module aktivieren (experimentell)

Experimentelle Unterstützung für die Module "C++ modules TS" und "Standard Bibliothek".

## <a name="cc-precompiled-headers-properties"></a>Eigenschaften von C/C++-vorkompilierten Headern

### <a name="createuse-precompiled-header"></a>Vorkompilierten Header erstellen/verwenden

Ermöglicht die Erstellung oder Verwendung eines vorkompilierten Headers während der Erstellung. Legt [`/Yc`](yc-create-precompiled-header-file.md) , fest [`/Yu`](yu-use-precompiled-header-file.md) .

#### <a name="choices"></a>Auswahl

- **Create** -weist den Compiler an, eine vorkompilierte Header Datei (. pch) zu erstellen, die den Zustand der Kompilierung zu einem bestimmten Zeitpunkt darstellt.
- **Use** : weist den Compiler an, eine vorhandene vorkompilierte Header Datei (. pch) in der aktuellen Kompilierung zu verwenden.
- **Vorkompilierte Header** werden nicht verwendet. es werden keine vorkompilierten Header verwendet.

### <a name="precompiled-header-file"></a>Vorkompilierte Headerdatei

Gibt den Header Dateinamen an, der beim Erstellen oder Verwenden einer vorkompilierten Header Datei verwendet werden soll. Legt [`/Yc`](yc-create-precompiled-header-file.md) , fest [`/Yu`](yu-use-precompiled-header-file.md) .

### <a name="precompiled-header-output-file"></a>Vorkompilierte Header Ausgabedatei

Gibt den Pfad oder den Namen der generierten vorkompilierten Header Datei an. Legt fest [`/Fp`](fp-name-dot-pch-file.md) .

## <a name="cc-output-files-properties"></a>Eigenschaften von C/C++-Ausgabedateien

### <a name="expand-attributed-source"></a>Attributierte Quelle erweitern

Erstellen Sie eine Listen Datei mit erweiterten Attributen in die Quelldatei. Legt fest [`/Fx`](fx-merge-injected-code.md) .

### <a name="assembler-output"></a>Assemblyausgabe

Gibt die Inhalte der Ausgabedatei für die Assemblysprache an. Legt [ `/FA` , `/FAc` , `/FAs` , `/FAcs` ](fa-fa-listing-file.md)fest.

#### <a name="choices"></a>Auswahl

- **Keine Auflistung** -keine Auflistung.
- Assemblyausschließliches **auflisten** : Assemblycode;*`.asm`*
- **Assembly mit Computercode** , Computer-und Assemblycode;*`.cod`*
- **Assembly mit Quellcode** -Quell Code und Assemblycode;*`.asm`*
- **Assembly, Computercode und Quellassembly** , Computercode und Quellcode;*`.cod`*

### <a name="use-unicode-for-assembler-listing"></a>Unicode für assemblyauflistung verwenden

Bewirkt, dass die Ausgabedatei im UTF-8-Format erstellt wird.

### <a name="asm-list-location"></a>ASM-Listen Speicherort

Gibt den relativen Pfad oder Namen für die ASM-Listen Datei an. kann ein Datei-oder Verzeichnisname sein. Legt fest [`/Fa`](fa-fa-listing-file.md) .

### <a name="object-file-name"></a>Name der Objektdatei

Gibt einen Namen an, um den Standardnamen der Objektdatei zu überschreiben. Dies kann ein Datei- oder Verzeichnisname sein. Legt fest [`/Fo`](fo-object-file-name.md) .

### <a name="program-database-file-name"></a>Programmdatenbank-Dateiname

Gibt einen Namen für eine vom Compiler generierte PDB-Datei an. gibt auch den Basis Namen für die erforderliche vom Compiler generierte IDB-Datei an. kann ein Datei-oder Verzeichnisname sein. Legt fest [`/Fd`](fd-program-database-file-name.md) .

### <a name="generate-xml-documentation-files"></a>XML-Dokumentationsdateien generieren

Gibt an, dass der Compiler XML-Dokumentations Kommentar Dateien generieren soll (. XDC). Legt fest [`/doc`](doc-process-documentation-comments-c-cpp.md) .

### <a name="xml-documentation-file-name"></a>Name der XML-Dokumentations Datei

Gibt den Namen der generierten XML-Dokumentationsdateien an. kann ein Datei-oder Verzeichnisname sein. Legt fest [`/doc:`\<name>](doc-process-documentation-comments-c-cpp.md) .

## <a name="cc-browse-information-properties"></a>C/C++-Eigenschaften zum Durchsuchen von Informationen

### <a name="enable-browse-information"></a>Browseinformationen aktivieren

Gibt die Ebene der Browseinformationen in der *`.bsc`* Datei an. Legt fest [`/FR`](fr-fr-create-dot-sbr-file.md) .

### <a name="browse-information-file"></a>Informationsdatei durchsuchen

Gibt den optionalen Namen für die Browser Informationsdatei an. Legt fest [`/FR`\<name>](fr-fr-create-dot-sbr-file.md) .

## <a name="cc-advanced-properties"></a>Erweiterte C/C++-Eigenschaften

### <a name="calling-convention"></a>Aufrufkonvention

Wählen Sie die Standard Aufruf Konvention für Ihre Anwendung aus (kann von einer Funktion überschrieben werden). Legt [ `/Gd` , `/Gr` , `/Gz` , `/Gv` ](gd-gr-gv-gz-calling-convention.md)fest.

#### <a name="choices"></a>Auswahl

- **__cdecl** : gibt die `__cdecl` Aufruf Konvention für alle Funktionen außer C++-Element Funktionen und-Funktionen an, die als oder gekennzeichnet sind `__stdcall` `__fastcall` .
- **__fastcall** : gibt die `__fastcall` Aufruf Konvention für alle Funktionen außer C++-Element Funktionen und-Funktionen an, die als oder gekennzeichnet sind `__cdecl` `__stdcall` . Alle `__fastcall`-Funktionen müssen Prototypen haben.
- **__stdcall** : gibt die `__stdcall` Aufruf Konvention für alle Funktionen außer C++-Element Funktionen und-Funktionen an, die als oder gekennzeichnet sind `__cdecl` `__fastcall` . Alle `__stdcall`-Funktionen müssen Prototypen haben.
- **__vectorcall** : gibt die `__vectorcall` Aufruf Konvention für alle Funktionen mit Ausnahme der C++-Element Funktionen und-Funktionen an, die als `__cdecl` , oder markiert sind `__fastcall` `__stdcall` . Alle `__vectorcall`-Funktionen müssen Prototypen haben.

### <a name="compile-as"></a>Kompilieren als

Wählen Sie Kompilierungs Sprache für *`.c`* -und- *`.cpp`* Dateien aus. Legt [ `/TC` , `/TP` ](tc-tp-tc-tp-specify-source-file-type.md)fest.

#### <a name="choices"></a>Auswahl

- **Standard**: die Standardeinstellung.
- **Als C-Code kompilieren**: als C-Code kompilieren.
- **Kompilieren Sie AS C++ Code** -Compile als C++-Code.

### <a name="disable-specific-warnings"></a>Bestimmte Warnungen deaktivieren

Deaktiviert die angegebenen Warnungs Nummern. Fügen Sie die Warnungs Nummern in eine durch Semikolons getrennte Liste ein. Legt fest [`/wd`\<number>](compiler-option-warning-level.md) .

### <a name="forced-include-file"></a>Erzwungene Includedatei

eine oder mehrere explizite Includedateien. Legt fest [`/FI`\<name>](fi-name-forced-include-file.md) .

### <a name="forced-using-file"></a>Erzwungene #using Datei

Gibt eine oder mehrere erzwungene #using Dateien an. Legt fest [`/FU`\<name>](fu-name-forced-hash-using-file.md) .

### <a name="show-includes"></a>Includedateien anzeigen

Generiert eine Liste der Includedateien mit Compilerausgabe. Legt fest [`/showIncludes`](showincludes-list-include-files.md) .

### <a name="use-full-paths"></a>Vollständige Pfade verwenden

Verwenden Sie vollständige Pfade in Diagnosemeldungen. Legt fest [`/FC`](fc-full-path-of-source-code-file-in-diagnostics.md) .

### <a name="omit-default-library-name"></a>Standard Bibliotheksnamen weglassen

Enthält keine Standard Bibliotheksnamen in *`.obj`* Dateien. Legt fest [`/Zl`](zl-omit-default-library-name.md) .

### <a name="internal-compiler-error-reporting"></a>Bericht für interne Compilerfehler

> [!NOTE]
> Diese Option ist veraltet. Ab Windows Vista wird die Fehlerberichterstattung durch [Windows-Fehlerberichterstattung (wer)](/windows/win32/wer/windows-error-reporting) -Einstellungen gesteuert.

### <a name="treat-specific-warnings-as-errors"></a>Bestimmte Warnungen als Fehler behandeln

Behandelt die spezifische Compilerwarnung als Fehler, wobei n eine Compilerwarnung ist.

### <a name="additional-options"></a>Zusätzliche Optionen

Zusätzliche Optionen.

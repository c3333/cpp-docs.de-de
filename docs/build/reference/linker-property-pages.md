---
title: Linker-Eigenschaftenseiten
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
ms.openlocfilehash: 2f2068c6c51fc6bf4e4104213e946e243fc6df2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336584"
---
# <a name="linker-property-pages"></a>Linker-Eigenschaftenseiten

Die folgenden Eigenschaften finden Sie unter **Project** > **Properties** > **Configuration Properties** > **Linker**. Weitere Informationen zum Linker finden Sie unter [CL Ruft die Linker-](cl-invokes-the-linker.md) und [Linkeroptionen](linker-options.md)auf.

## <a name="general-property-page"></a>Eigenschaftenseite „Allgemein“

### <a name="output-file"></a>Ausgabedatei

Die Option [/OUT](out-output-file-name.md) überschreibt den Standardnamen und Speicherort des Programms, das der Linker erstellt.

### <a name="show-progress"></a>Status anzeigen

Druckt Linker-Fortschrittsmeldungen

**Entscheidungen**

- **Nicht gesetzt** - Keine Ausführlichkeit.
- **Alle Fortschrittsmeldungen anzeigen** – Zeigt alle Fortschrittsmeldungen an.
- **Für durchsuchte Bibliotheken** – Zeigt Fortschrittsmeldungen an, die nur die durchsuchten Bibliotheken anzeigen.
- **ComDAT-Faltung beim optimierten Verknüpfen** - Zeigt Informationen zum COMDAT-Falten während der optimierten Verknüpfung an.
- **Informationen zum Entfernen von Daten während der optimierten Verknüpfung** – Zeigt Informationen über Funktionen und Daten an, die während der optimierten Verknüpfung entfernt wurden.
- **Informationen zu Modulen,** die nicht mit SEH kompatibel sind - Zeigt Informationen zu Modulen an, die mit der sicheren Ausnahmebehandlung nicht kompatibel sind.
- **Informationen zu Linkeraktivitäten im Zusammenhang mit verwaltetem Code** – Anzeigen von Informationen zu Linkeraktivitäten im Zusammenhang mit verwaltetem Code.

### <a name="version"></a>Version

Die Option [/VERSION](version-version-information.md) weist den Linker an, eine Versionsnummer in den Header der .exe- oder .dll-Datei zu setzen. Verwenden Sie DUMPBIN /HEADERS, um das Bildversionsfeld der OPTIONAL HEADER VALUES anzuzeigen, um die Auswirkungen von **/VERSION**zu sehen.

### <a name="enable-incremental-linking"></a>Inkrementelle Verknüpfung aktivieren

Aktiviert die inkrementelle Verknüpfung. ([/INKREMENTELL](incremental-link-incrementally.md), /INKREMENTELL:NEIN)

### <a name="suppress-startup-banner"></a>Startbanner unterdrücken

Die Option [/NOLOGO](nologo-suppress-startup-banner-linker.md) verhindert die Anzeige der Copyright-Nachricht und der Versionsnummer.

### <a name="ignore-import-library"></a>Importbibliothek ignorieren

Durch diese Eigenschaft wird der Linker angewiesen, keine während des aktuellen Builds erstellte LIB-Ausgabe mit einem abhängigen Projekt zu verknüpfen. Es ermöglicht dem Projektsystem, DLL-Dateien zu verarbeiten, die keine .lib-Datei erzeugen, wenn sie erstellt wird. Wenn ein Projekt von einem anderen Projekt abhängt, das eine DLL generiert, verknüpft das Projektsystem automatisch die LIB-Datei, die von diesem untergeordneten Projekt erstellt wurde. Diese Eigenschaft ist in Projekten, die GG-DLLs oder reine Ressourcen-DLLs erzeugen, möglicherweise nicht erforderlich, da diese DLLs keine sinnvollen Exporte haben. Wenn eine DLL keine Exporte hat, generiert der Linker keine .lib-Datei. Wenn keine .lib-Exportdatei vorhanden ist und das Projektsystem den Linker anweist, eine Verknüpfung mit der fehlenden DLL herzustellen, schlägt die Verknüpfung fehl. Verwenden Sie die Eigenschaft **Importbibliothek ignorieren**, um dieses Problem zu beheben. Wenn auf **Ja**festgelegt, ignoriert das Projektsystem das Vorhandensein oder Fehlen der .lib-Datei und bewirkt, dass jedes Projekt, das von diesem Projekt abhängt, keine Verknüpfung mit der nicht vorhandenen .lib-Datei enthält.

Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>.

### <a name="register-output"></a>Ausgabe registrieren

Führt `regsvr32.exe /s $(TargetPath)` für die Buildausgabe aus, dies ist nur für DLL-Projekte gültig. Bei EXE-Projekten wird diese Eigenschaft ignoriert. Legen Sie zum Registrieren einer EXE-Ausgabe für die Konfiguration ein Postbuildereignis fest, um die benutzerdefinierte Registrierung auszuführen, die für registrierte EXE-Dateien stets erforderlich ist.

Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>.

### <a name="per-user-redirection"></a>Umleitung pro Benutzer

Die Registrierung in Visual Studio erfolgte herkömmlicherweise in HKEY_CLASSES_ROOT (HKCR). Unter Windows Vista und höheren Betriebssystemen müssen Sie Visual Studio im erweiterten Modus ausführen, um auf HKCR zugreifen zu können. Entwickler möchten nicht immer im erhöhten Modus ausgeführt werden, müssen aber dennoch mit der Registrierung arbeiten. Mit der Benutzerumleitung können Sie sich registrieren, ohne im erhöhten Modus ausgeführt werden zu müssen.

Die Umleitung pro Benutzer erzwingt eine Umleitung aller Schreibvorgänge für HKCR zu HKEY\_CURRENT\_USER (HKCU). Wenn die Umleitung pro Benutzer deaktiviert ist, kann der [Projektbuildfehler PRJ0050](../../error-messages/tool-errors/project-build-error-prj0050.md) auftreten, wenn das Programm versucht, in HKCR zu schreiben.

### <a name="additional-library-directories"></a>Zusätzliche Bibliotheksverzeichnisse

Ermöglicht dem Benutzer das Überschreiben des umgebungsbedingten Bibliothekspfads. ([/LIBPATH](libpath-additional-libpath.md):Ordner)

### <a name="link-library-dependencies"></a>Bibliothekabhängigkeiten verknüpfen

Gibt an, ob die LIB-Dateien verknüpft werden sollen, die von abhängigen Projekten erstellt wurden. Normalerweise möchten Sie in den .lib-Dateien eine Verknüpfung herstellen, dies ist jedoch bei bestimmten DLLs möglicherweise nicht der Fall.

Sie können auch eine OBJ-Datei angeben, indem Sie den Dateinamen und den relativen Pfad angeben, z.B. ..\\..\MyLibProject\MyObjFile.obj. Wenn der Quellcode für die .obj-Datei einen vorkompilierten Header #includes, z. B. pch.h, befindet sich die Datei pch.obj im selben Ordner wie MyObjFile.obj. Sie müssen auch pch.obj als zusätzliche Abhängigkeit hinzufügen.

### <a name="use-library-dependency-inputs"></a>Bibliothekabhängigkeitseingaben verwenden

Gibt an, ob die Eingaben für das Bibliothekstool und nicht die Bibliotheksdatei selbst beim Verknüpfen in Bibliotheksausgaben von Projektabhängigkeiten verwendet werden sollen. Wenn durch ein abhängiges Projekt in einem umfangreichen Projekt eine LIB-Datei generiert wird, werden inkrementelle Verknüpfungen deaktiviert. Wenn es viele abhängige Projekte gibt, durch die LIB-Dateien generiert werden, kann die Anwendungserstellung längere Zeit in Anspruch nehmen. Wenn diese Eigenschaft auf **Ja**festgelegt ist, verknüpft das Projektsystem in den .obj-Dateien für .libs, die von abhängigen Projekten erstellt wurden, und ermöglicht die inkrementelle Verknüpfung.

Informationen zum Zugriff auf die **Eigenschaftenseite "Allgemeine** Verknüpfung" finden Sie unter Festlegen von [C++-Compiler- und Buildeigenschaften in Visual Studio](../working-with-project-properties.md).

### <a name="link-status"></a>Linkstatus

Gibt an, ob der Linker einen Fortschrittsindikator anzeigen soll, der anzeigt, welcher Prozentsatz der Verknüpfung vollständig ist. Standardmäßig werden diese Statusinformationen nicht angezeigt. ([/LTCG](ltcg-link-time-code-generation.md):STATUS| LTCG:KEIN STATUS)

### <a name="prevent-dll-binding"></a>DLL-Bindung verhindern

[/ALLOWBIND](allowbind-prevent-dll-binding.md):NO legt ein Bit im Header einer DLL fest, das bind.exe angibt, dass das Bild nicht gebunden werden darf. Möglicherweise möchten Sie nicht, dass eine DLL gebunden wird, wenn sie digital signiert wurde (die Bindung macht die Signatur ungültig).

### <a name="treat-linker-warning-as-errors"></a>Behandeln von Linkerwarnungen als Fehler

[/WX](wx-treat-linker-warnings-as-errors.md) bewirkt, dass keine Ausgabedatei generiert wird, wenn der Linker eine Warnung generiert.

### <a name="force-file-output"></a>Force File Output

Die Option [/FORCE](force-force-file-output.md) weist den Linker an, eine EXE-Datei oder DLL zu erstellen, auch wenn auf ein Symbol verwiesen, aber nicht definiert oder multipliziert ist. Es kann ungültige EXE-Datei erstellen.

**Entscheidungen**

- **Aktiviert** - /FORCE ohne Argumente impliziert sowohl mehrere als auch ungelöste.
- **Nur definiertes Symbol multiplizieren** - Verwenden Sie /FORCE:MULTIPLE, um eine Ausgabedatei zu erstellen, auch wenn LINK mehr als eine Definition für ein Symbol findet.
- **Nur undefiniertes Symbol** - Verwenden Sie /FORCE:UNRESOLVED, um eine Ausgabedatei zu erstellen, unabhängig davon, ob LINK ein nicht definiertes Symbol findet oder nicht. /FORCE:UNRESOLVED wird ignoriert, wenn das Einstiegspunktsymbol nicht aufgelöst ist.

### <a name="create-hot-patchable-image"></a>Erstellen eines Hot Patchable-Images

Bereitet ein Bild für hotpatching vor.

**Entscheidungen**

- **Aktiviert** – Bereitet ein Abbild für das Hotpatching vor.
- **Nur X86 Image** - Bereitet ein X86-Bild für hotpatching vor.
- **Nur X64 Image** - Bereitet ein X64-Bild für hotpatching vor.
- **Itanium Image Only** - Bereitet ein Itanium-Bild für Hotpatching vor.

### <a name="specify-section-attributes"></a>Abschnittsattribute angeben

Die Option [/SECTION](section-specify-section-attributes.md) ändert die Attribute eines Abschnitts und überschreibt die Attribute, die beim Kompilieren der .obj-Datei für den Abschnitt festgelegt wurden.

## <a name="input-property-page"></a>Eingabe-Eigenschaftenseite

### <a name="additional-dependencies"></a>Zusätzliche Abhängigkeiten

Gibt zusätzliche Elemente an, die der Link-Befehlszeile hinzugefügt werden sollen, z. *B. kernel32.lib*.

### <a name="ignore-all-default-libraries"></a>Alle Standardbibliotheken ignorieren

Die Option [/NODEFAULTLIB](nodefaultlib-ignore-libraries.md) weist den Linker an, eine oder mehrere Standardbibliotheken aus der Liste der Bibliotheken zu entfernen, die beim Auflösen externer Verweise durchsucht werden.

### <a name="ignore-specific-default-libraries"></a>Bestimmte Standardbibliotheken ignorieren

Gibt einen oder mehrere Namen der zu ignorierenden Standardbibliotheken an. Trennen Sie mehrere Bibliotheken mit Semikolons. (/NODEFAULTLIB:[Name, Name, ...])

### <a name="module-definition-file"></a>Moduldefinitionsdatei

Die Option [/DEF](def-specify-module-definition-file.md) übergibt eine Moduldefinitionsdatei (.def) an den Linker. Es kann nur eine .def-Datei für LINK angegeben werden.

### <a name="add-module-to-assembly"></a>Hinzufügen von Modul zur Baugruppe

Mit der Option [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md) können Sie einer Baugruppe einen Modulverweis hinzufügen. Typinformationen im Modul sind für das Bauprogramm, das die Modulreferenz hinzugefügt hat, nicht verfügbar. Die Eingabeinformationen im Modul sind jedoch für jedes Programm verfügbar, das auf die Assembly verweist.

### <a name="embed-managed-resource-file"></a>Einbetten der verwalteten Ressourcendatei

[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) bettet eine Ressourcendatei in die Ausgabedatei ein.

### <a name="force-symbol-references"></a>Symbolverweise erzwingen

Die Option [/INCLUDE](include-force-symbol-references.md) weist den Linker an, der Symboltabelle ein angegebenes Symbol hinzuzufügen.

### <a name="delay-loaded-dlls"></a>Verzögerte geladene DLLs

Die Option [/DELAYLOAD](delayload-delay-load-import.md) führt zu einem verzögerten Laden von DLLs. Der DLL-Name gibt eine DLL an, um das Laden zu verzögern.

### <a name="assembly-link-resource"></a>Assembly-Link-Ressource

Die Option [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md) erstellt einen Link zu einer .NET Framework-Ressource in der Ausgabedatei. Die Ressourcendatei wird nicht in der Ausgabedatei abgelegt.

## <a name="manifest-file-property-page"></a>Manifestdatei-Eigenschaftenseite

### <a name="generate-manifest"></a>Manifest generieren

[/MANIFEST](manifest-create-side-by-side-assembly-manifest.md) gibt an, dass der Linker eine seite-für-seite-Manifestdatei erstellen soll.

### <a name="manifest-file"></a>Manifestdatei

[Mit /MANIFESTFILE](manifestfile-name-manifest-file.md) können Sie den Standardnamen der Manifestdatei ändern. Der Standardname der Manifestdatei ist der Dateiname mit angehängtem .manifest.

### <a name="additional-manifest-dependencies"></a>Zusätzliche Manifestabhängigkeiten

[Mit /MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md) können Sie Attribute angeben, die im Abhängigkeitsabschnitt der Manifestdatei platziert werden.

### <a name="allow-isolation"></a>Isolation zulassen

Gibt das Verhalten bei der Manifestsuche an. ([/ALLOWISOLATION](allowisolation-manifest-lookup.md):NEIN)

### <a name="enable-user-account-control-uac"></a>Benutzerkontensteuerung aktivieren (UAC)

Gibt an, ob die Benutzerkontensteuerung aktiviert ist.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md), /MANIFESTUAC:NO)

### <a name="uac-execution-level"></a>UAC-Ausführungsebene

Gibt die angeforderte Ausführungsstufe für die Anwendung an, wenn sie mit der Benutzerkontensteuerung ausgeführt wird.  (/MANIFESTUAC:level=[Wert])

**Entscheidungen**

- **asInvoker** - UAC Execution Level: als Aufrufer.
- **highestAvailable** - UAC Execution Level: höchste verfügbare.
- **requireAdministrator** - UAC Execution Level: Erfordern Sie Administrator.

### <a name="uac-bypass-ui-protection"></a>UAC Bypass UI-Schutz

Gibt an, ob die Schutzebenen der Benutzeroberfläche für andere Fenster auf dem Desktop umgangen werden sollen.  Legen Sie diese Eigenschaft nur für Eingabehilfen auf "Ja" fest.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md):uiAccess=[true | false])

## <a name="debugging-property-page"></a>Eigenschaftenseite "Debugging"

### <a name="generate-debug-info"></a>Debug-Informationen generieren

Diese Option ermöglicht die Erstellung von Debuginformationen für die EXE-Datei oder die DLL.

**Entscheidungen**

- **Nein** - Erzeugt keine Debuginformationen.
- **Debuginformationen generieren** – Erstellen Sie eine vollständige Programmdatenbank (PDB), die für die Verteilung an Microsoft Symbol Server geeignet ist.
- **Debug-Informationen generieren, optimiert für schnellere Links** - Erzeugt eine Programmdatenbank (PDB), die sich ideal für den Edit-Link-Debug-Zyklus ausgibt.
- **Debuginformationen generieren, die für die Freigabe und Veröffentlichung optimiert sind** – Erstellt eine Programmdatenbank (PDB), die sich ideal für den Edit-Link-Debug-Zyklus ausgibt.

### <a name="generate-program-database-file"></a>Generieren der Programmdatenbankdatei

Wenn [/DEBUG](debug-generate-debug-info.md) angegeben ist, erstellt der Linker standardmäßig eine Programmdatenbank (PDB), die Debuginformationen enthält. Der Standarddateiname für die PDB hat den Basisnamen des Programms und die Erweiterung .pdb.

### <a name="strip-private-symbols"></a>Strip Private Symbole

Die Option [/PDBSTRIPPED](pdbstripped-strip-private-symbols.md) erstellt eine zweite PDB-Datei (Program Database), wenn Sie Ihr Programmabbild mit einer der Compiler- oder Linkeroptionen erstellen, die eine PDB-Datei generieren (/DEBUG, /Z7, /Zd oder /Zi).

### <a name="generate-map-file"></a>Kartendatei generieren

Die Option [/MAP](map-generate-mapfile.md) weist den Linker an, eine Mapfile zu erstellen.

### <a name="map-file-name"></a>Name der Zuordnungsdatei

Ein benutzerbestimmter Name für die Mapfile. Er ersetzt den Standardnamen.

### <a name="map-exports"></a>Kartenexporte

Die Option [/MAPINFO](mapinfo-include-information-in-mapfile.md) weist den Linker an, die angegebenen Informationen in eine Mapfile aufzunehmen, die erstellt wird, wenn Sie die Option /MAP angeben. EXPORTS weist den Linker an, exportierte Funktionen einzuschließen.

### <a name="debuggable-assembly"></a>Debuggable Assembly

[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md) gibt das Attribut DebuggableAttribute mit Debuginformationsverfolgung aus und deaktiviert JIT-Optimierungen.

## <a name="system-property-page"></a>Systemeigenschaftenseite

### <a name="subsystem"></a>Subsystem

Die Option [/SUBSYSTEM](subsystem-specify-subsystem.md) teilt dem Betriebssystem mit, wie die EXE-Datei ausgeführt wird. Die Auswahl des Subsystems wirkt sich auf das Einstiegspunktsymbol (oder die Einstiegspunktfunktion) aus, die der Linker auswählen wird.

**Entscheidungen**

- **Nicht gesetzt** - Kein Subsystemsatz.
- **Konsole** - Win32-Zeichenmodusanwendung. Konsolenanwendungen erhalten vom Betriebssystem eine Konsole. Wenn main oder wmain definiert ist, ist CONSOLE die Standardeinstellung.
- **Windows** - Die Anwendung erfordert keine Konsole, wahrscheinlich weil sie eigene Fenster für die Interaktion mit dem Benutzer erstellt. Wenn WinMain oder wWinMain definiert ist, ist WINDOWS die Standardeinstellung.
- **Native** - Gerätetreiber für Windows NT. Wenn /DRIVER:WDM angegeben ist, ist NATIVE der Standard.
- **EFI-Anwendung** - EFI-Anwendung.
- **EFI Boot Service Driver** - EFI Boot Service Driver.
- **EFI ROM** - EFI ROM.
- **EFI-Laufzeit** - EFI-Laufzeit.
- **POSIX** - Anwendung, die mit dem POSIX-Subsystem in Windows NT ausgeführt wird.

### <a name="minimum-required-version"></a>Mindest-Erforderliche Version

Geben Sie die mindestens erforderliche Version des Subsystems an. Die Argumente sind Dezimalzahlen im Bereich 0 bis 65.535.

### <a name="heap-reserve-size"></a>Heap-Reservegröße

Gibt die Gesamtgröße der Heapzuweisung im virtuellen Speicher an. Der Standardwert ist 1 MB.    ([/HEAP](heap-set-heap-size.md):Reserve)

### <a name="heap-commit-size"></a>Heap-Commit-Größe

Gibt die Gesamtgröße der Heapzuordnung im physischen Speicher an. Der Standardwert ist 4 KB.    ([/HEAP](heap-set-heap-size.md):reserve,commit)

### <a name="stack-reserve-size"></a>StackReserveSize

Gibt die Gesamtgröße der Stapelreservierung im virtuellen Speicher an. Der Standardwert ist 1 MB.     ([/STACK](stack-stack-allocations.md):Reserve)

### <a name="stack-commit-size"></a>StackCommitSize

Gibt die Gesamtgröße der Stapelzuordnung im physischen Speicher an. Der Standardwert ist 4 KB.     ([/STACK](stack-stack-allocations.md):reserve,commit)

### <a name="enable-large-addresses"></a>Aktivieren großer Adressen

Die Option [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md) teilt dem Linker mit, dass die Anwendung Adressen verarbeiten kann, die größer als 2 Gigabyte sind. Standardmäßig ist /LARGEADDRESSAWARE:NO aktiviert, wenn /LARGEADDRESSAWARE nicht anderweitig in der Linkerzeile angegeben ist.

### <a name="terminal-server"></a>Terminalserver

Die Option [/TSAWARE](tsaware-create-terminal-server-aware-application.md) legt ein Flag im Feld IMAGE_OPTIONAL_HEADER DllCharacteristics im optionalen Header des Programmabbilds fest. Wenn dieses Flag festgelegt ist, wird der Terminalserver keine bestimmten Änderungen an der Anwendung vornehmen.

### <a name="swap-run-from-cd"></a>Swap Run von CD

Die Option [/SWAPRUN](swaprun-load-linker-output-to-swap-file.md) weist das Betriebssystem an, zuerst die Linkerausgabe in eine Auslagerungsdatei zu kopieren und dann das Image von dort aus auszuführen. Bei dieser Option handelt es sich um eine Windows NT 4.0-Funktion (und höher). Wenn **CD** angegeben ist, kopiert das Betriebssystem das Abbild auf einem Wechseldatenträger in eine Auslagerungsdatei und lädt es dann.

### <a name="swap-run-from-network"></a>Swap Run aus dem Netzwerk

Die Option [/SWAPRUN](swaprun-load-linker-output-to-swap-file.md) weist das Betriebssystem an, zuerst die Linkerausgabe in eine Auslagerungsdatei zu kopieren und dann das Image von dort aus auszuführen. Bei dieser Option handelt es sich um eine Windows NT 4.0-Funktion (und höher). Wenn **NET** angegeben ist, kopiert das Betriebssystem zuerst das Binärabbild aus dem Netzwerk in eine Auslagerungsdatei und lädt es von dort. Diese Option ist nützlich, um Anwendungen über das Netzwerk auszuführen.

### <a name="driver"></a>Treiber

Verwenden Sie die Linkeroption [/DRIVER,](driver-windows-nt-kernel-mode-driver.md) um einen Windows NT-Kernelmodustreiber zu erstellen.

**Entscheidungen**

- **Nicht festgelegt** - Standardtreibereinstellung.
- **Treiber** - Treiber
- **NUR UP** - /DRIVER:UPONLY bewirkt, dass der Linker das IMAGE_FILE_UP_SYSTEM_ONLY Bit zu den Merkmalen im Ausgabeheader hinzufügt, um anzugeben, dass es sich um einen Uniprozessortreiber (UP) handelt. Das Betriebssystem weigert sich, einen UP-Treiber auf ein Multiprozessorsystem (MP) zu laden.
- **WDM** - /DRIVER:WDM bewirkt, dass der Linker das IMAGE_DLLCHARACTERISTICS_WDM_DRIVER Bit im DllCharacteristics-Feld des optionalen Headers setzt.

## <a name="optimization-property-page"></a>Optimierungseigenschaftsseite

### <a name="references"></a>Verweise

[/OPT](opt-optimizations.md):REF eliminiert Funktionen und/oder Daten, auf die nie verwiesen wird, während /OPT:NOREF Funktionen und/oder Daten speichert, auf die nie verwiesen wird.

### <a name="enable-comdat-folding"></a>COMDAT-Faltung aktivieren

Verwenden Sie [/OPT](opt-optimizations.md):ICF\[=iterations], um identische COMDAT-Faltungen durchzuführen.

### <a name="function-order"></a>Funktionsreihenfolge

Die Option [/ORDER](order-put-functions-in-order.md)weist LINK an, Ihr Programm zu optimieren, indem bestimmte COMDATs in einer vorgegebenen Reihenfolge in das Bild eingefügt werden. LINK platziert die Funktionen in der angegebenen Reihenfolge innerhalb jedes Abschnitts im Bild.

### <a name="profile-guided-database"></a>Profilgeführte Datenbank

Geben Sie die .pgd-Datei für profilgesteuerte Optimierungen an. ([/PGD](pgd-specify-database-for-profile-guided-optimizations.md))

### <a name="link-time-code-generation"></a>Link-Zeitcode-Generierung

Gibt Link-Zeitcodegenerierung an. ([/LTCG](ltcg-link-time-code-generation.md))

**Entscheidungen**

- **Standard** - Standard-LTCG-Einstellung.
- **Verwenden Sie Fast Link Time Code Generation** - Verwenden Sie Link Time Code Generierung mit [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md).
- **Link Time Code Generierung** verwenden - [Link Time Code Generierung](ltcg-link-time-code-generation.md)verwenden.
- **Profilgeführte Optimierung - Instrument** - [Profilgeführte Optimierung](../profile-guided-optimizations.md) mit :PGINSTRUMENT verwenden.
- **Profilgeführte Optimierung - Optimierung** - Gibt an, dass der Linker die Profildaten verwenden soll, die nach dem Ausführen der instrumentierten Binärdatei erstellt wurden, um ein optimiertes Abbild zu erstellen.
- **Profilgeführte Optimierung - Update** - Ermöglicht und verfolgt die Liste der Eingabedateien, die aus dem in der :PGINSTRUMENT-Phase angegebenen Hinzugefügt oder geändert werden können.

## <a name="embedded-idl-property-page"></a>Eingebettete IDL-Eigenschaftenseite

### <a name="midl-commands"></a>MIDL-Befehle

Geben Sie DIE MIDL-Befehlszeile Optionen an. ([/MIDL](midl-specify-midl-command-line-options.md):@responsefile)

### <a name="ignore-embedded-idl"></a>Embedded IDL ignorieren

Die Option [/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md) gibt an, dass alle IDL-Attribute im Quellcode nicht in einer .idl-Datei verarbeitet werden sollen.

### <a name="merged-idl-base-file-name"></a>Zusammengeführter IDL-Basisdateiname

Die Option [/IDLOUT](idlout-name-midl-output-files.md) gibt den Namen und die Erweiterung der .idl-Datei an.

### <a name="type-library"></a>Typbibliothek

Die Option [/TLBOUT](tlbout-name-dot-tlb-file.md) gibt den Namen und die Erweiterung der .tlb-Datei an.

### <a name="typelib-resource-id"></a>TypeLib-Ressourcen-ID

Ermöglicht es Ihnen, die Ressourcen-ID der vom Linker generierten Typbibliothek anzugeben. ([/TLBID](tlbid-specify-resource-id-for-typelib.md):id)

## <a name="windows-metadata-property-page"></a>Windows-Metadaten-Eigenschaftenseite

### <a name="generate-windows-metadata"></a>Generieren von Windows-Metadaten

Aktiviert oder deaktiviert die Generierung von Windows-Metadaten.

**Entscheidungen**

- **Ja** - Aktivieren Sie die Generierung von Windows-Metadatendateien.
- **Nein** - Deaktivieren Sie die Generierung von Windows-Metadatendateien.

### <a name="windows-metadata-file"></a>Windows-Metadatendatei

Der Optionsschalter [/WINMDFILE.](winmdfile-specify-winmd-file.md)

### <a name="windows-metadata-key-file"></a>Windows-Metadatenschlüsseldatei

Geben Sie das Schlüssel- oder Schlüsselpaar zum Signieren einer Windows-Metadaten an. ([/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md):Dateiname)

### <a name="windows-metadata-key-container"></a>Windows-Metadatenschlüsselcontainer

Geben Sie einen Schlüsselcontainer zum Signieren einer Windows-Metadaten an. ([/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md):Name)

### <a name="windows-metadata-delay-sign"></a>Windows-Metadatenverzögerungszeichen

Teilweise signieren Sie eine Windows-Metadaten. Verwenden Sie [/WINMDDELAYSIGN,](winmddelaysign-partially-sign-a-winmd.md) wenn Sie den öffentlichen Schlüssel nur in den Windows-Metadaten platzieren möchten. Der Standardwert ist /WINMDDELAYSIGN:NO.

## <a name="advanced-property-page"></a>Erweiterte Eigenschaftenseite

### <a name="entry-point"></a>Einstiegspunkt

Die Option [/ENTRY](entry-entry-point-symbol.md) gibt eine Einstiegspunktfunktion als Startadresse für eine EXE-Datei oder DLL an.

### <a name="no-entry-point"></a>Kein Einstiegspunkt

Die Option [/NOENTRY](noentry-no-entry-point.md)ist zum Erstellen einer reinen Ressourcen-DLL erforderlich. Verwenden Sie diese Option, um `_main` zu verhindern, dass LINK einen Verweis mit der DLL verknüpft.

### <a name="set-checksum"></a>Festlegen von Checksum

Die Option [/RELEASE](release-set-the-checksum.md) legt die Prüfsumme im Header einer EXE-Datei fest.

### <a name="base-address"></a>Basisadresse

Legt eine Basisadresse für das Programm fest. ([/BASE](base-base-address.md):-Adresse,\[Größe] | @filename,Schlüssel)

### <a name="randomized-base-address"></a>Randomisierte Basisadresse

Randomisierte Basisadresse. ([/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md)\[:NEIN])

### <a name="fixed-base-address"></a>Feste Basisadresse

Erstellt ein Programm, das nur an seiner bevorzugten Basisadresse geladen werden kann. ([/FIXED](fixed-fixed-base-address.md)\[:NEIN])

### <a name="data-execution-prevention-dep"></a>Datenausführungsverhinderung (Data Execution Prevention, DEP)

Markiert eine ausführbare Datei als getestet, um mit der Windows Data Execution Prevention-Funktion kompatibel zu sein. ([/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)\[:NO])

### <a name="turn-off-assembly-generation"></a>Deaktivieren der Assembly-Generierung

Die Option [/NOASSEMBLY](noassembly-create-a-msil-module.md) weist den Linker an, ein Abbild für die aktuelle Ausgabedatei ohne .NET Framework-Assembly zu erstellen.

### <a name="unload-delay-loaded-dll"></a>Entladen Verzögerung geladen eLl

Der **UNLOAD** UNLOAD-Qualifizierer weist die Delay-Load-Hilfsfunktion an, das explizite Entladen der DLL zu unterstützen. ([/DELAY](delay-delay-load-import-settings.md):ENTLADEN)

### <a name="nobind-delay-loaded-dll"></a>Nobind-Verzögerung geladene DLL

Der **NOBIND** NOBIND-Qualifizierer weist den Linker an, keine bindbare IAT in das endgültige Bild aufzunehmen. Das Standardverhalten ist, die bindungsfähige IAT für verzögert geladene DLLs zu erstellen. ([/DELAY](delay-delay-load-import-settings.md):NOBIND)

### <a name="import-library"></a>Importbibliothek

Überschreibt den Standardnamen für die Importbibliothek. ([/IMPLIB](implib-name-import-library.md):Dateiname)

### <a name="merge-sections"></a>Zusammenführen von Abschnitten

Die Option [/MERGE](merge-combine-sections.md) kombiniert den ersten Abschnitt (von) mit dem zweiten Abschnitt (bis) und benennt den resultierenden Abschnitt nach. Beispiel: /merge:.rdata=.text.

### <a name="target-machine"></a>Zielmaschine

Die Option [/MACHINE](machine-specify-target-platform.md) gibt die Zielplattform für das Programm an.

**Entscheidungen**

- **Nicht eingestellt**
- **MachineARM**
- **MaschineARM64**
- **MachineEBC**
- **MaschineIA64**
- **MachineMIPS**
- **MaschineMIPS16**
- **MaschineMIPSFPU**
- **MaschineMIPSFPU16**
- **MaschineSH4**
- **MachineTHUMB**
- **MachineX64**
- **MachineX86**

### <a name="profile"></a>Profil

Erstellt eine Ausgabedatei, die mit dem Leistungstoolprofiler verwendet werden kann. Erfordert GenerateDebugInformation (/[/DEBUG](debug-generate-debug-info.md)), die festgelegt werden muss. ([/PROFIL](profile-performance-tools-profiler.md))

### <a name="clr-thread-attribute"></a>CLR-Threadattribut

Geben Sie explizit das Threadingattribut für den Einstiegspunkt Ihres CLR-Programms an.

**Entscheidungen**

- **MTA-Threadingattribut** – Wendet das MTAThreadAttribute-Attribut auf den Einstiegspunkt Ihres Programms an.
- **STA-Threadingattribut** – Wendet das STAThreadAttribute-Attribut auf den Einstiegspunkt Ihres Programms an.
- **Standard-Threadingattribut** - Genauso wie nicht [angeben /CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md). Lässt die Common Language Runtime (CLR) das Standard-Threadingattribut festlegen.

### <a name="clr-image-type"></a>CLR-Bildtyp

Legt den Typ (IJW, rein oder sicher) eines CLR-Images fest.

**Entscheidungen**

- **IJW-Bild erzwingen**
- **Force Pure IL Image**
- **Force Safe IL-Image**
- **Standardbildtyp**

### <a name="key-file"></a>Schlüsseldatei

Geben Sie schlüssel- oder schlüsselpaar an, um eine Baugruppe zu signieren. ([/KEYfile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md):Dateiname)

### <a name="key-container"></a>Schlüsselcontainer

Geben Sie einen Schlüsselcontainer zum Signieren einer Baugruppe an. ([/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md):Name)

### <a name="delay-sign"></a>Verzögerungszeichen

Teilweise signieren Sie eine Baugruppe. Verwenden Sie [/DELAYSIGN,](delaysign-partially-sign-an-assembly.md) wenn Sie nur den öffentlichen Schlüssel in der Assembly platzieren möchten. Der Standardwert ist /DELAYSIGN:NO.

### <a name="clr-unmanaged-code-check"></a>CLR-Überprüfung für nicht verwalteten Code

[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md) gibt an, ob der Linker SuppressUnmanagedCodeSecurityAttribute auf linkergenerierte PInvoke-Aufrufe von verwaltetem Code in systemeigene DLLs anwenden soll.

### <a name="error-reporting"></a>Fehlerberichterstellung

Ermöglicht Ihnen, Informationen über interne Compilerfehler direkt an das Visual C++-Team zu senden.

**Entscheidungen**

- **PromptImmediately** - Sofort auffordern.
- **Warteschlange für die nächste Anmeldung** - Warteschlange für die nächste Anmeldung.
- **Fehlerbericht senden** - Fehlerbericht senden.
- **Kein Fehlerbericht** - Kein Fehlerbericht.

### <a name="sectionalignment"></a>SectionAlignment

Die Option [/ALIGN](align-section-alignment.md) gibt die Ausrichtung jedes Abschnitts innerhalb des linearen Adressraums des Programms an. Das Zahlenargument ist in Bytes und muss eine Stärke von zwei sein.

### <a name="preserve-last-error-code-for-pinvoke-calls"></a>Letzten Fehlercode für PInvoke-Aufrufe beibehalten

[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md), der standardmäßig aktiviert ist, behält den letzten Fehlercode von Funktionen bei, die über den P/Invoke-Mechanismus aufgerufen werden, mit dem Sie systemeigene Funktionen in DLLS aufrufen können, aus Code, der mit /clr kompiliert wurde.

**Entscheidungen**

- **Aktiviert** CLRSupportLastError.
- **Deaktiviert** CLRSupportLastError.
- **Nur System-Dlls** - Aktivieren Sie CLRSupportLastError nur für System-DLLs.

### <a name="image-has-safe-exception-handlers"></a>Image hat sichere Ausnahmehandler

Wenn [/SAFESEH](safeseh-image-has-safe-exception-handlers.md) angegeben ist, erzeugt der Linker nur dann ein Bild, wenn er auch eine Tabelle der sicheren Ausnahmehandler des Bildes erstellen kann. In dieser Tabelle ist für das Betriebssystem angegeben, welche Ausnahmehandler für das Image gültig sind.

---
title: Linker-Eigenschaftenseiten
ms.date: 07/24/2019
ms.topic: article
ms.assetid: 7e7671e5-a35a-4e67-9bdb-661d75c4d11e
ms.openlocfilehash: fd0befd7b8ed4e7a4209c3c80602be2f2a99422f
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079595"
---
# <a name="linker-property-pages"></a>Linker-Eigenschaftenseiten

Die folgenden Eigenschaften finden Sie unter **Project** > **Properties** > **Configuration Properties** > **Linker**. Weitere Informationen zum Linker finden Sie unter [cl Ruft die Linker](cl-invokes-the-linker.md) -und [Linkeroptionen](linker-options.md)auf.

## <a name="general-property-page"></a>Eigenschaften Seite "Allgemein"

### <a name="output-file"></a>Ausgabedatei

Die Option [/out](out-output-file-name.md) überschreibt den Standardnamen und den Speicherort des Programms, das der Linker erstellt.

### <a name="show-progress"></a>Status anzeigen

Druckt linkerstatusmeldungen.

**choices**

- **Nicht festgelegt** : keine Ausführlichkeit.
- **Alle Fortschrittsmeldungen anzeigen** : zeigt alle Statusmeldungen an.
- **Für durchsuchte Bibliotheken** : Zeigt Statusmeldungen an, die nur die durchsuchten Bibliotheken angeben.
- Informationen **über COMDAT-Faltung während der optimierten Verknüpfung** : zeigt Informationen zur COMDAT-Faltung während der optimierten Verknüpfung.
- Informationen **zu Daten, die während der optimierten Verknüpfung entfernt** wurden
- Informationen **zu Modulen, die mit Seh nicht kompatibel** sind: zeigt Informationen über Module an, die mit der sicheren Ausnahmebehandlung
- Informationen **über die Linkeraktivität im Zusammenhang mit verwaltetem Code**

### <a name="version"></a>Version

Die [/Version](version-version-information.md) -Option weist den Linker an, eine Versionsnummer in den Header der exe-oder DLL-Datei einzufügen. Verwenden Sie DUMPBIN/Headers, um das Feld Bildversion der optionalen Header Werte anzuzeigen und die Auswirkung von **/Version**anzuzeigen.

### <a name="enable-incremental-linking"></a>Inkrementelle Verknüpfung aktivieren

Aktiviert inkrementelles Verknüpfen. ([/Incremental](incremental-link-incrementally.md),/Incremental: No)

### <a name="suppress-startup-banner"></a>Startbanner unterdrücken

Die Option [/nologo](nologo-suppress-startup-banner-linker.md) verhindert die Anzeige der Copyright Meldung und der Versionsnummer.

### <a name="ignore-import-library"></a>Importbibliothek ignorieren

Durch diese Eigenschaft wird der Linker angewiesen, keine während des aktuellen Builds erstellte LIB-Ausgabe mit einem abhängigen Projekt zu verknüpfen. Sie ermöglicht es dem Projekt System, DLL-Dateien zu verarbeiten, die keine lib-Datei erstellen, wenn Sie erstellt werden. Wenn ein Projekt von einem anderen Projekt abhängt, das eine DLL generiert, verknüpft das Projektsystem automatisch die LIB-Datei, die von diesem untergeordneten Projekt erstellt wurde. Diese Eigenschaft ist möglicherweise unnötig in Projekten, die COM-DLLs oder reine Ressourcen-DLLs entwickeln, da diese DLLs keine sinnvollen Exporte aufweisen. Wenn eine DLL keine Exporte hat, generiert der Linker keine lib-Datei. Wenn keine Datei "Export. lib" vorhanden ist und das Projekt System den Linker anweist, mit der fehlenden DLL zu verknüpfen, schlägt die Verknüpfung fehl. Verwenden Sie die Eigenschaft **Importbibliothek ignorieren**, um dieses Problem zu beheben. Wenn diese Einstellung auf **Ja**festgelegt ist, ignoriert das Projekt System das vorhanden sein oder Fehlen der LIB-Datei und bewirkt, dass alle Projekte, die von diesem Projekt abhängen, nicht mit der nicht vorhandenen lib-Datei verknüpft werden.

Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreImportLibrary%2A>.

### <a name="register-output"></a>Ausgabe registrieren

Führt `regsvr32.exe /s $(TargetPath)` für die Buildausgabe aus, dies ist nur für DLL-Projekte gültig. Bei EXE-Projekten wird diese Eigenschaft ignoriert. Legen Sie zum Registrieren einer EXE-Ausgabe für die Konfiguration ein Postbuildereignis fest, um die benutzerdefinierte Registrierung auszuführen, die für registrierte EXE-Dateien stets erforderlich ist.

Informationen zum programmgesteuerten Zugriff auf diese Eigenschaft finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.RegisterOutput%2A>.

### <a name="per-user-redirection"></a>Umleitung pro Benutzer

Die Registrierung in Visual Studio erfolgte herkömmlicherweise in HKEY_CLASSES_ROOT (HKCR). Unter Windows Vista und höheren Betriebssystemen müssen Sie Visual Studio im erweiterten Modus ausführen, um auf HKCR zugreifen zu können. Entwickler möchten nicht immer im erweiterten Modus ausgeführt werden, müssen aber trotzdem mit der Registrierung arbeiten. Die Umleitung pro Benutzer ermöglicht es Ihnen, sich zu registrieren, ohne dass Sie im erweiterten Modus ausgeführt werden müssen.

Die Umleitung pro Benutzer erzwingt eine Umleitung aller Schreibvorgänge für HKCR zu HKEY\_CURRENT\_USER (HKCU). Wenn die Umleitung pro Benutzer deaktiviert ist, kann der [Projektbuildfehler PRJ0050](../../error-messages/tool-errors/project-build-error-prj0050.md) auftreten, wenn das Programm versucht, in HKCR zu schreiben.

### <a name="additional-library-directories"></a>Zusätzliche Bibliotheksverzeichnisse

Ermöglicht dem Benutzer das Überschreiben des umgebungsbedingten Bibliothekspfads. ([/LIBPATH](libpath-additional-libpath.md): Ordner)

### <a name="link-library-dependencies"></a>Bibliothekabhängigkeiten verknüpfen

Gibt an, ob die LIB-Dateien verknüpft werden sollen, die von abhängigen Projekten erstellt wurden. In der Regel möchten Sie einen Link in den lib-Dateien durchsuchen, aber dies ist für bestimmte DLLs möglicherweise nicht der Fall.

Sie können auch eine OBJ-Datei angeben, indem Sie den Dateinamen und den relativen Pfad angeben, z.B. ..\\..\MyLibProject\MyObjFile.obj. Wenn der Quellcode für die OBJ-Datei einen vorkompilierten Header #includes, z. b. "PCH. h", befindet sich die Datei "PCH. obj" im selben Ordner wie "myobjfile. obj". Außerdem müssen Sie "PCH. obj" als zusätzliche Abhängigkeit hinzufügen.

### <a name="use-library-dependency-inputs"></a>Bibliothekabhängigkeitseingaben verwenden

Gibt an, ob die Eingaben in das Bibliotheks Tool statt in die Bibliotheksdatei selbst verwendet werden sollen, wenn die Bibliotheks Ausgaben von Projekt Abhängigkeiten verknüpft werden. Wenn durch ein abhängiges Projekt in einem umfangreichen Projekt eine LIB-Datei generiert wird, werden inkrementelle Verknüpfungen deaktiviert. Wenn es viele abhängige Projekte gibt, durch die LIB-Dateien generiert werden, kann die Anwendungserstellung längere Zeit in Anspruch nehmen. Wenn diese Eigenschaft auf " **Ja**" festgelegt ist, verknüpft das Projekt System in den OBJ-Dateien für. lib, die von abhängigen Projekten erstellt werden, sodass inkrementelles Verknüpfen ermöglicht wird

Weitere Informationen zum Zugreifen auf die Eigenschaften Seite " **Allgemein** " finden Sie [unter C++ Festlegen von Compiler-und Buildeigenschaften in Visual Studio](../working-with-project-properties.md).

### <a name="link-status"></a>Linkstatus

Gibt an, ob der Linker eine Statusanzeige anzeigen soll, die anzeigt, welcher Prozentsatz des Links abgeschlossen ist. Standardmäßig werden diese Statusinformationen nicht angezeigt. ([/LTCG](ltcg-link-time-code-generation.md): Status | LTCG: NOSTATUS)

### <a name="prevent-dll-binding"></a>DLL-Bindung verhindern

[/ALLOWBIND](allowbind-prevent-dll-binding.md): No legt ein Bit im Header einer DLL fest, das BIND. exe angibt, dass das Image nicht gebunden werden darf. Möglicherweise möchten Sie nicht, dass eine DLL gebunden wird, wenn sie digital signiert wurde (die Bindung macht die Signatur ungültig).

### <a name="treat-linker-warning-as-errors"></a>Linker-Warnung als Fehler behandeln

[/WX](wx-treat-linker-warnings-as-errors.md) bewirkt, dass keine Ausgabedatei generiert wird, wenn der Linker eine Warnung generiert.

### <a name="force-file-output"></a>Dateiausgabe erzwingen

Die [/Force](force-force-file-output.md) -Option weist den Linker an, eine exe-Datei oder-dll zu erstellen, auch wenn auf ein Symbol verwiesen wird, aber nicht definiert oder die Multiplikation definiert ist. Möglicherweise wird eine ungültige exe-Datei erstellt.

**choices**

- **Aktiviert** -/Force ohne Argumente impliziert sowohl mehrfach als auch nicht aufgelöst.
- **Nur mehrfach definiertes Symbol** verwenden: Verwenden Sie/Force: Multiple, um eine Ausgabedatei zu erstellen, auch wenn der Link mehr als eine Definition für ein Symbol findet.
- Nicht **definiertes Symbol** : Verwenden Sie/Force: nicht aufgelöst, um eine Ausgabedatei zu erstellen, unabhängig davon, ob Link ein nicht definiertes Symbol findet /Force: nicht aufgelöste wird ignoriert, wenn das Einstiegspunkt Symbol nicht aufgelöst wird.

### <a name="create-hot-patchable-image"></a>Erstellen eines hotpatchfähigen Images

Bereitet ein Image für Hotpatching vor.

**choices**

- **Aktiviert** : bereitet ein Image für Hotpatching vor.
- **Nur x86-Image** : bereitet ein x86-Image für Hotpatching vor.
- **Nur x64-Image** : bereitet ein x64-Image für Hotpatching vor.
- **Nur Itanium-Image** : bereitet ein Itanium-Image für Hotpatching vor.

### <a name="specify-section-attributes"></a>Abschnitts Attribute angeben

Die Option [/section](section-specify-section-attributes.md) ändert die Attribute eines Abschnitts und überschreibt die Attribute, die beim Kompilieren der obj-Datei für den Abschnitt festgelegt wurden.

## <a name="input-property-page"></a>Eingabe Eigenschaften Seite

### <a name="additional-dependencies"></a>Zusätzliche Abhängigkeiten

Gibt zusätzliche Elemente an, die der Link Befehlszeile hinzugefügt werden sollen, z. b. *Kernel32. lib*.

### <a name="ignore-all-default-libraries"></a>Alle Standardbibliotheken ignorieren

Die [/NODEFAULTLIB](nodefaultlib-ignore-libraries.md) -Option weist den Linker an, mindestens eine Standardbibliothek aus der Liste der Bibliotheken zu entfernen, die beim Auflösen externer Verweise durchsucht werden.

### <a name="ignore-specific-default-libraries"></a>Bestimmte Standardbibliotheken ignorieren

Gibt einen oder mehrere Namen der zu ignorierenden Standardbibliotheken an. Trennen Sie mehrere Bibliotheken durch Semikolons. (/NODEFAULTLIB: [Name, Name,...])

### <a name="module-definition-file"></a>Modul Definitionsdatei

Die Option [/DEF](def-specify-module-definition-file.md) übergibt eine Modul Definitionsdatei (. def) an den Linker. Es kann nur eine DEF-Datei angegeben werden, die verknüpft werden kann.

### <a name="add-module-to-assembly"></a>Modul zur Assembly hinzufügen

Mit der [/ASSEMBLYMODULE](assemblymodule-add-a-msil-module-to-the-assembly.md) -Option können Sie einen Modul Verweis auf eine Assembly hinzufügen. Typinformationen im Modul stehen nicht für das Assemblyprogramm zur Verfügung, das den Modul Verweis hinzugefügt hat. Typinformationen im Modul stehen jedoch allen Programmen zur Verfügung, die auf die Assembly verweisen.

### <a name="embed-managed-resource-file"></a>Verwaltete Ressourcen Datei einbetten

[/ASSEMBLYRESOURCE](assemblyresource-embed-a-managed-resource.md) bettet eine Ressourcen Datei in die Ausgabedatei ein.

### <a name="force-symbol-references"></a>Symbolverweise erzwingen

Die [/include](include-force-symbol-references.md) -Option weist den Linker an, der Symboltabelle ein angegebenes Symbol hinzuzufügen.

### <a name="delay-loaded-dlls"></a>Verzögerte geladene DLLs

Die Option [/DELAYLOAD](delayload-delay-load-import.md) bewirkt ein verzögertes Laden von DLLs. Der DLL-Name gibt eine DLL an, die das Laden verzögert.

### <a name="assembly-link-resource"></a>Assembly-Link Ressource

Die Option [/ASSEMBLYLINKRESOURCE](assemblylinkresource-link-to-dotnet-framework-resource.md) erstellt einen Link zu einer .NET Framework Ressource in der Ausgabedatei. die Ressourcen Datei wird nicht in die Ausgabedatei eingefügt.

## <a name="manifest-file-property-page"></a>Manifest-Datei (Eigenschaften Seite)

### <a name="generate-manifest"></a>Manifest generieren

[/Manifest](manifest-create-side-by-side-assembly-manifest.md) gibt an, dass der Linker eine Seite-an-Seite-Manifest-Datei erstellen soll.

### <a name="manifest-file"></a>Manifest-Datei

[/MANIFESTFILE](manifestfile-name-manifest-file.md) ermöglicht das Ändern des Standard namens der Manifest-Datei. Der Standardname der Manifest-Datei ist der Dateiname mit angefügtem Manifest.

### <a name="additional-manifest-dependencies"></a>Zusätzliche Manifest-Abhängigkeiten

Mit [/MANIFESTDEPENDENCY](manifestdependency-specify-manifest-dependencies.md) können Sie Attribute angeben, die im Abhängigkeits Abschnitt der Manifestressource abgelegt werden.

### <a name="allow-isolation"></a>Isolation zulassen

Gibt das Verhalten bei der Manifestsuche an. ([/ALLOWISOLATION](allowisolation-manifest-lookup.md): Nein)

### <a name="enable-user-account-control-uac"></a>Benutzerkontensteuerung (User Account Control, UAC) aktivieren

Gibt an, ob die Benutzerkontensteuerung aktiviert ist.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md),/MANIFESTUAC: No)

### <a name="uac-execution-level"></a>UAC-Ausführungs Ebene

Gibt die angeforderte Ausführungs Ebene für die Anwendung an, wenn Sie mit der Benutzerkontensteuerung ausgeführt wird.  (/MANIFESTUAC: Level = [Wert])

**choices**

- **asInvoker** -UAC-Ausführungs Ebene: als INVOKER.
- **highestAvailable** -UAC-Ausführungs Ebene: höchste Verfügbarkeit.
- **requilesministrator** -UAC-Ausführungs Ebene: Administrator erforderlich.

### <a name="uac-bypass-ui-protection"></a>UAC Umgehung des UI-Schutzes

Gibt an, ob Benutzeroberflächen-Schutz Ebenen für andere Fenster auf dem Desktop umgangen werden sollen oder nicht.  Legen Sie diese Eigenschaft nur für Barrierefreiheits Anwendungen auf "yes" fest.  ([/MANIFESTUAC](manifestuac-embeds-uac-information-in-manifest.md): UIAccess = [true | false])

## <a name="debugging-property-page"></a>Eigenschaftenseite "Debugging"

### <a name="generate-debug-info"></a>Debuginformationen generieren

Diese Option ermöglicht die Erstellung von Debuginformationen für die exe-Datei oder die dll.

**choices**

- **Nein** : Es werden keine Debuginformationen erzeugt.
- **Generieren von Debuginformationen** : Erstellen Sie eine komplette Programmdatenbank (PDB), die ideal für die Verteilung an Microsoft Symbol Server geeignet ist.
- **Für schnellere Verknüpfungen optimierte Debuginformationen generieren** : erzeugt eine Programmdatenbank (PDB), die sich ideal für den Edit-Link-Debug-Cycle eignet.
- **Generieren von Debuginformationen, die für Freigabe und Veröffentlichung optimiert** sind: erstellt eine Programmdatenbank (PDB), die ideal für den Edit-Link-Debug-Cycle ist

### <a name="generate-program-database-file"></a>Programm Datenbankdatei generieren

Wenn [/Debug](debug-generate-debug-info.md) angegeben wird, erstellt der Linker standardmäßig eine Programmdatenbank (PDB), die Debuginformationen enthält. Der Standard Dateiname für die PDB enthält den Basis Namen des Programms und die Erweiterung pdb.

### <a name="strip-private-symbols"></a>Private Symbole entfernen

Mit der [/PDBSTRIPPED](pdbstripped-strip-private-symbols.md) -Option wird eine zweite Programm Datenbankdatei (PDB) erstellt, wenn Sie das Programm Image mit einer der Compileroptionen oder Linkeroptionen erstellen, die eine PDB-Datei generieren (/Debug,/Z7,/ZD oder/Zi).

### <a name="generate-map-file"></a>Zuordnungs Datei generieren

Die [/map](map-generate-mapfile.md) -Option weist den Linker an, eine Mapfile zu erstellen.

### <a name="map-file-name"></a>Name der Zuordnungsdatei

Ein vom Benutzer angegebener Name für die Mapfile. Der Standardname wird ersetzt.

### <a name="map-exports"></a>Zuordnungs Exporte

Die [/MapInfo](mapinfo-include-information-in-mapfile.md) -Option weist den Linker an, die angegebenen Informationen in eine Mapfile aufzunehmen, die erstellt wird, wenn Sie die/Map-Option angeben. Exporte weist den Linker an, exportierte Funktionen einzuschließen.

### <a name="debuggable-assembly"></a>Zu entladbare Assembly

[/ASSEMBLYDEBUG](assemblydebug-add-debuggableattribute.md) gibt das DebuggableAttribute-Attribut mit debuginformationsnachverfolgung aus und deaktiviert JIT-Optimierungen.

## <a name="system-property-page"></a>System Eigenschaften Seite

### <a name="subsystem"></a>System

Die Option [/Subsystem](subsystem-specify-subsystem.md) teilt dem Betriebssystem mit, wie die exe-Datei ausgeführt werden soll. Die Auswahl des Subsystems wirkt sich auf das Einstiegspunkt Symbol (oder die Einstiegspunkt Funktion) aus, das der Linker wählt.

**choices**

- **Nicht festgelegt** -kein Subsystem festgelegt.
- **Konsolen** -Win32-zeichenmodusanwendung. Konsolen Anwendungen erhalten eine Konsole vom Betriebssystem. Wenn Main oder wmain definiert ist, ist Console die Standardeinstellung.
- Für **Windows** -Anwendungen ist keine Konsole erforderlich, weil es wahrscheinlich für die Interaktion mit dem Benutzer eigene Fenster erstellt. Wenn WinMain oder wWinMain definiert ist, ist Windows der Standardwert.
- **Native** Gerätetreiber für Windows NT. Wenn /DRIVER:WDM angegeben ist, ist NATIVE der Standard.
- **EFI-Anwendung** : EFI-Anwendung.
- **EFI-Start Dienst Treiber** : der EFI-Start Dienst Treiber.
- **EFI Rom** -EFI-Rom.
- **EFI-Laufzeit** : EFI-Laufzeit.
- **POSIX** -Anwendung, die mit dem POSIX-Subsystem in Windows NT ausgeführt wird.

### <a name="minimum-required-version"></a>Mindestens erforderliche Version

Geben Sie die mindestens erforderliche Version des Subsystems an. Die Argumente sind Dezimalzahlen im Bereich 0 bis 65.535.

### <a name="heap-reserve-size"></a>Heap Reserve Größe

Gibt die gesamte Heap Zuordnungs Größe im virtuellen Speicher an. Der Standardwert ist 1 MB.    ([/Heap](heap-set-heap-size.md): Reserve)

### <a name="heap-commit-size"></a>Heapcommitgröße

Gibt die Gesamtgröße der Heap Zuordnung im physischen Speicher an. Der Standardwert ist 4 KB.    ([/Heap](heap-set-heap-size.md): Reserve, Commit)

### <a name="stack-reserve-size"></a>StackReserveSize

Gibt die Gesamtgröße der Stapelreservierung im virtuellen Speicher an. Der Standardwert ist 1 MB.     ([/Stack](stack-stack-allocations.md): Reserve)

### <a name="stack-commit-size"></a>StackCommitSize

Gibt die Gesamtgröße der Stapel Zuordnung im physischen Speicher an. Der Standardwert ist 4 KB.     ([/Stack](stack-stack-allocations.md): Reserve, Commit)

### <a name="enable-large-addresses"></a>Große Adressen aktivieren

Die [/LARGEADDRESSAWARE](largeaddressaware-handle-large-addresses.md) -Option teilt dem Linker mit, dass die Anwendung Adressen verarbeiten kann, die größer als 2 GB sind. Standardmäßig ist/LARGEADDRESSAWARE: No aktiviert, wenn/LARGEADDRESSAWARE nicht anderweitig in der Linker-Zeile angegeben wird.

### <a name="terminal-server"></a>Terminalserver

Die Option [/TSAWARE](tsaware-create-terminal-server-aware-application.md) legt ein Flag im Feld IMAGE_OPTIONAL_HEADER DllCharacteristics im optionalen Header des Programm Bilds fest. Wenn dieses Flag festgelegt ist, wird der Terminalserver keine bestimmten Änderungen an der Anwendung vornehmen.

### <a name="swap-run-from-cd"></a>Austauschen von CD ausführen

Die Option [/SWAPRUN](swaprun-load-linker-output-to-swap-file.md) weist das Betriebssystem an, zuerst die Linkerausgabe in eine Auslagerungs Datei zu kopieren und dann das Abbild von dort aus auszuführen. Bei dieser Option handelt es sich um eine Funktion von Windows NT 4,0 (und höher). Wenn **CD** angegeben wird, kopiert das Betriebssystem das Abbild auf einem Wechsel Datenträger in eine Auslagerungs Datei und lädt es dann.

### <a name="swap-run-from-network"></a>Austausch aus Netzwerk ausführen

Die Option [/SWAPRUN](swaprun-load-linker-output-to-swap-file.md) weist das Betriebssystem an, zuerst die Linkerausgabe in eine Auslagerungs Datei zu kopieren und dann das Abbild von dort aus auszuführen. Bei dieser Option handelt es sich um eine Funktion von Windows NT 4,0 (und höher). Wenn **net** angegeben wird, kopiert das Betriebssystem zuerst das binäre Abbild aus dem Netzwerk in eine Auslagerungs Datei und lädt es von dort. Diese Option ist nützlich für die Ausführung von Anwendungen über das Netzwerk.

### <a name="driver"></a>Treiber

Verwenden Sie die Option [/Driver](driver-windows-nt-kernel-mode-driver.md) Linker, um einen Windows NT-Kernelmodustreiber zu erstellen.

**choices**

- **Nicht festgelegt** -Standardtreiber Einstellung.
- **Treiber** Treiber
- **Nur nach oben** :/Driver bewirkt, dass der Linker das IMAGE_FILE_UP_SYSTEM_ONLY Bit den Merkmalen im Ausgabe Header hinzufügt, um anzugeben, dass es sich um einen Uniprozessor-Treiber (up) handelt. Das Betriebssystem wird das Laden eines uptreibers auf einem Multiprozessorsystem (MP) ablehnen.
- **WDM** -/Driver: WDM bewirkt, dass der Linker das IMAGE_DLLCHARACTERISTICS_WDM_DRIVER-Bit im DllCharacteristics-Feld des optionalen Headers festgelegt hat.

## <a name="optimization-property-page"></a>Eigenschaften Seite "Optimierung"

### <a name="references"></a>References

[/Opt](opt-optimizations.md): Ref löscht Funktionen und/oder Daten, auf die nie verwiesen wird, während/OPT: NOREF die Funktionen und/oder Daten, auf die nie verwiesen wird, beibehält.

### <a name="enable-comdat-folding"></a>COMDAT-Faltung aktivieren

Verwenden Sie [/opt](opt-optimizations.md): ICF\[= Iterationen], um eine identische COMDAT-Faltung auszuführen.

### <a name="function-order"></a>Funktions Reihenfolge

Die Option [/Order](order-put-functions-in-order.md)gibt den Link an, um das Programm zu optimieren, indem bestimmte COMDATs in einer vordefinierten Reihenfolge in das Bild platziert werden. Mit Link werden die Funktionen in der angegebenen Reihenfolge in den einzelnen Abschnitten des Bilds platziert.

### <a name="profile-guided-database"></a>Profil gesteuerte Datenbank

Geben Sie die PGD-Datei für Profil gesteuerte Optimierungen an. ([/PGD](pgd-specify-database-for-profile-guided-optimizations.md))

### <a name="link-time-code-generation"></a>Link-Zeit Code Generierung

Gibt Link-Zeitcodegenerierung an. ([/LTCG](ltcg-link-time-code-generation.md))

**choices**

- **Standard** -LTCG-Standardeinstellung.
- **Schnelle Link-Zeit Codegenerierung verwenden** -Link-Zeit Codegenerierung mit [/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)verwenden.
- **Link-Zeit Codegenerierung** verwenden- [Link-Zeit Codegenerierung](ltcg-link-time-code-generation.md)verwenden.
- **Profil gesteuerte Optimierung-Instrument** -verwenden Sie die [Profil gesteuerte Optimierung](../profile-guided-optimizations.md) mit:P ginstrument.
- **Profil gesteuerte Optimierung-Optimierung** : gibt an, dass der Linker die nach dem Ausführen der instrumentierten Binärdatei erstellten Profildaten verwenden soll, um ein optimiertes Image zu erstellen.
- **Profil gesteuerte Optimierung-Update** : erlaubt und verfolgt die Liste der Eingabedateien, die hinzugefügt oder geändert werden sollen, was in der:P ginstrument-Phase angegeben wurde.

## <a name="embedded-idl-property-page"></a>Eingebettete IDL-Eigenschaften Seite

### <a name="midl-commands"></a>Mittel l-Befehle

Geben Sie die Optionen für die mittlere Befehlszeile an. ([/MIDL](midl-specify-midl-command-line-options.md):@responsefile)

### <a name="ignore-embedded-idl"></a>Eingebettetes IDL ignorieren

Die [/IGNOREIDL](ignoreidl-don-t-process-attributes-into-midl.md) -Option gibt an, dass alle IDL-Attribute im Quellcode nicht in einer IDL-Datei verarbeitet werden sollen.

### <a name="merged-idl-base-file-name"></a>Zusammen geführter IDL-Basis Dateiname

Die Option [/IDLOUT](idlout-name-midl-output-files.md) gibt den Namen und die Erweiterung der IDL-Datei an.

### <a name="type-library"></a>Typbibliothek

Die Option [/TLBOUT](tlbout-name-dot-tlb-file.md) gibt den Namen und die Erweiterung der TLB-Datei an.

### <a name="typelib-resource-id"></a>TypeLib-Ressourcen-ID

Ermöglicht Ihnen die Angabe der Ressourcen-ID der vom Linker generierten Typbibliothek. ([/TLBID](tlbid-specify-resource-id-for-typelib.md): ID)

## <a name="windows-metadata-property-page"></a>Eigenschaften Seite für Windows-Metadaten

### <a name="generate-windows-metadata"></a>Generieren von Windows-Metadaten

Aktiviert oder deaktiviert die Generierung von Windows-Metadaten.

**choices**

- **Ja** , Generierung von Windows-Metadatendateien aktivieren.
- Deaktivieren Sie die Generierung von **Windows-** Metadatendateien.

### <a name="windows-metadata-file"></a>Windows-Metadatendatei

Der [/WINMDFILE](winmdfile-specify-winmd-file.md) -Options Schalter.

### <a name="windows-metadata-key-file"></a>Windows-Metadaten-Schlüsseldatei

Geben Sie einen Schlüssel oder ein Schlüsselpaar zum Signieren von Windows-Metadaten an ([/WINMDKEYFILE](winmdkeyfile-specify-winmd-key-file.md): filename)

### <a name="windows-metadata-key-container"></a>Windows-metadatenschlüsselcontainer

Geben Sie einen Schlüssel Container zum Signieren von Windows-Metadaten an. ([/WINMDKEYCONTAINER](winmdkeycontainer-specify-key-container.md): Name)

### <a name="windows-metadata-delay-sign"></a>Windows-Metadaten-Verzögerungs Zeichen

Partielles Signieren von Windows-Metadaten. Verwenden Sie [/WINMDDELAYSIGN](winmddelaysign-partially-sign-a-winmd.md) , wenn Sie nur den öffentlichen Schlüssel in den Windows-Metadaten platzieren möchten. Der Standardwert ist/WINMDDELAYSIGN: No.

## <a name="advanced-property-page"></a>Erweiterte Eigenschaften Seite

### <a name="entry-point"></a>Einstiegspunkt

Die Option [/Entry](entry-entry-point-symbol.md) gibt eine Einstiegspunkt Funktion als Startadresse für eine exe-Datei oder eine DLL-Datei an.

### <a name="no-entry-point"></a>Kein Einstiegspunkt

Die [/NOENTRY](noentry-no-entry-point.md)-Option ist erforderlich, um eine reine Ressourcen-DLL zu erstellen. Verwenden Sie diese Option, um zu verhindern, dass Verknüpfung einen Verweis auf `_main` in die DLL verknüpft.

### <a name="set-checksum"></a>Prüfsumme festlegen

Die Option [/Release](release-set-the-checksum.md) legt die Prüfsumme im Header einer exe-Datei fest.

### <a name="base-address"></a>Basisadresse

Legt eine Basisadresse für das Programm fest. ([/Base](base-base-address.md): {Address\[, size] | @filename, Key})

### <a name="randomized-base-address"></a>Zufällige Basisadresse

Zufällige Basisadresse. ([/DynamicBase](dynamicbase-use-address-space-layout-randomization.md)\[: No])

### <a name="fixed-base-address"></a>Basisadresse korrigiert

Erstellt ein Programm, das nur an seiner bevorzugten Basisadresse geladen werden kann. ([/Fixed](fixed-fixed-base-address.md)\[: No])

### <a name="data-execution-prevention-dep"></a>Daten Ausführungs Verhinderung (Data Execution Prevention, DEP)

Markiert eine ausführbare Datei als mit der Windows-Funktion zur Daten Ausführungs Verhinderung kompatibel. ([/NXCOMPAT](nxcompat-compatible-with-data-execution-prevention.md)\[: No])

### <a name="turn-off-assembly-generation"></a>Assemblygenerierung deaktivieren

Die [/noAssembly](noassembly-create-a-msil-module.md) -Option weist den Linker an, ein Bild für die aktuelle Ausgabedatei ohne eine .NET Framework Assembly zu erstellen.

### <a name="unload-delay-loaded-dll"></a>Verzögert geladene DLL entladen

Der **Entlade** Qualifizierer weist die Hilfsfunktion für das verzögerte Laden an, das explizite Entladen der dll zu unterstützen. ([/Delay](delay-delay-load-import-settings.md): entladen)

### <a name="nobind-delay-loaded-dll"></a>NOBIND verzögert geladene DLL

Der **NOBIND** -Qualifizierer weist den Linker an, keine bindbare IAT in das endgültige Image einzuschließen. Das Standardverhalten ist, die bindungsfähige IAT für verzögert geladene DLLs zu erstellen. ([/Delay](delay-delay-load-import-settings.md): NOBIND)

### <a name="import-library"></a>Importbibliothek

Überschreibt den Standardnamen für die Importbibliothek. ([/IMPLIB](implib-name-import-library.md): filename)

### <a name="merge-sections"></a>Zusammenführen von Abschnitten

Die Option [/Merge](merge-combine-sections.md) kombiniert den ersten Abschnitt (von) mit dem zweiten Abschnitt (zu) und benennt den resultierenden Abschnitt in. Beispiel:/Merge:. rdata =. Text.

### <a name="target-machine"></a>Zielcomputer

Die [/Machine](machine-specify-target-platform.md) -Option gibt die Zielplattform für das Programm an.

**choices**

- **Nicht festgelegt**
- **Machinearm**
- **MachineARM64**
- **Machineebc**
- **MachineIA64**
- **Machinemips**
- **MachineMIPS16**
- **Machinemipsf**
- **MachineMIPSFPU16**
- **MachineSH4**
- **Machinethum b**
- **MachineX64**
- **MachineX86**

### <a name="profile"></a>Profil

Erstellt eine Ausgabedatei, die mit dem Leistungstoolprofiler verwendet werden kann. Erfordert, dass GenerateDebugInformation (/[/Debug](debug-generate-debug-info.md)) festgelegt wird. ([/Profile](profile-performance-tools-profiler.md))

### <a name="clr-thread-attribute"></a>CLR-Thread Attribut

Geben Sie das Threading Attribut für den Einstiegspunkt des CLR-Programms explizit an.

**choices**

- **MTA-Threading Attribut** : wendet das MTAThreadAttribute-Attribut auf den Einstiegspunkt des Programms an.
- **STA-Threading Attribut** : wendet das STAThreadAttribute-Attribut auf den Einstiegspunkt des Programms an.
- **Standard Threading Attribut** , identisch mit der Angabe von [/CLRTHREADATTRIBUTE](clrthreadattribute-set-clr-thread-attribute.md). Ermöglicht der Common Language Runtime (CLR) das Festlegen des Standard Threading Attributs.

### <a name="clr-image-type"></a>CLR-Imagetyp

Legt den Typ (IJW, rein oder sicher) eines CLR-Images fest.

**choices**

- **IJW-Image erzwingen**
- **Reines Il-Image erzwingen**
- **Sicheres Il-Bild erzwingen**
- **Standard Bildtyp**

### <a name="key-file"></a>Schlüsseldatei

Geben Sie einen Schlüssel oder ein Schlüsselpaar zum Signieren einer Assembly an. ([/Keyfile](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md): filename)

### <a name="key-container"></a>Schlüssel Container

Geben Sie einen Schlüssel Container zum Signieren einer Assembly an. ([/Keycontainer](keycontainer-specify-a-key-container-to-sign-an-assembly.md): Name)

### <a name="delay-sign"></a>Verzögertes Vorzeichen

Eine Assembly teilweise signieren. Verwenden Sie [/delaysign](delaysign-partially-sign-an-assembly.md) , wenn Sie nur den öffentlichen Schlüssel in der Assembly platzieren möchten. Der Standardwert ist/delaysign: No.

### <a name="clr-unmanaged-code-check"></a>Überprüfung von nicht verwaltetem CLR-Code

[/CLRUNMANAGEDCODECHECK](clrunmanagedcodecheck-add-suppressunmanagedcodesecurityattribute.md) gibt an, ob der Linker SuppressUnmanagedCodeSecurityAttribute auf vom Linker generierte PInvoke-Aufrufe von verwaltetem Code in Native DLLs anwendet.

### <a name="error-reporting"></a>Fehlerberichterstellung

Ermöglicht Ihnen, Informationen über interne Compilerfehler direkt an das Visual C++-Team zu senden.

**choices**

- **Promptimmediately** : sofort auffordern.
- **Warteschlange für nächste** Anmelde Warteschlange für nächste Anmeldung.
- **Fehlerbericht senden** -Fehlerbericht senden.
- **Kein Fehlerbericht** -kein Fehlerbericht.

### <a name="sectionalignment"></a>Sectionalignment

Die [/align](align-section-alignment.md) -Option gibt die Ausrichtung der einzelnen Abschnitte innerhalb des linearen Adressraums des Programms an. Das number-Argument ist in Bytes und muss eine Potenz von zwei sein.

### <a name="preserve-last-error-code-for-pinvoke-calls"></a>Letzten Fehler Code für PInvoke-Aufrufe beibehalten

[/CLRSUPPORTLASTERROR](clrsupportlasterror-preserve-last-error-code-for-pinvoke-calls.md), das standardmäßig aktiviert ist, behält den letzten Fehlercode von Funktionen bei, die durch den P/Aufruf-Mechanismus aufgerufen werden. Dadurch können Sie Native Funktionen in DLLs aufrufen, von Code, der mit/CLR. kompiliert wurde.

**choices**

- **Aktiviert** -CLRSUPPORTLASTERROR aktivieren.
- **Deaktiviert** : CLRSUPPORTLASTERROR deaktivieren.
- **Nur System-DLLs** : Aktivieren Sie CLRSUPPORTLASTERROR nur für System-DLLs.

### <a name="image-has-safe-exception-handlers"></a>Das Image weist sichere Ausnahmehandler auf.

Wenn [/SAFESEH](safeseh-image-has-safe-exception-handlers.md) angegeben wird, erstellt der Linker nur dann ein Image, wenn er auch eine Tabelle mit den sicheren Ausnahme Handlern des Bilds ausgeben kann. In dieser Tabelle ist für das Betriebssystem angegeben, welche Ausnahmehandler für das Image gültig sind.

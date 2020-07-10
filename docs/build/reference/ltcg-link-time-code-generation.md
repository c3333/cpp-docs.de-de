---
title: /LTCG (Code zur Verknüpfungszeit generieren)
description: Die MSVC-Linkeroption/ltcg aktiviert die Link-Zeit Codegenerierung für die Optimierung des gesamten Programms.
ms.date: 07/08/2020
f1_keywords:
- VC.Project.VCLinkerTool.LinkTimeCodeGeneration
- VC.Project.VCConfiguration.WholeProgramOptimization
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
- /ltcg
- VC.Project.VCCLCompilerTool.WholeProgramOptimization
helpviewer_keywords:
- link-time code generation in C++ linker
- /LTCG linker option
- -LTCG linker option
- LTCG linker option
ms.assetid: 788c6f52-fdb8-40c2-90af-4026ea2cf2e2
ms.openlocfilehash: c954794d6d0fd087eee74ebb7e86d77b89a9a8fc
ms.sourcegitcommit: 80c8a512b361bd84e38958beb1a1bf6db7434021
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/09/2020
ms.locfileid: "86180798"
---
# <a name="ltcg-link-time-code-generation"></a>`/LTCG`(Link-Zeit Codegenerierung)

Verwenden **`/LTCG`** Sie, um die Optimierung des gesamten Programms auszuführen oder die PGO-Instrumentation (Profil gesteuerte Optimierung) zu erstellen, Schulungen auszuführen und Profil gesteuerte optimierte Builds zu erstellen.

## <a name="syntax"></a>Syntax

> **`/LTCG`**[**`:`**{**`INCREMENTAL`**|**`NOSTATUS`**|**`STATUS`**|**`OFF`**}]

Diese Optionen sind von Visual Studio 2015 an veraltet:

> **`/LTCG:`**{**`PGINSTRUMENT`**|**`PGOPTIMIZE`**|**`PGUPDATE`**}

### <a name="arguments"></a>Argumente

**`INCREMENTAL`**<br/>
Optionale Gibt an, dass der Linker anstelle des gesamten Projekts nur die Optimierung des gesamten Programms oder die Link-Zeit Codegenerierung (Link-Time Code Generation, LTCG) auf Dateien anwendet Standardmäßig ist dieses Flag nicht festgelegt **`/LTCG`** , wenn angegeben wird, und das gesamte Projekt wird mithilfe der Optimierung des gesamten Programms verknüpft.

**`NOSTATUS`**&#124;**`STATUS`**<br/>
(Optional) Gibt an, ob der Linker eine Statusanzeige anzeigt, die darstellt, welcher Prozentsatz des Links abgeschlossen ist. Standardmäßig werden diese Statusinformationen nicht angezeigt.

**`OFF`**<br/>
(Optional) Deaktiviert die Codegenerierung zur Verknüpfungszeit. Dieses Verhalten ist identisch mit dem, wenn **`/LTCG`** nicht in der Befehlszeile angegeben wird.

**`PGINSTRUMENT`**<br/>
(Optional) Diese Optionen sind von Visual Studio 2015 an veraltet. Verwenden Sie stattdessen **`/LTCG`** und `[/GENPROFILE` oder `/FASTGENPROFILE` ] (genprofile-fastgenprofile-Generate-Profiling-Instrumented-Build.MD), um einen instrumentierten Build für die Profil gesteuerte Optimierung zu generieren. Die Daten, die in instrumentierten Ausführungen gesammelt werden, werden zum Erstellen eines optimierten Images verwendet. Weitere Informationen finden Sie unter [Profilgesteuerte Optimierungen](../profile-guided-optimizations.md). Die Kurzform dieser Option ist **`/LTCG:PGI`** .

**`PGOPTIMIZE`**<br/>
(Optional) Diese Optionen sind von Visual Studio 2015 an veraltet. Verwenden Sie stattdessen **`/LTCG`** und, [`/USEPROFILE`](useprofile.md) um ein optimiertes Image zu erstellen. Weitere Informationen finden Sie unter [Profilgesteuerte Optimierungen](../profile-guided-optimizations.md). Die Kurzform dieser Option ist **`/LTCG:PGO`** .

**`PGUPDATE`**<br/>
(Optional) Diese Optionen sind von Visual Studio 2015 an veraltet. Verwenden Sie stattdessen **`/LTCG`** und, **`/USEPROFILE`** um ein optimiertes Image neu zu erstellen. Weitere Informationen finden Sie unter [Profilgesteuerte Optimierungen](../profile-guided-optimizations.md). Die Kurzform dieser Option ist **`/LTCG:PGU`** .

## <a name="remarks"></a>Bemerkungen

Die **`/LTCG`** -Option weist den Linker an, den Compiler aufzurufen und die Optimierung des gesamten Programms auszuführen. Alternativ können Sie auch eine profilgesteuerte Optimierung ausführen. Weitere Informationen finden Sie unter [Profilgesteuerte Optimierungen](../profile-guided-optimizations.md).

Mit den folgenden Ausnahmen können Sie keine Linker-Optionen zur PGO-Kombination von und hinzufügen **`/LTCG`** **`/USEPROFILE`** , die nicht in der vorherigen PGO-Initialisierungs Kombination der **`/LTCG`** Optionen und angegeben wurden **`/GENPROFILE`** :

- [`/BASE`](base-base-address.md)

- [`/FIXED`](fixed-fixed-base-address.md)

- **`/LTCG`**

- [`/MAP`](map-generate-mapfile.md)

- [`/MAPINFO`](mapinfo-include-information-in-mapfile.md)

- [`/NOLOGO`](nologo-suppress-startup-banner-linker.md)

- [`/OUT`](out-output-file-name.md)

- [`/PGD`](pgd-specify-database-for-profile-guided-optimizations.md)

- [`/PDB`](pdb-use-program-database.md)

- [`/PDBSTRIPPED`](pdbstripped-strip-private-symbols.md)

- [`/STUB`](stub-ms-dos-stub-file-name.md)

- [`/VERBOSE`](verbose-print-progress-messages.md)

Alle Linker-Optionen, die mit der **`/LTCG`** -Option und der- **`/GENPROFILE`** Option zum Initialisieren von PGO angegeben werden, müssen nicht angegeben werden, wenn Sie mit **`/LTCG`** und erstellen **`/USEPROFILE`** ; Sie sind impliziert.

Im weiteren Verlauf dieses Artikels wird die Link-Zeit Codegenerierung erläutert, die von durchgeführt wird **`/LTCG`** .

**`/LTCG`** impliziert mit [`/GL`](gl-whole-program-optimization.md) .

Der Linker Ruft die Codegenerierung der Link Zeit auf, wenn ein Modul, das mithilfe von oder einem MSIL-Modul kompiliert wurde, übermittelt wird **`/GL`** (siehe [ `.netmodule` Dateien als Eingabe für den Linker](netmodule-files-as-linker-input.md)). Wenn Sie **`/LTCG`** beim übergeben **`/GL`** von oder MSIL-Modulen an den Linker nicht explizit angeben, erkennt der Linker diese Situation schließlich und startet den Link mithilfe von neu **`/LTCG`** . Geben **`/LTCG`** Sie explizit **`/GL`** an, wenn Sie und MSIL-Module an den Linker übergeben, um eine möglichst schnelle Buildleistung zu erzielen.

Verwenden Sie für eine noch schnellere Leistung **`/LTCG:INCREMENTAL`** . Diese Option weist den Linker an, nur die Dateien, die von einer Änderung der Quelldatei betroffen sind, und nicht das gesamte Projekt erneut zu optimieren. Mit dieser Option kann die benötigte Verbindungszeit erheblich reduziert werden. Diese Option ist nicht mit der [inkrementellen Verknüpfung](incremental-link-incrementally.md)identisch.

**`/LTCG`** ist nicht für die Verwendung mit zulässig [`/INCREMENTAL`](incremental-link-incrementally.md) .

Wenn **`/LTCG`** zum Verknüpfen von Modulen verwendet wird [`/Og`](og-global-optimizations.md) , die mit,, [`/O1`](o1-o2-minimize-size-maximize-speed.md) oder kompiliert [`/O2`](o1-o2-minimize-size-maximize-speed.md) [`/Ox`](ox-full-optimization.md) wurden, werden die folgenden Optimierungen ausgeführt:

- Inlineoptimierung über verschiedene Module hinweg

- Interprozedurale Registerreservierung (nur bei 64-Bit-Betriebssystemen)

- Benutzerdefinierte Aufrufkonvention (nur x86)

- Geringe TLS-Verschiebung (nur x86)

- Doppelte Stapelausrichtung (nur x86)

- Verbesserte Speichereindeutigkeit (verbesserte Interferenzinformationen für globale Variablen und Eingabeparameter)

> [!NOTE]
> Der Linker bestimmt, welche Optimierungen zum Kompilieren der einzelnen Funktionen verwendet wurden, und wendet die gleichen Optimierungen zur Linkzeit an.

Die Verwendung von **`/LTCG`** und **`/O2`** bewirkt eine Optimierung mit doppelter Ausrichtung.

Wenn **`/LTCG`** und **`/O1`** angegeben sind, wird die doppelte Ausrichtung nicht durchgeführt. Wenn die meisten Funktionen in einer Anwendung für die Geschwindigkeit kompiliert werden und einige Funktionen für die Größe kompiliert werden (z. b. mithilfe des [`optimize`](../../preprocessor/optimize.md) Pragmas), werden die Funktionen, die für die Größe optimiert sind, vom Compiler doppelt ausgerichtet, wenn Sie Funktionen aufzurufen, die eine doppelte Ausrichtung erfordern.

Wenn er alle Aufrufziele einer Funktion identifizieren kann, ignoriert der Compiler die expliziten Aufrufkonventionsmodifizierer der Funktion und versucht, die Aufrufkonvention der Funktion zu optimieren:

- Übergeben von Parametern in Registern

- Neuanordnen von Parametern zur Ausrichtung

- Entfernen nicht verwendeter Parameter

Wenn eine Funktion über einen Funktionszeiger aufgerufen wird, oder wenn eine Funktion von außerhalb eines Moduls aufgerufen wird, das mit kompiliert wird **`/GL`** , versucht der Compiler nicht, die Aufruf Konvention der Funktion zu optimieren.

> [!NOTE]
> Wenn Sie verwenden **`/LTCG`** und neu definieren `mainCRTStartup` , kann die Anwendung unvorhersehbares Verhalten aufweisen, das sich auf den Benutzercode bezieht, der vor dem Initialisieren globaler Objekte ausgeführt wird. Es gibt drei Möglichkeiten, dieses Problem zu beheben: definieren Sie `mainCRTStartup` die Datei, die mit enthalten ist, nicht neu, kompilieren Sie die Datei mit `mainCRTStartup` **`/LTCG`** , oder initialisieren Sie globale Variablen und Objekte statisch.

### <a name="ltcg-and-msil-modules"></a>`/LTCG`und MSIL-Module

Module, die mit und kompiliert werden, [`/GL`](gl-whole-program-optimization.md) [`/clr`](clr-common-language-runtime-compilation.md) können als Eingabe für den Linker verwendet werden, wenn **`/LTCG`** angegeben wird.

- **`/LTCG`** kann Native Objektdateien und gemischte systemeigene/verwaltete Objektdateien (kompiliert mit) akzeptieren **`/clr`** . Die **`/clr:pure`** **`/clr:safe`** Compileroptionen und sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 und höher nicht unterstützt.

- **`/LTCG:PGI`** akzeptiert Native Module nicht, die mit und kompiliert wurden. **`/GL`****`/clr`**

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Lesen Sie dazu [Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften**  >  Seite**Allgemeine** Konfigurations Eigenschaften aus.

1. Ändern Sie die Eigenschaft **Optimierung des ganzen Programms** .

Sie können auch **`/LTCG`** auf bestimmte Builds anwenden, indem **Build**Sie  >  auf der Menüleiste die Option "**Profil gesteuerte Optimierung** erstellen" auswählen oder eine der Optionen für die Profil gesteuerte Optimierung im Kontextmenü für das Projekt auswählen.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkTimeCodeGeneration%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC (linkerreferenz)](linking.md)\
[Linkeroptionen](linker-options.md)

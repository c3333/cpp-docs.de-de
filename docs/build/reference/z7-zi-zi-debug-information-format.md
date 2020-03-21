---
title: /Z7, /Zi, /ZI (Debuginformationsformat)
ms.date: 04/08/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.DebugInformationFormat
- /ZI
- /Zi
- /Z7
- VC.Project.VCCLWCECompilerTool.DebugInformationFormat
helpviewer_keywords:
- C7 compatible compiler option [C++]
- Debug Information Format compiler option
- ZI compiler option
- -Zi compiler option [C++]
- /ZI compiler option [C++]
- Z7 compiler option [C++]
- debugging [C++], debug information files
- Zi compiler option [C++]
- /Zi compiler option [C++]
- program database compiler option [C++]
- full symbolic debugging information
- /Z7 compiler option [C++]
- line numbers only compiler option [C++]
- cl.exe compiler, debugging options
- -Z7 compiler option [C++]
ms.openlocfilehash: aeaf435874b6d6b9dbc8a3d12ec06d38bf33aaae
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078265"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (Debuginformationsformat)

Gibt den Typ der Debuginformationen an, die für das Programm erstellt werden, und gibt an, ob diese Informationen in Objektdateien oder in einer Programm Datenbankdatei (PDB) gespeichert werden.

## <a name="syntax"></a>Syntax

> **"/Z**{**7**|**i**|**i**}

## <a name="remarks"></a>Bemerkungen

Wenn Code kompiliert und im Debugmodus erstellt wird, erstellt der Compiler Symbolnamen für Funktionen und Variablen, Typinformationen und Positionen von Zeilennummern, die vom Debugger verwendet werden können. Diese symbolischen Debuginformationen können entweder in die Objektdateien (OBJ-Dateien) eingefügt werden, die vom Compiler erstellt wurden, oder in einer separaten PDB-Datei (PDB-Datei) für die ausführbare Datei.  Die Optionen für das Debuginformationsformat werden in den folgenden Abschnitten beschrieben.

### <a name="none"></a>Keine

Wenn keine Debuginformationsformat-Option angegeben ist, erzeugt der Compiler standardmäßig keine Debuginformationen, sodass die Kompilierung schneller erfolgt.

### <a name="z7"></a>/Z7

Die Option **/Z7** erzeugt Objektdateien, die auch vollständige symbolische Debuginformationen für die Verwendung mit dem Debugger enthalten. Diese Objektdateien und die erstellter ausführbare Datei können wesentlich größer sein als Dateien, die keine Debuginformationen aufweisen. Zu den symbolischen Debuginformationen gehören die Namen und Typen von Variablen sowie Funktionen und Zeilennummern. Es wird keine PDB-Datei erstellt.

Für Verteiler von Debugversionen von Drittanbieterbibliotheken gibt es einen Vorteil, dass keine PDB-Datei vorhanden ist. Allerdings sind die Objektdateien für vorkompilierte Header während der Bibliotheks Verknüpfungs Phase und zum Debuggen erforderlich. Wenn in der PCH-Objektdatei nur Typinformationen (und kein Code) vorhanden sind, müssen Sie auch die Option [/Yl (PCH-Verweis für Debugbibliothek einfügen)](yl-inject-pch-reference-for-debug-library.md) verwenden, die beim Erstellen der Bibliothek standardmäßig aktiviert ist.

Die Option veraltet [/GM (minimale Neuerstellung aktivieren)](gm-enable-minimal-rebuild.md) ist nicht verfügbar, wenn **/Z7** angegeben wird.

### <a name="zi"></a>/ZI

Die Option **/Zi** erzeugt eine separate PDB-Datei, die alle symbolischen Debuginformationen für die Verwendung mit dem Debugger enthält. Die Debuginformationen sind nicht in den Objektdateien oder der ausführbaren Datei enthalten, wodurch Sie wesentlich kleiner werden.

Die Verwendung von **/Zi** wirkt sich nicht auf Optimierungen aus. **/Zi** impliziert jedoch **/Debug**; Weitere Informationen finden Sie unter [/Debug (Debuginformationen generieren)](debug-generate-debug-info.md) .

Wenn Sie sowohl **/Zi** als auch **/CLR**angeben, wird das <xref:System.Diagnostics.DebuggableAttribute>-Attribut nicht in die Assemblymetadaten eingefügt. Wenn Sie dies wünschen, müssen Sie es im Quellcode angeben. Dieses Attribut kann Auswirkungen auf die Laufzeitleistung der Anwendung haben. Weitere Informationen dazu, wie sich das **Debugfähige** Attribut auf die Leistung auswirkt und wie Sie die Auswirkungen auf die Leistung ändern können, finden Sie unter Vereinfachen des Debuggens [eines Bilds](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).

Der Compiler benennt die PDB-Datei *Project*. pdb. Wenn Sie eine Datei außerhalb eines Projekts kompilieren, erstellt der Compiler eine PDB-Datei mit dem Namen VC*x*. pdb, wobei *x* eine Verkettung der Haupt-und neben Versionsnummer der verwendeten Compilerversion ist. Der Compiler bettet den Namen der PDB und eine identifizierende Signatur mit Zeitstempel in jede Objektdatei ein, die mit dieser Option erstellt wurde, die den Debugger auf den Speicherort von symbolischen und Zeilennummern Informationen verweist. Der Name und die Signatur in der PDB-Datei müssen mit der ausführbaren Datei für die im Debugger zu ladenden Symbole identisch sein. Der WinDbg-Debugger kann nicht übereinstimmende Symbole mit dem `.symopt+0x40` Befehl laden. Visual Studio verfügt nicht über eine ähnliche Option zum Laden von nicht übereinstimmenden Symbolen.

Wenn Sie eine Bibliothek aus Objekten erstellen, die mit **/Zi**kompiliert wurden, muss die zugehörige PDB-Datei verfügbar sein, wenn die Bibliothek mit einem Programm verknüpft ist. Wenn Sie die Bibliothek verteilen, müssen Sie daher auch die PDB-Datei verteilen. Wenn Sie eine Bibliothek erstellen möchten, die Debuginformationen enthält, ohne PDB-Dateien zu verwenden, müssen Sie die Option **/Z7** auswählen. Wenn Sie die Optionen für vorkompilierte Header verwenden, werden Debuginformationen sowohl für den vorkompilierten Header als auch den restlichen Quellcode in der PDB-Datei abgelegt.

### <a name="zi"></a>/ZI

Die **/Zi** -Option ähnelt **/Zi**, aber Sie erzeugt eine PDB-Datei in einem Format, das die Funktion " [Bearbeiten und Fortfahren](/visualstudio/debugger/edit-and-continue-visual-cpp) " unterstützt. Sie müssen diese Option verwenden, um Debuggingfeatures bearbeiten und Fortfahren verwenden zu können. Die Funktion "Bearbeiten und Fortfahren" ist für die Produktivität von Entwicklern nützlich, kann aber Probleme bei der Code Größe, Leistung und Compilerkonformität verursachen. Da die meisten Optimierungen nicht mit "Bearbeiten und Fortfahren" kompatibel sind, deaktiviert die Verwendung von **/Zi** alle `#pragma optimize` Anweisungen in Ihrem Code. Die **/Zi** -Option ist auch mit der Verwendung des [ &#95; &#95;vordefinierten&#95; &#95; Zeilen voreingestellten Makros](../../preprocessor/predefined-macros.md)nicht kompatibel. Code, der mit **/Zi** kompiliert wurde, kann keine  **&#95; &#95;&#95; Zeile** als Nichttyp-Vorlagen Argument verwenden, obwohl **&#95; &#95;line&#95;** in Makro Erweiterungen verwendet werden kann.

Die Option **/Zi** erzwingt, dass die Optionen [/Gy (Aktivierung der Funktionsebene)](gy-enable-function-level-linking.md) und [/FC (vollständiger Pfad der Quell Code Datei in Diagnose)](fc-full-path-of-source-code-file-in-diagnostics.md) in der Kompilierung verwendet werden.

**/Zi** ist nicht kompatibel mit [/CLR (Common Language Runtime-Kompilierung)](clr-common-language-runtime-compilation.md).

> [!NOTE]
> Die **/Zi** -Option ist nur in den Compilern verfügbar, die auf x86-und x64-Prozessoren abzielen. Diese Compileroption ist nicht in den Compilern verfügbar, die auf ARM-Prozessoren abzielen.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Öffnen Sie die **Eigenschaften Seite Konfigurations Eigenschaften** > **C++ C/**  > **Allgemein** .

1. Ändern Sie die Eigenschaft **Debuginformationsformat** . Klicken Sie auf **OK**, um die Änderungen zu speichern.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)

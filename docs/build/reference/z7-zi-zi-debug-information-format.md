---
title: /Z7, /Zi, /ZI (Debuginformationsformat)
ms.date: 07/06/2020
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
ms.openlocfilehash: bc3fd9c065219a128e29290084b1e1fb51fc773e
ms.sourcegitcommit: 85d96eeb1ce41d9e1dea947f65ded672e146238b
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86058593"
---
# <a name="z7-zi-zi-debug-information-format"></a>/Z7, /Zi, /ZI (Debuginformationsformat)

Die **`/Z7`** **`/Zi`** **`/ZI`** Compileroptionen, und geben den Typ der Debuginformationen an, die für das Programm erstellt wurden, und ob diese Informationen in Objektdateien oder in einer Programm Datenbankdatei (PDB) gespeichert werden.

## <a name="syntax"></a>Syntax

> **`/Z7`**\
> **`/Zi`**\
> **`/ZI`**

## <a name="remarks"></a>Hinweise

Wenn Sie eine Debugoption angeben, erstellt der Compiler Symbolnamen für Funktionen und Variablen, Typinformationen und Zeilen Speicherorte, die vom Debugger verwendet werden können. Diese symbolischen Debuginformationen können entweder in die *`.obj`* vom Compiler erzeugten Objektdateien (Dateien) oder in einer separaten PDB-Datei ( *`.pdb`* Datei) für die ausführbare Datei eingeschlossen werden. Die Optionen für das Debuginformationsformat werden in den folgenden Abschnitten beschrieben.

### <a name="none"></a>Keine

Wenn keine Debuginformationsformat-Option angegeben ist, erzeugt der Compiler standardmäßig keine Debuginformationen, sodass die Kompilierung schneller erfolgt.

### <a name="z7"></a>/Z7

Mit der- **`/Z7`** Option werden Objektdateien erstellt, die auch vollständige symbolische Debuginformationen für die Verwendung mit dem Debugger enthalten. Diese Objektdateien und Bibliotheken, die aus Ihnen erstellt wurden, können wesentlich größer sein als Dateien, die keine Debuginformationen aufweisen. Zu den symbolischen Debuginformationen gehören die Namen und Typen von Variablen, Funktionen und Zeilennummern. Vom Compiler wird keine PDB-Datei erzeugt. Eine PDB-Datei kann jedoch dennoch aus diesen Objektdateien oder Bibliotheken generiert werden, wenn dem Linker die Option übergeben wird **`/DEBUG`** .

Für Verteiler von Debugversionen von Drittanbieterbibliotheken gibt es einen Vorteil, dass keine PDB-Datei vorhanden ist. Allerdings sind die Objektdateien für vorkompilierte Header während der Bibliotheks Verknüpfungs Phase und zum Debuggen erforderlich. Wenn in der Objektdatei nur Typinformationen (und kein Code) vorhanden *`.pch`* sind, müssen Sie auch die Option [ `/Yl` (PCH-Verweis für Debugbibliothek einfügen)](yl-inject-pch-reference-for-debug-library.md) verwenden, die beim Erstellen der Bibliothek standardmäßig aktiviert ist.

Die veraltete Option [ `/Gm` (minimale Neuerstellung aktivieren)](gm-enable-minimal-rebuild.md) ist nicht verfügbar, wenn **`/Z7`** angegeben wird.

### <a name="zi"></a>/ZI

Mit der- **`/Zi`** Option wird eine separate PDB-Datei erstellt, die alle symbolischen Debuginformationen für die Verwendung mit dem Debugger enthält. Die Debuginformationen sind nicht in den Objektdateien oder der ausführbaren Datei enthalten, wodurch Sie wesentlich kleiner werden.

Die Verwendung von **`/Zi`** wirkt sich nicht auf Optimierungen aus. Impliziert jedoch **`/Zi`** **`/debug`** . Weitere Informationen finden Sie unter [ `/DEBUG` (Debuginformationen generieren)](debug-generate-debug-info.md).

Wenn Sie sowohl als **`/Zi`** auch angeben **`/clr`** , wird das- <xref:System.Diagnostics.DebuggableAttribute> Attribut nicht in die Assemblymetadaten eingefügt. Wenn Sie dies wünschen, müssen Sie es im Quellcode angeben. Dieses Attribut kann Auswirkungen auf die Laufzeitleistung der Anwendung haben. Weitere Informationen dazu, wie sich das `Debuggable` Attribut auf die Leistung auswirkt und wie Sie die Auswirkungen auf die Leistung ändern können, finden Sie unter [vereinfachen des Debuggens eines Bilds](/dotnet/framework/debug-trace-profile/making-an-image-easier-to-debug).

Der Compiler benennt die PDB-Datei *`<project>.pdb`* , wobei *`<project>`* der Name Ihres Projekts ist. Wenn Sie eine Datei außerhalb eines Projekts kompilieren, erstellt der Compiler eine PDB-Datei mit dem Namen *`VC<x>.pdb`* , wobei *`<x>`* eine Verkettung der Haupt-und neben Versionsnummer der verwendeten Compilerversion ist. Der Compiler bettet den Namen der PDB und eine identifizierende Signatur mit Zeitstempel in jede Objektdatei ein, die mit dieser Option erstellt wurde. Dieser Name und diese Signatur zeigen den Debugger auf den Speicherort von symbolischen und Zeilennummern Informationen. Der Name und die Signatur in der PDB-Datei müssen mit der ausführbaren Datei für die im Debugger zu ladenden Symbole identisch sein. Der WinDbg-Debugger kann mit dem Befehl nicht übereinstimmende Symbole laden **`.symopt+0x40`** . Visual Studio verfügt nicht über eine ähnliche Option zum Laden von nicht übereinstimmenden Symbolen.

Wenn Sie eine Bibliothek aus Objekten erstellen, die mit kompiliert wurden **`/Zi`** , muss die zugehörige PDB-Datei verfügbar sein, wenn die Bibliothek mit einem Programm verknüpft ist. Dies bedeutet, dass Sie, wenn Sie die Bibliothek verteilen, auch die PDB-Datei verteilen müssen. Wenn Sie eine Bibliothek erstellen möchten, die Debuginformationen enthält, ohne PDB-Dateien zu verwenden, müssen Sie die **`/Z7`** Option auswählen. Wenn Sie die Optionen für vorkompilierte Header verwenden, werden Debuginformationen sowohl für den vorkompilierten Header als auch den restlichen Quellcode in der PDB-Datei abgelegt.

### <a name="zi"></a>/Zi

Die- **`/ZI`** Option ähnelt **`/Zi`** , aber Sie erzeugt eine PDB-Datei in einem Format, das die Funktion " [Bearbeiten und Fortfahren](/visualstudio/debugger/edit-and-continue-visual-cpp) " unterstützt. Sie müssen diese Option verwenden, um Debuggingfeatures bearbeiten und Fortfahren verwenden zu können. Die Funktion "Bearbeiten und Fortfahren" ist für die Produktivität von Entwicklern nützlich, kann aber Probleme bei der Code Größe, Leistung und Compilerkonformität verursachen. Da die meisten Optimierungen nicht mit "Bearbeiten und Fortfahren" kompatibel sind, werden durch die Verwendung **`/ZI`** von alle- `#pragma optimize` Anweisungen in Ihrem Code deaktiviert. Die **`/ZI`** Option ist auch mit der Verwendung des [ `__LINE__` vordefinierten Makros](../../preprocessor/predefined-macros.md)nicht kompatibel. mit kompilierter Code **`/ZI`** kann nicht `__LINE__` als Nichttyp-Vorlagen Argument verwendet werden, obwohl `__LINE__` in Makro Erweiterungen verwendet werden kann.

Die **`/ZI`** -Option erzwingt die Verwendung der Optionen [ `/Gy` (Aktivierung der Funktionsebene)](gy-enable-function-level-linking.md) und [ `/FC` (vollständiger Pfad der Quell Code Datei in Diagnose)](fc-full-path-of-source-code-file-in-diagnostics.md) in der Kompilierung.

**`/ZI`** ist nicht kompatibel mit [ `/clr` (Common Language Runtime-Kompilierung)](clr-common-language-runtime-compilation.md).

> [!NOTE]
> Die **`/ZI`** Option ist nur in den Compilern verfügbar, die auf x86-und x64-Prozessoren abzielen. Diese Compileroption ist nicht in den Compilern verfügbar, die auf ARM-Prozessoren abzielen.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Öffnen Sie die **Eigenschaften**  >  Seite Eigenschaften von**C/C++**  >  **Allgemein** .

1. Ändern Sie die Eigenschaft **Debuginformationsformat** . Klicken Sie auf **OK**, um die Änderungen zu speichern.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)

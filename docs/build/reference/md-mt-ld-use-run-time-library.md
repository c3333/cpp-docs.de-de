---
title: /MD,-MT,-LD (Lauf Zeit Bibliothek verwenden)
ms.date: 07/17/2019
f1_keywords:
- /ld
- /mt
- VC.Project.VCCLWCECompilerTool.RuntimeLibrary
- VC.Project.VCCLCompilerTool.RuntimeLibrary
- /md
- /ml
helpviewer_keywords:
- /MT compiler option [C++]
- -MD compiler option [C++]
- threading [C++], multithread compiler option
- MSVCRTD.lib
- MSVCRT.lib
- LIBCMT.lib
- MD compiler option [C++]
- /MD compiler option [C++]
- MT compiler option [C++]
- LD compiler option [C++]
- MDd compiler option [C++]
- -MDd compiler option [C++]
- LIBCD.lib
- -MTd compiler option [C++]
- MTd compiler option [C++]
- /MTd compiler option [C++]
- -LD compiler option [C++]
- /MDd compiler option [C++]
- multithread compiler option
- _STATIC_CPPLIB symbol
- LIBC.lib
- /LD compiler option [C++]
- DLLs [C++], compiler options
- LIBCMTD.lib
- -MT compiler option [C++]
ms.assetid: cf7ed652-dc3a-49b3-aab9-ad60e5395579
ms.openlocfilehash: a66677ebbef984e9a4c8190f184ca3a9126a7b83
ms.sourcegitcommit: d4da3693f83a24f840e320e35c24a4a07cae68e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/18/2020
ms.locfileid: "83550757"
---
# <a name="md-mt-ld-use-run-time-library"></a>/MD, /MT, /LD (Laufzeitbibliothek verwenden)

Zeigt an, ob es sich bei einem Multithread-Modul um eine DLL handelt, und gibt Veröffentlichungs- oder Debugversionen der Laufzeitbibliothek an.

## <a name="syntax"></a>Syntax

```
/MD[d]
/MT[d]
/LD[d]
```

## <a name="remarks"></a>Bemerkungen

|Option|BESCHREIBUNG|
|------------|-----------------|
|**/MD**|Bewirkt, dass die Anwendung die DLL-spezifische und Multithreaded-Version der Laufzeitbibliothek verwendet. Definiert `_MT` und `_DLL` und veranlasst, dass der Compiler den Bibliotheksnamen "MSVCRT.lib" in der OBJ-Datei positioniert.<br /><br /> Mit dieser Option kompilierte Anwendungen werden statisch mit der Bibliothek "MSVCRT.lib" verknüpft. Diese Bibliothek stellt eine Codeschicht bereit, die dem Linker ermöglicht, externe Verweise aufzulösen. Der tatsächliche Arbeitscode ist in Msvcr*VersionNumber*enthalten. DLL-Datei, die zur Laufzeit für Anwendungen verfügbar sein muss, die mit MSVCRT. lib verknüpft sind.|
|**/MDd**|Definiert `_DEBUG`, `_MT` und `_DLL` und veranlasst, dass die Anwendung die DLL-spezifische und Multithreaded-Version der Laufzeitbibliothek verwendet. Außerdem wird verursacht, dass der Compiler den Bibliotheksnamen "MSVCRTD.lib" in der .obj-Datei positioniert.|
|**/MT**|Bewirkt, dass die Anwendung die statische Multithreaded-Version der Laufzeitbibliothek verwendet. Definiert `_MT` und bewirkt, dass der Compiler den Bibliotheksnamen "LIBCMT.LIB" in der OBJ-Datei ablegt, sodass diese Bibliothek vom Linker zum Auflösen externer Symbole verwendet wird.|
|**/MTD**|Definiert `_DEBUG` und `_MT`. Diese Option führt auch dazu, dass der Compiler den Bibliotheksnamen "LIBCMTD.lib" in der .obj-Datei positioniert, sodass der Linker "LIBCMTD.lib" für das Auflösen externer Symbole verwendet.|
|**/LD**|Erstellt eine DLL.<br /><br /> Übergibt die **/dll** -Option an den Linker. Der Linker sucht nach einer `DllMain`-Funktion, die jedoch nicht unbedingt erforderlich ist. Wenn Sie keine `DllMain`-Funktion schreiben, fügt der Linker eine `DllMain`-Funktion ein, die TRUE zurückgibt.<br /><br /> Verknüpft den DLL-Startcode.<br /><br /> Erstellt eine Importbibliothek (LIB), wenn in der Befehlszeile keine Exportdatei (EXP) angegeben wurde. Sie verknüpfen die Importbibliothek mit Anwendungen, die die DLL aufrufen.<br /><br /> Interpretiert [/Fe (Name der exe-Datei)](fe-name-exe-file.md) als Benennung einer DLL und nicht als exe-Datei. Standardmäßig wird der Programmname anstelle von *baseName*. exe zu *baseName*. dll.<br /><br /> Impliziert **/MT** , sofern Sie **/MD**nicht explizit angeben.|
|**/LDd**|Erstellt eine Debug-DLL. Definiert `_MT` und `_DEBUG`.|

Weitere Informationen über C-Laufzeitbibliotheken und welche Bibliotheken bei der Kompilierung mit [/CLR (Common Language Runtime-Kompilierung)](clr-common-language-runtime-compilation.md)verwendet werden, finden Sie unter [Funktionen der CRT-Bibliothek](../../c-runtime-library/crt-library-features.md).

Alle an einen bestimmten Aufruf des Linkers über gebenden Module müssen mit derselben Lauf Zeit Bibliotheks-Compileroption (**/MD**, **/MT**, **/LD**) kompiliert werden.

Weitere Informationen zur Verwendung der Debugversionen der Laufzeitbibliotheken finden Sie unter [C-Lauf Zeit Bibliotheks Referenz](../../c-runtime-library/c-run-time-library-reference.md).

Weitere Informationen zu DLLs finden Sie unter [Erstellen von C/C++-DLLs in Visual Studio](../dlls-in-visual-cpp.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Code Generierung** aus.

1. Ändern Sie die Eigenschaft **Lauf Zeit Bibliothek** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeLibrary%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)

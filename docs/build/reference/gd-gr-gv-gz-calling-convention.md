---
title: /Gd, /Gr, /Gv, /Gz (Aufrufkonvention)
ms.date: 09/05/2018
f1_keywords:
- /Gr
- /Gv
- /Gd
- VC.Project.VCCLCompilerTool.CallingConvention
helpviewer_keywords:
- -Gd compiler option [C++]
- -Gv compiler option [C++]
- /Gv compiler option [C++]
- -Gr compiler option [C++]
- Gd compiler option [C++]
- Gr compiler option [C++]
- /Gz compiler option [C++]
- -Gz compiler option [C++]
- /Gd compiler option [C++]
- Gz compiler option [C++]
- Gv compiler option [C++]
- /Gr compiler option [C++]
ms.assetid: fd3110cb-2d77-49f2-99cf-a03f9ead00a3
ms.openlocfilehash: e1617b7c158e9705a6211310fa7873f667a62ba5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234366"
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (Aufrufkonvention)

Mit diesen Optionen wird festgelegt, in welcher Reihenfolge die Funktionsargumente auf den Stapel verschoben werden, ob die aufrufende oder die aufgerufene Funktion die Argumente am Ende des Aufrufs aus dem Stapel entfernt, und welche Namensergänzungskonvention der Compiler zur Erkennung einzelner Funktionen verwendet.

## <a name="syntax"></a>Syntax

> **`/Gd`**\
> **`/Gr`**\
> **`/Gv`**\
> **`/Gz`**

## <a name="remarks"></a>Bemerkungen

**`/Gd`**, die Standardeinstellung, gibt die [__cdecl](../../cpp/cdecl.md) Aufruf Konvention für alle Funktionen mit Ausnahme der C++-Member-Funktionen und-Funktionen an, die als [__stdcall](../../cpp/stdcall.md), [__fastcall](../../cpp/fastcall.md)oder [__vectorcall](../../cpp/vectorcall.md)gekennzeichnet sind.

**`/Gr`** Gibt die **`__fastcall`** Aufruf Konvention für alle Funktionen mit Ausnahme von C++-Element Funktionen, Funktionen mit dem Namen und Funktionen an, die als `main` **`__cdecl`** , oder markiert sind **`__stdcall`** **`__vectorcall`** . Alle **`__fastcall`** Funktionen müssen über Prototypen verfügen. Diese Aufrufkonvention ist nur in Compilern verfügbar, die auf x86 abzielen, und wird von Compilern ignoriert, die auf andere Architekturen abzielen.

**`/Gz`** Gibt die **`__stdcall`** Aufruf Konvention für alle Funktionen mit Ausnahme von C++-Element Funktionen, Funktionen mit dem Namen und Funktionen an, die als `main` **`__cdecl`** , oder markiert sind **`__fastcall`** **`__vectorcall`** . Alle **`__stdcall`** Funktionen müssen über Prototypen verfügen. Diese Aufrufkonvention ist nur in Compilern verfügbar, die auf x86 abzielen, und wird von Compilern ignoriert, die auf andere Architekturen abzielen.

**`/Gv`** Gibt die **`__vectorcall`** Aufruf Konvention für alle Funktionen mit Ausnahme von C++-Element Funktionen, Funktionen mit dem Namen `main` , Funktionen mit einer `vararg` Variablen Argumentliste oder Funktionen an, die mit einem in Konflikt stehenden-,-oder-Attribut gekennzeichnet sind **`__cdecl`** **`__stdcall`** **`__fastcall`** . Diese Aufrufkonvention ist nur auf x86- und x64-Architekturen verfügbar, die „/arch:SSE2“ und höher unterstützen, und wird von Compilern ignoriert, die auf die ARM-Architektur abzielen.

Funktionen, die eine Variable Anzahl von Argumenten annehmen, müssen als markiert werden **`__cdecl`** .

**`/Gd`**, **`/Gr`** **`/Gv`** und **`/Gz`** sind nicht kompatibel mit [`/clr:safe`](clr-common-language-runtime-compilation.md) oder **/clr: pure**. Die Compileroptionen **/clr:pure** und **/clr:safe** sind in Visual Studio 2015 veraltet und werden in Visual Studio 2017 und höher nicht unterstützt.

> [!NOTE]
> Standardmäßig verwenden C++-Member-Funktionen für x86-Prozessoren [`__thiscall`](../../cpp/thiscall.md) .

Für alle Prozessoren wird eine Member-Funktion, die explizit als **`__cdecl`** , **`__fastcall`** , oder gekennzeichnet ist, **`__vectorcall`** **`__stdcall`** die angegebene Aufruf Konvention verwendet, wenn Sie für diese Architektur nicht ignoriert wird. Eine Member-Funktion, die eine Variable Anzahl von Argumenten annimmt, verwendet immer die **`__cdecl`** Aufruf Konvention.

Diese Compileroptionen haben keine Auswirkungen auf die Namensergänzung von C++-Methoden und -Funktionen. Sofern sie nicht als `extern "C"` deklariert sind, kommt für C++-Methoden und -Funktionen ein anderes Schema für Namensergänzungen zur Anwendung. Weitere Informationen finden Sie unter [Ergänzte Namen](decorated-names.md).

Weitere Informationen zu Aufrufkonventionen finden Sie unter [Calling Conventions (Aufrufkonventionen)](../../cpp/calling-conventions.md).

## <a name="__cdecl-specifics"></a>__cdecl-Besonderheiten

Auf x86-Prozessoren werden alle Funktionsargumente auf dem Stapel von rechts nach links übergeben. Auf ARM- und x64-Architekturen werden einige Argumente nach Register übergeben und der Rest wird auf dem Stapel von rechts nach links übergeben. Die Aufrufroutine ruft die Argumente vom Stapel auf.

Bei C verwendet die **`__cdecl`** Benennungs Konvention den Funktionsnamen, dem ein Unterstrich ( `_` ) vorangestellt ist. es wird keine Groß-/Kleinschreibung durchgeführt. Sofern sie nicht als `extern "C"` deklariert sind, kommt für C++-Funktionen ein anderes Schema für Namensergänzungen zur Anwendung. Weitere Informationen finden Sie unter [Ergänzte Namen](decorated-names.md).

## <a name="__fastcall-specifics"></a>__fastcall-Besonderheiten

Einige der **`__fastcall`** Argumente einer Funktion werden in Registern (für x86-Prozessoren, ECX und EDX) übergeben, und der Rest wird von rechts nach links auf den Stapel verschoben. Die aufgerufene Routine nimmt diese Argumente vor ihrem Rücksprung vom Stapel auf. Normalerweise verringert **/Gr** die Ausführungszeit.

> [!NOTE]
> Seien Sie vorsichtig, wenn Sie die **`__fastcall`** Aufruf Konvention für eine Funktion verwenden, die in der Inline-Assemblysprache geschrieben ist. Es kann zu Konflikten zwischen Ihrer Verwendung von Registern und deren Verwendung durch den Compiler kommen.

Bei C verwendet die **`__fastcall`** Benennungs Konvention den Funktionsnamen, dem ein @-Zeichen vorangestellt **\@** ist, gefolgt von der Größe der Funktionsargumente in Byte. Groß-/Kleinbuchstaben werden nicht umgewandelt. Der Compiler verwendet für die Benennungskonvention diese Vorlage:

`@function_name@number`

Wenn Sie die **`__fastcall`** Benennungs Konvention verwenden, verwenden Sie die standardmäßigen Includedateien. Andernfalls erhalten Sie nicht aufgelöste externe Verweise.

## <a name="__stdcall-specifics"></a>__stdcall-Besonderheiten

Die **`__stdcall`** Argumente einer Funktion werden von rechts nach links auf den Stapel verschoben, und die aufgerufene Funktion holt diese Argumente vor der Rückgabe aus dem Stapel.

Bei C verwendet die **`__stdcall`** Benennungs Konvention den Funktionsnamen, dem ein Unterstrich () vorangestellt ist, **\_** gefolgt von einem at-Zeichen ( **\@** ) und der Größe der Argumente der Funktion in Bytes. Groß-/Kleinbuchstaben werden nicht umgewandelt. Der Compiler verwendet für die Benennungskonvention diese Vorlage:

`_functionname@number`

## <a name="__vectorcall-specifics"></a>__vectorcall-Besonderheiten

**`__vectorcall`** Die ganzzahligen Argumente einer Funktion werden als Wert weitergegeben, wobei bis zu zwei (auf x86) oder vier (bei x64) ganzzahligen Registern und bis zu sechs XMM-Register für Gleit Komma-und Vektor Werte verwendet werden, und der Rest wird auf dem Stapel von rechts nach links weitergegeben. Die aufgerufene Funktion bereinigt den Stapel vor dem Zurückgeben. Vektor- und Gleitkomma-Rückgabewerte werden in XMM0 zurückgegeben.

Bei C verwendet die **`__vectorcall`** Benennungs Konvention den Funktionsnamen, gefolgt von zwei @-Zeichen ( **\@\@** ) und der Größe der Funktionsargumente in Byte. Groß-/Kleinbuchstaben werden nicht umgewandelt. Der Compiler verwendet für die Benennungskonvention diese Vorlage:

`functionname@@number`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die Eigenschaften Seite **C/C++**  >  **erweitert** aus.

1. Ändern Sie die Eigenschaft **Aufrufkonvention**.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>.

## <a name="see-also"></a>Siehe auch

- [MSVC-Compileroptionen](compiler-options.md)
- [MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)

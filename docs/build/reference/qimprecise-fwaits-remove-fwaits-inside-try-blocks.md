---
title: /Qimprecise_fwaits (Entfernen von fwaits in Try-Blöcken)
ms.date: 11/04/2016
f1_keywords:
- /Qimprecise_fwaits
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
ms.openlocfilehash: 424feda66f6925cb305256249101ea4013e3090f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232676"
---
# <a name="qimprecise_fwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits (Entfernen von fwaits in Try-Blöcken)

Entfernt die `fwait` internen Befehle, die blockiert werden, **`try`** Wenn Sie die Compileroption [/fp: außer](fp-specify-floating-point-behavior.md) verwenden.

## <a name="syntax"></a>Syntax

```
/Qimprecise_fwaits
```

## <a name="remarks"></a>Bemerkungen

Diese Option hat keine Auswirkung, wenn **/fp: mit Ausnahme** von nicht ebenfalls angegeben wird. Wenn Sie die Option **/fp:, außer** angeben, fügt der Compiler einen `fwait` Befehl für jede Codezeile in einem- **`try`** Block ein. Auf diese Weise kann der Compiler die bestimmte Codezeile ermitteln, die eine Ausnahme erzeugt. **/Qimprecise_fwaits** entfernt interne `fwait` Anweisungen, sodass nur die Warte Vorgänge um den Block verschoben werden **`try`** . Dadurch wird die Leistung verbessert, aber der Compiler kann nur sagen, welcher **`try`** Block eine Ausnahme auslöst, nicht welche Zeile.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **C/C++** .

1. Klicken Sie auf die Eigenschaftenseite **Befehlszeile** .

1. Geben Sie die Compileroption im Feld **Zusätzliche Optionen** ein.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Siehe auch

[/Q-Optionen (Vorgänge auf niedriger Ebene)](q-options-low-level-operations.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)

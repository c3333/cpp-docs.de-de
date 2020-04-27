---
title: "\"/UTF-8\" (Quelle und ausführbare Zeichensätze festlegen UTF-8auf)"
ms.date: 04/26/2020
f1_keywords:
- /utf-8
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
no-loc:
- UTF
- UTF-8
- UTF-16
ms.openlocfilehash: c98a30b0ec4b36b8bd87fb0956d9382751975cfd
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168864"
---
# <a name="utf-8-set-source-and-executable-character-sets-to-opno-locutf-8"></a>`/utf-8`(Legen Sie Quell-und ausführbare UTF-8Zeichensätze auf fest).

Gibt den Quell Zeichensatz und den Ausführungs Zeichensatz UTF-8als an.

## <a name="syntax"></a>Syntax

> **`/utf-8`**

## <a name="remarks"></a>Bemerkungen

Sie können die **`/utf-8`** -Option verwenden, um die Quell-und Ausführungs Zeichensätze als mit UTF-8codiert festzulegen. Dies entspricht der Angabe **`/source-charset:utf-8 /execution-charset:utf-8`** von in der Befehlszeile. Jede dieser Optionen aktiviert auch die **`/validate-charset`** Option standardmäßig. Eine Liste der unterstützten Codepage-IDs und Zeichensatz Namen finden Sie unter [Code Page Identifier](/windows/win32/Intl/code-page-identifiers).

Standardmäßig erkennt Visual Studio eine Byte Reihenfolge Markierung, um zu bestimmen, ob die Quelldatei in einem codierten Unicode-Format vorliegt UTF-16 , UTF-8z. b. oder. Wenn keine Byte Reihenfolge Markierung gefunden wird, wird davon ausgegangen, dass die Quelldatei mithilfe der aktuellen Benutzer Codepage codiert wird, es sei denn, Sie **`/utf-8`** haben mithilfe **`/source-charset`** der-Option oder der-Option eine Codepage angegeben. Visual Studio ermöglicht es Ihnen, den C++-Quellcode mit einer beliebigen Zahl von Zeichen Codierungen zu speichern. Weitere Informationen zu Quell-und Ausführungs Zeichensätzen finden Sie unter [Zeichensätze](../../cpp/character-sets.md) in der Sprachdokumentation.

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Festlegen der Option in Visual Studio oder Programm gesteuert

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften** > **C/C++** > -**Befehlszeile** aus.

1. Fügen Sie unter **zusätzliche Optionen**die **`/utf-8`** Option hinzu, um Ihre bevorzugte Codierung anzugeben.

1. Klicken Sie auf **OK**, um die Änderungen zu speichern.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Weitere Informationen:

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
["/Execution-charset" (Ausführungs Zeichensatz festlegen)](execution-charset-set-execution-character-set.md)<br/>
[/source-charset (Quellzeichensatz festlegen)](source-charset-set-source-character-set.md)<br/>
[/validate-charset (Auf kompatible Zeichen überprüfen)](validate-charset-validate-for-compatible-characters.md)

---
title: /Zp (Ausrichten des Strukturmembers)
ms.date: 04/04/2019
f1_keywords:
- /zp
- VC.Project.VCCLCompilerTool.StructMemberAlignment
- VC.Project.VCCLWCECompilerTool.StructMemberAlignment
helpviewer_keywords:
- Struct Member Alignment compiler option
- Zp compiler option
- /Zp compiler option [C++]
- -Zp compiler option [C++]
ms.assetid: 5242f656-ed9b-48a3-bc73-cfcf3ed2520f
ms.openlocfilehash: c78e670303bde68299725e18c6f588f5e410a971
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234301"
---
# <a name="zp-struct-member-alignment"></a>/Zp (Ausrichten des Strukturmembers)

Steuert, wie die Elemente einer Struktur in den Arbeitsspeicher gepackt werden, und gibt die gleiche Verpackung für alle Strukturen in einem Modul an.

## <a name="syntax"></a>Syntax

> **`/Zp`**[**`1`**|**`2`**|**`4`**|**`8`**|**`16`**]

## <a name="remarks"></a>Bemerkungen

Die- **`/ZpN`** Option weist den Compiler an, wo jedes Strukturmember gespeichert werden soll. Der Compiler speichert Member nach dem ersten an einer Grenze, die kleiner ist als die Größe des Elementtyps oder eine *N*-Byte-Grenze.

Die verfügbaren Verpackungs Werte werden in der folgenden Tabelle beschrieben:

|/ZP-Argument|Auswirkung|
|-|-|
|1|Packt Strukturen auf 1-Byte-Begrenzungen. Identisch mit **`/Zp`** .|
|2|Packt Strukturen an 2-Byte-Begrenzungen.|
|4|Packt Strukturen auf 4-Byte-Begrenzungen.|
|8|Packt Strukturen an 8-Byte-Begrenzungen (Standardwert für x86, Arm und ARM64).|
|16| Packt Strukturen auf 16-Byte-Grenzen (Standard für x64).|

Verwenden Sie diese Option nur, wenn Sie über bestimmte Ausrichtungs Anforderungen verfügen.

> [!WARNING]
> C++-Header in der Windows SDK festgelegt und sollten **`/Zp8`** intern verpackt werden. Arbeitsspeicher Beschädigung kann auftreten, wenn die **`/Zp`** Einstellung innerhalb der Windows SDK-Header geändert wird. Die Header sind nicht von einer Option betroffen, die **`/Zp`** Sie in der Befehlszeile festlegen.

Sie können auch verwenden [`pack`](../../preprocessor/pack.md) , um die Struktur Verpackung zu steuern. Weitere Informationen zur Ausrichtung finden Sie unter:

- [`align`](../../cpp/align-cpp.md)

- [`alignof`KOM](../../cpp/alignof-operator.md)

- [`__unaligned`](../../cpp/unaligned.md)

- [`/ALIGN`(Abschnitts Ausrichtung)](align-section-alignment.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Code Generierung** aus.

1. Ändern Sie die **Ausrichtungs Eigenschaft Strukturmember** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StructMemberAlignment%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md) \
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)

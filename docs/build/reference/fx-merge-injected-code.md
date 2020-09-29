---
title: /Fx (Eingefügten Code zusammenführen)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExpandAttributedSource
- /Fx
- VC.Project.VCCLCompilerTool.ExpandAttributedSource
helpviewer_keywords:
- Fx compiler option [C++]
- -Fx compiler option [C++]
- injected code
- merging injected code
- /Fx compiler option [C++]
ms.assetid: 14f0e301-3bab-45a3-bbdf-e7ce66f20560
ms.openlocfilehash: b928ca63171f0f6d28859d049a1ed5008b908686
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91500100"
---
# <a name="fx-merge-injected-code"></a>/Fx (Eingefügten Code zusammenführen)

Erzeugt eine Kopie jeder Quelldatei mit injiziertem Code, der in die Quelle eingefügt ist.

## <a name="syntax"></a>Syntax

```
/Fx
```

## <a name="remarks"></a>Bemerkungen

Damit eine zusammengeführte Quelldatei von einer unveränderten Quelldatei unterschieden werden kann, fügt **/Fx** die Erweiterung „.mrg“ zwischen dem Dateinamen und der Dateierweiterung ein. Eine Datei mit dem Namen „MeinCode.cpp“, die attribuierten Code enthält und mit **/Fx** erstellt wird, erzeugt eine Datei mit dem Namen „MyCode.mrg.cpp“, die den folgenden Code enthält:

```
//+++ Start Injected Code
[no_injected_text(true)];      // Suppress injected text, it has
                               // already been injected
#pragma warning(disable: 4543) // Suppress warnings about skipping
                               // injected text
#pragma warning(disable: 4199) // Suppress warnings from attribute
                               // providers
//--- End Injected Code
```

In einer MRG-Datei wird Code, der aufgrund eines Attributs injiziert wurde, wie folgt abgetrennt:

```
//+++ Start Injected Code
...
//--- End Injected Code
```

Das [no_injected_text](../../windows/attributes/no-injected-text.md) -Attribut wird in eine MRG-Datei eingebettet, was die Kompilierung der MRG-Datei ohne erneute Injizierung von Text ermöglicht.

Es sollte Ihnen bewusst sein, dass die MRG-Quelldatei als Darstellung des vom Compiler injizierten Quellcodes beabsichtigt ist. Die MRG-Datei lässt sich möglicherweise nicht genau wie die ursprüngliche Quelldatei kompilieren oder ausführen.

Makros werden in der MRG-Datei nicht erweitert.

Wenn Ihr Programm eine Headerdatei umfasst, die injizierten Code verwendet, erstellt **/Fx** eine „.mrg.h“-Datei für den betreffenden header. **/Fx** führt keine Includedateien zusammen, die keinen injizierten Code verwenden.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **C/C++** .

1. Klicken  Sie auf die Eigenschaftenseite **Ausgabedateien** .

1. Ändern Sie die **Expand Attributed Source** -Eigenschaft.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExpandAttributedSource%2A>.

## <a name="see-also"></a>Weitere Informationen

[Ausgabedatei Optionen (/F)](output-file-f-options.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)

---
title: /Za, /Ze (Spracherweiterungen deaktivieren)
ms.date: 02/19/2019
f1_keywords:
- VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions
- /za
- /ze
- VC.Project.VCCLCompilerTool.DisableLanguageExtensions
helpviewer_keywords:
- -Za compiler option [C++]
- Za compiler option [C++]
- language extensions, disabling in compiler
- -Ze compiler option [C++]
- language extensions
- enable language extensions
- /Za compiler option [C++]
- /Ze compiler option [C++]
- Disable Language Extensions compiler option
- Ze compiler option [C++]
ms.assetid: 65e49258-7161-4289-a176-7c5c0656b1a2
ms.openlocfilehash: 9a2584591f6ca22d6767a5c447ffb72bea0a78ea
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825874"
---
# <a name="za-ze-disable-language-extensions"></a>/Za, /Ze (Spracherweiterungen deaktivieren)

Mit der **/Za** -Compileroption werden Fehler für Microsoft-Erweiterungen für C deaktiviert und ausgegeben, die nicht mit ANSI C89/ISO C90 kompatibel sind. Die veraltet **/Ze** -Compileroption aktiviert Microsoft-Erweiterungen. Standardmäßig sind Microsoft-Erweiterungen aktiviert.

## <a name="syntax"></a>Syntax

> **/Za**\
> **/Ze**

## <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Die Verwendung von **/Za** , wenn Code als C++ kompiliert wird, wird nicht empfohlen. Die **/Ze** -Option ist veraltet, da ihr Verhalten standardmäßig aktiviert ist. Eine Liste der veralteten Compileroptionen finden Sie unter [veraltete und entfernte Compileroptionen](compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options).

Der Microsoft C/C++-Compiler unterstützt die Kompilierung von C-Code auf zwei Arten:

- Der Compiler verwendet standardmäßig den C-Kompilierungs Modus, wenn eine Quelldatei eine Erweiterung " *. C* " aufweist oder wenn die Option [/TC](tc-tp-tc-tp-specify-source-file-type.md) oder [/TC](tc-tp-tc-tp-specify-source-file-type.md) angegeben wird. Der c-Compiler ist ein C89/C90-Compiler, der standardmäßig Microsoft-Erweiterungen der Programmiersprache c ermöglicht. Weitere Informationen zu bestimmten Erweiterungen finden [Sie unter Microsoft-Erweiterungen für C und C++](microsoft-extensions-to-c-and-cpp.md). Wenn sowohl die c-Kompilierung als auch die **/Za** -Option angegeben werden, entspricht der c-Compiler strikt dem C89/C90-Standard. Der Compiler behandelt erweiterte Microsoft-Schlüsselwörter als einfache Identifizierer, deaktiviert die anderen Microsoft-Erweiterungen und definiert [ \_ \_\_ ](../../preprocessor/predefined-macros.md) automatisch das vordefinierte stdc-Makro für C-Programme.

- Der Compiler kann C-Code im C++-Kompilierungs Modus kompilieren. Dieses Verhalten ist die Standardeinstellung für Quelldateien, die nicht über die Erweiterung " *. c* " verfügen, und wenn die Option " [/tp](tc-tp-tc-tp-specify-source-file-type.md) " oder " [/tp](tc-tp-tc-tp-specify-source-file-type.md) " angegeben wird. Im Kompilierungs Modus C++ unterstützt der Compiler diese Teile der ISO C99-und C11-Standards, die in den C++-Standard integriert wurden. Fast sämtlicher C-Code ist auch gültiger C++-Code. Eine kleine Anzahl von C-Schlüsselwörtern und Codekonstrukten ist kein gültiger C++-Code oder wird in C++ anders interpretiert. Der Compiler verhält sich in diesen Fällen gemäß dem C++-Standard. Im C++-Kompilierungs Modus kann die **/Za** -Option unerwartetes Verhalten verursachen und wird nicht empfohlen.

Andere Compileroptionen können beeinflussen, wie der Compiler die Standardkonformität gewährleistet. Informationen zur Angabe spezifischer Standardeinstellungen für C und C++ finden Sie unter der [/Zc](zc-conformance.md) -Compileroption. Weitere C++-Standardeinstellungen für die Konformität finden Sie unter den Compileroptionen [/permissive-](permissive-standards-conformance.md) und [/Std](std-specify-language-standard-version.md) .

Weitere Informationen zu Konformitäts Problemen bei Visual C++ finden Sie unter [nicht dem Standard entsprechende Verhalten](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie im Navigationsbereich die Option **Konfigurations Eigenschaften** > **C/C++** > **Sprache**aus.

1. Ändern Sie die Eigenschaft **Spracherweiterungen deaktivieren** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>.

## <a name="see-also"></a>Weitere Informationen

[Compileroptionen](compiler-options.md)<br/>
[/Zc (Übereinstimmung)](zc-conformance.md)<br/>
[/permissive- (Übereinstimmung mit Standards)](permissive-standards-conformance.md)<br/>
[/Std (Standard Version der Sprache angeben)](std-specify-language-standard-version.md)<br/>

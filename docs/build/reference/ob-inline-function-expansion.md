---
title: /Ob (Inlinefunktionserweiterung)
ms.date: 08/08/2019
f1_keywords:
- VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion
- VC.Project.VCCLCompilerTool.InlineFunctionExpansion
- /ob
helpviewer_keywords:
- inline functions, function expansion compiler option [C++]
- -Ob1 compiler option [C++]
- -Ob0 compiler option [C++]
- /Ob0 compiler option [C++]
- /Ob1 compiler option [C++]
- any suitable compiler option [C++]
- Ob2 compiler option [C++]
- Ob1 compiler option [C++]
- /Ob2 compiler option [C++]
- Ob compiler option [C++]
- -Ob2 compiler option [C++]
- disable compiler option [C++]
- -Ob compiler option [C++]
- /Ob compiler option [C++]
- only __inline compiler option [C++]
- Ob0 compiler option [C++]
- inline expansion, compiler option
ms.assetid: f134e6df-e939-4980-a01d-47425dbc562a
ms.openlocfilehash: 238e5533c062678c59b61ebeba71eee3231fb5fb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215217"
---
# <a name="ob-inline-function-expansion"></a>/Ob (Inlinefunktionserweiterung)

Steuert die Inlineerweiterung von Funktionen. Standardmäßig erfolgt die Erweiterung bei der Optimierung bei allen Funktionen, die häufig als *Automatische Inlining*bezeichnet werden, nach dem Ermessen des Compilers.

## <a name="syntax"></a>Syntax

::: moniker range=">=vs-2019"

> **/Ob**{**0** | **1** | **2** | **3**}

::: moniker-end

::: moniker range="<=vs-2017"

> **/Ob**{**0** | **1** | **2**}

::: moniker-end

## <a name="arguments"></a>Argumente

**1,0**\
Der Standardwert unter [/od](od-disable-debug.md). Deaktiviert Inline-Erweiterungen.

**1**\
Ermöglicht nur die Erweiterung von Funktionen, die als [Inline](../../cpp/inline-functions-cpp.md), [__inline](../../cpp/inline-functions-cpp.md)oder [__forceinline](../../cpp/inline-functions-cpp.md)gekennzeichnet sind, oder in einer C++ Member-Funktion, die in einer Klassen Deklaration definiert ist.

**2**\
Der Standardwert unter [/O1](o1-o2-minimize-size-maximize-speed.md) und [/O2](o1-o2-minimize-size-maximize-speed.md). Ermöglicht dem Compiler, jede Funktion zu erweitern, die nicht explizit für das Inlining markiert ist.

::: moniker range=">=vs-2019"

**€**\
Diese Option gibt einen aggressiveren Inlining als **/Ob2**an, hat jedoch dieselben Einschränkungen. Die **/Ob3** -Option ist ab Visual Studio 2019 verfügbar.

::: moniker-end

## <a name="remarks"></a>Bemerkungen

Der Compiler behandelt die Inlineerweiterungsoptionen und -Schlüsselwörter als Vorschläge. Es gibt keine Garantie dafür, dass eine Funktion Inline erweitert wird. Sie können Inline Erweiterungen deaktivieren, aber Sie können den Compiler nicht zwingen, eine bestimmte Funktion Inline zu verwenden, selbst wenn Sie das- **`__forceinline`** Schlüsselwort verwenden.

Sie können [__declspec (noinline)](../../cpp/noinline.md)oder eine Region verwenden, die von #pragma auto_inline-Direktiven ( [Off)](../../preprocessor/auto-inline.md) und [#pragma auto_inline (on)](../../preprocessor/auto-inline.md) -Direktiven gekennzeichnet ist, um Funktionen von der Überlegung als Kandidaten für die Inline Erweiterung auszuschließen. Informationen zu einer anderen Möglichkeit zum Bereitstellen von Inlining-Hinweisen für den Compiler finden Sie in der [#pragma intrinsischen](../../preprocessor/intrinsic.md) Direktive.

> [!NOTE]
> Informationen, die bei der Profilerstellung für Testläufe gesammelt werden, überschreiben Optimierungen, die andernfalls wirksam wären, weil Sie **/ob**, **/OS**oder **/OT**angegeben haben. Weitere Informationen finden Sie unter [Profilgesteuerte Optimierungen](../profile-guided-optimizations.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Optimierung** aus.

1. Ändern Sie die Eigenschaft **Inline Funktionserweiterung** .

::: moniker range=">=vs-2019"

Die **/Ob3** -Option ist in der Eigenschaft " **Inline Funktionserweiterung** " nicht verfügbar. So legen Sie **/Ob3**fest:

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf der Eigenschaftenseite auf **Konfigurationseigenschaften** > **C/C++** > **Befehlszeile**.

1. Geben Sie **/Ob3** in **zusätzliche Optionen**ein.

::: moniker-end

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>.

## <a name="see-also"></a>Weitere Informationen

[/O-Optionen (Code optimieren)](o-options-optimize-code.md)\
[MSVC-Compileroptionen](compiler-options.md)\
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)

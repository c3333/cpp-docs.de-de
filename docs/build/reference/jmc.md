---
title: /JMC (Debuggen von „Nur eigenen Code“)
ms.date: 08/20/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SupportJustMyCode
helpviewer_keywords:
- /JMC compiler option [C++]
- Just my code [C++]
- -JMC compiler option [C++]
- User code, debugging
- JMC compiler option [C++]
ms.openlocfilehash: 7b22a754f9f49564cd7f76c7d1989cd562f70874
ms.sourcegitcommit: 31a443c9998cf5cfbaff00fcf815b133f55b2426
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86373878"
---
# <a name="jmc-just-my-code-debugging"></a>/JMC (Debuggen von „Nur eigenen Code“)

Gibt die Compilerunterstützung für System eigenes *nur eigenen Code* Debuggen im Visual Studio-Debugger an. Diese Option unterstützt die Benutzereinstellungen, mit denen Visual Studio System-, Framework-, Bibliotheks-und andere Nichtbenutzer Aufrufe überspringen und diese Aufrufe im Aufruf Stapelfenster reduzieren kann. Die **/JMC** -Compileroption ist ab Visual Studio 2017, Version 15,8, verfügbar.

## <a name="syntax"></a>Syntax

> **/JMC** \[ **-** ]

## <a name="remarks"></a>Hinweise

Die Visual Studio- [nur eigenen Code](/visualstudio/debugger/just-my-code) Einstellungen geben an, ob der Visual Studio-Debugger System-, Framework-, Bibliotheks-und andere Nichtbenutzer Aufrufe überschreitet. Die **/JMC** -Compileroption ermöglicht die Unterstützung für das nur eigenen Code Debuggen im systemeigenen C++-Code Wenn **/JMC** aktiviert ist, fügt der Compiler Aufrufe an eine Hilfsfunktion, `__CheckForDebuggerJustMyCode` , in den Prolog der Funktion ein. Die Hilfsfunktion bietet Hooks, die Visual Studio-Debugger-nur eigenen Code Schritt Vorgänge unterstützen. Wenn Sie nur eigenen Code im Visual Studio-Debugger **aktivieren möchten, wählen Sie**in der Menüleiste Extras  >  **Optionen**aus, und legen Sie dann die Option in allgemeine **Debuggen**  >  **General**  >  **aktivieren nur eigenen Code**fest.

Die **/JMC** -Option erfordert, dass Ihr Code mit der C-Lauf Zeit Bibliothek (CRT) verknüpft ist, die die- `__CheckForDebuggerJustMyCode` Hilfsfunktion bereitstellt. Wenn Ihr Projekt nicht mit der CRT verknüpft ist, wird möglicherweise Linker Error **LNK2019: nicht aufgelöstes externes Symbol __CheckForDebuggerJustMyCode**angezeigt. Um diesen Fehler zu beheben, verknüpfen Sie entweder mit der CRT, oder deaktivieren Sie die Option **/JMC** .

Standardmäßig ist die **/JMC** -Compileroption deaktiviert. Ab Visual Studio 2017 Version 15,8 ist diese Option jedoch in den meisten Visual Studio-Projektvorlagen aktiviert. Um diese Option explizit zu deaktivieren, verwenden Sie die **/JMC-** -Option in der Befehlszeile. Öffnen Sie in Visual Studio das Dialogfeld Eigenschaften Seiten des Projekts, und ändern Sie die Eigenschaft **Unterstützung nur eigenen Code Debuggen** auf der **Eigenschaften**  >  Seite Eigenschaften von**C/C++**  >  **Allgemein** auf **Nein**.

Weitere Informationen finden Sie unter [C++ nur eigenen Code](/visualstudio/debugger/just-my-code#BKMK_C___Just_My_Code) in [angeben, ob nur Benutzer Code mit nur eigenen Code in Visual Studio debuggt werden soll](/visualstudio/debugger/just-my-code), und im Visual C++ Team-Blog Beitrag [ankündigen von C++ nur eigenen Code Schritt in Visual Studio](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Navigieren Sie zur Eigenschaftenseite **Konfigurationseigenschaften** > **C/C++**  > **Allgemein**.

1. Ändern Sie die Eigenschaft **Unterstützung nur eigenen Code Debuggen** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)<br/>

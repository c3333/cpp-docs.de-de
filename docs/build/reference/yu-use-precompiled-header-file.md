---
title: /Yu (Vorkompilierte Headerdatei verwenden)
ms.date: 07/31/2020
f1_keywords:
- /Yu
helpviewer_keywords:
- Yu compiler option [C++]
- /Yu compiler option [C++]
- -Yu compiler option [C++]
- PCH files, use existing
- .pch files, use existing
- precompiled header files, use existing
ms.assetid: 24f1bd0e-b624-4296-a17e-d4b53e374e1f
ms.openlocfilehash: 8cccce39949f23e4ceb72807ecaef3597ab733c4
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520461"
---
# <a name="yu-use-precompiled-header-file"></a>`/Yu`(Vorkompilierte Header Datei verwenden)

Weist den Compiler an, eine vorhandene vorkompilierte Header *`.pch`* Datei () in der aktuellen Kompilierung zu verwenden.

## <a name="syntax"></a>Syntax

> **`/Yu`**\[*Dateiname*]

## <a name="arguments"></a>Argumente

*filename*<br/>
Der Name einer Header Datei, die in der Quelldatei mit einer `#include` Präprozessordirektive enthalten ist.

## <a name="remarks"></a>Bemerkungen

Der Name der Includedatei muss für die **`/Yc`** Option, mit der der vorkompilierte Header erstellt wird, und für jede spätere **`/Yu`** Option, die die Verwendung des vorkompilierten Headers angibt, identisch sein.

Für **`/Yc`** gibt *filename* den Punkt an, an dem die Vorkompilierung beendet wird. der Compiler kompiliert den gesamten Code mit dem *Datei* Namen und benennt den resultierenden vorkompilierten Header mithilfe des Basis namens der Includedatei und einer Erweiterung von *`.pch`* .

Die *`.pch`* Datei muss mithilfe von erstellt worden sein **`/Yc`** .

Der Compiler behandelt den gesamten Code, der vor der h-Datei als vorkompiliert auftritt. Sie überspringt direkt hinter der- `#include` Direktive, die der *`.h`* Datei zugeordnet ist, verwendet den in der Datei enthaltenen Code *`.pch`* und kompiliert dann den gesamten Code nach dem *Dateinamen*.

In der Befehlszeile ist zwischen und filename kein Leerzeichen zulässig **`/Yu`** . *filename*

Wenn Sie die **`/Yu`** Option ohne einen Dateinamen angeben, muss das Quell Programm ein [`#pragma hdrstop`](../../preprocessor/hdrstop.md) pragma enthalten, das den Dateinamen des vorkompilierten Headers, der Datei, angibt *`.pch`* . In diesem Fall verwendet der Compiler den vorkompilierten Header ( *`.pch`* Datei) mit dem Namen [`/Fp (Name .pch file)`](fp-name-dot-pch-file.md) . Der Compiler überspringt den Speicherort dieses Pragmas und stellt den kompilierten Zustand aus der angegebenen vorkompilierten Header Datei wieder her. Anschließend wird nur der Code kompiliert, der auf das Pragma folgt. Wenn `#pragma hdrstop` keinen Dateinamen angibt, sucht der Compiler nach einer Datei mit einem Namen, der vom Basisnamen der Quelldatei mit einer Erweiterung abgeleitet ist *`.pch`* . Sie können auch die **`/Fp`** Option verwenden, um eine andere *`.pch`* Datei anzugeben.

Wenn Sie die **`/Yu`** Option ohne einen Dateinamen angeben und ein `hdrstop` pragma nicht angeben, wird eine Fehlermeldung generiert, und die Kompilierung ist nicht erfolgreich.

Wenn die **`/Yc`** _Datei_ Namen-und **`/Yu`** _Datei_ Namen Optionen in derselben Befehlszeile auftreten und beide auf denselben Dateinamen verweisen, hat der **`/Yc`** _Dateiname_ Vorrang, wobei der gesamte Code bis einschließlich der benannten Datei vorkompiliert wird. Diese Funktion vereinfacht das Schreiben von Makefiles.

Da *`.pch`* Dateien Informationen über die Computerumgebung und Informationen zur Speicheradresse des Programms enthalten, sollten Sie nur eine *`.pch`* Datei auf dem Computer verwenden, auf dem Sie erstellt wurde.

Weitere Informationen zu vorkompilierten Headern finden Sie unter:

- [`/Y`(Vorkompilierte Header)](y-precompiled-headers.md)

- [Vorkompilierte Headerdateien](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Geben Sie [ `/Yc` (Vorkompilierte Header Datei erstellen)](yc-create-precompiled-header-file.md) für eine CPP-Datei in Ihrem Projekt an.

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++**  >  **Vorkompilierte Header** aus.

1. Ändern Sie die Eigenschaft " **Vorkompilierte Header** ", die Eigenschaft " **PCH durch Datei erstellen/verwenden** " oder die Eigenschaft " **vorkompilierten Header erstellen/verwenden** ".

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> und <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.

## <a name="example"></a>Beispiel

Wenn der folgende Code:

```cpp
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
...
```

wird mithilfe der Befehlszeile kompiliert `CL /YuMYAPP.H PROG.CPP` , der Compiler verarbeitet die drei include-Anweisungen nicht. Stattdessen wird der vorkompilierte Code aus verwendet *`MYAPP.pch`* , wodurch die Zeit gespart wird, die bei der Vorverarbeitung aller drei Dateien (und sämtlicher Dateien, die Sie einschließen können) beteiligt ist.

Sie können die- [`/Fp (Name .pch file)`](fp-name-dot-pch-file.md) Option mit der-Option verwenden, **`/Yu`** um den Namen der *`.pch`* Datei anzugeben, wenn sich der Name von dem *filename* -Argument **`/Yc`** oder dem Basisnamen der Quelldatei unterscheidet, wie im folgenden Beispiel gezeigt:

```cmd
CL /YuMYAPP.H /FpMYPCH.pch PROG.CPP
```

Dieser Befehl gibt eine vorkompilierte Header Datei mit dem Namen an *`MYPCH.pch`* . Der Compiler verwendet seinen Inhalt, um den vorkompilierten Status aller Header Dateien bis zu und einschließlich wiederherzustellen *`MYAPP.h`* . Der Compiler kompiliert dann den Code, der nach der `#include "MYAPP.h"` *-Direktive auftritt.

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)

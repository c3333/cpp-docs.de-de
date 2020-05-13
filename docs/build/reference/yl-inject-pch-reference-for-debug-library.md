---
title: /Yl (PCH-Verweis für Debugbibliothek einfügen)
ms.date: 01/29/2018
f1_keywords:
- /yl
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
ms.openlocfilehash: 816ba66c94e616407a8891cd149a41e44e29358d
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825716"
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (PCH-Verweis für Debugbibliothek einfügen)

Mit der **/Yl** -Option wird ein eindeutiges Symbol in einer vorkompilierten Header Datei generiert, und ein Verweis auf dieses Symbol wird in alle Objektdateien eingefügt, die den vorkompilierten Header verwenden.

## <a name="syntax"></a>Syntax

>**/Yl**\
>**/Yl**_name_\
>**/Yl-Option wird**

### <a name="arguments"></a>Argumente

*name*<br/>
Ein optionaler Name, der als Teil des eindeutigen Symbols verwendet wird.

*\-*<br/>
Ein Bindestrich (-) deaktiviert die **/Yl** -Compileroption explizit.

## <a name="remarks"></a>Bemerkungen

Die **/Yl** -Compileroption erstellt eine eindeutige Symbol Definition in einer vorkompilierten Header Datei, die mithilfe der [/Yc](yc-create-precompiled-header-file.md) -Option erstellt wurde. Verweise auf dieses Symbol werden automatisch in alle Dateien eingefügt, die den vorkompilierten Header mit der [/Yu](yu-use-precompiled-header-file.md) -Compileroption enthalten. Die **/Yl** -Option ist standardmäßig aktiviert, wenn **/Yc** zum Erstellen einer vorkompilierten Header Datei verwendet wird.

Die Option **/Yl**_Name_ wird verwendet, um ein identifizierbares Symbol in der vorkompilierten Header Datei zu erstellen. Der Compiler verwendet das Argument *Name* als Teil des ergänzten Symbol namens, das er erstellt, `__@@_PchSym_@00@...@name`ähnlich wie, wobei die Auslassungs Zeichen (...) eine eindeutige vom Compiler generierte Zeichenfolge darstellen. Wenn das *Name* -Argument weggelassen wird, generiert der Compiler automatisch einen Symbolnamen. Normalerweise müssen Sie den Namen des Symbols nicht kennen. Wenn das Projekt jedoch mehr als eine vorkompilierte Header Datei verwendet, kann die Option **/Yl**_Name_ nützlich sein, um zu bestimmen, welche Objektdateien den vorkompilierten Header verwenden. Sie können *Name* als Such Zeichenfolge verwenden, um den Symbol Verweis in einer Dumpdatei zu suchen.

**/Yl-Option wird** deaktiviert das Standardverhalten und legt in der vorkompilierten Header Datei kein identifizierendes Symbol ab. Kompilierte Dateien, die diesen vorkompilierten Header enthalten, erhalten keinen allgemeinen Symbol Verweis.

Wenn **/Yc** nicht angegeben ist, hat jede **/Yl** -Option keine Auswirkung, aber wenn angegeben, muss Sie mit jeder **/Yl** -Option verglichen werden, die bei Angabe von **/Yc** erfolgreich ist.

Wenn Sie die Optionen **/Yl-Option wird**, **/Yc** und [/Z7](z7-zi-zi-debug-information-format.md) zum Erstellen einer vorkompilierten Header Datei verwenden, werden die Debuginformationen in der Objektdatei für die Quelldatei gespeichert, die zum Erstellen des vorkompilierten Headers verwendet wird, anstelle einer separaten PDB-Datei. Wenn diese Objektdatei dann Teil einer Bibliothek wird, können [Linkertoolfehler LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md) -Fehler oder [Linkertoolwarnung Lnk4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md) -Warnungen in Builds auftreten, die diese Bibliothek und die vorkompilierte Header Datei verwenden, wenn die Quelldatei, die zum Erstellen der vorkompilierten Header Datei verwendet wurde, keine Symbole selbst definiert. Der Linker kann die Objektdatei zusammen mit den zugehörigen Debuginformationen aus dem Link ausschließen, wenn im Bibliothek Client auf nichts in der Objektdatei verwiesen wird. Um dieses Problem zu beheben, geben Sie **/Yl** (oder entfernen Sie die **/Yl-Option wird** -Option) an, wenn Sie **/Yc** zum Erstellen der vorkompilierten Header Datei verwenden. Dadurch wird sichergestellt, dass die Objektdatei aus der Bibliothek, die die Debuginformationen enthält, im Build verknüpft wird.

Weitere Informationen zu vorkompilierten Headern finden Sie unter:

- [/Y (Vorkompilierte Header)](y-precompiled-headers.md)

- [Vorkompilierte Header Dateien](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften** > **C/C++** > -**Befehlszeile** aus.

1. Fügen Sie die **/Yl**_Name_ -Compileroption im Feld **zusätzliche Optionen** hinzu. Klicken Sie auf **OK**, um die Änderungen zu speichern.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)

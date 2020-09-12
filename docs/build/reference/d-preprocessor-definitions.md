---
title: /D (Präprozessordefinitionen)
ms.date: 09/18/2019
f1_keywords:
- VC.Project.VCNMakeTool.PreprocessorDefinitions
- VC.Project.VCCLCompilerTool.PreprocessorDefinitions
- /d
helpviewer_keywords:
- preprocessor definition symbols
- constants, defining
- macros, compiling
- /D compiler option [C++]
- -D compiler option [C++]
- D compiler option [C++]
ms.assetid: b53fdda7-8da1-474f-8811-ba7cdcc66dba
ms.openlocfilehash: 7c8a500820c8cc4655c409f4628d72a69acafa5a
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040937"
---
# <a name="d-preprocessor-definitions"></a>/D (Präprozessordefinitionen)

Definiert ein Vorverarbeitungssymbol für eine Quelldatei.

## <a name="syntax"></a>Syntax

> **/D** \[ ]_Name_ \[ `=` \| `#` \[ { *String* \| *Number* }]] \
> **/D** \[ ] `"` _Name_ \[ `=` \| `#` \[ { *String* \| *Number* }]]`"`

## <a name="remarks"></a>Bemerkungen

Sie können dieses Symbol mit `#if` oder `#ifdef` zur bedingten Kompilierung von Quellcode verwenden. Die Symbol Definition bleibt wirksam, bis Sie im Code neu definiert wird oder im Code durch eine-Direktive nicht definiert ist `#undef` .

**/D** hat denselben Effekt wie eine `#define` Direktive am Anfang einer Quell Code Datei. Der Unterschied besteht darin, dass **/D** Anführungszeichen in der Befehlszeile entfernt und eine- `#define` Direktive Sie beibehält. Zwischen dem **/D** und dem Symbol können Leerzeichen stehen. Es dürfen keine Leerzeichen zwischen dem Symbol und dem Gleichheitszeichen oder zwischen dem Gleichheitszeichen und einem zugewiesenen Wert vorhanden sein.

Standardmäßig wird einem Symbol der Wert 1 zugeordnet. `/D name` entspricht beispielsweise `/D name=1`. Im Beispiel am Ende dieses Artikels wird die Definition von `TEST` gedruckt `1` .

Das Kompilieren mithilfe von `/D name=` bewirkt, dass der Symbol *Name* keinen zugeordneten Wert hat. Obwohl das Symbol trotzdem zur bedingten Codekompilierung verwendet werden kann, ergibt das Symbol keinen Wert. Wenn Sie in diesem Beispiel mithilfe von kompilieren `/DTEST=` , tritt ein Fehler auf. Dieses Verhalten ähnelt der Verwendung von `#define` mit oder ohne Wert.

Die **/D** -Option unterstützt keine Funktions ähnlichen Makro Definitionen. Wenn Sie Definitionen einfügen möchten, die nicht in der Befehlszeile definiert werden können, berücksichtigen Sie die Compileroption [/fi (Name erzwungene Includedatei)](fi-name-forced-include-file.md) .

Sie können **/D** mehrmals in der Befehlszeile verwenden, um zusätzliche Symbole zu definieren. Wenn das gleiche Symbol mehrmals definiert ist, wird die letzte Definition verwendet.

Dieser Befehl definiert das DEBUG-Symbol in TEST.C:

```cmd
CL /DDEBUG TEST.C
```

Mit dem folgenden Befehl werden alle Vorkommen des Schlüsselworts `__far` aus TEST.C entfernt.

```cmd
CL /D __far= TEST.C
```

Die **cl** -Umgebungsvariable kann nicht auf eine Zeichenfolge festgelegt werden, die das Gleichheitszeichen enthält. Wenn Sie **/D** in Verbindung mit der **cl** -Umgebungsvariablen verwenden möchten, müssen Sie das Nummern Zeichen ( `#` ) anstelle des Gleichheitszeichens angeben:

```cmd
SET CL=/DTEST#0
```

Wenn Sie ein Vorverarbeitungssymbol an der Eingabeaufforderung definieren, sollten Sie Compileranalyseregeln sowie Shell-Analyseregeln berücksichtigen. Wenn Sie z. b. ein Vorverarbeitungs Symbol für das Prozentzeichen ( `%` ) in Ihrem Programm definieren möchten, geben Sie `%%` an der Eingabeaufforderung zwei Prozentzeichen () an. Wenn Sie nur eine Angabe angeben, wird ein Fehler bei der Verarbeitung ausgegeben.

```cmd
CL /DTEST=%% TEST.C
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie im linken Bereich **Konfigurations Eigenschaften**, **C/C++**, **Präprozessor**aus.

1. Öffnen Sie im rechten Bereich in der rechten Spalte der Eigenschaft **Präprozessordefinitionen** das Dropdown Menü, und wählen Sie **Bearbeiten**aus.

1. Fügen Sie im Dialogfeld **Präprozessordefinitionen** (eine pro Zeile) ein, ändern oder löschen Sie eine oder mehrere Definitionen. Klicken Sie auf **OK**, um die Änderungen zu speichern.

   Sie müssen das Optionen Präfix "/D" nicht für die hier angegebenen Definitionen einschließen. Auf der Eigenschaften Seite werden Definitionen durch Semikolons () getrennt `;` .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PreprocessorDefinitions%2A>.

## <a name="example"></a>Beispiel

```cpp
// cpp_D_compiler_option.cpp
// compile with: cl /EHsc /DTEST cpp_D_compiler_option.cpp
#include <stdio.h>

int main( )
{
#ifdef TEST
    printf_s("TEST defined %d\n", TEST);
#else
    printf_s("TEST not defined\n");
#endif
}
```

```Output
TEST defined 1
```

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)\
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)\
[/FI (Name erzwungene Includedatei)](fi-name-forced-include-file.md)\
[/U,/U (Symbole aufheben)](u-u-undefine-symbols.md)\
[#undef-Direktive (C/C++)](../../preprocessor/hash-undef-directive-c-cpp.md)\
[#define-Direktive (C/C++)](../../preprocessor/hash-define-directive-c-cpp.md)

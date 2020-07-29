---
title: /H (Länge externer Namen beschränken)
ms.date: 09/05/2018
f1_keywords:
- /h
helpviewer_keywords:
- public name length
- /H compiler option [C++]
- H compiler option [C++]
- external names
- -H compiler option [C++]
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
ms.openlocfilehash: 9a8976700cfb0f333c2715c573aa2d239e2a8e3a
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218987"
---
# <a name="h-restrict-length-of-external-names"></a>/H (Länge externer Namen beschränken)

Veraltet. Schränkt die Länge externer Namen ein.

## <a name="syntax"></a>Syntax

> **/H**-<em>Nummer</em>

## <a name="arguments"></a>Argumente

*Zahl*<br/>
Gibt die maximale Länge externer Namen an, die in einem Programm zulässig sind.

## <a name="remarks"></a>Bemerkungen

Standardmäßig ist die Länge externer (öffentlicher) Namen 2.047 Zeichen. Dies gilt für C-und C++-Programme. Die Verwendung von **/H** kann nur die maximal zulässige Länge von bezeichatoren verringern und diese nicht erhöhen. Ein Leerzeichen zwischen **/H** und *Number* ist optional.

Wenn ein Programm externe Namen enthält, die länger als die *Zahl*sind, werden die zusätzlichen Zeichen ignoriert. Wenn Sie ein Programm ohne **/H** kompilieren und ein Bezeichner mehr als 2.047 Zeichen enthält, generiert der Compiler einen schwerwiegenden [Fehler C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md).

Der Grenzwert für die Länge schließt alle vom Compiler erstellten führenden Unterstriche ( **\_** ) oder das Zeichen ( **\@** ) ein. Diese Zeichen sind Teil des Bezeichners und nehmen einen signifikanten Speicherort an.

- Der Compiler fügt den Namen, die **\_** von den (standardmäßigen) und den Aufruf Konventionen geändert werden, einen führenden Unterstrich () und **`__cdecl`** **`__stdcall`** ein vorangeführtes Zeichen ( **\@** ) an Namen, die durch die **`__fastcall`** Aufruf Konvention geändert werden

- Der Compiler fügt Argument Größen Informationen an Namen an, die durch die **`__fastcall`** -und- **`__stdcall`** Aufruf Konventionen geändert werden, und fügt Typinformationen zu C++-Namen hinzu.

Möglicherweise finden Sie **/H** nützlich:

- Wenn Sie gemischte oder portable Programme erstellen.

- Wenn Sie Tools verwenden, die die Länge externer Bezeichner einschränken.

- Wenn Sie den Speicherplatz einschränken möchten, den Symbole in einem Debugbuild verwenden.

Das folgende Beispiel zeigt, wie die Verwendung von **/H** tatsächlich Fehler verursachen kann, wenn Bezeichnerlängen zu stark eingeschränkt sind:

```cpp
// compiler_option_H.cpp
// compile with: /H5
// processor: x86
// LNK2005 expected
void func1(void);
void func2(void);

int main() { func1(); }

void func1(void) {}
void func2(void) {}
```

Sie müssen auch bei Verwendung der **/H** -Option bei Verwendung der vordefinierten Compilerbezeichner Vorsicht walten lassen. Wenn die maximale Bezeichnerlänge zu klein ist, werden bestimmte vordefinierte Bezeichner ebenso wie bestimmte Bibliotheks Funktionsaufrufe nicht aufgelöst. Wenn beispielsweise die `printf` -Funktion verwendet wird und die Option **/H5** zur Kompilierzeit angegeben wird, wird das Symbol **_prin** erstellt, um darauf zu verweisen `printf` , und dieses wird in der Bibliothek nicht gefunden.

Die Verwendung von **/H** ist mit [/GL (Optimierung des gesamten Programms)](gl-whole-program-optimization.md)nicht kompatibel.

Die **/H** -Option ist seit Visual Studio 2005 veraltet. die maximalen Längen Limits wurden angehoben, und **/H** wird nicht mehr benötigt. Eine Liste der veralteten Compileroptionen finden Sie unter **veraltete und entfernte Compileroptionen** in [Compileroptionen nach Kategorien sortiert](compiler-options-listed-by-category.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Befehlszeile** aus.

1. Geben Sie die Compileroption im Feld **zusätzliche Optionen** ein.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)

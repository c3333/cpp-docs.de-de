---
title: /QIfist (_ftol unterdrücken)
ms.date: 11/04/2016
f1_keywords:
- /qifist
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
ms.openlocfilehash: 5d6e12a1003ea125b0da4bfef580d8096e97553a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336103"
---
# <a name="qifist-suppress-_ftol"></a>/QIfist (_ftol unterdrücken)

Veraltet. Unterdrückt den Aufruf der `_ftol` -Hilfsfunktion, wenn eine Konvertierung von einem Gleitkommatyp zu einem ganzzahligen Typ erforderlich ist.

## <a name="syntax"></a>Syntax

```
/QIfist
```

## <a name="remarks"></a>Bemerkungen

> [!NOTE]
> **/QIfist** ist nur im Compiler für x86 verfügbar. Diese Compileroption ist in den Compilern für x64 oder ARM nicht verfügbar.

Durch die `_ftol`-Funktion wird nicht nur ein Gleitkommatyp in einen ganzzahligen Typ konvertiert, sondern ist auch gewährleistet, dass die Gleitkommaeinheit (Floating-Point Unit, FPU) gegen 0 (null) rundet (abschneidet), indem die Bits 10 und 11 des Steuerworts entsprechend festgelegt werden. Dadurch wird garantiert, dass die Konvertierung eines Gleitkommatyps in einen ganzzahligen Typ wie im ANSI C-Standard durchgeführt wird, dass also der Teil nach dem Komma verworfen wird. Bei Verwendung von **/QIfist**gilt diese Garantie nicht mehr. Das Rundungsverhalten entspricht einem der vier im Intel-Referenzmaterial dokumentierten Modi:

- Runden auf die nächste Maschinenzahl (auf eine gerade Zahl bei gleichem Abstand)

- Runden in Richtung minus unendlich

- Runden in Richtung plus unendlich

- Runden in Richtung Null (0)

Sie können die [_control87, \__controlfp _control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) C-Run-Time-Funktion verwenden, um das Rundungsverhalten der FPU zu ändern. Die Standardeinstellung der FPU ist "Runden auf die nächste Maschinenzahl". Die Verwendung von **/QIfist** kann die Leistung Ihrer Anwendung verbessern, jedoch nicht ohne Risiko. Sie sollten die Teile des Codes, die für Rundungsmodi empfindlich sind, gründlich testen, bevor Sie sich auf Code verlassen, der mit **/QIfist** in Produktionsumgebungen erstellt wurde.

[/arch (x86)](arch-x86.md) und **/QIfist** können nicht auf demselben Kompiland verwendet werden.

> [!NOTE]
> **/QIfist** ist standardmäßig nicht in Kraft, da sich die Rundungsbits auch auf die Gleitkommarundung auswirken (was nach jeder Berechnung geschieht), sodass die Gleitkommaberechnungen unterschiedlich sein können, wenn Sie die Flags für die Rundung im C-Stil (in Richtung Null) festlegen. **/QIfist** sollte nicht verwendet werden, wenn ihr Code vom erwarteten Verhalten beim Abrunden des Bruchteils der Gleitkommazahl abhängt. Wenn Sie sich nicht sicher sind, verwenden Sie **/QIfist**nicht .

Die Option **/QIfist** ist ab Visual Studio 2005 veraltet. Für den Compiler wurde die Geschwindigkeit der Konvertierung von Gleitkommatyp in ganzzahligen Typ deutlich erhöht. Eine Liste veralteter Compileroptionen finden Sie unter **Veraltete und Entfernte Compileroptionen** in [Compileroptionen, die nach Kategorie aufgelistet](compiler-options-listed-by-category.md)sind.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **C/C++** .

1. Klicken Sie auf die Eigenschaftenseite **Befehlszeile** .

1. Geben Sie die Compileroption im Feld **Zusätzliche Optionen** ein.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Siehe auch

[/Q-Optionen (Vorgänge auf niedriger Ebene)](q-options-low-level-operations.md)<br/>
[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)

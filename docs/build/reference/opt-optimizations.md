---
title: /OPT (Optimierungen)
ms.date: 05/18/2018
f1_keywords:
- VC.Project.VCLinkerTool.OptimizeReferences
- /opt
- VC.Project.VCLinkerTool.OptimizeForWindows98
- VC.Project.VCLinkerTool.EnableCOMDATFolding
- VC.Project.VCLinkerTool.OptimizeFolding
- VC.Project.VCLinkerTool.FoldingIterations
- VC.Project.VCLinkerTool.OptimizeFoldingIterations
helpviewer_keywords:
- LINK tool [C++], controlling optimizations
- -OPT linker option
- linker [C++], optimizations
- OPT linker option
- optimization, linker
- /OPT linker option
ms.assetid: 8f229863-5f53-48a8-9478-243a647093ac
ms.openlocfilehash: b25db4d6c260c3c6751de293aa2a82df8aa05e7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336221"
---
# <a name="opt-optimizations"></a>/OPT (Optimierungen)

Steuert die Optimierungen, die während eines Builds von LINK ausgeführt werden.

## <a name="syntax"></a>Syntax

> **/OPT:**.**. .** | . . . . . . . . . . . .**.**. . . . . . .<br/>
> **/OPT:****ICF****=**[_Iterationen_] | **NOICF**<br/>
> **/OPT:****LBR** | **NOLBR**

## <a name="arguments"></a>Argumente

**REF** &#124; **NOREF**

**/OPT:REF** eliminiert Funktionen und Daten, auf die nie verwiesen wird; **/OPT:NOREF** speichert Funktionen und Daten, auf die nie verwiesen wird.

Wenn /OPT:REF aktiviert ist, entfernt LINK nicht referenzierte verpackte Funktionen und Daten, die als *COMDATs*bezeichnet werden. Diese Optimierung ist als transitive COMDAT-Eliminierung bekannt. Die Option **/OPT:REF** deaktiviert auch die inkrementelle Verknüpfung.

Inline-Funktionen und Memberfunktionen, die in einer Klassendeklaration definiert sind, sind immer COMDATs. Alle Funktionen in einer Objektdatei werden in COMDATs umgewandelt, wenn sie mit der Option [/Gy](gy-enable-function-level-linking.md) kompiliert werden. Um **const-Daten** in COMDATs zu platzieren, müssen Sie sie mithilfe `__declspec(selectany)`von deklarieren. Informationen zum Angeben von Daten zum Entfernen oder Falten finden Sie unter [selectany](../../cpp/selectany.md).

Standardmäßig wird **/OPT:REF** durch den Linker aktiviert, es sei **denn, /OPT:NOREF** oder [/DEBUG](debug-generate-debug-info.md) ist angegeben. Um diese Standardeinstellung zu überschreiben und nicht referenzierte COMDATs im Programm beizubehalten, geben Sie **/OPT:NOREF**an. Sie können die Option [/INCLUDE](include-force-symbol-references.md) verwenden, um das Entfernen eines bestimmten Symbols zu überschreiben.

Wenn [/DEBUG](debug-generate-debug-info.md) angegeben ist, ist die Standardeinstellung für **/OPT** **NOREF**, und alle Funktionen bleiben im Bild erhalten. Um diese Standardeinstellung zu überschreiben und einen Debugbuild zu optimieren, geben Sie **/OPT:REF**an. Dies kann die Größe Ihrer ausführbaren Datei reduzieren und kann eine nützliche Optimierung auch in Debugbuilds sein. Es wird empfohlen, **auch /OPT:NOICF** anzugeben, um identische Funktionen in Debugbuilds beizubehalten. Dadurch wird es einfacher, in Funktionen, die andernfalls gefaltet würden, Stapelüberwachungen zu lesen und Haltepunkte festzulegen.

**ICF-Iterationen**\[**=**_iterations_] &#124; **NOICF**

Verwenden Sie\[**=** **ICF-Iterationen**], um identische COMDAT-Faltungen durchzuführen._iterations_ Redundante COMDATs können aus der Linkerausgabe entfernt werden. Der Parameter *optionale Iterationen* gibt an, wie oft die Symbole für Duplikate durchlaufen werden. Die Standardanzahl der Iterationen ist 1. Zusätzliche Iterationen können mehr Duplikate auffinden, die bei der Faltung in vorherigen Iterationen unentdeckt blieben.

Standardmäßig wird **/OPT:ICF** durch den Linker aktiviert, es sei **denn, /OPT:NOICF** oder [/DEBUG](debug-generate-debug-info.md) ist angegeben. Um diese Standardeinstellung zu überschreiben und zu verhindern, dass COMDATs im Programm gefaltet werden, geben Sie **/OPT:NOICF**an.

In einem Debugbuild müssen Sie **explizit /OPT:ICF** angeben, um das COMDAT-Falten zu aktivieren. Da **/OPT:ICF** jedoch identische Daten oder Funktionen zusammenführen kann, kann es die Funktionsnamen ändern, die in Stapelablaufverfolgungen angezeigt werden. Es kann auch unmöglich machen, Haltepunkte in bestimmten Funktionen festzulegen oder einige Daten im Debugger zu untersuchen, und Sie können unerwartete Funktionen in den einzelnen Schritt durch den Code führen. Das Verhalten des Codes ist identisch, aber die Debuggerpräsentation kann sehr verwirrend sein. Daher wird nicht empfohlen, **/OPT:ICF** in Debugbuilds zu verwenden, es sei denn, die Vorteile kleinerer Codes überwiegen diese Nachteile.

> [!NOTE]
> Da **/OPT:ICF** dazu führen kann, dass dieselbe Adresse verschiedenen Funktionen oder schreibgeschützten Datenmembern zugewiesen wird (d. h. **const-Variablen,** wenn sie mit **/Gy**kompiliert werden), kann es ein Programm unterbrechen, das von eindeutigen Adressen für Funktionen oder schreibgeschützte Datenmember abhängt. Weitere Informationen finden Sie unter [/Gy (Funktionslevel-Linking aktivieren)](gy-enable-function-level-linking.md).

**LBR** &#124; **NOLBR**

Die Optionen **/OPT:LBR** und **/OPT:NOLBR** gelten nur für ARM-Binärdateien. Da bestimmte Anweisungen für den ARM-Prozessorzweig einen begrenzten Bereich haben, ersetzt der Linker, wenn er einen Sprung zu einer A-Range-Adresse erkennt, die Zieladresse der Zweiganweisung durch die Adresse eines Codes "Insel", der eine Zweiganweisung enthält, die auf das tatsächliche Ziel abzielt. Sie können **/OPT:LBR** verwenden, um die Erkennung von Anweisungen für lange Zweigstellen und die Platzierung von Zwischencodeinseln zu optimieren, um die Gesamtcodegröße zu minimieren. **/OPT:NOLBR** weist den Linker an, Codeinseln für lange Zweiganweisungen zu generieren, sobald sie auftreten, ohne Optimierung.

Standardmäßig wird die Option **/OPT:LBR** festgelegt, wenn die inkrementelle Verknüpfung nicht aktiviert ist. Wenn Sie eine nicht inkrementelle Verknüpfung, aber keine langen Verzweigungsoptimierungen wünschen, geben Sie **/OPT:NOLBR**an. Die Option **/OPT:LBR** deaktiviert die inkrementelle Verknüpfung.

## <a name="remarks"></a>Bemerkungen

Bei Verwendung in der Befehlszeile ist der Linker standardmäßig **auf /OPT:REF,ICF,LBR**. Wenn **/DEBUG** angegeben ist, ist der Standardwert **/OPT:NOREF,NOICF,NOLBR**.

Die **/OPT-Optimierungen** verringern in der Regel die Bildgröße und erhöhen die Programmgeschwindigkeit. Diese Verbesserungen können in größeren Programmen erheblich sein, weshalb sie standardmäßig für Einzelhandelsbuilds aktiviert sind.

Die Linker-Optimierung nimmt im Voraus zusätzliche Zeit in Anspruch, aber der optimierte Code spart auch Zeit, wenn der Linker weniger Verschiebungen zu beheben hat und ein kleineres endgültiges Image erstellt, und er spart noch mehr Zeit, wenn er weniger Debuginformationen zum Verarbeiten und Schreiben in die PDB hat. Wenn die Optimierung aktiviert ist, kann dies insgesamt zu einer schnelleren Verbindungszeit führen, da die geringen zusätzlichen Kosten in der Analyse durch die Zeitersparnis bei Linkerdurchläufen über kleinere Binärdateien mehr als ausgeglichen werden können.

Die **/OPT-Argumente** können zusammen angegeben werden, getrennt durch Kommas. Anstelle von **/OPT:REF /OPT:NOICF**können Sie beispielsweise **/OPT:REF,NOICF**angeben.

Sie können die Linkeroption [/VERBOSE](verbose-print-progress-messages.md) verwenden, um die Funktionen anzuzeigen, die von **/OPT:REF** entfernt werden, und die Funktionen, die von **/OPT:ICF**gefaltet werden.

Die **/OPT-Argumente** werden häufig für Projekte festgelegt, die mithilfe des Dialogfelds **"Neues Projekt"** in der Visual Studio-IDE erstellt wurden, und haben in der Regel unterschiedliche Werte für Debug- und Releasekonfigurationen. Wenn für diese Linkeroptionen in Ihrem Projekt kein Wert festgelegt ist, erhalten Sie möglicherweise die Projektstandards, die sich von den Standardwerten unterscheiden können, die vom Linker in der Befehlszeile verwendet werden.

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie die OPT:ICF- oder OPT:REF-Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die Eigenschaftenseite > **Konfigurationeigenschaften-Linkeroptimierung** > **Optimization** aus. **Configuration Properties**

1. Ändern Sie eine der folgenden Eigenschaften:

   - **COMDAT-Faltung aktivieren**

   - **Verweise**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie die OPT:LBR-Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die Eigenschaftenseite **Configuration Properties** > **Linker** > **Command Line** aus.

1. Geben Sie die Option in **Zusätzliche Optionen**ein:

   `/opt:lbr` oder `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

- Siehe die Eigenschaften <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> und <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A>.

## <a name="see-also"></a>Siehe auch

- [MSVC-Linkerreferenz](linking.md)
- [MSVC-Linkeroptionen](linker-options.md)

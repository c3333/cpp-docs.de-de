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
ms.openlocfilehash: 7f576d971425a67fc533bb417583173617615e3b
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040404"
---
# <a name="opt-optimizations"></a>/OPT (Optimierungen)

Steuert die Optimierungen, die während eines Builds von LINK ausgeführt werden.

## <a name="syntax"></a>Syntax

> **/OPT:**{**ref** \| **NOREF**} \
> **/OPT:**{**ICF**- \[ **=** _Iterationen_] \| **NOICF**} \
> **/OPT:**{**LBR** \| **nolbr**}

## <a name="arguments"></a>Argumente

**Ref** &#124; **NOREF**

**/OPT: Ref** löscht Funktionen und Daten, auf die nie verwiesen wird. **/OPT: NOREF** speichert Funktionen und Daten, auf die nie verwiesen wird.

Wenn/OPT: REF aktiviert ist, entfernt Link nicht referenzierte Paketfunktionen und-Daten, die als *COMDATs*bezeichnet werden. Diese Optimierung ist als transitive COMDAT-Eliminierung bekannt. Die Option **/OPT: Ref** deaktiviert auch die inkrementelle Verknüpfung.

Inline Funktionen und Member-Funktionen, die innerhalb einer Klassen Deklaration definiert sind, sind immer COMDATs. Alle Funktionen in einer Objektdatei werden in COMDATs erstellt, wenn Sie mithilfe der [/Gy](gy-enable-function-level-linking.md) -Option kompiliert werden. Zum Platzieren **`const`** von Daten in COMDATs müssen Sie diese mithilfe von deklarieren `__declspec(selectany)` . Informationen zum Angeben von Daten zum Entfernen oder Falten finden Sie unter [Selectany](../../cpp/selectany.md).

Standardmäßig wird **/OPT: Ref** vom Linker aktiviert, es sei denn, **/OPT: NOREF** oder [/Debug](debug-generate-debug-info.md) wurde angegeben. Um diese Standardeinstellung zu überschreiben und unreferenzierte COMDATs im Programm beizubehalten, geben Sie **/OPT: NOREF**an. Sie können die [/include](include-force-symbol-references.md) -Option verwenden, um das Entfernen eines bestimmten Symbols zu überschreiben.

Wenn [/Debug](debug-generate-debug-info.md) angegeben wird, ist der Standardwert für **/opt** **NOREF**, und alle Funktionen werden im Image beibehalten. Um diese Standardeinstellung zu überschreiben und einen Debugbuild zu optimieren, geben Sie **/OPT: Ref**an. Dadurch kann die Größe Ihrer ausführbaren Datei reduziert werden, und Sie kann auch in Debugbuilds eine sinnvolle Optimierung sein. Es wird empfohlen, auch **/OPT: NOICF** anzugeben, um identische Funktionen in Debugbuilds beizubehalten. Dadurch wird es einfacher, in Funktionen, die andernfalls gefaltet würden, Stapelüberwachungen zu lesen und Haltepunkte festzulegen.

**ICF** \[ **=** _Iterationen_] &#124; **NOICF**

Verwenden Sie **ICF**- \[ **=** _Iterationen_], um eine identische COMDAT-Faltung auszuführen. Redundante COMDATs können aus der Linkerausgabe entfernt werden. Der optionale *Iterationen* Parameter gibt an, wie oft die Symbole für Duplikate durchlaufen werden. Die Standard Anzahl von Iterationen ist 1. Zusätzliche Iterationen können mehr Duplikate auffinden, die bei der Faltung in vorherigen Iterationen unentdeckt blieben.

Standardmäßig wird **/OPT: ICF** durch den Linker aktiviert, es sei denn, **/OPT: NOICF** oder [/Debug](debug-generate-debug-info.md) wurde angegeben. Um diese Standardeinstellung zu überschreiben und zu verhindern, dass COMDATs im Programm gefaltet werden, geben Sie **/OPT: NOICF**an.

In einem Debugbuild müssen Sie explizit **/OPT: ICF** angeben, um die COMDAT-Faltung zu aktivieren. Da **/OPT: ICF** identische Daten oder Funktionen zusammenführen kann, kann es jedoch die Funktionsnamen ändern, die in Stapel Überwachungen angezeigt werden. Außerdem kann es unmöglich sein, in bestimmten Funktionen Haltepunkte festzulegen oder einige Daten im Debugger zu untersuchen. Außerdem können Sie unerwartete Funktionen verwenden, wenn Sie den Code in Einzelschritten durchlaufen. Das Verhalten des Codes ist identisch, aber die Debugger-Präsentation kann sehr verwirrend sein. Daher empfiehlt es sich nicht, **/OPT: ICF** in Debugbuilds zu verwenden, es sei denn, die Vorteile von geringerem Code überwiegen diese Nachteile.

> [!NOTE]
> Da **/OPT: ICF** bewirken kann, dass dieselbe Adresse verschiedenen Funktionen oder schreibgeschützten Datenmembern zugewiesen wird (d. h. **`const`** Variablen bei der Kompilierung mit **/Gy**), kann Sie ein Programm unterbrechen, das von eindeutigen Adressen für Funktionen oder schreibgeschützte Datenmember abhängt. Weitere Informationen finden Sie unter [/Gy (Funktionslevel-Linking aktivieren)](gy-enable-function-level-linking.md).

**LBR** &#124; **nolbr**

Die Optionen **/OPT: LBR** und **/OPT: nolbr** gelten nur für Arm-Binärdateien. Da bestimmte ARM-Prozessor Verzweigungs Anweisungen einen begrenzten Bereich aufweisen und der Linker einen Sprung zu einer außerhalb des gültigen Bereichs gültigen Adresse erkennt, ersetzt er die Zieladresse der Verzweigungs Anweisung durch die Adresse einer "Insel", die eine Verzweigungs Anweisung enthält, die auf das eigentliche Ziel abzielt. Sie können **/OPT: LBR** verwenden, um die Erkennung von langen Verzweigungs Anweisungen und die Platzierung von zwischen Code Inseln zu optimieren, um die Gesamt Code Größe zu minimieren. **/OPT: nolbr** weist den Linker an, Code Inseln für lange Verzweigungs Anweisungen zu generieren, die ohne Optimierung auftreten.

Standardmäßig wird die Option **/OPT: LBR** festgelegt, wenn die inkrementelle Verknüpfung nicht aktiviert ist. Wenn Sie einen nicht inkrementellen Link, aber keine langen Verzweigungs Optimierungen möchten, geben Sie **/OPT: nolbr**an. Die Option **/OPT: LBR** deaktiviert die inkrementelle Verknüpfung.

## <a name="remarks"></a>Bemerkungen

Bei Verwendung in der Befehlszeile wird der Linker standardmäßig auf **/OPT: ref, ICF, LBR**festgelegt. Wenn **/Debug** angegeben wird, lautet der Standardwert **/OPT: NOREF, NOICF, nolbr**.

Die **/opt** -Optimierungen verringern die Bildgröße in der Regel und erhöhen die Programm Geschwindigkeit. Diese Verbesserungen können in größeren Programmen beträchtlich sein. aus diesem Grund sind Sie für Einzelhandels Builds standardmäßig aktiviert.

Die linkeroptimierung nimmt zusätzliche Zeit in Anspruch, aber der optimierte Code spart auch Zeit, wenn der Linker weniger Umsetzungen aufweist, um eine Korrektur durchführen zu können, und ein kleineres endgültiges Image erstellt, und es spart noch mehr Zeit, wenn weniger Debuginformationen zum Verarbeiten und Schreiben in die PDB benötigt werden. Wenn die Optimierung aktiviert ist, kann dies zu einer schnelleren Verknüpfungs Zeit führen, da die kleinen zusätzlichen Kosten bei der Analyse mehr als versetzt werden können, wenn die Zeitersparnis im Linker über kleinere Binärdateien verläuft.

Die **/opt** -Argumente können durch Kommas getrennt angegeben werden. Beispielsweise können Sie anstelle von **/OPT: Ref/OPT: NOICF** **/OPT: ref, NOICF**angeben.

Mit der [/verbose](verbose-print-progress-messages.md) Linker-Option können Sie die Funktionen anzeigen, die von **/OPT: Ref** entfernt wurden, sowie die Funktionen, die von **/OPT: ICF**gefaltet werden.

Die **/opt** -Argumente werden häufig für Projekte festgelegt, die mit dem Dialogfeld " **Neues Projekt** " in der Visual Studio-IDE erstellt wurden, und in der Regel unterschiedliche Werte für Debug-und Releasekonfigurationen Wenn für diese Linkeroptionen in Ihrem Projekt kein Wert festgelegt ist, können Sie die Projekt Standardwerte erhalten, die sich von den Standardwerten unterscheiden können, die vom Linker in der Befehlszeile verwendet werden.

### <a name="to-set-the-opticf-or-optref-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie die OPT:ICF- oder OPT:REF-Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die Eigenschaften Seite für die Linker-Optimierung der **Konfigurations Eigenschaften**  >  **Linker**  >  **Optimization** .

1. Ändern Sie eine der folgenden Eigenschaften:

   - **COMDAT-Faltung aktivieren**

   - **Referenzen**

### <a name="to-set-the-optlbr-linker-option-in-the-visual-studio-development-environment"></a>So legen Sie die OPT:LBR-Linkeroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften**Seite für die  >  **Linker**  >  **Linkerbefehlszeile** der Configuration Properties

1. Geben Sie die Option in **zusätzliche Optionen**ein:

   `/opt:lbr` oder `/opt:nolbr`

### <a name="to-set-this-linker-option-programmatically"></a>So legen Sie diese Linkeroption programmgesteuert fest

- Siehe die Eigenschaften <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableCOMDATFolding%2A> und <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OptimizeReferences%2A>.

## <a name="see-also"></a>Weitere Informationen

- [MSVC-Linkerreferenz](linking.md)
- [MSVC-Linkeroptionen](linker-options.md)

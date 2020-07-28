---
title: /guard (Ablaufsteuerungsschutz aktivieren)
ms.date: 11/04/2016
f1_keywords:
- /guard
- VC.Project.VCCLCompilerTool.ControlFlowGuard
ms.assetid: be495323-f59f-4cf3-a6b6-8ee69e6a19dd
ms.openlocfilehash: 8661f94e0ee35f8d5e2c8caba1fc01bbf4072876
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87190688"
---
# <a name="guard-enable-control-flow-guard"></a>/guard (Ablaufsteuerungsschutz aktivieren)

Aktivieren der Compilergenerierung von Ablaufsteuerungsschutz-Sicherheitsüberprüfungen.

## <a name="syntax"></a>Syntax

```
/guard:cf[-]
```

## <a name="remarks"></a>Bemerkungen

Die Option **/guard:cf** veranlasst den Compiler, die Ablaufsteuerung für indirekte Aufrufziele zum Zeitpunkt der Kompilierung zu analysieren und dann Code einzufügen, um die Ziele zur Laufzeit zu überprüfen. Standardmäßig ist **/guard:cf** deaktiviert und muss explizit aktiviert werden. Um diese Option explizit zu deaktivieren, verwenden Sie **/guard:cf-**.

**Visual Studio 2017 und**höher: diese Option fügt Wächter für **`switch`** Anweisungen hinzu, die Sprung Tabellen generieren.

Wenn die **/guard:cf** Ablaufsteuerungsschutz-Option (Control Flow Guard, CFG) angegeben wurde, fügen der Compiler und der Linker zusätzliche Laufzeitsicherheitsüberprüfungen zum Erkennen von Versuchen, den Code zu beschädigen, ein. Beim Kompilieren und Verknüpfen werden alle indirekten Aufrufe im Code analysiert, um jede Stelle zu finden, die der Code erreichen kann, wenn er ordnungsgemäß ausgeführt wird. Diese Informationen werden in zusätzlichen Strukturen in den Headern der Binärdateien gespeichert. Der Compiler fügt auch eine Überprüfung vor jedem indirekten Aufruf in Ihren Code ein, um sicherzustellen, dass das Ziel eine der überprüften Positionen ist. Wenn die Überprüfung zur Laufzeit auf einem CFG-fähigen Betriebssystem fehlschlägt, schließt das Betriebssystem das Programm.

Eine häufige Form des Angriffs auf Software nutzt die Vorteile von Fehlern bei der Verarbeitung extremer oder unerwarteter Eingaben. Sorgfältig ausgearbeitete Eingaben in die Anwendung können eine Position mit einem Zeiger auf den ausführbaren Code überschreiben. Dies kann verwendet werden, um die Ablaufsteuerung an Code umzuleiten, der durch den Angreifer gesteuert werden. Die CFG-Laufzeitüberprüfungen korrigieren nicht die Datenbeschädigungsfehler in der ausführbaren Datei. Sie erschweren stattdessen einem Angreifer das Verwenden dieser Überprüfungen, um beliebigen Code auszuführen. CFG ist ein Minimierungstool, das Aufrufe an andere Positionen als Funktionseinstiegspunkte in Ihrem Code verhindert. Es ähnelt der Art und Weise, in der die Datenausführungsverhinderung (Data Execution Prevention, DEP)  [/GS](gs-buffer-security-check.md) -Stapelüberprüfungen und [/DYNAMICBASE](dynamicbase-use-address-space-layout-randomization.md) sowie [/HIGHENTROPYVA](highentropyva-support-64-bit-aslr.md) Address Space Layout Randomization (ASLR) die Wahrscheinlichkeit verringern, dass der Code zu einem Angriffsvektor wird.

Die **/guard:cf** -Option muss an den Compiler und den Linker übergeben werden, um Code zu erstellen, der die CFG-Angriffsminimierungstechnik verwendet. Wenn die Binärdatei mit einem einzigen `cl` -Befehl erstellt wird, übergibt der Compiler die Option an den Linker. Wenn Sie separat kompilieren und verknüpfen, muss die Option für die Compiler- und Linkerbefehle festgelegt werden. Die Linkeroption /DYNAMICBASE ist ebenfalls erforderlich. Um zu überprüfen, ob die Binärdatei CFG-Daten enthält, verwenden Sie den Befehl `dumpbin /headers /loadconfig` . CFG-fähige Binärdateien haben `Guard` in der Liste der EXE- oder DLL-Merkmale, und Wächterflags enthalten `CF Instrumented` sowie `FID table present`.

Die **/guard:cf** -Option ist nicht kompatibel mit [/ZI](z7-zi-zi-debug-information-format.md) (Bearbeiten- und Fortfahren-Debuginformationen) oder [/clr](clr-common-language-runtime-compilation.md) (Common Language Runtime-Kompilierung).

Code, der mithilfe von **/guard:cf** kompiliert wird, kann mit Bibliotheken und Objektdateien verknüpft werden, die nicht mit dieser Option kompiliert werden. Nur dieser Code, wenn er auch mit der **/guard:cf** -Option verknüpft und auf einem CFG-fähigen Betriebssystem ausgeführt wird, verfügt über CFG-Schutz. Da Code, der ohne die Option kompiliert wurde, keinen Angriff aufhalten kann, sollten Sie die Option im gesamten Code verwenden, den Sie kompilieren. Für CFG-Überprüfungen fallen geringe Laufzeitkosten an, aber die Compileranalyse versucht, die Überprüfungen auf indirekte Sprünge zu optimieren, die nachweislich sicher sind.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie **Konfigurationseigenschaften**, **C/C++**, **Codegenerierung**aus.

1. Wählen Sie die **Ablaufsteuerungsschutz** -Eigenschaft aus.

1. Wählen Sie im Dropdown-Steuerelement **Ja** aus, um den Ablaufsteuerungsschutz zu aktivieren, oder **Nein** , um ihn zu deaktivieren.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)

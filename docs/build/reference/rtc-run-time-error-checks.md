---
title: /RTC (Laufzeitfehlerüberprüfungen)
ms.date: 11/04/2016
f1_keywords:
- /rtc
- VC.Project.VCCLCompilerTool.SmallerTypeCheck
- VC.Project.VCCLCompilerTool.UninitializedVariableCheck
- VC.Project.VCCLCompilerTool.StackFrameCheck
- VC.Project.VCCLCompilerTool.BasicRuntimeChecks
helpviewer_keywords:
- /RTCs compiler option [C++]
- -RTC1 compiler option [C++]
- run-time errors, error checks
- -RTCu compiler option [C++]
- /RTC1 compiler option [C++]
- /RTCc compiler option [C++]
- /RTCu compiler option [C++]
- __MSVC_RUNTIME_CHECKS macro
- -RTCs compiler option [C++]
- RTCs compiler option
- RTC1 compiler option
- run-time errors, run-time checks
- run-time checks, /RTC option
- RTCu compiler option
- RTCc compiler option
- -RTCc compiler option [C++]
ms.assetid: 9702c558-412c-4004-acd5-80761f589368
ms.openlocfilehash: 49f0e4bace5f3dd199b58854e838204bd2cd5f3b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222016"
---
# <a name="rtc-run-time-error-checks"></a>/RTC (Laufzeitfehlerüberprüfungen)

Wird verwendet, um die Lauf Zeit Fehlerüberprüfungen in Verbindung mit dem [runtime_checks](../../preprocessor/runtime-checks.md) -Pragma zu aktivieren und zu deaktivieren.

## <a name="syntax"></a>Syntax

```
/RTC1
/RTCc
/RTCs
/RTCu
```

## <a name="arguments"></a>Argumente

**1**<br/>
Entsprechung von **/RTC** `su` .

**scher**<br/>
Meldet, wenn ein Wert einem kleineren Datentyp zugewiesen wird, und führt zu einem Datenverlust. Wenn z. b. ein Wert des Typs `short 0x101` einer Variablen vom Typ zugewiesen ist **`char`** .

Diese Option meldet Situationen, in denen Sie abschneiden möchten, z. b. wenn die ersten acht Bits eines **`int`** als zurückgegeben werden sollen **`char`** . Da **/RTC** `c` einen Laufzeitfehler auslöst, wenn Informationen aufgrund der Zuweisung verloren gehen, können Sie die Informationen, die Sie benötigen, maskieren, um einen Laufzeitfehler aufgrund von **/RTC**zu vermeiden `c` . Beispiel:

```
#include <crtdbg.h>

char get8bits(int value, int position) {
   _ASSERT(position < 32);
   return (char)(value >> position);
   // Try the following line instead:
   // return (char)((value >> position) & 0xff);
}

int main() {
   get8bits(12341235,3);
}
```

**Hymnen**<br/>
Aktiviert die Lauf Zeit Fehlerüberprüfung für Stapel Rahmen wie folgt:

- Initialisierung lokaler Variablen auf einen Wert ungleich 0 (null). Dadurch können Fehler identifiziert werden, die bei der Ausführung im Debugmodus nicht angezeigt werden. Aufgrund von Compileroptimierungen von Stapel Variablen in einem Releasebuild ist die Wahrscheinlichkeit größer, dass Stapel Variablen in einem Debugbuild weiterhin 0 (null) sein werden. Wenn ein Programm einen Bereich seines Stapels verwendet hat, wird es vom Compiler nie auf 0 zurückgesetzt. Folglich können nachfolgende, nicht initialisierte Stapel Variablen, die den gleichen Stapelbereich verwenden, Werte zurückgeben, die von der vorherigen Verwendung dieses Stapel Speichers übrig bleiben.

- Erkennung von Überläufen und unter Läufen lokaler Variablen (z. b. Arrays). **/RTC** `s` erkennt über Läufe nicht, wenn auf den Speicher zugegriffen wird, der sich aus dem compilerpadding innerhalb einer Struktur ergibt. Auffüll Zeichen können mithilfe von [align](../../cpp/align-cpp.md), [/ZP (Strukturmember Alignment)](zp-struct-member-alignment.md)oder [Pack](../../preprocessor/pack.md)oder, wenn Sie Strukturelemente auf eine Weise sortieren, um den Compiler aufzufordern, Padding hinzuzufügen.

- Stapelzeiger Überprüfung, mit der Stapelzeiger Beschädigungen erkannt werden. Die Beschädigung des Stapel Zeigers kann durch eine nicht Übereinstimmung der Aufruf Konvention verursacht werden. Beispielsweise rufen Sie mithilfe eines Funktions Zeigers eine Funktion in einer DLL auf, die als [__stdcall](../../cpp/stdcall.md) exportiert wird, aber Sie deklarieren den Zeiger auf die Funktion als [__cdecl](../../cpp/cdecl.md).

**n**<br/>
Meldet, wenn eine Variable verwendet wird, ohne initialisiert worden zu sein. Eine Anweisung, die generiert, `C4701` kann z. b. auch einen Laufzeitfehler unter **/RTC**generieren `u` . Jede Anweisung, die [Compilerwarnung (Ebene 1 und Ebene 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) generiert, generiert unter **/RTC**einen Laufzeitfehler `u` .

Beachten Sie jedoch das folgende Code Fragment:

```cpp
int a, *b, c;
if ( 1 )
b = &a;
c = a;  // No run-time error with /RTCu
```

Wenn eine Variable initialisiert werden kann, wird Sie zur Laufzeit nicht von **/RTC**gemeldet `u` . Wenn z. b. eine Variable durch einen-Zeiger als Alias verwendet wird, verfolgt der Compiler die Variable nicht und meldet nicht initialisierte Verwendungen. In der Tat können Sie eine Variable initialisieren, indem Sie Ihre Adresse übernehmen. Der &-Operator funktioniert in dieser Situation wie ein Zuweisungs Operator.

## <a name="remarks"></a>Bemerkungen

Lauf zeitfehlerüberprüfungen sind eine Möglichkeit, Probleme in Ihrem ausgelaufenden Code zu finden. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden von nativen Laufzeitüberprüfungen](/visualstudio/debugger/how-to-use-native-run-time-checks).

Wenn Sie das Programm mithilfe einer der **/RTC** -Compileroptionen in der Befehlszeile kompilieren, treten bei allen Pragma- [Optimierungs](../../preprocessor/optimize.md) Anweisungen im Code automatisch Fehler auf. Dies liegt daran, dass Lauf Zeit Fehlerüberprüfungen in einem Releasebuild (optimiert) nicht gültig sind.

Verwenden Sie **/RTC** für Entwicklungsbuilds. **/RTC** sollte nicht für einen Einzelhandels Build verwendet werden. **/RTC** kann nicht mit Compileroptimierungen verwendet werden ([/O-Optionen (Code optimieren)](o-options-optimize-code.md)). Ein mit **/RTC** erstelltes Programm Image ist etwas größer und etwas langsamer als ein Image, das mit **/od** erstellt wird (bis zu 5 Prozent langsamer als ein **/od** -Build).

Die __MSVC_RUNTIME_CHECKS-Präprozessordirektive wird definiert, wenn Sie eine **/RTC** -Option oder [/gz](gz-enable-stack-frame-run-time-error-checking.md)verwenden.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Klicken Sie auf den Ordner **C/C++** .

1. Klicken Sie auf die Eigenschaften Seite **Code Generierung** .

1. Ändern Sie eine oder beide der folgenden Eigenschaften: **grundlegende Laufzeitüberprüfungen** oder eine **kleinere Typüberprüfung**.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe die Eigenschaften <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> und <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)<br/>
[How to: Verwenden von nativen Laufzeitüberprüfungen](/visualstudio/debugger/how-to-use-native-run-time-checks)

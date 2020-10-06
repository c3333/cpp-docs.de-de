---
title: /RTC (Laufzeitfehlerüberprüfungen)
description: Der Microsoft C/C++-Compiler/RTC Optionen für Lauf Zeit Fehlerüberprüfungen.
ms.date: 07/31/2020
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
ms.openlocfilehash: 888a81d0d5c21b0b85420a43d534c5b2742aa082
ms.sourcegitcommit: 30792632548d1c71894f9fecbe2f554294b86020
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/06/2020
ms.locfileid: "91765234"
---
# <a name="rtc-run-time-error-checks"></a>`/RTC` (Lauf Zeit Fehlerüberprüfungen)

Wird verwendet, um die Lauf Zeit Fehlerüberprüfungen in Verbindung mit dem [runtime_checks](../../preprocessor/runtime-checks.md) -Pragma zu aktivieren und zu deaktivieren.

## <a name="syntax"></a>Syntax

> **`/RTC1`**\
> **`/RTCc`**\
> **`/RTCs`**\
> **`/RTCu`**

## <a name="arguments"></a>Argumente

**`/RTC1`**<br/>
Entspricht **`/RTCsu`** .

**`/RTCc`**<br/>
Meldet, wenn ein Wert einem kleineren Datentyp zugewiesen wird, und führt zu einem Datenverlust. Beispielsweise meldet Sie, ob ein **`short`** Typwert von `0x0101` einer Variablen vom Typ zugewiesen wird **`char`** .

Mit dieser Option können Sie Situationen melden, in denen Sie abschneiden möchten. Wenn Sie z. b. möchten, dass die ersten 8 Bits eines **`int`** als zurückgegeben werden **`char`** . Da **`/RTCc`** einen Laufzeitfehler auslöst, wenn eine Zuweisung einen Informationsverlust auslöst, sollten Sie zunächst die Informationen maskieren, die Sie benötigen, um den Laufzeitfehler zu vermeiden. Zum Beispiel:

```C
#include <crtdbg.h>

char get8bits(unsigned value, int position) {
   _ASSERT(position < 32);
   return (char)(value >> position);
   // Try the following line instead:
   // return (char)((value >> position) & 0xff);
}

int main() {
   get8bits(12341235,3);
}
```

Da **`/RTCc`** Code zurückweist, der dem Standard entspricht, wird er von der C++-Standardbibliothek nicht unterstützt. Code, **`/RTCc`** der und die C++-Standard Bibliothek verwendet, verursacht möglicherweise Compilerfehler [C1189](../../error-messages/compiler-errors-1/fatal-error-c1189.md). Sie können definieren `_ALLOW_RTCc_IN_STL` , um die Warnung zu stillen, und die **`/RTCc`** Option verwenden.

**`/RTCs`**<br/>
Aktiviert die Lauf Zeit Fehlerüberprüfung für Stapel Rahmen wie folgt:

- Initialisierung lokaler Variablen auf einen Wert ungleich 0 (null). Diese Option hilft, Fehler zu identifizieren, die bei der Ausführung im Debugmodus nicht angezeigt werden. Es besteht eine größere Wahrscheinlichkeit, dass Stapel Variablen in einem Debugbuild im Vergleich zu einem Releasebuild immer noch über einen Nullwert verfügen. Dies liegt an Compileroptimierungen von Stapel Variablen in einem Releasebuild. Wenn ein Programm einen Bereich seines Stapels verwendet hat, wird es vom Compiler nie auf 0 zurückgesetzt. Dies bedeutet, dass nicht initialisierte Stapel Variablen, die den gleichen Stapelbereich später verwenden, Werte zurückgeben können, die von der früheren Verwendung dieses Stapel Speichers übrig geblieben sind.

- Erkennung von Überläufen und unter Läufen lokaler Variablen (z. b. Arrays). **`/RTCs`** erkennt über Läufe nicht, wenn auf den Speicher zugegriffen wird, der aus dem Auffüll Leerraum innerhalb einer Struktur resultiert. Auffüll Zeichen können mithilfe von [`align`](../../cpp/align-cpp.md) , [ `/Zp` (Strukturmember-Ausrichtung)](zp-struct-member-alignment.md)oder [`pack`](../../preprocessor/pack.md) , oder, wenn Sie Strukturelemente auf eine Weise sortieren, um den Compiler aufzufordern, Padding hinzuzufügen.

- Stapelzeiger Überprüfung, mit der Stapelzeiger Beschädigungen erkannt werden. Die Beschädigung des Stapel Zeigers kann durch eine nicht Übereinstimmung der Aufruf Konvention verursacht werden. Beispielsweise rufen Sie mithilfe eines Funktions Zeigers eine Funktion in einer DLL auf, die als exportiert wird, [`__stdcall`](../../cpp/stdcall.md) aber Sie deklarieren den Zeiger auf die Funktion als [`__cdecl`](../../cpp/cdecl.md) .

**`/RTCu`**<br/>
Meldet, wenn eine Variable verwendet wird, ohne initialisiert worden zu sein. Beispielsweise kann eine Anweisung, die Warning C4701 generiert, auch einen Laufzeitfehler unter generieren **`/RTCu`** . Jede Anweisung, die [Compilerwarnung (Ebene 1 und Ebene 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md) generiert, generiert einen Laufzeitfehler unter **`/RTCu`** .

Beachten Sie jedoch das folgende Code Fragment:

```cpp
int a, *b, c;
if ( 1 )
b = &a;
c = a;  // No run-time error with /RTCu
```

Wenn eine Variable initialisiert werden kann, wird Sie von nicht zur Laufzeit gemeldet **`/RTCu`** . Wenn z. b. eine Variable einen Alias durch einen Zeiger hat, verfolgt der Compiler die Variable nicht und meldet nicht initialisierte Verwendungen. In der Tat können Sie eine Variable initialisieren, indem Sie Ihre Adresse übernehmen. Der- **`&`** Operator funktioniert in dieser Situation wie ein Zuweisungs Operator.

## <a name="remarks"></a>Bemerkungen

Lauf zeitfehlerüberprüfungen sind eine Möglichkeit, Probleme in Ihrem ausgelaufenden Code zu finden. Weitere Informationen finden Sie unter Gewusst [wie: Verwenden von nativen Laufzeitüberprüfungen](/visualstudio/debugger/how-to-use-native-run-time-checks).

Sie können mehr als eine **`/RTC`** Option in der Befehlszeile angeben. Die Options Argumente können kombiniert werden. beispielsweise **`/RTCcu`** ist identisch mit **`/RTCc /RTCu`** .

Wenn Sie das Programm mithilfe einer der Compileroptionen in der Befehlszeile kompilieren **`/RTC`** , treten bei allen Pragma- [`optimize`](../../preprocessor/optimize.md) Anweisungen in Ihrem Code automatisch Fehler auf. Dies liegt daran, dass Lauf Zeit Fehlerüberprüfungen in einem Releasebuild (optimiert) nicht gültig sind.

Verwenden Sie **`/RTC`** für Entwicklungsbuilds. Verwenden Sie nicht **`/RTC`** für einen Releasebuild. **`/RTC`** kann nicht mit Compileroptimierungen verwendet werden ([ `/O` Optionen (Code optimieren)](o-options-optimize-code.md)). Ein mit erstelltes Programm Image **`/RTC`** ist etwas größer und etwas langsamer als ein mit erstelltes Bild **`/Od`** (bis zu 5 Prozent langsamer als ein **`/Od`** Build).

Die `__MSVC_RUNTIME_CHECKS` Präprozessordirektive wird definiert, wenn Sie eine beliebige **`/RTC`** Option oder verwenden [`/GZ`](gz-enable-stack-frame-run-time-error-checking.md) .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Code Generierung** aus.

1. Ändern Sie eine oder beide der folgenden Eigenschaften: **grundlegende Laufzeitüberprüfungen** oder eine **kleinere Typüberprüfung**.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe die Eigenschaften <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A> und <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.SmallerTypeCheck%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
[How to: Use native run-time checks (Vorgehensweise: Verwenden von nativen Laufzeitüberprüfungen)](/visualstudio/debugger/how-to-use-native-run-time-checks)

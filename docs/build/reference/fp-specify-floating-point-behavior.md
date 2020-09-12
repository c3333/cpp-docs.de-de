---
title: /fp (Gleitkommaverhalten festlegen)
ms.date: 11/09/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.floatingPointModel
- VC.Project.VCCLWCECompilerTool.FloatingPointExceptions
- /fp
- VC.Project.VCCLWCECompilerTool.floatingPointModel
- VC.Project.VCCLCompilerTool.FloatingPointExceptions
helpviewer_keywords:
- -fp compiler option [C++]
- /fp compiler option [C++]
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
ms.openlocfilehash: 7a8ae885bbbf00ae916505bf5df646b32268a17a
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2020
ms.locfileid: "90040911"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (Gleitkommaverhalten festlegen)

Gibt an, wie der Compiler Gleit Komma Ausdrücke, Optimierungen und Ausnahmen behandelt. Die **/FP** -Optionen geben an, ob der generierte Code Gleit Komma Umgebungs Änderungen an den Rundungs Modus, Ausnahme Masken und das subnormale Verhalten zulässt und ob Gleit Komma Statusüberprüfungen aktuelle, genaue Ergebnisse zurückgeben. Es steuert, ob der Compiler Code generiert, der die Quell-und Ausdrucks Reihenfolge verwaltet und dem Standard für die Nan-Weitergabe entspricht, oder ob er stattdessen effizienteren Code generiert, der möglicherweise Vorgänge neu anordnet oder kombiniert und vereinfachende algebraische Transformationen verwendet, die vom Standard nicht zugelassen werden.

## <a name="syntax"></a>Syntax

> **/fp:**[**präzise**  |  **Strict**  |  **fast fast**,  |  **außer**[ **-** ]]

### <a name="arguments"></a>Argumente

#### <a name="precise"></a>sesten

Standardmäßig verwendet der Compiler das- `/fp:precise` Verhalten.

Unter `/fp:precise` dem Compiler behält die Reihenfolge der Quell Ausdrücke und die Rundungs Eigenschaften von Gleit Komma Code bei, wenn der Objektcode für den Zielcomputer generiert und optimiert wird. Der Compiler rundet bei der Ausdrucks Auswertung um die Quell Code Genauigkeit an vier bestimmten Punkten: bei den Zuweisungen bei Typecasts, wenn ein Gleit Komma Argument an einen Funktions Aufrufwert und ein Gleit Komma Wert von einem Funktions Aufrufwert zurückgegeben wird. Zwischenberechnungen können bei der computergenauigkeit durchgeführt werden. Typecasts können verwendet werden, um Zwischenberechnungen explizit zu runden.

Der Compiler führt keine algebraischen Transformationen für Gleit Komma Ausdrücke aus, z. b. Neuzuordnung oder Verteilung, es sei denn, die Transformation erzeugt ein bitweises identisches Ergebnis.
Ausdrücke, die spezielle Werte (NaN, + unendlich,-unendlich,-0,0) einschließen, werden gemäß den IEEE-754-Spezifikationen verarbeitet. Beispielsweise wird `x != x` zu ausgewertet, **`true`** Wenn x NaN ist. Gleit Komma *Kontraste*, d. h. Computeranweisungen, die Gleit Komma Operationen kombinieren, können unter generiert werden `/fp:precise` .

Der Compiler generiert Code, der in der standardmäßigen Gleit [Komma Umgebung](#the-default-floating-point-environment) ausgeführt werden soll, und geht davon aus, dass zur Laufzeit nicht auf die Gleit Komma Umgebung zugegriffen oder diese geändert wird. Das heißt, es wird davon ausgegangen, dass der Code keine Gleit Komma Ausnahmen, Lese-oder Schreibvorgänge von Gleit Komma Status Registern oder die Rundungs Modi ändert.

Wenn Ihr Gleit Komma Code nicht von der Reihenfolge der Vorgänge und Ausdrücke in den Gleit Komma Anweisungen abhängt (wenn Sie z. b. nicht interessiert sind, ob `a * b + a * c` als `(b + c) * a` oder als berechnet wird `2 * a` `a + a` ), sollten Sie die Option [/fp: fast](#fast) in Erwägung nehmen, die schnelleren und effizienteren Code liefern kann. Wenn Ihr Code sowohl von der Reihenfolge der Vorgänge als auch von Ausdrücken abhängig ist und auf die Gleit Komma Umgebung zugreift oder diese ändert (z. b. um Rundungs Modi zu ändern oder um Gleit Komma Ausnahmen zu fangen), verwenden Sie [/fp: strict](#strict).

#### <a name="strict"></a>strict

`/fp:strict` weist ein ähnliches Verhalten auf, d. h. `/fp:precise` der Compiler behält die Quell Reihenfolge und die Rundungs Eigenschaften von Gleit Komma Code bei, wenn er Objektcode für den Zielcomputer generiert und optimiert und den Standard bei der Verarbeitung spezieller Werte beachtet. Außerdem kann das Programm zur Laufzeit sicher auf die Gleit Komma Umgebung zugreifen oder diese ändern.

Unter `/fp:strict` generiert der Compiler Code, der dem Programm das sichere Aufheben der Maskierung von Gleit Komma Ausnahmen, das Lesen oder Schreiben von Gleit Komma Status Registern oder das Ändern der Rundungs Modi ermöglicht. Bei der Ausdrucks Auswertung wird die Genauigkeit des Quellcodes an vier bestimmten Punkten gerundet: bei den Zuweisungen bei Typecasts, bei Übergabe eines Gleit Komma Arguments an einen Funktions Aufruf, und wenn ein Gleit Komma Wert von einem Funktions Aufrufwert zurückgegeben wird. Zwischenberechnungen können bei der computergenauigkeit durchgeführt werden. Typecasts können verwendet werden, um Zwischenberechnungen explizit zu runden. Der Compiler führt keine algebraischen Transformationen für Gleit Komma Ausdrücke aus, z. b. Neuzuordnung oder Verteilung, es sei denn, die Transformation erzeugt ein bitweises identisches Ergebnis. Ausdrücke, die spezielle Werte (NaN, + unendlich,-unendlich,-0,0) einschließen, werden gemäß den IEEE-754-Spezifikationen verarbeitet. Beispielsweise wird `x != x` zu ausgewertet, **`true`** Wenn x NaN ist. Gleit Komma Kontraste werden nicht unter generiert `/fp:strict` .

`/fp:strict` ist Rechen intensiver als der Grund `/fp:precise` dafür, dass der Compiler zusätzliche Anweisungen zum Abfangen von Ausnahmen einfügen und es Programmen ermöglicht, zur Laufzeit auf die Gleit Komma Umgebung zuzugreifen oder diese zu ändern. Wenn Ihr Code diese Funktion nicht verwendet, aber die Reihenfolge und Rundung von Quell Code erfordert, oder auf besondere Werte basiert, verwenden Sie `/fp:precise` . Andernfalls sollten Sie die Verwendung von in Erwägung gezogen `/fp:fast` , wodurch schneller und kleinerer Code erzeugt werden kann.

#### <a name="fast"></a>fast

Die- `/fp:fast` Option ermöglicht es dem Compiler, Gleit Komma Operationen neu anzuordnen, zu kombinieren oder zu vereinfachen, um Gleit Komma Code für Geschwindigkeit und Speicherplatz zu optimieren. Der Compiler darf Rundungen bei Zuweisungs Anweisungen, Typecasts oder Funktionsaufrufen weglassen. Sie kann Vorgänge neu anordnen oder algebraische Transformationen durchführen, z. b. durch die Verwendung von assoziativen und verteilbaren Gesetzen, auch wenn solche Transformationen zu einem observativ unterschiedlichen Rundungs Verhalten führen. Aufgrund dieser verbesserten Optimierung kann sich das Ergebnis einiger Gleit Komma Berechnungen von den Werten unterscheiden, die von anderen Optionen erzeugt werden `/fp` . Spezielle Werte (NaN, + Infinity,-Infinity,-0,0) werden möglicherweise nicht weitergegeben oder Verhalten sich nicht strikt gemäß dem IEEE-754-Standard. Gleit Komma Kontraste können unter generiert werden `/fp:fast` . Der Compiler ist weiterhin durch die zugrunde liegende Architektur unter gebunden `/fp:fast` , und zusätzliche Optimierungen sind möglicherweise durch die Verwendung der [/arch](arch-minimum-cpu-architecture.md) -Option verfügbar.

Unter `/fp:fast` generiert der Compiler Code, der in der standardmäßigen Gleit Komma Umgebung ausgeführt werden soll, und geht davon aus, dass die Gleit Komma Umgebung nicht zur Laufzeit aufgerufen oder geändert wird. Das heißt, es wird davon ausgegangen, dass der Code keine Gleit Komma Ausnahmen, Lese-oder Schreibvorgänge von Gleit Komma Status Registern oder die Rundungs Modi ändert.

`/fp:fast` ist für Programme vorgesehen, die keine strikte Quell Code Anordnung und Rundung von Gleit Komma Ausdrücken benötigen, und die Standardregeln für die Verarbeitung spezieller Werte wie z. b. NaN nicht benötigen. Wenn Ihr Gleit Komma Code die Beibehaltung der Quell Code Ordnung und-Rundung erfordert oder das Standardverhalten spezieller Werte verwendet, verwenden Sie [/fp: präzise](#precise). Wenn Ihr Code auf die Gleit Komma Umgebung zugreift oder diese ändert, um Rundungs Modi zu ändern, die Maskierung von Gleit Komma Ausnahmen aufzuheben oder den Gleit Komma Status zu überprüfen, verwenden Sie [/fp: strict](#strict).

#### <a name="except"></a>davon

Mit der- `/fp:except` Option wird Code generiert, um sicherzustellen, dass alle nicht maskierten Gleit Komma Ausnahmen an der Stelle ausgelöst werden, an der Sie auftreten, und dass keine zusätzlichen Gleit Komma Ausnahmen ausgelöst werden. Standardmäßig aktiviert die `/fp:strict` -Option `/fp:except` und `/fp:precise` nicht. Die `/fp:except` Option ist nicht mit kompatibel `/fp:fast` . Die Option kann von uns von uns explizit deaktiviert werden `/fp:except-` .

Beachten Sie, dass keine Gleit `/fp:except` Komma Ausnahmen eigenständig aktiviert, aber für Programme erforderlich ist, um Gleit Komma Ausnahmen zu aktivieren. Weitere Informationen zum Aktivieren von Gleit Komma Ausnahmen finden Sie unter [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) .

## <a name="remarks"></a>Bemerkungen

`/fp`In derselben Compilerbefehlszeile können mehrere Optionen angegeben werden. Es können nur eine der `/fp:strict` `/fp:fast` Optionen, und `/fp:precise` gleichzeitig wirksam werden. Wenn mehr als eine dieser Optionen in der Befehlszeile angegeben ist, hat die spätere Option Vorrang, und der Compiler generiert eine Warnung. Die `/fp:strict` -Option und die- `/fp:except` Option sind nicht mit kompatibel `/clr` .

Die Option [/Za](za-ze-disable-language-extensions.md) (ANSI-Kompatibilität) ist mit nicht kompatibel `/fp` .

### <a name="using-compiler-directives-to-control-floating-point-behavior"></a>Verwenden von Compilerdirektiven zum Steuern des Gleit Komma Verhaltens

Der Compiler stellt drei pragma-Direktiven bereit, um das Gleit Komma Verhalten zu überschreiben, das in der Befehlszeile angegeben ist: [float_control](../../preprocessor/float-control.md), [fenv_access](../../preprocessor/fenv-access.md)und [fp_contract](../../preprocessor/fp-contract.md). Sie können diese Direktiven verwenden, um Gleit Komma Verhalten auf Funktionsebene und nicht innerhalb einer Funktion zu steuern. Beachten Sie, dass diese Anweisungen nicht direkt mit den `/fp` Optionen übereinstimmen. Diese Tabelle zeigt, wie die `/fp` Optionen und pragma-Direktiven einander zugeordnet werden. Weitere Informationen finden Sie in der Dokumentation für die einzelnen Optionen und pragma-Direktiven.

| Option | float_control (präzise) | float_control (außer) | fenv_access | fp_contract |
|-|-|-|-|-|
|`/fp:fast`|aus|aus|aus|on|
|`/fp:precise`|on|aus|aus|on|
|`/fp:strict`|on|on|on|aus|

### <a name="the-default-floating-point-environment"></a>Die standardmäßige Gleit Komma Umgebung

Wenn ein Prozess initialisiert wird, wird die standardmäßige Gleit *Komma Umgebung* festgelegt. In dieser Umgebung werden alle Gleit Komma Ausnahmen maskiert, der Rundungs Modus auf "Next ()" gerundet `FE_TONEAREST` , subnormale Werte (DENORMAL) beibehalten, die Standardgenauigkeit von "signifiand (Mantisse)" für die Werte, und festgelegt **`float`** **`double`** , und **`long double`** Wenn unterstützt, wird das Unendlichkeits Steuerelement auf den standardmäßigen affinen Modus festgelegt.

### <a name="floating-point-environment-access-and-modification"></a>Zugreifen auf und Ändern von Gleit Komma Umgebungen

Die Microsoft Visual C++-Laufzeit stellt mehrere Funktionen für den Zugriff auf und die Änderung der Gleit Komma Umgebung bereit. Hierzu gehören [_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md), [_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)und [_statusfp](../../c-runtime-library/reference/status87-statusfp-statusfp2.md) und deren Varianten. Um ein korrektes Programmverhalten zu gewährleisten, wenn Ihr Code auf die Gleit Komma Umgebung zugreift oder diese ändert, `fenv_access` muss entweder durch die- `/fp:strict` Option oder durch Verwendung des-Pragmas aktiviert werden, `fenv_access` damit diese Funktionen wirksam werden. Wenn `fenv_access` nicht aktiviert ist, kann der Zugriff oder die Änderung der Gleit Komma Umgebung zu unerwartetem Programmverhalten führen: der Code berücksichtigt möglicherweise angeforderte Änderungen an der Gleit Komma Umgebung nicht. die Gleit Komma Statusregister melden möglicherweise keine erwarteten oder aktuellen Ergebnisse, und es können unerwartete Gleit Komma Ausnahmen auftreten, oder es treten möglicherweise keine Gleit Komma Ausnahmen auf.

Wenn Ihr Code auf die Gleit Komma Umgebung zugreift oder diese ändert, müssen Sie vorsichtig sein, wenn Sie Code kombinieren, bei dem `fenv_access` mit nicht aktiviertem Code aktiviert ist `fenv_access` . Im Code, in dem `fenv_access` nicht aktiviert ist, geht der Compiler davon aus, dass die standardmäßige Gleit Komma Umgebung der Plattform aktiviert ist und dass auf den Gleit Komma Status nicht zugegriffen oder geändert wird. Es wird empfohlen, dass Sie die lokale Gleit Komma Umgebung speichern und in Ihrem Standardzustand wiederherstellen, bevor die Steuerung an eine Funktion übertragen wird, die nicht `fenv_access` aktiviert ist. In diesem Beispiel wird veranschaulicht, wie das `float_control` pragma festgelegt und wieder hergestellt werden kann:

```cpp
#pragma float_control(strict, on, push)
// Code that uses /fp:strict mode
#pragma float_control(pop)
```

### <a name="floating-point-rounding-modes"></a>Gleit Komma-Rundungs Modi

Sowohl `/fp:precise` als auch `/fp:fast` der Compiler generiert Code, der in der standardmäßigen Gleit Komma Umgebung ausgeführt werden soll, und geht davon aus, dass die Umgebung nicht zur Laufzeit aufgerufen oder geändert wird. Das heißt, es wird davon ausgegangen, dass der Code keine Gleit Komma Ausnahmen, Lese-oder Schreibvorgänge von Gleit Komma Status Registern oder die Rundungs Modi ändert.  Allerdings müssen einige Programme die Gleit Komma Umgebung ändern. In diesem Beispiel werden z. b. Fehler Begrenzungen einer Gleit Komma Multiplikation berechnet, indem Gleit Komma-Rundungs Modi geändert werden:

```cpp
// fp_error_bounds.cpp
#include <iostream>
#include <limits>
using namespace std;

int main(void)
{
    float a = std::<float>::max();
    float b = -1.1;
    float cLower = 0.0;
    float cUpper = 0.0;
    unsigned int control_word = 0;
    int err = 0;

    // compute lower error bound.
    // set rounding mode to -infinity.
    err = _controlfp_s(&control_word, _RC_DOWN, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_DOWN, _MCW_RC) failed with error:" << err << endl;
    }  
    cLower = a * b;

    // compute upper error bound.
    // set rounding mode to +infinity.
    err = _controlfp_s(&control_word, _RC_UP, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_UP, _MCW_RC) failed with error:" << err << endl;
    }
    cUpper = a * b;

    // restore default rounding mode.
    err = _controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC) failed with error:" << err << endl;
    }
    // display error bounds.
    cout << "cLower = " << cLower << endl;
    cout << "cUpper = " << cUpper << endl;
    return 0;
}
```

Da der Compiler die standardmäßige Gleit Komma Umgebung unter annimmt, `/fp:fast` `/fp:precise` ist es möglich, die Aufrufe von zu ignorieren `_controlfp_s` . Wenn beispielsweise sowohl mit `/O2` als auch mit `/fp:precise` der x86-Architektur kompiliert werden, werden die Begrenzungen nicht berechnet, und das Beispielprogramm gibt Folgendes aus:

```Output
cLower = -inf
cUpper = -inf
```

Bei der Kompilierung von `/O2` und `/fp:strict` für die x86-Architektur gibt das Beispielprogramm Folgendes aus:

```Output
cLower = -inf
cUpper = -3.40282e+38
```

### <a name="floating-point-special-values"></a>Gleit Komma-Sonderwerte

Unter `/fp:precise` und `/fp:strict` Verhalten sich Ausdrücke, die spezielle Werte (NaN, + unendlich,-unendlich,-0,0) betreffen, gemäß den IEEE-754-Spezifikationen. Unter `/fp:fast` ist das Verhalten dieser speziellen Werte möglicherweise inkonsistent mit IEEE-754.

Dieses Beispiel veranschaulicht das unterschiedliche Verhalten von speziellen Werten unter `/fp:precise` , `/fp:strict` und `/fp:fast` :

```cpp
// fp_special_values.cpp
#include <stdio.h>
#include <cmath>

float gf0 = -0.0;

int main()
{
    float f1 = INFINITY;
    float f2 = NAN;
    float f3 = -INFINITY;
    bool a, b;
    float c, d, e;
    a = (f1 == f1);
    b = (f2 == f2);
    c = (f1 - f1);
    d = (f2 - f2);
    printf("INFINITY == INFINITY : %d\n", a);
    printf("NAN == NAN           : %d\n", b);
    printf("INFINITY - INFINITY  : %f\n", c);
    printf("NAN - NAN            : %f\n", d);

    e = gf0 / abs(f3);
    printf("std::signbit(-0.0/-INFINITY): %d\n", std::signbit(c));
    return 0;
}
```

Bei der Kompilierung mit `/O2` `/fp:precise` oder `/O2` `/fp:strict` für die x86-Architektur entsprechen die Ausgaben der IEEE-754-Spezifikation:

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 0
INFINITY - INFINITY  : -nan(ind)
NAN - NAN            : -nan(ind)
std::signbit(-0.0/-INFINITY): 1
```

Bei der Kompilierung mit `/O2` `/fp:fast` für die x86-Architektur sind die Ausgaben nicht mit IEEE-754 konsistent:

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 1
INFINITY - INFINITY  : 0.000000
NAN - NAN            : 0.000000
std::signbit(-0.0/-INFINITY): 0
```

### <a name="floating-point-algebraic-transformations"></a>Gleit Komma-algebraische Transformationen

Unter `/fp:precise` und führt `/fp:strict` der Compiler keine mathematischen Transformationen aus, es sei denn, die Transformation erzeugt ein bitweises identisches Ergebnis. Der Compiler kann solche Transformationen unter Ausführen `/fp:fast` . Beispielsweise kann der Ausdruck `a * b + a * c` in der Beispiel Funktion `algebraic_transformation` in unter kompiliert werden `a * (b + c)` `/fp:fast` . Solche Transformationen werden unter oder nicht ausgeführt `/fp:precise` `/fp:strict` , und der Compiler generiert `a * b + a * c` .

```cpp
float algebraic_transformation (float a, float b, float c)
{
    return a * b + a * c;
}
```

### <a name="floating-point-explicit-casting-points"></a>Explizite Gleit Komma-Umwandlungs Punkte

Unter `/fp:precise` und `/fp:strict` rundet der Compiler die Quell Code Genauigkeit an vier bestimmten Punkten während der Ausdrucks Auswertung ab: bei der Zuweisung an Typecasts, bei der Übergabe eines Gleit Komma Arguments an einen Funktions aufzurufen und bei Rückgabe eines Gleit Komma Werts von einem Funktions Aufruf. Typecasts können verwendet werden, um Zwischenberechnungen explizit zu runden. Unter `/fp:fast` generiert der Compiler keine expliziten Umwandlungen an diesen Punkten, um die Genauigkeit des Quellcodes zu gewährleisten. Dieses Beispiel veranschaulicht das Verhalten unter verschiedenen `/fp` Optionen:

```cpp
float casting(float a, float b)
{
    return 5.0*((double)(a+b));
}
```

Wenn Sie mithilfe von `/O2` `/fp:precise` oder kompiliert `/O2` `/fp:strict` werden, sehen Sie, dass explizite Typumwandlungen sowohl am Typ-als auch am Funktions Rückgabe Punkt im generierten Code für die x64-Architektur eingefügt werden:

```asm
        addss    xmm0, xmm1
        cvtss2sd xmm0, xmm0
        mulsd    xmm0, QWORD PTR __real@4014000000000000
        cvtsd2ss xmm0, xmm0
        ret      0
```

Unter `/O2` `/fp:fast` dem generierten Code wurde vereinfacht, da alle Typumwandlungen entfernt werden:

```asm
        addss    xmm0, xmm1
        mulss    xmm0, DWORD PTR __real@40a00000
        ret      0
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie die **Eigenschaften Seite Konfigurations Eigenschaften**  >  **C/C++-**  >  **Code Generierung** aus.

1. Ändern Sie die Eigenschaft Gleit **Komma Modell** .

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)<br/>
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)<br/>

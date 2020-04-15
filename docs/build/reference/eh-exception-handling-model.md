---
title: /EH (Ausnahmebehandlungsmodell)
ms.date: 08/14/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExceptionHandling
- /eh
- VC.Project.VCCLCompilerTool.ExceptionHandling
helpviewer_keywords:
- exception handling, compiler model
- cl.exe compiler, exception handling
- EH compiler option [C++]
- -EH compiler option [C++]
- /EH compiler option [C++]
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: 8546b14995317afb57e4cc23a5d6f81c2172a1a6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328296"
---
# <a name="eh-exception-handling-model"></a>/EH (Ausnahmebehandlungsmodell)

Gibt die Art der Ausnahmebehandlung an, die vom Compiler verwendet werden soll, gibt an, ob Ausnahmeprüfungen wegoptimiert werden sollen, und gibt an, ob C++-Objekte zerstört werden sollen, die sich aufgrund einer Ausnahme nicht mehr im Gültigkeitsbereich befinden. Wenn **/EH** nicht angegeben ist, ermöglicht der Compiler dem Code, sowohl asynchrone strukturierte Ausnahmen als auch C++-Ausnahmen abzufangen, zerstört jedoch keine C++-Objekte, die aufgrund einer asynchronen Ausnahme aus dem Gültigkeitsbereich verschwinden.

## <a name="syntax"></a>Syntax

> **/EH**{**s**|**a**}[**c**][**r**][**-**]

## <a name="arguments"></a>Argumente

**Eine**<br/>
Das Ausnahmebehandlungsmodell, das sowohl asynchrone (strukturierte) als auch synchrone (C++) Ausnahmen mithilfe der C++-Syntax `catch(...)` abfängt.

**s**<br/>
Das Ausnahmebehandlungsmodell, das nur synchrone (C++) Ausnahmen abfängt und den Compiler anweist, davon auszugehen, dass Funktionen, die als **extern "C"** deklariert wurden, eine Ausnahme auslösen können.

**C**<br/>
Wenn mit **s** (**/EHsc**) verwendet wird, werden nur C++-Ausnahmen abgefangen und der Compiler angewiesen anzunehmen, dass als **externes "C"** deklarierte Funktionen niemals eine C++-Ausnahme auslösen. **/EHca** entspricht **/EHa**.

**R**<br/>
Weist den Compiler an, immer Laufzeitbeendigungsprüfungen für alle **noexcept-Funktionen** zu generieren. Standardmäßig können Laufzeitprüfungen auf **noexcept** entfernt optimiert werden, wenn der Compiler bestimmt, dass die Funktion nur nicht auslösende Funktionen aufruft.

## <a name="remarks"></a>Bemerkungen

Die Compileroption **/EHa** unterstützt die asynchrone strukturierte Ausnahmebehandlung (Structured Exception Handling, SEH) mit der systemeigenen C++-Klausel `catch(...)` . Um SEH zu implementieren, ohne **/EHa**anzugeben, können Sie die **Syntax __try**, **__except**und **__finally** verwenden. SEH wird zwar von Windows und Visual C++ unterstützt, trotzdem ist die Verwendung der ISO-Standard-C++-Ausnahmebehandlung (**/EHs** oder **/EHsc**) empfehlenswert, da Code damit besser portierbar und flexibler ist. Dennoch müssen Sie in vorhandenem Code oder für bestimmte Arten von Programmen, z. B. in Code, der zur Unterstützung der Common Language Runtime ([/clr (Common Language Runtime Compilation) )](clr-common-language-runtime-compilation.md)) kompiliert wurde, SEH möglicherweise noch verwenden. Weitere Informationen finden Sie unter [Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md).

Die Angabe von **/EHa** und der Versuch, alle Ausnahmen mit `catch(...)` zu behandeln, kann riskant sein. Da asynchrone Ausnahmen größtenteils nicht behebbar sind, gelten sie als schwerwiegende Ausnahmen. Wenn Sie sie abfangen und den Prozess anschließend fortsetzen, können Beschädigungen und Fehler auftreten, die schwer zu finden und zu beheben sind.

Wenn Sie **/EHs** oder **/EHsc**verwenden, werden durch die `catch(...)` -Klausel keine asynchronen strukturierten Ausnahmen abgefangen. Zugriffverletzungen und verwaltete <xref:System.Exception?displayProperty=fullName> -Ausnahmen werden nicht abgefangen, und beim Erzeugen von asynchronen Ausnahmen werden Objekte im Gültigkeitsbereich nicht beschädigt, auch dann nicht, wenn die asynchrone Ausnahme behandelt wird.

Wenn Sie **/EHa**verwenden, ist das Image möglicherweise größer und funktioniert möglicherweise weniger gut, da der Compiler einen **Try-Block** nicht so aggressiv optimiert. Außerdem bewirkt es ein Verlassen in Ausnahmefiltern, die automatisch die Destruktoren aller lokalen Objekte aufrufen, und zwar selbst dann, wenn der Compiler keinen Code feststellt, der eine C++-Ausnahme auslösen kann. Dies ermöglicht sichere Stapelentladungen für asynchrone Ausnahmen sowie für C++-Ausnahmen. Wenn Sie **/EHs**verwenden, geht der Compiler davon aus, dass Ausnahmen nur bei einer **throw-Anweisung** oder bei einem Funktionsaufruf auftreten können. Damit kann der Compiler Code für die Lebensdauerverfolgung vieler nicht entladbarer Objekte entfernen, wodurch sich die Codegröße u. U. deutlich reduziert.

Es wird empfohlen, Objekte, die mithilfe von **/EHa** kompiliert wurden, nicht mit Objekten zu verknüpfen, die mithilfe von **/EHs** oder **/EHsc** im gleichen ausführbaren Modul kompiliert wurden. Wenn Sie eine asynchrone Ausnahme behandeln müssen, indem Sie **/EHa** an einer beliebigen Position innerhalb des Moduls verwenden, kompilieren Sie mithilfe von **/EHa** den gesamten Code im Modul. Sie können strukturierte Ausnahmebehandlungssyntax im selben Modul wie Code verwenden, der mithilfe von **/EHs**kompiliert wird, aber Sie können die SEH-Syntax nicht mit **try**, **throw**und **catch** in derselben Funktion mischen.

Verwenden Sie **/EHa,** wenn Sie eine Ausnahme abfangen möchten, die durch etwas anderes als einen **Wurf**ausgelöst wird. Im nachfolgenden Beispiel wird eine strukturierte Ausnahme generiert und abgefangen:

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail() {   // generates SE and attempts to catch it using catch(...)
   try {
      int i = 0, j = 1;
      j /= i;   // This will throw a SE (divide by zero).
      printf("%d", j);
   }
   catch(...) {   // catch block will only be executed under /EHa
      cout<<"Caught an exception in catch(...)."<<endl;
   }
}

int main() {
   __try {
      fail();
   }

   // __except will only catch an exception here
   __except(EXCEPTION_EXECUTE_HANDLER) {
      // if the exception was not caught by the catch(...) inside fail()
      cout << "An exception was caught in __except." << endl;
   }
}
```

Für die **/EHc** -Option muss **/EHs** oder **/EHa** angegeben sein. Die Option **/clr** impliziert **/EHa** (d. h., **/clr** **/EHa** ist redundant). Der Compiler generiert einen Fehler, wenn **/EHs** oder **/EHsc** nach **/clr**verwendet wird. Optimierungen haben auf dieses Verhalten keinen Einfluss. Wenn die Ausnahme abgefangen wird, werden vom Compiler die Klassendestruktoren für die Objekte aufgerufen, die sich in demselben Gültigkeitsbereich wie die Ausnahme befinden. Wenn eine Ausnahme nicht abgefangen wird, werden diese Destruktoren nicht ausgeführt.

Weitere Informationen über Beschränkungen für die Ausnahmebehandlung unter **/clr**finden Sie unter [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md).

Die Option kann mit dem **-** Symbol gelöscht werden. Beispielsweise wird **/EHsc-** als **/EHs** **/EHc-** interpretiert und entspricht **/EHs**.

Die Compileroption **/EHr** erzwingt Die Laufzeitbeendigungsüberprüfung aller Funktionen, die über ein **noexcept-Attribut** verfügen. Standardmäßig können Laufzeitprüfungen wegoptimiert werden, wenn das Compiler-Back-End feststellt, dass eine Funktion nur *nicht auslösende* Funktionen aufruft. Nicht auslösende Funktionen sind alle Funktionen, die ein Attribut haben, das angibt, dass keine Ausnahmen ausgelöst werden können. Dazu gehören Funktionen, `throw()`die `__declspec(nothrow)`als **noexcept**, , und, wenn **/EHc** angegeben ist, **externe "C"-Funktionen.** Zu den nicht auslösenden Funktionen gehört auch jede Funktion, für die der Compiler durch Prüfung ermittelt hat, dass sie nicht auslösend ist. Sie können die Standardeinstellung explizit mit **/EHr-** festlegen.

Das Attribut für nicht auslösend bedingt jedoch keine Garantie, dass von einer Funktion keine Ausnahmen ausgelöst werden können. Im Gegensatz zum Verhalten einer **noexcept-Funktion** betrachtet der MSVC-Compiler eine Ausnahme, die von einer Funktion ausgelöst wird, die mit `throw()`, `__declspec(nothrow)`oder extern **"C"** deklariert wird, als nicht definiertes Verhalten. Funktionen, für die diese drei Deklarationsattribute verwendet werden, erzwingen keine Laufzeitbeendigungsprüfungen für Ausnahmen. Sie können die Option **/EHr** verwenden, um dieses nicht definierte Verhalten zu identifizieren, indem Sie den Compiler zwingen, Laufzeitprüfungen für nicht behandelte Ausnahmen zu generieren, die einer **noexcept-Funktion** entfliehen.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie **Konfigurationseigenschaften** > **C/C++** > **Codegenerierung**aus.

1. Ändern Sie die Eigenschaft **C++-Ausnahmen aktivieren** .

   Oder legen Sie den Wert für **C++-Ausnahmen aktivieren** auf **Nein**fest, und fügen Sie dann auf der Eigenschaftenseite **Befehlszeile** im Feld **Zusätzliche Optionen** die Compileroption hinzu.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)<br/>
[Syntax für die MSVC-Compilerbefehlszeile](compiler-command-line-syntax.md)<br/>
[Behandeln von Fehlern und Ausnahmen](../../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Ausnahmespezifikationen (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)

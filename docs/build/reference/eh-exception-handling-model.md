---
title: /EH (Ausnahmebehandlungsmodell)
description: Referenzhandbuch zu den Microsoft C++ /EH -Compileroptionen (Ausnahmebehandlungsmodell) in Visual Studio.
ms.date: 04/14/2020
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
no-loc:
- SEH
- try
- catch
- throw
- extern
- finally
- noexcept
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: 68d6af657e7c20c0f5e84674dd91803beb35fba0
ms.sourcegitcommit: 0e4feb35b47c507947262d00349d4a893863a6d3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2020
ms.locfileid: "81396289"
---
# <a name="eh-exception-handling-model"></a>/EH (Ausnahmebehandlungsmodell)

Gibt die vom Compiler generierte Unterstützung für die Ausnahmebehandlungsmodellanmundungen an. Argumente geben an, ob Syntax sowohl auf strukturierte als auch auf Standard-C++-Ausnahmen angewendet `catch(...)` werden soll, ob throw **noexcept** ** extern "C"-Code** für Ausnahmen angenommen wird und ob bestimmte Prüfungen optimiert werden sollen.

## <a name="syntax"></a>Syntax

> **`/EHa`**[**`-`**]\
> **`/EHs`**[**`-`**]\
> **`/EHc`**[**`-`**]\
> **`/EHr`**[**`-`**]

## <a name="arguments"></a>Argumente

**`a`**\
Ermöglicht das Entladungsprogramm des Standard-C++-Stacks. Fängt sowohl strukturierte (asynchrone) als auch standardmäßige C++-Ausnahmen (synchron) ab, wenn Sie Syntax verwenden. `catch(...)` **`/EHa`** überschreibt **`/EHs`** beide **`/EHc`** argumente.

**`s`**\
Ermöglicht das Entladungsprogramm des Standard-C++-Stacks. Fängt nur Standard-C++-Ausnahmen `catch(...)` ab, wenn Sie Syntax verwenden. Sofern **`/EHc`** nicht auch angegeben, geht der Compiler davon throw aus, dass als ** extern "C"** deklarierte Funktionen eine C++-Ausnahme sein können.

**`c`**\
Bei Verwendung **`/EHs`** mit geht der Compiler davon aus, dass als ** extern "C"** deklarierte Funktionen niemals throw eine C++-Ausnahme darstellen. Es hat keine Wirkung **`/EHa`** bei Verwendung **`/EHca`** mit **`/EHa`**(d. h. entspricht ) . **`/EHc`** wird ignoriert, wenn **`/EHs`** angegeben oder **`/EHa`** nicht angegeben.

**`r`**\
Weist den Compiler an, immer Laufzeitbeendigungsprüfungen für alle **noexcept** Funktionen zu generieren. Standardmäßig kann die Laufzeitprüfung für **noexcept** das Nicht-Auslösen von Funktionen entfernt optimiert werden, wenn der Compiler bestimmt, dass die Funktion nur nicht auslösende Funktionen aufruft. Diese Option bietet eine strikte C++-Konformität auf Kosten von zusätzlichem Code. **`/EHr`** wird ignoriert, wenn **`/EHs`** angegeben oder **`/EHa`** nicht angegeben.

**`-`**\
Löscht das vorherige Optionsargument. Wird z. B. **`/EHsc-`** als **`/EHs /EHc-`** interpretiert **`/EHs`** und entspricht .

**`/EH`** Argumente können separat oder in beliebiger Reihenfolge angegeben oder kombiniert werden. Wenn mehr als eine Instanz desselben Arguments angegeben wird, überschreibt die letzte Instanz alle früheren.  Beispielsweise **`/EHr- /EHc /EHs`** ist die gleiche **`/EHscr-`** wie **`/EHscr- /EHr`** , und **`/EHscr`** hat den gleichen Effekt wie .

## <a name="remarks"></a>Bemerkungen

### <a name="default-exception-handling-behavior"></a>Standard-Ausnahmebehandlungsverhalten

Der Compiler generiert immer Code, der asynchrone strukturierte Ausnahmebehandlung (SEHunterstützt). Standardmäßig (d. h., **`/EHs`** wenn **`/EHa`** keine **`/EHsc`**, oder SEH Option angegeben ist) unterstützt `catch(...)` der Compiler Handler in der systemeigenen C++-Klausel. Es generiert jedoch auch Code, der C++-Ausnahmen nur teilweise unterstützt. Der standardmäßige Sperrcode für das Entladen von Ausnahmen [try](../../cpp/try-throw-and-catch-statements-cpp.md) zerstört keine automatischen C++-Objekte außerhalb von Blöcken, die aufgrund einer Ausnahme nicht in den Gültigkeitsbereich fallen. Ressourcenlecks und undefiniertes Verhalten können auftreten, wenn eine C++-Ausnahme ausgelöst wird.

### <a name="standard-c-exception-handling"></a>Standard-C++-Ausnahmebehandlung

Vollständige Compilerunterstützung für das Standard-C++-Ausnahmebehandlungsmodell, **`/EHsc`** das **`/EHs`** Stackobjekte **`/EHa`** sicher auflöst (empfohlen), oder .

Wenn Sie **`/EHs`** **`/EHsc`** oder verwenden, verwenden `catch(...)` Ihre catch Klauseln keine asynchronen strukturierten Ausnahmen. Alle Zugriffsverletzungen und <xref:System.Exception?displayProperty=fullName> verwalteten Ausnahmen werden nicht abgefangen. Und Objekte im Gültigkeitsbereich, wenn eine asynchrone Ausnahme auftritt, werden nicht zerstört, auch wenn der Code die asynchrone Ausnahme behandelt. Dieses Verhalten ist ein Argument dafür, strukturierte Ausnahmen nicht zu behandeln. Betrachten Sie diese Ausnahmen stattdessen als schwerwiegend.

Wenn Sie **`/EHs`** **`/EHsc`** oder verwenden, geht der Compiler davon **throw** aus, dass Ausnahmen nur bei einer Anweisung oder bei einem Funktionsaufruf auftreten können. Diese Annahme ermöglicht es dem Compiler, Code für die Nachverfolgung der Lebensdauer vieler nicht verwindbarer Objekte zu eliminieren, wodurch die Codegröße erheblich reduziert werden kann. Wenn Sie **`/EHa`** verwenden, ist das ausführbare Image möglicherweise größer **try** und langsamer, da der Compiler Blöcke nicht so aggressiv optimiert. Außerdem werden Ausnahmefilter angezeigt, die lokale Objekte automatisch bereinigen, auch wenn throw der Compiler keinen Code sieht, der eine C++-Ausnahme darstellen kann.

### <a name="structured-and-standard-c-exception-handling"></a>Strukturierte und standardmäßige C++-Ausnahmebehandlung

Die **`/EHa`** Compileroption ermöglicht das abwickeln des sicheren Stapels sowohl für asynchrone Ausnahmen als auch für C++-Ausnahmen. Es unterstützt die Handhabung sowohl von Standard-C++- als `catch(...)` auch von strukturierten Ausnahmen mithilfe der systemeigenen C++-Klausel. Zum SEH Implementieren ohne **`/EHa`** Angabe von können Sie die **Syntax __try**, **__except**und **__finally** verwenden. Weitere Informationen finden Sie unter [Strukturierte Ausnahmebehandlung](../../cpp/structured-exception-handling-c-cpp.md).

> [!IMPORTANT]
> Das **`/EHa`** Angeben und Versuchen, alle `catch(...)` Ausnahmen mithilfe von Ausnahmen zu behandeln, kann gefährlich sein. Da asynchrone Ausnahmen größtenteils nicht behebbar sind, gelten sie als schwerwiegende Ausnahmen. Wenn Sie sie abfangen und den Prozess anschließend fortsetzen, können Beschädigungen und Fehler auftreten, die schwer zu finden und zu beheben sind.
>
> Obwohl Windows und Visual C++ unterstützen, SEHwird dringend empfohlen, die Iso-Standard-C++-Ausnahmebehandlung (**`/EHsc`** oder **`/EHs`**) zu verwenden. Es macht Ihren Code tragbarer und flexibler. Es kann immer noch Zeiten SEH geben, die Sie in Legacy-Code oder für bestimmte Arten von Programmen verwenden müssen. Es ist in Code erforderlich, der kompiliert wird, um z. B. die Common Language Runtime ([/clr](clr-common-language-runtime-compilation.md)) zu unterstützen. Weitere Informationen finden Sie unter [Strukturierte Ausnahmebehandlung](../../cpp/structured-exception-handling-c-cpp.md).
>
> Es wird empfohlen, Objektdateien, **`/EHa`** die mithilfe von **`/EHs`** Dateien **`/EHsc`** kompiliert werden, die mit oder in demselben ausführbaren Modul kompiliert wurden, niemals zu verknüpfen. Wenn Sie eine asynchrone Ausnahme **`/EHa`** mithilfe einer beliebigen **`/EHa`** Stelle in Ihrem Modul behandeln müssen, verwenden Sie diese, um den gesamten Code im Modul zu kompilieren. Sie können strukturierte Ausnahmebehandlungssyntax im selben Modul wie Code **`/EHs`** verwenden, der mithilfe von kompiliert wird. Sie können SEH die Syntax jedoch nicht mit **try** **throw** C++ , und **catch** in derselben Funktion mischen.

Verwenden **`/EHa`** Sie diese catch Verwendung, wenn Sie eine Ausnahme **throw** verwenden möchten, die von etwas anderem als einer ausgelöst wird. Im nachfolgenden Beispiel wird eine strukturierte Ausnahme generiert und abgefangen:

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail()
{
    // generates SE and attempts to catch it using catch(...)
    try
    {
        int i = 0, j = 1;
        j /= i;   // This will throw a SE (divide by zero).
        printf("%d", j);
    }
    catch(...)
    {
        // catch block will only be executed under /EHa
        cout << "Caught an exception in catch(...)." << endl;
    }
}

int main()
{
    __try
    {
        fail();
    }

    // __except will only catch an exception here
    __except(EXCEPTION_EXECUTE_HANDLER)
    {
        // if the exception was not caught by the catch(...) inside fail()
        cout << "An exception was caught in __except." << endl;
    }
}
```

### <a name="exception-handling-under-clr"></a>Ausnahmebehandlung unter /clr

Die **`/clr`** Option **`/EHa`** impliziert (d. h., **`/clr /EHa`** ist redundant). Der Compiler generiert **`/EHs`** einen **`/EHsc`** Fehler, **`/clr`** wenn oder wird er nach verwendet. Optimierungen wirken sich nicht auf dieses Verhalten aus. Wenn eine Ausnahme abgefangen wird, ruft der Compiler die Klassendestruktoren für alle Objekte auf, die sich im gleichen Bereich wie die Ausnahme befinden. Wenn keine Ausnahme abgefangen wird, werden diese Destruktoren nicht ausgeführt.

Informationen zu Ausnahmebehandlungseinschränkungen **`/clr`** finden Sie unter [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md).

### <a name="runtime-exception-checks"></a>Laufzeit-Ausnahmeprüfungen

Die **`/EHr`** Option erzwingt Die Laufzeitbeendigungsprüfungen **noexcept** in allen Funktionen, die über ein Attribut verfügen. Standardmäßig können Laufzeitprüfungen entfernt optimiert werden, wenn das Compiler-Back-End feststellt, dass eine Funktion nur *nicht auslösende* Funktionen aufruft. Nicht auslösende Funktionen sind alle Funktionen, die ein Attribut haben, das angibt, dass keine Ausnahmen ausgelöst werden können. Sie enthalten **noexcept** Funktionen, `__declspec(nothrow)`die mit **`/EHc`** , `throw()`, und, wenn angegeben, ** extern "C"-Funktionen** gekennzeichnet sind. Zu den nicht auslösenden Funktionen gehört auch jede Funktion, für die der Compiler durch Prüfung ermittelt hat, dass sie nicht auslösend ist. Sie können das Standardverhalten **`/EHr-`** explizit festlegen, indem Sie verwenden.

Ein nicht auslösendes Attribut ist keine Garantie dafür, dass Ausnahmen nicht von einer Funktion ausgelöst werden können. Im Gegensatz zum **noexcept** Verhalten einer Funktion betrachtet der MSVC-Compiler `throw()` `__declspec(nothrow)`eine Ausnahme, die von einer Funktion ausgelöst wird, die mit , oder ** extern "C"** deklariert wird, als nicht definiertes Verhalten. Funktionen, die diese drei Deklarationsattribute verwenden, erzwingen keine Laufzeitbeendigungsprüfungen für Ausnahmen. Sie können **`/EHr`** die Option verwenden, um dieses nicht definierte Verhalten zu identifizieren, indem Sie den **noexcept** Compiler zwingen, Laufzeitprüfungen für nicht behandelte Ausnahmen zu generieren, die einer Funktion entfliehen.

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Festlegen der Option in Visual Studio oder programmgesteuert

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie **Konfigurationseigenschaften** > **C/C++** > **Codegenerierung**aus.

1. Ändern Sie die Eigenschaft **C++-Ausnahmen aktivieren** .

   Oder legen Sie den Wert für **C++-Ausnahmen aktivieren** auf **Nein**fest, und fügen Sie dann auf der Eigenschaftenseite **Befehlszeile** im Feld **Zusätzliche Optionen** die Compileroption hinzu.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)\
[MSVC Compiler-Befehlszeilensyntax](compiler-command-line-syntax.md)\
[Fehler- und Ausnahmebehandlung](../../cpp/errors-and-exception-handling-modern-cpp.md)\
[Ausnahmespezifikationenthrow( )](../../cpp/exception-specifications-throw-cpp.md)\
[Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)

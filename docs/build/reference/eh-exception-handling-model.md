---
title: /EH (Ausnahmebehandlungsmodell)
description: Referenzhandbuch zu den Compileroptionen für Microsoft C++/EH (Ausnahme Behandlungsmodell) in Visual Studio.
ms.date: 08/25/2020
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
ms.openlocfilehash: 0d18d0f1d73b1de46b12262deecb2436c34e6176
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898384"
---
# <a name="eh-exception-handling-model"></a>`/EH` (Ausnahme Behandlungsmodell)

Gibt die vom Compiler generierte Ausnahme Behandlungsmodell Unterstützung an. Mit Argumenten wird angegeben, ob eine `catch(...)` Syntax auf strukturierte und standardmäßige C++-Ausnahmen angewendet werden soll, ob ** extern "C"** -Code throw Ausnahmen angenommen werden und ob bestimmte Überprüfungen entfernt werden sollen **`noexcept`** .

## <a name="syntax"></a>Syntax

> **`/EHa`**[**`-`**]\
> **`/EHs`**[**`-`**]\
> **`/EHc`**[**`-`**]\
> **`/EHr`**[**`-`**]

## <a name="arguments"></a>Argumente

**`a`**\
Aktiviert die standardmäßige C++-Stapel Entwicklung. Fängt bei Verwendung von Syntax sowohl strukturierte (asynchrone) als auch C++ (synchrone) Standard Ausnahmen ab `catch(...)` . **`/EHa`** Überschreibt beide **`/EHs`** -und- **`/EHc`** Argumente.

**`s`**\
Aktiviert die standardmäßige C++-Stapel Entwicklung. Fängt nur bei Verwendung von Syntax Standard-C++-Ausnahmen ab `catch(...)` . Sofern nicht **`/EHc`** auch angegeben wird, geht der Compiler davon aus, dass als ** extern "C"** deklarierte Funktionen throw eine C++-Ausnahme darstellen dürfen.

**`c`**\
Bei Verwendung mit **`/EHs`** geht der Compiler davon aus, dass Funktionen, die als ** extern "C"** deklariert sind, niemals throw eine C++-Ausnahme sind. Sie hat keine Auswirkung, wenn Sie mit verwendet wird **`/EHa`** (das heißt, **`/EHca`** ist äquivalent zu **`/EHa`** ). **`/EHc`** wird ignoriert, wenn **`/EHs`** oder **`/EHa`** nicht angegeben ist.

**`r`**\
Weist den Compiler an, immer Lauf Zeit Beendigungs Prüfungen für alle Funktionen zu generieren **`noexcept`** . Standardmäßig können Lauf Zeit Prüfungen für **`noexcept`** optimiert werden, wenn der Compiler feststellt, dass die Funktion nur Funktionen aufruft, die keine throw Funktionen sind. Diese Option bietet strikte C++-Konformität mit den Kosten für zusätzlichen Code. **`/EHr`** wird ignoriert, wenn **`/EHs`** oder **`/EHa`** nicht angegeben ist.

**`-`**\
Löscht das vorherige options Argument. Beispielsweise **`/EHsc-`** wird als interpretiert **`/EHs /EHc-`** , und entspricht **`/EHs`** .

**`/EH`** Argumente können in beliebiger Reihenfolge separat oder kombiniert angegeben werden. Wenn mehr als eine Instanz desselben Arguments angegeben wird, überschreibt der letzte alle früheren Instanzen.  Beispielsweise **`/EHr- /EHc /EHs`** ist identisch mit **`/EHscr-`** und **`/EHscr- /EHr`** hat denselben Effekt wie **`/EHscr`** .

## <a name="remarks"></a>Hinweise

### <a name="default-exception-handling-behavior"></a>Standardverhalten bei der Ausnahmebehandlung

Der Compiler generiert immer Code, der die asynchrone strukturierte Ausnahmebehandlung () unterstützt SEH . Wenn keine **`/EHsc`** ,- **`/EHs`** oder- **`/EHa`** Option angegeben ist, unterstützt der Compiler standardmäßig SEH Handler in der nativen C++- `catch(...)` Klausel. Es generiert jedoch auch Code, der nur teilweise C++-Ausnahmen unterstützt. Der standardmäßige Entwicklungscode für Ausnahmen zerstört keine automatischen C++-Objekte außerhalb von [`try`](../../cpp/try-throw-and-catch-statements-cpp.md) Blöcken, die aufgrund einer Ausnahme außerhalb des Gültigkeits Bereichs liegen. Ressourcen Lecks und undefiniertes Verhalten können ergeben, wenn eine C++-Ausnahme throw n ist.

### <a name="standard-c-exception-handling"></a>Standard mäßige C++-Ausnahmebehandlung

Vollständige Compilerunterstützung für das Standard mäßige C++-Ausnahme Behandlungsmodell, das Stapel Objekte sicher entlädt, erfordert **`/EHsc`** (empfohlen), **`/EHs`** oder **`/EHa`** .

Wenn Sie **`/EHs`** oder verwenden **`/EHsc`** , dann sind Ihre- `catch(...)` Klauseln keine catch asynchronen strukturierten Ausnahmen. Alle Zugriffs Verletzungen und verwalteten <xref:System.Exception?displayProperty=fullName> Ausnahmen werden nicht abgefangen. Außerdem werden Objekte im Bereich, wenn eine asynchrone Ausnahme auftritt, nicht zerstört, auch wenn der Code die asynchrone Ausnahme behandelt. Dieses Verhalten ist ein Argument, mit dem strukturierte Ausnahmen nicht behandelt werden. Beachten Sie stattdessen, dass diese Ausnahmen schwerwiegend sind.

Wenn Sie **`/EHs`** oder verwenden **`/EHsc`** , geht der Compiler davon aus, dass Ausnahmen nur bei einer- **`throw`** Anweisung oder bei einem Funktions aufzurufen auftreten können. Diese Annahme ermöglicht es dem Compiler, Code zum Nachverfolgen der Lebensdauer von vielen nicht windable-Objekten auszuschließen, wodurch die Codegröße erheblich reduziert werden kann. Wenn Sie verwenden **`/EHa`** , kann das ausführbare Image größer und langsamer sein, da der Compiler **`try`** Blöcke nicht als aggressiv optimiert. Außerdem gibt es Ausnahme Filter, die lokale Objekte automatisch bereinigen, auch wenn der Compiler keinen Code sieht, der throw eine C++-Ausnahme haben kann.

### <a name="structured-and-standard-c-exception-handling"></a>Strukturierte und standardmäßige C++-Ausnahmebehandlung

Die **`/EHa`** -Compileroption ermöglicht eine sichere Stapel Auflösung für asynchrone Ausnahmen und C++-Ausnahmen. Sie unterstützt die Behandlung von standardmäßigen C++-und strukturierten Ausnahmen mithilfe der nativen C++- `catch(...)` Klausel. Wenn SEH Sie ohne Angabe von implementieren möchten **`/EHa`** , können Sie die **`__try`** **`__except`** Syntax, und verwenden **`__finally`** . Weitere Informationen finden Sie unter [strukturierte Ausnahmebehandlung](../../cpp/structured-exception-handling-c-cpp.md).

> [!IMPORTANT]
> Das angeben **`/EHa`** und angeben try , um alle Ausnahmen mithilfe von zu verarbeiten, `catch(...)` kann gefährlich sein. Da asynchrone Ausnahmen größtenteils nicht behebbar sind, gelten sie als schwerwiegende Ausnahmen. Wenn Sie sie abfangen und den Prozess anschließend fortsetzen, können Beschädigungen und Fehler auftreten, die schwer zu finden und zu beheben sind.
>
> Obwohl Windows und Visual C++ unterstützt SEH werden, wird dringend empfohlen, die ISO-Standard-C++-Ausnahmebehandlung ( **`/EHsc`** oder) zu verwenden **`/EHs`** . Dadurch wird Ihr Code portabler und flexibler. Manchmal müssen Sie SEH in Legacy Code oder für bestimmte Arten von Programmen verwenden. Dies ist beispielsweise erforderlich, wenn Code für die Unterstützung der Common Language Runtime ( [`/clr`](clr-common-language-runtime-compilation.md) ) kompiliert ist. Weitere Informationen finden Sie unter [strukturierte Ausnahmebehandlung](../../cpp/structured-exception-handling-c-cpp.md).
>
> Es wird empfohlen, dass Sie die mit kompilierten Objektdateien niemals mit den Dateien verknüpfen, **`/EHa`** **`/EHs`** die mit oder **`/EHsc`** im selben ausführbaren Modul kompiliert wurden. Wenn Sie eine asynchrone Ausnahme behandeln müssen, indem Sie eine beliebige Stelle **`/EHa`** in Ihrem Modul verwenden, kompilieren Sie mithilfe von **`/EHa`** den gesamten Code im Modul. Sie können die Syntax für die strukturierte Ausnahmebehandlung im selben Modul wie Code verwenden, der mit kompiliert wurde **`/EHs`** . Die Syntax kann jedoch nicht SEH mit C++ **`try`** , **`throw`** und **`catch`** in derselben Funktion gemischt werden.

Verwenden **`/EHa`** Sie, wenn Sie catch eine Ausnahme verwenden möchten, die von einem anderen als einem ausgelöst wird **`throw`** . In diesem Beispiel wird catch eine strukturierte Ausnahme generiert und erstellt:

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

### <a name="exception-handling-under-clr"></a>Ausnahmebehandlung unter/CLR

Die **`/clr`** Option impliziert **`/EHa`** (d. h **`/clr /EHa`** . ist redundant). Der Compiler generiert einen Fehler, wenn **`/EHs`** oder **`/EHsc`** nach verwendet wird **`/clr`** . Optimierungen wirken sich nicht auf dieses Verhalten aus. Wenn eine Ausnahme abgefangen wird, ruft der Compiler die klassendefiktoren für alle Objekte auf, die sich im gleichen Bereich wie die Ausnahme befinden. Wenn eine Ausnahme nicht abgefangen wird, werden diese debugtoren nicht ausgeführt.

Informationen zu Ausnahme Behandlungs Einschränkungen unter **`/clr`** finden Sie unter [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md).

### <a name="runtime-exception-checks"></a>Lauf Zeit Ausnahme Überprüfungen

Die- **`/EHr`** Option erzwingt Lauf Zeit Abbruch Prüfungen in allen Funktionen, die über ein- **`noexcept`** Attribut verfügen. Standardmäßig können Laufzeitüberprüfungen entfernt werden, wenn das Compiler-Back-End feststellt, dass eine Funktion nur *nicht- throw * Funktionen aufruft. throwNichtingfunktionen sind Funktionen, die über ein Attribut verfügen, das angibt, dass keine Ausnahmen n sein können throw . Sie umfassen Funktionen, die mit,, und gekennzeichnet sind, **`noexcept`** `throw()` `__declspec(nothrow)` Wenn **`/EHc`** angegeben wird, und **`extern "C"`** Functions. Zu throw den Funktionen, die der Compiler bestimmt hat, sind auch alle, die der Compiler bei der Überprüfung nicht erschließt throw . Sie können das Standardverhalten mithilfe von explizit festlegen **`/EHr-`** .

Ein throw nichtingattribut ist keine Garantie dafür, dass Ausnahmen nicht throw von einer Funktion n sein können. Im Gegensatz zum Verhalten einer **`noexcept`** Funktion betrachtet der MSVC-Compiler eine Ausnahme throw n durch eine Funktion, die mit, oder deklariert wurde, `throw()` `__declspec(nothrow)` als nicht **`extern "C"`** definiertes Verhalten. Funktionen, die diese drei Deklarations Attribute verwenden, erzwingen keine Lauf Zeit Beendigungs Prüfungen für Ausnahmen. Sie können die- **`/EHr`** Option verwenden, um dieses nicht definierte Verhalten zu identifizieren, indem Sie erzwingen, dass der Compiler Lauf Zeit Prüfungen für nicht behandelte Ausnahmen generiert, die eine Funktion mit Escapezeichen versehen **`noexcept`** .

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Festlegen der Option in Visual Studio oder Programm gesteuert

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie **Konfigurations Eigenschaften**  >  **C/C++-**  >  **Code Generierung**aus.

1. Ändern Sie die Eigenschaft **C++-Ausnahmen aktivieren** .

   Oder legen Sie den Wert für **C++-Ausnahmen aktivieren** auf **Nein**fest, und fügen Sie dann auf der Eigenschaftenseite **Befehlszeile** im Feld **Zusätzliche Optionen** die Compileroption hinzu.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.

## <a name="see-also"></a>Weitere Informationen

[MSVC-Compileroptionen](compiler-options.md)\
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)\
[Fehler-und Ausnahmebehandlung](../../cpp/errors-and-exception-handling-modern-cpp.md)\
[Ausnahme Spezifikationen ( throw )](../../cpp/exception-specifications-throw-cpp.md)\
[Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)

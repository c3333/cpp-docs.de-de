---
title: /EH (Ausnahmebehandlungsmodell)
description: Referenzhandbuch zu den Compileroptionen für Microsoft C++/EH (Ausnahme Behandlungsmodell) in Visual Studio.
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
- ':::no-loc(SEH):::'
- ':::no-loc(try):::'
- ':::no-loc(catch):::'
- ':::no-loc(throw):::'
- ':::no-loc(extern):::'
- ':::no-loc(finally):::'
- ':::no-loc(noexcept):::'
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: f158e951d595d5934ff513254871710db5920bf1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232715"
---
# <a name="eh-exception-handling-model"></a>/EH (Ausnahmebehandlungsmodell)

Gibt die vom Compiler generierte Ausnahme Behandlungsmodell Unterstützung an. Mit Argumenten wird angegeben, ob eine `:::no-loc(catch):::(...)` Syntax auf strukturierte und standardmäßige C++-Ausnahmen angewendet werden soll, ob ** :::no-loc(extern)::: "C"** -Code :::no-loc(throw)::: Ausnahmen angenommen werden und ob bestimmte Überprüfungen entfernt werden sollen **`:::no-loc(noexcept):::`** .

## <a name="syntax"></a>Syntax

> **`/EHa`**[**`-`**]\
> **`/EHs`**[**`-`**]\
> **`/EHc`**[**`-`**]\
> **`/EHr`**[**`-`**]

## <a name="arguments"></a>Argumente

**`a`**\
Aktiviert die standardmäßige C++-Stapel Entwicklung. Fängt bei Verwendung von Syntax sowohl strukturierte (asynchrone) als auch C++ (synchrone) Standard Ausnahmen ab `:::no-loc(catch):::(...)` . **`/EHa`** Überschreibt beide **`/EHs`** -und- **`/EHc`** Argumente.

**`s`**\
Aktiviert die standardmäßige C++-Stapel Entwicklung. Fängt nur bei Verwendung von Syntax Standard-C++-Ausnahmen ab `:::no-loc(catch):::(...)` . Sofern nicht **`/EHc`** auch angegeben wird, geht der Compiler davon aus, dass als ** :::no-loc(extern)::: "C"** deklarierte Funktionen :::no-loc(throw)::: eine C++-Ausnahme darstellen dürfen.

**`c`**\
Bei Verwendung mit **`/EHs`** geht der Compiler davon aus, dass Funktionen, die als ** :::no-loc(extern)::: "C"** deklariert sind, niemals :::no-loc(throw)::: eine C++-Ausnahme sind. Sie hat keine Auswirkung, wenn Sie mit verwendet wird **`/EHa`** (das heißt, **`/EHca`** ist äquivalent zu **`/EHa`** ). **`/EHc`** wird ignoriert, wenn **`/EHs`** oder **`/EHa`** nicht angegeben ist.

**`r`**\
Weist den Compiler an, immer Lauf Zeit Beendigungs Prüfungen für alle Funktionen zu generieren **`:::no-loc(noexcept):::`** . Standardmäßig können Lauf Zeit Prüfungen für **`:::no-loc(noexcept):::`** optimiert werden, wenn der Compiler feststellt, dass die Funktion nur Funktionen aufruft, die keine :::no-loc(throw)::: Funktionen sind. Diese Option bietet strikte C++-Konformität mit den Kosten für zusätzlichen Code. **`/EHr`** wird ignoriert, wenn **`/EHs`** oder **`/EHa`** nicht angegeben ist.

**`-`**\
Löscht das vorherige options Argument. Beispielsweise **`/EHsc-`** wird als interpretiert **`/EHs /EHc-`** , und entspricht **`/EHs`** .

**`/EH`** Argumente können in beliebiger Reihenfolge separat oder kombiniert angegeben werden. Wenn mehr als eine Instanz desselben Arguments angegeben wird, überschreibt der letzte alle früheren Instanzen.  Beispielsweise **`/EHr- /EHc /EHs`** ist identisch mit **`/EHscr-`** und **`/EHscr- /EHr`** hat denselben Effekt wie **`/EHscr`** .

## <a name="remarks"></a>Bemerkungen

### <a name="default-exception-handling-behavior"></a>Standardverhalten bei der Ausnahmebehandlung

Der Compiler generiert immer Code, der die asynchrone strukturierte Ausnahmebehandlung () unterstützt :::no-loc(SEH)::: . Wenn keine **`/EHsc`** ,- **`/EHs`** oder- **`/EHa`** Option angegeben ist, unterstützt der Compiler standardmäßig :::no-loc(SEH)::: Handler in der nativen C++- `:::no-loc(catch):::(...)` Klausel. Es generiert jedoch auch Code, der nur teilweise C++-Ausnahmen unterstützt. Der standardmäßige Entwicklungscode für Ausnahmen zerstört keine automatischen C++-Objekte außerhalb von [:::no-loc(try):::](../../cpp/:::no-loc(try):::-:::no-loc(throw):::-and-:::no-loc(catch):::-statements-cpp.md) Blöcken, die aufgrund einer Ausnahme außerhalb des Gültigkeits Bereichs liegen. Ressourcen Lecks und undefiniertes Verhalten können ergeben, wenn eine C++-Ausnahme :::no-loc(throw)::: n ist.

### <a name="standard-c-exception-handling"></a>Standard mäßige C++-Ausnahmebehandlung

Vollständige Compilerunterstützung für das Standard mäßige C++-Ausnahme Behandlungsmodell, das Stapel Objekte sicher entlädt, erfordert **`/EHsc`** (empfohlen), **`/EHs`** oder **`/EHa`** .

Wenn Sie **`/EHs`** oder verwenden **`/EHsc`** , dann sind Ihre- `:::no-loc(catch):::(...)` Klauseln keine :::no-loc(catch)::: asynchronen strukturierten Ausnahmen. Alle Zugriffs Verletzungen und verwalteten <xref:System.Exception?displayProperty=fullName> Ausnahmen werden nicht abgefangen. Außerdem werden Objekte im Bereich, wenn eine asynchrone Ausnahme auftritt, nicht zerstört, auch wenn der Code die asynchrone Ausnahme behandelt. Dieses Verhalten ist ein Argument, mit dem strukturierte Ausnahmen nicht behandelt werden. Beachten Sie stattdessen, dass diese Ausnahmen schwerwiegend sind.

Wenn Sie **`/EHs`** oder verwenden **`/EHsc`** , geht der Compiler davon aus, dass Ausnahmen nur bei einer- **`:::no-loc(throw):::`** Anweisung oder bei einem Funktions aufzurufen auftreten können. Diese Annahme ermöglicht es dem Compiler, Code zum Nachverfolgen der Lebensdauer von vielen nicht windable-Objekten auszuschließen, wodurch die Codegröße erheblich reduziert werden kann. Wenn Sie verwenden **`/EHa`** , kann das ausführbare Image größer und langsamer sein, da der Compiler **`:::no-loc(try):::`** Blöcke nicht als aggressiv optimiert. Außerdem gibt es Ausnahme Filter, die lokale Objekte automatisch bereinigen, auch wenn der Compiler keinen Code sieht, der :::no-loc(throw)::: eine C++-Ausnahme haben kann.

### <a name="structured-and-standard-c-exception-handling"></a>Strukturierte und standardmäßige C++-Ausnahmebehandlung

Die **`/EHa`** -Compileroption ermöglicht eine sichere Stapel Auflösung für asynchrone Ausnahmen und C++-Ausnahmen. Sie unterstützt die Behandlung von standardmäßigen C++-und strukturierten Ausnahmen mithilfe der nativen C++- `:::no-loc(catch):::(...)` Klausel. Wenn :::no-loc(SEH)::: Sie ohne Angabe von implementieren möchten **`/EHa`** , können Sie die **__ :::no-loc(try)::: **-, **`__except`** -und- **`__:::no-loc(finally):::`** Syntax verwenden. Weitere Informationen finden Sie unter [strukturierte Ausnahmebehandlung](../../cpp/structured-exception-handling-c-cpp.md).

> [!IMPORTANT]
> Das angeben **`/EHa`** und angeben :::no-loc(try)::: , um alle Ausnahmen mithilfe von zu verarbeiten, `:::no-loc(catch):::(...)` kann gefährlich sein. Da asynchrone Ausnahmen größtenteils nicht behebbar sind, gelten sie als schwerwiegende Ausnahmen. Wenn Sie sie abfangen und den Prozess anschließend fortsetzen, können Beschädigungen und Fehler auftreten, die schwer zu finden und zu beheben sind.
>
> Obwohl Windows und Visual C++ unterstützt :::no-loc(SEH)::: werden, wird dringend empfohlen, die ISO-Standard-C++-Ausnahmebehandlung ( **`/EHsc`** oder) zu verwenden **`/EHs`** . Dadurch wird Ihr Code portabler und flexibler. Manchmal müssen Sie :::no-loc(SEH)::: in Legacy Code oder für bestimmte Arten von Programmen verwenden. Dies ist beispielsweise erforderlich, wenn Code zur Unterstützung der Common Language Runtime ([/CLR](clr-common-language-runtime-compilation.md)) kompiliert ist. Weitere Informationen finden Sie unter [strukturierte Ausnahmebehandlung](../../cpp/structured-exception-handling-c-cpp.md).
>
> Es wird empfohlen, dass Sie die mit kompilierten Objektdateien niemals mit den Dateien verknüpfen, **`/EHa`** **`/EHs`** die mit oder **`/EHsc`** im selben ausführbaren Modul kompiliert wurden. Wenn Sie eine asynchrone Ausnahme behandeln müssen, indem Sie eine beliebige Stelle **`/EHa`** in Ihrem Modul verwenden, kompilieren Sie mithilfe von **`/EHa`** den gesamten Code im Modul. Sie können die Syntax für die strukturierte Ausnahmebehandlung im selben Modul wie Code verwenden, der mit kompiliert wurde **`/EHs`** . Die Syntax kann jedoch nicht :::no-loc(SEH)::: mit C++ **`:::no-loc(try):::`** , **`:::no-loc(throw):::`** und **`:::no-loc(catch):::`** in derselben Funktion gemischt werden.

Verwenden **`/EHa`** Sie, wenn Sie :::no-loc(catch)::: eine Ausnahme verwenden möchten, die von einem anderen als einem ausgelöst wird **`:::no-loc(throw):::`** . In diesem Beispiel wird :::no-loc(catch)::: eine strukturierte Ausnahme generiert und erstellt:

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail()
{
    // generates SE and attempts to :::no-loc(catch)::: it using :::no-loc(catch):::(...)
    :::no-loc(try):::
    {
        int i = 0, j = 1;
        j /= i;   // This will :::no-loc(throw)::: a SE (divide by zero).
        printf("%d", j);
    }
    :::no-loc(catch):::(...)
    {
        // :::no-loc(catch)::: block will only be executed under /EHa
        cout << "Caught an exception in :::no-loc(catch):::(...)." << endl;
    }
}

int main()
{
    __:::no-loc(try):::
    {
        fail();
    }

    // __except will only :::no-loc(catch)::: an exception here
    __except(EXCEPTION_EXECUTE_HANDLER)
    {
        // if the exception was not caught by the :::no-loc(catch):::(...) inside fail()
        cout << "An exception was caught in __except." << endl;
    }
}
```

### <a name="exception-handling-under-clr"></a>Ausnahmebehandlung unter/CLR

Die **`/clr`** Option impliziert **`/EHa`** (d. h **`/clr /EHa`** . ist redundant). Der Compiler generiert einen Fehler, wenn **`/EHs`** oder **`/EHsc`** nach verwendet wird **`/clr`** . Optimierungen wirken sich nicht auf dieses Verhalten aus. Wenn eine Ausnahme abgefangen wird, ruft der Compiler die klassendefiktoren für alle Objekte auf, die sich im gleichen Bereich wie die Ausnahme befinden. Wenn eine Ausnahme nicht abgefangen wird, werden diese debugtoren nicht ausgeführt.

Informationen zu Ausnahme Behandlungs Einschränkungen unter **`/clr`** finden Sie unter [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md).

### <a name="runtime-exception-checks"></a>Lauf Zeit Ausnahme Überprüfungen

Die- **`/EHr`** Option erzwingt Lauf Zeit Abbruch Prüfungen in allen Funktionen, die über ein- **`:::no-loc(noexcept):::`** Attribut verfügen. Standardmäßig können Laufzeitüberprüfungen entfernt werden, wenn das Compiler-Back-End feststellt, dass eine Funktion nur *nicht- :::no-loc(throw)::: * Funktionen aufruft. :::no-loc(throw):::Nichtingfunktionen sind Funktionen, die über ein Attribut verfügen, das angibt, dass keine Ausnahmen n sein können :::no-loc(throw)::: . Sie umfassen Funktionen, die mit,, und gekennzeichnet sind, **`:::no-loc(noexcept):::`** `:::no-loc(throw):::()` `__declspec(no:::no-loc(throw):::)` Wenn **`/EHc`** angegeben wird, ** :::no-loc(extern)::: "C"** -Funktionen. Zu :::no-loc(throw)::: den Funktionen, die der Compiler bestimmt hat, sind auch alle, die der Compiler bei der Überprüfung nicht erschließt :::no-loc(throw)::: . Sie können das Standardverhalten mithilfe von explizit festlegen **`/EHr-`** .

Ein :::no-loc(throw)::: nichtingattribut ist keine Garantie dafür, dass Ausnahmen nicht :::no-loc(throw)::: von einer Funktion n sein können. Im Gegensatz zum Verhalten einer **`:::no-loc(noexcept):::`** Funktion betrachtet der MSVC-Compiler eine Ausnahme :::no-loc(throw)::: n durch eine Funktion, die mit `:::no-loc(throw):::()` , `__declspec(no:::no-loc(throw):::)` oder ** :::no-loc(extern)::: "C"** als nicht definiertes Verhalten deklariert wurde. Funktionen, die diese drei Deklarations Attribute verwenden, erzwingen keine Lauf Zeit Beendigungs Prüfungen für Ausnahmen. Sie können die- **`/EHr`** Option verwenden, um dieses nicht definierte Verhalten zu identifizieren, indem Sie erzwingen, dass der Compiler Lauf Zeit Prüfungen für nicht behandelte Ausnahmen generiert, die eine Funktion mit Escapezeichen versehen **`:::no-loc(noexcept):::`** .

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Festlegen der Option in Visual Studio oder Programm gesteuert

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>So legen Sie diese Compileroption in der Visual Studio-Entwicklungsumgebung fest

1. Öffnen Sie das Dialogfeld **Eigenschaftenseiten** des Projekts. Weitere Informationen erhalten Sie unter [Set C++ compiler and build properties in Visual Studio (Festlegen der Compiler- und Buildeigenschaften (C++) in Visual Studio)](../working-with-project-properties.md).

1. Wählen Sie **Konfigurations Eigenschaften**  >  **C/C++-**  >  **Code Generierung**aus.

1. Ändern Sie die Eigenschaft **C++-Ausnahmen aktivieren** .

   Oder legen Sie den Wert für **C++-Ausnahmen aktivieren** auf **Nein**fest, und fügen Sie dann auf der Eigenschaftenseite **Befehlszeile** im Feld **Zusätzliche Optionen** die Compileroption hinzu.

### <a name="to-set-this-compiler-option-programmatically"></a>So legen Sie diese Compileroption programmgesteuert fest

- Siehe <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.

## <a name="see-also"></a>Siehe auch

[MSVC-Compileroptionen](compiler-options.md)\
[MSVC-compilerbefehlszeilensyntax](compiler-command-line-syntax.md)\
[Fehler-und Ausnahmebehandlung](../../cpp/errors-and-exception-handling-modern-cpp.md)\
[Ausnahme Spezifikationen ( :::no-loc(throw)::: )](../../cpp/exception-specifications-:::no-loc(throw):::-cpp.md)\
[Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)

---
title: Linkertoolfehler LNK2019
description: Alles zum Microsoft Visual Studio Linker-Fehler LNK2019 und zur Diagnose und Korrektur in C-und C++-Code.
ms.date: 01/15/2020
f1_keywords:
- LNK2019
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
no-loc:
- main
- WinMain
- wmain
- wWinMain
- __cdecl
- __stdcall
- __fastcall
- __vectorcall
- extern
- static
- const
- ARCH
- AVX2
- wchar_t
- VERBOSE
- EXPORTS
- SYMBOLS
- DUMPBIN
- UNDNAME
ms.openlocfilehash: d09e232b934761d138fee7324c462c915d919959
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509732"
---
# <a name="linker-tools-error-lnk2019"></a>Linkertoolfehler LNK2019

> nicht aufgelöstes extern Al-Symbol '*Symbol*' in Funktion '*Funktion*' referenziert

Der kompilierte Code für die *Funktion* erstellt einen Verweis oder einen Code, aber der Linker kann die Symbol Definition nicht in einer der Bibliotheken oder Objektdateien *finden, die verknüpft werden sollen*.

Auf diese Fehlermeldung folgt ein schwerwiegender Fehler [Linkertoolfehler LNK1120](../../error-messages/tool-errors/linker-tools-error-lnk1120.md). Um Fehler Linkertoolfehler LNK1120 zu beheben, müssen Sie zuerst alle LNK2001-und LNK2019-Fehler beheben.

## <a name="possible-causes"></a>Mögliche Ursachen

Es gibt viele Möglichkeiten, diesen Fehler zu erhalten. Alle Elemente beinhalten einen Verweis auf eine Funktion oder Variable, die der Linker nicht *Auflösen*konnte, oder es wurde eine Definition für gefunden. Der Compiler kann erkennen, wenn ein Symbol nicht *deklariert*ist, aber er kann nicht erkennen, wenn das Symbol nicht *definiert*ist. Das liegt daran, dass sich die Definition in einer anderen Quelldatei oder Bibliothek befinden kann. Wenn auf ein Symbol verwiesen wird, aber nie definiert, generiert der Linker einen nicht aufgelösten extern Al-symbolfehler.

Hier sind einige der häufigsten Probleme aufgeführt, die zum Fehler LNK2019 führen:

### <a name="the-source-file-that-contains-the-definition-of-the-symbol-isnt-compiled"></a>Die Quelldatei, die die Definition des Symbols enthält, ist nicht kompiliert.

Stellen Sie in Visual Studio sicher, dass die Quelldatei, die das Symbol definiert, als Teil des Projekts kompiliert wird. Überprüfen Sie das zwischen Verzeichnis der Buildausgabe auf eine entsprechende obj-Datei. Wenn die Quelldatei nicht kompiliert ist, klicken Sie in Projektmappen-Explorer mit der rechten Maustaste auf die Datei, und wählen Sie **Eigenschaften** aus, um die Eigenschaften der Datei zu überprüfen. Auf der Seite "allgemeine **Konfigurations Eigenschaften**"  >  **General** sollte ein **Elementtyp** des **C/C++-Compilers**angezeigt werden. Stellen Sie in der Befehlszeile sicher, dass die Quelldatei, die die Definition enthält, kompiliert ist.

### <a name="the-object-file-or-library-that-contains-the-definition-of-the-symbol-isnt-linked"></a>Die Objektdatei oder-Bibliothek, die die Definition des Symbols enthält, ist nicht verknüpft.

Stellen Sie in Visual Studio sicher, dass die Objektdatei oder die Bibliothek, die die Symbol Definition enthält, als Teil des Projekts verknüpft ist. Stellen Sie in der Befehlszeile sicher, dass die Liste der zu verknüpfenden Dateien die Objektdatei oder-Bibliothek enthält.

### <a name="the-declaration-of-the-symbol-isnt-spelled-the-same-as-the-definition-of-the-symbol"></a>Die Deklaration des Symbols ist nicht mit der Definition des Symbols identisch.

Überprüfen Sie, ob Sie die richtige Rechtschreibung und groß Schreibung sowohl in der Deklaration als auch in der Definition verwenden und wo das Symbol verwendet oder aufgerufen wird.

### <a name="a-function-is-used-but-the-type-or-number-of-the-parameters-dont-match-the-function-definition"></a>Eine Funktion wird verwendet, aber der Typ oder die Anzahl der Parameter stimmt nicht mit der Funktionsdefinition.

Die Funktionsdeklaration muss mit die Definition übereinstimmen. Stellen Sie sicher, dass der Funktions Aufrufder Deklaration entspricht und dass die Deklaration mit der Definition übereinstimmt. Für Code, der Vorlagenfunktionen aufruft, sind auch entsprechende Deklarationen der Vorlagenfunktionen erforderlich, die dieselben Vorlagenparameter wie die Definition enthalten. Ein Beispiel für eine nicht übereinstimmende Vorlagen Deklaration finden Sie im Abschnitt "Sample LNK2019e. cpp" im Abschnitt "Beispiele".

### <a name="a-function-or-variable-is-declared-but-not-defined"></a>Eine Funktion oder Variable wurde deklariert, aber nicht definiert.

LNK2019 kann auftreten, wenn eine Deklaration in einer Header Datei vorhanden ist, aber keine übereinstimmende Definition implementiert ist. Für Element Funktionen oder static Datenmember muss die-Implementierung den klassenbereichsselektor enthalten. Ein Beispiel finden Sie unter [Missing Function Body or Variable](../../error-messages/tool-errors/missing-function-body-or-variable.md).

### <a name="the-calling-convention-is-different-between-the-function-declaration-and-the-function-definition"></a>Die Aufruf Konvention unterscheidet sich zwischen der Funktionsdeklaration und der Funktionsdefinition.

Aufruf Konventionen ( [__cdecl](../../cpp/cdecl.md) , [__stdcall](../../cpp/stdcall.md) , [__fastcall](../../cpp/fastcall.md) oder [__vectorcall](../../cpp/vectorcall.md) ) werden als Teil des ergänzten Namens codiert. Stellen Sie sicher, dass die Aufruf Konvention identisch ist.

### <a name="a-symbol-is-defined-in-a-c-file-but-declared-without-using-no-locextern-c-in-a-c-file"></a>Ein Symbol ist in einer C-Datei definiert, wurde aber ohne Verwendung von extern "C" in einer C++-Datei deklariert.

Symbole, die in einer als C kompilierten Datei definiert sind, haben andere ergänzte Namen als Symbole, die in einer C++-Datei deklariert sind, es sei denn, Sie verwenden einen [ extern C](../../cpp/extern-cpp.md) -Modifizierer Stellen Sie sicher, dass die Deklaration der Kompilierungs Verknüpfung für jedes Symbol entspricht. Auch wenn Sie ein Symbol in einer C++-Datei definieren, die von einem C-Programm verwendet wird, verwenden Sie `extern "C"` in der Definition.

### <a name="a-symbol-is-defined-as-no-locstatic-and-then-later-referenced-outside-the-file"></a>Ein Symbol wird als definiert static und später außerhalb der Datei referenziert.

Im Gegensatz zu C haben [globale const Ameisen](../../error-messages/tool-errors/global-constants-in-cpp.md) in C++ eine **`static`** Verknüpfung. Um diese Einschränkung zu umgehen, können Sie die **`const`** Initialisierungen in eine Header Datei einfügen und diesen Header in die CPP-Dateien einschließen, oder Sie können die Variable als nicht Ant festlegen const und einen Ant- const Verweis verwenden, um darauf zuzugreifen.

### <a name="a-no-locstatic-member-of-a-class-isnt-defined"></a>Ein static Member einer Klasse ist nicht definiert.

Ein static Klassenmember muss eine eindeutige Definition aufweisen oder gegen die eindefinitions Regel verstoßen. Ein static Klassenmember, der nicht Inline definiert werden kann, muss mithilfe seines voll qualifizierten Namens in einer Quelldatei definiert werden. Wenn er überhaupt nicht definiert ist, generiert der Linker LNK2019.

### <a name="a-build-dependency-is-only-defined-as-a-project-dependency-in-the-solution"></a>Eine Buildabhängigkeit wird nur als Projekt Abhängigkeit in der Lösung definiert.

In früheren Versionen von Visual Studio war dieses Abhängigkeits Niveau ausreichend. Ab Visual Studio 2010 erfordert Visual Studio jedoch einen [Projekt-zu-Projekt-Verweis](/visualstudio/ide/managing-references-in-a-project). Wenn das Projekt nicht über einen Projekt-zu-Projekt-Verweis verfügt, wird möglicherweise dieser Linker-Fehler angezeigt. Fügen Sie einen Interprojektverweis hinzu, um den Fehler zu beheben.

### <a name="an-entry-point-isnt-defined"></a>Ein Einstiegspunkt ist nicht definiert.

Der Anwendungscode muss einen geeigneten Einstiegspunkt definieren: `main` oder `wmain` für Konsolen Anwendungen und `WinMain` oder `wWinMain` für Windows-Anwendungen. Weitere Informationen finden Sie unter [ main Funktions-und Befehlszeilenargumente](../../cpp/main-function-command-line-args.md) oder [ WinMain Funktion](/windows/win32/api/winbase/nf-winbase-winmain). Wenn Sie einen benutzerdefinierten Einstiegspunkt verwenden möchten, geben Sie die Linkeroption [/Entry (Einstiegspunkt Symbol)](../../build/reference/entry-entry-point-symbol.md) an.

### <a name="you-build-a-console-application-by-using-settings-for-a-windows-application"></a>Sie erstellen eine Konsolenanwendung mithilfe von Einstellungen für eine Windows-Anwendung.

Wenn die Fehlermeldung dem nicht aufgelösten Al-Symbol ähnelt, ** extern auf das WinMain in der Funktions** *function_name*verwiesen wird, verknüpfen Sie es mit **/Subsystem: Console** anstelle von **/Subsystem: Windows**. Weitere Informationen zu dieser Einstellung und Anweisungen zum Festlegen dieser Eigenschaft in Visual Studio finden Sie unter [/SUBSYSTEM (Specify Subsystem)](../../build/reference/subsystem-specify-subsystem.md).

### <a name="you-attempt-to-link-64-bit-libraries-to-32-bit-code-or-32-bit-libraries-to-64-bit-code"></a>Sie versuchen, 64-Bit-Bibliotheken mit 32-Bit-Code oder 32-Bit-Bibliotheken in 64-Bit-Code zu verknüpfen.

Bibliotheken und Objektdateien, die mit dem Code verknüpft sind, müssen für die gleiche Architektur wie der Code kompiliert werden. Stellen Sie sicher, dass die Bibliotheken, auf die Ihr Projekt verweist, für dieselbe Architektur wie das Projekt kompiliert werden. Stellen Sie sicher, dass die Eigenschaft [/LIBPATH](../../build/reference/libpath-additional-libpath.md) oder **zusätzliche Bibliotheks Verzeichnisse** auf Bibliotheken verweist, die für die richtige Architektur erstellt wurden.

### <a name="you-use-different-compiler-options-for-function-inlining-in-different-source-files"></a>Sie verwenden verschiedene Compileroptionen für Inline Funktionen in verschiedenen Quelldateien.

Durch die Verwendung von Inlinefunktionen, die in CPP-Dateien definiert sind, und die Kombination von Inlinecompileroptionen für Funktionen in anderen Quelldateien kann LNK2019 verursacht werden. Weitere Informationen finden Sie unter [Function Inlining Problems](../../error-messages/tool-errors/function-inlining-problems.md).

### <a name="you-use-automatic-variables-outside-their-scope"></a>Sie verwenden automatische Variablen außerhalb ihres Bereichs.

Automatische Variablen (mit Funktionsgültigkeitsbereich) können nur im Rahmen dieser Funktion verwendet werden. Diese Variablen können nicht deklariert **`extern`** und in anderen Quelldateien verwendet werden. Ein Beispiel finden Sie unter [Automatic (Function Scope) Variables](../../error-messages/tool-errors/automatic-function-scope-variables.md).

### <a name="you-call-intrinsic-functions-or-pass-argument-types-to-intrinsic-functions-that-arent-supported-on-your-target-architecture"></a>Sie können intrinsische Funktionen oder Argument Typen an intrinsische Funktionen übergeben, die von der Zielarchitektur nicht unterstützt werden.

Wenn Sie z. b. eine systeminterne AVX2 Funktion verwenden, aber nicht die [ / ARCH AVX2 :](../../build/reference/arch-x86.md) -Compileroption angeben, geht der Compiler davon aus, dass die intrinsische extern Funktion eine Al-Funktion ist Anstatt eine Inline Anweisung zu generieren, generiert der Compiler einen-Befehl extern mit dem gleichen Namen wie das systeminterne-Symbol. Wenn der Linker versucht, die Definition dieser fehlende Funktion zu finden, wird LNK2019 generiert. Stellen Sie sicher, dass Sie nur systeminterne und von der Zielarchitektur unterstützte Typen verwenden.

### <a name="you-mix-code-that-uses-native-no-locwchar_t-with-code-that-doesnt"></a>Sie mischen Code, der Native wchar_t mit Code verwendet, der nicht

C++-sprach Konformität in Visual Studio 2005 hat **`wchar_t`** standardmäßig einen systemeigenen Typ hergestellt. Wenn nicht alle Dateien mit denselben **/Zc: wchar_t ** -Einstellungen kompiliert wurden, werden Typverweise möglicherweise nicht in kompatible Typen aufgelöst. Stellen Sie sicher, dass **`wchar_t`** die Typen in allen Bibliotheks-und Objektdateien kompatibel sind. Aktualisieren Sie entweder aus einer **`wchar_t`** typedef, oder verwenden Sie beim Kompilieren konsistente **/Zc: wchar_t ** settings-Einstellungen.

## <a name="third-party-library-issues-and-vcpkg"></a>Drittanbieter-Bibliotheks Probleme und vcpkg

Wenn dieser Fehler angezeigt wird, wenn Sie versuchen, eine Drittanbieter Bibliothek als Teil Ihres Builds zu konfigurieren, sollten Sie die Verwendung von [vcpkg](../../build/vcpkg.md), einem C++ Package Manager, zum Installieren und Erstellen der Bibliothek in Erwägung gezogen. vcpkg unterstützt eine große und wachsende [Liste von Bibliotheken von Drittanbietern](https://github.com/Microsoft/vcpkg/tree/master/ports). Dabei werden alle Konfigurations Eigenschaften und Abhängigkeiten festgelegt, die für erfolgreiche Builds als Teil des Projekts erforderlich sind.

## <a name="diagnosis-tools"></a>Diagnosetools

Manchmal ist es schwierig festzustellen, warum der Linker eine bestimmte Symbol Definition nicht finden kann. Häufig besteht das Problem darin, dass Sie den Code, der die Definition enthält, nicht in Ihren Build eingefügt haben. Oder Build-Optionen haben unterschiedliche ergänzte Namen für extern Al-Symbole erstellt. Es gibt mehrere Tools und Optionen, die Ihnen bei der Diagnose von LNK2019 Fehlern helfen können.

- [/VERBOSE](../../build/reference/verbose-print-progress-messages.md)Mithilfe der Option Linker können Sie feststellen, auf welche Dateien der Linker verweist. Mit dieser Option können Sie überprüfen, ob die Datei mit der Definition des Symbols in Ihrem Build enthalten ist.

- [/EXPORTS](../../build/reference/dash-exports.md)Mithilfe der [/SYMBOLS](../../build/reference/symbols.md) Optionen und des **DUMPBIN** Hilfsprogramms können Sie ermitteln, welche Symbole in den dll-und Objekt-oder Bibliotheksdateien definiert sind. Stellen Sie sicher, dass die exportierten ergänzten Namen den ergänzten Namen entsprechen, die der Linker sucht.

- Das **UNDNAME** Hilfsprogramm kann Ihnen das entsprechende nicht ergänzte extern Al-Symbol für einen ergänzten Namen anzeigen.

## <a name="examples"></a>Beispiele

Hier sind einige Beispiele für Code aufgeführt, der einen Fehler LNK2019 verursacht, sowie Informationen zur Behebung des Fehlers.

### <a name="a-symbol-is-declared-but-not-defined"></a>Ein Symbol wurde deklariert, aber nicht definiert

In diesem Beispiel ist eine extern Al-Variable deklariert, aber nicht definiert:

```cpp
// LNK2019.cpp
// Compile by using: cl /EHsc /W4 LNK2019.cpp
// LNK2019 expected
extern char B[100];   // B isn't available to the linker
int main() {
   B[0] = ' ';   // LNK2019
}
```

Es folgt ein weiteres Beispiel, in dem eine Variable und eine Funktion als deklariert werden, **`extern`** aber keine Definition bereitgestellt wird:

```cpp
// LNK2019c.cpp
// Compile by using: cl /EHsc LNK2019c.cpp
// LNK2019 expected
extern int i;
extern void g();
void f() {
   i++;
   g();
}
int main() {}
```

`i` `g` Der Linker generiert LNK2019, es sei denn, und werden in einer der Dateien definiert, die im Build enthalten sind. Sie können die Fehler beheben, indem Sie die Quellcodedatei mit den Definitionen in die Kompilierung einbeziehen. Alternativ können Sie obj-oder LIB-Dateien, die die Definitionen enthalten, an den Linker übergeben.

### <a name="a-no-locstatic-data-member-is-declared-but-not-defined"></a>Ein static Datenmember wurde deklariert, aber nicht definiert.

LNK2019 kann auch auftreten, wenn ein static Datenmember deklariert, aber nicht definiert ist. Im folgenden Beispiel wird LNK2019 generiert und gezeigt, wie Sie diesen Fehler beheben.

```cpp
// LNK2019b.cpp
// Compile by using: cl /EHsc LNK2019b.cpp
// LNK2019 expected
struct C {
   static int s;
};

// Uncomment the following line to fix the error.
// int C::s;

int main() {
   C c;
   C::s = 1;
}
```

### <a name="declaration-parameters-dont-match-the-definition"></a>Deklarations Parameter stimmen nicht mit der Definition

Code, der Vorlagenfunktionen aufruft, muss übereinstimmende Deklarationen von Vorlagenfunktionen aufweisen. Deklarationen müssen dieselben Vorlagenparameter wie die Definition enthalten. Das folgende Beispiel generiert LNK2019 für einen benutzerdefinierten Operator und zeigt, wie Sie diesen Fehler beheben.

```cpp
// LNK2019e.cpp
// compile by using: cl /EHsc LNK2019e.cpp
// LNK2019 expected
#include <iostream>
using namespace std;

template<class T> class
Test {
   // The operator<< declaration doesn't match the definition below:
   friend ostream& operator<<(ostream&, Test&);
   // To fix, replace the line above with the following:
   // template<typename T> friend ostream& operator<<(ostream&, Test<T>&);
};

template<typename T>
ostream& operator<<(ostream& os, Test<T>& tt) {
   return os;
}

int main() {
   Test<int> t;
   cout << "Test: " << t << endl;   // LNK2019 unresolved external
}
```

### <a name="inconsistent-no-locwchar_t-type-definitions"></a>Inkonsistente wchar_t Typdefinitionen

In diesem Beispiel wird eine DLL mit einem Export erstellt `WCHAR` , der verwendet, der in aufgelöst wird **`wchar_t`** .

```cpp
// LNK2019g.cpp
// compile with: cl /EHsc /LD LNK2019g.cpp
#include "windows.h"
// WCHAR resolves to wchar_t
__declspec(dllexport) void func(WCHAR*) {}
```

Im nächsten Beispiel wird die dll im vorherigen Beispiel verwendet, und LNK2019 wird generiert, da die Typen `unsigned short*` und `WCHAR*` nicht identisch sind.

```cpp
// LNK2019h.cpp
// compile by using: cl /EHsc LNK2019h LNK2019g.lib
// LNK2019 expected
__declspec(dllimport) void func(unsigned short*);

int main() {
   func(0);
}
```

Um diesen Fehler zu beheben, ändern **`unsigned short`** Sie in **`wchar_t`** oder `WCHAR` , oder kompilieren Sie "LNK2019g. cpp mithilfe von **/Zc: wchar_t - **.

## <a name="additional-resources"></a>Zusätzliche Ressourcen

Weitere Informationen zu möglichen Ursachen und Lösungen für LNK2001 finden Sie in der Stack Overflow Frage [Was ist ein nicht definierter Verweis/nicht aufgelöstes extern symbolfehler und wie kann ich das Problem beheben?](https://stackoverflow.com/q/12573816/2002113).
